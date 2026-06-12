---
title: "Does Wine is working in Beta1 ?"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Neo40 on 2012-03-05
I have downloaded Precise Beta-1 64 bits. Before I install it on my machine,
I read there is problem with dependancies(?). Is it true?
Or I should way for the next Beta?

Thanks .

---

### Post by dino99 on 2012-03-05
works for many users :) so you will know after having tried yourself :)

---

### Post by grahammechanical on 2012-03-05
I have been using 12.04 since November 2011 and using wine as well. No problems. You will find that wine 1.4 is in the software centre. I usually install it through a PPA.

I got into this habit a few years ago when I first started using Ubuntu and the windows program that I wanted to use was said to work well in the then beta version, which was 1.01. Whereas 1.0 was in the software centre. 

But I am sure that my windows program will work just as well on 1.3 from the software center as it does on 1.4 from the PPA. I, of course, cannot speak for the program that you wish to use.

Regards.

P.S. As regards 12.04 itself, packages are being upgraded daily. You need to do a daily update. Sometimes packages are held back because they are not yet ready for being part of 12.04. In this case you will be offered a partial upgrade. Do not accept. Just close the message window and do a normal update. You will find that the held back packages will be downloaded in a day or two. That is how things are being done.

---

### Post by prana on 2012-03-05
It works for me. I am running Xubuntu 12.04 i386

---

### Post by Gavin77 on 2012-03-05
> **Neo40 said:**
> I have downloaded Precise Beta-1 64 bits. Before I install it on my machine,
I read there is problem with dependancies(?). Is it true?
Or I should way for the next Beta?

Thanks .

I tried Precise beta 1 64bit with Wine 1.4 and couldn't get any windows apps to install.  They all failed.

---

### Post by Neo40 on 2012-03-05
Maybe it's just me, but when I try to install Civilization IV, there is a pop up error message about the kernel...
It never happened with previous versions...
I should reinstall to make sure.

---

### Post by xeizo on 2012-03-05
Wine won't even install on my 64-bit Precise, there's too many broken dependencies.  First I tried a 11.10 Kubuntu upgraded to Precise, then I tried todays daily build. None of them work.  Most other things do work in the daily, just got some error message which was commonly reported, sadly the not working Wine is a dealbreaker as it makes ie running Xampp impossible. I hope this has a large priority being fixed!

---

### Post by xeizo on 2012-03-05
Wow, that was fast! A bunch of updates a few minutes ago and Wine is up and running again!  :)

---

### Post by Neo40 on 2012-03-05
Ok, so I reinstalled Precise Beta1 ( a fresh new install + latest updates).
Then, I installed wine  1.4 rc-6.
I started to install Civilization IV and this is the error  I got:

```
Code d'erreur :	-5006 : 0x8000ffff
Information d'erreur :
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\ObjectHolder.cpp (442)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\ObjectHolder.cpp (442)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>K>SetupDLL\SetupDLL.cpp (1284)
PAPP:Sid Meier's Civilization 4
PVENDOR:Firaxis Games (http://www.2kgames.com/civ4/)
PGUID:CFBCE791-2D53-4FCE-B3FB-D6E01F4112E8
$11.0.0.28844
@Windows XP Service Pack 3 (2600) BT_OTHER 96.17
```

As I said, the previous releases (11.10 and 11.04) were working correctly.
Any idea?
Thanks in advance for help.


PS: Another problem. If I try to install "steam" here the result:```
eric@eric-desktop:~$ winetricks --no-isolate steam
Executing w_do_call steam
Executing load_steam
Executing mkdir -p /home/eric/.cache/winetricks/steam
Executing wine msiexec /i SteamInstall.msi
fixme:storage:create_storagefile Storage share mode not implemented.
wine: Unhandled page fault on write access to 0x000000b4 at address 0x7bc450e6 (thread 0028), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc47aac
------------------------------------------------------
Note: command 'wine msiexec /i SteamInstall.msi' returned status 5.  Aborting.
------------------------------------------------------
```


[code]

---

