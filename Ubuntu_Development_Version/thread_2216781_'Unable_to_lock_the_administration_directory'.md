---
title: "'Unable to lock the administration directory'"
date: 2014-04-13
forum: Ubuntu Development Version
---

### Post by frank18 on 2014-04-13
Hi guys; i have this on the terminal when i want to install some slftware in ubuntu 14.04

---

### Post by 23dornot23d on 2014-04-13
You only need to enter

**sudo apt-get install synaptic**

then it might work - as long as nothing else is running like USC or

( yep - spotted it on the left - two white markers next to the orange bag - with A on it Ubuntu Software Center is running )

the lock may have been on if it was trying to do some automatic updates in the background maybe - need to come out

of it - so that you can use the terminal command as above in bold that is all you need to get synaptic in.

_________________________

---

### Post by deadflowr on 2014-04-13
Maybe I'm too late, but isn't that synaptic installing down at the bottom of the launcher?
You have the software center open, so it would seem you've already started the download process to install synaptic.
The software center does an interesting thing that the terminal and other installation method do not.
That is it throws the new applications icon onto the launcher as it is being installed.

Anyway, the odd thing is, if you had tried installing it through the terminal, it probably would have spit out a no package found for what you wrote. It looked like synaptic has a capital S. As well as Package and Manager would be read as two different programs altogether.

Well, hope something I wrote helps, somewhat...maybe.

---

### Post by frank18 on 2014-04-14
Thanks guys;i rebooted the pc and now all good, thanks

---

### Post by zika on 2014-04-14
> **23dornot23d said:**
> You only need to enter

**sudo apt-get install synaptic**

then it might work - as long as nothing else is running like USC or

( yep - spotted it on the left - two white markers next to the orange bag - with A on it Ubuntu Software Center is running )

the lock may have been on if it was trying to do some automatic updates in the background maybe - need to come out

of it - so that you can use the terminal command as above in bold that is all you need to get synaptic in.

_________________________Using plain **sudo** with GUI application (especially with one such as Synaptic) is not a good idea... **Gksu** or at least **sudo -H** should be used as we have wrote one time too much here and elsewhere... ;) It is weird that it still persist...

Edit: Mea culpa, I made an error in reading, explained below... Sorry...

---

### Post by 23dornot23d on 2014-04-14
> 
Using plain **sudo** with GUI application (especially with one such as Synaptic) is not a good idea... **Gksu** or at least **sudo -H** should be used as we have wrote one time too much here and elsewhere... :wink: It is weird that it still persist... 				


Think you should re-read .......... am installing it not running it ........

---

### Post by zika on 2014-04-14
> **23dornot23d said:**
> Think you should re-read .......... am installing it not running it ........Mea culpa, did not read well...
I've edited my message, sorry...
To redeem myself I'm offering a nice video: [http://www.youtube.com/watch?v=BKezUd_xw20](http://www.youtube.com/watch?v=BKezUd_xw20) ... ;)

---

### Post by 23dornot23d on 2014-04-14
Its ok - guessed you just scanned through it ....... early morning too ...... ;)

---

### Post by zika on 2014-04-14
> **23dornot23d said:**
> Its ok - guessed you just scanned through it ....... early morning too ...... ;)I wish I've scanned, obviously just glanced with this old glasses... ;)

---

### Post by grahammechanical on 2014-04-14
This problem will happen in whatever version of Ubuntu we are using if we try to access the repositories using the terminal and the software centre at the same time. Not 14.04 specific.

---

