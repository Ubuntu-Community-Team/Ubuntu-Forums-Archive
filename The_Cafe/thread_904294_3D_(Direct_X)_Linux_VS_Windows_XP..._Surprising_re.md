---
title: "3D (Direct X) Linux VS Windows XP... Surprising results."
date: 2008-08-29
forum: The Cafe
---

### Post by zx6r1033 on 2008-08-29
Mods: I didn't know exactly where to put this, so if you would be so kind... make sure it lands wherever it belongs? Thanks!




I ran Performance Test, which is a benchmark tool, tonight. The graphics are all DirectX based, so DX needed to be loaded in order to run the program. The program itself, as well as DX, were both installed via Wine.    I will post the results as a GIF this afternoon, since the overall test was interesting enough, but the most shocking were the results on the graphics. 



The computer is one that I built...

Motherboard: M2N-SLi
Processor: AMD Athlon 64 x2 4800+ 2.5ghz dual core OC'd to 2800mhz
Memory A.Data DDR2 6400 800mhz 2 x 2gb sticks
GPU: EVGA Nvidia GeForce 8500GT 128bit 1gb

OS Versions: 

Ubuntu 8.04 Hardy 64bit
Windows XP 32bit with SP3

The 3d graphics were tested in 3 categories: Simple 3d objects, medium 3d graphics, and advanced 3d graphics. The simple 3d is tested at 640x480 32bit res, and the medium and advanced are both tested at 800 x 600 32bit. Medium is displayed in a small box, and the advanced is expanded to full screen. 



Simple 3D graphics (Average)

Windows XP: 560fps
Ubuntu:     1640fps


Medium 3D Graphics (Average)

Windows XP: 150fps
Ubuntu      220fps


Advanced 3D Graphics

Windows XP: 48fps
Ubuntu:     27fps (and vertical bars)



While the Advanced 3d did exactly what I was expecting after reading the various threads about DirectX + Wine, I couldn't believe the frame rate tripled on simple 3d objects... and I definitely wasn't expecting the medium graphics to be better. 



The other odd twist in my testing was "simple 2d text." XP registered nearly 600fps on the scrolling tests, and Linux nearly died out at 3.2fps. I am going to re-run that test when I wake up. Something definitely went wrong there, and it's not my gpu's ability to render text, that's for sure!


Anyway... I will post the results when I get up. I just thought someone else might find the results as interesting as I did.


Just one side note to save from anyone asking... both XP and Ubuntu had the newest graphics drivers installed and running, and both programs are a fresh install with virtually nothing added to either of them for programs and things like that. I wiped my HD last week and started from scratch with the dual boot setup on this computer.

---

### Post by Prefix100 on 2008-08-29
Wait you installed DirectX in wine?

I thought that caused the program to completely fail?

---

### Post by zx6r1033 on 2008-08-29
> **Prefix100 said:**
> Wait you installed DirectX in wine?

I thought that caused the program to completely fail?


That is what everything I read had said as well... but I installed it in wine and it works.

---

### Post by zx6r1033 on 2008-08-29
[Test Results]("http://www.dv8films.com/perfres.gif")

---

### Post by SunnyRabbiera on 2008-08-29
> **Prefix100 said:**
> Wait you installed DirectX in wine?

I thought that caused the program to completely fail?

Well Direct X 9 is known to work most of the time via wine.

---

### Post by Crafty Kisses on 2008-08-29
> **SunnyRabbiera said:**
> Well Direct X 9 is known to work most of the time via wine.

Yeah, I've seen some videos about this stuff last night. :)

---

### Post by Prefix100 on 2008-08-31
so I can get better performance by installing dx9? Cause some games run like ****.

---

### Post by zx6r1033 on 2008-08-31
> **Prefix100 said:**
> so I can get better performance by installing dx9? Cause some games run like ****.


Depends on the game. (Based only on my experience, of course.)

When I was running the test in full screen mode, I got some very abnormal vertical scrolling bars that were about 1" wide and spaced a few inches apart. At any one time there would be two bars on the screen. 

When I ran the test at the same resolution, but in a window instead of full screen, it ran with better performance than the exact same test on Windows XP.

---

### Post by Levander on 2009-03-05
> **zx6r1033 said:**
> When I was running the test in full screen mode, I got some very abnormal vertical scrolling bars that were about 1" wide and spaced a few inches apart. At any one time there would be two bars on the screen.

Would you be surprised if this were a hint as to why your numbers turned out so screwy?

Maybe the Wine implementation was just throwing out some operations and just not doing all the things the benchmark and DirectX were asking it to perform??

And, taking the guess a step further, possibly the Advanced benchmark, Wine was so awful, that even though it was throwing some stuff out and not doing it, the stuff it was doing was so ridiculously slow that even the subset of the stuff it was doing was still slower than a native Windows run?

---

### Post by handy on 2009-03-06
I remember a year or so ago discussing dx on the Codeweavers forum & it was stated that there is no need to install dx9 as Crossover (dare I say Wine) has many (certainly not all) of the functions of dx incorporated into it.

---

