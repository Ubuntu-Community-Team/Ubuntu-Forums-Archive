---
title: "High load average but idle CPU?"
date: 2010-11-26
forum: Server Platforms
---

### Post by thefirstM on 2010-11-26
I am having a problem with the server that I use to host my personal site.  The load average quite often spikes to exceed 1.00 for the 1 and 5 minute intervals, and the 15 minute interval gets above .5.  This occurs while the server is idle, serving very few or no requests and with the CPU 99% idle with <1% IOWAIT usage.  I have checked top and vmstat, but neither one provides any useful info.  Top continues to say the CPU is 99% idle, and vmstat says that there are 0 runnable and 0 blocking tasks.  Occasionally, vmstat will say that there is 1 runnable task, but this doesn't even coincide with the load average spikes.  I have already searched for other solutions to this problem, but everything I have seen says to use top and/or vmstat, but those aren't showing anything out of the ordinary.  Can anyone recommend anything else I might do?

My server has a Pentium 4 HT 3gHz processor, 2GB RAM, and runs Kubuntu 10.10.  (The reason it runs Kubuntu instead of Ubuntu Server is that it needs an X environment so that the Nvidia driver can initialize and put its graphics card into a power saving mode.)

---

### Post by jaakan on 2010-11-26
What type of website are you running? Static content : Apache just html file, or dynamic Tomcat/jboss java based, Php based, database driven content etc...

you should have htop and iotop install

what is htop showing when your system is on high load? 

Do you have a lot of logging turned on? what else is running on this box?

---

### Post by thefirstM on 2010-11-26
htop shows basically the same thing as top, that the system is basically idle.  iotop shows occasional disk usage by a few different processes like Apache and mysql, but none of these coincide with the load spikes.

The server is running a personal website/blog based on Drupal.  It gets very little traffic though, and the Apache log does not show any abnormal activity (usually no activity at all) when the load spikes occur.  The server is also running Dovecot and Postfix for email, but mail.log also doesn't show any activity before/during the load spikes.  One thing out-of-the-ordinary that I have noticed is that the byte counters for the NIC say that many,many more bytes have been downloaded that uploaded.  This is the opposite of what I would expect for a server, but I can't find where the network IO is coming from.

---

### Post by jaakan on 2010-11-26
> **thefirstM said:**
>   One thing out-of-the-ordinary that I have noticed is that the byte counters for the NIC say that many,many more bytes have been downloaded that uploaded.  This is the opposite of what I would expect for a server, but I can't find where the network IO is coming from.

netstat -a  / should give you the  current state of connections to your server it may or may not even help

if you running the gui on this box install and run wireshark so you can sniff the traffic, start capture on the web facing interface.

you might be getting attacked

---

### Post by thefirstM on 2010-11-26
netstat shows just the connections I made to the server at the time and a few listening ports.  I don't think I am getting attacked.

---

### Post by jaakan on 2010-11-26
> **thefirstM said:**
> netstat shows just the connections I made to the server at the time and a few listening ports.  I don't think I am getting attacked.

I saw other posts related to a php high load bug It could be that you should look on launchpad.net

---

### Post by thefirstM on 2010-11-30
I figured out what the problem is.  I was looking at the output of "cat /proc/interrupts" and I noticed that IRQ 16 (with "nvidia" on it) had many more interrupts than any other channel in the system.  I clocked it at approximately 60 IRQs/sec and determined that it must be due to the video card firing an IRQ for vsync.  Then, I found that you can disable this for 2D mode on Nvidia cards by adding "    Option         "OnDemandVBlankInterrupts" "True" to the Device section of the xorg.conf.  After I did this, the load averaged dropped to below 0.10.

---

### Post by Vegan on 2010-11-30
Check the BIOS and make sure no IRQ is assigned to the video card. Reboot and see how it looks.

---

### Post by thefirstM on 2010-11-30
But I already fixed it.  And if no IRQ was assigned to the video card, then the driver would not be able to load.  Also, I can't access the BIOS because the server is headless.

---

