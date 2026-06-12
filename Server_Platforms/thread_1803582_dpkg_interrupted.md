---
title: "dpkg interrupted"
date: 2011-07-13
forum: Server Platforms
---

### Post by kirthi on 2011-07-13
sudo apt-get install mysql-client-5.1

This code showed me the error that dpkg is interrupted.
 What should I do. Wha does it mean by dpkg?

---

### Post by sikander3786 on 2011-07-13
Nothing miserable, I hope. Just post us the output of these commands:

```
sudo dpkg --configure -a
sudo apt-get install -f
```

These commands are intended to fix any broken packages that might have left un-configured after dpkg being interrupted.

---

### Post by kirthi on 2011-07-13
linux@linux-laptop:~$ sudo dpkg --configure -a
[sudo] password for linux: 
Setting up skype (2.2.0.35-0lucid1) ...

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for python-support ...
linux@linux-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-utidylib python-gtkmozembed libtidy-0.99-0 python-feedparser
  python-rsvg python-evolution python-chardet
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.



Thanks for reply.That's what I got.

---

### Post by sikander3786 on 2011-07-14
There was one un-configured package i.e. skype. Running the commands configured it and didn't return any errors so we can expect that everything is just fine. If there are errors with the installation of any packages later, you can just post those and let us take a look.

For now, I guess it is solved ;)

---

