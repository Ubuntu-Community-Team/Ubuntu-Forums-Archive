---
title: "WARNING! Windows overwrote ubuntu !?!?!"
date: 2010-04-06
forum: The Cafe
---

### Post by anaconda on 2010-04-06
I installed Microsoft security essentials to my XP installation (the free windows antivirus program)

And my ubuntu partition was destroyed! Or should I say the dangerous Ubuntu-virus was efficiently removed...

#&"&#/¤¤/#

Yes. I really didn't modify any partitions or anything. just installed microsoft security essentials and let it seach for viruses.

OK. Have to say that there was something wrong with my windowsXP ubuntu dualboot even before this happened.

For some strange reason my ubuntu partition was mapped as a D: drive in windows (in reality it was ~80% full ext3 partition, but windows thought it was an empty ntfs partition) And security essentials repaired? the partition and wrote some 140MB to the "empty" partition, and wiped my ubuntu in the process. Damn.

F#CK is it possible to rescue files from the overwritten ubuntu partition?

---

### Post by MichealH on 2010-04-06
Only if you have sectors which aren't overwritten. (Highly Unlikely in other words!)

---

### Post by tica vun on 2010-04-06
Oh wow, I sure am glad I got rid of my windows partitions right about now...

---

### Post by NightwishFan on 2010-04-06
Bad luck! I would have to say, no you probably will not recover the partition though you may find some files. (Not sure how that works). If you are asking for a better place is the help forums above. A mod will probably move this one though.

---

### Post by dragos240 on 2010-04-06
Try testdisk, it's your only saving grace now, your last bastion of hope.

---

### Post by anaconda on 2010-04-06
> **dragos240 said:**
> Try testdisk, it's your only saving grace now, your last bastion of hope.

I will try that, when I get back home.

Damn, I should have removed the D: drive from windows when I noticed it.

I do hope my files can still be found from the partition.. after all it was a 60GB partition, and windows only wrote 140MB on it....

.

---

### Post by anaconda on 2010-04-06
> **NightwishFan said:**
> Bad luck! I would have to say, no you probably will not recover the partition though you may find some files. (Not sure how that works). If you are asking for a better place is the help forums above. A mod will probably move this one though.

No, Mostly I just wanted to warn other users of the danger, so I think cafe is the right place.

Never had windows destroy my ubuntu before. Well, actually windows has overwritten grub before, but I guess that is "normal".

---

### Post by NightwishFan on 2010-04-06
Thanks for the warning. I will keep this in mind for a few of my dual-booting friends.

---

### Post by ve4cib on 2010-04-06
Out of curiosity did you have any Windows Ext-2/3/4 drivers installed?  At home I have an XP/9.10 dual-boot with Ext-3 Windows drivers installed and the Ubuntu partition mapped to E:/ and I've never run into this problem.

If you didn't have the Ext drivers installed then there's a chance that was the root cause of the problem; Windows detected a mapped partition using a filesystem it didn't understand.  It made the best guess available to it (an empty, damaged NTFS partition), and did its best to repair the problem.

---

### Post by CharlesA on 2010-04-06
> **ve4cib said:**
> Out of curiosity did you have any Windows Ext-2/3/4 drivers installed?  At home I have an XP/9.10 dual-boot with Ext-3 Windows drivers installed and the Ubuntu partition mapped to E:/ and I've never run into this problem.

If you didn't have the Ext drivers installed then there's a chance that was the root cause of the problem; Windows detected a mapped partition using a filesystem it didn't understand.  It made the best guess available to it (an empty, damaged NTFS partition), and did its best to repair the problem.

This sounds like the most plausible explanation.

---

### Post by fatality_uk on 2010-04-06
Did it ask to "Auto Repair"? I have had Windows try and clear a partition before, but lucikly I did select ask before applying changes. Is that an option on "Microsoft security essentials"?

---

### Post by Uncle Spellbinder on 2010-04-06
> **anaconda said:**
> I installed Microsoft security essentials to my XP installation (the free windows antivirus program)

And my ubuntu partition was destroyed! Or should I say the dangerous Ubuntu-virus was efficiently removed...

#&"&#/¤¤/#

Yes. I really didn't modify any partitions or anything. just installed microsoft security essentials and let it seach for viruses.

OK. Have to say that there was something wrong with my windowsXP ubuntu dualboot even before this happened.

For some strange reason my ubuntu partition was mapped as a D: drive in windows (in reality it was ~80% full ext3 partition, but windows thought it was an empty ntfs partition) And security essentials repaired? the partition and wrote some 140MB to the "empty" partition, and wiped my ubuntu in the process. Damn.

F#CK is it possible to rescue files from the overwritten ubuntu partition?
I've got to admit, I've never heard of such a thing. I've used MSE since the alpha days on 3 machines, each dual booting and one triple booting. Never had any such issues. Very strange indeed, sorry for the loss of your files and such. There use to be a bug reporting feature in MSE. Don't think it's there anymore though. Not sure if there is a way to report bug for MSE any longer.

---

### Post by Psumi on 2010-04-06
Wait... what?

Antivirus shouldn't detect partitions it can't map. Meaning it can't overwrite them.

As long as I've known Windows, Windows has never been able to physically see any linux partition, which means no application would be able to modify it.

Drivers or not, the app can't go into the partition without negotiating with the driver, unless that's all done universally now.

---

### Post by whiskeylover on 2010-04-06
> **Psumi said:**
> Wait... what?

Antivirus shouldn't detect partitions it can't map. Meaning it can't overwrite them.

As long as I've known Windows, Windows has never been able to physically see any linux partition, which means no application would be able to modify it.

Drivers or not, the app can't go into the partition without negotiating with the driver, unless that's all done universally now.


Windows can see all partitions. It just cannot map your linux partitions to a drive Letter. The Disk Manager reports them as 100% free partitions of unknown type.

---

### Post by kmsalex on 2010-04-06
you could also try this program from inside windows.
[http://www.piriform.com/recuva](http://www.piriform.com/recuva)
the lesson here, always back up you files, gpart tough me that.

---

### Post by befana on 2010-04-06
How could this happened? I'm dual-booting Ubuntu and Win7 with MSE and have any problem. Even I usually make hibernate both Ubuntu and Windows and rarely shut down.

---

### Post by PC_load_letter on 2010-04-06
> **anaconda said:**
> ...

F#CK is it possible to rescue files from the overwritten ubuntu partition?

running from an Ubuntu live cd try to see if foremost or scalpel can salvage any files from that partition. I'd run ```
sudo gparted
``` first to see what's going on, then ```
sudo apt-get install foremost scalpel
``` if they are not installed by default.

**EDIT:** In the mean time do NOT use the computer, the more you use it the greater the chance more files will be overwritten and will be harder to recover.

---

### Post by CharlesA on 2010-04-27
Start a new thread.

---

### Post by Rasa1111 on 2010-04-27
this almost feels like a 'joke' by ms. 
boo. 

sorry to hear your loss man.

---

### Post by houshdaran on 2010-04-27
To me, Charles?
What thread?

---

