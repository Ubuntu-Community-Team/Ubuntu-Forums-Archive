---
title: "Beyond the Red Line (Game With Linux Version)  Based on  Battlestar Galactica"
date: 2007-04-19
forum: The Cafe
---

### Post by mtn on 2007-04-19
EDIT: Just realized this should have gone in Gaming & Leisure. Mods, please move if you get a chance.

I came across a new community developed game today, [Beyond the Red Line]("http://www.game-warden.com/bsg/"), based on the new (rather than original) Battlestar Galactica TV series. This was exciting as there is a Linux (as well as Windows and Apple) version. I did have a problem running the game tho (on my Toshiba A120 running Ubuntu Feisty Fawn beta - fully updated), so I have documented the solution here for future reference.

Installing the game was easy. [Download]("http://www.game-warden.com/forum/showthread.php?t=3502") the Linux install to the desktop (took about 30mins). Then change the permissions of the file so that it is executable - right click on the file, choose the permissions tab and click the &#8220;allow executing file as program&#8221; check box, and then click close. Then run the install - double click the install file (BtRLDemoInstaller.run) and click &#8220;run&#8221;. After checking the files integrity the install box pops up, then click through the couple of options. install completed.

To run the game pop up Nautilus file manager and navigate to home-directory~/btrl_demo, double click the btrl_demo file (I might have had to make this executable as well!). The game starts - excellent. The problem was when I click on the &#8220;Briefing&#8221; option the game crashed with the error [Linux] **ERROR: &#8220;Could not load ABexp04 anim file&#8221; at fireball/fireballs.cpp:697**. This was solved by checking out the[ BtRL forums]("http://www.game-warden.com/forum/forumdisplay.php?f=36"), and following this [thread]("http://www.game-warden.com/forum/showthread.php?t=3696&highlight=fireball%2Ffireballs.cpp%3A697").

Download the file[ libtxc_dxtn060508.tar.gz]("http://homepage.hispeed.ch/rscheidegger/dri_experimental/libtxc_dxtn060508.tar.gz") (from the bottom of the [s3tc]("http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html") page) on to the desktop. Unpacked it with archive manager - double click it and click extract. Then install libtxc_dxtn - pop up a terminal using Ubuntu&#8217;s main menu Applications>Accessories>Terminal and navigate to the libtxc_dxtn dircetory by typing&#8230; cd Desktop/libtxc_dxtn &#8230;and then hit the enter key. Then type the two commands below, hitting enter after each command, to install libtxc_dxtn.

make

make install

That got things going for me. I still have a problem with [garbled sound]("http://www.game-warden.com/forum/showthread.php?t=3639&highlight=sound+problem"), but I&#8217;m working on this but any help would be appreciated!

---

### Post by gaspar on 2007-04-19
Nice game! :)
 But I didn't have to compile the libtxc_dxtn...
Anyway, what do you mean with garbled sound? During the briefing, I can hear the sounds okay, but in the ship, sounds strange, but I think it's simulating a radio transmission, no?

---

### Post by dantakeoff on 2010-10-05
hey man thanks for the how-to, but i just cant find litxc_dxtn, the link you provided takes me to a german website and i have no idea where to begin looking for it... pleeeeez walk me through where to find this thing....

---

### Post by Cowboybebop79 on 2010-10-05
> **dantakeoff said:**
> hey man thanks for the how-to, but i just cant find litxc_dxtn, the link you provided takes me to a german website and i have no idea where to begin looking for it... pleeeeez walk me through where to find this thing....

Just found a link to it here hope this helps

[http://archlinux.ro/~heftig/libtxc_dxtn070518.tar.gz]("http://archlinux.ro/~heftig/libtxc_dxtn070518.tar.gz")

bear in mind google only finds three matches for this, one of which is this thread so if you have a ubuntu one account drop a copy in your public folder and post a link here. For future Battlestar Fans.

---

