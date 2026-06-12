---
title: "Should I get an RMA# for my power supply[details inside]??"
date: 2007-03-01
forum: The Cafe
---

### Post by billdotson on 2007-03-01
I have had my Core 2 Duo PC running for about 6 months (not straight, turning it on and off normally) and on boot half of the time my PC would freeze at the BIOS screen and I would have to reboot one or sometimes several times to get past the BIOS screen.  I talked to Asus about it and we went through all of the troubleshooting steps, and the final answer was the one IO was dreading get an RMA# for your motherboard.  So I took everything apart and packed up my motherboard and have it in the box to send it away.  I have heard that freezing at te BIOS screen is sometimes an indication of a failing or faulty power supply.  

My question is if I have a failing/ faulty PSU wouldn't I have more issues than the PC freezing at the BIOS screen half the time?  I ask because while my PC is worthless without a motherboard should I just go ahead and send off for a replacement PSU.  I would like to add that the freezing at the BIOS screen is not only after having the computer off for a long time but often it has happened when I have had the machine running for 5 or so hours or even all night and then simply reboot to switch to Ubuntu or after I install and update or program in Windows.  So if I just rebooted and the machine had been on for a few hours wouldn't the motherboard still be retaining power in the capacitors??

Sounds like to me that it was my motherboard because I am almost certain that the motherboard would still have electricity in the capacitors.  Some of the times to get the computer to get past the BIOS screen I would turn the surge protector off and back on and it would work.

What are your thoughts?  MB and PSU bad, MB bad, or just the PSU and I wasted my time getting the MB out of the case?        Thanks.

---

### Post by SishGupta on 2007-03-01
IMHO it doesn't sound like a power supply problem. In my experience, BIOS lockups are usually hardware related (the mobo or some device attached the the mobo).

Sometimes my BIOS locks up during POST and it is ALWAYS because my iPod has frozen during the reboot and when the bios tries to poll the device it stalls.

Your PSU will generally always have power in the capacitors unless you turn it off on the PSU or if you unplug the power from the PSU. 
The off switch on the front of your PC is more like a soft-off. One of the reasons the power button on the front of your PC works when "off" is because there is still power running to the mobo.
Regardless, the capacitor thing wouldn't be an issue imo.

If I were you I would troubleshoot each part one at a time, so wait for the mobo to come back and see if you still have the problem before you RMA your PSU.

---

### Post by billdotson on 2007-03-01
the Asus rep told me to RMA the board.  I tested the RAM and it is compatible (actually I ran memtest86 6 times wth all passes and no errors) the CPU and motherboard were not overheating (they were actually pretty cool.. like 87 degrees Fahrenheit max and normally about 84F) the videocard seems to be working fine and my PSU fan speed was actually running at about 785RPM because my system was so cool (my antec PSU has a thermal management fan that adjusts itself according to the current temperature internally.. and my system was actually cool enough that my BIOS had the PSU fan speed in the red text because the fan wasn't going at least 800RPM so that  was actually an indication of how cool my system was)  

I also have a soundblaster audigy 4 soundcard ,a SATA and an IDE DVD burner, a floppy drive and a 5-in-1 media card reader.  I also have a Maxtor 300GB external USB 2.0 HDD that is plugged in.  I have been running my machine for about 6 months and didn't have issues until a month ago.  I have hd my external HDD plugged up the whole 6 months I have had it and didn't notice the freezing until just a month ago.
I loaded Ubuntu on my external HDD about 6 weeks ago but Ubuntu wouldn't bother the BIOS.  In fact I didn't notice the slow and/or freezing BIOS until I got it back about a month ago from the local university computer support center.  I took it to them and told them to reformat my internal HDD and put XP back on it.  I didn't notice any issues until I got it back from them.  Oh well, at least I am getting a replacement MB.

---

### Post by Boomy on 2007-03-01
> **billdotson said:**
>   Some of the times to get the computer to get past the BIOS screen I would turn the surge protector off and back on and it would work.

What are your thoughts?  MB and PSU bad, MB bad, or just the PSU and I wasted my time getting the MB out of the case?        Thanks.

Actually that sounds like it could be a bad PSU. I had a box with the same problem, and turning the main power switch on and off again would sometimes help to get it started. I t was like it needed a jumpstart. 

It kept getting worse until one day it just smoked, literally, and ruined everything on the machine. Both hard drives were shot. One of them rattled because something inside was physically broken. The Ram, when insterted in another machine, kept it from booting. I think what happened is the PSU allowed unregulated or unrectified voltage into the board. 

I'm not saying it is definitely your PSU, but at the very least, I would check the output with a DMM at startup and make sure your voltages are within spec. If you don't have a DMM, just get a new PSU, it's probably not much more $ than a meter.

---

### Post by billdotson on 2007-03-02
I think I will just RMA my PSU and get a replacement for it.  I am not going to have my motherboard back for about a 1.5 weeks so I might as well get a replacement PSU so they will both come in about the same time.  If the PSU wasn't bad then I just have a new one that will live a little bit longer..

---

