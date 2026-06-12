---
title: "borderline ubuntu hate.."
date: 2011-07-19
forum: Testimonials &amp; Experiences
---

### Post by dhruvraj on 2011-07-19
why does the install NOT support NVidia 8600M GT drivers, or say  broadcom wireless by default?

I've spent painful hours being a loyal ubuntu enthusiast trying most versions starting ubuntu 8.0 

It is extremely frustrating to keep coming to the same problem countless number of times, and something or the other breaks. 

When these drivers are already available, what prevents them to be on the basic install package? Is it the size of the install? Can't their be a windows profiler to check all the components of a running Windows system - and then creating an install disk for that? 

I have come to a point that I think it is worthless to stick to ubuntu, as I've spent frustratingly long hours trying to get basic things to work every time.

As of now my 11.04 install (already tried 5 iteration of full installs, with each time I've to go somehow get the stupid nvidia and broadcom wireless drivers so I can work properly) 

is broken (done by wubi) - in the sense that my startup does not load, says file not found to begin with, then the grub page comes with stupid symbols, and i select the kernel - and it says again file now found, and you need to load the kernel first.

then if you try once more - it works. however, plymouth doesnt work - the startup screen is in basic text fonts

besides, my shutdown doesnt work. hibernate however does but for shutdown, my X session gets killed but then the screen remains black and the PC is on - with no disk activity or anything.

it is so painfully stupid that I have to say, being a ubuntu enthusiast, I've come to the end of the road and think it is complete rubbish to go through this hell - for basic things that dont work

i think this stupidity is almost over for me - but im venting it out here, if anyone has any suggestions to stop me from killing ubuntu from my system and never ever even turning up to this garbage again

Dhruv

---

### Post by bodhi.zazen on 2011-07-19
*Thread moved to **null**.*

Some distros, Ubuntu and Fedora, are more cutting edge.

If you want stability try RHEL, Centos, Scientific, Debian (stable), Slackware ...

Some of your issues you need to bring up with Nvidia and other 3rd party vendors.

---

### Post by dhruvraj on 2011-07-19
also why was the thread moved to null? i think everyone should know the pain a loyal ubuntu enthusiast can also go over.. and brushing under the carpet wont solve this basic problem.

> **bodhi.zazen said:**
> *Thread moved to **null**.*

Some distros, Ubuntu and Fedora, are more cutting edge.

If you want stability try RHEL, Centos, Scientific, Debian (stable), Slackware ...

Some of your issues you need to bring up with Nvidia and other 3rd party vendors.

branding it "cutting edge" is irrelevant here. The drivers being absent is since ubuntu 8.0, and these 3rd party drivers are obviously available to install on demand, what is the problem in them being a part of basic install package is my question

---

### Post by akand074 on 2011-07-19
> **dhruvraj said:**
> why does the install NOT support NVidia 8600M GT drivers, or say  broadcom wireless by default?

When these drivers are already available, what prevents them to be on the basic install package? Is it the size of the install? Can't their be a windows profiler to check all the components of a running Windows system - and then creating an install disk for that? 

There are several reasons why they aren't there by default. 

1) They aren't open-source (FOSS software), only open source software is allowed in Ubuntu by default as to their philosophy on software (though it seems they are becoming a bit more lenient).
2) They insist on keeping the size of the Ubuntu ISO image below 700MB so they can fit on a standard CDR. Filling the image with every single/most drivers will increase it's size quite drastically
3) Legal reasons. It's illegal to distribute some software (like flash, and codecs) as part of your OS without paying licensing fees, though it's free for users to download.

Open-source versions of all the drivers are trying to be made, but it's very difficult when the companies don't co-operate and you have to actually reverse engineer (hardest part) the hardware before you can even try to code for it, where as if all the information was released, the drivers could be written a lot easier. Open-source drivers are built right into the Linux kernel, so they work by default, you don't need to even install/download anything. The proprietary drivers that you download aren't even that good, most companies don't put enough time on their Linux drivers as compared to Windows.

In my opinion, the Linux teams are doing a fantastic job given the resources they have and the challenges they have to face that is of no fault of their own.

---

### Post by dhruvraj on 2011-07-19
> **akand074 said:**
> There are several reasons why they aren't there by default. 

1) They aren't open-source (FOSS software), only open source software is allowed in Ubuntu by default as to their philosophy on software (though it seems they are becoming a bit more lenient).
2) They insist on keeping the size of the Ubuntu ISO image below 700MB so they can fit on a standard CDR. Filling the image with every single/most drivers will increase it's size quite drastically
3) Legal reasons. It's illegal to distribute some software (like flash, and codecs) as part of your OS without paying licensing fees, though it's free for users to download.

Open-source versions of all the drivers are trying to be made, but it's very difficult when the companies don't co-operate and you have to actually reverse engineer (hardest part) the hardware before you can even try to code for it, where as if all the information was released, the drivers could be written a lot easier. Open-source drivers are built right into the Linux kernel, so they work by default, you don't need to even install/download anything. The proprietary drivers that you download aren't even that good, most companies don't put enough time on their Linux drivers as compared to Windows.

In my opinion, the Linux teams are doing a fantastic job given the resources they have and the challenges they have to face that is of no fault of their own.

that's insightful, but i really think we need the windows profiler option and then creating an image based on what your system really is. It could be an on demand job, and can imagine is resource intensive - but atleast everything would work like a charm straight out of the box, and with user's choice to include proprietary drivers

this is going to go really long way in establishing a real ubuntu stronghold

---

### Post by walt.smith1960 on 2011-07-19
It sounds like the OP might want to try Mint.  More things work "out of the box", like BroadCom.  Mint has been based on ubuntu though they may have a release based on Debian, same as Ubuntu.

---

### Post by akand074 on 2011-07-19
> **dhruvraj said:**
> that's insightful, but i really think we need the windows profiler option and then creating an image based on what your system really is. It could be an on demand job, and can imagine is resource intensive - but atleast everything would work like a charm straight out of the box, and with user's choice to include proprietary drivers

this is going to go really long way in establishing a real ubuntu stronghold

I agree. At least on the overall concept. I also second the suggestion of the post above me. [Linux Mint]("http://www.linuxmint.com/") is a very popular distribution and for good reason. It's basically Ubuntu with their own custom shell and things like flash/codecs and some drivers by default. Also comes with different DE like KDE/XFCE. I've personally haven't had much trouble with drivers thankfully.

---

### Post by bodhi.zazen on 2011-07-19
> **dhruvraj said:**
> branding it "cutting edge" is irrelevant here.

No, understanding what you expect out of a distro is the first step in choosing the most appropriate distro for your needs.

If you choose to run Ubuntu you will have more problems with stability of the nature you describe in this thread then if you choose a more stable OS such as RHEL.

The trade off is that you will have nice shiny new packages ;)

---

### Post by MG&amp;TL on 2011-07-19
Surely if you stick a graphics card in a Windows machine, you still have to run the installation cd? I appreciate that linux will not support the cd, but if you can get the drivers, and they work, what's the problem? At least yours work, once they've been installed-ish. Mine broke practically everything, then refused to let me boot.

I am sorry to hear that you're leaving Ubuntu. Good luck elsewhere.

---

### Post by 3rdalbum on 2011-07-20
> **dhruvraj said:**
> why does the install NOT support NVidia 8600M GT drivers, or say  broadcom wireless by default?

Depends exactly what you mean by that.

The Nvidia 8600M should be supported for 2D by the default Nouveau driver that comes standard in Ubuntu.

"Broadcom wireless" isn't just one chip, you know. Broadcom has heaps and heaps of different wireless chips - some of which have open-source drivers and firmware and are included on the CD, and some of which don't.

Ubuntu makes it easy to install the non-open-source Nvidia 3D driver (or experimental Nouveau 3D driver) and the non-open-source drivers/firmware for many Broadcom wireless devices, using a piece of software called Additional Drivers. If you obtain an internet connection using an Ethernet cable or some other supported-out-of-the-box internet connection method, you can use Additional Drivers to download the non-open-source drivers and firmware for you. Easy.

I presume that, because you don't have your wireless running, you haven't seen anything appear in Additional Drivers. Try plugging your computer straight into your modem/router via an Ethernet cable and you should have some driver downloads offered in Additional Drivers.

---

### Post by pommie on 2011-07-20
> **dhruvraj said:**
> snip

i think this stupidity is almost over for me - but im venting it out here, if anyone has any suggestions to stop me from killing ubuntu from my system and never ever even turning up to this garbage again

Dhruv

I have three suggestions,
 1, try installing Ubuntu not Wubi,  "(*done by wubi*)"
2,try *_using_* the OS, not just trying and giving up because you have to install a couple of drivers, "*a loyal ubuntu enthusiast trying most versions*"
3, the most important one, ask for help on these forums, with an explanation of your problem, not a rant that says nothing.

As far as the drivers are concerned, Ubuntu has a lot more drivers than Windows, the first thing you have to do with a fresh install of Windows is to install the motherboard drivers, not so with Ubuntu.

If those suggestions are not sufficient for you then please close the door quietly on your way out.

Cheers David

---

### Post by mastablasta on 2011-07-20
Drivers also can't be on CD due to legal issues. For them to be on CD Nvidia would have to allow them to be there (i.e. allow Cannonical to copy them, i.e. give cannonical copyrights) which they don't.
 
even in windows you get only basic vga driver driver by default. in order to have windows looks as they should you need to use the CD that comes with the card to install the drivers. or better yet (oh and notice the similarity here with Ubuntu!) to get the latest drivers with patches and all that you need to download them from the internet and install. and since vendors now have driver packages (ie. one package for all cards) this means (like in Ubuntu) a sizeable download.
 
same goes for wi-fi chips/cards. some are supported in windows some are not. for exampel i bought a PCMCIA wi-fi card. windows needed a driver. ubuntu it works out of the box. no driver neede.
 
and as mentioned trying is not using.

---

### Post by zero244 on 2011-07-20
As far as broadcom chips.....its been my experience the chips HP uses seem to be easier to get going.

I tried Unity on a HP laptop and the broadcom drivers were running immediately on first boot up.

I eventually settled on Lucid for that laptop and they were located by Ubuntu eventually and installed, just not automatically.

Maybe just lucky but Ive never had a nvidia card I couldnt getting running eventually.
Ive even got a few ati cards running.......though it took some extra work.

I wont even consider a ATI card anymore, even though they can be a better bang for the buck.

I think the bottom line problem stems from the fact that Windows has such a huge share of the market, that hardware venders put linux on the back burner.

---

### Post by bodhi.zazen on 2011-07-20
If you want a computer that "just works" it is best to purchase it with the OS already installed and configured.

Windows users are used to this and frankly 99.9999 % would be frustrated if they had to install windows for themselves the way Linux users do, Installing windows is difficult. Try running your windows recovery CD on some random PC and see how long it takes you to install windows + all the drivers you need (and good luck to you).

The recovery CD are custom built to include all the drivers you need for your  particular machine.

If you prefer Ubuntu, purchase a machine with Ubuntu installed. There are several vendors who provide this service , zareason is but one:

[http://zareason.com/shop/home.php](http://zareason.com/shop/home.php)

Hey look you can choose from several OS in fact Ubuntu, Debian, Mint, or Fedora.

If you choose to install it yourself on incompatible hardware, you get the same result with any OS, Ubuntu or otherwise. Try installing Windows on an iphone, or OSX on your PC.

---

