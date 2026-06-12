---
title: "Eye candy, hardware support, and 2d effects"
date: 2007-01-01
forum: The Cafe
---

### Post by NoWhereMan on 2007-01-01
I was so excited and all when I heard about Compiz for the first time.

I was struggling against xcompmgr which was so SLOOOOW on my old laptop, and which was a little slow on my p4 1.6 too :/ , when I saw that magic Novell screencast. "It'll have to take a super 3d-graphics-capable pc" I thought; I was surprised when they told me it would have run on a "low-end hardware" too.

Great, but my laptop was old and I wasn't expecting its "ProSavage" graphic card to be "xgl-enabled" (let me use this term). Unfortunately I was right; mesa driver didn't support some "visuals", and so I had to just forget about it in the short term.

Some time later, I bought a new laptop. I didn't care enough about the graphic card; the choice was between a scarcely reliable branded laptop with an ATi card, and a nice Packard Bell using a not well advertised one, which then I came to know was a VIA "Unichrome".

Well. I'll let you imagine. Neither this brand new laptop was supported. Moreover the mesa driver lacks a maintainer. ](*,) 

Yeah. This sucks.

But that's not the point. 

**Isn't all this gl-enhanced-xserver making devs forget about less-supported hardware?** 

I mean, I know, that's not the most important thing for an OS; it just have to work, at least; and a command line junkie won't mind about wobbly windows (neither do I :D I'd like shadows, btw; and transparency may help). 

**But why do they just dumped any support to a good old 2d compositing?** Actually the OS X interface is almost 2d; *shadows* are 2d; why do we need an entire OpenGL core just to have a little more shiny-ness on our desktops? Things that both mac users and windows users already can have? And I'm not talking about Vista's Aero; Win XP already has alpha compositing.

Why nobody works on an xcompmgr alternative? **Why don't they fix at least the gnome shutdown panel bug ?** :( [1]

Of course, keep in mind that if I had an ati or an nvidia card I would never mind about non supported hardware :D

btw, just a thought; share yours :)

[1] Yesterday I was trying to write a stupid zenity-based dialog to substitute gnome's shutdown panel so that I can use xcompmgr without having to loose all the lock, shutdown, reboot options (I know already all of the workarounds; I'd like to find a *solution*) :D

---

### Post by Valinski on 2007-01-01
I dont know too much about the ins and outs of this business but im guessing it the old "Majority Rules" and as the majority seem to want shiny spankey computers, then thats what the people at the programming end will give. 

Im sorry i know thats no help ;)

---

### Post by Nonno Bassotto on 2007-01-01
Are you sure you're using the correct drivers? As far as I know Mesa are generic drivers, but there should be more specific drivers for your graphic card. At least I'm sure that they exist fro Savage cards, don't know about your ProSavage.

About using 3d capabilities of your motherboard to draw a 2d desktop: why do you think xcompmgr was so slow? ;)

---

### Post by NoWhereMan on 2007-01-01
> **Valinski said:**
> I dont know too much about the ins and outs of this business but im guessing it the old "Majority Rules" and as the majority seem to want shiny spankey computers, then thats what the people at the programming end will give. 

Im sorry i know thats no help ;)

no probs; I just wanted to open a debate, not to save the world :D

> **Nonno Bassotto said:**
> Are you sure you're using the correct drivers? As far as I know Mesa are generic drivers, but there should be more specific drivers for your graphic card. At least I'm sure that they exist fro Savage cards, don't know about your ProSavage.

I don't have the (pro)savage (driver is the same) anymore. Now it's Unichrome
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus)

> About using 3d capabilities of your motherboard to draw a 2d desktop: why do you think xcompmgr was so slow? ;)
it's not :/ and, btw, why then OS X and XP aren't that slow?

---

### Post by Patrick-Ruff on 2007-01-01
bah, there are some real problems here.  ATI users are HARDLY supported at all.  we are forced to use the FGLRX drivers (except those lucky few who can use the open source drivers with no issues), and FGLRX does not support AIGLX (which is built into xorg 7.1 rather then XGL; which runs on top of it.) I find it quite ridiculous that fglrx doesn'te ven support aiglx.  I don't have a clue what ATI is thinking here, they are using a lot of business because of this.  ATI users are switching to nVidia because nVidia is the most compatable with everything.  nVidia cards are the only cards you will see right now running all that awesome eye candy without losing a ridiculous ammount of global operating system functionality.  Aiglx allows you to do so much more then XGL which is very unstable, doesn't allow a lot of other 3d-related stuff because it conflicts with it, and it's just really messed up. 

I think I've made my views clear enough on this, I am a frustrated user who has an ATI laptop, and it doesn't appear to be really fully compatable with any system other then bloody Windows . . . it got close with ubuntu, but then I have an ATI card. . . .

---

### Post by Lord Illidan on 2007-01-01
Meh, just switch to Nvidia.

*Inserts gratuitous beryl-screenshot here  to make  them feel jealous*

---

### Post by NoWhereMan on 2007-01-01
hard to do, on a laptop

---

### Post by Lord Illidan on 2007-01-01
> **NoWhereMan said:**
> hard to do, on a laptop

I feel for ya man. But until the other Graphics card manufacturers release their drivers either under OSS or propietary licences for Linux, then it will be hard to release Beryl/Compiz/XGL/AIGLX for them.

---

### Post by Patrick-Ruff on 2007-01-01
I feel your pain!!!! bah. it is so frustrating to have an incompatable laptop and not have anything to do about it . . . yours is more incompatable then mine is but it's still not too much different, the only way I can use beryl is through XGL, and I'd rather not use beryl if I have to use XGL with it . . . .

---

### Post by mushroom on 2007-01-01
> But why do they just dumped any support to a good old 2d compositing? Actually the OS X interface is almost 2d; *shadows* are 2d; why do we need an entire OpenGL core just to have a little more shiny-ness on our desktops? Things that both mac users and windows users already can have? And I'm not talking about Vista's Aero; Win XP already has alpha compositing.

OS X has used OpenGL for compositing since Jaguar, it's just a bit more discrete about it. I would attribute the slowness of Beryl in 2D operations to the fact that it doesn't have an entirely vector-based UI to work with, and the fact that it's still pretty beta. 2D compositing isn't the way to go, because there's no benefit if it's not hardware accelerated. In the long run, it would be way too slow. Look at OS X pre-10.2, and you'll see what I mean.

I have faith in the Ubuntu devs to make the integration with the UI and performance of Beryl/Compiz more acceptable in the next release. The only real problems with it now is dealing with fullscreen video and other OpenGL operations.

As for dropping support for 2D composition, it was never really supported in the first place. XCompmgr was really just a test, not to mention that development is all but dead, and KWin's Kompmgr is probably going to be replaced with an OpenGL composite manager in KDE 4.

All that said, I wish there was a glxcompmgr. I know there was one once, but it wasn't really anything more than a proof-of-concept. XCompmgr's eyecandy is understated and it all integrates much more gracefully with the native WM/DE. Hardware-accelerated, it would be absolutely perfect.

---

### Post by Lord Illidan on 2007-01-01
The only problem with Beryl and all the others is resources. Beryl takes up a heck of a lot of resources. Now whether it is because it is alpha software I don't know, but it could be improved.

---

### Post by NoWhereMan on 2007-01-02
> **mushroom said:**
> All that said, I wish there was a glxcompmgr. I know there was one once, but it wasn't really anything more than a proof-of-concept. XCompmgr's eyecandy is understated and it all integrates much more gracefully with the native WM/DE. Hardware-accelerated, it would be absolutely perfect.

yep, I am with you. I guess that if they worked on something like that, there would be even support for less-supported graphic cards as mine is; heck is just a couple of shadows what I want; I don't need wobble :P

btw, at the moment, if the gnome shutdown panel bug was fixed I would be happy with xcompmgr as well (setting gstream-properties not to use Xw - whatever it is :D - videos work like a charm, too; and I have no problem with OpenGL games)

bye

EDIT:
~/.gnomerc :
> export LTSP_CLIENT=1

now shutdown dialog works :)

EDIT2: LTSP_CLIENT let the shutdown dialog work, but brigns with that a lot of drawbacks (no more eject command in removable drives desktop icon, for instance) so I'd say that's not a good workaround...

---

### Post by Kevin on 2007-01-23
The problem with xcompgr though, other than its instability, is that its extremely slow unless the driver you are using supports composite acceleration.  But then, I can't think of a single driver that supported composite acceleration but doesn't support opengl acceleration.

As far as glxcompmgr goes, well that was essentially compiz, but they decided to import a lot of metacity's window manager code and make it a full fledged window *and* compositing manager.  The reasoning behind this is because its impossible to do many of the effects without changing the wm code.  (such as minimize, when you press minimize, metacity stops drawing the window, but then glxcompmgr had nothing to use for a minimize animation)  Also, glxcompmgr needed the same stuff compiz requires, so it really doesn't help much there...

The shutdown dialogue bug doesn't happen anymore with compiz in feisty for me, so maybe in feisty it will work with xcompmgr too.  And opengl games work fine in aiglx.

As far as hardware support goes, well right now, any nvidia card after like geforce 1 or 2 (can't remember the cutoff for the legacy driver) works perfectly.  Ati open source drivers work beautifully for me (mobility 9600) and should work for the whole 9xxx series, most  of the Xxxx series, and support for the X1xxx series seems to be on its way, so I wouldn't say its horrible for Ati.  Every Intel card works well.  I'd say that makes up quite a lot of the current market, especially considering Intel themselves make up more than Ati and nvidia combined as far as marketshare goes.

The situation can only get better :)

---

### Post by NoWhereMan on 2007-01-23
yeah but no via or sis ](*,)

---

### Post by Amaranth on 2007-01-23
What do you expect from such a cheap card?

---

### Post by NoWhereMan on 2007-01-23
> **Amaranth said:**
> What do you expect from such a cheap card?

[sarcasm]
What would *you* expect from such a cheap **comment** ? :D
[/sarcasm]

sorry, I couldn't resist :lolflag:

It's not (only) the card to be poor, but the support... (but my critic is not about this)

---

### Post by Mathiasdm on 2007-01-23
> **NoWhereMan said:**
> yeah but no via or sis ](*,)

I'm in the same boat here :( But next time, I'll just look for a computer with a supported graphics card (and a supported wireless card, for that matter!).

---

### Post by NoWhereMan on 2007-01-25
the answer? [http://www.mandriva.com/en/projects/metisse](http://www.mandriva.com/en/projects/metisse)

---

### Post by timpino on 2007-01-25
Two questions, one off topic and one kinda on topic...

What's the difference between beryl and compiz?

I have a GeForce 440 Go will I be able to get the cube working? or is this a to old card? And I can find info about supported Desktop cards but not about laptop adapters, whats up with that?

Maybe a beryl-light or something should be created for us with old cards with just the cube and shadows?

---

### Post by Mathiasdm on 2007-01-25
> **NoWhereMan said:**
> the answer? [http://www.mandriva.com/en/projects/metisse](http://www.mandriva.com/en/projects/metisse)

Not for me ;)

[quote=Metisse FAQ]Do I need a high-end 3D graphical card to use metisse?
No. Metisse uses basic openGL commands for most of its feature and can run on entry level 3D graphic cards. For instance, metisse is able to run (slowly) on PIII 450Mhz with TNT2 graphical chipset.[/quote]
My graphics card can do 3D, but not in Linux ;)

I hope yours is better!

---

### Post by Aetherius on 2007-01-25
I suffered with an Integrated Via S3 Unicrome for a long time. SIS are satan spawn, this is not just a linux problem, the support for SIS/Via cards is terrible on anything other than OEM windows pre-installed. Years ago I spent weeks trying to get drivers for the card on a fresh windows installation. (when I was a windows man I took to the habit of carrying ALL my drivers on a flash drive after this incident)

Thank god thats far behind me.

I eventually got fed up with SIS on linux and bought a GeForce 6300 for cheap cheap.

:D


Aeth

---

### Post by prizrak on 2007-01-25
AIGLX works with nVidia and Intel cards (together that covers about 70% of the market). Some ATI cards can do AIGLX with open drivers others can do XGL with FGLRX driver. The less supported hardware you are talking about is barely 1% of the market and as such isn't really viable for support (not to mention it's much harder to get your hands on one for testing).

Another thing you are forgetting is that Beryl/Compiz are basically Window Managers that are capable of OpenGL compositing. KDE/Gnome use their own WM's that are not capable of either 2D or 3D compositing. Enlightenment does 2D compositing pretty well and is actually quite quick about it. 

It basically all comes down to the focus of the project. Beryl/Compiz are trying to create a WM that could rival Vista/OS X with 3D effects. Gnome/KDE are all about providing a nice GUI to work with. XGL is all about providing a fully OpenGL X server.

---

### Post by NoWhereMan on 2007-01-25
> **Mathiasdm said:**
> Not for me ;)


My graphics card can do 3D, but not in Linux ;)

I hope yours is better!

I've tried the livecd and it works with VESA :D:D:D (SLOW AS HELL)

EDIT: [http://www.ubuntuforums.org/showthread.php?p=2062766#post2062766](http://www.ubuntuforums.org/showthread.php?p=2062766#post2062766)
well.. it works... not as much integrated as beryl, btw... I wish they could add it to feisty!

---

### Post by prizrak on 2007-01-25
Feisty has pretty good Beryl support even though it's beta. Beryl isn't taking much resources on my box not sure why it would for others. Currently it's using about 10MB of RAM and 0% CPU. Battery life is also not impacted (this is AIGLX not XGL) it's 10 minutes less than Windows, which is normal for nVidia cards on Linux because of lack of GPU throttling.

---

