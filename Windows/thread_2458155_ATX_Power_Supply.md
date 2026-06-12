---
title: "ATX Power Supply"
date: 2021-02-17
forum: Windows
---

### Post by max8425752574 on 2021-02-17
Hi,
I try to reactivate my 10 year old PC which I had to deactivate about 8 years ago. The reason was that I had problems to start the PC. I had to disconnect the ATX power supply from the power grid and then hope.

Now still the same problem.
I had to learn that my PS2 keyboard caused a crash and now with an USB keyboard I could install Windows to a certain point. After the second try (with a frozen screen) I removed the USB sticks and could install Windows XP.
I also could install the drivers.
But now it looks to me that the system freezes much faster and I can't do almost nothing.
(The screen freezes and keyboard and mouse doesn't react. The reset button has no function but the on off button at the front react sometimes. But I think it's better to use the power switch at the back).

Ok, it looks like a power supply problem ...
... But I've installed Ubuntu too and it worked now for more than 2 hours and I had only one freezing screen.

"Ubuntu knows the magic words" &#128521;
Honestly ... Does a new power supply makes the system stable?

---

### Post by CelticWarrior on 2021-02-17
For such old system is anyone's guess.
Testing Ubuntu for several hours/days is a good troubleshooting step to rule out (or in) hardware issues.
Now, irrespective of the age and overall hardware status what you MUSTN'T do is use such an obsolete and unsafe OS like Windows XP that under no circumstance should be online. Please act responsibly for your and everybody else's sake.

---

### Post by guiverc on 2021-02-17
PSU or power supplies have a rating of how much power they can provide when they leave the factory.  As they age, the maximum amount of power they can provide will reduce, and a PSU maybe reliable with certain hardware connected.

I wanted to use keep using a second hard drive on a dell optiplex 780 (a 2008 or 2009 computer) which is something the box is supposed to deal with, having cable & position, even second drive (it was an option when the box is ordered).  The box was unreliable with the second drive, esp. on warm days (or if heater came on in cooler weather given it's location relative to a heating vent).

The old PSU didn't have enough power for the two drives, plus *cooling *fans (*motors draw a fair amount of power*) needed when the box warmed up. I could keep it running slightly longer by being careful with what I did (*keeping its temperature cool so cooling fans didn't start*), but I quickly gave up on the idea of the second drive.

With a single drive, the box is perfectly reliable (*second drive is still in box, but its power cable is disconnected*), but the PSU just can't provide enough power any more to function with it.

How you use an OS can influence the amount of power being used, as can the OS itself, but if the box is unreliable as you say, I'd confirm the PSU is good (test box with another PSU, even if not the correct size/shape, you can still test with it), perform a *cap-check* of the motherboard & circuit boards..  Old PS2 keyboard can draw more power than a USB one, however the difference is very small, meaning if it creates problems the box is so near threshold it likely won't deal with heat well at all (and fans coming on to try and cool it); that or you have faulty hardware (replace components and assess).

I kept my d780 perfectly reliable just by removing it's second drive (less power being drawn from PSU), as I didn't have another (better) PSU that fitted the case available, and didn't feel it was worth buying one. 

 From your description I'd add up what hardware you have and roughly the power each item will draw from the PSU and see if you're trying to draw more than the PSU would be expected to provide (*given its age*).  Many books (*I have at least two hardware books that provide it*) give rough guides/figures for various devices (fans, drives, cpus of each generation, ps2 devices, usb devices (usb 1, usb 1.1-2, usb 3 etc) allowing calculation of expected draw, which can be compared with the *initial.rating of the PSU - (age x %estimated.loss)*** to know if power problems are to be expected (*guide anyway based on averages*).  I may rarely calculate it out as suggested in the book (*theory*), but the knowledge in the material gives a pretty good understanding so you can guesstimate without needing *pencil & back-of-envelope*. 

** at least one of the books suggests a sliding scale for calculated expected maximum power output due to age, but using that complicates the math considerably so I just remember the easy *less accurate* way

---

### Post by max8425752574 on 2021-02-18
Thx for answering :)

The system has a 400 watt power supply with only onboard graphics. The problem exists without any drives. I tried now another power supply without any changes.

I've mentioned the PS2 keyboard because I could start Ubuntu with it and that was the reason to give the system a chance! ;)
(maybe only for getting the experience what will happen) But after that I wasn't able to start the BIOS setup. Without that keyboard the system told me about the non existing drives. That's why I now use a USB keyboard.

Ok I believe it's an aged capacitor but cannot decide if it's Mainboard or the power supply.
It's also strange that Ubuntu works more stable than Windows. I've played some minutes with the online shooter that came with Ubuntu :) And if it's an capacitor why has Windows more problems?

Anyway I need Windows for old games. I believe it's online the safest what you can get. The internet explorer isn't working and opera has limited access. Videos aren't working.

Thx for reading ;)

---

### Post by CelticWarrior on 2021-02-18
> [COLOR=#000000]Anyway I need Windows for old games. I believe it's online the safest what you can get.[/COLOR]
Simply put, this is an asinine remark that shows a tremendous disconnect with reality. 
Please read the words of a true expert regarding a case such as yours: [https://ubuntuforums.org/showthread.php?t=2457851](https://ubuntuforums.org/showthread.php?t=2457851)
The first part is what matters and is entirely applicable to your case, the rest is about the specific question in that thread.
Hopefully after reading you may understand "[COLOR=#000000]why has Windows more problems"... Probably not, the same was thoroughly explained [here]("https://ubuntuforums.org/showthread.php?t=2457607"), but one can hope.[/COLOR]

---

### Post by max8425752574 on 2021-02-18
@CelticWarrior I haven't that experience and it's not my problem. I have that old games and the patches for them. All I need is a stable system and not emulator Software like virtual PC

And then &#65533;&#65533; with all the power failure the Linux system has some file system errors. If I boot now Linux try to repair but the system freezes ...

... Now I'll wait till I build my next PC and try the new power supply with that system :(

> **max8425752574 said:**
> Hopefully after reading you may understand "why has Windows more problems"... Probably not, the same was thoroughly explained*here, but one can hope.

That's my other PC with a broken USB 3 ports

---

### Post by CelticWarrior on 2021-02-18
> **max8425752574 said:**
> That's my other PC with a broken USB 3 ports

I know, I've read it all. And that matters because...?

The matter to which you replied was a critique of your constant asinine remarks regarding the use of obsolete and unsupported OS, namely dead and buried Windows versions, online. It's about computer literacy and personal and social responsibility. It should added that discussions about or help with, directly or indirectly, illegal ("pirated"), unlicensed or no longer licensed software (this includes all Windows versions prior to Windows 8) aren't allowed in this forum, so there's that. And, by extension, a warning about the abuse of this forum.

---

### Post by QIII on 2021-02-18
And, with that, closed.

---

