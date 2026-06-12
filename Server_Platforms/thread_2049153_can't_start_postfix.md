---
title: "can't start postfix"
date: 2012-08-28
forum: Server Platforms
---

### Post by said76 on 2012-08-28
Hi,

I was wondering if I could get some help here. I was trying to start postfix service by running the following code

$ /etc/init.d/postfix start
bash: /etc/init.d/postfix: /bin/bash^M: bad interpreter: No such file or directory

I wonder what I need to do to resolve the problem so that I can start postfix service using the start-up script.

Any help would be greatly appreciated.

Thank you

---

### Post by lisati on 2012-08-28
What version of Ubuntu are you using?
In newer releases, the proper command is:
```
sudo start service postfix
```

---

### Post by steeldriver on 2012-08-28
did you by any chance copy the postfix script from (or via) a Windows machine? The ^M code usually indicates a DOS-style (CR-LF) line termination

---

### Post by said76 on 2012-08-28
Thank you for your reply.

Sorry that I forgot to tell you my Ubuntu version. it's Ubuntu server 12-04 LTS.

I actually installed postfix from source so I use my own bash start-up script.

hmm. you got me thinking about ^M code. I'll double check again in my script. I use nano editor to edit it.

Thank you

---

