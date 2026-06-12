---
title: "Anyone else with a Core 2 Duo that can't run Ubuntu?"
date: 2007-01-03
forum: The Cafe
---

### Post by Rackerz on 2007-01-03
I was wondering if there was any Core 2 Duo users that aren't able to run Ubuntu because of the jmicron problems and if they found a way around it. I can't even run the livecd without it freezing, I can't even see how Ubuntu+Beryl will run on my new machine. 

It was supposed to be fixed in Edgy, but it's not. So is there anyone else who has been 'locked out' per say?

---

### Post by mips on 2007-01-03
Your title is misleading. Instead of mentioning Core 2 Duo you should mention Jmicron as that is where the problem lies.

---

### Post by pmj on 2007-01-04
I can boot the livecd and install Ubuntu, though the installer often freezes before it's complete. I can't boot the newly installed system, however. To get around this, I use a controller card. This is a pretty huge problem, and it would be sad if it will be in Feisty as well. It still isn't truly fixed, is it?

And mentioning Core 2 Duo isn't all that misleading, as many of the Core 2 Duo motherboards has the jmicron controller. Non-geek users aren't going to understand, or care, that the problem lies with the support for a PATA/SATA controller; what they see is that Ubuntu won't work on their new Core 2 Duo computer.

---

### Post by haxer on 2007-01-04
what is this jmicron? Is it on all motherboards? How to see if my new computer has it havent picked it up yet but in a few hours so:P

---

### Post by kevinf311 on 2007-01-04
Hmmm, interesting. Last night I was going to show my friend what Ubuntu Linux was. I brought him down to my parents new Dual Core computer and threw in the Live CD.

I was expecting a speedy impressive load up and demonstration. Instead it kept throwing random errors (perhaps jmicron, I was too busy trying to save face :rolleyes: ). Eventually it just froze and I turned off the computer to reboot and show him screenshots/Beryl youtube videos instead.

I was kinda peeved because I had had an unsuccessful attempt at loading it up on our old Win98 box (500MHz, 128MB Ram, 16MB vid card) last week. It's the same disk I installed my OS from in Atlanta.

*sigh* Maryland hates me :(

---

### Post by haxer on 2007-01-04
Ok .. hmmm:-k  but what should i do if i  cant install ubuntu?

---

### Post by v8YKxgHe on 2007-01-04
I use to have this problem with my Abit AB9, in the end (about 3 weeks of trying) I gave up and brought a new motherboard (Abit AW9d-Max) which works perfectly.

I emailed JMicron and told them about the problem, but they sort of insisted that there was no problem and they have worked with the Kernel devs to make sure it works...... obviously not the fact.
> 
what is this jmicron? Is it on all motherboards?

No it's not on all motherboards, it's an IDE to SATA converter/controller thingy that doesn't play nice with Linux.

---

### Post by futz on 2007-01-04
What a coincidence! I just built myself a nice new Conroe box today. The mainboard, a Gigabyte GA-965P-DQ6 is an Intel 965/ICH8 chipset board. The ICH8 does 6 SATA2's and RAID but doesn't do IDE at all, so Gigabyte put a JMicron controller onboard to get one channel of IDE and another pair of SATA2s.
 [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2295]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2295")

Anyway, this is the second board I own with a JMicron controller onboard. Installing from a drive controlled by the JM, or to a drive controlled by the JM, is impossible. I've tried EVERYTHING! As far as I can tell it just can't be done. The drivers just don't work, or aren't in the installer or something. The installer crashes every time, no matter which installer you use or what options.

On the GA-965P-DQ6 I finally yanked the IDE cable out of the DVD drive and disabled the JMicron controller in the BIOS. I scratched around in the junk boxes and found an IDE-to-SATA adapter I'd been wanting to test out anyway. Plugged that into the DVD drive and plugged the SATA cable from it into the ICH8 and voila! She works perfect! :mrgreen: :mrgreen: :mrgreen:  Installed without a hitch.

On the Asrock 939Dual-SATA2 mainboard I have, I couldn't install on a SATA hard drive controlled by the JMicron. The drive works fine otherwise (I use it as an archive drive), but you can't install to it. I had to install another IDE drive (on the other controller) to install Ubuntu to.

---

### Post by kuja on 2007-01-04
Hmm, I wonder if that's fixed in feisty.

---

### Post by futz on 2007-01-04
> **kuja said:**
> Hmm, I wonder if that's fixed in feisty.
Hope so, but I'm not holdin my breath. I've tried several other modern distros with the latest kernels on the JMicron boxes and had no luck at all with them either. That driver still really needs some work before it's done.

---

### Post by haxer on 2007-01-04
> **AlexC_ said:**
> I use to have this problem with my Abit AB9, in the end (about 3 weeks of trying) I gave up and brought a new motherboard (Abit AW9d-Max) which works perfectly.

I emailed JMicron and told them about the problem, but they sort of insisted that there was no problem and they have worked with the Kernel devs to make sure it works...... obviously not the fact.


No it's not on all motherboards, it's an IDE to SATA converter/controller thingy that doesn't play nice with Linux.

How does this ide to sata converter looks like? If i use the cabels i get to my motherboard for sata will it work then?:-k

---

### Post by futz on 2007-01-04
> **haxer said:**
> How does this ide to sata converter looks like? If i use the cabels i get to my motherboard for sata will it work then?:-k
It's just a tiny circuit board with an ide plug on one side and a sata connector and floppy-size power connector and a couple LED's on the other side. Plug it into the back of your IDE device and connect power and SATA cables, and your IDE device has become a SATA device.

They're cheap! We got some off Ebay for something like $2.00 each. Paid like $12 each locally, but those came in real packaging and with SATA cables.

Mechanically they suck bad (hey, they're cheap!). The IDE connectors aren't keyed well - you have to be careful that you line them up with the pins because you can be one pin off either way if you don't watch what you're doing. 

The connector wobbles badly when plugged in, and the cables make it sag and make like it's gonna pull off. I tied my cables up to some solid framework with a cable tie. That firmed up the connection quite well - the cables kinda hold it semi-solid. Good enough as long as you're not rough with it.

On some hard drives, the circuit board interferes with the drive's power connector. Some drives just aren't going to work with these things. But for opticals they're great.

EDIT: Some pics
[http://www.satasite.com/sata-ide-converter.htm](http://www.satasite.com/sata-ide-converter.htm)
[http://www.cooldrives.com/sata-adapters.html](http://www.cooldrives.com/sata-adapters.html)
[http://www.satacables.com/html/sata-acessories.html](http://www.satacables.com/html/sata-acessories.html)

---

### Post by Rackerz on 2007-01-04
> **futz said:**
> It's just a tiny circuit board with an ide plug on one side and a sata connector and floppy-size power connector and a couple LED's on the other side. Plug it into the back of your IDE device and connect power and SATA cables, and your IDE device has become a SATA device.

They're cheap! We got some off Ebay for something like $2.00 each. Paid like $12 each locally, but those came in real packaging and with SATA cables.

Mechanically they suck bad (hey, they're cheap!). The IDE connectors aren't keyed well - you have to be careful that you line them up with the pins because you can be one pin off either way if you don't watch what you're doing. 

The connector wobbles badly when plugged in, and the cables make it sag and make like it's gonna pull off. I tied my cables up to some solid framework with a cable tie. That firmed up the connection quite well - the cables kinda hold it semi-solid. Good enough as long as you're not rough with it.

On some hard drives, the circuit board interferes with the drive's power connector. Some drives just aren't going to work with these things. But for opticals they're great.

EDIT: Some pics
[http://www.satasite.com/sata-ide-converter.htm](http://www.satasite.com/sata-ide-converter.htm)
[http://www.cooldrives.com/sata-adapters.html](http://www.cooldrives.com/sata-adapters.html)
[http://www.satacables.com/html/sata-acessories.html](http://www.satacables.com/html/sata-acessories.html)

So using an adapter I shouldn't have a problem using my IDE drives (3) and my one SATA DVD Drive in Ubuntu?

---

### Post by futz on 2007-01-04
> **Rackerz said:**
> So using an adapter I shouldn't have a problem using my IDE drives (3) and my one SATA DVD Drive in Ubuntu?
Depends on your mainboard, the way it's designed and what controllers are onboard.

---

### Post by futz on 2007-01-04
Ooooohhhhh!!! This morning I go to cold boot the new box and it won't start. It's the cheap no-name IDE-SATA adapter causing the trouble. I pulled it out and put the JMicron back on line for the DVD. 

Now that I'm not installing I hope that it will work for everyday use, like the one on the 939Dual-SATA2. That one runs a 320GB hard drive perfectly fine, but you can't install on it.

Have no idea why it worked fine last night but won't work this morning... ](*,)

EDIT: Just talked to buddy who tested one of these on windows. He had lots of trouble with it. So I guess the thing to do is buy from a reputable shop and return it if it causes trouble. Or do like I did - use it as a tool to get Linux installs done on JMicron equipped boxes and then remove it for everyday use.

Eventually I guess the Linux JMicron drivers will get fixed so they actually work, and all this bullcrap will go away.

---

### Post by Rackerz on 2007-01-04
I think I've been pretty lucky in terms of actually getting Ubuntu installed using my SATA DVD ROM and installing to my IDE. I had to do abit of searching for some parameters to restrict some drivers loading so I wouldn't get a freeze up. I'm happily Ubuntu'd, thanks to people on this forum, I really do appreciate the help. 

I hope the issue is fixed with Feisty, I don't feel like messing around too much :).

---

### Post by shadco on 2007-01-06
Hmmm
 
Installed from the Kubuntu Edgy 6.10 Live dvd just fine on my Gigabyte GA-965P-DS3 with my dvd/rw atached to the jmicron and it fould the silly marvell gige too.
 
It runs great and the DVD/RW works fine too once installed.
 
I had problems installing Fed6 in that I had to edit /etc/fstab and change from sda to hda and I had to do the same with grub.
 
Gentoo was the same but I could never get the marvell gige to work.
 
The only problem is that I need 2.6.19-r2 or newer to get sensors to work

---

### Post by maniacmusician on 2007-01-06
so how do i confirm if a board has a JMicron controller? I was just about to buy a board and then I read this. I've also recommended that same board to a couple of other people so I better get this straight quickly. So, uhh, yeah. How do I tell?

I'm assuming that if a board has IDE connectors, it won't be using JMicron, right?

---

### Post by Rackerz on 2007-01-06
The board should have a name like MSW-10086876 or something like that. Type it in google and if your lucky enough it will come up with detailed info on the board.

---

### Post by emperon on 2007-01-07
Have you tried noapic boot option ?

---

### Post by ssam on 2007-01-07
there is lots of stuff at
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/57502](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/57502)
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

maybe try disabling legacy USB support (keyboard/mouse) in the BIOS.

---

### Post by shadco on 2007-01-07
> **maniacmusician said:**
> so how do i confirm if a board has a JMicron controller? I was just about to buy a board and then I read this. I've also recommended that same board to a couple of other people so I better get this straight quickly. So, uhh, yeah. How do I tell?
 
I'm assuming that if a board has IDE connectors, it won't be using JMicron, right?
 
Not quite right.
 
If it has an Intel 965 chipset and an IDE port it most likely has the Jmicron IDE Contorller on it.

---

### Post by Cynical on 2007-01-07
[quote=maniacmusician]so how do i confirm if a board has a JMicron controller? I was just about to buy a board and then I read this. I've also recommended that same board to a couple of other people so I better get this straight quickly. So, uhh, yeah. How do I tell?

I'm assuming that if a board has IDE connectors, it won't be using JMicron, right?[/quote]

Intel's newest chipsets don't have IDE controllers. Manufacturers like Gigabyte / Asus have been forced to add controllers of their own, and they chose Jmicron for that.

But this whole thread is kind of strange, because the bug was patched a while ago, and the edgy release works perfectly. I'm posting from a Gigabyte GA-965P-DS3....

And anyway proper jmicron driver support is included in kernel 2.6.19, so if the problem is still affecting some people it'll be gone by the next Ubuntu release. (I'd definitely recommend getting a supported board, like mine, or one with an nvidia chipset in the mean time)

---

### Post by pmj on 2007-01-07
> **Cynical said:**
> But this whole thread is kind of strange, because the bug was patched a while ago, and the edgy release works perfectly. I'm posting from a Gigabyte GA-965P-DS3....

And anyway proper jmicron driver support is included in kernel 2.6.19, so if the problem is still affecting some people it'll be gone by the next Ubuntu release. (I'd definitely recommend getting a supported board, like mine, or one with an nvidia chipset in the mean time)

So they say, but if you read the comments to the bug report that were made after the fix, this thread or use google, you'll see that whatever the problem is it's not completely fixed. And last I heard it wasn't fixed in Feisty either. Any updates on that?

---

### Post by Rackerz on 2007-01-07
It hasn't been completely fixed, it's still buggy. I managed to get mine working but only after using about 7 boot flags.

---

### Post by futz on 2007-01-08
So it gets even weirder... I managed to totally hose that Ubuntu install on Saturday (don't ask - long story) and decided to reinstall rather than fight it. The reinstall (from the JMicron controlled IDE DVD drive) went totally fine this time. Not a single problem. Huh? WTF was going on the first time???

Anyway today I replaced the DVD writer with a SATA unit, so all drives are on the ICH8 controller and the JMicron is disabled.

**Final list:**
1 - Gigabyte GA-965P-DQ6 Mainboard
1 - Mushkin HP2-6400 2x1GB 4-5-4-11-1T
1 - Intel Core 2 Duo E6600 Dual Core Conroe 2.40GHZ
1 - WD360GD 36GB Raptor SATA Hard Drive
1 - WD740GD 74GB Raptor SATA Hard Drive
1 - Samsung Spinpoint T Series 300GB SATA2 Hard Drive
1 - Liteon SH-16A7S 16X SATA DVD Writer
1 - EVGA E-GEFORCE 7950 GT KO 560MHZ PCI-E 512MB
1 - Belkin F5D7000 Wireless G Desktop Card
1 - OCZ GameXStream 600W SLI Ready Active PFC power supply
1 - Atop XBlade tower case
[ATTACH]22546[/ATTACH]

The machine is *wicked fast* compared to everything else in the room, and some of those aren't too shabby. It runs the SuperPI benchmark **twice** as fast as my Athlon 64 X2 4200+ machine. I'm very pleased with it.

Don't laugh at the Belkin card. I'd ordinarily never touch any of their products, but it was blowout priced. Turns out it's an Atheros card, so what I paid was about 1/3 the price of a comparable D-Link. And both Ubuntu and SabayonLinux (both running the wonderful NetworkManager applet) pick it up automatically. It just works.

---

### Post by maniacmusician on 2007-01-08
Oh sweet, thanks for the info! I was worried because I'm actually upgrading my computer completely.

I'm getting the 650i nForce chipset from ASUS so it's good to know I won't even have to worry about it, even though it seems like its fixed.

---

### Post by jformsma on 2007-01-09
I had the same problem several months ago. Until Ubuntu has a fix, OpenSuse 10.2 will work at least work on my system, so I'm using that in the meantime.

My system has the Intel DP965LT mainboard, Core 2 Duo 2.13 gHz proc, and 1 G Ram.

With OpenSuse, at least I'm getting used to Linux (very slowly), and have a dual-boot system with Win XP, which is what I was used to.

John

---

### Post by PilotJLR on 2007-01-19
My Core 2 Duo works perfectly with Edgy. I have an Intel board... the only gotcha is the Marvell PATA controller. I had to install the OS via a USB CD drive, then install the Marvell patch... all gravy after that. Great OS and great processor!

---

### Post by Gehaktbal on 2007-01-25
This is really anoying. I finally managed to install ubuntu but it still gives me this after selecting in grub:

PCI:JMB36x: enabling dual function on 0000:04:00.0
PCI:cannot allocate resource 0 of device 0000:04:00.0
PCI:cannot allocate resource 1 of device 0000:04:00.0
PCI:cannot allocate resource 2 of device 0000:04:00.0
PCI:cannot allocate resource 3 of device 0000:04:00.0
PCI:error while adapting region 0000:04:00.0/0
PCI:error while adapting region 0000:04:00.0/1

Can somebody please help me.

I have:
Abit ab9
2x512mb memory
nvidia Geforce 7900GS
1 SATA HD connected between the pci slots
1 PATA cdrom drive connected between the pci slots.

---

### Post by luca.b on 2007-01-25
Try using the "irqpoll" boot option.

---

### Post by Gehaktbal on 2007-01-25
No use

---

### Post by Happy_Man on 2007-01-25
After reading all this, I cannot help but say "Thank God I'm not on the cutting-edge!"

---

### Post by futz on 2007-01-25
> **Gehaktbal said:**
> This is really anoying. I finally managed to install ubuntu but it still gives me this after selecting in grub:

PCI:JMB36x: enabling dual function on 0000:04:00.0
PCI:cannot allocate resource 0 of device 0000:04:00.0
PCI:cannot allocate resource 1 of device 0000:04:00.0
PCI:cannot allocate resource 2 of device 0000:04:00.0
PCI:cannot allocate resource 3 of device 0000:04:00.0
PCI:error while adapting region 0000:04:00.0/0
PCI:error while adapting region 0000:04:00.0/1
But it still finishes booting up, right? That looks like the standard batch of error lines I see on bootup on every machine with an enabled JMicron controller in it. They all still work, except sometimes when you're trying to install with em.

I just ignore it.

---

### Post by Gehaktbal on 2007-01-26
No that's the problem it doesn't boot after that. I even let it on for a few hours. A member on a dutch forum said i had the same errors but it still boots. In my case it hangs after those errors.

---

### Post by macogw on 2007-01-26
> **kuja said:**
> Hmm, I wonder if that's fixed in feisty.

Try the herd 2 disc and if it's not, bug report it and give it a higher than normal importance level

---

### Post by tnseditor on 2007-01-27
I had the same problem.  I have an Intel DG965ss board.  I tried Feisty Herd 2 and everything works.

---

### Post by Rackerz on 2007-04-21
Glad you guys got some luck out of Feisty, I didn't :(.

---

### Post by KiwiNZ on 2007-04-21
I havent been able to rum any flavour of Linux on my Core 2 Duo 6700 machine since I purchased it .Tried and tried and finally surrendered

---

### Post by Rackerz on 2007-04-22
What problems do you get?

---

### Post by jrusso2 on 2007-04-22
I was listening to a podcast the other day with the developer of Mepis and he indicated that he put the fix for the jmicron in mepis 6.5 if someone wants to run a ubuntu based distro that should work.

---

