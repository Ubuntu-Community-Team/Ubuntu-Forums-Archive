---
title: "How do I compile Wine properly from Git?"
date: 2010-08-11
forum: Wine
---

### Post by Espionage724 on 2010-08-11
Heres what I imagine I have to do:

1. Install Git
2. Get wine from Git
3. Get dependicies (this is a somewhat hard task)
4. do a ./configure
5. do make
6. then make install

---

### Post by ronnielsen1 on 2010-08-11
Open a terminal and type in the following

sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update && sudo apt-get install wine


This will give you the latest wine and automatically update

---

### Post by cogadh on 2010-08-11
Unless you are a Wine developer or need to create a custom patched version of Wine or are both curious and a glutton for punishment, there is no need for anyone to compile Wine themselves. 

If you fall into any of those categories, then the steps you listed are pretty much accurate. The dependencies thing is actually easier than it seems. If you run "sudo apt-get build-dep wine" it should take care of everything for you. Make sure you check the output of the configure process, it will tell you if there were any missed dependencies.

If you don't fall into those categories, follow ron's advice, you'll be much happier in the end.

---

