---
title: "It is possible that someone is doing something nasty!"
date: 2009-10-20
forum: The Cafe
---

### Post by GreenDance on 2009-10-20
Hi, I've installed Ubuntu 9.04 Minimal in a VirtualBox, along with LAMP-Server & SSH...

I'm trying to SSH into it from the terminal on the same PC, below is the error msg I'm getting :(, please can someone help, thank you

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
[key removed]
Please contact your system administrator.
Add correct host key in /home/snow/.ssh/known_hosts to get rid of this message.
Offending key in /home/snow/.ssh/known_hosts:1
RSA host key for 192.168.0.5 has changed and you have requested strict checking.
Host key verification failed.

---

### Post by days_of_ruin on 2009-10-20
You must have ssh'd into a computer with the same local IP address before. Just delete the first line in your ~/.ssh/known_hosts file.

---

### Post by GreenDance on 2009-10-20
> **days_of_ruin said:**
> You must have ssh'd into a computer with the same local IP address before. Just delete the first line in your ~/.ssh/known_hosts file.

it still doesn't work :(

---

### Post by Excedio on 2009-10-20
> **days_of_ruin said:**
> You must have ssh'd into a computer with the same local IP address before. Just delete the first line in your ~/.ssh/known_hosts file.
 
I deleted the entire known_hosts file and it solved the problem for me.
 
> **GreenDance said:**
> it still doesn't work :sad: 
 
Try deleting the whole file and then connecting. It will then create a brand new RSA Key.

---

### Post by The Real Dave on 2009-10-20
Beware, deleting the whole file will get rid of any other known hosts, and if you have ssh without keys set up for another ip address, could cause problems :) 

The 1 in this line "Offending key in /home/snow/.ssh/known_hosts:1" shows that its just the first line in that file is causing the conflict. Open the file in an editor like nano, it shows the lines better than gedit does

```
sudo nano /home/snow/.ssh/known_hosts
```

---

### Post by GreenDance on 2009-10-20
Hi, I deleted the whole file, still didn't work, so I've reinstalled ubuntu on my pc, reinstalled virtualbox then installed ubuntu on there and it's working now :)

---

