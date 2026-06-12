---
title: "HOWTO: Install Anarchy Online and have it work (almost) perfect."
date: 2009-09-05
forum: Wine
---

### Post by RabidWeezle on 2009-09-05
**[SIZE="6"][COLOR="Red"][CENTER]Installing Anarchy Online[/CENTER][/COLOR][/SIZE]**

[center][IMG]http://i30.tinypic.com/r224oo.jpg[/IMG][/center]

AnarchyOnline is a free mmo (well, the first 2 expansions are free, but it is a very full free experiance with the entire mainland to play and many free classes you can do) but it doesn't have a linux port. In this tutorial I will show you how to install, patch and play the game (tested in kubuntu jaunty). I'm not going to use synaptic since the kubuntu folks don't have synaptic by default, just terminal (konsole/xterm/whatever) commands. This has been tested with Kubuntu 32bit Jaunty.

**What's not perfect:**
If you hold up on the arrow keys to walk forward you will kinda shuffle your feet. So you hold forward and tap left or right once and it gets moving. It's enough to make the game not gold, but it's very easy to work around. Beats having to run it in windows. [read bottom for possible fix]

Here's the basic gist of what we are going to do.

[LIST]
[*]Add the wine repo + gpg key
[*]install wine and cabextract
[*]install ies4linux
[*]install anarchy online + patch and play
[/LIST]

1. **Installing Wine** (skip to section 2 if you have wine installed from the winehq repo)

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

then

```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/winehq.list

```

then

```
sudo apt-get update
```

then

```

sudo apt-get install wine cabextract

```
once done with this, skip to step 3

2. **Install cabextract** 
If you already have cabextract skip to step 3

```
sudo apt-get install cabextract
```

3. **Install ies4linux**

```

wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux

```
Install IE6 with that (the autopatcher/launcher requires it)

4. **Installing AO** 

Download and install the game in wine. Goto [www.anarchyonline.com](www.anarchyonline.com) and get the small client for free play, the large one if you want to play on a paid account. This part I have ***not*** tested as the initial installer JUST downloads the real installer, I did that part in windows myself, please post a reply if it doesn't work for you, but I figure it *should*. I can also upload legally a copy of the installer I used that I downloaded in windows then put it on megaupload. 

**When you get done installing, uncheck the "run the game after installing" you DON'T want to run the game yet!** Instead make a script and make it executable(swap out YOUR_LINUX_USERNAME_HERE for your linux username):

```

cd /home/YOUR_LINUX_USERNAME_HERE/.wine/drive_c/Program\ Files/Funcom/Anarchy\ Online/
WINEPREFIX="/home/YOUR_LINUX_USERNAME_HERE/.ies4linux/ie6" wine "Anarchy.exe"

```

Save it to like ~/anarchyonline, make it executable in the permissions, then you can run it like

```

cd
./anarchyonline

```
Or create a launcher that points to that script.

5. **Playing**

Anyway, once you install, patch up to the latest version and you will be ready to play, just make your free account on [www.anarchyonline.com](www.anarchyonline.com). The only people I don't suggest playing this on are people with asus eeepc's because they don't have the video drivers to get any decent framerate. Make sure to set your screen resolution in the launcher before you start the game. I run it in a window at 800x600 myself so I can alt-tab easily. **Only use your script you made to run the game so the autopatcher doesn't frag your game**

[B]Running this on my machine I get about 95 fps with all the settings maxed inside a shop:
[/B]
[LIST]
[*]AMD Athlon X2 2ghz laptop
[*]Nvidia 8200M G with shared memory with nvidia drivers from their website.
[*]Kubuntu Jaunty 32-bit
[*]4 gigs of ram (I know, not all of it is being seen, but I encountered too many problems in 64 bit with certain apps I use.
[/LIST]

UPDATE: I was reading in a WoW thread that they were having the same issue with the walking in wow...

> Hey nickgaydos..About the walk/run issue,i noticed that it only happens when i use <<w>>(forward or uparrow).When im pressing both clicks simultaneously nothing happened!!So go to system/preferences/keyboard and uncheck the option <<key presses repeat when key is held down>>.That worked for me m8

nomanarmy: try deleting everything in ur config.wtf(ofc always keep a backup somewhere else) and then run wow..1st time u ll start the game i think the file will be created corectly.

my english sux..^^

I can't test this right now since I'm at work, but I will check it out when I get home, and post an update if it does.

Taking a look at kde4 on kubuntu, that seems to be controlled by: click the K menu>Computer>System Settings>Under Computer Administration click Keyboard and Mouse>on the keyboard tab, uncheck "Enable keyboard repeat". That should get rid of the walk stuttering in the game I'm guessing, won't know until I get home.

**UPDATE: Confirmed!** The movement ingame is fixed when you disable keyboard repeating! So the game is platinum when you install this way and shutoff keyboard repeating, been playing it, and has run solid as a rock at high FPS and no crashes.

---

### Post by RabidWeezle on 2009-09-07
Added confirmed fix for jerky movement, game now runs 100% without crashes or messed up input (look at bottom of top post)

---

### Post by J V on 2009-09-24
Maybe we can add something to the script to turn key repeat off at the start and on at the end of the program... (xset r off, xset r on, dont use in terminal or bug will cause havoc)

On another note, running the script in the run dialogue correctly starts the program, as does terminal, but the exact same code from the wine menu looks like ies4u doesn't work, the window on the launcher says:
> Sorry, can't connect to anarchy-online.com!
Please check that your Internet connection is OK, or contact [EMAIL="support@funcom.com"]support@funcom.com[/EMAIL]

Any ideas on how to run the game windowed?

---

### Post by russnash37 on 2009-11-18
Thanks for this great guide!  I just got back into AO after a four year break and am finding myself addicted all over again!

I've been experiencing regular crashes running the game under wine with the latest version from budgetdedicated.  Has anyone else had similar issues and can offer a suggested fix?  One message I do seem to see a lot after a crash pertains to GL being out of memory.

Hoping I won't need to do something as reckless as re-install windows just so I can play AO without crashing >.< .

Russ.

---

### Post by russnash37 on 2009-11-18
I've just been doing some more digging around and found what may be the cause of my crashes, apparently, this GL_OUT_OF_MEMORY error has been seen in quite a few games under wine when using an ATI graphics card, notably the R300 series and up (which I am).

It seems that wine allocates 4gb of virtual memory to simulate the windows address space, however, the ati driver performs its memory allocation internally without wine getting to know anything about it, causing an eventual out of memory issue.

The latest beta version of wine supposedly contains a fix, I'm going to try this out and respond back here in the next day or two.

Russ.

---

### Post by russnash37 on 2009-11-23
I have to report, unfortunately, that despite trying the latest releases of wine (1.1.33) from winehq that this problem still persists.

---

### Post by bcboybuzz on 2009-12-20
Ah, that's what I was doing wrong, I had no clue that I needed ies4linux... Thanks a lot mate, I've missed AO since I went to Vista...now that I've ditched that piece of...er...spit...I can go back to an old fave...

EDIT: I had to find out the hard way, but do NOT restart your computer with ao client running, you'll frag your character and have to /petition to get it back...

I have the absolute worst internet connection possible, so I couldn't get out of the client....

---

### Post by ericwwheeler on 2009-12-21
I am getting a wine error right after downloading the small client.
I am running Ubuntu 9.10 64bit on a HP Tx1220us 

error as follows:


Archive:  /home/eric/Downloads/AnarchyOnline_18.1.1-Small (1).exe
[/home/eric/Downloads/AnarchyOnline_18.1.1-Small (1).exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/eric/Downloads/AnarchyOnline_18.1.1-Small (1).exe or
          /home/eric/Downloads/AnarchyOnline_18.1.1-Small (1).exe.zip, and cannot find /home/eric/Downloads/AnarchyOnline_18.1.1-Small (1).exe.ZIP, period.

Is there a way to download the whole thing instead of just the part?

Thanks in advance

Eric

---

