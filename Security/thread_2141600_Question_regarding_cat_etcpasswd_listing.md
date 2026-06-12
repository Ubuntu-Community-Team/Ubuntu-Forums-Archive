---
title: "Question regarding cat /etc/passwd listing"
date: 2013-05-03
forum: Security
---

### Post by intransit on 2013-05-03
when I invoke

cat /etc/passwd

some accounts have hashes, some have a * in that place

I was hoping to get an explanation why some have the password hash and some have the *

is it because the ones with hashes are actually set, and in use?

also

if you're looking for an obvious backdoor, is netstat (and well sniffing traffic perhaps) the most obvious and straight forward ways to start. (I have been given a vmware image with an iso pre-installed, the source is trustworthy, but I am paranoid).

(...Is some one going to now say, i'm wasting my time because if someone went to the effort, they would have rootkit all those commands and hidden it anyway...)

Thanks!

---

### Post by TheFu on 2013-05-03
```
cat /etc/passwd
```
shouldn't show any hashes.  The hashed passwords should be inside the /etc/shadow file (if not stored elsewhere thanks to PAM) and not available to non-root userids for viewing.

---

### Post by schragge on 2013-05-03
You can convert you system to use shadow passwords with [pwconv](http://manpages.ubuntu.com/manpages/raring/en/man8/pwconv.8.html)

---

### Post by slickymaster on 2013-05-03
TheFu is absolutely right. 

Encripted passwords are not stored in **/etc/passwd** file. They are stored in **/etc/shadow** file. In the good old days there was no great problem with this general read permission. Everybody could read the encrypted passwords, but the hardware was too slow to crack a well-chosen password, and moreover, the basic assumption used to be that of a friendly user-community.
Almost, all modern Linux / UNIX line operating systems use some sort of the shadow password suite, where **/etc/passwd** has asterisks (*) instead of encrypted passwords, and the encrypted passwords are in **/etc/shadow** which is readable by the superuser only.

---

### Post by Stonecold1995 on 2013-05-04
What does your /etc/passwd look like?  If it actually has hashes of course remove them before posting!

Mine starts like this.
```
alex@kubuntu:~$ head -5 /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
```

If it looks like this on the other hand, then that's suppose to be in /etc/shadow, not /etc/passwd!  If that's the case then that's a problem, but I have no idea what caused it.
```
root@kubuntu:~# head -5 /etc/shadow
root:*:15656:0:99999:7:::
daemon:*:15504:0:99999:7:::
bin:*:15504:0:99999:7:::
sys:*:15504:0:99999:7:::
sync:*:15504:0:99999:7:::
```

As for what the * is, that's in /etc/shadow.  You can find information about that by running the command "man shadow".  According to the man page:
> If the password field contains some string that is not a valid result of crypt(3), for instance ! or *, the user will not be able to use a unix password to log in (but the user may log in the system by other means).

---

