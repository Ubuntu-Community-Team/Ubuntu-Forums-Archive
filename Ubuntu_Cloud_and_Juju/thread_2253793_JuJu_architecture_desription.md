---
title: "JuJu architecture desription?"
date: 2014-11-22
forum: Ubuntu Cloud and Juju
---

### Post by eddie-shvartsman on 2014-11-22
Greetings! Is there any document that describes juju architecture? What is the role and functions provided by the juju server? The role and function of the juju client? Where do they reside in relation to the deployed instances. What platforms can juju deploy to?  For example, can I deploy a RHEL based workload or does juju only support Ubuntu hosted workloads? I have explored juju.ubuntu.com, but this is somewhat high level and does not really describe the architecture. 

Any help would be greatly appreciated!

---

### Post by eddie-shvartsman on 2014-11-22
Greetings! I am new :) 

What platforms can juju deploy workloads/services on?  For example, can I deploy a RHEL  based workload described in a juju charm?

Thanks!

---

### Post by QIII on 2014-11-22
Merged.

These questions are much the same.  Please do not start multiple threads regarding the same issues.  It dilutes the community's efforts by causing different people to answer in different places and also causes confusion.

Thanks.

---

### Post by eddie-shvartsman on 2014-11-22
I don't really think they are the same.. one is asking about a documentation source, the other a specific technical question.

---

### Post by grahammechanical on 2014-11-22
> [COLOR=#333333][FONT=Ubuntu]Like Juju itself, the GUI is 100% Free Software, feel free to check it out and get in touch with us.[/FONT][/COLOR]

[https://juju.ubuntu.com/resources/juju-gui/](https://juju.ubuntu.com/resources/juju-gui/)

Juju is open source. There is nothing stopping the Redhat developers from taking the Juju code and modifying it according to the licence agreement so that it runs on the Redhat distribution. That is work for the Redhat developers to do, if they are so inclined.

> [COLOR=#333333][FONT=Ubuntu]This tutorial will show you how to get started with Juju, including installing, configuring and bootstrapping a new Juju environment. Before you start you will need:[/FONT][/COLOR]

[LIST]
[*]An Ubuntu, OSX or Windows machine to install the client on.
[/LIST]


[https://juju.ubuntu.com/docs/](https://juju.ubuntu.com/docs/)

> [COLOR=#333333][FONT=Ubuntu]The new project supports more cloud providers and run on Linux, Windows, and OS X.[/FONT][/COLOR]

[https://launchpad.net/juju](https://launchpad.net/juju)

Juju is software. It uses what are called "Charms." These charms are something like scripts that automate the process of deploying cloud based services to cloud servers. These charms have to be written. Anyone can write a charm. The Juju client is the bit of software that runs on a computer and it is used to run the charms that deploy the cloud services to servers in the cloud. There is a client for Ubuntu, Windows and OSX

Juju is developed by Ubuntu developers and so it is only natural that its developers focus on using Juju on Ubuntu and not some other Linux distribution. As far as I know Canonical does not a offer a cloud based hosting service. Juju will deploy services to Amazon Web Service, Windows Azure, HP Public Cloud, Joyent, DigitalOcean, OpenStack, and MAAS (Metal As A Service).

> [COLOR=#252525][FONT=sans-serif] Canonical has publicly announced[/FONT][/COLOR][SUP][*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*][/SUP][COLOR=#252525][FONT=sans-serif] that they are open to contributions to support other operating systems.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Juju_%28software%29](http://en.wikipedia.org/wiki/Juju_%28software%29)

Why do they call it Juju? Because it works like magic and with magic we are not supposed to know how it works.

Regards.

---

### Post by eddie-shvartsman on 2014-11-23
@[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") Thank you for the reply. I have read the documentation you have referenced and to be candid, these pubs are all rather vague from a technical perspective. Let me try to give an example of what seems to be "magic" as you say.. ;-)  The following questions should be straight forward and answered by basic product documentation:
(1) What are the functional roles of the Juju server and the Juju client? 
(2) Where do the clients and servers run in relation to the services they are managing? For example, can I run Juju client and server on same operating system instance? Do I have to deploy services on the same operating system instance where Juju is running? Or can I deploy to a remote system? All of this is somewhat glossed over in the docs. 
(3) Where do charms reside? On the Juju server or are they simply transportable files that can be consumed wherever? 
(4) Irrespective of where Juju runs, if I construct my charm to stand up a non-Ubuntu distro (like RedHat for example), will that work with the current product set? (this would imply that Juju can deploy remotely)

Thanks for the help!

---

### Post by Elfy on 2014-11-24
*Thread moved to **Ubuntu Cloud and Juju**.*

---

