---
title: "no such file or directory error"
date: 2011-05-11
forum: Server Platforms
---

### Post by v1ad on 2011-05-11
rcon@li121-251:~/b3$ ./b3_run.py
: No such file or directory
rcon@li121-251:~/b3$ l;
CHANGELOG              b3/           ez_setup.py*     setup.py*
ChangeLogDetailed.txt  b3.egg-info/  listversions.py  setupPy2exe.py
MANIFEST.in            b3_debug.py*  logs/            update*
PKG-INFO               b3_run.py*    py2exe_builder/  versions.txt
README.md              cache/        setup.cfg        xlr sql/
rcon@li121-251:~/b3$

as you can see up top it gives me an error when i try to run the file. it is a Ubuntu error and i don't what the heck is causing it. had it before but don't remember how i resolved it.

---

### Post by Ryan Dwyer on 2011-05-11
What is l? A bash alias for ls? What do the asterisks mean?

Is the file executable? chmod +x b3_run.py

---

### Post by v1ad on 2011-05-11
the file is executable, thats what the asterisks are for. i set the alias for l something like ls -als , forgot already.

---

### Post by paulm23 on 2011-05-11
Is it executing python for that file?

What's the shebang?

head -n1 b3_run.py

Paul.

---

### Post by v1ad on 2011-05-11
it is executing python.
#!/usr/bin/env python
 the problem is when i actually try to run the script. ubuntu does not see it. (or so i think)

---

### Post by paulm23 on 2011-05-11
yes, but the "No such file or directory" could actually be coming from the script!

If python isn't working then you'll get that error, through I'd expect "/usr/bin/env: python: No such file or directory".  But I'm guess it's not that, as python is installed by default.  Do you have execute permission on the home volume?

mount -v

and look for noexec for the mount.

Paul.

---

### Post by v1ad on 2011-05-11
don't think it's that, maybe it cant find python under that directory?


rcon@li121-251:~$ mount -v
/dev/xvda on / type ext3 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
/dev on /dev type devtmpfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
rcon@li121-251:~$

---

### Post by v1ad on 2011-05-11
problem seems to be that it can't find the interpreter under /usr/bin/env considering the env directory does not exist.

env seems to be some kind of file..

---

### Post by v1ad on 2011-05-13
bump?

---

