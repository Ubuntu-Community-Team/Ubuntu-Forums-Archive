---
title: "best flavor use to run many shell scripts"
date: 2016-10-17
forum: Ubuntu, Linux and OS Chat
---

### Post by sed_faster on 2016-10-17
hello folks,

Which flavors of the linux do you advice to you use as system headless to run many scripts in shell scripts?

Normally I use ubuntu server, because my knowledge is more embracing on this distro, but I want learn about another distro!
thanks

---

### Post by SeijiSensei on 2016-10-17
If you want to try another distribution, then I'd suggest [CentOS]("http://www.centos.org"), a free clone of RedHat Enterprise Linux.  

There is no distribution that is innately better at running shell scripts than any other.  I do recommend using bash as the shell, though.  Ubuntu defaults to a more limited shell called dash when using the "sh" command though bash is also available.  I prefix all my scripts with 
```
#!/bin/bash
```
to ensure bash is used.

---

### Post by Habitual on 2016-10-17
Short list: 
Ubuntu LTS and CentOS

---

### Post by sed_faster on 2016-10-17
Ok, I will choose ubuntu server!
Exist some which I can do to orientate the power of the cpu and ram to direct to the my script? Or it is enough execute the script and system management resources!?

---

### Post by kevdog on 2016-10-17
@SeijiSensei -- Perhaps you could open another thread to talk about CentOs -- specifically your experiences.  I'm interested in hearing about it.

---

### Post by deadflowr on 2016-10-17
Not Ubuntu support, so
*Thread Moved to **Ubuntu, Linux and OS Chat***

---

### Post by sed_faster on 2016-10-18
@deadflowr
Why you don't support Ubuntu?

---

### Post by lisati on 2016-10-18
> **Edgar_Oliveira said:**
> @deadflowr
Why you don't support Ubuntu?

You weren't asking about Ubuntu. In your own words:
> Normally I use ubuntu server, because my knowledge is more embracing on this distro, [COLOR="#FF0000"]but I want learn about another distro![/COLOR]

---

