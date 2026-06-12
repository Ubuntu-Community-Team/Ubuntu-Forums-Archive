---
title: "Grumbling again about Linux"
date: 2013-05-11
forum: Ubuntu, Linux and OS Chat
---

### Post by Oldmartian on 2013-05-11
I'm now almost 71 years old.  I've been involved with computers since their infancy.  I grew up with MSDOS.  I ebraced Windows.  Until it got unweildly.

But Linux has always intrigued me.  I've tried almost every distro from the early days until now.  But if I want to get something done; to make my computer productive I always have to go back to Windows.  

I was recently telling a friend about this ...  And that got me to thinking:  I haven't given the new Ubuntu a try recently.  I D/L the 64-bit Ubuntu 13 live and it was sweet.  So I tried to install it beside Windows 8.  Almost lost my Windows 8.  Three days lost, but I recoverd my Win8, but I'm still trying.  My problem had something to do with EUFI.  So I studied up on that but I think I need one of the LTS versions.  I'll worl on dual-boot and EUFI vs. lagacy later, maybe. 

So today I got the Ubuntu 12.4.2 LTS, fired it up and it's not as good as the latest (13.x), but that's not so bad.  I ran the Live CD and I fired up Firefox and LINUX STRIKES AGAIN!!  I get an error message that the Internet cable isn't connected.  Well Windows 8 thinks the cable *is* connected.  The computer hasn't moved.  I don't have a cat.  I took out the Live CD and rebooted and I'm now using Windows 8 using the Internet to type this.

I've never had much luck trouble-shooting Linux.  I've had friends help me in the past but they get into a multitude of command line statements that are way over my head.  I don't want to write code to have to type a letter;  I don't want to take apart my computer to run a Linux program or go on the Internet.  I just want to get on the Internet.  Maybe try e-mailing on a Live CD.

Before I die (the male side of my family generally doesn't get too far beyond 74 years of age) I'd like to functionally "use" Linux.  

So, why would a Live CD of Ubuntu 13.x connect to the Internet, Windows 8 would connect to the Internet, but a Live CD of 12.4.2 won't.  Nothing's changed on the computer.  And I'm running a screaming Gigabyte GA-Z77x-Ud3x  (not overclocked - yet) with 16 GB ram and a fistful of hard drives and using cable for my Internet service.

There is one thing I *can* say about Linux/Ubuntu, though.  For me, it's never worked so that I could do anything with it.  All my Linux time ihas been used to *try to make it work.*

Obviously an answer won't be forthcoming.  I just wanted to get this off my chest.  Thanks for listening (reading).  I will call again to read comments, though.  I do applaud the spirit of Linux, but it's not a tool: it's a hobby.  ...Unfortunately, not mine.

Old Martian
Ohio

---

### Post by Ranko Kohime on 2013-05-11
If it's very new, perhaps there wasn't built-in driver support for your network card in 12.04.2.  That's just my best guess.  I've only run into problems supporting hardware when I'm on the bleeding edge, which usually leaves me with anemia and a pocketbook full of nothing save regret.  :)

ETA: I'd also suspect that 13.04 would be better with UEFI than 12.04.2, simply because they've been working on it, but I must admit that every attempt I've made at installing with a GPT partition has failed miserably, (my last attempt being with 12.10) though the installations will boot successfully in a VM running under Windows.  I suspect foul play on Microsoft's part.

---

### Post by cbraxton on 2013-05-11
I guess it depends on what you are trying to do that is productive. I am also an 'old fart' but did not grow up with MS-DOS or embrace Windows -- I grew up with Unix, have been working with Unix and Unix-like systems since the 1970s, and have done a lot of productive work with them. I have not had much trouble getting Linux systems to work for me, generally I use Debian or CentOS for servers and Ubuntu (actually Xubuntu now) for desktop use. I am currently running Xubuntu 12.04 LTS on my desktop, a couple of laptops, and a netbook and have not had any serious issues. I also run Linux (Tomato) on my router. None of my PCs run Windows and I don't have any Apple systems. For what I do, Linux fits the bill very nicely.

Your network connection problem sounds like it is a driver issue, if your hardware is very new there just may not be driver support for your network card. In a situation like that I would just get an Intel gigabit card, they perform well and are well-supported under Linux. (I know you said you don't want to take apart your computer, but on most systems installing a network card is really no more complex than screwing in a light bulb. Alternatively if you really don't want to open up the computer case a Linux-compatible USB network card would suffice.)

There are certainly other distributions you can try as well to see if they work better on your hardware.

---

### Post by Mark Phelps on 2013-05-12
Can't give you a specific answer, but the general answer to why a newer version of Ubuntu works better with your hardware than an older version is simple -- the newer version comes with updated drivers.

Unfortunately, the opposite can also be true in Linux -- the newer version comes WITHOUT drivers because support for them was dropped with an older version.  This has happened to fold who still have an AMD 2x/3x/4x-series card and want to continue to use fglrx drivers with those with new Ubuntu versions -- as they did with older versions.  Starting last summer, AMD quit writing drivers for those cards.

As to the networking problem, if you post the hardware info (from an "lspci" command) in the hardware forum, or do a search on the networking hardware info, you may be able to get answers.

---

### Post by grahammechanical on 2013-05-12
May I show the other side of the coin?

I have been able to use Ubuntu productively ever since I first installed Ubuntu 7.04. I was able to get the data from my Windows based documents into libreoffice and the one Windows application that I need to use and that does not have a Linux version, I have been able to use under Wine. I have been using the Ubuntu development branch as a daily work machine since about September 2010. I take precautions for when things break. They do break sometimes. I am posting this from Saucy Salamander development branch. If we are swapping ages, then I am 65 years old.

How old is that version of 12.04? There have been 2 point releases of 12.04 since it was first released. Each point release brings in the latest Linux firmware code from the Linux developers. If a person downloads 12.04 to day they will not get 12.04 but 12.04.2. Point release 2 might have the firmware for your hardware. That is the purpose of point releases, to keep the LTS up to date without throwing too much change at the user. Ubuntu 12.04.2 should also deal with EFI boot systems and secure boot enabled EFI boot systems.

> [COLOR=#333333][FONT=Ubuntu]Use the last version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[/FONT][/COLOR][SecureBoot]("https://help.ubuntu.com/community/SecureBoot")[COLOR=#333333][FONT=Ubuntu] appeared in 12.10 and 12.04.2.[/FONT][/COLOR]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by coffeecat on 2013-05-12
Not a support thread. So...

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Yellow Pasque on 2013-05-12
This subforum (General Help) is for specific support questions.
Generalized grumbling should go here: [http://ubuntuforums.org/forumdisplay.php?f=434](http://ubuntuforums.org/forumdisplay.php?f=434)

EDIT: coffeecat's reading my mind :o

---

### Post by Dave_L on 2013-05-12
> **Oldmartian said:**
> There is one thing I *can* say about Linux/Ubuntu, though.  For me, it's never worked so that I could do anything with it.  All my Linux time ihas been used to *try to make it work.*

I started with Linux (MEPIS) about 9 years ago. For a while I used it alongside of Windows. Now I use Linux exclusively.

It can take a lot of patience to get things working, but I think it's worth the reward of not being dependent on big companies that want to you pay them (over and over again) for the privilege of using a computer, and being stuck with doing it "their way".

Are there any Linux user groups in your area?  That could be helpful in getting you started.

---

### Post by jefelex on 2013-05-12
I am also a linux oldbee - but with these newer issues of Ubuntu, I have had nothing but frustration.  I've been with Ubuntu since 7.04 and before that RedHat 6 and 7, (and msdos 3.3 and upwards in the microsoft camp until W98) and I know Gnome 2 just about as well as I can, but this Gnome 3 thing is completely wrong.  It is difficult to configure, and is really beyond my ability to care anymore - myself, I'm still with 11.04, since I figure it's about as good as Ubu will get. Gnome 3 may be great for newbies who don't care about how they want it and default is good enough (too engrained in msdos windows desktops and portable device screens)  My partner has 12.04 and she has asked me to remove a couple of launchers from her panel - I've spent on and off a couple of hours working on that and have got absolutely nowhere.  I did modify them so they point to secure local things on her computer (6 month old Asus laptop) but I can't tell her how they got there, or why I can't seem to remove them. <snip>
 
Now to help oldmartian - the easiest way around the issue you are having is go get a 8.04 live install cd, and use that.  then you can work upward - I repair old computers, and ran into this same situation not long ago - the newer issues of Ubu are similar to XP and especially W7 which assume that all the older hardware is never going to be used again so do not include much support for legacy devices.  8.04 was a good release, because it supports everything I have installed it on that was built in this century anyway! Wireless and all!  I hope this backward facing advise may help you - older Ubu - good, newer Ubu, - less good

This post officially breaks my boycott of the Ubu forums - depending if this post actually makes it to the forum or not
John

---

### Post by screaminj3sus on 2013-05-12
Networking doesn't work out of the box in windows on all computers either. I've seen plenty of computers where a clean windows install doesn't have working wired or wireless until you go and find the driver. In my experience linux is usually better when it comes to things like this working out of the box, windows just has the advantage of usually coming preinstalled from the OEM with all drivers, and hardware manufactorers almost always provide an installer for windows drivers, whilst in linux sometimes you may have to do a little bit in the commandline for it to work. Linux can't be expected to work out of the box on all hardware, especially when hardware manufacturers don't always support linux, its just unrealistic to even expect that... Just looking at the amount of hardware linux DOES support out of the box is impressive IMO.

Ubuntu 13.04 probably works for you because it has a significantly newer kernel than 12.04, and this new kernel must include a new driver that supports your network card, whilst 12.04's kernel does not because its older. New hardware support is *constantly* added with each new linux kernel, its entirely possible that a distro with an older kernel won't work well for some hardware.

Eventually 12.04 will get 13.04's kernel backported with the 12.04.3 release (ubuntu LTS releases get regular "hardware-enablement" updates where backported kernels are made available. 12.04 came with kernel 3.2 originally, and it now has kernel 3.5 available, and will eventually have 13.04's 3.8 kernel available), so when that happens you would probably be able to use 12.04 with things working out of the box :)

---

### Post by ppv on 2013-05-12
Maybe you could give Linux Mint a try. This comment is not based on the issues with your network card/connectivity but in a more general perspective. Mint is also based on Ubuntu though they do have a Debian fork as well.

---

### Post by aysiu on 2013-05-12
I think your best bet if you're really interested in using Linux and not just getting it set up, is to have someone else set it up for you.

Not sure where in Ohio you are, but there are Linux installfests, where people can actually help you get up and running (for free). Here's one, for example:
[http://www.meetup.com/LaunchHouse/events/117572892/](http://www.meetup.com/LaunchHouse/events/117572892/)

Otherwise, buy it preinstalled. Here are three examples:
[http://www.dell.com/us/business/p/xps-13-linux/pd](http://www.dell.com/us/business/p/xps-13-linux/pd)
[http://zareason.com/shop/Laptops/](http://zareason.com/shop/Laptops/)
[https://www.system76.com/laptops/](https://www.system76.com/laptops/)

---

### Post by mips on 2013-05-12
I'll have to revisit this thread later.

---

### Post by Dry Lips on 2013-05-12
I haven't used linux as long as some of you guys, but finding a distro that works on your computer isn't usually that difficult. The only reason why I still have a computer with Windows around, is because of certain programs that do NOT work in Linux, even under wine.

---

### Post by mips on 2013-05-12
> **Oldmartian said:**
> I'm now almost 71 years old.

Henceforth I will address thee as Sir! My parents were always smacking into me on how to respect your elders :D

Sorry but I don't have anything constructive to add to your gripe, maybe try out some distros outside of the Ubuntu fold? [COLOR=#000000][FONT=sans-serif]"Mama always said life was like a box of chocolates. You never know what you're gonna get."[/FONT][/COLOR]

---

### Post by Warprunner on 2013-05-12
> [COLOR=#000000]I'm now almost 71 years old. I've been involved with computers since their infancy. I grew up with MSDOS. I ebraced Windows. Until it got unweildly.[/COLOR]

Yeah, well I am almost there myself. I was in the Air Force before the "Internet" and grew up 1st with mainframes all the way to distributed servers. {SHUDDER} Geez, I am getting old.

Anyhow before I digress too much, I see what you're saying. However think about all the things you learned or relearned from using Ubuntu. You have kept up on it all and I would think in large part thanks should be given to this OS. Yes, we are or have been the lucky ones. The individuals that have been subjected to Windows and plug 'n Play gain nothing in the exchange. That is except ease. Allow you to think, "Oh Well it just works.". Our jobs at our age is to relay our wisdom while NEVER forgetting that younger people may have BETTER ideas. So do that. 

I think the dev's of Linux know this. Yes, they ease things but keep them open to learn. That is something I NEVER want to stop doing. Learning. If I did, give me a pumped up thin client and put on Counter Strike and lead me to my bed to play and play. Nope, thanks to the dev's I continue learning. I learn hardware, electronics, coding, ...name it. 

I haven't had any issues that took more than a couple hours to fix unless waiting for a bug fix. So don't stop. 



Warprunner is off his soapbox.

---

### Post by kevdog on 2013-05-12
It seems like an obvious driver issue, however if you post a followup post to this one, please post a link.  I'd be happy to follow any follow-up thread since I'm fairly certain there is a solution.  And lastly -- if you don't want to kind of "tinker" with your system, why in the heck do you want to use Linux?? Linux is a hobbyist and tinker's paradise.  It works for many out of the box, however there are also many that just need a little TLC to get it to work.  Your problems are quite common -- at least they appear to be on the surface -- which makes me think there is probably an easy work around -- but you are going to have to get your hands dirty at the command line!!

---

### Post by mastablasta on 2013-05-13
> **Oldmartian said:**
> So, why would a Live CD of Ubuntu 13.x connect to the Internet, Windows 8 would connect to the Internet, but a Live CD of 12.4.2 won't. Nothing's changed on the computer. And I'm running a screaming Gigabyte GA-Z77x-Ud3x (not overclocked - yet) with 16 GB ram and a fistful of hard drives and using cable for my Internet service.



this question is easy to answer. In linux drivers are part of kernel (core). They are often built in except in certian specific cases where to improve system performance closed source proprietary drivers need to be downloaded and installed. 

now then - 12.04 is from year 2012 (12) April (.04). It's kernel could be a little bit older not sure about it at the moment.
13.04 is from year 2013 (13) April (.04) - so it has relatively current stable kernel. Probably one from this year or end of last year. Now your hardware is new (indicated by Windows 8). so for best match with your hardware use 13.04. 

furthermore commands can be copied and pasted into terminal. people often give them because they are faster (just copy paste and enter instead of running multiple apps clickign all arround) and because they work on different desktops (e.g. Kubutnu has a very different desktop environemnt from Ubuntu) and also in some cases different distributions (e.g. some command from Debian will work on UBuntu as well as on Linux Mint).

i wish i could help you with UEFi issue (i haven't run into it yet). But UEFI secureboot is sort of brain child from Microsoft. they say it is for security but in reality it only makes harder for other operating systems (Linux, MacOS) to be installed on PC. windows 8 compatible motherboards should have disabel secureboot switch. many come with enabled and widnows 8 preinstalled.

---

### Post by Oldmartian on 2013-05-13
Thx Ranko.
I got the 12.04.2 at the Ubuntu site, so yeah, my Mobo could be newer than 12.04.2.
I like Ubuntu 13.1 better, anyway.  Now I'm hung up on the wording of the partition screens...
What forum would you recommend for this (13.1)?

---

### Post by Sam Mills on 2013-05-13
> **Oldmartian said:**
> Thx Ranko.
I got the 12.04.2 at the Ubuntu site, so yeah, my Mobo could be newer than 12.04.2.
I like Ubuntu 13.1 better, anyway.  Now I'm hung up on the wording of the partition screens...
What forum would you recommend for this (13.1)?
Just post in the **General** section, and someone will be happy to help you.

---

### Post by Oldmartian on 2013-05-13
To Kevdog,
You asked why I want to run Ubuntu.  Well exactlu 5 years ago I was playing with Ubuntu (Hardy Heron) but I and into trouble trying to get a dual monitor runing.  I ended up messing with the xconf and messed up the install and went back to Windows.  Running on one screen gave me a good taste of Ubuntu, though.  B4 I die, I gotta try again.  

I posted something back then.  The discussion went like this:

[INDENT]Re: Hardy Dual Monitor (dual head) with nvidia GeForce 9800 card 

Back-up your xorg.conf file in case it got messed up and you have to revert to the currently working one:

Code:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
Next, run nvidia-settings with sudo:

Code:
sudo nvidia-settings
Click "X Server Display Configuration" on the left pane. Here you can set-up dual screens (it will take some experimenting to get what you want and unfortunately, I don't think it's not the most intuitive application).

Once you are satisfied with the results, click "Save to X Configuration File", quit nvidia-settings, and reboot your PC.[/INDENT]

---

### Post by Oldmartian on 2013-05-13
Thanks to all who have responded.  The version where the network didn't work was 12.04.2.  I decided to go with the 13.1 (or later) and go to an Installfest which someone suggested.  I started to do it myself again, but (remember I almost lost my Windows 8 install) got hung up on the questions about partitions and drive names and lettering.  I'm just too slow to understand this by myself.  Several years ago I remember using Grub and GPT but I'd rather install Linux in a roomful of geeks who know far more than I do about Linux.  I used to be a serious DOS and Windows geek in my younger years.

The installfest will be in 3 weeks so I won't be posting anything until after that.  I might still log-in here to read the posts and glean what I can.

What I didn't mention before is that I want to completely migrate to Ubuntu.  Completely means dragging my wife along.  So that means *everything* that she currently is using has to be available to her unless it's a trivial application.  I already use Thunderbird and Libre Office, so I'm on top of that.  I'll probably use Firefox for Internet (I should start now, I suppose) and use Wine to run other favorites like the MS Spider and Freecell.  Substitutes will not be acceptable to her.  She just doesn't understand my changing things on the computer, so substitutes have to ge good.  Real good.  She cooks, feeds and clothes me.  I don't want her to change what I'm used to.

I appreciate all your kind comments and thoughtful suggestions.

Old Martian (Fred)
Ohio, US

---

### Post by leclerc65 on 2013-05-13
I have the feeling you think Linux is untrustable (please excuse me if I am wrong), but the LHC (Large Hadron Collider) won't be able to analyze zillions of collisions without the help of Linux.

---

### Post by kurt18947 on 2013-05-14
Now is a difficult time for Linux users in terms of new machines.  There is a switch underway from "MSDOS" type BIOS and hard drive formatting to UEFI, GPT and Secure Boot.  The old standards had their limitations and foibles but the limitations and foibles were well understood.  The newer standards less so and manufacturers seem to not be on the 'same page' yet.  Kinda late for oldmartian but if I were needing a new machine to run Linux today, I'd be looking for a notebook running Windows 7.  They're still sold but not at 'big box' stores.

---

### Post by Dave_L on 2013-05-14
> **Oldmartian said:**
> ... So that means *everything* that she currently is using has to be available to her unless it's a trivial application.  ... Substitutes will not be acceptable to her. 

Depending on what she's currently using, that may not be realistic. WINE works well for a few applications, but (in my experience) not so well for most applications.

But if you need help finding close alternatives, ask. :)

---

### Post by |{urse on 2013-05-14
Make sure your hardware (especially video and wireless) is supported BEFORE and you will have total usability afterwards ;) Most OEM systems were designed with Windows in mind and not Linux. Can't fault the penguin for that.

---

### Post by NM5TF on 2013-05-14
> **Dave_L said:**
> Depending on what she's currently using, that may not be realistic. WINE works well for a few applications, but (in my experience) not so well for most applications.

But if you need help finding close alternatives, ask. :)

I agree with Dave about WINE....:mad:

my job requires me to take on-line H & S training to retain my HAzWOPER certification, but the
training site ONLY supports IE 8/9....:confused:

I have installed WIN XP in a VM & that satisfies that requirement nicely....that would also keep
the Wife, and YOU by default, HAPPY!!!:popcorn::popcorn:

all WIN APP's run just as if they are in a WIN box...

check out Virtual Box...:)

Tommy

---

### Post by SeijiSensei on 2013-05-14
Running a Win7 VM in VirtualBox is a possibility.  You might even try using "seamless" mode where both operating systems share the desktop.  When I run in this mode, I configure Win7 to put its taskbar at the top of the screen leaving my Kubuntu panel at the bottom.  Then to run a Windows app, I move my mouse to the top of the screen and pick it from Windows taskbar.  This might be too much clutter for your wife, though.  What are the "absolutely must have" applications on her list?

---

### Post by mamamia88 on 2013-05-14
wrong thread

---

