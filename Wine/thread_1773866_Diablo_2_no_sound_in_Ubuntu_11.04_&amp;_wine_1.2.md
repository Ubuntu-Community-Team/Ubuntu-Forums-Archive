---
title: "Diablo 2 no sound in Ubuntu 11.04 &amp; wine 1.2"
date: 2011-06-02
forum: Wine
---

### Post by Clicksights on 2011-06-02
Well just had my first day with wine today.
I dont drink it, but i do feel like starting to drink a double cuba libre right now.... #-o

I felt like gaming, and wanted too make a start using wine.
I been addicted to Tux Karting and frozenbubble too long :p . 
So for old times sake i tried too install Diablo 2.

Installed wine via the software mananger.
Installed wine tricks via the software manager
Started Wine tricks and installed Diablo 2 from original cd's.
So the patch for no cd etc. is installed automatic.

Everything went okay so far...
I can even start the game without the cd's, it works! Seems Wine works fine!
(This is very important since i and some of my friends all still have the original Diablo cd's.... i also have too install it on an MSI x340 and a MSI u100 and those have no cd drive!)

But no sounds... 
Appart from the menu button for choosing a caracter... 
Also the movies worked, but no music and no sounds or speech in the game!

I tried al kinds of things, but no sound! I tried emulate in wine config, tried all drivers etc.
Also if i try the test sound button there is no sound.

I surfed the web whole day for a solution, but couldnt find one...
Does some one have a solution?
I really need an solution, for i am the one installing ubuntu on all laptops/pc's i get my hands on...
and try to convince, ehh force ;) all my friends to at least do a dual boot with M$....

info:
ubuntu 11.04
wine 1.2 
wine tricks 
msi gx-620 with NVida 9600 Game laptop ( i know its overkill for this game ;)
 
Thankx!

---

### Post by disabledaccount on 2011-06-02
Switch sound driver to software emulation, ensure that sound test works in winecfg.

Besides I'll recomed You to add wine ppa to Your repositories and upgrade to latest version.

---

### Post by Clicksights on 2011-06-02
Hello tomazzi.

I did switch to emulate, but no sound.
Not in the test not in the game.

I can try updating to an newer version, if there is,
i now use the one from the software center.

Any other tips?

Thankx

---

### Post by disabledaccount on 2011-06-02
What sound driver is selected in winecfg? It should be Alsa. If this is correct, then install gnome-alsa-mixer and check for disabled/muted devices. Secondary, I suggest to use (very convenient) "PulseAudio Device Chooser" and disable "simultaneous output mode" in pulseaudio server config.

Wine 1.2 is rather old - it is marked "stable", but in case of WINE this term is misleading, so normally it's better to at least try newest version.

---

### Post by Clicksights on 2011-06-02
thankx again, and i fixed it, :D since i used wine tricks, there was no profile for it in wine, but in wine tricks.
I changed to emulate in wine tricks and voila...sound! :p

so problem solved in record time! wish i had that idea before!
Thankx for the info though, i will try the new release soon, first gone try to install it somehow without the cd.

you dont happen too know a way to make the resolution 1024 without getting a small virtual window?
;)

---

### Post by disabledaccount on 2011-06-02
> **Clicksights said:**
> 
you dont happen too know a way to make the resolution 1024 without getting a small virtual window?
;)Have you tried MultiRes patch (unofficial)? :)

---

### Post by Clicksights on 2011-06-03
Hi again Tomazzi,

after 6 hours of play time in single player done by my friend, i can confirm it works perfect. ( havent had a change to play it myself longer than 5 minutes LOL.)
But i/we do miss the LOD expansion, i tried installing it, but seems i can get it done...yet...

any advice is welcome, since i installed Diablo without a problem with wine tricks,
( its now running on the x340 too! :) ) i dunno yet how to install it manually.
the LOD is a seperate cd, also original one.
If i put it in the external cd/dvd player it does show up on my desktop,
but how do i run it and install it? (I tried playonlinux that didn't work either)
Or is there such a wine trick script for lod expansion?

info:
ubuntu 11.04
wine 1.2 
wine tricks 
msi gx-620 with NVida 9600 Game laptop &
msi x340 :P

havent tried the high resolution yet.... too busy with helping others...
Installing ubuntu on a friends samsung laptop, wipe-ing a hdd for another friend and making booteble usb with ubuntu for another friend all while trying to catch some meat off the BBQ...:P

---

### Post by disabledaccount on 2011-06-03
I have separate expansion disk too, but I haven't any problems with installing LOD. Can You tell what exactly is hapening when You launch the installer?

---

### Post by Clicksights on 2011-09-26
so sorry i didn't get back sooner!

I haven't had a chance to try yet, i was hoping to find another winetricks script for the LOD cd.
;)

But since i have a new laptop, hehe a bigger brother form my MSI Wind netbook,
a MSI X460DX i have been very busy making my optimus video card work, tweaking the install etc.
And i was installing a friends MSI X340, with no windooz just ubuntu, trying to do my part in spreading the good OS! 
Than i found playdeb, and tried several games...
Currently installing ubuntu on 2 MSI 350's for my new employer, who is going to switch to ubuntu and open source, after my input! :p So proud!

hehe and the weeks fly by....

---

