---
title: "Working an creating an appliance - cant logon to system"
date: 2013-02-04
forum: Security
---

### Post by rushinblue on 2013-02-04
I was working on adding a profile.d script to this server and now I can't log on to the system and run commands. How can I delete the /etc/profile.d/ folder?

Thanks

ubuntu server

---

### Post by cariboo on 2013-02-05
You'll have to connect a monitor and keybaord to the system, then boot in recovery mode. Once at the root prompt type the following command to mount the / partition in read/write mode:

```
mount -o remount,rw /
```

you should now be able to delete any files and directories that you need to.

---

### Post by rushinblue on 2013-02-05
Awesome! That worked. I noticed while trying to do other things in recovery mode that it had changed from previous versions and that appeared to be in readonly mode

---

