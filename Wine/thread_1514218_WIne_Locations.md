---
title: "WIne Locations?"
date: 2010-06-20
forum: Wine
---

### Post by jchase45 on 2010-06-20
Ok I have a few questions, I wanted to know first If I can install the windows system any where other then C:/.wine , because my C hard drive is the smallest drive I have , and I want to install my games on a different drive.

Also , I'm installing steam through Wine, and it's asking me where to install too, my question is can I install it any where I want or does it need to be installed in my home / .wine / program files folder?

---

### Post by jchase45 on 2010-06-20
help

---

### Post by hikaricore on 2010-06-20
You need to be patient and wait for someone to respond or all you're going to get is pissy replies like this one..

---

### Post by cogadh on 2010-06-20
I think you need to clarify things a little. Linux doesn't have a "C:" drive and Wine, by default, sets up its fake Windows drive in your home directory (/home/<whatever your username is>/.wine). It will be limited by the size of the partition your home directory is on, so if you are saying that you made that the smallest possible drive, then you have bigger problems than Wine not fitting. Your home directory is pretty much where everything goes in Linux, so it should be one of the largest (if not *the* largest) partitions you have.

As for whether or not you can direct an app to install in different location, yes you can, provided that location has been set up in Wine as a drive, but a better solution would be to set up the entire Wine fake Windows in its own location:
```
wineprefixcreate --prefix /path/to/new/.wine-prefix
```
When you go to install or use anything in that prefix, you will need to specify it, like these two examples:
```
env WINEPREFIX=/path/to/new/.wine-prefix winecfg
env WINEPREFIX=/path/to/new/.wine-prefix wine foo.exe
```

---

### Post by jchase45 on 2010-06-20
Yea thats what Im talking about is the windows virtual installation 

No , the Hard drive is 72 GB's , but what I'm saying is that all my games are huge , so If I can only install things on this one drive then i might have issues. 

Ok I'll give ita shot , thanks ! :p

---

