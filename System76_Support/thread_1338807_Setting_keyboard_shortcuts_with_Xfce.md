---
title: "Setting keyboard shortcuts with Xfce?"
date: 2009-11-26
forum: System76 Support
---

### Post by miniyak on 2009-11-26
With 9.10 karmic

Today I installed xfce through synaptic and need to customize a few things to make the overall experience usable. But im having a hard time setting my own shortcuts.

Here are the shortcuts im looking to set

Set "Right-Alt+left" back one page in firefox (this doesn't work for me in Gnome ether... and it does in 9.04...Anyone else having this issue?) 

Set "caps lock" as backspace (now im kind of cursing myself that im used to this... makes life easier when its working though..)

Set "Alt+X" as close window (vs. using the finger stretching alt-f4)

Thanks for any help, Any one else using odd keyboard shortcuts?

---

### Post by thomasaaron on 2009-11-27
jdb, do you know anything about this one?

---

### Post by jdb on 2009-11-27
> **thomasaaron said:**
> jdb, do you know anything about this one?

I haven't got xfce4 loaded on anything right now so I can't try it.

I used keytouch & keytouch-editor when I was running Xubuntu:

```
keytouch
	A program to configure extra function keys in multimedia
keytouch-editor
	create keyboard files for keytouch

```
Right now I'm using Fluxbox on Arch & Ubuntu, I load the command line version of Ubuntu and add Fluxbox.

When I get time I want to try the new Gnome, it sounds pretty neat.

jdb

---

### Post by miniyak on 2009-11-27
Cool, Just installed keytouch and keytouch-editor. Its asking me if what the keyboard model is. Do you know Tom? 

There are alot of options, I could guess the make but it would take while. I couldn't find a generic option

---

### Post by jdb on 2009-11-28
> **miniyak said:**
> Cool, Just installed keytouch and keytouch-editor. Its asking me if what the keyboard model is. Do you know Tom? 

There are alot of options, I could guess the make but it would take while. I couldn't find a generic option

I found some notes I made.
```

keycode for emacs #########################################
  sudo keytouch-editor
  select event1 & press windows key
  use New to add windows key & assign to emacs
  save as KD-2201.China (must be model.manufacturer) in /usr/shar/keytouch/keyboards
  keytouch
  set program for windows key to emacs

file locations on darter (daru2) ##########################
  deamon /etc/init.d/keytouch
  keyboard_file /usr/share/keytouch/keyboards/ms-1221.msi
	  This file was made by KeyTouch Editor, manufacturer msi, model ms-1221
  keyboard_file_pointer /etc/keytouch/current_keyboard.xml
```

As an aside, to do the same thing in fluxbox I just add this line to ~/.fluxbox/keys :

Super_L :ExecCommand emacs /

jdb


jdb

---

### Post by miniyak on 2009-11-28
Thanks for the extra info jdb, Right now keytouch is giving me a list of keyboard makes and models but i couldn't find anything labled msi or kd2201, not that those would be right, but i think ill have to import a layout to start messing around with things.

I know im kind of side tracking this a bit, but is it easer to set shortcuts and mount other partitions with fluxbox?... actually anything is probably easy when you know what you're doing. Just wondering its simpler out the box. ha ha

---

### Post by jdb on 2009-11-28
> **miniyak said:**
> Thanks for the extra info jdb, Right now keytouch is giving me a list of keyboard makes and models but i couldn't find anything labled msi or kd2201, not that those would be right, but i think ill have to import a layout to start messing around with things.

I know im kind of side tracking this a bit, but is it easer to set shortcuts and mount other partitions with fluxbox?... actually anything is probably easy when you know what you're doing. Just wondering its simpler out the box. ha ha

yes & no :)

Right clicking any empty spot on the screen brings up a menu for
doing most things.
Other things, like setting short-cut keys, can only be done by editing
configuration files.
The files are in plain english, no xml or other gibberish.
Anything can be added to the menu just by editing ~/.fluxbox/menu

It does support any number of workspaces, but you can't keep files
or short-cuts on the desktop.
You can put shortcuts in the menu.

It's a very simple desktop, but I like that.

[IMG]http://www.jdbowman.com/links/screenshot.jpg[/IMG]

jdb

---

### Post by thomasaaron on 2009-11-30
Generic 105-Key (Intl) keyboard

---

