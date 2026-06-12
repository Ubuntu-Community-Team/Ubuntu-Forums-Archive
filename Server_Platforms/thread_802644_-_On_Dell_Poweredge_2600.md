---
title: "- On Dell Poweredge 2600"
date: 2008-05-21
forum: Server Platforms
---

### Post by anup09 on 2008-05-21
Hey everyone, Ive previously used Ubuntu 7.04 on my Notebook Dualbooted with Windows XP. I have yet to try 7.10

K, for my problem
I have just recieved a Dell Poweredge 2600 from a company that no-longer needs it. It came to me with Windows 2000 Family Server Edition and really want to get rid of that, Ive managed to turn this thing on and get to the Logon Page, but it requires to be put into the network domain which im not on their anymore, so i planned to refortmat it.

Ive looked into putting Ubuntu or Windows XP on it but i have no experience with server platforms as their are more then 1 drive and i dont really know what im doing when it comes to servers.

Can anyone please list the steps in order to get Ubuntu 7.10 Running on this server, Thanks Alot.

---

### Post by molotov00 on 2008-05-21
What exactly are you looking for?

The upgrade process involves running update-manager. This site describes it quite well (although it's an update TO 7.04 the commands should be the same). If you look on Google harder than I did I'm sure you can find an updating tutorial for your versions.

[http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/](http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/)

---

### Post by anup09 on 2008-05-21
Thanks for your quick reply, but thats not exactly what im Looking for,

The Server currently has windows 2000 server, and i need instructions on how to put Ubuntu on their.

---

### Post by molotov00 on 2008-05-21
Ok. I was confused bc you said you previously had Ubuntu on your dual-booted laptop.

This is probably the documentation that will be most useful to you:

[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)

Within that, here are the installation instructions:

[https://help.ubuntu.com/8.04/switching/installing.html](https://help.ubuntu.com/8.04/switching/installing.html)

I should also point out that if you install Ubuntu for the desktop (with a GUI) then it can perform server functions. Or you can install Ubuntu for the server and not have a point-and-click desktop interface. Finally, you could opt to install Ubuntu within VMWare, which will cause Ubuntu to appear within a window in Windows. This might be a good route if you are looking to familiarize yourself with the OS.

EDIT: One last thing. The term 'server' is loosely used. You can install any version of Ubuntu and have it share files, etc. What makes the 'server' version a server is the fact that it includes NOTHING that isn't needed. This makes it more secure and a better starting point for experienced users. For you, I'd just install Ubuntu or Kubuntu (which have a GUI) and experiment with the command line. Down the road you could delve deeper.

M

---

### Post by anup09 on 2008-05-21
> **molotov00 said:**
> Ok. I was confused bc you said you previously had Ubuntu on your dual-booted laptop.

This is probably the documentation that will be most useful to you:

[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)

Within that, here are the installation instructions:

[https://help.ubuntu.com/8.04/switching/installing.html](https://help.ubuntu.com/8.04/switching/installing.html)

I should also point out that if you install Ubuntu for the desktop (with a GUI) then it can perform server functions. Or you can install Ubuntu for the server and not have a point-and-click desktop interface. Finally, you could opt to install Ubuntu within VMWare, which will cause Ubuntu to appear within a window in Windows. This might be a good route if you are looking to familiarize yourself with the OS.

EDIT: One last thing. The term 'server' is loosely used. You can install any version of Ubuntu and have it share files, etc. What makes the 'server' version a server is the fact that it includes NOTHING that isn't needed. This makes it more secure and a better starting point for experienced users. For you, I'd just install Ubuntu or Kubuntu (which have a GUI) and experiment with the command line. Down the road you could delve deeper.

M
Thanks also for they reply, but I put in a Live Ubuntu 7.04 CD and i choose the first option to start or install ubuntu. On the first time, it just lagged out and had some weird line in the midle of screen, on the second time, a loading linux kernel window came up, then abunch of random strings of lines, and it just froze there..

What should i do?

---

### Post by barichardson5727 on 2008-05-21
> **anup09 said:**
> Thanks also for they reply, but I put in a Live Ubuntu 7.04 CD and i choose the first option to start or install ubuntu. On the first time, it just lagged out and had some weird line in the midle of screen, on the second time, a loading linux kernel window came up, then abunch of random strings of lines, and it just froze there..

What should i do?


So..did the you get this error during the installation, or did this error occur on the first boot after completing the installation? Also, it may be helpful to see the output from the "random strings of lines" as this can prove to be very helpful in determining the cause of failure. 

I might add that since you are running this installation on a PE2600 you will probably have better luck installing the server version of ubuntu since that version will probably install better on hardware with components such as raid controllers and other server specific hardware. Once installed, the main difference in the server version is that there will be no graphical interface, but its only a single command to install the full graphical environment.

---

### Post by hazyumps on 2008-12-30
not that this is too much help months later, but i just installed the newest 8.1 on a dell poweredge 2600 today. It was rediculious how easy everything was - raid was auto configured, detected both xeon processors w/o ne issues - really - congrats and appreication to ALL who made ubuntu possible :)

---

