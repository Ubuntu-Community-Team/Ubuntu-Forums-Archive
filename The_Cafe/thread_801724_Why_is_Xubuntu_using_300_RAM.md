---
title: "Why is Xubuntu using 300 RAM"
date: 2008-05-20
forum: The Cafe
---

### Post by -gabe-noob- on 2008-05-20
you heard me right, Xubuntu 8.04 is using 300 RAM on my system...

---

### Post by bufsabre666 on 2008-05-20
i bet firefox is a good chunk of that

---

### Post by -gabe-noob- on 2008-05-20
49 mb's...  how about the other 250?

---

### Post by FuturePilot on 2008-05-20
Well the machine I run Xubuntu on doesn't even have 300MB of RAM. Not even close
```
              total       used       free     shared    buffers     cached
Mem:           186        175         10          0         13         86
-/+ buffers/cache:         74        111
Swap:          541        107        433

```

---

### Post by bufsabre666 on 2008-05-20
everything else? my kde uses 700mb with usually about 100 to firefox and ktorrent

so 250 compared to 600 isnt that bad

---

### Post by -gabe-noob- on 2008-05-20
yea but I swiched from gnome cause i wanted everything to be FAST!!!

and that was using around 300 runing compiz among other things

---

### Post by bufsabre666 on 2008-05-20
> **FuturePilot said:**
> Well the machine I run Xubuntu on doesn't even have 300MB of RAM. Not even close
```
              total       used       free     shared    buffers     cached
Mem:           186        175         10          0         13         86
-/+ buffers/cache:         74        111
Swap:          541        107        433

```

well look at your swap usage, ive never even had more than 4mb in my swap, the computer assesses what you have and knows how much it can put everywhere

---

### Post by bufsabre666 on 2008-05-20
> **-gabe-noob- said:**
> yea but I swiched from gnome cause i wanted everything to be FAST!!!

and that was using around 300 runing compiz among other things

try e17 or flux

sry about the double post

---

### Post by gsmanners on 2008-05-20
I'm running Xubuntu with about 2000 apps installed along with Firefox and several other apps (and I just got through using K3b), and I'm still only at 272 MBs.

---

### Post by -gabe-noob- on 2008-05-20
anyways I don't know how to customise XFCE like i custimised gnome...

---

### Post by Tatty on 2008-05-20
Linux uses memory a little differently to windows.  When software gets closed on a linux machine, it doesnt remove it from the RAM, it will only remove it if the space is needed by some other software.

The idea is that if you open the application again shortly after closing it (most of the time it is the same software that is run again and again) then it is already loaded into RAM so it doesnt take as long to start.

Try it, open firefox, then close it, then open it again, It will be much quicker the second time because it is already loaded into ram.

So the 300Mb will be the total amount of memory that has been used by software from when you first booted.

To find out how much memory is acutally needed by software right now you need to run the "free" command in a terminal and then subtract the used cache from the used memory.  for example on my machine:

```
             total       used       free     shared    buffers     cached
Mem:        964328     955244       9084          0        828     341660
-/+ buffers/cache:     612756     351572
Swap:      2827400      43284    2784116
```

So the amount of memory being used atm on my machine is 955244 - 612756 = 342488

So around 342Mb is being used - which sounds about right cos ive got a lot of big things open at the moment.

---

### Post by -gabe-noob- on 2008-05-20
Anyone know how to install a theme in XFCE?

---

### Post by -gabe-noob- on 2008-05-20
Nice post tatty.

---

### Post by cardinals_fan on 2008-05-20
> **-gabe-noob- said:**
> Anyone know how to install a theme in XFCE?
Copy the folder to /usr/share/themes/ and select it under UI Settings / WM Settings.

---

### Post by myusername on 2008-05-20
actually xfce just takes getting used to. but i can customize things better in it

---

### Post by swoll1980 on 2008-05-20
If your pc has the ram the os will use as much of it as it can to make things run faster that doesn't mean you need 300mb of ram to run Xubuntu. Ive seen puppy linux using over 500mb of ram before on a copy I installed on my friends pc, but you only need like 8mb of ram on a system which has it installed on the hard drive

---

### Post by andrewabc on 2008-05-23
Xubuntu using 300mb of ram is very wierd. My default ubuntu install on a pentium4 768mn ram computer uses around 300mb of ram. Same for my new computer with 3gb of ram. It uses 250mb ram on startup, then uses some more for firefox etc.

---

### Post by shrimphead on 2008-05-23
> **cardinals_fan said:**
> Copy the folder to /usr/share/themes/ and select it under UI Settings / WM Settings.

~/.themes/ works too and doesn't require root privaleges

---

### Post by TenPlus1 on 2008-05-23
300mb is a bit much as my Gnome 8.04 install boots into 100mb usage at desktop, with up to 60mb for Opera, up to 20mb for Deluge and 10 for Pidgin...

---

