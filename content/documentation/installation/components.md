---
title: Components
weight: 10
type: documentation
url: /installation
menu:
  main:
    parent: installation
---

# Understanding Vamp's components

To get Vamp up and running on an architecture of your choice, you first need to have a basic grip on Vamp's various components and how Vamp works with [container drivers](/documentation/installation/container_drivers/). If that's all clear, then proceed to the installation steps of your choice.

- [Centos & RHEL](/installation/centos_rhel/)
- [Ubuntu](/installation/ubuntu/)
- [Debian](/installation/debian/)
- [OSX](/installation/osx/)

If that sounds to much like work, then just use our [Docker quickstart](/quick-start).

## Architecture and components

Vamp consists of multiple server and client side components that together create the Vamp platform. Before installing, it is necessary to understand the role of each component and its preferred location in typical architecture. 

![](/img/vamp_arch.svg)

component              | purpose
-----------------------|--------
**[Vamp](https://github.com/magneticio/vamp)**               | Main API endpoint, business logic and service coordinator. Talks to the configured container manager (Docker, Marathon etc.) and synchronizes it with Vamp Gateway Agent via ZooKeeper. Uses a standard JDBC database for persistence (H2 and MySQL are tested). Uses Elasticsearch to store Vamp events (e.g. changes in deployments).
**[Vamp Gateway Agent](https://github.com/magneticio/vamp-gateway-agent)** | Reads the HAProxy configuration from ZooKeeper and reloads the HAProxy on each configuration change with as close to zero client request interruption as possible. Reads the logs from HAProxy over socket and push them to Logstash over UDP. Handles and recovers from ZooKeeper and Logstash outages without interrupting the haproxy process and client requests.
**[Vamp UI](https://github.com/magneticio/vamp-ui)**            | Graphical web interface for managing Vamp. Packaged with Vamp. 
**Vamp CLI**           | Command line interface for managing Vamp and integration with (shell) scripts.

Please see our [configuration documentation](/documentation/installation/configuration) on how to configure all Vamp components.

  