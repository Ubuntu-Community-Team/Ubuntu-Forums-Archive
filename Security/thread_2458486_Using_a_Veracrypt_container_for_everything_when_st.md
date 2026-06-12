---
title: "Using a Veracrypt container for everything when storing to external drive"
date: 2021-02-25
forum: Security
---

### Post by linuxyogi on 2021-02-25
Some 5 years back I had purchased a WD My Passport 500GB external drive. It went bad after just 8 months of usage. In short a complete waste of money.
The only reason I didn't claim warranty is the fact that I was afraid that the company staff will get access to my personal data.

At the moment I am using a 32GB Sandisk flash drive for backups. In terms of storage space my needs are very minimal so 32GB is enough.

My plan is to create a 32GB encrypted Veracrypt container on the flash & use Grsync to copy all my data to the Veracrypt container. Nothing remains unencrypted.

Is that a good thing to do ?

---

### Post by TheFu on 2021-02-25
I wouldn't use veracrypt.  Why not use a backup tool that has built-in encryption and versioning too?  For 32G, something like duplicity should be fine, but there are many others.  
If you want to keep encryption separate from the backups, I'd use a LUKS container. LUKS is what Linux servers use. The tools are built into most popular Linux distros. Some Linux file managers will guide you though unlocking the encrypted container just by clicking. I know Caja does this, provided the cryptsetup tool has been installed, of course.

---

### Post by linuxyogi on 2021-02-25
> **TheFu said:**
> I wouldn't use veracrypt.  Why not use a backup tool that has built-in encryption and versioning too?  For 32G, something like duplicity should be fine, but there are many others.  
If you want to keep encryption separate from the backups, I'd use a LUKS container. LUKS is what Linux servers use. The tools are built into most popular Linux distros. Some Linux file managers will guide you though unlocking the encrypted container just by clicking. I know Caja does this, provided the cryptsetup tool has been installed, of course.

Yes I want to keep separate from backups.

Can you please tell me why you advise not to use Veracrypt ? The only reason I am asking is coz I am using Veracrypt for a long time. I am very familiar with its interface.

Googling about "LUKS container ubuntu" as soon as I finish typing this post.

---

