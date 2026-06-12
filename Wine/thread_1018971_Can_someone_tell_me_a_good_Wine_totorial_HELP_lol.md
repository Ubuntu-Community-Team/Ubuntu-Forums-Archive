---
title: "Can someone tell me a good Wine totorial HELP lol"
date: 2008-12-22
forum: Wine
---

### Post by criskat777 on 2008-12-22
I have been using Linux for about 2 Yr's now and the only part of Linux that i have not been able to conquer is WINE. I don't know what it is but i can't get anything to run in wine. I have search for a comprehensive Wine tutorial all over but just can't find one that seems to do the trick so if someone can let me know were i can find one. I will appreciate it.Just in case my box specs. 2 8800 GTX 512mb MSI Diamond MB 4gb OZ MEM Q6600 Intel. everything works Compiz Fusion 3D Emerald setup for 4 HP w2207's Monitors. Like i seed Ubuntu Rocks But every time i try to use Wine i end up giving up but not with out a fight . some HELP would be appreciated Thank you

---

### Post by pytheas22 on 2008-12-22
Using wine should not be too difficult in most situations.  You need just to install it by typing:
```

sudo apt-get install wine
```

Then you should be able to open Windows .exe files by right-clicking on them and selecting 'Open With Wine'.

Of course, there are more advanced things that you can do to hack wine's configuration, but for most people this shouldn't be necessary.  wine is quite mature now and should be able to run a majority of Windows software without special configuration.

It could be the case that the Windows software that you're trying to use is not supported.  You should look it up in the [wine application database]("http://appdb.winehq.org/") to check its status.

For more documentation on wine, check [here]("https://help.ubuntu.com/community/Wine") and [here]("http://www.psychocats.net/ubuntu/wine").

---

