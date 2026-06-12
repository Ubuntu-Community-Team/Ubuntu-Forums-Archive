---
title: "Folder synchronisation utility"
date: 2006-10-30
forum: The Cafe
---

### Post by Castar on 2006-10-30
Hi, I was wondering if anyone knows of anything similar to Allway Sync for windows? What it does is keeping folders in different locations, such as the Documents folder to the /home directory to the Documents folder in a USB stick. Allway sync is nice for windows but I would really like one for linux.

---

### Post by chaosgeisterchen on 2006-10-30
I intended to write one some time ago but school won't allow me to take my time.

---

### Post by Castar on 2006-10-30
Actually, it's not a bad idea to write one. And it should be relatively easy to do. Maybe I will... :-k

---

### Post by DoctorMO on 2006-10-30
I have some drawings for one, the idea was to control data flow and syncing specificly for devices (mass storage/pdas etc), online hosts, cds/dvd backups and computer folders. any of which could be sync'ed and it would handle files and databases of various kinds.

nice gui too, but I'm busy right now.

---

### Post by stimpsonjcat on 2006-10-30
Unison (apt-get install unison-gtk)
works like a charm. Even cross-platform!

---

### Post by Castar on 2006-10-30
Thank you! I'll have a look.

---

### Post by TheWizzard on 2006-10-30
> **Castar said:**
> Hi, I was wondering if anyone knows of anything similar to Allway Sync for windows? What it does is keeping folders in different locations, such as the Documents folder to the /home directory to the Documents folder in a USB stick. Allway sync is nice for windows but I would really like one for linux.

rsync is a command line program for synchronistaion and backups

---

### Post by MarnixV on 2006-11-05
Hi, I tried Unison to sync a new file in my /home with a USB DISK. Unison said it could not set the permission of the new file on the USB DISK to rw-r--r--, and that it set the permission to rw------- instead. But when I check the USB DISK I see it has not transferred the file at all.
I don't want to change permissions for any files I want to sync, so can I get Unison to transfer the files anyway? Thanks in advance...

---

### Post by professor_chaos on 2006-11-05
if your usb disk is formated as fat, then your not going to be able to preserve permissions, as all files on a fat disk have permissions of the person who mounted it. It will no nothing of groups.

---

### Post by MarnixV on 2006-11-06
thanks, I thought it would have something to do with the USB being FAT. Is there anything I can do to keep it FAT, while being able to use it with Unison?

---

### Post by stimpsonjcat on 2006-11-07
it should work without doing anything else. did you unmount the usb disk after sync'ing? Linux does not necessarily write changes to usb disks immediately - you have to wait a few seconds or perform an unmount/mount if you want changes to be written immediately.

there's some info about cross platform usage and permissions in the unison docs, though I don't think it's relevant to your problem: [http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html]("http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html")

---

### Post by MarnixV on 2006-11-07
Thanks for your help...I have not tried to unmount the USB disk. The problem arises while unison is trying to synchronise. I can get it to work on two folders in my own home directory. I think it has something to do with permission rights on the mounted USB DISK.

My input:
```
$ unison /home/marnix/documents/a.tmp /media/USB\ DISK/b.tmp
```

Output of unison:

a.tmp          b.tmp              
props    <-?-> props      /  []

I tell him to skip this *props*. It is not a file, and not present in the directories, not even as a hidden file/folder.
Next unison proposes the actual file synchronisation:

file     ---->            eerste.txt  [f] 

with *eerste.txt* being a file I put in a.tmp to try it out. It should indeed sync to folder b.tmp so I press enter. I get the following:

-------------------------------------------------------------
UNISON started propagating changes at 00:42:34 on 08 Nov 2006
[CONFLICT] Skipping 
[BGN] Copying eerste.txt
  from /home/marnix/documents/a.tmp
  to /media/USB DISK/b.tmp
Failed: Failed to set permissions of file /media/USB DISK/b.tmp/.#eerste.txt.4676517c19e96f815b32b6061d0c853e.unison.tmp to rw-r--r--: the permissions was set to rw------- instead
100%  00:00 ETAFailed [eerste.txt]: Failed to set permissions of file /media/USB DISK/b.tmp/.#eerste.txt.4676517c19e96f815b32b6061d0c853e.unison.tmp to rw-r--r--: the permissions was set to rw------- instead
UNISON finished propagating changes at 00:42:34 on 08 Nov 2006


Saving synchronizer state
Synchronization incomplete  (0 items transferred, 1 skipped, 1 failure)
  skipped: 
  failed: eerste.txt
--------------------------------------------------------------

I hope this rings a bell for you. By the way, when I 'ls' /media I get the following for the USB DISK:

drwx------ 16 marnix marnix 23040 2006-11-08 00:32 USB DISK

The USB DISK gets mounted automatically when I plug it in. 

Thanks anyway

---

### Post by stimpsonjcat on 2006-11-09
you could try the perms=0 option (ignore all permissions, since they don't work on FAT anyway).

BTW, have you noticed the unison-gtk package? it provides a gtk user interface for unison.

---

### Post by xpan on 2007-02-04
can I sync between my folder and a remote folder through samba sharing using Unison?

It seems that the only options it supports are SSH, RSH, socket.

---

### Post by sam81 on 2007-02-04
Have a look to grsync [http://www.opbyte.it/grsync/]("http://www.opbyte.it/grsync/") as well it's a very handy graphical frontend for rsync, and it's in the universe repos

---

### Post by mostwanted on 2007-02-04
I always use Grync for syncing between my backup hard disk and my home folder.

---

### Post by xpan on 2007-02-04
thanks for your answers, but I can't see any way for me to sync between a local and a remote folder (shared with Samba). 

GrSync, asks me to type in two folders starting with a "/". How can I point to a remote folder starting with a "/"?

Can I link a local folder to a remote one? For instance /home/<user>/remote_folder, so I can use it as if it was local?

---

### Post by cowlip on 2007-02-04
I think fusesmb allows you to browse SMB  mounted on  /

It should be default because gnomevfs sucks :)

---

### Post by xpan on 2007-02-05
> **cowlip said:**
> I think fusesmb allows you to browse SMB  mounted on  /

It should be default because gnomevfs sucks :)


i installed fusesmb, but I can't see how to mount a public folder in another machine.

For instance, I use a folder named "public2" on a machine at 192.168.1.15

how can I mount that folder on my (local) machine with fusesmb?

---

### Post by xpan on 2007-02-06
Ok.

I managed to mount my remote folder at a local folder using fstab and smbfs.

So when I go to /mnt/pub I can browse through the remote folder contents.

However, grsync although it says that synchronization completed successfully, nothing has been transfered to the remote folder.

Unison, says something like this:

Error in setting permissions:
Operation not permitted [chmod(/mnt/pub/test/.#testfile.odt.b6ba3fde8b601cb7bdab1ecc9a20b714.unison.tmp)]

However, I had set user read-write perimisions while mounting...

thanks!

---

### Post by cowlip on 2007-02-08
hope you get some more help today!  I don't know...what does your fstab look like?  Can you copy  files to it within Nautilus or the command line?

---

### Post by dekaru on 2007-12-01
thx 4 the tip !

---

### Post by John_T on 2008-01-03
> **stimpsonjcat said:**
> you could try the perms=0 option (ignore all permissions, since they don't work on FAT anyway).

Bingo, that did the trick for me!

I'm synchronizing data on an EXT3 Ubuntu partition and an NTFS partition on a portable hard drive shared with Windows and Linux systems when I'm out and about.

---

### Post by Chonnawonga on 2008-04-05
You can add ```
perms = 0
``` to the config file, which is at ```
/home/username/.unison/default.prf
```

(Of course, you should replace "username" with your user name.)

---

### Post by jancelis on 2009-04-14
Here's how I do a folder synchronisation from linux to a vfat USB stick:
unison -perms=0 -batch /home/ubuntu /media/USB

So you can add the perms option in commandline too.

---

