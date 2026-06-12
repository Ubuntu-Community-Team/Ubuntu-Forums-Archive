---
title: "how to give preference to certain server services"
date: 2010-05-27
forum: Server Platforms
---

### Post by skrite on 2010-05-27
Hey all, 
I have a server that does a lot of things. Web server, sftp, mail, etc.. for our business. It also runs an asterisk PBX. 
I notice that when our processors spike, and we are at a peak time, we start loosing quality in voice applications. They become garbled. Is there a way i give the asterisk server preference in ram and processor to everything else?

thanks

---

### Post by craigp84 on 2010-05-29
Lookup "nice" for  a simple but effective way of increasing a process's priority on the CPU.

---

