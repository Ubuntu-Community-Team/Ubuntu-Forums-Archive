---
title: "server not booting automatically 12.04"
date: 2012-08-17
forum: Server Platforms
---

### Post by darkapec on 2012-08-17
Hello, 

I recently upgraded from 10.04 ubuntu server to 12.04. I do have a couple issues going on and I am not sure if they are the reason this is happening or if something else is going on.

When I reboot the server, grub appears, attempts to auto start the first option, loads to a black screen and does not load any further.

I will then press ctrl+alt+delete, the server will reboot again only this time it will hang at the grub menu waiting for me to interact with it ( I assume default behavior if the prior startup did not load correctly) If I simply press enter at the grub screen this time (still selecting the first option) it will boot just fine. I have enabled the bootlogd option in /etc/default/bootlogd however it does not seem to be printing.

I am not sure where to look to see what could be causing the problem.

But I currently do have a failing raid with only 3 of the 4 devices hooked up (not sure if this could halt startup). The new drive will be here Tuesday to fix that problem. I also noticed on my 10.04 setup of ubuntu server would occasionally attempt to boot into the GUI, locking up before it fully loaded. So I am not sure if there are some GUI components that are still hanging around and the upgrade to 12.04 brought them back to life. 

Any ideas?

---

### Post by darkod on 2012-08-18
If that is a software raid, there is one option saying whether it should boot degraded or not. A faulty disk might be stopping the boot if the option to boot degraded is not enabled.

You can boot it once and change that option. I don't know where from the top of my head but google can easily answer where to find that option.

---

### Post by darkapec on 2012-08-18
I do get a "degraded raid" error on the second reboot. The first reboot seems to hang either at that point or just before it. I guess I will know Tuesday when the new drive arrives. 

I have had this server for many many years and have done so many things to it trying to figure things out that I probably just screwed something up at some point. Maybe it is time to do a fresh install, now that I am much more familiar with ubuntu. 

Thanks for your help

---

