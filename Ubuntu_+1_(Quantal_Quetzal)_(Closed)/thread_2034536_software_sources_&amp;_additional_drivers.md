---
title: "software sources &amp; additional drivers"
date: 2012-07-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by flipper T on 2012-07-28
hi, just took plunge into 12.10, been using ubuntu excelusively for 3 yrs now.

have searched for answer but with no luck.

Q. when i select software sources from system settings, nothing happens. i know this is an unresolved bug, but it stop me from running the Additional Drivers dialog, which i believe is now there. so, is there another way of accessing the Additional Drivers screen ?

on the plus side, laptop seems to be running cooler when streaming flash in 12.10 than it did in 12.04. perhaps due to new nvidia driver.

---

### Post by mc4man on 2012-07-28
update your current source & then check & see if aptdaemon is at this version - aptdaemon (0.45+bzr848-0ubuntu1)

If not upgrade to it thru whatever method you like, (i use synaptic only) & software sources will then  open, may take several seconds or more, just wait...

---

### Post by flipper T on 2012-07-28
hi,

i have that version of aptdaemon installed according to synaptic.

on the off chance, i reinstalled it & re booted, but nothing has changed.

---

### Post by ventrical on 2012-07-28
Had the same prob here. But software sources just took time to load. (too long). Also, can't close SS with (x) button. Have to use (Close) button.

---

### Post by flipper T on 2012-07-28
some further info:

when i select software sources, something called "software-properties-gtk" runs for a few seconds & then stops.

if i run software-properties-gtk from a terminal i get

```
jk@jk-M570RU:~$ software-properties-gtk
gpg: /tmp/tmp5b1b97/trustdb.gpg: trustdb created
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 180, in __init__
    self.show_drivers()
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1280, in show_drivers
    widget = Gtk.Label("{}: {}".format(self.devices[device]['vendor'], self.devices[device]['model']))
KeyError: 'vendor'

```

don't know if this helps

---

### Post by mc4man on 2012-07-28
Sounds like this bug though not I'm affected here
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1028388](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1028388)

---

### Post by flipper T on 2012-07-28
as stated in op, i am aware that its a known issue, just wanting to know if there is a temp hack to get to Additional drivers.

probably my fault for not being clear...

---

### Post by mc4man on 2012-07-28
> **flipper T said:**
> 

probably my fault for not being clear...
Not really - there was a similar break that just got fixed the other day, now or concurrently to the previous is another one though this may only affect some.
(not aware here of any workaround.

---

### Post by cwsnyder on 2012-07-28
Your sources list is in /etc/apt/sources.list , but should have nothing to do with loading 'Additional Drivers', if you are speaking of the proprietary graphics drivers.  You were asked if you wanted to install the proprietary graphics drivers during the installation.

---

### Post by flipper T on 2012-07-28
hi, not a fresh install, a dist upgrade from 12.04.

looks like i will just sit tight for a few days, rocking gently as i repeatedly chant "its only alpha, its only alpha". has worked in the past :)

thx for help.

ps not graphic driver issue, as stated in op.

---

### Post by arpanaut on 2012-07-28
If you know what driver you want to use you can install with synaptic.
On the left select Origin then above that select quantal/restricted
then you can choose to install the driver you need.

That should work for you, No?

---

### Post by philinux on 2012-07-29
> **cwsnyder said:**
> Your sources list is in /etc/apt/sources.list , but should have nothing to do with loading 'Additional Drivers', if you are speaking of the proprietary graphics drivers.  You were asked if you wanted to install the proprietary graphics drivers during the installation.

Additional drivers has now been moved to within software updater. Those also causes the 15 second delay for it to open

---

### Post by jerrylamos on 2012-07-29
> **ventrical said:**
> Had the same prob here. But software sources just took time to load. (too long). Also, can't close SS with (x) button. Have to use (Close) button.

"Software Sources" deadly slow here.  I did a dpkg install of Opera so I don't care about Software Sources, but Software Sources got in the way with a v-e-r-y l-o-n-g update.  Just to add one link??  No clue what Software Sources is so slow or what Software Sources is even doing.

Jerry

---

### Post by cwsnyder on 2012-08-03
This _IS_ only an alpha! It is not meant to work as your main machine.

That said, because I also run Debian, I am used to updating from the CLI using ```
sudo apt-get update && sudo apt-get dist-upgrade -y
```which still works in Quantal.  That is how I am getting by with my VM of Quantal.

---

