---
title: "is this possible, reguarding apt-get"
date: 2006-05-01
forum: The Cafe
---

### Post by DoeRayMe on 2006-05-01
Is it possible to do something like this?

> apt-get --purge remove debconf-i18n | install debconf-english

so it purges the first and installs the second?

(i dont use Synaptic and Adept only allows you to choose purge, if it has'nt been selected for removal ;) )

---

### Post by harisund on 2006-05-01
I am thinking this might do the trick though

apt-get --purge remove debconf-i18n debconf-english+

The plus at the end tells it to install. 

Similarly, apt-get install debconf-english debconf-i18n-

Tells it to remove (the - at the end) but it wouldn't 'purge' it. So I would stick with the first version

---

### Post by DoeRayMe on 2006-05-01
thanks alot, that worked :)

---

