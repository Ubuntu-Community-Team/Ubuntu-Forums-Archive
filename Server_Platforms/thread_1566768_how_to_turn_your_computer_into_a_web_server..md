---
title: "how to turn your computer into a web server."
date: 2010-09-02
forum: Server Platforms
---

### Post by brandenmikal on 2010-09-02
i would like to know the easiest way to setup your old computer to be used as a web server for building and hosting your own website and domain using ubuntu. how do i go about that?

---

### Post by kevin11951 on 2010-09-02
> **brandenmikal said:**
> i would like to know the easiest way to setup your old computer to be used as a web server for building and hosting your own website and domain using ubuntu. how do i go about that?

install ubuntu and:

```
tasksel
```

Then select "LAMP Server" and go...

---

### Post by lolzywut on 2010-09-02
Install apache
```
sudo apt-get install apache2
```

---

### Post by lisati on 2010-09-02
This thread is probably better off being in the "server platforms" section. 

kevin11951 is on to the right idea: If you have an already functiong system, install LAMP or similar is a good place to start.

You might want to consider installing the Ubuntu server edition. More information can be found here: [http://www.ubuntu.com/server](http://www.ubuntu.com/server)

For domain names, many of us here use [no-ip.com]("http://www.no-ip.com/") or [dyndns.com]("http://www.dyndns.com/")

---

### Post by brandenmikal on 2010-09-03
> **lisati said:**
> This thread is probably better off being in the "server platforms" section. 

kevin11951 is on to the right idea: If you have an already functiong system, install LAMP or similar is a good place to start.

You might want to consider installing the Ubuntu server edition. More information can be found here: [http://www.ubuntu.com/server](http://www.ubuntu.com/server)

For domain names, many of us here use [no-ip.com]("http://www.no-ip.com/") or [dyndns.com]("http://www.dyndns.com/")

sorry i didn't post in the proper place, i didn't even know there was a "server platforms" section. 

i took your advice and considered obtaining a copy of Ubuntu server edition. i will most likely use that with lamp and/or apache. i'm not sure which is better to go with since i'll be a beginner on this route.

wish me luck! :)

btw, thanks for the domain sites; i'll be looking into them soon.

---

### Post by kevin11951 on 2010-09-03
> **brandenmikal said:**
> sorry i didn't post in the proper place, i didn't even know there was a "server platforms" section. 

i took your advice and considered obtaining a copy of Ubuntu server edition. i will most likely use that with lamp and/or apache. i'm not sure which is better to go with since i'll be a beginner on this route.

wish me luck! :)

btw, thanks for the domain sites; i'll be looking into them soon.

LAMP is a software stack made up of: Apache (Web Server), MySQL (Database), and PHP (Web Programming).  So, you should install the LAMP stack if you plan to run anything more than HTML.

---

