---
title: "server 10.04 skip mount errors during boot"
date: 2010-04-29
forum: Server Platforms
---

### Post by Chal on 2010-04-29
is it possible to skip mounting errors during boot?

i have 3 usb disks and for them entries in the fstab.
when they are connected there is no problem during boot, but if one of them is disconnected the boot stops with a purple screen and says that the disk coul not be mounted.

the problem is that the boot stops there until u press s to skip it and cannot login per ssh

karmic booted with these errors and just didnt mount this disk

thank you for help

---

### Post by Chal on 2010-04-30
after a whole day of trying to fix this i have to give up

i just want to skip automatically and not always press s to skip

anyone any idea?

---

### Post by starcom on 2010-05-01
I had the same problem.
Fixed it by editing /etc/fstab

Edit the line with the affected drive, and add the following option: nobootwait

[COLOR=DeepSkyBlue]/dev/sdax       /media/drive    auto    rw,user,exec,**nobootwait**    0       0[/COLOR]

It works!

---

### Post by Chal on 2010-05-01
thank you soooooooooooooo much 
was trying 2 days to get this work

but now i get the error 
mountall: disconnected from plymouth

but this doesnt affect my system

thank you

---

### Post by Freaky#Funga on 2010-10-17
This solved also my problem, thank You so much!

---

### Post by jjv on 2010-12-29
I just upgraded a couple notebooks from 8.04 to 10.04 and this was the last niggling issue.

Thanks

---

### Post by Freaky#Funga on 2011-01-06
> **starcom said:**
> I had the same problem.
Fixed it by editing /etc/fstab

Edit the line with the affected drive, and add the following option: nobootwait

[COLOR=DeepSkyBlue]/dev/sdax       /media/drive    auto    rw,user,exec,**nobootwait**    0       0[/COLOR]

It works!

Hi,
I've followed your instructions and added nobootwait, but the drive still hangs in "s or m" option. Any idea why?

---

### Post by Doomicle on 2011-01-22
Fewz! Another linux crisis painstakingly averted...
As for why it's not working for you Freaky Funga. I can only speculate, as I really have no idea what I'm talking about, but perhaps it's because the fstab entry that isn't working is the system partition? I.e the computer wouldn't be able to continue because it's unable to mount the OS filesystem?

---

### Post by Freaky#Funga on 2011-01-22
> **Doomicle said:**
> Fewz! Another linux crisis painstakingly averted...
As for why it's not working for you Freaky Funga. I can only speculate, as I really have no idea what I'm talking about, but perhaps it's because the fstab entry that isn't working is the system partition? I.e the computer wouldn't be able to continue because it's unable to mount the OS filesystem?

Nope, system partition is working fine. This is my entry for one of drives which makes problems
```
UUID=b3f7fe47-5169-4e51-ba3a-93f7532c9a59 /media/data3     jfs     defaults,nobootwait,user        0       0
```
and maybe this NFS export has something common with problem
```
/media/data3  /export/data3  bind  bind,nobootwait  0  

```

---

### Post by lordgibbness on 2011-11-15
> **starcom said:**
> I had the same problem.
Fixed it by editing /etc/fstab

Edit the line with the affected drive, and add the following option: nobootwait

[COLOR=DeepSkyBlue]/dev/sdax       /media/drive    auto    rw,user,exec,**nobootwait**    0       0[/COLOR]

It works!

Thanks for this.

I had an interesting issue whereby I could sucessfully reboot the machine from the GUI and never had a problem.  However, if I was remotely connected via SSH and restarted the machine remotely from PuTTY (e.g. sudo reboot) - the GUI would never start.

I would get the mountall plymouth errors and VNC never started.  I could remote in via SSH, but I always had to reboot the machine if I ever wanted to make use of it for media (I use the machine for XBMC).

I added the nobootwait to my network shares in fstab, and the machine can be successfully rebooted from an SSH session now.

Thanks,
Rob.

---

