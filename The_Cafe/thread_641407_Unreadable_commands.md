---
title: "Unreadable commands"
date: 2007-12-15
forum: The Cafe
---

### Post by Frak on 2007-12-15
What does ^S mean? I'm trying to use rtorrent, and have driven into a brick wall with cryptic speaking.

Also, this needs to be changed in future doc versions. There is no need for people to have to look up cryptic keybinds (^S in Google treats the ^ as a *")

---

### Post by popch on 2007-12-15
At a guess I would say that that's

Control-Uppercase-Letter-S

---

### Post by Frak on 2007-12-15
> **popch said:**
> At a guess I would say that that's

Control-Uppercase-Letter-S
I've tried every combination of ctrl, alt, shift, and S keys.

---

### Post by popch on 2007-12-15
That documentation is a bit on the terse side, and it says so, too.

However, have you noticed the following passage:

> Note that ^s (and ^q for quit) is often used for terminal control to pause screen output (and ^q to resume). This may interfere with rTorrent. Type stty -a to see whether these have been mapped. To remove the mappings, execute the commands 
 stty stop undef
stty start undef
before running rTorrent (or reattaching to screen) to leave them undefined.

If your difficulty applies to ^S only (and not all commands in the page starting with the caret) that could be your solution.

---

### Post by Frak on 2007-12-15
> **popch said:**
> That documentation is a bit on the terse side, and it says so, too.

However, have you noticed the following passage:



If your difficulty applies to ^S only (and not all commands in the page starting with the caret) that could be your solution.
I got it to work... somehow... but it works nonetheless. Thanks for your help, and I'm planning on writing some of the documentation now.

---

### Post by zekopeko on 2007-12-15
using rtorrent:

backspace: give the location of torrent file (can be a link or on your disk (tabbing aka autocomplete works))

A S D - uppercase letters; set download speed by +1, +5 +50
Z X C- uppercase letters; set download speed by -1, -5, -50

a s d - lowercase letters; set upload speed by +1 , +5 ,+50
z x c - lowercase letters; set upload speed by -1, -5, -50

cursor keys - move through the menus (when you have the torrent loaded press RIGHT 
to enter that torrents specific stats. from there you can go to files(i think) and by pressing SPACE you can set the files to either low, high ,don't download priority)

i think that's all

---

### Post by ~LoKe on 2007-12-15
The reason it says ^s and not ctrl+s is because your modifier key might not be control.  Some people use alt or mod key (windows key).

in rTorrent, here are some of the more useful key combinations.

**Enter** or **Return** allows you to select which torrent to open.
**^s** starts the selected torrent
**^k** stops the selected torrent
**^d** removes the select torrent from rTorrent (and not, as far as I know, from your hard drive).

---

