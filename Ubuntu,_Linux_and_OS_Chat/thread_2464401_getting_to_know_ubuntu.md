---
title: "getting to know ubuntu"
date: 2021-07-01
forum: Ubuntu, Linux and OS Chat
---

### Post by corvairbob on 2021-07-01
ok i am a win 10 os user and now i see they want to go to win 11 and that win 11 is going to obsolete may older good pcs. does ubuntu work on older pcs? i had chromebooks for years they google decided to stop updating them and most of my chromebooks that got there last update became so slow that my old win 7 pcs could out run the chromebooks for booting up and online tasks. so i went back to windows 7 machines, then along came win10 and that got shoved down my throat. so tell me is ubuntu any better? and if so how does it differ from win10 or the new win11 that is coming?  and if i was to get a used pc say form ebay that had a win10 os on it how would i install ubuntu on it and take win10 off it? also how if ubuntu for have the need for antivirus programs will i need to now buy one and run it as win10 has some built into there system.

plus i have app that help keep popups away and ad blocker away and such but they are in the chrome browser so will i be able to run the chrome browser still or have to change over to one ubuntu likes better?

lots of questions here but things i have to find out before i start a new learning curve. thanks for any help you guys can send my way.  bp.

---

### Post by scorp123 on 2021-07-01
> **corvairbob said:**
>  does ubuntu work on older pcs? 

Yes. Usually. Unless there's some exotic badly documented hardware in it? WiFi chipsets being the usual culprits here. You see, many hardware makers **refuse** to open up their documentation about how exactly their hardware works. So the guys writing the Linux kernel and working on distributions such as Ubuntu have to figure it out all by themselves (aka reverse-engineering). With older hardware there usually should have been sufficient time to figure everything out and make it work. But then again there's also the odd chip or so that won't work no matter what, usually because it relies on some "trade secret" closed-source bit of software. Apple being the usual offenders here, there are some Mac models you will have a very hard time to get working under Linux.

> **corvairbob said:**
>  so tell me is ubuntu any better? 

It is for me. I can't decide for you. Make a bootable USB stick and try it out in the "Live Session" mode?

> **corvairbob said:**
>  and if so how does it differ from win10 or the new win11 that is coming? 

**Linux is not Windows!** While some things might work the same way (e.g. you get icons and programs get launched when you click on them ...) other things will be very very different. If you are unwilling to re-learn a few things then you won't find happiness here.

> **corvairbob said:**
>  and if i was to get a used pc say form ebay that had a win10 os on it how would i install ubuntu on it and take win10 off it? 

[https://ubuntu.com/download]("https://ubuntu.com/download")

> **corvairbob said:**
>  also how if ubuntu for have the need for antivirus programs will i need to now buy one and run it as win10 has some built into there system. 

**Antivirus??? What for??  Linux is not Windows. Viruses are not a thing here.**  That said:  There ARE "security issues", e.g. things you should not do (e.g. blindly type in commands you find on the Internet, open attachments from unknown people, open unneeded TCP/IP ports towards the Internet ...) but viruses are not amongs them.

---

### Post by corvairbob on 2021-07-01
thanks i had one person tell me to look into the mint version on linux. is that a bit better?  also does any of the linux operating systems work with the chrome browser, or will i have to use a linux browser? thanks

---

### Post by slickymaster on 2021-07-01
Not a support thread.

Moved to **Ubuntu, Linux and OS Chat**.

---

### Post by corvairbob on 2021-07-01
ok so can you link me to that one thanks.

---

### Post by oldfred on 2021-07-01
Ubuntu comes with various flavors for different desktops/gui & default applications.

Full Ubuntu uses gnome is is really for newer systems. 
Some flavors are designed for older systems and have lighter weight gui and lightweight apps.
Some users like the lightweight flavors even on new systems.
You  can create live installer for any flavor and just try it in live mode. It will be a bit slower loading from flash drive that it would be once installed. But once in RAM live installer works well.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I just converted to Kubuntu on my desktops and find it somewhat more light weight than full Ubuntu.
My old 2006 laptop with 1.5GB of RAM used to install Ubuntu, but was slow. Tried 20.04 just to see if it would install & it would not. 
But I was able to install Kubuntu and it worked. But system that old will not be fast compared to any newer system.

---

### Post by scorp123 on 2021-07-01
> **corvairbob said:**
>   is that a bit better?  

I personally don't like it. Too much green everywhere. ;)

And I've had my issues (and a bit of a beef) with some people in their community in the distant past, back when I was a forum admin and "1-man support team" for them. You might still find tons of old threads of mine on their forums. But that shouldn't have any influence on your experience. As for Mint as a Linux distribution... I said it above: I can't decide for you. Try it out? In face I'd recommend to try as many as you can, and try them all out in their "Live Session" mode.

Other variants worthy of being mentioned:

[LIST]
[*]Zorin OS, [https://zorinos.com/]("https://zorinos.com/")
[*]Elementary OS, [https://elementary.io/]("https://elementary.io/")
[*]Ubuntu Budgie, [https://ubuntubudgie.org/]("https://ubuntubudgie.org/")
[*]Xubuntu, [https://xubuntu.org/]("https://xubuntu.org/")
[/LIST]

> **corvairbob said:**
>  also does any of the linux operating systems work with the chrome browser 

It's the other way around: The Chrome browser also happens to exist for Linux and thus functions there too. In fact many browsers exist as Linux versions, e.g. Mozilla Firefox, Chromium, Opera ... Even Microsoft Edge exists for Linux.

---

### Post by corvairbob on 2021-07-01
one person here said to install it on a stick and run it form the usb so how big of a thumb stick will i need for these? i have a 16gb stick now but if i need to get a larger stick i will just to give this a try. and then how do i get to that os? do i reboot my pc to the usb and run it form the usb? i'm thinking that is the way but have to ask to be sure and to save some time figuring out what i need to do this? i figure it will be a bit slower but worth that to give these operating systems a try. i guess i can try most of them that way. thanks

---

### Post by scorp123 on 2021-07-01
What you can also use is this: Ventoy, [https://www.ventoy.net/en/index.html]("https://www.ventoy.net/en/index.html")

Just write their software onto a USB stick. And then you just copy the various Linux ISO images onto the stick. The Ventoy software allows you to directly boot into those ISO images as if your USB stick were a CD/DVD drive. It should work with most PC's and Laptops. That way you could use the full capacity of that 16 GB stick and load it with all kinds of Linux OS images you want to try without having to re-format the stick everytime you want to try out a new variant.

Video tutorial:
[https://www.youtube.com/watch?v=CuonyS3xdwg]("https://www.youtube.com/watch?v=CuonyS3xdwg")

---

### Post by VMC on 2021-07-01
**corvairbob, **You didn't state what specs your "old" computer has that can't run Windows 11.

---

### Post by corvairbob on 2021-07-01
i guess i'm just trying to get a jump on this before all of a sudden i wind up with win11 and my pc fails to operate as it should. i had that happen with my chromebooks and got in a bind trying to find a pc to use. they say they will keep up on win10 for a few years but that can change fast.

i have a hp probook 6470b win10 20h2 ver. 64bit machine.   thanks

---

### Post by corvairbob on 2021-07-01
thanks i will go there and download that to a stick and try some of the different linx systems. one you tube is talking aobut the kubuntu version and says that is the best one but i will see i guess. thanks

---

### Post by dragonfly41 on 2021-07-01
A few points:

1. You might not be in a position to use Win 11 even if you wanted.  I find that I need to have TPM version 2.0.
[https://www.cnet.com/how-to/windows-11-microsoft-drops-pc-health-check-app-how-to-see-if-your-laptop-works-with-the-new-os/](https://www.cnet.com/how-to/windows-11-microsoft-drops-pc-health-check-app-how-to-see-if-your-laptop-works-with-the-new-os/)

2. There is already an option inside Windows 10 to experiment with Ubuntu.  It is called WSL
Windows Subsystem Linux.  The full version of Ubuntu is found in WSL2.  But really I prefer a separate installation of Ubuntu in an external SSD, not within Windows.

3. You can also try different versions of Linux in VirtualBox inside Windows 10.

---

### Post by dddman on 2021-07-01
> **dragonfly41 said:**
> You can also try different versions of Linux in VirtualBox inside Windows 10.
Virtualbox has my vote.  With vbox you can load up as many systems as you like.  It has built in backup (snapshots).  It's mostly point and click, easy to use.  Just a bit of a learning curve at first.  I consider minimum system requirements to be:  4core/8G ram and 128G of storage.  Good luck

---

