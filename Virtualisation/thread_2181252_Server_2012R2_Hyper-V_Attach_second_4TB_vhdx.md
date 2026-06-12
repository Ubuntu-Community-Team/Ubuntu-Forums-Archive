---
title: "Server 2012R2 Hyper-V Attach second 4TB vhdx"
date: 2013-10-17
forum: Virtualisation
---

### Post by Acer8888 on 2013-10-17
Hello, i apologize if this has already been asked.
 
I just installed Windows Server 2012R2 and am running Ubuntu 12.04 Server on Hyper-V. I have a 30gig vhdx for the OS, I would like to add a secondary drive for media. I created a 4tb vhdx and have attached it to the VM. I tried using Gparted and gdisk to create a GPT partition, when i go to format the drive it never completes i left if for 14hours and still didnt complete. What am i doing wrong?

I am no ubuntu expert any steps provided will be much appreciated.

Thank you in advanced

---

### Post by L486XGW on 2013-10-17
There are tons of bugs with hyper-v still. The drive just may be too big to mount as one partition. Do you have it mounted as ide or scsi?

---

### Post by Acer8888 on 2013-10-17
I have tried adding the vhdx as an IDE drive. I havnt tried it as a scsi. Before i had the VM set with a passthrough physical drive but would like to use the physical drive for other things as well.


> **L486XGW said:**
> There are tons of bugs with hyper-v still. The drive just may be too big to mount as one partition. Do you have it mounted as ide or scsi?

---

