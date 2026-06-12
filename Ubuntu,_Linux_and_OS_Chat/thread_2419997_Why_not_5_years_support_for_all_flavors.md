---
title: "Why not 5 years support for all flavors ?"
date: 2019-05-28
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2019-05-28
I am using Lubuntu 18.04 and it will be supported for 3 years (2021) only.

Why not 5 years support for all flavors ?

---

### Post by PaulW2U on 2019-05-28
The flavour teams are very small. Some have as few as two developers who can fix bugs and upload fixes and updates to the archive. The flavour teams are unpaid volunteers and work on their chosen flavour in their spare time.  They simply don't have the resources to support LTS releases for five years.

---

### Post by linuxyogi on 2019-05-28
> **PaulW2U said:**
> The flavour teams are very small. Some have as few as two developers who can fix bugs and upload fixes and updates to the archive. The flavour teams are unpaid volunteers and work on their chosen flavour in their spare time.  They simply don't have the resources to support LTS releases for five years.

Point taken but Linux Mint is also a project maintained by unpaid volunteers abut they maintain all their flavors (Cinnamon/Mate/Xfce)  for full 5 years.

I used to be a distro hopper for a long time but now I just hate new installations.

After Lubuntu 18.04 reaches its eol I am planning to move to Centos.

---

### Post by PaulW2U on 2019-05-28
> **linuxyogi said:**
> Point taken but Linux Mint is also a project maintained by unpaid volunteers abut they maintain all their flavors (Cinnamon/Mate/Xfce)  for full 5 years.
I've never taken much interest in Linux MINT but a quick look at their version release history on Wikipedia suggests that they're not releasing a new version every six months like Ubuntu do. Linux MINT seems to be based only on Ubuntu LTS releases and any interim updates are based on Ubuntu LTS point releases.

Probably less work for Linux MINT developers compared to that of the Ubuntu flavour developers which means they have the resources to offer the full five years. :)

---

### Post by cruzer001 on 2019-05-28
Its not necessary to always play by the rules :)
> If you install Ubuntu server or mini, followed by LXDE/Lubuntu DE, then this is treated as a mainline install of which the DE is only another "app". Therefore, it will get 5 years support. Moreover, you can update it to the next LTS to start the whole 5-yr cycle again. So long as the devs feel that LXDE is worth supporting, it will also continue to show up on the repos. Therefore, this method can take you far beyond the end date of the strict Lubuntu flavour.

A loophole? Or a feature? Like beauty, I suppose it is in the eye of the beholder. 
[https://ubuntuforums.org/showthread.php?t=2418225&p=13861176#post13861176](https://ubuntuforums.org/showthread.php?t=2418225&p=13861176#post13861176)

---

### Post by PaulW2U on 2019-05-28
> **cruzer001 said:**
> [https://ubuntuforums.org/showthread.php?t=2418225&p=13861176#post13861176](https://ubuntuforums.org/showthread.php?t=2418225&p=13861176#post13861176)
Unfortunately there are some inaccuracies in that now closed thread. 

Every flavour of Ubuntu shares the same repositories. Flavour packages aren't removed after three years. Just because a package is still in the repositories doesn't mean it is still supported. If you want to run a supported system then it **is** best to play by the rules. :)

---

### Post by linuxyogi on 2019-05-28
Also, I read somewhere that the mini.iso doesn't support UEFI.

I don't know if that's still true.

---

### Post by yetimon_64 on 2019-05-28
> **linuxyogi said:**
> Also, I read somewhere that the mini.iso doesn't support UEFI.

I don't know if that's still true.

The standard mini installer doesn't support UEFI. But there are files included in it if extracted can create a USB installer which can install in UEFI mode. 

A guide for the procedure required to make the mini iso UEFI enabled is [[COLOR=#0000ff]--here--[/COLOR]]("https://www.onetransistor.eu/2015/12/install-ubuntu-minimal-cd-uefi-enabled.html").

I have done several mini.iso installs of 14.04 and 18.04 with UEFI enabled using that information. Though I must admit running into quite a bit of trouble on 18.04 and had to extract a file from an existing full 18.04 installation and include it in the new USB installer to get it working. A bit of a messy procedure, not particularly easy at times.

---

### Post by linuxyogi on 2019-05-28
@[**[COLOR=#000000]yetimon_64[/COLOR]**]("https://ubuntuforums.org/member.php?u=1969424")

Thanks for the info.

---

