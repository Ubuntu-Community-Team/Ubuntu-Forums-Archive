---
title: "virus on portable hdd"
date: 2008-08-15
forum: The Cafe
---

### Post by ACF1 on 2008-08-15
This is a Windows question, but I am going to ask it here becuase this is the only tech forum I am a member of. 

I have viruses on this old laptop harddrive, but I want to get the files off of it.  If I just plug it in (its in a case so that it acts as a portable), will I get a virus?  

Thanks.

---

### Post by Riffer on 2008-08-15
Yes

---

### Post by LaRoza on 2008-08-15
> **ACF1 said:**
> This is a Windows question, but I am going to ask it here becuase this is the only tech forum I am a member of. 

I have viruses on this old laptop harddrive, but I want to get the files off of it.  If I just plug it in (its in a case so that it acts as a portable), will I get a virus?  

Thanks.

You can. If you need to get files, use a live cd and use ClamAV to scan the files before transfering them anywhere.

I found this, but there are other distros: [https://launchpad.net/clamav-livecd](https://launchpad.net/clamav-livecd)

---

### Post by Icehuck on 2008-08-15
> **ACF1 said:**
> This is a Windows question, but I am going to ask it here becuase this is the only tech forum I am a member of. 

I have viruses on this old laptop harddrive, but I want to get the files off of it.  If I just plug it in (its in a case so that it acts as a portable), will I get a virus?  

Thanks.

Shouldn't be an issue unless you execute it from the the drive. To clarify it would need to be a boot sector virus for it to just "infect" your windows PC.  This virus would also have to use the MBR root kit to exploit this on anything based on NT. If it even could do this the FIXMBR command removes the root kit with no issues.

---

### Post by ACF1 on 2008-08-15
I believe the boot sector is toasted, that is why it didn't work in the laptop any more.  I want to get some documents and pictures off of it.  I plugged it in once, and my virus scan detected the viruses.  I didn't do anything further. Should I let my virus scan do what it wants with the viruses? (as in, my files should be ok, correct?)  Or should I just grab my files and hope for the best?

---

### Post by LaRoza on 2008-08-15
> **ACF1 said:**
> I believe the boot sector is toasted, that is why it didn't work in the laptop any more.  I want to get some documents and pictures off of it.  I plugged it in once, and my virus scan detected the viruses.  I didn't do anything further. Should I let my virus scan do what it wants with the viruses? (as in, my files should be ok, correct?)  Or should I just grab my files and hope for the best?

Never hope. Scan the files themselves (ClamAV, or in Windows, ClamWin can do that) to see.

---

### Post by ACF1 on 2008-08-15
> **LaRoza said:**
> Never hope. Scan the files themselves (ClamAV, or in Windows, ClamWin can do that) to see.

I have AVG installed right now?  Can I scan it with that?

---

### Post by lisati on 2008-08-15
Personally, I wouldn't want malware sitting on any of my disks, no matter how unlikely that it will hurt linux, for the simple reasons that I sometimes use Windows, and I'm in regular contact with Windows users. 

My own preference for scanners is for "AVG free"; if you choose that one, don't forget to add your user-name to the avg user group (as outlined in the AVG documentation), otherwise updates will be a pain. 

Others in these forums prefer ClamAV, avast, and/or a handful of other scanners.

---

### Post by ACF1 on 2008-08-15
So can I pull the pics and stuff off of it and then scan those files?  Or can I scan the portable right away and get rid of the viruses without harming the files?

---

### Post by Icehuck on 2008-08-15
> **ACF1 said:**
> So can I pull the pics and stuff off of it and then scan those files?  Or can I scan the portable right away and get rid of the viruses without harming the files?

Just scan the drive before copying the files.

---

### Post by LaRoza on 2008-08-15
> **ACF1 said:**
> So can I pull the pics and stuff off of it and then scan those files?  Or can I scan the portable right away and get rid of the viruses without harming the files?

Scan the files before moving them. They are likely safe (random pics are usually not affected) but why gamble? 

> **Icehuck said:**
> Just scan the drive before copying the files.
Scan the files. Much more logical.

---

### Post by Icehuck on 2008-08-15
> **LaRoza said:**
> Scan the files before moving them. They are likely safe (random pics are usually not affected) but why gamble? 


Scan the files. Much more logical.

Yeah, but given his technical inexperience he is better off just scanning the drive. This way he is less likely to copy over anything at a later date.

---

### Post by ACF1 on 2008-08-15
Hey guys, I am some what knowledgeable when it comes to computers.  But I am not that experienced with this type of thing.  I have mostly used Linux and Windows 98 before.  And I have never used portable hard drives. 

So, can a virus get off the portable by itself?  Or do I have to move something off of it (portable hdd) that has it (the virus) on it? 

Thanks.

---

### Post by ACF1 on 2008-08-16
> **ACF1 said:**
> Hey guys, I am some what knowledgeable when it comes to computers.  But I am not that experienced with this type of thing.  I have mostly used Linux and Windows 98 before.  And I have never used portable hard drives. 

So, can a virus get off the portable by itself?  Or do I have to move something off of it (portable hdd) that has it (the virus) on it? 

Thanks.

Do you guys know?  Thanks.

---

### Post by LaRoza on 2008-08-16
> **ACF1 said:**
> 
So, can a virus get off the portable by itself?  Or do I have to move something off of it (portable hdd) that has it (the virus) on it? 


Some can. You don't want to take chances. Assume the worst, and all surprises are pleasant.

If you only want a few files from it, scan those files with ClamAV or something. If they are clean, copy them to where you want them. Then if the drive's data isn't needed, reformat it and you can use it again.

---

### Post by Vishal Agarwal on 2008-08-16
> **LaRoza said:**
> Some can. You don't want to take chances. Assume the worst, and all surprises are pleasant.

If you only want a few files from it, scan those files with ClamAV or something. If they are clean, copy them to where you want them. Then if the drive's data isn't needed, reformat it and you can use it again.

What LaRoza is saying is right. Copy all the files in a new folder in the old drive and scan the complete folder, and transfer the files to new location.

---

### Post by ACF1 on 2008-08-16
So if I plug it in, there is a chance I could get the virus off of it?  But since my virus scan detects them, I should just scan and delete and then get the files?  Thanks for all the help guys, I appreciate it.

---

### Post by LaRoza on 2008-08-16
> **ACF1 said:**
> So if I plug it in, there is a chance I could get the virus off of it?  But since my virus scan detects them, I should just scan and delete and then get the files?  Thanks for all the help guys, I appreciate it.

There is a chance. Although you are unlikely to, I can't suggest you do anything but the safest action.

You can delete the files that are detected as being bad and then get the files.

---

### Post by ACF1 on 2008-08-16
Sorry for all the confusion.  So what exactly should I do?

---

### Post by LaRoza on 2008-08-16
> **LaRoza said:**
> Some can. You don't want to take chances. Assume the worst, and all surprises are pleasant.

If you only want a few files from it, scan those files with ClamAV or something. If they are clean, copy them to where you want them. Then if the drive's data isn't needed, reformat it and you can use it again.

> **ACF1 said:**
> Sorry for all the confusion.  So what exactly should I do?

Do what I said:

[list]
[*] Scan the files you want to keep on that drive
[*] If they are clean, copy them over to where you want to keep them
[*] Reformat drive
[/list]

---

