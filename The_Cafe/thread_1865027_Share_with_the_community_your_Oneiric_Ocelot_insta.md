---
title: "Share with the community your Oneiric Ocelot install/upgrade experience"
date: 2011-10-19
forum: The Cafe
---

### Post by cariboo on 2011-10-19
[SIZE="3"][COLOR="Red"]*** Disclaimer for those willing to analyse this poll ***[/COLOR][/SIZE]

- Most of users voting here are users with issues,
users with painless experience are not likely to come here. So the statistics here do not represent the reality.
- If you want to compare Oneiric Ocelot release with other ubuntu releases based on this poll then here are the previous polls except for Natty Narwhal due to technical problems there isn't one :

[Maverick Meerkat]("http://ubuntuforums.org/showthread.php?t=1595311") Click Me
[Lucid Lynx Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=1465548")
[Karmic Koala Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=1305924")
[Jaunty Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=1133869")
[Intrepid Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=963853")
[Hardy Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=764847")
[Gusty Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=580852")

The purpose of this thread is to share your experience installing/upgrading Oneiric Ocelot. **Any off topic posts, and answers to the off topic posts will be jailed, there will be no warnings**
This thread is to document your experiences, not to help you solve problems

Did it work flawlessly ? 
Did you get problems ? 
Did you manage to solve them ? 
if yes how ?
...
...
.

Feel free to post your experience here and please explain how you solved the problems you got, it might help other users in your case.

Thank you for contributing

---

### Post by Elfy on 2011-10-19
Should be multiple options imo

I have failed upgrade and flawless install

---

### Post by cariboo on 2011-10-19
oops, wasn't paying attention, it's in the right place now

---

### Post by Elfy on 2011-10-19
:)

---

### Post by KiwiNZ on 2011-10-19
I did a clean install on a new Sony Vaio purchased for the purpose. The install was flawless and quite quick.

Very little post install tweaking was required to have a fully functioning Laptop.

---

### Post by sammiev on 2011-10-19
No issues at all! It was one of the best installs that I have had. :)

---

### Post by drawkcab on 2011-10-19
Upgraded on 2 systems:  trivial bugs but I could not fix them.

Fresh Install:  no bugs, everything's fine.

---

### Post by sffvba[e0rt on 2011-10-19
> **forestpiskie said:**
> should be multiple options imo

i have failed upgrade and flawless install

+1


404

---

### Post by Naiki Muliaina on 2011-10-19
Flawless install.

No link in the OP to Nattys poll?

---

### Post by cariboo on 2011-10-19
> **Naiki Muliaina said:**
> Flawless install.

No link in the OP to Nattys poll?

Check my first post.

---

### Post by Redblade20XX on 2011-10-19
Beautifully smooth installation and setup! Couldn't have asked for more! :)

- Red

---

### Post by madjr on 2011-10-19
like some others here, faulty upgrade, but flawless install (should have that option lol)

---

### Post by 23dornot23d on 2011-10-19
I had a few things to fix on the Official upgrade .... but my aptitude dist-upgrades were fine.
and the system runs well once tweaked ..... ;)


> 
- Most of users voting here are users with issues,
users with painless experience are not likely to come here. So the statistics here do not represent the reality.
- Most of users voting here are users that have not already left through having bad experiences too =
users with bad experiences are not likely to come here. So the statistics here do not represent the reality.

Also a week earlier you may have got one or two more .... failed upgrades .... checking in the link below.

---

### Post by Naiki Muliaina on 2011-10-19
> **cariboo907 said:**
> Check my first post.

*rubs eyes again*. Clearly in my absence from Ubuntu Forums I have actually gone blind. :(

---

### Post by Frogs Hair on 2011-10-19
No problems with the installation at all and I have the cube up and running . I didn't know if the 11.04 methods posted on the web would work . I pieced together my own method for the cube from an 11.10 beta tutorial and got it working without breaking Unity . All is well with every thing else . I hope there are more themes available soon . :)

---

### Post by jilbruke on 2011-10-19
Complete disaster. Coming from 11.04

Used the upgrade button on the new version notification window. That spent time downloading and preparing for the upgrade then hung the system. Upon reboot the graphics card had failed to be recognised so I attempted to run with a default configuration. The interface that followed had a black background, the white bar on top with nothing in it, and what looked like the small login panel that did nothing but show the computer name. There was nothing I could do but reboot. This time the boot failed entirely, where I was eventually greeted with the console. On attempting to log in it told me my account was broken/corrupted, but in some way logged in anyway. So I used 'startx' as I'd learned long ago, which yielded the basic desktop asking how I would like to repair the graphics configuration, but hitting ok, cancel, anything had no effect and I could only reboot again.

Reading a forum I found some instruction on how to reattempt to upgrade again:
sudo apt-get clean
sudo apt-get update (required running another command to make it work)
At this point I needed to restart and get onto a wired network, then got to the sudo apt-get upgrade which after about three hours of downloads seemed to do well. On reboot the bootup still hung, and I had to Ctrl + Alt + F2 to get to a terminal, from which I could log in, and startx again. That is how I am here now, booted in using the chrome that was installed in the previous version. Though nothing seems to be connected. It took extra effort and installs to get an icon in the top bar for a reboot/restart menu item (before this I could only Ctrl + Alt + Del to reboot).

So the present state is, to get to the desktop I need to catch the failed bootup and go to terminal, then log in and startx to get to the interface. At this point for instance the System Settings>Additional Drivers item does not exist, the clock does not show in the top bar and searching for 'terminal' in the Dash home returns nothing. I have no idea what behind the scenes is/might be badly broken, and no idea where to look to start solving it. Any ideas?

---

### Post by bohemian9485 on 2011-10-19
Upgrade from 11.04 to 11.10, network connection became erratic, cannot install some programs in software center. Will try the full install later after downloading the ISO

---

### Post by alco75 on 2011-10-20
Upgrade from Ubuntu Natty to Xubuntu Oneiric from a Xubuntu Live USB worked okay, but didn't warn me that it'd be *completely reinstalling* MySQL and Postgres, and hence all my databases would be dropped. Same with Apache, so I had to set up all my vhosts again. Luckily, I don't use that laptop for any serious work. :o

My laptop's WiFi in Oneiric didn't work out-of-the-box, but that's not an issue with the upgrade process really.

Otherwise, it worked fine, and I subsequently purged a tonne of previously installed Ubuntu Natty packages based on information [here]("http://www.psychocats.net/ubuntu/purexfce").

---

### Post by dasan on 2011-10-20
Instead of upgrade installed directly...

Since i am using root and home different partition this is a best option for me and liked the new oxygen theme with line

---

### Post by E_Sound on 2011-10-20
I had no problems after upgrade from Xubuntu 11.04 to 11.10. ;)

---

### Post by madjr on 2011-10-21
@cariboo,

Mark is [promising]("http://www.markshuttleworth.com/archives/810") that upgrades from 10.04 to 12.04 will be "smooth".

you're still using 10.04 right?

Will you go ahead and do the upgrade or do a clean install to be more secure?

I hope things go better next release. I might go ahead and reinstall the old lts just to see how well it goes compared to an 11.10 upgrade to the lts ;D

but one thing is "promise" and another is it really happening, well lets see how it goes..

---

### Post by ubupirate on 2011-10-21
> **madjr said:**
> @cariboo,

Mark is [promising]("http://www.markshuttleworth.com/archives/810") that upgrades from 10.04 to 12.04 will be "smooth".

you're still using 10.04 right?

Will you go ahead and do the upgrade or do a clean install to be more secure?

I hope things go better next release. I might go ahead and reinstall the old lts just to see how well it goes compared to an 11.10 upgrade to the lts ;D

On this note, I may very well just try an upgrade for the first time. I've done clean installs since 9.10, and figured there is a first time for everything.

Want to see how "smooth" he actually means. I've got nothing to lose, as most of the stuff I can just redownload from the net (legal stuff ;P urbanterror, warsow, etc etc).

---

### Post by cariboo on 2011-10-23
> **madjr said:**
> @cariboo,

Mark is [promising]("http://www.markshuttleworth.com/archives/810") that upgrades from 10.04 to 12.04 will be "smooth".

you're still using 10.04 right?

Will you go ahead and do the upgrade or do a clean install to be more secure?

I hope things go better next release. I might go ahead and reinstall the old lts just to see how well it goes compared to an 11.10 upgrade to the lts ;D

but one thing is "promise" and another is it really happening, well lets see how it goes..

The only system I have 10.04 on is my server, but I have a couple of P4 systems that I will install Lucid on, along with all the applications and data I have on my daily use system, and start trying the upgrade from 10.04 to 12.04 around the time of the beta release. One system has a 6xxx series agp graphics card and the other has an ATI graphics card, and as much as I dislike ATI, I won't swap it out for a better one, and see how the upgrades go.

I tested upgrading from 8.04 to 10.04 during the RC release of 10.04, and aside from doing it on a fairly slow laptop, the upgrade went quite well.

---

### Post by madjr on 2011-10-23
seems the forum poll has been slow this cycle.

Omgubuntu started a [poll]("http://www.omgubuntu.co.uk/2011/10/how-well-did-your-ubuntu-11-10-upgrade-go/") and its almost at **1700** votes within a few hours...

Looks like 40% had a good upgrade, 34% had some stuff broken, but the remaining 22% can be considered "**severe**" (no other choice except backup files and reinstall). So if our expected base of "12 million" plans to upgrade at one point, then 22% seems pretty alarming. Even if its 10% there is potential for *a million* users affected.

I knew the problem was a little rough, but didnt think the figures were getting so high.

Is a good time to tackle this, before the userbase starts growing exponentially..

---

### Post by Olph on 2011-10-23
11.04 to 11.10

First upgrade that has given me any trouble.

A little too much difficulty restoring previous desktop.

Numerous media issues that responded to reinstalls.

Cannot get Asus soundcard to work.

I wish I'd stayed at 11.04.

---

### Post by Guitar John on 2011-10-24
I did a clean install of Ubuntu 11.10 (Oneiric) on a ThinkPad X100e.  I was hesitant, because 11.04 didn't go all that well.  But I have to say that things are working a LOT better this time.  

All of my hardware was recognized out of the box. Wireless was quick and painless. The webcam works with GUVCView. The mic works with SoundRecorder. I installed gpointing-device-settings to configure the middle button scrolling feature with the TrackPoint.

Unity is something that I'll have to get used to, but the install went well.

EDIT: For what it is worth, I used the Alternate Installer (text based installer).

---

### Post by AVH on 2011-10-24
I did an update. My regular account has no launchers and windows problems. The Guest account has launchers and the windows seem to work ok. Everything is rather slow. Tried 'unity --reset" in a terminal and it failed with multiple errors. No solution yet.

---

### Post by Stovey on 2011-10-25
I did a fresh install on an Acer Aspire 1810T - no problems whatsoever, very smooooth.  The upgrade was taking too long, a few hours at least.  :D

---

### Post by stingray69 on 2011-10-25
I upgraded from 11.04 and haven't been able to get classic working. All the panels are gone so there is no real interface. Tried gnome-session-fallback but it didn't help anything. I've been using unity in the meantime but it's driving me crazy.

I'm also having trouble connecting to my own network. It takes 5-10  minutes before it connects, though it doesn't have a problem connecting to my neighbor's open network.

I'll either try a fresh install or move to xubuntu if I can't get back to a working gnome classic. Hope others are having better luck.

---

### Post by divergex on 2011-10-26
I was previously testing the Oneiric beta on an old Dell D620, and it had a couple issues that were not present in 11.04, especially with the brightness keys. So this past weekend I bought a Lenovo G570 that was on sale at Fry's. I was pleasantly surprised by the speed of the i3 processor in it, and decided to give the official release a try.

I created the restore discs in case I wanted to come back to Windows 7 - I don't really like to dual boot. The install was smooth... everything was recognized, even wireless. I tested sleep and hibernation, and they worked as well. The brightness and volume keys work great, as did two-finger scrolling with the touchpad. I must say this is the best Linux experience I have had on a laptop ever.

I will be keeping this G570 Ubuntu only. I have since installed all the tools I need, and it is working great.

---

### Post by dave2001 on 2011-10-26
I did a fresh install, as I wanted to give this release the best chance for success that I could. Unfortunately there were a lot of bugs (small and large). One of the most annoying for me, and one I could not solve, was a hold-over from 11.04 that was apparently never addressed: Full-screen flash video in web-browser has garbled audio.

Overall result: After several days of attempting to make this release workable and enjoyable, I threw up my hands in frustration and went back to 10.04

---

### Post by Perfect Storm on 2011-10-26
Installed Flawless. Then installed Gnome Shell - still flawless :KS

---

### Post by cariboo on 2011-10-26
I did a second install to prepare for Precise Pangolin, and it didn't go as well as the first one. It may have something to do with the fact that Windows 8 was already installed on the same hard drive. I used the Windows disk management tools to resize the the second Windows partition, and installed on the resulting empty space. The install went well by itself, but when I rebooted it booted straight to the first Oneiric install, there was no indication that there was a second Oneiric anywhere. Once in the first Oneiric install, I chrooted the second install and installed grub again, and this time it worked, and all was well.

So at the moment my system triple boots, Precise by default, with Oneiric and Windows 8, as the other choices.

If I could vote a second time I'd choose:

Install - worked but had a few things to fix, nothing serious though

---

### Post by melora.adams on 2011-10-26
The system bugged me to upgrade until I gave in. Now it fails to boot. So overall, it has been a negative experience. I'm about to find out whether the forum is going to be any help. I hope so.

---

### Post by shwallace on 2011-10-27
Ran Oneric from CD and it seemed to work fine. Installed it and now my computer hangs up at boot.

---

### Post by sports fan Matt on 2011-10-27
Every single install I have ever had has worked flawlessly.  This time I actually upgraded all the way from 10.04 and all went smooth:)

---

### Post by buddhadba on 2011-10-27
First bad upgrade in three or four releases. Used to be (Intrepid and before), I always had to tweak the post-upgrade system to get wireless Broadcomm modem and nVidia video card to work, then for several versions, it auto-detected everything and all I had to do was occasionally activate the correct driver.

When upgrading from 11.04 to 11.10, it seemed to go well, I installed the Gnome Shell and selected it for booting, and checked things out. My wireless card required considerable tweaking via instructions on the Forums, and finally got it working. Then, my HP Laserjet 4L failed to print. After uninstalling/reinstalling various drivers, I deleted the printer to try to reinstall it. No luck. The system can't see it, so doesn't see a need for the driver, so no printer. I cannot find anything more to do to get this to see the printer or get the printer to work. My next step is to install the OS from scratch and see if that works. If not, it's off to Fedora, which I've already installed on my other, older Dell laptop because it works where none of the _ubuntu flavors (Xubuntu, Kubuntu, Ubuntu) work with it. And, Fedora comes with Gnome Shell as the default.

---

### Post by mebomechanicno1 on 2011-10-28
Installed to a Sony Vaio that had been around the block a few times . It started life with Vista Business then when it was retired from business to play with had 9.10 Karmic Koala then Lucid Lynx, neither of which worked successfully (wifi kept dropping on Koala, but while it worked after a fashion with Lynx, I could never actually configure a smooth automatic email download), so I went back to Vista, which never worked properly after the interlude with Linux, and got progressively worse the more I tried to fix it, then I tried Ocelot, initially live from a USB, and next day installed it over the top of the Vista with no problems.
 
:popcorn::KS:KS:KS

---

### Post by stormelf on 2011-10-29
(Mega rant warning!)

Upgrade totally borked the desktop settings on my work computer. Reinstalled from scratch but was unable to create anything resembling a usable desktop environment for work and productivity. 

Everything I do seems to take two clicks extra with Unity. It is visually "fun" in a Apple-meets-Playtime-Disney kind of way but from a productivity perspective it is now a train wreck. It ignores several basic rules of user friendly interaction design. The flaws have been pointed out in great detail innumerable posts and videos, and solutions have been given, but every attempt at constructive criticism seems to be ignored by Canonical. 

I have been a very happy user of Ubuntu for a long time, since 6.06, and got rid of Windows completely by version 8.04. I have never had any problems. Not until now. 

Ubuntu had a brilliant future ahead of it. Then gradually strange decisions started to be made, beginning with the pointless moving of the window buttons to the left side, and now finally culminating with the ironically named "Unity", that seems to be causing the greatest mass exodus in Ubuntu history. 

Maybe I am just too old and grumpy to appreciate the value of huge wiggling icons. (I'm 26.)

(/rant)

---

### Post by Mezzoforte on 2011-10-29
Installed Oneiric (64-bit) on a new desktop I put together a few weeks ago. Worked flawlessly. I was afraid that there would be problems because I installed the not-recommended 64-bit version, but it seems fine.

One problem I have experienced so far is that once or twice when switching between logged-in users, the graphical interface has gone astray. Otherwise nothing at all.

---

### Post by goldshirt9 on 2011-10-31
[COLOR=Red]other than the time it takes to boot[/COLOR] :-( far too long for me
, it works a treat , nothing crashes , nothing untoward.
 a nice o/s :)

---

### Post by lorin30 on 2011-11-02
I did a clean install (Xubuntu 11.10) and used it as an opportunity to finally switch to 64 bit... worked flawlessly, other than taking a few tries to find a flash plugin that didn't crash but... that's to be expected.

---

### Post by jcoles on 2011-11-04
On some hardware and VMs, installation was smooth. On an Acer AOA-150 netbook (dual boot with Win7) it was horrible! The partition table was permanently altered: 
- No more sda1, the first (Windows) partition is sda2
- No more sda3, Linux root partition now sda7

Was able to export/edit/reimport the partition table with sfdisk to eliminate the bogus zero-length sda1 partition. sda2 then became sda1 as it was before. Removed all other partitions and ran the Ubuntu install to put Linux alongside Windows. Boot leads only to grub rescue prompt.

Following the "Rescue Mode (''grub rescue>'') Booting" instructions in [https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting]("https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting"), I was able to start my installed system. Then I ran 
> sudo grub-install /dev/sda
to restore the Grub bootloader.
Not sure why this installation was so rough. An inexperienced user would have ended up with a "broken" computer with neither Linux or Windows available.

---

### Post by cloyd on 2011-11-04
Did an upgrade . . . all my old applications were still there, and the installation went without a hitch. After instalation, I'm having problems with very slow wireless. I wasn't surprised, because live cd gave slow wireless. Had no problems whatsoever with previous versions on this machine. Currently running wired, but would like to solve the problem. Problem posted elsewhere.

[http://ubuntuforums.org/showthread.php?t=1874668](http://ubuntuforums.org/showthread.php?t=1874668)  

Anyway, just had to have the newest release.

---

### Post by zer010 on 2011-11-05
As a user of old tech, the fresh install of Lubuntu 11.10 has insofar been flawless. There is still an issue with the calendar in my Conky, but I'm sure that's just a regex thing. I had to change the window option from "override" to "normal" just to get it to appear.  All in all, a very welcome member to the Ubuntu community. ^_^d

BTW, I voted wrong. Should've been "Install - worked flawlessly", NOT "*Upgrade - worked flawlessly"...*

---

### Post by wojox on 2011-11-05
Went good, had troubles with the installer crashung twice but made it through. It's all good now. :P

---

### Post by jcoles on 2011-11-05
Acer Aspire One AOA150. Wireless (Atheros) cannot be enabled. Trying to follow complex technical instructions in forum.

You will never get beyond geek users unless laptop/netbook wireless works straight out of the box.

My machine is dual-boot with Windows 7. I got my wireless back by starting Windows and operating the netbook's hardware switch to enable wireless. Back in Ubuntu, wireless works. You can even turn it off and back on again with the hardware switch. Not sure how the problem could have been solved on an Ubuntu-only system.

---

### Post by sidewalkcynic on 2011-11-05
> **jcoles said:**
> An inexperienced user would have ended up with a "broken" computer with neither Linux or Windows available.
The inexperienced user has to go through the hardships of learning what sudo grub-install, and other stuff is just like you did.

Believe, me, after three years and twenty-some installation cycles, of trying to get it better - I lost everything (10GB of general research info, and 250MB of my progress notes), all I had was my last  /home, the 11.10.iso, and a LinuxLive app on an FAT32. - too bad I didn't use the Backup app/client service - was that in 11.04?

I'm starting from scratch, and it seems like - free at last, free at last.

---

### Post by BillyBoa on 2011-11-06
Perfectly working apart from a strange bug, I cannot rename files in Downloads folder and in some NTFS folders. Moving the files to a new folder solves the problem temporally.

---

### Post by drreed on 2011-11-06
Congratulations. I don't think I've ever installed a linux distro during and immediately after which, everything worked. As usual, I did have to install a flash plugin. My sound worked immediately, so did everything else. I didnt have to configure my network connection either. I turned it on, had internet access, and was working within minutes. For the record, I had identical experiences with both new installs and upgrades.  Oh and the very best part is, Grub actually worked and I could choose either Ubuntu or Windows and both launched! Ha! 

I'm terribly sorry others have had difficulties. Wish I could have helped you, but I'd have probably only made things more complicated. :guitar:

---

### Post by AllenGG on 2011-11-06
Surprise !!  The only word to describe this experience. This is by far the smoothest O-S around.  Some things are hard to find. But thats good, heres why.
After installing the ¨O¨ on my old Acer laptop, I installed it, as a favor on an old P4 (LGA775) system designed for a one person office.  That person can not easily install crap on the system, thus saving me a lot of trouble.
With a 3 minute intro, the user was a happy camper.

---

### Post by AllenGG on 2011-11-06
Oh a PS.   
Had the usual problem with the Broadcom BCM4318 device. [**BCM43XX]**
Solved fast here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

---

### Post by quequotion on 2011-11-12
Awful.

Just absolutely awful.

Worse than Natty and Natty was bad.

What is going on during the testing phase?

---

### Post by cariboo on 2011-11-12
> **quequotion said:**
> Awful.

Just absolutely awful.

Worse than Natty and Natty was bad.

What is going on during the testing phase?

Why don't you join us, and find out. Check [here]("http://ubuntuforums.org/forumdisplay.php?f=412")

---

### Post by vasa1 on 2011-11-12
I upgraded and voted for "flawlessly" but ...
[list]
[*]I'm not on a fast net connection and so it took several hours. Given that I had to provide responses at various times, the upgrade is apparently something that can't be left unattended. I guess if a response is not provided when asked for, the process will pause at that point.
[*]To some extent, the upgrade involves a "duplication". This is because we're recommended to try out the new version to ensure that it plays well with our hardware. This means trying out the live CD/USB. **Then**, the upgrade occurs online. No doubt a huge chunk of data is already on the live CD/USB. If there was a **simple** way to upgrade from the LiveUSB, that would be great. Obviously, only software present on the Live CD will be "**updated**". The rest could be **updated** later online.
[/list]

---

### Post by spezticle on 2011-11-13
no problems in instillation at all. I just really don't like gnome 3.0

---

### Post by Giulia27 on 2011-11-20
Smooth installation. 
However, I had some stuff to fix on the desktop, but nothing that serious (so, no drama here, at least for me).

I am happy that I can have a Cairo-Dock session, instead of the not-so-awesome Unity desktop (Unity is not that bad, but Cairo-Dock is much more beautiful than the Unity desktop).

---

### Post by danceswithcats on 2011-11-21
I've installed Oneiric on a new machine tonight and I think it is awful.  The install went flawlessly, even loading the ATI drivers without a hitch, but, even with the Unity thing switched off, it is like a neutered Ubuntu, with half the features I'm used to gone.  I'm downloading the LTS now and will update to Natty, which, on an old server box, was much better.  I'm very disappointed.

---

### Post by buckeyered80 on 2011-11-21
Everything good on my end. I had to uninstall dmraid before the installation, because it was messing with my raid controllers. That was my only issue. 

And by the way, I like Unity, have some patience with it...it's still new. I think it's nice.

---

### Post by Jordanwb on 2011-11-22
I decided to upgrade from 11.04 to 11.10. Kubuntu's dist-upgrade GUI crashed during a package install so I had to kill that, restore /etc/apt/sources.list, then do apt-get dist-upgrade. The rest of the process went well.

Then slow boot times. Normally it would take around 20 seconds for my laptop to boot, it takes me a full minute because wait-for-root idles for 30 seconds.

I can't browse samba shares in dolphin.

The CPU's fan spins up for 10 seconds every few minutes even when the CPU's not under load.

---

### Post by ~Hinterland on 2011-11-24
Fresh install on a Lenovo S12 netbook.
Install seemed to take quite a bit longer than previous versions.
Only problem was wireless (BCM4312 LP-PHY) didn't work until I blacklisted acer_wmi.
Didn't like Unity at all, but I do like Gnome 3, which runs well :)

---

### Post by Gael33 on 2011-11-25
I have a 3 year old desktop ... AMD Athlon X2 6000+ CPU, 3.8 Gb Memory, 160 GB HDD.
I have been using Ubuntu for a couple of years, and although I am no technical wizz-kid I was easily able to clean install Ubuntu 11.10 without any problems. Everything worked out of the box so to speak. The only little niggle is that closing down is problematic and I have to use the terminal (sudo halt) to shut down on occasion. Apart from that the system is stable, reliable and runs like a F1 racing car. Well done the Ubuntu team :)

---

### Post by Atomic-Fanboy on 2011-11-26
Upgrading to Oneiric was a very time consuming process. I had no media at hand to make a live CD or USB stick... so I had to make a Wubi Lucid Lynx install, use wubi-move to fully install Lucid, and then update sequentially to Maverick, Natty and then Oneiric....

---

### Post by Gael33 on 2011-11-26
> **Atomic-Fanboy said:**
> Upgrading to Oneiric was a very time consuming process. I had no media at hand to make a live CD or USB stick... so I had to make a Wubi Lucid Lynx install, use wubi-move to fully install Lucid, and then update sequentially to Maverick, Natty and then Oneiric....

Wow! that really was the long way round :) Preparation is key when upgrading so you don't lose any of your personal stuff. I always back-up everything that I will require later, and then I wipe the HDD clean. Clean install the OS and then add all the stuff I'd saved by copy & Paste or drag & drop and within no time the computer is running like new.

---

### Post by Atomic-Fanboy on 2011-11-28
"Wow! that really was the long way round :smile:" - Yes, it really was. I had to do it this way because I had no spare disks and only a 128 MB flash stick. 

First, I had to wait until after midnight to create a wubi install. (My family and I use BT broadband and BT love to throttle download speeds - especially regarding torrent files). While downloading the Lucid torrent, I was stuck using Windows for quite a while - and it was slow. Even with no eye candy and control panel settings selected for "Best Performance", it was still painfully slow (and ugly to boot.)

After installing Lucid, it was easy enough, bar a few problems, such as a horrible, distracting screen flicker (problems with i915 drivers and Intel Mobile Chipset 4). 

Fortunately, I could use an older version of Ubuntu (eg. Maverick Meerkat) while downloading and installing the subsequent version (Natty Narwhal).

---

### Post by typhoon_tip on 2011-11-29
Install flawless but upgrade had some major problem with compiz & OpenGL in general, I could not get completely around it (frequent X crashes).

---

### Post by kio_http on 2011-11-29
I had one upgrade from Kubuntu 11.04 and one fresh install. No issues to report. Big performance boost between the two though!

---

### Post by Gael33 on 2011-11-29
> **kio_http said:**
> I had one upgrade from Kubuntu 11.04 and one fresh install. No issues to report. Big performance boost between the two though!

You don't actually say, but I would guess that the clean install has given you the better performance. The problem with up-grades is that all the junk that has been accumulated (seen and unseen) is carried over to the new OS. I always check first before starting whether the new OS is an improvement over my present OS. If it is, I save what I want saving to my external drive, then, and only then do I wipe the computer hdd and follow the new installation procedure. Afterwards, I introduce all my saved stuff from the external drive. So far (touch wood) it has never failed.

---

### Post by OrangeCrate on 2011-11-29
No problems here with a fresh install. After I removed the indicator-appmenu package, it looks pretty much like Lucid with a dock. Unity is fine - I like it, and, the software stack seems very solid.

[http://askubuntu.com/questions/10481/how-do-i-disable-the-global-application-menu](http://askubuntu.com/questions/10481/how-do-i-disable-the-global-application-menu)

---

### Post by kio_http on 2011-11-30
> **Gael33 said:**
> You don't actually say, but I would guess that the clean install has given you the better performance. The problem with up-grades is that all the junk that has been accumulated (seen and unseen) is carried over to the new OS. I always check first before starting whether the new OS is an improvement over my present OS. If it is, I save what I want saving to my external drive, then, and only then do I wipe the computer hdd and follow the new installation procedure. Afterwards, I introduce all my saved stuff from the external drive. So far (touch wood) it has never failed.

Sorry, I meant between natty and oneiric, oneiric being faster. This was because 
1) KDE 4.7 has performance boosts over 4.6
2) The Intel graphics driver in 11.04 conflicted with KDE 4.6

Although installing KDE 4.7 from backports in natty did improve things a lot, 11.10 is still a tiny bit faster than that.

---

### Post by km6xz on 2011-11-30
I tried to install after trying with the USB drive but my HP i7 17in laptop has Windows 7 and it uses all 4 possible partitions so there is no place to install 11.10 :confused:

But from the trial with the USB I must say everything worked great, no hardware incompatibilities, screen looks sharp and crisp compared 10.04 which is what I have installed on 28 desktops in my office. I played for a few hours and by hour 2 I was actually liking Unity. The whole package seems polished and easy to navigate. It found and configured drivers for 2 printers, a scanner, camera, the hd display, the wireless adapter, wireless mouse etc. 
Even with running off the USB drive normal tasks are quicker and more responsive than Windows 7. Maybe due to having the 8gig of RAM, the sensation of snappiness is distinct, really impressive. 

I just wish I could dual boot on a permanent install.

After the experience of switching 28 users set in their ways with various flavors of Windows in the office, and being prepared for battles and complaints, I am happy to say that even the most diehard Windows fans took right to the 10.04LTS version. It was painless and fast. But if I show them the 11.10, the complaints will be "why can't I have that?"

---

### Post by khelben1979 on 2011-12-03
I had no issues installing Ubuntu 11.10, everything just worked and I was impressed by it.

One minor issue caused the screen to go all black, but it was quickly resolved by just changing the cable to the other port of the graphics card. It doesn't use the same one which Debian uses which I'm used to.

---

### Post by ccwillrun on 2011-12-03
I just clean installed 11.10 on an old emachines laptop that used to run windows xp just as something to play around with.

My minor issue was a firmware problem with my wireless card. I found a solution here on the forums and now everything is working fine. So far I'm enjoying the switch!

---

### Post by weasel fierce on 2011-12-04
I upgraded and it worked flawlessly. This was Kubuntu though, rather than Ubuntu, for what its worth. But I figure all the core bits are the same.

---

### Post by boazjones on 2011-12-05
The Mission:

Get my Ubuntu Oneiric Ocelot to provide same services as Windows.

Steps:

1. Ubuntu Install = Smooth with no problems
2. Video = VLC installation provided minor configuration changes in order to play DVDs.
3. Download Videos in Firefox = Download Helper installed smoothly.
4. USB Flash Drive = Not a problem ("every thing's a file" - Media Folder)
5. Libre Office = Downloaded Libre Office Base (Access Equivalent)
6. Bluetooth = challenges remain...
7. Compiz-Fusion/Unity = challenges remain
8. Quantum GIS / Grass GIS = Smooth with no problems

Installed on my trusty Asus G50v - rockin' Oneiric Ocelot...

---

### Post by mgentles on 2011-12-05
New Wubi install alongside Win7 on ASUS X44L 64-bit. Not a huge fan of Unity. Prefer desktop in 10.10, with Compiz Fusion running. Missing Synaptic, but found and installed, got Medibuntu going after doing some digging. Now have installed KDE Plasma, hoping it will be more stable on this machine than it was on the old Dell I have with 10.10. Wanted to run Compiz on this one, but a quick google search revealed a nightmare of problems associated with it. Not highly impressed yet. though it has some ok features.

---

### Post by mgentles on 2011-12-05
> **km6xz said:**
> 

I just wish I could dual boot on a permanent install.



You certainly can dual boot...Use Wubi.exe included on the CD (Not sure if this works from USB) Installs in a virtual disk within Windows, when complete you will have the option to boot to Windows or Ubuntu at start-up. Working great on my laptop.:)

---

### Post by Lalaith on 2011-12-06
Newbie in Ubuntu's life, installed Oeniric Ocelot, and had some minor problems with my Asus that apparently are the same on most of the models [lots of threads on Asus support Forums].  I have to confess that it's a bit annoying, if I had no time maybe I would go back to windows... luckily I do have time and I like to learn this kind of things.:)

Next step will be to install VirtualBox and start changing risky things inside with Ubuntu 11.10.:P

---

### Post by thaelim on 2011-12-07
Clean install on a brand new (Ubuntu Certified) Dell laptop. Two things needed fixing:

- Install Ironhide to disable the Optimus graphics (which works correctly now). 
- Install a psmouse_alps dkms package to get the touchpad recognised properly. 

Everything on the laptop now works perfectly.

---

### Post by flyingfisch on 2011-12-08
Here is my experience with 11.10.

This is my first time with ubuntu, i have used another distro called gNewSense on my laptop, but that was a long time ago. So, heres what happened:

1. I took a day with my slow internet to install ubuntu
2. I installed it (first time) but found that i accidentally put GRUB2 on the wrong drive.
3. I reinstalled (try 2) and found that i accidentally made the partition 6GB. idk how i did that.
4. I enlarged the partition with the liveCD and gParted.
5. I found that for some reason, linux-swap was not set as sw in fstabs
6. fixed that
7. 3 days later (today), i find that ubuntu wont boot.
8. I spent all day trying to figure out whats wrong: [http://ubuntuforums.org/showthread.php?t=1892645](http://ubuntuforums.org/showthread.php?t=1892645)
9. I finally give up and reinstall ubuntu.
10. I still like ubuntu better than winXP though, and im willing to keep trying to fix it.

---

### Post by jacobsallan on 2011-12-10
An upgrade from an 11.10 Ubuntu desktop was blocked.  The message dialog read "An unresolvable problem occurred while calculating the upgrade: E:Error pkgProblemResolver::Resolve generated breaks, this may be caused by held packages."  The packages held are listed in /var/log/dist-upgrade/apt.log.  There were 140 packages in this list.

---

### Post by guyver_dio on 2011-12-11
I've installed oneiric twice now, both from cd

First time I decided not to connect to the net during installation and installation was very quick and flawless. It just meant I needed to install third party codec pack after the installation was complete.

Second time the cd had trouble getting to the trial screen where you can choose to try or install ubuntu. Not sure why but after rebooting a few times it finally worked, I decided to connect to my wireless network during installation. The installation took alot longer since it had to download updates but other then that still quite good. Even with downloading updates and codec pack it still installed faster than windows.

Both times I completely removed my partitions and created new ones, maybe some assistance or notes would be helpful if people try and install it this way. To novices it's not clear that you need to set up a swap partition and after setting up your root partition you need to click it then edit it to make it root. Someone new to ubuntu might get a bit lost.

---

### Post by sunfromhere on 2011-12-14
The upgrade borked everything, it wouldn't even run Ubuntu live CD. No GUI, no command line, it just hung on start up. Managed to reinstall from scratch, lost about a years worth of photos (thankfully, other stuff was on the external HD), and also learned a valuable lesson: back-up and do a clean install!

---

### Post by viperdvman on 2011-12-14
Did an full install from a USB a few weeks ago on my netbook (I don't remember if I used the LiveCD or LiveDVD iso). Everything works beautifully. I've had no problems running Oneric on the netbook, and I even customized it a little bit, with panel, launcher, and menu transparencies and the Ambiance Dark Nautilus Sidebar theme.

Note: I run an EeePC with the AMD V105 "Nile" with ATI Radeon HD 4250. And it runs everything, including Unity 3D and Compiz, beautifully. :)

Still using Natty on the desktop since I still like my Mac OS X look in GNOME 2.

---

### Post by Myglaren on 2011-12-17
Tried to install from a download that went hopelessly wrong - bad burn I expect.
Installed 10.04 from an original CD then upgraded through the builds.
Oneiric had a few flaws, mainly with installs from the software centre.
It won't display installs properly for one thing.

Then, while trying to increase the size of the top panel*, I installed Compiz, Emerald and Window Manager.
The last two can't be found but I tried Compiz, that dumped Unity but had very limited access to anything.
I can only use the 2D desktop now, which kinda makes purchasing a graphics card suitable for 11.1 somewhat useless.
I have ordered original CDs of Oneiric and will perform a clean install, see how that goes.

*this is required for my wife's laptop as she has a visual impairment and can't read the standard panel.
Installed from a download but passed that CD on to a friend. Could also be that My CD reader doesn't like the discs made by the writer, should make the writer the master so I can boot from it. If only I wasn't so lazy :(

---

### Post by xgiannak on 2011-12-20
The upgrade worked, but I had to tweak with the desktop to bring it back into usable state. Pity that the panels on classic desktop have lost functions.
Migration of evolution was poor.
Thanks for the good work anyway,
xgiannak

---

### Post by Ronco Pizatto on 2011-12-23
The install was amazingly easy.

There is no free driver for my wide format printer. (I can buy TurboPrint)
My Canon IDE scanner has cloudy scans. (I'll buy a different one.)
I miss Adobe Acrobat Writer to edit pdf's but i can do that on line.

BricsCad Linux works great. So I am very happy. I even like Unity now!

---

### Post by Sijmen on 2011-12-28
Did a fresh install of Xubuntu 11.10 on a Toshiba Satellite Pro A300. Everything works okay. Haven't tested Bluetooth yet since I haven't got a Bluetooth device.

The thing that surprised me was that my Huawei HSPA USB modem was detected and usable. I figured I had to find some drivers and install those. All in all, this went better than I expected :)

Edit: and by the way. I bought a Hercules DJ Console MP3 for my Powerbook years ago, after some searching I found  Rojtberg's repo and it has the drivers I need. I can once again pretend I'm a qualified DJ :D

---

### Post by QIII on 2011-12-28
Kubuntu, fresh install, no hitches.

I just hope Nepomuk and Akondi are fixed in KDE 4.8 because they are nothing more than CPU stress tests until you turn them off in 4.7.  Sigh.

---

### Post by toyoracer on 2011-12-29
The install went very smooth on my new build. Everything worked great. The Unity will take some time to get use to though. ;)

---

### Post by itpro007ca on 2012-01-07
I installed Ubuntu 11.10 and it worked...but have a few problems(which I posted about under "installation and upgrades") with Display and Dual-Booting.

---

### Post by StewartM on 2012-01-13
The upgrade went flawlessly as in "ending up with a working system as per developer intent". I can't complain there.

Restoring or finding workarounds for the functionality I lost was another issue. That was my biggest problem. 

StewartM

---

### Post by Kingnothing412 on 2012-01-14
i chose "Install - worked but had a few things to fix, nothing serious though" but only because it was my first time ever working with anything othar than Windows. I Still have some issues with the language and stuff but its all going great overall :) i think im getting used to it. I like it more than win xp. :)

---

### Post by Papi47 on 2012-01-20
I have been using 10.04 since it came out and after reading all all of the negatives about Unity and G3 I tried it in VBox and came away not really liking 11.10.  The launcher was on the left and couldn't be moved to the right.  There were a lot of usage issues.  When the 5yr LTS was announced I decided to try Oneiric again.  I am dual booting and have learned some of short cuts so the left side doesn't matter to much.  Maybe someday.  I do miss some of the applets but I think they will come in time.  Everything works except for Tonido so I will go back to KMyMoney.  I will install 12.04 when it arrives but I will probably leave 10.04 on my wife's notebook.  She has a hard time will OS's.  Ubuntu has come along ways since I started using Feisty.  :P

---

### Post by desktorp on 2012-01-20
I have had some problems:

[LIST]
[*]LightDM logs in twice at system starts with autologin
[*]the notification tray's icons randomly go blank when a new icon is added, usually becoming unresponsive when blank.
[*]window movement smoothness degrading suddenly
[*]minimize/restore malfunctions when using window buttons
[/LIST]

I have Xfce using Compiz on this system, but I have found some bug reports in each project that seem relevant, so it's possible that I'm experiencing unrelated Compiz and Xfce bugs, rather than a negative side-effect of their combination.

It's also very likely that I did *something* wrong, but I've done this a few times before (with previous releases) and don't recall having the problems I'm having now.  Admittedly, due to laziness, I've done very little to really track down the problems.

I found tolerable workarounds for everything except the window movement thing.. then abruptly, Counterstrike broke in  a really bizarre way.  Backtracked on my workarounds to no avail.  Removed Counterstrike and reinstalled- still messed up.. etc.. If I go back to 10.04 or something and I still  get these bugs, I will chalk it up to hardware problems, but I'm guessing it's not.

---

### Post by Lensman on 2012-01-21
Upgrade from 10.10 to 11.10 went flawlessly. I usually do a clean install, but I am pleased so far.

---

### Post by addinall on 2012-01-27
Did a clean install on a new Toshiba Sat Pro Laptop.  I had 10.x on my old ACER so I thought I would jump straight to 11.10 on the new box.

I don't know how anyone runs this.  Honestly, after using UNIX daily since 1987 and Linux daily since 1995, Ubuntu 11.10 has to be the worst computer experience I have ever come across.  Most of that time since 1987 has been as a systems administrator or systems programmer.

Firstly, I hated the menu that came as standard so went through the routines of installing and switching to Gnome 3.  The System option was missing with no clear way of restoring it to the menu system.  Small worry, I could fix that later, however, application after application would just crash the system using the Gnome interface.

Biting my tongue, I put the new "look at me!  I am a cross between a cheap telephone and an Apple Mac" interface back on the beast.  At least SOME applications would work for a while.

I have never ever had a worse browsing experience.  Firefox crashes, Chromium crashes, Chrome crashes.  Not daily.  Hourly if I am lucky.  The shockwave blue screen of aw can be expected at least 20-30 times a day.  Googleing the errors provides no fix apart from "start again from scratch".

This thing has had more reboots in the last week than my Windoze box has had in a year.

It still will not talk to my Belkin Wireless router on the upstream properly, and the logs to trace errors seem to have gone AWOL and the tools to investigate either do not exist on the distro, and don't install cleanly through Ubuntu software manager or apt-get.  I have problems with apt-get and dpkg EVERY day.

Using the supplied application to burn an ISO just creates beer glass coasters.

It is truly shocking.  For the first time in my life I just advised a mate to go and buy a copy of Windows 7 as Linux looks pretty much stuffed right now.

Mark Addinall.

---

### Post by cariboo on 2012-01-27
> **addinall said:**
> Did a clean install on a new Toshiba Sat Pro Laptop.  I had 10.x on my old ACER so I thought I would jump straight to 11.10 on the new box.

I don't know how anyone runs this.  Honestly, after using UNIX daily since 1987 and Linux daily since 1995, Ubuntu 11.10 has to be the worst computer experience I have ever come across.  Most of that time since 1987 has been as a systems administrator or systems programmer.

Firstly, I hated the menu that came as standard so went through the routines of installing and switching to Gnome 3.  The System option was missing with no clear way of restoring it to the menu system.  Small worry, I could fix that later, however, application after application would just crash the system using the Gnome interface.

Biting my tongue, I put the new "look at me!  I am a cross between a cheap telephone and an Apple Mac" interface back on the beast.  At least SOME applications would work for a while.

I have never ever had a worse browsing experience.  Firefox crashes, Chromium crashes, Chrome crashes.  Not daily.  Hourly if I am lucky.  The shockwave blue screen of aw can be expected at least 20-30 times a day.  Googleing the errors provides no fix apart from "start again from scratch".

This thing has had more reboots in the last week than my Windoze box has had in a year.

It still will not talk to my Belkin Wireless router on the upstream properly, and the logs to trace errors seem to have gone AWOL and the tools to investigate either do not exist on the distro, and don't install cleanly through Ubuntu software manager or apt-get.  I have problems with apt-get and dpkg EVERY day.

Using the supplied application to burn an ISO just creates beer glass coasters.

It is truly shocking.  For the first time in my life I just advised a mate to go and buy a copy of Windows 7 as Linux looks pretty much stuffed right now.

Mark Addinall.

I'd suggest you start a support thread, although it does look like you just created your account in order to complain.

---

### Post by oscarivera9 on 2012-01-30
I upgraded from 11.04 flawlessly.  The only problem, which looking back is no big deal, was that the upgrade took too long.  All in all, I am pretty satisfied.  Especially after the awful experience I had upgrading from 10.10 to 11.04, but that's another topic.
After the upgrade was completed, I had ZERO complaints. 
I hope it's all the same when I go to 12.04!

---

### Post by oscarivera9 on 2012-01-30
> **cariboo907 said:**
> I'd suggest you start a support thread, although it does look like you just created your account in order to complain.

I do agree

---

### Post by addinall on 2012-01-31
> **cariboo907 said:**
> I'd suggest you start a support thread, although it does look like you just created your account in order to complain.

You asked...

"Share with the community your Oneiric Ocelot install/upgrade experience"

Does that translate into...

"Please say nice things about us"

Because if so, you need to point out to the general public that the forums are encoded.

Now, not alluding that you are a BAD person, until this little interchange, don't know you from a bar of soap.

I ran 10.x on my Acer, and it was OK.  The only problem I had with that installation was that SOMETHING was leaving 2-8GB files in /tmp and not cleaning up on reboot.  I never did figure that out, although didn't look very hard.

Now the old Acer, after lugging it around the world for 5 years, 1 MOBO, 3 CPUs and a disk later, it was about to become a Norwegian Blue.

So I went and bought a BRAND NEW Toshiba Satellite Pro with a 4 core CPU and a squeaky clean 500 MB drive.

Downloaded the ISO and did a clean install.  The install went fantastic.  I let it run, never touched the partitions or any 'custom' fiddling (I wanted to see what the partition table was going to look like).  So the load looked great!  REBOOT.

Unity is really, really bad.  If it makes you feel better, Gnome 3.2 under Fedora is worse.  I didn't think it was possible.  What is wrong with the people doing MMI these days?  Bizarre....

Anyway.  From a clean install:

1. Firefox would either
   1.1  Flash has crashed.  This was either every five minutes, sometimes on launch
   1.2  Lock the whole system.  Power cord time.
   1.3  Just dump itself out of memory and refused to come back.

2. Installed Chromium
   2.1 Same as Firefox, just much worse

3. Installed Chrome
   3.1 Same as Chromium

Googled around for a long time and found a reference to a version of Firefox that was supposed to fix these problems, so,

4. De-installed Firefox
  4.1 wget the new version
  4.2 try to install it using dpkg

5. dpkg broke on dependencies.  Removed all Firefox, Chromium and Chrome by hand.  Went round and round in circles for a while
   dpkg --configure -a
   apt-get clean (or apt-get auto-clean)
   apt-get -f install
   apt-get update
   apt-get upgrade
several times, until the thing seemed to stabilise for a while.

6. Used Nautilus to get the 'NEW" Firefox.
    Installed new Firefox.  A bit better, only crashed every hour.

7. Move over to Gnome classic presented some bizarre half-implemented system that bore no resemblance to 10.x Gnome.

8. After the move to Gnome classic, system became even more unstable.

9. Moved back to Unity.

10. Brasero didn't work out of the box.

11. Belkin wireless router would no longer UPLOAD.

I stuffed around with it for a few days until I dumped the lot and installed Fedora 16 and the horrid Gnome 3.2 interface.  Apart from the MMI, Fedora installed, everything worked including the PAE kernel.  Virtualbox installed cleanly, Solaris chugging along inside.  Wireless router works again.  The last boot was the PAE kernel source load.
Fedora seem to have got it right.  This hasn't always been the case.  I threw Fedora/Red Hat in the bin during 2005ish when KDE went berserk, and the RPM client and database came broken out of the box.  I liked the simplicity of apt-get, and when I chose Ubuntu 10.x for my last few machines, I did so because it was the best distribution on offer at the time and for a deal of time.  As Fedora seems to have found the error of their ways, Ubuntu has been broken.  Which is rather sad as it was a nice easy to live with distribution.

I started using Linux 30th January 1995.  I remember it quite well as it is my birthday and girlfriend bought me a BRAND NEW server.  On went Red Hat!  And I stayed more or less Red Hat until they broke it a decade later.

Prior to that, ran my first UNIX box in 1986.  So I have been around for a while, and this installation was the most painful EVER.  Reading through the Google results on error searches, and reading through this forum, it seems I am not alone and 11.10 does have some rather large quality issues that need addressing.

So don't get snippy.  If you think you might not like the answer, then don't ask the question capiche?

Good luck with it.

Mark Addinall.

---

### Post by cariboo on 2012-01-31
@addinall, I didn't suggest that we didn't want to hear about your experience, it's just that I find it unusual as a new member you managed to find the Cafe and post your experience. Most of our members have no idea the Cafe even exists.

My suggestion to start a thread in the support section was to help you get things working the way they should. I've been using a a Linux distribution since 1998, there are still many things I don't know, and I usually learn something new from our members daily.

---

### Post by addinall on 2012-02-06
> **cariboo907 said:**
> @addinall, I didn't suggest that we didn't want to hear about your experience, it's just that I find it unusual as a new member you managed to find the Cafe and post your experience. Most of our members have no idea the Cafe even exists.

My suggestion to start a thread in the support section was to help you get things working the way they should. I've been using a a Linux distribution since 1998, there are still many things I don't know, and I usually learn something new from our members daily.


I lurk, a LOT.  When things look a little odd, I GOOGLE and read, and read, and read.  I have known about the forums for quite some time, never felt like posting, just used it to troubleshoot in the past.

Indeed, learning new things on a daily basis is the way to go, and I am sure that your members have a lot to offer.

However, this distro was BROKEN. Given thirty years as a systems administrator, if I load an OS and can't get a bloody browser to work, out of four different browsers, then something is very, very wrong with the OS.

Good luck!

Mark Addinall.

---

### Post by Wild_Duck66 on 2012-02-07
Hi, I use Kubuntu.
My ageing Acer laptop upgraded OK, my newer Acer Desktop did`nt. I ended up with a black screen and a Nepomuk stopped working and mail watcher messages. I did a clean install and it worked but still with the same messages every boot. I evently read how to change Nepomuk permissions so it did`nt run.
Now it works fine.

---

### Post by GraeW on 2012-02-07
clean install on my acer aspire 5050 (about 5 years old) .. no real issues to note with the install - I am trying to work on a few things which are hardware related, not Ubuntu. Overall, Ubuntu has been a good experience this time around.

---

### Post by grovenor on 2012-02-07
Upgrade has disabled my "evolution" although it still shows in the menus it doesn't open. The software centre shows it as not installed but the installer does not work, flags up a conflict of some sort. Currently I am having to get my email via webmail and its getting irritating.
regards
Keith

---

### Post by cariboo on 2012-02-07
@grovenor, if you post a support question with the error you're getting, you should get help installing evolution.

---

### Post by roachk71 on 2012-02-10
I've been in the habit of using a fresh installation instead of an upgrade for several years, regardless of distribution; this procedure has always worked better.

As for 11.10, I believe we should have stuck with the 2.6 kernel for the time being, until some of the wrinkles (bloat mainly) have been ironed out. Unity also needs more work; it and GNOME 3 are kinda sluggish together.

Still, not too bad an experience, given the Samba server works flawlessly in Oneiric, whereas its development has apparently stalled in Lucid. :mrgreen:

---

### Post by Flazer on 2012-02-11
upgrade on my main Linux machine went great. no noticeable issues. fresh install on new reborn net book went well with all different flavors, except kubuntu.  kubuntu gave me issues on both machines after updating packages post install.  currently running ubuntu on older lapper and Lubuntu on the net book (a few minor bugs)

---

### Post by rich52x on 2012-02-14
Installed well onto the laptop, but been getting random CPU spikes every 15-20 minutes which will render the computer inoperable for around a minute. Kinda odd. When I check system monitor its says the system monitor is what's causing the spikes. Which is equally odd.

---

### Post by cariboo on 2012-02-14
> **rich52x said:**
> Installed well onto the laptop, but been getting random CPU spikes every 15-20 minutes which will render the computer inoperable for around a minute. Kinda odd. When I check system monitor its says the system monitor is what's causing the spikes. Which is equally odd.

Open a terminal and try **top** instead.

---

### Post by pootan on 2012-02-17
I did a clean install of 11.10 and had no major problems. Getting my desktop resolution set to 1920x1080 was a hassle, but fortunately I had kept a copy of xorg.conf around and was able to paste in the required letters to get it working. Unity was a bit sluggish so I decided to try out Gnome 3 which ran decidedly better. 

I really miss having Ubuntu Tweak around as it provided an easy method to workaround a lot of minor annoyances, but again, there's nothing that can't be solved with a quick search online.

---

### Post by Guilden_NL on 2012-02-17
I've been on Ubuntu since Gutsy, and have nine client systems (7 laptops, 2 desktops).

Oneric was the most problematic by far, introducing all sorts of problems that made me wonder if I had downloaded a very old version. (I had all the right versions)

It didn't matter if it was an upgrade in place, or a clean install, Oneric was a royal PITA for me.  One system took me three days to fix after a clean install; the list of problems was so long, there isn't enough web space here to list them.

Name a subsystem and Oneric croaked on them: keycodes, RAID, video, wireless firmware problems that haven't existed in three years, etc etc.

After a brief rest, I plan to begin looking elsewhere.  Lubuntu offered a desktop that I can live with, but the underpinning of Ubuntu means my search will go on.

---

### Post by eternalnoob on 2012-02-18
](*,)Worst experience yet. I'm almost tempted to go back to M$.
I've been using Ubuntu since 7.04 and there has been a big improvement in every release - up until 11.04.
I'm still using 10.04 for my every day computing on my desktop. I have a clean install of 64 bit 11.10 on 2 separate hard drives, one in my desktop and one in lenovo T410 laptop.
The Good
--------
Install was trouble free
All hardware detected and worked OOTB, graphics card, printer, scanner, wifi.
Browsing and office suite work fine. The reason I switched to Ubuntu was I resented paying for an operating system (Windows) and then paying more money to do something with it (MS Office)
The Bad
-------
Completely unusable
1. Display
Unity / Compiz crashes every time I even think about changing the settings. The furthest I have ever got is to get wobbly windows and burn on close working at the same time. I have spent days trawling the forums and tried dozens of fixes some of which totally trashed my install. It probably wasn't totally necessary but it was easier to do a clean install. I've done it so many times that I've now started to use Clonezilla to backup and restore the whole partition. I also use a little script I found on the web that resets compiz back to defaults.
If I try and save my progress as a profile ccsm crashes and when I restart the new profile is displayed as hieroglyphics Has anyone else seen that?
What's with the scroll bars? They are different on almost every window and they are all useless.
Why on earth is the application menu at the top of the screen and only visible when you hover over it. Unless your application is maximised the menu is completely detached from the application it belongs to.
I've figured out how to resize the launcher icons, but not the dashboard icons. On a 24in monitor they are way too big.  
2. Audio
Playback works OK but I can't record anything. I have a collection of vinyl that I have plugging away at for years converting to mp3 or ogg. Each release of Ubuntu has got steadily worse since 8.?? where I was able to record and edit with Audacity via line in. In 10.04 I had to resort to "record what you hear" and use a separate editor to split the tracks. In 11.04 and 11.10 I can't record anything
3. I can't get mono to work with KeePass 2.
I haven't been able to get past the video and audio problems to explore any of the other features of 11.10 and I've now pretty much given up and resigned myself to waiting for 12.04.

---

### Post by Robynsveil on 2012-02-20
Did it work flawlessly? -- Clean install, flawless.
Did you have problems? -- One major, the rest very minor
Did you manage to solve the problem? -- Yes
If yes: how? -- The problem was that I use two monitors (laptop base and accessory monitor) - 2nd monitor didn't work. I didn't use Ubuntu for a long time (years?). Then, I installed the Cinnamon desktop and voila: sorted.

---

### Post by Gael33 on 2012-02-20
> **Guilden_NL said:**
> I've been on Ubuntu since Gutsy, and have nine client systems (7 laptops, 2 desktops).

Oneric was the most problematic by far, introducing all sorts of problems that made me wonder if I had downloaded a very old version. (I had all the right versions)

It didn't matter if it was an upgrade in place, or a clean install, Oneric was a royal PITA for me.  One system took me three days to fix after a clean install; the list of problems was so long, there isn't enough web space here to list them.

Name a subsystem and Oneric croaked on them: keycodes, RAID, video, wireless firmware problems that haven't existed in three years, etc etc.

After a brief rest, I plan to begin looking elsewhere.  Lubuntu offered a desktop that I can live with, but the underpinning of Ubuntu means my search will go on.

I understand where you are coming from as I too had problems with the 'new' Ubuntu. I downloaded a copy of Mint 12 (Lisa) and have stuck with it since. It's stable, uses Gnome 3, everything worked straight out of the box, as they say. I didn't like Unity after trying it for several weeks. Somehow, it just seemed like a work in progress and as an author I wanted something that works now. So! Linux Mint 12 (Lisa) ... I suggest you give it a try :)

---

### Post by Wraakvol on 2012-02-24
I installed Oneiric without problems, and it worked flawlessly... :D

I had problems, but just because I'm a Ubuntu noob... :lolflag:

I solved it, anyway... How? Well, I forgot to create a swap partition, but playing with GParted I created it. Those notebook manufacturers, they put 4 partitions at once... :mad:

In summary: I have a long journey through the Ubuntu universe... :)

---

### Post by musicman10489 on 2012-02-25
I installed onto a Macbook Pro 8.1 which is notorious for having wifi issues. I was utterly saved by this wonderful article, though :D

[http://www.ubuntubuzz.com/2011/10/macbook-pro-wireless-broadcom-bcm4331.html]("http://www.ubuntubuzz.com/2011/10/macbook-pro-wireless-broadcom-bcm4331.html")

---

### Post by Max Blyss on 2012-02-29
Installed 11.10, Unity broke.  Installed Linux Mint 12.  Gnome 3 broke.  Reinstalled 11.10.  OS somehow erased itself from HDD!?  Reinstalled LM 12.  Gnome 3 broke AGAIN.  (There were more issues besides, but they were either small or fixable.)

Swore off all Unity / Gnome 3 tomfoolery.

Installed Xubuntu 11.10.  Installed Compiz & Metacity.  Changed a couple startup items, and...

EVERYTHING has worked PERFECTLY.  FLAWLESS VICTORY.:guitar:

I think that being as I own PC's and not an EFFING TABLET, I think I am going to turn my 'Swear Off' of Gnome 3 and such into a flat - out boycott.  If I wanted something pretty and sickeningly fragile, I'd have taken up Bonsai instead of computers as a hobby!:lolflag:

---

### Post by Robynsveil on 2012-03-01
> **Max Blyss said:**
> ...think that being as I own PCs and not an EFFING TABLET, I think I am going to turn my 'Swear Off' of Gnome 3 and such into a flat-out boycott....

Something I don't get. If development in Linux Desktop towards tablets was a direction Ubuntu wanted to go, why not create a special branch for that? instead of subjecting PC users to this "technology"?
Just askin'...

---

### Post by cariboo on 2012-03-01
> **Robynsveil said:**
> Something I don't get. If development in Linux Desktop towards tablets was a direction Ubuntu wanted to go, why not create a special branch for that? instead of subjecting PC users to this "technology"?
Just askin'...

That is exactly what is happening, the current Unity interface is horrible on tablets, there will be a tablet version available soon.

It seems someone mistakenly decided that the Unity interface was designed for tablets, and the way blog posts are syndicated, this assumption was spread all over the web, and seems like everyone is saying this, when in reality it is only one or two bloggers that made the mistake, especially seeing as they at the time had never even tried Unity.

---

### Post by Robynsveil on 2012-03-02
Thanks Cariboo - I was wondering it that whole tablet-interface idea was just someone's take on where things were going (i.e., with Unity) vs what the Ubuntu team were really trying to accomplish.

---

### Post by madjr on 2012-03-02
> **cariboo907 said:**
> That is exactly what is happening, the current Unity interface is horrible on tablets, there will be a tablet version available soon.

It seems someone mistakenly decided that the Unity interface was designed for tablets, and the way blog posts are syndicated, this assumption was spread all over the web, and seems like everyone is saying this, when in reality it is only one or two bloggers that made the mistake, especially seeing as they at the time had never even tried Unity.

yes, and we should also note that **the desktop is not going anywhere**.

tablets are not going to "kill" laptops or the mouse :)

In fact most companies are not even selling that many. Is just another option and an alternative to netbooks (which didnt die either).

and seeing **ubuntu for android**, the desktop is the future on smartphones too.

unity has some elements that are touch friendly, but that doesnt mean is optimized for tablets. Is mainly a mouse OS.

if anyone wants to try linux on tablets they should use **Kde's Plasma Active** for now.

---

### Post by Max Blyss on 2012-03-02
nevermind, lol.

---

### Post by dave2001 on 2012-03-04
After running Oneiric on my test machine for awhile, I'll be interested to see where Ubuntu is going with the next LTS. Although, if it's more Unity crap, I may be checking out Fedora or OpenSUSE instead. Unity just gets more useless the longer I try to work with it. If I wanted an OS that was confusing and limited my ability to control things, I'd go pirate the latest copy of Mac OSX.

---

### Post by cariboo on 2012-03-05
Unity is here to stay, but you don't have to use it. Try one of the other members of the Ubuntu family.

---

