---
title: "Pc bottle necking??"
date: 2011-05-12
forum: Wine
---

### Post by Dlambert on 2011-05-12
Hello, ive been playing fallout: New Vegas on max settings and the longer i play the more sluggish the game gets...Seems to only be while walking outdoors(loading). But i have a phenom II x2 OC'd to 4 GHz and i was wondering if this might have a part in the problem. The OC is stable and the game is still playable (60FPS+) on GTS 450.




              Thanks:confused:

---

### Post by HolgerB on 2011-05-13
> **Dlambert said:**
> Hello, ive been playing fallout: New Vegas on max settings and the longer i play the more sluggish the game gets...Seems to only be while walking outdoors(loading). But i have a phenom II x2 OC'd to 4 GHz and i was wondering if this might have a part in the problem. The OC is stable and the game is still playable (60FPS+) on GTS 450.

Thanks:confused:
Hm, this could indicate a memory issue with intense swaping. You can easily find out this by writing a simple BASH script monitoring your system ressources :D

Increasing slowdowns might also indicate thermal throttling of the CPU because it overheats. You could simply lower your frequency back to standard. Also doing a prime test overclocked plus monitoring your CPU temp might help.

Edit: A simple cat /proc/cpuinfo | grep "cpu MHz" will help monitoring the CPU clock but reveal multiple values for each core though :)

---

### Post by Dlambert on 2011-05-14
Any other ideas? Im currently running the game in windows

---

### Post by HolgerB on 2011-05-15
> **Dlambert said:**
> Any other ideas? Im currently running the game in windows
So you tried out and have confirmed none of the things I mentioned are a possible issue ?

Did you also crosscheck with other CPU / GPU intense games under WINE and native Ubuntu ?

---

### Post by Dlambert on 2011-05-15
I meant, i am not running this game in linux. only on windows. The game is just buggy. Thanks tho

---

### Post by HolgerB on 2011-05-15
You are welcome !
I haven' t tried the new Fallout stuff since I haven't finished Fallout 3 by now.
After some googling it seems pretty buggy to me too and you will find a lot postings if you search for "fallout new vegas slow downs"

Hopefully they fix those issues soon.

---

### Post by Dlambert on 2011-05-17
It freezes too... :(

---

### Post by HolgerB on 2011-05-17
> **Dlambert said:**
> It freezes too... :(
It freezes too....you mean New Vegas under Windows ?
My suggestion would be to try without overclocked system. 

Just to be shure ;)

---

### Post by Dlambert on 2011-05-17
Nope, just the game

---

