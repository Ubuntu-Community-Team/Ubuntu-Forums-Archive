---
title: "Network Problem post-Ubuntu update(VMware Workstation)"
date: 2008-02-12
forum: Virtualisation
---

### Post by mrb88 on 2008-02-12
I'm using 7.10 with the latest VMware Workstation. I just installed some updates from Ubuntu using the update manager (looked like kernel security updates). When I restarted my VPC, the little exclamation point next to my network icon indicated that it was no longer detecting my network (which I assume is part of the VMware tools drivers). I tried re-running the vmware tools configuration, to no avail. Ideas?

---

### Post by fjgaude on 2008-02-12
You likely have to run the config script, something like vmware-workstation-config.pl.

In the vmware server directly from vmware.com the script is vmware-config.pl. It may be the same in workstation, which should be in /usr/bin.

Happy hunting.

---

### Post by mrb88 on 2008-02-12
> **fjgaude said:**
> You likely have to run the config script, something like vmware-workstation-config.pl.

In the vmware server directly from vmware.com the script is vmware-config.pl. It may be the same in workstation, which should be in /usr/bin.

Happy hunting.
I did. Didn't work.

---

### Post by mrb88 on 2008-02-12
Tried uninstalling the package and starting from scratch. Still no success. Wondering if ubuntu has a detect-network-cards feature I could use to restore the network driver I was using before the one from VMware tools. The following is what I get to do after I ran the configuration (which didn't do much):

To use the vmxnet driver, restart networking using the following commands: 
/etc/init.d/networking stop
rmmod pcnet32
rmmod vmxnet
modprobe vmxnet
/etc/init.d/networking start

---

### Post by fjgaude on 2008-02-13
Interesting... but I don't have a clue as to what might be at issue.

I suppose you have network connection in Ubuntu host?

---

### Post by esj on 2008-02-13
I'm sorry but you have just tripped over one of the most terrific rat holes of the VMWare product line.  It has gotten so bad for me that I am considering ditching VMware for something else.  It has been a nightmare for myself and my customers.  The usual VMware response is "then don't upgrade your kernel".  As we all know, this is impractical and unrealistic.  Security fixes come out and we must upgrade and every time we upgrade, we break the VMware guest toolset.  My only advice is this:

When you boot your virtual machine, instead of activating the most recent kernel, use the last kernel that worked with the network.  Once you have connectivity again, verify that you have all of the kernel headers matching the latest kernel installed.  You reboot again, selecting the most recent kernel then you go through the whole installation process all over again.  Be double sure you are using the right version of the VMware tools, i.e. the ones that match your VMware players/server/workstation.

I swear to God, this particular rathole has caused me no end of lost hours and I am so sick of it.

---

### Post by mrb88 on 2008-02-13
I don't have another kernel I can load - it seemed like some kind of kernel-level security patch.

I have the most up-to-date VMware workstation and VMware tools. I guess I'll just re-install Ubuntu. Ugh.

---

### Post by osman s borutecene on 2008-02-13
I can confirm that the latest kernel update has some problems. My network has gone after the update too. I am not on a virtual machine. This is a native Gutsy Gibbon installation.

I can say that the problem is not vmware related.

---

### Post by blwarburton on 2008-02-19
Same problem here (network stops working) after updating Ubuntu 7.10.

I tried this on 2 PC's - one running Win2K another on WinXP.
Both running VMWare Workstation 6.0.2

VM created with NAT network defined. Installaion of Ubuntu goes ok and VMWare-Tools are compiled and install ok - network is working.
After updating, Ubuntu complains about the proprietry VMWare network driver and appears to replace it.

This problem doesn't effect Ubuntu 7.04

---

### Post by DChamp on 2008-02-19
First time post, be gentle.

Same problem here.
Have VMWare 6.0.2, Ubuntu 7.10 Gutsy Gibbon, ran fine.
Installed VMWare tools, worked fine.

This morning, Ubuntu wanted to run some updates, so stupidly I said yes. When it rebooted, no network.
Tried the DHCP trick, didn't work.

Had to do the ifconfig eth0 up trick
then the dhclient

BUT, I have to do this every time I bring up Ubuntu! Not fun.

Seeing as I'm VERY new to Ubuntu (and any form of Linux), this should be interesting.. *chuckling*

---

### Post by mrb88 on 2008-02-22
Wow.

Doing sudo ifconfig eth0 up and then sudo dhclient made my internet go back up. Is there a more permanent solution so I don't have to keep doing that?

---

### Post by yao_man on 2008-02-22
I had the same problem and ran sudo ifconfig eth0 up and sudo dhclient in my console but am still unable to connect to the internet via bridged, NAT, or any of the possible connections. I am VERY new to Linux and Ubuntu so I may be doing something wrong.

Also, I am using a wireless NETGEAR wg311T card if that makes any difference.

[CENTER]-----------------------------------------------------------------------------------------[/CENTER]

I did something with my virtual computer and it now connects via NAT automatically when I boot. It may contain unnecessary steps, but it worked and I am connected, hopefully it helps.

(in the console) sudo /usr/bin/vmware-uninstall-tools.pl
Wait a second for everything to be uninstalled
Re-install VMwareTools following the directions [here]("http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/")
Restart the virtualPC
(in the console) sudo ifconfig eth0 up
(in the console) sudo dhclient
Restart the virtualPC

Once it booted up after I restarted the second time, my network connected from the beginning and everything has worked fine up until now.

---

### Post by Active Listener on 2008-02-22
I have also reinstalled VMware Tools and my network is now back online.  I did not have to do the 
 - sudo ifconfig eth0 up
 - sudo dhclient
After my restart everything came back up.

---

### Post by yao_man on 2008-02-23
As I said, may have included unnecessary steps, but I simply posted what I did before it worked. Anyway, glad to help. 

PS If anyone knows how to create a bridged internet connection on a Ubuntu virtualPC please let me know.

---

### Post by mrb88 on 2008-02-24
I don't have a /usr/bin/vmware-uninstall-tools.pl

---

### Post by blwarburton on 2008-02-25
I did a fresh install of 7.10 (running under VMWare Workstation 6.0.2) and then installed the VMWare tools - networking running in bridged mode.
Then installed the linux-kernel-2.6.22-14 update and network stopped working.
Then re-installed the VMWare tools again and the network started after a reboot.

---

### Post by bhyman on 2008-02-26
This should be a sticky post...  :KS

I had same problem, found this thread in the archives, all is well now.  

[http://ubuntuforums.org/archive/index.php/t-574427.html](http://ubuntuforums.org/archive/index.php/t-574427.html)

I am using a bridged wireless connection on /dev/vmnet2 now, and I get my own IP and can see the rest of the LAN.  Brilliant stuff.  It is important that you create two bridged connections during the network wizard part of the install process, one mapping from eth0 to /dev/vmnet0 for the wired connection and a mapping from eth1(or whatever it is on your system) to /dev/vmnet2 for wireless. 

I am running Gutsy Gibbon and VMWare Workstation 6.0.2 build-59824.

Good luck.

---

### Post by iceman2k3 on 2011-05-03
Hi,
I've got the same problem with my ubuntu 11.04

sudo vmware-modconfig --console --install-all

fix it for me.

for sharefolder, it's seem that the update disable it by default.

Regards

iceman2k!

---

