---
title: "Still not sure if Ubuntu is right for me"
date: 2008-06-09
forum: Testimonials &amp; Experiences
---

### Post by Jordanwb on 2008-06-09
I've had some kind of mental block in getting used to Ubuntu (I really don't know how to explain it). Also Ubuntu seems to have a lot of software already installed, that I'll never use, and I can't install it because it's packaged with Gnome (so I guess that's not Ubuntu's fault). Plus the Heron background isn't doing it for me (Tried changing it, couldn't, background would never change). 

So I was wondering what other Linux distros and desktop systems (Gnome, XFCE etc.)are available, where I can start up my computer and within 30 seconds I'm at the desktop of my Linux OS. On my computer Ubuntu took up to 1 and a half minutes to boot up (twice as long as XP).

I'm downloading the Gentoo Live CD right now and I'm gonna give that a try.

---

### Post by s3r4phim on 2008-06-09
The only time i ever used Gentoo was when i built the OS from scratch (compiling the kernel, etc.), so i'm a bad source on that, but i know Debian is great. It's smaller than Ubuntu, but probably a bit harder to get configured.

To change a background in Ubuntu, right-click on the desktop and select the bottom option, Change Desktop Background. If that doesn't work, something is screwed up.

To get rid of any of the applications that you don't want, simply use the command:

```
sudo apt-get remove (application name)
```

and it will uninstall it for you.

good luck with Linux!

---

### Post by tyler_roach on 2008-06-09
Try kubuntu:

sudo aptitude install kubuntu-desktop

A lot of people who are turned off by Gnome's ugliness find happiness with KDE.

---

### Post by macness on 2008-06-09
One of the neatest things about ubuntu is that it has all that software preinstalled so that you don't have to search for the most commonly used reasons you use a computer.. like internet, media, firefox, etc.

I felt the same way when I installed Dapper Drake on my computer, but I have to say it's come a long way.  This [link here]("http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710/") has helped me on new setups and is relevant.

As far as other distros, some people migrating from windows feel like kubuntu is more their cup of tea because of the menus (seems more familiar is suppose).

---

### Post by aysiu on 2008-06-09
Something's wrong with your installation.

You should be able to remove whatever package you want to remove. If you get a warning about it remove *ubuntu-desktop*, don't worry. That's an empty package that just points to all the default packages. If you remove one of the default packages you, by definition, remove the pointer to the defaults.

And you should also be able to change the desktop background. If right-clicking on the desktop doesn't work, try System > Preferences > Appearance

---

### Post by GotEmRunnin on 2008-06-09
Not sure if it'll help cuz it may be harder but I tried knoppix for a while.

---

### Post by Jordanwb on 2008-06-09
> **s3r4phim said:**
> To change a background in Ubuntu, right-click on the desktop and select the bottom option, Change Desktop Background. If that doesn't work, something is screwed up.


> **aysiu said:**
> And you should also be able to change the desktop background. If right-clicking on the desktop doesn't work, try System > Preferences > Appearance

Um:

> **Jordanwb said:**
> (Tried changing it, couldn't, background would never change).

> **tyler_roach said:**
> Try kubuntu:
A lot of people who are turned off by Gnome's ugliness find happiness with KDE.

I think KDE was the one used in Knoppix. I did like Knoppix and had no trouble using it.

---

### Post by aysiu on 2008-06-09
Yeah, and I'm saying something is wrong with your installation if you can't change the background. You should be able to.

And I offered another way to do it in case the first method didn't work.

---

### Post by Jordanwb on 2008-06-09
I could change the background in 7.10 but it would never work in 8.04. I'm burning the Gentoo live CD so I'll give it a try. I'll also give Kubuntu a try.

---

### Post by ConMan318 on 2008-06-09
If you are trying to change the background in the Firefox 3 Beta, right-clicking a picture and using the 'set as background' has not worked for a lot of people.  Try right-clicking and saving an image, then right-click your desktop, navigate to that image, and you should be able to set it.

---

### Post by Jordanwb on 2008-06-09
Um I was using Ubuntu, not Fedora, so what you said isn't relevant.

---

### Post by Jordanwb on 2008-06-09
I popped in the Gentoo LiveCD, but X failed because it doesn't have drivers for my ATI video card (curse you ATI).

---

### Post by JoshuaRL on 2008-06-09
Richard Stallman said it best:

[QUOTE=RMS]Don't buy ATI.[/QUOTE]

---

### Post by Jordanwb on 2008-06-09
Well I wasn't using Linux when I got my video card, which was December of 2006. But I find it weird that Ubuntu supports my ATI card, so does Knoppix(an older version at that) but Gentoo doesn't. :confused:

---

### Post by ConMan318 on 2008-06-10
> **Jordanwb said:**
> Um I was using Ubuntu, not Fedora, so what you said isn't relevant.

Um, "Firefox" does not equal "Fedora".  Read before disregarding.

Also, just because you were unsuccessful in changing your background in a select few ways does not mean it can't be done on your computer.  That is why two other users and I offered suggestions on ways to do it.

You haven't really given much information as to your problems either, i.e. how did you try to remove unneeded software?  While I realize that solving the software/wallpaper issues were not the purpose for this thread, if you aren't going to put any effort into fixing your problems before completely switching your OS (for example, googling "ubuntu software remove" gives countless pages of different ways to uninstall software), I don't think you are going to find any suitable variation of Linux.  They will all take a bit of effort, most of them much more than Ubuntu.

Not trying to switch you over to the dark side of Windows, but it's true.

---

### Post by Xiong Chiamiov on 2008-06-10
If you're looking for a fast-and-stripped-down Linux, Arch Linux is rather popular right now.  The easy beginner guide is a bit... more difficult than Ubuntu, however.

The issues you had with extra packages are why I have the kde-core and gnome-core packages installed, instead of those massive *buntu-desktop meta packages with all their prereqs.

---

### Post by Jordanwb on 2008-06-10
> **ConMan318 said:**
> Um, "Firefox" does not equal "Fedora".  Read before disregarding.

Sorry I thought it said Fedora. :(

> **Xiong Chiamiov said:**
> If you're looking for a fast-and-stripped-down Linux, Arch Linux is rather popular right now.  The easy beginner guide is a bit... more difficult than Ubuntu, however.

The issues you had with extra packages are why I have the kde-core and gnome-core packages installed, instead of those massive *buntu-desktop meta packages with all their prereqs.

Well I like the look of Gentoo (what I saw in the screenshots), but if I get the video card to work I may go with it.

---

### Post by SunnyRabbiera on 2008-06-10
Gentoo really isnt for beginners anyway.
I suggest mandriva, I am really impressed with 2008.1

---

### Post by fiddledd on 2008-06-10
You could also try Linux Mint 5, I've got it Dual Booting with Vista. Seems fast and stable, so far on my Laptop.:)

---

### Post by mangurt on 2008-06-10
> **fiddledd said:**
> You could also try Linux Mint 5, I've got it Dual Booting with Vista. Seems fast and stable, so far on my Laptop.:)

+1 for Linux Mint.  One of the slickest things I've seen is right click uninstall is killer!

---

### Post by lazyart on 2008-06-10
> **mangurt said:**
> +1 for Linux Mint.  One of the slickest things I've seen is right click uninstall is killer!

+1 as well.

---

### Post by melrom on 2008-06-10
Also, the first time you boot into either OS after partitioning is usually slow.

Gentoo and Arch aren't good suggestions for a beginner! Ubuntu *is* basically Mint. But Mint might be more intuitive. I dual-boot Mint and Ubuntu. I didn't enjoy the same compatiblities that I did with Ubuntu [but haven't downloaded Elyssa yet], but it was still easy to use.

-MelRom

---

### Post by macness on 2008-06-10
I'm still of mind here that ConMan318 makes a good point.  In my experience there are no "super-easy" versions of Linux.  It almost seems that's part of the territory that comes with Linux.  I must say though -- for me, Ubuntu MOSTLY just works.  It's simple to use but can be as complicated as you want it to be, and it's not perfect.  Sounds like your original problem needs to be clarified more if that's the only thing keeping you from using Ubuntu/Kubuntu....

---

### Post by The Cosmic Hobo on 2008-06-10
I might have to check "Mint" out. Not something I've heard of, but then, I have been out of the Linux loop for a couple of years.
As a distro, I love Ubuntu. Ran great for me two years ago (with some minor problems due to my Toshiba laptop of the time running things like screen and volume controls as .exe under Windows), runs even better now (on another Toshiba laptop) - even in Live CD mode.

I think we all spend some time wondering "Is this right for me?" - especially if, say, we're used to Windows. Same with a big purchase or any big change. If you can, I'd say give it a try for a while before you instinctively revert back to your old OS. Ubuntu is very beginner-friendly, and so is our community here :)

---

### Post by stalkingwolf on 2008-06-10
the only distro that I know of that would fall into the 
"super easy" class is freespire.  I wont even go there.

As for the desktop background I will echo the above statement
you have a flaky install.  I just tried to change the background
running from the live disk. Right click on desktop > select
change background > select add and choose one of your pictures or
> select one of the provided ones > click open.

pretty simple.

---

### Post by mde123 on 2008-06-10
> **melrom said:**
> Also, the first time you boot into either OS after partitioning is usually slow.

Gentoo and Arch aren't good suggestions for a beginner! Ubuntu *is* basically Mint. But Mint might be more intuitive. I dual-boot Mint and Ubuntu. I didn't enjoy the same compatiblities that I did with Ubuntu [but haven't downloaded Elyssa yet], but it was still easy to use.

-MelRom
Haha? whay would you dual boot ubuntu and Mint?

---

### Post by signseeker on 2008-06-10
> **Jordanwb said:**
> I popped in the Gentoo LiveCD, but X failed because it doesn't have drivers for my ATI video card (curse you ATI).

I've used gentoo for several years and loved it. It's not for someone who doesnt like a bit of tinkering around - if you want things to just work out of the box ubuntu is the way to go. If you dont mind getting your hands dirty and are not scared of messing your system up gentoo is the way to go. 

I've got a relatively modern system and gentoo needed to be coaxed to work with it. Even something as simple as the nvidia drivers needed some work. Whereas with xubuntu - everything just worked with minimal fuss. 

I prefer xubuntu since it's lean and fast. My system can more than handle ubuntu/kubuntu etc with eyecandy/bells/whistles - but I prefer the less bloated xubuntu. 

My advice - stick with linux :) it will pay off in the end.

---

### Post by Inxsible on 2008-06-10
I am really surprised that no one in 3 pages of replies has given you the suggestion to build your system from ground up. Use the Debian business iso or the Ubuntu minimal and then install whatever software that you like.

I always do that. I too have always hated the software that Gnome and KDE give. Xfce is better to a degree, since it has less, but still bloated in my opinion.

I have a Debian business iso + Xfce install - yes I installed just xfce4 - which installs nothing BUT xfce4 and thunar. no editors nothing...you can then install whatever you want.

I also have a Debian business iso + Fluxbox and a Debian + Enlightenment 17.

Fluxbox is the fastest to get to the desktop among the 3, then E17 and finally Xfce4.

Building your own system is far far easier than going into Gentoo, especially if you are new to linux

---

### Post by aysiu on 2008-06-10
I don't see how building from the ground up will solve the problem of changing the desktop wallpaper.

---

### Post by ByteJuggler on 2008-06-10
> **Jordanwb said:**
> (Tried changing it, couldn't, background would never change)

Make a thread about it.  

I would suggest installing the "gnome-art" package, a world of desktop backgrounds and other eye candy is then at your fingertips!

---

### Post by Inxsible on 2008-06-10
> **aysiu said:**
> I don't see how building from the ground up will solve the problem of changing the desktop wallpaper.
I was not alluding that building from the ground up will solve his wallpaper problem.

I was just saying that because he was not happy with all the apps that come by default in Gnome, so building from the ground up will let him choose what he wants to install.

---

### Post by buntunub on 2008-06-10
> **Jordanwb said:**
> I've had some kind of mental block in getting used to Ubuntu (I really don't know how to explain it). Also Ubuntu seems to have a lot of software already installed, that I'll never use, and I can't install it because it's packaged with Gnome (so I guess that's not Ubuntu's fault). Plus the Heron background isn't doing it for me (Tried changing it, couldn't, background would never change). 

So I was wondering what other Linux distros and desktop systems (Gnome, XFCE etc.)are available, where I can start up my computer and within 30 seconds I'm at the desktop of my Linux OS. On my computer Ubuntu took up to 1 and a half minutes to boot up (twice as long as XP).

I'm downloading the Gentoo Live CD right now and I'm gonna give that a try.

:lolflag:

That post is a real riot! You cant figure out how to change Desktop Wallpaper, but you think you can figure out a Gentoo install?..

K. Please try not to feed the trolls guys.

---

### Post by Jordanwb on 2008-06-10
> **buntunub said:**
> That post is a real riot! You cant figure out how to change Desktop Wallpaper, but you think you can figure out a Gentoo install?..

K. Please try not to feed the trolls guys.

Why'd I even bother coming here? Plus a new version Gentoo doesn't support my video card whereas a two year old LiveCD of Knoppix does. :confused:

> **macness said:**
> In my experience there are no "super-easy" versions of Linux.

I'm not trying to find a "super-easy" version of Linux. I'm looking for one that boots quick (so far Ubuntu fails horribly), and I can choose what software I want from the get go. I don't mind using the command line. I use it all the time on my server.

---

### Post by signseeker on 2008-06-10
> **Jordanwb said:**
> Why'd I even bother coming here? Plus a new version Gentoo doesn't support my video card whereas a two year old LiveCD of Knoppix does. :confused:



I'm not trying to find a "super-easy" version of Linux. I'm looking for one that boots quick (so far Ubuntu fails horribly), and I can choose what software I want from the get go. I don't mind using the command line. I use it all the time on my server.


What kind of hardware are you running? 

If it's relatively new - then it wont really matter too much which flavour of linux you run - ie, it will be a matter of tweaking a distribution to your satisfaction.

What you need to do is run a lightweight desktop environment - xfce/fluxbox/openbox. And then recompile your kernel to make it smaller and more streamlined. Make sure ur not starting up services you dont need / and even things like DHCP can slow you down while booting up.

One of the advantages of gentoo - is that it will definitely make you learn more about linux just to install it. 

Good luck.

---

### Post by barney385 on 2008-06-10
> **Jordanwb said:**
> Why'd I even bother coming here? Plus a new version Gentoo doesn't support my video card whereas a two year old LiveCD of Knoppix does. :confused:



I'm not trying to find a "super-easy" version of Linux. I'm looking for one that boots quick (so far Ubuntu fails horribly), and I can choose what software I want from the get go. I don't mind using the command line. I use it all the time on my server.

[http://www.distrowatch.com](http://www.distrowatch.com)

---

### Post by JoshuaRL on 2008-06-10
If all you want is a super easy Linux, use either Linux Mint or Lindows.  Mint is really easy, but is a little more limited to default software choices than Ubuntu.  Lindows now called Linspire, but you might find it easy too.  At least that's what they say it is, I have never tried it and prefer never to.

But buntunb is right.  If a problem like this is giving you fits, Gentoo might be a little beyond your current skill level.  You might try Debian or Mandriva though.  Linux Mint, Lindows and Debian are somewhat related distrobutins.

---

### Post by Jordanwb on 2008-06-10
> **signseeker said:**
> What kind of hardware are you running? 

If it's relatively new - then it wont really matter too much which flavour of linux you run - ie, it will be a matter of tweaking a distribution to your satisfaction.

What you need to do is run a lightweight desktop environment - xfce/fluxbox/openbox. And then recompile your kernel to make it smaller and more streamlined. Make sure ur not starting up services you dont need / and even things like DHCP can slow you down while booting up.

One of the advantages of gentoo - is that it will definitely make you learn more about linux just to install it. 

Good luck.

HP Workstation xw4100
Intel Pentium 4 @ 2.4 Ghz
1280 MB RAM
320 GB Western Digital SATA HD 
ATI Radeon x1600 Pro AGP 8X
Hauppauge TV tuner card (don't use it a whole lot)
Creative Audigy Sound Blaster 0090
HP Scanjet 3600 (I know Linux doesn't support it at the moment)

> **JoshuaRL said:**
> If all you want is a super easy Linux, use either Linux Mint or Lindows.  Mint is really easy, but is a little more limited to default software choices than Ubuntu.  Lindows now called Linspire, but you might find it easy too.  At least that's what they say it is, I have never tried it and prefer never to.

But buntunb is right.  If a problem like this is giving you fits, Gentoo might be a little beyond your current skill level.  You might try Debian or Mandriva though.  Linux Mint, Lindows and Debian are somewhat related distrobutins.

I'll give Linux Mint a shot.

---

### Post by Jordanwb on 2008-06-10
What about installing Ubuntu Server with nothing installed then install my desktop of choice?

There's:

XFCE
Gnome
KDE
What else?

I assume if I wanted to install XFCE I would type "sudo apt-get install xfce-desktop", or for KDE "sudo apt-get install kde-desktop"? I know that I could just install Xubuntu or Kubuntu but I want to tailor it to what I want. I assume that if I install KDE or XFCE I wouldn't get the console login that I get on my Server running Ubuntu? I'd get the desktop login window.

Also regarding partitions: If I create two partitions (let's call them sda1 and sda2), will sda1 be faster than sda2? Or are they seperated logically rather than physically?

---

### Post by doorknob60 on 2008-06-10
Debian, for me it boots about twice as fast as Ubuntu, I installed from the regular KDE CD, but of course if you want a more minimal install go with netinst. And it has apt-get, a killer app IMO.

---

### Post by Jordanwb on 2008-06-10
So for NetInst it would install the basics to get me started then I could install my desired desktop program (correct term?) using sudo apt-get install xfce or kde

---

### Post by buntunub on 2008-06-10
> **Jordanwb said:**
> What about installing Ubuntu Server with nothing installed then install my desktop of choice?

There's:

XFCE
Gnome
KDE
What else?

I assume if I wanted to install XFCE I would type "sudo apt-get install xfce-desktop", or for KDE "sudo apt-get install kde-desktop"? I know that I could just install Xubuntu or Kubuntu but I want to tailor it to what I want. I assume that if I install KDE or XFCE I wouldn't get the console login that I get on my Server running Ubuntu? I'd get the desktop login window.

Also regarding partitions: If I create two partitions (let's call them sda1 and sda2), will sda1 be faster than sda2? Or are they seperated logically rather than physically?

If you managed to get Gentoo installed and it did not work, then you did it wrong. That distro was designed to run on any system, no matter how old it is - dont matter. Your final option is Slackware, and that is even more complex than Gentoo is these days. The upside is that its a faster install than Gentoo by about 2 days, but more complicated and certainly not a distro for anyone but advanced Linux users.

---

### Post by Jordanwb on 2008-06-10
So let's say I download NetInst that doorknob suggested. Then at the console (assuming I get a console), if I wanted to install KDE I'd type

sudo apt-get install kde-desktop

or for XFCE

sudo apt-get install xfce-desktop

The problem is that I don't know which to go with. I like KDE the least, but I don't prefer XFCE over Gnome or the other way around.

Someone asked about what I'd be doing:

C#/PHP development
Video Editing with my video camera (firewire), not a lot though
DVD/CD burning

I'd still have XP installed though for a bit of gaming now and then. Not a lot though. This is why I asked about partitions.

---

### Post by JoshuaRL on 2008-06-10
> **Jordanwb said:**
> What about installing Ubuntu Server with nothing installed then install my desktop of choice?

There's:

XFCE
Gnome
KDE
What else?

I assume if I wanted to install XFCE I would type "sudo apt-get install xfce-desktop", or for KDE "sudo apt-get install kde-desktop"? I know that I could just install Xubuntu or Kubuntu but I want to tailor it to what I want. I assume that if I install KDE or XFCE I wouldn't get the console login that I get on my Server running Ubuntu? I'd get the desktop login window.

Also regarding partitions: If I create two partitions (let's call them sda1 and sda2), will sda1 be faster than sda2? Or are they seperated logically rather than physically?

Actually, the command to install a desktop environment uses Aptitude and one of the desktop meta-packages.  The command looks like this:
```

sudo aptitude install ubuntu-desktop
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop

```
The reason is that since the DE's are put into a meta-package, and if you want to uninstall one someday APT won't be able to.

But yeah, that is one way to make sure you only have the applications you want.

---

### Post by Jordanwb on 2008-06-10
But I'm thinking of using NetInst. And from what I understand only apt-get is available. Confirm/Deny?

Also what about Sound and Video drivers? Do they come preinstalled or do I need to install them myself?

---

### Post by Inxsible on 2008-06-10
> **Jordanwb said:**
> What about installing Ubuntu Server with nothing installed then install my desktop of choice?There's:

XFCE
Gnome
KDE
What else?

........There are lots of options.
1)Fluxbox
2)Blackbox
3)Openbox
4)IceWM
5)JWM
6)PekWM
7)TWM
8 )Enlightenment DR17

All of the above mentioned are Window Managers and lighter than Gnome, KDE and Xfce

---

### Post by Jordanwb on 2008-06-10
I think I'm going to go with Gnome. I found that once Ubuntu loaded, Gnome was very quick.

---

### Post by JoshuaRL on 2008-06-10
> **Jordanwb said:**
> But I'm thinking of using NetInst. And from what I understand only apt-get is available. Confirm/Deny?

Also what about Sound and Video drivers? Do they come preinstalled or do I need to install them myself?

No, it should install all the drivers for you.  If you don't have access to Aptitude, then you can still use APT.  Just use that package name.  Realize however, that you won't be able to remove the whole meta-package.  You'll need to track down every package in there to get rid of it.  So just be sure you want the specific desktop environment.

---

### Post by Jordanwb on 2008-06-11
> **JoshuaRL said:**
> No, it should install all the drivers for you. If you don't have access to Aptitude, then you can still use APT. Just use that package name.

So for sound, I remember that in Ubuntu it used Alsa (I think). What else is available? Are there any pages listing the advantages of one sound system over another? Also for video drivers I had to use the restricted drivers.

> **JoshuaRL said:**
> Realize however, that you won't be able to remove the whole meta-package. You'll need to track down every package in there to get rid of it. So just be sure you want the specific desktop environment.

So do you mean that if I want Gnome I'd type "sudo apt-get install gnome-desktop"?

---

### Post by Inxsible on 2008-06-11
> **Jordanwb said:**
> [snip]So do you mean that if I want Gnome I'd type "sudo apt-get install gnome-desktop"?ubuntu-desktop = Gnome + ubuntu apps
kubuntu-desktop = KDE + kubuntu apps
xubuntu-desktop = Xfce + Xubuntu apps


but if you want Gnome, but not the ubuntu apps then you would have to install Gnome core on a minimal ubuntu install```
sudo aptitude install gnome-core
```That will give you Gnome, but not the apps that come standard in Ubuntu. You can then choose to install what you want.

---

### Post by Jordanwb on 2008-06-11
So with gnome-core, I'd get the desktop, sound and video drivers, synaptec.

---

### Post by Inxsible on 2008-06-11
> **Jordanwb said:**
> So with gnome-core, I'd get the desktop, sound and video drivers, synaptec.No, you would get only the desktop.

Sound and video you would get from the kernel, not from gnome-core. 

And I am not completely sure if Synaptic is part of gnome-core or not. It is of ubuntu-desktop. Try it out install gnome-core over a minimal ubuntu install. See if you get syanptic. 

If you don't you can always install it using ```
sudo aptitude install synaptic
```

---

### Post by Jordanwb on 2008-06-11
Ok thanks. Since I'm finished School on Friday I'll take Monday to install Debian using NetInst, then install Gnome.

Also I have two questions. One that I posted but was never answered.

1) If a create two partitions on a disk (sda1 and sda2), will sda1 be closer to the center (and thus faster), or are they seperated logically rather than physically?
2) Will two 40 GB IDE drives be faster in LVM than a single 320 GB SATA hard drive?

I need to plan my hard drive set up.

---

### Post by Inxsible on 2008-06-11
> **Jordanwb said:**
> Ok thanks. Since I'm finished School on Friday I'll take Monday to install Debian using NetInst, then install Gnome.

Also I have two questions. One that I posted but was never answered.

1) If a create two partitions on a disk (sda1 and sda2), will sda1 be closer to the center (and thus faster), or are they seperated logically rather than physically?
2) Will two 40 GB IDE drives be faster in LVM than a single 320 GB SATA hard drive?

I need to plan my hard drive set up.
Depends on how you create your partitions. But mostly it depends on what you access most of the time. If you keep listening to your music and everything is located at the center ...then great....but if its all over the place...there are going to be more seeks.

Even if you keep all you music in 1 partition near the center, I am sure you are not going to use the computer only for that...suppose you try to access some other file like your documents which are in a different partition...there is again going to be some seek time.

Bottomline, it is *nearly* impossible to predict how your partitions should be setup so that there is negligible seek time. You can take wild guesses at it, but that's what they will be...guesses.

Today's drives are fast enough, that the seek times are negligible and you can rest assured that no matter how you create partitions, you will not see a huge difference between seeks in either case.

Have a look at [this link]("http://www.psychocats.net/ubuntu/partitioning") for planning your partitions[ ]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by michaelramm on 2008-06-11
> **Inxsible said:**
> 
I have a Debian business iso + Xfce install - yes I installed just xfce4 - which installs nothing BUT xfce4 and thunar. no editors nothing...you can then install whatever you want.

I also have a Debian business iso + Fluxbox and a Debian + Enlightenment 17.

Where do you get the Debian Business ISO or Debian Core? I am looking at the listing on the Debian Download site and see 3 DVD ISOs. I am wanting to try to build a system in a VirtualBox VM. ***I think that you must be talking about the Business Card ISO, yes??***

I have recently started testing Crunchbang (#!) Linux. It is Ubuntu with OpenBox WM. It is at [http://www.crunchbang.org/projects/linux](http://www.crunchbang.org/projects/linux). It is pretty fast and uses some apps that are not as familiar to Ubuntu users as the stock Ubuntu apps. It is the work of one guy and creating his own distro. It is nice and I like supporting the efforts of one man.

Thanks for the thread. It has shown me a number of new options for my distro hopping!

Michael

---

### Post by Inxsible on 2008-06-11
> **michaelramm said:**
> Where do you get the Debian Business ISO or Debian Core? I am looking at the listing on the Debian Download site and see 3 DVD ISOs. I am wanting to try to build a system in a VirtualBox VM. ***I think that you must be talking about the Business Card ISO, yes??***

I have recently started testing Crunchbang (#!) Linux. It is Ubuntu with OpenBox WM. It is at [http://www.crunchbang.org/projects/linux](http://www.crunchbang.org/projects/linux). It is pretty fast and uses some apps that are not as familiar to Ubuntu users as the stock Ubuntu apps. It is the work of one guy and creating his own distro. It is nice and I like supporting the efforts of one man.

Thanks for the thread. It has shown me a number of new options for my distro hopping!

MichaelYes I am talking about the business card iso. comes to about 40 MB download.

Crunchbang eh? Never heard of it...will have a look.

BTW...Northport  huh? I was in UA from 2001-2003 for my MS. Roll Tide !!!

---

### Post by michaelramm on 2008-06-11
> **Inxsible said:**
> Yes I am talking about the business card iso. comes to about 40 MB download.

Cool, that is what I grabbed and am installing it into a VM right now.

> **Inxsible said:**
> 
Crunchbang eh? Never heard of it...will have a look.

Yeah, it is cool. I am running it on my temp desktop. My mobo/ps melted together at the pin and have not gotten them replaced yet. It is very quick, and I really am liking OpenBox. It is my first exposure to OB, though I have used Fluxbox a little. Not sure of the diffs exactly.

> **Inxsible said:**
> 
BTW...Northport  huh? I was in UA from 2001-2003 for my MS. Roll Tide !!!

Cool, I graduated in 1994 from UA and never left. I am the IT Mgr for the City of Northport now. Hopefully I can start moving us to non-Novell/Microsoft solutions in the near future.

BTW, I see Ubuntu Geek in your sig. Do you write that blog, or just a fan? I have been reading it for quite awhile.

Thanks for the reply,
Michael

---

### Post by FakeOutdoorsman on 2008-06-11
> **Jordanwb said:**
> ...I'm not trying to find a "super-easy" version of Linux. I'm looking for one that boots quick (so far Ubuntu fails horribly), and I can choose what software I want from the get go. I don't mind using the command line. I use it all the time on my server.
I second the suggestion of Arch Linux.  Arch is based on simplicity and will allow you to build a system they way you want it.  I'm running Arch with Openbox as my Windows Manager and I boot to desktop in under 30 seconds (mysqld and apache are also running).  From the [Arch vs Others]("http://wiki.archlinux.org/index.php/Arch_vs_Others#Arch_vs_Ubuntu") wiki page:
> Ubuntu is an immensely popular Debian-based distro commercially sponsored by Canonical Ltd., while Arch is an indepedently developed system built from scratch. Arch has a simpler foundation than Ubuntu. If you like to compile your own kernels, try out bleeding-edge CVS-only projects, or build a program from source every once in a while, Arch is better suited. If you want to get up and running quickly and not fiddle around with the guts of the system, Ubuntu is better suited. Arch is presented as a much more minimalist design from the installation onward, relying on the user to customize it to their own specific needs. In general, developers and tinkerers will probably like Arch better than Ubuntu, though many Arch users claim to have started on Ubuntu and eventually migrated to Arch.
Debian minimal and Ubuntu command-line/minimal are also good choices.  Before using Arch on my desktop machine I would use the alternate Ubuntu installation disc and use the "Install a command-line system" option and build up from there.  K.Mandla has a recent post about Gnome on Arch vs Gnome on Debian Etch: [Two fresh systems]("http://kmandla.wordpress.com/2008/05/22/two-fresh-systems/").  Crunchbang also looks interesting, but I haven't used it.

---

### Post by Inxsible on 2008-06-11
> **michaelramm said:**
>  [...snip]
BTW, I see Ubuntu Geek in your sig. Do you write that blog, or just a fan? I have been reading it for quite awhile.

Oh no ! I don't write it. I just have the link coz it has a shi*load of information which newbies can get simply by clicking on the link from my sig. saves me the time to type in the entire url or actually going to the site and copy pasting the url :)

---

### Post by Jordanwb on 2008-06-11
In the part regarding Arch Vs. Ubuntu it says "If you like to compile your own kernals...", does that mean that I would have to do that?

Currently I'm in favour of Debian's NetInst.

---

### Post by FakeOutdoorsman on 2008-06-11
No.  They are suggesting that if you are a tinkerer, or prefer to super-customize your install, then Arch would be a better choice than Ubuntu.  It's not saying that you need to do anything special with the kernel to get Arch running.  Basically with Arch, you customize some configuration files and then Arch creates a command-line system.  Then you add what packages you want from there (xorg, openbox, firefox, etc).  The best resources are [Official Arch Linux Install Guide]("http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide") and the [Beginners Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide").

---

### Post by Jordanwb on 2008-06-11
So for Arch, to get Gnome I'd type "sudo apt-get install gnome-core"

Also something I've never understood is where did "x86" come from? That messed me up when I first used Linux (Knoppix more specifically).

---

### Post by FakeOutdoorsman on 2008-06-11
Almost, but you would use pacman instead apt:
```
pacman -S gnome
```
Take a look at the [Arch Wiki]("http://wiki.archlinux.org/index.php/Main_Page").  It's one of the best around (Gentoo's is probably the best documented in my opinion).

If you prefer Debian based systems or apt package management, then Debian will be for you.

---

### Post by Jordanwb on 2008-06-11
Maybe I'll go with Debian's NetInst after all. My server runs Ubuntu, if on one I'd use apt-get and on the other I use pacman, I'd get confused.

---

### Post by kansasnoob on 2008-06-11
Why hasn't this thread been moved?

All it does is eat up time and space when some folks really need help!

---

### Post by Jordanwb on 2008-06-11
I smell a troll.

Why should it? I'm a beginner at Linux and I'm asking questions as to an optimal install.

---

### Post by twright on 2008-06-11
> **Jordanwb said:**
> Why'd I even bother coming here? Plus a new version Gentoo doesn't support my video card whereas a two year old LiveCD of Knoppix does. :confused:



I'm not trying to find a "super-easy" version of Linux. I'm looking for one that boots quick (so far Ubuntu fails horribly), and I can choose what software I want from the get go. I don't mind using the command line. I use it all the time on my server.gentoo doesn't do as many things automatically as it is aimed largely at geeks who know how to fix drivers and stuff

i always just suspend

---

### Post by Inxsible on 2008-06-11
> **Jordanwb said:**
> So for Arch, to get Gnome I'd type "sudo apt-get install gnome-core"

Also something I've never understood is where did "x86" come from? That messed me up when I first used Linux (Knoppix more specifically).Do not confuse the two OSes. 

They are separate incarnations of the Linux kernel. So one uses apt while the other uses pacman. These are not the only 2. some distros use rpm,some use yast, some use emerge (gentoo), some use netpkg (zenwalk).

Every distro created/assigned themselves to a particular package management software.

---

### Post by kansasnoob on 2008-06-11
> **Jordanwb said:**
> I smell a troll.

Why should it? I'm a beginner at Linux and I'm asking questions as to an optimal install.

Cute! I'm no troll, but I suspect you might be. 

You started this thread over two days ago saying, "I've had some kind of mental block in getting used to Ubuntu (I really don't know how to explain it). Also Ubuntu seems to have a lot of software already installed, that I'll never use, and I can't install it because it's packaged with Gnome (so I guess that's not Ubuntu's fault). Plus the Heron background isn't doing it for me (Tried changing it, couldn't, background would never change)."

Well, I love Ubuntu, it's very, very easily modified. It provides ease of use and many choices. Being the aged nOOb that I am I lean towards gui, but I don't criticize those who prefer cli. After all they've helped me out of a hole more than once!

One great example would be that I have trouble seeing the upper "tray" (header panel) on the default Ubuntu desktop so I modify the header panel (just because it's easier) and then delete the lower panel and move the upper panel down to the bottom.

The whole process takes about 5 minutes.

If I ever totally hose my Ubuntu OS I can reinstall in an hour!

And multiple booting is so simple a trained monkey could do it!

I'd think two days would be long enough to decide whether or not you want to devote a few gigs of hard drive to Ubuntu.

---

### Post by johnlvs2run on 2008-06-11
This thread is good being set up this way as one person's odyssey.

It is easier to read and reference, and gets better answers than individuals posting random questions on the forum.  My questions get a few answers here and there but mostly don't get answered at all.  There are excellent suggestions but no follow through.  I try a couple of good ideas, that sometimes don't work and the screen goes black, I post about that and no answer.  

I think it would be more helpful for people to post questions in a blog style instead, like this one, as they would be more helpful as a reference and easier to follow.  There is rarely one specific thread that has the be-all and end-all answer for an ongoing process anyway and, if so, then it is not all that easy to find.  In any case, the same searches for various issues will work whether the answers are posted in blog style continuity, or as fragmented tidbits spread all over the forum. 

Just a rant, perhaps no one agrees, but look at all the helpful responses on this thread.  And many other desperate questions get ignored.  It is nice to see some continuity of a person going from start - to finish - from finding Linux all the way through to getting it humming, without threads having to end when this little bit or that little bit has been done.

> **kansasnoob said:**
> One great example would be that I have trouble seeing the upper "tray" (header panel) on the default Ubuntu desktop so I modify the header panel (just because it's easier) and then delete the lower panel and move the upper panel down to the bottom.

Cool.  I've been wondering if that could be done.  :)

---

### Post by kansasnoob on 2008-06-11
"My questions get a few answers here and there but mostly don't get answered at all."

That is exactly why I rocked the boat and got tagged as a troll.

Folks need real help!

This is not a chat site!

---

### Post by aysiu on 2008-06-11
Even though people have offered good help in this thread, it's gone nowhere in seven pages and with no end in sight. This "blog"/"chat" style of posting isn't helpful to the forums, to the people trying to help, or to the OP (otherwise, we'd have seen a [SOLVED] subject title change a lot sooner).

I'm closing this thread.

To the OP, if you want help, post new threads with one specific problem per thread. When the problem is solved, mark the thread solved.

---

