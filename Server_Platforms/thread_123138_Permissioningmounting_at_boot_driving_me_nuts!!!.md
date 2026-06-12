---
title: "Permissioning/mounting at boot driving me nuts!!!"
date: 2006-01-29
forum: Server Platforms
---

### Post by MetalMusicAddict on 2006-01-29
I recently switched my home server to Ubuntu. :) Yay for me. Converted all the drives from NTFS to Ext3. I have everything mounted on the server *where* I want it but permissions are killing me.

I want **ALL** users to be able to read/write. Are these examples right?

_fstab mount_
/dev/hdd1      /media/Downloads      ext3       **defaults      0      0**


Then I guess I need to set the permissions on the folder itself right? Whats the command to own the folder *and* everything in it and also allow everyone to read/write?

Finally, I can mount at boot fine from a win machine to the Ubuntu server but mounting from another Ubuntu machine to the server seems different.

Any help/links is great. :)

---

### Post by MartinG on 2006-01-29
[QUOTE=MetalMusicAddict]I recently switched my home server to Ubuntu. :) Yay for me. Converted all the drives from NTFS to Ext3. I have everything mounted on the server *where* I want it but permissions are killing me.

I want **ALL** users to be able to read/write. Are these examples right?

_fstab mount_
/dev/hdd1      /media/Downloads      ext3       **defaults      0      0**


Then I guess I need to set the permissions on the folder itself right? Whats the command to own the folder *and* everything in it and also allow everyone to read/write?

Finally, I can mount at boot fine from a win machine to the Ubuntu server but mounting from another Ubuntu machine to the server seems different.

Any help/links is great. :)[/QUOTE]Try the following link:[indent][http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)[/indent]
I'm not an expert, but I'd suggest you need to modify your typical fstab entry to read:
[INDENT]/dev/hdd1      /media/Downloads      ext3       **defaults,user,rw      0      0**
[/INDENT]
To change ownership, use [indent]chown -R newusername.newgroup <directory name>[/indent]
To modify permissions, the command is chmod 666 <folder-name>, or, if you want to allow execute permission, 777.

Can't help on the mount problems, but if they persist after the above I'd start by looking at firewalls.

---

### Post by MetalMusicAddict on 2006-01-29
Thanx for the info but I still cant get the command to apply to *everything* (files/folders) in the folder.

**sudo chmod 777 /media/Downloads** works on *that* folder but not sub folders/files.

---

### Post by kakashi on 2006-01-29
try chmod -R 777 <file>
or mauybe it was 
chmod 777 -R 

wel try both.

---

### Post by MetalMusicAddict on 2006-01-29
Kick @$$ man. It was:

**chmod 777 -R /media/Downloads** I guess the **-R** is for recursive?

Now that I see what works Ill be able to understand it better. ;)

---

### Post by MetalMusicAddict on 2006-01-30
OK. New problem. On the PC that the drives are on I have set the permissions like so in the fstab:
```
/dev/hdd1 /media/Audio defaults,user,rw 0 0
```

And the permissions in "Properties" looks like this on the local machine:

[[IMG]http://img494.imageshack.us/img494/2141/screenshot1yp.th.png[/IMG]](http://img494.imageshack.us/my.php?image=screenshot1yp.png)

Through the network the owner and group are both "root". Why?

I want EVERYONE to be able to write,read,delete,execute on this drive. Through the network or local. I dont wanna see any little "lock" on files/folders at all. Full access for everyone. And when new files/folders are created by users there are no restrictions on those either.

I know Im missing something.

---

### Post by CujoQuarrel on 2006-01-30
Is there anyway to give yourself all permsissions to everything? \

I want it to be as if I had logged in as root.

---

### Post by Sutekh on 2006-01-30
chmod changes the modes of access, ie read write and execute

chown changes the ownership

```

sudo chown -R <user>:<user> /media/Downloads
```

Edit: Just looked at your pic.  I'm not sure why it looks like root owns it through the network

---

### Post by Sutekh on 2006-01-30
[QUOTE=CujoQuarrel]Is there anyway to give yourself all permsissions to everything? \

I want it to be as if I had logged in as root.[/QUOTE]
Giving yourself permissions to everything is a really bad idea.  It can cause lots of problems.

And I really would advise against logging in as root.  There are usually good reasons as to why certain things can't be accessed.

[Ubuntu Guide - How to allow root user to login into GNOME?]("http://ubuntuguide.org/#allowrootlogingnome")
May have what you want, but use with caution.

---

### Post by MetalMusicAddict on 2006-01-30
For me, the drives Im trying to give everyone access to arent OS drives. Their all just storage.

---

### Post by Sutekh on 2006-01-30
[QUOTE=MetalMusicAddict]For me, the drives Im trying to give everyone access to arent OS drives. Their all just storage.[/QUOTE]
Mm, that wasn't aimed at you.  :p 

From the pic you had, the folder was owned by 'master' and the group 'users'.  I guess its a dumb question, but are the users on the network part of this group?

---

### Post by MetalMusicAddict on 2006-01-30
Yes, the network users are part of the "users" group.

The way it is now if a network user creates a file/folder another user cant change it.

---

### Post by Sutekh on 2006-01-30
[QUOTE=MetalMusicAddict]Yes, the network users are part of the "users" group.

The way it is now if a network user creates a file/folder another user cant change it.[/QUOTE]
How about ading a 'umask=0000' to your fstab entry?

---

### Post by MetalMusicAddict on 2006-01-30
So like:

/dev/hdd1 /media/Audio defaults,user,rw,**umask=0000** 0 0

Or...

/dev/hdd1 /media/Audio defaults,user,rw,**umask=0000**

---

### Post by Sutekh on 2006-01-30
Sorry, this one.
[QUOTE=MetalMusicAddict]
/dev/hdd1 /media/Audio defaults,user,rw,**umask=0000** 0 0
[/QUOTE]

---

