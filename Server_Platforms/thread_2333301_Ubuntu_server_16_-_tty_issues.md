---
title: "Ubuntu server 16 - tty issues"
date: 2016-08-09
forum: Server Platforms
---

### Post by androbase16 on 2016-08-09
Hi
I'm quiet new to ubuntu server , I installed it and then I added a desktop-gui 
I made some changes so it will auto login (necessary) and then bashrc runs "startx" and the gui launches (also necessary)
when it finishes to boot it has a print from tty1 announcing "ubuntu tty1" & "ubuntu@user auto login"
I have to delete those outputs , I tried to change the getty but it doesnt help/
how can I totally delete those outputs printings (I have to keep the server structure with the gui and the auto-login and )
Thank's ahead for helping:-)

---

### Post by mastablasta on 2016-08-09
why do you need a gui on server? if you need a gui for administrating the server then use something like for example Ajenti or Zentyal (webguis) instead.

if you need a gui why not just install a desktop version and then add what services you need? you can install something lighter like Xubuntu or Lubuntu (or just a windows manager) & tick the autologin on boot option.

---

### Post by steeldriver on 2016-08-09
It may be that you simply need to 

```

exec startx

```

to *replace *the (auto) login shell with your GUI session

OTOH if you want to auto login with a GUI, it's probably simpler to install a display manager such as lightdm and configure *that *to autologin instead - that way, you don't need to mess with getty

---

### Post by androbase16 on 2016-08-11
Where to run this command? currently I run startx in ~/home/user/.bashrc 
should I replace something?
Thank's ahead for helping

---

### Post by howefield on 2016-08-11
Thread moved to the "*Server Platforms*" forum.

---

### Post by Vegan on 2016-08-11
PUTTY can connect to a server in a data center, no need for a GUI that wastes memory that could be better used for a database etc

---

### Post by steeldriver on 2016-08-11
Putting startx in your ~/.bashrc sounds like a bad idea - doesn't that try to start a session within a session anytime you invoke a non-login bash shell (such as starting a terminal emulator in the desktop session)?

IF you want to do that, at least put it where it's only going to be invoked ONCE for a LOGIN shell e.g. ~/.profile

THEN if you use 

```

exec startx

```

in place of 
```

startx

``` 

then once you exit the X session you will be logged out, I think

---

### Post by darkod on 2016-08-12
When your first steps on a linux server are to install a GUI and configure auto-login then you know you are doing something wrong... Maybe if explained what you are trying to achieve and why a login is necessary the community could advise you what is best.

The beauty of servers, especially linux, is that they don't need GUI and login to serve their services. Even windows servers don't need someone to be logged in to work... Hence most servers are headless.

---

### Post by MAFoElffen on 2016-08-12
Remember to breath. 

Agreed that user might have needed//wanted a Desktop with a few server services might have save him a lot of work and steered him from the trouble he is having now.

Immaterial of the security and overhead of installing a GUI full-time on a server... I do server and virtualization support. I do Install & update support.  I do hardware and dev support. Some of you might also know that I've been supporting Xorg and the Linux Graphics Layer, since... before Linux was born. So, I see this as a broken desktop.

To the OP:
The one step you forgot was to install the Desktop Manager (with It's graphical login). That is the piece that ties that all together and links the boot process to auto-start into that Graphical Login. And the Desktop Manager then point from the login to the Window Manager. 

If you then wanted to use it as a server with a console bootup, then add another startup boot menu option, appending "text" into the kernel boot line. 

Putting your "startx ... command in .bashrc is just technically wrong by way of protocol. <-- that would only count against you if your were trying to get your LPIC cert's or working for someone, where it matters... functionally, it would work about the same if you put in as the last line of .bashrc, but... The "correct" file to put that, if you needed to would be in your .profile file . If the user adds a ~/.bash_profile or ~/.bash_login file, then bash will ignore that file as an override. But that is just for legacy reasons. The reason to put it in that file is for order of precedence, and the order those files are read. ".profile" is read after .bash, .bashrc, .bash_profile or .bash_login (if it either exists). then the .profile file.

---

