---
title: "Virtualbox stops responding after installation"
date: 2013-12-14
forum: Virtualisation
---

### Post by soeren.mehnert on 2013-12-14
Hey guys,

hope you can help me, ive been having some problems with installing Ubuntu 13.10 through my virtualbox.
Everything runs smoothly until the installation finishes and it asks for a reboot. If i click it, the virtualbox stops responding, and i have to start the installation all over again. ive tried reseting the virtualbox instead of clicking 'restart now', nothing helps, always the same result.

Ive tried it both on windows 7(32bit) and windows 8.1(64bit), ive even tried an older version of Oracles virtualbox.
Ive tried older Ubuntu versions and even openSUSE, always with the same result.
I enabled virtulization in the BIOS and everything, even gave it about 3gb of RAM and about 50gb hard drive.

Please help... this problem is getting quiet annoying actually...
Thanks so much!

---

### Post by brian.joe.kelley on 2013-12-14
It's got nothing to do with the Ubuntu 13.10, because as you say, you had tried other versions of linux with the same result.
I bet you have a mismatch in the Oracle Virtual box software architecture chosen for your CPU.
In other words,  you're mentioning Win 7 (32bit) and then Win 8 (64bit).  You're kind of all over the place.
Do this, 
Windows start menu-> type in white field misnfo32 -> hit ok-> look for system type under system information. It it x64 based pc or x32?
Deinstall virtual box completely. reboot. Choose appropriate Oracle virtual box architecture. Download and intall.  Make sure you download and install Virtual box extension pack.
Then create your machine, install Ubuntu and see what happens.
Capiche?

---

### Post by soeren.mehnert on 2013-12-15
When i say ive tried it on windows 7 and 8, I'm talking about different computers.
tried what you said and it didn't work...

---

### Post by jackdalton00 on 2013-12-15
This probably won't work, and you have to transfer all your VB OS's over, but have you tried running VirtualBox as root?
```
gksudo Virtualbox
```

---

### Post by ajbozdar on 2013-12-18
Try VMware. I have installed Ubuntu 12.04 LTS using VMware, providing 1GB of RAM. I have Windows 8. It was quite slower, but It worked. It could connect to network as well. Give a try to VMware, it has a free version as well. I never tried VirtualBox myself but I think it is not simple compare to VMware. Best Wises!

---

### Post by QIII on 2013-12-18
Using VMWare doesn't solve the problem.

Try starting VirtualBox from the terminal WITHOUT gksudo.

```
virtualbox
```

When it fails, see if you get error messages in the terminal and paste them back here between code tags (see my Sig for that).

---

### Post by ajbozdar on 2013-12-19
> **QIII said:**
> Using VMWare doesn't solve the problem.

Try starting VirtualBox from the terminal WITHOUT gksudo. 

May I know why VMware will not solve the problem? Do you mean [COLOR=#ff0000]gksudo[/COLOR] is creating problem for Ubuntu to reboot?

Many Thanks. :)

---

### Post by VMC on 2013-12-19
> **ajbozdar said:**
> May I know why VMware will not solve the problem? Do you mean [COLOR=#ff0000]gksudo[/COLOR] is creating problem for Ubuntu to reboot?

Many Thanks. :)

The topic is Virtualbox and suggesting VMware is going in another direction.

---

### Post by QIII on 2013-12-19
And gksudo is unnecessary because the user should be able to run VirtualBox without elevated priviledges.  If there is a privilege issue, using gksudo will mask the problem.

---

### Post by ajbozdar on 2013-12-24
> **VMC said:**
> The topic is Virtualbox and suggesting VMware is going in another direction.

I understand. :) Is it necessary to stick on something if there is alternative?

---

### Post by ajbozdar on 2013-12-24
> **QIII said:**
> And gksudo is unnecessary because the user should be able to run VirtualBox without elevated priviledges.  If there is a privilege issue, using gksudo will mask the problem.

Thank you very much. I got the point. :)

---

### Post by plurga on 2013-12-24
i hope this link can help u 

[http://forums.opensuse.org/english/get-technical-help-here/virtualization/483397-virtualbox-stops-working-after-reboot.html](http://forums.opensuse.org/english/get-technical-help-here/virtualization/483397-virtualbox-stops-working-after-reboot.html)

---

