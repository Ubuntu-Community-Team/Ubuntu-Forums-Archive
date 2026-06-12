---
title: "Removing all graphical applications without fresh install"
date: 2008-04-28
forum: Server Platforms
---

### Post by danielsbrewer on 2008-04-28
I have a machine that I use to use as a desktop, but now use as a server.  I upgraded to Hardy today and realized that there is a huge amount of cruft on the machine that I do not need - specifically x.org and the related items.

What is the best way to get rid of x.org and all the graphical applications?

The answer is probably a fresh install but I would prefer an alternative as it is not that easy to get physical access to the machine.

---

### Post by Oldsoldier2003 on 2008-04-28
> **danielsbrewer said:**
> I have a machine that I use to use as a desktop, but now use as a server.  I upgraded to Hardy today and realized that there is a huge amount of cruft on the machine that I do not need - specifically x.org and the related items.

What is the best way to get rid of x.org and all the graphical applications?

The answer is probably a fresh install but I would prefer an alternative as it is not that easy to get physical access to the machine.

One answer to your problem would be use aptitude to remove ubuntu-desktop ```
sudo aptitude remove ubuntu-desktop
```
Of course this assumes its a pure gnome desktop and you never installed KDE or XFCE.

Then after completing this uninstall xorg.

if you've run a mixed environment a less elegenat solution would be to follow the instructions on pychocats website for a [pure kde environment]("http://www.psychocats.net/ubuntu/purekde") (or gnome of xfce environment). The pages show you how to remove all the fluff and desktop aps if you used apt-get instead of aptitude to install additional desktops. 

Then once again remove xorg.

The only catch to this is that if you have gone and installed additional programs you'll have to root them out manually. you can use dpkg to find them ```
dpkg --get-selections >sometxtfile
``` 

Not the most elegant solution and it will take some work but thats the best I can come up with for your particular problem. 

I hope this has been helpful and perhaps someone else can chime in with a better method.

---

