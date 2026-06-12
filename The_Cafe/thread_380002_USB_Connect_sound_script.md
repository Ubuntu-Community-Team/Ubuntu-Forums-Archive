---
title: "USB Connect sound script"
date: 2007-03-09
forum: The Cafe
---

### Post by om3ganet on 2007-03-09
Hi!

First post here, so please forgive me if this is in the wrong category, or this has already been done! (I looked, found nothing... maybe its already available somewhere?)

I've wanted to make Ubuntu play a sound whenever I connect a USB device to my computer (like in XP), but I found no such option anywhere, so I decided to write a script that would play a sound for when a USB device was connected, and another sound when disconnected.

Firstly you'll need to have sox installed (gives the console *play* command):

```
sudo apt-get install sox
```

And requires two files (I copied and renamed from Windows XP) named insert.wav and remove.wav in /usr/share/sounds/ (can edit script to change location, etc). Place the following in a file, give it exec access (chmod, etc):

```

#!/bin/sh

# USB Insert / Remove sound script
# Created by om3ganet (msn@om3ga.net)
# --------------------------------------------------
# This script could probably be cleaned up, and add checking
# of unrecognised usb sounds (and play fail noise)

# change this if you want sounds elsewhere
SNDDIR=/usr/share/sounds/;
# check frequency (default 0.25 seconds)
CHECKFREQ=0.25


# Do not edit below this line
# --------------------------------------------------
DEVCOUNT=`lsusb | wc -l | awk '{ print $1 }'`
OLDDEVCOUNT=$DEVCOUNT;

while(true) do
  sleep $CHECKFREQ;
  DEVCOUNT=`lsusb | wc -l | awk '{ print $1 }'`
  if [ $DEVCOUNT -gt $OLDDEVCOUNT ]; then
    play `echo $SNDDIR`insert.wav;
  else if [ $DEVCOUNT -lt $OLDDEVCOUNT ]; then
    play `echo $SNDDIR`remove.wav;
  fi fi
  OLDDEVCOUNT=$DEVCOUNT;
done

```

You should be able to add it to your startup scripts (System->Preferences->Session in Gnome) so it works once you login.

This is my first script using bash, and first useful script for Ubuntu, so If anyone has any comments, or wish to point me to an already existing alternative, feel free to. I've barely tested this, it just seems to work.

Cheers,
om3ganet

---

### Post by ~LoKe on 2007-03-09
My computer makes a sound when I plug USB devices in.

---

### Post by om3ganet on 2007-03-09
It does? Never had that happen when I use Ubuntu (with Gnome). What are you using, or what does it specifically?

-om3ganet

---

### Post by tageiru on 2007-03-09
That is a horribly ugly way of doing it. You should look into udev events instead.

[http://www.reactivated.net/writing_udev_rules.html#external-run](http://www.reactivated.net/writing_udev_rules.html#external-run)

---

### Post by DoctorMO on 2007-03-09
yea just wait for hal to give your script the heads up to play the sound, code it into the main gnome sound daemon and it'll be a very useful addition to the future sound config.

If you want some example python scripts using dbus/hal let me know.

---

### Post by om3ganet on 2007-03-09
Thanks for the info, I thought they'd be a better way of doing it, but I wouldn't know unless I asked I guess. I'll look at the udev event stuff quite soon too, it appears to be a much more cleaner way of doing it, and in regards to example scripts, I'd love to see some for it :D

---

### Post by 3esmit on 2010-10-26
Hello dear community,

Is there a script using events that does that? 
Something to install in repositories?

I opened a brainstorm about it: [http://brainstorm.ubuntu.com/idea/26216/](http://brainstorm.ubuntu.com/idea/26216/)

I believe this is really important to new users.

---

