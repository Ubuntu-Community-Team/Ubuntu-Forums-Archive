---
title: "startup stalls latest kernel update"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Robertjm on 2012-04-01
Anyone having issues with the 12.04 and the latest kernel update from a day or so ago? (*-20)

When I launch my computer it will sit on the blank purple screen after I choose the most recent kernel and I've waited for several minutes before finally rebooting the computer and using the *-18 kernel. 

Haven't tried failsafe mode yet to see if it's desktop related. But, figured I'd throw that out to see if anyone else has had issues.

Robert

---

### Post by josephmills on 2012-04-01
I have had no troubles with 3.2.0-20-generic
and booting. 
 
But I have had troubles with lightdm Dont know if this helps :) 
maybe look at dmesg in the terminal and look for error? 
Sorry that I can not be of more help.

---

### Post by cwhebert on 2012-04-01
> **Robertjm said:**
> Anyone having issues with the 12.04 and the latest kernel update from a day or so ago? (*-20)

When I launch my computer it will sit on the blank purple screen after I choose the most recent kernel and I've waited for several minutes before finally rebooting the computer and using the *-18 kernel. 

Haven't tried failsafe mode yet to see if it's desktop related. But, figured I'd throw that out to see if anyone else has had issues.

Robert

I'm having a similar problem, I think it is the video card driver not being loaded.  I did get my system to boot, however, when i checked for additional drivers I see that my video card driver Nvidea, is not loaded.  I then try to activate it and get referred to the log file to see the problem.  I hope someone comes up with a fix or work around.

---

### Post by Gregory Lee on 2012-04-01
> **Robertjm said:**
> Anyone having issues with the 12.04 and the latest kernel update from a day or so ago? (*-20)

Yes, assuming you mean *-21, the kernel version from Friday.  Since I installed that update, all my system shells crash all the time.  I started a thread "all shells crash" about that.

---

### Post by Doug S on 2012-04-01
As Gregory mentions, I am confused also, my most recent updates have me at:
 
Linux version 3.2.0-[COLOR=red]21[/COLOR]-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu3) ) [COLOR=red]#34[/COLOR]-Ubuntu SMP Fri Mar 30 04:25:35 UTC 2012
 
However, I am not having any issues, nor did I with 3.2.0.20 (I only use server versions).

---

### Post by drumour on 2012-04-01
Same purple screen problem with -21 on two ati systems, but it works okay on a dual screen nvidia setup. Gone back to -20 for the ati's in the meantime.

---

