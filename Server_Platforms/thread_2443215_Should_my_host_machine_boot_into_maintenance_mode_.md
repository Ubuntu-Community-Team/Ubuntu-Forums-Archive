---
title: "Should my host machine boot into maintenance mode as root user?"
date: 2020-05-12
forum: Server Platforms
---

### Post by Robert_Boutin on 2020-05-12
I have three RAID1 arrays configured on my host machine.  Two are active, the third was just for increased storage to swap out one of the arrays.  All three arrays are in my mdadm.conf file.  If all three UUIDs are uncommented, my host machine tries to find all three arrays, but it only finds two working arrays and boots into maintenance mode as root user.  I can go in and edit /etc/fstab and /etc/mdadm/mdadm.conf with no password required.  I didn't try to add a new sudo user but I feel like I could have.  Am I missing something or is this is a massive security issue?  Is my machine just improperly configured to allow this to happen?  My host is 16.04.

---

### Post by TheFu on 2020-05-13
Cannot tell much from the description. It is possible for someone with sudo or a an external boot device to take over a system, unless that system uses whole drive encryption.  

As with all computing devices, physical access means everything. With physical access to a system and the system isn't whole disk encrypted, we can own it in a few minutes unless steps are taken to prevent boots from external storage and modifying the grub boot parameters is prevented. If those things are prevented, it takes a little longer.

---

### Post by Robert_Boutin on 2020-05-13
Very interesting.  Shows what I know, I had no idea one could gain root access so easily.  So I know I can reinstall my OS on my m.2 drive with encryption.  Is there a guide somewhere that you can suggest on how to properly encrypt the raid arrays that hold the VBox guests?  I prepare tax returns and I need to ensure that the guest machines that contain client data are protected.  I'm comfortable they are protected against online attacks, not comfortable anymore about physical theft of my machine.  Thanks for your comments.

---

### Post by Robert_Boutin on 2020-05-13
Very interesting, I had no idea it was that easy to gain access to a machine.  Do you have any suggestions where to look for guidance on encrypting a hard drive?  I run only my host OS on my m.2 so I could easily reinstall it with disk encryption, but my VBox guests all sit on the raid arrays,  Thanks for your comments, that was an eye-opener.

---

### Post by TheFu on 2020-05-13
Any storage device used that contains business proprietary data should be encrypted.  ideally, 2FA should be required to unlock the encryption container.  i use 2fa to unlock my laptops.  Had a cell phone stolen while travelling overseas.  I&#8217;ve struggled whether to encrypt storage internal to desktop and servers here.  i know that i should just encrypt everything for many reasons.  But the hassle factor and the need to remotely reboot systems is the main reason that i haven't just encrypted everything.

A good understanding of devices, file systems, mounting should be sufficient to handling encryption.  if you install the base OS using whole disk encryption and check out the way storage is setup, you'll get a good idea for how stuff works.

The commands to look up that are new would be **cryptsetup** and 
```
alias lsblk='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
The 2nd one shows how different parts of the storage area each related; what contains what, the hierarchy. it will really help to visualize.   Also, if you are still using mdadm, that isn't needed anymore when we use LVM.

And don't worry about setting up 2FA for anything.  Every LUKS header has 8 slots to allow access, so you can use slot 0 for a long passphrase and slot 5 for a 2FA challenge/response.  Changing any slot doesn't force re-encryption.

BTW, a few years ago, during the Redhat certification practical test, access to the system console was provided but no userid or login.  The first step was to quickly hack in using grub options and reset any userid passwords. if you know what you are doing, that can be almost as quick as looking up a login and entering that data.

---

