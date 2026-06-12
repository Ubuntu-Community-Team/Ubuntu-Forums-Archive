---
title: "Should you eventually reboot after a Livepatch?"
date: 2019-05-21
forum: Security
---

### Post by mohamed-m-m-hafez on 2019-05-21
[COLOR=#242729][FONT=Arial]so lets say a livepatch comes in and my current running kernel gets patched, and I don't reboot the server because I don't need to any more. What happens if weeks/months/whatever down the line *another* livepatch comes in, and weeks later another, etc? Is this situation sustainable without rebooting *ever*?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The only way I could see that being the case is if each livepatch patches the running kernel to be exactly what it would be if you did the normal apt dist-upgrade to get the latest kernel and rebooted, but my impression was that livepatching only fixed high and critical security issues and left everything else untouched.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Or, do they just test each livepatch against a variation of older base kernels + varying numbers of previous livepatches made to them? If this were the case I'd guess there's a limit to how far back they would test, and that *eventually* you should reboot to make sure your base kernel is one that the livepatch was tested against?[/FONT][/COLOR]

---

### Post by deadflowr on 2019-05-21
Not all security updates can be applied via livepatch.
So there will be eventualities where you need to install an upgraded kernel and reboot.

[Signup for Ubuntu Security Notices]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce") and you'll get updates notices including those for live patching.
And in some cases the notice will also explain that you'll need to install a normal kernel update and reboot like this recent one
> Due to the high complexity of the fixes and the need for a corresponding
CPU microcode update for a complete fix, we are unable to livepatch these
CVEs. Please plan to reboot into an updated kernel as soon as possible.



> Or, do they just test each livepatch against a variation of older base kernels + varying numbers of previous livepatches made to them? If this were the case I'd guess there's a limit to how far back they would test, and that eventually you should reboot to make sure your base kernel is one that the livepatch was tested against?

The notices will also explain which kernel version can apply the livepatch.
They are limited, so not every kernel version in livepatch compatible.

(Unfortunately there is no easily attainable web page for the livepatch notices, but fortunaely the notices are bundled with Ubuntu normal security notices.)
Some more here:
[http://blog.dustinkirkland.com/2016/10/canonical-livepatch.html]("http://blog.dustinkirkland.com/2016/10/canonical-livepatch.html")

---

### Post by crip720 on 2019-05-21
Think that even if you don't need to reboot, a reboot once in a while does the system good.  This way you can do it when it is best for you.

---

### Post by mohamed-m-m-hafez on 2019-05-21
Ah thanks deadflowr, looking through the archives of ubuntu-security-announce, it looks like livepatches were provided for any kernel that came after a Livepatch Security Notice that required a reboot, in one case going back to kernels released over a year and half prior!

---

