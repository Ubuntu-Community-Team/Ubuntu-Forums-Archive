---
title: "Dell PowerEdge 2500 does not boot after adding PCI SATA raid card"
date: 2009-05-31
forum: Server Platforms
---

### Post by paulnj on 2009-05-31
I have a working installation of Ubuntu Server (8.04) on an old PowerEdge 2500 dell server.  I want to add SATA HD, so I attenpted to install a Rosewill e-SATA 4 Port PCI Adapter with RAID (Model RC-2009-EX), but when I bring the system back up, Ubuntu does not boot.  I get the:
[INDENT][FONT=Courier New][COLOR=Blue]-"Dell" Startup screen,
-embedded server management and primary system backplane controller firmware information

-Processor information

- New SATA RAID control detected
  - lists Harddrive installed on it (blank)

-Raid Controller
-Press Ctrl A for the raid config util
-Booting controller kernel....Controller Started

-Waiting for Controller to start, controller started.

-Controller Post operation successful
-Controller memory sixe 128MB

-Container #0 (lists size and other info)
-Container #1 (Lists size and other info)
-2 Container(s) Found

-Bios Installed Successfully! 
[/COLOR][/FONT][/INDENT]
And then nothing.  It just sits there... I have looked at the server managment console and see that teh new hardrive is at the end... in reading other posts (which are all geared towards a new install of Ubuntu) I see some suggestion for increasing the boot delay in GRUB, but I don't currently see this entry in my /boot/grub/menu.lst.

Any help from the comunity would be greatly appreciated.

---

### Post by alastair on 2009-05-31
If this is not getting to grub, perhaps something up with boot device priority? 

A guess only - perhaps it is looking to boot from a SATA disk (non-existent). This means going into the BIOS and looking at boot order/priority. It might have changed when you added the card, and you need to push your boot/OS disk up the list again.

---

### Post by paulnj on 2009-06-02
@alastair Thanks for your quick reply and sorry I did not mention it... I also check that... I can enter the BIOS and check the order of drives... I see that the new (empty) drive was detected and added to the bottom of the list... thus the original boot order was maintained: CD, C, <new drive>. 

I'm still hopping that someone here will share their experiences if they have encountered this issue as well...

In the mean time, I spent sunday researching this issue and found that in some cases it seems that the BIOS of the RAID card could interfeer with an already existing RAID and specially if loaded before the existing RAID's bios, it could prevent the system from booting... With that in mind, I have ordered a PCI card that I can flash the bios to not load at boot time (found helpful information on newegg).

---

### Post by alastair on 2009-06-02
OK, well maybe use CTRL-A (or whatever) at boot and go into the BIOS of the RAID card, and have a look around (maybe disable it). Perhaps that will help. Perhaps try a different PCI slot?

---

### Post by windependence on 2009-06-02
> **paulnj said:**
> @alastair Thanks for your quick reply and sorry I did not mention it... I also check that... I can enter the BIOS and check the order of drives... I see that the new (empty) drive was detected and added to the bottom of the list... thus the original boot order was maintained: CD, C, <new drive>. 

I'm still hopping that someone here will share their experiences if they have encountered this issue as well...

In the mean time, I spent sunday researching this issue and found that in some cases it seems that the BIOS of the RAID card could interfeer with an already existing RAID and specially if loaded before the existing RAID's bios, it could prevent the system from booting... With that in mind, I have ordered a PCI card that I can flash the bios to not load at boot time (found helpful information on newegg).

You're probably gonna have to disable the existing RAID card to use the other one, or, if you have the OS on the new RAID card, you'll have to set up the drive on the new card and even then, there will be issues with grub. It's not fun. The best way would be to do a new install once the card is installed.

-Tim

---

### Post by paulnj on 2009-06-03
@alastair, @windependence: Thank you both for your responses and suggestions... So the good news is I HAVE SOLVED MY PROBLEM... As I indicated in my earlier post, some information I saw online (particularly the newegg page for this card **[COLOR=Blue][http://www.newegg.com/Product/Product.aspx?Item=N82E16816132007](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132007)[/COLOR]** ) suggested that in some systems (particularly older ones) the BIOS on the addin card may get in front of an already existing RAID bios and not allow you to boot your system... This was exactly the issue... I purchased the addin card in the link above and used the instruction by Erik_FL in that same product's user reviews page (**[COLOR=Blue][here]("http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16816132007")[/COLOR]**) to erase the card's BIOS... This worked... My system boots up just fine now.  
What I found interesting is that it is very hard to find an addin card without a bios on it... Seems all of them have them now a day, which in my case (and others accoring to my research) causes an issue with an existing RAID system if one exists.
Hopefully others will find my experience and how I was able to fix it helpful.  (now to buy an external SATA disk enclosure).

Thanks again.

---

