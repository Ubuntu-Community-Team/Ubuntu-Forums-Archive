---
title: "Ubuntu 13.04 won't boot after yesterday's updates (03/13/13)"
date: 2013-03-14
forum: Ubuntu Development Version
---

### Post by jrivera86 on 2013-03-14
[COLOR=#333333][FONT=Ubuntu Beta]After daily updates, the system won't boot onto Ubuntu. This is a dual-boot machine and it was working fine. I already tried re installing Grub and repairs using Boot-Repair. Your help is appreciated. I get the following message:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]-Missing Modules (cat /proc/modules; ls /dev)
 Alert! /dev/disk/by-uuid/5fd6f7a1-9e3c-438d-ad0b-332c29463c92 does not exist.
 Dropping to a shell![/FONT][/COLOR]

---

### Post by schragge on 2013-03-14
So, what would the commands suggested in the error message show?
```

cat /proc/modules|more
ls /dev

```

The last update probably installed new kernel. Try to boot Ubuntu with the previous kernel: [uhelp]community/Grub2/Submenus[/uhelp]

---

### Post by Harry33 on 2013-03-14
> **jrivera86 said:**
> [COLOR=#333333][FONT=Ubuntu Beta]After daily updates, the system won't boot onto Ubuntu. This is a dual-boot machine and it was working fine. I already tried re installing Grub and repairs using Boot-Repair. Your help is appreciated. I get the following message:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]-Missing Modules (cat /proc/modules; ls /dev)
 Alert! /dev/disk/by-uuid/5fd6f7a1-9e3c-438d-ad0b-332c29463c92 does not exist.
 Dropping to a shell![/FONT][/COLOR]

You have enabled the proposed repository in RR. That is not recommended.
Anyways, after your system drops to busybox shell, just type exit and hit enter, your system will then boot.
This is an initramfs-tools issue.
Fortunately there is a fixed update in RR-proposed repo already (version 0.103ubuntu0.7).
So, go and upgrade initramfs-tools and your setup is fine.

---

### Post by jrivera86 on 2013-03-14
Thanks for the quick reply...I also think it installed a new Kernel...tried it already, but the funny thing is that the Grub menu doesn't show that option anymore...it just gives me 2 options, generic (which did not work) and if I go into recovery mode it simply hangs at USB devices and won't do anything else.

---

### Post by serdotlinecho on 2013-03-14
Similar [thread]("http://ubuntuforums.org/showthread.php?t=2125269").

---

### Post by jrivera86 on 2013-03-14
Thanks for the tip! I will do it today when I get home and reply with the outcome.

---

### Post by grahammechanical on 2013-03-14
Someone posted about this issue yesterday and said that the work around was to type exit and press enter. It works. This happened to me yesterday and when I booted just now but exit at the Busybox prompt gets us to a desktop. There were some updates to initramifs (I think) in today's updates. I have not rebooted. So, I cannot say if the updates fixes things. 


Update: Rebooted = bug fixed. Well done - whoever!

Regards.

---

### Post by mdalacu on 2013-03-14
For me , the fix does nothing. I have changed the repos to the main server and upgraded.
Also, the exit command just drops again in busybox. 
/dev/by-uuid only shows the dvd unit, no hdds(it should be 2 of them).
If in grub i choose the kernel from Oneric, all is working fine.
Can i install an older version of 3.8 kernel or initramfs tools?
What else i can do?
Thank you very much.

---

### Post by zika on 2013-03-14
> **mdalacu said:**
> For me , the fix does nothing. I have changed the repos to the main server and upgraded.
Also, the exit command just drops again in busybox. 
/dev/by-uuid only shows the dvd unit, no hdds(it should be 2 of them).
If in grub i choose the kernel from Oneric, all is working fine.
Can i install an older version of 3.8 kernel or initramfs tools?
What else i can do?
Thank you very much.Are You sure You're running with newest kernel? I ask this because in upgrade process only newest kernel gets update-initramfs treatment... Of course, You could run```
sudo update-initramfs -ck all
```to treat them all...

---

### Post by mdalacu on 2013-03-14
Yes, i am sure, this is the file
-rw-r--r-- 1 root root 30940281 Mar 14 18:46 initrd.img-3.8.0-12-generic
the one from 3.5 is this
-rw-r--r-- 1 root root 30011005 Mar 13 22:40 initrd.img-3.5.0-26-generic
I am afraid to rebuild the 3.5 one, should i run your command? Or should i try something else?
Thank you.

---

### Post by mdalacu on 2013-03-14
Update.
I have run this 
> sudo update-initramfs -c -k 3.8.0-12-generic 
and i got this:
> -rw-r--r-- 1 root root 30940063 Mar 14 19:16 initrd.img-3.8.0-12-generic
Different file size, why is that? I will try to reboot...


UPDATE:
No luck, it still drops to busybox and exit does not work.
What else?

Thank you

---

### Post by zika on 2013-03-14
> **mdalacu said:**
> Yes, i am sure, this is the file
-rw-r--r-- 1 root root 30940281 Mar 14 18:46 initrd.img-3.8.0-12-generic
the one from 3.5 is this
-rw-r--r-- 1 root root 30011005 Mar 13 22:40 initrd.img-3.5.0-26-generic
I am afraid to rebuild the 3.5 one, should i run your command? Or should i try something else?
Thank you.Decision is totally Yours... Never trust anyone... Except yourself... ;)
These are only files, You could always keep backup, You could always enete via chroot... Keep LiveCD handy...

---

### Post by mdalacu on 2013-03-14
How can i install an older kernel version, let's say 3.8.0-11-generic or something like this?
I am running out of ideas...
Thank you.

---

### Post by dino99 on 2013-03-14
synaptic is your friend  :p install it if not already done.

---

### Post by mdalacu on 2013-03-14
I think this bug affects me. I hope that it will be fixed soon.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1154800](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1154800)

---

### Post by jrivera86 on 2013-03-15
Harry33 thank you so much...it worked!

---

### Post by mdalacu on 2013-03-15
I think the problem is bigger because i have downloaded the latest dayly build and booted off the cd. The installer and also "Try Ubuntu" don't see any of my hdds. No devices under /dev/sd*, only the CD Drive.
With kernel 3.5.0.26 i have no such problems!
The MB it is an "Asrock 890FX Deluxe 4", AMD 890FX chipset.

---

