---
title: "Screen resolution problem with 8.04.1 and 8.10"
date: 2009-01-09
forum: System76 Support
---

### Post by David Haas on 2009-01-09
My desktop Ratel, purchased in Feb. 2006, has run all Ubuntu versions well. However, the installation of 8.04.1 LTS has a screen-resolution problem. The resolution defaults to 960x600 on my 17" Medion monitor, and the dialog offers no higher setting--so the version is unusable (lower settings are listed). With 6.06 LTS, which I had been running, the default was 1280--as it was on prior versions. I burned an iso of 8.10, but it gave the same problem. I also noticed that the screen resolution was too low (text and graphics too large) even as the CD was loading--"Ubuntu" was way too big. Other than this problem, installation was flawless. I see that both of these versions have xorg.conf files that don't list resolutions, as prior ones did. So, I don't see how they can be edited.

Can you diagnose the defect? Is it failure to recognize the graphics card? Your original sheet lists the card as "Integrated Graphics - SIS Real 2" and the command "lspci | grep VGA" returns "VGA compatible controller: Silicon Integrated Sytems (SIS) 661/741/760/761 PCI/AGP VGA Display Adapter".

By the way, my Serval laptop runs 8.04 LTS perfectly.   

Thanks for any help you can offer.

David

---

### Post by mikewhatever on 2009-01-10
You may want to reboot into recovery mode and select 'fix xserver' option. Sometimes it helps.

---

### Post by tgs1952 on 2009-01-10
I recently purchased a Koala from system76 running 8.10. I am extremely happy with everything but the screen resolutio. My 19" Samsung Monitor works best at 1280 x 1024 60hz.

Ubuntu is only giving me 1152 x 864 and everything is a bit too big. Text is also a bit fuzzy.

While the current setting is acceptable, I would really like to get the correct resolution.

In the past, I was running Fedora and was able to edit xorg.conf. Apparently that is not an option on this system.

---

### Post by blackdown on 2009-01-10
If you whant change your secreen resolution use "Screen and Graphics" ( System - Administration ).

---

### Post by David Haas on 2009-01-10
I rebooted into Recovery Mode and clicked on fix xserver. It ran the program, but this did not affect my screen resolution problem.

Under System > Administration there is no listing labelled "Screen and Graphics". You may be thinking of System > Preferences: Screen Resolution. I tried this latter, but in the Screen Resolution dialog, the highest setting listed is only 960x600. This is the problem I'm having with 8.04 and 8.10--but didn't have with 6.06 LTS, which I ran at 1260.

---

### Post by mikewhatever on 2009-01-10
What about the output of the command <xrandr -q> without brackets?

---

### Post by tgs1952 on 2009-01-10
I rans the xrandr -q and this is the output. 1280 x 1024 is the resolution I want 1152x864 is all it is giving me. What does this tell me?

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1600 x 1600
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0     60.0     60.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0* 
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
TMDS-1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

---

### Post by mikewhatever on 2009-01-10
Try running <xrandr -s 1280x1024>.

---

### Post by thomasaaron on 2009-01-12
If you guys want to shoot me emails, I'll help you get this sorted out. It's a little difficult working with multiple computer models in the same thread, particularly when I suspect the root cause of the problem isn't the same with your computers.

---

### Post by David Haas on 2009-01-14
Re: Screen resolution problem with 8.04.1 and 8.10
I'm the originator of this thread. tgs1952 jumped in with his problem, thinking it is the same, but it would have been better (less confusing) if he had begun his own thread. At any rate, welcome thomasaaron from System 76! My Ratel is the 1000 and my monitor is a Medion 17 inch LCD color. Its book-recommended resolution is 1024x768, but with Ubuntu 6.06 and prior versions, it defaulted to 1280x1024--which I prefer.

With 8.04.1 and also 8.10 (and also Debian etch), the xorg.conf file lists "configured monitor" in the monitor Identifier section, "configured video device" in the Device Identifier section and "Default Screen" in the Screen Identifier section. Of course, in 6.06 specific information was given in the xorg.conf. Monitor identifier listed "MD9404QB" with option "DPMS". Under Device > Identifier was listed "Generic video card", and as driver "vesa". I can give you the lot if you need it.

xrandr gives this:
haas@desktop:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 960 x 600
default connected 800x600+0+0 0mm x 0mm
   960x600        60.0  
   960x540        60.0  
   800x600        60.0*    56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   400x300        60.0  
   320x240        61.0

I read the Ubuntu wiki on troubleshooting wrong resolutions. Here it says to run xrandr, as suggested by a respondent. I ran it and it gave the same too-low and incorrect resolutions listed in the GUI for screen resolution. Then I ran sudo get-edid|parse-edid and this indicated an EDID fail, if I understood its lingo correctly. According to the wiki, this result means I'll need to manually configure my xorg.conf settings. Of course, my first attempt crashed xorg completely! The command's result is below:

&#65279;haas@desktop:/etc/apt$ sudo get-edid|parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11110 "SiS"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "MD9404QB"
	VendorName "MED"
	ModelName "MD9404QB"
	# Block type: 2:0 3:fd
	HorizSync 30-83
	VertRefresh 50-75
	# Max dot clock (video bandwidth) 140 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fe
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:no

	Mode 	"1280x1024"	# vfreq 60.020Hz, hfreq 63.981kHz
		DotClock	108.000000
		HTimings	1280 1328 1440 1688
		VTimings	1024 1025 1028 1066
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fe
EndSection


The video card in the Ratel is "Integrated Graphics -- SIS Real2" (from your sheet) and "VGA compatible controller: Silicon Integrated Systems (SIS) 661/741/760/761 PCI/AGP VGA Display Adapter" (from lspci|grep VGA).

What do you think--do I need to hand-configure xorg.conf, and if so, can you make recommendations about how to do this? What is the driver for this card? I'm surprised that "vesa" was listed in xorg.config as the driver in 6.06, and yet 6.06 ran perfectly.

Thanks,
David

---

### Post by thomasaaron on 2009-01-14
Hi, David.

I'm still waiting to hear if the fix I sent you via email worked. Are you all set now?

---

### Post by David Haas on 2009-01-14
I haven't received an email from you, but from your last message, I assume that you've received the one I sent to you. I even looked in my spam folder, but it wasn't there either. 

I'm looking forward eagerly for any possible fix you can suggest.

Thanks,

David Haas

---

### Post by thomasaaron on 2009-01-15
Shoot. I see you have yahoo email. We've had a ton of problems sending email to customers using yahoo. Here's what I sent. If we need to communicate further on this, and you have an alternate email address, that would be the way to go.
===============================

Try running these commands (I'd copy and paste them into your terminal to avoid typing/capitalization mistakes)...
NOTE: If any of these commands throw errors, just keep going...

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get --purge remove xserver-xorg-video-sis
sudo apt-get install xserver-xorg-video-sis
sudo apt-get --reinstall install xserver-xorg-video-sisusb
sudo dpkg-reconfigure xserver-xorg

Now reboot your computer and see if you can go to System > Prefs > Screen Resolution and select the correct resolution.

If not, go to System > Administration > Hardware Drivers and see if there are any sis drivers that need to be enabled (but I doubt there will be.

If that doesn't work, try specifying the sis driver in your xorg.conf. It would look something like this:

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "sis"                        
EndSection

If you have too much difficulty figuring out where to put it, send me the output of this command, and I'll figure it out...

cat /etc/X11/xorg.conf > ~/Desktop/xorg.txt

It will create a copy of your xorg.conf on your desktop that you can attach to this email and send to me.

---

### Post by thomasaaron on 2009-01-15
Change the driver section to "vesa" and see what happens.

---

