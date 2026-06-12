---
title: "Permission denied (publickey)."
date: 2010-01-25
forum: Server Platforms
---

### Post by LepeKaname on 2010-01-25
Today I just updated 4 Hardy servers which are pretty much the same in setup. 

3 of them went without any problem, however one is displaying this error when trying to connect through ssh:

```
Permission denied (publickey).
```

However I have never setup a publickey access for that specific server (always password based). 

As the only way (for me) to access it is remotely, is there any way I can fix that problem?

Thank you in advance.

---

### Post by LepeKaname on 2010-01-25
I was able to connect through one of the "twin" servers which I just remember I set a public key between them (long time ago). Now I will be able to fix it... 

I will post here what went wrong during the update as reference.

UPDATE:

For some strange reason the following line was uncommented during the update (in /etc/ssh/sshd_config):

```
PasswordAuthentication no
```

How can that be possible? 

That specific server was since the beginning very slow to connect through ssh. Now its normal (fast). It may be related? who knows.

cheers :)

---

