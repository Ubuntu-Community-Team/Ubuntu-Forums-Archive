---
title: "Controling Banshee from handheld"
date: 2010-12-24
forum: The Cafe
---

### Post by ki4jgt on 2010-12-24
Have:
- Banshee
- Zipit (Z2) <Rootnexus's Userland>
- Wireless headphones

I just got a pair of wireless headphones I've hooked them up to my laptop and now I need to be able to control Banshee all around my house. Can I setup Ubuntu to allow me to control Banshee from a web gui on the Zipit?

---

### Post by jerenept on 2010-12-24
> **ki4jgt said:**
> Have:
- Banshee
- Zipit (Z2) <Rootnexus's Userland>
- Wireless headphones

I just got a pair of wireless headphones I've hooked them up to my laptop and now I need to be able to control Banshee all around my house. Can I setup Ubuntu to allow me to control Banshee from a web gui on the Zipit?

Don't know about Banshee, but XBMC can be used in this manner. [http://xbmc.org/](http://xbmc.org/)

---

### Post by ki4jgt on 2010-12-24
> **jerenept said:**
> Don't know about Banshee, but XBMC can be used in this manner. [http://xbmc.org/](http://xbmc.org/)

I love XBMC, but they didn't do random the last time I checked them out.

---

### Post by mozzwald on 2010-12-25
Banshee has command line options like --next and --prev. Checkout the manpage for all the command line options. 

[http://manpages.ubuntu.com/manpages/lucid/man1/banshee.1.html]("http://manpages.ubuntu.com/manpages/lucid/man1/banshee.1.html")

On a basic level you could ssh into the machine running banshee and use these commands.

You can also run those commands from a webpage if you have apache installed on your banshee server. Checkout this page that tells you how to run shell scripts from web pages.

[http://www.cyberciti.biz/faq/run-shell-script-from-web-page/]("http://www.cyberciti.biz/faq/run-shell-script-from-web-page/")

---

### Post by gnomeuser on 2010-12-25
Banshee supports LIRC and has a dbus interface for control (in fact I believe there is a standard for this we support). I think we can find a solution that will work for you.

---

### Post by forrestcupp on 2010-12-25
I thought maybe you figured out how to control a Halo Banshee with your handheld. :)

---

