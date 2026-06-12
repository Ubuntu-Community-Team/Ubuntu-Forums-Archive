---
title: "Recovery Mode"
date: 2015-08-06
forum: Ubuntu Development Version
---

### Post by flocculant on 2015-08-06
Can people have a look at recovery mode and try and get a root shell from it. 

I'm seeing a prompt for root password ... 

[lpbug]1481904[/lpbug]

---

### Post by QDR06VV9 on 2015-08-06
You forgot to say Please.=;(you know that was a joke)
Working fine here. DE Mate.
Kind Regards
Forgot to mention I am using Upstart && not Systemd
Have you yet tried "[COLOR=#333333]init=/lib/systemd/systemd systemd.unit=emergency.service"[/COLOR]

---

### Post by howefield on 2015-08-07
Ubuntu 64 bit freshly updated, no issues for me getting to a root shell from recovery mode.

---

### Post by sudodus on 2015-08-07
> **flocculant said:**
> Can people have a look at recovery mode and try and get a root shell from it. 

I'm seeing a prompt for root password ... 

[lpbug]1481904[/lpbug]

I understand that you are running Xubuntu Wily 64-bit

> ***Install not encrypted.***

Image attached (excuse the flash)

ProblemType: Bug
DistroRelease: Ubuntu 15.10
Package: friendly-recovery 0.2.31
ProcVersionSignature: Ubuntu 4.1.0-3.3-generic 4.1.3
Uname: Linux 4.1.0-3-generic x86_64
ApportVersion: 2.18-0ubuntu5
Architecture: amd64
CurrentDesktop: XFCE
Date: Wed Aug 5 21:28:24 2015
InstallationDate: Installed on 2015-05-12 (85 days ago)
InstallationMedia: Xubuntu 15.10 "Wily Werewolf" - Alpha amd64 (20150512)


I tried with an installed Xubuntu Wily 64-bit (today's daily), and I see no prompt for root password. I get into the root prompt # at once and can run commands (but the frame around the menu where I select root is ugly (maybe some UTF-8 incompatibility or similar font problem)).

Maybe you should wipe your 85 days old Wily system and start from the beginning from a fresh daily iso file.

---

### Post by flocculant on 2015-08-07
>  Maybe you should wipe your 85 days old Wily system and start from the beginning from a fresh daily iso file.  noooooooooooooooooooooooooooooooo ... :p

I'll check out with a new one - if it *is* the poor old things age and the obvious fiddling and mucking about then that's all good.

> **howefield said:**
> Ubuntu 64 bit freshly updated, no issues for me getting to a root shell from recovery mode. Thanks for checking :)

---

### Post by mc4man on 2015-08-07
Bootup > recovery > root shell 'works' here, no password prompt but the fs is read only so no point really.
Bootup > recovery > fsck (mounts read/write) > root shell still no password prompt, can write.

---

### Post by flocculant on 2015-08-08
> **mc4man said:**
> Bootup > recovery > root shell 'works' here, no password prompt but the fs is read only so no point really.
Bootup > recovery > fsck (mounts read/write) > root shell still no password prompt, can write.


Yes - I know :)

I'd done other things prior to wanting the shell so it would have been fine.

Anyway - seems like just one of those dev install kicking around for ages things.

---

