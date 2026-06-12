---
title: "lubuntu: what is the standard procedure to enable multiple keyboard layouts?"
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by GeorgeVita on 2012-01-19
Testing [COLOR="Blue"]Lubuntu 12.04[/COLOR], 
I can't find the "typical procedure" to enable multiple keyboard layouts and especially which key(s) to use for switching.

Using Ubuntu (classic gnome) my preferable procedure is:

System > Preferences > Keyboard > Layouts > Add
and then System > Preferences > Keyboard > Layouts > Options > Key(s) to change layout

At Lubuntu there are a lot of options and menu items that possibly confuse the user:

Menu > Preferences > Input Method switcher
Menu > Preferences > Keyboard and Mouse > Keyboard > lxkeymap
Menu > Preferences > Keyboard Input Methods
Menu > Preferences > Language Support
Menu > Preferences > lxkeymap
Menu > System Tools > iBus

Although there are all above options, I can't find the "appropriate" to select both English and Greek keyboard layouts. 

Possible solution is via the terminal command:
```
setxkbmap -layout "us,gr" -option "grp:ctrl_shift_toggle"
```
which can be permanent by editing the same parameters into file /etc/default/keyboard

But using lxkeymap overrides above setting (after testing the keyboard layouts with lxkeymap the "hot key" stops changing them).

1. Is there a "standard procedure" to enable and use multiple keyboard layouts?
2. Can developers add more options to lxkeymap to become the main configuration tool?

Thanks for reading,
George


**edit:** there is a bug report on #2:
Please add support for multiple keyboard layouts: [#904386]("https://bugs.launchpad.net/lxkeymap/+bug/904386")

**2nd edit:** developer of lxkeymap commented above bug:
> I will take a look at it. We aren't currently using setxkbmap but xklavier. So I think I need to work around this somehow. Give me some weeks to fix that.

---

### Post by jodorami on 2012-03-25
If you are looking for a solution for English and Romanian, here is something that worked for me in my Lubuntu 11.10:

1. Open the terminal. Type

sudo nano \home\user\.bashrc

[Replace "user" with your username. Also, you may replace "nano" with your favourite editor, e.g. "gedit," etc. Additionally: for safety, you might want to create a backup for your current .bashrc configuration so that, in case this solution doesn't work, you can go back to your previous settings. A friend did it for me, so I can't really help you with it.]

2. Enter your password. The terminal will start processing your command. When it's done:

3. Scroll down all the way to the last line, then type:

setxkbmap -layout "us,ro(winkeys)" -option "grp:ctrl_shift_toggle"

3. Press Ctrl+X and then y [to implement the changes].

4. Log out, then log in again.

You should now be able to switch between the English and the Romanian keyboard layouts by pressing Ctrl+Shift. 

Comment: Please note that Lxkeymap has a number of variants for Romanian. I've tried using Romanian (standard) in the code and it didn't work. Apparently Romanian (WinKeys) works. I don't know about the other variants. 

Hope this helps :)

---

### Post by jodorami on 2012-03-25
All of a sudden it stopped working... I can still switch between the layouts using Ctrl+Shift, but when I try to type in Romanian, I can't do it.

---

### Post by seppalta on 2012-03-25
For Lubuntu 11.10 you need to edit autostart and add Keyboard Layout Switcher to the taskbar.  See [http://douwil7.100webspace.net/linux/Tuning.html#19]("http://douwil7.100webspace.net/linux/Tuning.html#19") for details.

---

