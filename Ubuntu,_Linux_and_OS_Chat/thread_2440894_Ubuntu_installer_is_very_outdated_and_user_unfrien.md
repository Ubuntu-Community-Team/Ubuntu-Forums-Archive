---
title: "Ubuntu installer is very outdated and user unfriendly"
date: 2020-04-16
forum: Ubuntu, Linux and OS Chat
---

### Post by peter1897 on 2020-04-16
If you select custom installation creating partitions is not straightforward and it's confusing, and encrypting the swap partition is practically impossible. Please, improve the installer, or integrate better and simple installer, like Calamares.

---

### Post by coffeecat on 2020-04-16
> **peter1897 said:**
>  Please, improve the installer, 

Since you've been a member of this forum for nigh on 7 years, I'm sure you know that the membership consists of end-users, who are not responsible for the design or development of Ubuntu.

Do you have a question? You posted in a support section.

---

### Post by peter1897 on 2020-04-16
> **coffeecat said:**
> 
Do you have a question?

If you mean a specific question, i want to know how to encrypt the swap partition during installation?

---

### Post by CelticWarrior on 2020-04-16
Do you need a swap partition - reuiored only for hibernation - or do judt think you need one? You don't, since several releases ago, a swapfile is used by default instead.

---

### Post by peter1897 on 2020-04-16
> **CelticWarrior said:**
> Do you need a swap partition - reuiored only for hibernation - or do judt think you need one? You don't, since several releases ago, a swapfile is used by default instead.

So, you are saying it's not possible to encrypt swap partition during installation?

---

### Post by CelticWarrior on 2020-04-16
No, I was asking if you really need it. Do you?

---

### Post by peter1897 on 2020-04-16
Yes, i may need hibernation.

---

### Post by VeloxNeb on 2020-04-16
your original request for a "better" installer like calamares would actually be a step backwards: 

ubiquity is accessible (making ubuntu one of the few fully (!) accessible distros) and calamares isn't.  
this actually makes calamares (quote:) "very outdated and user unfriendly" and ubuntu's installer better, more up to date and user friendly.

---

### Post by QIII on 2020-04-16
This thread started as a gripe about the installer.

Moved to Ubuntu, Linux and OS Chat.  As it is now in a Chat area, it is no longer appropriate as a support thread.  Please start a support thread with swap question.

---

### Post by peter1897 on 2020-04-17
> **VeloxNeb said:**
> your original request for a "better" installer like calamares would actually be a step backwards: 

ubiquity is accessible (making ubuntu one of the few fully (!) accessible distros) and calamares isn't.  
this actually makes calamares (quote:) "very outdated and user unfriendly" and ubuntu's installer better, more up to date and user friendly.

Ubuntu installer might be used on more distros, but there is no way it's more user friendly than Calamares installer.

---

### Post by Tadaen_Sylvermane on 2020-04-17
This could be narrowed down to the same argument that people have between Windows or Linux. At the end of the day they both work great, just differently. Same with installers. I have never tried encrypting swap on installation but it may be such a niche case that they didn't bother adding it to the installer. I can say I've never heard a gripe about encrypting swap on installation before today, especially when it's so easy to do after the fact. That doesn't mean it's any more or less than anything else, Calamares in this case. They can't plan for every single possibility. They have to aim for the majority of their target audience, and I would venture that most of their target audience doesn't or has never even requested that feature.

---

### Post by Hwæt on 2020-04-20
I might offer that a swap partition is wholly unnecessary if you're using an SSD. In fact, it will lower the lifetime of your SSD if you have one.

This is probably a big reason why the installer doesn't really support it. Hard disks have largely been sidelined by cheaper and cheaper SSDs.

---

### Post by poorguy on 2020-04-21
> **peter1897 said:**
> If you select custom installation creating partitions is not straightforward and it's confusing, and encrypting the swap partition is practically impossible.


Perhaps these will help.

[https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/](https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/)

[https://fossbytes.com/ubuntu-18-04-lts-18-10-installation-guide/](https://fossbytes.com/ubuntu-18-04-lts-18-10-installation-guide/)

---

### Post by guiverc on 2020-04-21
> **peter1897 said:**
> Ubuntu installer might be used on more distros, but there is no way it's more user friendly than Calamares installer.

I do like `calamares`, however it's far from perfect. Lubuntu uses it as their installer (has since 18.10), and as such I've seen various issues we have using `calamares` that `ubiquity` used by other flavors of Ubuntu have not encountered.

Yes visually I do like `calamares`, but given for my own installs I always use "*Something else*" (`ubiquity`) or "*Manual Partitioning*" (`calamares`), I find almost no difference between them.

Also with the skins (eg. I think the skin on `ubiquity` used by Kubuntu makes it looks very close to `calamares` and I've seen a number of reviewers mistakenly think it is `calamares`) makes the difference somewhat moot anyway.

I like `calamares`, but every piece of software has advantages and disadvantages when compared with other software, and personally I'm too aware of flaws our team (Lubuntu) are currently having with `calamares`.

ps:  if you have a floppy drive on any of your systems, I'd love for you to confirm a bug with `calamares` for me, so I can file it upstream!  (*I'm the only Lubuntu team member with machines old enough to still have floppy drives*)

---

### Post by MartyBuntu on 2020-04-21
Even accounting for wanting hibernation, why would anyone want to encrypt swap? It's volatile storage.

---

### Post by hk42 on 2020-04-22
> **MartyBuntu said:**
> Even accounting for wanting hibernation, why would anyone want to encrypt swap? It's volatile storage.

+1
And if such a special case was to be taken into account on the installer it would render it very complex and out of reach for
the majority of Ubuntu users.
The success of Ubuntu is mainly due to it's installation being quite user friendly.

---

### Post by TheFu on 2020-04-22
Ubuntu Server Installer last minute changes for 20.04 to better support RAID during installs: [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-2004-Subiquity-Multi-ESP](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-2004-Subiquity-Multi-ESP)

If you are encrypting swap, probably want to encrypt as much of the OS as possible.  Last time I installed a desktop ubuntu flavor, it had the option to encrypt the install and use LVM.  
This resulted in a setup like this: [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987) after some rework. Usually there's just a single huge root LV and swap LV inside the LUKS encrypted container, which doesn't work for my needs. My rework reduced the size of the root LV, enlarged the swap LV and added home and stuff LVs for ... home and stuff. ;) That was all done post-install.  

What installer is friendly really is a matter of opinion. Whatever people get used to will almost always be what they consider friendly.

---

