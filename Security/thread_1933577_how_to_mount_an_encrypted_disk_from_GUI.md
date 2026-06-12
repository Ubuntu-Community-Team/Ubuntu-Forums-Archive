---
title: "how to mount an encrypted disk from GUI"
date: 2012-02-29
forum: Security
---

### Post by alfonso78 on 2012-02-29
Hi,

I normally mount my encrypted disk from command line.

Something like:

```
sudo cryptsetup luksOpen /dev/md0 storage
sudo mount -t ext4 /dev/mapper/storage /storage

```

but I wanted to be able to do with a GUI. This is how I did it.

First, install eMount: 
[http://emount.sourceforge.net/?page=download](http://emount.sourceforge.net/?page=download)

then, start the root version and create an entry for your encrypted device.

if you look at the terminal script I wrote earlier
- Source should be "/dev/md0" 
- Volume Label is a string of your choice

I think the rest is quite straight forward.

Once you added a new entry, right click on it a choose "Properties", then "Options" then check "Mount when eMount starts" (if this is what you want)

Finally, to automatically get the prompt every time you log-in, type the following in a terminal window:

sudo cp /usr/share/applications/emount\(super-user\).desktop /etc/xdg/autostart

[COLOR="Red"]**Please disregard the last step. Sometimes after login the GUI hangs until you kill emount if you put it in the auto-start folder.**[/COLOR]

finally, enjoy. :popcorn:

---

