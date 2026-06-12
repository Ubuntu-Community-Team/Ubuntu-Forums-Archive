---
title: "Temporarily not load U1 at startup"
date: 2012-11-14
forum: Ubuntu One (CLOSED)
---

### Post by RogerDavis on 2012-11-14
How do I TEMPORARILY stop Ubuntu One from loading at startup while I test something?

And the flip side - Once done testing, how do I make it start up again?

---

### Post by Isamu715 on 2012-11-24
Go to "Startup Appliations..." and uncheck Ubuntu One. Once done testing you can simply check it back. If you don't have U1 listed in your startup apps open a terminal and run the following line:
       ```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```Some other apps that are hidden by default will also appear in "Startup Applications...".

---

### Post by RogerDavis on 2012-11-25
OK, that answers my original question, but after I entered the line into Terminal it showed MANY programs.  Were these all running in the background before, and I just didn't know it?

---

### Post by Isamu715 on 2012-11-25
Yes, they are all startup programs that get launched on login.

---

