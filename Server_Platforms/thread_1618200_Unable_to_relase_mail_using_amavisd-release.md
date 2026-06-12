---
title: "Unable to relase mail using amavisd-release"
date: 2010-11-10
forum: Server Platforms
---

### Post by jedimastersa on 2010-11-10
Hi,

I hope I am posting in the right place. If not please let me know where to post.

I have a Ubuntu 10.04 server setup with Postfix+Amavis+Spamassassin+Clamav as well as Samba & ProFTP.

I followed the howto on howtoforge.com for most of my setup as I am very new to Linux and Ubuntu. 

I have a problem where I have a few false positives been held in my /amavis/virusmails/spam folder that I would like to release.

I have identified which file it is I need to release but when running the amavisd-release command I get the following error:

```
amavisd-release spam-gYDsF2-9nxcQ.gz 450 4.5.0 Failure: File /var/lib/amavis/virusmails/spam-gYDsF2-9nxcQ.gz does not exist at (eval 111) line 385, <GEN33> line 5.
```

I have searched the net for an answer and have not come up with much. I would appreciate it if someone could point me in the right direction.

Thanks!

---

