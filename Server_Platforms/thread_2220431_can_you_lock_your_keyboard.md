---
title: "can you lock your keyboard"
date: 2014-04-27
forum: Server Platforms
---

### Post by killernat on 2014-04-27
The other day when I had to do some work on my server i was greeted with a load of random gibberish for the login prompt (due to some furry animal that runs around my apartment all day) and is a common occurrence in my household. Anyway I was hoping; is there a way to lock the keyboard on log out like windows can do for its workstations i.e. use ctrl+alt+del to gain access to the login prompt any help or advice is much appreciated

like so:
[IMG]http://www.lehigh.edu/classrooms/publicsiteguide/CTRLALTDEL.jpg[/IMG]

---

### Post by CharlesA on 2014-04-28
Unplug the keyboard. ;)

I have my server's keyboard sitting at an angle so they can't walk on it.

---

### Post by killernat on 2014-04-28
yeh I kind of do the same but it tends to get knocked over even if I stuff it behind the monitor.

---

### Post by Zwisel on 2014-04-28
Try this:

1. sudo apt-get install vlock
2. man vlock
3. vlock
or
4. vlock -a

Hope this helped.

---

### Post by CharlesA on 2014-04-28
> **Zwisel said:**
> Try this:

1. sudo apt-get install vlock
2. man vlock
3. vlock
or
4. vlock -a

Hope this helped.

I think that requires you to be logged in.

@OP: This might help:
[http://unix.stackexchange.com/questions/75155/locking-console-input-without-screen-blanking](http://unix.stackexchange.com/questions/75155/locking-console-input-without-screen-blanking)

#2 in particular - unloading the usbhid modules - if the server is headless that would stop the usb keyboard from working without unplugging it.

---

### Post by LHammonds on 2014-04-28
Unplug the keyboard.  If you need to access the server, just use PuTTY or plug the keyboard back in when you need it.

I wouldn't install anything extra on the server to do something like this.  I follow the KISS principle. ;)

LHammonds

---

### Post by grumblebum2 on 2014-04-28
Get your keyboard id....
```
xinput list
```

```
/usr/bin/xinput --disable [COLOR="#696969"]<id>[/COLOR]
/usr/bin/xinput --enable [COLOR="#696969"]<id>[/COLOR]
```
***Make sure you have a way to enable without a keyboard.

---

### Post by CharlesA on 2014-04-28
> **LHammonds said:**
> Unplug the keyboard.  If you need to access the server, just use PuTTY or plug the keyboard back in when you need it.

I wouldn't install anything extra on the server to do something like this.  I follow the KISS principle. ;)

LHammonds

Yep. :)

---

### Post by volkswagner on 2014-04-28
Hot plugging should only be done with a USB keyboard.

PS2 connections are not hot-pluggable, and should not be used as such.

---

### Post by killernat on 2014-04-28
> **volkswagner said:**
> Hot plugging should only be done with a USB keyboard.

PS2 connections are not hot-pluggable, and should not be used as such.


exactly why I don't unplug it, it is a ps/2 keyboard.

all of the suggested solutions are helpful but not rely useful because it would mean I would need to ssh in to enable the keyboard before I go to login at the machine, and 90% of the time when I need to work at the machine is because I cant ssh to it (or I happen to be on that end of the apartment). so I am looking for that a key combination to unlock the login and automatically lock when you logout 
[IMG]http://www.lehigh.edu/classrooms/publicsiteguide/CTRLALTDEL.jpg[/IMG]

it is a headless server 

the vlock looks quite useful but only to lock your active session (without using screen)

---

