---
title: "My experience with Feisty, and why i will not recommend it to newbies:"
date: 2007-06-01
forum: Testimonials &amp; Experiences
---

### Post by steve196 on 2007-06-01
After 1 day with Feisty Fawn (wubi)

1.) Internet doesn't work although it says it is connected.

I already knew that one, and knew i had to enter the DNS by hand and then install an old version of  dhcpcd and run it everytime after booting. A newbie has no chance of finding this out. Furthermore even if, he would need Windows, so he can download dhcpcd.

2.) Flash

Of course flash is not preinstalled, but when accidentially visiting a flash site before i had it, firefox would just not show the flash content and give no indication, what is missing. Someone, who doesn't know, what flash is just sees, it doesn't work

3) Internet video other than flash

Firefox uses totem for that and it doesn't work. I am myself in the process of finding out, how to make it use the already installed mplayer plugin instead. A newbie would not even get the idea to get something like an mplayer plugin.

4) Monkey audio

I hate monkey audio, but it is a widespread format and everyone will run across it sooner or later. The necessary codecs are not auto-installed, in fact you have to add a third party repository and then point the file association towards another player (and for starters, you have to know, that .ape stands for "monkey"). Impossible for newbies

I am sure I would soon be able to continue this list. 

I find it truly frustrating, when highly talented programmers go a million miles to create a great system and then stop half an inch before making it usable.

For now i cannot recommend Ubuntu for my friends, although i would like to. There are still too many phonecalls, that would follow such a recommendation.

---

### Post by Tux Aubrey on 2007-06-01
I can understand your frustration - but Feisty worked pretty much out of the box for me.

Network was fine, I installed codecs, java and flash (I used Automatix - bad Aubrey!) and then did the restricted drivers - all on the first reboot after the install.  A few (very few) updates then I grabbed a few extra packages I needed and all was done from a clean install in one short evening.

When I compare this to the several hours I spent the last (the very last!) time I installed XP SP2 and MS Office on the same machine, its a different universe - that took me all day!

Just remember that installing an OS and all the required apps would be well beyond most noobs regardless of the branding of the OS.  And Ubuntu gets better and easier with every new release.

---

### Post by super breadfish on 2007-06-01
Feisty has been my best install yet.

LiveCD was quick, it installed quickly and without a hitch, all my hardware except the TV card was detected and configured automatically. I didn't even need to install the ATI drivers. I've only had to configure two things by hand, the TV card, and taking out a few old entries from the GRUB list.
It's the first time I've ever had Beryl/Compiz working. With Dapper and Edgy it would brake my install no matter how I did it, with Feisty desktop effects work from the off, and Beryl works fine from the repos.

The only problem I've had so far is with Sound Juicer, which crashes whenever I try to change the settings, forcing me to open up a terminal and run gnome-audio-profiles-properties each time, but that's no big problem.

I think you underestimate Windows users. There are a lot of things in Linux that would cause headaches, but most newbies are fine with browser plug ins.

---

### Post by Extreme Coder on 2007-06-01
Could be speculating here, but maybe some of the problems could be caused by using Wubi? It's still very immature you know.

---

### Post by frodon on 2007-06-01
1) never saw this before, as far as i know only those with a static IP need to specify by hand the DNS address, i think you are really unlucky on this one.

2), 3) and 4) it takes 3 clicks !
Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

Take the time to read the documentation ;), ubuntu is not a out of the box distribution (it's a choice)  :
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

---

### Post by mips on 2007-06-01
> **frodon said:**
> 1) never saw this before, as far as i know only those with a static IP need to specify by hand the DNS address, i think you are really unlucky on this one.


Well if DHCP is not working you will have to configure all IP parameters manually, and that includes DNS.

---

### Post by frodon on 2007-06-01
That's why i think he's unlucky on this one because i never saw dhcp issues before.

---

### Post by shijirou on 2007-06-01
Installs aren't the same for every machine. I installed Ubuntu Feisty on my laptop without any problems. Internet was there so was wifi and about Firefox not telling you you don't have flash? I didnt experience that. When I visited a flash site Firefox just gave me that lil'old "missing plugin" thing so I just clicked on it and let it install.

It was different on my Desktop though, since I had a router and everything on my home network was on static IP addresses, I had to enter those manually plus I had a couple of issues on the install so I had to disable the acpi thing (acpi=off).

---

### Post by gusjones on 2007-06-01
I've installed Fiesty on 5 different PCs (3 boxes at home and 2 boxes at work) without any problems. For me Fiesty at work now is a great improvement as I can specify proxy validation from within Synaptic GUI itself.

---

### Post by kelvin spratt on 2007-06-01
fiesty worked excellent out of the box for me on the subject of codecs and flash, i also have Xp on computer it did not install with flash and media player only comes with ms format codecs, and monksies audio certainly is not installed by Ms . also flash does not support 64bit in windows as my wife found out the other day. by all means bash Ubuntu but please check what you are saying first some Distros do come with codecs and flash but they also have weak points of thier own.Fiesty tells you that you need codecs, firefox tells you you need to install flash and offers to download it for you just one click or is it just my setup that tells me this info ?.as its a darn sight easier to set ubuntu up than most others out there and its more stable than most as well

---

### Post by mips on 2007-06-01
> **frodon said:**
> That's why i think he's unlucky on this one because i never saw dhcp issues before.

Maybe not yourself but many people have complained about and it is an issue. The "fix" is for them to install a different version.

---

### Post by prizrak on 2007-06-01
> .1) Internet doesn't work although it says it is connected.
I already knew that one, and knew i had to enter the DNS by hand and then install an old version of dhcpcd and run it everytime after booting. A newbie has no chance of finding this out. Furthermore even if, he would need Windows, so he can download dhcpcd.

Surprised to hear that, 2 of my boxes and a friend's laptop had no issues. Hardware issue perhaps? 
> 2.) Flash

Of course flash is not preinstalled, but when accidentially visiting a flash site before i had it, firefox would just not show the flash content and give no indication, what is missing. Someone, who doesn't know, what flash is just sees, it doesn't work
That is plain weird, whenever I go to a site with any plug in missing it tells me that the content requires a missing plug in. Just like it did in Windows, IIRC Flash is actually auto-install by Firefox if you click on the green picture that tells you that you need a plug in. Could be wrong though. 
> 3) Internet video other than flash

Firefox uses totem for that and it doesn't work. I am myself in the process of finding out, how to make it use the already installed mplayer plugin instead. A newbie would not even get the idea to get something like an mplayer plugin.

No problem here, installed good, bad and ugly plug in sets from the official repositories and had no video issues since. I think it's in Add/Remove too, I used Synaptic though.
> 4) Monkey audio

I hate monkey audio, but it is a widespread format and everyone will run across it sooner or later. The necessary codecs are not auto-installed, in fact you have to add a third party repository and then point the file association towards another player (and for starters, you have to know, that .ape stands for "monkey"). Impossible for newbies
What is monkey audio? I have never heard or encountered it in 10 years on the net. It shouldn't be too difficult to equate "Ape" with "Monkey".  

I'm sorry that you had so many problems though.

---

### Post by phidia on 2007-06-01
It's just my opinion, experiance based, but feisty gets mixed reviews here. I have several distros installed on my desktop machine and feisty is definately slower to boot. Also of those distros (slack11, frugalware, zenwalk, & edgy) feisty is the only one that ff crashes on. I can't figure out why firefox crashes so I've taken to using ephinany. I had some problem setting up internet. I'm on dial up and have alot of experiance with setting up ppp. It's working but disconnecting takes up to a minute. It's not a big deal but I don't have those issues in edgy.

---

### Post by Nano Geek on 2007-06-01
What in the world is monkey audio?

---

### Post by Sepp1 on 2007-06-01
Dapper worked for me out of the box.
Edgy and Feisty had some issues, but allmost all solved now.

It really comes down to luck. Some installs go smoothly, and others are troublesome.
I would only recommend a newbie to install any OS, if it was to learn something about the procedure. 

If you just want a box that works, buy preinstalled.

Sepp1

---

### Post by forrestcupp on 2007-06-01
Maybe you're just used to buying Windows computers with all of this preinstalled.  Have you ever actually tried to do a clean install of XP or Vista?  If so, then you'll know that none of these things are automatically installed in Windows either.  To me, it's much more of a pain to get a Windows rig working properly than to get Ubuntu set up, especially Feisty.  I'm speaking from a lot of experience with both, too.  When I set up XP recently on a computer, it took me forever to get my internet connection working.  I know all about setting up IP's and how to manually mess with networks, routers, default gateways, etc.  But my problem was tracking down the correct drivers for my built in network card.  Then digging out all of my CDs with all of the other drivers I needed.  With Ubuntu, I didn't need to look for drivers.  Getting codecs was as easy as clicking the install button in the window that came up when I tried to play a file.  Installing Flash was at least as easy as it was in Windows.  For nvidia restricted drivers, I didn't have to track them down first, I just opened up the manager and let it do it for me.

It's really somewhat easier to install Feisty than it is to do a clean install of Windows.

---

### Post by Chilli Bob on 2007-06-01
I gotta disagree. I was a Linux noob till Dapper, and apart from some fiddling with printer drivers my installation was unbelievably easy.  Feisty was even easier! Definitely easier than any Windows installation, and I've been doing those since 3.1.

And lets face it, if a noob has problems, where would you rather send them?  Here to the friendly, helpful Ubuntu forums, the unintelligible, dead-link filled Microsoft site, or the flame-war battle ground forums of certain other distros who shall remain nameless?

Oh yeah, and what the heck is Monkey Audio???

Edit- [Here]("http://www.monkeysaudio.com/") it is.  I can live without it.

---

### Post by Lucifiel on 2007-06-01
Hmmm... I've a feeling that you've always bought machines with Windows pre-loaded and pre-configured.

Well, guess what? Reinstalling Windows was a lot more painful than reinstalling Ubuntu for me. However, I share your pain. Perhaps don't use Wubi this time round and try doing a "real" install of Feisty?

---

### Post by Spr0k3t on 2007-06-01
> **steve196 said:**
> 1.) Internet doesn't work although it says it is connected.I didn't have to change a thing on mine.  Worked out of the box.> 2.) FlashI'm using 64bit, I still had no problems getting it to work.  I only had to follow a simple guide I found in these forums when searching for "flash".  Of the sites I frequent, I was informed I did not have flash installed prior to.  It wasn't hard to figure it out, even for an unsupported 64bit codec wrapper.> 3) Internet video other than flashI haven't added any codecs outside of the multi/universe and it works fine> 4) Monkey audioFor being a "widespread format" I've never heard of it.  This audio format sounds like a non-standard.> I find it truly frustrating, when highly talented programmers go a million miles to create a great system and then stop half an inch before making it usable.That, is flamebait.  Since it is flamebait, I doubt Steve196 is going to respond to anything.  So I move to lock this thread or cede into the desktop readiness monster.

---

### Post by Nano Geek on 2007-06-01
Well here's a link to the [Wikipedia page]("http://en.wikipedia.org/wiki/Monkey_Audio") on "Monkey's Audio." Still, I have never head or have run across this format. I am fairly sure that it is not a "standard" format.

---

### Post by tehbeermang on 2007-06-01
The only real issue I had with my install was the M6 Ly mobile radeon, and that was to smooth out Beryl. It was fine if I turn off beryl and use metacity. That's fixed.

---

### Post by stmiller on 2007-06-01
> **steve196 said:**
> 
I find it truly frustrating, when highly talented programmers go a million miles to create a great system and then stop half an inch before making it usable.

For now i cannot recommend Ubuntu for my friends, although i would like to. There are still too many phonecalls, that would follow such a recommendation.

Linux is a community project. We need your help too. Why not give specific feedback (instead of just complaining) so we can fix what is wrong?

---

### Post by fbmx24 on 2007-06-01
Ubuntu has been the only distro to date that worked right out of the box. I recently decided to try open suse and pclinuxos but had serious issues with both of these and put ubuntu back on. :D

---

### Post by aysiu on 2007-06-01
The *install missing plugins* dialogue in Firefox works for me in Feisty. I tested that about a month ago--works just the same way it does in Windows.

---

### Post by steve196 on 2007-06-02
I'll be more precise: 

The network thing:
Here this happens anytime i try to connect an Ubuntu/Debian/Damnsmalllinux computer to a cable modem via LAN (note: All cable services here are from the same company). The problem does not show up when i connect to a DSL modem via the same LAN. A bug report about that exists for a long time. I suspect it has to do with dhclient being ipv6 compatible and thereby doing something that makes the cablemodem reject it, but that is just a wild guess. The dhcpcd, that works for me is strictly ipv4

The flash thing:
Meanwhile, of course, i have flash, but before it really showed nothing. The text above the flash thing was immediately followed by the one that should have been below it. Since nobody else seems to see this, it may be a one time oddity.

The media player thing:
Totem has all the codecs, it is just unable to download the videos. It can play those, that are already on the disk.

Monkey audio:
It is a totally useless alternative to flac, but files happen to have that format, because it is so GREAT because the files are 0.000001% smaller than with flac. On windows it is extremely easy to find and download the codec. On linux, well, finally i found everything, but it is very well hidden (maybe because linux folks hate it because of its free (like the beer only) but weird licence (any use needs approval from the author)).

---

### Post by cyberlite on 2007-06-02
Hi 

Just a though, the DSL modem has a default setting to 192.168.1.1 , your router too... This will make your DSL modem to get rejected.

for the rest install automatrix  the one stop shop for all your codes and flash needs.

[www.getautomatix.com](www.getautomatix.com) 

:D

---

### Post by 3rdalbum on 2007-06-03
Monkey Audio or whatever it's called is not a format anyone is likely to come across. As it's lossless compression, it's too big for most people to download. And even with broadband, people are more likely to download the smaller, almost-as-good 320kbps MP3s.

---

### Post by greymongrey on 2007-06-04
I would recommend any newbie to start with Ubuntu. The documentation and community is wonderful. I doubt if I would reccomend 7.04, though. For me, 6.10 was nearly perfect and it would be the one I would reccomend. Of course, some else's milage may vary. One of the deal breakers for me was when 7.04 named my two DVD drives incorrectly in fstab. I did fix that but DVDs would never work quite right and they certainly wouldn't always automount (and place an icon on my desktop) like 6.10 did.

---

### Post by Talon2 on 2007-06-06
> **steve196 said:**
> 
For now i cannot recommend Ubuntu for my friends, although i would like to. There are still too many phonecalls, that would follow such a recommendation.

I agree.

I did recommend it to one friend.  I can confirm what you predicted.

---

