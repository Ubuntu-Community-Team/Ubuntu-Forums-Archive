---
title: "Can anyone help me w/ a Windows issue??"
date: 2007-03-25
forum: Windows
---

### Post by billdotson on 2007-03-25
I just put my PC back together (with my replacement MB and PSU) and I have been using Windows XP SP2 as my OS because Ubuntu will now not work w/ the internet.  So today I tell Windows to restart and it goes to the blue Windows screen and says the "Windows is shutting down" line.  I sit there and wait.  I leave it for ~5 minutes and it still says it is shutting down.  It does not say it is installing updates or anything like it would if it had system updates.  I wait for ~5 minutes and just shut it off manually because it wouldn't shut down.  

Windows has been working fine for me and the only other time it has done this freezing while shutting down was when I was screwing w/ the registry (when I had my old MB and PSU).  Wehn it messed up then though it would freeze everything I tried to shut down, but this isn't doing that AFAIK (see paragraph above).  I get it reformatted and put it back on here and now have a replacement MB and PSU and as I have stated earlier it froze.  I had the Zenwalk Linux CD when I told Windows to restart so I do not know if that was an issue.  I booted back into Windows (didn't sign in) and took out the CD and told it to restart.  Windows didn't take as long but it took about 30-60 seconds which I assume is normal.  I know I have no viruses or spyware as I keep the scanners going and always up to date.  

Isn't it weird that I wouldn't get a disk check before going to the Windows login screen if I had turned it off in the middle of a restart?  AHHHHH this is making me angry.. Ubuntu won't connect to the internet Windows started acting stupid and doesn't want to shut down.. AHHHHH

This Windows install is only about a month old and I shouldn't be having problems of this magnitude, especially since I do not have any viruses, spyware/adware, do not go to sketchy sites and HAVE NOT done anything internally such as editing the registry. 
This sucks.  If Windows stops working I have got to completely reinstall everything and then I won't have an OS at all really because Ubuntu won't even connect to the internet right now. 

I am going to try and restart and shut down from within Windows (after I login) and see if it freezes again.  ARGGGH

Interesting.. I just tried to open Word and I got a dialog box saying that it is looking for vcssetup.msi and cannot find it.  I installed Visual Studio a couple days ago but it wasn't installed using an .msi it was a package/.exe from Microsoft.com.  COuld a corrupt visual studio cause shut down problems that severe?

---

### Post by aysiu on 2007-03-25
Not sure what to tell you except that maybe when you do have a working Windows installation (and a working Ubuntu one, for that matter), you can image the partition with PartImage or Norton Ghost, so that you can restore the working version easily instead of doing a complete reinstall.

---

### Post by ezphilosophy on 2007-03-25
Well, as you are posting on these forums, I think I and most other users would like to know the details to why you cannot connect  to the internet with Ubuntu.  What are you using?  Broadband?  Modem?  Router?  Do you need a username and password?  If we can work that out for you, then maybe you don't need that windows install at all.  :)

EDIT:  I just noticed your bean count and can assume you have been around the forums a bit.  I'm surprised that you have let an Ubuntu install exist without being able to connect to the Internet.

---

### Post by timcredible on 2007-03-25
the fix for windows problems is to erase it and install linux.  if you're having issues connecting to the internet with ubuntu, we can probably help you fix that.

---

### Post by billdotson on 2007-03-25
I know the general response is going to be use Linux but I play many PC games and there are things like my favorite firefox extensions that do not work in Linux, I can't burn or format CDs or DVDs for some reason (using Gnomebaker) and there are some other things like getting dual screen setup.. which in Ubuntu has been less than helpful.  Also, my bean count is mainly when Ubuntu actually could connect to the internet, after I put my replacement MB in it just quit.
It is so weird, the Visual C# 2005 Express Studio kept saying it was being configured and installed anytime I tried to open MS Word and kept asking for the vcssetup.msi, but the thing was the installer for it was from Microsoft's site and it was vcssetup.exe, NOT .msi  I uninstalled it, the 2005 express redistributable, and the XNA game studio and now if I open Word it doesn't do that anymore.  

I need Windows to work because I have ~20 games on Windows.. almost all of them do not work in Linux at all.  Why in the world is it freaking out?  WOuld having the Zenwalk Linux CD in while shutting down freak it out that badly?  Could it have been an error in Visual C# Express 2005?  Argghh if Windows messes up I have no OS and to reinstall Windows I have to take it up to the university because the university installs the OS for my PCs under some sort of redistribution license.  

Everything I have been doing lately is annoying and very frustrating.  My PC kept freezing at the BIOS so I sent off for a replacement MB and PSU.  I wait 2 weeks for it to come back and am hoping to get it back together and have my PC back.  But guess what? Ubuntu quits working, my CPU cores are switched in the BIOS (core 1 has only 32KB of cache, and core 2 has 4096KB.. it was the other way around on my other MB [I have a Core 2 Duo E6600])  My computer either froze up at the BIOS or it took so long (around a minute) to get past it I just had to shut it down (I do not know if it would've gone past the BIOS screen if I had left it for a bit longer) and now this crap w/ Windows freezing on shutting down for absolutely no apparent reason.  

AHHHHHH

---

### Post by aysiu on 2007-03-25
Let's keep this thread to Windows help.

If you want to help billdotson with the internet in Ubuntu, do so in this thread:
[Cannot connect to internet in Ubuntu](http://ubuntuforums.org/showthread.php?t=389615)

---

### Post by smoker on 2007-03-25
hi, Bill,

maybe a silly question, but did you install the motherboard drivers usually supplied with a new motherboard? also, if you have a sata harddrive, xp usually requires drivers for that during install,

best of luck

---

### Post by Stew2 on 2007-03-25
Hello billdotson, I am not really sure if I am following everything right so please correct me if I am wrong. Your PC was locking etc. so you sent the mobo and PSU back for replacements. You got the replacements and installed them and it is now locking at the bios or crashing windows? Just out of curiousity, did you reinstall Windows after replacing the mobo? Or was the new mobo identical to the previous one? I replaced a mobo once and tried to use the preexisting install of Windows on the harddrive, it loaded occasionaly but was very erratic and prone to locking up. As my new mobo was different than the one that I had originally installed Windows on, it would not work properly... I had to do a fresh install and that solved the problem.

The only other thing I can really think of is possibly the ram. If it is locking at the bios, and it did on the other board too I would suspect faulty ram. If it was a hard drive problem it would not lock at the bios and it is highly unlikely that you have had 2 bad/corrupted bios's. If you have two sticks try removing one and rebooting and see if you still have the same problem? Alternate the sticks in case the one you left in the first time was a bad one.

Hopefully one of these suggestions will help or solve your problem for you. I am not an expert by any means though, just a hobbyist who puts together his own systems, so dont take my suggestions as gospel or anything :). I hope you get it sorted... sounds like its giving you a lot of grief. Relax and take deep breaths :D .

Good luck,
Stew2

---

### Post by BuffaloX on 2007-03-25
From what you describe, soo many things could be the cause.
You don't give much to narrow it down, but here are some general things you could check:

If your hardware isn't "proven", you could have a hardware problem.
To ensure all connections are good, you could disconnect everything, one thing at a time, and then reconnect it, making sure everything is connected properly.

Second you may have HDD problem, Try to enable smartdrive if it's not already enabled.
You could also have a heat problem, try to start your PC with the case open, and see if all fans are working, and if it increases stability to run with the case open, you definately have a heat problem.

Third, you may have buggy software installed. Some virus scanners are really bad.
Especially Norton and mcaffee are known to cause weird errors.
Also Visual studio may mess things up, especially if you use older version.

You may want to try a roll back, or uninstall your virus scanner, visual studio, and other software, that interfere with how Windows Work. Btw you write scnner**s** you should only use ONE scanner at a time, since they may interfere with each other.

Happy debugging.
I'm so happy I don't have all those nasty extra problems any more...  :biggrin:

---

### Post by BuffaloX on 2007-03-25
> **Stew2 said:**
> did you reinstall Windows after replacing the mobo? Or was the new mobo identical to the previous one?

Sure, If it's another MOBO Windows rarely works without reinstallation.
But then you may have a license problem with your Windows. :-&

---

### Post by billdotson on 2007-03-25
No my replacement motherboard is exactly the same model as the previous one.  By replacement I mean I got the motherboard RMAed, as it was only 5 months old (as with everything else w/ my PC).  I (actually the university tech support center) installed Windows when my PC was using the old motherboard.  The only thing that is different about the MBs is that they have different BIOS revisions.  The last one had 0507 which I flashed to the latest something like 1004 before RMAing it.  This MB has revision 0704 or something like that.  I installed all of the drivers using the CD from my last MB, the one I got RMAed.  I will try installing the drivers from the CD that came with this one to see if they are different.  

To make a correction, my Windows XP install isn't being erratic and crashing often.  It was just that today when I had the Zenwalk Linux CD in the drive and told it to reboot it got stuck at the shutting down Windows screen.  I then booted into Windows and immediately restarted at the login screen.  Then I logged back in, got on firefox and started typing up this post.  Then when I tried to open MS Word a dialog box came up saying configuring Visual C# 2005 Express Studio and then another popped up and said that the installer file vcssetup.msi could not be found.  I found that odd because I installed it using an .exe, the .exe that came straight from MS site.  So I started that .exe and told it to repair.  Then it said I had to reboot to finish.  I rebooted and it took only 20-30 seconds to shut down Windows and start the reboot.  

So then I went to try and open Word again and it did the same thing.  I was really angry so I just uninstalled Visual C# 2005 Express, Visual C# 2005 Express redistributable, and XNA game studio.  Then I rebooted again and it started rebooting after ~25 seconds (meaning from the shutting down Windows screen was up for that long) and opened Word.  No Visual C# Express dialog boxes.  Btw, the Visual Express dialog boxes would not let MS Word open until I either canceled them ~4 times.  I suppose if I could've found a vcssetup.msi I could've installed it and got it to work, but I could find no such file on the internet.   I have AVG free 7.5 and Spybot S&D with the latest definitions installed for both.  I generally do not use both of them to scan at the same time although I probably have done it once or twice, but not anytime recent.  I guess I assumed that a spyware scanner and a virus scanner wouldn't interfere with one another.  I only have Spybot S&D and AVG Free 7.5, so I don't have more than one virus scanner or anything as I know that having more than one can cause some issues.  

The only time I have noticed the BIOS to freeze is once.  I put back my PC Tuesday, and ran it Tues., turned it off all night and then turned it back on Wed. and it froze at the BIOS screen.  Either that or it was just taking a long time (longer than 45+ seconds) and would've eventually booted past into the POST but regardless after about 40-45 seconds I turned the PC off.  Before I RMAed my old motherboard I ran memtest86 long enough so that it would do 5 complete checks on my RAM.  My RAM passed all 5 times w/ no errors (I was using the memtest86 that comes w/ the Ubuntu install).  Thurs morning I turned it on W/O the external HDD plugged in and it booted fine (all the mornings I turn it on it has been off all night) and only took 15-20 seconds max to get past it.  Friday morning I turned it on w/ the external HDD plugged in and it did the same thing 15-20 seconds.  

I doubt I have a license problem w/ XP as before I got this replacement board I was able to install IE7 (which requires the WGA).  If I had a license problem wouldn't many other things not be working correctly?

Also, I do not think I have a heat problem as my MB stays @ about 80 Fahrenheit and the CPU at 92 Fahrenheit.

As I said earlier before I got a reinstall of Windows (the one I am using now) it would freeze at EVERY shutdown/restart.  Of course it was probably me changing a couple things in the registry that were supposed to increase RAM performance.  It is weird though because it kept doing that even after I changed those values back to what they were. 

Thanks for your help.  I hope I can get all of this sorted out as it is quite frustrating.  It would be different if it wasn't my main machine that I do stuff on.  If it was a secondary or something I would actually probably have fun trying to troubleshoot it, but when I want to get something done and my main PC isn't working I get MAD. 

Also, if you want to help w/ my Ubuntu internet and other issues I have a ticket on launchpad which is #4323 or follow the link: [https://answers.launchpad.net/ubuntu/+ticket/4323]("https://answers.launchpad.net/ubuntu/+ticket/4323")

Thanks again.

---

### Post by BuffaloX on 2007-03-25
Reading your above post, one thing comes to mind.

After upgrading BIOS, you should enter CMOS and load default settings.
If you forgot to do that, it can cause instability, Even if you configure all settings correctly.
If you have ports enabled, that you don't use, then disable them, to free their resources for other hardware. ( serial and parallel ports are usually enabled, but rarely used.. )

For now that's all I can think of...
Good luck.

---

### Post by billdotson on 2007-03-25
So I should flash my BIOS to the newest revision and then go into the BIOS setup and reset to defaults?  THen after that go through and disable the ports I do not use such as the PS/2 mouse and keyboard ports, the S/PDIF port, onboard wi-fi, onboard HD audio and the serial port?  So I shouldn't clear my CMOS with the MB jumpers and take the CMOS battery out?  Just upgrade to 1004 or whatever the version is and then reset to defaults?

---

### Post by BuffaloX on 2007-03-26
You could see if there are any relevant fixes in newer versions, and update if you think it could help.

You don't need to clear CMOS or update it, just load default settings.
And then configure.

---

### Post by billdotson on 2007-03-26
Well I looked and here are the things associated w/ the two latest BIOS versions:

 	
 All OS 
 				 Version	0910	2007/01/23 update 



 Description	P5B Deluxe release BIOS 0910
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
 				 Version	1004	2007/01/26 update 



 Description	P5B Deluxe Release BIOS 1004
**Please update AsusUpdate to V7.09.02 or later prior making this update.**
**This BIOS does not support roll back to older BIOS**
1 Enhance memory compatibility
2 Support CONROE E0 CPU(FSB 1333)

I don't really know if any of these are relevant but if they are not then how should I go about resetting to the defaults?  Should I just go into the BIOS settings and say load defaults or should I open up the case, pop the CMOS battery out, move the motherboard jumpers from 1+2 to 2+3 (this is how you are told to reset the CMOS in the manual) leave them on for ~10 seconds and then switch them back and pop the CMOS battery back in.  Then go in and change the settings I need, like disabling onboard wi-fi, onboard sound, etc.?

Also, I have another question.. it probably isn't that much of an issue but just to make sure.. I have two SATA devices hooked up to the MB, a SATA HDD and a SATA optical drive.  I have the HDD hooked up to SATA port 1 and then the SATA DVD drive hooked up to SATA port 3, should I have the devices in order of how the BIOS recognizes them (as in the BIOS it shows SATA devices as HDD on SATA port 1, nothing on SATA port 2, the optical drive on SATA port 3 and nothing in SATA ports 4,5 and 6) should I have it so the DVD drive is right after the HDD on SATA port 2?

---

### Post by BuffaloX on 2007-03-26
Those BIOS updates are VERY relevant, since they both address RAM compatibility.
The pre 910 seems to be almost beta stage.
I would definitely go for the newest version.
Because it improves RAM compatibilty. I could also suspect that there is a little more to that update than what they say.

Removing battery, or clearing CMOS with jumper, and updating BIOS, all require you to load default settings afterwards. You do this from the BIOS/CMOS menu, there should be a setting called
Load defaults or something very similar.

It doesn't matter with the SATA devices, you should be able to connect them any way you like.
You could have Optical drives first if you want, but I would personaly not like that, because of old habits. :lolflag:

---

### Post by billdotson on 2007-03-26
so should I just do load defaults then flash to the 09-- version and then after that do load defaults?

Also, I have a question that I think might me pertinent to my issue.  I unplugged the internal HDD when I installed GRUB to the MBR of my external HDD and Ubuntu to my external HDD.  I have heard that the BIOS trying to see 2 MBRs can freak it out.  Could this be my issue?  Should I just unplug the HDD I am not going to be using when I boot?

---

### Post by BuffaloX on 2007-03-26
> **billdotson said:**
> so should I just do load defaults then flash to the 09-- version and then after that do load defaults?

Yes.

> **billdotson said:**
> 
Also, I have a question that I think might me pertinent to my issue.  I unplugged the internal HDD when I installed GRUB to the MBR of my external HDD and Ubuntu to my external HDD.  I have heard that the BIOS trying to see 2 MBRs can freak it out.  Could this be my issue?  Should I just unplug the HDD I am not going to be using when I boot?
[/QUOTE]

I have Never heard of that problem, sounds a bit illogical.
The BIOS should just boot the drive you have selected as primary boot drive.

---

