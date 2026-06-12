---
title: "Try my debs"
date: 2016-06-23
forum: The Cafe
---

### Post by CantankRus on 2016-06-23
Had some free time so I decided to learn how to create a launchpad ppa and construct deb files.
I made 2 debs of scripts I use to create a clipboard for often used snippets and a countdown timer.
Both applications use unity launcher quicklists.
I use them all the time...maybe you will find them useful too.

**_Quicksnips_**
[ATTACH=CONFIG]269750[/ATTACH]
I use this as a companion to my normal clipboard manager for phone numbers, email addresses, 
often used terminal commands or any snippet I use regularly.
Left clicking the launcher opens the snippets file.
Right clicking shows the snippets quicklist, which are copied to middle mouse click.
Highlighted text can be copied to the snippets list using the "Add clipboard Content" quicklist item.

Quicksnips is added to /etc/xdg/autostart.
If you log out/in you'll find a quicksnips item on the launcher 
or you can drag and drop from the dash.



**_ConkyTimer_**
[ATTACH=CONFIG]269751[/ATTACH] [ATTACH=CONFIG]269873[/ATTACH]
This is a countdown timer which displays the countdown in the top panel using conky.
Right clicking the launcher shows some preset times you can choose or you can left click to set a custom time.
When a countdown is running left clicking the launcher will kill it.
Drag and drop ConkyTimer from the dash to launcher
You can change the alarm sound by editing line #13 of /usr/share/conkytimer/countdown.sh.
Set the path to your own custom sound or one from /usr/share/conkytimer/sounds.

You can change the horizontal position of the conky readout by editing /usr/share/conkytimer/timer-conkyrc
Line #94... "gap_x = 413" sets the position from the right hand side.


To install...
```
sudo add-apt-repository ppa:stinkeye/misc
sudo apt update
sudo apt install quicksnips conkytimer 
```

---

### Post by izznogooood on 2016-06-24
Nice script ;)

I prefer guake and have all of those in .bash_alias EX:  alias update='sudo apt update && sudo apt list --upgradables' 

Simply put it updates the repositories and list possible upgrades... I have a simulere on for upgrade ;)

---

### Post by CantankRus on 2016-06-24
I know what an alias is and how to use them.
In fact I use aliases for most of the example commands you noticed in the example pic.
Quite often I want a code snippet copied to the clipboard for use somewhere else other the terminal...eg answering forum questions.
guake-indicator only sends custom commands  to be run terminal.

---

### Post by izznogooood on 2016-06-24
> **CantankRus said:**
> I know what an alias is and how to use them.
In fact I use aliases for most of the example commands you noticed in the example pic.
Quite often I want a code snippet copied to the clipboard for use somewhere else other the terminal...eg answering forum questions.
guake-indicator only sends custom commands  to be run terminal.

I ment Guake the drop down terminal, and the alias comments was mostly for other people. I assumed you knew about aliases ;).
This would be great for a lot of people, your script i mean! (Maybe you can send a promote request / tip to webupd8)!.

---

### Post by mastablasta on 2016-06-25
but snaps are the future :-P

it's great when you learn something knew, it works and you are able to share it with others.

---

