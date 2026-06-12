---
title: "Too much distrohopping becomes a chronic disease"
date: 2014-12-30
forum: The Cafe
---

### Post by linuxyogi on 2014-12-30
Hi,

Leaving 8.04 there is not a single release of any distro that I have used till its EOL. After 8.04 I moved to openSUSE, Manjaro Gnome/MATE/XFCE/LXDE, PCLINUXOS, FreeBSD, PCBSD, Linux Mint, LMDE, Antergos. Ubuntu MATE, Fedora, Slitaz.

I stayed on each distro for max 3-4 months. I had lost a considerable amount of data during this period. Specially while moving from Linux to BSD coz I didn't have an external HDD back then. I have purchased an external HDD now and I rsync almost every day.

Any one experienced a similar situation ?

---

### Post by Bucky Ball on 2014-12-30
I only run the LTS releases as my main squeeze and have a few partitions for 'plaything', like other distros and interim releases of Ubuntu.

I have all my data stored on a /data partition. Inside the /home directory of each install I have symlinks to the data directories on the data partition. That way, all installs are accessing the same data and whatever changes made in any install are reflected to all the others. I also use the same /swap partition for all installs (as they can only be booted one at a time).

For testing distros, maybe try using virtual machines. Virtualbox is in the Software Centre and is pretty straightforward. You can run the distro directly from the ISO without needing to create install media. 

[This]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979") gives some ideas about symlinks. Good luck. ;)

---

### Post by sammiev on 2014-12-30
I guess I'm stuck on gnome, but I have most others installed under VM.

---

### Post by linuxyogi on 2014-12-31
I know it doesn't make any sense but the fact is I never feel satisfied with virtualization. To me if its not running on real hardware it doesn't count.

---

### Post by Bucky Ball on 2014-12-31
Know the feeling. I went through a virtualisation craze that lasted about a month and haven't been there since. That's why I have a few spare partitions. ;)

---

### Post by user1397 on 2014-12-31
I concur.  I'm permanently dissatisfied with at least a few aspects of any particular distro/OS.  It is most frustrating.

I also hate the sluggishness/"fake" factor of virtualization, but it is definitely a whole lot easier to at least preview a distro than to install it to a partition (I've long since abandoned the whole distro hopping on different partitions game).  I had a few virtualbox crazes myself but I think I'm mostly done (for now :))

I also agree with Bucky Ball about symlinking to a /data partition.  Definitely safer and easier than having separate /home partitions.

---

### Post by linuxyogi on 2014-12-31
Problem with dual booting Linux and BSD is you have to manually add an entry in the active grub. BTW, PCBSD is also using grub2 and to dual boot one need to manually add an entry in 40_custom file mentioning EXT2 and some other modules. Most of the Linux distros I have tried dual booting recognizes the other distro and adds the entry but PCLINUXOS doesnt. Its still using Grub legacy

---

### Post by Bucky Ball on 2014-12-31
> **ubuntuman001 said:**
> 

I also agree with Bucky Ball about symlinking to a /data partition.  Definitely safer and easier than having separate /home partitions.

Agreed. Also means you only have to backup one data partition and you don't have data spat all over various partitions, which gets confusing and can be hard to keep track of what's where.

---

### Post by d-cosner on 2014-12-31
I did more than my share of distro hopping this year.... Mainly searching for a distro with a complete, current version of Gnome Shell. I ended right back on Ubuntu 14.04 and with Fedora 21 on another hard drive. I needed Ubuntu installed to help support people that I have switched from Windows. I managed to work around the couple of things that bugged me and updates did the rest. Fedora 21 just worked, that was a welcome change!

I back up my data so changing distros was not a problem. It seems I have finally settled down and decided to just use my computer rather than re-load it all the time. :) Jumping around from different distros does get on your nerves after a while and for the most part they all have their fair share of annoying bugs. Ubuntu has been behaving pretty decent this time around and I have been using it daily for a while now.

I still have the Fedora install in case I get the urge to run Gnome Shell and it only takes a minute to swap the hard drives.

---

### Post by mbott on 2014-12-31
At least I only bounce between Mint and Ubuntu.  ;)

Edited to add:

> I ended right back on Ubuntu 14.04 and with Fedora 21 on another hard drive. 

Oh great!  Now I find myself burning a copy of Fedora to check it out.  Thanks alot d-cosner.  :)

-- 
Mike -- looking for a spare hard drive.

---

### Post by d-cosner on 2014-12-31
> Oh great!  Now I find myself burning a copy of Fedora to check it out.  Thanks alot d-cosner.  :smile:

If you are interested in Gnome Shell it really is worth a look!

---

### Post by linuxyogi on 2015-01-01
In my experience the Nvidia non free driver installation of Fedora is very problematic. I installed Fedora 21 two times but after I installed the binary driver from rpmfusion I got a black screen with a blinking cursor. The main reason I tried Fedora is selinux.

---

### Post by Tuxclear on 2015-01-01
Yes, I feel that all the time. I have tried distros and OSes and the only ones that I think are best are Ubuntu and OpenBSD. The things that I want from an open-source OS are flexibility and functionality and for some reason, it's difficult to find these in most linux distros.

---

### Post by ventrical on 2015-01-01
I would mainly only VM Windows XP and 8, just to have it in a fish bowl so to speak :) I do a lot of private testing elsewhere but (n)Ubuntu get the greater part of my time. Any OS that allows me to have 50, 60 or greater Firefox tabs open at the same time is a researchers dream - and not only that .. but with no performance lag. Even on older machines, there is nothing out there today atm which can hold a candle to (n)ubuntu. Firefox deserves lots of kudos also.

   Running Ubuntu is like being a kid in a candy store  that has a credit card with no limit. Not only that but there is the educational aspect from all the KBs that we don't have to pull our hair out trying to obtain information, solutions and discoveries.

Regards..

---

### Post by Tuxclear on 2015-01-01
It is said that the fastest and most powerfull Linux distribution is Gentoo. Have you tried it?

---

### Post by linuxyogi on 2015-01-01
No but I used Sabayon for some months. Sabayon is similar to what Manjaro is to Arch. I tried Antergos once. It uses the Arch repos directly and my experience was horrible. Three breakages in one week and there was no warning in the Arch news. Gentoo is quite similar to Arch in terms of stability so I am gonna stay away.

---

### Post by Tuxclear on 2015-01-01
> **linuxyogi said:**
> No but I used Sabayon for some months. Sabayon is similar to what Manjaro is to Arch. I tried Antergos once. It uses the Arch repos directly and my experience was horrible. Three breakages in one week and there was no warning in the Arch news. Gentoo is quite similar to Arch in terms of stability so I am gonna stay away.

I actually was applying to ventrical's post, but OK. :p

I don't know how stable or functional it is, but in terms of speed, when I personally used Calculate Linux and tried to install [COLOR=#cc6633]*firefox*[/COLOR], portage was so slow with compiling that the whole system froze.

---

### Post by mbott on 2015-01-01
> **d-cosner said:**
> If you are interested in Gnome Shell it really is worth a look!

I guess it's just not for me.  Just too many things that are almost instinctive for me in Ubuntu required too much thought in Fedora. I guess I'm too old to learn new tricks. It's interesting though that Fedora was the first linux-based OS that I tried when escaping from windows.  :)  **Edited to add:** Just checked the Fedora Forum and I signed up back on 15 Jan 2007.  

Thankfully hard drives are relatively inexpensive.

-- 
Mike

---

### Post by mips on 2015-01-01
I really don't see the point in distro hopping. You will never find a distro that suites you 100%. Find something you like the most and mould it to your liking. I still install ubuntu or mint for people. The other day I upgraded someones 13.10 ubuntu install which was <400MB download and the whole process took ages compared to updating a arch based distro using pacman. Thing is the update also bombed the entire system which I said I would fix with the latest lts install when I have time. Once you find something or a component of it you like overall stick with it, for me it's the pacman package manager.

---

### Post by user1397 on 2015-01-01
> **ventrical said:**
> I would mainly only VM Windows XP and 8, just to have it in a fish bowl so to speak :) I do a lot of private testing elsewhere but (n)Ubuntu get the greater part of my time. Any OS that allows me to have 50, 60 or greater Firefox tabs open at the same time is a researchers dream - and not only that .. but with no performance lag. Even on older machines, there is nothing out there today atm which can hold a candle to (n)ubuntu. Firefox deserves lots of kudos also.

   Running Ubuntu is like being a kid in a candy store  that has a credit card with no limit. Not only that but there is the educational aspect from all the KBs that we don't have to pull our hair out trying to obtain information, solutions and discoveries.

Regards..
jesus what kind of hardware do you have?  I can't imagine running that many tabs without the system grinding to a halt.  And you say this is only possible for you under ubuntu (unity)? That again seems surprising, you would think you would be running lubuntu at least or something lighter...

Also what did you mean by "KBs"?

---

### Post by user1397 on 2015-01-01
> **mips said:**
> I really don't see the point in distro hopping. You will never find a distro that suites you 100%. Find something you like the most and mould it to your liking. I still install ubuntu or mint for people. The other day I upgraded someones 13.10 ubuntu install which was <400MB download and the whole process took ages compared to updating a arch based distro using pacman. Thing is the update also bombed the entire system which I said I would fix with the latest lts install when I have time. Once you find something or a component of it you like overall stick with it, for me it's the pacman package manager.
So you run arch as your main OS I take it?  I found pacman to be as good as apt and I liked the minimalist and control aspect of arch.  Only thing I wasn't too fond of is constant maintenance (as in having to look up whether any updates would break the system all the time) and how it's sorta a pain if you ever have to reinstall.

Otherwise, I agree for the most part with your first comment.  Indeed, most people won't ever find a distro that suites them 100%, but I think a bit of distro-hopping at first is essential to find the distro that suites you the best.  Constant distro hopping is where the problem lies hehe.

---

### Post by mips on 2015-01-01
> **ubuntuman001 said:**
> So you run arch as your main OS I take it?

No, been running Manjaro based on Arch which uses pacman  since 2012. Less frequent updates (compared to Arch) and none of the maintenance issues keeping an eye on the update news. Prior to that I ran Arch for a long time. Also did Sabayon for a while after trying Gentoo. Last fond memory of Ubuntu for me was 6.06, tried newer versions a few times after that but 6.06 still sticks in my mind :D

---

### Post by d-cosner on 2015-01-01
Trying out Ubuntu Mate 14.04 x64 today on a spare drive!

Edit: The developers really did a great job with this! It sure looks nice too! Almost forgot what it was like having a screen saver and this is really light. Glad I did not fight the urge to try this!

---

### Post by MrSteve on 2015-01-01
done my share of distro hopping
red hat - fedora - lindows- xandros - debian - lubuntu - xubuntu - ubuntu - mint
and a few others that i cant remember over the years

finally found my home kubuntu 14.04 LTS ...
have it set up with a separate / (20GB) and /home (rest of HDD) partitions plus a backup HDD.

---

### Post by mbott on 2015-01-01
> **mips said:**
> I really don't see the point in distro hopping. 

I know in my case, it's kinda fun and entertaining.  I learn something new every time and gives me exposure to other ways of doing things.  

There are times it is like watching a dog chase it's tail for 5 minutes and then you realize you just watched a dog chase it's tail for 5 minutes.

-- 
Mike

---

### Post by user1397 on 2015-01-01
> **mips said:**
> No, been running Manjaro based on Arch which uses pacman  since 2012. Less frequent updates (compared to Arch) and none of the maintenance issues keeping an eye on the update news. Prior to that I ran Arch for a long time. Also did Sabayon for a while after trying Gentoo. Last fond memory of Ubuntu for me was 6.06, tried newer versions a few times after that but 6.06 still sticks in my mind :D
O ok.  Gonna check out manjaro for sure then.  Indeed, 6.06 is one of my fondest memories of old ubuntu as well :P

---

### Post by mikodo on 2015-01-01
+1 for sym-linked data partitions/drives. It is also great for re-installing or for new installs.

I too, am pretty much done with distro hopping also. They can be very entertaining but, I find it addictive.

The more I find out about BDFL/Canonical/Ubuntu/Xubuntu, the surer I am about using it and learning more. Recently I found that Ubuntu jails, lots of services for security, including more to come or whatever people call it here, (AppArmor). I allowed this for Firefox in Xubuntu, with no ill effects on the browsing experience. Chromium is is set at complain-mode, out of the box. I would give a link to this, but I don't remember where I found it. hmm. I am going to have to find how that is done again???

---

### Post by sffvba[e0rt on 2015-01-02
Wait... there is more than one distro?!

---

### Post by Bucky Ball on 2015-01-02
> **not found said:**
> Wait... there is more than one distro?!

lol ;)

---

### Post by vasa1 on 2015-01-02
> **ubuntuman001 said:**
> ...

Also what did you mean by "KBs"?
Probably KBs = knowledge bases.

---

### Post by mbott on 2015-01-02
> **d-cosner said:**
> Trying out Ubuntu Mate 14.04 x64 today on a spare drive!

Edit: The developers really did a great job with this! It sure looks nice too! Almost forgot what it was like having a screen saver and this is really light. Glad I did not fight the urge to try this!

You did this on purpose!

-- 
Mike

---

### Post by d-cosner on 2015-01-02
> You did this on purpose!

:)

Yeah, I did! I found some things to customize it too and it really looks amazing! This will allow you to change the greeter background to match your desktop wallpaper.

[http://www.webupd8.org/2014/10/lightdm-gtk-greeter-settings-gui.html](http://www.webupd8.org/2014/10/lightdm-gtk-greeter-settings-gui.html)

Also, I gave it a more Ubuntu look using the Ambiance themes from a ppa. Not only is this light and fast, it looks great too! I think this is a keeper!

---

### Post by PondPuppy on 2015-01-03
My desktop PC stays with Ubuntu (currently 14.04) but I have other distros on a couple of laptops. Manjaro is a good one, and I use Salix too -- like Manjaro, it's a fast-and-easy distro, but based on Slackware instead of Arch. There are two partitions on the 32-bit older laptop that get new distros now and then -- currently Elementary and OpenSUSE, but I'm not thrilled with either.

As far as data goes, nothing much lives on the laptops except the OSes and applications. The desktop and its backup drives are where all the files go. I could completely wipe either of the laptops and lose nothing of importance, so it's easy to do some distro-hopping.

I sympathize with Mips' point of view -- choose the distro which is best for you and stick with that -- but I kind of like tinkering with different GUIs and setups. To each his own.

---

### Post by mbott on 2015-01-04
> **PondPuppy said:**
> My desktop PC stays with Ubuntu (currently 14.04) but I have other distros on a couple of laptops. Manjaro is a good one, and I use Salix too -- like Manjaro, it's a fast-and-easy distro, but based on Slackware instead of Arch. There are two partitions on the 32-bit older laptop that get new distros now and then -- currently Elementary and OpenSUSE, but I'm not thrilled with either.

As far as data goes, nothing much lives on the laptops except the OSes and applications. The desktop and its backup drives are where all the files go. I could completely wipe either of the laptops and lose nothing of importance, so it's easy to do some distro-hopping.

I sympathize with Mips' point of view -- choose the distro which is best for you and stick with that -- but I kind of like tinkering with different GUIs and setups. To each his own.

I have almost the same atitude and practice as PondPuppy.  My desktop is my permanent Ubuntu system (14.04 LTS), except for tax time, when I disconnect the Ubuntu hard drive and re-connect the system to a win8 hard drive. My preference is to run TurboTax locally while I prepare our taxes. My laptop is purely for fun: surfing, music and experimentation with music being the most important part. Oh, I do keep my reloading log on it because it resides in the basement.

My foray into Ubuntu Mate is currently continuing. Bluetooth is the only real issue I've encountered so far and I'm guessing it will just be a matter of time until it's resolved. Anyway, it keeps me off the streets. 

I'd really like to find a reason to renew my SQL skills, which have really fallen off since my retirement 6 years ago. Maybe when I'm done distrohopping.

-- 
Mike

---

### Post by Bucky Ball on 2015-01-04
Nice work, mbott. Really enjoyed reading [that]("http://ubuntuforums.org/showthread.php?t=2258841&page=4&p=13200587&viewfull=1#post13200587"). ;)

---

### Post by Mike_Walsh on 2015-01-04
I think I've had my fill of distro-hopping; 6 months is enough for me.

Tried ALL the 'buntus; PCLinuxOS. Mint, Zorin, SliTaz, Kolibri (just a toy, really; can't DO owt with it.....but I LOVE those 'eyes' on the desktop!)....and a whole bunch of Puppies (Wary, Racy, Precise, Slacko). Wanted to try Damn Small Linux too, but couldn't get it to run...

I've now settled down to Ubuntu on my Compaq desktop; Xubuntu on a 16GB flash drive.....and Puppy Linux 'Tahrpup' on my old brick of a laptop, a Dell Inspiron 1100 from 2002.

Never tried VMs; never got bitten by 'the bug'. Like Linuxyogi, I'd rather run the real thing.

Lubuntu & Ubuntu share a /home partition, and 'Puppy' file-shares with the two of them via SAMBA.....and prints over the home network, too, so....that'll do me. And back-ups are taken care of by a USB hard drive that I plug in once a week, and sync to. It then gets unplugged and put back in the bottom drawer of my desk till next time.

Only use Samba because we have a modern Dell lappie in the house running Windows 7; go figure. And 'Puppy' has a Samba client built-in as standard, so it's easier just to use it. Does the job.

I've still got 2 or 3 spare partitions on the external Seagate, though.....just in case!


Regards,

Mike. ;)

---

### Post by Erik1984 on 2015-01-04
I have never really distro hopped outside the *buntusphere but I did switch a lot between Ubuntu and Kubuntu as I like them both for different reasons, normally don't using one install longer than 6 months. But my current Kubuntu install (including one upgrade) is about 11 months old and I hope to keep this one for a while. The trick is having enough things to do to prevent you from messing too much with the OS, boredom is the enemy :P

---

### Post by PondPuppy on 2015-01-04
How many of you have a handful of distros on thumb drives? I've taken to using Porteus from a thumb drive in "always new" (amnesiac) mode when I'm going online over airport wifi, and I have a couple of Puppies that I carry with me as well.

---

### Post by Mike_Walsh on 2015-01-04
> **PondPuppy said:**
> How many of you have a handful of distros on thumb drives? I've taken to using Porteus from a thumb drive in "always new" (amnesiac) mode when I'm going online over airport wifi, and I have a couple of Puppies that I carry with me as well.

Snap!

'Slacko' 5.7 & 'Tahrpup' 6.0.....+Lubuntu 14.04 32-bit.

I LIKE the Puppies; they were originally designed for flash-drives, anyway, as you probably know. I like 'Tahrpup' so much, I've done a frugal install onto my hard drive, alongside Ubuntu 14.04. I feel a bit guilty, 'cos 'Tahrpup' is getting WAY more use than Ubuntu at the moment!

And I like having one of the 'buntus with me, too.....so I settled for the 32-bit version of the lightest one of all. 

Works a treat.


Regards,

Mike.

---

### Post by mips on 2015-01-05
> **PondPuppy said:**
> How many of you have a handful of distros on thumb drives?

Only one I have is [Kali]("https://www.kali.org/"), swiss army knife in case of emergency.

---

### Post by kevdog on 2015-01-06
I just pretty much stick with Ubuntu and Arch.  Ubuntu LTS seems so rock stable its boring -- which is good for a server environment.  For daily use, Arch gives me plenty to play with.  Argh -- recent pacman upgrade caused issues.  It's enough for me to learn about the linux systems that I seem content.

---

### Post by mamamia88 on 2015-01-06
I'm done distrohopping I hope.  From now on I'm either using a debian based distro or arch.   I think I will most likely stick with debian based stuff though because I like to install chrome/dropbox on all my computers and I like the fact that debs are supplied.   Arch is great but, I don't want to rely on someone updating pkgbuilds in a timely manner.   Sure I could do it myself but, too lazy nowadays.

---

### Post by user1397 on 2015-01-09
> **vasa1 said:**
> Probably KBs = knowledge bases.
Gotcha, thanks.

---

### Post by d-cosner on 2015-01-10
So glad I have a spare hard drive! I took a look at the Korora 21 Cinnamon beta release this morning. I was stunned when I saw how nice they made Cinnamon look! I love the flat round icons it uses by default, they really look good in Cinnamon! The plymouth theme is nice too, just a simple thin blue progress bar. The greeter uses a simple blue background, I personally like this because it transitions to the desktop so much nicer.

The Fedora base Korora uses was up to date other than just 2 packages, very impressive and even the kernel was up to date. I loved Fedora 21 but this is even better to me because Cinnamon is more resource friendly and the Korora developers did an amazing job of making everything look good and modern. Multimedia playback worked right out of the box with no crippled applications. I did have to turn off a Firefox add-on to get flash videos to play but I was fine with that.

Cinnamon runs great with the underlying Gnome 3.14 packages, it's quick! This just might end my distro hopping once and for all, it's that nice! I do still have Ubuntu 14.04 installed on my laptop and my other desktop hard drive and they will stay there because the LTS has a lot of support time. The spare hard drive will remain plugged in though on the desktop because this has everything I could ever want and it runs perfect on my hardware.

Edit: I took the time to join the Korora Forum to thank the developers for their fine work on this release. I am still blown away at how nice this is!

---

### Post by kagashe on 2015-01-13
Mandrake Linux 9.1 (Renamed Mandriva later on)
Mandrakelinux 10
Ubuntu since 5.04 version
Linspire
LFX 6.1 & BLFS
Fluxbuntu 7.10
gOS
DSL
Puppy
SLAX
Mandriva 2008
Slitaz
Debian Lenny
March Linux 2.0
Arch Linux
Fedora 10
Tiny Core Linux
Knoppix 6.0 Live
antiX M8
Zenwalk 6.0
Debian Live LXDE
My Own Ulx 9.04 LIve CD (Ubuntu+LXDE)
Chromium OS
Sidux
PCLinux OS
Ubuntu 10.04 LTS
Ubuntu 12.04 LTS
antiX 13.2
Ubuntu 14.04 LTS

But I always kept Ubuntu alongwith others.

DSL, Puppy Debian were used on my old Desktop which had only 32 MB RAM.

Kamalakar

---

### Post by UsrBinSomething on 2015-01-16
I always like trying out new distros - but now I'll use VirtualBox instead.
I've tried:

Linux Mint
OpenSuse 10.2 - 13.2
Suse 9.2
Fedora
Ubuntu
Lubuntu
Netrunner
Gentoo
Arch
Kali
Debian
Trisquel
GNewSense
Magiea

I use Arch now - it's very fast.

---

### Post by dastasha on 2015-01-17
Ubuntu (K,L,X) since 7.10, Mint, Debian, Backtrack, Kali, Tails, done the VM thing with various [VM]("http://virtualboxes.org/images/") images available for download. Also some weird machines I found (like Pear OS). A few that I forget too.
Also the raspberry pi stuff. (Wheezy, Raspian, Arch with LXDE, Openelec and Android - that counts as linux?)
Ubuntu 14.04 and Unity right now. Stable and pretty.

Thanks to d-cosner I'm now on Korora 21-beta and cinnamon. Looks nice but no graphics acceleration means cinnamon will only run under software rendering mode. I'll try loading up the 32 bit image on my machine next to try and fix that.
Oh and since reading this thread I'm also using Puppy-Tahr with a lovely fast compact USB install.

---

### Post by macbreak on 2015-01-17
> **Bucky Ball said:**
> Agreed. Also means you only have to backup one data partition and you don't have data spat all over various partitions, which gets confusing and can be hard to keep track of what's where.

Oh dear... that's **me.  **:lolflag:

---

### Post by Bucky Ball on 2015-01-17
> **macbreak said:**
> Oh dear... that's **me.  **:lolflag:

Lol. You are not alone, I'm certain. :)

---

### Post by Linuxratty on 2015-01-18
In my younger days,I distrohopped quite a bit. Of late,I've just lost interest in doing it. I'm using ElementaryOS, which sits atop Ubuntu's shoulders. I'm keeping an eye on Xubuntu in case EOS goes the way of the dodo.

---

### Post by d-cosner on 2015-01-18
I think I have the disto hopping out of my system. I have Korora 21 Cinnamon running on my desktop and have it customized better than I have had any other distro looking. Korora has been working perfect with my desktops hardware and I have not had a single problem since installing it.

I switched my laptop to Xubuntu because it has an AMD E1 processor and runs kind of slow. Xubuntu runs great on the laptop and I have it looking as nice as my Korora Cinnamon install. I have been having problems with anything Ubuntu based and plymouth not displaying on shut down and restart, so far the problem has not happened with Xubuntu though. 

Should I have problems with plymouth again on the laptop I might look at Manjaro. I would like to remain with Xubuntu though because it has quite a bit of support time. The laptop is using almost half the resources it did with Ubuntu and it is much more responsive. Thanks to te Korora project and people submitting screen shots here I have Xubutu looking very good now too!

---

### Post by mbott on 2015-01-24
> **d-cosner said:**
> I think I have the disto hopping out of my system. 

I don't think I'll commit quite that strongly, but I have noticed that when I try out other distros, I usually end up back with Ubuntu and Unity because whatever I tried can't be bent to my liking. Hmmm...

-- 
Mike

---

### Post by d-cosner on 2015-01-24
Actually, I was so impressed with Korora 21 that I installed the Xfce edition on the laptop and also on the desktops spare hard drive. So now I have Cinnamon and Xfce to enjoy. The funny thing is that I never cared all that much for Xfce until I tried the Korora 21 Xfce beta, it looks every bit as nice as the Cinnamon edition.

---

### Post by mbott on 2015-01-24
You're doing it again!  ;)

-- 
Mike

---

### Post by sammiev on 2015-01-24
> **d-cosner said:**
> Actually, I was so impressed with Korora 21 that I installed the Xfce edition on the laptop and also on the desktops spare hard drive. So now I have Cinnamon and Xfce to enjoy. The funny thing is that I never cared all that much for Xfce until I tried the Korora 21 Xfce beta, it looks every bit as nice as the Cinnamon edition.

This is why I use a VM. ):P

---

### Post by d-cosner on 2015-01-24
I might just use a virtual machine now that I have found what I want to stick with. :)  I finally found something that I am content with.

---

### Post by craig10x on 2015-01-25
@d-cosner: maybe there is a "distro hoppers anonymous" you know, like alcoholics anonymous :D

---

### Post by d-cosner on 2015-01-25
Hi Craig! I think I do not need any counseling.:) I have been very content with Korora 21 Cinnamon and Xfce and plan on staying with them. The Korora Team's refinements on the 21 series releases is exactly what I had been searching for all this time.

---

### Post by craig10x on 2015-01-25
Ok Don, I will cancel your appointment with the next group meeting ;) :biggrin:

---

### Post by d-cosner on 2015-01-25
Thanks Craig! :D I like everything about Korora 21! The developers actually participate in the forum and even ask if you have suggestions to make it better! The forum is a lot different than what I am used too but the community seems really nice. I really hope these guys get some good press and recognition for their hard work when Korora 21 goes final. Their work has brought back some of that excitement to Linux that I have not felt for a long time. 

Something kind of funny, I had never really heard anything about Korora before. They really need to get some screen shots up for the Korora 21 release. I think they really hit one out of the park this time!

---

