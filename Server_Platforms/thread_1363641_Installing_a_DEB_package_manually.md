---
title: "Installing a DEB package manually"
date: 2009-12-24
forum: Server Platforms
---

### Post by Vegan on 2009-12-24
OK I downloaded a DEB file for Webmin no problem from my Windows box on the /public on the Linux machine, I can navigate there but before I jump in, I wanted to general info on installing all DEB files for future reference.

Then with in hand I can search for details on the program de jour.

---

### Post by spikoley on 2009-12-24
Check out this great article on [**How To Install *ANYTHING* In Ubuntu**]("http://amitech.50webs.com/installing/index.php.html").

---

### Post by CharlesA on 2009-12-24
If you've got a GUI just double click it.

If you are using just the terminal you can run dpkg, but you'll have to install to dependencies manually.

---

### Post by HighCommander540 on 2009-12-25
> **Vegan said:**
> OK I downloaded a DEB file for Webmin no problem from my Windows box on the /public on the Linux machine, I can navigate there but before I jump in, I wanted to general info on installing all DEB files for future reference.

Then with in hand I can search for details on the program de jour.

Yeah, its damn easy if you have the package:

```
 sudo dpkg -i "path to .deb file"
```

*clap* And ya done.

---

### Post by Vegan on 2009-12-25
What is the default port that Webmin comes up with, or do I need to add it to Apache2 manually?

---

### Post by CharlesA on 2009-12-25
Webmin uses port 10000 by default.

There is no need for apache to be installed.

---

### Post by Vegan on 2009-12-25
I have apache installed and in use as the machine is my web server, as well as a bunch of other things.

This is why I asked as I wanted to dodge conflicts.

So should I add a subdomain to my vhosts so it comes up as webmin.contract.developer.dyndns.biz or somthing like that?

---

### Post by CharlesA on 2009-12-25
I do not know. I always just access it at [https://ip.address.goes.here:10000](https://ip.address.goes.here:10000)

---

### Post by Vegan on 2009-12-25
I use that approach myself, just thought I could use a URL and add it to the hosts etc.

---

