---
title: "can't install XP"
date: 2008-02-20
forum: Windows
---

### Post by edgranholm on 2008-02-20
I have a big problem.  My laptop froze, and then all of a sudden shut off a while back.  It had been sitting idle for a little while, and then when I go to get on it, the screen freezes, and then it goes black with some tiny orange vertical lines and then shuts off.  When I tried to turn it back on, it would freeze at the Windows logo and do nothing.  I had no system recovery nor recovery discs at the time, so I managed to used my wife's XP disc to install on here long enough to get my files off, but for some reason, none of the usb ports would work.  I had to use a PCMCIA  USB/firewire card to transfer my files to an external HDD.  After I got all that done, I decided I'd give ubuntu a try.  It was my first time to ever use Linux, and I must say, I've really been enjoying it.  However, my USB ports still don't work.  I also really need to get XP back on here, because of my music recording and gps usage needs, among other thing. 

 I was able to purchase some recovery discs from Acer, but they won't load up.  I also even tried a pirated copy of XP but that wouldn't load up either.  It would just freeze at the blue screen when it says "setup is now starting windows" or something similar.  When using the recovery discs, it freezes after the setup progress bar goes all the way across and then says "please wait".  I've tried these discs on my wifes computer, and they load up like a charm.  

I've also tried to wipe the HDD clean, but every program I've used on the Ultimate Boot CD freezes at around 10% or so and the computer abruptly shuts off.

I can't understand what the problem is, since my wifes Dell XP HE burnt back up disc will work perfect, and ubuntu will work perfect, but nothing else will.  I also can't figure out why my USB ports won't work.

The computer is an Acer Aspire 5100-5022 laptop.  The original OS was XP media center edition.  I'll gladly give any more info that may be needed.

I'm at a loss, and very frustrated.  I'm extremely happy with Ubuntu, but I unfortunately need XP too.

Anybody got any ideas of how to resolve this?

---

### Post by metallicamaster3 on 2008-02-20
Sounds to me like your hard drive died... Sorry dude :-\

EDIT: Well perhaps not. If Ubuntu was able to get installed, then maybe there is some hope. Try to use Ubuntu to install GNOME Partition Editor. Then, set a new disklabel. This will wipe your drive "to the second degree" so to speak. Then try to install Windows.

This _**WILL**_ erase everything on your hard drive.

---

### Post by SunnyRabbiera on 2008-02-20
Pirating?
No wonder why you have issues.
maybe you should buy the real thing, I know XP is a drag but you might as well get it legit.

---

### Post by metallicamaster3 on 2008-02-20
I wouldn't say that... I know pirating is looked down upon but I've never had any problems with the ones I've downloaded. As long as you download the 'good ones', if you know what I mean.

---

### Post by edgranholm on 2008-02-20
I'm not trying to use pirated software.  I'm trying to use my legal recovery discs that came straight from Acer.  I just tried using the other copy to see if it would give me problems too.... it's called troubleshooting.  

The only hardware issues I have in Ubuntu is my USB ports not working.  No HDD issues that I'm aware of.  I'm typing this on the same computer I'm talking about, running Ubuntu.

I installed the GNOME Partition editor, but can't seem to find where it is :confused:

---

### Post by metallicamaster3 on 2008-02-20
It's under System --> Administration ;)

Also: Ubuntu could be fine, it could be a bad part of the hard drive that Ubuntu is not touching... perhaps Ubuntu is on the 'good' part of the hard drive, while XP is taking the 'bad part'.

Understand?

---

### Post by edgranholm on 2008-02-20
Found it :rolleyes:, and I understand.

So, setting a disklabel will completely erase the HDD and get it ready to install a new OS?

---

### Post by metallicamaster3 on 2008-02-20
If you only want one partition, yes. Use the GNOME Partition Editor to create partitions.

---

### Post by edgranholm on 2008-02-20
Thanks, I'll give it a shot.

---

### Post by metallicamaster3 on 2008-02-20
Glad I can help :)

---

### Post by edgranholm on 2008-02-21
Unfortunately (assuming that I did it correctly), setting disklabel didn't work. :(

---

### Post by metallicamaster3 on 2008-02-21
Ah crap. I'm still big on thinking you're hard drive has failed.

---

### Post by edgranholm on 2008-02-21
very possible.  Still can't figure out why my wifes Home disc will work, but my MCE disc won't.

Also, something else I should mention...  I noticed that while I was running the ultimate boot cd, no matter what program was being used, after it had ran for so long the computer would just shut off.

---

### Post by metallicamaster3 on 2008-02-21
Hmm, could also be a power supply problem. This happened with an old thinkpad I have, the power rail came loose.

I'd take it to a shop and let professionals take a look at it, and potentially fix the issue.

---

### Post by edgranholm on 2008-02-21
That's probably going to be my best bet, since nothing that I've done has come close to fixing it, and I'm not comfortable with opening up a laptop.

---

### Post by Northstorm1x on 2008-02-22
Sounds like your MBR might be screwed up

Insert the Windows XP Install CD and reboot the computer.
When “Press any key to boot from CD” appears, press any key.
When the “Welcome to Setup” screen appears, press”R”to enter the Recovery Console.
When asked which Windows installation to log onto, enter the number for the correct Windows install, then press”Enter”.
Type the Administrator password or just press”Enter”if there isn’t one.
Type”FIXMBR”and press”Enter.
It will ask if you are sure you want to write a new MBR. Type”y”and press”Enter”.
It should say “The new master boot record has been successfully written”. Type”exit”and press”Enter”to reboot the computer.
Insert the Windows XP Install CD and windows should install
Remove the Installation CD as soon as the computer powers up so it won’t boot from the CD again.
The computer should now boot into Windows

---

### Post by edgranholm on 2008-02-22
Already tried that, and it didn't work at all.  Problem is, my install disc won't even get that far.  It freezes before you have the option to go into the recovery console.  The only way I was able to do it was to use my wifes disc.  Either way, it doesn't work.

---

### Post by Northstorm1x on 2008-02-23
must be hardware problem then. ( HDD,PSU, or Mb.)
Good luck :)

---

### Post by rickyjones on 2008-02-23
I'm going to chime in to say that it is most likely a hardware problem. It could be a motherboard issue. A repair shop is most likely in your future.

-Richard

---

### Post by derek72 on 2008-04-30
I have a Aspire 5100 and the same XP issue has occured. I've switched to Ububtu (8.04) and it works great, except I can't get the USB ports to work - anyone know how to get them working?

---

### Post by Battie on 2008-04-30
Is the fan cranking hard when this happens?  Or is it not running at all?  Is the laptop unusually warm?

Some laptops will shut down abruptly as a safety measure when they overheat.  This becomes more of a problem as they get old and dusty.

My old laptop pulled that stunt a few times in Windows, with no errors.  But when I got Kubuntu on it, before shutting off it was kind enough to report that the critical temperature had been reached.

And if that's not the case--

While the HDD might be a victim of whatever's going on, I very much doubt it's the primary issue.  I would expect a lot of random restarts, but shutting off and distorted screens leads me to believe it would be an issue with the motherboard or power supply.

If you can remove the hard drive and plug it into another system, use the UBCD to run a diagnostic on it.  If you don't have the adapter, take the HDD out anyway and run the Ubuntu live CD or the Windows setup CD for a while.  If you run into a freeze or restart, then you know the HDD isn't the culprit.

Good luck!

---

### Post by derek72 on 2008-04-30
No fan issue. It all started on day after plugging in the laptop when the power was low. Windows locked up and has never run again. I've tried to reinstall from CD and from the backup on the hard drive and they both lock up during setup. I ran Ubuntu from CD and it was fine, then I installed it and it runs great. Like I said the USB issue is my main concern because I can't use a flash drive or print. When I upgraded to 8.04 the SD Card became functional which helps a little. Does Kubuntu or the other Linux flavors have better luck with USB?

---

### Post by anantshri on 2008-04-30
one thing you can try 

it seems asif your harddisk is developping some bad sectors

try attaching it on some other laptop as external harddisk and run a chkdisk.

or you cna try one more thing from your ubuntu installation try running ntfsfix on your partition to fix any error it might have.

---

### Post by sbd on 2008-06-08
i think your problem can be solved in the bios. look at the legacy support for your hdd drive. change it to the opposing value. the xp install should work.

---

### Post by mac143_01 on 2008-06-10
try to remove and clean the memory of your machine with an eraser,.. then re install you os

---

### Post by vasa_gameboy on 2008-07-17
I have same problem. XP refuses to install. It freeze when saying starting windows. KNOPPIX vector-linux and ubunto installs ok but USB port are non working. I have an ACER 5102 laptop. My belivings are that when XP is trying to detect USB ports it freeze, While linux distros seams to have better errorhandling on this case. Can anybody confirm this teory? I haven't managed to get USB ports working under linux and any windows install freeze. I also tryed to boot the laptops HD in an desktop and then was no problem with the booting of XP.

---

### Post by Jim! on 2008-07-17
If you can't get the USB ports working in linux either then it COULD be a driver issue. I don't know if it would do anything useful but you could wipe your HDD with 'dban' (Dban Completely Erases All Data on a Hard Drive).

---

