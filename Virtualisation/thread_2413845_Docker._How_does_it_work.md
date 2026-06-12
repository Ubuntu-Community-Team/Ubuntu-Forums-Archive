---
title: "Docker. How does it work?"
date: 2019-03-02
forum: Virtualisation
---

### Post by Tadaen_Sylvermane on 2019-03-02
I can find any number of guides to install and create docker containers. But I don't understand how to use them. Are they in the hosts $PATH and work like any other app or program ?Do they have internal networking, or like a container that I can bridge to my lan?

For example, mythtv seems like it could work in docker well. But how do I actually connect to it, start it, and so forth.

Ultimately I'd like to move everything I can into Docker. But I can't find how to actually use it beyond container creation.

---

### Post by kc1di on 2019-03-03
[This guide ]("https://wsvincent.com/beginners-guide-to-docker/")may be of help in answering your questions about Docker. And [this one ]("https://medium.com/devgorilla/how-to-install-docker-on-ubuntu-18-04-495216a16092")also.

---

### Post by rahulkhot3333 on 2019-04-24
You can check install docker on Ubuntu guide to know more about docker. There you will get most of the information about using docker on Ubuntu. I have installed docker using [install docker on Ubuntu]("https://linux4one.com/how-to-install-and-use-docker-on-ubuntu-18-04/") guide

---

### Post by TheFu on 2019-04-27
Docker is a form a "container."  In Linux, containers are a shortened way to say cgroups, permissions, and limited access to specific hardware devices.  You could build your own "container" manually, but these things are complex and have taken years, over a decade, for the container professionals to get close to secured.

Whatever you do, don't confuse containers with virtualization. They are nothing alike under the covers. They work in completely different ways, though they appear to a neophyte admin as similar.  Containers have more in common with a chroot setup than hypervisors.

DO NOT TREAT CONTAINERS like you would treat a VM.  The security of containers mostly comes from limiting any extra tools inside the container.  For example, don't have bash (or any shell) inside a container, unless absolutely necessary.  The best practices for containers are clear about a few things.  Only put those things absolutely required for the 1 service the container is meant to provide inside the container.  1 service, 1 container.  If you need to modify any settings, destroy the container, modify the build-files, then recreate the container.  Basically, treat containers like you'd treat a zombie that stops doing what you need. Shoot it in the head and make another.

Whether there is networking provided into a container or not is optional.  Whether there is data available from inside a container or not, is optional.  The big push is called "microservices" and "serverless-computing", which leverage containers.  Containers are spun up for each request, as needed, handle the request, then destroyed.

You can read more about cgroups via google.

The good thing about containers is that they are implemented in the Linux kernel and don't have any hardware requirements.  Containers work on any system that runs a modern Linux kernel (v3.x and later), regardless of the hardware.

Training on all these things is available, for a price.  [https://www.theregister.co.uk/Tag/serverless%20computing](https://www.theregister.co.uk/Tag/serverless%20computing)

---

### Post by 1clue on 2019-04-27
The software implementing virtual machines implements a piece of hardware, and you create a guest and install an operating system on it. The guest can be the same OS as the host, or a different one. Or a different version of the same one. You assign it RAM and disk space and a network card or 2, and whatever else you need.

Docker is a container, like TheFu said. Containers use the kernel of the host, and are restricted by namespaces which are implemented in the kernel. It's a less robust isolation than VMs have, which means less overhead and less secure. By default docker has a private network used by docker, which is a virtual network. No real computer except the docker host can see this network, it works with NAT like most home routers do, and your docker host is the router. You can create a number of networks for your docker containers, and assign each running container to whatever network you want. You can also choose to use the host's network.

The above paragraph means that you could set up some sort of app server, for example, on one docker container, and have another docker container which has its database. You can configure a network containing only the host (your docker "server") and the app server and the database server. You can expose just the http interface of the app server, and the database is hidden from all outside access. You can have other docker containers running too, and they would then have some other network in common or you would separate them out. This practice isolates containers from outside attack, meaning they need to compromise your host before they can get to the docker database server for the above app server. As opposed to an http-based attack on your app server, which (hypothetically) you exposed in order to let your docker container do real work on a real network.

---

