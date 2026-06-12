---
title: "When using samba is it the winows box or server writing to the disk?"
date: 2008-05-22
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-22
I haven't been able to find the answer to this yet although I have set up my 500gb NTFS usb disk (to the server) and have Linux apps and windows (via network) apps writing with no probs.

Is NTFS-ng safe for writing large dvd .iso's (torrentlfux / amule) to a ntfs drives? This seems to work but is it stable?
If a NTFS drive is connected to a Linux box shared over the network and I save on the drive with windows via the network, is the linux box doing the writing or just providing a 'gateway / middleman' for the windows machine to write. 
Should the drives be ext3 format because they're connected to ubuntu even tho I am constantly accessing them with xp / vista?
I have a usb NTFS drive that is plugged into the server. I also have an 80, 60, and 10 gb (all ide) drives in the server box (the 60 with ubuntu os on). I don't know what to format the them all with.
Also while I'm here how do I mount the other ide drives, they're not done automatically.

I'm having trouble with permissions and accounts aswell. I need to setup a group for 'family' who have read write access to most files on the 80gb drive but only read on the others. The family should not be able to see the 10 gb drive as that will be my work drive.
I also need to share var/www for putting files for my apache website, at the moment I can only access by doing gksudo thunar (i think its thunar) Also the whole 60gb ubuntu drive should be read/write for me.

Can I have NTFS and Ext3 or is it one or the other? Can I write to an Ext3 drive from windows and 'map as a network drive'?

Sorry this is so long but I have searched for ages for whether it should be NTFS / Ext3 with samba. I'm suprised this question isn't pointed it to begginers or documented although I could be looking in the wrong places. 
The permissions issues are also a struggle so any help with that would be greatly appreciated.
Cheers

---

### Post by camccall on 2008-05-22
> If a NTFS drive is connected to a Linux box shared over the network and I save on the drive with windows via the network, is the linux box doing the writing or just providing a 'gateway / middleman' for the windows machine to write.
Should the drives be ext3 format because they're connected to ubuntu even tho I am constantly accessing them with xp / vista?

When you are using samba running on Linux, it is the Linux machine doing the writes to the drive.  
My recommendation is if the drive is going to be accessed primarily by the Linux OS locally, is to format it with a Linux supported file system such as ext3 or reiserfs.  This will allow you to set permissions correctly using the native tools.  

> Also while I'm here how do I mount the other ide drives, they're not done automatically.

Are the other drives formatted, if they are not you won't be able to mount them.  If they are use the [mount]("http://linux.die.net/man/8/mount") command or add them to the [/etc/fstab]("http://linux.die.net/man/5/fstab") file.  


> I also need to share var/www for putting files for my apache website, at the moment I can only access by doing gksudo thunar (i think its thunar) Also the whole 60gb ubuntu drive should be read/write for me.

Are you trying to share this over the network with your windows box, or are you trying to access this via ubuntu locally?
Additionally when using Linux you should never have read/write access for the entire drive the OS resides on, just your home folder and a few other directories.

> Can I have NTFS and Ext3 or is it one or the other? Can I write to an Ext3 drive from windows and 'map as a network drive'?

You can only have one or the other, when you map the drive in windows, it doesn't matter what file system is on the partition, as long as the server that the partition physically resides on can write to it the windows box can write to it. 

As far as the permission issues, give us a better idea of what you are looking for and I'm sure we can give you a hand.

---

