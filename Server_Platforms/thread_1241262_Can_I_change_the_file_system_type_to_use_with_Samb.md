---
title: "Can I change the file system type to use with Samba?"
date: 2009-08-15
forum: Server Platforms
---

### Post by jsast21 on 2009-08-15
I googled this and could not find anything that matched exactly to my problem. I am trying to set up an older (3 yrs) desktop as a linux server and then run samba in order to be able to save files to it from both my windows and my linux machines at home. The server name is alex-svr.

I installed ubuntu server 9.04 and samba and almost everything works great. I can ssh to it from my ubuntu laptop and from putty on my windows laptop. 

However, when I open up networking in windows, I can see the 'alex-svr' machine and when I click on it, I can access it fine. It shows two icons 'hda public hard disk' and 'printers'. But when I click on 'hda public hard disk', I get the following error: \\ALEX-SVR\public hard disk is not accessible. 

So I went back to the alex-svr machine and typed fdisk -l. Here is the output:

--------------------

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            3651        9729    48829567+  83  Linux
/dev/sda3            3407        3650     1959930    5  Extended
/dev/sda5            3408        3650     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

----------------

When I set up the partitioning when I installed linux, I thought I made one of these fat16 so windows could see it (I named it /store when I partitioned it). But now I cannot tell which one it is. I meant for it to be sda2 and I made it 50 GB.

And lastly, I just powered down alex-svr and powered it back up again to see if there were any error messages. There was one fail, it scrolled by so quickly, I didn't really catch it, but it was something about NTFS failed to mount (or something to that effect).

My questions are:

1. How can I tell which partition linux is running on? 

2. Is there a way to change sda1 or sda2 (whichever one linux is not running on) from a linux format to a fat16 format so samba and windows can see it?

3. Or am I hosed and have to reinstall linux from scratch this time partitioning them correctly?

Thanks very much for any advice.

Regards

Joe.

---

### Post by john stiles on 2009-08-15
From a quick read, I do not think your problem is the format of the drive, more the permissions. Check that the folders/directories you wish to share on the Samba server are set to read by all, or specific groups you wish.

---

### Post by jsast21 on 2009-08-15
> **john stiles said:**
> From a quick read, I do not think your problem is the format of the drive, more the permissions. Check that the folders/directories you wish to share on the Samba server are set to read by all, or specific groups you wish.

I do not think it is a permission problem. Here are the permissions for the /media/store folder:

root@alex-svr:/media# ls -lart
total 24
...
drwxrwxrwx  2 root root 4096 2009-08-15 15:10 store
...

Can samba read a linux file system or does it have to be fat16?

---

### Post by scorp123 on 2009-08-15
> **jsast21 said:**
>  Is there a way to change sda1 or sda2 (whichever one linux is not running on) from a linux format to a fat16 format so samba and windows can see it? SAMBA does not care about the filesystem. Why would it? That's a totally different layer.

I'd suggest you check your smb.conf if you really have write permissions and what not on that share (and that's totally independent from the real filesystem that really is used on that location).

By the same logic you'd still have errors even if you changed the filesystem to MS-DOS ... It simply does not matter to SAMBA.

---

### Post by scorp123 on 2009-08-15
> **jsast21 said:**
> I do not think it is a permission problem. Here are the permissions for the /media/store folder:

root@alex-svr:/media# ls -lart
total 24
...
drwxrwxrwx  2 root root 4096 2009-08-15 15:10 store You misunderstand. What ever "ls -al" is showing has _NOTHING_ to do with SAMBA. What matters is how the shares are setup in your **smb.conf** and how the permissions *_in there_* are set (per each share).

---

### Post by jsast21 on 2009-08-15
> **scorp123 said:**
> You misunderstand. What ever "ls -al" is showing has _NOTHING_ to do with SAMBA. What matters is how the shares are setup in your **smb.conf** and how the permissions *_in there_* are set (per each share).

Thanks very much, I'll check that.

---

### Post by john stiles on 2009-08-15
> **jsast21 said:**
> 
root@alex-svr:/media# ls -lart
total 24
...
drwxrwxrwx  2 root root 4096 2009-08-15 15:10 store
...

Can samba read a linux file system or does it have to be fat16?

Samba is a Unix/Linux program so it can read their file systems yes. It's primary job is to manage this process between the Windows and Linux environments.

Have a read of the [* _Samba wiki_*]("http://en.wikipedia.org/wiki/Samba_%28software%29") to get a flavour of what it is doing. This is why I do not think that the format is the issue, particularly as you say that you can see the share.

You appear to have the root as the owner of the share. I recommend creating a user and changing the owner using [*_chown_*]("http://en.wikipedia.org/wiki/Chown")

I set up my Samba following this [*_guide_*]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by jsast21 on 2009-08-15
That was it, thanks. I added this: 

```

[public]
        comment = Public Share
        path = /path/to/share/point
        read only = no
        guest only = yes
        guest ok = yes

```

and adjusted the permissions and it worked perfectly!! thanks very much. I still have to play around with it a bit, but now at least I have a direction to go. Files are still coming up read only as soon as I edit them with vim, but I'm off to google to fix that little problem.

Thanks again.

Joe.

---

### Post by scorp123 on 2009-08-16
> **john stiles said:**
> sudo chmod **[COLOR="Red"]0777[/COLOR]** /media/samba
 Oh look ... a **_world-writable file share!!!!!_** Yippieeeh. :twisted:

Can you give me your IP address please? I have tons of illegal stuff I want to upload somewhere ....  Don't worry: they won't catch us. But if they do ... I mean you have a good lawyer, right? Oh well. Sorry I can't send you mine. I am in a totally different continent you see. But as I said, don't worry. Your world-writable share up there will surely give you tons of new friends ..... :twisted:

End of sarcasm.

That guide clearly says that the "chmod 0777" is only to be used for the section that is shared between all users and not as a "general rule of thumb". So the guide is good .... but you are misunderstanding and/or misquoting it and giving bad advice. Enabling world-writable shares definitely is NOT a good advice and NOT a good idea, especially if the people involved don't really seem to know what they are doing. You therefore should at least have mentioned the security considerations the author of that guide brings up (e.g. limiting SAMBA to a certain network) and so on.

Don't get me wrong. But opening up your filesystem via a "chmod 0777" is probably a bigger security gap than you realise. You should not suggest such things to people especially if you yourself don't really yet know why and how this command works and what exactly its implications are.

---

### Post by john stiles on 2009-08-18
Apologies to jsast21 and thanks Scorp123. I stand corrected, humbled and educated.

---

### Post by scorp123 on 2009-08-19
> **john stiles said:**
> Apologies to jsast21 and thanks Scorp123. Thank you as well -- that guide you posted really is good. Just yesterday I was able to use it. One our apprentices was tinkering with SAMBA and that guide just came in very handy. :)

---

