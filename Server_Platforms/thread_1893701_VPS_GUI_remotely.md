---
title: "VPS GUI remotely"
date: 2011-12-10
forum: Server Platforms
---

### Post by louis vitton on 2011-12-10
Hi guys, 
I have just got myself a Ubuntu 11.04 natty VPS server and I have installed the GUI on it now i want to remotely access it and use the GUI interface.\
I tried VNC but it is junk and every time i hit the letter "d" everything minimized on the screen.
Next i looked into freeNX but has issues as the packages are now supported automatically in the respiratory and i had issues adding them myself.
So i am wondering what other people use and if there are some good ones out there, because i know nothing about them.

also help on installing and configuring them would be a very good help.

Thank you 

Also my VPS is unmanaged and has no control panel.

---

### Post by yeats on 2011-12-11
If you're running an X server on the machine you're trying to access the server from, you can do:

```
ssh -XC user@servername
```

Then you can just type the name of individual programs and they'll pop up for you.

---

