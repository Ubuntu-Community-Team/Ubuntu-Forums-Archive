---
title: "start up problems in Windows xp"
date: 2009-01-15
forum: Windows
---

### Post by Grukmuck on 2009-01-15
my little sister asked me to help her fix her laptop, which is having start up problems. when you turn it on it displays the Windows screen, but then says "windows failed to start up correctly", or whatever. It gives the option to start in safe mode, with networking, command promp etc. Once i click any of the options the laptop restarts and does the same thing all over again. Is there a way i can get it to actually boot in safe mode, or another option to diagnose the problem and fix it? i have the option of reformatting the drive and re-installing windows, but would rather not do that. If all else fails and i have to, how would i go about getting all the files off that she would want to keep?

thanks in advanced

-gruk

---

### Post by cabbiinc on 2009-01-16
If you have the original install disk or you made a rescue disk when the computer was new you can put one of those in and use a system restore.

You could just reinstall windows without wiping the disk. You may have to reinstall some programs but you should still have all your data files (pics, music, etc...) in tact.

---

### Post by RJARRRPCGP on 2009-01-16
It's the symptom of Windows' equivalent of a kernel panic. 

Because of a hardware problem or Windows got corrupted by malware or n00bness.

For me, usually occurs, because I overclocked by too much.

---

### Post by Grukmuck on 2009-01-17
im guessing it was n00bness. she doesn't know anything about computers, and was probably clicking all over the place and mucked something up. she says that she didn't download any programs or songs or anything like that. but who knows. i haven't actually got a chance to mess with it again since i've been busy, but im gonna try to re-install windows and let yall know how it turns out.

---

### Post by Frak on 2009-01-17
Has she recently hardbooted the computer from an update or install? Lots of times, reboot after boot menu has to do with a vital registry entry pointing to a non-existant file.

---

### Post by Grukmuck on 2009-01-17
> **cabbiinc said:**
> If you have the original install disk or you made a rescue disk when the computer was new you can put one of those in and use a system restore.

You could just reinstall windows without wiping the disk. You may have to reinstall some programs but you should still have all your data files (pics, music, etc...) in tact.

every time i put the disc in it tells me that i have to reformat the drive. it doesnt give me an option to just reinstall windows.

---

### Post by Universal344 on 2009-01-18
One thing you could try is creating an Ubuntu live CD and troubleshoot from there.  You could see if it will see the NTFS partition and if so try mounting it and recovering the data that way.  If it doesn't see the partition than you've most likely got a corrupt partition table.  But since NTLDR (screen at which you select safe mode, debugging, etc.) seems to start fine the partition is probably in tact (unless NTLDR is stored in the MBR but I think it is the main windows partition, correct me if I'm wrong please).

---

### Post by Grukmuck on 2009-01-18
so i was trying to back up her data with acronis 9 (sp?), but for some reason it wouldnt let me do it. it said something about the files werent formatted right or something, i dont really remember what it said exactly. so i decided to try and start it up again, and CHKDSK started running, and windows fixed the problems without me having to do anything. to me its very strange. i didnt make any changes to anything. now im trying to use the backup utility inside windows and it tells me this:

The backup file name could not be used.

D:\Backup.bkf

Please unsure it is a valid path, and that you have sufficient access.


i dont understand why it wont let me back up her data.

thank you all for all of your helpful comments:P


-gruk

---

### Post by Grukmuck on 2009-01-20
well, i figeured it out. it wouldnt let me because it wont write the back up data directly to a disc. so i just used acronis, which i should have in the first place.

thank you again for all your help everyone.


-gruk

---

