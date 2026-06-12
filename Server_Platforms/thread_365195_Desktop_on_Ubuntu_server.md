---
title: "Desktop on Ubuntu server"
date: 2007-02-19
forum: Server Platforms
---

### Post by r1ckh on 2007-02-19
If there is anyone new to Ubuntu server and would like to have a desktop installed on the server but not have it run as soon as it starts up look no further!!!.

I searched for a while to figure out how to do this (because I am also new to Ubuntu in fact i am new to linux and to a server dedicated O.S.) but found no specifics, what you need to do is  log in as normal onto the text based terminal then type: 

sudo apt-get install ubuntu-desktop

which installs the full desktop package then once its all installed which may take a while, you need to type:

sudo apt-get remove gdm

which then removes the bit that starts it automatically once that is done to start the desktop all you have to do is type:

startx

you cant shut down the p.c. form here like in normal linux or windows you have log out which takes you back to the command line terminal then type:

sudo shutdown -h now

I hope this is of help to some one I know how difficult it can be when your just starting out, if you can drop me an email and let me know if it helped you solve your problem.


P.S. Thanks to everyone at Ubuntu for putting in the effort to make and continually develop these operating systems it is defiantly bringing linux to the masses and is very much appreciated by me and I'm sure by many around the world!

---

### Post by lenwood on 2007-02-19
This is pretty cool, and is definitely helpful for getting files onto the system, etc. I just installed Webmin on my new server yesterday, and its also very helpful for administrative tasks and settings. The installation was pretty straight forward. If you're interested, do a search for the howto here on UbuntuForums.

Thanks,
Len

---

