---
title: "Custom Debian spin"
date: 2011-05-25
forum: The Cafe
---

### Post by bodhi.zazen on 2011-05-25
For anyone who is interested, I have been working on a respin of Debian Squeeze, Zenix (you may have noticed the change to my sig).

[http://zenix-os.net/](http://zenix-os.net/)

It is a light weight OS using openbox + tint2 or awesome window manager.

I have also configured a few security features out of the box (for use on netbooks on untrusted LAN) with a firewall , psad, and snortfw.

Zenix uses persistence if you so desire.

Additional features are listed on the features page.

Feel free to take it for a spin, it is fairly polished (more so then the first release of zenix) and people who have tried it have given favorable reviews.

[http://www.bodhizazen.fivebean.net/zenix-2.0/](http://www.bodhizazen.fivebean.net/zenix-2.0/)

---

### Post by sffvba[e0rt on 2011-05-25
Cool... I have always liked the look of openbox... tried it in #! but got putt of by the fact that you have to add any applications manually to the menu :p


Looks good... 


404

---

### Post by bodhi.zazen on 2011-05-25
> **not found said:**
> Cool... I have always liked the look of openbox... tried it in #! but got putt of by the fact that you have to add any applications manually to the menu :p


Looks good... 


404

Well I am using a custom menu in Zenix as well.

You can add new apps with a graphical tool, obmenu, it is in the configuration section.

The alternate of course is to use the debian menu, but that is not as much fun as a custom menu :p

---

### Post by galacticaboy on 2011-05-25
Looks awesome and I would try it if my distro hopping days wernt coming to a close. I bookmarked it thought so when I get a new pc I can try it out!

---

### Post by Dustin2128 on 2011-05-25
Looks interesting- I think I'll try it in a vm!

---

### Post by bodhi.zazen on 2011-05-25
> **Dustin2128 said:**
> Looks interesting- I think I'll try it in a vm!

Runs well in a VM, virtualbox guest additions are included.

Sometimes the resolution of the guest is too large in virtualbox. In that event, you need to turn cairo off before changing the resolution (from the configuration menu) or you will get a black screen.

See the zenix live page.

---

### Post by NMFTM on 2011-05-25
Is pronounced the same as Microsoft's [Xenix]("http://en.wikipedia.org/wiki/Xenix") Unix OS. It's possible that they might threaten legal action.

---

### Post by Dry Lips on 2011-05-25
> **NMFTM said:**
> Is pronounced the same as Microsoft's [Xenix]("http://en.wikipedia.org/wiki/Xenix") Unix OS. It's possible that they might threaten legal action.

A **z** and a **x** isn't pronounced the same way.

/&#712;zi&#720;/ versus /&#712;&#603;ks/

I think the name of ZENix quite obviously alludes to Zen, 
so I don't think Microsoft would protest. Think about all
the -ix'es out there...

---

### Post by s.fox on 2011-05-25
My mirror is up - [here]("http://serial-coder.co.uk/blog/zenix/") :KS

---

### Post by murderslastcrow on 2011-05-25
Absolutely lovely. This is probably one of the easiest ways to get a working Debian system- I think I'll probably give it a go on a few older computers, since it comes with all the stuff I usually get for people who need a lighter-than Xfce4 environment.

Good job.

---

### Post by bodhi.zazen on 2011-05-25
> **murderslastcrow said:**
> Absolutely lovely. This is probably one of the easiest ways to get a working Debian system- I think I'll probably give it a go on a few older computers, since it comes with all the stuff I usually get for people who need a lighter-than Xfce4 environment.

Good job.

Glad you liked it. Works well on low RAM installs with two caveats ...

1. Make a swap partition before you fire up Zenix.

2. Midori is much faster then icecat (firefox).

---

### Post by el_koraco on 2011-05-25
> **bodhi.zazen said:**
> 
2. Midori is much faster then icecat (firefox).

What version of Midori is included? If it's anything other than the latest, it ain't gonna be viable. The latest, 0.3.6 is good enough to use full time. 

For anybody interrested, it can be downloaded here: 

[http://www.twotoasts.de/index.php?/archives/44-Fixed-crashers,-faster-JSON-import-and-fewer-allocations.html]("http://www.twotoasts.de/index.php?/archives/44-Fixed-crashers,-faster-JSON-import-and-fewer-allocations.html")

do an apt-get build-dep midori before you try to follow the build instructions.

---

### Post by bodhi.zazen on 2011-05-25
It is from debian squeeze , 0.2.4-3

Found it to be stable and functional, what is the advantage of 0.3.6 ? Is there a ppa for midori ?

---

### Post by el_koraco on 2011-05-25
> **bodhi.zazen said:**
> It is from debian squeeze , 0.2.4-3

Found it to be stable and functional, what is the advantage of 0.3.6 ? Is there a ppa for midori ?

Midori has a very rapid development cycle, especially since it's become the default browser in eOS. With every version, new features get added, and a lot of bugs get fixed. Just the changes from the last version, 0.3.5 were spectacular. There was a host of problems whe visiting websites a few weeks ago, the browser would crash. Although, there are still some problems, particularly with sites loaded with javascript and flash. A lot also has to do with the refinement of the Webkit engine.

There is a PPA with the latest version, here: [https://launchpad.net/~midori/+archive/ppa]("https://launchpad.net/~midori/+archive/ppa"), but the build takes about two minutes all in all. I've been using it since the last update 99 percent of the time.

---

### Post by bodhi.zazen on 2011-05-25
> **el_koraco said:**
> Midori has a very rapid development cycle, especially since it's become the default browser in eOS. With every version, new features get added, and a lot of bugs get fixed. Just the changes from the last version, 0.3.5 were spectacular. There was a host of problems whe visiting websites a few weeks ago, the browser would crash. Although, there are still some problems, particularly with sites loaded with javascript and flash. A lot also has to do with the refinement of the Webkit engine.

There is a PPA with the latest version, here: [https://launchpad.net/~midori/+archive/ppa]("https://launchpad.net/~midori/+archive/ppa"), but the build takes about two minutes all in all. I've been using it since the last update 99 percent of the time.

Alright, thank you for the information. I will look into it ;)

---

### Post by el_koraco on 2011-05-25
No probs, and the distro looks great.

---

### Post by bodhi.zazen on 2011-05-26
> **el_koraco said:**
> No probs, and the distro looks great.

OK, it was easy enough to add midori 0.3.6 from the ppa, will update the iso (takes a few hours to update the images).

---

### Post by Bart_D on 2011-05-26
> **bodhi.zazen said:**
> For anyone who is interested, I have been working on a respin of Debian Squeeze, Zenix....
**It is a light weight OS using openbox** + tint2 or awesome window manager.....

I was WAITING for this in the fall of 2007!!!  What took you so long???

---

### Post by galacticaboy on 2011-05-26
If I use this can I still use sudo apt-get? What is the package manager? Is it just Synaptic?

---

### Post by bodhi.zazen on 2011-05-26
> **Bart_D said:**
> I was WAITING for this in the fall of 2007!!!  What took you so long???

I had to polish it a bit =)

If you fire up zenix you will see it is not just openbox + a set of the lightest weight apps I could find, but a well integrated, themed functional install, at least IMO.

Sure each of us might add packages, but zenix is a nice working base.

> **galacticaboy said:**
> If I use this can I still use sudo apt-get? What is the package manager? Is it just Synaptic?

zenix uses apt get and synaptic is also available if you prefer a graphical front end.

The repos are debian squeeze + a few ppa (midori and icecat). I have tried to maintain as much compatibility with Debian as possible.

---

### Post by galacticaboy on 2011-05-26
> **bodhi.zazen said:**
> I had to polish it a bit =)

If you fire up zenix you will see it is not just openbox + a set of the lightest weight apps I could find, but a well integrated, themed functional install, at least IMO.

Sure each of us might add packages, but zenix is a nice working base.



zenix uses apt get and synaptic is also available if you prefer a graphical front end.

The repos are debian squeeze + a few ppa (midori and icecat). I have tried to maintain as much compatibility with Debian as possible.

I am just curiuos I have never used Debian. I need a good lightweight os, lighter than XFCE that I can run Dropbox, Playstation Emulator, SNES and NES Emulator, Browse the web, listen to music, and read ebooks with.

---

### Post by bodhi.zazen on 2011-05-26
> **galacticaboy said:**
> I am just curiuos I have never used Debian. I need a good lightweight os, lighter than XFCE that I can run Dropbox, Playstation Emulator, SNES and NES Emulator, Browse the web, listen to music, and read ebooks with.

I am obviously biased, but you can give zenix a try. You might need to install a few applications, but can do so with apt-get or synaptic.

For multimedia, out of the box, zenix includes vlc and audacious.

---

### Post by matty-guy on 2011-05-26
How different is it from crunchbang?

---

### Post by galacticaboy on 2011-05-26
> **bodhi.zazen said:**
> I am obviously biased, but you can give zenix a try. You might need to install a few applications, but can do so with apt-get or synaptic.

For multimedia, out of the box, zenix includes vlc and audacious.

I just tried it in VirtualBox and I liked it, it was not bad at all. I think I am still going to wait until I get a new hard drive before I install and try fully. I have already downloaded it and it is now burning to a disk for my Linux Collection!

---

### Post by bodhi.zazen on 2011-05-26
> **matty-guy said:**
> How different is it from crunchbang?

Both distros are debian and both use openbox.

Different set of default applications.

zenix has a few security features #! lacks (psad, fwsnort, wireshark, zenmap, UFW enabled by default).

Again I am biased, but IMO zenix is a little more polished as I wrote custom themes for zenix, including a custom skin for audacious, lol, and extended that theme to all applications, from vlc to gedit to xchat.

---

### Post by bodhi.zazen on 2011-05-26
> **galacticaboy said:**
> I just tried it in VirtualBox and I liked it, it was not bad at all. I think I am still going to wait until I get a new hard drive before I install and try fully. I have already downloaded it and it is now burning to a disk for my Linux Collection!

Well, one nice thing about zenix, you do not need to install it.

Use persistence. You can use a persistent home for example, see the live page.

[http://zenix-os.net/live.html#Persistence](http://zenix-os.net/live.html#Persistence)

---

### Post by matty-guy on 2011-05-26
> **bodhi.zazen said:**
> Both distros are debian and both use openbox.

Different set of default applications.

zenix has a few security features #! lacks (psad, fwsnort, wireshark, zenmap, UFW enabled by default).

Again I am biased, but IMO zenix is a little more polished as I wrote custom themes for zenix, including a custom skin for audacious, lol, and extended that theme to all applications, from vlc to gedit to xchat.

Okay, I'll give it a test possibly tomorrow or saturday :)

---

### Post by bodhi.zazen on 2011-05-31
Zenix is listed in Distrowatch under "New distributions added to waiting list"

I made a [blog page]("http://blog.bodhizazen.net/linux/zenix2-0/") with some features as well.

---

### Post by ivanovnegro on 2011-06-01
Hey, bodhi zazen, how difficult is Openbox to use, when I tried #! I was a bit confused, is it usable out of the box? I mean can I configure basic things the easy way, not only from config files?
The distro looks interesting and I want to try it anyway.
But I have to admit I dont have a security paranoia, normally on Linux I never use security things, can I disable them also? :D

---

### Post by bodhi.zazen on 2011-06-01
> **ivanovnegro said:**
> Hey, bodhi zazen, how difficult is Openbox to use, when I tried #! I was a bit confused, is it usable out of the box? I mean can I configure basic things the easy way, not only from config files?
The distro looks interesting and I want to try it anyway.
But I have to admit I dont have a security paranoia, normally on Linux I never use security things, can I disable them also? :D

I tried to make zenix as easy to use as possible and yes there are a number of configuration options in the menu, including the ability to turn psad and ufw on an off.

There are graphical tools included if you need to modify the openbox configuration.

---

### Post by gutterslob on 2011-06-01
AwesomeWM isn't exactly my favourite, but still good to see more distro re-spinners like yourself adopting a tiling WM.

Congrats. Will give it a go when I find time :)

---

### Post by ivanovnegro on 2011-06-01
> **bodhi.zazen said:**
> I tried to make zenix as easy to use as possible and yes there are a number of configuration options in the menu, including the ability to turn psad and ufw on an off.

There are graphical tools included if you need to modify the openbox configuration.

Ok, great, thank you for the reply, your distro looks really good and I like the minimalism, especially lateley I am trying to learn some of the lighter alternatives.
What is your plan with the release cycle, it is Debian based and I find this great, I only ask to know what addtional repos/PPAs you are using to have some of the latest apps because I read here you included yet the newest Midori. Do you plan some little point releases or are you using exclusiveley the Debian repos, I think #! is including also some newer stuff?
Ah, another question, do you included the non-free repo from Debian, I mean this codec stuff etc.?

---

### Post by bodhi.zazen on 2011-06-01
> **ivanovnegro said:**
> Ok, great, thank you for the reply, your distro looks really good and I like the minimalism, especially lateley I am trying to learn some of the lighter alternatives.
What is your plan with the release cycle, it is Debian based and I find this great, I only ask to know what addtional repos/PPAs you are using to have some of the latest apps because I read here you included yet the newest Midori. Do you plan some little point releases or are you using exclusiveley the Debian repos, I think #! is including also some newer stuff?
Ah, another question, do you included the non-free repo from Debian, I mean this codec stuff etc.?

Release cycle will depend on three variables:

1. Demand (requests) for a respin.

2. Assistance from the community. I do most of the work on zenix on my own in my free time.

3. Stability of Ubuntu / Debian testing.

In terms of repos, I added a ppa for icecat and midori.

Zenix uses the non-free debian repo as well.

---

### Post by krapp on 2011-06-01
> **galacticaboy said:**
> I am just curiuos I have never used Debian. I need a good lightweight os, lighter than XFCE that I can run Dropbox, Playstation Emulator, SNES and NES Emulator, Browse the web, listen to music, and read ebooks with.

Debian can do this, though Crunchbang with Openbox (based on Debian) might be ideal.

---

### Post by ivanovnegro on 2011-06-01
> **bodhi.zazen said:**
> Release cycle will depend on three variables:

1. Demand (requests) for a respin.

2. Assistance from the community. I do most of the work on zenix on my own in my free time.

3. Stability of Ubuntu / Debian testing.

In terms of repos, I added a ppa for icecat and midori.

Zenix uses the non-free debian repo as well.

Thank you again for your reply, Im running it now in VirtualBox, and yes I like it.

---

### Post by bodhi.zazen on 2011-06-01
> **ivanovnegro said:**
> Thank you again for your reply, Im running it now in VirtualBox, and yes I like it.

You are most welcome, thank you for trying zenix, and glad you like it.

---

### Post by ivanovnegro on 2011-06-01
> **bodhi.zazen said:**
> You are most welcome, thank you for trying zenix, and glad you like it.

Its indeed easy to configure basic things to my liking. :D
Maybe I will install it into a netbook.
Great work Bodhi Zazen!

---

### Post by disabledaccount on 2011-06-01
I've tried some lightweight distros till now (like f.e. SliTaz) but Zenix is much better balanced.

> **murderslastcrow said:**
> Absolutely lovely. This is probably one of the easiest ways to get a working Debian systemCompletely agree with this opinion - very nice, easy to install and good looking and  distro. I'm running it right now in VM (writing this), Live session works perfectly -> really good job bodhi.zazen :)

---

### Post by Rodney9 on 2011-06-01
Way cool, very nice indeed.

Just installed it on my spare drive. Love the backgrounds, playing Andreas - Aurora streaming on Audacious, typing this in Midori.

May have to put it on my laptop, it's small foot[print and low resource use is perfect.

---

### Post by sffvba[e0rt on 2011-06-03
I am too scared to try it out... I might like it and that will prompt my distro-hop gene to kick in again... :p



404

---

### Post by disabledaccount on 2011-06-03
That's good moment to start training Your power of will :)
...or configure several VMs (I have 12 now) ;)

---

### Post by bodhi.zazen on 2011-06-03
> **not found said:**
> i am too scared to try it out... I might like it and that will prompt my distro-hop gene to kick in again... :p

404

lol

---

### Post by sffvba[e0rt on 2011-06-11
Nice to see the spin getting a bit of buzz on the net...

[http://ostatic.com/blog/zenix-gnu-linux-fun-fast-different](http://ostatic.com/blog/zenix-gnu-linux-fun-fast-different) (got this link from [www.linuxtoday.com]("http://ubuntuforums.org/www.linuxtoday.com")).



404

---

### Post by Kexolino on 2011-06-11
> **bodhi.zazen said:**
> In terms of repos, I added a ppa for icecat and midori.

Zenix uses the non-free debian repo as well.

I'm a bit confused now... I read that it's not good to add ppas to Debian, because it messes it up. Is it not true? Or is Zenix somehow different?

Sorry to bother you with the noob questions #-o

---

### Post by ivanovnegro on 2011-06-11
> **Kexolino said:**
> I'm a bit confused now... I read that it's not good to add ppas to Debian, because it messes it up. Is it not true? Or is Zenix somehow different?

Sorry to bother you with the noob questions #-o

Thats a good question because its indeed not recommended to install PPAs on a Debian system. Not sure how Bhodi.Zazen is doing it.

---

### Post by sffvba[e0rt on 2011-06-11
> **ivanovnegro said:**
> Thats a good question because its indeed not recommended to install PPAs on a Debian system. Not sure how Bhodi.Zazen is doing it.

When your kung-fu is this powerful you can do anything...


404

---

### Post by BigSilly on 2011-06-11
Has anyone tried this on an old Eee PC? We have a 701 4G Surf, and I've kissed a lot of frogs with it but yet to meet the princess. It really needs something lightweight (it only has 512Mb RAM and a Celeron), but needs to be able to handle Flash and Facebook duties.

This looks like it could fit the bill. Please let me know if you've tried it. Thanks.

---

### Post by bodhi.zazen on 2011-06-11
> **ivanovnegro said:**
> Thats a good question because its indeed not recommended to install PPAs on a Debian system. Not sure how Bhodi.Zazen is doing it.

Well, you can add a ppa, but you need to know what you are doing (what Ubuntu version to use) and I would not add a large or complex package via a ppa.

midori and icecat seem reasonable, at least to me, but I would not add a large packages such as X or nouveau.

---

### Post by BigSilly on 2011-06-12
OK, have this installed now on our Eee, and have to say it positively flies. Thank you very much for this excellent option for the somewhat left behind spec. :)

I have a couple of simple problems that I hope you can help me with here. I may register later for your forum for assistance, but for now I would appreciate some guidance. I had to install via the text install as the graphical install wouldn't work. This is fine, but I think I messed up the sources list. There is only the choice for the Debian CD in my sources list below.

```
# 

# deb cdrom:[Debian GNU/Linux 6.0.0 _Squeeze_ - Official Snapshot i386 LIVE/INSTALL Binary 20110525-22:59]/ squeeze main

deb cdrom:[Debian GNU/Linux 6.0.0 _Squeeze_ - Official Snapshot i386 LIVE/INSTALL Binary 20110525-22:59]/ squeeze main

# Line commented out by installer because it failed to verify:
#deb http://security.debian.org/ squeeze/updates main
# Line commented out by installer because it failed to verify:
#deb-src http://security.debian.org/ squeeze/updates main
```

I can't seem to find any other sources on your site to add them manually. Can you help with this? 

Also, for some reason the touchpad scroll wheel on the Eee isn't working. What would you suggest to fix this?

Many thanks. :)

---

### Post by bodhi.zazen on 2011-06-12
Glad it is working well for you.

I can post the sources list later today , you will likely need to import the gpg keys, do you know how to do that ?

And last, I am not sure about your touchpad, I will try to see if I can find some information, but it is hard when one does not have the hardware ;)

---

### Post by BigSilly on 2011-06-12
Yes, I should be OK importing the keys. I'll post up if I can't get it figured. :)

RE: The touchpad. I think I need the xorg synaptics driver, but I don't see it in the default Debian repo and I can't figure out how to enable it. If you have any ideas do let me know. Thanks. :)

---

### Post by bodhi.zazen on 2011-06-12
> **BigSilly said:**
> Yes, I should be OK importing the keys. I'll post up if I can't get it figured. :)

RE: The touchpad. I think I need the xorg synaptics driver, but I don't see it in the default Debian repo and I can't figure out how to enable it. If you have any ideas do let me know. Thanks. :)

OK, here are the repos:

```
    # /etc/apt/sources.list
     
    deb http://cdn.debian.net/debian/ squeeze main contrib
    deb http://security.debian.org/ squeeze/updates main contrib
    deb http://cdn.debian.net/debian/ squeeze-updates main contrib

    # cairo composite manager
    deb http://download.tuxfamily.org/ccm/debian/ sid main

    # For icecat 4.0
    deb http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu lucid main
     
    # midori ppa
    deb http://ppa.launchpad.net/midori/ppa/ubuntu lucid main
          
    # webkit ppa
    deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu lucid main
```

If it is a synaptics touchpad see:

[http://wiki.debian.org/SynapticsTouchpad](http://wiki.debian.org/SynapticsTouchpad)

[http://packages.debian.org/squeeze/xserver-xorg-input-synaptics](http://packages.debian.org/squeeze/xserver-xorg-input-synaptics)

---

### Post by BigSilly on 2011-06-12
Magic! Thanks for that, I'll see how I go. 

:)

---

### Post by BigSilly on 2011-06-12
Just thought I'd post up to say I've got it all working, and it's really lovely. :)  I ended up just reinstalling, as the original install was too problematic to recover. I managed to boot the graphical installer by selecting 311 as the video mode, and I had connected the Eee via ethernet just to get it up to date. After installing correctly I set up the wireless connection with no problems, and installed the required xorg-synaptics driver which seemed to do it's thing automatically after a reboot. The scroll wheel is working and the mouse is less sensitive.

It's a really nice system, and I'd just like to thank you again for it. It's great on the Eee 701 because it just doesn't demand a lot to run it. The RAM and CPU usage is comparatively low, making it a better option than the others I'd tried.

I'm gonna tailor it a little, just to make text easier to read on a small screen, but that's the single only thing I have to do to complete it. But other than that, perfect!

---

### Post by spcwingo on 2011-06-12
I might just have to fire up qemu to try this, thanks.  ;)

---

