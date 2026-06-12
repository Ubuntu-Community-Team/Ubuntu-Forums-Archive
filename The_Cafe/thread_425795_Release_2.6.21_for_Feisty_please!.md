---
title: "Release 2.6.21 for Feisty please!"
date: 2007-04-27
forum: The Cafe
---

### Post by Tim.R on 2007-04-27
Is there any chance that if enough of us ask, the Ubuntu developers will release kernel 2.6.21 for Feisty?  It's got some features I would really like, but compiling it myself leads to troubles with l-r-m and vmware.

Anyone else?

---

### Post by Polygon on 2007-04-28
the kernel gets updated a few times during the lifetime of the release, but usually it goes up one version number (aka 20 to 21) only once or twice, as that breaks a lot of stuff like 3d drivers... stuff that depends on the kernel version, etc

so i expect that eventually it will get upgraded to that

---

### Post by igknighted on 2007-04-28
It's really easy to do yourself, see this thread for details.

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by LookTJ on 2007-04-28
> **igknighted said:**
> It's really easy to do yourself, see this thread for details.

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)thanks for link :D

---

### Post by Hobbsee on 2007-04-28
> **Tim.R said:**
> Is there any chance that if enough of us ask, the Ubuntu developers will release kernel 2.6.21 for Feisty?  It's got some features I would really like, but compiling it myself leads to troubles with l-r-m and vmware.

Anyone else?

No.  Definetly wont happen.  

and the kernel wont be bumped to .21, by all the security updates - you may want to look a little more carefully at the numbering.

---

### Post by LookTJ on 2007-04-28
> **Taylor said:**
> thanks for link :D
it worked like a charm

only one con so far for me

had to copy the firmware crap.

---

### Post by igknighted on 2007-04-28
> **Taylor said:**
> it worked like a charm

only one con so far for me

had to copy the firmware crap.

True... when using a custom built kernel anything from the repos that comes with a kernel module (like most proprietary graphics and wifi drivers) need to be built manually as well.  Personally I think it is worth it, but keep it in mind when you decide to build a new kernel.

---

