---
title: "My report on that Vista Presario FT 762 NR  Laptop for $399"
date: 2008-05-06
forum: Windows
---

### Post by Midwest-Linux on 2008-05-06
Just a report of sorts as this might help others. Staples (here in the U.S.) has a Presario laptop on sale this week for $399. I picked it up with the intention of installing XP and Linux on it. Specs are 1.9 Ghz dual core AMD Athlon X2 with 1 GB Ram and Vista Premium. 

 The Ram use was like 70%, under no activity. Looking at some forums on how to speed this slug up. I got rid of the User account control, disabled superfetch, disabled Windows defender, turned off system restore, deleted Norton anti spyware, deleted Symantec, turned off aero, got rid of all the free games on it. Reduced startup programs to bare minimum. 

 Now I am at 51% ram usage, still way more than XP. 

But it gets better. I ran the Ubuntu 8.04 Live DVD, the ram usage hovered around 165 MB, the Live DVD found and installed the Athos wireless wifi and the required HAL....more about this later.

I ran the live KNOPPIX 5.3 DVD, within no time the Knoppix booted up, found all the drivers and worked flawlessly! I was able to access the internet, listen to streaming audio, install flash. And the Ram usage was averaging 150 to 155 MB of Ram. Guess whats going to be running on this computer soon?

 I decided that I will redo the entire installation later this month after I check all the forums for the XP drivers for this machine. Forget about going to Compaq for the XP drivers, but some forums listed where drivers for XP can be found. If anyone is interested I can post one link for starters.

 In the meantime, I'll just install Wubi 8.04 for a Ubuntu dual boot the easy way. Downloaded wubi and that started downloading Ubuntu 8.04 and installing 8.04 ended me up at initramfs. No installation, remember that the Ubuntu 8.04 LIVE DVD ran fine on this machine and why a install of the same distro would not work is beyond me. 

 Uninstall Wubi 8.04 and did some searching.

 Read some posts, some suggested using 7.04 instead, I tracked down the Wubi 7.04 installer. Installed that and then it slowly downloaded the alternate 7.04...I mean slowly... at times at 11 kbs. Stopped downloading, shut the machine off and turned it back on and restarted downloading this time a lot faster at 1.1 MB. Then it came for it to install, it went through all the processes of installing much like you would see if you are using the alternate installer.

 Little message says time to reboot. Then started through the start up and got as far as the xorg.org which messages included about "Screens not found". 

 At that time I quit and will try another approach or two before I do a complete wipe of the hard drive and do a dual boot with XP Pro and likely Knoppix or Linux Mint later this month.

 So why didn't I buy a EEePC instead? Simple, The EePC is a great concept, but for the same price, instead of a 4 BG or 8 GB drive, you can get one with 120 Gig hard drive, twice the ram and a CD and DVD burner. Maybe if the EePC was priced at $129 or $149 it would be worth it... in my opinion.

 I'll add more later to this as try other options, the reason for this post was to maybe help others who bought or are considering buying this laptop.

---

### Post by smoker on 2008-05-06
good review, and i'm sure anyone looking for a laptop would appreciate it,
:-)

---

### Post by SidStudios on 2008-05-06
It seems you have a laptop similar to mine; I've got a Compaq Presario v3000 series laptop. The only problem in mine which I've had on Ubuntu was the Broadcom Wireless. I seriously suggest 8.04; I had some problems in 7.10 about monitors being detected:
this is caused because Wubi sets a too high resolution for your monitor, and without the proprietary nVidia drivers, it cannot load that resolution. I suggest deleting the /etc/xorg.conf and using 800x600 for about 5 minutes until you get the nVidia driver.
But then again, I suggest 8.04. You've got Atheros Wifi, an AMD Turion TL-58 and nVidia 7000M or 7050M or something, I'm guessing? I've got 7150M, but this is a laptop I got free, and Ubuntu works quite well on it. If you need help, you can refer to the guide in my sig, and post here if there are any problems ;)

---

### Post by Midwest-Linux on 2008-05-06
> **SidStudios said:**
> It seems you have a laptop similar to mine; I've got a Compaq Presario v3000 series laptop. The only problem in mine which I've had on Ubuntu was the Broadcom Wireless. I seriously suggest 8.04; I had some problems in 7.10 about monitors being detected:
this is caused because Wubi sets a too high resolution for your monitor, and without the proprietary nVidia drivers, it cannot load that resolution. I suggest deleting the /etc/xorg.conf and using 800x600 for about 5 minutes until you get the nVidia driver.
But then again, I suggest 8.04. You've got Atheros Wifi, an AMD Turion TL-58 and nVidia 7000M or 7050M or something, I'm guessing? I've got 7150M, but this is a laptop I got free, and Ubuntu works quite well on it. If you need help, you can refer to the guide in my sig, and post here if there are any problems ;)

 The only reason I went the Wubi route instead of doing a straight dual boot partition. Because I have heard stories that Vista does not like partitioning and I felt Wubi was a wiser choice for now.

 I don't want to hose the Vista just yet, until I get enough to buy a XP PRO license and then will do a dual boot with Knoppix later this month. 

 If I know for a fact I could partition the Vista without hosing it, I'd do it in a heartbeat. I am still amazed that Vista still runs 51% Ram with nothing running other than the desktop and thats after I got everything deleted and hacked without hosing the system. 

 Now I have a desktop with Windows XP and Linux Mint 4.0 which installed absolutely fine. The original partition was NTFS and there were no issues with Linux Mint 4.0 hosing the partition. So I don't see how there could be issues with hosing the system if I did a dual boot with Vista. But then again all I know about Vista, is that one needs to hack and delete programs to make it run a bit better or buy more ram ...which I refuse to do. 

 The computer I have is also known as the F700, the F762NR is of the F700 series. 

[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01430212&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01430212&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)




Product Number   	KW831UA#ABA
Microprocessor 	1.90 GHz AMD Athlon 64 X2 Dual-Core Processor TK-57
Microprocessor Cache 	512KB L2 Cache
Memory 	1024 MB
Memory Max 	Up to 3GB DDR2
Video Graphics 	NVIDIA GeForce 7000M
Video Memory 	Up to 287 MB
Hard Drive 	120 GB (5400 rpm)
Multimedia Drive 	Super Multi 8X DVD±R/RW with Double Layer Support
Display 	15.4" WXGA High-Definition BrightView Widescreen (1280 x 800)
Fax/Modem 	High speed 56K modem
Network Card 	Integrated 10/100 Ethernet LAN
Wireless Connectivity 	802.11 b/g WLAN
Sound 	Altec Lansing speakers
Keyboard 	101-key compatible
Pointing Device 	Touch Pad with dedicated vertical and horizontal Scroll Up/Down pad
External Ports 	

    * 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
    * 3 Universal Serial Bus USB 2.0
    * 1 VGA (15-pin)
    * 1 RJ-11 (modem)
    * 1 TV-Out (S-video)
    * 1 RJ -45 (LAN)
    * 1 headphone-out
    * 1 microphone-in

Dimensions 	14.06" (L) x 10.12" (W) x 1.2" (min H)/1.55" (max H)
Weight 	5.68lbs
Security 	

    * Kensington MicroSaver lock slot
    * Power-on password
    * Accepts 3rd party security lock devices

Power 	

    * 65 W AC Adapter
    * 6-cell Lithium-Ion (Li-Ion)

Software
Operating System:
Genuine Windows Vista Home Premium with Service Pack 1

---

### Post by SidStudios on 2008-05-07
If I remember correctly, I'm pretty sure you can use your Windows Vista CD key for XP ;)

---

### Post by Midwest-Linux on 2008-05-07
> **SidStudios said:**
> If I remember correctly, I'm pretty sure you can use your Windows Vista CD key for XP ;)

 I'll have to check that out, I have both XP Home and XP Pro legal install discs.

Thanks for the scripts on your page.

sudo aptitude install ubuntu-restricted-extras

sudo aptitude install vlc

Which got me thinking, is there a main site with Ubuntu scripts like those you gave? I know they have them spread apart in various pages. Is there like a main depository for them?

More info on that Presario F762NR

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&dlc=en&product=3694906&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&dlc=en&product=3694906&lang=en)

 Driver - Audio
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	Conexant HD-Audio SmartAudio 221 Driver
				11-2007 				4.31.2.50 A 				
»   	Version:
				14.75M 			
	  				  				  				  				 

	
Driver - Graphics
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	NVIDIA GeForce Series Video Driver
				11-2007 				7.15.11.5671 A 				- 				131.31M 			
	  				  				  				  				 

	
Driver - Keyboard, Mouse and Input Devices
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	Ricoh 5-in-1 Card Reader Driver
				03-2008 				3.52.02 A 				
»   	Version:
				2.99M 			
	  				  				  				  				 
	
»   	Synaptics Touchpad
				10-2007 				10.0.13.2 				
»   	Version:
				24.26M 			
	  				  				  				  				 

	
Driver - Modem
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	Conexant HDAUDIO Soft Data Fax Modem with SmartCP Driver
				11-2007 				7.67.0.0 A 				- 				22.23M 			
	  				  				  				  				 

	
Driver - Network
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	Broadcom Wireless LAN Driver for Microsoft Windows Vista
				10-2007 				6.00 E 				
»   	Version:
				17.67M 			
	  				  				  				  				 

	
CD-ROM order page - Recovery Discs
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	Notebook Recovery Disc Set Windows Vista Premium 32bit SP1
				04-2008 				N/A 				- 				0 bytes 			
	  				  				  				  				 

	
BIOS
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	WinFlash for HP Notebook System BIOS (for Notebooks with AMDProcessors) - Microsoft Windows/Vista-Based
				04-2008 				F.07 				
»   	Version:
				2.51M 			
	  				  				  				  				 

	
Software - Security
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	NIS 2008 Modem Compatibility Update
				12-2007 				1.00 A 				- 				433.42k 			
	  				  				  				  				 

	
Software - Solutions
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	Cyberlink YouCam Software
				11-2007 				1002 				- 				49.54M 			
	  				  				  				  				 
	
»   	LightScribe Host Software
				11-2007 				1.10.13.1 				
»   	Version:
				11.76M 			
	  				  				  				  				 

	
Utility - Tools
				
Date
				
Version
				
Previous
				
Size
		
	  				  				  				  				 
	
»   	HP Help and Support for Microsoft Windows Vista (32-bit Editions)
				10-2007 				1.5.1.0 				
»   	Version:
				21.31M 			
	  				  				  				  				 
	
»   	HP Active Support Library
				09-2007 				2.03.0.2 				
»   	Version:
				5.76M 			
	  				  				 

 Thanks again for the fine info.

---

### Post by SidStudios on 2008-05-07
> 
» Broadcom Wireless LAN Driver for Microsoft Windows Vista
10-2007 6.00 E 

You said you had Atheros; just checking up about that.
I don't think you'll need to do much to get Hardy working on your laptop; since you have the same kind of speakers and audio driver as me, this is what you'll need to do:
-Get the nVidia Driver through the restricted drivers manager (This literally takes seconds)
-If your Wireless doesn't work on the live CD, you might have to use a guide to get NDISWrapper working with Atheros, but I think that **Wireless** will work out of the box.
-Sound shouldn't be a problem since this was fixed in Hardy.

---

### Post by Midwest-Linux on 2008-05-09
> **SidStudios said:**
> You said you had Atheros; just checking up about that.
I don't think you'll need to do much to get Hardy working on your laptop; since you have the same kind of speakers and audio driver as me, this is what you'll need to do:
-Get the nVidia Driver through the restricted drivers manager (This literally takes seconds)
-If your Wireless doesn't work on the live CD, you might have to use a guide to get NDISWrapper working with Atheros, but I think that **Wireless** will work out of the box.
-Sound shouldn't be a problem since this was fixed in Hardy.


 I have another laptop with XP Home. I sucessfully did a Wubi with Xubuntu with no issues. Installed flawlessly and that laptop was a HP Pavillion DV 4000. The only odd thing was when I tried the script for the Ubuntu extras, it would not do it. Is that because this was a Xununtu install and not a Ubuntu install?

Can one use Wubi to install Linux Mint 4.0 using the Linux Mint 4.0 disc, since Linux Mint is based from Ubuntu? 

Getting back to this laptop Presario F762NR, would I be better off just shrinking the Vista partition and doing a install without Wubi that way? 

Someone in some post was saying that it would be better to copy Wubi to the C drive and install from there, but how much of a difference would there be from installing from a desktop as opposed from the C drive?

Thanks again

---

### Post by man_from_mystery_babylon on 2008-05-10
Hello Midwest-Linux,

I just bought the same laptop you have, a  Compaq Presario F762NR, and I'd like to convert it to XP too. Could you please post the links to the XP drivers? Thank you.

Regards,
Man_From_Mystery_Babylon

---

### Post by DTMTCM on 2008-05-10
> **man_from_mystery_babylon said:**
> Hello Midwest-Linux,

I just bought the same laptop you have, a  Compaq Presario F762NR, and I'd like to convert it to XP too. Could you please post the links to the XP drivers? Thank you.

Regards,
Man_From_Mystery_Babylon

I just received this laptop too (staples anyone?) and I found a site with the drivers listed.  I got everything but the audio working now on XP.  I'd like to hear more about getting from ground zero to up and running on this laptop in Ubuntu.

Drivers: [http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1210462437565+28353475&threadId=1228428](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1210462437565+28353475&threadId=1228428)

---

### Post by man_from_mystery_babylon on 2008-05-10
Thanks for the info.

---

### Post by Midwest-Linux on 2008-05-10
Links to XP on F700, almost the same as F762

[http://forum.notebookreview.com/archive/index.php/t-194728.html](http://forum.notebookreview.com/archive/index.php/t-194728.html)

[http://forums.techarena.in/showthread.php?t=912857](http://forums.techarena.in/showthread.php?t=912857)


XHead (the poster - seemed to line up all the drivers here)

[http://forum.lowyat.net/topic/596572/+20](http://forum.lowyat.net/topic/596572/+20)

This one seemed to have most of the answers incl the sound.

[http://jmorris.name/computers/quick-review-compaq-presario-f755us-laptop-xp-driver-package-download/](http://jmorris.name/computers/quick-review-compaq-presario-f755us-laptop-xp-driver-package-download/)


Regarding Ubuntu on a Vista machine. My experience is that Wubi does not seem to get along with Vista. I tried the Wubi with Ubuntu 8.04 and Wubi with Ubuntu 7.04 and it didn't install. When I ran a LIVE Ubuntu 8.04 DVD it ran flawlessly. But this machine does not get along with Wubi, or at least my F762NR.

 Side note,... did some checking and there is a F762AU, that must be the Australian model. It seems that F700 is the series of Presario laptops that the F762NR falls under. 

But there is more good news....

 Vista's best feature (and perhaps its only feature worth noting)  is that it comes with a partition shrink program. It is top notch
and its real easy to do.

 If you want to do dual boot, shrink the partition on the C Drive. (As you know, the Presario F762NR comes with a D partition too, used for system recovery). 

You want to shrink the C drive some 10 or 15 GB less to give you a free partition (if you have 100 Gig-shrink this by 10 to 15 GB and you now have 85 to 90 gig for Vista and have the rest as free space for your installation of Ubuntu, (I did 12 GB). Here is how its done.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

However the instructions are different for the Presario F762NR

Here is what I did (Double Click)

1. Control Panel
2. Administrative Tools
3. Computer Management
4. Disk Management (You will see it in the left side column)

One Left click (highlight the C Drive)
Right click once the C drive (Opens a window, scroll down a bit to "Shrink Volume" and that will brink up yet another window called "Shrink C"...and then take it from there.

After doing that, shut down and reboot. Use the ALTERNATE Ubuntu 8.04 Version. When the partitioner part comes up, use the freed space to install Ubuntu 8.04 on. Make sure you leave the internet connected up to it via the Ethernet, makes things easier. Then it should install with no issues and will even install the proprietary drivers for it to. It seems to hang a bit when it gets to "Apt Mirror" at about 28%, just leave it and it should be fine.

It will also install grub. Upon boot you will go to the grub window and select what you want.... it will read.

Ubuntu Generic
Ubuntu Recovery
Ubuntu Mem Test
Other Operating Systems
Vista Longhorn Loader
Vista Longhorn Loader

The reason why there are two Vista Loaders is because of that D partition recovery for Vista. Grub picks that up as a separate Vista installs. The First Vista Loader is the C Drive one.

 After everything goes OK 
Type this into the terminal

sudo aptitude install ubuntu-restricted-extras


After all that installs and is done
Type this now into the terminal if you want VLC

sudo aptitude install vlc

(Thanks to SidStudios for the above two scripts)



 About wireless with Ubuntu? I haven't configured that yet. Not important right now. Maybe someone can contribute on how to set up. Don't have much time right now to figure it out.


Bon Appetit!

---

### Post by RyanthePenguin on 2008-05-30
Can anyone help me get the wireless up and running on this one?  I really love Ubuntu, but not having wireless is a definite deal breaker.

---

### Post by jrusso2 on 2008-05-31
> **Midwest-Linux said:**
> Just a report of sorts as this might help others. Staples (here in the U.S.) has a Presario laptop on sale this week for $399. I picked it up with the intention of installing XP and Linux on it. Specs are 1.9 Ghz dual core AMD Athlon X2 with 1 GB Ram and Vista Premium. 

 The Ram use was like 70%, under no activity. Looking at some forums on how to speed this slug up. I got rid of the User account control, disabled superfetch, disabled Windows defender, turned off system restore, deleted Norton anti spyware, deleted Symantec, turned off aero, got rid of all the free games on it. Reduced startup programs to bare minimum. 

 Now I am at 51% ram usage, still way more than XP. 

But it gets better. I ran the Ubuntu 8.04 Live DVD, the ram usage hovered around 165 MB, the Live DVD found and installed the Athos wireless wifi and the required HAL....more about this later.

I ran the live KNOPPIX 5.3 DVD, within no time the Knoppix booted up, found all the drivers and worked flawlessly! I was able to access the internet, listen to streaming audio, install flash. And the Ram usage was averaging 150 to 155 MB of Ram. Guess whats going to be running on this computer soon?

 I decided that I will redo the entire installation later this month after I check all the forums for the XP drivers for this machine. Forget about going to Compaq for the XP drivers, but some forums listed where drivers for XP can be found. If anyone is interested I can post one link for starters.

 In the meantime, I'll just install Wubi 8.04 for a Ubuntu dual boot the easy way. Downloaded wubi and that started downloading Ubuntu 8.04 and installing 8.04 ended me up at initramfs. No installation, remember that the Ubuntu 8.04 LIVE DVD ran fine on this machine and why a install of the same distro would not work is beyond me. 

 Uninstall Wubi 8.04 and did some searching.

 Read some posts, some suggested using 7.04 instead, I tracked down the Wubi 7.04 installer. Installed that and then it slowly downloaded the alternate 7.04...I mean slowly... at times at 11 kbs. Stopped downloading, shut the machine off and turned it back on and restarted downloading this time a lot faster at 1.1 MB. Then it came for it to install, it went through all the processes of installing much like you would see if you are using the alternate installer.

 Little message says time to reboot. Then started through the start up and got as far as the xorg.org which messages included about "Screens not found". 

 At that time I quit and will try another approach or two before I do a complete wipe of the hard drive and do a dual boot with XP Pro and likely Knoppix or Linux Mint later this month.

 So why didn't I buy a EEePC instead? Simple, The EePC is a great concept, but for the same price, instead of a 4 BG or 8 GB drive, you can get one with 120 Gig hard drive, twice the ram and a CD and DVD burner. Maybe if the EePC was priced at $129 or $149 it would be worth it... in my opinion.

 I'll add more later to this as try other options, the reason for this post was to maybe help others who bought or are considering buying this laptop.

Another gig of ram is needed to really run Vista Home Premium.  It takes two gigs really.

---

