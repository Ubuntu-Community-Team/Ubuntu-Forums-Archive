---
title: "WINE - Does it slow down your PC? Always running in background? Is there a switch?"
date: 2009-08-18
forum: Wine
---

### Post by edwardtilbury on 2009-08-18
I'm very interested in wine but I don't want to mess-up my perfectly running installation of Ubuntu 9.04 .... 

How easy it to uninstall and is it a memory hog when you're not running windows apps?

If wine is always running once you turn on your system, is there a switch or something that you can have, so that you can turn it on before playing games? 

Thanks!

---

### Post by IsstanarLW on 2009-08-18
Wine only runs when you're running windows apps.
Also very easy to uninstall from Add/Remove.

---

### Post by edwardtilbury on 2009-08-18
awesome!

I'm coming from the windows world... this is good news!!!:guitar:

---

### Post by Marlonsm on 2009-08-18
Just remember that while Wine is great, it's not perfect, so it's always better to run Linux native applications when possible. And Wine still can't run everything perfectly, but you can find a very big list of apllications and how well they run in Wine here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by edwardtilbury on 2009-08-19
yeah, I'm pretty paranoid about messing up this install because it's working so perfectly.. so the only time I'll use wine is for a game...

I saw some posts about people running windows messenger on wine.. that seemed pretty wacky, not only is there a linux native app for msn messenger, but why have wine always on wasting so many extra cpu cycles for compatibility just to run that horrible-spammy microsoft program...

Right now, the only extra thing I run is compiz in wall mode and emerald :) , other than that, not too much junk on here.. :)

---

### Post by majamba on 2009-08-19
virtual box works great

but yeah he is right is better run linux native but for some of them require research sometimes some applications are only under windows

---

### Post by NightMKoder on 2009-08-20
True, native is better, but WINE = Wine Is not an Emulator. It runs as fast as it would on windows, so if the program wastes CPU cycles on windows, itll waste them on wine, but if it doesn't on windows, it won't on wine. (assuming perfect support for the app).

---

### Post by datacw on 2009-08-20
The answer to your question is no

Wine does not slow down 9.04 or any ubuntu district

also you can uninstall it by going to appllicaions wine uninstall wine

hope i helped:P

---

### Post by Marlonsm on 2009-08-20
> **NightMKoder said:**
> True, native is better, but WINE = Wine Is not an Emulator. It runs as fast as it would on windows, so if the program wastes CPU cycles on windows, itll waste them on wine, but if it doesn't on windows, it won't on wine. (assuming perfect support for the app).

Wine is actually a bit slower than native Windows.

For example, there is an application called SuperPI, that calculates the PI number with lots of decimals. It has both Linux and Windows versions.

The native Linux one took 18 seconds to calculate PI with 1 million decimals in my computer.
The Windows version running in Wine took 28 seconds.
And the Windows version in Windows, took 24 seconds.

---

### Post by Dark Aspect on 2009-08-20
> **Marlonsm said:**
> Wine is actually a bit slower than native Windows.

For example, there is an application called SuperPI, that calculates the PI number with lots of decimals. It has both Linux and Windows versions.

The native Linux one took 18 seconds to calculate PI with 1 million decimals in my computer.
The Windows version running in Wine took 28 seconds.
And the Windows version in Windows, took 24 seconds.

Thats interesting, but don't you have to take into account how much ram was being used in Windows/Linux from background task?

Seems like background task and free resources would play a large role.

---

### Post by del_diablo on 2009-08-20
> Wine is actually a bit slower than native Windows.

Which depends on what parts of the Windows API is used. Some games runs BETTER under Wine than under Windows, others got the same performance and others run on worse performance.
It all depends on the code.

---

### Post by almigi on 2009-08-21
> **del_diablo said:**
> Which depends on what parts of the Windows API is used. Some games runs BETTER under Wine than under Windows, others got the same performance and others run on worse performance.
It all depends on the code.

Indeed. Although, sometimes I wonder when I get something running under Wine with better performance then native Windows if it's because Wine is handling the program better then Windows, or if it's because a typical Linux install is less taxing on system resources then a typical Windows install, and the program I'm running is just benefiting from that.

Either way, what you say is correct, there are some Windows programs that do work better when you run them in Linux using Wine.

---

