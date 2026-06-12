---
title: "USB 3.0 and SATA III (6gb)"
date: 2010-05-31
forum: The Cafe
---

### Post by McRat on 2010-05-31
The newest standards to get put into motherboards this year are USB 3.0 (about 85 MB per second transfer, measured), and SATA 6.0 (about 375 MB/sec measured).

ASUS has MB's that support both of these, but I'm not seeing much in the way of peripherials for them though.

Anyone play with these interfaces yet?

I heard Linux already supports the USB3 spec, but what about SATA6?

---

### Post by babydanks on 2010-06-19
Welp, I just tried to install ubuntu on my SSD plugged into a SATA 6gb/s. No luck. It only recognized my data drive on install. Anyone else had this problem?

---

### Post by cascade9 on 2010-06-19
I've recently built a system with USB 3.0 support (via a NEC chip). Worked fine with the flash drive that I tried with it, and but I didnt do any speed tests. 

SATAIII should work well with linux, but I dont know of anybody thats tested it yet. I havent LOL. Since there are only a few SSDs and HDDs with SATAIII support so far, its not that suprising. 

I would expect that the 'burst' rate with a HDD should hit 600MB/sec with SATAIII. Of course, that is just burst, its not going to do that continuous transfer (fastest HDD I've seen would be, ohh, maybe 125MB/sec max transfer). 

> **babydanks said:**
> Welp, I just tried to install ubuntu on my SSD plugged into a SATA 6gb/s. No luck. It only recognized my data drive on install. Anyone else had this problem?

Let me guess, you have a SATAIII port from an on-baord RAID controller? Most of them arent that great, andn the jmicron SATAIII RAID controllers that the majority of manufacturers are using are not linux friendly at all. I dont know if its even possible to use them with linux :|

---

### Post by babydanks on 2010-06-19
No actually I just have 2 SATA III ports, unable to support raid. SSD unrecognized by Ubuntu, but recognied by grub 2 and win7. My SSD boots Ubuntu fine off the SATA II ports which do support raid; of course i dont have raid turned on...

---

### Post by cariboo on 2010-06-19
@babydanks

Try the [alternate install iso]("http://releases.ubuntu.com/lucid/"), it always detects SATA drives correctly, The Live CD is hit and miss when it comes to detecting SATA drives.

---

### Post by babydanks on 2010-06-19
Thanks, I'll give it a whirl!

---

### Post by babydanks on 2010-06-20
Unfortunately the alternate CD did not recognize it either. I also had a copy of G-parted live, which also failed to recognize the SSD. I find it so odd that grub and win boot fine, but ubuntu can't for some reason...

---

### Post by cascade9 on 2010-06-20
> **babydanks said:**
> No actually I just have 2 SATA III ports, unable to support raid. SSD unrecognized by Ubuntu, but recognied by grub 2 and win7. My SSD boots Ubuntu fine off the SATA II ports which do support raid; of course i dont have raid turned on...

Well, even if its not RAID capable, its still going to be an add-on controller chip. 

Do you know what model motherboard you are using?

---

### Post by javyn999 on 2010-06-23
I have a GIGABYTE GA-770TA-UD3 w/ SATA III and USB 3.0 support.

I have a Caviar Blue SATA II that I tried plugging into the SATA III port on the mobo, and Ubuntu just wouldn't load.

When I pulled it out and plugged into a standard SATA II port, works just fine.  

Unfortunate, I would like to get one of the Caviar Black 1TB Sata IIIs.

edit:  I have no USB 3.0 devices so I can't test that.

---

### Post by cascade9 on 2010-06-24
GA-770TA-UD3, SATAIII via an addon RAID chip (Marvell 9128)- 

> Marvell 9128 chip: 

[LIST=1]
[*]2 x SATA 6Gb/s connectors (GSATA3_6, GSATA3_7) supporting up to 2 SATA 6Gb/s devices
[*]Support for SATA RAID 0 and RAID 1
[/LIST]
[http://www.gigabyte.com/products/product-page.aspx?pid=3272#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3272#sp)

According to marvel, it does have support, but I'm tonight I'm too stuffed to figure out if it actually works under *nix- 

> Windows and Linux OS support[http://www.marvell.com/products/storage/storage_system_solutions/sata_controllers_pc_consumer/](http://www.marvell.com/products/storage/storage_system_solutions/sata_controllers_pc_consumer/)

Dont worry, a WD Cariar Black SATAIII drive will work just fine on a SATAII port. The only real difference between running it on SATAII compared to SATAIII isn that the burst speed will be lower on SATAII. Actual sustained transfer speeds will be pretty much exactly the same (as mechanical HDDs are still slower than the maximum transfer speed of SATAII)

---

### Post by Jungleboss on 2010-08-05
Have anyone gotten SATA III to work with the Marvell 9128? I'm thinking of buying a ssd with SATA III support (Crucial C300).

---

### Post by Moshis on 2010-09-01
Hi All :

I am having the exact same issue on a ASUS P7P55D-E and two 1TB Caviar Black SATA III disks.

Apparently the kernel has reconized the chipset , however it is not able to "see" the disks...


Has anyone solved this ?

Thanks in advance !

---

### Post by clgy15 on 2010-09-01
Well I have the new MSI 880GMA-E45 board with all the new things. The new AMD 880 Chipset, with USB 3.0 and all its SATA ports are the new III ports.
I have had no trouble with any of my hardware at all. However I dont have any SATA III peripherals but all the SATA II peripherals work just fine when plugged in to the SATA III ports

---

### Post by mikakukk on 2010-11-06
> **Moshis said:**
> Hi All :

I am having the exact same issue on a ASUS P7P55D-E and two 1TB Caviar Black SATA III disks.

Apparently the kernel has reconized the chipset , however it is not able to "see" the disks...


Has anyone solved this ?

Thanks in advance !

I don't know how to solve that, but I'm having exactly the same motherboard and hard disks and haven't got it working. I have tried it also in ACHI-mode, but no luck.

---

### Post by cariboo on 2010-11-06
Try the Alternate install iso. It usually doesn't have any problems detecting hardware.

---

