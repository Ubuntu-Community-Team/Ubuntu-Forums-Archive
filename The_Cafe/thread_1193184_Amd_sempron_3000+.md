---
title: "Amd sempron 3000+"
date: 2009-06-21
forum: The Cafe
---

### Post by elliotn on 2009-06-21
I cant seem to find what the speed of this processor is. Not even conky can show it

---

### Post by elliotn on 2009-06-21
Bump

---

### Post by ajgreeny on 2009-06-21
```
sudo lshw -C cpu
``` will show you the speed in the output in the following format, like mine:-

```
*-cpu
          description: CPU
          product: AMD Sempron(tm)   2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1670MHz
          capacity: 3GHz
          width: 32 bits
          clock: 166MHz
```You can save the full hardware output as a txt file or an html file if you prefer, with the commands ```
sudo lshw -C cpu >lshw.txt
```or ```
sudo lshw -C cpu -html > ~/hardware.html
```

---

### Post by elliotn on 2009-06-21
And is there a way to find the type of mobo.

---

### Post by CharmyBee on 2009-06-21
Socket 754 or 939 with DDR400/500 usually.

---

### Post by Dropbear on 2009-06-21
> **CharmyBee said:**
> Socket 754 or 939 with DDR400/500 usually.

Can also be AM2 with DDR2 533/667/800 memory.

I'm pretty sure they run at 1.6 GHZ

---

### Post by cariboo on 2009-06-21
Another option, is to install lshw-gtk, it is in the repositories. You have to start it as root to get proper results. Press Alt-F2 and type:

```
gksu lshw-gtk
```

See screenshot to see results.

---

### Post by ajgreeny on 2009-06-21
also you could install **hwinfo** which will do it with a gui, but the command line is so quick and easy I've never bothered.

---

