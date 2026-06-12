---
title: "Ubuntu as a router/firewall"
date: 2012-10-20
forum: Server Platforms
---

### Post by MrBurrito on 2012-10-20
First of all thank you for looking at my thread. Before I start asking for help I want to say I've searched the forums and only found 2 threads related one is from [2006]("http://ubuntuforums.org/showthread.php?t=111972&highlight=Ubuntu+router+firewall") and the other one was last edited back in [2009]("http://ubuntuforums.org/showthread.php?t=926001&highlight=Ubuntu+router+firewall"), non of the two describe what I want to do exactly so I am creating a thread for it.  

Right now I have a Netgear WNDR3700 with DD-WRT as my router, and unfortunately it has to be rebooted every other day with because of a full routing table and other load issues. I've been wanting to replace this with a low power computer running Ubuntu Server as a router/firewall but I want this to be a non-headless unit, I want to be able to monitor and visualize what the kids do. So I want this setup to have a graphical interface so I am able to run monitoring tools from within.  

I want the setup to do basic routing, firewalling, upnp, DMZ, and maybe some content filtering and access restrictions. I guess if I put it in layman terms I want something similar to DD-WRT but with a graphical interface if that makes any sense at all. 

Is this even a possibility? I am not highly concerned about Fort Knox security for this unit since it is just a home network, with no file server or storage running. I have some computers setup with my HDTV's to stream video content etc, that are online for long periods of time, but there is no personal file storage on them. I attached a visual concept of what I am trying to do if it is of any help.

Any suggestions about where to start will be greatly appreciated.

---

### Post by iponeverything on 2012-10-20
the wndr3700 should run openwrt just fine - and you can install monitoring tools on it..

---

### Post by MrBurrito on 2012-10-21
> **iponeverything said:**
> the wndr3700 should run openwrt just fine - and you can install monitoring tools on it..

Thank You for your reply. I am aware of OpenWRT as I currently have DD-WRT on the WNDR3700. But I am looking at another solution/possibility as mentioned on my post.

---

### Post by cariboo on 2012-10-21
You amy find it easier to run something like [ipcop]("http://www.ipcop.org/") or [smoothwall]("http://www.smoothwall.org/"), instead of trying to do the same thing with Ubuntu.

---

### Post by MrBurrito on 2012-10-21
> **cariboo907 said:**
> You amy find it easier to run something like [ipcop]("http://www.ipcop.org/") or [smoothwall]("http://www.smoothwall.org/"), instead of trying to do the same thing with Ubuntu.

Thank you very much, I will look into those.

---

### Post by sandyd on 2012-10-21
You may find [clearOS]("http://www.clearfoundation.com/Software/overview.html") useful as well.

---

### Post by Cheesemill on 2012-10-21
Another option would be [Zentyal]("http://www.zentyal.org/"), which is based on Ubuntu 12.04.

---

### Post by MrBurrito on 2012-10-21
> **Cheesemill said:**
> Another option would be [Zentyal]("http://www.zentyal.org/"), which is based on Ubuntu 12.04.

Thank you for your reply. I am looking a this as an option right now. I'm over at their forums figuring things out. This solution has everything I am looking for with the exception of Upnp, which I guess I will figure out on getting it working.

---

### Post by kennethconn on 2012-10-21
If "low power computer" is your requirement, I'd revisit your current devices' configuration or upgrade to a similar device that will meet your needs, as opposed to running an old computer.

_Of the products that have been mentioned so far:_
[LIST=1]
[*]I found IPCop to be great (think it's based on smoothwall, but I liked it so much I stuck with it);
[*]ClearOS is also good (I've always found it's web interface very slow though and it is overkill for your needs);
[*]Give me dd-wrt over OpenWRT any day.
[/LIST]

---

### Post by iponeverything on 2012-12-16
> **kennethconn said:**
> 
[*]Give me dd-wrt over OpenWRT any day.
[/LIST]

I have ran both, and OpenWRT is more stable and flexible that dd-wrt.

every tried to build a new module for dd-wrt?

how about reporting a bug, like transparent bridging being broken (like it was for over year) and have bs and friends declare it invalid.

how about writeable filesystem? how about support for rc.local?

how about working traffic shaping?

you can have dd-wrt --

---

