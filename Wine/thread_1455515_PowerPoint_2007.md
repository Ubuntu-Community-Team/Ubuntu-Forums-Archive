---
title: "PowerPoint 2007"
date: 2010-04-16
forum: Wine
---

### Post by roderakker on 2010-04-16
Guys, I got PowerPoint 2007 working perfectly fine within Wine using Ubuntu 9.10, and I wanted to share this with you, because I've been told music, videos and inserting media into a PowerPoint presentation doesn't work. Well, it does for me!

* install Ubuntu, I used 9.10 
* update it completely 
* open the synaptic package manager - 
and add ppa:ubuntu-wine/ppa to the repository 
* install Wine 1.2 from the synaptic package manager, 
it'll automaticly get the latest version (I'm running 1.1.41 still) 
* install MS Office 2007 
* open winecfg and set winemp3.acm to native (& bulletin) 
* install the K-Lite codec, Basic or Full, it makes little difference 
* in the terminal, enter: 
```
wget http://www.kegel.com/wine/winetricks
```then 
```
sh winetricks wmp9
```* have it install wmp9 and the required components 
 
everything should work fine by now, 
but I got crashes when using mp3's. 
 
* open winecfg and remove msvcrt from the libraries list 
* make a symlink called 'winemp3.acm' to 'l3codeca.acm' - 
which is located in the system32 folder 
* Open winecfg and set winemp3.acm to native (& bulletin)

Ba-daaa-DONE!

---

### Post by dino99 on 2010-04-16
Nice
should be a sticky  =D>

have you post on winehq (appDB), this will be usefull for everyone

---

