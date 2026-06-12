---
title: "MaaS hosting"
date: 2014-10-09
forum: Ubuntu Cloud and Juju
---

### Post by psca119.tech on 2014-10-09
My other thread was basically worthless, so i think i narrowed it down to a few simple questions:
1) As my understanding MaaS takes slave "nodes" that you install on it as a OS, and then it can be used by the server "controller" that uses the nodes as "pools of resources"? Is this true? If so, my plan should work properly to start hosting major applications from vm's with this.

2) How would i be able to directly (without Juju, openstack, etc) have this attack to a hypervisor such as QEMU/KVM or Virtual Box, AND have some sort of web managment panel to create new vms, manage them, see their charts/graphs, delete them, and see the console (instance view) of them all on a webpage (some php software or some software in general)? what am i missing? How can i do this?

[IN SHORT]
Use hypervisor software (Virtual Box, QEMU/KVM) to use MaaS as its pools of resources, without extra software such as Juju would be nice, but not required, any suggestion would be appreciated greatly!
[/IN SHORT]

== SEPARATE ==
3) What is super similar to IIS, however is not Apache, NGINX, etc. Something that is best for binding ports, ip addresses, domains to, and best for automation so i can have a user register on a main site and have them create a subdomain and launch a new website attached with their account. Also with this... i have tried many SQL's such as MySQL, MariaDB, etc. etc. and hate them all, is it true i can simply create a PHP document and assign variables to that and have that be my database with MD_5 Hashed passwords? But then i would run into the problem of async file saving/file opening.


From old post:
[ATTACH=CONFIG]257084[/ATTACH]

---

### Post by tgalati4 on 2014-10-10
You want a simpler [framework]("https://help.ubuntu.com/community/UbuntuCloudInfrastructure") to use [MAAS]("http://maas.ubuntu.com/docs/install.html").  It doesn't exist.  Unless you write it.  That might make an interesting Google Summer of Code project.

And yes, you can write your own database to store your Node State with PHP.  But there are several good databases to choose from.  They all have a learning curve measured in Agony Units.  Are the Agony Units of writing your own PHP Node State Keeper lower or higher than learning *sqlite* to perform the same task?  Only you can answer that.

There are probably better frameworks for spinning up websites.  I am thinking of [Cyclone]("https://www.drupal.org/project/cyclone") on Drupal.  There may be others.

---

### Post by psca119.tech on 2014-10-10
Thank you! What do you exactly mean by simpler framework? OpenStack seems like a very complex framework compared to something simple of what i need, Anything you recommend? And i think my agony tward any database is more then having to write a php state of usernames and passwords (encrypted with MD_5 of course).

But i still don't know what to do, i am at level 0, any recommendations? Were you suggesting i follow [these]("https://help.ubuntu.com/community/UbuntuCloudInfrastructure") instructions? I am very confused, appologies.

---

### Post by tgalati4 on 2014-10-10
Yes, spend the time to learn the frameworks that have been designed to work together.  All of this may be overkill for what you want to use it for.  How many websites do you anticipate managing?  How many websites do you anticipate to manage in 5 years?

I am confused as well.  That's OK.  We can be confused together.  These are not Level 0 topics.  More like Level 8.

---

### Post by psca119.tech on 2014-10-10
I ment level 0 as in rock bottom there is no where to go but up on my services.

And thank you very much tgalati4 for your time haha, this is way over my head and i hope to learn from this expirience as i do it, but i need this up soon! And i hope you can help me with this:

I was wanting to host 3 services (webhosting, mc server instance hosting, file hosting)
But first i need something to fit the following needs:

Router = 192.168.0.1
Server = 192.168.0.2
Computers = DHCP 192.168.0.10+

I need lots of junk computers that are hooked up to a network switch (192.168.0.x) that will be running "client side software" and for a controller server (the Lenovo TS130 192.168.0.2) to run "server side software" to some how to take those computers and use them as pools of resources, as well as part of the local machine's resources (the server) and to have the interface of this software to be on port 80 (http) like openstack where i can see the stats and run instances, see the vms, etc, etc, but without the complex extra things that openstack has. These vms should be on the same network (192.168.0.x).

I was thinking MaaS but i need something simple. where i can literally plug in computers to this network switch, install clientside software or some sort (MaaS or something) and have goto the server and add that computer to the "slave cluster"...

Previously i have installed openstack with the DevStack installer, and my current Lenovo TS130 has 14 GB DDR3 RAM, an i3 dual core (hyperthreading) CPU, and 500 GB HDD storage, and openstack some how said in its interface IT had:
50 GB memory
1000 GB storage
and 10 vCPU's??

How?? And how can i achieve that with something simple and not openstack, is there something like a broken down simple version of OpenStack that has no "super network control with tennants etc etc.." i just want software like openstack that will do what im asking basically lol, anything sound similar? i was thinking MaaS could do the clustering part while i can just have MaaS attach to say virtualbox and give it those resources. But I'm guessing it is not that simple.

The website administration can wait for now, literally now i just need this to work, then i'd be happy to take the next steps.

=========================

As for just a preview of what i wanted:

1) You said yes that i could use PHP to replace MySQL for a login database etc, which i do prefer to know my own code then use something foreign to me such as SQL, plus i can be un-standard and not have the exploits that many of the SQL's have, since its custom. So anyways, my plan was when people goto my main page, then they register (sign up) their information executes a php file to add them to a php file where their information will either be added, modiefied, or deleted, depending on what they want to do, and in the users panel when they login they will have options of their services, Website, Minecraft, File hosting etc. Where they can manage that and or modify and or delete their account.

2) I need to know a webserver similar to IIS, not Apache, or NGINX, or node-js. But one that supports PHP. (easy address and port binding and website deployment, so when users buy a new website from my service, they get a sub-domain specified and on the backside php executes something to make the webserver auto create this website. And when a user (in the PHP custom "database") is deleted the website will be deleted as well.) some really automated simple system.

3) Automated minecraft administration and deployment with PHP, some how need to see the console without r-con and a way to make minecraft run on the same port, but bind to addresses like HTTP.

---

### Post by tgalati4 on 2014-10-11
So, after 5 posts, what you really want is an automated minecraft server--one that spins up different minecraft servers for each paying customer.  I don't know of an off-the-self solution to this Use Case.

A simple google search:  "How do I spin up multiple minecraft servers?"

[http://www.reddit.com/r/admincraft/comments/2iwely/minecraft_instance_management/](http://www.reddit.com/r/admincraft/comments/2iwely/minecraft_instance_management/)

[http://www.yourwarrantyisvoid.com/2013/03/10/how-to-build-a-better-minecraft-server/](http://www.yourwarrantyisvoid.com/2013/03/10/how-to-build-a-better-minecraft-server/)

[http://www.spigotmc.org/threads/multiple-instances-on-single-box-to-run-one-server.134/](http://www.spigotmc.org/threads/multiple-instances-on-single-box-to-run-one-server.134/)

As for MAAS:  Has anyone written a JuJu charm to spin up minecraft servers?

I found at least one description of a minecraft charm:  [http://marcoceppi.com/2011/11/deploying-the-minecraft-charm/](http://marcoceppi.com/2011/11/deploying-the-minecraft-charm/)

---

### Post by psca119.tech on 2014-10-11
Not only minecraft server hosting, again multiple services, not just minecraft, website creation must also be automated.

I have done 2 years of minecraft hosting manually and it would be nice to make it automated, but thats not my main concern as to this server, i need a good base system to work off of, virtualization, hypervisor, as i have listed above.

---

### Post by tgalati4 on 2014-10-11
There are Juju charms to spin up web servers, file servers, and minecraft servers.  Install the Ubuntu Cloud Infrastructure and you have all of that at your disposal.

---

