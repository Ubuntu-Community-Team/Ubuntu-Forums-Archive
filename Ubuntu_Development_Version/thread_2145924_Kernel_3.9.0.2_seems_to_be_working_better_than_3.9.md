---
title: "Kernel 3.9.0.2 seems to be working better than 3.9.0.1"
date: 2013-05-16
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-05-16
Have NOT tried a Cold Boot Up yet (where I had my problem) but Ubuntu Kernel 3.9.0.2 seems to be working better than 3.9.0.1 on my 2010 Dell Inspiron Zino 400 HD Desktop PC! Just FYI!

---

### Post by kevpan815 on 2013-05-18
Cold Boot on 3.9.0.2 works just fine on my 2010 Dell Inspiron Zino 400 HD PC! :-)

---

### Post by cariboo on 2013-05-18
I just updated my atom powered netbook, I got a kernel panic while installing the kernel, but after going into recovery mode, and selecting dpkg from the menu, and letting it do it's thing. I selected resume, it booted to a black screen without even a flashing cursor. A reboot solved all the problems, and I'm posting from it now.

```
cariboo@redstone:~$ uname -a
Linux redstone 3.9.0-2-generic #6-Ubuntu SMP Tue May 14 16:55:36 UTC 2013 i686 i686 i686 GNU/Linux
```

and

```
cariboo@redstone:~$ gnome-shell --version
GNOME Shell 3.9.1
```

The only problem I'm running into, is I keep trying to bumping the mouse up against the left edge, even though I'm running Gnome shell on this system. I guess I've been spending to much time in Unity. :-D

---

### Post by jerrylamos on 2013-05-19
This is an Intel Atom N455 in an Acer Aspire One D255E running Saucy amd64 updated to 19 May O.K.  cli df is showing disk space usage growing so I may try an install soon.  purge linux-image, linux-headers and remove, autoremove don't get rid of all the oudated code.  Out of laziness I'm running unity just because that's the way ubuntu comes lately.  - I'm no unity fan.

---

### Post by zika on 2013-05-19
> **jerrylamos said:**
> This is an Intel Atom N455 in an Acer Aspire One D255E running Saucy updated to 19 May O.K.  cli df is showing disk space usage growing so I may try an install soon.  purge linux-image, linux-headers and remove, autoremove don't get rid of all the oudated code.  Out of laziness I'm running unity just because that's the way ubuntu comes lately.  - I'm no unity fan.In cases like that I break my principles and use gtk-orphan...

---

### Post by jerrylamos on 2013-05-19
> **zika said:**
> In cases like that I break my principles and use gtk-orphan...

Thanks....I took a look at gtkorphan.  Looks like I could wipe out saucy pretty easily if I didn't know what I was doing, which is the case.  Install cleans things up and is a no-think solution....might turn up a ubiquity bug who knows.

---

### Post by cariboo on 2013-05-19
> **jerrylamos said:**
> This is an Intel Atom N455 in an Acer Aspire One D255E running Saucy amd64 updated to 19 May O.K.  cli df is showing disk space usage growing so I may try an install soon.  purge linux-image, linux-headers and remove, autoremove don't get rid of all the oudated code.  Out of laziness I'm running unity just because that's the way ubuntu comes lately.  - I'm no unity fan.

It's only natural that the size of your install grows, as you use it. First off if you do updates, all the downloaded packages are stored in /var/cache/apt/archives, it's easy enough to get rid of them, as for unused kernel and obsolete packages, synaptic shows you them, and easily allows you to remove them. One other thing to keep in mind, is that logging is always active, and the logs themselves get larger each time you use the system. Logrotate, installed by default, creates archives, daily, or weekly depending on the log. You can remove those without incurring any problems.

---

### Post by zika on 2013-05-19
> **jerrylamos said:**
> Thanks....I took a look at gtkorphan.  **Looks like I could wipe out saucy pretty easily if I didn't know what I was doing**, which is the case.  Install cleans things up and is a **no-think** solution....might turn up a ubiquity bug who knows.Yes, that is true, but... I do not mind thinking, though... I'm not sure that my thinking produces desirable result but at least I do try... ;)

---

### Post by pqwoerituytrueiwoq on 2013-05-19
3.9.0.3 is out
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.3-saucy](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.3-saucy)

---

### Post by pqwoerituytrueiwoq on 2013-05-24
3.9.4 is out
[http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.9.4-saucy](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.9.4-saucy)

---

