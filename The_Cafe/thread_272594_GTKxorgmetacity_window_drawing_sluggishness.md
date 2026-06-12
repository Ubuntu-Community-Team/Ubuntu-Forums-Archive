---
title: "GTK/xorg/metacity window drawing sluggishness"
date: 2006-10-06
forum: The Cafe
---

### Post by NoTiG on 2006-10-06
Ok, i recently posted this before.... it is not my imagination or hardware. I have THREE different computers, each with completely different hardware. I have used open source drivers, mesa drivers... and binary drivers and the result is the same regardless.

1. Open up system monitor and watch cpu usage
2. Click on the top of a window and hold it down
3. watch the cpu usage go from 0 - 100 when you start moving the window around

So what exactly is causing this? xorg, metacity, or gtk? 

BTW i have tested this with systems with ATI and nvidia cards. it makes no difference.

(i havent tested aiglx or xgl though)

---

### Post by mushroom on 2006-10-06
That's generally my biggest complaint about desktop Linux. Really sluggish window drawing; it has me considering turning on composite and moving to KDE so I can use its neat effects without having to use Compiz/Beryl.

---

### Post by ahaslam on 2006-10-06
Have you got intergrated graphics?

Tony.

---

### Post by NoTiG on 2006-10-06
no i dont have integrated graphics... even on my laptop. I have a Geforce 7900 GS, a geforce 6200 and an ati 9600

---

### Post by NoTiG on 2006-10-06
interestingly enough though........ i just tested with 3d acceleration and it doesnt seem to spike the processor

---

### Post by maniacmusician on 2006-10-06
and no sluggishness either? [sigh] lucky you

---

### Post by NoTiG on 2006-10-06
the edges of windows still look a bit glitchy when moving....... just because the cpu isnt being spiked anymore doesnt necessarily mean nothing is wrong.... it just means that the burden has transfered to the graphics card.

---

