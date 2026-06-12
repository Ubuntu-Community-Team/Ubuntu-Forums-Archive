---
title: "Restrict User to Home and Links (FTP)"
date: 2009-03-14
forum: Server Platforms
---

### Post by lvleph on 2009-03-14
I have vsftp and I set things up so that my fpt users can only move around their home directory. However, this causes some problems because I have symbolic links to other directories and cannot access those directories.

So my question; how do I restrict users to their home directories and allow them to get into linked directories?

vsftpd.conf
```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_world_readable_only=NO
dirmessage_enable=YES
xferlog_enable=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

Any suggestions are welcome.

---

### Post by lvleph on 2009-03-15
Bump.

---

### Post by lloyd_b on 2009-03-15
As you've discovered, having them in a chroot'ed environment makes it impossible for them to access symlinks that point to outside of the "jail" (or "gaol" if you prefer).

You *can* bypass this:```
mount --bind oldir newdir
``` can be used to remount a directory from outside the jail to a point under their home directory, and they will have access to that directory (and any subdirectories it may have).

"man mount" for more details.

You can have these automatically mounted by adding an appropriate line to the file "/etc/fstab", or have a script that is run (as root) that mounts all of them at once.  

Lloyd B.

---

### Post by lvleph on 2009-03-15
So instead of sym linking I just mount it. This will require me to mount the same folder in all of my users home folders. And I have 6 different folders I have to do this for. hmmmm.

---

### Post by lloyd_b on 2009-03-15
> **lvleph said:**
> So instead of sym linking I just mount it. This will require me to mount the same folder in all of my users home folders. And I have 6 different folders I have to do this for. hmmmm.
Yes - working around a chroot can be a pain.  Unless you can identify somewhere else that they all have access to and mount them there (I'm not familiar with vsftp, so I don't know how it organizes the chroot).  There *has* to be a common area for the "/bin" directory, if nothing else...

Lloyd B.

---

