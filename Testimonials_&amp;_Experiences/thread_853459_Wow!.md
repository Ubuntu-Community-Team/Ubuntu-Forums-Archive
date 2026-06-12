---
title: "Wow!"
date: 2008-07-08
forum: Testimonials &amp; Experiences
---

### Post by surfinstyle on 2008-07-08
First Post...

Just spent my first week on the other side with Ubuntu, as far as I'm concerned there is no going back to Windows. 

Ubuntu is so intuitive to me, I have used XP every day at work for as long as I can remember. Yet I started ubuntu and it just screamed intuitive to me. I always though linux as a bit quirky - single click, strange controls, odd right click etc. but ubuntu just did what I expected. I have to admit my first experience was with Kubuntu and it almost put me off Linux - no offense but it looks lovely but some of the behaviors I'm just not used to.

I've totally loved tweaking the interface and the programs to work just how I'd like.

Some observations:

I now seem to have the mindset where I will only consider buying hardware that runs on ubuntu.

My work Laptop - which is a little beauty and spec wise should fly now feels sluggish and old. My home PC has been given a new lease of life.

My girlfriend who has no interest in a PC's OS can use ubuntu - I tried to tell her how it was different in many ways to windows (free, funky, quick etc) he wasn't interested, but the biggest testament is she can use it and i can get away with installing it on our laptop! I'm half considering installing ubuntu on my folks pc - for which I am basically IT support (restart and hope)

Sudo - what the heck is this all about? What does sudo even mean? I'm no where near competent enough to run these commands. To the devlopers: the more you can move away from command line to these "deb" type packages the better. I am someone that struggles (can't) to change directory using the command line. 

I'm convinced by this system but have spent a (fun) week of tweaking and adding removing programs - is there anyway for me to take what I've done and both a) back it up in case I need to reinstall the OS b)Move it to a new machine or laptop?

If I want to find some help I go to Google and type "xxxxxx Ubuntu" where xxxxxx = problem, hardware, software, error message etc - is there a better way?

Cheers and all the best!

---

### Post by tamoneya on 2008-07-08
> If I want to find some help I go to Google and type "xxxxxx Ubuntu" where xxxxxx = problem, hardware, software, error message etc - is there a better way?

+1

This is the thing that makes it or breaks it for most new linux users.  The search function is key and makes life so much easier and is so far the best way I have found.  If you get really stuck just post on these forums and you get very helpful responses.

Welcome to Ubuntu.

Addition: I predict that with in the next month you will be loving command line.  It is scary at first but beats the GUI any day.  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by pofigster on 2008-07-08
Glad you're enjoying Ubuntu!

If you need help, the first place I would suggest trying is here - the Ubuntu Forums.  There hasn't been a problem to date that I haven't been able to get solved by either posting here or digging through the archives.  Search first, read what problems other people have had and try and use the responses there to learn.

"sudo" is to use your computer as the "root" user without actually be logged in as "root"  Typically, you shouldn't need to mess with the command line.  If a solution requires it, the folks in the forums here are great at posting every line of code you need so that all you need to do is copy and paste.

To backup your system, I would try remastersys (google it...) which has worked great for me.  It'll make a .iso file (CD/DVD image) of your system as a backup that you can burn to a DVD.  You can also turn it into a "distribution" which will allow you to basically clone what you have on another computer.  It's great free software.

Hope you continue to enjoy your experience!

---

### Post by surfinstyle on 2008-07-08
Blimey you guys are quick to respond!

Thanks very much for the tips! 

I've tried following a few of the step by step guides and had a few problems, I'll dig a bit deeper on the forum. 

A lot of you old skool linux people must really be witnessing a bit of a sea change at the moment - if people like me and my gf are moving across then linux is really starting to broaden its appeal. I would say that my biggest concern would be for the pure number of distro's out there - it took me perhaps 2 weeks of livecds to get to one that I had that "lightbulb moment". Now I'm convinced I may revisit those distos in the future, but if I didn't have the perseverance I wouldn't of made it.

Cheers

---

### Post by kazuya on 2008-07-08
welcome to the linux or opensource world. lol The sheer number of distros are there to give you choice. I kno wthere are many, but they all serve similar purpose, but maybe in different ways for some. 

You may and would hit some obstacles, but it is way worth the time to use linux.

---

### Post by wolfen69 on 2008-07-08
welcome to the wonderful world of linux. as far as sudo goes, i find it much easier to:
```
sudo apt-get install amarok
```
and it is installed in seconds. as opposed to windows, where you have to get to the website, find the download link, wait for the download, click through endless screens, hope that it doesnt contain extra garbage and spyware, agree to the eula, etc. now tell me, which one is easier? and if you are that scared of the terminal, just use synaptic package manager or add/remove programs. click and install. very easy. just be patient and things will start to makes sense to you. good luck.

---

### Post by armandh on 2008-07-08
to get all the DVD and codex to run 
[http://www.medibuntu.org/](http://www.medibuntu.org/)
go to the how-to and several copy/paste in to teriminal

---

### Post by 3rdalbum on 2008-07-09
Debian packages are good, but there's two major reasons why source code must still be distributed in compilable form:

1. Debian packages are not native to other distributions (they could switch though, or another packaging format could be created to work on all distros)

2. Major MAJOR reason: A compiled Debian package will not work on a computer that has a different architecture of processor. An x86 package won't run on an PowerPC computer, and vice-versa. This isn't a flaw in Debian packaging, it's just a reality of processors that they do not run compiled code from another processor architecture.

I do agree that there should be more Debian packages, because there are benefits over source code (no compiling time, easy installation and removal), but they shouldn't replace compilable source code.

Packaging for Debian-based systems like Ubuntu is pretty easy; if you feel passionate enough about there being more Debs, you could always learn how to package and offer your services to open-source projects. Just look for a HOWTO, and about 10 minutes later you'll have your very first Debian package.

---

### Post by Sukarn on 2008-07-09
> **3rdalbum said:**
> Debian packages are good, but there's two major reasons why source code must still be distributed in compilable form:

1. Debian packages are not native to other distributions (they could switch though, or another packaging format could be created to work on all distros)

2. Major MAJOR reason: A compiled Debian package will not work on a computer that has a different architecture of processor. An x86 package won't run on an PowerPC computer, and vice-versa. This isn't a flaw in Debian packaging, it's just a reality of processors that they do not run compiled code from another processor architecture.

I do agree that there should be more Debian packages, because there are benefits over source code (no compiling time, easy installation and removal), but they shouldn't replace compilable source code.

Packaging for Debian-based systems like Ubuntu is pretty easy; if you feel passionate enough about there being more Debs, you could always learn how to package and offer your services to open-source projects. Just look for a HOWTO, and about 10 minutes later you'll have your very first Debian package.

I see you decided to go quite offtopic here. The OP wasn't asking about compiling and installing stuff.

In response to your post - it wouldn't be "opensource" if the source code wasn't available, now would it?

The biggest problem people have had with using opensource softwares is that they have had to compile and install the softwares themselves, which has turned a lot of people away from using said softwares. This has changed a lot in the past few years with wide availability of packages.

The source code of open source softwares won't go away since that would make the term "open source" an obsolete term, and the closed source softwares are never released in source form anyway. They are released as binary "blobs".

I really don't see where your argument came from and where it is headed.

---

### Post by stalkingwolf on 2008-07-10
remastersys is an easy , nice tool. Im still playing with it.

---

### Post by steveneddy on 2008-07-22
Indeed....

---

