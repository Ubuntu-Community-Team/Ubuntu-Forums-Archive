---
title: "any one know why max payne does not work"
date: 2009-07-07
forum: Wine
---

### Post by starcraftmaster on 2009-07-07
hey guys
can any one tell me why max payne 1 (patched) wont work ?
i keep getting this error when trying to start it

Error: no zbuffer formats found

also starwars battle front 1(patched) wont start either
that justs closes on its on self

also starcraft brood war is very slow and lags heaps
i did the registry trick and it does not work at all

on the wine database it says they should both work

does wine need direct x to be installed ?

or does wine need any thing else to be installed to make it more better/easier ?

---

### Post by cogadh on 2009-07-07
It sounds like this is probably a graphics card issue. What do you have for graphics hardware and are you using the accelerated/restricted driver for it? How are you running the app (via a shortcut or from the terminal)? If you are running it from the terminal, what is Wine producing for error messages?

Wine already has its own DirectX and installing the real DirectX will very likely break Wine, so don't do it.

Technically, Wine doesn't need anything to run better, other than more coding. It is not actually complete yet. However, particular applications may need additional items installed in order to run correctly, but we can't say that for certain in this case without some error output from Wine. If you are looking for ease of use, then you might try using one of the third party front ends for Wine, like [PlayOnLinux]("http://www.playonlinux.com/en/"), it might help make using Wine a little easier.

---

### Post by starcraftmaster on 2009-07-07
> **cogadh said:**
> It sounds like this is probably a graphics card issue. What do you have for graphics hardware and are you using the accelerated/restricted driver for it? How are you running the app (via a shortcut or from the terminal)? If you are running it from the terminal, what is Wine producing for error messages?

Wine already has its own DirectX and installing the real DirectX will very likely break Wine, so don't do it.

Technically, Wine doesn't need anything to run better, other than more coding. It is not actually complete yet. However, particular applications may need additional items installed in order to run correctly, but we can't say that for certain in this case without some error output from Wine. If you are looking for ease of use, then you might try using one of the third party front ends for Wine, like [PlayOnLinux]("http://www.playonlinux.com/en/"), it might help make using Wine a little easier.


well i got a geforce 4 mx 440 se pci 64mb
the driver am using is : 96.43.10
ubuntu installed them on its on when i tried to put desktop effects on 
so how do i know if i have accelerated/restricted driver

see max payne starts
its control panel starts(where you set its options and stuff) and then you go to ok and its trys to start the game and then the error comes
also am running max payne from drive D:
would that matter ?

i know something that works
star wars jediknight jedi out cast
that works fine

---

### Post by cogadh on 2009-07-07
Turn off Desktop Effects, that interferes with Wine.

---

