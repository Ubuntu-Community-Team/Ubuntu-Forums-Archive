---
title: "Why does the upgrade system on Ubuntu NEVER WORK properly EVER!"
date: 2015-06-10
forum: Ubuntu, Linux and OS Chat
---

### Post by musicboy on 2015-06-10
I have been using Ubuntu for 6 years now and my first computer was in 1984 so I am not exactly new to computers. AND EVERY single time I test out to see if Ubuntu will upgrade via the internet, it turns it into COMPLETE and utter mush! SOMETHING always breaks!!

This time was VERY close to actually working I upgraded from 14.04 to 14.10 and sorted it all out........... THAT to my UTTER surprise worked for the first time EVER properly!  (so the title of this is not 100% correct BUT read on!) BUT MY PLAN was to then see if it would upgrade to 15.04 as well and that turned to complete and utter rubbish where it wouldn't even boot properly and some apps wouldn't work I filled bug reports etc.

BUT why can't Ubuntu get this right when I have had Android phones, a Sony at present that when Android needs to upgrade its fine all be it I switch to Cyanogen Mod of which Ubuntu Mobile is based upon, so I would like the confidence IF I WERE to eventually get a mobile with Ubuntu mobile on it that this would not happen and I would have to manually update as, well its a nightmare and you have to re instate back ups when you do fresh installs where as just doing a back up and then upgrading is a LOT simpler.

That is all...........

---

### Post by Bashing-om on 2015-06-10
musicboy; Humm ???

Not holding your mouth right ?

I too am a long time user of ubuntu, and I have never ever had a problem doing a on-line release upgrade on numerous machines.

I do realize that ubuntu is not a magic box, and when I do the release upgrade I revert everything back to standard defaults of the software repository - that includes graphics and WIFI drivers -. When I cannot revert I disable all 3rd party sources. If it is not unbuntu, then ubuntu has little or no control over the package or what happens in the upgrade process. I also make sure that the screen saver is disabled .

[INDENT][INDENT]I keep it in the family
[INDENT][INDENT][INDENT]no fuss'n
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-06-10
> **Bashing-om said:**
> musicboy; Humm ???

**Not holding your mouth right ?**
I keep it in the family[INDENT][INDENT][INDENT][INDENT][INDENT]no fuss'n
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

Yep the mouth is very important in the dist-upgrade process.;)
You Crack Me Up. LOL
Cheers

---

### Post by efflandt on 2015-06-10
If you have any ppa's you need to ppa-purge them and purge related files before doing an Ubuntu version upgrade. Otherwise those and/or proprietary video driver changes might trip you up.

Actually I normally install a fresh system when changing versions, the only time I upgraded versions was my backup system on SSD when I updated it from 64-bit Ubuntu 11.10 to 12.04, and that went smoothly. When updating my main system from 12.04 to 14.04 I first copied (cp -r) my home directory to ext4 partition on external drive, installed 14.04 fresh, then copied my home from the external drive to new system. Everything just worked (once I installed whatever programs).

---

### Post by simonn on 2015-06-11
I installed Breezy (server) on my Koolu (little low power server) in 2005, upgraded Dapper -> Hardy -> Lucid via net with no worries. It was only when they dropped support for older than i686 with Precise (at least for LTS, and while keeping an i386 designation so I found out the hard and non obvious way <insert many swear words>) that I went to debian (server uses an AMD Geode LX800 processor which uses i586 instruction set).

Another thing to think about - it works with debian so should work with ubuntu is, after adjusting source.list etc:
```

# apt-get update
# apt-get --download-only dist-upgrade
# apt-get dist-upgrade

```

This will stop and/or aid recovery from network or disc space problems.

Always have /home on a different partition helps too.

---

### Post by Bucky Ball on 2015-06-11
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. 

You need to sing the 'Upgrade' incantation whilst slowly spinning three times in an anti-clockwise direction and throw the navel lint of your first-born over your shoulder ...

Bottom line: Kill anything not officially Ubuntu prior to upgrade. As mentioned, disable added third-party PPAs and if you've installed any programs manually, switch off or remove if you're unsure they will work in the newer release (you can do some research to find out). I also have never had an issue with the net upgrade. I generally go a clean install, but have done five or six upgrades via the net over the years. I avoid third-party repos generally, though, so that is not a major issue, and rarely, if ever nowadays, install anything that is not officially supported by Ubuntu repos.

---

### Post by echotech2 on 2015-06-11
...whilst slowly spinning three times in an anti-clockwise direction.

  All my clocks are digital,  which way should I spin?

---

### Post by Bucky Ball on 2015-06-11
> **echotech2 said:**
> ...whilst slowly spinning three times in an anti-clockwise direction.

  All my clocks are digital,  which way should I spin?

Ha. Attempt to look at your left ear and keep turning your head until your body follows! 

PS: The Ubuntu upgrade guide says it's best to be standing up for this to work properly. Oh, and the navel lint should be no more than 12 hours old, but snap frozen within 12 hours of harvesting and thawed at a later time is also acceptable at a pinch, but you might have trouble with grub after the upgrade. If this occurs, repeat procedure with fresh, rather than frozen and thawed, lint ... :)

Also, confirm with an in tune piano or tuning fork that the first note of the incantation is an Ab. Bb can take out your hard drive and C# could possibly fry your motherboard.

---

### Post by mikodo on 2015-06-11
for ever and ever ... amen.

Wait!

That might be

forever and ever 

Whatever the difference may be ...

---

### Post by Bucky Ball on 2015-06-11
> **mikodo said:**
> for ever and ever ... amen.

Wait!

That might be

forever and ever 

Whatever the difference may be ...

Grammatical errors and misspellings during the upgrade incantation may have unpredictable consequences during or after upgrade ...

---

### Post by echotech2 on 2015-06-11
>  ...trouble with grub after the upgrade

  So this may be where the grubs in my lawn came from.  I must research this further!

---

### Post by craig10x on 2015-06-11
I upgraded from 14.04 to 14.10 then to 15.04 and both upgrades were 100% perfect...but i just use a stock ubuntu without heavy modifications (just add some apps of course) and the only ppa i have is the Google Chrome updater which i un check in software sources until after the upgrade has completed...and i only use the open source driver that ubuntu installs...I think that is the secret to getting the best upgrade success...then it works like a charm...

I have a high speed cable internet connect (50 mbps) so downloading the packages only take like 2 minutes...and after that, it only takes about an hour to install everything...
There is even a neat clean up janitor at the end which if you tell it do so (i do) it nicely cleans out the stuff you no longer need (like old kernels for example)....

Works EXTREMELY WELL if you follows those rules...;)

And it doesn't hurt to recite a little prayer over your computer while the upgrade is going on...for good luck :mrgreen:

---

### Post by Bucky Ball on 2015-06-11
Yep, good point previously overlooked. A cable connection is essential IMHO. I've never used wireless for a net upgrade. Increases the risk of breakage.

---

### Post by beelzebufo on 2015-06-11
I agree with you 100%  Every time I update or upgrade something breaks, I am currently in the process of trying to fix one of those mush situations myself.  I updated and now it won't boot.  Apparently I lost my keyring?  or something.  Anyway, Ubuntu really needs to start getting this right.  It drives me nuts having to start over from scratch every couple of months because I was an idiot and decided to let it update.

---

### Post by cariboo on 2015-06-11
> **Bucky Ball said:**
> Yep, good point previously overlooked. A cable connection is essential IMHO. I've never used wireless for a net upgrade. Increases the risk of breakage.

I've never had a problem using wireless while upgrading, The system using at the moment, started out running utopic, then was upgraded to vivid and now I'm running wily.

---

### Post by mikodo on 2015-06-11
In seriousness now, I just read Craig's response, hence this question.

I read recently about, oh what is the command. I forget but, about using ppa-purge before upgrading. 

Or, is that being too anal. I sure could easily edit the sources list, or tick them off in Synaptic. That's to my liking really.

hmm ... I just looked. PPA's aren't in sources.

---

### Post by SurfaceUnits on 2015-06-11
My customers' computers which run a couple different buntu distros, mostly Xubuntu, are as stock as possible and I don't have any problems when upgrading them. My computers, which are modded extremely, only have problems when I don't purge ppa's, etc. I have in the past run out of disk space during an upgrade and was able to recover using basic commands. This recent upgrade to 15.04, I didn't purge a couple of ppa's and I was stuck with in between versions. Was able to boot in recovery mode, run the ppa purges and a little while later I was running 15.04.

---

### Post by mikodo on 2015-06-12
> **SurfaceUnits said:**
> My computers, which are modded extremely, only have problems when I don't purge ppa's, etc. I have in the past run out of disk space during an upgrade and was able to recover using basic commands. This recent upgrade to 15.04, I didn't purge a couple of ppa's and I was stuck with in between versions. Was able to boot in recovery mode, run the ppa purges and a little while later I was running 15.04.

Thank you.

I'll do ppa purges.

---

### Post by monkeybrain20122 on 2015-06-12
> **mikodo said:**
> Thank you.

I'll do ppa purges.

It will be much faster to do a clean install than to restore your system to pristine state and then upgrade. Clean install takes 15 - 20 minutes (15.04 took only 10 minutes on my machine) even after re-adding ppas and re-installing programs you are still WAY ahead and it is much less likely to go wrong.

Edited: disabling ppas is not enough because upgrade check package versions. If you keep the ppa packages the versions will come out higher than expected, or even higher than what you are about to "upgrade" to and this confuses the upgrader.

---

### Post by mikodo on 2015-06-12
> **monkeybrain20122 said:**
> It will be much faster to do a clean install than to restore your system to pristine state and then upgrade. Clean install takes 15 - 20 minutes (15.04 took only 10 minutes on my machine) even after re-adding ppas and re-installing programs you are still WAY ahead and it is much less likely to go wrong.

Edited: disabling ppas is not enough because upgrade check package versions. If you keep the ppa packages the versions will come out higher than expected, or even higher than what you are about to "upgrade" to and this confuses the upgrader.

Alright. 

I have never done anything but clean/fresh installs. Truly, for fun, I plan to upgrade the next time, just to see how well it goes for me. I am trying to give myself the best chance for success hence, the question(s). If it I screw it up well, I'll do like you and clean install again. I just want to try it.

Thanks, for the advice. :)

---

### Post by d-cosner on 2015-06-12
When I ran Ubuntu I never had any problems with upgrading from one release to another. The first time I tried it was because I was out of DVD's to burn an install disk. I used the same method craig10x described and everything worked as expected.

---

### Post by craig10x on 2015-06-12
Oh yes, by the way....some mentioned about purging your ppas but i have found that if you simply uncheck them in the "software sources" as i mentioned previously, it does the same as purging (in terms of not causing any upgrade problems) but at the same time, leaves them on so that all you have to do is re-check them again AFTER you boot into the new upgraded version...;)

---

### Post by buzzingrobot on 2015-06-12
> **craig10x said:**
> Oh yes, by the way....some mentioned about purging your ppas but i have found that if you simply uncheck them in the "software sources" as i mentioned previously, it does the same as purging (in terms of not causing any upgrade problems) but at the same time, leaves them on so that all you have to do is re-check them again AFTER you boot into the new upgraded version...;)

This make sense. If a PPA remains active in the list of sources during a release upgrade, packages maintained at that PPA may be upgraded/installed. I don't know when in the process the sources list is rewritten to reflect the new target repositories. In any case, there's no guarantee that a PPA package that worked with, say, 14.04, will work well with 15.04.  If the 14.04 package replaced a core component and no 15.04 equivalent exists, then would the release upgrade process remove the 14.04 PPA package and install the 15.04 package, or would it do something else, or nothing? (My own preference would be that the upgrade process install and use exactly the same packages as would happen in a clean install, disabling but not removing conflicting packages.)

Installing packages from some PPA's, though, can trigger the replacement of a number of packages from the same PPA for dependency reasons. Video card driver PPA's often do this, in my experience.

---

### Post by Bucky Ball on 2015-06-13
Yes, unticked during upgrade is all I've ever done to PPAs. No need to purge. One issue though, yea, sure, you can switch them on again after the upgrade, but that does not guarantee that you are switching on a PPA for your new release. It may be a PPA specific to your old one and there may not be anything in it for the new release. Check and change where necessary.

---

### Post by monkeybrain20122 on 2015-06-13
It makes no sense that as a general rule you can just disable the ppas without purging. Many ppas boost system libraries to higher versions than the repo's (or even higher than the versions in next release) there is no install candidate if you want to upgrade/or install packages which depend on these with the ppa turned off. You can see this phenomenon just in normal software install and upgrade (as oppose to system upgrade) For some ppa maybe you can just check it off but that is because they don't upgrade pieces that other packages may depend on (or perhaps the version in the new release is higher)but not as a general rule, e.g if you use xorg-edgers in Trusty then chances are the versions of a lot of system libs are even higher than the corresponding versions in vivid's repo and you will have a broken system if you try to 'upgrade' to Utopic or Vivid without purging it first.

---

### Post by kansasnoob on 2015-06-13
> **monkeybrain20122 said:**
> It makes no sense that as a general rule you can just disable the ppas without purging. Many ppas boost system libraries to higher versions than the repo's (or even higher than the versions in next release) there is no install candidate if you want to upgrade/or install packages which depend on these with the ppa turned off. You can see this phenomenon just in normal software install and upgrade (as oppose to system upgrade) For some ppa maybe you can just check it off but that is because they don't upgrade pieces that other packages may depend on (or perhaps the version in the new release is higher)but not as a general rule, e.g if you use xorg-edgers in Trusty then chances are the versions of a lot of system libs are even higher than the corresponding versions in vivid's repo and you will have a broken system if you try to 'upgrade' to Utopic or Vivid without purging it first.

+1!

If added properly all PPA's should appear in /etc/apt/sources.list.d now, although I still do occasionally encounter PPA's added to /etc/apt/sources.list improperly (or as a result of ancient upgrades). Basically, it required user action to install packages from PPA's which all say "You can update your system with unsupported packages from this untrusted PPA" so user action will be required to restore the OS package list to a pristine condition before upgrading.

While preparing to "ppa-purge" it's also wise to use the "-s" suffix to see what form of breakage may occur when purging each PPA. The "-s" suffix simply simulates what will happen so if breakage appears imminent you can stop and regroup.

But my biggest question is, why upgrade 14.04 to 14.10 and then 15.04???? Ubuntu 14.04 is a 5 year LTS (supported until April 2019), and the "flavors" are supported for 3 years (until April 2017) so why upgrade every 6 months? 

If it ain't broke don't fix it. If it is broke it probably won't upgrade properly anyway, and it's quite possible to lose a wireless connection during upgrades so access to a high-speed wired connection is almost a must have.

Also, if Ubuntu (or one of the official flavors) is the only operating system on the machine it's now possible to upgrade using a live DVD/USB which uses apt-clone. Using that method apt-clone simply will not reinstall any packages that are not available in the official repos.

---

### Post by buzzingrobot on 2015-06-13
> **monkeybrain20122 said:**
> It. makes no sense that as a general rule you can just disable the ppas without purging. Many ppas boost system libraries to higher versions...

As my rather long caveat mentioned.  It comes down to changes a users makes to a baseline system. Some will be innocuous, some maybe not so innocuous. Purging PPA's is one form of trying to return a system to a baseline configuration before doing a release upgrade. Ideally, users would record all changes to a system, not just adding packages from unsupported sources like PPA's. (And more users should note what "unsupported" means.)

---

### Post by mikodo on 2015-06-13
dumb stupid post.

---

### Post by monkeybrain20122 on 2015-06-13
> **kansasnoob said:**
> 

But my biggest question is, why upgrade 14.04 to 14.10 and then 15.04???? Ubuntu 14.04 is a 5 year LTS (supported until April 2019), and the "flavors" are supported for 3 years (until April 2017) so why upgrade every 6 months? 
.

Well there are reasons to switch to an interim release. e.g LTS too old for new hardware, some software not installable because of old libs etc. For myself a reason is that the ffmpeg vs avconv situation is kind of messy in 14.04 (the -dev files cannot coexist so I have to compile a lot of stuffs just because I can't install the avconv-dev files since I use the ffmpeg' ones)in 15.04 it is a lot cleaner, just get ffmpeg and that's it. But anyway, the question is about why upgrade breaks, not whether one should upgrade. Personally I always do clean install.

---

### Post by mikodo on 2015-06-13
> **kansasnoob said:**
> If added properly all PPA's should appear in /etc/apt/sources.list.d
aah!

```
/etc/apt/sources.list.d/libreoffice-ppa-trusty.list
/etc/apt/sources.list.d/libreoffice-ppa-trusty.list.save
/etc/apt/sources.list.d/rvm-smplayer-trusty.list
/etc/apt/sources.list.d/rvm-smplayer-trusty.list.save
/etc/apt/sources.list.d/unit193-crosswire-trusty.list
/etc/apt/sources.list.d/unit193-crosswire-trusty.list.save
/etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-trusty.list
/etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-trusty.list.save
```

---

### Post by craig10x on 2015-06-13
Yes, that is why i also prefer the latest release....you get newer apps and often it runs smoother and more refined then the previous version and that's why i don't stick with the LTS...That's why i like the concept of snappy desktop stable....because that would give you a stable base along with all the latest apps and features on a continuous basis (with re-installing or upgrading) so i hope that eventually it will make it to prime time and be available as an option...

Regarding ppas...well, actually the only one i have is for Google Chrome's updater so maybe that is why just unchecking and re-checking after install never causes any problems when i do an upgrade...

---

### Post by Bucky Ball on 2015-06-13
> **monkeybrain20122 said:**
> Well there are reasons to switch to an interim release. e.g LTS too old for new hardware, some software not installable because of old libs etc.

One remedy is to [run the newer kernel in the LTS release]("http://linuxg.net/how-to-install-kernel-4-0-on-ubuntu-15-04-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/"). I've done that a few times due to there being a particular hardware driver in the newer kernel. Guess the kernel might be unsupported when the release it belongs to is, but by then a new LTS would hopefully have arrived. :)

---

### Post by mikodo on 2015-06-13
> **kansasnoob said:**
> Also, if Ubuntu (or one of the official flavors) is the only operating system on the machine it's now possible to upgrade using a live DVD/USB which uses apt-clone. Using that method apt-clone simply will not reinstall any packages that are not available in the official repos.
Added insurance!  :)

---

### Post by craig10x on 2015-06-13
I have used the upgrade feature on the ubuntu install dvd in the past, and from my experience, unlike the "in place" upgrade which is actually done ON your drive (using software updater) that the dvd upgrade process is not as reliable...using that method, apps were often lost, sometimes even certain settings had to be changed after install...data usually came through fine, though...but i never had 100% perfect upgrade using the dvd method as compared to the software updater way...Probably because the stuff has to be transferred from the dvd to the drive instead of being done directly on it...

---

### Post by monkeybrain20122 on 2015-06-13
> **Bucky Ball said:**
> One remedy is to [run the newer kernel in the LTS release]("http://linuxg.net/how-to-install-kernel-4-0-on-ubuntu-15-04-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/"). I've done that a few times due to there being a particular hardware driver in the newer kernel. Guess the kernel might be unsupported when the release it belongs to is, but by then a new LTS would hopefully have arrived. :)

Sure, but that is only one part of the equation, you may also need e.g the latest mesa driver for your graphic card. You can get that from xorg-edgers or oibaf ppa but these are beta drivers, one may prefer the latest stable in the most up to date Ubuntu release (xorg-edgres and oibaf are offering mesa 1.7 now, vivid has the latest stable mesa 1.5, Trusty's default is 1.2 I think, which is buggy on my machine,--some animations are very sluggish,--so I updated to 1.6 and then disable oibaf and re-enable it to upgrade only every 2-3 months)

---

### Post by mikodo on 2015-06-13
> **craig10x said:**
> I have used the upgrade feature on the ubuntu install dvd in the past, ... what you said ...
Good to know.

---

### Post by SurfaceUnits on 2015-06-13
> **mikodo said:**
> Alright. 

I have never done anything but clean/fresh installs. Truly, for fun, I plan to upgrade the next time, just to see how well it goes for me. I am trying to give myself the best chance for success hence, the question(s). If it I screw it up well, I'll do like you and clean install again. I just want to try it.

Thanks, for the advice. :)

The only ppa's you need to purge are add ons that don't come with the standard buntu image or that modify core OS files, something like Gnome3 Team ppa. If you've added a ppa for Firefox of LibreOffice for instance,  the upgrade will take care of that.

---

### Post by mikodo on 2015-06-14
> **SurfaceUnits said:**
> The only ppa's you need to purge are add ons that don't come with the standard buntu image or that modify core OS files. ...
Alright.

Thanks.  :p

---

### Post by LastDino on 2015-06-14
Honestly, I've more trouble updating/upgrading my Windows side of the machine than I do with Ubuntu. And within the Linux family, Ubuntu is probably one of the least troublesome followed by Fedora. At least compared to Arch based family, Manjaro is fairly stable though.

Could be just me.

---

### Post by buzzingrobot on 2015-06-14
> **SurfaceUnits said:**
> The only ppa's you need to purge are add ons that don't come with the standard buntu image...

There are no PPA's in the standard official install.

> ...If you've added a ppa for Firefox of LibreOffice for instance,  the upgrade will take care of that.

Firefox is built as a standalone app that does not created the dependency chain typical Linux apps do. That's why distributions can quickly distribute each of the frequent upgrades. (Ditto LibreOffice, I believe.) Although I've never used a PPA for Firefox since updates are pushed to the repos within a day or so. 

But, if a PPA is active in the list of sources during any upgrade, and a new package is available, then the upgrade process will try to install it.  For Firefox, that's almost certainly always going to succeed. With others, which will target typical Linux packages, the success of the upgrade depends on whether or not any existing or newly installed PPA package are compatible with official packages, and whether or not a PPA creates an unresolveable dependency chain.  Fixing those problems is annoying and often difficult for experienced users and most likely beyond the abilities of most users.

The best approach is to copy your list of PPA's and other unofficial sources off somewhere, disable/remove the PPA sources, use ppa-purge and common sense to remove PPA packages (assuming you kept a list of packages installed from each PPA) unless you are certain they will not interfere with the upgrade, do the upgrade, reinstall the PPA sources and attempt to re-install the needed packages, after determining that the PPA actually maintains packages built for the new release.

This is a long and tedious process. One reason to avoid loading system with PPA's. Few people record the packages installed from PPA's and, I suspect, most users cut-and-paste PPA install lines from a web site without ever visiting the PPA's site to see what it has to say.
\

---

### Post by SurfaceUnits on 2015-06-14
No one said there was, but there are 13,452 PPA's for items that don't come in the standard install and that is what you need to watch for in your upgrade. PPA's are also used to keep software updated on older OS releases.

---

### Post by craig10x on 2015-06-14
Actually though, if you just use update ppas it wouldn't seem you would have anything to worry about if you just uncheck (disable) them before the upgrade and re-check (enable) after it's done...

---

### Post by monkeybrain20122 on 2015-06-14
> **buzzingrobot said:**
> 
This is a long and tedious process. One reason to avoid loading system with PPA's. Few people record the packages installed from PPA's and, I suspect, most users cut-and-paste PPA install lines from a web site without ever visiting the PPA's site to see what it has to say.


Yes, this is a long and tedious process, but instead of avoiding ppas one can just do clean install instead of 'upgrade'. I never understand what the appeal of upgrade is. Even in best case scenario (pristine system) it takes a lot longer to upgrade than to just clean install and reinstall all your applications (if you have a separate /home than all your user settings (e.g firefox tabs) would be saved)

Reinstall applications is fast and easy if your system is standard. If you have a lot of tweaks and customisation,--the only reason why one would want to do 'upgrade' but then in this only scenario where upgrade may be desirable chances are it would be messy so you're better off doing a clean install anyway. So in conclusion clean install is always preferred.

---

### Post by help_me2 on 2015-06-17
I never do online upgrades. I just have a separate /home partition that I keep and clean install the / partition. Takes maybe 40 min. from the start of the install to where I was before. I don't see the need to do a questionable online upgrade.

---

### Post by help_me2 on 2015-06-17
> **monkeybrain20122 said:**
> Yes, this is a long and tedious process, but instead of avoiding ppas one can just do clean install instead of 'upgrade'. I never understand what the appeal of upgrade is. Even in best case scenario (pristine system) it takes a lot longer to upgrade than to just clean install and reinstall all your applications (if you have a separate /home than all your user settings (e.g firefox tabs) would be saved)

Reinstall applications is fast and easy if your system is standard. If you have a lot of tweaks and customisation,--the only reason why one would want to do 'upgrade' but then in this only scenario where upgrade may be desirable chances are it would be messy so you're better off doing a clean install anyway. So in conclusion clean install is always preferred.
I 100% agree. When installing Ubuntu from a flash drive, it should only take someone about 8 min. to reinstall, then reinstall your apps. But I guess people would rather take over an hour to do an online upgrade then spend more time trying to fix things. <scratches head> <shrugs shoulders>

---

### Post by MartyBuntu on 2015-06-17
I got over the "installing OS's is fun!" thing about 9 years ago....

---

### Post by SurfaceUnits on 2015-06-19
> **craig10x said:**
> Actually though, if you just use update ppas it wouldn't seem you would have anything to worry about if you just uncheck (disable) them before the upgrade and re-check (enable) after it's done...

The upgrade process disables PPA entries before it runs the update. but it is messier than disabling them yourself.

---

### Post by sports fan Matt on 2015-07-11
This is a few weeks old, but way back in November 1st, 2007, I wanted a way out of the viruses world that was Microsoft and started with 7.10 Gutsy Gibbon.  I upgraded every six months till around Lucid, then decided LTS were the way to go for me.  No issues on really any release, probably because i have Intel hardware.

---

