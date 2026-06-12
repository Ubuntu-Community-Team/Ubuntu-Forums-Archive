---
title: "Ubuntu Server installation and RAID hardware"
date: 2009-06-13
forum: Server Platforms
---

### Post by televisi on 2009-06-13
Hi All,
Has anyone install Ubuntu with / using RAID hardware controller? Just wonder how hard it is going to be...

I just bought [Adaptec 5405]("http://www.adaptec.com/en-US/support/raid/sas_raid/SAS-5405/") as well as 3 SAS drive for my server (73GB, 300GB, 300GB).

My plan is to install Ubuntu server to the 73GB and put all important data to the 1st 300GB drive, and hopefully the 2nd 300GB as the backup using RAID1.

Is this plausible? is it easy to do using Ubuntu? Any step / info that I need to follow?


Also, according to Adaptec site, they are not really support Ubuntu, but they supply [Linux Driver source code]("http://www.adaptec.com/en-US/downloads/linux_source/linux_source_code?productId=SAS-5405&dn=Adaptec+RAID+5405"). Will this be a good thing??

I never really install any hardware / compile anything in linux (especially Ubuntu), if you have any suggestion that would be great too :)

Thanks!

---

### Post by basdoorn on 2009-06-13
I am running the 5405 myself with a 2 disk SAS mirror. The controller and its raid mirror were detected as /dev/sda without any help from my part. Simply setup the raid set you want in the controller bios and boot from the Ubuntu install media. I guess with a single drive and a raid set as you propose they would simply become sda and sdb, you can distinguish the 2 arrays by looking at the size.
I am running Ubuntu 8.10 myself, with 9.04 it might be a bit different. Ubuntu standard install media support the Adaptec 5405 in any case. On my 8.10 server it has been running for over 6 months with good performance and stability.

---

### Post by fjgaude on 2009-06-13
You might wish to take a look at this link:

[http://ubuntuforums.org/showthread.php?t=1019045&highlight=mdadm](http://ubuntuforums.org/showthread.php?t=1019045&highlight=mdadm)

Seems all is well and getting better.

---

### Post by televisi on 2009-06-13
Hi guys thanks for your prompt reply, I really really really appreciate it!!

basdoorn: Thanks for your input, so you were saying that you just install the RAID using the normal BIOS software they supply (the one that you need to press CTRL+A during boot up) and your Ubuntu installation just detect it as 1 hard drive?, you don't even need to install driver as explained in their site? that's great!!!
I have couple of question for you though:
- Do you need to fresh install your ubuntu server to setup this RAID? or can I use existing Linux installation?
- Have you ever use their "Command Line Utility"? if yes, how did you install it to Ubuntu? (as in the manual for other linux distro, I have to install it first)
- Now, how do you restore if 1 of the drive fails (considering I'm about to use RAID1 / 10)? did you just put out the fail one and install the new one and the RAID will restore the original files straight away?
OR should I manage the "Hot Spare" initially and once the disk fail, install the new drive and restore it manually again?

fjgaude: Thanks for this, I'll try above approach first, if I still need to install the driver / anything, I'll check this package


My intention is to install Ubuntu server 8.04 using this RAID hardware (Adaptec 5405); as I said in the beginning, this is the first time I am using RAID hardware, and quite surprised (or shock to be exact) with the PDF that comes with the hardware (182 pages), and even shock further after seeing Ubuntu is not in their supported OS list...but thankfully some people in this forum already have experience in using this hardware... :)

> **fjgaude said:**
> You might wish to take a look at this link:

[http://ubuntuforums.org/showthread.php?t=1019045&highlight=mdadm](http://ubuntuforums.org/showthread.php?t=1019045&highlight=mdadm)

Seems all is well and getting better.

---

### Post by ducksun43 on 2009-06-14
take a look at that link

[http://sunoano.name/ws/public_xhtml/hardware.html#adaptec_31205_raid_hba](http://sunoano.name/ws/public_xhtml/hardware.html#adaptec_31205_raid_hba)

it might be exactly what you look with regards to your RAID task

---

### Post by televisi on 2009-06-14
Thanks, I will take a look on this site as another way of installing my RAID :)

> **ducksun43 said:**
> take a look at that link

[http://sunoano.name/ws/public_xhtml/hardware.html#adaptec_31205_raid_hba](http://sunoano.name/ws/public_xhtml/hardware.html#adaptec_31205_raid_hba)

it might be exactly what you look with regards to your RAID task

---

### Post by televisi on 2009-06-20
Hi Basdoorn,
At the moment I'm installing my Ubuntu Server 8.04 together with my RAID, with these combinations:
- 1x73GB SAS HD (as '/boot' EXT3, '/' EXT3, and LVM swap)
- 2x300GB SAS HD (RAID 1, using LVM partition for DATA)

I initialized and "build/verify" the 2nd&3rd HD as RAID 1;
and initialized as "normal volume" for the 1st HD.

Was it takes an ages for you to install them? as **mine takes an ages**. especially in:
"Installing software part", when I go to different terminal (alt+f4), apparently it is downloading bunch of small files (approx 300kb)....strangely no one is using internet at my place now (which it should be faster), is this normal? considering I am installing it to a RAID disks?

Once I finish install Ubuntu, is there anyway for me to know that the RAID hardware will be doing its job? 
(I'm just afraid the RAID hardware not doing its job, is there anyway to test / simulate RAID reconstruction/repair process?)

Thanks

> **basdoorn said:**
> I am running the 5405 myself with a 2 disk SAS mirror. The controller and its raid mirror were detected as /dev/sda without any help from my part. Simply setup the raid set you want in the controller bios and boot from the Ubuntu install media. I guess with a single drive and a raid set as you propose they would simply become sda and sdb, you can distinguish the 2 arrays by looking at the size.
I am running Ubuntu 8.10 myself, with 9.04 it might be a bit different. Ubuntu standard install media support the Adaptec 5405 in any case. On my 8.10 server it has been running for over 6 months with good performance and stability.

---

### Post by windependence on 2009-06-20
Don't let people confuse you with software RAID. What you did was fine, and IMHO the best way and most trouble free way to do it. You will not see a speed increase with RAID 1 because it is only a mirror, it does not stripe your data between drives

If you're seeing two drives, one around 73G and one 300G, you have done it correctly. Good job!

-Tim

---

### Post by televisi on 2009-06-20
Ah... so it is normal to be slow? strange...by the time I reply this thread, it is still 85% complete :(

Does it because I install 32 bit version instead of 64 bit version in my Xeon 2.67Ghz?
Should I use 64 bit Ubuntu server instead?

Thanks

> **windependence said:**
> Don't let people confuse you with software RAID. What you did was fine, and IMHO the best way and most trouble free way to do it. You will not see a speed increase with RAID 1 because it is only a mirror, it does not stripe your data between drives

If you're seeing two drives, one around 73G and one 300G, you have done it correctly. Good job!

-Tim

---

### Post by windependence on 2009-06-21
> **televisi said:**
> Ah... so it is normal to be slow? strange...by the time I reply this thread, it is still 85% complete :(

Does it because I install 32 bit version instead of 64 bit version in my Xeon 2.67Ghz?
Should I use 64 bit Ubuntu server instead?

Thanks

Not necessarily. In fact, because the data path is twice as big, 64 bit is sometimes much slower than 32 b it. You only need 64 bit to address more than 4GB of memory.

If you're talking about the speed of building the array, it always takes a while on big disks, however, if you were expecting a performance increase from RAID 1, you will not get one. For that you want RAID 0 or RAID 5.

-Tim

---

### Post by televisi on 2009-06-21
Ah... apparently this is an ongoing issue during installation (especially when Ubuntu tries to search for mirroring), right after I unplug my LAN cable from the NIC card, the installation is fast again.

But now I receive a new issue, which is located in [http://ubuntuforums.org/showthread.php?t=1193107](http://ubuntuforums.org/showthread.php?t=1193107)

Another quick question, is there anyway to test / simulate RAID reconstruction/repair process?
Thanks heaps!

---

