---
title: "how to check if mount.cifs will need a password?"
date: 2011-11-12
forum: Server Platforms
---

### Post by thinking on 2011-11-12
hi,

i have a daemon running which automatically mounts cifs shares using /etc/fstab entries
but one of those entries also needs a password which i dont have access to
the problem is that the daemon tries to mount resulting in an error (13 - permission denied) which makes sense
so i want to prevent the error message (which also is logged to dmesg kernel log)
i thought about overriding some error logging value but mount.cifs dont seem to have one

any other idea's how i can check if a fstab entry will need a username/password key OR how i can check if a fstab entry will fail to mount in case of my automated daemon so i can prevent flooding my error log?

thx

---

### Post by thinking on 2011-11-12
one possiblity i found is using smbclient like this
smbclient -N -c "cd ." -U username [my fstab based smb server]

---

