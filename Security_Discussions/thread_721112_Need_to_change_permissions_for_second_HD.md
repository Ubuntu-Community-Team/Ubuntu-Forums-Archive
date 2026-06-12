---
title: "Need to change permissions for second HD"
date: 2008-03-11
forum: Security Discussions
---

### Post by LinuxUser99 on 2008-03-11
I have Ubuntu Linux 7.04 installed on a machine that has two hard drives.  The operating system installed successfully and boots up just fine.  The operating system is installed on the first hard drive and the second hard drive permission was automatically set to root user.  I am the only user and I need to change the permission settings  back the same as for the first hard drive.  The second drive mount point is /media/hdb1.  My swap partition is on the first drive and I want to use the second drive just for routine storage.  I have only one ext3 partition on the second drive.  Both drives are large drives.

Can somebody give me some advice on how I can log in as root user to get my permission settings changed?  Any help would be appreciated.

---

### Post by pana.corbului on 2008-03-11
Hi!

You could change permissions for all your second partition and make yourself owner of it. 
Use the following command should do the trick: 

sudo chown -R youruser /mnt/mount_point

If doesn't work change permissions it to /dev/hdb1 [I doubt thought that won't work  1st choice]

---

### Post by LinuxUser99 on 2008-03-13
Thank you.  I'll try your suggestion.  I printed it out.  I'll post another message in a couple of days after I find time to work on it.

---

### Post by LinuxUser99 on 2008-03-16
Thank you for your help.  I was able to set the permissions for the drive properly.  Your command wasn't exactly right but you enabled me to figure out what to do.  I appreciate your help.  I'm trying to get the machine ready to use and I am a new Linux user.  I have some other permission issues and settings to fix so I am working on those.  Thanks very much.

---

### Post by pana.corbului on 2008-03-17
You welcome. I'm glad you solved your problem.

---

