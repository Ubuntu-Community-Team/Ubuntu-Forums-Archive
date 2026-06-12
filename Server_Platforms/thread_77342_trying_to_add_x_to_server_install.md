---
title: "trying to add x to server install"
date: 2005-10-16
forum: Server Platforms
---

### Post by bmckenna on 2005-10-16
Extreme linux newb here.

I installed the server version of ubuntu b/c I didn't need things like openoffice, I plan on using the machine for ftp purposes, mostly, as well as maybe a mailserver and a few other things.

When i did 
sudo apt-get install xserver-xorg it seemed to install fine, but wouldn't boot afterwards. It hung on "starting periodic task scheduler" or something like that and ctrl-c wouldn't do anything, nor would anything else. So, I did a fresh install of the server version. Read another post, which said to run apt-get install ubuntu-desktop but that has all the stuff I don't want, like openoffice and such. Any suggestions on how to get x, gnome, gui, etc, running on my machine would be much appreciated.

Bryan

---

### Post by bmckenna on 2005-10-16
edit: "starting periodic command scheduler"

did that again, after I updated the kernel to 686, without trying to install xserver. now, just won't boot at all.

---

### Post by bmckenna on 2005-10-16
found a guide to install x and make a lightweight server at [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

only problem with this is after i'm done installing everything, system still won't boot, hangs at "starting periodic command scheduler".

---

### Post by bmckenna on 2005-10-16
worked through the issue on my own. i'm pretty sure it was a problem with xserver-xorg not installing properly...mods, you can delete this thread if you like.

---

