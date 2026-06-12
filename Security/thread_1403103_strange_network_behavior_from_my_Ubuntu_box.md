---
title: "strange network behavior from my Ubuntu box"
date: 2010-02-09
forum: Security
---

### Post by TheAlien on 2010-02-09
I was going trough my network log this night, and discovered that my Ubuntu box has made several connections to rkhunter.sourceforge.net. It starts with this:

*DNS Standard query A rkhunter.sourceforge.net*

Then followed by a lot of TCP and HTTP traffic.

Is this normal? Why is my computer connecting to this address and transferring data now and then?

I have rkhunter installed from the software repository.

---

### Post by FuturePilot on 2010-02-09
rkhunter periodically checks for and downloads updates to the database files. Sounds normal to me.

---

