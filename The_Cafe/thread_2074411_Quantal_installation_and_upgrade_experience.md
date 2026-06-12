---
title: "Quantal installation and upgrade experience"
date: 2012-10-21
forum: The Cafe
---

### Post by cariboo on 2012-10-21
It seems we didn't create one of these threads for the last release, but I was asked to do it this time around.

Please tell us about your experience upgrading, or doing a fresh install of Quantal Quetzal.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

For previous polls, have a look [here]("http://ubuntuforums.org/showthread.php?t=1865027")

---

### Post by dniMretsaM on 2012-10-21
I did a fresh install and had no problems.

---

### Post by PaulInBHC on 2012-10-21
Install went well but system unusable until video driver situation is resolved. Went back to 12.04

---

### Post by vasa1 on 2012-10-21
Fresh install of Lubuntu 12.10 beta 2 followed by updating to the present. Dell 1545 laptop. No problems.

---

### Post by ~LoKe on 2012-10-21
Fresh install of 12.10 went pretty badly.  Failed to update grub on my SSD, so I had to boot the live demo, mount the partition and re-create it.  Fairly unstable after that, but I don't think it's related to the OS itself as I have the same issues on 12.04.

So something about these recent OS's isn't playing well with my hardware.

---

### Post by SantaFe on 2012-10-22
Updated Xubuntu 12.04 with both Xfce & LXDE to Xubuntu 12.10.  No problems whatsoever.  Well, there IS this pesky Lubuntu 12.10 Plymouth log in/log out screen.  Hmmmmm.....

Although after reading all the posts from Ubuntu 12.04 users who upgraded & had problems, I was just a Little scared to try it myself.

---

### Post by IWantFroyo on 2012-10-22
It wouldn't accept my passwords for encryption, root, or user. I was bewildered, and filed a bug report. This was right after it was released.

I'm about to give it another try.

---

### Post by flavouride on 2012-10-22
Noticed linux-headers-generic-3.5.0-17 was removed at the end of installation. Just reinstalled it and installed nvidia-current.

Nothing serious though.

---

### Post by jmull on 2012-10-22
Did two upgrades on laptops running Xubuntu and both worked fine. 

Did an upgrade on my netbook with Xubuntu and the system booted directly to tty1. After messing around with different graphics driver options and going back to kernel 3.2 I was able to start xfce manually from tty1 but with limited functionality. Tried a clean install and had the same issues and decided to revert back to 12.04 until a workaround for GMA35x0 graphics drivers is found to work well. None of the existing fixes worked for me.

---

### Post by kherring7383 on 2012-10-22
I have to admit that I'm a regular Mint user but in the past used Ubuntu extensively and even though I do use Mint, I like to try out a new distro to see how Ubuntu is coming along so so I thought I'd install Ubuntu 12.10 and give a try.

As usual there were several issues that I had to resolve with the Nvidea drivers and getting the splash screen to finally act right. 

And as expected there were new PPAs I had to research since some of the ones I used in for 12.04 couldn't be found but after correcting this, all my favorite apps are now installed and seen to work except one or two that generates an occasional error message which I guess has something to do with compatibility with the app. 

But in spite of these little hick-ups I'll stick with it for awhile since these issues will be addressed eventually. Besides if there's anything Iv'e learned over the years with Linux, is that there will always be bugs for couple of months until there patched with a more stable version. 

As for the Launcher and Dash, personalty I don't use them but use Synapse instead since I can usually type the command and run the app faster than scrolling through the Dash. 

And as for the dreaded Amazon lens, I simply removed it post installation which by the way was pretty easy. As for all the hoopla surrounding this lens,I really don't see the big deal about it. My philosophy is if you don't like certain features don't use them or just remove them. 

I'm sure Canonical is trying to make the product better, it's just going to take time. And even though I'm a Mint user, I still think we need to give Shuttleworth a break and focus on using Ubuntu and offer some positive feed back and keeping in the spirit of what FOSS is really all about.

---

### Post by Ubun2to on 2012-10-22
I had no problem on 2 of my machines.
However, I have an AMD graphics card on one of mine, and the Catalyst Control Center is giving me headaches trying to re-configure my multi-monitor setup.
Thank goodness my new nVidia card is on the way! nVidia has always provided good driver support, so this should be much better.
Edit: I also decided to do the full disk encryption. I like the way it acts-it actually looks good (not necessary, but it sure is nice to have a decent looking password prompt), and it even prevents you from editing the partitions in GParted.
Correct me if I am wrong, but you can not do custom partitioning in the "Something else" option on install and also have full disk encryption. I may not have a swap partition now, but I am perfectly fine with it, and I am planning on upgrading the RAM when prices drop.
I just wish GParted could enter the password so I could add in a swap partition. Oh well, I guess that is the price you pay for security. At least it is open source, so it is likely to get fixed a lot faster if any security flaws are found.
Probably the best thing about it is the boot time. When I say 10.91 seconds, I mean 10.91 seconds. Note that I mean from the time I press enter after entering my password to the time I see the login screen pop up-measuring the time from the BIOS post screen would be difficult to stop and start my watch at the right time.

---

### Post by cariboo on 2012-10-22
I've been running Quantal, since the tool chain was uploaded, so I knew what problems I would run into during and after the fresh installation, my Quantal install went flawlessly, but when I did a fresh install of the [Ubuntu GNome Remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta"), grub didn't behave at is should. Even though I wiped the partitions on the hard drive I am using, the menu entires didn't show what I actually have on this system.

Currently it is a triple boot system, with 12.04, 12.10 and Gnome Remix 12.10. I had menu entries for:

[LIST]
[*]Gnome Remix
[*]Quantal develop version
[*]Gnome Remix
[*]!2.04
[*]12.10
[/LIST]

Once I booted back into Quantal, I reran grub-install and update-grub, and now the menu entries are as they should be.

---

### Post by IWantFroyo on 2012-10-23
I downloaded the image again and gave it another try. No problem now.

---

### Post by philinux on 2012-10-23
Clean install on an Acer 1410 was not problem at all.

Upgrade of 12.04 to 12.10 on desktop pc with nVidia graphics has had a few hiccups and seems to have a memory leak.
Today booted up to busybox. Rebooted to safe mode, although reisub didn't work had to use reset button, and fsck sorted it out. 
Couple of other minor annoyances so not too bad. I never do upgrade but I did this to test it out. Always takes ages to upgrade whereas clean install is very quick.

```
[edit] free -m
             total       used       free     shared    buffers     cached
Mem:          2002       1780        222          0         88        767
-/+ buffers/cache:        924       1078
Swap:         1906          0       1906
```

```
[edit2] this with nouveau drivers. free -m
             total       used       free     shared    buffers     cached
Mem:          2002       1220        782          0         79        511
-/+ buffers/cache:        629       1373
Swap:         1906          0       1906
```

---

### Post by weasel fierce on 2012-10-24
Everything was smooth and without fuss for me, though I should add that currently I use openbox, rather than unity or KDE.

---

### Post by Dragonbite on 2012-10-24
My laptop needs the alternative (non-PAE) kernel so I don't know if I will be able to install 12.10 or if this is the end of the road for me & Ubuntu on my laptop,

---

### Post by JPR65 on 2012-10-24
Upgraded to 12.10 last Sunday. Upgrade went fine. After the restart, unity was gone--all I had was a terminal, and I had no way to reset unity. I reinstalled 12.04....

---

### Post by majabl on 2012-10-24
Went from Xubuntu 12.04 to something approximating to Xubuntu 12.10 that doesn't work. So I'm going to have to do a reinstall - hurrah....

---

### Post by duplicate on 2012-10-24
I first upgraded from 12.04, and couldn't boot.  Ran boot-repair, still nothing but a 'grub rescue>' prompt.  I then wiped the disk and did a fresh install with a newly downloaded .iso, same thing.  The kernel was missing.

I reverted to 12.04, from a bootable USB stick, and the system is working fine.  I will be re-attempting the 12.10 install this weekend.

---

### Post by Erik1984 on 2012-10-25
Well errors may show up later but as it seems now updating Kubuntu 12.04.1 to 12.10 went nearly flawless. Nearly because my desktop widgets appeared scrambled, but after updating their settings they showed up ok again. Also updating started an activity I had explicitly stopped in 12.04.  So all in all I'm happy with the upgrade :)

---

### Post by COMECON on 2012-10-25
Hi!
I didn't have any problems with doing a fresh install of Quantal. I used 12.04 and with the updates lots of Unity bugs were fixed. Now, with 12.10, I can say that the 90% of those bugs are fixed, and Unity is very smooth for my laptopt -I can run windows effects now! The only **con** I see is that if I install a restricted driver it's not smooth and it's slow (and only the NVIDIA experimental driver worked), so I'm happy using Nouveau -the same happened to me with GNOME Shell and KDE.
Great work, I used to use Mint because of Unity but for each update and bug fix I love more Ubuntu and Unity!
BTW, greetings to all, I'm new here -don't eat me :P

---

### Post by scouser73 on 2012-10-25
Install went perfect, upon selecting logging in without a password I encountered a problem; my password wouldn't work but that's now fixed.

---

### Post by Erik1984 on 2012-10-25
Discovered another quirk, the splash screen is messed up again. Starting with Oneiric I finally had a nice splash screen (high resolution) properly handled by the graphics card drivers. Now it's back to boring black on white and ugly moving dots. The right drivers are in place though, compositing on the desktop is really smooth. <3 Kubuntu.

---

### Post by ian.leckey on 2012-10-26
Only thing that bugged me after the upgrade was the unity launcher icons reverted to the default massive size, sticky edges had reverted to default, and launcher display settings on mulimonitor setup had reverted to default (launcher on both screens).

---

### Post by Paneless on 2012-10-26
A fresh install.
A few graphics driver quirks but nothing to compare with my formatting of my home partition. Luckily, the important stuff was safely retrieved from the cloud(s).:)

---

### Post by verymadpip on 2012-10-26
Xubuntu 12.10 fresh install:  ndiswrapper is uninstallable.  Even with the usual workarounds of installing ndiswrapper-dkms or installing from tarball - gutted.
Archive manager keeps crashing.
 
Gone back to 12.04 for now, might be brave & try again in a few days.

---

### Post by cariboo on 2012-10-26
> **verymadpip said:**
> Xubuntu 12.10 fresh install:  ndiswrapper is uninstallable.  Even with the usual workarounds of installing ndiswrapper-dkms or installing from tarball - gutted.
Archive manager keeps crashing.
 
Gone back to 12.04 for now, might be brave & try again in a few days.


Did you create a bug report, before re-installing 12.04?

---

### Post by verymadpip on 2012-10-26
> **cariboo907 said:**
> Did you create a bug report, before re-installing 12.04?

That would have been an excellent idea had I thought of it.

I'm also not seeing any similar problems out there, so it's probably me messing stuff up.

edit: I can give it another try tonight to confirm the issues remain & to create bug reports if that'll be of use to anyone.
It's not vital that this particular rig be up & running right this minute.

edit: ndiswrapper installs from 1.58rc1 .tar.gz - my bad for using an older file, sorry.

---

### Post by Elfy on 2012-10-26
> **Dragonbite said:**
> My laptop needs the alternative (non-PAE) kernel so I don't know if I will be able to install 12.10 or if this is the end of the road for me & Ubuntu on my laptop,

I 'think' you can get around that with the mini.iso - though I'm not completely sure.

Possibly lubuntu still uses the non-pae kernel as well

---

### Post by verymadpip on 2012-10-26
> **Elfy said:**
> I 'think' you can get around that with the mini.iso - though I'm not completely sure.

Possibly lubuntu still uses the non-pae kernel as well

12.04 mini.iso is supported for 5 years I think.  I'm sticking with that on a Compaq TC1000 tablet (truly ancient hardware).
+1 for checking the Lubuntu option too.

---

### Post by Dragonbite on 2012-10-26
> **Elfy said:**
> I 'think' you can get around that with the mini.iso - though I'm not completely sure.

Possibly lubuntu still uses the non-pae kernel as well

12.04 Alternate (and Xubuntu and Lubuntu) were non-PAE.  I think I read somewhere that 12.10 wasn't even going to provide the non-PAE kernel (at least on Xubuntu and Lubuntu) so it really comes down to whether or not the alternate or mini are using a non-PAE kernel.

---

### Post by Ubun2to on 2012-10-26
> **ian.leckey said:**
> Only thing that bugged me after the upgrade was the unity launcher icons reverted to the default massive size, sticky edges had reverted to default, and launcher display settings on mulimonitor setup had reverted to default (launcher on both screens).

And MyUnity has not been released for 12.10 yet.
So much pain waiting for the day I can change the mode on the Dash from Laptop to Desktop.
> **ostraaten said:**
> I **HATE** the mouse magnet on the middle edge with multi monitors. My left bars are always visible so the mouse magnet has no function. It **SUCKS**!

Mouse magnet?

---

### Post by cariboo on 2012-10-27
> **Ubun2to said:**
> Mouse magnet?

I laughed when I saw that the first time. :-D

---

### Post by Linuxisfast on 2012-10-27
Fresh install, works fine except for the missing linux headers for ati and nvidia install. Otherwise Unity is much improved, HDMI video via VLC is smoother, everything running good.

---

### Post by guntbert on 2012-10-27
Upgrade on my Lenovo T60 went flawless (original install dates from June 2010).
The iwl3459 bug (very slow downloads) seems to have found a fix at last.
Only quirk (after upgrading): sometimes the dash appears extremely slowly (takes several seconds) while the system overall reacts fine

---

### Post by kpkeerthi on 2012-10-28
Saved a snapshop in Back In Time and upgraded from 12.04. Except minor niggles, it was pretty smooth. 

1. Desktop and Login window theme were messed up post upgrade. I had to reset to Ambiance.
2. Plugged in my backup drive. Back In Time complained backup partition does not exist. Update Manager commented out the custom mount line I had for the backup partition in /etc/fstab. Enabled the line.

I had a couple of third party apt sources for Ubuntu Tweak and Banshee. Both were commented out by update manager. I had to enable them both and updated the system. Finally ran Janitor in Ubuntu Tweak. Everything seems OK so far.

---

### Post by cariboo on 2012-10-28
> **kpkeerthi said:**
> Saved a snapshop in Back In Time and upgraded from 12.04. Except minor niggles, it was pretty smooth. 

1. Desktop and Login window theme were messed up post upgrade. I had to reset to Ambiance.
2. Plugged in my backup drive. Back In Time complained backup partition does not exist. Update Manager commented out the custom mount line I had for the backup partition in /etc/fstab. Enabled the line.

I had a couple of third party apt sources for Ubuntu Tweak and Banshee. Both were commented out by update manager. I had to enable them both and updated the system. Finally ran Janitor in Ubuntu Tweak. Everything seems OK so far.

Upgrade-manager disables ppa's as part of the upgrade process. so that unneeded dependencies aren't pulled in during the process. 

Ppa's were one of the main reasons that upgrades failed, before this feature was added.

---

### Post by SantaFe on 2012-10-28
Just discovered my first two quirks with the Post Updated Xubuntu, both concerning GIMP.

First one, GIMP was updated from 2.6 to 2.8.  Now, for some reason, zeitgeist-datahub is having a hissy fit when I reboot about every GIF file I edited with GIMP 2.6 before the update, showing a bunch of errors like the following:
```
** (zeitgeist-datahub:2385): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/santafe/.themes/AntiGrey-Xfce/xfwm4/bottom-left-active.xpm" was not found, exec: gimp-2.6, mime_type: image/x-xpixmap
```

Funny, it's right there, in plain sight.  Fix is to re-edit every one of them with 2.8 & the error message goes away. ;)  Only 200 more to go. {sigh} :D

Second, apparently during the update I guess, one of the fonts got grunged.  So when I was using the Text tool & scrolling up the menu (I usually use Verdana) I'd get to DroidSansEthiopic-Bold & GIMP would shutdown & Ye Old Crash Alert would pop-up.  While I never use DroidSansEthiopic-Bold, it makes it hard to get towards the beginning of the alphabet with it there.  Fix: I deleted DroidSansEthiopic-Bold.ttf from the /usr/share/fonts folder. ;)

Other than that, Xubuntu 12.10 is working great.  Not too shabby for a machine I've updated from 8.04 up till now. ;)

---

### Post by stinkeye on 2012-11-03
Fresh install with nvidia GeForce 9400 GT gfx.
Booted into desktop using nouveau drivers.
The system would freeze or crash back to login screen randomly on mouse movement.
Installed proprietary nvidia and rebooted to a dis-functional desktop.
Stumbled on a post about purging nvidia and installing linux-headers.
```
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
```

Surely they must test the install on a common gfx card before releasing.
Why so hasty to remove unity 2d which at least is a stable fallback mode?
I pity a new user trying 12.10 and trying to sort this out.
You might say a new user should use 12.04, but look at the [**_[COLOR="DarkRed"]download page[/COLOR]_**]("http://www.ubuntu.com/download/desktop") 
and if you were a new user which would you choose?

---

### Post by cariboo on 2012-11-03
Most new users don't seem to pay a lot of attention to what's on the download page, they want the latest, even if it's pre-release, as we see in the U+! (VERSION$) sub-forum all the time.

---

### Post by bryncoles on 2012-11-04
I upgraded Xubuntu 12:04 to 12:10, and found it wouldn't boot any more!  Just hung at the Xubuntu loading screen.  It was odd, because I'm running it on a Dell Inspiron 1525, that came with Ubuntu pre-intalled, so I knew all my hardware was compatible.  I'd also fun Xubuntu 12:10 from a live USB, to check it worked.  

So, I did a fresh install instead.  Found that to be sooo buggy that I reinstalled 12:04, just so I could get some work done.  This is the first time I have ever had a problem with the upgrade process, and the first time I have ever had to resort to reinstalling a previous version.  I've been using Ubuntu since Gutsy Gibbon in '07, and I even had the random freezing problems what, one or two years back.  

Was rather disappointed, but as reinstalling 12:04 left me with no problems, I've not started any help threads on anything!

---

### Post by viperdvman on 2012-11-04
I did a **fresh install** of **[COLOR=Blue]Kubuntu[/COLOR]** 12.10 for this release cycle. I decided to put "worked flawlessly" despite having to do the install and initial bootup with nomodeset (current nouveau does not support my NVidia GTX 560 card). Once the proprietary driver was installed, everything is running perfectly.

I am noticing that xorg.conf is eating more RAM in 12.10 than it did in 12.04, and some of the PPA's I used in 12.04 don't have 12.10 packages (yet). Other than that, everything works flawlessly :)

---

### Post by Jakin on 2012-11-05
Fresh install of 12.10 Ubuntu with Unity today, was all pretty flawless.. but im finding myself stray-jacketed, trying my best to like it.

The 3.5 kernel is awesome, its too bad it refuses to work with my 12.04 system :(

---

### Post by Wild_Duck66 on 2012-11-06
Upgraded Kubuntu 12.04 to 12.10 without problem, it's the LightDM Login Manager I don't care for, when changed to my prefered background the Users names are unreadable.(black on black) You can move the users but they don't stay there and the users and the password are in the. centre spoiling the picture(sexy)

---

### Post by Ubun2to on 2012-11-07
> **Wild_Duck66 said:**
> Upgraded Kubuntu 12.04 to 12.10 without problem, it's the LightDM Login Manager I don't care for, when changed to my prefered background the Users names are unreadable.(black on black) You can move the users but they don't stay there and the users and the password are in the. centre spoiling the picture(sexy)

Really? I wasn't sure if it was a bug or not that the change background to user wallpaper feature did not work for me.

---

### Post by Jakin on 2012-11-07
> **Ubun2to said:**
> Really? I wasn't sure if it was a bug or not that the change background to user wallpaper feature did not work for me.

Didn't work for me either, no matter what i chose, it shows as a solid white background. Though user images work fine.

---

### Post by Ubun2to on 2012-11-07
> **Jakin said:**
> Didn't work for me either, no matter what i chose, it shows as a solid white background. Though user images work fine.

I got the default purple salad wallpaper as my login background.

---

### Post by Calinou on 2012-11-08
Xubuntu 12.10 fresh install on a netbook which had (I said "had" :)) Windows 7. Works fine, boots and shutdowns faster than Windows. Uses two times less RAM too.

---

### Post by w o l f on 2012-11-11
Unity crashes when I upgrade.

---

### Post by fballem on 2012-11-11
I have an nVidia card in my machine. Did a fresh install of 12.10 and finally managed to work my way through the linux-header issues and got the proprietary drivers working.

Final straw was when I installed Eclipse 4.2 from the eclipse.org website. It was slow and reported errors and crashed frequently. Sounds like there is stuff missing on the installation, because it works flawlessly on 12.04. Turns out, according to AskUbuntu.com (here: [http://askubuntu.com/questions/213646/cant-start-eclipse-juno-ubuntu-12-10](http://askubuntu.com/questions/213646/cant-start-eclipse-juno-ubuntu-12-10)), that Eclipse 4.2.1 seems to be incompatible with version 1.10 of libwebkitgtk-1.0.0. Oh well.

Re-installed 12.04 and am happy as a clam. I would like to have the webapp in 12.04. That looked like it would be very useful. But alas, that is not to be - they won't be backporting to 12.04.

---

### Post by georgelappies on 2012-11-11
For me it was the worst Ubuntu release ever. Unity with ATI was so unstable it couldn't even load. There was no 2D fallback. It actually made me explore other distro's.

openSUSE being currently used as my main.

---

### Post by Jakin on 2012-11-11
> **georgelappies said:**
> For me it was the worst Ubuntu release ever. Unity with ATI was so unstable it couldn't even load. There was no 2D fallback. It actually made me explore other distro's.

openSUSE being currently used as my main.

With Unity, i had to install the fglrx updates (i did so ontop of fglrx that didnt work properly), to fix the issue of th desktop not loading. After which everything seemed fine.

```
apt-get install fglrx-updates fglrx-amdcccle-updates
```

---

### Post by spier on 2012-11-18
My worst experience since dapper drake.
After an upgrade from 12/04 it wouldn't boot. For now I went back to precise, but will try Mint mate/cinnamon soon.

---

### Post by StuFranks on 2012-11-20
12.10 is the first linux OS I've used and it installed quickly and works brilliantly, obviously some work was needed to get appropriate drivers and things set up but that was quick and easy. No problems whatsoever!

---

### Post by Erik1984 on 2012-12-02
I have to come back on a statement I made earlier on successful upgrade. The upgrade went well but last week I tried a clean install of Quantal and it didn't turn out so well, the proprietary Nvidia drivers simply didn't seem to work or get activated after rebooting and I was presented an empty desktop. Clean install of 12.04 has solved the problem for now ;)

---

### Post by DukeOfMixture on 2012-12-02
Fresh install. No prob. Xubuntu 12.10

---

### Post by linuxcoffeelover on 2012-12-15
Did a clean install about a week ago and the install when through flawlessly, but I will have system errors popup alittle more than often more than I did on 12.04.

---

### Post by Ubun2to on 2012-12-16
> **linuxcoffeelover said:**
> Did a clean install about a week ago and the install when through flawlessly, but I will have system errors popup alittle more than often more than I did on 12.04.

Solution: disable Apport.

---

### Post by ZombieApocalypse on 2012-12-19
Had to downgrade my laptop back to 12.04 (Kubuntu) because it uses a ati mobility HD 4250, which is no longer supported with the fglrx drivers in xserver 1.13. Boo to AMD. 

But my desktop works fine once I updated the fglrx drivers to 12.10 (using an XFX HD5850). That said gaming performance through WINE is poor for me with these drivers. I'm hoping 12.11 will better (though I haven't tried the beta release).

I'm hoping the upcoming linux Steam release will pressure AMD into providing much better support for linux. Otherwise I'll be buying a Nvidia card for my desktop.

---

### Post by codingman on 2012-12-19
The only reason it was a little bad for me was that the new Maximus V Gene from Asus had old BIOS, and I had installed Kubuntu 11.10 for a short period of time, so I could upgrade, but there happened to be some broken packages, and so I had to do a fresh install.

---

### Post by pierceTN on 2012-12-19
reinstalled 12.04... :D


-Pierce

---

### Post by cecilpierce on 2012-12-19
> **pierceTN said:**
> reinstalled 12.04... :D


-Pierce

Lots of relatives in Elizabethton, TN...:)

So far RR 13.04 has worked better then PP or QQ.

---

### Post by Ubun2to on 2012-12-19
> **cecilpierce said:**
> Lots of relatives in Elizabethton, TN...:)

So far RR 13.04 has worked better then PP or QQ.

I am going to have to look into 13.04 beta for a problematic machine. Sometimes, jumping on the betas is a really good idea-it fixed some problems I had with 11.10 when I installed the 12.04 beta.

---

### Post by zikalify on 2012-12-20
I installed 12.10 clean and enabled broadcom driver and did the install. Then I reboot and my driver needs re-enabling then I tether with my phone and enable the driver but then wireless networks never show up in network manager.

---

### Post by loballn on 2012-12-20
the fresh install went flawless; problems started after the install completed.

---

### Post by Rickubun2 on 2012-12-29
Upgrade worked flawlessly, but my system is now way, way too slow.  Won't bother to install it in my main system.

---

### Post by cjwelborn on 2012-12-30
Installed: **Ubuntu 12.10 Secure-Remix 64bit**

LiveDVD was not recognized as boot disc (MD5 Checksum Confirmed)
    had to use *BOTH* _LiveUSB_ and _LiveDVD_ (*booted from USB, read files from DVD*).

Screen was black during grub, boot, splash, login, and after
    had to use acpi=off because of acpi problems with screen brightness
    had to manually set brightness after install using /sys/class/backlight/intel_backlight/brightness

Grub2 Menu Entries were broken, Windows 8 would not boot
    had to run **Boot-Repair** after install to get Grub2 working correctly (*Windows 8 was not loading, Ubuntu was. It's fixed now*)

...**KDE**/**Unity** apparently auto-corrected because my "fix" is gone from /etc/init.d/rc.local and everything works now.

Machine is running perfectly now, no problems.
    HP 2000-2b59wm Laptop
    Intel 2nd Generation Core Integrated Graphics Chip
    Intel Pentium Processor
    Windows 8 pre-installed (**UEFI** Boot)

Just wanted to be truthful, I love Debian & Ubuntu. I'm glad I got it working now, I hope in the future this will not be a problem. I was worried for a minute, there are alot of people having the same or similar problem with these Windows 8 pre-installed machines, UEFI Boot, and the Intel 2nd Generation Graphics Chip...

-Cj

---

### Post by cariboo on 2012-12-30
> **cjwelborn said:**
> Installed: **Ubuntu 12.10 Secure-Remix 64bit**

LiveDVD was not recognized as boot disc (MD5 Checksum Confirmed)
    had to use *BOTH* _LiveUSB_ and _LiveDVD_ (*booted from USB, read files from DVD*).

Screen was black during grub, boot, splash, login, and after
    had to use acpi=off because of acpi problems with screen brightness
    had to manually set brightness after install using /sys/class/backlight/intel_backlight/brightness

Grub2 Menu Entries were broken, Windows 8 would not boot
    had to run **Boot-Repair** after install to get Grub2 working correctly (*Windows 8 was not loading, Ubuntu was. It's fixed now*)

...**KDE**/**Unity** apparently auto-corrected because my "fix" is gone from /etc/init.d/rc.local and everything works now.

Machine is running perfectly now, no problems.
    HP 2000-2b59wm Laptop
    Intel 2nd Generation Core Integrated Graphics Chip
    Intel Pentium Processor
    Windows 8 pre-installed (**UEFI** Boot)

Just wanted to be truthful, I love Debian & Ubuntu. I'm glad I got it working now, I hope in the future this will not be a problem. I was worried for a minute, there are alot of people having the same or similar problem with these Windows 8 pre-installed machines, UEFI Boot, and the Intel 2nd Generation Graphics Chip...

-Cj

The Ubuntu 12.10 Secure-Remix 64bit, isn't an official release, so I'd suggest that if you are having problems booting it, that you should report a bug to the creator of the re-spin.

---

### Post by r123 on 2013-01-07
It installed perfectly for me and I even had wireless going out of the box. However, I then proceeded to preform an update. After restarting there was no wireless, which makes it hard to install wireless drivers!

Unrelated, I started getting crash notifications relating to Ubuntu's desktop UI applications.

I've also noticed these crash notifications on another box, which appears to be related to Intel graphics cards and the Unity and Gnome Shell desktops.

Lastly, I never realised the "Additional" drivers were in Software Sources. Must say, I would never have guessed considering Software Sources is to do with *Software*, and drivers on the other hand are to do with *Hardware*. I bet lots of new users will be completely lost.

Unfortunately, for the time being I'm jumping ship to mint. Really it's a combination of the above problems and with the Unity UI design itself (sorry I'm not a fan). However I have donated as I appreciate how much good use I've had from Ubuntu and that mint makes good use of Ubuntu also :)

---

### Post by Ubun2to on 2013-01-08
> **r123 said:**
> It installed perfectly for me and I even had wireless going out of the box. However, I then proceeded to preform an update. After restarting there was no wireless, which makes it hard to install wireless drivers!

Unrelated, I started getting crash notifications relating to Ubuntu's desktop UI applications.

I've also noticed these crash notifications on another box, which appears to be related to Intel graphics cards and the Unity and Gnome Shell desktops.

Lastly, I never realised the "Additional" drivers were in Software Sources. Must say, I would never have guessed considering Software Sources is to do with *Software*, and drivers on the other hand are to do with *Hardware*. I bet lots of new users will be completely lost.

Unfortunately, for the time being I'm jumping ship to mint. Really it's a combination of the above problems and with the Unity UI design itself (sorry I'm not a fan). However I have donated as I appreciate how much good use I've had from Ubuntu and that mint makes good use of Ubuntu also :)

The crash notifications, unless it brings down Unity or system services like the network manager, are nothing worth worrying about 90% of the time (unless you are making a program and so you need to know what the problem is). The Software Center crashes every now and again, especially when the system is under load.
You can [disable Apport]("http://www.techdrivein.com/2012/08/how-to-disable-system-program-problem.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29") to eliminate these messages. I always do on every install if it is not already disabled, as it is a real pain constantly clicking on those, and those come a lot when I am getting all of my packages in, my PPAs updated, etc.
On the wireless drivers, have you made a post about it yet? Have you looked in the network menu and enabled wireless or reconnected? It may have gone into manual-on, rather than auto-on. I set mine to manual start because I use Ethernet primarily (speedy and reliable), and when I use Ethernet and WiFi at the same time, when I boot, they fight for awhile over who gets to connect and get the static IP, until eventually the Ethernet somehow wins and my connection is restored.

---

### Post by cabz on 2013-01-08
fresh install ubuntu 12.10 64bit/ dual boot with wubi on win 7 dell laptop.
I found out that 12.10 did not have 1386 files ia32-libs-multiarch , had issues installing google earth,wine and skype . found temp sulution in this thread.
[http://ubuntuforums.org/showthread.php?t=2100827](http://ubuntuforums.org/showthread.php?t=2100827)

---

