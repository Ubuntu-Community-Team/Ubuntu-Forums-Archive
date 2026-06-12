---
title: "Feisty Poll"
date: 2007-04-20
forum: The Cafe
---

### Post by Guns90 on 2007-04-20
I'm trying to find out just how good feisty is. I've never done a poll before.  Hope this works.

---

### Post by Big_J on 2007-04-20
This isn't exaclty a poll, but here goes
I HATE FEISTY!!
I wasn't even trying to upgrade to it, and somehow a security update for Edgy released with it completely destroyed my edgy.

---

### Post by wizardofyendor on 2007-04-20
Feisty is great!!!, it's much faster then edgy on my box.  It even works with pSX (playstation one emulator) that wouldn't work in edgy (sound underrun errors).  I've had no complaints.

I don't recommend an upgrade though... I was running the Official Nvidia drivers with XGL, and during the upgrade everything related, to Nvidia and Mesa3D failed to upgrade.  then after reboot, I had to title bars on any windows O_o...  but after a backup, fresh install of feisty, then a restore, I couldn't be happier.

(note it's always best to partition your self, and give around 10-20 gigs just to the home directory.  makes backup and restores easier.

---

### Post by OmniCloud on 2007-04-20
Yeah I agree with the user above, I don't recommend an installation from the update manager if you have heavily customized your Ubuntu with stuff like Beryl and what not. But if your an average user, it's definitely an improvement. 3D desktop is standard as well as the wiggly pages....Some more surprises will surface I'm sure.

---

### Post by wizardofyendor on 2007-04-20
One thing I've noticed is when I enabled desktop effects (compiz) it was slower in feisty then it was in edgy.  I tried it with the default video driver, the restricted video driver in the repos, and the official nvidia driver.  I believe compiz and feisty by default uses ALGX and not XGL, and I know in edgy I was running XGL.  is ALGX slower on nvidia cards then XGL?

---

### Post by Emx on 2007-04-20
I'm upgraded to Feisty for more than two months, and I've **never** experienced any problem at all.

---

### Post by wipeout140 on 2007-04-20
I am just amazed how good 7.04 is when i think i paid £60 for Windows XP back in the day and Ubuntu is free and better then vista ever could be

BTW I voted for: *I did a clean install and everything is fine.*

---

### Post by mpvano on 2007-04-20
UPDATE: I guess you could move me into another column of your poll....

The grub boot issue was resolved after I did a full BIOS reset (removing the battery and resetting everything). I'm guessing it was a weird plug and play issue and had nothing to do with Feisty.

The blank screen issue can be worked around by removing the splash screen option from the Grub menu entry.

Otherwise, things are now working fairly well. Congratulations to the team, (but I hope someone looks into the video problem).

mpv


----- The previous content of this message was ------

Tried a clean, plain vanilla (all defaults) install into a Dell Celeron 2400 using a drive known to be good 40gb WD drivethat had previously been used, but was NOT being booted from, so it may have had a virgin boot sector. The install used the entire disk using guided partitioning from the released Desktop disk. Install is on SDA1. (This seems a little odd to me, since it's an IDE disk - is everything remapped to SCSI now?)

Two unusual things: There is NO floppy (but it's disabled in the bios) and there are TWO  Optical drives (a DVD on the second IDE as master, and a CD burner on the same cable as secondary). There's no secondary on the first IDE.

After the install, the boot loader fails silently before the Grub menu and dumps things back to the BIOS error message.

The Dell was originally configured to use IDE 1 with a high density SINGLE DRIVE cable and the drive was set for cable select (as is usual on these machines). Switching the drive to MASTER makes no difference. The optical drives use a low density cable and Master/slave jumpering.

Grub code APPEARS to be installed correctly into MBR. (At least I can read it back using DD, and it looks like it contains a GRUB error message).

The fresh install WILL boot to HD from install disk "boot from first hard disk" option (which uses grub install on CD). HOWEVER, during the entire boot process, the screen is blank until X starts.

Note that the splash screen problem also occurs when booting from either of the released CDs, so something seems to be seriously wrong with the boot code's use of the intel video card. Changing the AGP aperture and legacy video memory size make no difference at all.

Disabling the splash screen from CD grub command line shows bootup normally.

Several attempts to reinstall GRUB from the recovery menu on Alternate startup disk succeed, but do not change the outcome.

It looks to me like the grub MBR boot code may be buggy - this code is rarely installed except on virgin disks with no partition table, since if there's code there, I believe it's left alone.

There seem to be a LOT of reports of problems in this forum that may be related to this issue - most solutions seem ot involve workarounds rather than recognizing the problem.

I'm going to try a few more things if I get time, but there's something definitely seriously wrong with the release on this very common machine. (I have two more of them and they're both currently running Debian Etch with no problems when dual booting alongside XP).

Mario

---

### Post by Guns90 on 2007-04-20
Thanks for all the info Mario.  If you haven't yet, you should report it as a bug.  Thanks  

Gary

---

### Post by frodon on 2007-04-20
@mpvano, is your problem only that you have a buggy splash screen ?

If yes just set the resolution of the splashscreen to one supported by your screen and graphic card. Open your menu.list file (it's in /boot/grub/menu.list) then find the line which start by :
```
# defoptions=quiet
```And add this at the end of the line :
vga = 785 for standard vga
vga = 788 for 800x600
vga = 791 for 1024x768 *
vga = 794 for 1280x1024

Your line will look like :
```
# defoptions=quiet splash vga=791
```Then run a "sudo update-grub" and you should be good to go.

---

### Post by Linuturk on 2007-04-20
I attempted an upgrade from a heavily custom edgy. It took forever to download all the packages, and it then hung up on "Installing powernowd config file"

I had to boot to recovery mode, burn the iso I had downloaded from the cli, and do a fresh install. My home is on a seperate partition, so it is just a matter of reinstalling the apps I need.

---

### Post by chakkaradeep on 2007-04-20
I have encountered few bugs

1) [Synaptic proxy authentication integration]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/105415") - This is there in both of my fresh install box and upgraded box (from edgy)

2) [Video does not work with Desktop Effects enabled]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/102290") - This is there only in my fresh install box

3) [No Beryl Menu Icon to start Beryl and also no Beryl Panel Icon]("https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/108076") - This is there only in my fresh install box

Other than these for my fresh install box, things are good.

It seems that Upgrade is working better than Fresh Install :)

---

### Post by TheTuna on 2007-04-20
I did a clean install, and in hind-sight, it really was easy.  BUT... I thought there was something wrong.  I WAS WRONG.   Read on...

During the install, the computer hung at 85%.  I waited quite some time and convinced myself that the install had hung.  I reset the box and started again.  Again, Hung at 85%.  No activity on the drives for what felt like way too long.   Hit reset again.  You guessed it.  Hung at 85%.  Went to kitchen, got cookies (chips ahoy) and a glass of 2% milk.   Sat down and looked at the screen.  Hung at 85%.  Smiled and said to myself, I'm glad I'm doing this on a clean hard drive, and took solice in the fact that Edgy sits waiting for me, and all I have to do is plug that SATA drive's data cable back in and hit reset.

Found the remote for the TV, called my lovely girlfriend and just about the time I was going to power off the box and switch cables I hear drive activity.  Feisty returned from the land of the lost and completed the install.  Those cookies tasted just a little better right about then.

Ok, so I voted for Clean install with a few problems, but actually, my impatience and lack of faith was the only problem. 

I must add that I was expecting the ATI Radeon X-Windows issue I read about yesterday.  Didn't happen.  I even got beryl running on the first try.

My Hardware:

Home built: AMD Sempron 2800+, ECS Nforce3-A, ATI Radeon X1300 Pro with 256Megs video memory.  1 GB DDR400 (single stick).  On-board sound, on-board LAN, wired connection to RoadRunner high speed internet.  Wireless Keyboard and Mouse.   19 inch monitor running 1280 x 1024 at 75Hz.

Everything worked. 

When I installed Vista on the same box, I struggled with networking and sound issues, when I installed XP on the same box, I went through 12 hours of cussing and throwing fits.  MB issues, no audio, video card issues, networking was a nightmare.

---

### Post by mpvano on 2007-04-20
You know, I would, but I've never been able to figure out how to use launchpad. It seems designed to prevent bugs from being reported by anyone except the development team.

How on earth can I GUESS what package to report this problem against? If you don't have the "correct" answer you can't report it, and if you "guess" wrong, they just blow off the problem.

Perhaps the development team shouldn't expect us to do our own triage this way. They're the only ones with a CLUE what they've changed? I, for one, have NO IDEA what they've added to Feisty's boot process and they're not telling yet. How can any of us be expected to know what package is broken?

How about a simple form for reporting bugs in layman's terms directly from this forum? I stopped reporting them about the time we switched to launchpad and the bug reporting process became a big secret that no one can find (it used to be an item iin the forum menus, but I guess they didn't like getting so many bug reports!).

Mario

---

### Post by savagenator on 2007-04-20
i have had enourmous xorg problems in edgy, but got them fixed with some extra xorg.conf entries, and now all i had to do was install the nvidia drivers in fiesty (couldnt boot into the GUI) and its fine

---

### Post by got_nix on 2007-04-20
fell asleep during the upgrade :(.. and it stalled on one of them popup questions.. hopefully by time i get home it'll be finished had to leave it to go to work.

---

### Post by tombott on 2007-04-20
WOW!!!
Superb stuff, did an upgrade from 6.10 everything works without any problems!!!

I have an Acer Aspire 9500 with ATI Radeon Mobility x700 Graphics card and it works perfectly without any fiddling! This is the first Ubuntu release to work straight away for me!

I'm very happy!

Thanks to all the dev's for making this possible!

---

### Post by brew1brew on 2007-04-20
I've done a clean install on i386 and upgrade on amd64 and both went without issue. 

It just works.

Les

---

### Post by JustinAlf on 2007-04-20
The upgrade for me was horrible.  I tried three times to upgrade.  It hung downloading files everytime.  I downloaded the ISO and installed from it and everything went fine.  But the upgrade was a nightmare of errors.

---

### Post by Fuzzy Logic on 2007-04-20
I have problems, too bad. I expected that it would all go fine knowing Ubuntu so far, but it didn't. Here's a list of all my probs: [http://ubuntuforums.org/showthread.php?t=415173](http://ubuntuforums.org/showthread.php?t=415173)

---

### Post by el_itur on 2007-04-20
I have very little problems after an update using the alternate cd method my probs are listed here [http://ubuntuforums.org/showthread.php?t=415188](http://ubuntuforums.org/showthread.php?t=415188) and if anyone bothers to take a look I will be glas.

Anyway I think the upgrade process is getting better with each relaese. And feisty looks very good in overall. A lot of polishment has been done on gnome side.

---

### Post by MCGrunge on 2007-04-20
Sadly I clean installed Feisty on a Vista/Edgy dual boot machine, and my Feisty partition refuses to finish booting.  Still waiting for a reply to my problem thread.  Sorry, I have to vote for clean install with major problems.  :(

---

### Post by niteice on 2007-04-20
I learned several very important things last night:

1) If you have a highly customized install (or in my case, I had upgraded 6.06.1->6.10) the upgrade may very well fail.
2) They say to keep /home on a separate partition for a reason.
3) A fresh install can be really frustrating once you realize how little is there by default compared to what you had before.

---

### Post by SittingCrow on 2007-04-20
My WiFi card dont work on festy clean install, on Edgy worked fine.

---

### Post by jsully1 on 2007-04-20
Feisty's Ubuntu Beryl package does not support Xgl, which took me a bit to figure out.  You need to force a downgrade of beryl-core.

Sound is very broken and any programs that try to play sound hang.

Network Settings hangs.

Not a good experience so far.

---

### Post by ajifans on 2007-04-20
I'm afraid that Feisty is the first ever Live CD to fail on my machine; not impressed!

It breaks down and I get the following error message:
/bin/sh: can't access tty: Job control turned off

This is being covered with on several other threads.

---

### Post by Npl on 2007-04-20
I have 2 HDDs:
1 Sata, which I use for Windows & Linux
1 ATA, for Backup & Data

Now Feisty deceided that it should install the Bootblock to the ATA-Drive, even my Computer doesnt boots from that drive. The priority is reversed in Ubuntu compared to the Bios, so you got 2 options:

1) install GRUB to ATA, and you wont be able to boot into Linux
2) install GRUB to SATA, and you wont be to boot into Linux or Windows (or any other OS).

Ofcourse I dint knew this and directed GRUB to the SATA-Drive. Great feeling if the only thing you can still run is the damn LiveCD. I mean its explicitely stated that detecting Bootpriority when running in Linux is unsafe! As Ubuntu is relying on it, the Installation procedure can be nothing but unsafe either, when running from LiveCD.
Theres no warning or even a hint in case something turns out wrong, I dont consider consider that User friendly. 
How about defaulting to making a boot-floppy if the slightest chance exists that the Bootorder is guessed wrong? 
How about asking the user to specify or correct the Mapping of drives ?
How about backing up the Bootblock to Floppy or Stick in case something goes wrong?
Beeing pretty amateurish when it comes to Linux I had a great time fixing that mess, so consider Im pretty pissed at yesterdays installation-torture. So I voted "Clean install with a lot of problems"

Further I moved the LiveCD to USB-Stick and installed from that ( I was planning to use persistent mode, but that aint working). After installing I had an entry in fstab that prevents the USB-Stick to be mounted.

---

### Post by wlp1979 on 2007-04-20
I did an upgrade from Edgy (6.10) and the only issue I had was due to a corrupt download.  As soon as I cleared the apt-get cache and downloaded a clean version of the remaining updates, everything went fine.

---

### Post by spaceghoti on 2007-04-20
Upgraded from 6.10 to 7.04; server connections were a bit flaky but I chalk that up to everyone hitting them at the same time.  Once I was finally able to finish downloading the updates installation went smoothly.  I had a few moments of panic when I wasn't sure how to respond to a few dialog boxes, but apparently I made the right choices because now my system appears to work better than ever.

---

### Post by cogadh on 2007-04-20
I've been trying to do a clean install and it has been so difficult that I've begun to call Feisty by a new name:

**Ubuntu Vista**

---

### Post by slugicide on 2007-04-20
I can't vote because I can't install since the live CD loads into a black and useless screen on my Dell E1505.

---

### Post by Bungo Pony on 2007-04-20
Installed Feisty on a brand new hard drive this morning. It seemed to jam at 85% and I thought it was buggered. But I gave it the benefit of the doubt and waited since this is more of a Windows trait ;)

Lo and behold, it picked back up again and finished the install. I have a nicely functioning Feisty, and my sound card works by default (it didn't in Edgy). Good job to the developers!

For those of you who's fresh installs are going wacky, try checking your burned CDs (there's an option on the live-cd boot). Also, I found that burning CDs at slower speeds makes them more reliable.

---

### Post by D@X on 2007-04-20
PC 1 - desktop @ work: I tried to upgrade from Breezy (5.1) directly to Feisty (x86). (Just wanted to test it, since i did not make upgrades for it for a looong time LOL). Did not work well. X and Networking were totally messed up. I decided to make clean install of Egdy (not Feisty), which went well. PS: Considering how old this PC is (RAM:256, GPU:MX400, Athlon XP 1+GHz), installing and runing beryl on this is SCI-FI, but i got to tell you - it's working fantastic. Ofcourse, i made backup before i tried to upgrade from Breezy to Feisty :D

PC 2 - new server @ home: Just got some hardware yesterday, so i decided to put it together. I made fresh install of Feisty x64 server, and it went pretty smoothly. I have some sort of USB Flash card reader installed on it, so this makes some errors, but nothing too scary. It was expected, so to say.

PC 3 - old server @ home: This one had Edgy x86 Server on it. I made upgrade, not a single problem. Nothing to say more. Everything is working as it was ... me very happy. :D

PC 4 - desktop @ home: This PC will get fresh copy of Feisty desktop tomorrow morning. I am too tired. Going to sleep now :)

Regards,
Dax
(yeah, i have many PCs)

---

### Post by drewbie03909 on 2007-04-20
I ran the upgrade from the update manager.  Edgy to Feisty.  Perfect!  Not a problem - what an improvement over the Dapper - Edgy upgrade process.  Nice job devs! [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by JackOfAllGames on 2007-04-20
I'm trying to install Fiesty right now. I can't get the installation to format the drive though. =/ I've run SpinRite, reinstalled Windows, the drive seems fine. No luck with Fiesty yet. =/ I AM new to Linux in general so I don't know too much yet...but yeah, still trying to get my drive reformatted and Ubuntu installed.

---

### Post by tommcd on 2007-04-20
> **Bungo Pony said:**
> Installed Feisty on a brand new hard drive this morning. It seemed to jam at 85% and I thought it was buggered. But I gave it the benefit of the doubt and waited since this is more of a Windows trait ;)

Lo and behold, it picked back up again and finished the install. I have a nicely functioning Feisty, and my sound card works by default (it didn't in Edgy). Good job to the developers!

For those of you who's fresh installs are going wacky, try checking your burned CDs (there's an option on the live-cd boot). Also, I found that burning CDs at slower speeds makes them more reliable.

Does anyone know why it hangs at 85%, and how long this is supposed to take? I always do a clean install from the alternate CD. It hung at 85% with "please wait...". I waited for an hour and a half. No drive activity or nothing. Finally gave up. I then did a clean install from the live CD. This time it installed in about 30 minutes with no hanging or slowdown at all. Both CDs md5sums passed. Option to check CD for defects on bootup also passed.
For those who hung at 85% how long did it take? Is it trying to download updates during this time?

---

### Post by AndrewNi on 2007-04-20
It seems to work... my internal Broadcom wireless card wouldn't work (it only worked with ndiswrapper in edgy anyway) but interestingly neither did my Netgear WG511T (which did work in edgy out of the box). I found some threads about the Broadcom card and a deb package, and now the Broadcom card works natively but no other card #-o 

Apart from that no odd things yet, ACPI on the laptop doesn't work at all anymore though :confused: 

Have to see how it goes, I can always reimage back to my backup of edgy.

---

### Post by karachuonyo on 2007-04-20
I have 2 computers (desktop and laptop) which i had to upgrade. Did a clean install on both of them and everything seems to go on fine despite a tendency to go to sleep at 85% install. However on my laptop when i tried to boot into my new OS   after installation i got an error stating "boot hard disk sector invalid". When i boot from the alternate cd and select to boot from the first hard drive then all is well and i 'm met with the familiar grub OS selection screen and all is well. Scratching my head at the grub issue but i'll try to get around it. All in all fiesty rocks and seems to be an improvement on edgy.

---

### Post by eapache on 2007-04-20
I did a clean install, and I had a few problems, but none of them were Ubuntu's fault. First time I burned the cd too fast and it got corrupted. Second time I got some dirt on it, and it gave me an IO error. I cleaned the second cd, and tried again and now it works like a charm.

I'm particularly impressed by the 3d desktop effects. I'm using a radeon 7200 and 384MB of ram, which won't even run Vista Home Basic, let alone the new aero theme, but Feisty with FX doesn't even slow it down. Very impressive.

---

### Post by MintabiePete on 2007-04-20
I ran the upgrade from the update manager,  Edgy to Feisty also  ,  only problem was  to date  the  gnome-screensaver , but  changed it to xscreensaver ,  which for me  fixed up the  screen  going blank .

Congratulations on a  fine  distro :guitar:

---

### Post by Av8or1ab on 2007-04-20
I tried to do a clean install and none of them would work.  The live CD's gave a xorg-server failure using all of the different versions (Ubuntu, Kubuntu, Xubuntu, Alternate). I even did a command line install which went fine until I tried to install ubuntu-desktop and got the same xorg crash as will the install CD's.  I love ubuntu and have been running the beta with no problems, but after the anticipation of doing a clean Fiesty install I was very disappointed. My hardware is a Dell E1705/9400 with an ATI X1400 and Core Duo processor which shouldn't have mattered considering the beta's all worked. 

I am still pondering why the betas worked but the final distro didn't.

---

### Post by The Pinny Parlour on 2007-04-20
Not overly impress at all so far,  things broken, graphics display issues, eye candy issues.  argh.  why oh why did I bother upgrading.

---

### Post by rainwalker on 2007-04-20
I know the upgrade is prone to errors if a lot of stuff has been heavily customized, but what qualifies as "heavily customized"? I think the most I've done is set a different icon for Firefox and the OpenOffice.org apps.
Also, if I have Beryl installed right now (on Edgy), does that complicate the upgrade process?

---

### Post by boarderpatrol on 2007-04-20
Rain,  

   My thoughts on that would be yes.  I ran an upgrade from update manager, recieved all the files, no problems until I got this error.

   [B]Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/Release](http://ubuntu.beryl-project.org/dists/edgy/Release) Unable to find expected entry  main-edgy/binary-i386/Packages in Meta-index file (malformed Release file?)
  [/B] 

so i cannot finish the upgrade.  I uninstalled beryl from pc an reran upgrade to feisty but same error.

I voted. upgrade with errors


edit uncommented reference to beryl repo in sources.list  BAM 
       install is ongoing.   I am so gonna have to change my vote now.

---

### Post by Xenaco on 2007-04-20
I upgraded Ubuntu 6.10 Server to Ubuntu 7.04 Server today.  I updated and upgraded 6.10 before proceeding to do the upgrade.  I made sure to install the latest update-manager-core (0.56). I used the "do-release-upgrade" as instructed on at [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

After upgrading the computer reported starting Ubuntu 7.04.

I entered 'uname -a' and the system reported that it was using Linux 2.6.17 instead of the 2.6.20 core described in the upgrade specifications.

What's up?  Anyone else notice this?

---

### Post by wataboutbob on 2007-04-20
Done a clean install and except for the video resolution problem - fixed by inserting native resolution in xorg.conf - I have an almost perfectly working Feisty installation with Beryl to boot.

Almost I say? Its Amarok! Don't know why it gets unresponsive when skipping to the next song or when populating playlists. Thats the only problem.

---

### Post by lilagaurangadas on 2007-04-20
I did an upgrade from ubuntu ultimate as I liked very much how nice it works ,was a bit disappointed when I did not see VirtualBox but I had noting to worry about,I just did a reinstall and am very happy with the result!

---

### Post by plafuro on 2007-04-21
Upgraded a not-so-tweaked 6.10 installation  to 7.04. And had a couple of problems:

ati fglrx driver -> got it working using the usual procedure ([http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide))

beryl + XGL -> worked again after following the beryl/feisty installation how-to (had to downgrade beryl-core to version 2.0 - [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)).

ndiswrapper + wpa_supplicant -> Driver worked almost exactly as before. Now i can see signal strength in network manager (before i couldn't), but i can not connect to WPA networks (not nice...).

---

### Post by Crosbie on 2007-04-21
As with plafuro, my ATI xgl setup and Beryl installation was borked and I followed similar steps to fix it.

Was dumped to a completely blank screen on first load-up - would have scared the bejeez out of a less experienced user (I'm no Linux guru)... but then again, I'm guessing it was the customisation that did it.

Interestingly, Compiz worked sooner than Beryl, and I gather optimisations in Feisty for Compiz are the culprit for knackering Beryl.  Might there have been a cleanly-presented question prior to installation about whether to install or not, as there is when you 'enable desktop effects'?

---

### Post by cascader on 2007-04-21
[B][COLOR=Red][SIZE=3]Upgrade Edgy to Feisty on LG50A not going well !![/SIZE]
[/COLOR][/B][COLOR=Red][COLOR=DimGray][SIZE=1]
[/SIZE]After reading as many posts as I could take, it appears that for a lot of ppl the Upgrade goes well, and for the rest, which is a lot of ppl as well, the Upgrade stuffs up.
[SIZE=1]
[/SIZE]Last night as I was cleaning up before bed, I noticed that little beacon telling me that there is a software update ready. But this time, instead of an update an Upgrade awaited me. So, after an overnight of 'Upgrading' my poor little overworked machine it refuses to work properly. And I cannot sit up in the luxury of my lounge to check the forums because the wireless is not working. So downstairs and online I am.
[SIZE=1]
[/SIZE]Of course, I should have checked the forums first. Bugger !
[SIZE=1]
[/SIZE]I haven't had to configure my wireless so far. From MS then migrating to Linux (except, of course, the early days) so far the wireless gets found - easily. So, as always with Linux, the research must begin to get that working. I am busy, so I do not have time to figure out yet another aspect of getting-Linux-to-work. Now don't get me wrong, Ubuntu does everything that I need to be productive, way better than anything that MSCorp has to offer, I cannot understand why Edgy isn't in every home, school and Government.
Anyways, getting off track . . .
[SIZE=1]
[/SIZE]I also noticed, as my laptop [/COLOR][/COLOR][COLOR=Red][COLOR=DimGray]tiredly shut [/COLOR][/COLOR][COLOR=Red][COLOR=DimGray] down, that some of my previously installed programs, including acroread - I print everything to PDF - was being uninstalled - this is not a bonus. I just hope it hasn't ripped out my other Adobe programs . . . 
[SIZE=1]
[/SIZE]**[COLOR=Red]So, the main points seem to me to be;[/COLOR]**
[/COLOR][/COLOR][INDENT][COLOR=Red][COLOR=DimGray]**[COLOR=DarkGreen]Do not upgrade to Feisty Fawn if your Edgy installation is heavily customised.[/COLOR]**[/COLOR][/COLOR]
[COLOR=Red][COLOR=DimGray]**[COLOR=DarkGreen]It might be ok if your Edgy install is pretty vanilla.[/COLOR]**[/COLOR][/COLOR]
[COLOR=Red][COLOR=DimGray]**[COLOR=DarkGreen]Be ready to reconfigure your wireless after Feisty install.[/COLOR]**[/COLOR][/COLOR]
[/INDENT][COLOR=Red][COLOR=DimGray][SIZE=1]
[/SIZE]As per usual, and I don't quite know why I did it this time, but I was tired and only really trying to get an Update. But, **[COLOR=Red]Upgrading is NOT a good way to go[/COLOR]**. If the Upgrade download is about the same size as a fresh install disc, do the fresh install. As long as your data is on a different hard drive as well as your home partition (and if it isn't, why isn't it ?) then clean install has to be better. Just got to be prepared to spend a day tweaking to get it right.
[/COLOR][/COLOR]

---

### Post by SwordRaven on 2007-04-21
I had to reinstall fglrx and downgrade Beryl but then all was well. It even fixed GNOME which I had broken previously :P

---

### Post by Bungo Pony on 2007-04-21
> For those who hung at 85% how long did it take?

It fell asleep for about 2-3 minutes for me.

---

### Post by Snowcat on 2007-04-21
I upgraded, it worked well (except for one non critical package which gave an error and I had to fix later) and Feisty seems to run much faster than Edgy did. My language settings, however, gave an error and disappeared, so I had to reinstall and reconfigure everything (which took like 5 minutes, no big deal).

Overall, everything seems fine, for now.

---

### Post by karachuonyo on 2007-04-21
> **Av8or1ab said:**
> I tried to do a clean install and none of them would work.  The live CD's gave a xorg-server failure using all of the different versions (Ubuntu, Kubuntu, Xubuntu, Alternate). I even did a command line install which went fine until I tried to install ubuntu-desktop and got the same xorg crash as will the install CD's.  I love ubuntu and have been running the beta with no problems, but after the anticipation of doing a clean Fiesty install I was very disappointed. My hardware is a Dell E1705/9400 with an ATI X1400 and Core Duo processor which shouldn't have mattered considering the beta's all worked. 

I am still pondering why the betas worked but the final distro didn't.

maybe just do a clean install with the beta cd then upgrade any updates. From what i understand there is very minor difference with the final release except for some bug fixes. Hopefully you will then end up with a working fiesty. For me fiesty rocks:guitar:

---

### Post by mvo on 2007-04-21
Hi,

I would like to encourage people with upgrade problems to report errors against the package that fails or against update-manager. Please always include the logs in /var/log/dist-upgrade so that the problems can be adressed.

Thanks,
 MIchael

---

### Post by Guns90 on 2007-04-21
Looking at the way the poll is going, I find it interesting that it matters not whether one did an upgrade or a clean install, the 'everything is fine' category is almost identical to the 'had/still having a lot of problems.  It appears to me (and believe me, I'm no expert) that it depends on the pc/laptop that its being put on.  Maybe from here on everyone should list their hardware.

---

### Post by WhimpyPeon on 2007-04-21
I started the upgrade and went out to dinner.  When I got back I had to answer a couple of configuration questions and wait about ten minutes for the configurations to finish.  Rebooted into Feisty without a hitch.

---

### Post by Guns90 on 2007-04-21
WhimpyPeon, please list your hardware.

---

### Post by Kuoi on 2007-04-21
I did an upgrade from Edgy 6.10 to Feisty Fawn 7.04 , and all is still working well !!!

I only had to edit the Grub again , but that's not an issue.
I didn't wanted to do a fresh install , because my Edgy was working very well , and was not much customized , but a bit 'configured'.
I can't see that much difference between Edgy an Feisty , but according to what I read , that must be because of my configuration and customisation.
I can tell it's faster then Edgy , for me it's about the only difference , but again , that must be my pc ... and I refuse to do a fresh install :-)
It's working like I want it , and that's fine for me.
90% of my time I spend on my computer is in Ubuntu , the other 10% is in Windoos , mostly for my minidisc needs.

Motherboard : AOpen AK77-8XN
Processor : AMD Athlon XP 2100
Videocard : Geforce4 mx440 128 MB 
Soundcard : Aureon 5.1 PCI  ( with Optical Input and Output ! )
DVD-Writer : NEC ND-4551A

Greetings , Kuoi

---

### Post by Big_J on 2007-04-21
I did a clean install on my desktop. It's running beautifully and much smoother than Edgy. I liked it so much that I upgraded my laptop. The upgrade was just as smooth as the fresh install. 

Kiba dock stopped working and no decorations showed up when running beryl, but a little tinkering with xorg.conf and all is good. Much smoother than Edgy. 

With edgy, I had some issues where my laptop would randomly freeze or suddenly restart as if overheating. Yet to happen with feisty!

---

### Post by W@LT on 2007-04-21
An interesting poll which indicates that upgrades possibly need a little more attention before they get released..

57% of people (who have replied to this poll) having / had issues is far too high!!!.. that is over half!!! (I was good at maths)

My upgrade was done via the Upgrade Manager... spent the best part of half day getting the thing to re-boot and maybe another day downloading a shed more updates that I missed!!

However... when I compare this to the issue I had / still have after upgrading to Vista there is no comparison..

Have succesfully migrated away from MS now.. with few exceptions Ubuntu is worth its weight in gold...

I just have to master VirtualPlayer / box !!!

---

### Post by HaoTian on 2007-04-21
Upgraded from Edgy to Feisty this morning.  Was a little nervous, as I had a hell of a time figuring out how to get my video working, etc.  I'm happy to say everything went absolutely perfect.  I've never had an upgrade go so smoothly.  Not a single error, and everything booted up great first time.

Things I noticed immediately: Networking is so much better.  I couldn't get Samba to display the computers on my Windows network for all the trying I did.  As soon as my computer rebooted, I opened my Networks, and all of the machines showed up instantly.  Yay!

I'm using an Acer Aspire 5110.  Dual core AMD 2ghz, 2 gigs RAM with an ATI 256mb video card.

---

### Post by Big_J on 2007-04-21
> **frodon said:**
> @mpvano, is your problem only that you have a buggy splash screen ?

If yes just set the resolution of the splashscreen to one supported by your screen and graphic card. Open your menu.list file (it's in /boot/grub/menu.list) then find the line which start by :
```
# defoptions=quiet
```And add this at the end of the line :
vga = 785 for standard vga
vga = 788 for 800x600
vga = 791 for 1024x768 *
vga = 794 for 1280x1024

Your line will look like :
```
# defoptions=quiet splash vga=791
```Then run a "sudo update-grub" and you should be good to go.

It's menu.lst not menu.list

---

### Post by FLJerseyBoy on 2007-04-21
System is a Dell Dimension 4550 (2003 vintage), 1GB RAM, 120GB HD, Dell flat-panel monitor (nVidia card + driver), LaserJet 2100 and Epson Stylus cx5200 multi-function. Dual-booting between Windows XP and (now) Feisty. (Installed Edgy, my first Linux, a few months ago.)

Used the built-in upgrade rather than a clean install. Kicked things off 2007-04-19, ~10pm EDT. Two problems so far, neither major:
[LIST=1]
[*]Took a LONG time to download, over a DSL connection.
[*]NTFS partition wasn't visible at first.
[/LIST]
The "predicted" download time was laughably offbase; it said something like 1h45m over a DSL line, 1 DAY+ over a 56kb dialup line. It actually took 24 hours. I attribute this less to a true "problem" than to trying to get the darned thing on release day.

One thing I noticed yesterday in posts on this and other threads was that the upgrade/install (other than from CD, I mean) seems to have hung up for a lot of people. Over the course of the 24 hours I thought mine had frozen, too, but patience carried the day. Advice: If you're going to upgrade via an online process -- at least until the initial upgrading frenzy is over -- figure on not having access to that computer for a day, at least, and be thankful for anything less than that. BE PATIENT. Note that the download information panel includes two pieces of information: "downloading X of Y files," and estimated time left. The latter detail was crazy to watch, even as it got down to the last few minutes -- it would say, like, "15m25s," and then suddenly go down to 9m, and then back up to 12m, 20m, down to 18m, and so on. 

(It's possible that the download time is refreshing too quickly; it seemed to fluctuate every couple of seconds and hence was highly susceptible to little blips up or down in latency. Much better, I'd think, to refresh based on say a 2-minute (or more!) cumulative average speed.)

As for item #2 above: On the first system restart following the upgrade, the system went into disk-diagnosis mode (or whatever it's called) before booting into the GUI. It failed to recognize the NTFS partition, however. I confirmed, by booting into XP, that the partition itself was safe. While in XP went online and found that ntfs-3g was built into Feisty (I'd installed it myself in Edgy), but that ntfs-3g.org had (since I installed it) added a GUI "ntfs-config" tool. Booted back into Feisty. Found ntfs-config in Synaptic, installed it, and used it mount the NTFS partition. This took a couple of tries because although the "windows" mount point wasn't recognized as a valid NTFS partition, that NAME for a mount point was still claimed. So I've currently got a working "windows3" mount point as well as non-working windows and windows2 versions of it. :)  Presumably I can correct the latter by unmounting them and remounting windows3 as plain-old windows.

Those were the ONLY problems I've encountered. (So far, true.) The first one was resolved by doing nothing other than leaving the computer alone; the second, by doing about 10 minutes of research and another 10 minutes of tweaking. (And the latter, strictly via GUI.)

YMMV but that was my experience.

---

### Post by WhimpyPeon on 2007-04-21
> **Guns90 said:**
> WhimpyPeon, please list your hardware.
Toshiba Satellite A135-S4499 Laptop
Intel Core 2 T5500
2GB Ram

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by TheThirdBardo on 2007-04-21
I have just upgraded from Edgy to Feisty (Kubuntu). No problems at all with the upgrade process.

The only minor issues were three, all related to non-standard software:

First Opera, which was removed and I had to search around a bit to get it fixed. Found that it is featured in something called automatix, which took some searching in the forum and adding a new repository. Now Opera works ok.

The other minor problem was with Freevo, which uses it's own repository; it got removed during the upgrade process, and afterwards I had to change the repository-line to use feisty instead of edgy, de-install some freevo-related packages (because of some dependency problems), and reinstall them again.

A problem which is yet unsolved is with Lirc (infrared remote control support). I always have the same problem when I upgrade the kernel, because Lirc is distributed by source code which must be compiled by hand. This seems like the only thing which needs a bit more researching before everything works like before the upgrade. [Update: this is now fixed after a quick search in the forum]


I voted for "Had a few problems (drivers, hardware, etc) but got them fixed" by the way.

---

### Post by Tine on 2007-04-21
I installed via update manager.
I had problems with nvidia drivers and Beryl.
But those were rather easy to fix, now feisty is working just fine.

Much easier upgrade than dapper->edgy, then **** hit the fan big time and i was so close to change back to windows... But after doing clean install it was smooth again.

Upgrade problems seem to be very common here which is bad.
Ubuntu has image for being suitable for n00bs but when noobs upgrade they don't order problems because it maybe difficult to fix these problems.
So maybe something should be done for upgrade process. It shouldn't be pain in the ***.

---

### Post by arvster on 2007-04-21
I did a clean install on an Acer laptop that I have. It had Arch Linux there before, but I thought that it was not really suitable for that laptop, as my family also uses it and they don't want to touch the terminal or bother with wireless configuration etc., so going back to Ubuntu for that laptop seemed like a good idea. 

So the desktop cd wasn't usable in live cd mode- resolution in X went out of range, for some strange reason other terminals didn't work too. I still wanted to try it, so I got alternate install cd. Installed it, but again, as I booted,  the resolution went out of range. This time I went to terminal, installed Ati drivers, reconfigured xorg.conf (I took it from my previous working Arch install) and everything worked. Apart from that everything else works.

If I would be a new user or wouldn't know Linux, I probably would have given up though. The laptop has a Ati X700 card, so it is not that uncommon at all. Also other distributions don't really have a problem with it; only other Ubuntu releases in the past had had similar problems before. That is definitely a thing to work on- detecting monitor and graphics card and automatically configuring xorg doesn't seem like a difficult task, compared to other hurdles that Linux has to jump. Also that is a thing that gives the first impressions to a lot of new users, so it should be the thing that gets a lot of attention and testing. These are just my impressions with Feisty, apart from that it is a really nice release and everything else works fine. My desktop stays with Arch though- it is even nicer :P

---

### Post by frodon on 2007-04-21
I just finished the upgrade on my edgy box and feisty is working really well, i don't see anything wrong for the moment.

---

### Post by frogotronic on 2007-04-21
Feisty is amazing,


Edgy was crappola - upgrading from Edgy didn't work at all - in fact upgrading from dapper to edgy was a hassle.  Feisty rocks.

---

### Post by suziequzie on 2007-04-21
I did a clean install on my /testdrive partition (a 10GB partition dedicated to trying out new/different distros) using the Alternate 386 Install CD.  I must say I'm impressed with the ease of installing multimedia and restricted codecs.:KS

I'm going to be testing this release for about a week or 2, and when I'm confident it's good and stable I'll be doing a fresh install over my Dapper partition. Home is it's own partition, so I should have no worries there.

---

### Post by jonl3379 on 2007-04-21
Clean install on Gateway laptop. I consider myself technically proficient (using Ubuntu since the very beginning hoary/warty or whatever).

This is a pretty bad release as far as polish goes (apparently all the effort was on the Gnome side of the house... everything on the KDE side is broken to heck). No automatic codec downloads for MP3 or sound/video. Hanging Azureus, hanging Amarok, hanging Adept! Still the problem with the "external amplifier" on the laptop sound (why? why?).

Automatix is a chainsaw when the solution calls for scissors. Installed but didn't use.

Compared to Edgy, it seems slower and more busted (upstart is much slower now). Did I mention Adept hangs?

I hate to imagine that Michael Dell is using this on a laptop right now because it's a mess for me. I'm tempted to try openSUSE again, ugh (ugh, because Novell bites).

Another annoyance: 915resolution breaks after a crash (also note I'm describing a crash).

---

### Post by static chaser on 2007-04-21
Upgraded and everything is working fine! Had to turn a couple of things back on but everything is ok

---

### Post by Belyel on 2007-04-21
Wow, the feisty upgrade went 1000% better than my edgy upgrade.  I upgraded my desktop, pretty standard but with two monitors.  I only had to download and install the envy script to get them working again.  Cheers to the devs!

---

### Post by quixote on 2007-04-21
The only choice for problems under "clean install" is "lots."  I'm not having lots of problems.  Just a few, but they seem kind of intractable.  Installed automatix, clicked the link for installing Sun Java runtime env, and it hangs at the stupid "agree to idiotic license" dialog box.  Automatix, and Apt-get then keeps trying to complete the install whenever I try to fix it and hangs at the same point.  Now I can't install anything the nice easy way!

I gather the java jre thing is a reported bug.  Hopefully it'll be fixed soon!

My other big problem is my wireless chip, uses the Broadcomm driver which means all sorts of manual futzing that I haven't got to because of the install problem.

I love Feisty, though.  Both versions, kde & gnome, look gorgeous and work well in all other respects.

---

### Post by nabla on 2007-04-22
First distro to ever get suspend to ram working for me, Edgy didn't work there either. Couldn't be happier.

btw I have a dell inspiron 6000.

---

### Post by Elrohir on 2007-04-22
This has been happening since Herd4, at least on my laptop...

Toshiba Satellite A105-S361

I HAVE NO SOUND!
According to alsamixer this are the specs:```
Card: HDA Intel
Chip: Realtek ALC861
```I downloaded the ISO and got it burned on a CD, popped it in and same with live, no sound... Which makes me not to trust much on Feisty... ALL I'M ASKING IS FOR SOUND! anyone having the same problem? anyone got a solution for it?

---

### Post by Kuoi on 2007-04-22
> **Elrohir said:**
> This has been happening since Herd4, at least on my laptop...

Toshiba Satellite A105-S361

I HAVE NO SOUND!
According to alsamixer this are the specs:```
Card: HDA Intel
Chip: Realtek ALC861
```I downloaded the ISO and got it burned on a CD, popped it in and same with live, no sound... Which makes me not to trust much on Feisty... ALL I'M ASKING IS FOR SOUND! anyone having the same problem? anyone got a solution for it?

I pressume you did a fresh install ?

I'm sure if you search this forum , or start a treath about your sound problem , that you'll have sound soon .

Greetings, Kuoi

---

### Post by konDA on 2007-04-22
I did a clean install from alternate CD (x86), I had only 1 problem with ATI card. But thanks this help [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) I fixed it :)
Feisty is great!
Ondra

Asus f2je, core 2 duo T5600, 1.83 Ghz, ATI X1450

---

### Post by boz on 2007-04-22
The only problems I had were with restricted modules (NVIDIA and Atheros drivers) and I was warned the modules wouldn't be installed during the upgrade.  Otherwise, it was a very clean upgrade.  Kudos to the developers.  Very well done.  I like the new restricted modules manager, too, by the way.

---

### Post by karhulitos on 2007-04-22
Ugrade from Edgy to Feisty on Acer Aspire 5040 laptop went without actual upgrade problems.

I don't have lot's of problems but I have no sound. So this must be a bug of somekind. Originally tested with Herd3 live CD, then sound was OK (tested again today with Herd3 CD -> sound just as good as in Edgy).
Tried all comprehensive sound guides, etc.. no help. No sound for hda-intel.

Also I cannot logoff for another user to login, screen goes blank. Don't know if this is related to sound problems.

So I need to say that first impression with Feisty is a bit worse than with Edgy.

---

### Post by topic58 on 2007-04-22
I guess it's like always with Ubuntu - the second edition works much better. Like 6.10 Edgy compared to 6.06 Dapper. And in october will 7.10 Gutsy Gibbon come. And most certainly that edition will be just fine. So I will wait until then. :lolflag:

---

### Post by blue_shift on 2007-04-22
Upgraded on my desktop, and ubuntu decided to change sound devices and use my pci card not mobo sound. Weird.

---

### Post by fjm03 on 2007-04-22
Miss Beryl and VMware. Waiting for solutions to both problems.
Didn't understand why the O/S reported a connection to local  network when there was no connection (router turned off during install).
Network interface no longer asks for workgroup ID for use on mixed network.

---

### Post by jonl3379 on 2007-04-22
If you have sound issues on a laptop, right-click your speaker in the notification area / system tray... hunt around the options (a lot in gnome, a little in KDE) until you see "External Amplifier" and uncheck that box. That fixes mine every time.

---

### Post by edonnelly on 2007-04-22
Too bad there is no "dead in the water" option on the poll. I did an update manager upgrade, things went without a hitch and I got to the point where the computer reboots, and now the computer won't boot at all (gets to grub, but all option just lead to black, unresponsive screen with a blinking cursor). I have no idea what went wrong and no real ability to debug anything right now. Maybe I'll download a live CD and see if I can get into the logs (or maybe it's not worth the effort). Edgy (without any customizations) had been working fine*. Now I need to decide if I should clean install back to Edgy, or try to clean install Fiesty (Fista). To add insult to injury, I am only able to post here and download whatever fixes I might need by using an old Windows machine. Bugger...

emachines T2385 

*Note to self: when computer is working fine, DON'T MESS WITH IT!

---

### Post by SimonV on 2007-04-22
Still doesn't work for me.
I'll be glad when the /bin/sh get's fixed.
Ubuntu looks nice, but the other distros which do work with sata, p965 are beginning to look appealing.

---

### Post by jarekl on 2007-04-22
> **edonnelly said:**
> Too bad there is no "dead in the water" option on the poll. I did an update manager upgrade, things went without a hitch and I got to the point where the computer reboots, and now the computer won't boot at all (gets to grub, but all option just lead to black, unresponsive screen with a blinking cursor). I have no idea what went wrong and no real ability to debug anything right now. Maybe I'll download a live CD and see if I can get into the logs (or maybe it's not worth the effort). Edgy (without any customizations) had been working fine*. Now I need to decide if I should clean install back to Edgy, or try to clean install Fiesty (Fista). To add insult to injury, I am only able to post here and download whatever fixes I might need by using an old Windows machine. Bugger...

emachines T2385 

*Note to self: when computer is working fine, DON'T MESS WITH IT!

Funny, I was looking for that option too. I'm actually still running dapper since it has become impossible to upgrade that to anything. Think I'll do an upgrade to mandriva. Use it at work since 6 or so years. Upgrades without a hitch every time. It's just that I've put so much work into this install (mythtv especially). This truly sucks.

---

### Post by edonnelly on 2007-04-22
For me (three posts up) a fresh install didn't work either. All of the menu option on the install disk went into a black hole from which I never escaped. I ended up doing a fresh install of Edgy, which went fine and is now working. So, after about 10 hours total of work I'm (almost, minus a few configurations here and there) back where I started. Not sure what went wrong with this release for me, but it looks like I'll be staying where I am for a while.

---

### Post by jamespi on 2007-04-22
just upgraded my laptop and desktop to feisty, and everything went without a hitch. feisty is SOOO fast compared to edgy it's unreal.

---

### Post by sixstring on 2007-04-22
I did a clean install of Fiesty x86 and x64 and both are unstable and lock up on my machine.  I get these error messages:
```
bug: timer not connected to IO-ACPI
bug: soft lockup detected on cpu#0!
rt61M1meEnqueue: full, msg dropped and may corrupt MLME
```

I searched the forums and found a handful of other people posted about having these exact same errors.  I went back to good ol' Edgy for now and it's still rock-solid.

my machine for whoever wants to know:
amd64 x2 3800+ (dual core)
2GB RAM
ATI x1900xt

---

### Post by GeneW on 2007-04-22
I have had three major problems so far on my IBM T42 and only two of them are solved:

[LIST=1]
[*]Metacity not loading
[*]wm-applet not seeing my network card
[*]No Sound
[/LIST]

I've managed to fix the first two with help from the forums but sound has me stumped.  It looks like the right driver is loading, the mixer is unmuted, no errors but no sound.

UPDATE:
Sound mysteriously started working again, not sure what I did to fix it.

---

### Post by gigmo on 2007-04-22
i did a fresh install on my ps3 . had a few bugs at first but still cant get wifi to work. thats ok i have a cable for now. had to do a few adjusts on video but now it runs at 720p. i like the respons time on evrything , its a lot faster than my old pavillion 6636. running edgy 6.10

---

### Post by Timokl on 2007-04-23
I upgraded with the Update Manager which worked without a problem. But after logging in for the first time, the window manager metacity did not load. When I activated Compiz through GL Desktop, the Metacity windows appeared but no Desktop Effects (I have an ATI card).

I installed the fglrx driver (on Edgy, I used the open source radeon driver) and Xgl, and this seems to have solved this problem.

However, after using it once, the "System" menu is some kinda locked. Let's see whether this is reproducable.

---

### Post by mills on 2007-04-23
its been 1 problem after another sometimes my fault sometimes not, iam in windows again now,(2nd time in a matter of hours) after getting the BROWN screen of death again. i'll sort it out tomorow i think. i need a break

i might try and reinstall again, iam not sure 3 times is enough

---

### Post by darkstarubutu on 2007-04-23
Did a clean install everything worked fine 
Nvidia, sound etc flawless

Only 2 major issues with it
I get some PCI error on boot and ...
I have a Broadcom  BCM4310 and that just aint working 
a lot of users are experiencing this

another day and im taking it off my system :-(

---

### Post by SunnyRabbiera on 2007-04-23
I had major issues with the live, it coughed up a lung when i tried it on my compy.
I had to use the alternate CD despite me having enough memory and stuff to handle Fiesty.

---

### Post by sonnywise on 2007-04-23
I upgraded 2 laptops without any problem !:)

---

### Post by hawa on 2007-04-23
Actually 3 votes

1. New Install on dual boot with raid: still having problems

2. Update from 6.10: crashed not able to recover

3. new install on the crashed : all up and running easy

---

### Post by rush_ad on 2007-04-23
> **hawa said:**
> Actually 3 votes

1. New Install on dual boot with raid: still having problems

2. Update from 6.10: crashed not able to recover

3. new install on the crashed : all up and running easy

1. first tried upgrade --> no go --> stopped in middle, could not recover

2. clean install --> few problems, mp3 codec installer hangs, no thumbnail icons, i have to manually connect to internet everytime i restart, and a few little things here and there

---

### Post by Andrej_BB on 2007-04-23
My Mp3 player is not being detected ( and it was in edgy ), everything else is fine.

---

### Post by mh114 on 2007-04-23
I upgraded, and it went perfectly. :)

---

### Post by GranpaDan on 2007-04-23
I upgraded from Edgy Eft to Feisty, just following the directions, and everything went just fine. I don't use any of the fancy desktop effects because I have an older computer. Ubuntu still works just fine for me.

---

### Post by Simon-v on 2007-04-23
Here's how i broke my Ubuntu.
Being relatively cautious, i planned to try upgrading on the (somewhat tweaked) desktop computer first and if it goes well on the (somewhat less tweaked) notebook as well.
Update-manager did quite well, though the download was mind-numbingly slow. A few simple questions, i'm taking notes on what to re-add into the config files after i have Fiesty running, rebooting, gasping at the beautiful artwork and then... unbelievingly staring at a complete lockup.
Not exactly what i expected.
A few more reboots proved, that it most likely is not a random issue. Reading the forums show that there **might** be a hanging problem. The LiveCD silently fails to load. Strange.
I figure that Fiesty won't work for me and try reinstalling Edgy and remounting /home.
The new installation immediately breaks. Hardware, users - everything messes up. Apparently, using new settings in the old system is not a healthy thing to do, huh? I wish someone mentioned that somewhere. My ideas quickly run out. Oh well. Looks like it's time to start over.

So that's what you get, trying to combine a relatively new computer with relatively new components and a constantly experimental OS? :)

"Could we start again, please?"

[SIZE="1"]Since some of you are asked:
Pentium 4 3 GHz w/ 1 GB RAM, nVidia GeForce 6200, a LevelOne (RaLink RT61) wifi card.[/SIZE]

---

### Post by starcraft.man on 2007-04-23
I tried clean install and upgrade, both failed. The new kernel doesn't like my ATA HDD, I will wait till they fix it.

---

### Post by Impaque on 2007-04-23
Well I have to say that I was a bit disgruntled when I found out that the Kubuntu upgrade wasn't tested thorough enough.

KDE frontend is very buggy and doesn't have proper automation. I had to manually install python-gnupginterface and atop of that, I had to apply a patch to the python update script itself, as explained [here]("https://bugs.launchpad.net/ubuntu/+source/upgrade-system/+bug/108556/comments/4").

I have to point out that my Kubuntu 6.10 was pretty "fresh", ie. I didn't meddle with it, so that couldn't be the case... I had the feel that this KDE updater wasn't tested enough and to fetch 700+ MB of updates from the net was out of the question (I wanted to do it/did it with Feisty alternate CD's package repository and just fetched the remainder off the net).

As I said on IRC, because of this rough upgrade, Kubuntu just felt dirty hackish over Ubuntu's Gnome/GTK, where people didn't have any problems at all?

And in general, KDE community compared to Gnome community is 3:1, if not even more drastic... :(

---

### Post by siucdude on 2007-04-23
WOW, what is so amazing is that most people who posted here with issues, its their first post on Ubuntu,  I wonder!!!!!!

Have fun

---

### Post by Impaque on 2007-04-23
> **siucdude said:**
> WOW, what is so amazing is that most people who posted here with issues, its their first post on Ubuntu,  I wonder!!!!!!

Have fun

Well some of us use search and Google to find solutions to problems and the post above was my 2 cents to this particular topic.

You have fun, too, and don't wonder too much. ;)

---

### Post by nybronx on 2007-04-23
Now I might not be your "usual" user.I wanted to try linux on my iBook G4 and thought I would be spending the weekend. fixing hardware when I installed the 6.0.1 Kubuntu image (couldn't find a fiesty image on any mirrors). But lo and behold, upon upgrading I get a pop-up telling me that a new version of Kubuntu Fiesty for ppc was available. It wanted to know if I wanted to upgrade. Huh...my screen color and size was screwy. wireless nonexistant. Hell Yeah upgrade...Let me say this. All is beautiful on the PPC Fiesty. Quick install of the wireless firmware and my wire free surfing is alive and well. Let me tell you as a PCLOS user I was not surprised. I was SHOCKED that Fiesty did all I wanted and then some. All I can say (tearing now)((really)) Thanks.

---

### Post by Guns90 on 2007-04-23
Well I decided to take the plunge.  I backed up my Dapper system on an external drive and did a clean install.  I have XP on my hda1 and Ubuntu on my hdb1.  (I only use XP for games.)  My modem wasn't recognized initially, but the instructions provided were a fast and easy fix .  Initially, I couldn't access a DVD or my mp3 player, but updating the repositories (medibuntu) fixed all that.  Everything appears to be working fine.  Now if I can just figure out how to replace my home file with the one I backed up.

---

### Post by JoshCrowl on 2007-04-23
I upgraded from edgy and after 22 hours and several blow ups my edgy was gone. So I wiped out the NTFS partition left over from my original Windows setup and did a fresh install from CD and just left my old edgy as my second partition (I’ll move every thing over later.) And with a few more hours of reinstalling all the codec’s ECT… sigh!!! -- Much better!! I like Feisty….

---

### Post by SimonV on 2007-04-23
> **topic58 said:**
> I guess it's like always with Ubuntu - the second edition works much better. Like 6.10 Edgy compared to 6.06 Dapper. And in october will 7.10 Gutsy Gibbon come. And most certainly that edition will be just fine. So I will wait until then. :lolflag:

The problem with that is ofcourse that more and more people are upgrading their computer.
A lot of the persons with a new computer can't get 7.04 working due to the /bin/sh error.
So saying just wait a bit won't work because then they'll migrate to another distro.
If knoppix works then it should be possible to fix the /bin/sh error.

---

### Post by GhostDawg on 2007-04-23
I'm sorry but I didn't read through all the posts. I just did a fresh install of Fiesty and everything seems to be working execpt for it stop booting when it got to my Western Digital external hard drive. I don't quite know what the problem is but when I installed the last beta release, it picked up the external drive without any issues.

Now why wouldn't final release not find it or load the drivers?

Thnx.

---

### Post by DJiNN on 2007-04-23
After upgrading to Feisty (In beta stage) from Edgy, all was working fine & i was well impressed. Then i installed Automatix2 & added a few things & "Poof".... the lights went out & my system wouldn't boot at all. So, i grabbed the new Feisty Download, installed, and now everything is better than it ever was, plus of course, being Linux, you get to keep all your important docs etc whenever you upgrade (Assuming you have a seperate /home of course!) :)

Wonderful!! I personally think that Ubuntu just gets better & better. I keep trying other distros (Zenwalk being my other fave - I'm a sucker for XFCE) but keep coming back to (X)Ubuntu everytime! 

:lolflag:

---

### Post by sixstring on 2007-04-23
> **siucdude said:**
> WOW, what is so amazing is that most people who posted here with issues, its their first post on Ubuntu,  I wonder!!!!!!

Have fun

> ..., and we are not going to make you feel like your lower because you don't know how computers work.

LOL.... right!
Maybe it's their first post because for the first time in a year of Ubuntu they couldn't find the solution after a quick forum search.
But as a p.s. to my first post, I discovered a thread with a solution later after spending more time searching.

---

### Post by Ynem on 2007-04-23
I really like working on ubuntu ever since I installed 5.10, it looks great, its free, doesn't require expensive new hardware. Great in Feisty is the easy setup for codecs.
My only BIG problem with it, is that Ubuntu still cant't handle wireless cards. I tried 4 cards (two USB interfaces) and none of them worked! Once your connected to the internet, you can look up almost everything, but without it, you need another (windows) computer, something not everyone has.

Y

---

### Post by aysiu on 2007-04-23
I've moved this to the Community Cafe, since it's not really a support thread--more of a discussion/experience sharing.

By the way, I upgraded from Edgy way back before Feisty was even beta... on three separate computers, and none of them has had any problems.

---

### Post by Kunstar on 2007-04-23
I upgraded from Edgy and have had the usual screen resolution and touchpad problem but other than that everything has gone smoothly and in no way do the afforementioned problems make ubuntu any less usable.

---

### Post by Malkosha on 2007-04-23
Fresh install of Feisty.

I have an AMD64 3500+, 1G RAM, Nvidia 7600GT, SB Live.

Everything works perfect. I moved the important stuff off the drive, did the fresh install then moved it back. No problems and everything seems to run much faster and far more crisp. I also ran Automatix2 which sealed the deal.

The only problem I have is that between Automatix2 and Feisty itself, the install was done with everything working. Not much to play with or configure. Everything just seems to work. No problems to solve. Bored.

---

### Post by adamJ5 on 2007-04-23
I upgraded, and as a thanks I get the "can't access tty"-error.

---

### Post by angkor on 2007-04-23
I upgraded a couple of weeks ago and everything was fine.

Because I wanted to repartition my disk I did a clean install last week and everything was fine again. Feisty is very nice to me....and fast.

---

### Post by speedygeo on 2007-04-23
Too many problems with feisty?
It is very easy and work out-of-the-box!!
If you want more help try MEPIS. It is more easy.
And in October take kubuntu 7.10

---

### Post by LookTJ on 2007-04-23
I was on Debian Etch. So I did a clean install and everything is great. no problems so far.

---

### Post by Mitlik on 2007-04-23
I had a major problem with some of the default settings in Kubuntu, the ttf-bengali-fonts and by association ttf-indic-fonts caused some sort of error on mine, but working through it with dpkg-reconfigure and aptitude made it so I finally made it through (though I wouldn't say survived, I made the mistake of rebooting and couldn't mount my harddrive less yet get into any version of a kernel) my first dist-upgrade with Linux. Hopefully I survive the next one (i.e. not needing my backups).
  That being said now that I finally have Feisty the it has some easily observable features that I was hoping for, the not so easily observable I probably can't tell you, since I've only been on Kubuntu (and GNU/Linux) for five months I still feel like a complete newb, but I am learning, and wouldn't dream of going back to Windows.

---

### Post by lefty.crupps on 2007-04-23
I was looking for someplace to vent a bit about this! :)

First, I upgraded my Kubuntu Edgy and it failed about halfway through.  I don't even recall what the error message was, but all of the packages had downloaded already so it was in the application of those packages where my first failure happened....

Luckily, I had burned a Kubuntu install CD.  I installed it cleanly and installed everything that I needed.  I rebooted to find my X was dead.  I logged in and it said my Apt wasn't installed, and that i should use Apt to install it!  I struggled here for a bit but nothing worked... I rebooted and got to the KDE login screen, but it wouldn't let me log in.  I chose the Failsafe mode and didn't have a /home/user directory!  So, I became root, deleted my user, created a new one, and rebooted again...

...except that I didn't create a password for that user, and root cannot log in to KDE on his/her own :(  And I never set a root-specific user so in deleting my first user somehow root was left without a password.  Two users, no passwords.

So I installed Kubuntu herd5 and re-downloaded a new Kubuntu and burned and installed it.  So far it seems to work pretty well, but I have had more crashes than I would like to admit.  K9Copy seems to be very unstable (hint: don't touch any of the Settings!  If you do and it crashes without opening, go to your ~/.kde/share/config/ and delete the k9copy files there).  My Media-applet doesn't show DVDs nor does the HAL/KDE popup work for DVDs.  This auto-codec-install thing is a joke in Kubuntu, the stepchild of the *buntus...

Amarok and Kopete have crashed more lately than ever.  My iPod (vfat) keeps mounting as a 'read-only filesystem' so I cannot drop files into it for RockBox to play any new tracks... looks to me like a reformat there, wee-haw.

Over all, I have spent about 10 hours on this and its been a bit frustrating, to say the least.  I have logged about 5+ bugs (i think they're bugs) since I got it running fully, yesterday.  But, I do like what DOES work, quite a bit!

---

### Post by FuturePilot on 2007-04-23
I'm not exactly having any huge problems but there are 2 minor problems that are more annoying than anything else
[LIST=1]
[*]Sometimes when I boot the computer X will start in the wrong depth. I can tell this because all the colors and shading is all messed up. It looks as though it started in 16 instead of 24. Though it can be fixed by restarting X. But it should be doing that in the first place. That has happened to me twice so far.
[*]Usually my external hard drive is detected during boot up and is mounted so it's all ready when I log in. However, I turned on the computer today and the hard drive was not mounted. I had to unplug it and plug it back in. That is only the first time that has happened to me.
[/LIST]

The weird thing is that I cannot reproduce these things. They seem completely random.:confused:

---

### Post by Jope on 2007-04-24
Running xubuntu here..

Tried a clean install of 7.04 on this Dell Latitude CSx, but no go.. All the kernel messages came up and right after it detected the optical drive, it hung.

After trying a couple of different methods I decided I'll go for the upgrade route..

That worked for the most part, but something was wrong with the flash plugin and it constantly hung my browser in youtube and also sleep/hibernate failed to bring back my lucent_cs card.

Now everything seems to work, but those flash videos still don't run as smoothly as they did in 6.10.

---

### Post by Sunflower1970 on 2007-04-24
My two desktops work great with Feisty, and I couldn't be happier. They seem to be faster in bootup, and shutdown, opening programs and the like...and that's no small feat for a PII :)

The laptop has a few problems, though. As long as I didn't use suspend or hibernate things were fine. I also did notice it was running hotter in Feisty than Edgy. In the end I downgraded to Edgy and all is happy again with the laptop.

---

### Post by NeoTaoistTechnoPagan on 2007-04-24
Running great here! I have had no probs at all with any version of Ubuntu! My 1.5TB server runs Edgy ( I see no reason to upgrade it - everything works.) I have installed Feisty on about ten systems now since it hit the servers on 4/19 - and this system is on an external USB HDD on a Compaq Presario C304NR.

I absolutely love it! I can hardly wait to see what comes out six months from now!

If anyone is going to the Ubuntu Live! conference in July - I will see you there!

Hail the Holy Motherboard!

Polk Linux Users Group
[www.mypc.is-a-geek.com](www.mypc.is-a-geek.com)

---

### Post by Sokraates on 2007-04-24
I did a clean install with Kubuntu Feisty Beta and even though everything went extremely well, one regression still causes me a lot of headaches: my wireless won't connect to my router using WPA. WEP works, though.

This could be knetwork-manger's fault, but since I've bee using it since Breezy without such issues, it's still very strange. A few bugs have been reported on this subject and the reason for the bug are still not clear.

A rather peculiar finding, also related to my WLAN (bcm4318), was, that even though Ubuntu brings along a bunch of proprietary firmware and the corresponding drivers, the bcm43xx-firmware was not included. But the driver was. Very strange, since I expected both to be included by now, since the bcm43xx-drivers are quite good. But this is nothing I would hold against Feisty.

Anyway, apart from the regression, Feisty rocks. Actually, even the beta worked better than Edgy final. Two thumbs up!

---

### Post by AndyCooll on 2007-04-24
I did a clean install and voted that everything is fine. And this is almost true. I installed Feisty on 3 laptops and a base unit and everything worked fine apart from a few issues with XDMCP (which I regularly use on my home network)

:cool:

---

### Post by senorian on 2007-04-24
Fascinating poll; and somewhat depressing. Of the "clean installs" about 40% continue to have problems.
An outfit called the "Standish group" evaluate large IT projects and entitled a report "The CHAOS Report"

[http://www.standishgroup.com/sample_research/chaos_1994_1.php](http://www.standishgroup.com/sample_research/chaos_1994_1.php)

That report was not about operating systems but an OS is surely a large IT project.
It seems we have a long way to go before we have OSs that are as reliable as bridges!

---

### Post by aysiu on 2007-04-24
I don't see that as depressing at all.

See, most people who install Ubuntu do not research the most Linux-compatible hardware they can find, buy it, and then install Ubuntu.

They just pick up whatever old computer they have lying around (probably one that came with Windows or Mac preinstalled) and then install Ubuntu on it... *hoping* everything will "just work."

The results are actually quite good.

As of this writing, 40.87% had no problems--that's a combined total of clean installs and upgrades. If you add in the ones who had small problems that got fixed, that total goes up to 64.23%.

---

### Post by braddcadd on 2007-04-24
I wonder what the pertcentages would be if the same random sample of people installed Vista.  My guess is that it would be pretty close due to the same thing aysiu mentioned (hardware, min requirements, drivers,...).

Most windoze users have the OS installed for them!

---

### Post by quixote on 2007-04-24
> **aysiu said:**
> 
I upgraded from Edgy way back before Feisty was even beta... on three separate computers, and none of them has had any problems.

Ah, but look at that 6th dan blackbelt ranking you have.  I'm not surprised none of the installs are giving you a hard time.  What I need to know is how I can do that!  I've had the same problem with wireless not working.  I've also had Broadcomm or Atheros chips, which doesn't help matters.  I'm looking forward to trying my new ndiswrapper with Feisty. :)

---

### Post by Ryzzen on 2007-04-24
Wireless still blows. I thought they were going to fix it in Feisty, but they made it worse. In Edgy, it took me forever to figure out how to get my wireless to work. Once I got it, it was fine. In Feisty, I already knew what to do, so I installed the drivers and got it working. Only problem is, it disconnects after 10 minutes of internet use, and will not reconnect until I reboot. This was most disappointing for me. =/

---

### Post by aysiu on 2007-04-24
I don't have a black belt of any kind (metaphorical or actual), and it wouldn't matter anyway. I'm not saying I experienced problems but luckily knew how to solve them because of some great skills that I have.

I'm saying I didn't have any problems.

There's a difference between having problems that get solved... and not having problems to begin with.

---

### Post by JerseyShoreComputer on 2007-04-24
Everything worked perfect after the upgrade, expect (of course) the wireless. A little tweaking and now it works just fine. In fact, I don't need wifi radar anymore. Turned off roam mode too.

So far, Fiesty is working for me.

---

### Post by Michl on 2007-04-24
I did a clean install on a computer on which I don;'t store very much.

I was going to upgrade on the computer I use for all my work and decided
against it.  It took me a while to get everything to work properly, I use
Shredder Chess with Sun Java -- and I don't want to lose all that with
a dysfunctional upgrade or a clean install.

I did try to upgrade but something failed to fetch, and so I checked here
and I see that there are too many problems with the upgrade method.

I don;t want to be kicking myself like someone above why  in the world
I messed with a smooth system to create chaos.  

One problem with alpha and beta testing, in which I participated.  I don't
remember anyone testing upgrades.   CLean install was tested only.

M

---

### Post by inzpektor on 2007-04-24
I did a clean install on my IBM Thinkpad T41.  Everything was great except that when running Beryl, the windows were sometimes without content.

This is not new to me, I had that problem on Dapper and Edgy as well (probably also in Hoary when I was messing aroung with the xcompmgr).  It's beause my graphics card (ATI Radeon Mobility 7500 - M7 LW) is not completely supported through the proprietary fglrx drivers, leading to the infamous "Nvidia Black Widow Bug" - although it's not an Nvidia card.  All I had to do was to switch to the open source "radeon" driver, and everything was fine.

In fact, the open source Radeon-driver is nowadays at least just as good as the fglrx driver.  That's amazing compared to how buggy it was just a few years back.  Good work!

---

### Post by quixote on 2007-04-24
> **aysiu said:**
> I don't have a black belt of any kind (metaphorical or actual), and it wouldn't matter anyway.  ...

I'm saying I didn't have any problems. 

Surely you know that machines can sense these things?  It's like when you take your broken car to the mechanic and it runs perfectly. :D 

(Seriously, though.  What kind of wireless chipsets were you using?  The notorious problematic ones that don't have Linux drivers, or something more well-behaved?)

---

### Post by aysiu on 2007-04-24
> **quixote said:**
> Surely you know that machines can sense these things?  It's like when you take your broken car to the mechanic and it runs perfectly. :D 

(Seriously, though.  What kind of wireless chipsets were you using?  The notorious problematic ones that don't have Linux drivers, or something more well-behaved?)
Ah, I see what you mean.

It's like when I'm having a problem with the printer at work and call the tech guy over. When he's standing next to me, the printer works just fine, of course...

---

### Post by Handssolow on 2007-04-24
I was looking forward to the day Feisty was on general release, having decided that I'd wait a week or so for the dust to settle, I couldn't wait and upgraded last Friday -- and lost my wireless connection in the process. Thank goodness we have more than one PC at home so I could look for a work round for my RT2500 wireless card, but I am a bit disappointed that I'm now waiting for the developers to come up with a bug fix.

Despite all this it won't stop my continued commitment to Ubuntu.

---

### Post by jimrz on 2007-04-24
3 fresh installs ... zero problems to date. 2 laptops + 1 really old desktop (for a friend who is now trying out ubuntu, and liking it). 2 more to go, but 3 was really more time than I should have done last weekend so these will have to wait just a bit longer.

---

### Post by Tundro Walker on 2007-04-25
See, now this poll misses the critical "middle niche" folks...

I upgraded Edgy to Feisty, and it screwed up.

But when I did a clean install, Feisty worked like a charm.

What button do I click for that?

I wish the poll was more of a "How do you rate Feisty? 1-10..."  I'd give it a 10 so far...

---

### Post by Guns90 on 2007-04-25
Some real interesting posts in here.  Prior to the poll, I was reading a lot of negative write ups on Feisty.  I couldn't believe that the latest release of ubuntu was was going the wrong way instead of making progress.  I had a suspicion that most of the negative reports were from those fairly new to Linux/Ubuntu.  Basically, the poll confirmed that.  In reality, the majority of voters in this poll are up and running with Feisty and all is well. 

As far as I can tell, the only 'problems' that people are having with Feisty is a lack of experience with Linux.  It seems to me that almost all of the so-called problems are unique to individual machines.  I'm not a technician or a programmer, but I have learned through experience that, as hard as manufacturers try, there simply isn't a 'standard' established for every component available to the world these days.  Some things just have to be tweaked, whether it be for Linux, Windows, or Mac.   I can't thank this forum enough for the help it provided me.

For those that have a problem with the install, and those about to install it, I want you  to know that I'm doing everything I want to do (multitasking, photography, mp3's, viop) in Feisty.  Just working through the small problem(s) that you might have is well worth the cost of instead buying newer versions of Windows, Office, and Photoshop,  Hang in there.  You'll get the help you need in here.

---

### Post by Muppeteer on 2007-04-25
Did a clean install of Feisty last Friday, everything wen't pretty smooth. Except i forgot to backup my fonts settings, but it seems people are having probs with Feisty's fonts. Got that pretty much fixed. Had another problem with Beryl not showing window borders, thankfully i backed up my xorg from Edgy and it's all sweet now :) 

Loving Feisty so far, doesn't seem much different from Edgy though :)

---

### Post by MoebusNet on 2007-04-25
Like Tundro Walker said, the poll does not address those of us forced to do a clean install of Feisty because the upgrade killed Edgy. Especially since the "official upgrade" procedure seems to be quite flawed judging from my own experience and numerous postings on the forum.

I guess that makes me just another beta tester, right?

---

### Post by Tachyon_ on 2007-04-25
I really hope I'm the only one with these kinds of **serious nvidia and xorg problems** (BUGS?)

I did a clean install

First, installing the nvidia drivers were essential because I couldn't get TV out. Well, I had hear that feisty had a way to do them "more easily". I had to google that way to find out - I could use the add/remove programs, they were quite more like hidden.

Well, when installed, they didn't work. I noticed in the description do "sudo nvidia-config enable" (or something). Well, I did that. Why didn't it do it automatically?
Okay, that resulted only to the problem. When booting, the usplash stops and I don't get any message, I mean I should get the X errors, which was the problem when running startx. ctrl+alt+f1 (how is an usual user supposed to know this) and sudo nvidia-config (only that, how is an usual...) and dpkg-reconfigure (...) and, I dont have a widescreen resolution anymore.
On the top of that, I think that the automatic beryl is completely pointless. I did that, and everythins goes black without borders. So googling, and I have to add this and that to X.org. In my opinion, there shouldn't be an automatic beryl install, because doing that only results in googling. So instead of googling the right method and getting it work, normal user would just install it to see "it just doesn't work".
Few more hours and those were fixed. And, my TV-out can't use widescreen resolution and nvtv says that my chip is not supported, while it's still quite new. So, no, I'm not brave enough to tray anything "automatic anymore". I had far less trouble even with Gentoo :(

My two very computer related friends did also feisty install, one had an integrated intel laptop chip and one ATI. Well, after using them for a week, both of them had a problem that X didn't come up anymore, resulting in black screen. The second I was able to fix and the other didn't even give an error message. I mean, they worked like a week fine. The other uses Vista and other XP now. And I am not going to recommend feistys cool "automatic"-methods.

I kind of understand the issues and hard things with commercial drivers, kernel and X integration, but, in what I have seen. these automatic things do more harm than good.

---

### Post by mikexgough on 2007-04-25
tis crap compared to edgy............reinstalled edgy until Nvidia issues are sorted.........come on Ubuntu this is a backward step

---

### Post by goumples on 2007-04-25
No problems yet... Drivers and apps and everything else still worked fine when I upgraded.

---

### Post by Tobor22 on 2007-04-25
Having a somewhat quick processor, no fancy hardware (everything integrated on the MB), a fast, stable, internet connection certainly helped me to have a quick (1 hour/ten minutes) trouble free upgrade. :)

---

### Post by michaeljb2005 on 2007-04-26
My computer restarted randomly due to, what it claimed to be overheating.  I had to revert back to edgy.  I saw that there are false alarm overheat bugs in the feisty kernel.  I attribute the problems to those bugs.  When the bugs are fixed I will consider upgrading again.  Otherwise I will wait for gutsy.

---

### Post by beefcurry on 2007-04-26
Edgy was working perfectly for me, now the New Nautilus seems to have a Bug regarding to the trash being on a different file system. So I cant delete files using Nautilus on my NAS. So nope, not everything is working. Performance and difference in user experience is minimal.

---

### Post by kdragon on 2007-04-26
some Fn keys dont work but Feisty is the 1st Linux distributor i love the best,i love it more than vista :D

---

### Post by asphaltjesus on 2007-04-26
First of all, who had the bright idea of automatically asking for an update?  

Judging by the number of failures in the poll, I'd say the release manager(s) didn't do their job well.

This upgrade should have been an optional meta-package.

Thanks for nothing.

---

### Post by McZika on 2007-04-26
I did a clean install, but had some trouble with fglrx drivers. They werent installed right away so the x.session could not load. But now i installed them manually and everything works just fine :)

Go Ubuntu 7.04

---

### Post by en3rgy on 2007-04-26
I upgraded from 6.10 to 7.04 and now when I boot into the OS all I can do is 800x600@50 hz. Weird though that the slash screen appears @ 1024x768.

nVidia control panel wont let me change resolution and says my monitor is @@@ whatever that means. I'm so confused and demoralized. I've spent hours searching these forums on how to fix this problem and have tried so many things like manually editing my xorg.conf file and such and nothing seems to help. I've even tries the "nv" driver instead of the nvidia one. I don't know what to do anymore.

BTW - I am new to Linux and Ubuntu but have a very strong understanding of MS operating systems dating back to DOS 2.xx

---

### Post by karhulitos on 2007-04-26
Upgrade & Acer Aspire 5044WLMi

no sound
no video
no logoff
no wlan (but this was pretty fast fixed)

all others just ok. Will go back to Edgy, in my case best to leave Feisty cooking fo a while

---

### Post by shadowfx78 on 2007-04-26
well i upgraded but havent been able to enable any of the fancy eyecandy like the 3d desktop stuff i have a crappy built in video card in my laptop. the only other problem i have had is sometimes when i resume from suspend the mouse doesnt work correctly its really sluggish and moves eratically

---

### Post by aysiu on 2007-04-26
If you look at [the similar poll about upgrading from Breezy to Dapper](http://ubuntuforums.org/showthread.php?t=187024&highlight=dapper+upgrade), you'll see the results are quite similar (a direct comparison can't be made because there was a "small problems" option, but it made no mention of whether the small problems were ever fixed or not).

The combination of small and no problems was 70.11% on the Breezy to Dapper poll

As of this writing, the combination of small (but eventually fixed) and no problems is 66.48% for going to Feisty.

You figure a margin of error plus the vague phrasing in the first poll (were the small problems fixed?), we could be doing better now, but we're probably about even in terms of success rate.

I think a 66-70% success rate for installations is pretty good, considering most of these computers were built for Windows and are not necessarily compatible with Linux.

That 30% is probably a combination of incompatible hardware, lack of user motivation to the find the solution to a problem, and lack of user ability to follow documentation instructions.

---

### Post by skwishybug on 2007-04-26
Only issue once Feisty was installed was my wireless card (as expected for a broadcomm). Had some issues getting the upgrade to work, had a bad repo list but generating a new default corrected that.

And on a very good note, my IR remote for the laptop works without having to do anything on my part, that is just freakin sweet! :D

---

### Post by tommcd on 2007-04-27
> **aysiu said:**
> If you look at [the similar poll about upgrading from Breezy to Dapper](http://ubuntuforums.org/showthread.php?t=187024&highlight=dapper+upgrade), you'll see the results are quite similar (a direct comparison can't be made because there was a "small problems" option, but it made no mention of whether the small problems were ever fixed or not).

The combination of small and no problems was 70.11% on the Breezy to Dapper poll

As of this writing, the combination of small (but eventually fixed) and no problems is 66.48% for going to Feisty.

You figure a margin of error plus the vague phrasing in the first poll (were the small problems fixed?), we could be doing better now, but we're probably about even in terms of success rate.

I think a 66-70% success rate for installations is pretty good, considering most of these computers were built for Windows and are not necessarily compatible with Linux.

That 30% is probably a combination of incompatible hardware, lack of user motivation to the find the solution to a problem, and lack of user ability to follow documentation instructions.

I wonder how accurate these polls really are. I would think that people who upgrade or install and have no problems are more likely to just go about their business, whereas people who have problems are more likely to search the forums for answers and vote in a poll like this. 
Perhaps we could find a way to survey random forum members via email to get a statistically relevant sample of users to get a more accurate picture.

---

### Post by eriqk on 2007-04-27
Clean install of a commandline system, then installed Xubuntu-desktop.
After startx, I ended up with a resolution of 640x480 and no panels (not visible, anyway). Used the file-manager to find a terminal (didn't find out about alt+F2 until later. D'Oh!) and did a dpkg-reconfigure xserver-xorg. Restarted X and all was fine.
Other than the X issue Feisty is very schmoove.

Toshiba Tecra 8000/PII-300/256MB/Sweex WiFi PCMCIA.

Groet, Erik

---

### Post by Unterseeboot_234 on 2007-04-27
I like Fiesty because of the available packages in 64-bit. Dapper was an 11 minute install from Live-CD, Fiesty was more like 13 minutes. Fiesty is slower booting to the desktop and little slower at shutdown than Dapper. Once Fiesty is loaded, everything is running fast. I appreciate the time and effort Fiesty developers have done for the fonts, colors and overall UI.

But, I was really impressed with how automatically everything went. Boot into Fiesty and the network works, the internet works. Installed Automatix2 to get the codecs and thus far the only problem is trying to remember what it was I did in Dapper to boost the sound volume so I can do the same thing in Fiesty.

---

### Post by Rumor on 2007-04-27
I did a clean install because it seemed easier than doing the much needed housekeeping in my home directory (since 5.10). My only problem is that my wired network does not automatically connect. I have to manually check the radio button in the network manager each time I restart. It is a minor annoyance, but an annoyance all the same.

---

### Post by VraiChevalier on 2007-04-28
Did a clean install of Feisty from CD. Had been using Dapper.

After about a week of trying to chase down and fix a problem with Feisty dropping my internet connection I finally gave up and went back to Dapper. 

Everything works beautifully in Dapper. Oh well.:)

---

### Post by Tux Aubrey on 2007-04-28
I have done 3 installs so far - two upgrades to edgy laptops which were superb and one clean install on a dual booting desktop which was a nightmare for three days trying to fix nVidia driver problems.  

I finally worked it out - no, that's not true - I eventually did something that got me back to 1920x1200 resolution and accelerated graphics (but Beryl won't draw borders etc, so I ditched it).   

Overall, I'm impressed and happy with Feisty.  Many minor improvements such as networking have made it worthwhile.  Oh, and Crack Attack now remembers where it should open on my desktop.  That alone was worth the pain.  I love Crack Attack.

---

### Post by blueturtl on 2007-04-29
For my wife's laptop (Compaq NX6125) Feisty has been a dream-come-true:

- 6.06: I had to enter extra boot-options to make it work (noapic nolapic).
7.04: no more, and the system can now use all the available RAM!
- 6.06: I didn't even dare touch the ATI restricted drivers.
7.04: I had a graphical interface to do it for me and it worked straight away. Working OpenGL, hooray!
- 6.06: I had to mess with ndiswrapper and Windows to get wireless going.
7.04: All I had to do was double-click a single deb file to add the firmware and lo- and behold, the wireless starts working.
- 6.06: I had to enter command line and fiddle to connect to unencrypted networks.
7.04: Sadly, this has not been resolved. I think it's Broadcoms fault though.

The easiest Ubuntu installation ever!

For my main desktop system it's even sweeter since I didn't have any problems there to begin with.
Here I have enabled desktop effects and am now more sure than ever that Ubuntu can take on Vista for the hearts of new users. Many people might say Compiz was the wrong choice, but I think minimalism in effects actually helps keep the system usable. Wobbling windows and desktops on the cube can actually help non-technological people understand the underlying concepts better (multiple workspaces, background and foreground execution).

Hooray for Feisty, it's the best Ubuntu release and IMO the best desktop Linux system to date!

---

### Post by fsando on 2007-04-30
I did a clean install of one of the last betas, so I reckon I did a clean install, not an upgrade.
Feisty is in most ways a decidedly improvement over edgy: It's faster Beryl runs better, the ati-drivers are fine even in xgl. Wireless is a lot better, virtualbox works better. 

Only problem (so far) is the scanner problem but it seems it is at last recognized and the actual bug has been tracked down, so now it is just a question of time before our scanners are up and running again.

---

### Post by sefs on 2007-04-30
anyone having problems related to winbind avahi and samba installed on the same system? where by accessing via the computer name is impossible?

---

### Post by Smaug067 on 2007-05-01
I upgraded and still have some minor problems with  the dreaded NVIDIA driver and xorg, but everything else works great!

---

### Post by deniro0311 on 2007-05-01
I haven't had linux on a non-server system since breezy, and let me just say, I love 7.04.  Holy **** it's amazing.  After fixing the wireless issue, I have only had one problem.  The damn thing froze for some reason.  Other then  that, it's been flawless.  And I love beryl and automatix.

---

### Post by 310ei on 2007-05-02
I&#8217;ve completed clean installs of 7.04 on several used laptops without any problems (Intel P4M-1.8GHz, 512MB, 60GB, 32MB ATI Radeon 7500).

Beryl installation went smooth and easy.

---

### Post by Genican1 on 2007-05-03
I did a clean install instead of upgrading, and have had a few problems.  The switch from hda to sda scared me, my cd burner wasn't detected (had to edit grub), and now when I unmount NFS volumes, my X somehow breaks.  CTRL-Alt-Backspace won't even fix it.  have to do a reboot.  I'm thinking of going back to edgy, or...  switching distros

---

### Post by merlinus on 2007-05-05
Overall, I am extremely pleased, especially to now live in a land without gates, windows, jobs, or apples.

But....

My cd burner has not been detected, and no forum suggestions have made it so.

The power-off-monitor-after-x-minutes feature does not work.

I am unable to access ubuntu from my win2000 box, although it works fine the other way round.

I still need my dual-boot in order to run one important program and burn cds, but otherwise I am very grateful.

-merlin

---

### Post by kelvin spratt on 2007-05-05
i've tried every flavour of linux i tried edgy ended up with The Ultimate Edition the then ugraded it to Fiesty
taking the oppertunity of setting up separate partition never looked back everything has work like a dream
did not even have to play with drivers for my Ati 9600 card i give fiesty 9/10 because nothing is perfect.

---

### Post by noneofthem on 2007-05-05
Fist I upgraded to Feisty and had a lot of problems so I tried a fresh install. Unfortunately that didn´t solve my problem. I did a search in this forum and came to the conclusion that there are more people with the same problems so I filed a bug report. Now I am still waiting. Just did another fresh install.  Here are my problems:  automount of CD/DVD ROM stopped working after updating May 4th. Also I am not able to unmount my external USB HDD. Trying these things manually with the console didn´t help me neither. Hope this will be resolved soon...  Apart from that everything seems to be great. The whole system seems to be faster than any other Ubuntu before and I love the new "Restricted Driver Manager". Helps a lot. Also the automatic codec search and download thing is awesome. If only these elementary issues with the mounting weren´t there I could say Feisty is perfect to me.

---

### Post by Workinman57 on 2007-05-06
Hi all. Did the Clean install, I have an all factory Dell Latitude C840 On Board: 2.0 P4 ,SAMSUNG DVD-ROM/CDRW, 1450 Internal Broadcom chipped Wireless card, 1 Gig of ram. NVIDIA GeForce4 440 with 64 mgs video ram. 15" Screen.  7.04 Runs well very fast. MP3's sound better then when she ran on windows 2000 pro or XP pro. Screen Resolution is 1600X1200 looks Great. I wasnt able to load win drivers for card in 6.10 before with ndiswrapper but in windows it was hit or miss as the card is an ebay white box special. Had no issue in 7.04 USB  Flash Drives work well.

Issues I am Having are: SAMSUNG CDRW/DVD not working correctly think that is caused by SCSI vs IDE recognition. Was able to load a music CD and click though "cant eject" error and ripped the cd to the hard drive and listened to Al Green while working on Bugs. Trying to run beryl but I get a white screen during startup of beryl-manager. Floppy doesn't read disks. Cant hook up to overhead projector for presentations.  Tried to swap Floppy for another CDRW I have for this laptop and it was not recognized. As I said I think issue is in the way 7.04 has setup drives as SCSI instead of IDE. Peace Out!

---

### Post by DraconPern on 2007-05-06
7.04 broke my power off.  As in the computer will no longer power off when doing the shutdown.  Worked with edgy. :(

---

### Post by Sokraates on 2007-05-08
> **DraconPern said:**
> 7.04 broke my power off.  As in the computer will no longer power off when doing the shutdown.  Worked with edgy. :(

I have this problem with Edgy. Haven't updated my Desktop to Feisty yet. In my case the computer begins to shut down, but then hangs at the end of the process.

The real problem is, that this won't happen every time and I haven't been able to find the reason yet. On my laptop I never had such issues with Edgy, nor now with Feisty.

---

### Post by mumushi on 2007-06-19
had upgraded to fiesty but had some problems. one by one i am fixing them now but still notall are fixed.

---

### Post by wxnker on 2007-06-22
Did a clean install and had a few annoying minor problems. Most of these problems were also present in Edgy so I know how to fix them from the command line. These are mainly screen resolution issues and network issues with DNS/nameservers and IPv6.

The only major persisting problem I still have, is "hangs during shutdown, reboot or log out". It's a pretty annoying problem, but I never really found the solution for it. The icons will disappear and I just get the desktop wallpaper, panel etc. CTRL+ALT+Backspace, CTRL+ALT+F2 etc. does not help. Nothing to do but to push "reset" on the PC.

I mainly keep Ubuntu/Kubuntu (Feisty at present)  to follow it's development. It's an interesting, very popular (but much hyped) project and a very nice OS. IMO there are better Linux distro's (that are: working better "out of the box"  on my system, more user/beginner friendly etc.) out there, though. Especially if you prefer KDE.

Feisty has some great features and compared to Edgy it's definitely a step in the right direction, Ubu/Kubu is still not a Linux newbie OS IMO, but it's a damn fine OS if your not afraid of solving minor problems from the command-line.

Looking forward to the next release.

---

### Post by nodcero on 2007-06-22
Same as Sokraates and others: Hangs at the very end of the shutdown-process after a clean install on my ancient desktop. Still a lot better than Win98ME not closing down properly 4 out of 5 times... ;)

Upgrade of Edgy on my laptop worked without a hitch.

So, in my case: multiple options in the poll would have been called for... *g*

---

### Post by rax_m on 2007-06-22
I've clean installed to feisty (b'cos the upgrade path wouldn't work). 
So far i think it's great! Must faster and more stable(?) than edgy. 
Even tho' I said no problems... what i meant is my suspend/hibernate didn't work properly in edgy and still doesn't work properly in feisty ;)

---

### Post by Lord Paladin on 2007-07-03
My transition from Edgy to Feisty has been a nightmare,

I have tried both upgrading and a fresh install my sys hangs randomly locking both my mouse and KB sometimes during boot (with the orange bar) and other-times shortly after login, never lasting more than 10mins.

Searched all over the web and have found heaps of solutions that work for different people but nothing works for me, even Alberto Milones detailed fix did nothing.

Please if anyone has a fix I could try I would appreciate the PM I just want to play WOW again when I get home from work.

---

### Post by Kowalski_GT-R on 2007-07-03
Ubuntu Feisty Fawn clean install and no probs here...:cool:

---

