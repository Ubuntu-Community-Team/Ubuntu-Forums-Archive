---
title: "NVidia module alias (nvidia_current_updates) problem"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-04-19
I have noticed a different behavior with nvidia and would like your opinion on this. I'm not sure if I should consider it as a bug.

After removing nvidia-current* and installing NVidia proprietary drivers via NVidia installer, I got stuck at console. I thought I had diverging kernel module / drivers version, but that was not the case. Went to look at xorg, compiz, etc as usual. No luck.

After some searching, I noticed the whole problem was in a wrong module alias: 
```
cat /etc/modprobe.d/nvidia*.conf
[...]
alias nvidia nvidia_current_updates
[...]

```
Of course, "modprobe nvidia" would default to a non-existing module (nvidia-current-updates). So, by just commenting this line and manually loading nvidia.ko things were fixed. 

When removing nvidia-current*, shouldn't that alias be commented out? I see no point in keeping an alias for a removed module.

Regards,
Effenberg

---

