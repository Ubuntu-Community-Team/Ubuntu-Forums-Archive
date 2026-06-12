---
title: "re-partition re-size"
date: 2009-05-19
forum: Server Platforms
---

### Post by salim.madni on 2009-05-19
dear gurus

i would like to know

i have 1 LIVE ENVIRONMENT machine small application i have installed on this

i created two partition

1st partition as swap
2nd partition as / root partition

and everything installed inside "/"

now i realize that it is not safe to put everything under root / 

so can some one suggest me i need to re-partition re-size
where i can get free space 

and create 3rd partition knows as /application

we have aprox 70% empty hard disk.

first we will try on testing machine then do on live

but since i am first time experiences have no exactly idea step by step what to do, how to do?

kind regards
salim

---

### Post by windependence on 2009-05-19
Boot from a live gparted CD and then shrink your root (/) partition to gain free space. Then, you can create your new partiton(s) from the CD, reboot, and you are good to go. the gparted CD is here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

-Tim

---

