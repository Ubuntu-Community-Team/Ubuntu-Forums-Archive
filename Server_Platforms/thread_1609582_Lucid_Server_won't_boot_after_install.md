---
title: "Lucid Server won't boot after install"
date: 2010-10-30
forum: Server Platforms
---

### Post by userFrodo on 2010-10-30
Although this is an old thread, I'm experiencing the same problem on a 10.04 LTS server installation.

I can install everything I wan't. But then the system will not boot. Error message: "No boot device available." with two options. Retry or enter setup (BIOS)

When I choose option Retry with the installation CD inserted, I can boot when I chose the option "Boot from first hard disc" in the Ubuntu installation menu which is then presented.

Strange thing is that I have two almost identical Dell SC1420's (only difference is 1 instead of 2 Gb memory). On the first machine the installation had no problems. Although I did have to "noapic"  installation.

I do this for learning purposes. So I have no hurry.

Thanks

---

### Post by CharlesA on 2010-10-30
Hi there,

I split your post off the other thread since it was an old thread.

It sounds like grub wasn't installed on the hard drive.

How did you install Ubuntu?

Make sure the boot order of the hard drives is set up correctly in the BIOS.

---

### Post by hantechbl on 2010-10-31
If you did install GRUB, did you check the jumpers? I had a similar problem then it hit me, JUMPERS!

---

### Post by userFrodo on 2010-10-31
> **CharlesA said:**
> Hi there,

I split your post off the other thread since it was an old thread.

It sounds like grub wasn't installed on the hard drive.

How did you install Ubuntu?

Make sure the boot order of the hard drives is set up correctly in the BIOS.

Thanks for the help.

I installed Ubuntu from the installation CD with the option "noapic"  turned on. Nothing fancy, only SSH.

I'll check the bios settings again and the jumpers.

How can I check whether GRUB is installed correctly?

---

### Post by CharlesA on 2010-10-31
I'm not quite sure how to check GRUB tbh, but if you have multiple hard drives, it could be trying to boot off the wrong one.

You can boot off a livecd and reinstall grub2 at the very least.

[https://help.ubuntu.com/community/Grub2#Installation](https://help.ubuntu.com/community/Grub2#Installation)

---

### Post by sikander3786 on 2010-10-31
Sometimes some PC's Bios creates problems like this if your HDD is configured as slave as already mentioned above. Did you check if it was the master and also the first bootable device in Bios menu?

You'll need a Live CD to either check or reinstall Grub. However it would be easier to first try reinstalling it before running into all the details and bootinfoscript etc.

---

### Post by userFrodo on 2010-11-01
Grub was installed correctly. 

I'm starting to think this might be a hardware or bios related problem because I also installed WinXP. At the end, it needed to reboot. It produced the same error "No boot device available."

The system is a Dell SC1420 with in it 2 SATA 80Gb drives. I have 2 of these Dell machines. I could not find any jumpers, but the bios config is exactly the same as in the other machine that works fine.

For the SATA drives only one option is possible in bios: ON or OFF.

I think I'll physically remove the drives and try an installation on both of them separately. See where that leads to.

Oh, both drives seem to be working. There is some Dell disc utility for disc checks. Also I was able to partion both the drives and create an ext4 filesystem on them.

---

### Post by CharlesA on 2010-11-01
Sounds like the BIOS is trying to boot off the drive that doesn't have the OS installed on it.

---

### Post by userFrodo on 2010-11-03
Problem solved.

Apparantly the BIOS / CERC SATA 2s software RAID controller conflicted with GRUB and the MBR.

While tinkering I noticed that the CERC also did something with the partition table and the MBR.

[strike]I disabled everything that had to do with RAID, removed RAID array with BIOS utility.[/strike]

Update:
Information between [strike] and [/strike] is inaccurate.
I removed the RAID array, but kept the option RAID = on in BIOS

Installed as usual from the CD. When it did not boot from hard drive automatically, which was the case, I could start from the drive using the BIOS RAID config. utility, which somehow forced a boot from the hard disc.

Anyway at the prompt all I had to do was:
```

$ sudo grub-install /dev/sda
$ sudo update-grub
$ sudo shutdown -r now

```And everything worked like it should.

Thanks for pointing me in the right direction.

---

