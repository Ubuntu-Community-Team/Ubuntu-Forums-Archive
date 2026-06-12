---
title: "Microsoft Works 8.5 for Ubuntu Lucid Lynx/10.04 (help installing)"
date: 2010-11-27
forum: Wine
---

### Post by shaobu on 2010-11-27
hello all.
I'm quite new at all this, so forgive me.

i'm trying to install microsoft office 2007 on ubuntu, but it needs to have works preinstalled (its an update version). I have wine installed (i believe 1.2, "sudo apt-get install wine" , did that today)

When I run the "setup.exe" from the disk, it gives me the error message 

title reads: "Blocked: wine start /unix"
body reads: "The file '/media/WORKS8/msworks/autorun.exe' is not marked as executable. If this was downloaded or copied form an untrusted source, it may be dangerous to run. For more details, read about the executable bit"

so I found online that I needed to right-click on the executable, properties, permissions, and I check the box "Allow executing file as program." when I do that, it gives me the error message "The permissions could not be changed" "sorry, could not change the permissions of "autorun.exe"; error setting permissions: read-only file system." 

I try to change the other options on the page, and receive same error message.

Thanks everyone.

---

### Post by Wobblybob on 2010-11-27
you may not have much luck with this see [[COLOR="Navy"]http://appdb.winehq.org/objectManager.php?sClass=version&iId=20235&iTestingId=53078[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20235&iTestingId=53078") as it looks like it may not be a supported program in Wine.

The other thought is have you copied the contents of the disk to the hard drive or are you trying to change the permission of the file while it's still on the CD. If you are trying to amend the CD then it will not let you as the CD is read only.

The other thought is why Office? Ubuntu has Open Office installed as default and it is able to open and save M/S files and in most cases without any problems.

---

