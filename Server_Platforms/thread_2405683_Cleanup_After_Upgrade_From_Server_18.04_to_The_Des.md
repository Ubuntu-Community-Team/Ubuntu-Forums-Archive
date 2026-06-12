---
title: "Cleanup After Upgrade From Server 18.04 to The Desktop 18.04 Vers"
date: 2018-11-09
forum: Server Platforms
---

### Post by sparks79 on 2018-11-09
[FONT=Ubuntu][COLOR=#F4AA90][FONT=FontAwesome][/FONT][/COLOR]
[/FONT]
[FONT=Ubuntu]I have Upgraded from The Server Edition of Ubuntu 18.04.1 to The Desktop version 18.04.1.
I am Using Two NVME M.2 Samsung 970 Evo’s Connected in raid0.
It was a Long Road to get my system setup in raid0 But it is fast.
I wanted the O/S to be on the Raid so I Installed the Server Edition first ( Created a Raid0 Array ) Then Upgraded it to the Desktop Vers.
I Upgraded Using ( sudo apt full-upgrade ) Then ( sudo apt install ubuntu-desktop ).
Now I have a few small problems.
I have noticed in the Ubuntu Software Down loader, a few Apps that are normally there in the desktop vers ( without being upgraded ) Are Not there.
Like if I Search for Dropbox, it can’t find it.
So I had to Install them through the Terminal.
Also On Boot Up I get the Full String of System Commands, that One would Normally see in The Server Edition.
I would like to know if this could be Removed.
Or Maybe there might be some Command to run to Cleanup all the Actions that The Server Edition would normally Use.
Any Help would be Appreciated.
John

[/FONT]

---

### Post by deadflowr on 2018-11-09
Open Software and Updates and see that the repositories for universe multiverse and restricted are all enabled.
(dropbox, for example, is in the multiverse repository on 18.04)

---

### Post by TheFu on 2018-11-10
I would backup my data and any specific server configs needed and make a list of manually installed packages (apt-mark), then wipe the system and install the Desktop.  Use "Do something Else" when prompted for the storage layout parts.  I'd use LVM with striping to get the RAID0 effect, but that isn't a beginner setup and I would only do that in a RAID10 setup.

After that install finishes, then I'd restore my data, server configs (selectively), and reinstall the applications using a list created by apt-mark.

RAID0 is pretty dangerous.  I pray you have excellent, versioned, automatic, backups.  I'd hate for you to loose everything because of a small failure in 1 SSD.

---

