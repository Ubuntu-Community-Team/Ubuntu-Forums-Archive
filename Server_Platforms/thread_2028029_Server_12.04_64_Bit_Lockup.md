---
title: "Server 12.04 64 Bit Lockup"
date: 2012-07-17
forum: Server Platforms
---

### Post by drakesword on 2012-07-17
So we have built us a workhorse/nas. Relevent Configuration:

Amd FX 4 core
32 GB ram ddr3 1600
Raid 5 (Controlled by ubuntu) made with 6x2 TB 7200 RPM Sata 3 drives
1 8gb thumbdrive as a boot key
Ubuntu 12.04 Server 64 bit
OpenSSHd installed

Problem:

Over the last few days we have gotten requests to handle a rediculious number of files (Over 1M at this point). My boss copied some files(414K ~16GB) mistakingly as root. So he issued a chmod command followed by a chown command (chmod a+rw folder/path/here -R && chown user:group folder/path/here -r). 

Shortly there after his ssh session ceased to respond. Within a minute the network share dropped as well (samba). 

At the time I was ssh'd in as well. I switched to the root user and attempted to locate the bad process. I entered ps aux. It generated a list of ~20 processes and failed to return (frozen) Ctrl-C, no response, ctrl-z no response. 

I hustled over to the server keyboard in hand where I was greeted by the login prompt (tty0). Entered username, entered password and no response. Switched to tty1 2 and 3 with simular results. 

Finally I considered it a loss and issued ctrl-alt delete. The terminal window responded with a system is going down for a reboot now. After 5 minutes (timed) it failed to procede. Left with 2 choices I issued a ctrl - alt - sysrq + B and the system instantly rebooted.

Now today a simular situation happened, except this time a co-worker issued a unrar command on a 5 gig archive before it died.

The only other time I have seen this sort of thing happen was on one of my desktops when I ran out of memory BUT there was entries in syslog and dmesg stating that. In both of these cases on the server there is no entry in the syslog or dmesg.

Does anyone have any idea what is going on here?

---

