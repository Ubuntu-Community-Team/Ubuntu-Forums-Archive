---
title: "Help with LTSP"
date: 2010-06-13
forum: Server Platforms
---

### Post by vpetcu on 2010-06-13
Hello all.

It seems to me that this is the place to ask questions about LTSP on ubuntu. So, If anyone knows about my problem, a hand would be really useful. 

I'm trying to get to work ltsp --fat-client on Lubuntu 10.04. but I'm getting this error:


I have installed Lubuntu 10-04 an a virtual machine
and I have run the command: ltsp-build-client --fat-client.

I: Configuring initramfs-tools...
W: Failure while configuring required packages.
I: Unpacking the base system...
W: Failure trying to run: chroot /opt/ltsp/i386 dpkg --force-overwrite --force-confold --skip-same-version --install
error: LTSP client installation ended abnormally
breeos@ltsp:/opt/ltsp$ sudo chroot /opt/ltsp/i386 dpkg --force-overwrite --force-confold --skip-same-version --install


thank you in advance... :)
Vasilica Petcu

P.S. I have tried to run the command sudo ltsp-build -client and gave me the same error. So This has nothign to do with --fat-client

---

### Post by cariboo on 2010-06-13
You will get more help here that in FF&H

---

