---
title: "How Upgrade too many computers at once?"
date: 2008-07-29
forum: Server Platforms
---

### Post by tofighi on 2008-07-29
I'm administrator of about 10 servers and 200 pc all of them are ubuntu.
I install ubuntu 8.04 on them and make a local repository by apt-mirror.

I have 2 Important questions:

1) Is there anyway to say to all pc get updates and install them automatically? you know, 200 pcs are hard to manage one by one.
and think about upgrades from ubuntu 8.04 to next release, it will be a nightmare if you want to upgrade them one by one again!

2) I have Hardy repository of ubuntu and as I said, I make it by apt-mirror, now think the next version will be released. I must run apt-mirro again for that release and make a new repository? I mean if I want only have the latest release of ubuntu on all of my computers and servers, I only need the latest repository, is there any way to upgrade my mirror too?:confused:

---

### Post by Sef on 2008-07-29
Moved to server platforms.

I would recommend to keep Hardy on the computers, as it is a long term stable release and all is working well.

---

### Post by tofighi on 2008-07-29
> **Sef said:**
> 
I would recommend to keep Hardy on the computers, as it is a long term stable release and all is working well.

You recommend I ignore new releases of ubuntu for 5 years and only update hardy repository and only get security patches?

Maybe I do that for servers, but please think about 200 PCs, I think it will be better to upgrade them, what you think?

---

### Post by SunnyRabbiera on 2008-07-29
yeh, well even windows will have issues like this in a scenario like the one you described

---

### Post by cdtech on 2008-07-29
You installed 200 pc's without planing for updates, or is this something planed for future?

There is a check box within the System > Administration > Software Sources that allows automatic security updates and downloading of all updates in the background.

---

### Post by tofighi on 2008-08-01
> **cdtech said:**
> You installed 200 pc's without planing for updates, or is this something planed for future?

I want to install them, is there any automatic full installation for all of them?

---

### Post by cdtech on 2008-08-02
A couple of places you can start -

[https://help.ubuntu.com/community/UbuntuOnCluster](https://help.ubuntu.com/community/UbuntuOnCluster)

FAI
[http://www.informatik.uni-koeln.de/fai/](http://www.informatik.uni-koeln.de/fai/)

Hope this helps.....

---

### Post by Chayak on 2008-08-02
I've done batch updates using clusterssh that allows you to send batch commands to many systems at once.  All of the client machines were setup to update off of our onsite mirror and the setup eventually went to automated updates as we went to testing everything and then updating the mirror.

Also in large deployments shell/python/perl scripting is your best friend.

---

### Post by windependence on 2008-08-02
The easiest way woud be to set up a boot server, and configure it so that when you boot the client, they automatically do the install. RedHat and CentOS do this very well, and I can't see why you couldn't set this up on Ubuntu. You can also record the install when you do a desktop install, so if you did that and put the install on the boot server, you could get them to start a fully automated install.

-Tim

---

