---
title: "Server GUI"
date: 2008-03-04
forum: Server Platforms
---

### Post by 3xpl0it on 2008-03-04
Hello,

Today I wanted to try something new, and I would like to make a mini server, and I am not quite sure where to start.  I was wondering what Linux distro is the best for hosting (besides red hat).  I would go ubuntu, but ubuntu doesn't have a GUI for the server edition (or does it).  Could someone point me in the right direction?

Thanks in advance,
-3xpl0it

---

### Post by igknighted on 2008-03-04
Servers aren't well served by GUIs.  You can install a GUI on Ubuntu server (or really any linux server), but there are no GUI configuration tools.  You should look at a web based console such as Webmin, or even Cpanel.  These will let you work on the server in a GUI environment, but not have to have the overhead of an xserver.

---

### Post by rapiscan on 2008-03-04
I agree with igknighted, and I think you should look into webmin for your server administration needs (cpanel has licensing fees).

However, if you would still like a gui for generally interfacing with the os (like moving files around, installing new packages through the GUI, etc.), then you can install the GUI using:

```
sudo aptitude install gnome-desktop
```

---

### Post by FakeOutdoorsman on 2008-03-04
Take a look at this recent thread:
[Why Ubuntu Server?]("http://ubuntuforums.org/showthread.php?t=707325")

Talk about servers and why GUI is unnecessary, and a little about Ubuntu and some other distros as servers.

---

### Post by steveneddy on 2008-03-04
I use Ubuntu Server 6.06 LTS and because I'm no expert at Unix administration, I installed gnome-desktop to I had a familiar interface while administering my server.

The server is a web server, music, movie and file server that does work for me online and while at home.

So use Ubuntu Server Edition of your choice and enjoy the work that all of the dev's did for us.

It works great.

I turn the GUI on when I log on by logging in on the text screen and then typing

```
sudo /etc/init.d/gdm start
```

and stop it when I want to log off by

```
sudo /etc/init.d/gdm stop
```

then I log out totally by typing 

```
exit
```

Once the GUI is turned off the power consumption and CPU temp both go down.

---

### Post by 3xpl0it on 2008-03-04
Thank you very much for your suggestions!  I will look into both the web based apps and possibly the gui method.

Thank you very much again, more suggestions are definitely welcome :)
-3xpl0it

---

### Post by Dr Small on 2008-03-05
I run a server and installed xorg and icewm to use occasionally, but found I don't need it very often with ssh on it ;)

Dr Small

---

