---
title: "Suggestions [What sucks about Ubuntu]"
date: 2007-04-12
forum: The Cafe
---

### Post by RealG187 on 2007-04-12
I like ubuntu so this is why I am gonna say some things that I think need to be improved about it.

1. No MP3, I had to use xine via Automatix and it screwup up my souns it now plays through my internal card oposed  to my USB Audio.

2. Internet, you have to have internet to install anything, this is bad if you dont have it or can't get it working. W/ Windows I could download the files to a flash drive or butn to a CD and install of that, I wish I could download the files I need once, burn them and install them from a CD each time to I don't have to use up bandwidth, etc....

---

### Post by maniacmusician on 2007-04-12
> **RealG187 said:**
> I like ubuntu so this is why I am gonna say some things that I think need to be improved about it.

1. No MP3, I had to use xine via Automatix and it screwup up my souns it now plays through my internal card oposed  to my USB Audio.

2. Internet, you have to have internet to install anything, this is bad if you dont have it or can't get it working. W/ Windows I could download the files to a flash drive or butn to a CD and install of that, I wish I could download the files I need once, burn them and install them from a CD each time to I don't have to use up bandwidth, etc....
1. "sudo apt-get install xine-extracodecs" if you're using xine, or whatever the equivalent packages for gstreamer are.

2. Ubuntu is an internet based distro. That's just the way it is. Internet works fine out of the box if you use ethernet (at least for installation and upgrades; you can always set up wireless later), and even wireless works out of the box sometimes. If you don't have internet access, using Ubuntu is just not a good idea.

---

### Post by Kingsley on 2007-04-12
Eazy does it. Nice avatar.

---

### Post by TravisNewman on 2007-04-12
1. in addition to what maniacmusician said, you can select your default audio device from the sound preferences. It's possible that something you installed somehow reconfigured the default, not sure why, but it's easy enough to change.

2. there are a few projects to put a lot of the most used packages onto a dvd image. You can back up the contents of your package archive in /var/cache/apt (or /var/apt/cache, I can't recall the directory now and I don't have access to my PC at the moment). Using this method, however, you miss out on updated versions. I wish there was a feature to apt that could install updates without having to download the entire package, using either rsync or the equivalent of the update RPM's in Fedora.

---

### Post by RealG187 on 2007-04-12
I think I switched my audio device under the second tab. I am kubuntu now [[http://ubuntuforums.org/showthread.php?t=390839]](http://ubuntuforums.org/showthread.php?t=390839]).


I can get sound outta my USB device using Amarok, haven't tried bak in totem yet....


Anyways, I hate how I have to download it EVERY time, maybe they should make it so it downloads and asks you where to save an offline istaller if you want, as a .deb file..

---

### Post by RealG187 on 2007-04-12
> **Kingsley said:**
> Eazy does it. Nice avatar.

U like Eazy-E too?

---

### Post by BoyOfDestiny on 2007-04-12
> **RealG187 said:**
> <snip>

Anyways, I hate how I have to download it EVERY time, maybe they should make it so it downloads and asks you where to save an offline istaller if you want, as a .deb file..

Well, unless you've cleared them explicitly

your debs are in:

/var/cache/apt/archives

I think synaptic is set to clear them out every 30 days... Dunno if Kubuntu is any different...

---

### Post by RealG187 on 2007-04-12
So I could copy those? If I quickly move them to my USB HD will they be safe?

---

### Post by BoyOfDestiny on 2007-04-13
> **RealG187 said:**
> So I could copy those? If I quickly move them to my USB HD will they be safe?

Yeah, only thing (if you pick like one or two apps) is to make sure you have the deb it needs too.

Like if you downloaded frozen bubble, it automatically grabs frozen-bubble-data. 
So make sure all the debs you need are on the drive.
Should work fine, you can always install the frozen-bubble-data first, so frozen-bubble doesn't complain anything is missing (it might work either way though, haven't tried it in a long time.)

If you just want to put them all, you can copy them back into /var/cache/apt/archives, and Ubuntu will use them again instead of re-downloading everything (it will just grab what's missing or what's newer off the web)

---

### Post by jaimz on 2007-04-13
I always knew ubuntu could be gangsta

---

### Post by zugu on 2007-04-13
Answering to OP:

- lack of a unified clipboard in Gnome
- the eternal sound problem caused by applications using different sound servers / daemons / whatever
- (this is my biggest issue): I have to upgrade the whole distro in order to get my hands on new software; I don't want to upgrade my OS every 6 months. I just want to install it, and for at least a couple of years to be able to install whatever I want.
- undocumented applications (Keyring Manager Help in 7.04, anyone?)
- automated removal of orphan packages in apt-get - it's a pleasure to install something with it, but if one decides to uninstall things using it, it leaves a mess behind.

---

### Post by Nonno Bassotto on 2007-04-13
> **zugu said:**
> Answering to OP:

- the eternal sound problem caused by applications using different sound servers / daemons / whatever
- (this is my biggest issue): I have to upgrade the whole distro in order to get my hands on new software; I don't want to upgrade my OS every 6 months. I just want to install it, and for at least a couple of years to be able to install whatever I want.
- automated removal of orphan packages in apt-get - it's a pleasure to install something with it, but if one decides to uninstall things using it, it leaves a mess behind.

For the sound problems, I hope that PulseAudio may become the standard sound server.

For automated removal, consider using aptitude instead of apt-get. Sadly, it doesn't have a nice graphical interface.

For the upgrade every six months... well, don't you think you should try another distro? For example many people recommend ArchLinux. Otherwise don't expect this to change in Ubuntu: it's just the release cycle that has been chosen. Many people like, and it is at the very base of Ubuntu.

---

### Post by Adamant1988 on 2007-04-13
> **RealG187 said:**
> I like ubuntu so this is why I am gonna say some things that I think need to be improved about it.

1. No MP3, I had to use xine via Automatix and it screwup up my souns it now plays through my internal card oposed  to my USB Audio.

2. Internet, you have to have internet to install anything, this is bad if you dont have it or can't get it working. W/ Windows I could download the files to a flash drive or butn to a CD and install of that, I wish I could download the files I need once, burn them and install them from a CD each time to I don't have to use up bandwidth, etc....

1) Fixed in feisty, it can't be included OOTB but it's in the repos. 

2) APTonCD solves this problem nicely, but since people are downloading/purchasing an operating system that is only available online you can imagine that the demand for this is pretty low.

---

### Post by RealG187 on 2007-04-13
> **Nonno Bassotto said:**
> For the sound problems, I hope that PulseAudio may become the standard sound server.

For automated removal, consider using aptitude instead of apt-get. Sadly, it doesn't have a nice graphical interface.

For the upgrade every six months... well, don't you think you should try another distro? For example many people recommend ArchLinux. Otherwise don't expect this to change in Ubuntu: it's just the release cycle that has been chosen. Many people like, and it is at the very base of Ubuntu.

If I would wanna upgrade to a newer ubuntu, would I have to uninstall my current one and re-install from scratch or can I just pop the CD in and it will change only what it needs to?

---

### Post by RealG187 on 2007-04-13
> **jaimz said:**
> I always knew ubuntu could be gangsta

I was bumpin sum Eazy-E outta Amarok!!

---

### Post by RealG187 on 2007-04-13
> **BoyOfDestiny said:**
> Yeah, only thing (if you pick like one or two apps) is to make sure you have the deb it needs too.

Like if you downloaded frozen bubble, it automatically grabs frozen-bubble-data. 
So make sure all the debs you need are on the drive.
Should work fine, you can always install the frozen-bubble-data first, so frozen-bubble doesn't complain anything is missing (it might work either way though, haven't tried it in a long time.)

If you just want to put them all, you can copy them back into /var/cache/apt/archives, and Ubuntu will use them again instead of re-downloading everything (it will just grab what's missing or what's newer off the web)

Hiow do I install off of .deb files? I can't get Ace of Penguins!

---

### Post by hanzomon4 on 2007-05-26
apt-get autoremove will remove stuff you no longer need. I haven't had audio problems since breezy but yeah it can be a headache. Is pulse audio going to replace ESD?

---

### Post by Albi on 2007-05-26
I've seen countless trolls in my day, and I'm very suspicious of this thread.

You "double click:" the deb file.

---

### Post by H.E. Pennypacker on 2007-05-26
> **Albi said:**
> I've seen countless trolls in my day, and I'm very suspicious of this thread.

You "double click:" the deb file.

He's actually not a troll.  Trolls have agendas.

---

### Post by jviscosi on 2007-05-27
> **zugu said:**
> 
- the eternal sound problem caused by applications using different sound servers / daemons / whatever


I've found that running artsd and esd at the same time, with each set to auto-suspend after two seconds of inactivity, clears up the conflicts I used to have between apps that use artsd and apps that use esd (at least in Fluxbox, XFCE, and Window Maker ... I don't run Gnome or KDE).  YMMV.

From my startup script:

artsd -s 2 &                                        # Run artsd and tell it to let go in 2 seconds
esd -nobeeps -noterminate -as 2 &   # Run esd and tell it to let go in 2 seconds

---

### Post by CarpKing on 2007-05-27
> **H.E. Pennypacker said:**
> Trolls have agendas.

Not necessarily.  But I have seen him post elsewhere, and he seems genuine enough.

---

### Post by Xzallion on 2007-05-27
Uhg not another one "Why Ubuntu sucks" thread.

Your complaining about MP3 not working out of the box.  Ubuntu cannot include MP3 support due to legal reasons, and you have to manually install it or use a installation script like Automatix or Easy Ubuntu.  Someone says Ubuntu sucks at least once a week just because of no MP3 support, and its gotten old fast.

A possible quick way to fix your sound card problem would be to disable your internal card if its part of the motherboard, so that it only detects your usb sound card.  You would do this through your computers BIOS.

As for the internet problem, downloading files is standard operating procedure for almost all Linux distrobutions.  You can manage to move them, but so far it is nowhere near as easy to move applications like it is in Windows.  I don't mind it myself, but I can see how it can be a hassle for  a lot of people.

---

### Post by RealG187 on 2007-05-27
I love Linux and am a real member!


Why cant MP3 be installed? Windoze has it...
I read something about non-free codecs, but isnt MP3 free? I never paid for it.....

I did double click AceofPenguins Deb file but it asked to extract it...

---

### Post by Adamant1988 on 2007-05-27
> **RealG187 said:**
> I love Linux and am a real member!


[B]Why cant MP3 be installed? Windoze has it...
I read something about non-free codecs, but isnt MP3 free? I never paid for it.....[/B]

I did double click AceofPenguins Deb file but it asked to extract it...

mp3 is a patent encumbered codec, so the functionality can't just be included OOTB, or it breaks the patent licensing (or lack thereof).  By the way, if you want to know how 'free' it is, just go ask Microsoft how much they just got sued for over .mp3.

---

### Post by aysiu on 2007-05-27
> **Xzallion said:**
> and you have to manually install it or use a installation script like Automatix or Easy Ubuntu. You don't need a script or a manual installation to install MP3 playback. You just have to try to play an MP3, and Ubuntu will prompt you to install the necessary codecs.

---

### Post by Roberticus on 2007-05-28
Sounds. They're sometimes really annoying. I usually listen to Internet radio, DI.fm, and after I listened to it for a moment and then I close it. After I dubble click the stream again (in Amarok) it says it isn't playable? :S

Amarok is not able to listen to a full 7h mp3 mix, only recognizes 3 hours. Audacious doesn't even open it.

Flash sometimes crash all the sound with short loops of "tk tk tk tk tk"
KSysGuard is my friend.

Why isn't there any stop button in Listen or Rhytmbox? Not good to press pause on an Internet radio stream, since it buffers up alot :)

---

### Post by 3rdalbum on 2007-05-28
> **RealG187 said:**
> Why cant MP3 be installed? Windoze has it...
I read something about non-free codecs, but isnt MP3 free? I never paid for it.....

[http://en.wikipedia.org/wiki/Free_software]("http://en.wikipedia.org/wiki/Free_software")

That is what is meant by "free" versus "non-free".

---

### Post by RealG187 on 2007-05-28
I still dont get it, I never had to pay for MP3 codec so why cant it be included?

---

### Post by aysiu on 2007-05-28
> **RealG187 said:**
> I still dont get it, I never had to pay for MP3 codec so why cant it be included?
Well, *you* never had to pay for it, but *someone* did. Dell, Microsoft, Apple (for iTunes). More importantly, for Ubuntu, it's less of a legal issue than an ideological one. Ubuntu is committed to free (think freedom, not cost or money) software. If there is a free alternative, Ubuntu will use that (Ogg, in this case, as opposed to MP3).

From [the community documentation on free formats](https://help.ubuntu.com/community/FreeFormats): > MP3 is patent-encumbered, for both encoding and decoding. These patents are being actively enforced, so usage and development of MP3-programs is not encouraged. Consider using Ogg Vorbis, which is a free and higher quality alternative to MP3 (you just need to buy audio equipment more carefully). You may also want to check out these links:
[http://www.ubuntu.com/community/ubuntustory/licensing](http://www.ubuntu.com/community/ubuntustory/licensing)
[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)

In any case, it's dead-easy to install MP3 playback, though. More details here:
[http://www.psychocats.net/ubuntu/mp3](http://www.psychocats.net/ubuntu/mp3)

If you don't agree with Ubuntu's philosophical approach to free and non-free software, consider using another Linux distribution: PCLinuxOS, Linux Mint, Blag, Mepis, Linspire, etc.

---

### Post by MellonCollie on 2007-05-28
Mark Shuttleworth recently blogged about one of the things I'm not 100% happy with: [Fonts.]("http://www.markshuttleworth.com/archives/119")

---

### Post by Bachstelze on 2007-05-28
What I dislike about Ubuntu is that it is way too experimental. It seems that someone has an idea and it's put into the distribution with little to no concern about what it means to the end-user.

Two examples :

1) The use of Dash instead of Bash as default shell. "Because it's faster", they say. Sweet. There's just one tiny problem about it : *it breaks an awful lot of shell scripts* ! Frostwire for example just won't run because Dash can't run it's startup script. There have also been many reports on configure scripts failing when trying to build something from source. Surely, not everyone runs shell scripts at all. But for the few who do, this is very confusing, they most often think the problem is in the script, not in the shell itself. 

Why not have /bin/sh a symlink to /bin/bash so the shell scripts will at least run, and have Dash as the default login shell, "because it's lighter". Ubuntu logic, dude ! Someone thought /bin/sh should be a symlink to /bin/dash, so let it be that way, and who cares if 5% of the Ubuntu users will have problems with it and 94% will see no difference ? As long as it makes the remaining 1% happy, it's fine !


2) The use of libata to handle IDE drives (the reason why your /dev/hda suddenly appears as /dev/sda in Feisty). This change is a bit different, because it *does* make sense, and could make lots of thing better, in the long run. And that's precisely the problem, it could make things better *in the long run*. Meanwhile, lots of people are forced to burn CDs at 1x because the support for burners is not quite mature yet.


People often dismiss Debian because of their long release cycles. But, when a version of Debian is released, it is because all of it has been given enough testing and is mature enough ! If people want to run testing stuff, they go with Debian testing or unstable. When they download a stable release, they know it will work fully, which is not always the case with Ubuntu (and as a side-note, the testing branch of Debian is ofter more stable than an Ubuntu release).

---

### Post by RealG187 on 2007-05-28
When I put MP3 on my Ubuntu, who pays? Is it piracy?

OGG might be better but all my songs already in MP3, and its more compatibile.. How come a Linux machine cant have but a PSP or MP3 player can? WHo owns the rights to MP3?

---

### Post by aysiu on 2007-05-28
I suggest you read these two links:
[http://mp3licensing.com/help/index.html#5](http://mp3licensing.com/help/index.html#5)
[http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues)

---

### Post by Kingsley on 2007-05-28
I've recently been using PCLinuxOS (superb and fast KDE OS) and came across this thread on their forums: [http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=18080.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=18080.0)

From what I've read, it's legal for PCLinuxOs and other distros to include proprietary codecs. It's dependent on your location to determine if they're legal or not to use.

---

### Post by aysiu on 2007-05-28
Before we continue this red herring any further, please read [post #29](http://ubuntuforums.org/showpost.php?p=2736667&postcount=29) again.

Ubuntu's primary motive in choosing software is not in consideration of legal issues but philosophical issues.

Legal issues are secondary considerations.

---

### Post by hanzomon4 on 2007-05-28
Had no idea /bin/sh was a link to dash.. How long has this been the case?

---

### Post by prizrak on 2007-05-28
> **hanzomon4 said:**
> Had no idea /bin/sh was a link to dash.. How long has this been the case?

Umm... I don't think that it is actually the case. Just tried typing in a random command and got a BASH error not DASH.... 
> People often dismiss Debian because of their long release cycles. But, when a version of Debian is released, it is because all of it has been given enough testing and is mature enough ! If people want to run testing stuff, they go with Debian testing or unstable. When they download a stable release, they know it will work fully, which is not always the case with Ubuntu (and as a side-note, the testing branch of Debian is ofter more stable than an Ubuntu release).
LTS is your friend..... If you want you can look at it this way, the normal releases are Ubuntu Beta or x.xx releasese. LTS is x.00, so Dapper could be considered a 1.00 of Ubuntu and Feisty is 1.2 (If we assume Edgy to be 1.1). With that being the case, intermittent releases are proving ground for new ideas/technology. 

Having said that, each distro has it's own intended audience. So people who want absolute stability have Debian Stable, those who want newest stuff can have Debian Testing/Unstable. Ubuntu is for those who want an easy to use, reasonably up to date desktop with a predictable and quick release cycle.

---

### Post by hanzomon4 on 2007-05-28
> **prizrak said:**
> Umm... I don't think that it is actually the case. Just tried typing in a random command and got a BASH error not DASH.... 



Not bash but sh

```
 ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2007-01-11 07:14 /bin/sh -> dash
``` 

Bash is still bash, but I use zsh....

---

### Post by RealG187 on 2007-05-29
i kinda get it, does microsoft pay thompson corp?

there are lots of pieces of software  that get away w/ it how come these people dont get sued?:
winamp
bahshee
xine
apple
real player
vlc
venturer
samsung
sony



in the faq it says its okay if there is no profit, ubuntu is non profit...

---

### Post by jrusso2 on 2007-05-29
> **HymnToLife said:**
> What I dislike about Ubuntu is that it is way too experimental. It seems that someone has an idea and it's put into the distribution with little to no concern about what it means to the end-user.
 
2) The use of libata to handle IDE drives (the reason why your /dev/hda suddenly appears as /dev/sda in Feisty). This change is a bit different, because it *does* make sense, and could make lots of thing better, in the long run. And that's precisely the problem, it could make things better *in the long run*. Meanwhile, lots of people are forced to burn CDs at 1x because the support for burners is not quite mature yet.


People often dismiss Debian because of their long release cycles. But, when a version of Debian is released, it is because all of it has been given enough testing and is mature enough ! If people want to run testing stuff, they go with Debian testing or unstable. When they download a stable release, they know it will work fully, which is not always the case with Ubuntu (and as a side-note, the testing branch of Debian is ofter more stable than an Ubuntu release).

The use of libata I believe is not Ubuntu's fault but is a kernel change for all 2.6.20 and later kernels.

---

### Post by hanzomon4 on 2007-05-29
I recently did a Vbox install of xp and it doesn't include an mp3 decoder. I believe you can install one but it's not there by default. However it was installed when I first got my Dell computer with xp pre-installed

---

### Post by Xzallion on 2007-05-29
> **aysiu said:**
> You don't need a script or a manual installation to install MP3 playback. You just have to try to play an MP3, and Ubuntu will prompt you to install the necessary codecs.

True, in newer versions of Ubuntu this works.  I keep remembering the days of Breezy Badger and trying to get .MP3 to work.  As usual, Aysiu dominates in helping, providing information, and correcting me. :p

---

### Post by tehkain on 2007-05-29
> **RealG187 said:**
> i kinda get it, does microsoft pay thompson corp?

there are lots of pieces of software  that get away w/ it how come these people dont get sued?:

in the faq it says its okay if there is no profit, ubuntu is non profit...

winamp -they pay
apple - They pay
real player - They pay
vlc - I do not think they really care
samsung -They pay
sony - They pay

---

### Post by saulgoode on 2007-05-29
> **tehkain said:**
> winamp -they pay
apple - They pay
real player - They pay
vlc - I do not think they really care
samsung -They pay
sony - They pay

The question is whether they pay the right people. Microsoft paid royalties to Thompson for years only to lose a $1,500,000,000 lawsuit from Alcatel-Lucent because they *also* had patented technology in the MP3 codec. I see no reason why Alcatel won't be going after the above companies seeking royalties from them as well.

I think software distributors, whether free or commercial, are being very prudent in deciding not to include MP3 codecs in their products. In fact, given that MPEG licensing seems to provide insufficient indemnity, I fail to see how inclusion of **any** MPEG codecs could be justified from a business standpoint.

---

### Post by Bachstelze on 2007-05-29
> **jrusso2 said:**
> The use of libata I believe is not Ubuntu's fault but is a kernel change for all 2.6.20 and later kernels.

Wrong. All my IDE disks appear as /dev/hd* in all other distros, even with 2.6.20+ kernels.

---

### Post by Swankyman on 2007-05-29
Hi,

just a quick one

> 2. Internet, you have to have internet to install anything, this is bad if you dont have it or can't get it working. W/ Windows I could download the files to a flash drive or butn to a CD and install of that, I wish I could download the files I need once, burn them and install them from a CD each time to I don't have to use up bandwidth, etc....

1) this is easy to do. goto synaptic package manager and mark the progs you wanna install

2) Select in synaptic package managers file menu is a option ´generate download script´

3) Open the generated file in a text editor -- and there are the files you need to download. each starting [http://.](http://.)......

4) go to another comp and download them, transfer to usb flash drive, put it into your ubuntu machine and double click on each starting with the top one and working your way down the list.

Just like windows but actually easier cos you already know where to down the files from

:p

Rich

---

### Post by LightB on 2007-05-29
Well I wouldn't say **this** "sucks" since it's just a design choice by the devs but:

If you could have a regular root user by default right from the install, that would be **sweet**. I know you can change this, but it's never the same as a regular root distro with all the menus hooked up accordingly. I think a choice at install time weather you want a classic root system, or a classic ubuntu sudo system - that would be great.

---

### Post by Bachstelze on 2007-05-29
sudo is certainly not "Ubuntu classic". It existed way before Ubuntu and is used on every other UNIX-like system (actually, many of them recommend using sudo instead of logging in as root). The only thing Ubuntu adds to it is giving sudo rights to the first user. And since it does that, there's really no point in having root login enabled.

---

### Post by LightB on 2007-05-29
I didn't say ubuntu invented sudo. I meant it's the way ubuntu has been always set up. And it doesn't matter who recommends what. Some users, like me, will always prefer a regular root system and to not have it will turn off those users to ubuntu which is too bad because it's a great distro.

---

### Post by prizrak on 2007-05-29
> **hanzomon4 said:**
> Not bash but sh

```
 ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2007-01-11 07:14 /bin/sh -> dash
``` 

Bash is still bash, but I use zsh....

Hmm I do get the same output, what I'm confused about though is what difference does it make if bash still seems to be the default. Or do you mean that when "your" script looks for /bin/sh and sees dash instead of bash it gets confused? This seems more a bad programming on the part of whoever wrote the script then a distro issue. (Unless I'm way off base here)
> Wrong. All my IDE disks appear as /dev/hd* in all other distros, even with 2.6.20+ kernels.
Wrong. Gentoo has had /dev/sd* for IDE disks for at least a year. Also distros use different kernel trees, the one Ubuntu uses has made that change.

---

### Post by RealG187 on 2007-05-29
Is the MP3 Codec illegal?

Wont VLC get sued??

Anyways, when I use Banshee or xine it works, who makes that, can they get sued.

Also Aysiu said if u play an MP3 file it will let you install it, who proviced the codec there, can they get sued?

---

### Post by RealG187 on 2007-07-16
How do I install [http://www.real.com/linux?](http://www.real.com/linux?)

It's a .bin file..

---

### Post by aysiu on 2007-07-16
Have you tried this? (with the Universe repositories enabled, of course): ```
sudo apt-get update && sudo apt-get install mozilla-helix-player
```

---

### Post by RealG187 on 2007-07-17
I have Helix player, I had real player before via repositories but it looked old, It doesnt look like real player 10, more like and older version, unless real player Linux is different than Windows version..

Windows:
[IMG]http://i85.photobucket.com/albums/k55/TheSaltinez/realplayergold.gif[/IMG]

Linux:
[IMG]http://base.linux-xp.com/confluence/download/attachments/320/RealPlayer.png[/IMG]

---

