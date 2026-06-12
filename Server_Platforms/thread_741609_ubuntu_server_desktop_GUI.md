---
title: "ubuntu server desktop GUI?"
date: 2008-03-31
forum: Server Platforms
---

### Post by fondoo on 2008-03-31
i just successfull installed ubuntu server edition v7.04. 
i was able to install gnome desktop and now i would like to go back to the command line interface. is it possible to flip back? thanks in advance.

---

### Post by Dr Small on 2008-03-31
Maybe?
```
sudo apt-get remove ubuntu-desktop --purge
```

---

### Post by fondoo on 2008-04-05
sudo apt-get remove ubuntu-desktop --purge

did not work. any idea?

rebooted the server and still got the desktop gui

---

### Post by daniel of sarnia on 2008-04-05
yeah that's because ubuntu-desktop is a meta package. Not the actual desktop and xorg packages, just a link to install them. You're going to have to uninstall all of the packages by hand as far as I know. Unless you installed them with aptitude. Then you can sudo aptitude remove ubuntu-desktop but if you used apt-get you have to remove all the different packages which I'm not sure what all the gnome packages are but if you do something like ```
 sudo apt-get remove xorg* 
```
That should stop the gui from starting.

Oh and you might also want to 
```
 sudo apt-get autoremove 
```

After and that might get ride of unused packages related to X so

---

