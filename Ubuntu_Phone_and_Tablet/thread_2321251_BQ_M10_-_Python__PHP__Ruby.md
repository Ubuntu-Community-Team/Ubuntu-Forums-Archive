---
title: "BQ M10 - Python / PHP / Ruby?"
date: 2016-04-21
forum: Ubuntu Phone and Tablet
---

### Post by Terence_Eden on 2016-04-21
Just got my M10.  I was expecting to be able to run scripts on the device - not heavy development, but basic stuff.

I can't seem to find Python in the app store, and it won't apt-get.  Same for PHP and Ruby.

What do I need to do in order to run normal Ubuntu stuff on the tablet?

---

### Post by mhaneferd on 2016-04-21
I have the same question. 

I understand that terminal applications do not work well on touch, but the programs that not require terminal should be allowed to install and run...
The apt-get update,upgrade and install does not work since the apt and some other files are read protected??

I tried these commands, but no luck:
sudo su
mount -o rw,remount,rw /system
-> Then got this message back: mount: cannot remount /dev/loop0 read-write, is write-protected

Anyone have some tips??

---

### Post by bernard-godard on 2016-04-21
I am also interested in this but I have not tried it yet so I cannot tell you the procedure.
But the author of this blog [https://eyskens.me/aquaris-m10-hd-ubuntu-edition-review/](https://eyskens.me/aquaris-m10-hd-ubuntu-edition-review/) did so he might be able to help you.

Also the reply by Evergreen in [http://askubuntu.com/questions/600065/consequences-of-using-apt-get-in-ubuntu-touch](http://askubuntu.com/questions/600065/consequences-of-using-apt-get-in-ubuntu-touch) seems to answer your questions and mine too.

---

### Post by John_Harris on 2016-04-22
I've explored a little, tentatively.

sudo mount -o rw,remount,rw /

That worked. I could then 

sudo apt-get update
sudo apt-get upgrade

but I can't

sudo apt-get install build-essential

because of unmet dependencies.

sudo apt-get -f install

would upgrade unity8 but won't run because it involves a cross-partition backup attempt ("Invalid cross-device link").

I'm going to stop at that stage and think a bit, I don't know the way the mounts have been done on this system. I'm assuming I'll end up doing a factory reset in a while.

---

