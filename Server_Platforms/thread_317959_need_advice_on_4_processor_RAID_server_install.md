---
title: "need advice on 4 processor RAID server install"
date: 2006-12-13
forum: Server Platforms
---

### Post by nephish on 2006-12-13
lo there all.

We are about to get our new server for the company website. The server we are getting has 6 drives that we intend to set up as a RAID 5 ( i think this part is being done at the factory where we are getting the machine ) . It has a raid card that i have checked to be compatable with linux. The machine has 4 processors. So, what i need to know is. When i go to load ubuntu on this device, i see where it asks if i want to set up a software RAID ( i dont think i want to because i have a RAID card ). What do i need to do to make sure that ubuntu will see the RAID setup via RAID card, and what do i need to do to make sure ubuntu will see and make use of all 4 processors ?

thanks for any tips, advice, gotcha warnings, or links to good how-tos.

---

### Post by psusi on 2006-12-13
Assuming the kernel already contains a driver for the raid card, and that it is, in fact, a hardware raid card, then you shouldn't have to do anything abnormal.  It will appear as one big hard disk.

---

### Post by nephish on 2006-12-13
ok, so do i need to do anything special to have the 4 processors recognized ?

---

### Post by psusi on 2006-12-15
> **nephish said:**
> ok, so do i need to do anything special to have the 4 processors recognized ?

Nope...

---

### Post by nephish on 2006-12-15
well, ok, thanks !

---

