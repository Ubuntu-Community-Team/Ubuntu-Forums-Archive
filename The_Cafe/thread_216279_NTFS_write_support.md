---
title: "NTFS write support"
date: 2006-07-15
forum: The Cafe
---

### Post by Engnome on 2006-07-15
[http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697](http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697)

Someone care to verify that this works? I don't have windows on my computer any longer...

---

### Post by G Morgan on 2006-07-15
You could test it with VMware if you want. Create a VM for XP then one for Linux with NTFS read/write then hack the file to add the XP image to the Linux VM. Mess around with it a bit then if XP works properly when booted the test was a success.

---

### Post by sapo on 2006-07-15
Who's gonna be the first Guinea Pig? :mrgreen: 

Not me.. [-(

---

### Post by pelle.k on 2006-07-15
w00t :)

Just tried it out, and lemme tell you it works great!
It requires you to install > fuse 2.5 (which is not in the repos... so i had to install it from source), but other than that it's a piece of pie...

---

### Post by lazyd2 on 2006-07-15
I tried it too. It works fine, but for some reason (don't ask me why) it brakes lm_sensors.

---

### Post by pelle.k on 2006-07-15
If you know how to, it probably is better to compile your own, but anyway... These are my checkinstall .deb files.
I'm using kernel 2.6.15-26-686 (i dont know if fuse compiled against my header files.)

[http://www.bestsharing.com/files/ms00181833/fuse_2.5.3-1_i386.deb.html]("http://www.bestsharing.com/files/ms00181833/fuse_2.5.3-1_i386.deb.html")
[http://www.bestsharing.com/files/ms00181837/ntfs-3g-beta_20070714-1_i386.deb.html]("http://www.bestsharing.com/files/ms00181837/ntfs-3g-beta_20070714-1_i386.deb.html")


This is from the webpage (you should check it out)...
> USAGE
 =====
 
 If there was no error during installation then you can mount NTFS volumes 
 for read-write access (unmount them if they were already mounted by 
 another NTFS driver.)
 
 	ntfs-3g /dev/hda1 /mnt/windows
 
 If you want to give full access for all users, ignore permission related 
 driver messages, and make national characters visible then use (drop or 
 replace the below hu_HU.utf8 with the appropriate setting, and also the 
 device and mount points, if needed).
 
 	ntfs-3g /dev/hda1 /mnt/windows -o silent,umask=0,locale=hu_HU.utf8  
 
 Please see the ntfs-3g manual page for more options and examples.
 
 You can also make NTFS to be mounted during boot by ensuring that the FUSE 
 kernel module is automatically loaded and by putting the below line into 
 /etc/fstab 
 
 	/dev/hda1 /mnt/windows ntfs-3g silent,umask=0,locale=hu_HU.utf8 0 0

---

### Post by cstudent on 2006-07-15
What is the difference between mounting ntfs drives with read/write with this ntfs-3g driver and doing it the way this thread discusses?

[http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)

I have my Windows drive mounted using the method mentioned in the thread and it works fine. Are there advantages to using this driver?

---

### Post by Anduu on 2006-07-16
> **cstudent said:**
> What is the difference between mounting ntfs drives with read/write with this ntfs-3g driver and doing it the way this thread discusses?

[http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)

I have my Windows drive mounted using the method mentioned in the thread and it works fine. Are there advantages to using this driver?

Using NTFS-Fuse is still considered experimental and I myself have noticed it has some odd quirks sometimes.

I have been playing with this new method and it has been smooth as silk...you even get the drive icon on the desktop 8)

Oh and it is hella faster too...heh

---

### Post by Engnome on 2006-07-16
> **pelle.k said:**
> If you know how to, it probably is better to compile your own, but anyway... These are my checkinstall .deb files.
I'm using kernel 2.6.15-26-686 (i dont know if fuse compiled against my header files.)

[http://www.bestsharing.com/files/ms00181833/fuse_2.5.3-1_i386.deb.html]("http://www.bestsharing.com/files/ms00181833/fuse_2.5.3-1_i386.deb.html")
[http://www.bestsharing.com/files/ms00181837/ntfs-3g-beta_20070714-1_i386.deb.html]("http://www.bestsharing.com/files/ms00181837/ntfs-3g-beta_20070714-1_i386.deb.html")


This is from the webpage (you should check it out)...

Thx for the debs :D

I wonder if this will make it into edgy or edgy +1 ? I remember installing dapper flight 5 and getting a 

"Do you want to activate writing support for ntfs? Warning it may break your ntfs partition" 

dialog. I was like wtf?! is that possible on linux:confused:

---

### Post by givré on 2006-07-16
Rectification:
ntfs-3g is just an improvement of ntfsmount, which is the driver use by this method : [http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481) and they both use fuse to mount in user space. But yeah, it's really better.

An easy HowTo to install this : [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by DoktorSeven on 2006-07-17
So am I missing something, or can you not create directories in ntfs-3g and have them work in Windows?

I can create a directory from ntfs-3g under Linux and mess around in it fine, but rebooting back to Windows, it claims that the directory created is corrupt -- running disk check in Windows will completely blow the directory away.  

Create/delete/resize normal files in existing directories seem to work fine.

(Win2k is my Windows OS -- maybe that's the issue, maybe people have been testing it on XP...)

---

