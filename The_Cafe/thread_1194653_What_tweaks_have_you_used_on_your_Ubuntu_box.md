---
title: "What tweaks have you used on your Ubuntu box?"
date: 2009-06-22
forum: The Cafe
---

### Post by LesterPalooza on 2009-06-22
What tweaks have you used on your Ubuntu box? Software wise... For example, setting vm.swappiness to 0 or 60. Any tweak that optimizes your experience with Ubuntu. The reason why I am asking this is because I just want to know what tweaks people use to make his/her box "perform" better, faster. :)

---

### Post by lovinglinux on 2009-06-23
My optimizations are [here](http://ubuntuforums.org/showthread.php?t=1152095) and [here](http://ubuntuforums.org/showthread.php?t=1193567).

My current top results:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118685&stc=1&d=1245766056[/IMG]

My browser benchmarks improvements along this month:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118681&stc=1&d=1245764692[/IMG]

---

### Post by 2hot6ft2 on 2009-06-23
Making drives NOT show up on the desktop
Yes -open a terminal and type

```
gconf-editor

```
go apps->nautilus->desktop and uncheck "volumes_visible"
----------------

And I have done just about all of the tweaks here
[http://forumubuntusoftware.info/viewtopic.php?f=42&t=894&sid=b0234a8891bbfb37ee63c45d986485bb](http://forumubuntusoftware.info/viewtopic.php?f=42&t=894&sid=b0234a8891bbfb37ee63c45d986485bb)

It's for Gutsy but they work fine on ultimate edition 2.0 which is the same as ubuntu 8.10 Intrepid Ibex.
---------------------

Making the menu faster. In the home folder open a terminal and use
```
sudo gedit .gtkrc-2.0
```
add the line
> gtk-menu-popup-delay = 40
lower number = faster menu
save and close. Restart (reboot) to apply

*********
Loading menu icons faster

The key is to get the icons cached in memory at startup.

Change the 'Human' to whatever theme you're using.
Nope, that latter code is shell code that must be executed by a shell interpreter such as 'sh'. The .gtkrc-file is parsed by gtk in a special way, and shell commands cannot be used in there.

What you can do is create a script for this:

```
echo "find /usr/share/pixmaps/ | xargs cat > /dev/null" >> ~/mystart
echo "find /usr/share/icons/Human/ | xargs cat > /dev/null" >> ~/mystart
chmod +x ~/mystart

```
Then add it as startup to gnome (System -> Settings -> Sessions -> Add, and write "~/mystart")

by opera118
*********

---

### Post by lovinglinux on 2009-06-23
Today's updates boosted my performance. Check [this thread](http://ubuntuforums.org/showthread.php?t=1195028).

---

