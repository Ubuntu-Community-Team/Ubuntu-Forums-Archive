---
title: "Frets on Fire (Guitar Hero clone)"
date: 2007-04-11
forum: The Cafe
---

### Post by SishGupta on 2007-04-11
I just came across this amazing open source Guitar Hero clone today.
It isn't new but it is new to me, and I thought I would share it.

It is called "Frets on Fire" and it is really quite fun. The main website is down, but here is the [source forge page]("http://sourceforge.net/projects/fretsonfire/") with Linux, Win32, and OSX binaries and source code! It is written in python if you want to develop for it and it is also mod-able.

[URL="http://digg.com/playable_web_games/An_open_source_Guitar_Hero_based_PC_game_for_Windows_and_Linux"]
Digg article with torrent links to download packs[/URL]

The guitar hero 1 songs are also in a torrent in the above mentioned digg article, but that isn't free or legal so downloader beware.

:guitar:

---

### Post by TravisNewman on 2007-04-11
Does it work with the guitar controller if you have a Playstation to USB adapter?

---

### Post by hardyn on 2007-04-11
there is a thread... 'best software you have never head of' or something to that effect... it has been there a few times...

yes FOF is a great game, but it needs more songs!  im getting bored with the ones i have, and im not good enough to play it on expert... hard is hard enough... i can ace most levels on easy.

have fun.

---

### Post by hardyn on 2007-04-11
> **panickedthumb said:**
> Does it work with the guitar controller if you have a Playstation to USB adapter?

i think so... they sell a USB guitar... i don't see how yours would be any different than that.

---

### Post by SishGupta on 2007-04-11
> **panickedthumb said:**
> Does it work with the guitar controller if you have a Playstation to USB adapter?

I don't know about the guitar in linux but it does work in windows. 
I don't own any of the guitars and that is why I don't know.
That said I am sure one could make it work if they had any knowledge with drivers (which I dont)

@hardyn
In the 2nd link i posted there are over 400 songs...

---

### Post by hardyn on 2007-04-11
frets... or frets and songs?

thanks!

---

### Post by mick0142 on 2007-04-12
the usb to playstation2 converter works, i just can't remember how, i THINk it was a driver issue.

if anyone can help with this, that would be great. i had it working at one time.

---

### Post by buttons on 2007-04-13
> **panickedthumb said:**
> Does it work with the guitar controller if you have a Playstation to USB adapter?

Why yes, yes it does.  /me looks at guitar with adapter he's been playing on all day

It was literally plug and play.  I fired up jstest after plugging in, and (nearly) everything works perfectly.  Even tilting the guitar presses button 4!  The only thing that *doesn't* work is the whammy bar, which is not fed through the adapter.  Bummer.  This is apparently a known problem which I'm too lazy to cite now, so it's not just my adapter.  If you're curious check the FAQ on the FoF site.

You can check the [Stepmania USB Adapters List]("http://www.stepmania.com/wiki/USB_Adapters") for ones that work.  Keep in mind to play GH you don't need to have an adapter that doesn't get confused when UP and DOWN are pressed at the same time (obviously a problem with DDR clones).  Unless, of course, you want to play DDR with a playstation pad ever...but I digress.

You can get them for about $8 on ebay (and they support two controllers + ddr!) or for $12 in radio shack.  RS appears to be the only brick and mortar store that carries them.

Best buy carries (wired) guitars for $40 each.  It's tough to find a better deal on a wired guitar, but you can do better than the $60 for a wireless one.

For the record I'm on a Rock Guitar II with the Playstation->USB adapter from the shack.

---

### Post by tqft on 2007-04-16
Has anyone seen or made a deb package of it?

I am downloading now 1.2.451 (released 15 April 2007) to see if I can get it too work - earlier versions keep crashing.

Some of the error messages suggest adjusting - turn anti-aliasing off but how?

---

### Post by ceil420 on 2007-04-16
Man I tried to get FoF, but I don't think my computer can take it. Odd, cos it's not like I'm on an ancient box or anything. But I started the game, and never got past the initial (orange/yellow) loading screen with the annoying repetetive music -_- I gave it like ten minutes before pushin' the power button on my computer, cos I couldn't alt+f2 to xkill it or anything :x

Shouldn't this computer be able to play it?

uname: Linux 2.6.17-11-generic
Distro: Xubuntu Edgy
CPU: Intel(R) Pentium(R) 4 CPU 1.70GHz 1695.254 MHz
Bogomips: 3394.71
Mem: 187/503M [||||||||||]
Diskspace: 91.34G Free: 72.29G
Graphic: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
Screen: 1280x1024 (32 bpp)

---

### Post by buttons on 2007-04-16
> **tqft said:**
> Has anyone seen or made a deb package of it?

I am downloading now 1.2.451 (released 15 April 2007) to see if I can get it too work - earlier versions keep crashing.

Some of the error messages suggest adjusting - turn anti-aliasing off but how?

Settings->Video Settings->Antialiasing quality

---

### Post by mchaggis211 on 2007-07-03
is ther a .deb for the newset verison of this game or even better a whole repo including the songs and the core files

---

### Post by macogw on 2007-07-04
> **tqft said:**
> Has anyone seen or made a deb package of it?

I am downloading now 1.2.451 (released 15 April 2007) to see if I can get it too work - earlier versions keep crashing.

Some of the error messages suggest adjusting - turn anti-aliasing off but how?

You can get it from the Debian repos.  [Game](http://packages.debian.org/unstable/games/fretsonfire-game) & [songs](http://packages.debian.org/unstable/games/fretsonfire-songs-sectoid) are needed.  There's a meta-package [here](http://packages.debian.org/unstable/games/fretsonfire) that you may want to install after those are in to make it easier to uninstall..though when I think about it, that might not actually work since they'd be marked manually installed....Whatever, you need the first 2.  They'll work on Feisty, and I don't know about Edgy, but probably not Dapper.

---

### Post by hokiejp on 2007-07-20
> **ceil420 said:**
> Man I tried to get FoF, but I don't think my computer can take it. Odd, cos it's not like I'm on an ancient box or anything. But I started the game, and never got past the initial (orange/yellow) loading screen with the annoying repetetive music -_- I gave it like ten minutes before pushin' the power button on my computer, cos I couldn't alt+f2 to xkill it or anything :x


I had this same problem.  When I started the game a second time, it went to the menu just as it should.  Its just a bug the first time some people start the game.  Also, just a tip - if your pc freezes up like that, you can sometimes get it back by hitting ctrl-alt-backspace.  This kills your X session and brings you back to the login prompt.  All your programs die, but it's better than the power button.

> **ceil420 said:**
>  Shouldn't this computer be able to play it?

uname: Linux 2.6.17-11-generic
Distro: Xubuntu Edgy
CPU: Intel(R) Pentium(R) 4 CPU 1.70GHz 1695.254 MHz
Bogomips: 3394.71
Mem: 187/503M [||||||||||]
Diskspace: 91.34G Free: 72.29G
Graphic: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
Screen: 1280x1024 (32 bpp)

You should be able to play it no problem.  When I first ran it, I had awful flickering so bad I couldn't play the game.  I installed the nvidia-glx package (binary drivers from nvidia for OpenGL) and enabled them, and it worked like a charm.

---

### Post by %hMa@?b&lt;C on 2007-07-20
what is all this talk of needing the guitar controller.  I have my telecaster for when I want to play guitar and my model M for when I want to play FOF! ;)

---

