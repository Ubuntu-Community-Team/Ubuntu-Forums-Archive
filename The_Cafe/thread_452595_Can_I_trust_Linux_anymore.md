---
title: "Can I trust Linux anymore?"
date: 2007-05-23
forum: The Cafe
---

### Post by FuturePilot on 2007-05-23
In light of what recently happened to my computer after a random Feisty freeze I wondering if I can still trust it? Basically after a hard reboot my BIOS got borked and now nothing will boot. Could this have been just a coincidence? Like I mean the same thing could have happened if Windows froze but I just happened to be using Ubuntu? 

If and when I get my computer back up and running, I almost scared to put Linux back on it. What if it happens again? I love Linux a lot and for the past 6 months I've been using Ubuntu almost exclusively. But it's rather unnerving to think that something like this could just about brick your computer. I'm using Windows right now and I can't stand it. I want to use Linux again, but now I'm a little scared to.

Can someone please enlighten me?[-o<

---

### Post by KIAaze on 2007-05-23
What do you mean by nothing will boot? Is it just GRUB not coming up or is really completely unbootable, not even into the BIOS?
If you can't even install a new OS from a bootable media, then it's probably a hardware problem.

Are you running Windows on the same PC after reinstalling it or not?
If you love Ubuntu so much, there's no reason giving up so fast. ;)

---

### Post by LaRoza on 2007-05-23
I wouldn't blame Feisty right off. Something like this could be a hardware problem, or if the computer is older, it could be a dying battery, (which powers the cmos when the computer is off, it does not recharge).

I say "could" because I am not sure if you know for sure it is Feisty, but I would say it IS hardware/battery, mainly because it happened after a hard boot, which I assume is not common for that computer.

---

### Post by Znupi on 2007-05-23
No OS can break your BIOS. It must've fallen apart itself, although this happens very rare (at least I never heard of a BIOS breaking, but...). So I guess yeah, you can trust Linux.

---

### Post by Lucifiel on 2007-05-23
Hmmm... maybe you could bring your pc to a reliable pc troubleshooting shop and ask them to test your components.

It sounds like something is getting wonky.

---

### Post by Eddie Wilson on 2007-05-23
> **Znupi said:**
> No OS can break your BIOS. It must've fallen apart itself, although this happens very rare (at least I never heard of a BIOS breaking, but...). So I guess yeah, you can trust Linux.

Znupi is correct. I've never seen an operating system break the BIOS. It is loaded and post begins before any os has a go at your computer. I have also seen a BIOS system go down so I would say its a hardware problem.
Eddie

---

### Post by FuturePilot on 2007-05-23
I mean it won't boot anything. Ubuntu, Windows, or even a live CD. I'm still getting POST so I will be able to try and flash it, but I seem to have hit a wall with that.

But doesn't an OS interact with the BIOS in some way? If so then it could break your BIOS right? I could be totally wrong on that. The thing is it was working perfectly fine before the reboot. Afterwards it was all messed up. But I've done hard reboots before with this computer and this is the first time something like this happened.

---

### Post by Lucifiel on 2007-05-23
Oh yes, possible causes of Bios going bonkus include:

a) dying power supply unit
A dying psu literally screwed up my motherboard. Now, I've to be careful when using the bios or else it might go bonkus and refuse to boot.

b) dying Cmos battery
If your time is constantly out of sync too, then this could be a possible cause.

c) Wonky motherboard
Yep, if some of the capacitors or other components on your motherboard are dying, then you could have problems booting up.

No, the o/s does NOT interact with your bios. If it did, everytime an o/s broke, there'd be mass chaos.

---

### Post by EdThaSlayer on 2007-05-23
Replace your bios chip. Thats how I fixed my nasty bios problem. Go to a repair shop you can trust.

---

### Post by dbott67 on 2007-05-23
Mere coincidence.

I've been a sys admin for over 12 years, with various combinations of Windows PCs running virtually every version of Windows (3.1 through Vista), Windows servers (NT 4 though 2003), Netware 3.x through 4.x, RHEL, AIX, etc.

I have had hardware failures on all.  Dozens of hard drives and power supplies; a few motherboards; just yesterday a stick of RAM; network cards; printers; monitors; mice; keyboards; barcode scanners; CD-ROMs; floppy drives; USB drives... the list is long.

I've also had hubs & switches fail; a Nortel Passport Fibre-optic core; gigabit switches; ISDN routers; broadband routers; DSL modems; wireless bridges.

Some of this stuff failed after a simple re-boot; a few failed after the big blackout in August of 2004 (eastern Canada & US); others just failed because it felt like it.

My recommendations are:

- UPS and filtered power (i.e. a good surge protector)
- regular backups of critical data

Hardware failure is not a question of "if" --- it's "when".

-Dave

---

### Post by Zyphrexi on 2007-05-23
would lm-sensors give a good indication of system health? Are there any programs that check that out?

---

### Post by FuturePilot on 2007-05-23
So it seems that this was a freak coincidence and this is most likely an issue with some piece of hardware crapping out on me?

---

### Post by Lucifiel on 2007-05-23
> **FuturePilot said:**
> So it seems that this was a freak coincidence and this is most likely an issue with some piece of hardware crapping out on me?

Yep. You can laugh on this, btw.

When I was playing Divine Divinity a few years ago, whenever it came to a certain part of the game, the pc would keep freezing.

In the end, it turned out that the hard disk had died.

---

### Post by WinterWeaver on 2007-05-23
NO, the OS does not interface with the BIOS. It cant break it, so the problem must be hardware related. As they mentioned before. CMOS battery, etc.

EDIT: lol... seems I need to refresh the page more, since there are soo many replies already, which I never noticed :P

---

### Post by cyrusrayne on 2007-05-23
It sounds very much like a hardware issue both from what I've been reading in the thread.  I stand with the others when I urge you to go visit your local repair shop.  They should be able to help you further with the problem.

---

### Post by FuturePilot on 2007-05-23
> **Lucifiel said:**
> Yep. You can laugh on this, btw.

When I was playing Divine Divinity a few years ago, whenever it came to a certain part of the game, the pc would keep freezing.

In the end, it turned out that the hard disk had died.

Good. I feel a lot better knowing it wasn't Ubuntu that did it. I will probably laugh at this one day.
It was weird when it froze because the screen flickered on me. Usually when something freezes, it just freezes. The screen doesn't flicker.

---

### Post by Lucifiel on 2007-05-23
> **FuturePilot said:**
> Good. I feel a lot better knowing it wasn't Ubuntu that did it. I will probably laugh at this one day.
It was weird when it froze because the screen flickered on me. Usually when something freezes, it just freezes. The screen doesn't flicker.

Maybe it could even be your graphics card but go find out, dude, and don't even boot up the pc anymore. 'Cos if something's dying, it could take down your entire system with it. 

Disconnect the power plug and lug it to a shop when you have the time to.

---

### Post by FuturePilot on 2007-05-23
My initial thought was that the graphics card died, because it still seemed to boot stuff fine until it came time to start the graphical interface. Ubuntu would still boot fine until it came time to start X and load the Nvidia driver. Then it just froze at a blank screen. Same with Windows. It started to boot Windows until it came time to load the graphics drivers then it just BSOD on me.

I'm going to look for someplace to take it. Go figure, I was supposed to take this computer to school next year:p

---

### Post by Znupi on 2007-05-23
So you tried booting it with the graphics card broken until you messed up the BIOS, too? :lolflag:

---

### Post by FuturePilot on 2007-05-23
No, the BIOS was already messed up after I rebooted from the Feisty freeze.

---

### Post by Tomosaur on 2007-05-23
> **FuturePilot said:**
> In light of what recently happened to my computer after a random Feisty freeze I wondering if I can still trust it? Basically after a hard reboot my BIOS got borked and now nothing will boot. Could this have been just a coincidence? Like I mean the same thing could have happened if Windows froze but I just happened to be using Ubuntu? 

If and when I get my computer back up and running, I almost scared to put Linux back on it. What if it happens again? I love Linux a lot and for the past 6 months I've been using Ubuntu almost exclusively. But it's rather unnerving to think that something like this could just about brick your computer. I'm using Windows right now and I can't stand it. I want to use Linux again, but now I'm a little scared to.

Can someone please enlighten me?[-o<

I would suggest that rather than Feisty causing your mobo to break - it was actually your motherboard crapping out and thus causing feisty to freeze.

If it's any comfort, I'm using feisty now and have been using Ubuntu for a few years - it has never once caused any of my hardware to die.

---

### Post by FuturePilot on 2007-05-23
> **Tomosaur said:**
> I would suggest that rather than Feisty causing your mobo to break - it was actually your motherboard crapping out and thus causing feisty to freeze.

If it's any comfort, I'm using feisty now and have been using Ubuntu for a few years - it has never once caused any of my hardware to die.

That's exactly what I thought. I think my Nvidia card just crapped out causing the freeze. It also could have been something else. It going to be a bit tricky finding out which component it is.

And thanks, I'm feeling a lot better now knowing that it wasn't caused by Ubuntu.;)

---

### Post by orb9220 on 2007-05-23
Also check by entering the bios and reset it to defaults.
or
open computer and find the usally 3pin jumper next to battery note which pins the jumper are on.
example Pins 1-2closed,3open then move the jumper from 1-2 to 2-3 leave for 30 secs then move jumper back to orig 1-2 that is the cmos hard reset for the bios.

Otherwise like the others I see it as a hardware problem.
Make sure your fans are running.

Most bios you can see the Cpu temps,fans,voltages on one of the pages. And see if anything is changing rapidly.

---

### Post by FuturePilot on 2007-05-23
Yeah I've tried resetting the BIOS by loading the defaults as well as trying the jumpers. No go though. I'm on the phone with HP now having having them make me do stuff that I already did.:p They made me erase the HD. No more Ubuntu, for now):P

---

### Post by DoctorMO on 2007-05-23
All the posts so far are correct.

 1) Computer freezes, hardware fault (remember computer hardware is a digital representation in an analog world, a loose pin or failing solder joint can be very bad) mostly ram problems or cpu over heating or if new or very old components, hardware failure.
 2) Computer reboots or turns off without warning, short, faulty hardware.
 3) Applications freeze but you can still use the mouse, X windows has died somehow (software problem)
 4) Freeze but able to press [ctrl]+[alt]+[delete] to restart? kernel problem, possible root service crapped all over the ram.

It reminds me, the other day I plugged in my tv cart (bttv bt878 pci) and the thing poped out of the slot while the computer was switched on (I didn't screw it down) the computer froze without allowing a soft reboot. hard off, plugging the card back, with screw and turning it back on and everything is fine (thank god)

---

### Post by lupin492 on 2007-05-28
FuturePilot, please give us a clue of what's going on on your PC ! 
While rebooting (or trying to), did your PC ?:
- emitted some "peeps" (sounds) ?
- gave any message ? Kinda "GRUB messages", "BIOS messages", a single-fu...-cursor blinking, or what ?
- did you perhaps reinstalled Microshit AFTER Linux ? 

Help us help you !  :-)

---

### Post by lupin492 on 2007-05-28
Sorry, I just seen a post of yours telling your PC restarted ok up to the Xserver startup.   If you changed some X parameters just before the crash, or installed new programs/drivers, try "ctrl+Alt+F1", log-in and "sudo dpkg-reconfigure xserver-xorg" and reconfigure your Xserver.
However, it doesn´t account for the fact of Microshit showing the same "pattern".    I end up finding your graphics-hardware as "guilty" the same as the other people here.  :-D
Regards!

---

### Post by Swab on 2007-05-28
> **FuturePilot said:**
> No, the BIOS was already messed up after I rebooted from the Feisty freeze.

If it boots the kernel then the BIOS is not the problem.

---

### Post by RAV TUX on 2007-05-28
You honestly should replace your Bios with the LinuxBIOS:

[http://linuxbios.org/Welcome_to_LinuxBIOS](http://linuxbios.org/Welcome_to_LinuxBIOS)
> 
 The Linux BIOS replaces the normal BIOS found on PCs and other machines. The BIOS boot and setup is eliminated and replaced by a very simple initialization phase, followed by a gunzip of a Linux kernel. The Linux kernel is then started and from there on the boot proceeds as normal. Amongst many other things, it provides a very fast boot time: 3 seconds from power-on to Linux console 
 Ronald started the [LinuxBIOS]("http://linuxbios.org/") project in 1999, with the simple goal of building a specialized BIOS for supercomputers. Since that time, the LinuxBIOS project has seen the usage grow by a factor of 10 each year, to a projected usage of well over 10 million in 2007, and 100 million in 2008. 
 With the advent of the [OLPC project]("http://laptop.org/"), there is enough critical mass to design hardware as it should be designed, and in turn, build a BIOS as it ought to be built. For example, the OLPC will not use badly designed standards such as ACPI -- there is no need to. 
 In this talk, Ronald will discuss:[LIST]
[*]some of the early history of LinuxBIOS, as a motivation for why it is designed the way it is;
[*]what he learned in building a free BIOS,
[*]including knowledge that was lost but was rediscovered;
[*]issues he faces in dealing with vendors
[*]interesting things you can do when you own the BIOS
[*]the work Google is supporting
[*]what the future holds[/LIST][http://www.fosdem.org/2007/schedule/events/linuxbios](http://www.fosdem.org/2007/schedule/events/linuxbios)

Even if it turns out your Bios is good there are a lot of positive reasons to use a LinuxBios beyond a three second boot time. For more information check out the OpenBios page also:
[http://www.openbios.info/Welcome_to_OpenBIOS](http://www.openbios.info/Welcome_to_OpenBIOS)

---

### Post by notquitemichael on 2007-05-28
on a side, reading his last post, it's really aggravating when support people suggest you erase your hard drive when the chances of the problem originating from there are minimal.

sorry. tiny once 'advised me' to use their cd to recover [wipe] my computer when they gave me a duff modem. so it's a bit of a sore point.

---

### Post by mthakur2006 on 2007-05-28
RAV TUX!! you are back!

---

### Post by RAV TUX on 2007-05-28
> **mthakur2006 said:**
> RAV TUX!! you are back!

I am here. I actually never left, just retired from the staff position. ;)

---

### Post by FuturePilot on 2007-06-07
A little update. I got the computer back, and you guys were right. There was a hardware failure.This is what it said on the sheet that came back with the computer.
> DDRII400 HYNIX 512MB 240P         Parity Error
DDRII400 HYNIX 512MB 240P         Parity Error
DDRII400 HYNIX 512MB 240P         Parity Error
DDRII400 HYNIX 512MB 240P         Fatal Exception/Divide Overflow
P5LP-LE/Limestone-GL8E/HPD         No Boot hangs on POST

So apparently they replaced all 4 sticks of RAM and the MB. It makes sense. The RAM probably crapped out which is why it froze which then messed up the MB. What a mess. Unfortunately during shipping the HD got damaged because now it keeps making a loud click every so often. Ugghh. Another mess:rolleyes:

Going to go find my Feisty CD:D

---

### Post by init1 on 2007-06-07
> **FuturePilot said:**
> In light of what recently happened to my computer after a random Feisty freeze I wondering if I can still trust it? Basically after a hard reboot my BIOS got borked and now nothing will boot. Could this have been just a coincidence? Like I mean the same thing could have happened if Windows froze but I just happened to be using Ubuntu? 

If and when I get my computer back up and running, I almost scared to put Linux back on it. What if it happens again? I love Linux a lot and for the past 6 months I've been using Ubuntu almost exclusively. But it's rather unnerving to think that something like this could just about brick your computer. I'm using Windows right now and I can't stand it. I want to use Linux again, but now I'm a little scared to.

Can someone please enlighten me?[-o<
Bad things often happen to me when I use linux. I repartitioned my entire hard drive, messed up my ubuntu partition, messed up my mepis partition, can't always use sound, apps don't always work, etc. But I still use it and have no plans to stop.

---

### Post by Tundro Walker on 2007-06-07
The "blame the messenger" syndrome...

**FALACY:** "Linux can't detect my hardware, so obviously, it's Linux' fault and that means Linux suckorz!"

**FACT:** A lot of hardware manufacturers don't make drivers for Linux.  If your hardware doesn't work on Linux, it's because the hardware manufacturer you chose to give money to decided that Linux wasn't right for you before you even installed it.  In other words, someone else has already made decisions for you, restricting your overall freedom (to use Linux).

**FALACY:** "My BIOS chipped got borked up, and since Linux was on my machine during that time, obviously it's Linux' fault, which means Linux suxorz."

**FACT:** Linux doesn't mess with your BIOS.  If your computer's not booting, it's because some piece of hardware is screwing up.  Boot your computer and listen to the beep codes.  Then get on someone else's comp and surf the net for the beep codes for your BIOS / CPU.  That should tell you what's screwing up. Sometimes it's bad RAM.  Sometimes bad BIOS chip.  Sometimes a bad piece of hardware.

Linux usually isn't the cause of your problems, it's just messenger telling you that something's screwed up.  So stop blaming it, and figure out what the real problem is.

---

### Post by smoker on 2007-06-07
> **FuturePilot said:**
> .. Unfortunately during shipping the HD got damaged because now it keeps making a loud click every so often...

i think i would check out the hard drive to be safe. download the bootable version of 'drive fitness test'
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

good luck:D

---

### Post by FuturePilot on 2007-06-07
> **smoker said:**
> i think i would check out the hard drive to be safe. download the bootable version of 'drive fitness test'
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

good luck:D

Thanks. I ran the test and everything was OK. I even ran the test in my BIOS and everything turned out OK. Not sure what that noise was, but it seems to have stopped.:-k

---

### Post by RedSquirrel on 2007-06-07
> **FuturePilot said:**
> Thanks. I ran the test and everything was OK. I even ran the test in my BIOS and everything turned out OK. Not sure what that noise was, but it seems to have stopped.:-k
I'm glad things are OK now.

I just wanted to agree with the advice above about listening to the beeps. A while ago, I was able to fix one of my really old machines by determining that the video card was toast. It wasn't too hard to track down the problem, which was a relief. New card => usable machine. Yay!

---

### Post by FuturePilot on 2007-06-07
Dah, it started again#-o

---

### Post by woodsmoke on 2007-06-08
> **Znupi said:**
> No OS can break your BIOS. It must've fallen apart itself, although this happens very rare (at least I never heard of a BIOS breaking, but...). So I guess yeah, you can trust Linux.

Znupi is correct here....the bios is part of the "hardwireing"....although it can be changed with a process called "flash"...."flashing the bios".....

but to continue Znupi is correct...... something else has happened...if you can't load either a Linux or a Microsith product then it is a hardware problem that is not connected to the OS...

I "thought" that I had somehow borked a dual boot with WinXP and "other distro"..... and I MESSED with the thing for several days.....

and.....came to find out....it was the "on-off" swithch.... :roll:

woodsmoke

---

### Post by Znupi on 2007-06-08
> **FuturePilot said:**
> Dah, it started again#-o
You should speak to the guys who repaired your PC.

---

