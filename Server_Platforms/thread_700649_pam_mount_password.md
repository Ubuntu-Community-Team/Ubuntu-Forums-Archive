---
title: "pam_mount password"
date: 2008-02-18
forum: Server Platforms
---

### Post by cmdln on 2008-02-18
[SOLVED]
I am trying to get pam mount to mount some cifs shares upon user login. It seems that pam_mount is not passing the password off to volumes.
for example I have a line like this
<code>
volume user cifs serverip share /home/user/share user=user,uid=user - -
</code>

I get errors when using a line like that
<code>
Feb 18 14:10:41 ubuntu kernel: [55499.235069]  CIFS VFS: Send error in SessSetup = -13
Feb 18 14:10:41 ubuntu kernel: [55499.368386]  CIFS VFS: cifs_mount failed w/return code = -13
Feb 18 14:10:41 ubuntu kernel: [55499.407393]  CIFS VFS: Send error in SessSetup = -13
Feb 18 14:10:41 ubuntu kernel: [55499.540075]  CIFS VFS: cifs_mount failed w/return code = -13
</code>
If I specify the users password on the line it does seem to work, but that kind of defeats the purpose.
<code>
volume user cifs serverip share /home/user/share user=user,password=pass,uid=user - -
</code>

I have added @include common-pammount
to /etc/pam.d/gdm, and pam_mount does ask me to reenter my password. So it looks like pam_mount should be getting the password. Any ideas why its not passing it on to volume? Am i missing something?

---

### Post by stevethemachine on 2008-04-30
> **cmdln said:**
> I am trying to get pam mount to mount some cifs shares upon user login. It seems that pam_mount is not passing the password off to volumes.
for example I have a line like this
<code>
volume user cifs serverip share /home/user/share user=user,uid=user - -
</code>

I get errors when using a line like that
<code>
Feb 18 14:10:41 ubuntu kernel: [55499.235069]  CIFS VFS: Send error in SessSetup = -13
Feb 18 14:10:41 ubuntu kernel: [55499.368386]  CIFS VFS: cifs_mount failed w/return code = -13
Feb 18 14:10:41 ubuntu kernel: [55499.407393]  CIFS VFS: Send error in SessSetup = -13
Feb 18 14:10:41 ubuntu kernel: [55499.540075]  CIFS VFS: cifs_mount failed w/return code = -13
</code>
If I specify the users password on the line it does seem to work, but that kind of defeats the purpose.
<code>
volume user cifs serverip share /home/user/share user=user,password=pass,uid=user - -
</code>

I have added @include common-pammount
to /etc/pam.d/gdm, and pam_mount does ask me to reenter my password. So it looks like pam_mount should be getting the password. Any ideas why its not passing it on to volume? Am i missing something?

I also have notices the same issue.  I thought it was me not understaning how to us pam_ount.conf.xml then had the thought to try and stick the password in the file.  

As you say, defeats the point of pam mount and is worse then using fstab and credentials file.

If anyone knows how to get pam to pass the password to the cifs share, please let us know.

---

### Post by stevethemachine on 2008-05-01
Installing smbfs seemed to fix it for me.

I had decided to try and use /etc/fstab credentials files and this was not working as well.  Some one mentioned "apt-get install smbfs" which installs mount.cifs and this fixed my credentials problem.

I had assumed that mount.cifs was installed since I was able to manuall mount with "mount -t cifs" commands.  However installing smbfs also corrected the pam_mount problems of not picking up the password from authentication.

I now have a working pam_mount to mount remote home directories.  Pam_mount does not appear to Unmount the directory upon logout though.

---

### Post by cmdln on 2008-05-01
Yeah I forgot I had posted that here. I also have to install smbfs and it started working.

---

