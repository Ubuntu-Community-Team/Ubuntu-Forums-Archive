---
title: "Multi-node Hadoop cluster with Docker"
date: 2016-01-27
forum: Virtualisation
---

### Post by Kovacs_Akos on 2016-01-27
I am in planning phase of a multi-node Hadoop cluster in a Docker based environment. So it should be based on a lightweight easy to use virtualized system.
Current architecture(regarding to documentation) contains 1 master and 3 slave nodes. This host machine uses HDFS filesystem and KVM for virtualization.
The whole cloud is managed by Cloudera Management Platform. There are several Hadoop modules installed on this cluster. There is also a NodeJS data upload service.
This time I should make architecture Docker based.
I have read several tutorials and have some opinions, but also open questions.
**A.** What do you think, is [this ]("https://github.com/Lewuathe/docker-hadoop-cluster")a good base for my project? I have found also an official [image]("https://hub.docker.com/r/cloudera/quickstart/"), but it is single-node.
**B.** How will system requirements change if I would like to make this in a single container? It would be great, because this architecture should work in different locations, so changes can be easily transferred between these locations. Synchronization between these so called clones should be important.
**C.** Do you have maybe some ideas, maybe best practices?

---

### Post by MAFoElffen on 2016-01-29
(1) I have a server acting as one of my virtualisation Hosts, that is hosting KVM, Docker and LXC. Note that the concept of what I said means that those 3 services can coexist side-by-side to each each other ... not that one exists within another.

So if your host is running KVM, then it would also be running Docker as a service, but it does not depend on KVM. Docker can be on it's own.

(2) Docker was made for the concept of running visualized application containers. 
> 
The **Docker** framework enables a Linux application and its dependencies to be packaged as a container. Container-based virtualization isolates applications from each other on a shared operating system (OS). This approach standardizes application program delivery, allowing apps to run in any Linux environment, whether physical or virtual. Because they share the same operating system, containers are portable among different Linux distributions and are significantly smaller than virtual machine (VM) images. 

Meaning it starts an basic OS container (flavored and selectable) to run an application, with that application installed in it, that runs until that application finishes what you had told it to do, then releases the environment container. So you to keep a container open, for like a server, then you open an environment with a job of Bash... configure your server in that environment... shut it down gracefully... etc... So when keeping it open, the services you are running are just a side/byproduct of the application container. You trick it to stay open. So can be done (I do it), but outside of what Docker's main purpose... Which leads to subject #3.

(3) So if I show you the Definition of LXC:
> 
**LXC** (Linux Containers) is an operating-system-level virtualization environment for running multiple isolated Linux systems (containers) on a single Linux control host.

Isn't that more along the lines of your role intend? Because the concept of nodes falls more within that framework. I no you might think of me being picky about semantics, but it comes down to treating a service or role as an application. When I think of applications, I think of them as something that has an end-point: something that runs to a completion. I don't think of services and roles as having a completion point... they are just available.

Just bringing up things from what I've seen on mine.

---

