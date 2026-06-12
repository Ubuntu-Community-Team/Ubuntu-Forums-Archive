---
title: "What do you install or configure first?"
date: 2010-06-12
forum: The Cafe
---

### Post by robofighter on 2010-06-12
When you get a get a new distro from a clean install, what is the first thing you install or configure.

I setup the samba server, setup my IMs, install the firefox plugins and extensions, etc

---

### Post by Legendary_Bibo on 2010-06-12
The GIMP, and then I go through the games in the software center to look for things I'd play when I'm bored. I also install Compiz and get it running.

---

### Post by NightwishFan on 2010-06-12
A few tidbits and utilities, and I replace some of the default applications with ones of my preference. I install Exaile, The Gimp, Cheese, Liferea, and Guake. I set up my grub with acpi_backlight=vendor to work around my laptop screen issues, and set my swappiness to 100.

---

### Post by cariboo on 2010-06-12
I usually install several packages, the first I always select is the ubuntu-restricted-extras meta package.

---

### Post by bigsmitty64 on 2010-06-12
> **cariboo907 said:**
> I usually install several packages, the first I aleays select is the ubuntu-restricted-extras meta package.
+1  Then Gimp, then adblock plus.

---

### Post by Frogs Hair on 2010-06-13
Install first , firewall is #1 .

---

### Post by CharlesA on 2010-06-13
SSH is probably #1, followed by Samba and VirtualBox.

---

### Post by cariboo on 2010-06-13
> **Frogs Hair said:**
> Install first , firewall is #1 .

The firewall is installed by default, it's called iptables. What you're installing is a frontend to set the rules. Ufw is also installed by default, so unless you need to set the rules via a gui, you don't need to install anything.

BTW, unless someone steps up to the plate and starts updating the unmaintained Firestarter, it will no longer work once Maverick is released.

---

### Post by NightwishFan on 2010-06-13
Pity, I liked firestarter. I use gufw now though since I only need to edit basic rules.

---

### Post by WinterRain on 2010-06-13
updates

---

### Post by garvinrick4 on 2010-06-13
Check the partners repository is installed, install the ubuntu-restricted-extras && update && upgrade and do my panels and edit menus and appearance while terminal is doing its thing. I believe in maverick I had to install gparted, compiz config, startupmanager, gpa and set up printer. It was ready to go in 20 minutes or so. Oh and import my bookmarks into firefox.

---

### Post by dtfinch on 2010-06-13
One of the first applications I install is Blender, but before doing so:

First I fix that hugely annoying mouse cursor speed issue caused by Ubuntu being almost hardcoded for 400dpi mice while mine is 1600dpi, by adding 'xinput set-prop "PS/2+USB Mouse" "Device Accel Constant Deceleration" 2' to my startup applications.

Then install proprietary nvidia driver and get dual monitors working.

Then I change the appearance to something really easy to look at:
Window border: Gilouche (package gnome-theme-gilouche)
Controls: Clearlooks
Fonts: 9pt Liberation *
Visual Effects: None
Wallpaper: Flow.png (package gnome-backgrounds)
Cursor: still DMZ-White, but with busy cursor removed.

[[img]http://techminati.net/misc/desktop-thumb.jpg[/img]](http://techminati.net/misc/desktop.png)

---

### Post by lisati on 2010-06-13
A habit I started with 7.04 (the first Ubuntu I used) was to install updates first. This happened to "cure" a couple of driver problems on the machine I was using at the time. 

Then, if I'm on a machine using legacy grub and if I remember, it's time to tinker with menu.lst. 

Next comes firefox plugins, email, and any files that I might had backed up. 

After that, it's whatever I remember, whenever I remember it, e.g. codecs, restricted extras, etc.

---

