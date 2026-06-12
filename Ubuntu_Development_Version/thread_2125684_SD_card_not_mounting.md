---
title: "SD card not mounting"
date: 2013-03-14
forum: Ubuntu Development Version
---

### Post by superchar42 on 2013-03-14
USB devices and everything else mounts just fine, but put in an SD card and it does nothing. 

Thoughts?

---

### Post by cariboo on 2013-03-14
Do you get any indication that the SD card is being detected when inserted? To check open a terminal and type:

```
dmesg
```

after you have plugged in the device.

---

### Post by superchar42 on 2013-03-14
Yes, a -110 error of some sort

```

 8150.208180] mmc0: Timeout waiting for hardware interrupt.
[ 8150.210238] mmc0: error -110 whilst initialising SD card
[ 8160.320051] mmc0: Timeout waiting for hardware interrupt.
[ 8160.322130] mmc0: error -110 whilst initialising SD card
[ 8170.432186] mmc0: Timeout waiting for hardware interrupt.
[ 8170.434258] mmc0: error -110 whilst initialising SD card
[ 8180.544187] mmc0: Timeout waiting for hardware interrupt.
[ 8180.546256] mmc0: error -110 whilst initialising SD card


```

---

### Post by superchar42 on 2013-03-14
apparently it's a kernel incompatibility - [http://www.linuxforums.org/forum/coffee-lounge/191312-new-kernels-incompatible-some-sdcards.html](http://www.linuxforums.org/forum/coffee-lounge/191312-new-kernels-incompatible-some-sdcards.html)

---

