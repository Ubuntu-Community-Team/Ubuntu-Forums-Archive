---
title: "Wine doesn't save settings"
date: 2010-07-28
forum: Wine
---

### Post by Volt9000 on 2010-07-28
Hey all,

Been a while since I've posted. I recently just came back into Ubuntu and I've already run into a problem; I'm so rusty I don't even know where to start!

I've installed Wine from the repos, so it's version 1.1.42. I run winecfg, add and configure an application, click OK, then run winecfg again and the application is gone!

I've got my .wine directory alright, but nothing is getting saved. This happens regardless of whether I run winecfg directly from the command-line or through the Applications menu.

Any thoughts?

---

### Post by ronnielsen1 on 2010-07-28
I'm not sure why it wouldn't. Did you click on Autodetect under the drives tab? I also would recommend installing wine 1.2

---

### Post by Volt9000 on 2010-07-28
I tried clicking Autodetect in the Drives tab, and it populated the drives list with a few extras which weren't there initially. But then when I click Apply and exit out of winecfg, when I come back in those drives are gone again.

Is version 1.2 the latest? I just apt-get'd the latest stable version from the repos. I guess the repos haven't been updated with 1.2 yet.

---

### Post by ronnielsen1 on 2010-07-28
Wine1.2 is in the universe repositories. It's a separate entry in synaptic then wine is. It was a rc, it just got released to full wine1.2

Synaptic Package Manager > Settings > Repositories > Make sure universe is checked

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-SynapticPackageManager-2.png[/IMG][IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-wine12Properties.png[/IMG]

---

### Post by Volt9000 on 2010-07-28
Universe is definitely checked, but Synaptic lists the latest version as 1.1.42-0ubuntu4, for both the "wine" and "wine1.2" packages. This is the case even after reloading everything.

I've attached a screenie.

---

### Post by ronnielsen1 on 2010-07-29
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
> It is also possible to add the Wine repositories and install via the command  line, as follows. These may be useful on Kubuntu, Xubuntu, and other Ubuntu  derivatives.  You will need to run these in a terminal window.
  *sudo add-apt-repository ppa:ubuntu-wine/ppa*
  

---

### Post by Volt9000 on 2010-07-29
Ok, Wine 1.2 is now installed. Unfortunately it's still doing the same thing. :(

---

### Post by Volt9000 on 2010-07-30
I'm an idiot. ](*,)

After not using Linux and Wine for awhile, I forgot how it works. I thought I had to add every app I want to use to the list; instead all I have to do is just rune "wine file.exe".

The reason it wasn't saving anything is I kept the Windows version as "Use global settings." As soon as I changed that to something else, it saved.

](*,)](*,)](*,)

---

### Post by ronnielsen1 on 2010-07-31
Great. I wondered what the deal was. If a program works correctly you can also start it by right click > open with wine or automatically associate exe's to open with wine. I usually don't because I have a lot of older games that I use dosbox for

---

