---
title: "Live 11.10 CD session: behaviour when clicking on MP3 file"
date: 2011-12-20
forum: The Cafe
---

### Post by keithpeter on 2011-12-20
Hello All

Working on a spin-off from the Unity 2d tutorial guide (see sig) and looking at a very graphical poster/handout for using a live Ubuntu 11.10 CD to do 'stuff'.

When I double click on an mp3 file on a USB stick, the following happens...

[LIST]
[*]Banshee loads
[*]Track listed in 'File System Queue' list in the left hand pane, *not visible* in main list
[*]Click on 'File System Queue' list, then track appears in main music list pane and can be clicked on...
[*]Then a window pops up saying 'Search for Suitable Plugin'
[*]I click search, another window, some seconds,
[*]Another error pops up saying 'No packages with requested plugins found'
[/LIST]

There is a functioning Internet connection. Is this what others are seeing? 

I've always just installed restricted extras as part of the post installation setup. Now looking at live CD specifically. If it is normal behaviour, I'll just not have a music related activity!

---

### Post by mips on 2011-12-20
The livecd has no codecs to handle mp3. You could 1) install them every single time you boot up, 2) create a new livecd that contains the codecs or 3) Just use something like Linux Mint that contains the codecs.

---

### Post by keithpeter on 2011-12-20
> **mips said:**
> The livecd has no codecs to handle mp3. You could 1) install them every single time you boot up, 2) create a new livecd that contains the codecs or 3) Just use something like Linux Mint that contains the codecs.

Hello mips

I know there are no codecs by default, but the behaviour struck me as odd (why offer to search if the search will always fail? and why hide the file clicked on in a sub-tree of the Banshee window?), so I thought that I would check. Thanks for confirming the behaviour. I'm not having any music activities!

Everyone

The next little anomaly is as follows, in Unity3d using 11.10 live session:

Edited:  Firefox must be in foreground for clicking on firefox icon in Launcher to bring it to the front when you are in another workspace

Strange thing...

---

