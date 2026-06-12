---
title: "[SOLVED] RSA Host Key Change error on client"
date: 2008-06-07
forum: Server Platforms
---

### Post by Jeztastic on 2008-06-07
Hi

I just updated my server, and apparently the ssh key needed changing. I now cannot get into the server from the client. How do I change the key file for the client?

Thanks!

---

### Post by .nedberg on 2008-06-07
Remove them on the client.

```
rm -rf ~/.ssh
```

or just rename them```
mv ~/.ssh ~/.ssh_old
```

Then try to connect

---

### Post by Jeztastic on 2008-06-07
Nope...

```
jez@jez-laptop:~$ rm -rf ~/.ssh
jez@jez-laptop:~$ sudo ssh jez@192.168.1.68
[sudo] password for jez: 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
7c:8d:2d:f4:48:ef:c5:50:c2:91:c7:0f:aa:7c:02:4e.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:1
RSA host key for 192.168.1.68 has changed and you have requested strict checking.
Host key verification failed.
```

---

### Post by Monicker on 2008-06-07
The error tells you which file has the key information which is now mismatched.

Delete the first line of the file /root/.ssh/known_hosts.

---

### Post by Jeztastic on 2008-06-07
No, that's not done it either, still getting the same error. :(

---

### Post by quelx on 2008-06-07
As Monicker point out
> Offending key in /root/.ssh/known_hosts:1
filename:linenumber
known_hosts:1

```
sudo nano -w /root/.ssh/known_hosts
```

**CTRL-k** to delete the first line, **CTRL-x** to save and exit

---

### Post by Jeztastic on 2008-06-07
Thanks, that did it. I was trying to edit through gedit, obviously wasn't doing it right. 

:)

---

