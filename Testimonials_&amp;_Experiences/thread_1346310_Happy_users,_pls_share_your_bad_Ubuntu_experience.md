---
title: "Happy users, pls share your bad Ubuntu experience"
date: 2009-12-04
forum: Testimonials &amp; Experiences
---

### Post by ed-koala on 2009-12-04
I'd like you to tell the story of your worst new Ubuntu experience. But one condition ... you have to have not given up, ever, on solving the problem. And still be a happy Ubuntu user. :)

I wanted to post and ask this question so, hopefully, all the new users who are having a tough time with Ubuntu will see that no matter how bad it gets, it can all turn out well.

My story ...

Not so much a new user, but 9.10 had been out a few weeks, so I figured I'd give it a go. I've been around for a few distros by now and figured I knew what to expect and could figure out any issues. Yeah, right.

First bad choice, decided to go the upgrade route from 9.04. Upgrading has worked in the past, so off I go.  I download, install, reboot, and ... nothing. PC is a brick and won't boot.

Back to a Live CD of 9.04, reinstalled, got a 9.10 Live CD downloaded and burned. Booted up, installed, rebooted, and ... it still won't boot up. What???

Ok, back to 9.04. Time to do some research. Oh, AMD64, seems I should use the alternate install CD. Ok.  Download, burn, install, reboot, and ... nothing. Still a brick. Now what the bloody hell is going on?

Ok, Time to start eliminating possibilities. Check CDs for defects. Done. Check release notes for any known hardware issues. Done.

Ok, I've narrowed the problem down a bit, and I've noticed something new when installing, though I didn't think much of it at the time since it was detected automagically and I figured it was ok. My 2 hard drives were seen as one big raid array.  I know they are set up that way, so why is this a problem?

Time to start playing around with settings.  However, nothing I try with partitioning the drives makes any difference. I go through 4 more installations and still have yet to boot up my PC with 9.10.

If I had enough hair to lose, I'd have been pulling it out in clumps by now.  9.04 worked great. How can this possibly be so hard to get 9.10 to work?

More research (yes, this includes a number of posts here wondering what's wrong). Finally I find something. A boot/install option called nodmraid.

I set that, install, and viola! My PC boots, and everything works wonderfully!  Relief doesn't begin to cover that feeling.

A truly terrible couple of days making 9.10 work, but in the end worth it.  Still happy with Ubuntu despite that, and I've learned new things from my experience.

---

### Post by jrusso2 on 2009-12-05
I have not had any issues but I am not the early adopter type.  I learned after so many years in the IT industry if you have a working stable system leave it until you have to update then go with something tried and tested.

Last Ubuntu I used was 8.04 and had no issues with it.  Of course it was close to two months old before I installed it.

My Mac still runs Leopard not snow leopard and my Windows PC's you won't see any Windows 7 yet.

---

### Post by craig10x on 2009-12-05
9.04 has been rock solid for me....i didn't even install it until about two months into the release...to give them a chance to work out the bugs in the final release of it....and i plan to stay with it for the long term....

Though i may be tempted to go with 10.04 if reports are favorable...since it is a Long Term Release....but even there, i wouldn't rush to put it on immediately after it comes out....

If you want reliability and little or no trouble with Ubuntu, i think the CONSERVATIVE approach is best ;)

---

### Post by ElSlunko on 2009-12-05
When I had an ATI vid card back innnnn, must've been 7.04, I had trouble getting the proper resolution to work. Just went to the store and bought a cheapy Nvidia card and problems solved!

---

### Post by armandh on 2009-12-05
I am a happy Ubuntu user!

but not every where

mostly due to win only apps


I just gave [traded] a box with this intel MOBO
[http://downloadmirror.intel.com/15110/eng/D201GLY2_ProductGuide_English.pdf](http://downloadmirror.intel.com/15110/eng/D201GLY2_ProductGuide_English.pdf) 
about page 9 you will note an SiS chipset/video
9.10 worked well only to 800x600, earlier even worse
it is now running XP and a magic[win only]jack for others
the trade runs ubuntu A-OK

my work computer still has xp and quickbooks
and I pray for native linux QB

my son the gamer is still xp
but he is not my problem
as he can do his own re-install

my wife prefers 8.04 on her HP/compaq lap top
she hated vista's constant interruptions
thank-you devs 
for getting over the closed BCM driver issues.

the rest default boot to various ubuntu since 7.04 [my first]

---

### Post by RickReichert on 2009-12-05
For months I've had an older PC parked beside my usual PC desktop, wondering if I should use it for a Linux machine.  It's a Jetway 800mHz Celeron with 66mHz bus, 256mB PC133 SDRAM, HP 9100 series CDRW, 3.5" floppy, 12.6gB HDD, keyboard and mouse.  At one time it had Windows 98 installed, but at some point I uninstalled it and went back to DOS 6.2, thinking I'd eventually put Linux on it or just get rid of it. 

I also have a home network, with a Dell 1100 laptop (wireless) and Compaq desktop (wired) to provide simultaneous computing for my wife and I.  An HP PSC 2175 all-in-one printer is connected to the desktop via USB.

Since I'm now semi-retired and had some time to look into Linux, I did the usual Google search of "best Linux versions", etc., and finally decided Ubuntu was the best choice for me.  Even though my old desktop didn't meet the recommended minimum system requirements, I really wanted to start with a GUI to ease the transition from my Win XP experience, and I was curious to see if Ubuntu would even run on my old desktop.  I still do DOS command line things in Win XP when needed, and I thought I could revert to Terminal mode if the Ubuntu GUI just didn't work.

So on Dec 3rd I downloaded Ubuntu 9.1.0 Karmic Koala, verified the download and burned a CD.  I removed the printer, monitor, and ethernet cables from the Compaq and plugged them into the Jetway, and powered on.  Hit the Delete key to enter Bios setup, changed boot sequence to start with CDROM, saved and exited Bios setup.  Jetway lurched thru POST, then spun the CDROM.  It's alive!  The Ubuntu Live CD main screen appeared, giving me four choices.  I decide on the first choice (already hi-lited), to try Ubuntu from the Live CD.  I hit Enter.

At first, nothing happens.  I wait.  Ahhh.  A white Ubuntu logo appears, then begins to slowly pulsate.  I wait.  I wait.  Still waiting.  Screen goes black, then a mouse pointer appears.  I try the mouse - it works!  I wait.  I wait.  I wait.  Parts of the Ubuntu desktop begin to appear.  An orangish-brownish-whitish background appears, then top and bottom whitish bars, and finally the completed Ubuntu desktop.  So far, so good.  The first hour wasn't too bad, just required a lot of patience.  I realize that having only 256mB of RAM means that there is a lot of Swap Disk action going on, not to mention the CDROM access time.  This slows things down - a lot.  But it appears to be working.  I get the internet connection working - easy!  I try Firefox, no problem!  I check the printer - there it is!

I want to get rid of those multiple HDD partitions, so I try gparted.  I remove two partitions, no problem!  Now have just three partitions left: the original 2gB DOS partition, the Ubuntu 2gB Swap partition, and the newly-combined 8gB partition.  I'm thinking, this is too easy!  Time to install Ubuntu and order more RAM.

I first try to install Ubuntu from the Live CD desktop already open, but it doesn't seem to "take".  I wait.  I wait.  I wait.  Nothing seems to happen, no little circular animated icon appears, just seems dead.  I try to close out of the Ubuntu Live CD desktop, but nothing happens.  I wait.  I wait.  I wait.  Finally I push and hold the PC power switch for a hard power down.  Hmmmm.  I power back up, and again boot to the first Ubuntu Live CD screen with four choices.  This time I choose "install Ubuntu".  I wait, I wait, etc, etc.  Finally the Ubuntu desktop comes up, but so do several "Crash" pop-up windows.  It's clear that it hasn't installed.  ??? 

I'm thinking that because I previously uninstalled Win 98, Ubuntu is finding bits of code on the HDD and can't make sense of it.  OK, I'll delete the boot partition, too.  Back to gparted, delete boot partition.  Back to Live CD desktop, try to install Ubuntu, no joy, finally push power button to shut down.  ???

Hook monitor, ethernet, printer back up to Compaq desktop, go online, go to Ubuntu web site, look for help.  I'm thinking it can't be that the Jetway doesn't have enough RAM, it should still work.  I stumble across something about needing to have a formatted partition to be able to install Ubuntu.  Aha. 

Shut down Compaq, hook monitor, printer, ethernet up to Jetway, power on with Live CD, wait, wait, wait, get to Ubuntu desktop.  Go to gparted, format previously unallocated 2gB partition to ext2.  I go back to Live CD desktop and just for fun "mount" the newly formatted partition.  Then from the Live CD desktop, I clicked on the "install Ubuntu" icon.  Hey, something new is happening.  The Ubuntu install process starts! 

It is slow, but chugs away.  I answer the six questions, with time to eat breakfast, take a shower, get dressed, etc.  Did I mention this is a slow process on my Jetway?  Finally, after lots of waiting, I get to re-boot to Ubuntu without the Live CD.  It works!  Much faster boot-up, since CD access is not needed.  Still clunky and slow, but like greased lightning compared to running from CD. 

A program upgrade tab appears on the Ubuntu desktop.  I open it and find it wants to do 143 upgrades.  OK.  I start the process, have lunch, go to Costco, have a snack.  Ubuntu is done with upgrades.  I'm guessing the entire install and upgrade process took about six hours total.

I try several of the installed applications, all take time to come up but all work OK.

Next step is to order more RAM and maybe even upgrade the processor.  Pentium III's are cheap these days.  I'm really looking forward to exploring Ubuntu, finding software, and learning Terminal mode commands.  Ubuntu has breathed new life into a machine that was on the edge of going to a landfill.

---

### Post by plurworldinc on 2009-12-05
I love my Ubuntu boxes around my house , but the only little down side I have found so far was when i tried to install 9.10 onto my main desktop, just to have a blank screen that seems to just not work. 

   Right now i am just running 9.04, because it just works on my multi monitor system, but i will like to get 10.4 up and running before the LTS comes out which I am looking forward to running on my desktops and main system.

---

### Post by Irihapeti on 2009-12-05
I've been using Ubuntu for nearly 2-1/2 years. Karmic is the first release that I've had major problems with. I put it on an old Toshiba Satellite A10 laptop (date of BIOS c. 2003) and got the dreaded xserver lockup. I filed a bug report, did some tests and eventually discovered a workaround. I don't use the laptop a lot anyway and it has Hardy on it as well, so there was no major problem.

I ought to point out that Karmic is also the first version that I've installed immediately after release and I think that has a lot to do with it.

---

### Post by michaelzap on 2009-12-05
See the link in my sig for my story of Karmic tragedy and redemption.

---

### Post by armandh on 2009-12-06
Rick
yes more ram
you will likely get the install to fly too

I suggest leaving the space you want for ubuntu unpartitioned
when installing select "use largest unpartitioned space"

Ubuntu creates all the needed partitions and installs.
this always works as expected for me.

---

### Post by margazhang on 2009-12-06
Yes, I am a happy user of Ubuntu despite the problems I had when upgrading and clean installing Ubuntu 9.10 :-)

The most problems occurred on HP computers (AMD64 dual or tri core) with the HP w2207h widescreen flat-panel monitor because the required monitor Nvidia driver does not come with any of the Ubuntu installation CD - why?

I know this problem could be avoided by installing using a non-widescreen monitor and after installation is finished, then one could use the "System > Administration > Hardware Drivers" route to install the required Nvidia driver. After this, one could connect to the HP monitor and boot up the computer.

After searching Ubuntu forums, this thread helped me to install the Nvidia driver during the install:

[http://ubuntuforums.org/showthread.php?p=8448809](http://ubuntuforums.org/showthread.php?p=8448809)

Both users jeffus_il and darkod gave a way to install the Nvidia driver. I used what darkod suggested and it worked great! I could even use the method to get my installed Ubuntu Studio back to life (Ubuntu Studio alternative DVD used a text-based process to install and the display problem did not show up until the installation was finished).

The second most annoying thing had to do with sharing a printer over the home network. Samba did work but did not work all the times. Also samba tends to give an exclusive use to WinXP in Ubuntu (via VirtualBox); the shared computer cannot be used in local Ubuntu computer or any other computers on the network unless WinXP shuts down and VirtualBox is closed. I found the simplest way to get away from this problem is given here without installing Samba - this way of finding the IP-based address for the printer works the best:

[http://www.arjenkarel.nl/archief/10_share-cups-printer-in-ubuntu.php](http://www.arjenkarel.nl/archief/10_share-cups-printer-in-ubuntu.php)

You may wonder why I still use WinXP in Ubuntu via VirtualBox. Well, it has to do with the Simply Accounting software we use for our store - we have not found a good linux accounting software to replace Simply Accounting yet. If you know one, let me know. Thanks!

The third annoying thing in Ubuntu has something to do with getting USB work in VirtualBox.

I found that I had to repeat all the five steps I posted here on my own blog (so that I won't forget) each time I do a clean install:

[http://gain4you.net/217/run-windows-inside-ubuntu-linux-desktop-os/](http://gain4you.net/217/run-windows-inside-ubuntu-linux-desktop-os/)

There are other minor problems but all these problems can be resolved if one stick to this wonderful, free and secure linux desktop system and refuse to go back to Windows no matter what!

---

### Post by rahilm on 2009-12-07
Karmic isn't bad. It just gives you more opportunity to solve problems. While using karmic I always have a feeling that things will go wrong the next instant. That's why jaunty still remains my primary OS.

Still, I use Karmic. Its a part of life

---

### Post by slumbergod on 2009-12-07
Clean install to Xubuntu Karmic. Actually managed to fix all the bugs that annoyed me except for one (which seems to have broken again after recent updates...

Wireless...specifically, Intel 3945

When the connection drops the only way to get it back is to reboot the pc. Before the updates I could just restart the wireless kernel modules. Now even that has stopped working. 

I am happy with most everything else but I'd be super happy if wireless worked as well as it did with Jaunty.

---

### Post by AlanR8 on 2009-12-07
I'm just coming up to my 3rd anniversary as a happy *buntu user. 

First two and a half years I used Kubuntu and was a happy camper. I switched over to Ubuntu about six months ago because, IMHO, it's slightly easier to network and mount drives. That's important to me as I have six machines on the home network. Most of them are Ubuntu/Kubuntu apart from the wife's Dell Dimension that runs XP.

The issue that COULD have made me give up was getting the web cam to work on this Sony Vaio VGN-FZ21S laptop. I can safely say it took me two years to get it to work reliably and I'm glad I took the time!

I find Karmic to be a good step forward despite all the negative comments that ALWAYS get made by people LOOKING for faults in new versions. 

Wireless just works on the Sony, my son's HP laptop and my EeePC with the Atheros network card. On the Sony, I'm sitting in my sad hotel room tonight connected via Bluetooth to my Nokia Navigator Mobile phone all courtesey of Network Manager that just works! (Why pay £15 per month for a "dongle")?

All my machines just talk to each other including my younger son's Mac Book Pro that I bought him to take to university. He'd been using Kubuntu since he was fifteen and still has it on his desktop at home! A brave decision for a youngster, but he never found any issues doing what he wanted to do.

So.....not many bad experiences! I did many "upgrades too far" when using alpha and beta versions of Karmic but so what? They don't count. Since I moved my mail to Gmail and started using DropBox for my main files (all backed up on the home server) I can brick any machine and get it up and running again in thirty minutes. 

Try doing THAT with Doze......

---

### Post by potestas on 2009-12-07
I am a happy Ubuntu user and try to pass on the good news to all my non-Linux friends.  I've used many different distros and keep coming back to Ubuntu.  However, it's hard for me to recommend Ubuntu right now because the repositories are toooooo slooooooow!  On a new install, it can take all day starting at around 85% (installing language packs - 9.10 desktop).  Windows folks immediately poo-poo it.  Canonical really needs to add some more capacity.

---

### Post by AlanR8 on 2009-12-07
> right now because the repositories are toooooo slooooooow! On a new install, it can take all day starting at around 85% (installing language packs - 9.10 desktop).

Really...............

Not here in the UK

---

### Post by julianb on 2009-12-07
I am a happy Ubuntu user. Why? With Ubuntu I...
-avoid malicious software
-avoid slowing down the computer with virus scanners
-get security updates in a convenient way
-EASILY use e-mail, word processing, wireless & wired networking,  apache/mysql/php, and other common hardware&software.

Ways Ubuntu has not succeeded for me:
-Ubuntu + Wine can't run the program I use most often at work: "Raiser's Edge". More features NEED to be added to the open source alternative before my office can quit using Raiser's Edge completely.
-I can't get OpenVZ or Linux-VServer to work at all, in recent Ubuntu versions. Have not tried older versions.
-I tried & failed to install Ubuntu on a machine with 2gb solid state disk: too little disk space.
-When compared against tinycorelinux, Ubuntu runs very slowly, requires extra disk space, and does not uninstall programs as cleanly.

---

### Post by julianb on 2009-12-07
Potestas - if the Ubuntu repo's are slow, have you tried linux mint? Does it work for ya?

---

### Post by JDorfler on 2009-12-07
I'd like to tell you how this or that program doesn't work for me, or how I'd like something to work differently.  However, I always find a way to make things work, and nine times out of ten, it works better than I thought it would.

The only thing I'm disappointed about is that I can't transfer songs and movies to my Zune.  I have found an alternative that I'm happy with.  A PSP.  I'm not one to usually spend my money on Sony products like this, but for the money, a PSP is a great little media player as well as a quick fix on games.  I just wish there were more games for it to make me laugh like Medieval.  I'm pretty sure a good dose of ScummVM will do wonders for this sucker.

---

### Post by Zoot7 on 2009-12-07
1)
The upgrade from Hardy to Intrepid broke my wireless and nvidia driver. The latter was easy fix but the former was a deal breaker. I did a clean install of Hardy the following day, and stuck with that for nearly a year, because it just worked so well.

2)
A kernel patch in Jaunty broke my sound, I upgraded to 2.6.30 and that sorted everything. My only reason for upgrading to jaunty was that my Atheros based N wireless card I have in my home built Desktop was recognized from the get go - no need for ndiswrapper and the XP driver, otherwise I would have stuck with Hardy.

3)
Karmic and it's heavy integration of pulseaudio has broken the functionality of my laptops's inbuilt microphone, which worked fine with Gutsy, Hardy, and Jaunty with Alsa alone. And it still does work fine with Alsa just not Pulse.
It's not too much of an issue as I rather use a headset with Skype anyway.
The next gripe I have is that all the kernel updates lately seem to break my nvidia driver, and the only fix is to re-install it (it might be the fact that I install the driver manually).

But despite those gripes Ubuntu is still my main OS. :)

---

### Post by 23dornot23d on 2009-12-07
Must admit the only reason I came to the forum was because of the latest version 9.10 ....

Here were my problems ..... going back to my first post .....
(and  all my hardware works fine .... with UBUNTU 8.10 ..... and  ..... with 9.04 ...... )

but when I upgrade to 9.10 ........ Quack Quack Ooooops ..........

No wireless modem
No sound
Nautilus giving errors ...

worst of all which worried me like mad was when I came out of 9.10

No USB shutdown and unmount for my 1 terra drive ......

Which lead to the problem of not being able to boot ....... any new user to UBUNTU ..... 
would have probably been a little worried here .....

as it reports no grub and no boot options ........ error 21
( cure was  ... to turn the drive off and on again .... then reboot ..... - now I just make sure I access it from thunar or dolphin before shutting down )
______________________________________________________________

Once I got the modem working problems were a lot easier to resolve ... ( this was resolved by adding a wired connection - then getting the latest updates )

The sound I used ALSA the latest version .... ( this was resolved by going to the ALSA site and compiling the latest drivers - and running alsaconf )

Nautilus ..... well I never solved that problem - it still does not work 100 % after the
upgrade ,,,, but I use Dolphin and Thunar for accessing my USB drive from my laptop
once accessed from Thunar or Dolphin and the Hard Drive will shut down properly on
exit ....... but if I do not access it at all ...... it just seems to stay mounted and running
even when I turn the computer completely off.

_________________________________________

So my Desktop Computer still runs 9.04 Jaunty ..... 

I keep watching the forum now to see how many similar problems are arising ...
and the fixes for them are now coming to light ,,,,, the ones that interest me are ...

1. The Boot up problems .... grub2 and ext4
2. The Nvidia and Dual Monitor problem as this is how I set my Desktop machine up .... so do not want to lose the functionality.
3. Sound ..... but that is reasonably easy to cure .....
4. The Nautilus problem ..... but not seen anybody else with this ..... I upgraded .... so it is maybe something specific to my set-up

The laptop is a Acer Aspire with Nvidia Graphics Card and a Wireless Modem ...... running 9.10 .... but still ext3 and grub legacy ...

This works very fast now once booted ..... and the wireless works great now and the graphics are superb on it .....
the sound is incredible too as it uses the built in surround sound and latest drivers  ....

So all in all I am very happy now ............... :D

---

### Post by The_Pirate_King on 2009-12-07
I actually posted a thread about my bad Ubuntu experience: [http://ubuntuforums.org/showthread.php?t=1347174](http://ubuntuforums.org/showthread.php?t=1347174)
I betcha I have got the worst :D

---

### Post by margazhang on 2009-12-08
> **slumbergod said:**
> Clean install to Xubuntu Karmic. Actually managed to fix all the bugs that annoyed me except for one (which seems to have broken again after recent updates...

Wireless...specifically, Intel 3945

When the connection drops the only way to get it back is to reboot the pc. Before the updates I could just restart the wireless kernel modules. Now even that has stopped working. 

I am happy with most everything else but I'd be super happy if wireless worked as well as it did with Jaunty.

I had a similar problem with wireless in Kubuntu and I just solved the problem today with WCID installed and now it works great!

---

### Post by Tamlynmac on 2009-12-08
>  Happy users, pls share your bad Ubuntu experience

For what purpose? :confused:

I'm one of the few (apparently) that has never had a bad experience with Ubuntu. *NEVER*

Glad you didn't ask us to share bad Windows experiences. As that would require the condensing of a small library. Not to mention the unnecessary rise in my blood pressure.

---

### Post by running_rabbit07 on 2009-12-08
My only bad Ubuntu experience has been with the people who think that because it didn't work on their system that it doesn't work on any system. Ubuntu is the shiznit on my system. I am running Jaunty for production and it is rock solid. I have Karmic on my daughter's desktop and it runs flawlessly. I have Lucid on a test machine and not one update has been broken on it, thus far. I realize they can't test it on every machine, but I have faith that Ubuntu will work on most systems.

---

### Post by sailorboy on 2009-12-08
Being new to ubuntu I had burned a couple of versions off to try. Jaunty brought a 2 ghz AMD to life and compiz seems quite happy with it's ATI card- I was both impressed and hooked. Now dual booting both machines (XP) and it's obvious which OS runs better.
 (yoda- like)- unfortunate this, that Karmic has issues. Is the 'open DNS' thing I did (MScorefonts) a security issue now? I feel using img burn under wine probably is but at least it burned .vob files easily. Links to alternative 'how to' ideas would be sweet. DeVeDe was taking 4ever to build temp file?.- I'm still a solid fan- it's obvious that a 'buildable' OS is the way to go- a small step to a better world. Back to R&D on video capture-

---

