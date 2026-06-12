---
title: "cannot rm directory? or change permissions?"
date: 2010-05-27
forum: Server Platforms
---

### Post by gobbledigook on 2010-05-27
hey!

um... this is probably obvious, but i'm having issues with a folder which I cannot write to or seem to do anything else with? i figured i'd delete it and start again but i can't even do that!!

```
server@server:~$ sudo chown server /media/server/swap/downloads/incomplete/
chown: changing ownership of `/media/server/swap/downloads/incomplete/': Operation not permitted
server@server:~$ sudo chmod 777 /media/server/swap/downloads/incomplete/
chmod: changing permissions of `/media/server/swap/downloads/incomplete/': Operation not permitted
server@server:~$ sudo rm -r /media/server/swap/downloads/incomplete/
rm: cannot remove directory `/media/server/swap/downloads/incomplete': Directory not empty
server@server:~$ sudo ls /media/server/swap/downloads/incomplete/
server@server:~$ sudo ls -l /media/server/swap/downloads/incomplete/
total 0
```

any help appreciated :)

---

### Post by jd65pl on 2010-05-27
Tell us who the owner and group are
```
\ls -l /media/server/swap/downloads/incomplete
```

Tell us what is in it
```
\ls -la /media/server/swap/downloads/incomplete/
```

---

### Post by gobbledigook on 2010-05-27
hi, thanx for your reply :) 

```
server@server:~$ \ls -la /media/server/swap/downloads/incomplete/
total 0
server@server:~$ \ls -l /media/server/swap/downloads/incomplete
total 0

```

---

### Post by arrrghhh on 2010-05-27
I've only seen that error related to non-Linux partitions, like NTFS... Is this an NTFS-formatted or FAT-formatted partition?

```
sudo mount
``` if you're not sure.

Oh, and if you do an rm -rf, it'll *probably* work.  Let me know if that doesn't.

---

### Post by CharlesA on 2010-05-27
You can try to see what the owner/permissions are by running this:

```
ls -ld /media/server/swap/downloads/incomplete/
```

---

### Post by Defrector on 2010-05-27
I've had similar issues when the connection to whatever is mounted got sketchy or when the mounting itself got sketchy.

Try unmounting that media and re-mounting it. If it won't unmount or tells you it is already mounted when you try to re-mounted and you know you "successfully" unmounted it, then you know that something's glitchy. In that case try rebooting (it might even hang on reboot), remount, and try again.

---

