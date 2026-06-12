---
title: "Upgrading Wine"
date: 2009-05-25
forum: Wine
---

### Post by themattjon on 2009-05-25
The Wine version I have (via Add/Remove with 9.04) is 1.0.1. What's the easiest way to get the latest version without resorting to Command Line or manual installation or whatever?

---

### Post by NightMKoder on 2009-05-25
The easiest way IS through command line. Just copy paste (from winehq):

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/`lsb_release -c -s`.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get upgrade

```

It'll ask you your password and a couple of times if you want to continue. say yes.

Edit: fixed for any release.

---

### Post by cogadh on 2009-05-25
Unless you are running Ubuntu Jaunty, don't use that command (your profile indicates you are using Intrepid). Just follow the instructions for your version of Ubuntu here and you'll be OK:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by themattjon on 2009-05-26
NightMKoder, thanks for the help. Hopefully it will help others too.
codadh, thanks for pointing out my profile, I forgot to change it when I installed the latest version. I actually am using Jaunty! Your link was a big help as well.

---

