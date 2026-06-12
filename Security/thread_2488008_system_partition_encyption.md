---
title: "system partition encyption"
date: 2023-06-20
forum: Security
---

### Post by aeronutt on 2023-06-20
The key phrase is, system *partition*.

What I don't want to do: use full disk (device) encryption. That seems to be what ubiquity is able to do on install, and what many of the online guides describe.

What I want to do. I have a device with multiple partitions (2-3 with linux, plus windows).  For ONE of those linux installs, I'd like to fully encrypt that partition, and have it behave just like it behaves for full disk encyption.  That is, during boot of that linux partition, it asks the user for the decryption password, and continues with boot.

I'm willing to do a fresh install to make this happen.

Thanks!

---

### Post by CharlesA on 2023-06-22
You can do that, but it's quite a bit more work as you need to set up the partitions manually before doing the install.

Just remember to back all your data up before trying this.

[https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html](https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html)

---

### Post by TheFu on 2023-06-22
> **CharlesA said:**
> You can do that, but _**it's quite a bit more work**_ as you need to set up the partitions manually before doing the install.
 

That's an understatement.  Installing the OS into a LUKS container is a single checkbox in most Ubuntu installers. It wipes the system disk and sets up everything. Easy.  

Any other methjod is a pain.  Since LUKS hooks into the boot loader, I don't know if it is possible to NOT use use it for all systems. The boot loader decrypts the LUKS container before booting the OS.  Might be possible. IDK.  Might be easier to have the encrypted boot loader on a flash drive or USB3.2 SSD and have all the other OSes without encryption installed as dual/tri/quad/penta-boot setups.

I don't know where the boot chain inserts LUKS. That would be a key thing to determine.

I literally bought an SATA SSD-2-USB3.1 enclosure for $12 this week to put an old Micron 1100 500GB m.2 SATA SSD into for fast access to OSes, data, lots of junk.

---

### Post by aeronutt on 2023-06-22
> **CharlesA said:**
> You can do that, but it's quite a bit more work as you need to set up the partitions manually before doing the install.

Just remember to back all your data up before trying this.

[https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html](https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html)

Thanks, this is exactly what I've been looking for.
Is there a reason you prefer a swap partition over the default of using a swap file?

---

### Post by aeronutt on 2023-06-22
> **TheFu said:**
> That's an understatement.  Installing the OS into a LUKS container is a single checkbox in most Ubuntu installers. It wipes the system disk and sets up everything. Easy.  

Any other methjod is a pain.  Since LUKS hooks into the boot loader, I don't know if it is possible to NOT use use it for all systems. The boot loader decrypts the LUKS container before booting the OS.  Might be possible. IDK.  Might be easier to have the encrypted boot loader on a flash drive or USB3.2 SSD and have all the other OSes without encryption installed as dual/tri/quad/penta-boot setups.

I don't know where the boot chain inserts LUKS. That would be a key thing to determine.

I literally bought an SATA SSD-2-USB3.1 enclosure for $12 this week to put an old Micron 1100 500GB m.2 SATA SSD into for fast access to OSes, data, lots of junk.

I understand nearly all of what his directions do, so it's not that big of a pain for me to implement.
Why does it matter where the boot chain inserts LUKS?  As long as it's been confirmed that it can decrypt a specific partition and not the device.

---

### Post by TheFu on 2023-06-22
When using volume managers, we will take a snapshot just prior to making a backup.  With a swap file, the snapshot would include that file, which is useless just eating storage that could be used for other needs.  It would be frozen until the snapshot was deleted.  With ZFS or BTRFS, those snapshots could be held for 30+ days, though with LVM, we'd typically keep them just a week, or even just 1 day, to make quick restores after a stupid admin mistake speedo-fast. That's just 1 example. There are others that you can google.

Keeping different types of storage in separate compartments is a "best practice" for lots of reasons.

There are other reasons to NOT use swapfiles.

---

### Post by TheFu on 2023-06-22
> **aeronutt said:**
>  Why does it matter where the boot chain inserts LUKS?  As long as it's been confirmed that it can decrypt a specific partition and not the device.

If it decrypts the LUKS container (really just inserts the dm-crypt driver) between the device and everything downstream (partition/file system/volume manager), then it could become an issue for the OSes that DON'T use encryption.

If dm-crypt gets used before MS-Windows is booted and there aren't any decryption keys available, why would there be, dm-crypt may not ignore the error, but it can't boot that OS.
But IDK where this happens. Could be a non-issue completely.  This is why I suggested using a USB boot device for the encrypted OS.  You'll want this for the evil maid attack anyway.

---

### Post by aeronutt on 2023-06-22
The Evil Maid isn't part of my risk profile.

I'll likely try an install as described.  Worst case, I'd have to re-install without encryption.
Thinking about this, I'll have make double sure that I don't install a boot loader if I install another OS later on a different partition. One of my pet peeves is that some installs don't give an option to not install a boot loader.

---

### Post by TheFu on 2023-06-22
> **aeronutt said:**
> The Evil Maid isn't part of my risk profile.

I'll likely try an install as described.  Worst case, I'd have to re-install without encryption.
Thinking about this, I'll have make double sure that I don't install a boot loader if I install another OS later on a different partition. One of my pet peeves is that some installs don't give an option to not install a boot loader.

I wish you luck.  Might be good to take a video of the process. Bet some people would be interested.

---

### Post by Rubi1200 on 2023-06-22
I am no expert in this subject and I certainly have not tried this but isn't this what you are looking for?
[https://www.linuxshelltips.com/encrypt-partition-linux/](https://www.linuxshelltips.com/encrypt-partition-linux/)

Obviously, as others have mentioned, backups are crucial in case something goes wrong.

---

### Post by aeronutt on 2023-06-22
> **Rubi1200 said:**
> I am no expert in this subject and I certainly have not tried this but isn't this what you are looking for?
[https://www.linuxshelltips.com/encrypt-partition-linux/](https://www.linuxshelltips.com/encrypt-partition-linux/)

Obviously, as others have mentioned, backups are crucial in case something goes wrong.

Thanks, but that can be used to encrypt/decrypt a partition for data, not an OS to boot.

---

### Post by Rubi1200 on 2023-06-22
> **aeronutt said:**
> Thanks, but that can be used to encrypt/decrypt a partition for data, not an OS to boot.
And that is why I said I am no expert ;-)

Good luck with your project!

---

### Post by aeronutt on 2023-06-22
> **Rubi1200 said:**
> And that is why I said I am no expert ;-)

Good luck with your project!

Obviously I'm not either!   
This forum is still the best place for help!

---

### Post by CharlesA on 2023-06-22
> **TheFu said:**
> That's an understatement.  Installing the OS into a LUKS container is a single checkbox in most Ubuntu installers. It wipes the system disk and sets up everything. Easy.  

Any other methjod is a pain.  Since LUKS hooks into the boot loader, I don't know if it is possible to NOT use use it for all systems. The boot loader decrypts the LUKS container before booting the OS.  Might be possible. IDK.  Might be easier to have the encrypted boot loader on a flash drive or USB3.2 SSD and have all the other OSes without encryption installed as dual/tri/quad/penta-boot setups.

Indeed. I did the same thing when I wanted to run a ZFS root and it took a lot of trial and error, even with a decent tutorials and reading the man pages.

Of course, this is also running with a single OS, not multiboot, and it was still a massive pain in the butt. I'm kinda scared to update the boxes since I've run into kernel updates that cause stuff to break (but thankfully that is rare).

@OP: If you can, I would do your testing on a VM and see what breaks. It's easier to troubleshoot stuff when you have a working system. ;)

---

