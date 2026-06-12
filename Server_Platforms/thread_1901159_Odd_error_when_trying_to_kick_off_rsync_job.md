---
title: "Odd error when trying to kick off rsync job"
date: 2011-12-27
forum: Server Platforms
---

### Post by Gizim on 2011-12-27
Trying to kick off a test rsync from my Ubuntu 10.04 server to a FreeNAS server, getting this error. Only thing I know is that the rsync version on the server is 3.0.7 and FreeNAS is 3.0.8


sudo rsync -azvv -e /home/user/webmin_1.570_all.deb [email]mailsync@freenas.local[/email]:/mnt/Store1

opening connection using: /home/user/webmin_1.570_all.deb -l mailsync freenas.local rsync --server --sender -vvlogDtprze.iLsf . /mnt/Store1
rsync: Failed to exec /home/user/webmin_1.570_all.deb: Permission denied (13)
rsync error: error in IPC code (code 14) at pipe.c(84) [Receiver=3.0.7]
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: error in IPC code (code 14) at io.c(601) [Receiver=3.0.7]

---

### Post by CharlesA on 2011-12-27
You are trying to execute a deb as the remote shell and that isn't possible.

Try it without the -e switch.

```
        -e, --rsh=COMMAND           specify the remote shell to use

```

---

### Post by Gizim on 2011-12-27
> **CharlesA said:**
> You are trying to execute a deb as the remote shell and that isn't possible.

Try it without the -e switch.

```
        -e, --rsh=COMMAND           specify the remote shell to use

```

I love you... now getting this



delta-transmission enabled
webmin_1.570_all.deb
rsync: mkstemp "/mnt/Store1/.webmin_1.570_all.deb.fmS2Jp" failed: Permission denied (13)
total: matches=0  hash_hits=0  false_alarms=0 data=14884300

sent 14889409 bytes  received 31 bytes  431577.97 bytes/sec
total size is 14884300  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
user@mail:~$

Seems like the username mailsync does not have access to right to Store1.. But i tried it with my admin account got the same error.

---

### Post by CharlesA on 2011-12-28
Do you have write access to /mnt/Store1/ with the user you are trying to rsync as?

---

### Post by Gizim on 2011-12-28
> **CharlesA said:**
> Do you have write access to /mnt/Store1/ with the user you are trying to rsync as?

Pretty sure...
humor me how can i check and how can i fix it if i don't?
The user is mailsync

---

### Post by rubylaser on 2011-12-28
Just look at the permissions on the directory, and see if the mailsync user is in any of them.

```
ls -la /mnt/ | grep Store1
```
```
groups mailsync
```

---

### Post by Gizim on 2011-12-28
> **rubylaser said:**
> Just look at the permissions on the directory, and see if the mailsync user is in any of them.

```
ls -la /mnt/ | grep Store1
```
```
groups mailsync
```

Figured it out 2 seconds after i posted
ls -la /mnt/ | grep Store1
drwxr-xr-x   2 root  wheel       2 Dec 21 11:30 Store1

In this case would i do a chown mailsync:mailsync /mnt/Store1

---

### Post by rubylaser on 2011-12-28
I'd make it recursive, but yes that will do it.
```
chown -R mailsync:mailsync /mnt/Store1
```

---

### Post by Gizim on 2011-12-28
> **rubylaser said:**
> I'd make it recursive, but yes that will do it.
```
chown -R mailsync:mailsync /mnt/Store1
```

It worked! Thank you sir

---

### Post by rubylaser on 2011-12-28
No problem, but the thanks goes to CharlesA, I just made sure you had your permissions set correctly :)

---

### Post by Gizim on 2011-12-28
> **CharlesA said:**
> Do you have write access to /mnt/Store1/ with the user you are trying to rsync as?

Also thank you :)

---

### Post by CharlesA on 2011-12-28
> **rubylaser said:**
> No problem, but the thanks goes to CharlesA, I just made sure you had your permissions set correctly :)

Nice job. :)

> **Gizim said:**
> Also thank you :)

Welcome. :)

---

