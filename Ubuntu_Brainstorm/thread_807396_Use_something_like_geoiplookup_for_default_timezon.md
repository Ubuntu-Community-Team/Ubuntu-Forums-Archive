---
title: "Use something like geoiplookup for default timezone and keyboard layout"
date: 2008-05-25
forum: Ubuntu Brainstorm
---

### Post by sq377 on 2008-05-25
During the Ubuntu install, something like geoiplookup could be used to determine the default timezone.  If canonical were to support this, they could put up a server returning the keyboard code, most common language, and the default timezone.

For example, I have the GeoLiteCity database installed (free)
```
squee@squee-laptop:~$ geoiplookup $(curl -s http://whatismyip.org/) -f /usr/share/GeoIP/GeoLiteCity.dat 
GeoIP City Edition, Rev 1: US, AZ, Phoenix, (null), 33.522202, -112.083900, 753, 602
```

Now the installer could know that my location is AZ, and set the default timezone accordingly.  

If canonical were to have a [license]("http://www.maxmind.com/app/city") for it, they could return a page containing the City / Keyboard keyboard code.
[wheretero]("http://myy.helia.fi/~karte/wheretero.html") does this for the keyboard code already: 
```
squee@squee-laptop:~$ wheretero
us	30

```
so that you can just run
```
setxkbmap $(wheretero -1)
```
and you are set.

They could also keep a database of a country's most common language, and select that by default as well.

These are not perfect, and should not be taken as fact.  But I would be impressed if I were to put in an Ubuntu disk and it guessed the correct defaults for my computer.

---

### Post by smartboyathome on 2008-05-25
Looks interesting, you should post this to the ubiquity mailing list and see what the devs think.

---

### Post by insane_alien on 2008-05-26
not always accurate. according to that i live in iraq. i know scotland isn't the least violent of places but its not that bad.

---

### Post by Lieter on 2008-05-26
A good idea but i live in the Netherlands, and very few people use the nl keyboard layout. We use the us layout, so ip lookup isn't effective.

Also, i have (more geeky) friends that use Dvorak, which isn't linked to any locale or country.

so a selection should be made and then asked "is this correct? yes, continue/no, modify manually"

---

### Post by sq377 on 2008-05-26
The way I was thinking it would work is it would just highlight what is most likely
[IMG]http://toastytech.com/guis/ubuntu7install.png[/IMG].  If it isn't right, then they just change it.
> not always accurate. according to that i live in iraq. i know scotland isn't the least violent of places but its not that bad. 
If you get one of the licenses they actually work to keep it up to date and a bit more accurate.

---

