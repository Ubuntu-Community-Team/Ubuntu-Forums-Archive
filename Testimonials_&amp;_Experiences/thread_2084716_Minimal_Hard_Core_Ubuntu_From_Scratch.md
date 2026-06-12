---
title: "Minimal Hard Core Ubuntu From Scratch"
date: 2012-11-16
forum: Testimonials &amp; Experiences
---

### Post by pompado on 2012-11-16
I notice after playing around that you can use any kind of distribution and only install neassery pakages ... with out window manager or other cosmetics.

Like Ubuntu ... i run 12.10 server edition install with out installing anything then the base pakages and with out server option.

Then you get a minimal Ubuntu distribution and just have to run apt-get to install and costomize your Ubuntu.

I run Ubuntu with Fluxbox and Openbox and it works great.
Just some simple and easy apt-get commands and you are done with a new Ubuntu distribution with your own needs and likes.

After a clean minimal install you just run the following ...

sudo apt-get install xorg
sudo apt-get install fluxbox

or

sudo apt-get install xorg
sudo apt-get install openbox
sudo apt-get install opconf
sudo apt-get install obmenu

Now if you want to start system with "startx" you have to add "apt-get install xinit" or if you would like a login prompt you add "apt-get install xdm"

I BELIVE that you can run any Linux Distribution with server edition, Fedora, RedHat, Mint or any other based upon the same principals i mention above.

My self use old computers that i got tierd on and put new life into them using this kind of minimal installations.
And i can experiment with no limits and learn alot as newbie that way.

HOPE you find this topic to gain you some inspiration.

---

### Post by ibjsb4 on 2012-11-16
The server edition contains server packages.  The mini.iso can give you a console only install without extra packages.

---

### Post by ajgreeny on 2012-11-16
Yes, much easier with [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by NikTh on 2012-11-16
> **ibjsb4 said:**
> The server edition contains server packages.  The mini.iso can give you a console only install without extra packages.

> **ajgreeny said:**
> Yes, much easier with [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Agreed +1 

Just last night I build one , with Unity . ubuntu-destkop --no-install-recommends :) 
Much lighter

---

### Post by Bucky Ball on 2012-11-16
> **ibjsb4 said:**
> The server edition contains server packages.  The mini.iso can give you a console only install without extra packages.

+1. Roll your own ... from scratch. You can also go here:

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

