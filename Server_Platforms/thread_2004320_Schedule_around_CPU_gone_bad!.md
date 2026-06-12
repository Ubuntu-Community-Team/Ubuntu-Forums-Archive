---
title: "Schedule around CPU gone bad?!?"
date: 2012-06-15
forum: Server Platforms
---

### Post by faroutliving on 2012-06-15
I have a remote server, which one of the 2 cpus has started overheating (as reported by sensors). I can't get to the server until Monday at the earliest, and when the server schedules something on the "bad" cpu the performance tanks.

What can I do remotely to disable the cpu/cores? So far, the best answer I have is to create 12 cpu intensive processes and use taskset to force them on to the bad cores (as soon as I figure out which cores are the ones on the overheated cpu).

Thanks for your help!

Deron

---

### Post by Gyokuro on 2012-06-15
Hi 

you can offline a CPU but it depends whether you are able to reboot the machine or disable it on the fly:

reboot method:

edit grub.cfg

and add following to your grub line

maxcpus=1

or on the fly method

sudo sh -c "echo 'n' > /sys/devices/system/cpu/cpu1/online

but this will not survive a reboot.

---

### Post by faroutliving on 2012-06-16
Thanks for the help, but I don't think it is working (the on the file method). Would online exist before copying something to it? Because they don't :-(

---

### Post by faroutliving on 2012-06-16
Never mind. The online files do exist, but they always contain "1" even after executing your command: sudo sh -c "echo 'n' > /sys/devices/system/cpu/cpu12/online"

Could "n" be 0 instead? Guess I have nothing to loose to try...

Yup, that seems to make a difference. And top now shows only the 12 "good" cpus.

Thanks for your help! I'll make this solved (well, the disabling the cpu, not the overheating ;-)

---

