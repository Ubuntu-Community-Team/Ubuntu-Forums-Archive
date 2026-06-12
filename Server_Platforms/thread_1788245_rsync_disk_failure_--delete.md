---
title: "rsync disk failure --delete"
date: 2011-06-22
forum: Server Platforms
---

### Post by ene_dene on 2011-06-22
I have two data hard drives on my Linux server and I use second as a backup for a first drive.
I use rsync for that purpose. An example would be:
```
rsync -r -v --delete /media/disk1/ /media/disk2/
```
What this does is that it copies every file/directory from /media/disk1/ to /media/disk2/ but also deletes any difference. For example, lets say that files A and B but not file C are on disk1, and on disk2 there is no A and B files, but there is C. The result would be that after the command on disk2 I'd have files A and B, but file C would be deleted, just like on disk1.

Now, a rather disastrous scenario had crossed my mind; what if disk1 dies, system continues to work since system files are on my system disk, but when rsync tries to backup my data on disk2 from broken disk1, it deletes all the files from disk2 because it can't read anything on disk1.

rsync manual states:
"If the sending side detects any I/O errors, then the deletion of any files at the destination will be automatically disabled. This is to prevent temporary filesystem failures (such as NFS errors) on the sending side from causing a massive deletion of files on the destination. You can override this with the --ignore-errors option."

But does this protect me from any probable scenario? Once I had 2 disks in LVM, one died, system continued to work, I could connect to disk, part of data was there, directory names where there, although some where empty (and they shouldn't have been)... Would rsync detect that or would I lose my data if lvm disk was disk I was backing up? Would "--delete" delete files from my backup disk in that case?

---

### Post by a2j on 2011-06-22
would raid1 work better for you?

---

### Post by ene_dene on 2011-06-22
> **a2j said:**
> would raid1 work better for you?
Perhaps it would, but for now as system is set right now I can't go to that sort of change.

---

### Post by Lars Noodén on 2011-06-22
I would look at using -a (or --archive) for the copying.  

As far as --delete goes, what about --delete-after ?  That way nothing gets deleted till the end, giving I/O errors a chance to be dealt with.

---

### Post by dtfinch on 2011-06-22
There's the --backup-dir option to save everything that's deleted to another folder. Though you'd have to move your backup destination to a subfolder of disk2 rather than its root to have both the backup and the deleted items on the same disk.

You could also store your backup script on disk1, so that if it fails, the backup doesn't happen. Or have the script check for the existence of a certain file on disk1. You may also want to verify that disk2 is mounted to avoid filling your root if it isn't.

---

### Post by YesWeCan on 2011-06-22
I use rsync just because the external drive I use isn't big enough to allow me to back up properly using a tool like "Simple Backup" (in the Software Centre). I would use this, otherwise. I run the rsync -avR --delete manually so I know what it is doing.

---

