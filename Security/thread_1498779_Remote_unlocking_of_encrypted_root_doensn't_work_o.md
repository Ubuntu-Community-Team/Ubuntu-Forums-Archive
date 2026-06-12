---
title: "Remote unlocking of encrypted root doensn't work on Lucid anymore"
date: 2010-06-01
forum: Security
---

### Post by hal2100 on 2010-06-01
Hello,

I hava a server which has an encrypted root with 8.04. I used the remote unlocking proposed in another thread to unlock the server shortly after boot.

The solution proposed [HERE]("http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu") is not working anymore, but there are some patches for debian which enable this by default, after some configuration.
Please see the dropbear package for details and 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465901]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465901")

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465902]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465902")

and 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465903]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465903")

As far as I understood these patches are accepted, also the dropbear package description seems to say the same.

SSHing into the encrypted box is possible, but the unlocking is not done if I do a
```
echo -n "PASSWORD" > /lib/cryptsetup/passfifo
```

Is there anything I missed to enable this feature?
Any help is greatly appreciated!

---

### Post by cdenley on 2010-06-01
I'm not sure how to solve your problem, but all the debian patches you mentioned are already in lucid.

---

### Post by hal2100 on 2010-06-01
If someone could give me some hints to debug this feature, I would try to solve this mystery.

Somehow there has to be a way...

Or am I doing something wrong? As far as I understood the "echo -n ...." should be enough.

:confused:

---

### Post by hal2100 on 2010-06-08
Am I really the only person who tries to unlock his encrypted server remotely?

---

### Post by daniel_L on 2010-09-14
Nope, you're not, I'm also looking for a solution to this problem. Did you find one in the meantime?

---

