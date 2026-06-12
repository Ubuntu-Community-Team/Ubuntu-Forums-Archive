---
title: "Feisty - Ubuntu's least stable release yet?"
date: 2007-05-02
forum: Testimonials &amp; Experiences
---

### Post by househead on 2007-05-02
Hello all.

I've been a Linux user for about 6 years. I have tried all of the Ubuntu releases in both development and stable branches since Warty.

Recently I decided to give Feisty a go after mainly using Debian Etch for the past six months.

I must say, on the whole I am not overly impressed with Feisty. After installing 3 machines in as many days, I have stumbled upon a number of "bugs"...

1) On the installation CD, using Gnome Parition Editor outside of the Installer is a fruitless task. It seems automounting and gparted dont play well together. Simple creation of filesystems has failed on a number of machines. Although a worthwhile tool on the liveCD, this should be fixed or gparted removed. Fdisk and / or mke2fs seemed to play happily enough.

2) Upon booting the installation / live CD, I am informed I can install the Nvidia binary driver to get full 3D support. The "Restricted Drivers Manager" allows me to download and install the driver in the live environment. It then prompts me to reboot. I seriously doubt rebooting would install the driver as it's running from a live CD. New users are unlikely to twig about this and perform pointless reboots, wondering why the result is the same every time.

3) When installed, the Restricted Drivers Manager is not much better. It activated my Intel ipw3945 suree enough, but activating the nvidia driver (in the installed environment now) does not work. Also, installing linux-restricted-modules and nvidia-glx did not work. Great, Ubuntu have provided a simpler, but non-working method of installing nvidia binary drivers and broken the existing method. Installing from the binary package from nvidia.com works, but only if i remove nvidia-glx and restricted-modules first. Nice and easy for me but you wouldn't expect a newcomer to know this, neither would you expect them to crawl forums etc.

4) Sound - non-working on my thinkpad x31 with intel chipset. Seems there are quite a few bugs around with feisty and alsa. My brother, using a totally different laptop is experiencing serious issues with sound too.

5) CPU Scaling - my CPU's apparently go to 50-Odd GHZ. I WISH!?

Is it me, or are standards slipping. LTS was a top relesase and Etch was up there, but feisty to me seems more like an effort to get the latest and greatest new software on peoples systems without any real thought going into stability.

While new features etc are nice, I prefer a stable, working system (there's no way I can wait around while my sound is fixed for example).

I think i'm gonna go back to Debian Etch for a while. It's a shame as in the past Ubuntu releases have always been excellent. Just seems this one was rushed out the door to compete with Etch.

---

### Post by Dcox on 2007-05-02
been reading more stories like this and yes it's a damn shame. Anyway it seems to be dependant on the hardware you run. Me for instance have no issues at all with Feisty (Barebone, ATI9800, PLextor DVD writer, Nvidia onboard sound, USB mic/headset for skype). I'm loving Feisty just because it's packed with all kind of easy features and all my stuff works out of the box!

Still I remember having the same issue with gparted / mouting as you had. Needs to be fixed for sure because "simple" users just want the product to work and not fiddle around with the command line.

So what I'm trying to say : it's not all bad but it would be nice if everyone could have had the same experiences as I did, namely get a kick *** OS which works out of the box.

---

### Post by kelvin spratt on 2007-05-02
it is a shame that some people have problems as i did not as far as gparted is concerned and i'm new to linus you are advised to use gparted live for partitioning and that really makes sence to me i had no issues what so ever and feel a lot of problems could be avoided if people researched a bit more before installing hardware about combatabilty and remember just cause it says nvidia or ati does not mean it was made by them and often as i know with my nvidia card is not even supported by them so you should not complain 
if it does not work wright when i purchased the ati card i'm using now i had a choice of 3 cards all the same
version 1 genuine 2 licenced but much cheaper only the genuine is fully supported as with the numerus laptops with compatability probs if the cards are made under licence oem they are not always fully supported factory versions and can give strange problems

---

### Post by ThinkBuntu on 2007-05-02
I do encounter bugs here and there. Compiz worked perfectly in Etch (and it didn't even come with it) but in Feisty I often log in, only to have no window manager...which makes moving windows a little hard! Hate to say it, but Edgy was a far stabler release...but Debian gave me a different set of troubles. For instance, I got errors every time I tried to eject my thumb drive, end usually ended up having to just pull it out.

The only distro I've encountered without bugs were Edgy and Mint, most likely because Mint 2.2 is based on Edgy. I'm going to stick with Feisty and hope that some software upgrades over the next month fix these bugs. But if Gutsy isn't more stable...

---

### Post by househead on 2007-05-02
> **ThinkBuntu said:**
> I do encounter bugs here and there. Compiz worked perfectly in Etch (and it didn't even come with it) but in Feisty I often log in, only to have no window manager...which makes moving windows a little hard! Hate to say it, but Edgy was a far stabler release...but Debian gave me a different set of troubles. For instance, I got errors every time I tried to eject my thumb drive, end usually ended up having to just pull it out.

The only distro I've encountered without bugs were Edgy and Mint, most likely because Mint 2.2 is based on Edgy. I'm going to stick with Feisty and hope that some software upgrades over the next month fix these bugs. But if Gutsy isn't more stable...

To be honest, I'm not to bothered about stuff like xgl/compiz/beryl etc. It's overkill for my needs and I find it hinders my productivity. I've installed them all and had a play etc. but that's it. As for making the desktop experience any better, i don't feel it does and clearly it brings its own set of bugs and issues that exist due to such a choice in hardware.

I'm now using an old deb package of a 2.6.20 vanilla kernel I had on debian. I still have Ubuntu feisty, but with a custom-compiled kernel. This fits fine for me, and I don't mind compiling but I think most people don't even care or want to care about the kernel. Why should they? They just want it to work. My sound works again now. I think I'll file a bug against linux-source-2.6.20-whatever because non-working sound would be a massive show-stopper for most. I have the advantage of being able to concoct a workaround but others don't.

I've never heard of mint, i'll check it out. I have found Etch and Edgy to both be more stable than feisty and probably Etch more-so.

---

### Post by newbie2 on 2007-05-02
Problems with Ubuntu Fiesty Fawn :
[http://www.extremetech.com/article2/0,1697,2124101,00.asp](http://www.extremetech.com/article2/0,1697,2124101,00.asp)
:rolleyes:

---

### Post by ThinkBuntu on 2007-05-02
> **househead said:**
> To be honest, I'm not to bothered about stuff like xgl/compiz/beryl etc. It's overkill for my needs and I find it hinders my productivity. I've installed them all and had a play etc. but that's it. As for making the desktop experience any better, i don't feel it does and clearly it brings its own set of bugs and issues that exist due to such a choice in hardware.
My main use for Compiz is the option to make one of my screen corners a "hot corner" that lays out all of my open windows, a la OS X. This increases my productivity significantly over using different workspaces or alt+tab+tab+tab... Metisse looks very interesting and I'm psyched to give it a try. It's focused on productivity, not incinerating closed windows and the like.

---

### Post by robtg on 2007-05-02
Feisty hasn't been unstable for me but the installation process was a no-go; I couldn't do a clean install off the live CD (needed to do a clean install of Edgy which went perfectly and then a network upgrade which went OK).

My advice to Canonical: drop the "new-release-every-6-months-come-hell-or-high-water" model.  That's nuts.  Release a new distro when it makes sense.  Meanwhile, your software update mechanism very nicely lets us upgrade to newer software and rarely has a problem (except for the occasional kernal mishaps).

Test, test, test.  Once your fans start wondering if the next release is going to be worse than the current release, as Rickey would say to Lucy, you're going to have a lot of 'splainin to do.   You're on a roll with Michael Dell; keep that roll going.

-Rob

---

### Post by jbmech006 on 2007-05-07
I encountered some problems with the install as well. I spent a couple of hours trying to fix the X server failing on the Desktop installer only to find out that it was a bug with my video card family (ATI Mobility X1400). I fixed this problem by downloading the alternative installer. Next I decided to try out the auto-installer for the restricted codec packs. I ended up having problems with the Xvid codecs which turned out to be a bug in gstreamer. I fixed this problem by switching to totem using xine-lib version 1.1.4. 

Other then those draw back the rest of the system setup was very smooth. I changed my usplash, splash, and login screens back to what I had in 6.10. The CPU scaling is working but I don't have access to the governors, that will be my next task. 

I agree that the 6th month release schedule is risky, I think Microsoft is on a 6 year release schedule.. (I hate Micro$oft) Its hard to complain about something that is free and I am very pleased with Ubuntu, even with the bugs.

---

### Post by sloggerkhan on 2007-05-07
This thread is how I felt about edgy. feisty's been great. If I crash under feisty, it's from running either: a) programs under wine or b) unsupported beryl svn stuff. I think my comp does run overall a bit hotter, though.

---

### Post by canadianwriterman on 2007-05-07
I have to agree with the original post that Feisty seems (on my system) not as stable and bug-free as Edgy was. My experience with Feisty that I did NOT have with Edgy (don't yell at me, I tried all the suggestions to fix these, but nothing worked):

[LIST]
[*]Live CD would not pick up my monitor resolution and I had to use the alternate CD.
[*]If I picked UTC time during install, I could not synch my clock and it was always off by hours. Had to reinstall and choose no to UTC.
[*]Keyboard was automatically detected as 105 key U.S. International, which meant I lost the apostrophe key (it bacame a accent key). Had to reinstall and choose the right keyboard.
[*]The default Java in Firefox would not work with some of my Web sites. Spent a lot of time uninstalling and installing various combiunations of Java plug-ins to get everything working.
[*]My monitor would power off if left idle for several hours. Reinstalled and farted around a lot. Ended up editing out the Energy Star activation from xorg.conf to get it working.
[*]OpenOffice Impress has a crash bug upon closing a slide show (annoying because I use it daily).
[/LIST]

---

### Post by otual on 2007-05-08
I was introduced to ubuntu a very short time ago, (had a computer with no OS and a live Ubuntu disk) one thing led to another and... well now I only turn on my windows machine to allow the file sharing on my home network.
 My first experience was with edgy. At first I loved it. Rock solid, everything worked straight out of the box (HP omnibook with 1.2GHz Celeron and 128MB Ram) The inbuilt ethernet connecter automatically detected and configured itself to the router. I was well impressed. Was really enjoying the advanced simplicity that linux and ubuntu provide.
  I purchased a wireless pcmia card so I could lose the ethernet cable and make my laptop truely portable. It took me over a week (a few hrs a day for that week) to finally get the system to recognise the card. After that I had no more problems. That is until feisty reared it fearsom head. I dutifully installed the update when it became available (been a windows user for many years) I had no wifi. and the only other difference I noticed was a magnifying glass (desktop search) in my top panel. I managed to finally get the wifi to work (by uninstalling default packages) but now I get all sorts of wierd behaviour.
  It crashes EVERYTIME I attempt to go into standby mode, other times the system suddenly freezes up all but the mouse pointer which still flies around the screen as if nothings wrong. I have issues when I boot up after a crash (and resulting power down). The average system load (graphical system load analyser)  goes up to maximum and things slow to an almost standstill for several minutes. I know my memory is very low, (I read that ubuntu required 256MB, but it seems to work ok with 128MB)
  It's frustrating I know, but 90% of the time my system works flawlessly and its 10 times more satisfying to use than my tired old desktop running XP.

---

### Post by chang47 on 2007-05-10
Just to pick up on release cycle.  I agree that 6 month is too short a cycle for major releases.  People can't even catch up with new iPod every year.  When you bought your new iPod, you knew you would be obsolete by next Spring.  6 month is a good cycle for bug fixes they call Service Packs in the other world.  IMHO 24 to 36 month is a better cycle for major releases.

My first cup of xubuntu so far is bitter.  Haven't given up yet, but close.

---

### Post by olskar on 2007-05-10
I also have to agree with the original post that Feisty seems less stable than Edgy. Had edgy for some months, loved it! Everything worked! Then I upgraded to feisty..that I regret.

Looks like this is the bughiest version of ubuntu so far.. I already know several people that has been scared back to XP by feisty...:(

Maybe back to Xp for me too but really don't want to...
Feisty sucks but I love edgy!
Can I keep using edgy?

---

### Post by jerrylamos on 2007-05-10
By all means keep running Edgy.  It's to be supported for 18 months after it was released.  I'm on Feisty and also on Feisty with parts of Gutsy.  Feisty gave me fits on Alpha and Beta but I always had a Dapper and an Edgy partition to fall back on.

Now even though I'm on Feisty, I can't think of a thing I'm doing that Edgy won't do.  I read where Gutsy is to do some "polish" rather than add new functions.  We'll see.  Based on Feisty I don't expect much.  I got all my Alpha and Beta bugs lined up to try on Gutsy come June 7, provided the June 7 will fit on a CD.

Cheers. Jerry:(

---

### Post by chek2fire on 2007-05-11
i have the same problem with feisty it crash every time i go to stanby mode.i dont know why

---

### Post by househead on 2007-05-12
> **jerrylamos said:**
> By all means keep running Edgy.  It's to be supported for 18 months after it was released.  I'm on Feisty and also on Feisty with parts of Gutsy.  Feisty gave me fits on Alpha and Beta but I always had a Dapper and an Edgy partition to fall back on.

Now even though I'm on Feisty, I can't think of a thing I'm doing that Edgy won't do.  I read where Gutsy is to do some "polish" rather than add new functions.  We'll see.  Based on Feisty I don't expect much.  I got all my Alpha and Beta bugs lined up to try on Gutsy come June 7, provided the June 7 will fit on a CD.

Cheers. Jerry:(

I have installed feisty on my laptop but the problems encountered mean I'm very worried about upgrading my main server machine which holds file shares and does routing / nat for my lan and wifi. There's just too many things ive done to it server-wise. I just know it'd break and i'd have to spend days getting it back to where it was. I'm happy with Edgy on the server until I know fesity is fairly stable and I can pencil in some time to make a backup of my config and perform a clean install.

I also echo the 6 month cycle being silly. If users are looking for something uber-stable, they could use dapper, or LTS as it's also known (for long-term-support), which is I think 3 years desktop support and 6 years server support. If I was performing large-scale implementations which needed stability and security over features and eye-candy, I'd seriously consider using either LTS or Debian Etch, which in my opinion is also very stable. The only problem I have / had with Etch is that the versions of NetworkManager and gnome-keyring are buggy as hell.

The improvements made to network-manager in feisty are much-welcomed. It's less buggy, plays nicer with the keyring, can handle manual configurations and also nicely integrates with openvpn via a separate .deb.

---

### Post by 3rdalbum on 2007-05-12
Maybe possibly less stable than Dapper or Edgy, but for me there are only a couple of bugs, and they're just a little strange (they don't actually make the machine unstable). The HAL update fixed up the only critical bug I had!

---

### Post by jerrylamos on 2007-05-12
> **househead said:**
> The improvements made to network-manager in feisty are much-welcomed. It's less buggy, plays nicer with the keyring, can handle manual configurations and also nicely integrates with openvpn via a separate .deb.

Glad someone has benefits from Network manager.  All it does for me is disable my wired network card during boot, every time, so every time I come up I have to manually select the Network Manager Icon, select wired network, wait for it to activate, and then close the message balloon.

Cheers, Jerry

---

### Post by Hoso001 on 2007-05-13
I kinda disagree, my personal experience with it has been excellent, i think its one of there best ever. I am running an Dell Laptop with a ATI Mobile X300? video i card i think. It has run excellent, I have upgraded from Dapper Drake, and this seems to be running great. I haven't really had any issues with this, no crashes. I took the route of using the alternate install CD though. I heard there was problems with the ATI support and to do that, but it installed fine, getting 3D enabled is easier than ever. Getting the Multimedia codecs installed was simple. My wireless ran like a charm, everything is running great. The only complaint i have is that my audio sounds a tad fuzzy, other than that Great! I think they did an excellent job. 

Just my 2 cents folks,

David

---

### Post by househead on 2007-05-14
> **Hoso001 said:**
> I kinda disagree, my personal experience with it has been excellent, i think its one of there best ever. I am running an Dell Laptop with a ATI Mobile X300? video i card i think. It has run excellent, I have upgraded from Dapper Drake, and this seems to be running great. I haven't really had any issues with this, no crashes. I took the route of using the alternate install CD though. I heard there was problems with the ATI support and to do that, but it installed fine, getting 3D enabled is easier than ever. Getting the Multimedia codecs installed was simple. My wireless ran like a charm, everything is running great. The only complaint i have is that my audio sounds a tad fuzzy, other than that Great! I think they did an excellent job. 

Just my 2 cents folks,

David

Maybe the vendor of your hardware is the giveaway.

As Dell have said they will be selling machines with Ubuntu pre-installed, I wouldn't be surprised if the focus of driver / hardware support bug-fixing was concentrated on Dell machines.

---

### Post by whitefort on 2007-05-14
I can live very happily without eye-candy, and in general I've found Feisty to be reasonably stable.

But what's driving me back to Dapper is that some essential software in the repo just isn't working with Feisty.

For example, Mondo Rescue is my most essential piece of software. It's a backup program that very easily allows you to back up your whole hard drive to a bootable CD/DVD, then restore it just the way it was, even from bare metal if necessary - all with just a few clicks and no messing about.  It means you can safely experiment, try a new OS,  but know that if you wreck your system,, you can still get your machine back ***exactly*** the way it was - in a matter of minutes.  Or even clone your whole installation to another machine.  It's absolutely wonderful.

 With Dapper, it worked perfectly.  With Feisty, it backs up just fine... but won't restore.  Any Feisty user who's depending on it for disaster recovery may get a nasty shock.

I've spent a few weeks reading forums and websites trying to get it to work, but I've just decided that life's too short.  it's much easier just to go back to Dapper (using my handy Mondo backup DVD!) and maybe by the time Gibbon appears this will be fixed.

---

### Post by misfitpierce on 2007-05-14
Bug's will be fixed eventually but as someone said its mostly reliant on hardware too as ive yet to encounter any bugs that are noticeable to what I do

---

### Post by househead on 2007-05-14
My guide to buying 100% linux compatible hardware...

1) Email linux kernel devs
2) Find out what they use
3) Buy the same
4) Live happily ever after

Failing that

1) Wait six months
2) Buy Dell

;-)

---

### Post by graigsmith on 2007-05-15
personally for me, it seems less buggy than the last version. the last version shipped with an annoying nautilus bug where nautilus would crash.    it got patched after it was shipped, thats all that mattered to me.

this one shipped with an annoying window resizing bug that pops up every now and then. not sure why. hope they patch it.

---

### Post by marcele on 2007-05-15
I have to agree with the original post 100%.It seems that each release keeps getting less stable for me. In fact I have tried installing Feisty on two separate machines and I can't even get Feisty installed due to this bug: 
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

P.S. I've been a linux sysadmin for almost 9 years!

---

### Post by st00ner on 2007-05-15
> **newbie2 said:**
> Problems with Ubuntu Fiesty Fawn :
[http://www.extremetech.com/article2/0,1697,2124101,00.asp](http://www.extremetech.com/article2/0,1697,2124101,00.asp)
:rolleyes:

My reply to this retared article:


Im completely ashamed of whoever wrote this article.


Why the hell would flash and nvidia drivers be installed by default? are they FOSS?

I thought not. Ubuntu has not, and will never come with proprietary software of this kind by default (besides a few restricted modules)
 
Stop bringing your proprietary values to a free open operating system. The community would be better of without you (The author of the article).
 

All you people who are new to linux are missing the whole point of it!

Yes it is a better operating system, but that is BECAUSE OF THE SOURCE CODE MODEL! GPL Free Open Source Software just works.

So please, if you(The Author) dont care about your freedom, go back to Windows, and stop hurting our community with your proprietary BS.

---

### Post by Ateo on 2007-05-17
Hmm.

Not sure if this is just me but I don't have any issues with [K]Ubuntu default installs. Kubuntu has a small hang up during install (time it stalls seems to vary between users). I also have a small start up glitch during startup right after grub launches. But that doesn't seem to affect anyting...

I can't compare to other releases since Feisty is my first cup of Ubuntu. But from my experience, they work well for me.

I have a it on 3 nodes, which includes one Ubuntu server edition (Feisty).

---

### Post by SnoopDeVille on 2007-05-18
> **canadianwriterman said:**
> I have to agree with the original post that Feisty seems (on my system) not as stable and bug-free as Edgy was. My experience with Feisty that I did NOT have with Edgy (don't yell at me, I tried all the suggestions to fix these, but nothing worked):

[LIST]
[*]Live CD would not pick up my monitor resolution and I had to use the alternate CD.
[*]If I picked UTC time during install, I could not synch my clock and it was always off by hours. Had to reinstall and choose no to UTC.
[*]Keyboard was automatically detected as 105 key U.S. International, which meant I lost the apostrophe key (it bacame a accent key). Had to reinstall and choose the right keyboard.
[*]The default Java in Firefox would not work with some of my Web sites. Spent a lot of time uninstalling and installing various combiunations of Java plug-ins to get everything working.
[*]My monitor would power off if left idle for several hours. Reinstalled and farted around a lot. Ended up editing out the Energy Star activation from xorg.conf to get it working.
[*]OpenOffice Impress has a crash bug upon closing a slide show (annoying because I use it daily).
[/LIST]

What the HELL ?!?! I had a go at Linux for the first time and i chose (yes idiot me) Ubuntu Edgy amd64. 

I had so many rounds but in the end i won over edgy with a major concussion to my brain. 
If id known how hard it would be to simply enable flash player in firefox i wouldnt have even bothered and stayed on Windows.

Then again, the feeling i got from the OS grew warm and fuzzy in my heart :) Really loved the system as i felt i had to pull some muscles to get everything working, including Wine emulated games, which was forced architecture (32bit Wine) on the OS , 

Feisty Fawn is kinda stable, easy....some mini bugs but appart from that i like it.

Overall my point here is: New users should always always always stick to a 32bit version of Linux unless its properly stable and easily manipulative :) 

Cheers  ^__^

---

### Post by BackwardsDown on 2007-05-18
> **chang47 said:**
> Just to pick up on release cycle.  I agree that 6 month is too short a cycle for major releases.  People can't even catch up with new iPod every year.  When you bought your new iPod, you knew you would be obsolete by next Spring.  6 month is a good cycle for bug fixes they call Service Packs in the other world.  IMHO 24 to 36 month is a better cycle for major releases.

My first cup of xubuntu so far is bitter.  Haven't given up yet, but close.

Then you could only use the LTS-versions if you dont bother about using software that is not the latest available. They come about once 36 month's. And they are more stable than the in-between releases.

---

