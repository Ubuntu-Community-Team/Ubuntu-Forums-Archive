---
title: "[SOLVED] Joining mp3 files"
date: 2008-10-24
forum: Ubuntu Studio
---

### Post by Robbyx on 2008-10-24
I downloaded an opera. It comes in mp3 sections. I wish to play it from  a CD player. I assume that it should be combined into one file. Using a GUI is there a program that will combine them into one file?

---

### Post by Stochastic on 2008-10-24
You can do this in Audacity, but that decodes/reencodes the mp3, loosing quality.

I'd recommend using the command line tool mp3wrap. just do ```
mp3wrap output.mp3 inputFile1.mp3 inputFile2.mp3 inputFile3.mp3
```

You also, could just burn the mp3's as separate tracks in a CD with the time between tracks set to 0 rather than the default 2 seconds.

---

### Post by Robbyx on 2008-10-25
As there are so many files a manual listing of them into a command line is very time consuming. I think your idea of setting the time to 0 is very helpful. Thank you. I will try that idea. I wonder how do get the player to play the first track. Is it automatic? Will it automatically play every file on the disk even if they are not sequential? 

I have a few CD burners. Which one do you suggest is the best for this?

---

### Post by ashmew2 on 2008-10-25
Hi robbyx, I think that you dont need to combine all the mp3's together because a CD player will play files according to alphabetical order , For example , for the following files :

CAD.mp3
DAX.mp3
ABCD12.mp3
BACD.mp3

The order would be :

ABCD12.mp3
BACD.mp3
CAD.mp3
DAX.mp3

By the way  , to simply join them together , you can 

1) Make a Desktop folder and put all the input mp3s in it.
2) In the terminal , do :
```

cd ~/Desktop
cd <folder name>

mp3wrap output.mp3 *

```

It should do the trick!


If you like to use paid-for software , I'd highly recommend [Mixcraft]("http://www.acoustica.com/mixcraft/").

---

