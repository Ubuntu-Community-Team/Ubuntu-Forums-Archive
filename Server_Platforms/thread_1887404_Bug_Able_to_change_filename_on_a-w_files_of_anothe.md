---
title: "Bug? Able to change filename on a-w files of another user"
date: 2011-11-26
forum: Server Platforms
---

### Post by halitus87 on 2011-11-26
Hi

I have just setup a NAS running ubuntu server 11.10 with a 3 drive array.

I have a dropbox folder where users can dump things which will be "published" on the NAS. I plan to set the perms of the directory to +w but every 24 hours ill set the perm -w to .../NAS/* I will also Chown it to root.

However when i set these perms I can still rename the files. I correctly an unable to delete or move the files.

This happens both locally and via samba.

Is this a bug? It seams like a security risk as I am trying to write protect my files and some one can come and rename everything.



On a side note which I would also like an answer for is why I can set a file u+rx-w and still be able to delete it if I am the owner? 

Thanks all

Halitus

---

### Post by SeijiSensei on 2011-11-27
I believe the answer is that the operations you're performing are actually happening at the directory level.  What are the permissions on the directory that contains the file?  I just created a test file in a directory I owned with u+w permissions.  Then I applied u-w to the directory.  I couldn't then rename the file even though I own it and have write permissions to it.

---

### Post by halitus87 on 2011-11-28
Hi yes that is what i suspected.

What I am trying to do is create the dropbox folder than people can add files to but then cant delete them or do anything to them.

Hence the cron job to set -w on all the files but not the dir.

Any ideas? 

PS It seams strange to me that the dir perm control file renaming.

Halitus

---

### Post by SeijiSensei on 2011-11-28
> **halitus87 said:**
> What I am trying to do is create the dropbox folder than people can add files to but then cant delete them or do anything to them.

The "[sticky bit]("http://en.wikipedia.org/wiki/Sticky_bit")" can enforce some of these restrictions, but the file's owner will still be able to delete or rename her own files.  However it will block users from deleting or renaming other users' files, even if they all have write permissions to the directory itself.

---

