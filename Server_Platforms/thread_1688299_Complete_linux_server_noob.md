---
title: "Complete linux server noob"
date: 2011-02-15
forum: Server Platforms
---

### Post by phraq on 2011-02-15
Ok So i have been using ubuntu for awhile on my home machine and decided to go with Ubuntu server for poweredge server however I need to be able to download some programs from the internet, for starts is there anyway to load a browser to the server and if not is there a way to control it from a windows 7 laptop.

Thanks For the help

Trying to get Cpanel for this machine but need to get to the website to do it.

---

### Post by James78 on 2011-02-15
CPanel requires licensing, so unless you've already paid an outrageous sum for it... You can use Webmin GPL which is very powerful and 100% free.
[http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)

As for controlling from another computer, you can just use SSH. Just select OpenSSH to install when installing the server (or just...
```
sudo tasksel
<select OpenSSH and click Ok>
```

Then use PuTTy on Windows to login to OpenSSH.

Please note a few things when using SSH. Do not allow the root user to login (suggested to turn off AllowRootLogin option on SSH, and well as keeping the root user disabled on Ubuntu), disable passworded logins (that way people can't bruteforce your server), and enable keyed authentication (that way you can still get into your server, which is the whole point of having SSH in the first place). Also, changing the default port to something else helps out a lot too.

OpenSSH community help
[https://help.ubuntu.com/community/SSH?action=show&redirect=SSH%2FOpenSSH](https://help.ubuntu.com/community/SSH?action=show&redirect=SSH%2FOpenSSH)

---

### Post by cariboo on 2011-02-15
There are several text based browsers available in the repositories. Elinks comes to mind off the top of my head.

---

### Post by psusi on 2011-02-15
Better yet, just look up the URL for what you need to download, and download it with wget.

---

### Post by lukeiamyourfather on 2011-02-15
I would suggest wget if you just need to download things from the internet. If you want to actually browse then you can connect with SSH and X tunneling (ssh -X user@host) which will allow you to run graphical applications on the server but the graphics will be sent to the SSH client. This only works if the client has X (e.g. not Windows).

---

### Post by psusi on 2011-02-15
> **lukeiamyourfather said:**
> This only works if the client has X (e.g. not Windows).

There are X servers you can get and install on Windows.

---

### Post by tgalati4 on 2011-02-15
Or you can dual boot.  Install the desktop version and treat the machine as a normal desktop.  Keep the server install on a separate partition or separate disk.  When you get more experience, you can simply copy over the webpages and other services to the server when you no longer need the training wheels.

There's not as much of a performance penalty running the graphical desktop, especially on faster and dual core machines.  There's a big gap from Ubuntu desktop to server and it's not learned in a day.

---

### Post by James78 on 2011-02-15
Whenever I needed to do a little command line webpage browsing, I've always used w3m.

---

### Post by phraq on 2011-02-15
Thanks for all the help especially the webmin bit lol that should save atleast 475

---

### Post by James78 on 2011-02-15
No problem. Webmin/Virtualmin/Usermin + OpenSSH is almost all you'll ever need. ;)

---

### Post by lukeiamyourfather on 2011-02-15
> **psusi said:**
> There are X servers you can get and install on Windows.

Good point. :-k

---

