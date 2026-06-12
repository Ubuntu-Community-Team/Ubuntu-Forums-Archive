---
title: "i need windows back"
date: 2008-09-26
forum: Windows
---

### Post by pdakid on 2008-09-26
i have looked and do not see anyone with my problem.  In my hast to install Unbuntu I did not put in a partition and now have wiped XP off of my hard drive.  The problem is, I need it for some software.  When I put in the XP CD it won't install.  If I put in my spare hard drive with Windows on it, it won't read it.  What can I do to remove Unbuntu?

---

### Post by pdakid on 2008-09-26
tried to boot from original xp cd it does not work.

---

### Post by rokytnji on 2008-09-26
One option is you can burn and boot this, then use it to wipe the hard drive.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by darrelljon on 2008-09-28
If you're Windows XP CD won't boot, the BIOS is probably set to boot from the Hard disk first.

---

### Post by skunkbad on 2008-09-29
One thing you need to realize is that your chances of recovering your previous installation of windows is not good. You should be able to reinstall windows, but that's not going to give you your data back.

---

### Post by fiddledd on 2008-09-30
> **pdakid said:**
> tried to boot from original xp cd it does not work.

Do you mean the CD doesn't boot, or the install fails?

---

### Post by arkticcool on 2008-09-30
Are you sure no one had your problem?

Try this thread:
[http://ph.ubuntuforums.com/showthread.php?t=859799]("http://ph.ubuntuforums.com/showthread.php?t=859799")

---

### Post by pdakid on 2008-09-30
i have benn trying to ask a few friends for help but not many bahamians have had this problem.my windows is gone i just want to reinstall in because i need i few programs that only know how to work on windows.i may have worded it wrong,but fiddledd is correct my windows install fails.never had this happen

---

### Post by mike1234 on 2008-09-30
Is your Windows disk a full version or do you have a restore disk included? Some OEM versions need both disks. Hopefully your restore info isn't located on your hard drive only.

M.

---

### Post by pdakid on 2008-09-30
my windows is the full disk i built the pc myself

---

### Post by mike1234 on 2008-09-30
Just wipe your hard drive with this. Everyone should have a copy of this in my opinion. 

[http://www.dban.org/download](http://www.dban.org/download)

M.

---

### Post by oldsoundguy on 2008-09-30
Your EXTRA PROGRAMS are already ERASED, so there is no way you can bring them back short of spending some money on some serious forensics software.

BUT to get XP back on:

[http://www.bootdisk.com/](http://www.bootdisk.com/) will have a boot disk to get you going.  You will have to f-disk and format.

(for that your bios will have to see a floppy .. I usually set bios for floppy/cd/hd when I am working on a computer)

Without a floppy in the drive, the machine will then boot from the CD and run XP again.  You are back at the very begining without ANY of your added programs.
(which. from what you have said, is REALLY what you want to get to .. but sorry!)

---

### Post by 3rdalbum on 2008-10-02
You need to tell us at what point the install failed, if there were error messages or whatever. There are hundreds of things that can go wrong with a Windows install.

The most common problem is that Windows' installer does not recognise Linux partitions. Boot up from an Ubuntu CD and use "Gparted" to remove all partitions on your hard disk and create just one new partition; with NTFS format.

Once that's done, Windows should be able to recognise the hard disk again and install without dramas. Assuming that's what was causing the install not to work.

---

### Post by sourchier on 2008-10-10
Before the XP start disk will work again, you need to uninstall grub. You can find out how to do that here [http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/]("http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/"). After grub is gone then you can use your XP install disk normally.

---

