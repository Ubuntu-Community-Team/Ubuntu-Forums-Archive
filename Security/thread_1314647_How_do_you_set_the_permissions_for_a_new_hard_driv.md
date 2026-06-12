---
title: "How do you set the permissions for a new hard drive?"
date: 2009-11-04
forum: Security
---

### Post by david.m.bailey on 2009-11-04
I recently added a second hard drive to a desktop computer. BIOS recognizes it. Ubuntu sees it and it places a "Lost and Found" directory in it.
 
But the system will not let me do anything to the drive. Is this a security permissions thing?
 
I am a heavy, old time Windows user. DOS before that. I understand command line entries for DOS, but have never tried it in Linux.
 
Any help would be greatly appreciated.

---

### Post by Lars Noodén on 2009-11-05
Yes.  It is a matter of setting the permissions. 

How are you going to use it?  One directory + one user, 

  # read the manual pages first, e.g. man chgrp
  sudo chgrp thegroup /path/to/newdrive
  sudo chown theuser  /path/to/newdrive
  sudo chmod u=rwx,g=rwxs,o=  /path/to/newdrive

one directory + many users, 

  # read the manual pages first, e.g. man chmod
  sudo chgrp thegroup /path/to/newdrive
  sudo chmod u=rwx,g=rwxs,o=  /path/to/newdrive

many users each with own directory, etc.
That includes system users like a web server, ftp server or other Internet service.  

If you're going to have a lot of users and shared material, it would be worth looking at ACLs:
 [http://www.cs.unc.edu/cgi-bin/howto?howto=linux-posix-acls](http://www.cs.unc.edu/cgi-bin/howto?howto=linux-posix-acls)

---

### Post by QLee on 2009-11-06
[QUOTE=david.m.bailey]I recently added a second hard drive to a desktop computer. BIOS recognizes it. Ubuntu sees it and it places a "Lost and Found" directory in it.[/QUOTE]

That L&F folder happened when you formatted the drive, eh?
 
[QUOTE=david.m.bailey]But the system will not let me do anything to the drive. Is this a security permissions thing?[/QUOTE]

Well, the system would probably let you read files on the drive if there were any there to read. Please be more specific, what is the "anything" that you are trying to do?

In this instance, I think you should read up on "mounting" partitions/filesystems (it's not something you had to do in Windows) and important to understand because in GNU/Linux "location" matters with respect to permissions.

Lars makes a lot of good points, some things need to be known about how you want to use the drive in order to give best advice.

[QUOTE=david.m.bailey]I am a heavy, old time Windows user. DOS before that. I understand command line entries for DOS, but have never tried it in Linux.[/QUOTE]

Naturally there are some differences in the command line interface with GNU/Linux systems. Your experience with DOS and batch files will help you learn faster because you will understand the concept. 
 
Edit: I will add that another thing Lars mentioned but which you may not yet understand. If you have questions about a command or want to investigate it before before taking someone's advice to run it, you can open a terminal window and type man <name-of-command>, as in Lars example, "man chgrp". That will open the manual page to explain the command and options (switches).


[QUOTE=david.m.bailey]Any help would be greatly appreciated.[/QUOTE]

I'm going to suggest some reading with a couple of links to Ubunty community documents, that should help get you started. Other people will probably also point you to links and you always have the forum to ask about anything you don't yet understand or that you encounter in your reading.

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Find the Ubuntu wikis.

Learn how to use the search function available here on the forum, most of the initial question a new user has have been answered lots of times.

---

### Post by scaine on 2009-11-06
I've had similar problems with usb drives when I plug them in for the first time.  If the disk is mounted on, say,  /media/disk1, then do 
```
sudo chown name:name /media/disk1
```
(replace name is your username)
That usually gives me ownership of the drive and I can then write to it normally.

---

### Post by soni1770 on 2009-11-06
in the ternamil
 

enter


gksudo nautilus

navagate to the drive and change the permissions.):P

---

### Post by Jive Turkey on 2009-11-06
> **scaine said:**
> I've had similar problems with usb drives when I plug them in for the first time.  If the disk is mounted on, say,  /media/disk1, then do 
```
sudo chown name:name /media/disk1
```
(replace name is your username)
That usually gives me ownership of the drive and I can then write to it normally.

That's what I do, and then:```
chmod -R 700 /media/disk
```
...makes it mine and only mine.

chown: changes ownersip to name:group
chmod XYZ: changes permissions 
X= owner permissions
Y= group permissions
Z= everyone else's permissions
7 means: read write and execute
0 means: disk? what disk?

google "chmod howto" for explanation of the area between 7-0.

---

### Post by bodhi.zazen on 2009-11-06
Actually , despite all the posts so far ...

Permissions and ownership depend on the file system. You can NOT set permissions and ownership in a NTFS or FAT partition with chown and / or chmod.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

That link will explain it to you and there is a gui tool as well ;)

Permissions on usb/flash drives should be automatic.

---

### Post by QLee on 2009-11-07
[quote=bodhi.zazen]Actually , despite all the posts so far ...
 
[/quote]
 
Well, actually that's all but one... the one suggested learning about mounting.

---

### Post by scaine on 2009-11-08
Might be wrong, but I thought "Lost and Found" directories were unique to ext2/3/4?  Anyway, good point.  Best learn about fstab from the off, cos there's still no usable gui for this stuff.

Funnily enough, I seem to remember that there used to be, back in the badger days, but the tool (disk-admin? I can't remember now) got dropped.  There was probably a good reason, but I was gutted.  Had to learn fstab instead.

Well, not really.  Just played with it enough to get things working, then wrote the settings down and used them since.  It does annoy me how inconsistently different linux distros treat different USB drives and even "new" internal drives.  There should be a tool, but at the moment you just have to knuckle down and learn some commands.

Maybe one day.

---

### Post by bodhi.zazen on 2009-11-08
> **scaine said:**
> cos there's still no usable gui for this stuff.

pysdm is a very nice gui tool to assist managing fstab.

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

It is in the Ubuntu repositories.

---

