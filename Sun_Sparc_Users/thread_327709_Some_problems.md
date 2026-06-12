---
title: "Some problems"
date: 2006-12-29
forum: Sun Sparc Users
---

### Post by gtorino on 2006-12-29
Hello, I've installed 6.06.1 server version on a new Sun X2100. I'm making the transition from Fedora on IBM machines to Ubuntu on both Sun and IBM boxes, and this is the first install so far.

I have two problems I need some advice on:

1. Ubuntu typing is slow. I'm not sure if this is the Sun box, ssh or a type speed setting on Ubuntu. Is there a way to change the type rate?

2. My users have discovered sftp since it's an easy choice on Macintosh machines. ](*,) Previously we used Proftpd to "jail" them, but sftp lets them escape the "jail." So I need to either "jail" them in openssh (sftp) or disable sftp and install something like proftpd. Is there an easy way to do this, or should I disable this line in sshd_config:
Subsystem sftp /usr/lib/openssh/sftp-server

And then install either proftpd or something similar? I say something similar because proftpd does not seem to be in the apt-get repositories so I'm guessing it would need to be a custom compile, and I'd rather have something more ubuntu-standard and easier to upgrade.

---

### Post by bernied on 2006-12-29
Does [this](http://www.ubuntuforums.org/showthread.php?t=128206) help for your #2?

Sorry, I don't know how to help with #1 (or even understand what you mean)

---

