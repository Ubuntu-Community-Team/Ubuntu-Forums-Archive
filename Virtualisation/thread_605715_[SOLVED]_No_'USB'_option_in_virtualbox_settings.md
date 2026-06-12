---
title: "[SOLVED] No 'USB' option in virtualbox settings"
date: 2007-11-07
forum: Virtualisation
---

### Post by viking777 on 2007-11-07
I've just started experimenting with virtualbox to run windows xp on kubuntu and everything has gone really well with one exception. I want to be able to access a usb pen drive  from the vm but I have no 'USB' section in the 'settings' menu. I have edited 'fstab' and 'rules.d-40permissions'as recommended I have made sure that I am in the vboxusers group, but I still have no 'USB' section so can't add devices. USB is obviously working because I have a usb mouse and keyboard and they both work, but nothing else. Incidentally there are no errors showing in the windows vm device manager.

Does anyone have any other ideas?

Forgot to say, I am already running the 'guest additions.iso'.

---

### Post by cenwesi on 2007-11-07
goto this link...
[http://ubuntuforums.org/showthread.php?t=588225](http://ubuntuforums.org/showthread.php?t=588225)

---

### Post by viking777 on 2007-11-07
> **cenwesi said:**
> goto this link...
[http://ubuntuforums.org/showthread.php?t=588225](http://ubuntuforums.org/showthread.php?t=588225)

Thanks for the reply, unfortunately this makes no difference to my particular problem, I have uncommented the lines in the file mentioned, rebooted, but I still have no USB section in the settings menu of my virtual machine and my usb key is still not recognised in the vm (although it is in ubuntu).

So the question is still open.

---

### Post by Delvien on 2007-11-07
If you are using Virtualbox OSE, there is no USB option.  

the Virtualbox PUEL ( Public user End license) has the USB option, check out their website to download the non - OSE.

EDIT: In order to install the full edition, you will have to uninstall the OSE first.

---

### Post by viking777 on 2007-11-07
> **Delvien said:**
> If you are using Virtualbox OSE, there is no USB option.  

the Virtualbox PUEL ( Public user End license) has the USB option, check out their website to download the non - OSE.

EDIT: In order to install the full edition, you will have to uninstall the OSE first.

Right, now this may well be the answer. I am using the ose version not the puel one.

One question though, I have spent an awful lot of time and effort into setting up my present vm. If I install another version does it mean that all that work is in vain, or will I still be able to boot my existing vm?

---

### Post by viking777 on 2007-11-07
> **Delvien said:**
> If you are using Virtualbox OSE, there is no USB option.  

the Virtualbox PUEL ( Public user End license) has the USB option, check out their website to download the non - OSE.

EDIT: In order to install the full edition, you will have to uninstall the OSE first.

Thank you a million million times over!!! 

I installed the puel version (after uninstalling the ose) and instantly I have complete connectivity.

How much work I could have saved myself if that had been made clearer earlier on today.

Still such is life, you learn from mistakes.

Did I say thank you?

In case not, 

Thank you.

(and again!!)

---

### Post by Delvien on 2007-11-07
> **viking777 said:**
> Thank you a million million times over!!! 

I installed the puel version (after uninstalling the ose) and instantly I have complete connectivity.

How much work I could have saved myself if that had been made clearer earlier on today.

Still such is life, you learn from mistakes.

Did I say thank you?

In case not, 

Thank you.

(and again!!)

Cheers 8-)

---

### Post by plasticM on 2010-01-12
Thank you for the explanation, although this little difference is quite annoying (why!!!).

I have the OSE because I just installed it from synaptic, and looking at the binaries download page on the virtualbox site I'm a little confused.  Can I install the PUEL with apt?  I dislike installing things manually because I'm quite new at all this, so I'm never sure where the appropriate place to install stuff is* and I lose track of what I've done.

*my confusion results from the fact that where Windows has a folder called "Program Files", linux has folders called "etc", and "opt" and "var" and stuff like that...??!

---

