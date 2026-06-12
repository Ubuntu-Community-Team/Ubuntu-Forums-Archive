---
title: "sudo problem"
date: 2017-06-20
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2017-06-20
running 17.10. cant enter my password. here is an example just used bleachbit but happens when i try to use any command with sudo

ray@nightmare:~$ sudo bleachbit
Invalid MIT-MAGIC-COOKIE-1 key/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Could not open X display
ray@nightmare:~$ 

any idea how to fix

---

### Post by ajgreeny on 2017-06-20
Can't specifically help with bleachbit as I've never seen a reason to use such programs, but if I recall correctly, it is a GUI program, and as such should **never be run using sudo.**  See [COLOR="#FF0000"]RootSudo[/COLOR] in my signature for an explanation.

To do so risks the possibility of locking you, as user, out from logging in to a GUI session.  If you must run a GUI program as root always use **sudo -H** or even the now deprecated **gksudo** if it is still available for 17.10.

---

### Post by #&amp;thj^% on 2017-06-20
> **ajgreeny said:**
> Can't specifically help with bleachbit as I've never seen a reason to use such programs, but if I recall correctly, it is a GUI program, and as such should **never be run using sudo.**  See [COLOR=#FF0000]RootSudo[/COLOR] in my signature for an explanation.

To do so risks the possibility of locking you, as user, out from logging in to a GUI session.  If you must run a GUI program as root always use **sudo -H** or even the now deprecated **gksudo** if it is still available for 17.10.
Bleachbit runs as "user" mode and "Root" mode. :)
For different reasons/functions.


> **rburkartjo said:**
> running 17.10. cant enter my password. here is an example just used bleachbit but happens when i try to use any command with sudo

ray@nightmare:~$ sudo bleachbit
Invalid MIT-MAGIC-COOKIE-1 key/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Could not open X display
ray@nightmare:~$ 

any idea how to fix

Have you customized your "XAUTHORITY" file?
Just a thought.
And if this on a wayland session...There is also a work-around mentioned in** post#52** here: [https://ubuntuforums.org/showthread.php?t=2358026](https://ubuntuforums.org/showthread.php?t=2358026)

---

### Post by ventrical on 2017-06-20
> **rburkartjo said:**
> running 17.10. cant enter my password. here is an example just used bleachbit but happens when i try to use any command with sudo

ray@nightmare:~$ sudo bleachbit
Invalid MIT-MAGIC-COOKIE-1 key/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Could not open X display
ray@nightmare:~$ 

any idea how to fix

I think you have some packages that are not updated fully.

You may have to go to recovery from grub and try:

sudo -i dpkg  --configure -a

---

### Post by rrnbtter on 2017-06-20
Greetings,
You won't be able to run x11 apps as super user under Gnome-Wayland until they are ported to Wayland's security structure.  Currently I log out and then login into Gnome x11 to use my super user apps such as Lucky Backup Super User. Gnome x11 works really well but I do like the snap that X-Wayland seems to provide. 
It doesn't take too much effort to convert the x11 apps to be Wayland compliant but the job is there to be done and everything is in flux right now so It may be release time or shortly there after before one or more of your favorites are converted.

---

### Post by rburkartjo on 2017-07-04
tks all. some of last updates solved the problem. wayland-gnome still a work in progress but i like it.

---

