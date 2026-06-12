---
title: "External hard drive; Permission Denied?"
date: 2010-10-26
forum: Security
---

### Post by helios16v on 2010-10-26
I have an external hard drive that has all of my Apple Powerbook G4 files on it. I plugged in my "Journal Extended" external hard drive into my new HP laptop with Ubuntu 10.10 on it.

All of my files are on the hard drive still, however lots of them have a little X on the folders and when I try to open them it tells me I don't have permission? 

How can I force the permission for everything on my external? It's my own files and I can't even access them lol.

-Ben

---

### Post by cariboo on 2010-10-26
There are several ways you can access your files. You could run the file manager as root, Press Alt-F2 and type:

```
gksu nautilus
```

You could set the permission and ownership to something to allow you to access the files. 

Most of the commands you use in a terminal on a Mac work the same way in Ubuntu.

---

### Post by helios16v on 2010-10-26
Ok that worked to give me access to all the files but how to I make it so I don't have to type that in every time?
After I closed it and opened the hard drive from the desktop it no longer worked.

**EDIT:**
I changed the permission of the folder to my user name and now I can access the folder but when I clicked "Apply Permissions to Enclosed Files" and it didn't change any of the files, all of the files in the folder now have little lock icons over them so I can access the files but it wont allow me to copy them onto the laptop or to delete the old ones I don't want anymore.. hmm..

---

### Post by CharlesA on 2010-10-26
What file system is the external drive using? Guessing ext3 or ext4.

If so, you can run this:

```
sudo chown -R username:username /path/to/mounted/drive
```

That'll change the owner and group of all the files on the drive, so make sure that's what you want to do.

---

### Post by helios16v on 2010-10-27
How do I include a space in the terminal?

The directory for my external is /media/500 GB but when I put the space for GB it tried to locate two different directories and told me /media/500 no such directory as well as 'GB/ no such directory?!

The name of the external is 500 GB, my Powerbook did that by default and I don't know how to change the name for it.. I tried right clicking and there is nothing for renaming it and double clicking slow does nothing as well..

Command for renaming my external? lol

**EDIT 1:**
Figured it out!

I had to put the path in quotations like this. '/media/500 GB' and now its going fine.
Thanks, I really hope this works :D

**EDIT 2:**
YAY! It worked :D
Thanks everyone!

---

### Post by nebraskann on 2011-01-19
I have followed the above instructions:

open shell using gksu nautilus
and after identifying my drive in /media I used

sudo chown -R username:username /path/to/mounted/drive

where my drive is labeled Untitled 1


I then used  
sudo chown -R username:username 'media/Untitled 1'
 
The files were then gone through with the following error after each
:Read-only file system

where the folders are still considered unreadable when I try to open them and show the little 'X' on them.

I have just installed Ubuntu 10.10 as of 1-19-2011.  Has something been changed that this is no longer possible?  Am I missing something completely obvious?

I would be so grateful for any advice, thanks in advance!!

---

### Post by CharlesA on 2011-01-19
Is the drive formatted as NTFS?

---

### Post by CharlesA on 2011-01-19
Is the drive formatted as NTFS?

---

### Post by nevius on 2011-01-20
> **CharlesA said:**
> Is the drive formatted as NTFS?

My guess is that since it contains information from a Powerbook G4, it is formatted HFS+ with journaling, which linux doesn't like.

[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

It appears the only way to write to an HFS+ partition is to disable journaling, which is not a very good long-term idea. Your best bet is to copy the information off the drive and reformat it as EXT3 or EXT4, then copy the info back. If you're trying to share an external drive between OSX and Linux, then your only real option is unfortunately FAT. Your best bet in that case may be to format the drive in EXT3 or 4 and share it with NFS or samba from a linux box.

Edit: Just read the thread more carefully and realized the OP solved his problem, so never mind. :)

---

### Post by bazzieb on 2011-12-13
Hi There

I have the same problem as the above posts. I have a usb drive formatted to NTFS. I have always been able to copy/paste to and from this drive but recently after an update, all this changed. I have tried everything you have mentioned above and it completed successfully but i still cannot copy anything to my portable from my ubuntu laptop. Works fine on my win7 pc.

Do you maybe know what could of changed?

Kind regards

---

### Post by CharlesA on 2011-12-13
> **bazzieb said:**
> Hi There

I have the same problem as the above posts. I have a usb drive formatted to NTFS. I have always been able to copy/paste to and from this drive but recently after an update, all this changed. I have tried everything you have mentioned above and it completed successfully but i still cannot copy anything to my portable from my ubuntu laptop. Works fine on my win7 pc.

Do you maybe know what could of changed?

Kind regards
Are you able to copy files to the drive via the terminal?

---

