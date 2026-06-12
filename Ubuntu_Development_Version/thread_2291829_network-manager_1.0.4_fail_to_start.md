---
title: "network-manager 1.0.4 fail to start"
date: 2015-08-23
forum: Ubuntu Development Version
---

### Post by dino99 on 2015-08-23
After getting the new 1.0.4 network-manager package, i cant get it starting after a cold reboot, both with systemd or upstart boot.
But downgrading to the previous 0.9.10.0 version resolve the issue. This is with wily i386 on gnome-shell session.

---

### Post by flocculant on 2015-08-23
You could I suppose report it as a bug - but as it's not made it out of -proposed yet, I guess they know there are issues with it. Though on the other hand - there's not actually anything wrong with that until it is out of -proposed.

---

### Post by rrnbtter on 2015-08-23
Greetings,
 It is trying to install the gnome network manager instead of the Unity network manager.  After purging network-manager-gnome with "sudo apt-get remove network-manager" , I had to do this "sudo apt-get install network-manager_0.9.10.0-4ubuntu23_i386.deb
".
It is still showing a network upgrade which I declined for now.

---

### Post by dino99 on 2015-08-26
> **flocculant said:**
> You could I suppose report it as a bug - but as it's not made it out of -proposed yet, I guess they know there are issues with it. Though on the other hand - there's not actually anything wrong with that until it is out of -proposed.

bug lp:1489154

---

### Post by syntaxerror74 on 2015-08-28
Yes, let that be a **big warning** to you guys to keep from 1.0.4 for the time being!!!
Yes, this is serious. Otherwise you won't even be able to find out about the issue on-line, since you plainly and simply won't be able to access the internet any more.

I could really have saved me half a day with this issue, had I known that "nm-connection-manager" was NOT at fault!! I wondered for quite a long time why it displayed none of my pre-set connections at all, but the actual reason was that NM was not running (because it crashed before and I didn't know about that until checking /var/log/*.crash )!! Sheesh, what a broken piece of cr@p they've made out of NM since v1.x...

Due to APT's habit of accessing the internet whenever it can, downgrading via *apt-get* when offline is normally a bloody hard thing to do (already been using bootable rescue CDs with an external flash drive connected I could save the .deb package file to), but in this case it is really enough to just downgrade NM by hitting in a *sudo dpkg -i*, using the .deb file in **/var/cache/apt/archives**. This was a life-saver for me.

---

### Post by dino99 on 2015-09-10
Got the new 1.0.4-0ubuntu3 version (proposed), and its works now :p

---

### Post by 3vi1 on 2015-09-12
> **dino99 said:**
> Got the new 1.0.4-0ubuntu3 version (proposed), and its works now :p

Got the new version yesterday, took the default option (not to replace config), and ended up with a completely borked network manager.

I had to downgrade, then re-upgrade (which seemed to replace config without asking the second time), to get it working.

Now here's the fun part:  NetworkManager has been using *18%* of a CPU (sometimes as high as 28%) ever since the upgrade.... and I'm pretty sure I completely rebooted right afterward.  :(

*Edit*:  Found the issue.  The updated versions hated a config line I had added to /etc/NetworkManager/dnsmasq.d/lan, so dnsmasq was constantly being restarted (and failing) by NetworkManager.

---

### Post by wgarcia on 2015-09-15
I upgraded today to the new version, accepted the new configuration files, and when I restarted the computer network-manager did not crash but was not connecting to my LAN. 

I went to /etc/NetworkManager/ and in NetworkManager.conf I changed "managed" from false to true, and after restarting network manager I got my network connection back.

---

