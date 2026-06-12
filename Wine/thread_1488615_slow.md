---
title: "slow"
date: 2010-05-20
forum: Wine
---

### Post by vigge_sWe on 2010-05-20
my wine is really slow and I don't know why. But it's only slow on the startups of programs. Even winecfg takes 5 minutes to launch.

I don't think it's my computer as it has 4GB RAM and dual-core CPU. It's a lenovo T61p.

Any ideas if it is possible to make it run faster?

---

### Post by cogadh on 2010-05-20
The fact that the slowness is also affecting winecfg points to a possible  problem with your .wine directory or your configuration, but without a lot more information, we can't even begin to make any meaningful suggestions. What version of Wine are you running? Have you made any special config changes to Wine, like library overrides? What have you installed in Wine? We need info like that just to understand the environment the problem is occurring in and without it, we'd just be throwing out random guesses.

---

### Post by vigge_sWe on 2010-05-21
> **cogadh said:**
> The fact that the slowness is also affecting winecfg points to a possible  problem with your .wine directory or your configuration, but without a lot more information, we can't even begin to make any meaningful suggestions. What version of Wine are you running? Have you made any special config changes to Wine, like library overrides? What have you installed in Wine? We need info like that just to understand the environment the problem is occurring in and without it, we'd just be throwing out random guesses.

wine-1.1.42

I override some things to try to get office 2007 to work:
[ATTACH]157737[/ATTACH]

also I installed dcom98 or something in winetricks to get office to work but it was a failure

---

### Post by cogadh on 2010-05-21
That rpcrt4 override is the first place I'd start. That particular DLL is linked to so many other critical DLLs, like ntdll and kernel32, that if something was going to slow down everything else, it would be my first suspect (second would be gdiplus). Try setting that DLL back to built-in or removing the override entirely then try running something (other than Office) in Wine to see if the speed has improved. If it does, then you may want to look into setting up an application profile for Office and only adding the offending override to that profile; that way, while Office may be slow to launch, the problem won't affect anything else in Wine.

---

### Post by darklegion on 2010-05-22
Try moving ~/.wine to ~/.wine.bak and then running the program again.

---

