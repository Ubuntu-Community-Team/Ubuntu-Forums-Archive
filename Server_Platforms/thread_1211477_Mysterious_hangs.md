---
title: "Mysterious hangs"
date: 2009-07-12
forum: Server Platforms
---

### Post by nordh on 2009-07-12
Hi all!

I have just upgraded to jaunty server edition on my file server and now it has started acting up on me. It hangs after a couple of hours running and I just can't seem to understand why.

So first of all, what do I mean when i state that the system is hanging?
I mean that it does not accept any input on existing SSH sessions, does not accept new SSH sessions, does not respond to keyboard input and the screen that was showing a logged in terminal a couple of hours earlier is pitch black (screen saver, i suppose). It might still accept forwarding of http(s) requests though (reverse proxy thingy), but I'm not sure...

What have I checked?
I've tried to check the logs but I don't find anything suspicious in any of the ones I've checked. I've checked /var/log/messages primarily but i tried to look through any that sounded plausible but perhaps I've configured things badly but some logs seem to be overwritten after a restart. Anyhow, /var/log/messages just looks like this:

```
Jul 11 17:13:48 frodo -- MARK --
Jul 11 17:33:48 frodo -- MARK --
Jul 11 18:29:31 frodo syslogd 1.5.0#5ubuntu3: restart.
```I have also  disabled a drive that I have suspected of beeing close to it's end of life.

The system is running from a partition on a brand new 1TB disk on an old VIA EPIA motherboard (can't remember exactly the type but it is with an 800MHz processor and not fanless) 256 MB RAM. I also use a Promise S-ATA controller for some of the drives, including the system drive.

Anyhow, I don't know what to look for to resolve this, all help i appreciated...

//nordh

---

### Post by kennedy7 on 2009-07-12
I have had this problem several times. It is probably because you have bad ram. Try using the "Memtest" option in the grub boot loader and see if that finds anything.
And also what is your server used for? does it get lots of high traffic?
Or it could be a filesystem error. Try running fsck in the recover options menu and see if it finds anything

---

### Post by dragos2 on 2009-07-13
If you want maximum stability do not perform release-upgrade.

Just an advice.

---

### Post by lavinog on 2009-07-27
I have the same mobo, but I am trying to use it as a desktop.
It hangs randomly when using a gui (even during the install it hung)
It works just fine in the recovery console.
i did find this post
[http://ubuntuforums.org/showthread.php?t=79395](http://ubuntuforums.org/showthread.php?t=79395)
edit: CONFIG_X86_LONGHAUL=Y in the kernel config, so I guess this means I have to recompile the kernel to turn this off?

I used to use this mobo as a linux server and hosted unreal tournament 2004 with it. I used dapper back then and I would get at least 6 months uptime with it.

Does your server load a gui by any chance?

Sometimes i got usb errors in my dmesg, but I think it had something to do with either the usb speakers or mouse. It still hangs though with everything disconnected.

---

### Post by dragos2 on 2009-07-27
Post
```

netstat -nat | wc

```

---

### Post by lavinog on 2009-07-30
adding notsc to the kernel options at boot seems to fixed the crashing on my epia. You may want to give that a try.

something to read:
[http://www.viaarena.com/displaydownload.aspx?PageID=1&DSCat=32&DCatType=3](http://www.viaarena.com/displaydownload.aspx?PageID=1&DSCat=32&DCatType=3)
> These documents describe how to turn on the Power Saver (previously known as &#8220;Longhaul&#8221;) 
...
An IDE lockup issue occurs on some VIA EPIA Mini-ITX mainboards when the Power Saver feature is enabled. 

bugreport:
[https://bugs.launchpad.net/ubuntu/+bug/398552](https://bugs.launchpad.net/ubuntu/+bug/398552)

---

