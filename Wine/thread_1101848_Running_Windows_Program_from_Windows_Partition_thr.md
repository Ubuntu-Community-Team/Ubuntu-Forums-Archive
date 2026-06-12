---
title: "Running Windows Program from Windows Partition through Ubuntu"
date: 2009-03-20
forum: Wine
---

### Post by arod529 on 2009-03-20
I have XP Pro dual booting with Ubuntu 8.1 on the same drive. I've heard of Wine but being that I am broke at the moment, is there any possible way to run a windows program from my windows partition through Ubuntu?

---

### Post by hikaricore on 2009-03-20
Uhhh WINE is free.
You can run some programs like WoW without having to reinstall them but for best results you should.

Check here to see if your apps are supported: [http://appdb.winehq.org](http://appdb.winehq.org)

Moved to the WINE forum.

---

### Post by arod529 on 2009-03-22
Opps.

I clicked on the CrossOver link at the top of this page:
[[COLOR="RoyalBlue"]http://www.winehq.org/download/[/COLOR]]("http://www.winehq.org/download/")

Clicking on the Ubuntu link gives me instructions for a online install.

Can I do it without an internet connection (since I don't have one on the linux box)? If so how?

---

### Post by arod529 on 2009-03-22
Nevermind I figured it out.

1. Go to sight [[COLOR="Blue"]http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wine[/COLOR]]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wine")
2. Under the title *Package Wine* click link for your version of Ubuntu
3. Scroll to the bottom of the screen and click the link for your architecture.
4. Pick a mirror sight and download the .deb file.(Some directly give the save dialog and others don't. I used the *mirrors.kernel.org/ubuntu* entry under North America.)
5. Go back to the page were you chose your architecture.(Page in step 3)
6. Under the title *Other packages related to wine* find *libaudio2*.
7. Repeat step 3 and 4 for *libaudio2*.
8. In linux, double click on *libaudio2*, install it, then the wine's .deb file, and install it.

(If you try to intall the .deb file for wine first it may result in an error for dependencys. The only dependency I had was *libaudio2*. Do steps 5 through 7 for any dependancy errors.)

---

### Post by GepettoBR on 2009-03-23
> **arod529 said:**
> Nevermind I figured it out.

1. Go to sight [[COLOR="Blue"]http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wine[/COLOR]]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wine")
2. Under the title *Package Wine* click link for your version of Ubuntu
3. Scroll to the bottom of the screen and click the link for your architecture.
4. Pick a mirror sight and download the .deb file.(Some directly give the save dialog and others don't. I used the *mirrors.kernel.org/ubuntu* entry under North America.)
5. Go back to the page were you chose your architecture.(Page in step 3)
6. Under the title *Other packages related to wine* find *libaudio2*.
7. Repeat step 3 and 4 for *libaudio2*.
8. In linux, double click on *libaudio2*, install it, then the wine's .deb file, and install it.

(If you try to intall the .deb file for wine first it may result in an error for dependencys. The only dependency I had was *libaudio2*. Do steps 5 through 7 for any dependancy errors.)

OR you can open a terminal window and type ```
sudo aptitude install libaudio2 wine
``` and accomplish the exact same thing.

---

