---
title: "Make gives error.  TV tuner Avertv Combo PCIE(M780) though just works great"
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-29
Adding you need file ngene_15.fw which is easy to get.
just install linux-firmware-nonfree package.

No need to compile anything.

trying to compile this driver following instructions
[http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner](http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner)


```
scott@scott-P5QC:~/v4l-dvb$ sudo make
make -C /home/scott/v4l-dvb/v4l 
make[1]: Entering directory `/home/scott/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 3.3.0
File not found: /lib/modules/3.3.0-17-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/scott/v4l-dvb/v4l'
make: *** [all] Error 2
scott@scott-P5QC:~/v4l-dvb$ 
```

---

### Post by sdowney717 on 2014-03-29
[http://www.linuxtv.org/wiki/index.php/Talk:How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/Talk:How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

Cant figure out this out. Talks of how to fix compiling error for DVD driver. I get the same error they talk of fixing, just a different kernel name.
Following their fixes, I still keep getting the same error.

---

### Post by sdowney717 on 2014-03-29
solved, As I do not have to make the dvd driver, it is already there.
Running TV Time with this Avertv Combo PCIE(M780)

It showed a device under /dvb folder, so it was already there.
And the linuxTV web page also mentions you may not have to compile the driver, So pleasantly surprised!

---

### Post by sdowney717 on 2014-03-29
This little program called metv is very nice.
I had also installed TVTime.
I noticed it needed better deinterlacing, so I set deinterlace to TVTime in the the settings for MeTv.
Then deinterlacing works well.

Actually it got better, but on very fast motion still has deinterlace problem.
Well restarted program and deinterlace is perfect!

---

