---
title: "Firestarter at boot?"
date: 2005-12-30
forum: Server Platforms
---

### Post by dalani on 2005-12-30
I installed and run Firestarter on my Hoary manually whenever I connect on the internet. But since I set up computer to automatically connect at bootup, I did the same for Firestarter. Unfortunately I get an error message of not having sufficient permission to start the firewall that way (i always have to type in a password to start it). WHat is the procedure for Firestarter startup at boot without typing the password??

---

### Post by cstudent on 2005-12-30
Firestarter actually runs as a daemon in the background all the time. The GUI is usee primarily for setting up your configuration. Once set you don't really need to run the GUI. But you can find out how to get it to start up automatically in the Firestarter FAQ.

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by 23meg on 2005-12-30
It's the best practice to just let Firestarter run as a daemon without enabling its GUI. Whenever you need to tweak its settings, hit alt+f2 and type ```
gksudo firestarter
```make the changes and quit. It will keep protecting you unless you explicitly stop it.

---

### Post by dalani on 2005-12-31
Thanks for clearing that up for me. You reminded me Firestarter was just a front end to Iptables etc...
Mark this solved

---

