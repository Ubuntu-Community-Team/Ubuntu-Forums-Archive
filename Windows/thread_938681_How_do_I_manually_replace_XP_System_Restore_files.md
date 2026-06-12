---
title: "How do I manually replace XP System Restore files?"
date: 2008-10-05
forum: Windows
---

### Post by curiousnoob on 2008-10-05
a few months back I found a posting on how to locate the System Restore files on the XP partition and use an older one to replace the current one to fix a broken installation that will not boot up.  
I cannot seem to find this article.  
Does anyone have a link or know how to do this?

---

### Post by Sef on 2008-10-05
Moved to Windows Discussions.

---

### Post by smoker on 2008-10-05
not sure if this is what you mean, but from 'safe mode with command prompt' you can use this command: 
> %systemroot%\system32\restore\rstrui.exe 

you may also be able to use this command using the 'recovery console' off an install cd, though i haven't tried that.

---

### Post by curiousnoob on 2008-10-07
> **smoker said:**
> not sure if this is what you mean, but from 'safe mode with command prompt' you can use this command: 


you may also be able to use this command using the 'recovery console' off an install cd, though i haven't tried that.

Not quite.  I am looking for the directory where past system restore files are stored and how to copy them to the current active location, thereby restoring the PC.

---

### Post by fiddledd on 2008-10-07
System Restore stores all it's files in C:\System Volume Information\.

---

### Post by curiousnoob on 2008-10-08
> **fiddledd said:**
> System Restore stores all it's files in C:\System Volume Information\.

That's what I was looking for.  Now does anyone know where the "active" directory is?  
I should be able to replace those files with one of the old ones and get it to work now.

---

### Post by Battie on 2008-10-09
> **curiousnoob said:**
> That's what I was looking for.  Now does anyone know where the "active" directory is?  
I should be able to replace those files with one of the old ones and get it to work now.

I'm not sure I understand why you're trying to do this.  If you start System Restore, it will ask you to choose the date/time to which you want to roll back.  There should be no need to replace any files.

---

### Post by curiousnoob on 2008-10-09
> **Battie said:**
> I'm not sure I understand why you're trying to do this.  If you start System Restore, it will ask you to choose the date/time to which you want to roll back.  There should be no need to replace any files.

I am unable to start Windows, even in Safe Mode or with the System Disc.

---

### Post by Battie on 2008-10-09
Have you tried booting with Last Known Good Configuration yet?  It sounds like you think it was a recent change that messed up your system, so this may work.

---

### Post by curiousnoob on 2008-10-09
> **Battie said:**
> Have you tried booting with Last Known Good Configuration yet?  It sounds like you think it was a recent change that messed up your system, so this may work.

Yes, I have tried that as well.  Regardless of what mode I use the system restarts a few seconds after the Windows splash screen with the progress bar appears.  
I had a similar issue with another PC a few months back and was able to fix it the way I have been describing.  Unfortunately I can no longer find the tutorial.

---

### Post by Battie on 2008-10-10
> **curiousnoob said:**
> Yes, I have tried that as well.  Regardless of what mode I use the system restarts a few seconds after the Windows splash screen with the progress bar appears.  
I had a similar issue with another PC a few months back and was able to fix it the way I have been describing.  Unfortunately I can no longer find the tutorial.

Wow.  I'm curious to see if this works.  I'd have thought it was impossible to fix a system with just those restore files.

---

### Post by ColinTempler on 2008-10-10
> **curiousnoob said:**
> a few months back I found a posting on how to locate the System Restore files on the XP partition and use an older one to replace the current one to fix a broken installation that will not boot up.  
I cannot seem to find this article.  
Does anyone have a link or know how to do this?


Try this:
[INDENT][http://support.microsoft.com/kb/307545/en-us]("http://support.microsoft.com/kb/307545/en-us")[/INDENT]
Part two describes using a previous system restore from c:\System Volume Information.

---

