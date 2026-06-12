---
title: "How much RAM to leave for host?"
date: 2009-10-21
forum: Virtualisation
---

### Post by maxxjr on 2009-10-21
I run a couple of VM's at one time with VMware workstation, and am thinking about adding a couple of more.  

Question: I have 8GB RAM in my PC, and am thinking about allocating 7GB to the VM's.  Is 1 GB enough for the Ubuntu host OS?  

The main job of the Ubuntu host is to run the VM's and to provide Samba file sharing to the VM's.  I won't be using the host itself as a desktop PC.

Thanks!

---

### Post by wilee-nilee on 2009-10-21
Each VM runs independently of each other so when you allocate memory to them it is only while they are running, not all of them together using 7 GiB. Your question sort of makes no sense. ;)  Although I am not real knowledgeable about VM usage other then the Sun version, are you able to run multiple VM or just one at a time.

---

### Post by Twintop on 2009-10-21
Short answer: 1GiB should be enough to let the host do what it needs to do (especially if it is just serving up VMs). The real questions you need to ask yourself, though, is: how many VMs are you going to be running, what will they be doing, and what resources do *they* need to get their tasks done and run smoothly? If they're going to be 'headless' servers for web/ftp/dhcp/print/etc, then they will require less RAM than if you're trying to run three copies of Windows with Visual Studio running on them at the same time.

Once you know those answers, then you can divvy up your memory to appropriate levels for the host and guests.

---

