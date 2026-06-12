---
title: "Windows XP Student edition wont install?"
date: 2007-09-10
forum: Windows
---

### Post by mattmagician on 2007-09-10
This is the Windows XP Pro. that they give at college to install, a fried gave me a copy. 
So i went to boot up with the disk in, and it freezes at 'Setup is starting windows' it wont go anywhere after that.
I have Ubuntu Dapper Drake installed, any help?

---

### Post by igknighted on 2007-09-10
> **mattmagician said:**
> This is the Windows XP Pro. that they give at college to install, a fried gave me a copy. 
So i went to boot up with the disk in, and it freezes at 'Setup is starting windows' it wont go anywhere after that.
I have Ubuntu Dapper Drake installed, any help?

Bad burn is most likely, but another possibility could be a bios setting is wrong.  This is something you would have to trial/error with to figure out.  I had a system once that had SMART capabilities of the HDs turned off and windows did that, after I turned it on in the BIOS it worked perfectly.

EDIT: You are aware that using a friend's version of Windows is illegal, right?

---

### Post by smoker on 2007-09-10
looks like windows isn't seeing a bootable partition, try making a fat32 or ntfs partition and flag it as bootable, use something like the 'gparted live cd'. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

best of luck

---

### Post by rickyjones on 2007-09-11
How long do you wait? Does it go to a BSOD? What kind of hard drive do you have? Have you tested the memory?

Usually, in my experience, if it hangs at that point then it is trying to detect the hard drive. A lot of times if there is a hardware problem with the drive then it'll freeze right there. I've also seen a similar issue with bad RAM. Finally, it could be a junk CD. See if you can get a different CD, preferably an original from Microsoft.

-Richard

---

### Post by kulturloseramerikaner on 2007-09-13
> **smoker said:**
> looks like windows isn't seeing a bootable partition, try making a fat32 or ntfs partition and flag it as bootable, use something like the 'gparted live cd'. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

best of luck

Agreed.  If you have Dapper on there, chances are the HD's formatted inn ext3, which a stock version of Win can't read.  Create an NTFS partition and set it as a primary, and give it another shot.  Gparted is a great way to do it.

---

