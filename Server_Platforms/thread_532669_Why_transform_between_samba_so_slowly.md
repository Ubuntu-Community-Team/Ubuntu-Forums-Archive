---
title: "Why transform between samba so slowly?"
date: 2007-08-23
forum: Server Platforms
---

### Post by bob.xiao on 2007-08-23
The samba server is running on RHAS4 machine in the same LAN, and I mount remote as local directory. When copy file from remote file to local, the speed is about 500Kb/s.

So, what's up?

---

### Post by jakev383 on 2007-08-23
Are you mounting the machine as a SMBFS or CIFS?  CIFS will improve the speed if you have not already tried it.  Here's how I mount a home share:
```

//192.168.76.1/HomeShare /media/HomeShare cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0

```

---

