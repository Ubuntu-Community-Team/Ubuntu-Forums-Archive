---
title: "encrypt whole server, without physical access?"
date: 2007-03-24
forum: Server Platforms
---

### Post by fadenb on 2007-03-24
Hi.

I have several computer running at home all encrypted like described in this how to: [https://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy](https://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy) 
That is working fine at home.

Now i want to rent a dedicated server and encrypt it in the same (or similar) way. The problem is that i do not have physical access to this server to enter the password after rebooting.
Setting up the server is no problem because I can get temporarily access via a ip-kvm, but this is not possible every time I want to reboot the server.

Any ideas how to solve this problem?


THX
FadenB

---

### Post by Nikron on 2007-03-24
Just have a partition that you can boot off of then, when it's finished booting, SSH in and mount the encrypted parts of the system.

---

### Post by fadenb on 2007-03-25
Hi.

Thats exactly what i am trying to circumvent. I don't want anything else then the boot partition unencrypted (if possible i would like to encrypt it also, but this does not seem possible in this situation). It would be easy to replace for example the binaries which are used to mount the encrypted partitions and get the pass phrase.

---

