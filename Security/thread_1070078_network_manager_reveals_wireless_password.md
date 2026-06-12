---
title: "network manager reveals wireless password"
date: 2009-02-14
forum: Security
---

### Post by fuchur on 2009-02-14
I am concerned about the following "feature" of network manager.

If I click on edit connections it is possible to reveal my current wifi-password (by clicking  "show password"). 

However, the institution I am connecting to uses PEAP, where my wifi-password is  at the same time my password for all kinds of services there (e-mail, ....). Thus I would preferred if it would not be so easy to see for anyone who gets access to my computer. 

Is there a way to hide that permanently. If not, where should I file bug reports etc.. No, I cannot convince the institution to use a different wifi-authentication-system, and of course I am too lazy not to save it at all.

Looking forward to any hints on how close this "security hole"

---

### Post by dplecto on 2009-02-15
Why don't you disable the networkmanager and use manual config ? Setup a shell script that sets up wireless network using iwconfig - have it setup with global execute permission but rw only to root. Hell you can even add the macchanger in the script so that it mods the mac each time you restart the network.

---

### Post by bodhi.zazen on 2009-02-15
I suggest two things.

First you should file a bug report against network manager.

Second, part of your solution needs to focus on physical access. Physical access is a BIG problem.

---

### Post by fuchur on 2009-02-15
Thanks for the above recommendations. 
The problem with manual login is that I also use other networks and thus NM makes things very convenient. 
I will file a bug.

---

