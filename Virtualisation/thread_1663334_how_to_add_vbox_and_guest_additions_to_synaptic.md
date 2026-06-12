---
title: "how to add vbox and guest additions to synaptic"
date: 2011-01-09
forum: Virtualisation
---

### Post by mystmaiden on 2011-01-09
I'm running 10.04 LTS


edited - I got Virtualbox 4.0 to show up on synaptic just now but I can not seem to get Virtualbox 4.0  guest additions added to synaptic. What commands should I run to add the source and/or keys needed. I see the 3.1. 6-1 guest additions there - will they work?


thanks 

mystmaiden

---

### Post by CharlesA on 2011-01-09
The guest additions are installed from within virtualbox. You won't find them in synaptic.

---

### Post by Zimmer on 2011-01-09
When Vbox is installed, and you have installed an OS into a created Virtual Machine....
when the Guest machine is loaded (I assume Win XP or similar) go to the CD drive icon , bottom right, and right click to choose a Virtual CD/DVD file. Navigate to the /usr/share/Virtualbox  directory and select the guestadditions iso file. It should start to install the additions automatically to the installed OS.

---

### Post by mystmaiden on 2011-01-09
Thanks so much for the replies, all installed now and working!

---

