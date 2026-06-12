---
title: "tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share na"
date: 2008-04-11
forum: Server Platforms
---

### Post by cocotu on 2008-04-11
I'm trying to follow the steps at: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
and I get this error:
4708: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

when I do the step: smbmount //myserver/myshare ~/mnt

I tried:
1. sudo
2. my home dir: //myserver/home/<user>/myshare
3. /myshare & /mnt are in my home dir
4. I tried: mount -t smbfs and same error.

Any ideas?, thanks!

---

### Post by cocotu on 2008-04-11
I had:
[homes]
   comment = Home Directories
   browseable = yes
and:
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

commented out. thanks, but I'm still not sure why that command didn't work.

---

