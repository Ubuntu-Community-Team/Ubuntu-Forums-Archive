---
title: "Should I OKAY the option: Installation of android emulator on Ubuntu via virtualBox"
date: 2019-02-18
forum: Virtualisation
---

### Post by zak100 on 2019-02-18
Hi,
 I am trying to install android emulator on my Ubuntu system via virtualbox. I have got following screen which I have attached. It shows me:


16 GiB  Linux filesystem                 Android Emulator
 
[Align]  [Backup] [Help] [Load] [New](selected) [Verify] [write]


 
Should I select write or not.
 
I have 1TB of harddisk and I am using Ubuntu 18.04. My android emulator version is: android-x86_64-8.1-r1.iso.

Somebody please guide me.

Zulfi.

---

### Post by oldrocker99 on 2019-02-18
Installing the Android emulator will create a new partition, which I do not recommend. You need to run a virtual machine from the .iso. I like Virtualbox, which is available here:

[https://www.ubuntuupdates.org/package/virtualbox.org_contrib/cosmic/contrib/base/virtualbox-6.0](https://www.ubuntuupdates.org/package/virtualbox.org_contrib/cosmic/contrib/base/virtualbox-6.0)

And here's the official instructions: [https://www.virtualbox.org/manual/ch01.html](https://www.virtualbox.org/manual/ch01.html)

Good luck, and don't be shy about asking questions.

---

### Post by zak100 on 2019-02-18
Hi,
I have got virtualBox installed on my Ubuntu. Can you please tell me from where I can find the VM for android emulator (i.e. the OVA file)?

 Zulfi.

---

### Post by howefield on 2019-02-18
Thread moved to the "*Virtualisation*" forum.

---

