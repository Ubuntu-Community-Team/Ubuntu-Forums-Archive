---
title: "Mounting UFS Read/Write"
date: 2014-05-29
forum: Server Platforms
---

### Post by Graysonh on 2014-05-29
It seems I've gotten myself into quite the predicament - here's some background:

Ran FreeNas on an internal 80GB drive for a couple months with a 1TB external drive that was formatted to UFS used for storage. I decided to install Ubuntu Server 14.04 to the internal drive, which went perfectly. I knew I would have some troubles getting at the data on my external drive, but I was able to see the data using a "read-only" flag when mounting.
ie. ```
[COLOR=#000000][FONT=Courier New]sudo mount -t ufs -o ro,ufstype=ufs2 /dev/sdb1 /home/exthdd[/FONT][/COLOR]
```
The problem here was that I had completely buggered the permissions in a couple of directories on the external drive and as a result I cannot recover many files, and I cannot change the permissions because I do not have write permissions.

After downloading my kernel sources (3.13.0) I used the commands found [_here_&#8203;]("http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/") to attempt to recompile the kernel with UFS write enabled. Everything goes well until I reach ```
[COLOR=#000000][FONT=Courier New]$ grep  CONFIG_UFS_FS_WRITE /usr/src/linux-source-2.6.27/.config[/FONT][/COLOR]
``` which returns "grep: usr/src/linux-source-3.13.0/.config: No such file or directory". 

I've tried and tried again, looked around a bit for alternatives and this seems to be the most straight forward. 
Ideas? Thoughts? Solutions?

Any, and all help is appreciated!

---

### Post by steeldriver on 2014-05-29
Surely there has to be a better way of getting **read** access than by building a kernel with **write** support? in what way exactly are the permissions preventing you from accessing your data?

---

### Post by Graysonh on 2014-05-29
I can gain read access using: ```
[COLOR=#000000][FONT=Courier New]sudo mount -t ufs -o ro,ufstype=ufs2 /dev/sdb1 /home/exthdd[/FONT][/COLOR]
``` However, while I can see and access files on the root of the drive, anything deeper is restricted (I'm simply told I don't have permission). To change these permissions I require write permissions, correct?

Ideally, I would like to recover some of the data from the drive and then format to NTFS.

---

### Post by steeldriver on 2014-05-29
How are you trying to access it? via command line or GUI file manager? are you doing so with elevated privileges (sudo / gksu / pkexec)?

---

### Post by Graysonh on 2014-05-29
I was using my other (windows) computer to access via samba. 

I've found that I am able to copy the contents to the internal 80GB drive and move it from there (although this is not practical at all). Thanks for you assistance steeldriver - any ideas on where to go from here?

edit: I obviously have to play with my samba permissions as I am unable to delete from windows (You require permission from unix user\root to make changes...) but I am able to remove using command line.

---

### Post by steeldriver on 2014-05-29
Hmm... well adding samba to the mix is certainly going to complicate things - have you considered sticking openssh-server on the machine, then you can use SSH (PuTTY) and SCP (WinSCP) from Windows. You may need to (temporarily) PermitRootLogin if the permissions don't allow you to copy the files otherwise.

---

### Post by Graysonh on 2014-05-29
I am actually using SSH and SCP to access the box but I am still new to it.

Here's what I ended up doing:

1. Copied the contents of the UFS drive to the internal drive loaded with Ubuntu.
2. Changed permissions to everyone.
3. Copied to alternate location (currently ongoing) and then wipe and reformat.

Thanks for your help steeldriver.

---

### Post by steeldriver on 2014-05-29
Sounds good! glad you got it sorted

---

