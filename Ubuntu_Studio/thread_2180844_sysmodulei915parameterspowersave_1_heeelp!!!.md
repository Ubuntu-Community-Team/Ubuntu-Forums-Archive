---
title: "/sys/module/i915/parameters/powersave 1 heeelp!!!"
date: 2013-10-14
forum: Ubuntu Studio
---

### Post by tThEA3h on 2013-10-14
Hi y'all! 

So i'm one of those lucky bastards with a laptop and optimus..but this time my problems arnt related to optimus...it's this! : /sys/module/i915/parameters/powersave 1

How can i change that so it's disabled?? 

As you probably understood than yeah it's for an intel hd graphics card..i just really would like to disabled this option so my graphics card arent running in power save mode..kinda sucks to have like 30 ish fps on screen savers lol..not to mention compiz effekts ( or kwin).<<<<

[ATTACH=CONFIG]246957[/ATTACH]  <<Here is a little info that might help you.
 

If you need any other info or whatever please do not hesitate to ask :)

Cheers!

---

### Post by jejeman on 2013-10-15
I guess you could do

```
echo 0 > /sys/module/i915/parameters/powersave
```

if that works you can add the option in /etc/modules.

---

