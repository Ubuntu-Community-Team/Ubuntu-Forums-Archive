---
title: "Ubuntu 10.10 LTSP some clients don't boot"
date: 2010-12-18
forum: Server Platforms
---

### Post by Lost Fisherman on 2010-12-18
In my mixed environment, we're trying to test multiple types and models of computers. Many of the computers boot just fine, but some go to a screen with ubuntu in the middle, with a 5-dot progress bar below the word.
 
How can I get rid of that screen, and see what's going on behind the scenes? I've modified the append line to remove quiet, add no splash, and and nomodeset, but that screen still appears.

---

### Post by neomod on 2010-12-18
Have a look here : [http://ubuntuforums.org/showthread.php?t=378861](http://ubuntuforums.org/showthread.php?t=378861)

and here: [http://ubuntuforums.org/showthread.php?t=542082](http://ubuntuforums.org/showthread.php?t=542082)

---

### Post by Lost Fisherman on 2010-12-18
Thanks for the reply neomod.  Two more questions if I may:
 
1.  Have the boot options changed between 8.04 and 10.10?  IIRC, 8.04 wanted 'nosplash' instead of just deleting the 'splash' parm.
 
2.  Are the suggestions from the linked threads equivalently implemented for LTSP by adding or removing parms from the 'append' line in the default pxe config?

---

### Post by neomod on 2010-12-18
> **Lost Fisherman said:**
> Thanks for the reply neomod.  Two more questions if I may:
 1.  Have the boot options changed between 8.04 and 10.10?  IIRC, 8.04 wanted 'nosplash' instead of just deleting the 'splash' parm.
 

As far as I can test, I've also noted this slight difference.

> **Lost Fisherman said:**
> 2.  Are the suggestions from the linked threads equivalently implemented  for LTSP by adding or removing parms from the 'append' line in the  default pxe config?
 
Honestly I can't grant it for sure, I'm sorry.

---

### Post by Lost Fisherman on 2010-12-21
Neomod et. al, thanks, removing quiet splash did the trick, now I can see what´s going on with the computers that don´t boot.

For some reason, after the image is downloaded, the computer requests a new IP address lease.  Don´t know why, but that´s what it is doing.  It never gets a response to the dhcp request, but logs a message along with the dhcp stuff:  ¨udhcpc (v0.9.9-pre) started¨

So why does the computer need a new lease? What is this message?  Why do some of the computers work?  And, finally, how do I fix this?

---

### Post by Lost Fisherman on 2010-12-21
MORE INFORMATION:  error message after image download and before the screen fills up with dhcp connect failures.

ADDRCONF:  NETDEV_UP:  eth0:  link is not ready

How can the link not be ready after the image was downloaded successfully?

---

### Post by Lost Fisherman on 2010-12-21
Yet more info:  this is occurring on computers that have multiple network interfaces, though not universally.  Seems to be related to 3Com NICs being installed, but I have not proven that conclusively.

---

### Post by Lost Fisherman on 2010-12-22
Bump.
 
Anybody have any advice at all?  I tried disabling the onboard NIC, no joy.

---

### Post by Lost Fisherman on 2010-12-22
Bump.
 
Any advice?

---

### Post by bab1 on 2010-12-22
> **Lost Fisherman said:**
> Bump.
 
Anybody have any advice at all?  I tried disabling the onboard NIC, no joy.

The latest versions of Ubuntu use Upstart insteat of SysV init.  Upstart is an event driven init system.  The problem looks like a timing of the network up and various services.  See [**_here _**]("http://www.google.com/search?q=Upstart+&btnG=Go!#sclient=psy&hl=en&q=upstart+ubuntu+tutorial&aq=3&aqi=g5&aql=&oq=&gs_rfai=&pbx=1&fp=ca05a7bb65e82229")for more info.

---

### Post by Lost Fisherman on 2010-12-22
Thanks bab1, I´ll take some time to look at that - that bit of kung fu is rather advanced for my level.

However, while researching the problem I seem to have stumbled upon something:  udhcpc and how interfaces are assigned their designators.  I guess the interface that initially downloads the image isn´t necessarily the one that is assigned as eth0.  I saw some advice about adding IPAPPEND 3 to the default config, but that didn´t help me.

Anybody know if it is possible to configure udchpc to fail over to the next interface when it fails to acquire an ip address on eth0?

---

### Post by bab1 on 2010-12-22
> **Lost Fisherman said:**
> Thanks bab1, I´ll take some time to look at that - that bit of kung fu is rather advanced for my level.

However, while researching the problem I seem to have stumbled upon something:  udhcpc and how interfaces are assigned their designators.  I guess the interface that initially downloads the image isn´t necessarily the one that is assigned as eth0.  I saw some advice about adding IPAPPEND 3 to the default config, but that didn´t help me.

Anybody know if it is possible to configure udchpc to fail over to the next interface when it fails to acquire an ip address on eth0?
I'm no expert on *udhcpc *, but I can tell you that it is part of **BusyBox** this is the embedded Linux that is part of the Debian/Ubuntu installer and rescue disk.  See [**_here for BusyBox_**]("http://en.wikipedia.org/wiki/BusyBox") and [**_here for udhcpc_**]("http://en.wikipedia.org/wiki/Udhcpc").  

It appears that when the Ubuntu boot fails (maybe a networking failure) you are being pushed to a BusyBox shell.  When I boot my server the networking is set and I never see *udhcpc * or *BusyBox* notices at all.

---

### Post by Lost Fisherman on 2010-12-23
> **bab1 said:**
> I'm no expert on *udhcpc *, but I can tell you that it is part of **BusyBox** this is the embedded Linux that is part of the Debian/Ubuntu installer and rescue disk. See [**_here for BusyBox_**]("http://en.wikipedia.org/wiki/BusyBox") and [**_here for udhcpc_**]("http://en.wikipedia.org/wiki/Udhcpc"). 
 
It appears that when the Ubuntu boot fails (maybe a networking failure) you are being pushed to a BusyBox shell. When I boot my server the networking is set and I never see *udhcpc *or *BusyBox* notices at all.
 
I don't think it's bouncing me out to a shell; it just keeps repeating the same error message sequence over and over as it continues to try connecting to the DHCP server

---

### Post by Lost Fisherman on 2011-01-04
I'm back after a holiday sabbatical.
 
I've determined that I have 2 issues - 1 solved, 1 unsolved.
 
Solved issue: Allied Telesyn NICs need IPAPPEND 2 in pxelinux.cfg/default.
 
Unsolved issue: 3Com 3CR990 NICs are still unbootable. 
 
If I leave out the IPAPPEND, then the workstation wants to start up on the system board's network interface, even though the image was downloaded through the 3Com NIC. If I connect both interfaces to the switch, the computer locks up after getting its addy from dhcpd on the server.
 
If I use IPAPPEND 1, it downloads the image then drops out to a busybox prompt.
 
If I use IPAPPEND 3, it downloads the image locks up.
 
If I use IPAPPEND 2, well, that doesn't work either, but I forgto to write down what the workstation does.
 
If it helps, the current workstation is an HP dc7900.
 
If I disable the system board interface, I get a kernel panic no matter how IPAPPEND is used, or if I don't use it.

---

### Post by vocoder42 on 2011-01-10
i'm having an issue where some clients don't boot either....was using Shuttle x27d clients and they work without issue - Shuttle no longer makes those so have 'upgraded' to Shuttle x35 and none of these will boot.  There were getting stuck on the splash screen, or right before it - disabling the splash screen shows the following info:

ipconfig: no devices to configure
/init: .: line 1: can't open /tmp/net-eth0.conf
3.498747 Kernel panic - not syncing: Attempted to kill init!
3.498819 Dumping ftrace buffer:
3.498874 (ftrace buffer empty)

any ideas???

I tried using the IPAPPEND option in pxelinux.cfg/default but doesn't seem to help

also, could it be that the ltsp-image doesn't have the correct network device driver? if this is the case, how do I add it? looks like its a Realtek RTL8191SE

edit: looks like that is the problem - the server is running Jaunty, which doesnt seem to support that network card.  I was sent this page, which looks good if you already have the module: [https://help.ubuntu.com/community/UbuntuLTSP/AddingModules](https://help.ubuntu.com/community/UbuntuLTSP/AddingModules)

but since the module isn't included with Jaunty, do I have any options (aside from upgrading to a more recent version like Lucid) ? Is there a way I can get the driver and somehow bundle it with my thin client image?

---

