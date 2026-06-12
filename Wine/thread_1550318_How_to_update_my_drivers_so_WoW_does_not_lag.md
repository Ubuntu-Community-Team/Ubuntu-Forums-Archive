---
title: "How to update my drivers so WoW does not lag"
date: 2010-08-10
forum: Wine
---

### Post by lilespo on 2010-08-10
My WoW is getting 1 fps i was told in my other post [http://ubuntuforums.org/showthread.php?p=9704774#post9704774](http://ubuntuforums.org/showthread.php?p=9704774#post9704774)

That it was my drivers so i need help learning on how to get my drivers for this computer.


specs:
Dell Inspiron 1525
3gb Ram
250gb hard drive
Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Tell me if you need more information
Thank you.

---

### Post by Caffeind on 2010-08-10
> **lilespo said:**
> My WoW is getting 1 fps i was told in my other post [http://ubuntuforums.org/showthread.php?p=9704774#post9704774](http://ubuntuforums.org/showthread.php?p=9704774#post9704774)

That it was my drivers so i need help learning on how to get my drivers for this computer.


specs:
Dell Inspiron 1525
3gb Ram
250gb hard drive
Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Tell me if you need more information
Thank you.

Hi Lilespo,

You have a nice enough system to be running WoW with nice FPS except for one thing... Your Intel Video Card is what's letting you down. From my extensive research you won't get any better performance while using the Intel GPU. My system is running WoW beautifully with an NVIDIA 9600GT, I also believe that ATI cards will run WoW under Ubunto 10.04.
If you decide to upgrade your GPU (Intel Graphics Card) I suggest using an NVIDIA as they seem to have the best OPENGL supported drivers for Ubuntu. Also, when (if) you upgrade your card you will need to edit the config.wtf file located in the WoW WTF folder, and add this line...
```
SET gxApi "opengl"
```... to force WoW to play under OPENGL (DirectX wont cut it under ubuntu).

Hope this post sees you in good health and you can solve your problems and start playing WoW as it was intended.

Cheers.

---

### Post by lilespo on 2010-08-10
> **Caffeind said:**
> Hi Lilespo,

You have a nice enough system to be running WoW with nice FPS except for one thing... Your Intel Video Card is what's letting you down. From my extensive research you won't get any better performance while using the Intel GPU. My system is running WoW beautifully with an NVIDIA 9600GT, I also believe that ATI cards will run WoW under Ubunto 10.04.
If you decide to upgrade your GPU (Intel Graphics Card) I suggest using an NVIDIA as they seem to have the best OPENGL supported drivers for Ubuntu. Also, when (if) you upgrade your card you will need to edit the config.wtf file located in the WoW WTF folder, and add this line...
```
SET gxApi "opengl"
```... to force WoW to play under OPENGL (DirectX wont cut it under ubuntu).

Hope this post sees you in good health and you can solve your problems and start playing WoW as it was intended.

Cheers.

Ok so  i added that to my config.wtf and now my wow runs with no lag but i cant see anything its all black and when i choose a  character it freezes and gives me a message saying wine encountered a problem and needed to close the program.

---

### Post by lilespo on 2010-08-11
Btw it ran perfectly on windows.

---

### Post by hikaricore on 2010-08-11
As has already been mentioned that "video" hardware is probably not sufficient to run WoW on linux.
It is probably lacking proper hardware/driver OpenGL support and setting the opengl flag makes things even worse.
Linux does not have DirectX but wine is capable of effieciently converting DX calls to OpenGL allowing WoW to run a little better than in pure OpenGL mode however the point still stands that your intel chipset is your main limitation.

You could look into the bleeding edge "xorg edgers" ppa and see if that improves your performance, but I doubt it will make much difference.

---

### Post by cruzowen on 2010-09-14
Try "Advanced Driver Updater".It is a program with which u just have to scan and it update all ur drivers in a single go. This may help u as it can replace corrupt drivers and can also provide the missing ones .For me it is the best driver updater..so u can also give it a try.u can download its FREE version from [http://systweak.com/adu/download/](http://systweak.com/adu/download/)

---

### Post by cwwilson721 on 2010-09-14
> **hikaricore said:**
> As has already been mentioned that "video" hardware is probably not sufficient to run WoW on linux.
It is probably lacking proper hardware/driver OpenGL support and setting the opengl flag makes things even worse.
Linux does not have DirectX but wine is capable of effieciently converting DX calls to OpenGL allowing WoW to run a little better than in pure OpenGL mode however the point still stands that your intel chipset is your main limitation.

You could look into the bleeding edge "xorg edgers" ppa and see if that improves your performance, but I doubt it will make much difference.
The issue, as has been stated, is the GMAXXX chip. Intel does NOT implement opengl correctly in these devices, and as such, does not run WoW as well as in Windows.

Changing drivers does NOTHING. Only a videocard/chipset change will help

---

