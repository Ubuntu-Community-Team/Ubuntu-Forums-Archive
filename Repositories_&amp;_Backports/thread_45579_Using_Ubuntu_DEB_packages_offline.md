---
title: "Using Ubuntu DEB packages offline"
date: 2005-06-30
forum: Repositories &amp; Backports
---

### Post by battlecat on 2005-06-30
The delimia is simple. I want to use Ubuntu on a totally offline computer. I do not want to hook this machine up to the internet at all.

I need to be able to download software on a public terminal, burn it to a CD and then install it from Cd on the non-networked computer.

How can this be done or is it not really feasable?

---

### Post by manicka on 2005-06-30
Just install the packages using sudo dpkg -i packagebnae.deb

Solving dependency issues might be big headache though.

---

### Post by moldboy on 2005-07-01
I have exactly the same desire, however I don't know where to find the .deb installer files.

---

### Post by tread on 2005-07-01
Go to packages.ubuntu.com and search for the packages you need. Make sure you get all the dependencies you need and don't have already installed.

---

### Post by manicka on 2005-07-01
[QUOTE=tread]Go to packages.ubuntu.com and search for the packages you need. Make sure you get all the dependencies you need and don't have already installed.[/QUOTE]
 Can you search through backports there as well or do you need to manually search through [http://ubuntu-backports.mirrormax.net/dists/](http://ubuntu-backports.mirrormax.net/dists/) to find them?

---

