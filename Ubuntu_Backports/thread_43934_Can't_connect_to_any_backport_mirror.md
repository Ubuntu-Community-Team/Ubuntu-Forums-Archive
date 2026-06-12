---
title: "Can't connect to any backport mirror"
date: 2005-06-23
forum: Ubuntu Backports
---

### Post by arjun on 2005-06-23
Hello.  I've put the following lines in my sources.list file:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main restricted universe multiverse 
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main restricted universe multiverse 

and i've tried all the other mirrors as well; but, each time i get the following error when i start package manager:

W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Is something wrong or am I just a tool? :)

---

### Post by Xian on 2005-06-23
Try it in this format:

```
deb ftp://ftp2.caliu.info/backports hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports hoary-extras main universe multiverse restricted
```
Here's a tutorial: [Using Ubuntu Backports](http://www.evolutioncolt.com/backports/index.php?title=Using_Ubuntu_Backports)

Edit: Oh, and be sure to issue this command after any edits of the sources.list

```
$ sudo apt-get update
```

---

### Post by jdong on 2005-06-23
You need to do an **apt-get update**, or a Reload from Synaptic. This is normal.

---

