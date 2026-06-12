---
title: "Ubutu and EBOX"
date: 2007-01-10
forum: Server Platforms
---

### Post by netbotix on 2007-01-10
Has anyone got both Ubuntu and eBox working together?
I am a newbie when it comes to ubuntu and found these [http://www.debianhelp.co.uk/ebox.htm](http://www.debianhelp.co.uk/ebox.htm)
installation instructions for debian, and was wondering if I followed the same guide would it still work since ubuntu is built off of debian?
thanks!

---

### Post by dexem on 2007-01-29
ebox it is not for debian nor ubuntu. It's a distro based on debian. So, if you want to use it, you should install it from the install CD or test it with the live CD version :)

Try it and comment us your feelings :)

---

### Post by maxamillion on 2007-01-29
> **dexem said:**
> ebox it is not for debian nor ubuntu. It's a distro based on debian. So, if you want to use it, you should install it from the install CD or test it with the live CD version :)

Try it and comment us your feelings :)

No, its not a distribution based on debian ... [http://www.ebox-platform.com/installation-guide](http://www.ebox-platform.com/installation-guide) <-- explains how one can add repositories and just install the packages. It does offer an installer, but its just a debian install image with the packages included and the sources appended to the sources.list

And I wouldn't recommend trying to run ebox ontop of ubuntu, I don't think you would get the results you had hoped for.

---

### Post by jrock2004 on 2007-01-29
why would you not recommend it? It looks better and setup to help noobs with setting up a firewall. Just curious cause I am going to be working on a firewall soon

---

### Post by dexem on 2007-01-30
> **maxamillion said:**
> No, its not a distribution based on debian ... [http://www.ebox-platform.com/installation-guide](http://www.ebox-platform.com/installation-guide) <-- explains how one can add repositories and just install the packages. It does offer an installer, but its just a debian install image with the packages included and the sources appended to the sources.list

Ok, that's true. It used to be able to be installed that way, but sometimes a working installation of debian could not work as expected if you install the packages, depending on the configuration. That's the reason because it's better to consider it as a derived distro (and install it from the Install CD) and not just a bunch of .deb's

Anyway, I'll file a bug to my workmates to talk about that page you point. Probably soon it will be fixed. Thanks :)

> And I wouldn't recommend trying to run ebox ontop of ubuntu, I don't think you would get the results you had hoped for.

Of course. Don't try it with ubuntu. Altough I made a patch to not overwrite /etc/sudoers each time the config is saved, the different packages versions between debian and ubuntu could create problems, because config files could be different.

---

### Post by Burgundavia on 2007-07-16
Ebox is now packaged for Ubuntu and is in the Gutsy repos. The server team has adopted it and it will be the official config platform in the future.

Corey

---

### Post by waynorthny on 2007-07-25
Will there be a backport for feisty? That would be *great*. I'd never heard of ebox before but it looks good.

I'd love to install and run it on a feisty server ... I'm configuring a server for a client now, and ebox would be the answer to a lot of problems I'm encountering, and a lot of the client's wishes for an easy administrative interface.

---

### Post by syadnom on 2007-07-26
though it is in the gutsy repos, it looks to be broken!

---

### Post by syadnom on 2007-07-26
correction, "partially broken".  now can be installed if done:

apt-get install ebox
apt-get install ebox-network

DONT apt-get install ebox-all or it breaks for now.  this is on launchpad so should be fixed pronto.

---

### Post by JGJones on 2007-08-01
eBox is really decent - I use this for a charity I work in and it works very well. It's also ideal for the non-admin to use as well with a guide - ie adding a new user etc. It's a perfect solution for small businesses and charities wishing to minimise their spending on IT.

It's not an enterprise level solution...yet, but apart from that, for a small ofice etc, it's ideal and I recommend it.

---

### Post by ChrisSnow on 2007-08-03
Great news for me! Have been trying to get ebox onto an AMD64 platform for a few days. The guys at ebox are very supportive but it's just not happening for me. Downloading the gutsy server image now!

---

### Post by ChrisSnow on 2007-08-03
All works just fine. Will all the various eBox elements become available in time via apt such as proxy server, content filtering and file sharing etc?

---

### Post by e30power on 2007-10-29
A few problems:
I installed EBox-all on a 7.10 server over SSH, and the EBOX firewall settings locked me out of the ssh session, thus forcing me to drive to the physical box, and hook a monitor up to it.
This needs to be addressed before ebox goes primetime.
Also, ebox is no where near as full featured as webmin IMHO. I use webmin to do a whole host of things, from manage what starts at boot to a DNS configurator.
E-Box does not seem to have all these functions, and part of the the spec as an easy business server would have to have user addition, boot scripts, etc etc through a web interface. Unless the plan is to write a whole new application (or I am missing something), E-Box only handles a select few of operations.
Why is Ubuntu moving away from webmin?

---

### Post by ZzeusS on 2007-11-04
Thank you e30power.  I spent the better part of an hour trying to figure out what I was missing with Ebox.  I've been using Webmin and know Jamie personally for the better part of probably eight years.

Good to know I'm not missing out on anything, and can still continue to install Webmin without worry.

Appreciate the simple validation

---

### Post by Geeman20000 on 2008-04-11
Have there been any updates guys? please can you share the updates on the wiki. So others can follow progress particularly ref hardy.

[https://wiki.ubuntu.com/SmallBusinessServer(](https://wiki.ubuntu.com/SmallBusinessServer() there is a section for Ubuntu+ebox)

---

### Post by JGJones on 2008-04-11
The latest news is that they are now putting test packages of the latest version of ebox (0.11.99 at moment) in Hardy - further details are available from the announcement page on ebox forum by the ebox staff:

[http://forum.eboxplatform.com/index.php?WSESSID=735f43794acd6c653a126b238780678e&topic=219.0](http://forum.eboxplatform.com/index.php?WSESSID=735f43794acd6c653a126b238780678e&topic=219.0)

Not all packages are available yet, but according to the announcement this is what is available and what is pending:

List of available modules

libebox
ebox
ebox-ca
ebox-dhcp
ebox-dns
ebox-firewall
ebox-network
ebox-ntp
ebox-objects
ebox-openvpn
ebox-printers
ebox-samba
ebox-services
ebox-squid
ebox-usersandgroups

Pending modules

ebox-mail
ebox-mailfilter
ebox-soap
ebox-software
ebox-trafficshaping

I have to say that ebox is really seriously excellent as an office server and I've got it running (on Debian) in 4 offices without issues and the SOAP control centre is going to make managing all of them so much easier.

---

### Post by nealmcb on 2008-04-25
eBox in Hardy should be lots better than the gutsy version.

Please see and contribute to the wiki documentation on eBox:

 [https://help.ubuntu.com/community/eBox](https://help.ubuntu.com/community/eBox)

and report any bugs in launchpad:

 [https://bugs.edge.launchpad.net/ubuntu/+source/ebox/+bugs](https://bugs.edge.launchpad.net/ubuntu/+source/ebox/+bugs)

---

### Post by Buffalo Soldier on 2008-04-30
nealmcb,

thanks for mentioning that link :) I'm just starting to use Ebox

---

### Post by sanesto on 2008-04-30
Hello, i am a new user to the ubuntu server, and i install the ebox, but the problem , i can't access to ebox , so how can i access to my ebox ??
thanks

---

### Post by mscdex on 2008-06-14
Is there a place to download a Live CD that uses the latest version (0.11.101) of eBox? Currently there is only 0.11.99 on the eBox download webpage.

---

