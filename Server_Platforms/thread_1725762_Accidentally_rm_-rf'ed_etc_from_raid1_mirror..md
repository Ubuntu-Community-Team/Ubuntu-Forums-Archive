---
title: "Accidentally rm -rf'ed /etc from raid1 mirror."
date: 2011-04-10
forum: Server Platforms
---

### Post by sinjanepal on 2011-04-10
Hi, 
I accidentally rm -rf 'ed /etc directory from the main server. The server has raid1 soft-raid. 
Is there a way to recover the directory.

Thanks in advance.

---

### Post by ian dobson on 2011-04-10
Hi,

Recover from your backup. RAID is not the same as a backup, in the same second as you deleted /etc on one drive, it was deleted on the other.

Regards
Ian Dobson

---

### Post by sinjanepal on 2011-04-10
I configuring backup but accidentally deleted the main /etc directory. So I don't have any backup. 
Is there a way to recover the files.

---

### Post by eskuge on 2011-04-10
Short answer: No
Long answer: [http://www.linuxforums.org/forum/newbie/69673-not-possible-recover-files-deleted-using-rm.html](http://www.linuxforums.org/forum/newbie/69673-not-possible-recover-files-deleted-using-rm.html)

In that link there is some talk about tools that can be used as long as the secotrs havnt been touched since etc was deleted.

---

### Post by elico on 2011-04-10
well it depends if your data was overwritten already
(most cases if you shut down the system on the second there is still a chance to restore some data)
and also it depends on what raid-1 you were using...

so if you indeed shutdown the computer on the spot and you have someone to pay for to do the job or a good software that supports raid restore you will might have a slight chance.
i had a server that the data just "gone" without a reason in the middle of the day while using rsync to a remote computer.
the rsync was working and replicating files to the remote computer and then: boom errors on rsync.
ls ...
disaster there is no single file in the directory.
restart the machine... wont boot.
connecting the drive to another running machine and ... almost all the filesystem was gone.
so i tried various of recovery software (ext4) and the only one that gave my results was
UFS explorer.
it wasn't a raid but a raw ext4 fs but i know they have raid module.

it restored for me almost any file i needed and the only thing i had to break my head on is:
which "inode???"(number) is what directory in the root FS.
means i had couple directories named "inode???".
so now i have a newly installed server with almost everything restored from the old one.

---

