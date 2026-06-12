---
title: "[SOLVED] ssh update blocks access"
date: 2008-06-23
forum: Server Platforms
---

### Post by hot_rod_hippie on 2008-06-23
I'm running a pretty simple server with web, ssh, ftp, and file sharing enabled on 7.10 (gusty).  I logged into the server a week or so ago and performed updates (the first in a while).  During the process, my putty terminal froze, and I have been prevented from logging in since.  The error I get is: "Server unexpectedly closed network connection."

openssh was one of the packages to be upgraded, and I assume this is the root of the problem.

My job has required me to be away from home quite a bit, so the server is at my parents' house (which means I have no direct access).  Currently my only option is to connect with putty from my work computer, or give my dad directions over the phone.

I'd appreciate any reasons why this happened, and how to fix it.

Thanks, 
Josh

---

### Post by apjone on 2008-06-23
Can you get access so you can run 

```

cat /var/log/access.log 

```

and see if it chucks up any errors when you have been trying to log in via ssh?

The only other thing i can suggest is some how you get your dad to either reboot the box or restart ssh. That may help.

---

### Post by wootah on 2008-06-23
> **hot_rod_hippie said:**
> I'm running a pretty simple server with web, ssh, ftp, and file sharing enabled on 7.10 (gusty).  I logged into the server a week or so ago and performed updates (the first in a while).  During the process, my putty terminal froze, and I have been prevented from logging in since.  The error I get is: "Server unexpectedly closed network connection."

openssh was one of the packages to be upgraded, and I assume this is the root of the problem.

My job has required me to be away from home quite a bit, so the server is at my parents' house (which means I have no direct access).  Currently my only option is to connect with putty from my work computer, or give my dad directions over the phone.

I'd appreciate any reasons why this happened, and how to fix it.

Thanks, 
Josh

Perhaps your key was one of the keys that got blacklisted through that security flaw that was introduced awhile back? ([http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1))

I would check out */var/log/messages*, **last **and **lastb**. You should find some clues in there. You may just have to generate new keys or double check that your public key is still in the *~/.ssh/authorized_keys* file.

---

### Post by hot_rod_hippie on 2008-06-24
Thanks for the help.

The server was not accepting my public key.
After generating new keys, everything works great.

Josh

---

