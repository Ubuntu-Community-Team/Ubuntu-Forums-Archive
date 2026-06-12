---
title: "x64 not in repositories anymore"
date: 2011-03-14
forum: The Cafe
---

### Post by honeybear on 2011-03-14
Hello,

It seems that there is no deb for emulating the c64 commodore? Which equivalent is now used by ubuntu? 

:popcorn:

---

### Post by Telengard C64 on 2011-03-14
**x64** is the C64 emulator included in the **vice** (Versatile Commodore Emulator) package. [VICE is available in Dapper, Hardy, Karmic, Lucid, Maverick, and Natty](http://packages.ubuntu.com/search?keywords=vice&searchon=names&suite=all&section=all). You must enable the Multiverse repository.

---

### Post by honeybear on 2011-03-14
> **Telengard C64 said:**
> **x64** is the C64 emulator included in the **vice** (Versatile Commodore Emulator) package. [VICE is available in Dapper, Hardy, Karmic, Lucid, Maverick, and Natty](http://packages.ubuntu.com/search?keywords=vice&searchon=names&suite=all&section=all). You must enable the Multiverse repository.

looks nice machine, would you know how to start it from command line, with joystick, video fullscreen, and tap ?

---

### Post by Telengard C64 on 2011-03-14
I usually just start **x64** and set whatever options I need as I go.

[VICE Manual](http://www.viceteam.org/vice_toc.html)

---

### Post by honeybear on 2011-03-15
> **Telengard C64 said:**
> I usually just start **x64** and set whatever options I need as I go.

[VICE Manual](http://www.viceteam.org/vice_toc.html)

wow great. And which options do you normally use, passed to command line?

---

### Post by Telengard C64 on 2011-03-15
> **honeybear said:**
> wow great. And which options do you normally use, passed to command line?

Honestly none at all. I rarely start x64 from the command line. I use the included XAW GUI to navigate the menus and choose whatever options I want. That's just the way I am accustomed to using VICE.

I think it is possible to save preference profiles under various file names and specify them from the command line, but I can't tell you how. Please refer to the VICE documentation I linked above.

Sorry I'm not able to help more. I'd have to read through the documentation to find out how to do what you want. I just think it would be better for you to learn it for yourself than to have me learn it for you.

---

### Post by honeybear on 2011-03-16
> **Telengard C64 said:**
> Honestly none at all. I rarely start x64 from the command line. I use the included XAW GUI to navigate the menus and choose whatever options I want. That's just the way I am accustomed to using VICE.

I think it is possible to save preference profiles under various file names and specify them from the command line, but I can't tell you how. Please refer to the VICE documentation I linked above.

Sorry I'm not able to help more. I'd have to read through the documentation to find out how to do what you want. I just think it would be better for you to learn it for yourself than to have me learn it for you.

well, I read the manual on the vice site. it is frustrating, it seems they arent clearly and efficiently thinking about communicating about how their tool works really. I tried their GUI vice, and visibly although well stuffed with features, you cannot even get all you simpley seek to get from the emulator. 

regards

---

### Post by Telengard C64 on 2011-03-16
I did research this a bit.

The *fullscreen* feature only works if the option is enabled at compile time. I don't know if the package in the 'buntu repositories has enabled this option.

If you compile the VICE source yourself I think the appropriate syntax would be like this:

```
./configure --enable-fullscreen
```

Thereafter to run **x64** fullscreen you pass it the **-fullscreen** option. At least, I think that's how it should work.


I compiled my VICE without any of the **configure** options so I can't even test this. There are many other interesting options for **configure** which you might want to look into as well.

HTH

---

