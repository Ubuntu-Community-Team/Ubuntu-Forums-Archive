---
title: "Kernel 3.13.0-4.19 &amp; epiphany 3.10.3 eat /run/shm 100%!?"
date: 2014-01-20
forum: Ubuntu Development Version
---

### Post by tista on 2014-01-20
Today I've found this issue:

When browsing with epiphany-browser 3.10.3, it got to eat /run/shm rapidly...:(
While seeing web pages up to 10 or 15, suddenly epiphany crashed, and I found that ephy eats shm 100%.
And this case would happen only if we run trusty with kernel 3.13.0-4.19 current kernel, but I confirmed that it didn't happen with latest intel-next kernel 3.13.0-997, they kept shm under 1% usage.

Did anyone see such weird thing?
Should I post some results of ipcs or so?

[Machine]
* Dell Vostro-A90 (employing i945GME)

[PPAs added]
* gnome3-team/gnome3-staging
* ricotz/testing

[Desktop environments]
* Gnome-shell 3.11.4
* Flashback session with current metacity, gnome-panel
* Pantheon with gala, plank, wingpanel etc

Best Regards,
Tista

---

### Post by tista on 2014-01-25
Guys,

Today I've confirmed this issue seemed to be solved by updating... ;)
Then the combination of linux-image 3.13.0-5.20 and epiphany-browser 3.11.3+git20140122 could do that.

Best Regards,
Tista

---

