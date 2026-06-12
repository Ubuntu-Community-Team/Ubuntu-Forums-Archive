---
title: "media player classic for ubuntu"
date: 2010-07-14
forum: Ubuntu Studio
---

### Post by mohan.mahi on 2010-07-14
I want media player classic for ubuntu

---

### Post by samstreet101 on 2010-07-15
Don't think there is a native linux build for media player classic (though I may be wrong). You could try running it under WINE. According to the app database on WINE HQ it runs ok ish: 
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3330](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3330)

---

### Post by endotherm on 2010-07-15
MPC is OSS but it uses the DirectShow api for windows, so it is a win32 only thing. 

I recommend smplayer, but be sure to get it from this ppa rather than from the ubuntu repos. smplayer is a gui frontend for mplayer (probably the best media player backend I've seen) so you have to install mplayer first. unfourtunatly the versions in the ubuntu repos arepretty old, which is why I suggest installing from the PPAs.
first add the mplayer ppa from [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
and then the smplayer ppa from [https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

make sure you have installed the mediubuntu repositories following [these]("https://help.ubuntu.com/community/Medibuntu")  instructions, and install libdvd2css and either the w32Codecs or  w64Codecs packages. 

then just run 
```
sudo apt-get install smplayer ubuntu-restricted-extras
```

that should take care of any codecs required and install the media player.

---

