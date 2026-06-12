---
title: "Best Applications for _____?"
date: 2011-12-05
forum: The Cafe
---

### Post by jaimeaux on 2011-12-05
So... What's the best software for Ubuntu? I don't just mean "office software" or "editing software..." I mean everything! Games, Office, Browsers, Music....
 
 
Don't just post what your software is, or the name, post how to get it, and what it is/does. Give a description; we're on a forum to TALK & Discuss!
 
Thanks!

---

### Post by tartalo on 2011-12-05
Synaptic: THE graphical application for package management.

---

### Post by jaimeaux on 2011-12-05
....Well played, I think. Was that a joke?
 
If sincere, I do agree, the package management is pretty reliable for Ubuntu.

---

### Post by Elfy on 2011-12-05
Thread moved to The Community Cafe.

Mostly I use defaults - but I do install liferea, clementine and synaptic (now)

---

### Post by Frogs Hair on 2011-12-05
7zip because it is cross platform and it is capable of handling many different package types and has decent compression .

---

### Post by haqking on 2011-12-05
whatever does what you need to achieve

---

### Post by jaimeaux on 2011-12-05
> **haqking said:**
> whatever does what you need to achieve
 
 
Guys, I feel like I'm being trolled here. C'mon, Be descriptive, tell me what software you ENJOY using. I'll let you guys know why I asked the question.
 
I have been using Linux for abot 2.5 years, with only about 3 months experience w/ Ubuntu. The last time I used ubuntu, it was 9.10, i think... I'd like to know what software I can get to really WOW the people I work with, as well as myself. 
 
I've got a new laptop on the way, a System76 Lemu3, and I'd like to use it to the max. I'm going home on leave for 2 weeks from Afghanistan, and I'd like to use the high-bandwidth of American internet as wisely as possible. What software should I download to entertain, write, burn disks, torrent, ANYTHING. 
 
Thanks.

---

### Post by jaimeaux on 2011-12-05
> **forestpiskie said:**
> Thread moved to The Community Cafe. 
 
 
Also, Thanks for that. I wasn't sure what forum it belonged in. I thought "General Help" made sense, at the time.

---

### Post by d2btoo on 2011-12-05
vlc - best video player IMO under both Linux/Win.
shutter - fantastic screen-shot tool I've ever seen.

---

### Post by jjex22 on 2011-12-05
Hi there - if it doesn't offend you, I'll assume that you're asking this question as a new user (based on join date and beans), and since Haqking is right- like any OS it's all personal preference and what you want to do. Ubuntu's intro to packages is [here]("https://help.ubuntu.com/community/InstallingSoftware")

A generic tip for getting started is to use the software centre! you can search by genre etc, and the review feature is really useful to see what other people think of the software you want to install, better still it's only one click away from being installed and will be automatically updated along with your system. 

The next level is downloading .deb files from the internet - you usually do this if you want the latest version - think chrome, virtualbox, wine, etc - all in the repo's, but usually not the latest version (they are considered more stable) this download to /home/username/Downloads and you open them with gdebi or the software centre if you've got 11.10.

If you want a package, and you can only download it from the net, but there's no .deb package, then you can build it from source - these are files ending in .tar.gz or .tar.bz2 - you have to install these from a terminal, but you don't have to find an ubuntu version! there's an intro guide [here.]("https://help.ubuntu.com/community/CompilingEasyHowTo")

One tip that has largeley been replaced by the gui tools is that if you are working in a terminal you can search the repositories for packages by typing

sudo apt-cache search *blah*

and it will search for packages containing the word blah. This may not seem that useful if you are always working in the gui, but I find it can be very useful when building from source - if ./configure returns dependancies I like to run the search to see what they are before installing them, and it helps not to leave the terminal.

In terms of packages I use (I know you said not to list packages I use... but I can't think of a reason I wouldn't have my favourite packages installed!)

Wine - fairly standard addition - allows you to run lots(but not all) windows programs on linux

Office - I stick to Libre office (or it's predecessor Open office) 90% of the time, but I do also use  AbiWord and MSOffice(under wine)

Media - I tend to use VLC, but this is just because it's cross platform, so I can use it on my OSX, Windows and BSD partitions and not have to bother with different UI.

Virtualisation - VirtualBox; I use this for playing with other distro's /OSs.

Browser - chrome mostly - this is the only one I get from the goole website usually.

Coding - Code::Blocks and Geany - I tend to write in Code::Blocks as I prefer it for long sessions, then edit my errors and run from Geany.

that's 90% of wht I do, for a useful starter check out
[10 things to do after install]("http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/")
[Similar, but additional]("http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal")

Edit - Sorry that took a while, just saw you're experience with linux - so ignore the first half :)

---

### Post by Elfy on 2011-12-05
> **jaimeaux said:**
> Guys, I feel like I'm being trolled here. It is kind of the thing that gets posted rather frequently :) 


> **jaimeaux said:**
> Also, Thanks for that. I wasn't sure what forum it belonged in. I thought "General Help" made sense, at the time.
Welcome. 

To answer you in a bit more detail 

sudo apt-get install liferea synaptic xubuntu-restricted-extras 

Then I either go [here]("http://www.clementine-player.org/downloads") or [here]("http://code.google.com/p/clementine-player/downloads/list") to get clementine, depending on whether the PPA actually has the right version yet or not.

---

### Post by Megaptera on 2011-12-05
I like using Prism in 10.04.3 for access to Gmail, Googledocs, and Google Reader. Fast and easy to configure. 
In repos for 10.04.3 - not sure about 11.04 &11.10 etc

From here:[https://launchpad.net/ubuntu/+source/prism](https://launchpad.net/ubuntu/+source/prism)
"Prism, previously called WebRunner, is an application that lets users split web applications out of their browser and run them directly on their desktop."

---

### Post by Linuxratty on 2011-12-05
> **tartalo said:**
> Synaptic: THE graphical application for package management.

Yup.I like Synaptic.
 And for me, the added touches are Compiz with the extra plug in's and Gimp with the extra plug in's and Amarock.Fire Fox as my browser and I'm good to go.

---

### Post by meh_phistopheles on 2011-12-05
first of all, all of my favorite applications are found in ubuntu software center/synaptic package manager, so i won't repeat that every time. my favorites though are:

audacious - it's like winamp... that should be enough
urban terror - the best game for when you feel like shooting people in the face. you do need to add the playdeb repository though
xournal - lets you read pdf files and underline/take notes on them

that's about it. i'm a simple person

---

### Post by Thewhistlingwind on 2011-12-06
I assume you want a list that's NOT GNU/Linux/etc utilities? (Those are half of Linux's functionality. At least.)

irssi: Awesome IRC client. 

Emacs: A more elegant editor for a more civilized age.

Blender: Computer animation software. (That actually works.)

Sorry, those probably aren't going to impress your coworkers. (And they have windows ports.) But they're notably awesome.

---

### Post by jaimeaux on 2011-12-06
I probably should've posted the programs I like too... Man, I'm an ***!
 
Oh well.
 
BTW, I've never worked with Emacs... I've always been more of a VI guy, just out of principle.
 
IRSSI is excellent! I love the customization aspect of it....
 
Blender I've never worked with, but I recently saw a review on it, and it was pretty friggin' schweet lookin'.
 
As far as my favorites go:
 
Browsers -- Elinks (yup, went there), chrome, firefox
 
Editors -- I'm a VI guy, but I can't REALLY (i'll make jokes.) hate on Emacs users
 
Chat -- Irssi, Empathy, Skype (stupid, proprietary... but useful)
 
Games -- Nexuiz, Wesnoth, 
 
Office -- Tomboy notes, basKet (i haven't messed with the gtk-version, heard it's good), and Libreoffice (it's nice to know it's not owned by oracle)
 
Photos -- digiKam. HOLY CRAP that program is AWESOME. Probably one of the many cool things in KDE.
 
Music Player -- Banshee takes first, but Amarok is a VERY, VERY close second. If it had better iPod support, and didn't crash as much.
 
Video Player -- VLC, hands down, always and forever. Amazing, and Cross platform. What's not to like?
 
Terminal Emulators -- Yakuake.... bazinga! Best, ever. Looks great, smooth, fast, friendly.
 
That's my take on the software though.

---

### Post by jaimeaux on 2011-12-07
I think I just killed this thread......:confused:

---

