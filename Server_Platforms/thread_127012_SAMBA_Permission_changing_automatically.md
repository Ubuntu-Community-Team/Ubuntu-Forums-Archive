---
title: "SAMBA: Permission changing automatically"
date: 2006-02-07
forum: Server Platforms
---

### Post by nuke1138 on 2006-02-07
I posted this in the general support forum and got no response.  Maybe the server people hang out here...

I am trying to setup a Ubuntu box as a fileserver for my home network.  Right now I only have one client pc (XP)  My goal was to set up XP's "My Documents" folder to reside on the Ubuntu machine, then map a drive to it from XP.

First I mounted a vfat partition with the following in fstab:
```
/dev/sda3       /home/jason/media      vfat  umask=000   0  0
```

Then I set up samba with the following share
```

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam, guest
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
[Documents]
	path = /home/jason/media/Documents
	read only = No
```
These were mostly defaults from SWAT.  

I set up a Ubuntu user called "jason" and made an smb user with the same name.  I also have an XP user "jason".  Both the Ubuntu user and the XP user have the same password.  "jason" also owns "/home/jason/media/Documents".  Everthing worked fine.  I could browse to the SAMBA share from XP through Network Neighborhood and could map drives to the share from XP.  I copied all my data to the SAMBA share and realized the first problem.

XP creates a file called "Thumbs.db" that keeps thumnails of pictures in a folder.  This file is created with both the system and hidden Windows attributes.  Normally these files are not displayed beause of the "Hide protected operating system files" option in Windows.  Once I copied folders with this "Thumbs.db" file to Ubuntu, they showed up in XP even though I had the option to hide them selected.  Not a major problem but annoying none the less.

It seems that Unix permissions don't match up with Windows attributes.  SAMBA accounts from this with the "MAP SYSTEM", "MAP HIDDEN", and "MAP ARCHIVE" options.  "MAP ARCHIVE" is turned on by default but the other two are off.  OK problem solved right?

I added the following to smb.conf
```

[Documents]
	path = /home/jason/media/Documents
	read only = No
	create mask = 0755
	map system = Yes
	map hidden = Yes
```

Everything worked after that.  I could change attributes on the windows side and they were reflected on the SAMBA share.  I'm not sure what the "create mask" entry does, but it didn't seem to work without it.  I was happy until the next morning.  I opened up the SAMBA share from XP and all my files were gone!  

I looked at them on the Ubuntu side and they were still there.  I turned off the "Hide protected operating system files" in Windows and low and behold the files showed up.  I changed all the attribues again on the Windows side and everything looked good again.  I left the PC for a while and came back later that evening and the files were hidden again.  What is going on?

I assume this has to do with either "umask=000" option if fstab or the "create mask" smb.conf.  Neither of which I fully understand.

The only thing I see happening in the logs that might be pertinent is this entry in /var/log/syslog:
```
localhost /USR/SBIN/CRON[18755] (root) CMD (   run-parts --report /etc/cron.hourly)
```
I haven't timed it to see if this problem occurs after this job runs, but there is nothing in cron.hourly anyway.

How are my permissions changing?

Tonight I just stumbled across a post talking about a file system called smbfs.  Should I be using that instead of vfat?

---

### Post by Robgould on 2006-02-08
You post in general is over my head.  I only really have one comment, when I mount my winxp shares in ubuntu I use smbfs and it works wonderfully.  I just add a line to my fstabe to mount it.  I would think that you would be able to mount your users "my documents" to your linux box this way as a share.  I am not sure if that would do what you want though.

---

### Post by mdr on 2006-02-08
Firstly 2 questions as you seem to be making life more complicated than it need be.

a) Why need to share "my documents" as such in particular.
Surely you mean just having a a general "data" dir that can be seen by all that is an equivalent of My docs ?  This can then be assigned a unique drive letter.

b) Why did you mount a VFAT partition on a Linux box for XP ?
Why not use an ordinary linux directory / partition and share that ?  this is what samba was meant to do.  the partition should be a linux filesystem such as ext3 or reiser.  Then you need not worry about the umask 000 when mounting the partition.

My understanding such as it is, if I remember correctly is that the create mask 0775 in samba allows the setting of correct permissions for folder and file creation on the shared drive when using samba (against a Linux drive) whereas the umask on the mount point sets valid file permissions for Windows files that do not have the permissions set (as they are to be presumably Windows files on a fat partition created presumably by Windows on a Windows PC).

Therefore they should not conflict as such.  (Someone with more knowledge may correct this),  However, I have not attempted to setup a VFAT partition on a Linux box that is shared out by Samba (bizarre way to do it imho).

smbfs is not a filesystem either, it is a utility to allow a linux box to mount (like any other partition)  any remote smb shares on an XP/Win32 box.  Thus allowing your ubuntu box to see shares on your XP box as if they were local hard drives, ie the opposite of what you are trying to do.  

hope this helps, google is your friend, especially this :) 
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by awi on 2006-02-08
1) [COLOR="Green"]vfat[/COLOR] es a file system for windows system (mostly), even though Linux could mount it, it is not a "native" file system, and the permissions' schema does not apply as if you are using a Unix "native" file system, as [COLOR="Green"]ext2/3[/COLOR], which in most of the cases are the default ones.
2) the map options from [COLOR="RoyalBlue"]smb.conf[/COLOR], try to map windows attributes to unix attributes, because of 1), you can't do that.
3) The line in messages from the [COLOR="RoyalBlue"]crond[/COLOR], has little to do with your problem, unless that in the ```
/etc/cron.daily
``` are some script that is messing up, with your directory.
4) [COLOR="RoyalBlue"]smbfs[/COLOR] es the one used to mount windows shared resources (a directory for instance), you could not mount a partition on your local disk using that file system, because it is a network file system, makes sense only in a network environment.
You should check [COLOR="RoyalBlue"]umask[/COLOR] from bash's manual page, and look at the [COLOR="RoyalBlue"]smb.conf[/COLOR] man's page too to understand better what are you actually doing with the parameters.
About the umask in your [COLOR="RoyalBlue"]/etc/fstab,[/COLOR] if you can, change your file system to ext2 or ext3; if you can't, change umask, and use de uid option like this:

```
dev/sda3       /home/jason/media      vfat  uid=1000   0  0
```

replacing 1000 for the jason's uid.

---

### Post by LordHunter317 on 2006-02-08
[QUOTE=nuke1138]I looked at them on the Ubuntu side and they were still there.  I turned off the "Hide protected operating system files" in Windows and low and behold the files showed up.[/quote]That's because you set the system bit on all of them.  Don't do that.

> I assume this has to do with either "umask=000" option if fstab or the "create mask" smb.conf.  Neither of which I fully understand.It has nothing to do with neither.

"create mask" determines what permissions newly created files will have.  For the mount, umask determines the permissions applied to all files and directories, since VFAT doesn't support permissions.

> How are my permissions changing?Because you didn't read the documentation carefully and because you're using VFAT.

> Tonight I just stumbled across a post talking about a file system called smbfs.  Should I be using that instead of vfat?No.  That's for mounting SMB shares from other machines.  You shouldn't be using VFAT, either.

[quote=mdr]a) Why need to share "my documents" as such in particular.
Surely you mean just having a a general "data" dir that can be seen by all that is an equivalent of My docs ? This can then be assigned a unique drive letter.[/quote]It's frequently a very desirable thing to have "My Documents" mapped to a network share, and many corporations do it automatically.

---

### Post by nuke1138 on 2006-03-26
Sorry about the delay reponding to the thread.

VFAT was the problem.  I made the assumption that I needed vfat for windows to be able to write to the share.  That is not the case.  I am using "map system = yes", "map hidden = yes", and "create mask = 755".  Everything is working now that I am using ext3.

Thanks for the help

---

