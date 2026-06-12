---
title: "Unwanted Security"
date: 2009-12-26
forum: Security
---

### Post by Silvernail on 2009-12-26
Recently one morning my laptop (running HH with all updates) woke up and said it was going to die. Its hard drive was failing.
I plugged in my USB external hard drive and using the 'file browser' that came up, copied my laptop 'home' directory to a directory on the external HD.

Plugged the HD into my desktop ( running a new install of 9.10). Now I have lock icons on a lot of the applications/files  laptop directory in the hard drive.

I would like to get  rid of all this unnecessary safe guarding. It gets frustrating. For  instance the following occured 10 minutes ago.
```
 cp /media/Teragb/laptop/signatures . 
``` 
```
gedit signatures
Cannot access 'signatures' You do not have permission.
```

I am the only one on this computer. I am the only person living in this house. I live on the back side of 40 acres. It is a 2 rut dirt road to the mail box. No one is going to get into my computer unless  they kill me during a break in.

I don't mind using 'sudo' to do some of the stuff with 'bin' 'sbin' file. How do I turn the other safe guards off?

---

### Post by CharlesA on 2009-12-26
You can't turn off permissions unless you set them to something to 777 (rwx to everyone). The permissions that were set were from the other machine. You can change them by running chown user:user and chmod.

---

### Post by RabidSpatula on 2009-12-27
You probably don't want to turn them off anyway. It's not just physical security (anyone with physical access can boot from a USB key and get access as root anyway) to consider, but application security too. A script run as a user will not trash your core system.

But... if you are absolutely intent on eliminating security, you can always just set a root password and log in as root. From there, security doesn't matter. Generally, that's a really bad idea tho.

Now, odds are the problem you have is caused by your current user not owning the files you're trying to access. This can happen when you're working with stuff that's backed up to an external harddrive when permissions are copied too. Permissions are set by the userID, and if the uid is different between installs... well, this happens. Been there, which is why I now format my backup externals to NTFS to explicitly avoid storing any permissions.

The fix for this is to gksudo nautilus (the file browser), then copy-paste (or use grsync/sync) and copy the files back to your desktop's drive. Once there you can chown and chgrp the files to your heart's content and give ownership back to the intended user. If you don't want to copy the files back, you can chown the stuff on the external drive... but if something goes wrong you won't have the originals to rely on.

---

### Post by Silvernail on 2009-12-28
OK, thanks for the feedback.

I'll have to think on this for a few day.

Dave

---

