---
title: "Basic Architecture Question"
date: 2017-08-17
forum: Virtualisation
---

### Post by agh98 on 2017-08-17
Greetings, 

I am looking to setup a new server that will host MySQL and Apache to run a Django-based web application. Also want to run a GIT server and a few other pieces. I will be starting with a recycled i5 quad core processor and a gigabyte mobo that I have available. I am looking for the most efficient and secure way to virtualize the environment. I am intrigued but know little about current offerings such as Juju, LXD, MAAS, etc. However, the prospect of running my key services in separate containers with the possibility to move/scale them up both locally and on the cloud is amazing - not to mention the potential for easier installation via Juju Charms to avoid a lot of manual setup and connection of services. 

Most basically, I am curious what my approach should be - install Ubuntu server, then LXD, then Juju, and then the services I need - OR, should I stick with traditional virtual environments and run separate instances of ubuntu.  While I have used hypervisors in the past, it has been some time and I am not up to speed on the current/best offerings.  

I want it to all run on one physical PC for now, until I scale up in the future. Thus, it seems I might want to:

1) Install Ubuntu Server;
2) Install LXD;
3) Install Juju;
4) Create a local controller;
5) Deploy applications [...]

Is there a cohesive howto for how to do the above? I have seen this link: [https://jujucharms.com/docs/stable/tut-lxd](https://jujucharms.com/docs/stable/tut-lxd) which has some good info.

Or, instead of Juju on top of Ubuntu/LXD, should I be thinking more bare metal and Juju running on top of MAAS or some other design? 

Thanks!

Adam

---

### Post by TheFu on 2017-08-18
Containers are not virtualization.

Don't use containers if you care about security. There are still to many issues.  
If you want to host internal web development, containers are great.
If you want to host cat videos, containers are great.
If you want to host HIPPA data, don't touch them.
If you want to honestly tell any clients that their data is secure, don't use containers.

Nothing but more time can make container security better.  Let the sheep discover many of the existing issues, not your clients.

And management of containers has little to do with management of normal systems. It is a completely different methodology.  Treat every container like a banana.  It goes bad quickly and needs to be replaced every time a patch is needed.  If you load ssh onto any container, then you are doing it wrong.

MySQL - really?  MariaDB is preferred.

And apache is a little heavy for containers. There are lighter web servers.

I realize this isn't what you want to hear.

---

### Post by agh98 on 2017-08-18
Thank you for your response. This is helpful and it IS what I want to hear - especially if it deters me from starting down a path I might later regret. I was excited about the potential ease of use of utilizing Juju to deploy the individual services which would then be wrapped together, but from what you say it sounds like it might not be ready for prime time yet. So, I guess MAAS is in the same boat...

Should I then be thinking about installing KVM on top of Ubuntu Server (or something lighter?) and just create a virtual machine for the database, and another for the web server? To answer your question, we were using MySQL because we needed Django integration, but it seems that people have been able to connect MariaDB with django (we thought this was not a possibility previously).

Thanks again for your guidance.

---

### Post by TheFu on 2017-08-18
The **2016 SELF** conference was all about working with containers and the best practices in doing so.  Redhat presented about 6 different container-related presentations. There are youtube videos.  These are high-level, not deep down details, so you can get a bunch of overview information about containers, working with them, best practices for continuous integration and security.

MariaDB is client-API compatible with MySQL. Use the mysql clients and/or client libraries to access mariaDB. It has been that way since the beginning.
On the server-side, use the same CLI tools and options with mariadb as you do with mysql.  For example, if you use mysqldump, keep doing that. The command names haven't changed.

I'm protective of my data.

---

