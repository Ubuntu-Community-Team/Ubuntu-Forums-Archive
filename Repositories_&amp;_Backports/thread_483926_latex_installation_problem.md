---
title: "latex installation problem"
date: 2007-06-25
forum: Repositories &amp; Backports
---

### Post by phoenix7 on 2007-06-25
I've tried to install latex by running the following:
```
apt-get install latex
```

but it cannot find the latex, how can I fix it?

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package latex is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  tetex-extra tetex-base
E: Package latex has no installation candidate

---

### Post by pvdg on 2007-06-25
There are currently two families of latex packages in ubuntu. The first, in the main repository, is tetex:
```
apt-get install tetex-base tetex-bin tetex-extra
```
The tetex-extra package is optional, but if you don't have a disk space problem, install the full set.
If you want to install the documentation, just install this package also:
```
apt-get install tetex-doc
```

As an alternative (they are incompatible with tetex), you might want to install the texlive packages, which are available in the universe repository. Make sure you have it enabled in your sources.list and then:
```
apt-get install texlive
```
or, if you want the full set (around 600MB):
```
apt-get install texlive-full
```.

Texlive has already replaced tetex in Debian, and the same will probably happen in ubuntu (perhaps in Gutsy). I have no experience with the texlive packages. I have been able to do all I need with tetex, but I'm planning to switch some time soon.

---

### Post by phoenix7 on 2007-06-27
Thanks pvdg!

---

### Post by pvdg on 2007-06-27
You're welcome!

---

### Post by gcordoba on 2007-12-05
Very good. However, why do synaptic  cannot find latex? I have all the repositories enabled.

---

### Post by gcordoba on 2007-12-05
Actually I installed Gutsy in an other PC and the  tip didnt work for me:
gcordoba@pc-pflow2:~$ sudo apt-get install texlive-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package texlive-full
gcordoba@pc-pflow2:~$ 

This sounds to me that the repositories are not working properly, despite sympatetic confirm that all of them are enabled.

Any idea?

---

### Post by pvdg on 2007-12-05
Please confirm that you have the **universe** repository enabled in that other PC. The package should be there: [http://packages.ubuntu.com/gutsy/tex/texlive-full](http://packages.ubuntu.com/gutsy/tex/texlive-full)

---

### Post by gcordoba on 2007-12-06
Thanks pvdg,
A fixed tha problem. It was due to I forgot to click "reload" after choosing the server.
 I found some interesting tips about the repositories in:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Thanks again.

Gustavo

---

### Post by Whiffle on 2007-12-06
Don't forget to give kile a shot if you havn't already :)  [http://kile.sourceforge.net/](http://kile.sourceforge.net/)

---

