---
title: "passwd: Authentication token manipulation error"
date: 2012-02-07
forum: Server Platforms
---

### Post by maverickaddicted on 2012-02-07
Hello,

While trying to assign password to one of my user, I am getting this error message

```

serveradmin@openserver:~/LAMP$ sudo passwd salaryuser
passwd: Authentication token manipulation error
passwd: password unchanged

```I also tried this -

```

serveradmin@openserver:~/LAMP$ sudo mount -rw -o remount /
serveradmin@openserver:~/LAMP$ su root
Password:
root@openserver:/home/serveradmin/LAMP# passwd salaryuser
passwd: Authentication token manipulation error
passwd: password unchanged

```Can anybody help me?

---

### Post by maverickaddicted on 2012-02-08
bump

---

### Post by SeijiSensei on 2012-02-09
> **maverickaddicted said:**
> ```

serveradmin@openserver:~/LAMP$ sudo mount -rw -o remount /
```

That's not the correct syntax.  Use this instead:

```
sudo mount -n -o remount,rw /
```

Make sure there's no spaces in the "remount,rw" string.  The "-n" switch tells the OS not to try and rewrite /etc/mtab, which would be impossible since the filesystem is marked read-only.

If, however, the filesystem really is marked read-only, that means it has errors that need to fixed with fsck.  Once you've remounted the root filesystem as writable, run

```
sudo touch /forcefsk
```

and reboot.  That will force a filesystem check when the machine starts up again.

---

### Post by maverickaddicted on 2012-02-10
> **SeijiSensei said:**
> That's not the correct syntax.  Use this instead:

```
sudo mount -n -o remount,rw /
```Make sure there's no spaces in the "remount,rw" string.  The "-n" switch tells the OS not to try and rewrite /etc/mtab, which would be impossible since the filesystem is marked read-only.

If, however, the filesystem really is marked read-only, that means it has errors that need to fixed with fsck.  Once you've remounted the root filesystem as writable, run

```
sudo touch /forcefsk
```and reboot.  That will force a filesystem check when the machine starts up again.

Sorry, but this didn't work. I am getting same error.

---

### Post by SeijiSensei on 2012-02-10
So did the system run fsck at boot?  What does mount say about the root filesystem?  Is it marked as rw?

How about this? 
```
ls -l /etc/passwd /etc/group/ /etc/shadow
```

passwd and group should be owned by root:root and have 644 permissions.  /etc/shadow is owned by root:shadow on my system with 640 permissions.  It should also work if shadow is owned by root:root with 600 permissions.  I've actually not seen the use of a "shadow" group before, but I'm more used to RedHat flavors when it comes to these details.

---

### Post by maverickaddicted on 2012-02-11
Yes, system ran the file check on boot. Here is the output of that command -

```

serveradmin@openserver:~$ ls -l /etc/passwd /etc/group /etc/shadow
-rw-r--r-- 1 root root   1200 2012-02-08 18:17 /etc/group
-rw-r--r-- 1 root root   2648 2012-02-08 18:17 /etc/passwd
-rw-r----- 1 root shadow 1648 2012-02-08 18:17 /etc/shadow

```

---

### Post by winh8r on 2012-02-11
Make sure the username in /etc/shadow is exactly the same as the username in /etc/passwd.

Quite often the cause of this problem when they are different.




If you are running likewise-open then please take a look here at a known bug and a workaround::

[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/302026]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/302026")

---

### Post by maverickaddicted on 2012-02-12
I am not running likewise open. Also, /etc/shadown file contains

```
salaryuser:!:15377:0:99999:7::
```

and /etc/passwd file contains

```
salaryuser:x:1001:33:Salary User,,,:/home/serveradmin/LAMP/nexus_salary/:/bin/bash
```

---

### Post by maverickaddicted on 2012-02-15
Still looking for some solution.

---

### Post by maverickaddicted on 2012-02-16
](*,)](*,)

---

### Post by maverickaddicted on 2012-04-12
:mad:

---

