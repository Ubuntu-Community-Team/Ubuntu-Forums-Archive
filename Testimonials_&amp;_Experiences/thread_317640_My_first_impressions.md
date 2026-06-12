---
title: "My first impressions"
date: 2006-12-12
forum: Testimonials &amp; Experiences
---

### Post by Peti29 on 2006-12-12
I work as a programmer so computers are close to me - however I don't consider myself a computer-geek. So when it comes to operating systems I'm mostly a user.
I'm total new to Linux and Ubuntu as well. These are my first impressions from my first week as a Linux user:

(Second time I start this review - the tabbed behaviour of 'gedit' just tricked me)
- First I checked out LiveCD. I liked it so I installed Ubuntu to my hard drive. (Nice partition editng tool - forgot the name. Maybe 'gparted'?)

- Installation was painless and quick. I really liked that my FAT-32 Windows partitions got automatically mounted (furthermore in UTF-8 mode so that my accentuated filenames display correctly)

- There should be a graphical tool for (DSL) internet setup. Luckily it's easy to find out 'pppoeconf' in the built in help documentation but I took some time searching for a tool in System/Administration and System/Preferences before I looked the Help docs. 

- I missed the little icon from the tray ("panel" if you like it better) showing my online/offline status. Later I found 'Network Monitor'. I created little shell scripts to connect/disconnect which I later put in the menu layout (only showed after X restart).

- Happily noticed that my sound card (SB Live) was set up automatically, it worked fine.

- Then I installed fglrx driver for my Radeon 9600XT using a package. I had to find a good how to ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) and with that help it was easy.

- Printer was next. Install was straightforward however it's a little disturbing having to use some 'BJC-7000' type with a 'BJC6000a1.upp' driver for my Canon i455. At least it's working :).

- It's annoying that Places/Recent Documents/Clear has no effect on Movie Player's (Totem's) recent list. One has to do it 'by hand': rm ~/.recently-used
Apart from that Totem works fine (I had some trouble with 'mplayer' and accentuated subtitlesb not to mention '-vo')

- I like 'Gaim' much and 'gedit' also.

- It'd be nice if 'Run in terminal' didn't close the terminal the very moment the execution ended. (To be able to see the output)

- Wine install succeeded and I managed to setup Age of Mythology. It worked but is unfortunately unplayable as it crashes (or freezes) after a few minutes.

- I really like the 'Add/Remove' tool

- The absence of a 'Cancel' button on all of the settings dialoges feels a little frightening.

- Next I made some customization: moved the panel to the bottom (just for the hack of it as I also liked it at the top), switched to another desktop theme ("Industrial tango"), and put up some nice OSX-like xcursor theme (I use that on W$ too). I miss the opportunity to customise each element: I'd like sliders to have somewhat stronger contrast as it's hard to distinguish the "pull thingy" from the "track".

- Set up 'Battle for Wesnoth' and tend to like it :)

- At first it seemed that the fglrx driver only worked for my user but now it works for the other as well. However second freeze occured during switching users back and forth.

- Registered for ubuntuforumes ;)

- Installed some more games including Glest. It's the first time I installed sg by hand (Ok, it was actually a Loki installer but still: I did it by hand :))

- It started to be annoying that File manager was unable to posess su rights. Found the answer: 'gksudo' but haven't installed that yet.

- Changed from double click activation to single click, but didn't like that so I switched back...

- 'Adblock' plugin for Firefox was next. (Also tried 'Adblock Plus' but liked the preciving one better)

- 'Beryl' came next. At first it seemd 'Beryl' couldn't go with fglrx, but then I found out I just needed a 'glx' session underneath ([http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)). Only thing that was troublesome is that window resize functionality was disabled by default (don't know why).

That's it more or less until now. There is a lot more to try (CD burning, pendrive/digital camera, devenv, etc..) but those will no longer count as a "first impression" to me.
It's really not that hard to get along with Ubuntu (as long as one can find the answers on various forums). It's a bit more laborious than Windows though.
I've had some freezes (I don't know of a way to get out of that other than pushing hard reset yet) though they all happened in non-trivial circumstances (running AOM in Wine; Beryl...)
On the whole I like Ubuntu very much.

---

### Post by teaker1s on 2006-12-12
can't put a price on quality I now have
3 ubuntu systems :mrgreen: and 2 xp that never get used on 4 computers

you will also notice ubuntu only breaks when you alter it wrongly-windows breaks repeatedly just through email,internet and installs-spyware and viruses](*,)

---

### Post by seijuro on 2006-12-12
Nice review, if you like RTS type games give Globulation2 a try it has a very unique spin has sweet graphics and is suitable for any age capeable of playing a RTS as there is no blood or gore.

You are correct with the partition tool name it is gparted. As for gksudo you don't need to "install" it just add at the front of the command line just like sudo. Personally I hate totem if you're having trouble with mplayer you might want to give VLC a try.

Welcome to the community, hope you continue to enjoy your experience.

---

### Post by dorcssa on 2006-12-12
> **Peti29 said:**
>  

- I missed the little icon from the tray ("panel" if you like it better) showing my online/offline status. Later I found 'Network Monitor'. I created little shell scripts to connect/disconnect which I later put in the menu layout (only showed after X restart).
On the whole I like Ubuntu very much.

Can you tell exactly how did you make it? :D I'm missing it too, but I don't have a history like you(programming), so it'd difficult for me. :)

Btw welcome to ubuntu(though I'm newbie too :mrgreen: ).

---

### Post by oskie on 2006-12-13
I like your post, you had some problems but you kept on. Sounds like you've overcome most of the significant challenges already. Yeah, DSL networking pppoeconf is ridiculously primitive looking and not obvious at first but  hey, it works.

---

### Post by Peti29 on 2006-12-13
I forgot to mention that I'm using the Edgy Eft version (6.10) of Ubuntu.

seijuro: Thx for the tip! Will give it a try (I didn't like Glest very much)

oskie: I have nothing against pppoecfg but it wasn't straightforward to find it. There should be at least a launcher for that in Administration I think.

Dorccsa: Szia! :) Hogy a többiek is értsék:
To put 'Network Monitor' on the panel do the following (guessing from memory as I write from work now):
- right-click on the panel
- choose 'Add to panel'
- a window should pop up with a collection of small applications
- select 'Network Monitor'
- apply. You're done. A little icon of monitores should appear on your panel at the place you right-clicked on it. You can moove it where you like by right-clicking on it and selecting 'move'.

As for the connect/disconnect scripts:
- create an empty file on your desktop (right-click than select 'new empty document')
- the inside of the file should be:
```
#!/bin/bash
pon dsl-provider
echo "Press Enter..."
read
```
Substitute 'dsl-provider' with whatever name your DSL connection has (the name that you usually type after 'pon' when connecting). You may have to insert 'sudo' before 'pon' - I just can't remember now.
Save the file. Right-click on it and set executable rights (enable the file to be executable).
Disconnect if you're online. Now double-click on the file. A window should pop up asking wether you'd like to display the contets or run the program. Select 'Run in Terminal'. Now you should be online :).
For the disconnect script copy the file and substitute 'pon dsl-provider' with 'poff -a'. Don't forget to set the new file to be executable as well.

To put them into the menu layout:
Select 'Menu layout' from the panel / preferences (or administration - I don't know which one). Add the two scripts from your desktop to the 'Internet' menu (or any other, you may even create a new entry). I had some trouble with this 'Menu layout' tool and found out that my new menu items only show after a restart (CTRL + ALT + Backspace).

Hope I could help!

---

### Post by dorcssa on 2006-12-13
Nahát, köszi szépen, meg tök jó h te is magyar vagy. :D
Back to english..
I have a router, so I don't need the script right now, but I'm going to save your guide, cos my boyfriend have dsl, and maybe I'll happen to have dsl too sometime in the future. :D The network monitor and adding to panel was obvius, but not for me, at least now I know it.

---

### Post by matt_risi on 2006-12-13
Anyone have a fix for that issue of not being able to see terminal output when a command is run in ALT+F2?

---

### Post by hoagie on 2006-12-13
Welcome to ubuntu. It looks like you are a challenging person since you didn't gave up after a few problems.
Welcome aboard!

---

### Post by seijuro on 2006-12-13
> **matt_risi said:**
> Anyone have a fix for that issue of not being able to see terminal output when a command is run in ALT+F2?

The only way I know of off hand is to actually run the command in a terminal meaning load up something like xterm or konsole and run it from there.

---

### Post by DoctorMO on 2006-12-14
you can create kde and gnome links which load up in terminals I'm surprised there isn't a check box to load the command in a terminal.

oh wait there is for kde at least; perhaps a bug report for  gnome?

---

