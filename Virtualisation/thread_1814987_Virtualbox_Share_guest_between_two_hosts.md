---
title: "Virtualbox: Share guest between two hosts"
date: 2011-07-30
forum: Virtualisation
---

### Post by yknivag on 2011-07-30
I'm running several guest machines in Virtualbox which I use for development purposes.  The host machine is dual boot Ubuntu/Win7.

I know, using a separate partition that I can share a guest between two Linux hosts, but can I do it between Ubuntu and Win7?

Could I export the guests as appliances and then store them on a shared partition?

---

### Post by lmarmisa on 2011-07-30
I am not sure if I understand you.

According to my experience, you can share the same virtual disk file stored in a NTFS partition between two VirtualBox installations on a dual boot system (Ubuntu host and Windows 7 host) but with some limitations. These limitations are not to use the snapshot feature of VirtualBox and always shutdown the virtual machine associated to the virtual disk file (do not use the **Save the machine state**).

So, I can boot into Ubuntu or Windows on my dual boot system, and I have access to virtual machines which use the same virtual disk. The limitations are due because the snapshots and machine states are not stored inside the content of the virtual disk file ".vdi".

I hope this information could help you.

Best regards,

Luis

---

### Post by yknivag on 2011-08-05
Thanks for your response, Luis.

I know I can share the vdi files, but I am looking to try and share the snapshots and machine configuration too if I can.

Anyone have any further ideas?

Gavin.

---

