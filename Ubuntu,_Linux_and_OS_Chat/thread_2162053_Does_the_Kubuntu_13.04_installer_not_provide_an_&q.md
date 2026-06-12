---
title: "Does the Kubuntu 13.04 installer not provide an &quot;alongside Windows&quot; option?"
date: 2013-07-12
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2013-07-12
The poster over here seems to feel that that is the case:  [http://askubuntu.com/questions/319389/where-to-find-the-latest-kubuntu-13-04-with-autoinstaller](http://askubuntu.com/questions/319389/where-to-find-the-latest-kubuntu-13-04-with-autoinstaller)

---

### Post by monkeybrain2012 on 2013-07-13
If you know how to install Windows you probably have no problem installing Kubuntu with manual install, if not, say, you have a laptop preinstalled with Windows chances are "install along Windows" won't work anyway as Windows tends to use up all 4 primary partitions on laptops and you have to shrink/repartition to install other OSes in that case.

Of course you should wipe out Windows IMO. ;)

---

### Post by Copper Bezel on 2013-07-13
Windows [uses logical volumes]("http://en.wikipedia.org/wiki/Storage_Spaces#Storage_Spaces") now. 

[IMG]https://dl.dropboxusercontent.com/u/17749392/Image%20Hosting/Mockupzen/lvs.png[/IMG]

Windows did use primary partitions all the way up through 7, but generally just two of them.

I know that *U*buntu will only display the "install alongside" option if it detects an existing system it can understand. If there are problems and the existing system can't be identified, that option just won't appear. It's *more *likely that the user encountered a bug than that one of the most basic features of the installer has simply been disabled, but I haven't tried it (though I'm downloading the .iso now to see, I'd guess that someone with an install disk on hand can tell you before I get there.)

---

### Post by vasa1 on 2013-07-13
> **Copper Bezel said:**
> ...
I know that *U*buntu will only display the "install alongside" option if it detects an existing system it can understand. If there are problems and the existing system can't be identified, that option just won't appear. It's *more *likely that the user encountered a bug than that one of the most basic features of the installer has simply been disabled, but I haven't tried it (though I'm downloading the .iso now to see, I'd guess that someone with an install disk on hand can tell you before I get there.)
The OP was short on detail. I haven't read anything about Kubuntu dropping the "alongside" option or not using the usual Ubiquity installer. And the options that appear depend on how Ubiquity "reads" the situation. If a partition isn't available, the alongside option isn't shown. Of course, it's possible that the new "ownership" has made some changes. But I think it a bit unlikely.

---

### Post by Copper Bezel on 2013-07-13
Tried it. Kubuntu does use Ubiquity, [but with a custom Qt front-end]("http://agateau.com/2013/04/11/hacking-on-ubiquity/"). The option to install "alongside" is definitely present and was selected by default, although it was labeled cryptically enough for me ("resize [X partition] and use freed space") that someone might miss it or mistake it for something else. I don't know if that's a result of the machine being dual boot already, but I remember the regular-blend Ubiquity saying "Install alongside Ubuntu *.* and Windows 7" or something similar.

---

