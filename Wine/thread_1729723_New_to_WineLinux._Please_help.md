---
title: "New to Wine/Linux. Please help"
date: 2011-04-15
forum: Wine
---

### Post by Samurai123 on 2011-04-15
I got my windows application to install(well it said it installed). but where does wine store these files? like in what directory did it just go to? in the terminal what directory do I go to? or if you can just tell me exactly where it is I would appropriate it. 

I was thinking that it would be installed to some type of "C" drive, but I guess Linux does not work that way.

---

### Post by cogadh on 2011-04-15
Normally, Wine installs things in its own "fake Windows" directory. In your home directory, there will be a hidden directory called ".wine", within that directory you will find a "dosdevices" directory (symlinks to your CD drive, hard drive, etc.) and a "drive_c" directory, which as it sounds, is a replication of the standard "C:" drive found in Windows. All the things you install will be found there. However, if you are just trying to run your application, when you installed it, it should have created shortcuts in the Applications menu under Wine.

---

### Post by Samurai123 on 2011-04-15
Thanks for the reply. 

But the problem is, now that I have installed the program it does not actually run. I will go to Applications>wine>programs>the program I want to run. but nothing happens. My HDD light will flicker, but after a little bit nothing happens. This is why I was hoping to figure out where the wine directory is, so maybe I could open it using the terminal. Because I realized that it only installed with the terminal as well.

---

### Post by cogadh on 2011-04-15
Ah, that makes sense. In that case what you want to do is open a terminal, change directories to where the app is installed, then "Wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/<app installation path>
wine <executable name>.exe
```
You'll get Wine's error output from that, which may explain what is happening.

However, before you go to all that trouble, it might be worth it to know what you are trying to run; it's entirely possible that whatever it is just doesn't work in Wine or requires some very specific configuration changes to run. Wine's Application Database can be extremely helpful with this. It is a database of testing results from Wine users for nearly everything that we (as a group) have tried to run, including how-to's and configuration steps required to get the best results: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

