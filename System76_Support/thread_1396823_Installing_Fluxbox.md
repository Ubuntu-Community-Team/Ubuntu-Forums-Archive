---
title: "Installing Fluxbox"
date: 2010-02-02
forum: System76 Support
---

### Post by samalex on 2010-02-02
Hi..

I used to use Fluxbox as my window manager for years, but not until getting my PanP5 did I stick with Gnome.  I'm thinking of installing Fluxbox again to give it a shot, but I wanted to see if anyone's done this because I don't want to chance hosing Gnome.

If I install it from the repositories and change it as the default Windows manager, anyone know of any caveats with going between it and Gnome?  Just curious---

Thanks,

Sam

---

### Post by thomasaaron on 2010-02-02
I installed fluxbox about a week ago, just to have a look at it. I didn't notice any glaring problems (although I didn't really check it out thoroughly).

I know jdb and other fluxbox fans are going to stomp a mud puddle in me for this, but... well... fluxbox kind of seems like a waste of high-tech hardware. What I mean is that the Pangolin is already a fine, snappy machine that doesn't need a minimalistic, ultra-light OS on it to keep it from being a dog. 

Plus, I don't like the idea of settling for minimalistic apps on cutting-edge hardware. I like options and versatility.

I like more, not less. A Porsche and a Yugo will both go 75 mph. But I'll take the Porsche, than you very much. 

OK, let the stompfest begin.

---

### Post by samalex on 2010-02-02
> **thomasaaron said:**
> I installed fluxbox about a week ago, just to have a look at it. I didn't notice any glaring problems (although I didn't really check it out thoroughly).

I know jdb and other fluxbox fans are going to stomp a mud puddle in me for this, but... well... fluxbox kind of seems like a waste of high-tech hardware. What I mean is that the Pangolin is already a fine, snappy machine that doesn't need a minimalistic, ultra-light OS on it to keep it from being a dog. 

Plus, I don't like the idea of settling for minimalistic apps on cutting-edge hardware. I like options and versatility.

I like more, not less. A Porsche and a Yugo will both go 75 mph. But I'll take the Porsche, than you very much. 

OK, let the stompfest begin.

Hi Thomas,

I'm mainly curious to see what's new because I used Flux for many years before moving to OSX in 2005.  Plus I'd like to do a demo of different Window Managers and Desktops to show them in an upcoming LUG meeting :-)  Actually I agree with you 100% that running Flux full time on a system like the PanP5 would greatly under-utilize what the system can do.

I just installed 32-bit Ubuntu 9.10 Desktop via VirtualBox so I'll probably test it there instead.  

Take care --

Sam

---

### Post by thomasaaron on 2010-02-02
OK. Well, I was just trying to start a riot (or pick a fight with jdb at a minimum). :popcorn:

---

### Post by HandyAndy on 2010-02-02
sam -

I've been using fluxbox as my window manager on top of a standard Gnome Ubuntu set-up for at least 3 years and it's never caused any problem with the underlying OS. On the rare occasions that I choose a Gnome session, everything works fine.

thom -

ok, I'll take the bait :)
I absolutely agree with your analogy and I'd take the Porsche too. Elegantly designed, beautifully engineered, form and function in perfect harmony, fun and fast - that's fluxbox!

---

### Post by thomasaaron on 2010-02-02
> ok, I'll take the bait
I absolutely agree with your analogy and I'd take the Porsche too. Elegantly designed, beautifully engineered, form and function in perfect harmony, fun and fast - that's fluxbox!

LOL. I'm don't think I'm witty enough to beat that! Nicely done.

---

### Post by samalex on 2010-02-02
> **HandyAndy said:**
> sam -

I've been using fluxbox as my window manager on top of a standard Gnome Ubuntu set-up for at least 3 years and it's never caused any problem with the underlying OS. On the rare occasions that I choose a Gnome session, everything works fine.

thom -

ok, I'll take the bait :)
I absolutely agree with your analogy and I'd take the Porsche too. Elegantly designed, beautifully engineered, form and function in perfect harmony, fun and fast - that's fluxbox!

Back in the day when I ran Red Hat (9 and below, pre-Fedora) I always used older systems (even for the day), so KDE and Gnome ran slower than I liked.  That's mainly why I started using Flux back then, which we're taking 2000 or 2001.  But after using Flux I started really enjoying the simplistic desktop and how easily it could be customized through just a few config files.

Though I don't think I'll ditch Gnome for Flux full time, the only things that would stop me from making the jump is if Fluxbox has problems connecting to wireless networks or VPN, both of which I use the Gnome network manager to do.  I guess I could always start Gnome Network Manager from Flux directly, so it may not be a big deal after all.

Too bad I can't boot into Flux with one user and Gnome with another, but I think by the time it's made it to the login the desktop manager of choice has already started.

Thanks --

Sam

---

### Post by jdb on 2010-02-02
> **samalex said:**
> 
Though I don't think I'll ditch Gnome for Flux full time, the only things that would stop me from making the jump is if Fluxbox has problems connecting to wireless networks or VPN, both of which I use the Gnome network manager to do.

I replaced network-manager with wicd long ago.
I don't know how Fluxbox works with network-manger, but it works great with wicd, so does Gnome.
In Gnome there is a widget on the menubar just like with network-manager.
In Fluxbox use wicd-client -n to bring up a GUI.

If you install Fluxbox it doesn't affect Gnome at all, you just have
the choice of loging in with Fluxbox or with Gnome.

I made my own theme.cfg file & stuck it under ~/.fluxbox/styles .
That along with 3 other files: init, menu & startup are all I need to
copy to a new install to make it look & feel like all my others.

I like Gnome with all it's nice effects, but sometimes I just like less between my apps & the system :)

All those cryptic XML files drive me nuts :lolflag:

jdb

---

### Post by samalex on 2010-02-02
I went ahead and started installing Fluxbox on my laptop, outside of VirtualBox, and while in there I selected wicd to use it with Flux.  I read too fast and didn't see the notice saying it would also uninstall network-manager and network-manager-gnome, so after it was done installing I had no network support.  I tried reinstalling these two packages but not being online and not having a 64-bit 9.04 desktop CD on hand it had no way to get them.

So I completely removed wicd and am on my wife's laptop downloading the 64-bit 9.04 Desktop ISO.  Yeah I could probably hunt around and find just he packages, but it's late so figured I'd just pull down the whole ISO.  Luckily I played with Bluetooth on my laptop today at work with my cellphone and figured out how it worked, so I'm connected to my wife's MacBook via Bluetooth and will copy the ISO over that way when it's downloaded.

Hopefully it didn't do a complete remove because I had all my VPN connections, WEP keys, everything setup via network-manager.  Blah

Four minutes left on the ISO and I'll pull it over to my laptop to grab the network-manager packages.

Sam

---

### Post by malachi1990 on 2010-02-02
Quick fix is to reinstall the ubuntu-desktop package, as that will bring in the network manager stuff back with it.

My two cents: Flux is a nice replacement for Metacity (if you're using it in conjunction with Gnome), and is great on its own, but doesn't hold a candle to E17.  

Flux is nice, and is definitely useful to show off how different a linux system can look (should you decide to show it off).

---

### Post by jdb on 2010-02-02
> **samalex said:**
> I went ahead and started installing Fluxbox on my laptop, outside of VirtualBox, and while in there I selected wicd to use it with Flux.  I read too fast and didn't see the notice saying it would also uninstall network-manager and network-manager-gnome, so after it was done installing I had no network support.  I tried reinstalling these two packages but not being online and not having a 64-bit 9.04 desktop CD on hand it had no way to get them.

So I completely removed wicd and am on my wife's laptop downloading the 64-bit 9.04 Desktop ISO.  Yeah I could probably hunt around and find just he packages, but it's late so figured I'd just pull down the whole ISO.  Luckily I played with Bluetooth on my laptop today at work with my cellphone and figured out how it worked, so I'm connected to my wife's MacBook via Bluetooth and will copy the ISO over that way when it's downloaded.

Hopefully it didn't do a complete remove because I had all my VPN connections, WEP keys, everything setup via network-manager.  Blah

Four minutes left on the ISO and I'll pull it over to my laptop to grab the network-manager packages.

Sam

It's normal for network-manager to be removed when wicd is installed, but wicd should have replaced it.
If I remember right you have to logout & back in for the network to re-connect though.
I'm using wicd in Gnome right now.

At any rate, it should have left all the old configuration files intact if you need to go back.

jdb

---

### Post by samalex on 2010-02-02
> **jdb said:**
> It's normal for network-manager to be removed when wicd is installed, but wicd should have replaced it.
If I remember right you have to logout & back in for the network to re-connect though.
I'm using wicd in Gnome right now.

At any rate, it should have left all the old configuration files intact if you need to go back.

jdb

I've never used wicd and couldn't find how to configure it, but I didn't try to reboot... maybe that was the problem.

After the ISO downloaded it would've taken 2 hours to transmit it over bluetooth, so I did dig-up the packages from Ubuntu's website, copied those over via BT, installed, and rebooted.  I'm back online now and yeah all my settings are there.

I've never used wicd though... any advantages to it over network manager?  Just curious.  

Take care,

Sam

---

### Post by jdb on 2010-02-02
> **samalex said:**
> I've never used wicd and couldn't find how to configure it, but I didn't try to reboot... maybe that was the problem.

After the ISO downloaded it would've taken 2 hours to transmit it over bluetooth, so I did dig-up the packages from Ubuntu's website, copied those over via BT, installed, and rebooted.  I'm back online now and yeah all my settings are there.

I've never used wicd though... any advantages to it over network manager?  Just curious.  

Take care,

Sam

I use static IP addresses in my home network & I could never get network-manager to work right with them.

Also I could not get a GUI configuration screen in Fluxbox.

To configure wicd in Gnome just left click the network widget in the menu tray, there should be one where the network-manager widget was.

Another way to to get the configuration GUI is to type

```
wicd-client -n
```

at the command line, that works in Gnome or Fluxbox.

jdb

---

### Post by samalex on 2010-02-03
> **jdb said:**
> I use static IP addresses in my home network & I could never get network-manager to work right with them.

Also I could not get a GUI configuration screen in Fluxbox.

To configure wicd in Gnome just left click the network widget in the menu tray, there should be one where the network-manager widget was.

Another way to to get the configuration GUI is to type

```
wicd-client -n
```

at the command line, that works in Gnome or Fluxbox.

jdb

Ahh that's what I was missing. Before removing it I tried running 'wicd' to see if that would've brought-up some sort of configuration tool, but didn't.

After getting network-manager reinstalled I did boot into Flux, but I guess I've gotten spoiled by Gnome and my years of using OSX because it was almost too minimalistic.  Also the fonts were really large for some reason, but everything seemed to work as it should.  I may tinker with it more later, but for now I'm back in Gnome.

I also have 9.10 installed in VirtualBox and will probably install several of the windows managers there to present at an upcoming LUG meeting, but for my personal use I may stick with Gnome after all... Thomas won :-D

Sam

---

### Post by jdb on 2010-02-03
> **samalex said:**
> Ahh that's what I was missing. Before removing it I tried running 'wicd' to see if that would've brought-up some sort of configuration tool, but didn't.

After getting network-manager reinstalled I did boot into Flux, but I guess I've gotten spoiled by Gnome and my years of using OSX because it was almost too minimalistic.  Also the fonts were really large for some reason, but everything seemed to work as it should.  I may tinker with it more later, but for now I'm back in Gnome.

I also have 9.10 installed in VirtualBox and will probably install several of the windows managers there to present at an upcoming LUG meeting, but for my personal use I may stick with Gnome after all... Thomas won :-D

Sam

Yea, Fluxbox is pretty simple when your used to Gnome & stock out
of the box it looks kind of funky.
I don't think I'll win many converts :)
I customized mine long ago & just keep reusing the config files
on other partitions & other machines.

Also, to use wallpaper you need to have a helper app installed.
feh serves well, if it is installed then wallpaper just works.

I use Gnome most of the time myself in Ubuntu but if I'm putting
a desktop on a command line Linux install, Fluxbox is a lot
faster & easier to do.
If I have a second user screen going in Ubuntu it's usually root with
a Fluxbox desktop, I never forget which screen I'm on.

jdb

---

