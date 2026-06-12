---
title: "how to rebuild a drive in RAID"
date: 2008-07-15
forum: Server Platforms
---

### Post by nephish on 2008-07-15
Hey there all, 
I have a dell poweredge that is running xubuntu gutsy. 
It is a RAID 5. 
I hot swapped a drive and it will not build the new one, it just sits there beeping and blinking amber lights. 

We kinda can't go down right now, is there something i can do short of restarting? And, if i do restart, how long would it take to build the RAID drive ? It is a 35GB 15000 RPM with 8 2-core xeon 2.7 Ghz procs.

thanks for any advice.

---

### Post by ixus_123 on 2008-07-16
it probably is rebuilding.

This can take anywhere from an hour to over 4 hours.

look for a package called megamanager and install that (from LSI)

It works with the perc5 and will give you a virtual RAID BIOS.  You need to be root to run it

and the following keys will help you out

arrows - to move around
space - selects
enter - confirms / ends a selection
F10 - performs an action - eg configuress an array.

F2 give you info - for example, when looking at a physical disk, it will tell you the brand and of there are any predictive failures.

Ofcourse, another route would be to install Dell Openmanage and you can do all of this through a web interface.  I think the default port is 1311

---

### Post by nephish on 2008-07-16
Hey there, thanks for the reply. I pulled a drive from an older server ( our backup ) and put the drive in and it started rebuilding right away. this one is a 10k rpm drive like the others. The weird thing is when i put the 15 k rpm drive ( the problem one ) into the older computer, it started rebuilding and now works fine. Could the newer server be rejecting faster drives?

thanks for your attention on this by the way

---

