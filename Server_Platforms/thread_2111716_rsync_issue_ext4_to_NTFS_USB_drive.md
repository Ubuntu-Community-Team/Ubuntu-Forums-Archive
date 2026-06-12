---
title: "rsync issue ext4 to NTFS USB drive"
date: 2013-02-02
forum: Server Platforms
---

### Post by lseg on 2013-02-02
Hello,

I am trying to do a cron with rsync, to bakup a certain folder to a NTFS formatted USB Harddisk

I use rsync -av .. .. for this.
Although nothing was changed in the source directory, I get following result:
a huge list of directories and subdirectories, followed by:
sent 2173361 bytes  received 136330 bytes  90576.12 bytes/sec
total size is 134506888816  speedup is 58235.88

I think that for some reason, the directory information do not match and are being updated. Or maybe rsync is just too verbose.
How can I avoid this.

Reason I want to avoid this, is because now the log is cluttered with all the directories, and I do not see what was really backed up.

Kind regards,

Luc

---

### Post by darkod on 2013-02-02
I don't know if that is the problem, but NTFS can't hold linux permissions. So, when doing the comparison it might consider everything as new.

---

### Post by SeijiSensei on 2013-02-02
If you must back up to an NTFS device, you'll need to create a "tarball" of the directory or directories you wish to back up, then write the tarball to the NTFS drive.

Suppose, for instance, you want to back up /home/julie and /var/www.  You would run these commands:
```

cd /
tar cjvpf backup.tar.bz2 home/julie var/www

```
Then copy backup.tar.bz2 to the NTFS drive.  

If you only intend to use the USB drive for Linux backups, I recommend replacing NTFS with ext4 by reformatting the device.  You can do this by running something like gparted, deleting the existing partition, and recreating it as a Linux partition with ext4.  Then you can use rsync as you intended.

---

### Post by CharlesA on 2013-02-02
> **SeijiSensei said:**
> 
If you only intend to use the USB drive for Linux backups, I recommend replacing NTFS with ext4 by reformatting the device.  You can do this by running something like gparted, deleting the existing partition, and recreating it as a Linux partition with ext4.  Then you can use rsync as you intended.

This. If I remember right, NTFS handles timestamps differently than a file system like EXTx. I've run into a similar issue with robocopy and backing up to my file server where the timestamps were off, so the program would copy everything again. I don't know if there is a switch but I did find this:
[http://serverfault.com/questions/291818/linux-ntfs-to-ntfs-rsync-repeatedly-recopying-files](http://serverfault.com/questions/291818/linux-ntfs-to-ntfs-rsync-repeatedly-recopying-files)

Also +1 to creating a tarball if you are going to be storing the data on a NTFS drive. Even if you use rsync, it will not know what permissions the original file/folder had, so if you need to restore it, you would need to figure that out for yourself.

---

### Post by lseg on 2013-02-03
Problem is that I need to use the backup on a Windows PC.
So formatting it to Ext4 would not be an option.

Also using Tar is not really an option, since then I have to backup everything every time, which is rather pointless.

The folder I am backing up only has 1 type of permission (it is a samba share drive).

Apparently it is updating all directories, although it does not update the content of the directories. Maybe it is because of the difference in permissions, but why is it not updating the files then (they also have different permissions)?

For me this makes the output list rather unreadable, I have to scroll through 728 KB of directory listings, to find the 1 or 2 files which were backed up. Which is a pitty. Maybe I can output the result to an output file and the do a grep in this file and output that instead.

Please advice,

Kind regards,

Luc

---

### Post by sudodus on 2013-02-03
It may be worth testing a driver, that helps Windows read linux ext file systems according to this link

[[COLOR="Red"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

So you can use ext4, which makes rsync work properly with the permissions on the file level, and at the same time, you can use the files in Windows.

---

### Post by sudodus on 2013-02-03
> **lseg said:**
> Also using Tar is not really an option, since then I have to backup everything every time, which is rather pointless.

tar has an update function, see
```
info tar
```
where you can find
```

     tar [-] A --catenate --concatenate | c --create | d --diff --compare |
         --delete | r --append | t --list | --test-label | [COLOR="Red"]u --update[/COLOR] | x
         --extract --get [options] [pathname ...]
...
     -u, --update
           only append files newer than copy in archive
```

---

### Post by SeijiSensei on 2013-02-03
> **lseg said:**
> Problem is that I need to use the backup on a Windows PC.
So formatting it to Ext4 would not be an option.

Then why not write the backup on the Windows side with something like xcopy?

---

### Post by CharlesA on 2013-02-03
> **SeijiSensei said:**
> Then wny not write the backup on the Windows side with something like xcopy?

Robocopy works too. ;)

But yeah +1 to that because that is what I do when I am backing up my Windows desktops.

robocopy script to network drive on my server then I backup the server to external media.

@OP: Without knowing more of what you want to accomplish or how your environment is set up, the best we can do is provide solutions we use that may not work for you.

---

### Post by lseg on 2013-02-04
Automating a backup is much easier on the Linux system, which I use as a NAS (and is always on, which is not the case for the windows PC). 

From a practical point of view it is easier for me if the USB drive is attached to the NAS instead of the windows PC.
This USB drive is more a backup, when the Linux System/NAS would fail. This way I could attach the USB drive to the WindowsPC (I have 2 USB drives which I swap from time to time, 1 is in the NAS, 1 is inactive at work).
This ext4 driver for windows would be an option. But I prefer to stick to NTFS, since that will always work with Windows PCs. And eventually the backup (if needed) would be used on a Windows PC.

Since the main problem for me was the text file, I just piped the results from rsync to a txt file and grepped the results I wanted (basically filtering all lines ending on /, which are directory updates).

For me this is good enough, not ideal. It is this, or formatting to Ext4.

Kind regards,

Luc

---

### Post by CharlesA on 2013-02-04
Isn't the whole point of having a NAS is to use it to store your files? If it goes down you can rebuild it and gain access to your files again. If that is not an option, or if you need to access your files quickly, a *nix livecd works wonders.

Personally I would stick to using ext4 and leave Windows out of the picture.

---

