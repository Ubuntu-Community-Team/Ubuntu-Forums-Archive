---
title: "Gnome-Shell with llvmpipe support in Precise"
date: 2012-02-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lucazade on 2012-02-24
Is there any plan to include llvmpipe support for gnome-shell in Precise?

This allows to run gnome-shell on machines without 3D opengl extensions on board (i.e. virtual machines or machines with broken video drivers).
I've tested Fedora 17 nightly in virtualbox and on a Gma500 netbook and it is working great, unexpected fast.

here is a screenshot of a running virtualbox

---

### Post by tista on 2012-02-24
> **lucazade said:**
> Is there any plan to include llvmpipe support for gnome-shell in Precise?

This allows to run gnome-shell on machines without 3D opengl extensions on board (i.e. virtual machines or machines with broken video drivers).
I've tested Fedora 17 nightly in virtualbox and on a Gma500 netbook and it is working great, unexpected fast.

here is a screenshot of a running virtualbox

Hey Luca ! 

What a nice plan you suggest !! :)

Yeah llvmpipe could do such trick on damned GPU drivers. so fedora 17 already improved this? if so, Ubuntu must do as well...

Ciao,
Tista

---

### Post by lucazade on 2012-02-24
> **tista said:**
> Hey Luca ! 

What a nice plan you suggest !! :)

Yeah llvmpipe could do such trick on damned GPU drivers. so fedora 17 already improved this? if so, Ubuntu must do as well...

Ciao,
Tista


Ciao Tista!

Yep, fedora 17 nightly already provides llvmpipe by default, enabling this way gnomeshell as default fallback session.
Don't know yet if related only to gnomeshell version (3.3.5) or there are other optimizations under the hood. Must investigate.
Nice thing is that animations and cool effects like transparencies are active like when employing gnomeshell in a opengl env.
Give it a try and let me know.

---

### Post by dino99 on 2012-02-24
can already be tested via ppa on Ubuntu : [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)

---

### Post by lucazade on 2012-02-24
> **dino99 said:**
> can already be tested via ppa on Ubuntu : [https://launchpad.net/~oibaf/+archive/graphics-drivers]("https://launchpad.net/%7Eoibaf/+archive/graphics-drivers")


oh.. interesting..
I'm going to give it a try :)

---

### Post by dino99 on 2012-02-24
Gentoo guys also play with llvm/gallium
[https://forums.gentoo.org/viewtopic-p-6946148.html](https://forums.gentoo.org/viewtopic-p-6946148.html)

---

### Post by lucazade on 2012-02-24
Bingo! Bravo Dino!

here is gnome-shell running in virtualbox with the llvmpipe sw renderer..  unfortunately it doesn't start from lightdm as a standard gnome session, probably because I've wiped some .session files, need to check.. 
so I've started it from terminal with a gnome-shell --replace

---

### Post by dino99 on 2012-02-24
> **lucazade said:**
> Bingo! Bravo Dino!

here is gnome-shell running in virtualbox with the llvmpipe sw renderer..  unfortunately it doesn't start from lightdm as a standard gnome session, probably because I've wiped some .session files, need to check.. 
so I've started it from terminal with a gnome-shell --replace

oh, good news, looks like the beginning of a new story :) and some tweaks for the week-end :)

---

### Post by lucazade on 2012-02-24
there are some glitches using gnome-shell in virtualbox using the ppa.. menus and windows produce a lot of artifacts.

fedora 17 instead works better, without glitches, probably llvmpipe and friends are newer.
I tried also to update gnome-shell to 3.3.9 using gs/gnome3 testing ppas but didn't help.

there is also a problem starting gnome-shell session from lightdm.. it fails to detect 3D accel:
```
gnome-session-is-accelerated: No hardware 3D support
gnome-session-check-accelerated: Helper exited with  code 256
gnome-session WARNING: Session 'gnome' runnable check failed.
```
it probably requires some more patches.. atm the only way is to start gnome-shell from another working session via terminal.

---

### Post by tista on 2012-02-25
> **lucazade said:**
> there are some glitches using gnome-shell in virtualbox using the ppa.. menus and windows produce a lot of artifacts.

fedora 17 instead works better, without glitches, probably llvmpipe and friends are newer.
I tried also to update gnome-shell to 3.3.9 using gs/gnome3 testing ppas but didn't help.

there is also a problem starting gnome-shell session from lightdm.. it fails to detect 3D accel:
```
gnome-session-is-accelerated: No hardware 3D support
gnome-session-check-accelerated: Helper exited with  code 256
gnome-session WARNING: Session 'gnome' runnable check failed.
```
it probably requires some more patches.. atm the only way is to start gnome-shell from another working session via terminal.

@Luca

Yeah I could agree with your opinions... :)
So I saw some patches in fedora17, and I think the key would be "cogl" you know.

ASAP I would open branch to polish cogl to fit our beloved Poulsbo. I've already started some ugly patchworks for cogl to run llvmpipe better and better... ;)

Ciao,
Tista

PS:
Still I stuck with Oneiric and emgd-1.10, but today I could run mutter with llvmpipe. even though it seems toooooooo slowly?! :P

---

### Post by lucazade on 2012-02-25
> **tista said:**
> @Luca

Yeah I could agree with your opinions... :)
So I saw some patches in fedora17, and I think the key would be "cogl" you know.

ASAP I would open branch to polish cogl to fit our beloved Poulsbo. I've already started some ugly patchworks for cogl to run llvmpipe better and better... ;)

Ciao,
Tista

PS:
Still I stuck with Oneiric and emgd-1.10, but today I could run mutter with llvmpipe. even though it seems toooooooo slowly?! :P

Great my friend :)

Googling here and there I've found a [thread]("http://www.fedoraforum.org/forum/showthread.php?p=1525316") on the fedora forum about GS and llvmpipe and a [wiki]("http://fedoraproject.org/wiki/Features/Gnome_shell_software_rendering") page of the current implementation. Maybe there is something interesting.

About performance it seems fast on a virtualbox machine (host is enough powerful.. i7, 8gb ram and nvidia 550 1gb) and pretty decent on the gma500.

This extension for gnome-shell could improve speed..
[https://extensions.gnome.org/extension/119/disable-window-animations/](https://extensions.gnome.org/extension/119/disable-window-animations/)

and also disabling vsync:
echo "export CLUTTER_VBLANK=none" | sudo tee -a /etc/environment

I expect btw other enhancements in both llvmpipe gallium and gnome-shell as well.

let me know if I can help or test cogl new stuff ;)

---

### Post by tista on 2012-02-25
Dear Luca.

Now I'm examing this patch:
[http://paste.ubuntu.com/856619/]("http://paste.ubuntu.com/856619/")

And screenshot of my VAIO typeP running with Oneiric and EMGD-1.10.
[screenshot]("http://img820.imageshack.us/img820/7736/screenshotat20120226000.png")

gs seems to score damned highly CPU usage 30% to 90% in usual?! X( oh god...
Now cogl-1.9.7 was applied with that patch, but it didn't get performance.

Or should I take psb_gfx instead of emgd?

Ciao.

---

### Post by lucazade on 2012-02-26
Cpu usage is high here as well.. it looks like it needs some more love :)

....on fedora instead is quite low, there is something different

---

