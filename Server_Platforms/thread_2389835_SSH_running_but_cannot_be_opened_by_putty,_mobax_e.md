---
title: "SSH running but cannot be opened by putty, mobax etc"
date: 2018-04-22
forum: Server Platforms
---

### Post by dave2011 on 2018-04-22
Hi all,

nubie here to asking about ubuntu...

Sorry if my english not good, I installed iso ubuntu who include the DVWA server. I tried to login via ssh port 22 but fail "**network error: software caused connection abort**", then I try to telnet my server by command prompt with 22 port and success "**SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4**". My firewal is inactive ([IMG]https://ibb.co/j4dkRx[/IMG]https://ibb.co/j4dkRx
) and fyi that I'm using ubuntu 10.04.
[IMG]https://drive.google.com/open?id=1PVSW8tM61i7cmtiHyQRHwxOa77jpiUnI[/IMG]

I also tried run /etc/init.d/ssh restart, and there were messages : 
[B]could not load host key: /etc/ssh/ssh_host_rsa_key[IMG]https://drive.google.com/open?id=1PVSW8tM61i7cmtiHyQRHwxOa77jpiUnI[/IMG]
could not load host key: /etc/ssh/ssh_host_dsa_key[IMG]https://drive.google.com/open?id=1PVSW8tM61i7cmtiHyQRHwxOa77jpiUnI[/IMG][/B]

What should I do? thank you for your help

---

### Post by wildmanne39 on 2018-04-22
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by LHammonds on 2018-04-22
Ubuntu 10.04 is extremely old and has not received security updates for YEARS.

You should consider that server a security risk and look to replace it with Ubuntu 16.04 (or very soon-to-be 18.04)

The auto-generated keys it came with might have simply expired.

Have you tried re-generating a set of keys?

```
ssh-keygen -A
```

LHammonds

---

### Post by dave2011 on 2018-04-22
yeah, I already read it from the forum but couldn't run ssh-keygen -A... there a message that ssh-keygen: illegal option --A

Thank you...

---

### Post by darkod on 2018-04-22
Be very careful with each character. The command posted by LHammonds said -A and in your post the error message says --A (double dash). Did you run it with one or two?

But I agree, use a more recent, supported LTS version like 16.04 (18.04 comes out next Thursday). I wouldn't use 10.04 even if you manage to resolve the ssh error.

---

