---
title: "I found KDE again..."
date: 2006-07-07
forum: The Cafe
---

### Post by Kimm on 2006-07-07
Back when I was a beginner Linux user I was using KDE. Mainly because it was allways installed by default be every distro I tried.
The first time I tried Gnome (Mandrake 10) I loathed it...

Then... Ubuntu came along and changed all that, and I have been using eighter Gnome or XFCE4 ever since Warty was released.
Today I desided to go ahead and install KDE again. And I have to say... I'm baffled.
It seems lighter than XFCE :o and applications launch faster, not to mention run faster... my games seem to perform much better and I love the polished look...

This time KDE is here to stay!

But I'm curious... can anyone explain to me what is causing this performance boost? :-k

---

### Post by raptros-v76 on 2006-07-07
kde's just more badass i guess. to tell you the truth im not sure, maybe certain libraries are kept loaded. or something. i dont know. i could be entirely wrong

---

### Post by bruce89 on 2006-07-07
It's a matter of choice really.  Speed is difficult to quantify in this sense.  What's the RAM usage like?

---

### Post by Kimm on 2006-07-07
Well yes, of course.
I don't know how much memory is in use... how do I tell in KDE? :-P

---

### Post by ComplexNumber on 2006-07-07
> **Kimm said:**
> Well yes, of course.
I don't know how much memory is in use... how do I tell in KDE? :-P
go to the commmand line and type in 'free'. if possible, print the result out here so that people can judge.

---

### Post by raptros-v76 on 2006-07-07
kde does use more memory, but if you have the memory to spare, its great

---

### Post by Kimm on 2006-07-07
```

             total       used       free     shared    buffers     cached
Mem:        254892     233380      21512          0       6028     103648
-/+ buffers/cache:     123704     131188
Swap:       746980      66620     680360


```

I have no idea how to interpret that :P

---

### Post by bionnaki on 2006-07-07
hmmm

---

### Post by bruce89 on 2006-07-07
Why does free seem to be wrong here?
```
             total       used       free     shared    buffers     cached
Mem:       1028508    1020504       8004          0      98720     449768
-/+ buffers/cache:     472016     556492
Swap:       265032          0     265032
```
System Monitor says just over 466MiB used.

---

### Post by croak77 on 2006-07-07
> **bruce89 said:**
> Why does free seem to be wrong here?
```
             total       used       free     shared    buffers     cached
Mem:       1028508    1020504       8004          0      98720     449768
-/+ buffers/cache:     472016     556492
Swap:       265032          0     265032
```
System Monitor says just over 466MiB used.

Cause it's cached. free -m will get the result in MB.

---

### Post by jnev on 2006-07-07
same thing happened to me. I started with kde, moved to gnome with ubuntu, and just now installed kubuntu on my system. I love it :D, uses less ram (~115mb on boot, I run kde on my 366mhz p2 laptop with 256mb ram), is faster than gnome, and has more options.

---

### Post by drizek on 2006-07-07
> **Kimm said:**
> can anyone explain to me what is causing this performance boost? :-k

A lot of blood, sweat and tears.

I guess the KDE devs got sick of people saying gnome was faster. The best news is that KDE 4 should be even better due to all the optimizations in Qt4 as well as all the overhaul of the entire KDE desktop that is required when porting.

Edit: BTW, top sucks. apt-get install htop

---

