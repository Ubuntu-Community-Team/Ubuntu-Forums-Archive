---
title: "Problem with my Kmix 2.6.1 sound controller"
date: 2009-12-31
forum: Ubuntu Studio
---

### Post by macjinlan on 2009-12-31
Hey everyone. I got problem when i try to change the volume in music player (i use amarok). The "master" input not work at my situation, and the PCM sound input is working for main sound regulator when i listen music. How i can fix this? Main sound channel - "master" input, but this not help me. I need for the main sound regulator "master" input, not PCM. 

Happy New 2010 all supporters. Good luck. I use Ubuntu 8.04 with KDE graphic.

---

### Post by SuperSonic4 on 2009-12-31
What is shown when you run ```
alsamixer
```

You may need to register a global shortcut for kmix

---

### Post by macjinlan on 2009-12-31
> You may need to register a global shortcut for kmix
How i can made this?
Here is my alsamixer settings.
[IMG]http://s59.radikal.ru/i166/0912/59/38adf4a5bc60.jpg[/IMG]

---

### Post by SuperSonic4 on 2009-12-31
Your alsamixer looks fine, no trouble there

To register a global shortcut go to Kmix and configure shortcuts, for example I mapped vol up to vol up on the keyboard

---

### Post by macjinlan on 2009-12-31
Now it work fine. But when i try change the volume in the player the "PCM" input controller go down or up. How i can fix this? I need to get main "master" input volume controller. thanks.
P.S Always i use console player like xmms2

---

### Post by SuperSonic4 on 2009-12-31
Can you change the master channel in Kmix? This is done by going to settings --> Select master channel

---

### Post by macjinlan on 2009-12-31
There is "master" input for the main channel. But this not really work.
I mean, when i try to use amarok and use mouse sound regulator the Kmix controller working normal. But when i use console player and hot keys, the volume is bumping in da Kmix master input.

---

### Post by macjinlan on 2009-12-31
Also can anyone help me with MOC 2.2.4 player installation? I dont understand the manual "how to"

> How to install it?
--------------------------------------------------------------------------------

Generic installation instruction is included in the INSTALL file. In short, just
type:
	./configure
	make
And as root:
	make install

Under FreeBSD, NetBSD, and possibly other systems it is required to run the
configure script this way:
./configure LDFLAGS=-L/usr/local/lib CPPFLAGS=-I/usr/local/include

Thanks.

---

### Post by SuperSonic4 on 2009-12-31
I don't get what you mean about amarok and console players but then I've been up since 7am (it's now 1am) so I'll check in the morning

Surely moc is in the repos ```
sudo apt-get install mocp
```


Nonetheless that instruction is largely self-explanatory

```
./configure && make && sudo make install
```



If you compile a lot of things it might be easier to give your user permission to use /usr/bin/make without asking for a password but I digress

---

### Post by macjinlan on 2009-12-31
Okay. 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mocp

Gm..

---

### Post by SuperSonic4 on 2009-12-31
```
sudo apt-get install moc
```

---

### Post by macjinlan on 2009-12-31
Big thanks for the support. 

Now i got 1 not fixable problem with console players and sound controller: Console players use the keyboard control, so when i try to get more sound in my console player (cmus or MOC), my Kmix controller "Master" input is bumping, but i need only console player sound "bumping". 

Sorry but my english not at very good skill. Good night..

---

