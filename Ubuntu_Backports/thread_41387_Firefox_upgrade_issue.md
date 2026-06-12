---
title: "Firefox upgrade issue"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by tzutolin on 2005-06-13
Hi, everyone

I did a fresh install today and everything was just fine (glad to see smeg is backported now :-)  until i opened the update manager: 

it said that the following packages will not be upgraded:
mozilla-firefox
mozilla-firefox-gnome-support

Is there a way to solve this little problem?

Thanks!!   :)  :)

---

### Post by ubuntu_demon on 2005-06-13
open a terminal and type (without the $):

$ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support

---

### Post by Gustav on 2005-06-13
Or you can type:

sudo apt-get dist-upgrade

---

