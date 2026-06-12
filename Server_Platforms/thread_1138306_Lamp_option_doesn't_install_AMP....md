---
title: "Lamp option doesn't install AMP..."
date: 2009-04-26
forum: Server Platforms
---

### Post by kevin1162 on 2009-04-26
Hi,

For the last year i've been setting up ubuntu lamp servers throughout my company. I'm not an expert but i can run through the install and get everything setup.

Since i started doing this whenever i select the LAMP 'server option' i only get the base system installed (no apache mysql php). I would either go through and setup everything individually or more recently use 'tasksel install lamp-server'.

I'd really like to not have to do the extra steps after setting up the system, can anyone tell me why only the base system is installing?

The hardware i'm using is different everytime... Dell 1U servers, dekstop grade PC's, workstations, etc... Some new, some old, but same result every time. No lamp.

Thanks

---

### Post by Vegan on 2009-04-26
I know, I had to manually install the LAMP stack after the basic installation. No big deal, but it takes time when you have 10,000 machines to set up.

---

### Post by kevin1162 on 2009-04-28
well at least i'm not the only one...lol

---

### Post by BKonkle on 2009-04-28
Take a look at Tasksel - you can simply run `sudo tasksel` and select LAMP server, and it should automatically install the stack through apt-get and configure it for you.

[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by kevin1162 on 2009-05-06
that's what i've been doing after running the install CD.

Works fine but i would like the LAMP option to install when i select it during setup, was wondering why it doesn't.

---

