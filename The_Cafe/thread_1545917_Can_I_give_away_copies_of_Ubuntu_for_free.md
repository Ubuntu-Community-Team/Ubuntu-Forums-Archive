---
title: "Can I give away copies of Ubuntu for free?"
date: 2010-08-04
forum: The Cafe
---

### Post by Gone Digital on 2010-08-04
Hi, I have been using Ubuntu for a month now, I used Windows for 19 years, and last month I changed to Ubuntu and have not looked back, I would like to know if I can give away copies of Ubuntu for free to people?

Thank You. ):P

---

### Post by Zorgoth on 2010-08-04
You most certainly can!  The GPL allows you to use, distribute, and modify Ubuntu in any way; as long as you don't steal code from Ubuntu and use it for a commercial product, you're fine.  That is why open source software is so awesome!

---

### Post by Gone Digital on 2010-08-04
> **Zorgoth said:**
> You most certainly can!  The GPL allows you to use, distribute, and modify Ubuntu in any way; as long as you don't steal code from Ubuntu and use it for a commercial product, you're fine.  That is why open source software is so awesome!

I fix old-ish laptops which I sell on, is it ok to Install Ubuntu on these and give away a free cd with each laptop?

Thank You.

---

### Post by Bachstelze on 2010-08-04
> **Gone Digital said:**
> I fix old-ish laptops which I sell on, is it ok to Install Ubuntu on these and give away a free cd with each laptop?

Thank You.

Yes.

---

### Post by endotherm on 2010-08-04
here are a list of the fundemental freedoms you shoudl inisist upon when selecting open source software (one of them is the right to redistribute):
[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

---

### Post by Gone Digital on 2010-08-04
> **Bachstelze said:**
> Yes.

Thank You. ):P

---

### Post by tgalati4 on 2010-08-04
You are doing a useful service of providing a second life to these laptops.  They have suffered through many years of Windows abuse, it's time they enjoy themselves in retirement with Ubuntu.

---

### Post by Gone Digital on 2010-08-04
Two of the laptops have a DVD drive, how could I go about installing a DVD Player program, would I need to pay a licence to install a DVD Player?

Thank You ):P

---

### Post by JBAlaska on 2010-08-04
```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Edit: stupid me LOL..

---

### Post by Zorgoth on 2010-08-04
This is probably not a big deal (I use libdvdcss2 myself since it is just stupid to have to pay extra money to have to play DVDs I already own when I paid for the DVD player in my laptop already) but if I am not mistaken the method given to you is technically illegal in the United States under the DMCA, because it is illegal to break the encryption on the DVDs (despite the fact that this encryption is extremely weak and easy to get past).  To do things legally I think you have to pay for a DVD codec from Fluendo, unless things have changed since last I checked.  Someone please say they have?

---

### Post by daniell59 on 2010-08-04
> **JBAlaska said:**
> ```
sudo ubuntu-restricted-extras
```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Please forgive my ignorance, but what does restricted-extras mean?

Thanks

---

### Post by howefield on 2010-08-04
> **daniell59 said:**
> Please forgive my ignorance, but what does restricted-extras mean?

It is an easy (but lazy) way of adding certain codecs, flash, java and some other packages to your system. Lazy from the point of view that the advice is often given, but seldom explained exactly what is actually in the package(s).

He probably means

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by daniell59 on 2010-08-04
> **howefield said:**
> It is an easy (but lazy) way of adding certain codecs, flash, java and some other packages to your system. Lazy from the point of view that the advice is often given, but seldom explained exactly what is actually in the package(s).

He probably means

```
sudo apt-get install ubuntu-restricted-extras
```

In particular what does restricted mean?

---

### Post by howefield on 2010-08-04
> **daniell59 said:**
> In particular what does restricted mean?

Restricted as in not open.

Proprietary / Closed source.

---

### Post by daniell59 on 2010-08-04
> **howefield said:**
> Restricted as in not open.

Proprietary / Closed source.

I thought that Ubuntu was open source.

---

### Post by JBAlaska on 2010-08-04
> **howefield said:**
> It is an easy (but lazy) way of adding certain codecs, flash, java and some other packages to your system. Lazy from the point of view that the advice is often given, but seldom explained exactly what is actually in the package(s).

He probably means

```
sudo apt-get install ubuntu-restricted-extras
```

oops, long night lol, thanks for fixing the code for me!
Contents:
    * gstreamer0.10-plugins-ugly
    * gstreamer0.10-plugins-ugly-multiverse
    * ttf-mscorefonts-installer
    * flashplugin-installer
    * unrar
    * gstreamer0.10-plugins-bad
    * gstreamer0.10-plugins-bad-multiverse
    * gstreamer0.10-ffmpeg
    * libavcodec-extra-52
    * icedtea6-plugin
    * libmp4v2-0

---

### Post by howefield on 2010-08-04
> **daniell59 said:**
> I thought that Ubuntu was open source.

Well it is, but there are packages that you can choose to add to the system at your own choice, the packages in ubuntu-restricted, or using proprietary HardWare Drivers.

They aren't in the default install, you have to choose to use them.

---

### Post by joereith on 2010-08-04
Please do!! I highly advise that you give it away to as many people as you can.

---

### Post by mbsullivan on 2010-08-04
> 
This is probably not a big deal (I use libdvdcss2 myself since it is just stupid to have to pay extra money to have to play DVDs I already own when I paid for the DVD player in my laptop already) but if I am not mistaken the method given to you is technically illegal in the United States under the DMCA, because it is illegal to break the encryption on the DVDs (despite the fact that this encryption is extremely weak and easy to get past). To do things legally I think you have to pay for a DVD codec from Fluendo, unless things have changed since last I checked. Someone please say they have?

Sort of... It's now (and very recently) become legal to circumvent the protection &#8220;solely in order to accomplish the incorporation of short portions of motion pictures into new works for the purpose of criticism or comment&#8221;. See [here]("http://www.zdnet.co.uk/blogs/jacks-blog-10017212/us-says-its-ok-to-jailbreak-an-iphone-and-take-excerpts-from-dvds-10018104/"). 

Taking whole DVDs (even for your own personal criticism and comment ;) ) *probably* remains illegal, though only because it hasn't been challenged directly. 

Hopefully that will change soon... It seems to me that, if you apply the same logic to DVDs that is being applied to software, etc., then you should be able to circumvent the copy protection to view the entire thing so long as you own it and are using it yourself (fair use). For instance, apply the following argument to DVDs:

> "Merely bypassing a technological protection that restricts a user from viewing or using a work is insufficient to trigger the (Digital Millennium Copyright Act's) anti-circumvention provision," Judge Garza wrote for the New Orleans-based court. "The DMCA prohibits only forms of access that would violate or impinge on the protections that the Copyright Act otherwise affords copyright owners." (from a recent court case about [circumventing software associated with UPSs]("http://www.courthousenews.com/2010/07/23/29099.htm"))

That being said, I'm no expert. Go EFF!

Mike

---

### Post by badbradmx on 2010-08-04
the restricted extras are codecs and such that arent legally allowed to be shipped with ubuntu, codecs for MP3's and the like

---

### Post by endotherm on 2010-08-04
Op, as it intersects your question, you can redistribute ubuntu, but you cannot redistribure the restricted items (proprietary codecs, applications, and drivers) as they require a license for redist, which you likely do not possess. that is part of why they are not on the ubuntu live cd and must be downloaded separately.

---

### Post by -kg- on 2010-08-04
> **badbradmx said:**
> the restricted extras are codecs and such that arent legally allowed to be shipped with ubuntu, codecs for MP3's and the like

That's not entirely accurate.  Some distros (like Ubuntu and Fedora) like to stick with strictly open-source (open source, meaning freely distributable and modifiable), but offer the ability to install non-free (closed source) software and codecs for compatibility.

It is not illegal to ship them with a distro.  A lot of them ship with Linux Mint, for example.  It's just a choice that each end user makes on whether to install them or use strictly open source software and codecs.

---

### Post by badbradmx on 2010-08-04
> **-kg- said:**
> That's not entirely accurate.  Some distros (like Ubuntu and Fedora) like to stick with strictly open-source (open source, meaning freely distributable and modifiable), but offer the ability to install non-free (closed source) software and codecs for compatibility.

It is not illegal to ship them with a distro.  A lot of them ship with Linux Mint.  It's just a choice that each end user makes on whether to install them or use strictly open source software and codecs.

thats what i read on the ubuntu site, but what ever the reason they have to be installed seperately, il try find the link

---

### Post by Gone Digital on 2010-08-04
What legal route could I take to enable DVD viewing, installed on the laptop before point of sale?

Thank You.

---

### Post by endotherm on 2010-08-04
> **Gone Digital said:**
> What legal route could I take to enable DVD viewing, installed on the laptop before point of sale?

Thank You.

there probably isn;t a good one, beyond writing a script to install the content off medibuntu and then dropping a link to the script on the desktop. that way they can click, enter a password, wait a few seconds, and drop a dvd in the drive.

here is a stab at a install script. be sure to link it using gksu (eg: 'gksu ./installCodecs.sh') so it runs as admin. 
```

#!/bin/bash

#isntalls restricted extras and the medibuntu repos.
#this script shoudl be run with gksu if being linked from a shortcut.

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update;
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu;
sudo apt-get install libdvdcss2 ubuntu-restricted-extras w32codecs

```

if you are installing 64 bit ubuntu, change w32codecs to w64codecs.

---

### Post by Gone Digital on 2010-08-04
> **endotherm said:**
> there probably isn;t a good one, beyond writing a script to install the content off medibuntu and then dropping a link to the script on the desktop. that way they can click, enter a password, wait a few seconds, and drop a dvd in the drive.

here is a stab at a install script. be sure to link it using gksu (eg: 'gksu ./installCodecs.sh') so it runs as admin. 
```

#!/bin/bash

#isntalls restricted extras and the medibuntu repos.
#this script shoudl be run with gksu if being linked from a shortcut.

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update;
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu;
sudo apt-get install libdvdcss2 ubuntu-restricted-extras w32codecs

```if you are installing 64 bit ubuntu, change w32codecs to w64codecs.

Thank You for that, and that will be legal for me?

Thank You ):P

---

### Post by goldblattster on 2010-08-04
You can also install VLC Media Player, it plays pretty much all formats, including DVDs.

---

### Post by endotherm on 2010-08-04
> **Gone Digital said:**
> Thank You for that, and that will be legal for me?

Thank You ):P
well, it's as legal as me providing the info to you.... just make sure the user clicks the link not you. most of this software is freely licensed to individual users, so the user isn't doing anything wrong by installing it, but you are acting as an OEM distributer, and if YOU want to install it on their behalf, then as an OEM you are infringing on their copyright unless you have a license to redistribute. since you doing it would cost money, but them doing it woudl be free, and legal, it seems like the best bet.

---

### Post by Zorgoth on 2010-08-04
VLC, if it plays DVDs, is using the exact same libdvdcss, unless you bought the stuff from Fluendo.  So no, that is not technically legal.

---

### Post by Zorgoth on 2010-08-04
I would be a little nervous about the script because Ubuntu can always use the defense that not all their users live in countries with this kind of patent law.  You can't...  To keep things above-board, I would probably recommend enabling the Medibuntu repository but not having a script to install libdvdcss2.  You can probably safely tell the customer that libdvdcss2 exists, if you advise them that the legality is questionable.

---

### Post by Gone Digital on 2010-08-04
I'm guessing (but could be wrong) that I have two options (to stay legal).

1. Give the user a step-by-step guide on how to install the codec(s).
or 2. Point the user to [http://shop.canonical.com/product_info.php?products_id=243](http://shop.canonical.com/product_info.php?products_id=243)

---

### Post by snowpine on 2010-08-04
Make UbuntuForums the Firefox home page, and we will gladly answer any questions the buyer may have. :)

---

### Post by -kg- on 2010-08-04
If there are all these legalities involved in including non-free software and codecs in a distribution, I wonder how Linux Mint does it?

---

### Post by Gone Digital on 2010-08-04
> **snowpine said:**
> Make UbuntuForums the Firefox home page, and we will gladly answer any questions the buyer may have. :)

Good Idea :D.

Thank You. ):P

---

### Post by snowpine on 2010-08-04
> **-kg- said:**
> If there are all these legalities involved in including non-free software and codecs in a distribution, I wonder how Linux Mint does it?

Mint is based outside the USA. :)

---

### Post by Gone Digital on 2010-08-04
> **snowpine said:**
> Mint is based outside the USA. :)

I'm from England (UK), so because "outside the USA" does the codec legalities still apply?

Thank You ):P.

---

### Post by dv3500ea on 2010-08-04
What country do you live in?
I get the impression this law is mainly for the USA.
*EDIT: you answered that while I was typing!*

tbh. no one's going to bother suing you anyway if you're just a small distributor. Surely the users' right to play DVDs they have bought and use the full capability of their hardware trumps a small legal technicality anyway.

---

### Post by snowpine on 2010-08-04
> **Gone Digital said:**
> I'm from England (UK), so because "outside the USA" does the codec legalities still apply?

Thank You ):P.

You're welcome... I am not a lawyer, and I don't even play one on TV. ;)

My feeling is that there's illegal, and then there is ILLEGAL, if you know what I'm saying... 

Ubuntu is the #1 desktop Linux distro in the world, with the backing of a large company (Canonical) and I think because they are high profile, they try to take the safest, most conservative policy so that Ubuntu can be freely distributed anywhere in the world. 

Mint is more of a one-man-project, run by a highly-opinionated guy in France (edit: Ireland), so...

---

### Post by _h_ on 2010-08-04
> **JBAlaska said:**
> oops, long night lol, thanks for fixing the code for me!
Contents:
    * gstreamer0.10-plugins-ugly
    * gstreamer0.10-plugins-ugly-multiverse
    * ttf-mscorefonts-installer
    * flashplugin-installer
    * unrar
    * gstreamer0.10-plugins-bad
    * gstreamer0.10-plugins-bad-multiverse
    * gstreamer0.10-ffmpeg
    * libavcodec-extra-52
    * icedtea6-plugin
    * libmp4v2-0

They need to update the list on ubuntu information, since ubuntu-restricted-extras also installs java.

---

### Post by mikodo on 2010-08-04
Sorry to sidetrack here; but what does this mean "ugly this or that"? 

I have used it I think in Smplayer and they work fine, I just don't know what the term "ugly" means!

* gstreamer0.10-plugins-ugly
    * gstreamer0.10-plugins-ugly-multiverse

thanks

---

### Post by pcgeekguru on 2010-08-04
Remember linux is not $$Microsoft$$ so no there's nothing wrong with sharing it with others.

---

### Post by badbradmx on 2010-08-04
> **mikodo said:**
> Sorry to sidetrack here; but what does this mean "ugly this or that"? 

I have used it I think in Smplayer and they work fine, I just don't know what the term "ugly" means!

* gstreamer0.10-plugins-ugly
    * gstreamer0.10-plugins-ugly-multiverse

thanks
yeah id like to know too actually, doesnt seem to make any sense lol

---

### Post by Zimmer on 2010-08-04
> **badbradmx said:**
> yeah id like to know too actually, doesnt seem to make any sense lol

You have not seen gstreamer0.10-plugins-good  and gstreamer0.10-plugins-bad , then ;)

---

### Post by badbradmx on 2010-08-04
> **Zimmer said:**
> You have not seen gstreamer0.10-plugins-good  and gstreamer0.10-plugins-bad , then ;)

not really looked tbh, but why would you name it bad or ugly? unless it was crap

---

### Post by mikodo on 2010-08-04
> **Zimmer said:**
> You have not seen gstreamer0.10-plugins-good  and gstreamer0.10-plugins-bad , then ;)
Now that's a play words! "The Good, Bad and the Ugly". A movie!

Seriously though, what does the ugly mean? A workaround maybe?

Thanks

---

### Post by mc4man on 2010-08-04
from synaptic
> This package contains plugins from the "ugly" set, a set of
good-quality plug-ins that might pose distribution problems.

> GStreamer Bad Plug-ins is a set of plug-ins that aren't up to par compared
to the rest. They might be close to being good quality, but they're missing
something - be it a good code review, some documentation, a set of tests, a
real live maintainer, or some actual wide use.

---

### Post by rory526 on 2010-08-04
> **Gone Digital said:**
> I'm from England (UK), so because "outside the USA" does the codec legalities still apply?

Thank You ):P.

No. You cannot patent software in the E.U., so it's legal to distribute with the restricted extras. There are no software patents in India either as far as I know.

The patent law applies to the U.S., Japan and Korea.

Not sure about elsewhere.

---

### Post by rory526 on 2010-08-04
> **snowpine said:**
> You're welcome... I am not a lawyer, and I don't even play one on TV. ;)

My feeling is that there's illegal, and then there is ILLEGAL, if you know what I'm saying... 

Ubuntu is the #1 desktop Linux distro in the world, with the backing of a large company (Canonical) and I think because they are high profile, they try to take the safest, most conservative policy so that Ubuntu can be freely distributed anywhere in the world. 

Mint is more of a one-man-project, run by a highly-opinionated guy in France, so...

I thought mint was Ireland-based?

---

### Post by Zorgoth on 2010-08-04
One thing to note is that if you install Ubuntu you should mention at least one thing:

Tell the person to install his/her programs from Ubuntu Software Center or Synaptic and not to try to download them from the web.  Otherwise they will destroy their OS within a week and bring it back :D

---

### Post by Zorgoth on 2010-08-04
I would consult someone professional about that actually; I am not sure the DMCA type laws are precisely software patents.  I think there are laws in some European countries that make distributing software that bypasses DVD protection illegal.

(I believe that *possession* of libdvdcss is probably legal in the UK, though don't quote me on it)

---

### Post by Ozymandias_117 on 2010-08-04
> **Zorgoth said:**
> This is probably not a big deal (I use libdvdcss2 myself since it is just stupid to have to pay extra money to have to play DVDs I already own when I paid for the DVD player in my laptop already) but if I am not mistaken the method given to you is technically illegal in the United States under the DMCA, because it is illegal to break the encryption on the DVDs (despite the fact that this encryption is extremely weak and easy to get past).  To do things legally I think you have to pay for a DVD codec from Fluendo, unless things have changed since last I checked.  Someone please say they have?

If they ever try to sue me for it, they can subtract the cost of all the DVDs I've bought that they won't allow me to watch from their settlement...

---

### Post by Zorgoth on 2010-08-04
An individual is quite safe from being sued.  A small distributor like the OP is also probably safe.  The problem is, if sued, his business could die, whatever the legalities; he will not have the resources to fight it, and while I am sure that people like the FSF would stand up for him, I doubt he would make back the lost revenue.

---

### Post by badbradmx on 2010-08-04
like someone said earlier theres illegal then there ILLEGAL, i think bypassing the encryption on a DVD you bought surely falls in the illegal area if illegal at all. im sure our government should be paying more attention to the number of stabbings than who is bypassing the encryption

---

### Post by mikodo on 2010-08-04
> **mc4man said:**
> from synaptic
Thanks for looking that up for me.

I guess I could have done a search....... dah!

Mike):P

---

### Post by beew on 2010-08-04
Zorgorth


> Tell the person to install his/her programs from Ubuntu Software Center  or Synaptic and not to try to download them from the web.  Otherwise  they will destroy their OS within a week and bring it backSorry, dude, this is nonsense.

While the Ubuntu software management system is great,  it doesn't get feature updates between releases and some programs are terribly out dated. It is safe to download from the web and/or enable third party PPAs to get more updated versions  as long as you do some research beforehand. Besides, there are good softwares that you just can't get from the repos, you may have to download it for buy it from some other vendors.(Sorry, PSPP is not a replacement for SPSS, not even close)

I have installed a lot of programs from third party PPAs and a few things I downloaded from the webs(like the latest OpenOffic instead of Ubuntu release from the repos and the Foxit pdf reader, I had to download the package gkrellm i8k from the web for my overheating Dell because it is no longer in the repos for some reasons, along with a few other stuffs )  and my system is running in top shape for quite a few months. 

Linux is supposed to give people more freedom rather than restrict  them . There is something wrong in the picture if your OS becomes a kind of benign big brother that protects you from yourself at every turn,---better than a big brother that spys on you ala Windows but a big brother still. Security is important, but  you can get overboard. Nothing in the world is 100% safe, the approach you advocate is like the fearful person who turns his own house into a prison for himself so that he wouldn't be harmed by criminals from outside.

If you install Ubuntu in an old computer by all means mess around, you may break a few things but is part of the Linux experience, learning how to fix themis part of the learning experience. If you don't want to experiment and customize your computing environment you should get a Mac, --you get both the software and hardware from one source and there is no risk.

---

### Post by Zorgoth on 2010-08-04
It is the OP's decision how closely to toe the line.

If someone has specific legal knowledge, that is helpful.

The ideology of the situation is not really relevant.  I do not disagree that it is ridiculous that some countries have laws that may criminalize distributors of software used for things which I would consider obvious fair use.  

However, I think that hijacking this thread with a discussion of the moralities or lack thereof of laws like the DMCA is not helpful to the OP.

I will not post again in this thread on this subject unless I find something I consider to be a credible source about the laws in the UK on bypassing protection on DVDs.

---

### Post by Zorgoth on 2010-08-04
@beew

I do not mean to tell them not to download things from the web ever.

I mean to tell them that the software center is the first place to look, particularly for a new user who may not know what they are doing.

---

### Post by snowpine on 2010-08-04
> **Zorgoth said:**
> Tell the person to install his/her programs from Ubuntu Software Center or Synaptic and not to try to download them from the web.  Otherwise they will destroy their OS within a week and bring it back :D

A huge +1; I would guesstimate that roughly half the beginner support requests on UbuntuForums involve either trying to install something from outside the repositories, or trying to recover the system after attempting to do so.

---

### Post by beew on 2010-08-04
> **snowpine said:**
> A huge +1; I would guesstimate that roughly half the beginner support requests on UbuntuForums involve either trying to install something from outside the repositories, or trying to recover the system after attempting to do so.


So? It is part of the learning process and I don't think that most experienced user would take the attitude that "it serves you right for screwing around" when the newbie comes for help. My experience in the forum is extremely positive :)

I just don't see the logic that you should make your decision on installing softwares based on what is in the officially approved repositories rather than your need (or want). Why should people put up with out dated buggy versions of some softwares when there are newer releases already for a few months or use plain crappy softwares (such as the aforementioned PSPP, Evince and the file roller) simply because they are in the repos?

---

### Post by fredbird67 on 2010-08-04
About the codecs for Flash, Java, MP3's, WMAs, WMV's, etc., someone mentioned that Linux Mint includes those, which it does.  But interestingly enough, even though patent law here in the United States does make things a little murky on whether those can legally be included in a Linux distro, I know of at least three Linux distributions made right here in these United States (Mepis, PCLinuxOS, and PC/OS) that are throwing caution to the wind and including them by default.

Fred in St. Louis

---

### Post by JBAlaska on 2010-08-05
As to the part of the OP's question: "Can I legally sell a used laptop with an OS that has the ability to play(decrypt)DVD's".

As far as I understand the law (and if your a lawyer in the US, correct me if I'm wrong), A royalty is paid by ALL DVD drive manufacturers for every drive they sell including the ones in your laptop or desktop, and it is perfectly legal to play original copies of commercial DVD's that you own (or rent)on any OS you choose.

If you sell a commercial OS like bill and steve, they have to pay a royalty to allow DVD's to play and you gotta pay $300 <> bucks for the privilege of owning that crap)

If you choose to use a free OS, you can still legally play those DVD's AND install that OS on a new or used computer with a DVD drive and sell it for profit, as the royalty has already been paid on the drive (weather you buy it new or it's already on the box).

I've been doing it for a few years now in the US (with a storefront) and if I'm wrong....That's still my story and I'm sticking to it. :)

Either way the gobermemt got plenty bigger fish to fry ATM.

---

### Post by utnubuuser on 2010-08-05
I was under the impression that the codec aren't installed by default, not because it is or isn't legal, so much as that the licence under which they're available isn't GPL, meaning that you're not free to use, modify, share, and redistribute at will.

Using them doesn't necessarily mean copyright/patent/license infringement, only that there is an actual EULA, (end-user-license-agreement), attached to some of them that may or may not require the your, (the end-user's), acknowledgement of said terms before your legally entitled to have them installed on your computer. 
Sun Java is a prime example.  Your welcome to install it on your computer, but you're required to agree to the license terms **beforehand**.

Considering the ease with which all the necessary codec and plugins can be installed once your even slightly familiar with the ins and outs of Ubuntu, it really wouldn't be difficult to include instructions, ie: the Ubuntu Manual (free), with your refurbished computers so your "customers" can easily take care of that themselves.

---

### Post by Ozymandias_117 on 2010-08-05
> I was under the impression that the codec aren't installed by default, not because it is or isn't legal, so much as that the licence under which they're available isn't GPL, meaning that you're not free to use, modify, share, and redistribute at will.

Using them doesn't necessarily mean copyright/patent/license infringement, only that there is an actual EULA, (end-user-license-agreement), attached to some of them that may or may not require the your, (the end-user's), acknowledgement of said terms before your legally entitled to have them installed on your computer. 
Sun Java is a prime example. Your welcome to install it on your computer, but you're required to agree to the license terms beforehand.

Considering the ease with which all the necessary codec and plugins can be installed once your even slightly familiar with the ins and outs of Ubuntu, it really wouldn't be difficult to include instructions, ie: the Ubuntu Manual (free), with your refurbished computers so your "customers" can easily take care of that themselves.

According to wikipedia, libdvdcss2 is licensed under the GPL. I don't have the deb-src repos for medibuntu to try to download it to confirm it though.

Edit: Apparently libdvdcss is part of the VideoLAN project. If you go to their page you can download the source.

---

### Post by ssj6akshat on 2010-08-05
OEM mode is the one you are probably looking for.
Canonical has licensed H.264 for OEMs so that rules out many of the patents.

---

### Post by t0p on 2010-08-05
All this talk about what is legal or illegal is pretty pointless, for a couple of reasons:


[LIST]
[*]Different countries have different laws.  The US and EU have fairly similar laws concerning copyright/intellectual property/etc, so something on this subject that's illegal in the US could very well also be illegal in the European Union.  But this is a broad-stroke generalisation.  And in other countries these laws do not apply at all.  So it all rather depends on where you are;
[*]A web forum is *not* a sensible place to ask for legal advice.  Just about everyone's posts in this thread should be prefixed with "IANAL" ("I am not a lawyer") - most of what you're being told is someone's opinion on what the law is, or even an opinion on what the poster thinks the law *should* be like.  Maybe there are lawyers specialising in international copyright/intellectual property laws contributing to the thread... but I doubt it.
[/LIST]
If you are really concerned that you might be breaking the law, you should get your wallet out and pay a real lawyer for his advice.  Alternatively you could quit stressing about whether you're committing a crime and just relax.  Jeez, who really cares anyway?  It's not like you're going to bankrupt any movie or music corporations.

---

### Post by Gone Digital on 2010-08-05
Thanks for everyones replies.

@ssj6akshat, I done a google search on what you mentioned, and [this article turned up]("http://www.zdnet.com/blog/hardware/are-ubuntu-users-covered-by-h264-license-it-depends/8228"). I'm a bit confused, as an OEM I'm not sure I would be covered, I'd need to get my own licence the article says?

Thank You ):P.

---

### Post by Prohibited on 2010-08-05
> **tgalati4 said:**
> You are doing a useful service of providing a second life to these laptops.  They have suffered through many years of Windows abuse, it's time they enjoy themselves in retirement with Ubuntu.

That's what my computer is doing ;)

---

### Post by badbradmx on 2010-08-05
from the link, it appears we are all right, too a degree. 

I think your best off not including the repo's but having a document on the desktop explaining how to install them.

---

### Post by Gone Digital on 2010-08-05
Thanks, that might be the best bet to choose.

):P

---

### Post by Gone Digital on 2010-08-05
Will the Ubuntu team mind if I apply for a few free cds from the ubuntu website?, what would be the estimated delivery time?

Thank You :)

---

### Post by eriktheblu on 2010-08-05
> **JBAlaska said:**
> As far as I understand the law (and if your a lawyer in the US, correct me if I'm wrong), A royalty is paid by ALL DVD drive manufacturers for every drive they sell including the ones in your laptop or desktop, and it is perfectly legal to play original copies of commercial DVD's that you own (or rent)on any OS you choose.
Not a lawyer, but I believe you're wrong.

The drive manufacturer would need to pay royalties to the patent holder (Sony I think), but this would simply cover the functions of accessing the data on the disk. 

The problem comes in with the codec and encryption. The MPEG-2 codec is proprietary. While it's perfectly legal to look at the 1s and 0s, decoding them into video supposedly requires a license from the patent holder. In Windows and Mac, I assume this license is purchased by MS and Apple respectively. In a stand alone DVD player, the license is purchased by the manufacturer.

CSS is slightly different as it is a DRM encryption system. The DCMA prohibits the means of circumventing DRM.

To eliminate the potential of legal trouble, obtain licensed software or don't play DVDs.

---

### Post by forrestcupp on 2010-08-05
> **Gone Digital said:**
> I fix old-ish laptops which I sell on, is it ok to Install Ubuntu on these and give away a free cd with each laptop?

Thank You.It's great that you're doing that, but ethically, it would be good for you to make sure people understand that they're not getting Windows when they buy a computer.  If they buy one of your computers, then go to Wal-mart and buy a PC game and it won't work, they probably won't be too happy.

> **snowpine said:**
> My feeling is that there's illegal, and then there is ILLEGAL, if you know what I'm saying...
The problem with that is that "illegal" can get you in just as much trouble as "ILLEGAL".  If you're facing a stiff fine or jail time for "illegal", it doesn't matter much to you that it wasn't "ILLEGAL".  one hundred thousand dollars is just as bad as ONE HUNDRED THOUSAND DOLLARS. ;)

I'd say that someone who is actually selling computers has a lot more to worry about than an individual user.

---

### Post by earthpigg on 2010-08-05
> **eriktheblu said:**
> To eliminate the potential of legal trouble, obtain licensed software or don't play DVDs.

An alternative is to play the [MAD]("http://en.wikipedia.org/wiki/Mutual_assured_destruction") game and join the [big Linux patent cartel]("http://en.wikipedia.org/wiki/Open_Invention_Network"). 

Sony, IBM, and Phillips are three of the members. If you join, they will not sue you for patent infringement related to Linux (& you agree not to sue them, of course). In exchange, they get identical access to any 'invention' you may create. In addition, any company not part of the cartel that sues any member over Linux is considered by the cartel to be suing all of them. Very Cold War NATO/Warsaw Pact.

They do have to accept you as a member, but that is not nearly as difficult as one would possibly assume. I had a little one man Ubuntu respin that made it into the distrowatch.org top 100 for about 5 minutes, and they invited me out of the blue based on that.

---

### Post by forrestcupp on 2010-08-05
> **earthpigg said:**
> An alternative is to play the [MAD]("http://en.wikipedia.org/wiki/Mutual_assured_destruction") game and join the [big Linux patent cartel]("http://en.wikipedia.org/wiki/Open_Invention_Network").

Wow.  That's pretty interesting.  The part about giving them the same access to any invention I may make is kind of scary, though.

---

### Post by endotherm on 2010-08-05
> **forrestcupp said:**
> Wow.  That's pretty interesting.  The part about giving them the same access to any invention I may make is kind of scary, though.
it probably doesn't work quite that way, but you would be agreeing not to sue them if they implemented code that infringed on your patents. remember though, patents are on abstract algorithms and claims, not on coded implementations (thats what copywrong is for) so they are not actually using your invention, but the general ideas behind a concept you patented. same concept as creating an open implementation of an ISO specification.

when it comes to soft patents (software and business process) the word "invention" should never be used, as the patentor did not actually invent anything. they just made some claims....

---

### Post by badbradmx on 2010-08-05
this is way off topic now. i say we leave it as is unless someone with hands on experience with the legal issues cares to post

---

### Post by epsolon77 on 2010-08-05
I'm at work and can't read the whole post, but in the first bunch of pages I didn't see anywhere that you can't charge for the OS.  If you give the customer a receipt or invoice, I would very specifically note on the receipt, "Ubuntu Operating system --free"  The liscence doesn't just say Linux CAN be free, the liscence says Linux MUST be free.  You CAN'T charge for linux, you do not have a choice.  I think the exception is that you can charge for the media you put it on.  So if you burn an OS recovery disk, you can charge the .10 USD for the CD.

---

### Post by forrestcupp on 2010-08-05
> **epsolon77 said:**
> I'm at work and can't read the whole post, but in the first bunch of pages I didn't see anywhere that you can't charge for the OS.  If you give the customer a receipt or invoice, I would very specifically note on the receipt, "Ubuntu Operating system --free"  The liscence doesn't just say Linux CAN be free, the liscence says Linux MUST be free.  You CAN'T charge for linux, you do not have a choice.  I think the exception is that you can charge for the media you put it on.  So if you burn an OS recovery disk, you can charge the .10 USD for the CD.

That's not true at all.  The license actually says that you *can* charge for it.  It's perfectly legal to take a GPL software and charge as much as you can possibly find some ignorant person to pay the price for it.  It's just crazy to pay for something when you can get it free of charge, unless your paying for the convenience of someone else doing the work for you.

---

### Post by tgm4883 on 2010-08-05
> **epsolon77 said:**
> I'm at work and can't read the whole post, but in the first bunch of pages I didn't see anywhere that you can't charge for the OS.  If you give the customer a receipt or invoice, I would very specifically note on the receipt, "Ubuntu Operating system --free"  The liscence doesn't just say Linux CAN be free, the liscence says Linux MUST be free.  You CAN'T charge for linux, you do not have a choice.  I think the exception is that you can charge for the media you put it on.  So if you burn an OS recovery disk, you can charge the .10 USD for the CD.

> **forrestcupp said:**
> That's not true at all.  The license actually says that you *can* charge for it.  It's perfectly legal to take a GPL software and charge as much as you can possibly find some ignorant person to pay the price for it.  It's just crazy to pay for something when you can get it free of charge, unless your paying for the convenience of someone else doing the work for you.

Not only can you charge for it, you are encouraged to do so. [http://www.gnu.org/philosophy/selling.html](http://www.gnu.org/philosophy/selling.html)

Here are some for sale.
[http://www.amazon.com/gp/search/ref=sr_nr_scat_229654_ln?rh=n:229654,k:ubuntu&keywords=ubuntu&ie=UTF8&qid=1281040181&scn=229654&h=6daa26094e66ffd264f35d8a090ee5b4f9439c42](http://www.amazon.com/gp/search/ref=sr_nr_scat_229654_ln?rh=n:229654,k:ubuntu&keywords=ubuntu&ie=UTF8&qid=1281040181&scn=229654&h=6daa26094e66ffd264f35d8a090ee5b4f9439c42)

---

