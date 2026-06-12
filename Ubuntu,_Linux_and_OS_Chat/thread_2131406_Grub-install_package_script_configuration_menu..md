---
title: "Grub-install package script configuration menu."
date: 2013-04-01
forum: Ubuntu, Linux and OS Chat
---

### Post by nekoexmachina on 2013-04-01
Hello, forums.
Firstly, sorry for probably misleading thread name.
I am talking about the menu that pops up every time user get grub updates.
This menu writes for me "If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them."


In what universe should it be considered anyhow good idea? I mean, really, WTF? 
It is generally BAD idea in at least one case (mine):
It puts up a menu with choices:
a) My Windows partition (which I don't need, but anyway it would broke it hardly)
b) My USB HDD (WTF?!?!)
c) My Live-USB with not so Linux live system (even if it was linux, grub whould have broken those. )
d) My BSD partition (WTF*2, Grub would have broken those. If in liveUSB area USB probably could boot with GRUB, this one could defenetely not)
e) My Windows rescue partition (see a))

If there is a package (grml) which detects installed systems and configures grub to use those, should'nt the grub-installer be aware of it and give no disaster-recommendations?

"User-friendly"? No, it is not. User should learn if he wants to update his base system (e.g. like 'If you unsure, check your bios settings"), or he should call a guy who knows what he's doing.
Or is this some kind of ubuntu philosophy I don't get?

---

### Post by oldfred on 2013-04-01
Are you installing 10.04 or has this bug reappeared?

Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)
[https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1](https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1)

---

### Post by nekoexmachina on 2013-04-02
I'm seeing this with 13.04.
Should I reopen, post a screenshot or what?
Also this is reproduced not in GUI mode (I'm running apt-get upgrade via console and getting this in ncurses configuration menu).

---

### Post by oldfred on 2013-04-02
If you can do screen shots, I would document it.

I might file a new bug, & refer to old bug report. But if just description issues, we find that they are not good about fixing or considering text as a bug. Even if the text says delete your entire system, they do not think that is a bug as it is not in the code. If the code deletes your entire system they immediately will try to fix it.

 bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by grahammechanical on 2013-04-02
[COLOR=#000000]"If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them."

All of what? Partitions? Including your Windows partition? No. The MBR of drives. That is what is being suggested. And the package that detects installed systems is called os-prober and the package that configures Grub is called grub-mkconfig and the package that installs Grub into the MBR is called grub-install. They are all GNU Grub packages not Ubuntu packages. The command update-grub just executes a shell script that runs grub-mkconfig.

Regards.[/COLOR]

---

