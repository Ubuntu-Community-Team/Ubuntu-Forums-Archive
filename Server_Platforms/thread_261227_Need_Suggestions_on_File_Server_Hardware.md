---
title: "Need Suggestions on File Server Hardware"
date: 2006-09-19
forum: Server Platforms
---

### Post by bowlofudon on 2006-09-19
I'm getting tired of all my files spread out throughout all of my computers. I'd like one centralized place to store my files. The system should be easily expandable and be able to handle network connections made by apple, linux, and windows systems. I plan on getting 1tb of storage.

Although not necessary, I would definately like to be able to access my files remotely.

Does any one have any suggestions/links/builds for my project? Thanks a bunch.

Budget: max $1500

Processor:
[AMD Athlon 64 3500+ 2.2Ghz AM2 - $90](http://www.newegg.com/Product/Product.asp?Item=N82E16819103633)
Motherboard:
[ ASUS M2N-SLI Deluxe Socket AM2 NVIDIA nForce 570 SLI MCP ATX AMD Motherboard  - $82](http://www.newegg.com/Product/Product.asp?Item=N82E16813131013R)
Memory:
[OCZ Gold Series 1GB (2 x 512MB) 240-Pin DDR2 SDRAM DDR2 667 (PC2 5400) - $112](http://www.newegg.com/Product/Product.asp?Item=N82E16820227046)
CD DVD Burner:
[NEC 16X DVD±R DVD Burner Black IDE/ATAPI Model ND-3550A - $30](http://www.newegg.com/Product/Product.asp?Item=N82E16827152058)
Hard Drives (4x):
[ Western Digital Caviar SE16 WD2500KS 250GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive - $78](http://www.newegg.com/Product/Product.asp?Item=N82E16822144701)
Video Card:
[eVGA 256-P2-N423-LX Geforce 7300LE Supporting 512MB(256MB On-Board) 64-bit GDDR2 PCI Express x16 Video Card - $56](http://www.newegg.com/Product/Product.asp?Item=N82E16814130009)
Case:
[ COOLER MASTER Centurion 5 CAC-T05-UW Black Aluminum Bezel, SECC ATX Mid Tower Computer Case - $45](http://www.newegg.com/Product/Product.asp?Item=N82E16811119068)
Power Supply:
[Antec SmartPower 2.0 SP-450 ATX12V 450W Power Supply 115/230 V UL, TUV, CB, FCC CLASS B, CUL - $60](http://www.newegg.com/Product/Product.asp?Item=N82E16817103936)

Total = $787


I'd like to put my hard drives in raid, but I'm unfamiliar with using raid. Any suggestions/links? If I put my hard drives in raid 5, would that require me to get an additional 4 hard drives?

---

### Post by ff2k on 2006-09-20
Q1: Why would you want a high-end video card for a file server? Why not get a motherboard with built-in video?

Q2: How important is the data you're going to store? Yes, data is important but is it important enough to invest in additional hardware for a RAID hardware device?

We have an old SCSI-to-SCSI RAID device. Which basically sits between the SCSI controller and the SCSI hard drives.

OS <--> SCSI CTRL <--> RAID HW <--> SCSI HDs

You configure RAID via the on-board control panel. The SCSI controller sees the RAID HW was one HD. This is OS independent.

If you want to replace a HD, just put that HD offline, replace it, then rebuild the array.

Nowadays, there are SCSI-to-[S]ATA devices or even SATA RAID enclosures so my suggestion is invest on that.

---

### Post by ff2k on 2006-09-20
BTW, my suggestion is RAID 1. The performance sucks but at least you have two identical copies.

For the truly paranoid, another USB/Fireware enclosure to be placed at another location or to take with you on the road.

---

### Post by bowlofudon on 2006-09-20
Thanks for the help ff2k. I'm planning on using raid 5. The $55 video card is for the INTENSE screensavers i'll be using (good point - going to switch it with a cheaper video card ;D ).

---

### Post by hkgonra on 2006-09-20
First off a 7300 is NOT a high end video card. 
If I were you for a fileserver I would look at Dell and catch a deal on one of their 1420sc servers. 
I have a couple of them that I picked up for $500 each. Added my own HD's and raid card and had a smoking system for under $1000 each.

---

### Post by Child of Wonder on 2006-09-20
I agree.  Unless you plan on actually using the GUI on your file server (which I would recommend against) all you need is onboard video and you should install Ubuntu server.  Everything you need to do can be done remotely via SSH or a Web interface such as Webmin.

Also, an Athlon 64 system is going to be hella overkill for what you need.

For example, I have a server at home running two 500GB drives in software RAID 0 (soon to be 4 drives in RAID 5 once I have the cash), Apache2, Postfix, FTP, Gnump3d, DNS, DHCP, a nightly rsync for a company I do consulting for, and more.  All I'm running on this machine is an Athlon XP 2100+ and 512MB of RAM and even that appears to be overkill.  Except during the rsync, my load avg rarely hits .10.

If you want 64 bit, I'd recommend getting a cheap Athlon 64 3000+ Venice core, Arctic 64 cooler, 512MB RAM, a motherboard with lots of SATA connections (and onboard video if possible or the cheapest video card you can find), the most reliable PSU you can buy (Seasonic, Fortron, etc), a nice full ATX case with great cooling for your drives, and then drop everything else on storage (4 500GB Seagates in RAID 5 would be perfect).

Check this out:

> 
1 	ENERMAX CS-10182-BA Black/Silver SECC 1.0 mm Server Computer Case - Retail
Model #: CS-10182-BA
Item #: N82E16811124034
	$86.00

4 	Seagate Barracuda 7200.10 ST3500630AS 500GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM
Model #: ST3500630AS
Item #: N82E16822148136
	$259.99 	  	$1,039.96

1 	Foxconn NF4UK8AA-8EKRS Socket 939 NVIDIA nForce4 Ultra ATX AMD Motherboard - Retail
Model #: NF4UK8AA-8EKRS
Item #: N82E16813186037
	$65.99 	  	$65.99

1  	 Connect3D 3001 Radeon X300SE 128MB DDR PCI Express x16 Video Card - Retail
Model #: 3001
Item #: N82E16814142069
	$40.99 	  	$40.99

1 	SONY Black IDE DVD-ROM Drive Model DDU1615/B2s - OEM
Model #: DDU1615/B2s
Item #: N82E16827101131
	$18.99 	  	$18.99

1 	SeaSonic S12-500 ATX12V 500W Power Supply - Retail
Model #: S12-500
Item #: N82E16817151024
Remove item from Cart Remove  Save Save  Move To Wish List
	$129.99 	  	$129.99

1 	ARCTIC COOLING Freezer 64 Pro Cooling Fan with Heatsink - Retail
Model #: Freezer 64 Pro
Item #: N82E16835185125
	$29.99 	  	$29.99

1 	Arctic Silver 5 Thermal Compound - OEM
Model #: ARCTIC SILVER 5
Item #: N82E16835100007
	$5.99 	  	$5.99

1 	OCZ Premier Series 512MB 184-Pin DDR SDRAM DDR 400 (PC 3200) System Memory Model OCZ400512PH - Retail
Model #: OCZ400512PH
Item #: N82E16820146846
	$54.99 	  	$54.99

1 	AMD Athlon 64 3000+ Venice 1.8GHz Socket 939 Processor Model ADA3000BPBOX - Retail
Model #: ADA3000BPBOX
Item #: N82E16819103537
	$64.00 	  	$64.00
  	
	Subtotal: 	$1,536.89

---

### Post by bowlofudon on 2006-09-20
Thanks for the comments Child of Wonder. I noticed a few things though.

I noticed that the motherboard's hardware raid only supports (NV RAID 0/1/0+1 JBOD) vs the motherboard on my list supports (NV RAID 0/1/0+1/5 JBOD) Raid which brings up another question. Is Nvidia's built in hardware raid reliable or should I go with a software raid solution?

---

### Post by Child of Wonder on 2006-09-20
> **bowlofudon said:**
> Thanks for the comments Child of Wonder. I noticed a few things though.

I noticed that the motherboard's hardware raid only supports (NV RAID 0/1/0+1 JBOD) vs the motherboard on my list supports (NV RAID 0/1/0+1/5 JBOD) Raid which brings up another question. Is Nvidia's built in hardware raid reliable or should I go with a software raid solution?

The RAID built into motherboards isn't true hardware RAID.  It still needs a driver/software to run.  It's no more reliable than software RAID, which is what I would go with in this case.

You can set it up using mdadm in Ubuntu and even have it email you if a drive fails.  Since those Seagates have 5 year warranties, when one goes bad you just pop that sucker out, RMA it, and put in the new drive when it arrives then rebuild the array.

---

### Post by bowlofudon on 2006-09-20
Thanks for all the help ;)

---

### Post by ff2k on 2006-09-20
> **hkgonra said:**
> First off a 7300 is NOT a high end video card. 


:razz: hehehe! That only means I'm no longer updated in the uber-l337 video cards anymore.

This is a bit OT but since we're discussing RAID, this is what we have:

[Mylex DAC960SX being sold on eBay.]("http://cgi.ebay.com/Mylex-DAC960SX-SCSI-Disk-Array-Controller_W0QQitemZ170026512531QQihZ007QQcategoryZ39969QQcmdZViewItem")

[IMG]http://www.technology-exchange.net/ebaypics/060901JDL-MylexController-01.JPG[/IMG]

You slap all your SCSI hard drive to this device and connect your SCSI card to it. The SCSI card sees the Mylex as your HD. Since it's hardware RAID, no worries on drivers and software configuration.

Ours is 8 years old and still working. I may have to look into a replacement like this:

[rack mounted RAID enclosure]("http://www.promise.com/product/product_detail_eng.asp?segment=UltraTrak&product_id=95")
[regular RAID enclosure]("http://www.promise.com/product/product_detail_eng.asp?segment=UltraTrak&product_id=89")

And have another external USB/Firewire based HD because I'm paranoid.

---

### Post by Zyzzyx on 2006-09-20
Just a couple things that I notice, that have been mentioned.

I'll agree on the RAID side, especially for a fileserver. RAID 1 would be great, but I don't see a problem with RAID 5, its done me well over the years. Get a dedicated RAID card to handle it.

And yeah, its only $90, but that cpu would be WAY more than you need for just a fileserver. At my previous job the fileserver there was a P3-800, with I think 1gb memory, handled an office of 40 workstations with no problems.


Now, something else to consider would be upgrading (if you haven't already) to a gigabit network and NICs for everything. If you are going to have everything on there, having gigabit connection will make a BIG difference in how fast it all feels.

---

