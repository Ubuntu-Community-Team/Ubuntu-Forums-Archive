---
title: "Newb: Can I get a GUI on a server without all the Apps?"
date: 2007-12-01
forum: Server Platforms
---

### Post by Smartin on 2007-12-01
Hi,

I need a lightweight GUI to run on Dapper server so I can run things like Firestarter.

Is it possible to install the Xubuntu desktop without all the associated applications? I don't want Abiword etc etc.

What command would I enter?

Do I have to install Xubuntu and then uninstall all the apps perhaps...?

Thanks!

Simon

---

### Post by prodezigner on 2007-12-01
well... you can install x and xfce seperately... or you can get the desktop and remove all programs you don't need.

---

### Post by netlogic on 2007-12-01
I think XFCE is way too BLOATED to be a server gui. It will install 200megs of junk you don't need. Try Fluxbox or Blackbox.

---

### Post by zekopeko on 2007-12-01
or even better. wmii

---

### Post by Smartin on 2007-12-01
> **prodezigner said:**
> well... you can install x and xfce seperately... or you can get the desktop and remove all programs you don't need.

prodezigner,

Thanks for the quick response...

What apt-get command would I use to install each of these?

sudo apt-get install ...?

(I really am a newb...)

Simon

---

### Post by Smartin on 2007-12-01
> **netlogic said:**
> I think XFCE is way too BLOATED to be a server gui. It will install 200megs of junk you don't need. Try Fluxbox or Blackbox.

netlogic,

Fluxbox looks good...

Will I be able to run any of the GUI apps using Fluxbox, just as if I were using the standard Ubuntu desktop edition?

sudo apt-get install fluxbox?

Simon

---

### Post by Smartin on 2007-12-01
> **zekopeko said:**
> or even better. wmii

zekopeko,

This looks a bit to hairy for me! :lolflag:

Will this allow me to run things like Firestarter etc?

Simon

---

### Post by Dr Small on 2007-12-01
Fluxbox, IceWM, Blackbox, JWM, Openbox...
Any of them are lightweight and would work for what you need.

---

### Post by koenn on 2007-12-02
```

# 'universe' repo needs to be enabled for fluxbox
sudo apt-get install xorg x-window-system-core xterm xdm fluxbox

```
and yes, this will allow you to run just any gui app. 
Just be aware that some feautures (panels ...) belong to the desktop environment/window manager. This means that you will NOT get (gnome) panels and menus with fluxbox. you'll get a fluxbox-style menu instead.

---

### Post by RedSquirrel on 2007-12-02
I would do:
```
sudo apt-get install xorg xterm fluxbox
```If you decide to go with Fluxbox, remember to generate the menu. Just run

```
sudo update-menus
```after you install the fluxbox package.

You could use a display manager (such as xdm), but it is not necessary. You could just create the file ~/.xinitrc with these two lines:

```
#!/bin/sh

exec startfluxbox

```Make it executable as well:

```
chmod +x ~/.xinitrc
```When you want to have a GUI, you just run (from the console):

```
startx
```and that will start Fluxbox.


EDIT:

If you know the video driver you need, you can install that up front. That way, apt will only install the one you need and not a whole bunch of drivers you'll never use.

```
sudo apt-get install *video-driver-package-name* xorg xterm fluxbox
```

---

### Post by Smartin on 2007-12-19
> **koenn said:**
> ```

# 'universe' repo needs to be enabled for fluxbox
sudo apt-get install xorg x-window-system-core xterm xdm fluxbox

```
and yes, this will allow you to run just any gui app. 
Just be aware that some feautures (panels ...) belong to the desktop environment/window manager. This means that you will NOT get (gnome) panels and menus with fluxbox. you'll get a fluxbox-style menu instead.

koenn,

I have some more time to tinker... :-)

I have installed the Gutsy server with the other apps you mention above but...

Now all I have is a blue desktop with a taskbar at the bottom. I can't see any menus and can't get to a terminal even.

What do I do now? :confused:

Thanks!

Simon

---

### Post by Smartin on 2007-12-19
Hi,

Found this thread

[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

Going to have a go in a while... :-)

(Edit) Worked!

Thanks!

Simon

---

### Post by koenn on 2007-12-19
click (or right-click ?) anywhere on the desktop, and you should get a menu. 

If not, that thread you found should get you going. 

there's also a number of files in your home  .fluxbox directory
one of them is the config file where you can manually edit the menu if need be (eg if installed apps did not create a meny entry

---

### Post by reckless2k2 on 2007-12-19
if you only need to admin a server then i suggest webmin. you can then access a GUI admin panel for that machine from another machine via a web browser.

---

