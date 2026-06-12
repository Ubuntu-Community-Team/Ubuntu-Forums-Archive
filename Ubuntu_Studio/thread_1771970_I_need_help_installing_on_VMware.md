---
title: "I need help installing on VMware"
date: 2011-05-30
forum: Ubuntu Studio
---

### Post by Ronagon on 2011-05-30
I'm trying to install Ubuntu Studio 11.04 on my VMware Workstation, and it runs all the way through the blue install screen, and then plops me down at a black screen with a login/password prompt.

When I enter the correct values, it just logs me into the command line, and does nothing else.  I ran the "sudo apt-get update" and upgrade commands, and they did their thing, but it never kicked over to a GUI desktop.

I'm running VMware within 64-bit Windows 7, on a dual-core Intel processor.

Any suggestions?

---

### Post by garvinrick4 on 2011-05-31
> I'm running VMware within 64-bit Windows 7, on a dual-core Intel processor.Are you installing 32 bit linux? A lot of processors though dual core will only support
32 bit Linux. I have installed different versions of distro's in VMware player and all
worked at 32 bit and Ubuntu was easiest to install VMware tools after install of O.S.
RedHat cousins uses a perl script for tools, is a real nice script to run though.
Check your processor with a google search.

---

### Post by jkott on 2011-09-30
Similar problem here, after installing Ubuntu Studio 11.04, I get a login command prompt, no desktop environment.

I am running VMWare Fusion 3.1.3 on Mac OSX Snow Leopard, v 10.6.8

---

### Post by dturanski on 2012-01-18
I found this helpful [http://communities.vmware.com/thread/35333](http://communities.vmware.com/thread/35333)

---

### Post by jeffs0214 on 2012-02-15
The following thread helped me to get the gui environment and all of the necessary plug-ins:


(you may need to copy and paste to your address bar)


[http://ubuntuforums.org/showthread.php?t=900676]("http://http//ubuntuforums.org/showthread.php?t=900676")

---

### Post by CivilizationII on 2012-02-17
vmware player 4.0.2 and workstation 8.0.2 are compatible with ubuntu 11.

If you want the player release and vmware tools, you need to download them by hand from 4.0.1, as the repo currently doesn't exist for 4.0.2 automatic tool

---

