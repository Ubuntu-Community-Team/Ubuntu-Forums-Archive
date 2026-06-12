---
title: "I now have Ubuntu 20.04 running on 5 machines"
date: 2020-05-21
forum: The Cafe
---

### Post by irv on 2020-05-21
When Ubuntu 20.04 was released last month, I had it already running on 3 machines doing some testing. When it was released I just did some update and kept going.
Yesterday I went down to the chapel sound room where I had two older laptops running Ubuntu 18.04. I decided to upgrade them to 20.04, which I did. In the past, I never had much luck with upgrades, I always ended up doing a clean install. But this all went well. I did it from the command line.
```
sudo do-release-upgrade -d
``` 
It took about 2 hours because of the slower machines and a 30mps Internet speed. Which I thought was pretty good. (I did both computers at the same time.)
My desktop and one laptop at home only took about 45 minutes to do the upgrade, but they are faster machines and I have a 200mps Internet speed. My smaller laptop a Dell Inspiron 11 3000 2 in 1 was a fresh install and on wifi at 22mps took about an hour. I installed it from a USB 3. Overall, 20.04 is a real mature OS in my opinion.

---

### Post by EuclideanCoffee on 2020-05-21
Interesting report. I'm happy to hear that the upgrade process went smoothly. I'm enjoying Ubuntu 20.04 on two computers. Still need to use 18.04 LTS. But I prefer 20.04 LTS. :)

---

### Post by irv on 2020-05-21
Just wondering why you need to keep using 18.04?

---

### Post by Perfect Storm on 2020-05-22
Congrats. ^_^

I myself love to do clean install to set everything up again, but that's just me. Again I tweak/modify stuff a lot so an upgrade may break my system. :D

---

### Post by Skaperen on 2020-05-24
i definitely will be doing a fresh re-install.  and that's not because that's just how i always do it, but because i need to re-partition to make /dev/sda1 get some more space.  so /dev/sda3 will shrink.  /devsdc will be made identical as a 1st level backup (2nd is an external drive, 3rd is an AWS S3 bucket, and a 4th is going to be at a 2nd cloud provider to be determined).  i've been working under the clean install principle since my early mainframe days circa 1979.

i also always do a reboot before and after each upgrade which is about once a week (manually).

---

### Post by poorguy on 2020-05-24
> **irv said:**
> Just wondering why you need to keep using 18.04?
It's all about choice if you want to upgrade to Ubuntu 20.04.

I'm using Ubuntu 18.04 and Ubuntu 20.0 4 and both are great imo.



@Artificial Intelligence

I agree and also like to do a clean install to set everything up again with minor tweaking.

There ain't nothing better than a clean install which is why I never do version to version upgrades.

---

### Post by mastablasta on 2020-05-25
> **irv said:**
> Just wondering why you need to keep using 18.04?


if it works, why mess with it? also i am curious when nvidia will suddenly drop their support for my card. it should be sometime in 2022 officially, but i am not sure what this actually means since ubuntu uses a bit older kernel and stuff than others.

in any case there are no issues with 18.04 at the moment. everything is setup. so i see no major reason to move to 20.04. PC is old anyway.. i was on windows XP until Jan 2019 and i still keep it on separate drive. though i see that i can run most (old) games i used to run on windows, so it's been a while since i actually booted to it.

---

### Post by poorguy on 2020-05-25
> **mastablasta said:**
> i am curious when nvidia will suddenly drop their support for my card. it should be sometime in 2022 officially, but i am not sure what this actually means since ubuntu uses a bit older kernel and stuff than others.

What graphics card are you using.

I've had excellent results using the Nouveau Diver with my old Nvidia integrated graphics adapter.

```


thomas@COMPAQ-PRESARIO:~$ inxi -G
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: x11 (X.Org 1.19.6 ) drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1152x720@59.97hz
           OpenGL: renderer: NV4C version: 2.1 Mesa 19.2.8
thomas@COMPAQ-PRESARIO:~$ 


```

---

### Post by mastablasta on 2020-05-26
good to hear that. i use GT 730 and i use it to play games on a really old PC. it can play a lot of games, at least at low settings.

---

### Post by Hwæt on 2020-05-26
In my case, I've just been too busy to upgrade to 20.04. One of these days I'll have the free time.

---

