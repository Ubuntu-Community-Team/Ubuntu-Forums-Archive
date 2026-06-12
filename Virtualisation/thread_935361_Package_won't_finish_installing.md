---
title: "Package won't finish installing"
date: 2008-10-01
forum: Virtualisation
---

### Post by BtotheH on 2008-10-01
So i'm at school right now, using my lab computer (which has Ubuntu 8.04 installed) trying to install virtualbox. I've installed it at home with no problems whatsoever.
So now to the problem, I'm trying to install the package and it needs two other files. (sorry, I don't have them written down, package installer is frozen on me.) These two files won't download, and when i go into synaptics, it won't bring up the list of all the packages. 

What's the deal guys?:confused:

---

### Post by Pro-reason on 2008-10-01
Open a terminal, and enter this:

```

sudo apt-get update
sudo apt-get -f install

```
What is the output?

---

