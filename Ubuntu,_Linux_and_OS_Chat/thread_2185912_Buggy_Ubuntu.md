---
title: "Buggy Ubuntu"
date: 2013-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by cessanfrancisco on 2013-11-04
Is it just me or is Ubuntu 13.10 super buggy?  More so than what should be expected as acceptable?

I don't know, but I have used a bunch of distros on various machines and never have I experienced somethings as buggy as Ubuntu 13.10 on a Lenovo Z580.  Sheesh.

Maybe it's just the perfect storm consisting of the most incompatible hardware-software relationship in Linux history.  :D

---

### Post by craig10x on 2013-11-05
Haven't really noticed anything significant....of course, bug fixes are starting to slowly filter down in the updates...I have a fairly new Toshiba laptop here with intel i3 core and graphics...running quite nice and stable here...

---

### Post by monkeybrain20122 on 2013-11-05
Can you be more specific? I have experienced some bugs with Compiz's edge flipping but have I have since fixed it with some helps from the forum. Other than that and not able to add ppa via synaptic (fixed too in Ubuntu but not in lubuntu) it has been smooth, fast and stable ever since. I am happy that I have replaced 12.04 with 13.10 (still running 13.04 as my main OS. will switch when all the ppas are set up)

---

### Post by mbeltov on 2013-11-05
I've had some problems with some of the panels crashing and dissapearing but that was fixed quickly with some terminal magic. 
Otherwise things are running fine

---

### Post by PJs Ronin on 2013-11-05
Not sure what the problem can/could be.   I've found Saucy super stable... so much so that it become my production environment about half way through the cycle.

---

### Post by coffeecat on 2013-11-05
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by grahammechanical on 2013-11-05
There you have it - "in Linux history." We are using a 'one size has to fit all' operating system - Linux.  Buy a machine with an OS preinstalled and you get an OS tailored to the hardware. We are asking the next to impossible by expecting any Linux distribution to run without any issues on the great variety of hardware on the market. I do not aggree with your claim that 13.10 is buggy. The biggest issues I had running both 13.04 and 13.10 during their development cycles were caused by kernel and video driver mismatches.  Not to mention the continuing development of Gnome 3 DE. I have found the development version to be so stable as to be boring. I have been using a development version for my usual computer activity for about two years. I am running  Trusty Tahr right now.

---

### Post by buzzingrobot on 2013-11-05
I haven't noticed anything alarming or unusual for a new release.  Software Center and Settings crash at first launch, but not subsequently.

Many distributions do not enable apport or any similar tool that pops up and alerts the user to problems.  That increases the perception that a distribution lacks bugs.

Also, like Windows, new Ubuntu releases cannot be tested on every possible hardware configuration it will be installed on.  Inevitably, bugs surface only after release.

---

### Post by Bucky Ball on 2013-11-05
> **cessanfrancisco said:**
> Is it just me or is Ubuntu 13.10 super buggy? ... incompatible hardware-software relationship ...

Perhaps a combination of all three. I don't go near new releases as my main install, personally. ;)

---

### Post by monkeybrain20122 on 2013-11-05
> **mbeltov said:**
> I've had some problems with some of the panels crashing and dissapearing but that was fixed quickly with some terminal magic. 
Otherwise things are running fine

I have experienced that as well, think that was a kernel problem. Unity crashed sporadically if many pdfs were open. Upgrade kernel to 3.11.3 and all is fine (now on 3.12, 3.11.6 is problematic as it doesn't see the Fedora partition)

---

### Post by craig10x on 2013-11-05
Oh...i did have that occasional problem with the top panel that was mentioned (either the clock or the little cogwheel in the right corner you use to shut down/restart, etc) would disappear and logging out and back in would bring it back...but that seems to have been fixed in an update...that is about the only thing i have observed....

---

### Post by cessanfrancisco on 2013-11-05
Thanks for your replies.  

I guess I would agree with most, if not all, of you if I could coax Ubuntu to boot up past a purple screen of nothingness, more than 10% of the time.:mad:

Apparently, that "one size fits all" simply doesn't fit my machine.  Any suggestions?

Thanks.

---

### Post by buzzingrobot on 2013-11-05
> **cessanfrancisco said:**
> Thanks for your replies.  

I guess I would agree with most, if not all, of you if I could coax Ubuntu to boot up past a purple screen of nothingness, more than 10% of the time.:mad:

Apparently, that "one size fits all" simply doesn't fit my machine.  Any suggestions?

Thanks.

You haven't mentioned anything specific.  Without that, it's impossible to assist.

How did you install? Clean install or in-place upgrade? Are you dual-booting?

How far into the boot can you get? What do you see on screen? Error messages? Are the failed boots consistent?

When it boots successfully, are any circumstances different?

Can you boot from a live image?

What's the hardware?  What video are you using?

---

### Post by cessanfrancisco on 2013-11-05
Thanks for helping out...

To answer your questions...
1.  I installed with a live USB made with Unetbootin
2.  I installed replacing Windows 7, which replaced Windows 8
3.  I get as far as a purple screen right after the "Lenovo" logo screen
4.  No error messages
5.  Failed boots are pretty consistent.  When they do fail, they fail multiple times consecutively. 
6.  No circumstances are different when booting successfully.
7.  I can boot Ubuntu 13.10 from a live image but not Mint 15 KDE
8.  Hardware:  Lenovo Z580
9.  Graphics:  Intel Ivybridge Mobile

Thanks.

---

### Post by monkeybrain20122 on 2013-11-05
I found this [http://forums.lenovo.com/t5/Linux-Discussion/how-to-install-ubuntu-on-z-580/td-p/839209](http://forums.lenovo.com/t5/Linux-Discussion/how-to-install-ubuntu-on-z-580/td-p/839209)

---

### Post by su:bhatta on 2013-11-06
Now this becomes a support thread :) 

Try this : [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

Have been using 13.10 since Alpha cycle and found it to be pretty stable. 

Now using the release don't find any problems. So yes, it might be your hardware specific !

---

### Post by cessanfrancisco on 2013-11-06
Thanks.  I'll take a look at those links.

---

### Post by suhongdoan on 2013-11-06
I haven't really noticed anything significant even Conky is the same except for VMWare workstation 9 kernel issues of incompatibilities. I have a fairly new Dell Latitude E6530  laptop here with Intel® Core&#8482; i7-3520M CPU @ 2.90GHz × 4 with 16gb RAM and 1gb graphics NVS 5200M/PCIe/SSE2 ... running quite nice  and stable here. It was an in place upgrade from 13.04 64 bit

shd

---

### Post by cessanfrancisco on 2013-11-06
Thanks everyone for you input.

I checked out those links and tried a couple of things, still to no avail.

I did stumble upon something interesting:  In my BIOS settings I have an option (I can't recall what it's called exactly now that I don't have it in front of me) to choose between "Other OS" and "Win8 64bit."  According to the brief BIOS descriptions, "Win8 64bit" is for "pure UEFI" while "Other OS" is "pure Legacy."  Oddly, the hang up at boot-up happens less frequently using the "Win8 64bit" option, but still not totally eliminated.  

I also noticed that my computer gets hung up when trying to install drivers from gutenprint.  When that happens, I do a hard reset and the hang up at boot-up issues seems to kick in right away.

Odd.

---

### Post by mc4man on 2013-11-06
Are you using grub-efi* or grub-pc?
( I have ubuntu 13.10/14.04 installed on lenovo y580 but it's installed on  an external drive. (which may be similar to having just ubuntu installed internally like you have.

Initially ubuntu installed using uefi, (grub-efi-amd64),  with the signed kernel & I saw some issues booting to ubuntu so switched to grub-pc & generic kernel. 
When I decided to do an install of 14.04 (again to the external drive), before installing I disabled uefi in bios setting, then installed ubuntu. 

So if inclined to do a re-install, (as in new, get rid of old),  maybe first switch to legacy in bios, then install ubuntu 13.10 & see how it goes.

---

### Post by cessanfrancisco on 2013-11-06
@mc4man

Thanks for your suggestion.  Actually, that's how I originally installed Ubuntu 13.10; under "Pure Legacy."

I did, however, do a fresh reinstall using "Pure UEFI" instead.  This seems to be rendering more consistent boot-ups for me.

---

### Post by cessanfrancisco on 2013-11-06
I'm still having issues with gutenprint.  Does anyone have any experience with that being buggy in 13.10?

Thanks.

---

### Post by oldos2er on 2013-11-07
Please create a thread in the support areas of the forum for help with gutenprint.

---

### Post by futz2 on 2013-11-13
> **cessanfrancisco said:**
> Is it just me or is Ubuntu 13.10 super buggy?  More so than what should be expected as acceptable?
It's not just you. I just upgraded from my much-loved and rock solid Ubuntu 12.04 to 13.10 (to get proper driver support for a new mainboard/CPU) and have found 13.10 to be a complete mess so far. Buggiest Ubuntu I've used in many many years, and I've used them all. Hope they get this mess cleaned up by 14.04 or I'm switching to Mint or some other distro. 

I'm testing Mint 15 on another box right now and it's very nice. I think I could live with it.

---

### Post by Bucky Ball on 2013-11-13
> **futz2 said:**
> It's not just you. I just upgraded from my much-loved and rock solid Ubuntu 12.04 to 13.10 (to get proper driver support for a new mainboard/CPU) and have found 13.10 to be a complete mess so far. 

Was there any specific reason at all to upgrade? I see this a lot. People are completely happy with their rock-solid system, upgrade for the hell of it then complain. 

12.04 LTS is supported until 2017 and unless there was something you desperately needed in 13.10, don't see the point. Really simple solution: reinstall 12.04. LTS releases are intended to be stable for production machines and servers, 13.10 is an interim release that is supported for the next eight months. Comparing an interim with what 14.04 LTS will be like doesn't really wash. 

Why not keep your LTS release stable, make a spare partition for testing the interim releases, because in my opinion, anything between the LTS is a testing release, particularly now with nine months support. Still be finding nits in 13.10 by the time 14.04 comes out. I used to wait six months after release before installing a new release. No point in that now as there'd only be three months support left! There was barely much point when it was eighteen months, which is probably why I use LTS release only as my main squeeze.

I need a stable, reliable computer.

---

### Post by futz2 on 2013-11-13
> **Bucky Ball said:**
> Was there any specific reason at all to upgrade? I see this a lot. People are completely happy with their rock-solid system, upgrade for the hell of it then complain.
I didn't upgrade for the hell of it. As I said in my previous post, I upgraded because there's no driver support in 12.04 (and probably never will be) for my new GA-Z87X-OC mainboard's USB and network. 

I looked at possibly installing the newest kernel in 12.04, did some Googling and decided it was more likely to break things than to fix my driver problems. Then I installed 13.10 on a test box and it seemed ok, so I installed it on my main box. The test box never gets worked as hard as the main box, and I never noticed the problems until I used it on the main for a few days.

Oh well... I'll keep slogging along and maybe I'll gradually get the worst of the problems worked out. Updates will probably eventually fix some of the problems I'm having, as the bug reports come in and things get fixed up.

> I need a stable, reliable computer.
So do I. Had one. Bought a new mainboard/CPU - didn't have one anymore. Installed 13.10 in an attempt to get one again, but it hasn't worked out so far... :D

---

### Post by charlieprime on 2013-11-14
> **cessanfrancisco said:**
> Is it just me or is Ubuntu 13.10 super buggy?

I think it is.  

ffmpeg doesn't work right.

gutenprint won't install.

The "software center" locks up every third time I use it.

I got tired of trying to make Samba work with it.

---

### Post by FakeOutdoorsman on 2013-11-14
> **charlieprime said:**
> ffmpeg doesn't work right.

Note that the "ffmpeg" in the repos is not from FFmpeg, but is a fake, buggy version from a fork forced upon Ubuntu users.

---

### Post by charlieprime on 2013-11-15
That's just crazy FO.  I convert video lectures from .mp4 to .mp3 so I can listen to them on my little player while I drive my car or mow the yard.

This works great on my little Debian machine in the garage, but takes a long time due to it being an old, weak machine.  This does not work on my monster Ubuntu machine in the office.

I spent two hours trying to install ffmpeg from Jon Severinsson's PPA, but gave up when my cost:benefit ratio for the week began to go upside-down.

---

### Post by Y^2om&amp;#7sgP on 2013-11-15
> **Bucky Ball said:**
> Was there any specific reason at all to upgrade? 

Agree with you there.  I re-built my main machine which 'was' running 12.04

Was happy with 13.10, looked good, ran well, but a few days ago, each time I rebooted started alerts that a service had failed on start, three each time.

No major deal, everything still runs OK, but this weekend it'll be back to 12.04 as it is rock solid and then a little patience until the next LTS

Moral of this is : LTS = Debian Testing = Pretty damn stable

Interim releases = Debian unstable = Likely to be buggy

If you need or want a stable system, stick with LTS, if you're happy to play around under the hood a lot, then go with the interims.

Just my two pennyworth ;)

---

### Post by futz2 on 2013-11-15
I'm starting to collect a list of problems that I can confirm happen on more than one computer:

1. Suspend doesn't work anymore. Come on! Really? I thought we left this crap behind many years ago. Suspend the box - then wake it up and things are just... wonky - crashy - unuseable. Have to reboot to fix. So I shut the boxes down and reboot instead. Annoying.

2. When I upgraded there was no top panel clock. I Googled and found how to put one with CLI. It was fine for a couple days. Today I look up to see what time it is and... no clock. WTF? Why did it go away? (Hmm... This might be only on my main machine. Haven't confirmed it on a second box. Could be because of upgrade instead of fresh install.) **EDIT:** After another restart it's back. :D

There are more, but I don't have them memorized yet. I'll have to start taking notes when strangeness happens. Some are just annoyances, like Nautilus being ruined, and Nemo being very good but not quite ready yet. Or Palimpsest being castrated of most of its useful features (not Ubuntu's fault, but still annoying).

---

### Post by Bucky Ball on 2013-11-15
> **hattpa said:**
> 
Moral of this is : LTS = Debian Testing = Pretty damn stable

Interim releases = Debian unstable = Likely to be buggy

If you need or want a stable system, stick with LTS, if you're happy to play around under the hood a lot, then go with the interims.



+1. Absolutely, and I wish more users would keep this in mind. 

The other option if you want stability *and* fiddling fun (that doesn't sound right!) or to help out testing, and what I do myself, is to have the LTS as your main, stable squeeze and a couple of spare partitions for installing 'playthings'; i.e. interim releases and other distros/flavours. I don't/can't/won't go near the interims for my main install, especially now they are only supported for nine months. I consider them testing, even after release. 

My tuppence worth. ;)

(Before anyone jumps in with '13.10 works great for me', that's great, you must have the ideal hardware for it, but there are plenty of others who don't and for them the bugs may not be ironed before the next LTS, 14.04, is released next April.)

---

### Post by FakeOutdoorsman on 2013-11-15
> **charlieprime said:**
> I spent two hours trying to install ffmpeg from Jon Severinsson's PPA, but gave up when my cost:benefit ratio for the week began to go upside-down.

Another alternative is to download a Linux build of ffmpeg. It's standalone so it won't interfere with anything. Just download, extract, and execute (notice the ./ before ffmpeg):
```

wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
./ffmpeg -i input.mp4 -codec:a libmp3lame -qscale:a 4 -vn output.mp3
```

---

### Post by FakeOutdoorsman on 2013-11-15
> **Bucky Ball said:**
> +1. Absolutely, and I wish more users would keep this in mind. 

Almost sounds like you're blaming the user.

---

### Post by OrangeCrate on 2013-11-15
Deleted

---

