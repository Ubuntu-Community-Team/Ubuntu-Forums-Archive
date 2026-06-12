---
title: "Ubuntu server 12.04 Booting to blank screen."
date: 2014-01-10
forum: Server Platforms
---

### Post by adam17 on 2014-01-10
Hi,

I have a dell precision 690 which I am trying to install ubuntu server on to host a website.

However after installing and setup all the opperating systems bits and the reboot after the cd is remover the tower wont boot, it runs the bios and starts to boot then the screen goes black and switches off and thats it. I have another Dell Precision in my loft as a media server but this one goes black for a few seconds then comes up with the server loging details.

Does anybody know what could be causing this? I am tearing my hair out!

Thanks in advance

Adam

---

### Post by Kirk Schnable on 2014-01-11
A potential troubleshooting step for you might be to boot to a live CD, mount your hard drive, and look at the logs in /var/log, particularly /var/log/syslog, /var/log/dmesg, and /var/log/messages.  There, maybe you will find something to shed light on your problem.  The log files will start when the system boots, and end when you shut it off.  So, if anything insightful is being logged, you will be able to access that information from the live environment.  Remember that when you're on the live CD, it has its own /var/log.  You want to look at the /var/log on the hard drive, which will be where you mounted the drive (eg. /mnt/var/log, not /var/log).

Otherwise, take a moment to consider any possible differences in your configuration between the two servers.  Did you install from different media, is it running an older\newer version of Ubuntu, are there any hardware differences you might not have considered?

---

### Post by houstonbofh on 2014-01-11
Ubuntu is trying to go in to a hi res mode, and the display does not support it.  Try this...
[http://askubuntu.com/questions/127851/change-boot-screen-resolution](http://askubuntu.com/questions/127851/change-boot-screen-resolution)

---

