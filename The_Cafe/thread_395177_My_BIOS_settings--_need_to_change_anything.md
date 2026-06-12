---
title: "My BIOS settings-- need to change anything?"
date: 2007-03-27
forum: The Cafe
---

### Post by billdotson on 2007-03-27
Here you go Futz:

What I did:

Popped out CMOS battery, moved the jumper cap over to pins 2 and 3 for 10 seconds then moved them back to 1 and 2 (all this with the power cable unplugged)  I then moved some fan power hookups around so that I could use the fan controller in the case to control one of the fans.
Hooked PC back up and then pressed the on button.  It booted for about half a second and immediately shut back down.  Then I HELD the power button in and it booted and got frozen at the BIOS screen.  So I shut down manually and rebooted.  It went through a bunch of lines of text and then had this paragraph:

CMOS settings wrong
Overclocking failed!  Please enter setup to reconfigure your system
Press F1 to run setup
Press F2 to load default values and continue

Then I shut down and unplugged and reconnected the IDE LED, HDD LED, Power switch, etc. back to the MB pins.
Then I lightly pressed the power button and it booted the PC.  It didn’t shut down immediately like earlier.  Then shut down and then rebooted twice.  Didn’t shut down anymore.  Then I booted up hit Del and POST was running through lines of text and the at:

Auto -  detecting USB Mass Storage Devices
Device#01: (hangs here for 20-30 seconds)

Main:
System Time [00:03:57]
System Date [Tues 01/01/2002]
Legacy Diskette A [1.44M, 3.5 in.]
Language [English]
SATA1 [ST3250620AS]
SATA2 [Not detected]
SATA3 [Lite-on DVDRW SH-1]
SATA4 [Not detected]
SATA5 [Not detected]
SATA6 [Not detected]

SATA1
Device : Hard disk
Vendor : ST3250620AS
Size : 250GB
LBA mode : supported
Block mode : 16 sectors
PIO Mode: 4
Async DMA : Multiword DMA-2
Ultra DMA : Ultra DMA-5
SMART monitoring supported
Type : [Auto]
LBA/Large Mode [Auto]
Block (Multi-Sector Transfer) M [Auto]
PIO Mode: [Auto]
DMA Mode : [Auto]
SMART monitoring : [Auto]
32Bit Data Transfer [enabled] 

SATA 2
Device: Not detected 
Type [Auto]
LBA/Large Mode [Auto]
Block(Multi-Sector Transfer) M [Auto]
PIO Mode [Auto]
DMA Mode [Auto]
SMART monitoring [Auto]
32Bit Data Transfer [Auto]

SATA3
Device : ATAPI CD-ROM
Vendor : Lite-On DVDRW SH-16A75
LBA mode : supported
PIO Mode: 4
Async DMA : Multiword DMA-2
Ultra DMA : Ultra DMA-5
Type : [Auto]
LBA/Large Mode [Auto]
Block (Multi-Sector Transfer) M [Auto]
PIO Mode: [Auto]
DMA Mode : [Auto]

SATA 4
Device: Not detected 
Type [Auto]
LBA/Large Mode [Auto]
Block(Multi-Sector Transfer) M [Auto]
PIO Mode [Auto]
DMA Mode [Auto]
SMART monitoring [Auto]
32Bit Data Transfer [Auto]

SATA 5
Device: Not detected 
Type [Auto]
LBA/Large Mode [Auto]
Block(Multi-Sector Transfer) M [Auto]
PIO Mode [Auto]
DMA Mode [Auto]
SMART monitoring [Auto]
32Bit Data Transfer [Auto]

SATA 6
Device: Not detected 
Type [Auto]
LBA/Large Mode [Auto]
Block(Multi-Sector Transfer) M [Auto]
PIO Mode [Auto]
DMA Mode [Auto]
SMART monitoring [Auto]
32Bit Data Transfer [Auto]

Main > System Info:

AMIBIOS
Version: 0910
Processor
Type : Intel ® Core ™ 2CPU 6600 @ 2.40GHz
Speed: 2400MHz
Count: 2
System Memory
   Available: 2048MB

IDE configuration
SATA configuration [Enhanced]
Configure SATA as [IDE]
Hard disk Write Protect [Disabled]
IDE Detect Write Protect [Disabled]

Advanced Section> Jumperfree Configuaration
Configure System Frequency/Voltage
AI Tuning [Auto]
DRAM Frequency [Auto]

LAN Cable Status Section 
POST Check LAN cable [Disabled]
LAN Cable Status

Pair     Status     Length
1-2       N/A
3-6       N/A
 4-5       N/A
 7-8       N/A
 1-2       N/A
 3-6       N/A
 4-5       N/A
 7-8      N/A

If I go to the AI Tuning manual option:
AI Tuning Manual
CPU Frequency [266] (Valid input Values: 100-650)
DRAM Frequency [Auto]
PCI Express Frequency [Auto]
PCI Clock Synchronization Mode [Auto]
Spread Spectrum [Auto]
Memory Voltage [Auto]
CPU VCore Voltage [Auto]
FSB Termination Voltage [Auto]
NB VCore [Auto]
SB VCore (SATA, PCIE) [Auto]
ICH Chipset Voltage [Auto]

USB Configuration
Module Version – 2.24.0 -11.4
   USB Devices enabled:
1 keyboard, I mouse, 5 drives
USB Functions [Enabled]
   USB WIFI/USB 9,10 [Enabled]
Legacy USB Support [Auto]
Port 64/60 Emulation [disabled]
USB 2.0 controller mode [HiSpeed]
BIOS EHCU Hand-ff [Enabled]

   USB Mass Storage Device Configuration
   USB Mass Storage Reset Delay [20 sec]
   Device #1 Maxtor 3200
   Emulation type [Auto]

CPU configuration
Configure Advanced CPU settings
Module Version 3C.0E
Manufacturer: Intel
Brand String: Intel ® Core ™ 2 CPU 6600 @ 2.40GHz
Frequency: 2.40GHz
FSB Speed: 1066MHz
Cache L1: 32KB
Cache L2: 4096KB
Ratio Status : Unlocked (Max: 09, Min: 06)
Ratio Actual Value: 9
CPUID: 6F6
Modify Ratio Support [Disabled]
C1E Support [Enabled]
Max CPUID Value Limit [Disabled]
Vanderpool Technology [Enabled]
CPU TM Function [Enabled]
Execute Disable Bit [Enabled]
PECI [Disabled]

Boot Settings Configuration
Quick Boot[Enabled]
Full Screen Logo [Enabled]
AddOn ROM Display Mode [Force BIOS]
Bootup Num-Lock [On]
PS/2 Mouse Support [Auto]
Wait for ‘F1’ If error [Enabled]
Hit ‘DEL’ Message display [Enabled]
Interrupt 19 Capture [Disabled]

Boot Device Priority
1st Boot Device [1st Floppy Drive]
2nd Boot Device [HDD:PM-ST3250620AS]
3rd Boot Device [CDROM: PS-LITE-ON D]
4th Boot Device [IDE: HL-DT-ST DVD-RA]

Power
Suspend Mode [S1(POS)only]
ACPI 2.0 Support [Disabled]
ACPI APIC Support [Enabled]

APM Configuration
Restore on AC Power Loss [Power Off]
Power on by RTC Alarm [Disabled]
Power on by external modems [Disabled]
Power on by PCI Devices [Disabled]
Power on by PCIE devices [Disabled]
Power on by PS/2 Keyboard [Disabled]
Power on by PS/2 Mouse [Disabled]

Advanced PCI/PnP Settings
Plug and Play O/S [No]
PCI Latency Tuner [64]
Allocate IRQ to PCI VGA [Yes]
Palette Snooping [Disabled]
IRQ 3 assigned to [PCI Device]
IRQ 4 assigned to [PCI Device]
IRQ 5 assigned to [PCI Device]
IRQ 7 assigned to [PCI Device]
IRQ 9 assigned to [PCI Device]
IRQ 10 assigned to [PCI Device]
IRQ 11 assigned to [PCI Device]
IRQ 14 assigned to [PCI Device]
IRQ 15 assigned to [PCI Device]

North Bridge Chipset Configuration
Memory Remap Feature [Disabled]
Configure DRAM timing by SPD [Enabled]
Static Read Control [Auto]
Initiate Graphic Adapter [PEG/PGI]
   PEG Port Configuration
      PEG Force x1 [Disabled]
      PEG link mode [Auto]  ( I think it says ‘link’ but my handwriting is kind of bad right there on my notes) 
ASUS C.G.I. [Auto]

South Bridge Chipset Configuration
PCIEX16_2/PCIEX1_1 Force [Auto]

Configure Win627EHF SuperIO Chipset
HD Audio Controller [Enabled]
   Front Panel Support Type [HD Audio]
Onboard 1394 Controller [Enabled]
Onboard PCIE GbE LAN_1 [Enabled]
   LAN option ROM [Disabled]
Onboard PCI LAN_2 [Enabled]
   LAN option ROM [Disabled]
JMicron SATA/PATA Controller [Enabled]
   JMicron Controller Mode [IDE]
Serial Port Address [3F8/IRQ4]	







Hardware Monitor
CPU temperature [34.5 C/94 F]
MB temperature [29 C/84 F]
CPU Fan Speed (RPM) [2057RPM]
CPU Q-Fan Control [Disabled]
Chassis Fan 1 [N/A] 
Chassis Fan 2 [N/A] 
Chassis Fan 3 [N/A] 
CPU Q-Fan Control [Disabled]
Power Fan Speed (RPM) [827RPM]
VCore Voltage [1.288V]
3.3V Voltage [3.248V]
5V Voltage [4.966V]
12V Voltage [12.038V]


Also, if anyone else wants to help my PC froze at the BIOS screen today and about a week ago and I am trying to narrow down the issue and fix it.  Futz said it could be a setting in the BIOS that is incorrect.

Thanks.

---

### Post by simonn on 2007-03-27
Is there a load failsafe defaults or similar option in the BIOS?

---

### Post by billdotson on 2007-03-27
yes there is a load defaults.. those are the defaults after I cleared the CMOS (by removing the CMOS battery and moving the jumper cap on the MB) then going into the BIOS and doing load defaults.

---

### Post by futz on 2007-03-28
> **billdotson said:**
> Popped out CMOS battery, moved the jumper cap over to pins 2 and 3 for 10 seconds then moved them back to 1 and 2 (all this with the power cable unplugged)
Pulling the battery is totally unnecessary. Waste of time. Just switch PSU to 0 (off), wait 20 seconds or so for all caps to discharge, move the jumper over for a second or two and then back, turn PSU back on, boot up.

> Hooked PC back up and then pressed the on button.  It booted for about half a second and immediately shut back down.
Normal. Just wait a few secs and it'll restart.

>  Then I HELD the power button in and it booted and got frozen at the BIOS screen.
Don't HOLD the power button in. Why would you do that?

>  So I shut down manually and rebooted.  It went through a bunch of lines of text and then had this paragraph:

CMOS settings wrong
Overclocking failed!  Please enter setup to reconfigure your system
Press F1 to run setup
Press F2 to load default values and continue
Normal after clearing CMOS.

> Then I shut down and unplugged and reconnected the IDE LED, HDD LED, Power switch, etc. back to the MB pins.
Why were they disconnected?

> Auto -  detecting USB Mass Storage Devices
Device#01: (hangs here for 20-30 seconds)
Sounds like your USB drive isn't picking up the phone. Is it powered up (spinning) when that happens? There's one setting I'll get you to change further down that may (or may not) help this work better.

> Advanced Section> Jumperfree Configuaration
Configure System Frequency/Voltage
AI Tuning [Auto]
DRAM Frequency [Auto]
Change 'AI Tuning' to Manual

> AI Tuning Manual
CPU Frequency [266] (Valid input Values: 100-650)
DRAM Frequency [Auto]
Change 'DRAM Frequency to DDR2-800MHz

> Memory Voltage [Auto]
Change this to 2.1V. NO HIGHER, or your RAM warranty is voided. You can go higher as part of an overclock, but your warranty is out the window if you smoke it at high voltage.

> USB Configuration
Module Version &#8211; 2.24.0 -11.4
   USB Devices enabled:
1 keyboard, I mouse, 5 drives
USB Functions [Enabled]
   USB WIFI/USB 9,10 [Enabled]
Legacy USB Support [Auto]
Change 'Legacy USB Support' to Enabled - might help with that USB drive.

> USB Mass Storage Device Configuration
   USB Mass Storage Reset Delay [20 sec]
If your USB drive is powered up when it causes bootup problems, then you might have to increase that delay a bit. Can't hurt to test different settings, anyway.

> Boot Settings Configuration
Quick Boot[Enabled]
Full Screen Logo [Enabled]
Disable full screen logo (stupid, ugly thing) so you can see what's going on.

> North Bridge Chipset Configuration
Memory Remap Feature [Disabled]
Configure DRAM timing by SPD [Enabled]
Disable 'DRAM timing by SPD' and set these:
CAS Latency - 4
RAS to CAS - 4
RAS Precharge - 4
RAS Activate to Precha - 12

> Configure Win627EHF SuperIO Chipset
HD Audio Controller [Enabled]
You have a sound card, don't you? Shouldn't this be disabled?

> Onboard 1394 Controller [Enabled]
If you don't use it, disable it. Won't hurt if you don't, but it's one more thing eating resources for nothing.

---

### Post by kvonb on 2007-03-28
If it froze at the BIOS, I would be looking at the hard disk, and also on the mainboard for "popped" capacitors.

---

### Post by PatrickBG on 2007-04-04
Im Having Bad lock ups.  I think I can prevent these from a Bios settings change.  Could any1 give me any advice with my problem plz. 


Motherboard
NFORCE 570 Slit-A v5.1
Socket 775 (Intel)

CPU: P4 (Intel) 3.2GHz
Memory: 1GB Buffalo Select DDR2
OS: XP Professional 

I just built this computer 3 months ago and it was working fine until my power supply gave out. I replaced my power supply and started having problems with my computer while gaming. I ran a Bios Update and the Flash program messed up and my computer wouldn’t reboot after update was complete. I’m guessing this corrupted my bios:( . I’ve replaced my motherboard. After I replaced my motherboard I reinstalled Windows and all the drivers for my motherboard and graphics card. And now…
My computer locks up, completely freezes after about 5-10 seconds after I start it up. Does any1 know if this is a Driver or Hardware issue? If so, is there any test or specific hardware I can replace. 
Tech support suggested this could be a memory setting on my bios, but im afraid to mess w/ my bios without knowing exactly what settings to change.

---

### Post by kvonb on 2007-04-04
> **PatrickBG said:**
> Im Having Bad lock ups.  I think I can prevent these from a Bios settings change.  Could any1 give me any advice with my problem plz. 


Motherboard
NFORCE 570 Slit-A v5.1
Socket 775 (Intel)

CPU: P4 (Intel) 3.2GHz
Memory: 1GB Buffalo Select DDR2
OS: XP Professional 

I just built this computer 3 months ago and it was working fine until my power supply gave out. I replaced my power supply and started having problems with my computer while gaming. I ran a Bios Update and the Flash program messed up and my computer wouldn’t reboot after update was complete. I’m guessing this corrupted my bios:( . I’ve replaced my motherboard. After I replaced my motherboard I reinstalled Windows and all the drivers for my motherboard and graphics card. And now…
My computer locks up, completely freezes after about 5-10 seconds after I start it up. Does any1 know if this is a Driver or Hardware issue? If so, is there any test or specific hardware I can replace. 
Tech support suggested this could be a memory setting on my bios, but im afraid to mess w/ my bios without knowing exactly what settings to change.

How many RAM chips do you have?  If you have 2, remove 1 and try again.

You can hard reset the BIOS using a "jumper" on the mainboard, have a look in the manual for the correct procedure, usually it involves moving the jumper for 30 seconds.

I would also suggest finding out what speed your memory is, and if it is compatible with the new mainboard.

Newer boards might need faster RAM, and your "old" RAM might not be fast enough!

Also, when you put the CPU into the new mainboard, did you use enough heat sink compound?  You MUST have that stuff between the CPU and the fan.

If not, then the computer will either lock up (as you are experiencing), or shut itself down for a minute or so, so that the CPU is not permanently damaged.

Incidentally, what CPU do you have, again make sure that the new mainboard supports that CPU.

Regards, Kev :)

---

### Post by PatrickBG on 2007-04-04
> **kvonb said:**
> How many RAM chips do you have?  If you have 2, remove 1 and try again.

You can hard reset the BIOS using a "jumper" on the mainboard, have a look in the manual for the correct procedure, usually it involves moving the jumper for 30 seconds.

I would also suggest finding out what speed your memory is, and if it is compatible with the new mainboard.

Newer boards might need faster RAM, and your "old" RAM might not be fast enough!

Also, when you put the CPU into the new mainboard, did you use enough heat sink compound?  You MUST have that stuff between the CPU and the fan.

If not, then the computer will either lock up (as you are experiencing), or shut itself down for a minute or so, so that the CPU is not permanently damaged.

Incidentally, what CPU do you have, again make sure that the new mainboard supports that CPU.

Regards, Kev :)

Ty for ur post.

I Have One Ram Chip inserted into one of the four RAM slots: 1 GB 667 MHz CL5 2Rx8 DDR2 DIMM, 240 Pin (Buffalo Select)

   I replaced the motherboard with the same exact model motherboard NFORCE 570 Slit-A v5.1.  I’m using the same RAM I used when my power supply failed on me.  

I've used sufficient Heat sink compound and my cpu is running at about 29-35*C. It’s set to automatically turn off once it reaches 60*C +

Right now I have my Bios set to Default settings.

Is it possible that I am over clocking something and causing the lock ups?  If so, can I change my memory settings in my Bios?

My lock ups are at random :( , sometimes my computer runs for 30 mins, sometimes for only a few seconds then it locks up.

---

### Post by kvonb on 2007-04-04
OK, and the board definitely supports DDR2?

Try removing any addon cards and external USB devices, does it have a built on video card?  If so remove your flashy one and just use the bare machine for testing.  ALso disconnect ALL drives.

The CPU seems to run almost cold from what you've told me, so heat isn't a problem (mine runs around the 50 to 70c mark, it's a P4 3.2 prescott and that is OK).

Have a look in the BIOS, check the CPU clock speed, have a look at the voltages, there will be a hardware monitor page (sorry I don't know the exact wordage), make sure they are within tolerances.

The easiest thing is to "load failsafe defaults" and tweak up from there if that works.

How big is your power supply?  I had to buy a top quality 550 watt to even get my mainboard to fire up, if you are using a 3xx watt, that might be the problem.

There will be settings in the BIOS to change the RAM speed, as there are several different BIOS versions, again I don't know the exact wordage, but disable "spread spectrum", change the "Auto detect DIMM clock" from "auto" to one of the other options.

---

### Post by PatrickBG on 2007-04-04
This Motherboard Doesnt have a built in video card :( , but I have removed all that you have said otherwise.

I also have antec 550 watt power supply.

Im in the process of reconfiguring Bios as you have instructed, hopefully it will work,  Tyvm for your help

This is my Exact Motherboard
[http://www.tigerdirect.com/applications/SearchTools/item-Details.asp?EdpNo=2473506&sku=S458-1240](http://www.tigerdirect.com/applications/SearchTools/item-Details.asp?EdpNo=2473506&sku=S458-1240)

---

### Post by ~LoKe on 2007-04-04
Rather than pull the battery, just turn off the computer, grab a paperclip and make it touch both jumpers, remove it, then turn it back on.

---

### Post by simonn on 2007-04-04
> 
I just built this computer 3 months ago and it was working fine until my power supply gave out.


This is really important info. Why did you leave it out to begin with? 

I have seen power supplies, particularily cheap ones, take out other gear when they die. it has happened to me a few times.

It sounds like your memory is farked. Run memtest - there should be an option in the grub menu when you boot.

Seriously though, if I can offer advice from around a decade working in software support, do not make assumptions when you report a problem unless you have evidence just give the history of a problem and leave the diagnosis to the readers. If you give unfounded assumptions, the problem generally takes longer to solve.

---

### Post by kvonb on 2007-04-04
Thanks for the mb link, that makes it a little easier :).

It had dual channel DDR support, seeing as you only have one chip, make sure that you disable dual channel in the BIOS, that could be causing the problem.

It might default to dual, so if you can get into the BIOS and disable it and save before it crashes you should be ok.

Otherwise you might have to borrow another RAM chip just to get it setup correctly.  That would help to see if it IS a memory problem too.

Regards, KEv :)

---

### Post by BuffaloX on 2007-04-04
The advice given by FUTZ are very good, I can only recommend to follow them.
Except 2.1 RAM volt seems a bit high.
You might want to check how much your ram requires, and configure accordingly.
Adding 0.1 to 0.2 volt may improve stability for some systems.
Higher settings only make sense for overclocking, and you shouldn't overclock until you have 100% stability.

---

### Post by futz on 2007-04-04
> **BuffaloX said:**
> The advice given by FUTZ are very good, I can only recommend to follow them.
Except 2.1 RAM volt seems a bit high.
Ordinarily, yes, DDR2 should be running at 1.8V. But his Corsair RAM is rated to run at 2.1V. Warranty is good up to 2.3V on that RAM.

---

### Post by futz on 2007-04-04
> **kvonb said:**
> It had dual channel DDR support, seeing as you only have one chip, make sure that you disable dual channel in the BIOS, that could be causing the problem.
There is no setting in BIOS to enable/disable dual-channel RAM. It gets auto-sensed on every mainboard I've ever seen (and I've seen a lot of them :mrgreen: ). If there's a stick in each channel it runs dual-channel (interleaved). If there's only one stick, or they're in the wrong slots it runs without dual-channel. There's an onscreen message after POST to inform you whether it's running in dual-channel/interleaved mode. If you don't see it, you either have only one stick or you have the second stick in the wrong slot. Consult your manual for specifics on your particular mainboard.

---

### Post by futz on 2007-04-04
> **~LoKe said:**
> Rather than pull the battery, just turn off the computer, grab a paperclip and make it touch both jumpers, remove it, then turn it back on.
Many mainboards store the cmos clear jumper on the 2/3 pins (where you'd use the 1/2 pins to clear cmos). The 3 pin is (I'm pretty certain) not connected to anything. So your advice might be confusing to newbs, as they'd first have to remove the jumper before a paper clip would work.

Then there's the danger factor of poking around powered parts with a bare piece of metal. It would be pretty easy to accidentally touch the wrong thing and burn something. A jumper is much safer.

I build a handy device for machines I overclock. It's a momentary spst switch on a PCI slot blank, wired to a molex connector plugged into the clear cmos pins. Saves tons of time and grief poking around in there to reach those pins buried in wires and behind a video card. But if you don't clear your cmos often that's not worth the bother.

---

### Post by PatrickBG on 2007-04-04
I Loaded optimized settings for my bios and reinstalled windows.  I believe it has fixed the problem.  Im in the process of installing my drivers atm and no lock ups so far :)   Ty for ur help!

---

### Post by ~LoKe on 2007-04-04
> **futz said:**
> Many mainboards store the cmos clear jumper on the 2/3 pins (where you'd use the 1/2 pins to clear cmos). The 3 pin is (I'm pretty certain) not connected to anything. So your advice might be confusing to newbs, as they'd first have to remove the jumper before a paper clip would work.

Then there's the danger factor of poking around powered parts with a bare piece of metal. It would be pretty easy to accidentally touch the wrong thing and burn something. A jumper is much safer.

My motherboard (Gigabyte 965P-S3) only has two pins and no jumper. ;)

---

### Post by futz on 2007-04-04
> **~LoKe said:**
> My motherboard (Gigabyte 965P-S3) only has two pins and no jumper. ;)
Yup, some boards are like that, and some have the three pin setup.

---

### Post by BuffaloX on 2007-04-05
> **futz said:**
> 
I build a handy device for machines I overclock. It's a momentary spst switch on a PCI slot blank, wired to a molex connector plugged into the clear cmos pins. Saves tons of time and grief poking around in there to reach those pins buried in wires and behind a video card. But if you don't clear your cmos often that's not worth the bother.

You give some REAL COOL answers in this thread.:popcorn: 

But your gadget sounds a bit complicated.
Why use spst? ( simple on/off )?
Why not just use a switch that connect 1-2 default, 2-3 when pressed, back to 1-2 when released. That would seem to be much simpler.

Does yours somehow have a failsafe against clearing with power on?
That's the one reason I never made one myself, because that can destroy the cmos,
at least according to my mobo manuals, but I'm not totally convinced that it's actually true.

---

### Post by futz on 2007-04-05
> **BuffaloX said:**
> But your gadget sounds a bit complicated.
Why use spst? ( simple on/off )?
Why not just use a switch that connect 1-2 default, 2-3 when pressed, back to 1-2 when released. That would seem to be much simpler.
That's SPDT. That would be more complex. Three wires instead of two. :) Also, I'm pretty certain that the third pin is not connected, and is only used as a storage place for the jumper. The 3-pin mainboard with my switch in it works fine with nothing on the third pin (that proves my theory).

> Does yours somehow have a failsafe against clearing with power on?
That's the one reason I never made one myself, because that can destroy the cmos,
at least according to my mobo manuals, but I'm not totally convinced that it's actually true.
I have no failsafe. I just know it's there and don't touch it while the machine is running. I really doubt if hitting it while powered up would destroy anything, but your computer would probably crash.

What I really should have in there is a missile switch, like this:
[http://www.maplin.co.uk/module.aspx?ModuleNo=37319&ma=Eltham%20-%20Missile%20Style%20Toggle%20Switch%20Cover]("http://www.maplin.co.uk/module.aspx?ModuleNo=37319&ma=Eltham%20-%20Missile%20Style%20Toggle%20Switch%20Cover")
Prevents inadvertent bumps, and makes you think about what you're doing one more time before you flick that switch.

---

### Post by BuffaloX on 2007-04-05
> **futz said:**
> I'm pretty certain that the third pin is not connected, and is only used as a storage place for the jumper. The 3-pin mainboard with my switch in it works fine with nothing on the third pin (that proves my theory).

I have no failsafe. I just know it's there and don't touch it while the machine is running. I really doubt if hitting it while powered up would destroy anything, but your computer would probably crash.

What I really should have in there is a missile switch, like this:
[http://www.maplin.co.uk/module.aspx?ModuleNo=37319&ma=Eltham%20-%20Missile%20Style%20Toggle%20Switch%20Cover]("http://www.maplin.co.uk/module.aspx?ModuleNo=37319&ma=Eltham%20-%20Missile%20Style%20Toggle%20Switch%20Cover")
Prevents inadvertent bumps, and makes you think about what you're doing one more time before you flick that switch.

I always thought the 3 pin layout was for the battery, so the battery got  disconnected when clearing the cmos. If it's just a parking position, simple on/off is of course adequate.
This also made it clear to me, what you have actually done, didn't quite get it before. :redface: 

The missile switch would be a nice failsafe, and add a bit of coolness. 8-) 
I think I'll go for that, if I can find something suitable for the front of my case.
Another option would be to make a combo switch, that turned the PSU off, when clearing CMOS.
That way it's fool proof, which means I may be able to safely use it myself. :-k 
Only problem is a lot of extra wiring.

---

### Post by futz on 2007-04-05
> **BuffaloX said:**
> Another option would be to make a combo switch, that turned the PSU off, when clearing CMOS
Trouble with that idea is that you have to hack open the PSU and run high voltage (115V here in North America, and 220V in Yurop) down to the the switch, making any possibly sloppy home-built wiring MUCH MUCH more dangerous. Don't mess up, or you could fry your entire computer, or yourself. :mrgreen:

Alternately, you could add a small relay (solid state unit would be nice) located right on or even  inside the PSU (to keep the high voltage lines short and safe), powered by the mainboard and that way have only low voltage lines down where you're going to be working. Here again, any sloppiness could end with you having mains voltage feeding into the mainboard - guaranteed instant destruction, smoke, fire, mayhem, bad, bad, bad!!!

---

### Post by BuffaloX on 2007-04-06
> **futz said:**
> 
Alternately, you could add a small relay (solid state unit would be nice) located right on or even  inside the PSU (to keep the high voltage lines short and safe), powered by the mainboard and that way have only low voltage lines down where you're going to be working. Here again, any sloppiness could end with you having mains voltage feeding into the mainboard - guaranteed instant destruction, smoke, fire, mayhem, bad, bad, bad!!!

Its too messy, and it wouldn't even work, now that I thought a bit more about it.
Because both PSU and MOBO keeps the power a little while.
And that delay in power off makes the hole idea futile.

---

### Post by futz on 2007-04-06
> **BuffaloX said:**
> Its too messy, and it wouldn't even work, now that I thought a bit more about it.
Because both PSU and MOBO keeps the power a little while.
And that delay in power off makes the hole idea futile.
Yup. I started to type a paragraph about exactly that, but decided to just drop it. You'd have to wait like 10 to 20 seconds or so for the caps to discharge before your cmos would actually clear. It's easy enough to reach around and hit the PSU switch.

---

