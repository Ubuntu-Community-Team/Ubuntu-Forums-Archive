---
title: "Once again I am defeated by linux"
date: 2007-07-24
forum: Testimonials &amp; Experiences
---

### Post by jijin on 2007-07-24
I have been trying about every year or so to install Linux, and I find that every year there is a show stopper for me that forces me back to XP. This time it was drivers. For all the flak that I had heard that linux had bad driver support I had, until now, no problems. Before it was mostly me being lazy, not wanting to take the time to learn things. 

I started to see games, including the one I play mostly, EVE Online, are moving over to Linux. So I decided to once more try it out. I'd have to admit, compiz/beryl/fusion, ubuntu studio, and  the OSX-like docks are pretty awesome looking too. 

I have on-board graphics, and I have not been able to get the drivers to install for the 7025 geforce card. I have tried the, restricted drivers thing, the Envy method, the latest Nvidia drivers (which supposedly support the 7025), and another method I found here on the forums. None worked, and in fact they had no idea I even had a 3d graphics card let alone the card I had. Every single time I failed the install the only thing I knew how to do to fix the graphics was to completely reinstall ubuntu. I do not mind that as installation is relatively quick.

BTW, when I first installed it it kicked me to a command line and I had just the right knowledge to get Gnome setup. Namely "sudo apt-get install ubuntu-desktop".

I know this is not linux/ubuntu's problem, but the manufacturer's and my fault. The former because they did not code Linux drivers, and the latter because I did not make sure they had it. But WTF? I know I don't game much, and I know onboard video sucks, but many people use it. I hardly believe I am the only one using the Biostar TF7025-M2 mobo.

I was really looking forward to installing this on  my computer, and (again) I am disappointed. Although I keep learning things every time I try to install Linux.

I'll be back for 7.10 though... My hopes are really low this time around.

Anyway, thanks to the DEV team for making the Distro, thanks to forum members figuring out all these people's problems, and thanks to the hackers figuring out how to keep and surpass the forefront of tech.

I'm off to swear and smoke like the Frenchmen I'm not.

---

### Post by fd9_ on 2007-07-24
Drivers are probably the hardest thing to install in Linux, if something doesn't work out-of-the-box. It's an uphill battle for sure, and you have to have enough time and patience to actually figure it out. Somebody out there has the solution and you just need to find out what it is.

---

### Post by mgmiller on 2007-07-25
The problem is that the 7025 (and the related 7050) are still very new, so the driver support is spotty.

I recently built a machine with nvidia onboard 7025 graphics.  It currently uses the vesa driver and works quite well for 2D stuff.  True, no fancy beryl/compiz and no games, but my 30 year old son doesn't do any of that.  He is quite happy using it the way it is for now.  Support for the 7025 should be in the Ubuntu repos by 7.10 at the latest.  I am hoping a little sooner, but meanwhile for any 2D stuff, it works great with VESA and 2 gig of ram and an AMD 4200+ CPU.  

You don't need to reinstall Ubuntu, once it kicks you to a command line type:
```
sudo nano /etc/X11/xorg.conf
```

scroll down to the area that looks sort of like this:

```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```

and replace the word "nvidia" (or it may say "nv") with "vesa"

It should now look like this:

```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "vesa"
EndSection
```

then save the file by hitting ctrl o  (letter o)

then exit with ctrl x

you should now be able to:

```
startx
```

or just do a ctrl>alt>backspace

You should have your GUI.

---

### Post by jijin on 2007-07-28
Thanks for the VESA driver tip..

> **mgmiller said:**
> The problem is that the 7025 (and the related 7050) are still very new, so the driver support is spotty.

spotty is an understatement

Fusion/compiz/beyrl were part of the reason I switched.

---

### Post by sloggerkhan on 2007-07-28
A few weeks ago I think nVidia had said that support for that integrated chipset (7025,7050) wasn't in their linux driver yet and that the next release would have it. This means that Ubuntu's easy method of installing drivers wouldn't work for it. :/

---

### Post by kelvin spratt on 2007-07-28
their are other Distros that have good driver support Pclinux, Elive, Pardus, all have extra drivers and are easy to install the latest Elive once setup is like nothing else the themes are excellent, I would try something else before you give up

---

### Post by HermanAB on 2007-07-28
The Vesa driver works with anything.  That is the driver that is used during the install process.  However, it won't do fancy graphics, otherwise it is fine.

Try different distributions: Fedora and Mandriva are both leading edge distributions.

Otherwise, talk to your friends and collect a few older graphics adaptors - most people have one or two lying in a junk box and an avid gamer will likely have several good ones.

'Hope that helps!

Herman

---

### Post by vwbeamer on 2007-07-29
Later, don't let the door hit ya, where the good lord split ya,

Linux is only for those who are cool, trendy and intelligent, so you're to big a dumbass to figure it out, later dude.

---

### Post by bonzodog on 2007-07-29
> **vwbeamer said:**
> Later, don't let the door hit ya, where the good lord split ya,

Linux is only for those who are cool, trendy and intelligent, so you're to big a dumbass to figure it out, later dude.

We don't need any of that attitude thank you very much.

---

### Post by TheMono on 2007-07-29
I'm sorry if you already know this, but for posterity I'll say it again.

Ubuntu works on a fixed release cycle, so no new functionality gets added between releases. That includes adding drivers. This means that the distribution can generally be more stable, as nothing new is being introduced to the mix, but it also means that you lose support for anything newer than about a month or so before the version was released. Having said that, with releases every six months, it isn't too bad

Give it another go in October when 7.10 is released, or you can use Alberto Milone's Envy to install more recent drivers (but this can and probably will break upgrades). Until then, all the best.

---

### Post by jijin on 2007-07-29
> **sloggerkhan said:**
> A few weeks ago I think nVidia had said that support for that integrated chipset (7025,7050) wasn't in their linux driver yet and that the next release would have it. This means that Ubuntu's easy method of installing drivers wouldn't work for it. :/
According to the nvidia driver site the driver version 100.14.11 is supposed to support it. Which is why it's disheartening, because _that_ driver doesn't even know it's there.

[http://www.nvidia.com/object/linux_display_amd64_100.14.11.html](http://www.nvidia.com/object/linux_display_amd64_100.14.11.html)

> **kelvin spratt said:**
> their are other Distros that have good driver support Pclinux, Elive, Pardus, all have extra drivers and are easy to install the latest Elive once setup is like nothing else the themes are excellent, I would try something else before you give up
I'm not sure about PCLinux I'll check it out later. Elive has Enlightenment, no thanks, I love the Gnome desktop. Also, the forums (my preferred support vector) are a bit slow looking.... not too  sure about Pardus, I'll check it out too. 

> **HermanAB said:**
> The Vesa driver works with anything.  That is the driver that is used during the install process.  However, it won't do fancy graphics, otherwise it is fine.

Try different distributions: Fedora and Mandriva are both leading edge distributions.

Otherwise, talk to your friends and collect a few older graphics adapters - most people have one or two lying in a junk box and an avid gamer will likely have several good ones.

I was thinking about Fedora actually, but yea, VESA drivers force me to have my desktop in 4:3, I need it in 16:10 specifically, as stretch and zooming are probably the most annoying things ever devised.

About the whole friends thing, I'm the guy _everybody_ calls when something breaks, also Asperger's doesn't help the friend situation much. It would have been a good idea otherwise.

thanks though.

> **vwbeamer said:**
> Later, don't let the door hit ya, where the good lord split ya,

Linux is only for those who are cool, trendy and intelligent, so you're to big a dumbass to figure it out, later dude.
NOUGTFOBRIDGETROLLgb2/SAforumsorGaia

On a more adult level... I have tried getting the nvidia drivers working. But they do not even see the graphics card and when I "force" it to install it won't load xorg, only a blue screen with ASCII graphics.

> **TheMono said:**
> I'm sorry if you already know this, but for posterity I'll say it again.

Ubuntu works on a fixed release cycle, so no new functionality gets added between releases. That includes adding drivers. This means that the distribution can generally be more stable, as nothing new is being introduced to the mix, but it also means that you lose support for anything newer than about a month or so before the version was released. Having said that, with releases every six months, it isn't too bad

Give it another go in October when 7.10 is released, or you can use Alberto Milone's Envy to install more recent drivers (but this can and probably will break upgrades). Until then, all the best.
Yea, I do know it but it's always good to repeat. I am going to wait maybe nvidia can get off their collective butts and write a real driver.

Else, I'll probably have a dedicated, well supported, known good video card by then. Any nvidia cards that fit that bill?

---

### Post by TheMono on 2007-07-29
Anything from the 7 series is great. I'm using a 7600GS, but I gather that the best value/performance can be found in a 7600GT.

---

