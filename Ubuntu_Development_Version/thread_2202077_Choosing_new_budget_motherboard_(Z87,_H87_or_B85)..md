---
title: "Choosing new budget motherboard (Z87, H87 or B85). Any suggestions?"
date: 2014-01-27
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2014-01-27
Hi guys.

Finally about to buy parts for my broken pc.

Just wondering if there any budget boards you'd recommend as well supported by Linux. Will also use FreeBSD if and when the new hardware is supported. I won't be using Windows at all, so I'll be happy as long as I can boot in legacy BIOS mode (preferably with gpt partitions). The Z87 boards in my price range are:

MSI Z87-G43
Gigabyte GA-Z87-HD3
Asus Z87-K
ASRock Z87 Pro4

I don't really need a Z87 board though because I won't be overclocking and I don't need SLI/Crossfire. I'll be using a locked CPU anyway. With that in mind, I'm also considering these H87 and B85 boards:

Asus H87-PRO
ASRock Fatal1ty H87 Performance
Gigabyte GA-H87-D3H
Asus H87-PLUS
ASRock B85 KILLER
Gigabyte G1.SNIPER B5

Taking the Asus H87-PRO as an example, I've created two draft builds.

Option 1 (preferred CPU, buy video card at a later date):

[http://uk.pcpartpicker.com/p/2GKZn](http://uk.pcpartpicker.com/p/2GKZn)

Option 2 (cheaper CPU and Nvidia GTX 650 Ti):

[http://uk.pcpartpicker.com/p/2Iqse](http://uk.pcpartpicker.com/p/2Iqse)

Thanks in advance for any suggestions.

Cheers,

Paul

---

### Post by oldfred on 2014-01-27
I cannot make any suggestions and am interested myself as I hope (finally) to do a new build.

On video cards
[http://www.phoronix.com/scan.php?page=article&item=linux_gpus_2014start&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_gpus_2014start&num=1)

That site has not done much on motherboards and the few have been high end.
[http://www.phoronix.com/scan.php?page=category&item=Motherboards](http://www.phoronix.com/scan.php?page=category&item=Motherboards)

But it has a related site where users post results based on build.
[http://openbenchmarking.org/](http://openbenchmarking.org/)
[http://openbenchmarking.org/s/Motherboard](http://openbenchmarking.org/s/Motherboard)

Have not seen a lot of threads on issues with motherboards or builds. Most are laptops, so either few are building systems or those that build systems do not have issues??
There have been a few issues with very specific settings on older versions of some brands.

 Gigabyte's ASPM Motherboard Fix: Use Windows
[http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg](http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg)

      Some have issues with Asrock.
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

     ASUS Rampage IV Extreme motherboard
[http://ubuntuforums.org/showthread.php?t=2063073](http://ubuntuforums.org/showthread.php?t=2063073)

Someone posted this:
 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

Often it is not the brand of motherboard, but specific parts on motherboard by model, like Ethernet or other chips that may be an issue. And most have drivers or work arounds.

---

### Post by QDR06VV9 on 2014-01-27
> **paul_in_london said:**
> Hi guys.

Finally about to buy parts for my broken pc.

Just wondering if there any budget boards you'd recommend as well supported by Linux. Will also use FreeBSD if and when the new hardware is supported. I won't be using Windows at all, so I'll be happy as long as I can boot in legacy BIOS mode (preferably with gpt partitions). The Z87 boards in my price range are:

MSI Z87-G43
Gigabyte GA-Z87-HD3
Asus Z87-K
ASRock Z87 Pro4

I don't really need a Z87 board though because I won't be overclocking and I don't need SLI/Crossfire. I'll be using a locked CPU anyway. With that in mind, I'm also considering these H87 and B85 boards:

Asus H87-PRO
ASRock Fatal1ty H87 Performance
Gigabyte GA-H87-D3H
Asus H87-PLUS
ASRock B85 KILLER
Gigabyte G1.SNIPER B5

Taking the Asus H87-PRO as an example, I've created two draft builds.

Option 1 (preferred CPU, buy video card at a later date):

[http://uk.pcpartpicker.com/p/2GKZn](http://uk.pcpartpicker.com/p/2GKZn)

Option 2 (cheaper CPU and Nvidia GTX 650 Ti):

[http://uk.pcpartpicker.com/p/2Iqse](http://uk.pcpartpicker.com/p/2Iqse)

Thanks in advance for any suggestions.

Cheers,

Paul
Paul I have never gone wrong with ASUS the Specs on that board look good enough even for expansion.
And if you have to get stuck with UEFi well this looked promising.
```
[COLOR=#333333][FONT=Arial]New UEFI BIOS &#8211; Friendlier, easier, and more intuitive with helpful info added[/FONT][/COLOR]
```
MSI Boards havent fared well at least for me.
Cant wait to see your new rig in action;)

---

### Post by kansasnoob on 2014-01-27
I grabbed one of these recently:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138377](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138377)

The stinking ATI Radeon HD 3000 has been such a pain I'm both getting bald and growing a neck-beard!

---

### Post by ventrical on 2014-01-27
> **paul_in_london said:**
> Hi guys.

Finally about to buy parts for my broken pc.

Just wondering if there any budget boards you'd recommend as well supported by Linux. Will also use FreeBSD if and when the new hardware is supported. I won't be using Windows at all, so I'll be happy as long as I can boot in legacy BIOS mode (preferably with gpt partitions). The Z87 boards in my price range are:

MSI Z87-G43
Gigabyte GA-Z87-HD3
Asus Z87-K
ASRock Z87 Pro4

I don't really need a Z87 board though because I won't be overclocking and I don't need SLI/Crossfire. I'll be using a locked CPU anyway. With that in mind, I'm also considering these H87 and B85 boards:

Asus H87-PRO
ASRock Fatal1ty H87 Performance
Gigabyte GA-H87-D3H
Asus H87-PLUS
ASRock B85 KILLER
Gigabyte G1.SNIPER B5

Taking the Asus H87-PRO as an example, I've created two draft builds.

Option 1 (preferred CPU, buy video card at a later date):

[http://uk.pcpartpicker.com/p/2GKZn](http://uk.pcpartpicker.com/p/2GKZn)

Option 2 (cheaper CPU and Nvidia GTX 650 Ti):

[http://uk.pcpartpicker.com/p/2Iqse](http://uk.pcpartpicker.com/p/2Iqse)

Thanks in advance for any suggestions.

Cheers,

Paul

  I aquired this MoBo ->  

[http://www.msi.com/product/mb/B75MA-P45.html](http://www.msi.com/product/mb/B75MA-P45.html)

I currently have the Intel G630 processor (dual core) and it runs great.  I am currently running it with onboard SandyBridge graphics and SATA III SSD. The BIOS allows you to overclock depending on which processor you install. It will not overclock a locked processor.  I only paid $89CAD but it has probably come down in price. It is smooth, quiet and fast. With USB 3 and SATA 3. Also with PCIe 3 (with next generation compatible).

 Testing with an SSD it makes for no down time. Haven't tried FreeBSD on it.

Downside: No IDE connectors on board. SATA only, but you can use a SATA to IDE bridge via USB .

Regards..

---

### Post by mörgæs on 2014-01-28
Hardly a matter relevant to U+1; moved to Hardware.

---

### Post by ventrical on 2014-01-28
> **mörgæs said:**
> Hardly a matter relevant to U+1; moved to Hardware.

We test development releases on new hardware, always.  So it is very relavant I would opine to believe.

Regards,

Ventrical

---

### Post by fjgaude on 2014-01-28
Here's what's working for me but only on 14.04 and 13.10. Will not work installing 13.04, 12.10 or 12.04.4:

Ubuntu Linux on a Z87 Haswell motherboard, ASRock Model Z87E-ITX with Intel i5-4440S CPU (2.8MHz, 800KHz to Turbo 3.3MHz as needed), 16G DDR3 G.Skill 2400MHz, Plextor M5S SSD 256G, WD VelociRaptor 500G HDD, latest UEFI BIOS 2.3, Suspend and Resume without issue. Booting fast, 10 to 20 seconds, from either Plextor SSD or VelociRaptor HDD in Lian Li PC-Q30X case.

It's a $1200 box but worth every bit of it.

---

### Post by QDR06VV9 on 2014-01-29
> **ventrical said:**
> We test development releases on new hardware, always.  So it is very relavant I would opine to believe.

Regards,

Ventrical
+1:) I thought it was safe when oldfred did not move it..Oh Well

---

### Post by ventrical on 2014-01-29
> **runrickus said:**
> +1:) I thought it was safe when oldfred did not move it..Oh Well

paul_in_london is always on the avant guard for testing release candidates for kernels ... a U+1 regular.. but .. anyways .. here we are....:)lol

---

### Post by mörgæs on 2014-01-29
Ok, moving it back. Was hoping to hear from original poster if he insisted, but here you go.

---

### Post by QDR06VV9 on 2014-01-29
> **mörgæs said:**
> Ok, moving it back. _Was hoping to hear from original poster if he insisted,_ but here you go.

Thanks morgaes.He's probably building his new rig as we speak :)

---

### Post by oldfred on 2014-01-29
> I thought it was safe when oldfred did not move it
oldfred probably would have moved thread also if he was paying attention. But often uses the new threads search and does not pay close attention to which sub-forum thread came from.

---

### Post by kansasnoob on 2014-01-29
I'm glad to see it back here because I need to upgrade a bunch of hardware :)

---

### Post by QDR06VV9 on 2014-01-29
And again a special appreciation to The Moderators for allowing this.:)

---

### Post by ventrical on 2014-01-30
> **runrickus said:**
> And again a special appreciation to The Moderators for allowing this.:)

+1

 btw .. for anyone interested.

intel

non-overclockable H61,H67,B75,H77
overclockable P67, Z68,Z75,Z77

---

### Post by paul_in_london on 2014-02-01
> **mörgæs said:**
> Hardly a matter relevant to U+1; moved to Hardware.

@mörgæs: Thanks for reinstating the thread.

Still trying to decide on components. Looking at buying something along these lines:

Motherboard: ATX Gigabyte H87-D3H (Audio chipset Realtek ALC892, LAN chipset Intel i217V)
CPU: Core i5-4570S (65W TDP)
RAM: Corsair Vengeance 16GB (2 x 8GB)
Storage: Crucial M500 or Samsung 840 EVO 120GB (and 2 existing 500GB HDD)
PSU: Antec NEO ECO 520C 520W
No gpu for now, but may get one at a later date.

I think the i217V is supported by the e1000e driver which is provided in kernel 3.13. The main thing I've been struggling with is the choice of mobo. H87 is good enough for me because I won't be gaming or overclocking. The other ATX boards I've been considering in the same price range are:

ASRock Z87 Pro 3
Gigabyte GA-H87-HD3
MSI H87-G43
Gigabyte GA-Z87-DS3H
Asus H87-Plus
Asus H87-Pro
ASRock H87 Performance
Gigabyte GA-Z87-HD3

Resources:

[http://uk.pcpartpicker.com](http://uk.pcpartpicker.com)
[http://www.reddit.com/r/buildapc](http://www.reddit.com/r/buildapc)
[http://www.tonymacx86.com/general-hardware-discussion/100568-latest-haswell-lga1150-motherboard-info.html](http://www.tonymacx86.com/general-hardware-discussion/100568-latest-haswell-lga1150-motherboard-info.html)
[http://www.gamersnexus.net/guides/1132-intel-haswell-chipset-comparison](http://www.gamersnexus.net/guides/1132-intel-haswell-chipset-comparison)
[http://www.logicalincrements.com/](http://www.logicalincrements.com/)
[http://www.asus.com/websites/global/aboutasus/OS/Linux1305.pdf](http://www.asus.com/websites/global/aboutasus/OS/Linux1305.pdf)
[http://hardforum.com](http://hardforum.com)
[http://www.overclock.net](http://www.overclock.net)
[http://www.pc-specs.com](http://www.pc-specs.com)
[http://www.tomshardware.co.uk](http://www.tomshardware.co.uk)
[http://forums.opensuse.org/showthread.php/493659-Hardware-motherboard-experience-for-new-PC](http://forums.opensuse.org/showthread.php/493659-Hardware-motherboard-experience-for-new-PC)
[http://www.linuxlookuphttp://www.reddit.com/r/linuxquestions/comments/1u64em/has_anyone_installed_linux_on_a_machine_with_a/.com/review/asus_z87_pro_motherboard_review](http://www.linuxlookuphttp://www.reddit.com/r/linuxquestions/comments/1u64em/has_anyone_installed_linux_on_a_machine_with_a/.com/review/asus_z87_pro_motherboard_review)
[http://www.linuxquestions.org/questions/linux-hardware-18/asrock-z87-pro3-motherboard-works-well-with-current-linux-4175484991/](http://www.linuxquestions.org/questions/linux-hardware-18/asrock-z87-pro3-motherboard-works-well-with-current-linux-4175484991/)
[http://www.anandtech.com/print/6989/intel-z87-motherboard-review-with-haswell-gigabyte-msi-asrock-and-asus-at-200](http://www.anandtech.com/print/6989/intel-z87-motherboard-review-with-haswell-gigabyte-msi-asrock-and-asus-at-200)
[http://www.reddit.com/r/linuxquestions/comments/1u64em/has_anyone_installed_linux_on_a_machine_with_a/](http://www.reddit.com/r/linuxquestions/comments/1u64em/has_anyone_installed_linux_on_a_machine_with_a/)

---

### Post by QDR06VV9 on 2014-02-02
> **paul_in_london said:**
> @mörgæs: Thanks for reinstating the thread.

Still trying to decide on components. Looking at buying something along these lines:

Motherboard: ATX Gigabyte H87-D3H (Audio chipset Realtek ALC892, LAN chipset Intel i217V)
CPU: Core i5-4570S (65W TDP)
RAM: Corsair Vengeance 16GB (2 x 8GB)
Storage: Crucial M500 or Samsung 840 EVO 120GB (and 2 existing 500GB HDD)
PSU: Antec NEO ECO 520C 520W
No gpu for now, but may get one at a later date.

I think the i217V is supported by the e1000e driver which is provided in kernel 3.13. The main thing I've been struggling with is the choice of mobo. H87 is good enough for me because I won't be gaming or overclocking. The other ATX boards I've been considering in the same price range are:

ASRock Z87 Pro 3
Gigabyte GA-H87-HD3
MSI H87-G43
Gigabyte GA-Z87-DS3H
[COLOR=#000080]Asus H87-Plus
Asus H87-Pro[/COLOR]
ASRock H87 Performance
Gigabyte GA-Z87-HD3



<Removed>
[COLOR=#000080]Asus H87-Plus
Asus H87-Pro
[COLOR=#000080][COLOR=#000080][COLOR=#000080]I Think you will be happy with either one!
All my MSI boards crapped out within one year![/COLOR][/COLOR]

[/COLOR][/COLOR]

---

### Post by cariboo on 2014-02-02
I've used and sold MSI exclusively for the last 10 years, and have never had a problem with any system, except for one that some how got coffee spilled inside. I've never had a problem installing and running any distribution. I'd recommend MSI as a good choice to base a system on.

---

### Post by QDR06VV9 on 2014-02-02
My Apologies if that sounded like a flame on MSI it wasn't.
That was merely _my_ experience with them.:(
I think Ventrical is using one now.
Been watching him give it the go round.:D

---

### Post by ventrical on 2014-02-04
> **runrickus said:**
> My Apologies if that sounded like a flame on MSI it wasn't.
That was merely _my_ experience with them.:(
I think Ventrical is using one now.
Been watching him give it the go round.:D

Yes .. the MSI B75MA-P45  with a dual core  G630 (upgradable to i7) with 16GB (upgradeable to 32GB) DDR3 and 120GB SSD is a screaming eagle. Don't forget you guys , the Intel HD Graphics comes with the processor for the LGA1155 socket!!

@paul_in_london

 Make sure when you purchase your Intel i5 that it has HD Intel graphics that comes with it. You will not need a gpu although you can put in a  nVidia or AMD card later in the PCIe slot.

  The Intel Graphics on the 3rd Gen processors are just awesome and with SSD it makes testing a breeze with quick results in that form factor.

  Actually , with these newer boards, you don't need to overclock unless you are really on the cutting edge testing bent. :) lol

  I was reluctant at first to try the MSI MoBo but  it has yet to flicker.:) It has been a  gradual build. Of course I will put an i7 in it and try to fry it. :) .. That's part of what we do here eh :)lol



Regards

---

### Post by bcschmerker on 2014-02-05
I'm looking at a contingency for a new rebuild of my Hot Rod gPC™ (2.9 GHz Advanced Micro Devices® Athlon 64® X2 5600+, 780G northbridge, SB700 southbridge, ATi® Radeon® HD™ 3200 GPU) around Intel® hardware, given the problems I have had in the past with LinUX Kernel 2.6.12-18-rt (originally tested in Ubuntu® 8.04-LTS) on AMD® hardware.  The Asus® H87M-PLUS and H87M-PRO both fit my old Everex® TC2502 case as modified, and I reckon that a 2.4 to 3.2 GHz Intel® 4th-Generation Core™ will run LinUX Kernel 3.13.0-lowlatency reliably (as did 2.6.11-14-rt on the TC2502's original VIA® C7-D under Ubuntu® 8.04-LTS); plus they will take one of the larger Unicomp® Model M's built for IBM® 85xx-compatible systems - I have an On The Stick 122 contingency design incorporating a fallback pointing device, in the unlikely event that the USB drivers crash.  (Not much luck with late-model micro-ATX's that will still support the disquette transport in my Mitsumi® FA404 combo drive, however, more's the pity.)

Anybody run into panics and oopses of Kernel 3.13.0-generic and/or -lowlatency on Intel® H87-equipped rigs running Ubuntu® 13.12a1 or 14.01a2?  I'd like a heads up on any complication that might give cause to delay my dist-upgrade(s) to 14.04-LTS.

---

