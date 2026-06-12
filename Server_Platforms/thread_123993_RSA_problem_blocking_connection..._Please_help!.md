---
title: "RSA problem blocking connection... Please help!"
date: 2006-01-31
forum: Server Platforms
---

### Post by chugru on 2006-01-31
Hi All...

I'm new with kubuntu and I have the following setup:
---Linksys Router
---WindowsXp pc, gentoo box, and new kubuntu box using the router and all 3 communicating with each other  by SSH
---Remote gentoo laptop trying to connect at will to either gentoo box or kubuntu box via internet

Problem: My laptop connects via internet to my gentoo box on port 22 without problem. On the other hand, my laptop trying to connect to the kubuntu box via internet (forwarding to port 666) fails with the following message:```
ssh -p 666 chugru@69.************
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
7a*****************************************************82.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:2
RSA host key for 69.***************has changed and you have requested strict checkin                                                         
g.
Host key verification failed.

```

I'm pretty much a newbie and would like some advice about fixing thie RSA key problem...

Thanks!

---

### Post by LordHunter317 on 2006-01-31
It's because you're connecting to different machines with the same hostname (because that host is really forwarding to differenet hosts).  It's ssh trying to protect you.  I would remove the key, like it says, and disable StrictHostKeyChecking.

---

### Post by chugru on 2006-01-31
OK... 

From which of the machines do I remove the key, and how would I do that?

And, do I disable StrictHostKeyChecking (I suppose it's in sshd_conf) in the remote gentoo laptop or in the Kubuntu box?

Thanks for responding!

---

### Post by ::brainproxy on 2006-02-17
Basically go to that file and delete that key:

/root/.ssh/known_hosts

Just remove the line.

However, it will happen again if you still have to machines with the same host.  Happens when you reinstall your OS and keep the same host names too.

---

