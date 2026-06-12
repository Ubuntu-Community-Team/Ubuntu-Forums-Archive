---
title: "Lazy shell scripts:"
date: 2007-11-05
forum: The Cafe
---

### Post by mouseboyx on 2007-11-05
This is extreme lazyness, instead of having to type out sudo apt-get install you just type whatever you save the shell script as:
```

sudo apt-get install $1
```Ownit: own everything you want to with one command: ownit
```
chmod -R a=rwx $1
```iso: Burning iso images the easy way
```
cdrecord -eject -v -V dev=X,X,X $1 
```Just type iso then drag and drop the image where X,X,X is your device id: ```
cdrecord -checkdrive
```MAKE SURE YOU DO NOT USE YOUR HARD DRIVE AS THE DEVICE!

What are some lazy shell scripts you have made?

---

### Post by yatt on 2007-11-05
I use [bash aliases]("http://en.wikipedia.org/wiki/Alias_%28Unix_shell%29") to map apt-get install to apt, apt-get remove to aptr, apt-get update to aptu, and apt-get upgrade to aptup.

---

### Post by Billy_McBong on 2007-11-05
[COLOR="Blue"]i got a bunch of them
and i still need to make more of them[/COLOR]

---

