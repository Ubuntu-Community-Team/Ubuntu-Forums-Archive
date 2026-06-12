---
title: "Performance against windows ?"
date: 2009-02-28
forum: Wine
---

### Post by unholy182000 on 2009-02-28
I am a new user to the Linux community.My primary concern with pc's are gaming and 3d modelling.After the vista's blue screen i decided to go with linux for trying something new.I chose Ubuntu because i heard it is most user friendly one.I read "How to do everything in Ubuntu" by Jeffrey Orloff and "Ubuntu Complete reference" by Richard Petersen.But still i am far away my skills at windows.But i like ubuntu and will go on with it but...

   My first question is "What is the performance of Ubuntu using wine or similar against Windows Vista ?" Both os are 64 bits.

   Second "Where the installing files written to?" i don't have much understanding file handling in ubuntu.

   My rig is Core2duo e8400 3ghz ,4gb ram ,radeon hd 3870 

If there is benchmark tests or other topics relating this please post them.Thank you.

---

### Post by AndrewRiedi on 2009-02-28
Native Linux applications usually run faster and more stable.

Wine applications (your windows ones) are installed into ~/.wine (open your "Home" directory and press ctrl-h then double click on .wine).  There are a few instances of Wine running faster than windows, but usually Wine runs a little slower.  Wine also does not support every Windows application.  Check the [AppDB]("http://appdb.winehq.org") for details of your specific applications and games.

---

### Post by albinootje on 2009-02-28
> **unholy182000 said:**
>  
   Second "Where the installing files written to?" i don't have much understanding file handling in ubuntu.

A lot of applications (read : binaries) end up in /usr/bin although there are more locations like for example /usr/sbin,  and /opt
When directly compiling from source, /usr/local/bin is the default place where binaries end up.
Check with for example this command in a terminal :
```

dpkg -L gimp|less

```
where the files of the package "gimp" are located.
> 
If there is benchmark tests or other topics relating this please post them.
Check [http://www.phoronix.com/](http://www.phoronix.com/) for Linux benchmark testing.

---

### Post by unholy182000 on 2009-02-28
thanks

---

