---
title: "Gnome-Shell won't load anymore, so I'm stuck with Unity"
date: 2012-06-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Starks on 2012-06-23
Even though 12.10's Unity is pretty much unchanged from 12.04 at the moment, using it is pure suffering.

I have a lot of hotkeys set to Alt and I really don't care for the stupid HUD coming up whenever I press it.

Is anyone else having problems getting Gnome-Shell to load?

---

### Post by VinDSL on 2012-06-23
Hold on.

I'll check...

**EDIT**

Yep!  Pretty much DOA...

I can log into GS, but all I get is the desktop wallpaper, and Conky -- no menus, and so forth, and so on.  Cannot go anyplace or do anything, other than log out..

Worked a couple of days ago, so I *guess* a recent upgrade puked it.

* I might also mention, Unity has been acting janky too, the past few days.

---

### Post by VinDSL on 2012-06-23
LXDE is still looking pretty foxy.  LoL!  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-23-jun-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-23-jun-2012-1.png")[/INDENT]


Might want to try that (LXDE/Openbox on top of UbuQQ)...

---

### Post by Starks on 2012-06-23
Meh. Lxde and Xfce really aren't that good IMO.

Cinnamon has its problems, but it's never failed me as a fallback.

I really need to stop giving Unity so many chances.

---

### Post by cariboo on 2012-06-23
Seems to be working ok here, I just did updates, then installed gnome-shell. When I went to log out, there was a notification that I needed to reboot. After a reboot see the screenshot for what I get.

---

### Post by VinDSL on 2012-06-23
> **cariboo907 said:**
> Seems to be working ok here, I just did updates [...]
Well, you rascal, you...  :)

Are you using the ricotz/testing PPA?

---

### Post by cariboo on 2012-06-24
> **VinDSL said:**
> Well, you rascal, you...  :)

Are you using the ricotz/testing PPA?

Nope, out of the box alpha 1 with regular updates. I'm using the Nvidia 295.53 drivers on top of the  3.5.0-1 kernel.

---

### Post by Kronos_neko on 2012-06-24
EY, I was searching the forum and I think this is the right place...
I have ubuntu 12.04 amd64 with unity default, gnome 3 and lxde and everything was working fine but in the afternoon the windows seemed a little bit slow so I used alt+f2+r to restard gnome-shell but it didn't restart...
then i rebooted...and nothing
I used dpkg-reconfigure...nothing
tried to reinstall(purge and remove)...and nothing

I think it has something to do with the gir1.2-clutter-1.0 libclutter-1.0-0 packages but when I try to update them a lot of unresolved dependencies come out and for most than I try I cannot get them upgrades x_x

Can someone help?

---

### Post by VinDSL on 2012-06-24
> **Kronos_neko said:**
> Can someone help?
Maybe...  ;)

> **cariboo907 said:**
> Nope, out of the box alpha 1 with regular updates. [...]
Alrighty, then.

I just did a wash, rinse, and restyle:

```
sudo ppa-purge ppa:ricotz/testing
sudo apt-get update
sudo apt-get upgrade
```

GS is working again -- using it as I type.

Thanks!

---

### Post by ronacc on 2012-06-24
@ vindsl  I like your conky can you post it ?

---

### Post by VinDSL on 2012-06-24
> **ronacc said:**
> @ vindsl  I like your conky can you post it ?
Thanks!

There's a link to it, in my sig (below).  

Data dump is in Post #4  ;)

Still working on the LXDE .conkyrc -- haven't published that yet, but...

The only difference is the spacing, alignment, and font size(s).

---

### Post by Starks on 2012-06-24
Still no luck.

```
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found

```

---

### Post by MacUntu on 2012-06-24
> **Starks said:**
> I have a lot of hotkeys set to Alt and I really don't care for the stupid HUD coming up whenever I press it.

Disable it?

---

### Post by ronacc on 2012-06-24
My G-S loads ok on either my updated precise or my 2 day old daily , I've got the launcher and can start progs but shortly thereafter the system locks up to the point that a hard reset is required . this only occurs with the 3.5.0-1 kernel 3.4.0-5 is ok . my sys is amd64 / nvidia .

---

### Post by bash on 2012-06-28
> **Starks said:**
> Still no luck.

```
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
    JS ERROR: !!!   Exception was: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found
    JS ERROR: !!!     message = '"Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/dateMenu.js"'
    JS ERROR: !!!     lineNumber = '5'
    JS ERROR: !!!     stack = '"@/usr/share/gnome-shell/js/ui/dateMenu.js:5
"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring GnomeDesktop, version none: Typelib file for namespace 'GnomeDesktop' (any version) not found

```

I had that same error for a long time as well. First I thought something broke in one of ricotz updates, but it just persisted on. Managed to fix it in the end. 

Sadly forgot how exactly. From what I remember seemed to be some strange bug related to previously installed and upgraded versions. Because I remember just booting up a live cd and installing the shell there and it worked without a problem. Might just try that and if it works, quickly reinstall the system.

---

### Post by Kronos_neko on 2012-06-28
I found what it was causing the error but cannot fix it yet...
the gnome shell extensions modified the configuration folder of gnome but I cannot find where exactly yet
even with that, neither uninstalling the extensions the issue is fixed

---

