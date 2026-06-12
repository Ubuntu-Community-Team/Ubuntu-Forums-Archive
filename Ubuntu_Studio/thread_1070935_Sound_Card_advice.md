---
title: "Sound Card advice"
date: 2009-02-15
forum: Ubuntu Studio
---

### Post by namelessone on 2009-02-15
I need advice on purchasing a fairly inexpensive sound card that will work well in Linux for voice recording through Audacity.

I see lots of posts talking about great $100+ cards, but I need something a little bit cheaper...like in the $50 and below range.

---

### Post by Reeman on 2009-02-16
> **namelessone said:**
> I need advice on purchasing a fairly inexpensive sound card that will work well in Linux for voice recording through Audacity.

I see lots of posts talking about great $100+ cards, but I need something a little bit cheaper...like in the $50 and below range.
Try to find a used M-Audio 24/96 delta. The linux support for the ice1712 is great and the analogue input s/n rating is 100db. Failing that the [SB]("http://www.tigerdirect.ca/applications/category/category_slc.asp?CatId=2771") cheapo blaster is a good start there is an auxiliary input on the card and you can easily rig a cd connector with rca ends to it. All you have to do is get two rca input jack post and solder them to a cd connector like in the attached pictures. This gives you the ability to record audio without using up the back panel combined mic/digital/analogue in jack which has to do rediculous input sensing to work. One thing to do is to make sure that you have the mike pre-amp turned off as this is a source of problems with SB cards even the windows drivers are flakey. The chipset on the Audigy cheapo is the same as on the expensive card it is just that there is no breakout box. The CA0106 series is well supported under alsa and will easily handle 24/96 audio! 

You could find a used Audigy2 ZS for cheap and do the same thing there are two sets of inputs on the card itself just make sure the DSP chip on the Audigy2 is the ZS model or better with the CA0102 DSP and it will do 24/96 analogue to digital at 95db plus! This one is available on E-Bay just search for the listing 370160228328. 
 
I use the Audigy2 ZS card in combination with an M-Audio 24/96 and easily can do 4channel 24/96 recording with Ardour2 and jack audio. Remember if you have an onboard DSP you should turn it off in the bios otherwise there might be interrupt trouble or serious configuration trouble. Don't forget an onboard AC97 chip relies heavily on the proccessor and is one heck of a resource hog!

---

### Post by namelessone on 2009-02-17
Thank you, Reeman, for your excellent advice!

I have a few questions, though, since I am not an audio expert:
> 
One thing to do is to make sure that you have the mike pre-amp turned off as this is a source of problems with SB cards even the windows drivers are flakey
By pre-amp are you talking about an internal software setting, or are you talking about something on the mixer that the microphone will be plugged in to?
> 
All you have to do is get two rca input jack post and solder them to a cd connector like in the attached pictures.
What is the pinout for the cd connector to rca jack?
> Remember if you have an onboard DSP you should turn it off in the bios otherwise there might be interrupt trouble or serious configuration trouble. Don't forget an onboard AC97 chip relies heavily on the proccessor and is one heck of a resource hog!
I do have an onboard (broken) sound card. How do I disable it in the  BIOS?

---

### Post by Reeman on 2009-02-17
> **namelessone said:**
> Thank you, Reeman, for your excellent advice!

I have a few questions, though, since I am not an audio expert:

By pre-amp are you talking about an internal software setting, or are you talking about something on the mixer that the microphone will be plugged in to? 

What is the pinout for the cd connector to rca jack?

I do have an onboard (broken) sound card. How do I disable it in the  BIOS?

Your welcome!

The mic control will show up in alsamixer and can be disabled by either setting the level to 0 or if you are using the ca0106 chipset (audigy with only 4 1/8 inch jacks) the first jack is automatically muted unless you plug in a mike..then the sound card senses the devices and allows alsa to set a mike interface in mixer. The first jack will accept a mike or stereo 1/8", it will also accept a digital plug that creative sells as an accessory.

Other sound cards are notorious for having the mic pre-amp on in which case they will show up in alsamixer and can be controlled.

About the pin out connector...the four pin auxiliary or cd connector on most SB cards have the two center pins as ground and the two outer pins as left and right channel. The connectors have a single ground wire (black) and white and red for the l+r channels. Here is the tricky part some cables are wired with the white for right hand channel! So you have to check which to use for left and right. Convention is that right is red in the real world. But the computer manufacturing space cadets decided to screw with things so the general public would give up easily!  If you get it wrong it is still no problem...just the channels will be reversed.

About onboard dsp chips, they can be disabled in most bios interfaces. You get at the bios before booting into an OS. With most asus boards you just press the delete key during POST (power on self test). With companies like Lenovo, Dell or HP/Compact it is usually one of the function keys.


Best of luck...if you do find a good used M-Audio 24/96 you will be very pleased with the card. If you are doing serious recording it is well worth the expense. I have had mine for 5 years and find that it is the best consumer grade audio card ever made.

Here are some screen shots of terminal with alsamixer in action...

---

### Post by Reeman on 2009-02-18
Your onboard sound might not be broken if it has been muted for some reason or other....try the command **alsamixer -c 0** in a terminal to see it shows up as a device. Use the arrow keys to navigate and set values if you have the onboard card registered in alsa. Sometimes things just get muted by the desktop software soundserver with Ubuntu, it can be a real PITA but is part of the normal linux learning curve. If you do the command **lspci** then you might see if it is detected as a device at all by Ubuntu. If it is there it will show up as a Multimedia Audio Controller or just an Audio Device. Here is my pci layout

eric@ratpile:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:05.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
03:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
eric@ratpile:~$ 


Yours will be different but if there is a detected audio device it will show up.

---

