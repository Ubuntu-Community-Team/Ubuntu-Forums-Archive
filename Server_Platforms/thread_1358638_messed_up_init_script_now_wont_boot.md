---
title: "messed up init script now wont boot"
date: 2009-12-18
forum: Server Platforms
---

### Post by kylegio on 2009-12-18
ive been having ongoing trouble with networking not working on boot ever since my upgrade to 9.10, anyway thats a problem for another day now. made some changes to the init script (yes i made a backup of the original). but i cant get the computer to boot now, it starts bootup then says networking ended with status 1 or something like that, it always said that ...but now it just sits there forever and goes no further. 

i have tied "recovery" mode from the grub menu, same deal, i have tried plugging my harddrive into another linux machine and it wont let me see the files, i do not have a startup disk on me but i will try to get one. 

anyway is there a way to boot without networking, or without processing any init scripts/ omitting certain ones that are causing troubles so i can atleast get back into terminal and replace my botched init script. 


thanks

---

### Post by kylegio on 2009-12-18
update: i did manage to get into terminal by just holding esc the whole time then it told me to type ctrl+d to boot a recovery console, got into the console (it only logs in as root) but the filesystem is "read only" and i cant fix anything that way
suggestions??

---

### Post by sisco311 on 2009-12-18
At the grub menu highlight the *Recovery Mode*, press e for edit, edit the *linux* line, replace *ro single* with *rw init=/bin/bash*, press Ctrl+x to boot.

---

### Post by sisco311 on 2009-12-18
> **kylegio said:**
> update: i did manage to get into terminal by just holding esc the whole time then it told me to type ctrl+d to boot a recovery console, got into the console (it only logs in as root) but the filesystem is "read only" and i cant fix anything that way
suggestions??

```
mount -o remount,rw /
```

---

### Post by kylegio on 2009-12-18
> **sisco311 said:**
> ```
mount -o remount,rw /
```

yeah i figured that one out, i have read-write access now, replacing my old init script did not fix the problem. it must have been the upgrade i performed before rebooting that f'd it up, it upgraded upstart and something else.... cant remember

anyway i have tried to just disable networking on init completly, i have removed execute permission from the etc/init.d/networking script, i have used update-rc.d -f networking remove

no matter what i do it lists off a bunch of errors sorry i dont have the exact errors it gives but its along the lines of 
init: eth0 processes terminated with status 1

it lists it for every interface then just says networking processes terminated with status 1 and stops boot.... i cant seem to do anything (although ctrl+alt+del does initiate a restart properly)


am i missing something here? is there another way that networking would be starting on boot?

---

### Post by sisco311 on 2009-12-18
> **kylegio said:**
> 

it lists it for every interface then just says networking processes terminated with status 1 and stops boot.... i cant seem to do anything (although ctrl+alt+del does initiate a restart properly)


Try to press Ctrl+c.

> **kylegio said:**
> 

am i missing something here? is there another way that networking would be starting on boot?

In Karmic the network is started by an Upstart job.

To disable it, rename the job file:
```
mv  /etc/init/networking.conf /etc/init/networking.conf.noexec
```

---

