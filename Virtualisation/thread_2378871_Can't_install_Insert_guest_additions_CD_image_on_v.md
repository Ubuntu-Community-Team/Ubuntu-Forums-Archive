---
title: "Can't install Insert guest additions CD image on virtualbox"
date: 2017-11-28
forum: Virtualisation
---

### Post by neovich on 2017-11-28
Hi!
I tried to install ubuntu on virtual box, download ubuntu 16.04 64bit from official site, 
installed it to virtualbox and started to install guest additions cd image, for turn on unitu 3d accelerator 
and I got this error [http://prntscr.com/hgc1i4](http://prntscr.com/hgc1i4)

What is wrong?

---

### Post by howefield on 2017-11-28
Thread moved to the "*Virtualisation*" forum.

---

### Post by ian-weisser on 2017-11-28
It's difficult to say without seeing the log.
Re-read the error messages, and locate that logfile. Post it here.

---

### Post by vasa1 on 2017-11-28
> **neovich said:**
> ...
What is wrong?
You can just copy paste terminal output here between code tags. Pointing to image-hosting sites loaded with trackers and ads isn't such a good idea. If you really need to include an image, use the forum's attachment facility (the paper clip icon).

---

### Post by neovich on 2017-11-28
> **vasa1 said:**
> You can just copy paste terminal output here between code tags. Pointing to image-hosting sites loaded with trackers and ads isn't such a good idea. If you really need to include an image, use the forum's attachment facility (the paper clip icon).
don't understand what you mean.

> [COLOR=#000000]It's difficult to say without seeing the log.[/COLOR]
[COLOR=#000000]Re-read the error messages, and locate that log file. Post it here.[/COLOR]
There this error [http://prntscr.com/hgec99](http://prntscr.com/hgec99)
**ERROR: Kernel configuration is invalid ****include/generated/autoconf.h or include/config/au$ ****Run 'make oldconfig && make prepare' on kernel sr$**


I used this guide [https://www.linuxbabe.com/virtualbox/speed-up-ubuntu-virtualbox](https://www.linuxbabe.com/virtualbox/speed-up-ubuntu-virtualbox) and it didn't help
my 3d accelerator doesn't work, 
tried use $ sudo m-a prepare, this command can't create links. 

3d accelerator doesn't work, ubuntu very slow work on virtualbox.

I read on site virtual box, v 2.2.2 has problem with [COLOR=#000000][FONT=Verdana]The Guest Additions image, will install v 2.1.3[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-11-28
It looks to me as though you have not yet added yourself to the group **vboxsf** in your guest OS.

Can we assume you are using VBox version 5.2, which I did not find as stable as 5.1 and had some problems with some of my guest OSs not running full screen, even with the suggested version of the guest additions ISO added.

I uninstalled VBox-5.2 and reinstalled VBox-5.1 and it works with no problems of any kind.
Perhaps worth a try?

---

