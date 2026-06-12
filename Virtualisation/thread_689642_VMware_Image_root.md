---
title: "VMware Image root"
date: 2008-02-06
forum: Virtualisation
---

### Post by wlindy27 on 2008-02-06
Hi guys, I got fed up with Windows and decided to try and use Ubuntu Linux :) The only problem is I just downloaded VMware player and used an Ubuntu image. When I boot it up, I think I go into the ROOT command line. I thought that Ubuntu had a desktop similar to Windows. Was I wrong or is there a command I have to use to get to it? Thanks guys!

---

### Post by jan quark on 2008-02-06
to try ubuntu 

download the LIVE CD (Desktop CD) and boot from it

[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

it will load entirely into the ram and will not affect your current system

---

### Post by wlindy27 on 2008-02-06
I tried to use one of those live Cd's but it never booted up even after I changed my BIOS settings. Any tips for my current problem?

---

### Post by emarkd on 2008-02-06
A default Ubuntu installation should boot into a graphical login screen.  Are you getting an error message or does it just boot cleanly to a login prompt?

---

### Post by lamalex on 2008-02-06
What's the location you got your VMware image from? Maybe you got a server version.

---

### Post by wlindy27 on 2008-02-06
It boots clearly into a prompt.

I got it from [www.thoughtpolice.co.uk](www.thoughtpolice.co.uk)

And I think Iamalex just solved my problem, it does say that it is a server edition so I am going to guess I need a desktop version right?

---

### Post by emarkd on 2008-02-06
You can get a desktop version, or you could try installing the ubuntu-desktop package from Synaptic.  I believe that contains everything you'd need to get a graphical interface going.

---

### Post by jan quark on 2008-02-06
yes the site offers only server editions

download the desktop edition from here

[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

or install the desktop with the terminal
```

sudo apt-get install ubuntu-desktop
```

---

