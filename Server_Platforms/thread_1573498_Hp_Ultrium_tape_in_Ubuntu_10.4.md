---
title: "Hp Ultrium tape in Ubuntu 10.4"
date: 2010-09-12
forum: Server Platforms
---

### Post by LtPitt on 2010-09-12
Hello everybody!

I'm trying my best to get this little damn thing working and I don't have a clue about what I'm doing wrong.
I've enabled it as a scsi device in vmware and looks like ubuntu server recognized it perfectly.
First backups I've tried worked great but as soon as I've prepared a silly script and put in on crontab things started to go crazy.

Right now if I do a fresh reboot of the virtual machine and I do a sudo -f /dev/st0 status

I get a "Device or resource busy".

If I try to remove the module with 

sudo rmmod st

I get a "Module ST is in use".

What's the next move?
Just resetting the tape drive or powering off the whole esxi machine that runs also the ubuntu server we're talking about?
Since it also works like a fileserver and mysql server turning it off would be my last action and I'd be really glad to remove and install by scratch the tape device without stopping other services.

I'd be pleased to receive any kind of hint or help, even just suggestion about what manual to read to understand better the whole process...
Sincere thanks for your time :)

---

