---
title: "Wine on 64 bit Ubuntu? Help!"
date: 2011-04-17
forum: Wine
---

### Post by Mike Loubet on 2011-04-17
Hi, using 64 bit ubuntu for the first time and after installing wine, I can't get any of the games which I got to work on my 32 bit laptop to work on this one.

Installed wine 1.3 from the PPA and followed the specific game installation instructions from winehq as I had done on the old computer, but I always get the "xx.exe has encountered a serious error and must now close" message.

I'm seeing stuff in the forums about wow64, no idea if that's of any relevance or If I have to do anything extra to run games on 64 bit ubuntu.

Thanks!

---

### Post by scott-ian on 2011-04-17
I don't know of any problems related to your computer being 64 Bit.  Are you sure the games work in Wine?

---

### Post by Mike Loubet on 2011-04-17
Hi, yes they were both working (Civilization V and Victoria II) under 32 bit. The only thing I have different is 64 bit ubuntu instead of 32 bit.

Will following instructions at [http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64) help?

---

### Post by scott-ian on 2011-04-17
Did you compile Wine from source or use the package manager?
This may help: [http://ubuntuforums.org/showthread.php?t=483035](http://ubuntuforums.org/showthread.php?t=483035)

---

### Post by Mike Loubet on 2011-04-17
I installed the latest 1.3 version from the PPA with the package manager.

The link on the thread is broken, but looking at the wine wiki, I'm trying this:

```
wget http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh
sudo sh install-wine-deps.sh
```

Hopefully it should get things working.

---

### Post by Mike Loubet on 2011-04-18
Nope, didn't work, but I got Photoshop CS2 running, so I'm putting it down to hardware...

---

### Post by lxwcn840709 on 2011-04-19
These things looked pretty good, and some that I can learn, and I hope to learn more on it!

---

