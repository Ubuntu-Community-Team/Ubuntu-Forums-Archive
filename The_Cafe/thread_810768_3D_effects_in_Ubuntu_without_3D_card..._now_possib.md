---
title: "3D effects in Ubuntu without 3D card... now possible!"
date: 2008-05-28
forum: The Cafe
---

### Post by madjr on 2008-05-28
am sure not many know about this, but is possible.

i got **cairo-compmgr** installed in an old laptop with no 3D card. it doesn't use up too much memory (but can get cpu intensive since it has many 3d effects by default).

awesome for simple effects and transparencies (you can do advance 3d but not recommended on an old piece of hardware)

now all these **mockups** flying around with light 3d and transparencies can become reality in the next ubuntu releases (probably after intrepid and when cairo-compmgr reaches v2.0).

Also the new **GDM face browser** might use something similar

note: if you have a 3D card then compiz is recommended since it will use your GPU instead of the cpu, else if no 3d card (or problems with your 3d drivers) give cairo-composite a try (it's still beta thou)

to install add the repo to your third party software sources
```
deb http://ppa.launchpad.net/gandalfn/ubuntu gutsy main universe
```

and update (if used the software sources gui, you can skip this) :

```
sudo apt-get update
```

Now to install Cairo Composite Manager:

```
sudo apt-get install cairo-compmgr
```

[http://cairo-compmgr.tuxfamily.org/](http://cairo-compmgr.tuxfamily.org/)

---

### Post by FuturePilot on 2008-05-28
I tried that once. But it was almost unusable it ran so slow.

---

### Post by madjr on 2008-05-28
> **FuturePilot said:**
> I tried that once. But it was almost unusable it ran so slow.

yea it can be **because a lot of 3D effects are ON by default**. but is a project to look forward to for simple things and compatibility in the future.

am sure v1.0+ will be awesome.

a **minimalistic version** of this compositor would be great. Might have to address that to the author.

but yea, 3D is possible now without 3D :)

am sure the author hasn't had enough testers yet.

the menu effect is cool but specially high on resources.

am just basically after the true transparencies

---

### Post by FuturePilot on 2008-05-28
In that case, why not just use Metacity's built in compositor? It's simple, much lighter, can run just fine on very low end cards, and can give you true transparency.

---

### Post by spupy on 2008-05-28
You can try xcompmgr - only shadows and transparency.

Little offtopic: Who makes an eye-candy program and puts ONLY ONE 300x200 px screenshot on their website?

---

### Post by madjr on 2008-05-28
so **Metacity's** built in compositor or **xcompmgr** work without 3d drivers?

this for an old lap with no 3d card

---

### Post by FuturePilot on 2008-05-28
Yes, I'm pretty sure it would. I have an old computer with an old ATI Rage 128 Pro which only works with the "ati" driver. That driver has almost no 3D capabilities, but it can run XFWM's composite manager pretty decently. Both Metacity's and XFWM's composite manager work the same by using XRender for compositing. So yes, it can be done without 3D drivers.

---

### Post by zmjjmz on 2008-05-28
A 700MHz PIII would be good for this?

---

### Post by madjr on 2008-05-29
> **zmjjmz said:**
> A 700MHz PIII would be good for this?

if it has less than 512mb then probably not.

at the current state is too bloated in 3d effects. You would have to disable most in the config file manually.

we're just testing it out and getting some feedback. This is a beta.

you're free to test.

am going to ask the dev to tone down the defaults.

---

### Post by forrestcupp on 2008-05-29
> **FuturePilot said:**
> Yes, I'm pretty sure it would. I have an old computer with an old ATI Rage 128 Pro which only works with the "ati" driver. That driver has almost no 3D capabilities, but it can run XFWM's composite manager pretty decently. Both Metacity's and XFWM's composite manager work the same by using XRender for compositing. So yes, it can be done without 3D drivers.
I'm pretty sure the ATI drivers do support 3D to an extent.  I know the ATI Rage 128 Pro card has minimal 3D support, and back in the day it was a decent card.

Try switching to the vesa drivers and see if Metacity's compositing would still work.  I doubt if it would.

---

### Post by FuturePilot on 2008-05-29
> **forrestcupp said:**
> I'm pretty sure the ATI drivers do support 3D to an extent.  I know the ATI Rage 128 Pro card has minimal 3D support, and back in the day it was a decent card.

Try switching to the vesa drivers and see if Metacity's compositing would still work.  I doubt if it would.
I switched it over to "vesa" and XFWM's compositor still worked somewhat decently.


> **madjr said:**
> if it has less than 512mb then probably not.



Just to give some specs of this computer I'm testing this on

Pentium III @ 900MHz
ATI Rage 128 Pro
192 MB RAM

---

### Post by durand on 2008-05-29
> **spupy said:**
> You can try xcompmgr - only shadows and transparency.

Little offtopic: Who makes an eye-candy program and puts ONLY ONE 300x200 px screenshot on their website?

There's this pic from the same site: [http://cairo-compmgr.tuxfamily.org/images/screenshot-281207.png]("http://cairo-compmgr.tuxfamily.org/images/screenshot-281207.png")

---

### Post by inportb on 2008-05-29
I don't think the thread title is altogether accurate. You don't need 3D support for compositing, but you do need 3D support for 3D effects.

Unless... you can get stuff like "the cube" using this software?

I've been running Enlightenment DR17 + Bling under Virtualbox. Virtualbox only does 2D acceleration, and Bling is none other than an EFL version of xcompmgr.

---

### Post by joninkrakow on 2008-05-29
> **madjr said:**
> so **Metacity's** built in compositor or **xcompmgr** work without 3d drivers?

this for an old lap with no 3d card

I'm typing this on an ancient Dell Latitude laptop (366mhz PII, 160meg of ram 2.5 meg vram), under Puppy, with xcompmgr giving me beautiful shadows under xfce, and it's running very snappily. I'm quite happy. Also, when I'm booted into Xubuntu on this 'book, I use its built-in compositing to get my shadows (how anybody can keep track of a screenful of windows without shadows is beyond me!), and, while it's a bit slower, due to all the behind-the-scenes goodies I have running, it is still quite usable. If fact, I can discern no difference in response, whether I have shadows on or off. 

I'm betting, however, that transparency would slow things down, but since I consider transparency to be a useless gimmick, I wouldn't know. :-)

-Jon

---

### Post by Bruce M. on 2008-05-29
> **joninkrakow said:**
> I'm typing this on an ancient Dell Latitude laptop (366mhz PII, 160meg of ram 2.5 meg vram), under Puppy, with xcompmgr giving me beautiful shadows under xfce, and it's running very snappily. I'm quite happy. Also, when I'm booted into Xubuntu on this 'book, I use its built-in compositing to get my shadows (how anybody can keep track of a screenful of windows without shadows is beyond me!), and, while it's a bit slower, due to all the behind-the-scenes goodies I have running, it is still quite usable. If fact, I can discern no difference in response, whether I have shadows on or off. 

I'm betting, however, that transparency would slow things down, but since I consider transparency to be a useless gimmick, I wouldn't know. :-)

-Jon

Hi Jon

Based on what you said above I downloaded xcompmgr to my Xfce (8.04) system but have no idea how to configure it. Any help would be appreciated.

Thanks
Bruce

---

### Post by joninkrakow on 2008-05-29
> **Bruce M. said:**
> Hi Jon

Based on what you said above I downloaded xcompmgr to my Xfce (8.04) system but have no idea how to configure it. Any help would be appreciated.

Thanks
Bruce

Yeah, I guess that would help, eh? :-) Sorry....

It's a commandline program, so you need to find a way to get it to launch at login. I find doing these things in Ubuntu a bit confusing, but maybe you can do it in the sessions manager.

Here's what I did. I created a new text file, and added this:

```

#!/bin/bash
xcompmgr -c -l -8 -t -8 -r 8 -o .72>/dev/nul &

```

I bit of explanation. These various switches set the shadow. I can't remember what they all do at this moment, but the -l -8 and -t -8 set the left and top offset, so the shadow is more to the right and bottom, and the -r 8 sets the radius to 8 (I believe these are all pixels). Those are the most important settings. The settings I chose are the closest I could get to OS X--but actually, what I was trying to get was a shadow that I felt didn't interfere, yet was visible. In the end, it looked like on my OSX box. :-)

btw, you can enter xcompmgr --help on the command line, and see a complete explanation of the various settings. Worth playing with to get what you want before committing it to your shell program.

Oh, to kill the program, I believe the command killall xcompmgr will kill it so you can reload it with new settings to test it. Once you like what you see, you can copy the whole command to your text editor, and use that for your shell file.

The end part, I suspect, simply routes any output to the stdout to never-never land, thus not clogging up stdout with its garbage. 

Now, once you have created this file, you need to save it, and give it executable privileges. I believe the terminal command is:
```

chmod -x /path/to/file/filename.sh

```

I would save this someplace "normal" and add it to the session manager. It should work then.

BTW, for the current session, you can enter the top command right in the terminal and see the effects right away. 

-Jon

---

### Post by Bruce M. on 2008-05-29
> **joninkrakow said:**
> Yeah, I guess that would help, eh? :-) Sorry....

Thanks for this ... I should have known it was command line and that --help will work or at least tried it.  :)

And (just tried it) so does
```
man xcompmgr
```

Got this saved as a TXT file now to look at later.

Thanks Jon.
Have a GREAT day.
Bruce

---

### Post by durand on 2008-05-29
You wouldn't actually need >/dev/nul & if you were going to add it to the session manager. Which is pretty simple, btw.

Go to *System* - *Preferences* - *Sessions*
Click on Add and Type in any name you want to call it; Xcompmgr will do. For Command, use: ***xcompmgr -c -l -8 -t -8 -r 8 -o .72*** or whatever you want. 
Then just press Ok and you're done.
When you next startup Ubuntu/Gnome, it will start that program.

---

### Post by Bruce M. on 2008-05-29
> **durand said:**
> You wouldn't actually need >/dev/nul & if you were going to add it to the session manager. Which is pretty simple, btw.

Go to *System* - *Preferences* - *Sessions*
Click on Add and Type in any name you want to call it; Xcompmgr will do. For Command, use: ***xcompmgr -c -l -8 -t -8 -r 8 -o .72*** or whatever you want. 
Then just press Ok and you're done.
When you next startup Ubuntu/Gnome, it will start that program.

And for Xfce (8.04) it would be:
Applications > Settings > Settings Manager > Autostarted apps.

I'm going to create a bash file (xcompmanager.sh) though as "Autostarted apps" doesn't allow for editing.

Then I'll create a few aliases:
```

alias xman='~/.xcompmanager.sh' # starts xcompmgr with preferred settings
alias kxman='killall xcompmgr' # kills xcompmgr
alias exman='gedit ~/.xcompmanager.sh' # edit xcompmgr's settings
alias ksxman='killall xcompmgr && ~/xcompmanager.sh' # kill and restart xcompmgr

```

We'll see how that works.

Yup, that works.  :popcorn:

Have a nice day.
Bruce

---

### Post by joninkrakow on 2008-05-30
[QUOTE=Bruce M.;5074360]And for Xfce (8.04) it would be:
Applications > Settings > Settings Manager > Autostarted apps.

And for LXDE??? I can't find it here! Maybe I need to boot into xfce? or will items set up there work in LXDE? 

I've got a startup file for icewm, but can't figure out what to do with LXDE.... still working on it, though.

-Jon

---

### Post by regomodo on 2008-05-30
> **spupy said:**
> You can try xcompmgr - only shadows and transparency.

Little offtopic: Who makes an eye-candy program and puts ONLY ONE 300x200 px screenshot on their website?

it's actually 1280x800px and i saw 2

---

### Post by durand on 2008-05-30
Oops, I forgot that you were on xfce. LXDE looks quite nice but I like gnome too much :P

---

### Post by saratchandra on 2008-05-30
> **durand said:**
> You wouldn't actually need >/dev/nul & if you were going to add it to the session manager. Which is pretty simple, btw.

Go to *System* - *Preferences* - *Sessions*
Click on Add and Type in any name you want to call it; Xcompmgr will do. For Command, use: ***xcompmgr -c -l -8 -t -8 -r 8 -o .72*** or whatever you want. 
Then just press Ok and you're done.
When you next startup Ubuntu/Gnome, it will start that program.

I tried that xcompmgr options and the shadows don't go away unless I refresh my desktop:( So I removed shadows completely. Only transparency for now.

I tried cairo composite manager too. It uses too much resouces and you can't disable certain features.

---

### Post by madjr on 2008-05-30
> **saratchandra said:**
> 

I tried cairo composite manager too. It uses too much resouces and you can't disable certain features.

yea the dev will be working on that.

it's only v0.1

he plans to get that done by v0.2

---

### Post by saratchandra on 2008-05-31
> **madjr said:**
> yea the dev will be working on that.

it's only v0.1

he plans to get that done by v0.2

Lets hope so:guitar:

---

