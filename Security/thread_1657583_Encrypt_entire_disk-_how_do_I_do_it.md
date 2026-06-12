---
title: "Encrypt entire disk- how do I do it?"
date: 2011-01-01
forum: Security
---

### Post by PDA1 on 2011-01-01
I want to encrypt my entire disk.  


Tell me if the following procedure is correct;  

1.  Back up my /Home Folder and /File System (exactly what program to use for back up I don't know) I would really nice if I could do a backup that be complete mirror of my existing system so that re-installation of the backed up files would simply be a matter copying to the newly encrypted hard drive.   

2.  Re-install Ubuntu 10.04 using the Alternate CD and use the &quot;encrypt-the-disk&quot; option (I think that's what it's called)  

3.  Re-install the previously backed up files (accomplished in step 1 above) to the machine. 

Any recommendations or suggestions would be much appreciated.  I want this to be as easy as possible (no laughing, please).

---

### Post by cariboo on 2011-01-01
Give [Clonezilla ]("http://clonezilla.org/") a try for backing up your system. It will backup a partition, or the whole disk. I use it all the time.

---

### Post by PDA1 on 2011-01-01
'Just looked it.  Man, that's way too complex for a simpleton like me.


There's gotta' be an easier way.

---

### Post by cariboo on 2011-01-01
Clonezilla uses the same type of interface as the alternate install cd, just create the Live CD and boot from it and follow the prompts. If you find Clonezilla hard to use, Have you had a look at [Remastersys]("http://www.geekconnection.org/remastersys/"), it allows you to make a live CD of your installation.

---

### Post by PDA1 on 2011-01-01
I don't want to backup my system to a cd or DVD- it's got to be on  USB hard drive.

It doesn't look like Remastersys has that option.  I'll investigate further.

---

### Post by handy on 2011-01-01
**@PDA1:** Clonezilla is not hard to use. & it works brilliantly across many & varied partition types from different systems. This I know because I have used it to do so after previous attempts failing.

You just need to read & understand how to use it. You can use it to make your desired copy & then verify that you have got what you wanted before destroying your original data. For that matter you could make more than one copy using different techniques if for no other reason than to grow your understanding of of how Clonezilla works.

From my past experience there is no other product out there, being made for any system that I would rather use for the job.

---

### Post by PDA1 on 2011-01-02
I just downloaded some variation of Clonezilla (Maverick?)

Here's the problem- I have NO idea what to do with the download now?  It's an ISO, so I burned it to a CD.

I read some of "how to" information about Clonezilla but for a neophyte it really is meaningless and installing the program or setting it up is beyond me.

There's got to be some simple way to backup, image or whatever the heck it is....a hard drive without all the hassle.

---

### Post by FuturePilot on 2011-01-02
Clonezilla is not the solution to this problem. It's not going to let you plop your system back on top of an encrypted LVM. It will just wipe everything out and restore your original system. Not to mention, Clonezilla hates when you try to restore an image to a partition or disk of a different size than the original which yours *will* be different because of the LVM setup.

The simplest thing to do would be to back up your home directory, do a reinstall with the alternate CD making sure to select the encrypted LVM option, then restore your home directory. There would be too much to reconfigure if you were to restore your system on top of the encrypted LVM rather than do a reinstall.

---

### Post by PDA1 on 2011-01-02
Oh boy!  Thanks.

The concern I have is if I backup my /Home Folder ONLY and not the File System too won't I have to reinstall the programs that I have running on my machine right now?


I want to backup everything so that when I do a reinstallation of files AFTER the disk has been encrypted (with Alternate CD) I won't have to fiddle with and adjust all of the programs I previously had on my computer.

In other words.

1.  Backup my entire disk.

2.  Reinstall Ubuntu 10.04 and make it encrypted

3.  Restore all previously installed programs (previously backed up in step 1) so that they work the first time flawlessly just as they do now.

Will you method accomplish that?  Is there some special, fancy commands I have to do to get everything backed up?

---

### Post by FuturePilot on 2011-01-02
The only thing you would have to do is reinstall all your programs. If you back up everything in your home directory including all your dot files (open a file browser and View > Show Hidden Files to see them) you won't have to reconfigure all your custom settings since they are stored in these dot files.

---

### Post by PDA1 on 2011-01-03
You recommend backing up only the /Home Folder and the hidden files in it (dot files).

Then....reinstall Ubuntu with alternate cd and LVM to encrypt.

Restore the /Home Folder files to the new installation.


But......you mention re-installing the program files.  I thought the dot files were the program files?  You know....like .Thunderbird  .GtkPod    that sort of stuff.

---

### Post by matt_symes on 2011-01-03
Hi

> But......you mention re-installing the program files. I thought the dot files were the program files? You know....like .Thunderbird .GtkPod that sort of stuff.

They are the program configuration files (etc) and not the programs themselves.

Kind regards

---

### Post by PDA1 on 2011-01-03
Ok...that sounds good.

Is there a backup program you would recommend?  A GUI would be nice.

---

