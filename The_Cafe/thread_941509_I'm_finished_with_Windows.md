---
title: "I'm finished with Windows"
date: 2008-10-08
forum: The Cafe
---

### Post by Abu Sabah on 2008-10-08
I have been testing out Ubuntu for awhile and since then I havn't had a need to use Windows, in fact I get upset when I forget to select Ubuntu from the options when I restart and then I have to look at it.

Originally I installed Ubuntu using Wubi but now I want to remove Windows entirely from the computer and just have Ubuntu there.

Can someone explain the best way to remove Windows and install Ubuntu? Thanks in advance.

Sorry if this topic has been discussed before or if I have posted in the wrong forum.

---

### Post by scourge on 2008-10-08
You should have probably posted this in the Installation & Upgrades forum.

If you want to get rid of Windows, then Wubi is obviously not an option. I think you should just backup your data, boot from the Ubuntu live cd, and install using the whole hard drive for Ubuntu. It's a very straightforward operation, you can't really screw it up.

---

### Post by billgoldberg on 2008-10-08
> **Abu Sabah said:**
> I have been testing out Ubuntu for awhile and since then I havn't had a need to use Windows, in fact I get upset when I forget to select Ubuntu from the options when I restart and then I have to look at it.

Originally I installed Ubuntu using Wubi but now I want to remove Windows entirely from the computer and just have Ubuntu there.

Can someone explain the best way to remove Windows and install Ubuntu? Thanks in advance.

Sorry if this topic has been discussed before or if I have posted in the wrong forum.

Download the ubuntu .iso image from [http://ubuntu.com](http://ubuntu.com) .

Burn it as an image (!!) to a cd.

Make sure your bios is set to boot from cd first.

Then the live cd will boot up.

Select the second option to do an install instead of using the live cd.

During the partitioning part of the installer just use the entire drive.

That should do it.

The Ubuntu wiki has more detailed instructions:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by AndyCooll on 2008-10-08
> **scourge said:**
> You should have probably posted this in the Installation & Upgrades forum.

If you want to get rid of Windows, then Wubi is obviously not an option. I think you should just backup your data, boot from the Ubuntu live cd, and install using the whole hard drive for Ubuntu. It's a very straightforward operation, you can't really screw it up.
As has been mentioned above, do a clean install. I just want to repeat what scourge has said, just make sure you backup any important data you have _first_!

:cool:

---

### Post by geoken on 2008-10-08
If you're trying to preserve data I think the quickest method is to resize your XP partition, create a new ext3 partition (which will become your /home when you do your real install), then move your important data into the new /home partition before finally deleting the XP partition and installing Ubuntu.

This method will have the added benefit of putting /home on a different partition.

---

### Post by Delvien on 2008-10-08
Just a reinstall will work, wipe the HDD clean and start new ( you'll get better performance this way too )

---

### Post by uberdonkey5 on 2008-10-08
> **Abu Sabah said:**
> I have been testing out Ubuntu for awhile and since then I havn't had a need to use Windows, in fact I get upset when I forget to select Ubuntu from the options when I restart and then I have to look at it.

Originally I installed Ubuntu using Wubi but now I want to remove Windows entirely from the computer and just have Ubuntu there.

Can someone explain the best way to remove Windows and install Ubuntu? Thanks in advance.

Sorry if this topic has been discussed before or if I have posted in the wrong forum.

Before you do this, just make sure there is NOTHING in windows that you want. You do have the choice of dual boot (with small partition for windows) and booting directly into ubuntu instead of windows. If you realise you actually want windows it is a pain reinstalling the other way around (i.e. installing windows on a ubuntu system) since windows tries to wipe everything else of before installation.

I don't use windows any more, but have been too lazy to remove it (it just sits gathering dust on my HD because I never boot into it).

---

### Post by stormtrooprdave on 2008-10-08
I installed Ubuntu through Wubi initially also and then used [this]("http://lubi.sourceforge.net/lvpm.html") thread about LVPM (Loopmounted Virtual Partition Manager) to move my Ubuntu installation from within Windows to its own partition on the HDD.  This meant that all my existing settings and programs were intact with no need to start again from scratch like all these people advising you to format and reinstall are doing.  Then you can choose to remove Windows altogether or leave it on as dual boot.

LVPM guide with screenshots - [http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html")
LVPM support thread from Wubi forum - [http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

---

