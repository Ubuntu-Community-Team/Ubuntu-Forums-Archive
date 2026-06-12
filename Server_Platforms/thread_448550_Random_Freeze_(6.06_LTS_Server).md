---
title: "Random Freeze (6.06 LTS Server)"
date: 2007-05-19
forum: Server Platforms
---

### Post by bikkies on 2007-05-19
Hi, 

New here, I have a server in our datacentre running away happily.... or at least it was for about 6 months.

This morning it froze completely and i had to go to the datacentre and reset it... everything seems fine.  It was only running vmware and wouldn't have had any load at the time that it froze?

All the logs I can see just stop at about 7:45 when it froze.... there is no indication of what has caused the crash, and obviously, I'm now concerned that it could happen again.  

Please can anyone offer any advice as to things to look for that could cause such a crash.

Many thanks, 
Chris

---

### Post by craigp84 on 2007-05-19
> or at least it was for about 6 months.

What changed? Any new patches installed recently? Especially kernels and the like.

Do you have a serial console hooked up to it? If not, it'd be a  good idea to sort one out. Then if it does crash again, you've got a fighting chances of getting an ooops.

Might also be a good idea to enable MagicSysRq (echo 1 > /proc/sys/kernel/sysrq) then using the serial console to dump the current tasks (BREAK+t).

What about hardware? I run just over 1000 linux hosts @ work, with that number of boxes, we experience failures weekly. Oftentimes the crashes are traced to hardware issues, or in some cases they lay in the unresolved queue for a while, then at a later date a part fails (normally memory or disk).

Failing the above, there are potentially options like the netdump package which can sometimes allow an ooops to be sent over the network.

Hope this helps,

Craig

---

### Post by bikkies on 2007-05-21
haven't patched in several months, so definitely no software changes
i haven't a serial console hooked up, but will look at doing this.

thanks for your help.
chris

---

