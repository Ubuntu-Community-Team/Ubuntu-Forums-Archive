---
title: "Ubuntu 20.04 LTS shows the state of desktop when waking up from hibernation"
date: 2020-05-17
forum: Security
---

### Post by sotenna on 2020-05-17
I'm new to Ubuntu, and Linux ingeneral, but I've been using Ubuntu 20.04 LTS since its release date, and have come to notice that on several ocassions when waking my PC, Ubuntu briefly shows my desktop and what I was working on before I hibernated the system, before the lockscreen comes on. This could be a big challenge security-wise.

---

### Post by EuclideanCoffee on 2020-05-17
This is a well-known issue. As you can see in this lengthy bug report.

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1280300](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1280300)

Here's a suggested work around from that thread.

> 
[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][Mike Jones (7-ubuntuone-kenl)]("https://launchpad.net/~7-ubuntuone-kenl") wrote on 2016-10-24:[/TD]
[TD="class: bug-comment-index"][#23]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1280300/comments/23")[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]Below is a workaround I use.
*********
#!/bin/sh
viewnior --fullscreen '/home/user_name/Images/My solid color image which obscures my desktop.png' && sleep 2 && dbus-send --system --print-reply --dest=org.freedesktop.login1 /org/freedesktop/login1 "org.freedesktop.login1.Manager.Suspend" boolean:true && i3lock -i '/home/user_name/Images/My image I like to look at when my computer wakes up.png' -p default -n
*********
I lock my screen with a keyboard shortcut I created in Xubuntu which I associated with the above script.
After my computer wakes up I need to exit Viewnior (the image viewer I am using) so that the the file called, "My solid color image which obscures my desktop.png" disappears.
I suppose the extra step would not be necessary if someone with some technical knowledge would explain how to cause i3lock to exit the image viewer after the computer wakes up.
I use "viewnior --fullscreen" instead of "viewnior -f" because the later didn't seem to work in a terminal. I suppose this was a result of my using a French language terminal.
Also, if you need to resize your image because you want it to appear centered on the screen, there's no need to install GIMP or any other draw or paint application.
I used Google Drawings to resize "My solid color image which obscures my desktop.png" to match my screen size which is 1366 x 768 pixels. I went to File&#8211;>Page configuration&#8211;>Customize and typed 1366 then 768 and chose pixels.
Then I downloaded "My solid color image which obscures my desktop.png" to my local drive.
I suppose if the developer(s) of this app were to a detailed explanation of the abovein a message, say the first five times a new image were used in i3lock, it would help new users quickly and easily lock their screen securely and ensure their images were centered on the screen.

[/FONT]
[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-05-17
Welcome.

Yes, you're right. It is a big security problem but certainly less than hibernation itself, not even avialable in the default installation and shouldn't be used (FYI, even the current Windows removed it). Unless you're talking about suspension? Many people confuse them...

Anyway, please post your hardware specifications, namely graphics as on way or another it likely boils down to graphics drivers.

---

### Post by EuclideanCoffee on 2020-05-17
> 
[COLOR=#000000][INDENT]Anyway, please post your hardware specifications, namely graphics as on way or another it likely boils down to graphics drivers.[/INDENT]


[/COLOR]
[COLOR=#000000][B]

Certainly there is no need.

This is a well-documented issue, and how I handled it in the past for enterprise is to disable hibernation and go to "shutdown when the lid is closed."

The rationale is for "good security" you'd not want to use hibernation to begin with.[RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by sotenna on 2020-05-18
machine: Lenovo ThinkPad W540.
Graphics card: [COLOR=#333333][FONT=&quot]Nvidia Quadro K2100 
OS: Ubuntu 20.04 LTS[/FONT][/COLOR]

---

