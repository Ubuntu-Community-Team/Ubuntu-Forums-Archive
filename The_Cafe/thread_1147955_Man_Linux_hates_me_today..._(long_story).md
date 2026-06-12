---
title: "Man Linux hates me today... (long story)"
date: 2009-05-03
forum: The Cafe
---

### Post by Brainy142 on 2009-05-03
Well I booted into my Mandriva installation (man Mandriva sucks crashing, took 4 GIGS, (like wtf) and decided to partition the drive into 5 partitions:confused:..... for no reason.... Sigh)

Well I booted up to do some Homework and guess what NOTHING usb would mount BLARG!!! #-o Well I rebooted, tried other devices and decided screw it I'm switching.:D

Then I decided why not try deban and choose dream linux.... (looks pretty and had apple bar thingy)

well..... erm.... It installed pretty dam fast and I was happy.... Untill the reboot...
It decided no I'm not going to work and said SDA1 could not be mounted due to specal features (WTF.....). then had error code 201.:shock:

Tried again and it failed... ](*,)

Then I said beep it I'm going back to ubuntu.... (which got nuked when pclinux OS COMPLETELY nuked my computer..... a while ago)

Booted the linux net install everything installs happly until i get to choose the packages I wanted. I thought if I pressed enter it would install what was currently selected and let it do stuff.... Well I was wrong and just ended the thng saying I'l just use the GUI package manager to install what I wanted..... BAD MOVE....#-o


Reboots and then I realized I...... Didn't have a GUI..... BLARG!!!!!!!!!!!!!!!!!! BLARG!!!!!!!!!!!!! BLARG!!!!!!!](*,)

Then I thought hmm.... whats that thing that I read before (I have never secsessfully used the terminal in mandriva as it was stupid)
and then I typed in apt get gnome .... Now it is installing and I'm hopeing it will then reboot and give me a freaking GUI....

I hope it auto configures....[-o<

---

### Post by MaxIBoy on 2009-05-03
Yeah, you'll probably get *something* out of it.

Handy tip:

If you install GNOME, restart, and then it kicks you into a terminal, just run the command "gdm," (or maybe "sudo gdm," I can't remember which,) to start GNOME manually.



Also, if everything is just goin' catastrophic at once, maybe it's your actual computer.

---

### Post by sandyd on 2009-05-03
> **MaxIBoy said:**
> Yeah, you'll probably get *something* out of it.

Handy tip:

If you install GNOME, restart, and then it kicks you into a terminal, just run the command "gdm," (or maybe "sudo gdm," I can't remember which,) to start GNOME manually.



Also, if everything is just goin' catastrophic at once, maybe it's your actual computer.

its
```

sudo gdm
```

---

### Post by Dngrsone on 2009-05-03
You know, that's what I'm thinking-- you have hardware issues, buddy.  Likely the hard drive, though I wouldn't doubt the memory being bad.

How about booting the Live disk and running memtest86+ on that bad boy, at least you'll be able to verify your RAM.

---

### Post by Brainy142 on 2009-05-03
Erm..ok the pclinux os thing was a long time ago (I was installing a package it crashed grub and everything got nuked....

usb thing just started today (not fryed as it is what I USED to install everything.

Right now it is configureing everything have a good day I'm going to fix this tommorrow

only thing that REALLY suck about linux for me is no 3d support (due to having a crappy onboard VIA.... I coundn't get that DMA or whatever to work as termonal (in Mandriva) kept denying me sudo (It evan said "what is sudo" lol)

thanks for the tip foe gnome though.

---

### Post by Brainy142 on 2009-05-04
I'm running a memtest86 now :D.
So far no errors...
Oddly my 1 core processor has 2 caches old AMD FTW:P

Good news: 
Memtest86 has no errors :P
I have a sort of gui.....................

bad news: I have no menus just a screen with the deban logo???? 
It starts ubuntu with one error something about usr tmp exits or somethink???


I really need a menu :( (I like my GUI's)

ps: why in the installer it told me not to start my user name with a capital???

---

### Post by Dngrsone on 2009-05-04
> **Brainy142 said:**
> I'm running a memtest86 now :D.
So far no errors...
Oddly my 1 core processor has 2 caches old AMD FTW:P

Good news: 
Memtest86 has no errors :P
I have a sort of gui.....................

bad news: I have no menus just a screen with the deban logo???? 
It starts ubuntu with one error something about usr tmp exits or somethink???


I really need a menu :( (I like my GUI's)

ps: why in the installer it told me not to start my user name with a capital???

I'm glad to hear that you RAM seems to be working.  We'll need specifics on the errors in order to figure that out.

As for the user name, that's a limitation imposed by one of the security protocols, as I recall.  I heard that this may be solved in Jaunty (9.04), but I may be mistaken.

---

### Post by MaxIBoy on 2009-05-04
Did you try booting in single-user mode (AKA recovery mode) and selecting the "repair X display" option?

---

### Post by LowSky on 2009-05-04
What is sudo...lol

um but many distros dont use Sudo, some need it to be installed or enabled

---

### Post by MaxIBoy on 2009-05-04
He's talking about Ubuntu specifically here.

---

### Post by Brainy142 on 2009-05-04
Good news everyone... you know that time I pressed enter...... well.... erm..... I didn't install a DESKTOP ROFL!!! I thought if I installed Gnome it would do it automatically but.... erm that failed.... and gave me some stupid error (256)...

Well I'm trying again a complete re-installation I hope it works...

---

### Post by hatten on 2009-05-04
why not do a simple clean install from a "normal" ubuntu CD, it is kinda impossible to fail with that one.

---

### Post by dragos240 on 2009-05-04
Perhaps you could try arch. If you have an ethernet connection (hardwire, or connected to wall), it'll be easier, read the manual, you'll have a nice gui, and everything you want. The begginners guide is awesome.

---

### Post by Sukarn on 2009-05-04
For a working ubuntu desktop, you could do **sudo apt-get install ubuntu-desktop** from the terminal, which would install the whole gnome thing with menus and everything, like in a normal ubuntu desktop.

---

### Post by Brainy142 on 2009-05-04
*screws net install and goes for regular install*

---

### Post by Brainy142 on 2009-05-04
Guy's it's not booting correctly (I get a black screen)

---

### Post by Eisenwinter on 2009-05-04
What exactly did you install, and in what method?

---

### Post by Brainy142 on 2009-05-04
Installed via live cd (from usb)... Live cd worked I wonder if it has something with using the home from my old linux and not formatting as I dont have anywhere to Back up my data.....

Note that root drive WAS formatted

going to possibly try to make a partition (the only remaning empty one besides the one ubuntu is in)

Note that GUI worked when it was on live USB.

---

### Post by Brainy142 on 2009-05-04
ITS ALIVE:guitar::guitar::guitar::guitar::guitar:

This is ALIVE

(ya I know I get over-excited)

problem was mounting of /home.

---

### Post by MaxIBoy on 2009-05-04
Glad you got it working.

---

