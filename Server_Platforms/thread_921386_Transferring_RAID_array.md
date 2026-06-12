---
title: "Transferring RAID array"
date: 2008-09-16
forum: Server Platforms
---

### Post by subliminalcecil on 2008-09-16
Hi,

I have a successful RAID 5 array running on ubuntu server 64 bit version. The current motherboard has gone extremely unstable and seems to be a common problem with these boards. I have ordered a different board from another manufacturer and am wondering how i go about succussfully transferring my existing RAID array to the fresh OS install i am going to do on the new board?

Any tips appreciated.





Thanks for your time!

---

### Post by Robstarusa on 2008-09-16
> **subliminalcecil said:**
> Hi,

I have a successful RAID 5 array running on ubuntu server 64 bit version. The current motherboard has gone extremely unstable and seems to be a common problem with these boards. I have ordered a different board from another manufacturer and am wondering how i go about succussfully transferring my existing RAID array to the fresh OS install i am going to do on the new board?

Any tips appreciated.





Thanks for your time!

Are you using mdadm?

You should only have to swap boards, and then the raid array should be seen again (I'm assuming you are using onboard sata ports)

---

### Post by fjgaude on 2008-09-16
Yes, I've done it many times... all you have to do, and nothing else, is take all you drives that you are using now, even the boot drive, and connect them to your new motherboard. Boot up.

If your raid array doesn't come up just like before you will have to remove, purge **mdadm** from your OS. Re-boot, then re-install mdadm, re-boot. Then your mdadm.conf file will be auto regenerated, and your array should mount, just as before with your old motherboard.

If you do a fresh install of Ubuntu, then after it is up, install mdadm, and then re-boot. Your array should be up.

Let us know how you do.

---

### Post by trmentry on 2008-09-16
Just to add to this... BACKUP YOUR DATA!!  Murphy tends to be around for such events like this.

---

### Post by subliminalcecil on 2008-09-17
Thanks guys!

Yes im using mdadm with onboard SATA ports. I Just swapped the motherboards out, put CPU, ram, drives etc back in and it booted up fine :D

Had to do a bit of config with the onboard NIC, but wasnt too much hassel. RAID array booted as normal and all content accessabile.

---

### Post by fjgaude on 2008-09-17
Have you installed an updated OS?

---

### Post by subliminalcecil on 2008-09-17
No, i used the OS from the boot drive previously. Ubuntu server 8.04

---

### Post by fjgaude on 2008-09-17
Okay, that means the UUID for the array stayed the same... that's good to know. I think I did what you did one time with similar results... I was amazed at the power of Ubuntu to know all the new hardware from the old. Now I understand that Ubuntu doesn't do much if anything the way Windows does... this is a good thing. <smile>

---

