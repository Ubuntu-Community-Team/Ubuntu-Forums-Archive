---
title: "Running Warcraft 3 in Full Screen Mode?"
date: 2009-04-24
forum: Wine
---

### Post by noob_penguin on 2009-04-24
Hi guys, I'm sorry I know this has been discussed before (without success I've noticed from the other threads) but I'm just wondering if anyone knows how to get Warcraft 3 to run in full screen mode using Wine?

Here is an image of what is happening when I run the game:
[http://imgur.com/1o0e.png](http://imgur.com/1o0e.png)

Essentially, when I am in-game and I try to pan around the map by moving my mouse to the corners of the screen, the mouse leaves the game window and moves onto the desktop, which kills the gameplay.

I am running the version 1.1.19 of Wine. I am running Ubuntu version 9.04. 
I have tried configuring Wine to run in a virtual desktop which does not work, as well as having it not run in a virtual desktop. 

I have a nVidia Geforce Go 6100 in my laptop, and currently have the nVidia accelerated graphics driver version 180 installed and working. 

The only problem with the game is that it won't run full screen. I've also tried simply switching the game to another workspace to see if it runs full screen, but it does not.

Anyways, if anyone can help me out here I'd greatly appreciate it. 

Thanks.

---

### Post by hikaricore on 2009-04-24
Have you tried turning off desktop effects?

---

### Post by noob_penguin on 2009-04-24
Hey, that fixed it. Thank you very much. :)

---

### Post by hungryOrb on 2009-04-30
Wow.. that fixed it? You didn't do anything extra? :O
Mine doesn't run full screen either, and no effects doesn't help.

Do I need to run it with opengl to get full screen? and if so, how is that possible? :O

TFC

---

### Post by BlahMan_of.Doom on 2009-04-30
> **hungryOrb said:**
> Wow.. that fixed it? You didn't do anything extra? :O
Mine doesn't run full screen either, and no effects doesn't help.

Do I need to run it with opengl to get full screen? and if so, how is that possible? :O

TFC

Just tack on --opengl at the end of it.

---

### Post by hungryOrb on 2009-04-30
thanks! didn't get the full screen though.. waaa

---

### Post by hotweiss on 2009-05-01
> **noob_penguin said:**
> Hi guys, I'm sorry I know this has been discussed before (without success I've noticed from the other threads) but I'm just wondering if anyone knows how to get Warcraft 3 to run in full screen mode using Wine?

Here is an image of what is happening when I run the game:
[http://imgur.com/1o0e.png](http://imgur.com/1o0e.png)

Essentially, when I am in-game and I try to pan around the map by moving my mouse to the corners of the screen, the mouse leaves the game window and moves onto the desktop, which kills the gameplay.

I am running the version 1.1.19 of Wine. I am running Ubuntu version 9.04. 
I have tried configuring Wine to run in a virtual desktop which does not work, as well as having it not run in a virtual desktop. 

I have a nVidia Geforce Go 6100 in my laptop, and currently have the nVidia accelerated graphics driver version 180 installed and working. 

The only problem with the game is that it won't run full screen. I've also tried simply switching the game to another workspace to see if it runs full screen, but it does not.

Anyways, if anyone can help me out here I'd greatly appreciate it. 

Thanks.

I have found the solution. Install compiz settings manager:

> sudo apt-get install compizconfig-settings-manager

Go into Compiz Settings, then Workarounds and enable Legacy Fullscreen Support.

---

### Post by grantbuntu on 2009-06-09
I found a solution from Dimitar Boichev which I have blogged on at  [Full-screen Warcraft under Wine]("http://p-s.co.nz/wordpress/?p=501").  The solution involves X windows and may have performance benefits as well.

Here is what worked for me (minor changes from what Dimitar did):

```
sudo gedit /etc/X11/Xwrapper.config
```

Change:

```
allowed_users=console
```
to
```
allowed_users=anybody
```

Then save and quit.

Applications>Wine>Configure Wine select the game you want under applications and then, under Graphics, make sure you untick “Emulate a virtual desktop”.

I also copied /etc/X11/xorg.conf as /etc/X11/only_one_monitor.conf so that I could handle my dual monitor setup by playing Warcraft full-screen in one monitor only. I needed to change:

```
"TwinView" "1"
```
to
```
"TwinView" "0"
```
i.e. turn dual (twin) view off

Then I created a bash script with the following content (NB to use **your** username and the correct path to **your** game) and saved it to my desktop:

```
#!/bin/bash
X :2 -ac -terminate -config only_one_monitor.conf & sleep 2
DISPLAY=:2 nice -20 env WINEPREFIX="/home/username/.wine" wine "c:\Program Files\Warcraft III\Warcraft III.exe"
```

Then make the bash script executable (under the file’s Properties>Permissions>Execute - tick the tickbox). Double click it and select run to enjoy full-screen Warcraft etc.

Ctrl+Alt+F7 and Ctrl+Alt+F9 lets you switch between X windows.

---

