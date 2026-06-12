---
title: "ssh-keygen + segmentation fault"
date: 2008-05-24
forum: Security
---

### Post by vlad_constantin_manea on 2008-05-24
Hi all,

I tried to generate a new ssh key pair, but I got a segmentation fault:

~$ ssh-keygen -f rsa
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): 
Segmentation fault (core dumped)
~$

Any idea how to fix it?

Thanks,
Vlad

---

### Post by mattress on 2008-05-26
I'd start with a simple memory test with Memtest86+

It's unlikely that the software is causing the problem....

-m

---

