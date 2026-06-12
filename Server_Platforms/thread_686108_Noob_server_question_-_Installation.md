---
title: "Noob server question - Installation"
date: 2008-02-02
forum: Server Platforms
---

### Post by Swerve1000 on 2008-02-02
Hi,

My situation is that I have used Ubuntu desktop 7.10 for a few weeks now dual booted with XP, love it.

Now I want to install Ubuntu to work as a server on my machine, allowing me to connect via SSH from work, and also host my personal sites with Apache/PHP/MySQL.

I have just re-installed XP, and have two empty partitions left. 

My question is should I install one copy of Ubuntu 7.10 to use as my 'normal' GUI operating system AND Ubuntu server edition to run the server I want to create, OR can I just install one copy of 7.10, and have that provide the server/SSH features I seek?


Any advice is greatly appreciated.

Many thanks :)

---

### Post by rockrocket on 2008-02-02
Hi Swerve1000,

-  My question is should I install one copy of Ubuntu 7.10 to use as my 'normal' GUI operating system AND Ubuntu server edition to run the server I want to create, OR can I just install one copy of 7.10, and have that provide the server/SSH features I seek?

If you are worried about space, (less than 8gb to 10gb i recommend) go with the server edition, but your going to have to install a graphical environment. Look at  this site really help me out. 

[http://www.psychocats.net/ubuntu/desktopeffects](http://www.psychocats.net/ubuntu/desktopeffects)

But if your not worried about 8gb to 10gb, i suggest installing the gnome (desktop) It's awesome.

Also you can merge those two partions with gparted if you decide to use the desktop and you can run servers on the desktop and its much easier. I highly recommend using ubuntu desktop as your os





I do, I learn, and i love it.

---

### Post by Swerve1000 on 2008-02-02
That does help, many thanks :) 

Going to be setting this up in the morning.

So no problem with connecting via SSH to the desktop version?

---

### Post by rockrocket on 2008-02-02
no you shouldn't have any problems the desktop is basically the same, just the server is for people with low memory.


-So no problem with connecting via SSH to the desktop version?


 I taught the exact same thing when i downloaded it, but it's not. Also if you still want to install the server you can get the desktop afterwards by just putting 

sudo apt-get update
sudo apt-get install ubuntu-desktop

ps: i still recommend you getting the desktop makes things much easier

---

