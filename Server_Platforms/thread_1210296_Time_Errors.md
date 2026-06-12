---
title: "Time Errors"
date: 2009-07-11
forum: Server Platforms
---

### Post by tim124 on 2009-07-11
A month back loads of services on my VPS stopped working. After messing about for an hour or so i worked out that the time had frozen. I gather it was some sort of virtualization bug and a reboot soon fixed it.
 
However, today I was trying to run my S3 backup and SSL failed due to the time being wrong. on checking the time i get:
 
Current default timezone: 'Europe/London'
Local time is now: Sat Jul 11 18:08:57 BST 2009.
Universal Time is now: Sat Jul 11 17:08:57 UTC 2009.
 
tim@vps:~$ sudo ntpdate ntp.ubuntu.com
11 Jul 18:09:30 ntpdate[3901]: step time server 91.189.94.4 offset -14404.833448 sec
 
Now im in the UK now and its clearly only just gone 14:10.
 
What have i messed up? ;)

---

### Post by tim124 on 2009-07-11
ive tried setting the date manually:
 
sudo date +%T -s "15:03:30"

and when i read it back, it hasnt changed

---

### Post by gombadi on 2009-07-11
> 
A month back loads of services on my VPS stopped working


What type of VPS are you using - xen or OpenVZ based?

If it is OpenVZ based then the time is controlled from the one kernel running all the VPS's. You will not be able to change the system time from within your VPS. 

What did your hosting provider say when you reported the problem to them?

---

### Post by tim124 on 2009-07-11
Its Xen. The hosting provider have been on to it and they think its a hardware issue, possibly bios battery. When the host machine boots up the clock is wrong and apparently they cant change the time while its up without locking up all the vm's!

---

### Post by tim124 on 2009-07-11
I did try to de-sync the time:
 
```
sudo echo 1 > /proc/sys/xen/independent_wallclock
```
 
but it says access denied which is weird...

---

