---
title: "change greeter"
date: 2016-03-21
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2016-03-21
I've been testing Ubuntu and Ubuntu Mate. So far I prefer UM, but I like the greeter used in Ubuntu.
Is it possible to use unity greeter in UM? and if so how?

---

### Post by pfeiffep on 2016-03-23
No takers???

BUMP

---

### Post by Joo_Alves on 2016-03-23
I'm also interested in this.. I've recently installed the MATE desktop but the greeter is quite visually outdated (from my point of view). Not a big problem though :P

---

### Post by dino99 on 2016-03-23
if mate does not have it hardcoded (like ubu) then you can purge the original one and install an other of your choice (maybe the metapackage needs to be removed for doing it)

---

### Post by Frogs Hair on 2016-03-23
There was an application in Gnome 2 and also Mint Mate called startup manager . This application had an appearance tab for customizing the greeter , but I don't know if it is or was available in U Mate.

---

### Post by deadflowr on 2016-03-23
Simply install unity-greeter; I'd recommend installing it with the no-install-recommends flag to minimize unity-ification.

Then if it doesn't default to it, create a simply lightdm.conf file pointing to unity-greeter.
I'd create a file called 99_myconfig.conf inside a directory called /etc/lightdm/lightdm.conf.d
(you might need to make the lightdm.conf.d directory if none exists.
Then simply add this
```
[Seat:*]
greeter-session=unity-greeter
```
(if [Seat:*] doesn't work, replace with [SeatDefaults])
Also for a quick note,
here are the depends it needs:
> Depends: dconf-gsettings-backend | gsettings-backend, libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libcairo2 (>= 1.14.0), libcanberra0 (>= 0.2), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.16.2), libido3-0.1-0 (>= 13.10.0daily13.06.19), libindicator3-7 (>= 0.4.90), liblightdm-gobject-1-0 (>= 1.15.2), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libx11-6, libxext6, upstart
and here are the extra recommends that would be installed if you don't add the exclude command:
> Recommends: unity-settings-daemon, indicator-application, indicator-datetime, indicator-keyboard, indicator-power, indicator-session, indicator-sound, network-manager-gnome, lightdm


even with no recommends it will install a few (only a few) extra packages.
It's up to you to determine if those extra packages are worth it.

For what it's worth I did this on a mate in a vm and nothing changed in terms of the behavior of mate.
And it did not add any extra desktop's, like unity.

---

### Post by pfeiffep on 2016-03-25
Thank you Deadflowr, I'll try this first on my HP tower which has Ubuntu installed with Mate desktop added.

---

