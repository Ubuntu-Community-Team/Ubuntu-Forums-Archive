---
title: "my experience of building my own PC is horrid!!"
date: 2007-03-22
forum: The Cafe
---

### Post by billdotson on 2007-03-22
This first experience of building my own PC has been a nightmare. First I thought my mouse had been messing up and I finally think it was a bug in a PC game I was playing, then I could not ever get my DVD drives to burn but then I realized that I had to install a driver for the JMicron to make the IDE drives work correctly (why in the heck do I have to install a driver for something soldered on the MB?!), 2 weeks ago I sent my motherboard and PSU off because my PC was freezing about half of the time at the BIOS screen regardless of a cold or warm boot. Finally I get my replacement MB and PSU back, put my PC together and then boot it up. I get CPU fan error and realize I plugged the CPU fan in the wrong place (my fault, I know). Then one of my case fans that is mounted inside the 3.5" bay where the hard drive kept rattling. I tightened up some screws on the hard drive and flicked the fan around a bit and I haven't noticed it since.

I was so happy to boot into Ubuntu for the first time in 2 weeks to only realize that the internet didn't work. Then after running avidemux and shutting it Ubuntu freaked out and my RAM was in full usage. To day the same thing happened except it was the CPU. The sound isn't been working in Ubuntu either. Then apart from that I booted up yesterday morning and after I thought I had fixed the problem of my BIOS freezing guess what the BIOS froze after booting up (PC was off all night) Then the CPU cores are reversed.. what the heck?! and the 2nd core is the primary one with 4096KB of cache while the 1st core only has 32KB.

IMO I think the main issue here is that I just got a terrible model of motherboard.

---

### Post by some_random_noob on 2007-03-22
lol... blame the motherboard eh? Building a computer should be pretty easy, just get your cables the right way around, use the standoffs for the motherboard and pay attention when installing the cpu. Also, check the documentation.

I built a computer recently on my course, it wasn't fun. But I'm confident now :D ... how old are you?

---

### Post by BarfBag on 2007-03-22
Building is the way to go.  You definitely get a better PC.  If you hunt around, it can even save you a little money.

Don't let your lemon motherboards discourage you.  If you buy your hardware from a retail store like CompUSA or BestBuy, you generally get better return policies then at an online store.  At an online store, you get better prices and more selection.

The things that are best bought at retail stores are your case, monitor, speakers, keyboard, and mouse.  You can see them in person and make sure they're not cheaply made before you buy it.

---

### Post by WalmartSniperLX on 2007-03-23
My favorite thing about building vs buying prebuilt from OEM is that you get retail parts that are unmodified (usually oem companies put some modified limits on your motherboard to prevent extra tweaking such as OCing that can void warranty or cause hell if an exeperienced goes too far thru the bios :P ). 

Sometimes the motherboard can have its issues in Linux. Sometimes its something else. :P Don't feel discouraged EVER. If you have a bad exp, learn from it and try again and you should have greater success But make sure you always read your documentation and do extra research online even before purchasing so you are positive everything is going to work smoothly for what you need.

---

### Post by WalmartSniperLX on 2007-03-23
> **BarfBag said:**
> Building is the way to go.  You definitely get a better PC.  If you hunt around, it can even save you a little money.

Don't let your lemon motherboards discourage you.  If you buy your hardware from a retail store like CompUSA or BestBuy, you generally get better return policies then at an online store.  At an online store, you get better prices and more selection.

The things that are best bought at retail stores are your case, monitor, speakers, keyboard, and mouse.  You can see them in person and make sure they're not cheaply made before you buy it.

TRUE TRUE TRUE :)

---

### Post by Ubunted on 2007-03-23
If at first it drives you nuts, do what I do - format the drive, take it apart, clean it up and start again.

---

### Post by billdotson on 2007-03-23
well I am 18 and I have put together a PC 3 times now.  I built this one, then built one for my friend, and then rebuilt this one after sending the motherboard and PSU off for RMA.  
Before I replaced my motherboard everything in Ubuntu worked fine.  Internet worked great, resource management was good but then now w/ the replacement Ubuntu can't do anything at all really.  As I said earlier the internet will NOT work no matter what.  It doesn't matter if I use my install or if I use the LiveCD.  The frustrating thing that isn't Ubuntu-related is that before I replaced my motherboard and PSU my PC would keep freezing at the BIOS screen regardless of whether I was doing a 'cold' boot or a 'warm' boot.  Sometimes I would have to restart ~3 or so times, then turn off the surge protector and then turn it and the PC back on.  Now, after all that  
it froze at the BIOS once again.  

I put it back together and booted into Windows and everything is working fine (in Windows).  I power down the PC before I go to sleep and then wake up boot it up and it freezes at the BIOS.  I've tested the RAM compatibility, and the CPU and MB temps and everything was fine in that regard so I assumed it must have been the external hard drive being plugged up when I booted.  So that night when I powered own I unplugged the external drive.  Then I booted up the next morning and it didn't freeze.  OK, so I thought I had proved it was the external HDD.  Well last night I power it down, DON'T unplug the external HDD and boot it up today about 20 minutes ago and it doesn't freeze.  So now I don't know if it is the external HDD or not. 

From what I know this annoying problem can be: system instability due to RAM errors or incompatibilities (checked that w/ memtest86), high hardware component temperatures (checked that), electromagnetic interference w/ the MB and something else (doesn't look like the MB is touching anything except screws), failing, faulty or not powerful enough PSU,  incorrect BIOS settings, devices not being detected correctly or fast enough by the BIOS on boot or the far-fetched one a faulty surge protector.  

I have run memtest86 6 times on my RAM and it passed 6 times w/ no errors.  My CPU and MB are cool enough, my motherboard doesn't have any blown capacitors, my MB is brand new, my PSU is brand new and has enough watts (and amps per rail) to power my system correctly, my MB doesn't appear to be having any electromagnetic interference, AFAIK my BIOS settings are correct (except that my CPU cores are recognized in the opposite order.. the 2nd core being the dominant core with the 4096KB of cache), I have a month old surge protector advertised as computer grade, and the only external device that is hooked up to my PC when it boots is my external HDD.  Maybe the external HDD is finicky and has to have some specific BIOS setting or messes up the boot sporadically.  I do not know but I hate having anything wrong w/ my PC.  I haven't gotten anything done in 3 days because I have been trying to diagnose the issue.  ARGGGH!!!

---

### Post by BeachBum on 2007-03-23
I also have issues booting with an external harddrive plugged in, the boot process hangs at the inital showing of the Ubuntu logo, but I've been to lazy to do anything about that :) .

I've had an interesting issue this latest build of mine; was carrying over some generic ram into a new HTPC with integrated graphics, and the graphics appeared not to work.  I had ran memtest before and it showed one of the sticks was bad, so I had a new and old stick in there; running memtest with the old one for 24hrs didn't produce an error.  I got fed up, and took it to MicroCenter to see what sort of support they could offer (I purchased online, but they offer great free support).  The tech took one look at its symptoms, swapped out some ram with sticks he had laying around and voila, it worked.  Both old sticks were bad, even though memtest revealed only one to be bad.  Other than such small glitches, building is great fun, but then again, somtimes troubleshooting is half the fun.

What brand stuff are you using?  Did you buy it new?  When you say you ran memtest, how long did you let it run? You indicated that the motherboard is most likely at fault, have you tried flashing the BIOS?  Resetting the CMOS?

---

### Post by futz on 2007-03-23
> **billdotson said:**
> ARGGGH!!!
Hehehe! If you were closer I'd just say, "Drop it off at my shop (my house) with a case of beer on a Friday. Pick it up Monday (sometimes Saturday or Sunday) with all problems fixed."

I build and rebuild probably 6 to 12 machines a year (sometimes more) for myself and other people. I've built every machine I use (I have too many) for the last 8 years or so. Customers from years back bring em in with malware and virus problems (idiot windoze users) and always say the machine has been rock solid.

So it can be done. You may have some odd combination of hardware that's causing problems, or you've made a mistake, or you got two defective products in a row? It's rare, but it happens.

> Building is the way to go. You definitely get a better PC.
YES! So true. I work on the odd package machine, and they're invariably annoying and crappy.

---

### Post by %hMa@?b&lt;C on 2007-03-23
my experience of building my Opteron box was good.  It was my first, and I had no errors, except a nasty gash on my left ring finger

---

### Post by billdotson on 2007-03-24
I bought all my parts new, bought the name brand stuff Antec, Asus, Zalman, Seagate, nvidia, Creative, Intel Core 2 Duo, and so on.  I ran memtest long enough the first time to completely check the RAM once.  The second time I let it run long enough where it went through 5 total checks.  All 6 times memtest showed no errors and the RAM passed each test.

I don't know if it is the motherboard but I guess flashing the CMOS couldn't hurt.  Just pop out the battery move the two jumpers over for ~10 seconds, move 'em back and put the battery back in.  Then go and set the BIOS to defaults.  If all else fails I could jsut flash the BIOS to the latest version that came out in December I guess.  The BIOS on this replacement board is something like 0704 or something and is ~4 months older than the BIOS version that was on the original which was something like 0507.  The latest version is 1004 or something like that.  I have never flashed the CMOS myself but I have flashed the BIOS. Before getting my replacement board I flashed the BIOS to the 1004 version.  I hear that flashing your BIOS generally is very risky but with Asus MB I have there is some easy update utility that made it quite simple.

---

### Post by billdotson on 2007-03-24
please help.

---

### Post by izanbardprince on 2007-03-25
> **WalmartSniperLX said:**
> My favorite thing about building vs buying prebuilt from OEM is that you get retail parts that are unmodified (usually oem companies put some modified limits on your motherboard to prevent extra tweaking such as OCing that can void warranty or cause hell if an exeperienced goes too far thru the bios :P ). 

Sometimes the motherboard can have its issues in Linux. Sometimes its something else. :P Don't feel discouraged EVER. If you have a bad exp, learn from it and try again and you should have greater success But make sure you always read your documentation and do extra research online even before purchasing so you are positive everything is going to work smoothly for what you need.

In my experience, Gateway and Dell systems run Ubuntu fairly well, but HP/Compaq systems don't.

---

### Post by Bartender on 2007-03-25
Sounds like motherboard or power supply to me.  I'd take everything back out of the case and set up the motherboard, power supply, and one optical drive on a piece of wood or cardboard, something non-conductive.  Plug just one piece of RAM in, no hard drive, see if the PC will boot to BIOS and leave it running for a day or two.  See if it freaks out.  If it does, swap that piece of RAM with your other.  I'm assuming you bought two sticks :) 

If it seems stable, turn it off, plug in your second piece of RAM, try again.  

Then plug in a HDD, start it up, go into BIOS, make sure the HDD is recognized correctly, leave it alone for a while again.

You see what I'm getting at.. start out with the absolute minimal setup and add parts until the problem arises.  If the problem comes at step one it's pretty much gotta be motherboard or power supply.

If it runs on the cardboard but freaks inside the case I'd be looking at something conductive touching the motherboard.

---

### Post by 3rdalbum on 2007-03-25
> **izanbardprince said:**
> In my experience, Gateway and Dell systems run Ubuntu fairly well, but HP/Compaq systems don't.

I have a Compaq system that runs Ubuntu like a dream... a good dream featuring lots of lovely ladies.

---

### Post by mips on 2007-03-25
> **billdotson said:**
> 
From what I know this annoying problem can be: system instability due to RAM errors or incompatibilities (checked that w/ memtest86), high hardware component temperatures (checked that), electromagnetic interference w/ the MB and something else (doesn't look like the MB is touching anything except screws).

I usually use the reddish non-conductive washers for those incase the heads of the screws overlap a bit. You never know. Also ensure you are using the latest bios.

---

### Post by adam.tropics on 2007-03-25
Bios problems can go from the irritating to down right bizarre. As mips said bring it up to date. It can be scary stuff, but less so on desktops. You have no power management system to contend with....that cost me one laptop! (flashing bios) Thankfully on that occasion Toshiba were great. Good luck though, once it's all done, building your own is a really good experience.

---

### Post by billdotson on 2007-03-25
should I just reset the CMOS and then flash the BIOS to the latest revision (is that the right order?)  The MB and PSU are both brand new replacements so I would assume the chance of them being defective is very low.  Before I sent my MB off for replacement I ran memtest86 long enough where memtest86 would complete 5 complete RAM checks.  My RAM passed all 5 times w/ no errors.  I do not think the MB would be having any such electromagnetic interference as around the screw holes on the MB there are little raised copper/something else bumps.. wouldn't that keep EMI from happening?

The odd thing is, apart from all of the annoying issues in Ubuntu (no internet!!) the PC seems pretty stable AFAIK, but for some reason every now and then when I boot up (cold boot; being off 6+ hours) it will freeze at the MB BIOS screen.. not the settings screen or POST screen but the blue Asus P5B Deluxe screen.  The day after I put it together and it froze at the BIOS it might have been that it was just taking a long time to get past it.  For the past few days when I boot (w/ my external HDD in) it will stay at the starting BIOS screen for about a minute before going to the POST and then loading the OS.  I do not know if it takes that long if I do not have my external drive plugged in.  Although, even if it was the external that is still annoying because I use it for my Linux distros.  **Also, I do not know if this is an issue but every time my PC is rebooted/booted the system does a single beep before going to the blue Asus BIOS screen (I also do not know if it does this w/ the external drive NOT plugged up)**  In my MB manual it says in the section Booting up for the First time:

One beep: Keyboard controller error, refresh time error or no master drive detected.

Two continuous beeps followed by two short beeps: floppy controller failure

Two continuous beeps followed by four short beeps: hardware component failure.

So could it be that (if) my PC does not beeo when booting when the external HDD isn't plugged in could it be that the refresh time on my external HDD is too short or that the system cannot detect a master HDD?  In my USB Mass Storage Device Configuration section of my BIOS setup menu there is a line that reads USB Mass Storage Reset Relay [20 sec] and then there are 3 other options that are either 10 sec, 30 sec, or 40 sec.  Maybe I need to change the time for the external drive?  Maybe I need to have it off of 

Device #1 Maxtor 3200 [auto] and have it be [hard drive] (side note I think I had it set to hard drive when I booted and it froze/I was too impatient to wait a minute and thought it froze)  

I am going to go try seeing if unplugging the external HDD when booting eliminates the one system beep and I will get back.  Although the problems in Ubuntu about my RAM and CPU sometimes getting maxed out for no reason are odd and I do not know if it is Ubuntu or my MB, RAM, and/or CPU.  Even if I can fix the thing where the booting past the BIOS screen takes awhile or it freezes that still doesn't seem to fix the things that are happening in Ubuntu.  Ubuntu was working perfectly fine w/ everything and the only thing that changed was my MB and my PSU, so I think that the MB is the culprit of the Ubuntu issues.. maybe I just need to reset the CMOS and flash the BIOS to the latest revision.

---

### Post by bastiegast on 2007-03-25
> **Ubunted said:**
> If at first it drives you nuts, do what I do - format the drive, take it apart, clean it up and start again.

LOL?? Im not sure what your refering to with "it" but taking your harddrive apart was hopefully meant sarcastically?

---

### Post by billdotson on 2007-03-25
please don't abandon this thread.  Don't forget me please!

---

### Post by futz on 2007-03-25
> **billdotson said:**
> please don't abandon this thread.  Don't forget me please!
Hehehe! Relax Bill. :mrgreen:

I haven't read everything that others have posted, but I wouldn't bother flashing BIOS. It should work without doing that.

Strip it down to just the mainboard in the case, with a video card, RAM, power supply and your main hard drive. 

Then go through your BIOS settings with a fine tooth comb. What you may have to diddle with is getting all your clock rates and possibly voltages set right. Sometimes AUTO just doesn't get it right.

Please tell me the make/model# of your mainboard, RAM, what CPU and any other information you think pertinent. I'll get manual and specs and go thru it and see if you should be changing some BIOS settings away from AUTO. Also, tell me exactly what the computer is doing that's bad, and when/how it does it.

You've been mentioning emi (electromagnetic interference) as a possible problem. Forget that. That aint it, unless you've done something incredibly strange. Once that mainboard is screwed (grounded) to that backplane, emi just isn't an issue anymore. It really isn't an issue even with the mainboard out in the open - they're very well designed.

> every time my PC is rebooted/booted the system does a single beep before going to the blue Asus BIOS screen
Perfectly normal. Unless it's a long beep. One short beep is to let you know it's successfully finished POST (Power On Self Test).

> I usually use the reddish non-conductive washers for those incase the heads of the screws overlap a bit.
Bullcrap. Totally unnecessary. Those screw pads are plenty big, and the screws are not going to touch traces unless your screw heads are huge. You want the mainboard grounded at those screw pads. I don't know why they still include those washers with hardware packages these days - just tradition, I guess. Haven't used em in many many years.

---

### Post by billdotson on 2007-03-26
Well I looked and here are the things associated w/ the two latest BIOS versions:


All OS 
Version 0910 2007/01/23 update 



Description P5B Deluxe release BIOS 0910
1. Update Jmicron option ROM to 1.06.59
2. Fix AC Power loss function not correct
3. Support x4 DIMM
4. Moidfy Write to Precharge Delay default from 10 to 11
5. Enable support for EIST under VISTA
6. Finetune Q-Fan rule
7. Support SLP 2.0
8. Fix BBS device string not correct under AHCI mode
9. Enable Disable USB capability
10.Support ASUS WIFI-TV card
11.Revise CPU temperature calculation algorithm for PECI

and 


All OS 
Version 1004 2007/01/26 update 



Description P5B Deluxe Release BIOS 1004
**Please update AsusUpdate to V7.09.02 or later prior making this update.**
**This BIOS does not support roll back to older BIOS**
1 Enhance memory compatibility
2 Support CONROE E0 CPU(FSB 1333)

I don't really know if any of these are relevant enough that I should flash my BIOS to one of them but if they are not then how should I go about resetting to the defaults? Should I just go into the BIOS settings and say load defaults or should I open up the case, pop the CMOS battery out, move the motherboard jumpers from 1+2 to 2+3 (this is how you are told to reset the CMOS in the manual) leave them on for ~10 seconds and then switch them back and pop the CMOS battery back in. Then go in and change the settings I need, like disabling onboard wi-fi, onboard sound, etc.?

Also, I have another question.. it probably isn't that much of an issue but just to make sure.. I have two SATA devices hooked up to the MB, a SATA HDD and a SATA optical drive. I have the HDD hooked up to SATA port 1 and then the SATA DVD drive hooked up to SATA port 3, should I have the devices in order of how the BIOS recognizes them (as in the BIOS it shows SATA devices as HDD on SATA port 1, nothing on SATA port 2, the optical drive on SATA port 3 and nothing in SATA ports 4,5 and 6) should I have it so the DVD drive is right after the HDD on SATA port 2?

My motherboard is an Asus P5B Deluxe/Wi-fi AP edition, CPU is Intel Core 2 Duo E6600 (NOT overclocked; at default) 2GB dual channel Corsair XMS2 PC6400C4 DDR2 RAM (says it is compatible in the MB manual I am almost cetain), an nVidia 7800GT 256MB PCI Express x16, Creative Soundblaster Audigy 4 (non-pro), a large copper Zalman CPU fan/heatsink, a Lite-On DVD+-RW SATA drive, an IDE LG Super-multi burner (DVD+-R/RW,CD+-R/RW [almost certain on the CD stuff])  The manual on Asus website.  I would give the link but the site is not responding right now. 

The issues w/ my PC are that the PC has frozen at the BIOS recently.  I RMAed my MB and PSU because my PC would freeze on the BIOS screen about half of the time regardless of whether it was a cold OR a warm boot.  I would have to restart the PC to get it past the BIOS and sometimes it was even bad enough that I had to actually turn off the surge protector, turn it back on and then start up the PC again.  So (last) Tuesday I put my PC back together w/ the replacement MB and PSU.  
Here are the things that I have done that are relevant to my issues:

Turned on the PC got a system beep.  I had plugged the CPU fan into a chassis fan connector instead of the CPU fan becasue I thought that the CPU fan connector was for 4-pin only (I didn't know I had done this at the time).  I went into the BIOS and told it to reset to defaults.  Then I booted into Windows and rebooted.  I got the same error so I researched it and then opened the PC up and moved the fan cable to the CPU fan connector.  I did NOT reset to default again after doing this.

Then that night (Tuesday) I turned off the PC (not completely, didn't flip the switch on the PSU to off).  Wed. I turned the PC on (I had one external device connected when I booted and that was an external USB2.0 Maxtor 3200 [7200RPM] HDD) and the PC either a) froze at the BIOS or b) took so long (probably over 45-60 seconds) that I thought it had frozen.  Iwas INCREDIBLY frustrated because this was the same thing I had gotten replacement MB and PSU for.  Although, that day I probably rebooted 4-5 times with no such errors.  

Wed. night I turned the PC off and unhooked the external HDD (to see if it was the external HDD) and then Thurs. morning I turned it on.  It did not freeze and took about ~10-15 seconds to get past the BIOS screen and go on to booting an OS.  So I thought it must've been the external HDD.  

Thurs. night I plugged the external HDD back in and then powered down the PC.  Friday morning I booted up and it didn't freeze but did the same thing that it has done when the external HDD wasn't plugged in.

So Friday night I turn it off w/ the external HDD in and Saturday morning booted up.  Did the same thing as Thurs. and Fri. morning.

I powered down Sat. night and I cannot remember if I left the external HDD unplugged or not but regardless the result was the same as the past few mornings where it would take ~10-15 seconds to boot past the BIOS screen.

Last night (Sunday) I powered down the PC, unplugged the external HDD, and then flipped the PSU switch to off.  Today I switched the PSU back on and powered up and it booted past the BIOS almsot instantaneously, probably ~1 second.  

So even though in about a week it had only frozen on a boot once it still concerns me as that was the issue that I had sent off for replacement MB and PSU, although this is not NEAR as bad.  This has only happened once and only during a cold boot after being off for ~8 hours.  The issue I had before the replacements would freeze about half of the time regardless or whether it was a cold boot or a warm boot/reboot.

Also, I have noticed an odd thing in my BIOS, on my old MB my CPU cores where shown with the first core having 4096KB of cache, and the second core having 32KB of cache but on this new MB the cores are switched in regard to the cache.  In Ubuntu I also noticed that instead of the first core acting as the primary core like with my old MB the second core seems to be the dominant core now (to clarify- the core that is used if a program is not multi-threaded).

Also, I do not know if this has to do w/ Ubuntu or the BIOS but in Ubuntu a couple days ago the following things happened:

I booted into Ubuntu, opened Avidemux, edited a video and encoded/transcoded the video and then shut down Avidemux.  Then I tried to see the properties window of the video I had just finished.  I had to wait for a long time before it opened so I opened the system monitor and ALL of my RAM AND SWAP was being used.  There were no processes taking up that kindof memory at all.  The next day I did the same thing except instead BOTH my CPU cores were maxed out for no reason.  Also, in Windows when I tried to shutdown Windows it froze an I just had to shut down manually, although it might've been (and probably was) the fact that I had Visual C# Express 2005 Studio installed and it was probably causing problems.  See this thread to see what it was doing specifically if you want: [http://ubuntuforums.org/showthread.php?t=393249]("http://ubuntuforums.org/showthread.php?t=393249")

Thanks man.  Sorry for the LOOOOONNNG reply; though I feel the information is neccesary.  Again, thanks again!

---

### Post by futz on 2007-03-26
I know the mainboard well. The box 3 computers over from this one has one in it.

Reading your message now....

---

### Post by futz on 2007-03-26
> **billdotson said:**
> I don't really know if any of these are relevant enough that I should flash my BIOS to one of them
I still say don't worry about flashing the BIOS, unless you know you have a specific problem that is addressed in one of the BIOS updates. Your hardware is pretty mainstream. It's unlikely a BIOS update is needed, and tho it's minimal, there is always some risk in a BIOS flash (unless you have dual or quad BIOSes, which eliminates the risk). 

> **billdotson said:**
> Should I just go into the BIOS settings and say load defaults or should I open up the case, pop the CMOS battery out, move the motherboard jumpers from
I've never had good luck with the "Load Defaults" BIOS command. You're much better off learning to set your own settings. Defaults only work if your setup matches what they picked for defaults. Pretty often it will work. Sometimes it won't.

You don't need to clear your bios unless you can't get it to POST for some reason (cough-BIG-overclock-cough). There's no point in doing that when you can still get to it and change things normally.

> I have two SATA devices hooked up to the MB, a SATA HDD and a SATA optical drive. I have the HDD hooked up to SATA port 1 and then the SATA DVD drive hooked up to SATA port 3, should I have the devices in order of how the BIOS recognizes them (as in the BIOS it shows SATA devices as HDD on SATA port 1, nothing on SATA port 2, the optical drive on SATA port 3 and nothing in SATA ports 4,5 and 6) should I have it so the DVD drive is right after the HDD on SATA port 2?
Doesn't matter. Put em wherever you want.

> Turned on the PC got a system beep.  I had plugged the CPU fan into a chassis fan connector instead of the CPU fan becasue I thought that the CPU fan connector was for 4-pin only (I didn't know I had done this at the time).  I went into the BIOS and told it to reset to defaults.  Then I booted into Windows and rebooted.  I got the same error so I researched it and then opened the PC up and moved the fan cable to the CPU fan connector.  I did NOT reset to default again after doing this.
The beep you got there was a CPU fan failure alarm. No need to change anything in BIOS for that. Just plug it in correctly and go.

---

### Post by futz on 2007-03-26
> **billdotson said:**
> 2GB dual channel Corsair XMS2 PC6400C4 DDR2 RAM
Is it TWIN2X2048-6400C4, with timings of 4-4-4-12?

---

### Post by Feenix3k on 2007-03-29
NOt for me...


I enjoy building my own system because you pick each part that goes in. So you know what you are getting.:-P

---

### Post by billdotson on 2007-03-29
Well Futz finally helped me get everything right.  Thanks Futz.


Yes I prefer building my own PC as the satisfaction of saying "Yes, I built it" is pretty good.  Also, if I have a problem I can open it up and look at it and move stuff around easily instead of having to call Dell or HP about stuff.  Also, I probably saved money on it if you compare the price of what I paid for mine with a Dell, HP or IBM with the same specs.

Also, you learn alot more when you build your own.

---

