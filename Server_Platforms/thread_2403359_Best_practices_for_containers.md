---
title: "Best practices for containers?"
date: 2018-10-10
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2018-10-10
My htpc / server is running a few services all bare metal. Dhcp, dns, apt-cache proxy, minecraft servers, transmission torrents, mariadb among others.

I want to bring my system in line with best practices. I'm comfortable with lxd and wondering if I should be isolating these all in different containers. What is best practice for a home server and container usage?

---

### Post by 1clue on 2018-10-10
Best practices depends on who you ask I think, with respect to lightweight containers.

***Edit:** I know you said lxd, linux containers. I don't have direct experience with them so I posted with respect to the larger subject. I hope you don't mind.*

If you're talking about a full VM (kvm, vmware, etc) then this is a well-traveled road and in use pretty much everywhere.

If you're talking about docker.io or Linux containers then the isolation is not as much as you might think, and I'm not sure of the security implications. These containers are designed to provide some sort of isolation while minimizing resources needed to run the services, but I personally think the isolation is more with respect to prevention of one micro-service from interfering with another. I have yet to see a serious security evaluation, not that there isn't one I just haven't seen it.

Having been a Linux guy at home and in the server room since the 90s, I've done a lot of it on bare metal, and a lot of boxes had a bunch of different services on them.

Doing it old-school sort of locks you in from making changes. You install each service and get it working, and as you go you make sure all the pre-existing services are working before you continue. But it's like a house of cards, one little mistake can wreck the whole stack. So especially in a production environment you tend to stress over changes, and changes become a bureaucratic process rather than a technical one. You have one or more test servers, you need to specify what exact change you want to make and then make it on the test servers to verify that it works. Then people test it for a week or two, and then you "promote" the change to the next server up the chain. The process reminds me of the environmental impact studies necessary to build a dam or power plant.

Absolutely, positively, if you have containers which isolate a service so that it can be executed in any suitable host, separate from any other service, that's a good thing with respect to maintenance and management. You can configure a failover server for DHCP or DNS by cloning the VM and tweaking it. You can detect an old service in need of an update, build a new container with the updated service and get it working before you shut down the old service, rather than have down time for an hours-long upgrade that may or may not work.

Absolutely, positively, a full VM without any of the convenience magic (shared drives, etc), on a host which supports vt-x, is as secure as a bare metal host. The small bit of code that causes virtualization to work on hardware which supports virtualization has been reviewed countless times.

Lightweight containers, the jury is still out on security. There's a bigger attack surface from one container to the next. Not all containers follow container best practices, which is that the container should only have code which directly pertains to the service and nothing else. Some of them have an entire Linux distro in there. The good news in that case is that all of your containers which use the same distro are using literally the same blocks on the disk. The bad news is that if one of those common dependencies is compromised then all your containers using those dependencies are compromised.

I use qemu with kvm, VirtualBox, vmware and cloud services in my work and on production servers. I'm playing with docker.io with intent to put some of our less critical services on it, purely internal stuff for now.

I also use tiny hardware for some things. For example, at home I use a Raspberry Pi for a stratum 1 time server. That would work nicely in a small to medium office too, but more than maybe 100 seats would overload it. You could do the dhcp/dns service on a pi too. The problem with this approach is that when your service needs more CPU time you can't get it. And when your service doesn't need the available hardware resources they can't be used for something else.

I recommend using containers in whatever way they help you out. I also recommend learning more about security and stability issues of whatever you use.

From a practical standpoint, dhcp and dns are frequently grouped together as they talk to each other in a typical network. I would make a VM with isc-dhcp-server and bind9 on it, get it working, clone it to different hardware and make failover servers from the clone. Minecraft and transmission would certainly be isolated as much as I could get them to be isolated.

***Edit:** lxd as I understand it is simply namespaces in Linux, which allows some control of limits of cpu, memory and disk space per namespace. As I have not used these I can't really say how much isolation there actually is. In reading the documentation it seemed like not very much isolation at all, which doesn't work for my purposes.*

---

