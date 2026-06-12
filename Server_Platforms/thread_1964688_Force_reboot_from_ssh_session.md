---
title: "Force reboot from ssh session"
date: 2012-04-24
forum: Server Platforms
---

### Post by mrmixaplix on 2012-04-24
We have an Ubuntu server 10.04 machine running a webcam in a firetower on a mountain top. It looks like the hard drive may be failing. I realize it will need to be replaced. I can ssh into the server, but most commands return a Input/output error. I've been trying to force a reboot on the off chance that disk check will run at reboot. I've tried "sudo shutdown -r now", "sudo reboot", "sudo init 6", they all threw the input/output error. Is there a way I can force ubuntu to reboot when the only commands I can use are the one currently loaded in ram?  I've already tried killing processes in an attempt to make the server crash, kill also throws the input/output error.

---

### Post by Habitual on 2012-04-24
```
sudo halt
```?

---

### Post by mrmixaplix on 2012-04-24
Opps, I wanted to say "sudo reboot"

---

### Post by SlugSlug on 2012-04-24
maybe scp reboot to the ram on server?

scp /sbin/reboot  usr@server:/dev/shm


then ssh in and 


sudo /dev/shm/reboot

sometimes ram its located 

 /run/shm

instead

---

### Post by dargaud on 2012-04-24
Neat trick about shm.

To force a disk check you normally do either:
```
sudo shutdown -rF
sudo touch /forcefsck && sudo reboot
```
But in your case it may throw an error as well.

---

### Post by mrmixaplix on 2012-04-24
> **SlugSlug said:**
> maybe scp reboot to the ram on server?

scp /sbin/reboot  usr@server:/dev/shm


then ssh in and 


sudo /dev/shm/reboot

sometimes ram its located 

 /run/shm

instead
Good thinking, unfortunately the server threw the input/output error when it tried to run scp at its end.

---

### Post by SlugSlug on 2012-04-24
ok try

 ssh root@server 'bash -s' < /sbin/reboot

---

### Post by SlugSlug on 2012-04-24
or maybe something like


 tar zcf - /sbin/reboot | ssh user@server 'tar zxf -'

---

### Post by kevdog on 2012-04-24
sudo init 6

or what I've done before is put init 6 within the roots cron daemon file and had it reboot at a specific time.

---

### Post by mrmixaplix on 2012-04-24
I tried using
ssh user@server cat < reboot ">" /dev/shm/reboot
That copied the reboot app to the memory on the server
did a chmod 775 on it
when I tried to run reboot I got all kinds of syntax errors
tried the same technique with init and shutdown
same thing, syntax errors
then I tried uuencoding the apps before I uploaded them to memory
uploaded fine, uudecode fails silently

Guess I have to wait until I can get up the mountain and pay an in person visit.

---

