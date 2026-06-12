---
title: "How to install Mp3splt"
date: 2008-07-29
forum: Ubuntu Studio
---

### Post by Dreamerman on 2008-07-29
Hi. I need help in installing Mp3splt/libmp3splt/mp3splt-gtk from [http://mp3splt.sourceforge.net/mp3splt_page/about.php](http://mp3splt.sourceforge.net/mp3splt_page/about.php)

There are 3 files & no instructions on how to install them. I managed to install mp3splt via Synaptic. The other 2 files are not available under Synaptic.

Can anyone help ?

Thanks

---

### Post by Stochastic on 2008-07-29
there are a variety of methods for installing these.
-go to the downloads page of that website
-there you'll see options for source code (which will contain instructions, but might be difficult for newbies) or .deb downloads (among others)
-you'll probably want to get the .deb files
-open them with gdebi package manager, and press install

I looked into this software a little while ago, and the reason why those debs aren't in the repos is because they don't meet ubuntu's quality standards, so use at your own risk - but they should work.

---

### Post by evets25 on 2008-07-29
I use mp3splt, and I installed it using apt-get. In fact, I just checked, and it *is* in the repository. Note that the package name is mp3splt (not mp3slit - remove the "i".). 
```
sudo apt-get install mp3splt

```

It's just a commandline tool, but it's not that complicated to use. Type this for more info on how to use it: 
```
man mp3splt
```

---

### Post by Dreamerman on 2008-07-29
> **evets25 said:**
> I use mp3splt, and I installed it using apt-get. In fact, I just checked, and it *is* in the repository. Note that the package name is mp3splt (not mp3slit - remove the "i".). 
```
sudo apt-get install mp3splt

```

It's just a commandline tool, but it's not that complicated to use. Type this for more info on how to use it: 
```
man mp3splt
```

Thanks but I already installed mp3splt via Synaptic. It is a command line tool but as a novice I much prefer GUI.

---

### Post by Dreamerman on 2008-07-29
> **Stochastic said:**
> there are a variety of methods for installing these.
-go to the downloads page of that website
-there you'll see options for source code (which will contain instructions, but might be difficult for newbies) or .deb downloads (among others)
-you'll probably want to get the .deb files
-open them with gdebi package manager, and press install

I looked into this software a little while ago, and the reason why those debs aren't in the repos is because they don't meet ubuntu's quality standards, so use at your own risk - but they should work.

Great thanks. Will try using gdebi, need to check if I have that installed.

Cheers

---

