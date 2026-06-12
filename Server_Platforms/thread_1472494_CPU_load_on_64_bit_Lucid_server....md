---
title: "CPU load on 64 bit Lucid server..."
date: 2010-05-04
forum: Server Platforms
---

### Post by pezball on 2010-05-04
cpu load on my dual hyperthreading core (4 apparent cores) home server is usually very close to zero, since not much going on there... however sometimes it goes up to well over 1.00, but I can not find that any processes are using much cpu time... ps -A does not show any changes in used cpu time for any processes...
 
Before update to 10.04 this never happened... if load was high I could always see that some process was eating processor time...
 
Are there any processes which can not be seen with ps for some reason?
 
The server is not acting slow, except for phpsysinfo which takes very very long time to show the page...
 
however if I reboot it may act fine again... this problem is not consistent between boots... which of course makes it impossible to solve... could it be that something happens to start a little quicker than something else, on some of the reboots or whatever... that is, it starts before it should, cos it relies on data from something that is slower to start... and so eats cpu time cos it does not get a response.. rather that go into wait state...

---

### Post by cariboo on 2010-05-04
Try top, or htop, to see if there is anything running that is causing the cpu to to peg.

---

### Post by pezball on 2010-05-04
thx will try that... right now there is no problem with this... will try top next time it happens

---

### Post by pezball on 2010-05-24
Hm interesting... now my load average is around 1.00 again and no processes using much CPU %...
 
running top tells my load average is 1.00 but CPU idle is close to 100% most of the time ... so it's more or less doing nothing and still doing a lot... how is that possible? how is load average calculated and how is it related to CPU idle if at all... sure seems strange... or is top not telling the whole truth for some reason? 
 
I hope there is no way for a process to run in an infinite loop, detached from the process manager in the kernel... so it's not showing up but still eating time... could it be possible for a process to be running while the kernel has no clue about it? ghost processes is something i do not need...
 
oh ya... now i see a process named khubd... it is interesting cos top says its status is D and it's using much processor time but not showing any cpu % or other data... does D stand for detached? if so... how do you kill it...
 
I need look more into what khubd is i guess...
 
I have noticed that this khubd is very active when i open up my phpsysinfo page... so i assume it collects some kind of info about my system... but after it's done it apparently does not always get idle or terminated as it should...

---

### Post by pezball on 2010-05-24
ok, khubd seems to be involved in the usb system...  now when load average is 1.00 as minimum and khubd eats much processortime, the command lsusb is incredibly slow...
 
phpsysinfo of course also reads usb status... so that's the link between slow phpsysinfo and this high processor load...
 
i have seen plenty bug reports about khubd eating processor time on older ubuntu releases...  and this is still true it seems... cups is now using a new system for usb printers, instead of the usblp kernel module, but i hope that does not give this problem.. the only usb device connected to my server is a printer.... so... can that be the problem somehow?

---

