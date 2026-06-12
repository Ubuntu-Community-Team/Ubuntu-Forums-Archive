---
title: "Where do I find all sysctl variables?"
date: 2014-11-04
forum: Security
---

### Post by addison6 on 2014-11-04
Hello Ubuntu Forums,

When I use "sysctl -A" command I get a long list of system variables, around 776 lines. But when I edit my /etc/sysctl.conf there are only a few system variables there. I would like to ask you where is the place all system variables are stored and grab by sysctl -a command? As I see there are already 776 system variables, in case I would like to alter some of them I can use /etc/sysctl.conf (which is not including all these variables). 

It will be great if I find the file which has those 776 system variables with comments, explaining what every variable means, like in sysctl.conf.

Thank you.

---

### Post by Lars Noodén on 2014-11-04
The closest I could find was this:

[https://www.kernel.org/doc/Documentation/sysctl/](https://www.kernel.org/doc/Documentation/sysctl/)

It may not be complete or up to date. However, it will be the closest you can get, the [README](https://www.kernel.org/doc/Documentation/sysctl/README) file suggests that there is no complete list.

---

### Post by addison6 on 2014-11-04
I appreciate for your help. A good point for a start. It will be great if I find only one file with all system variables and comments. I will continue digging.

Do you know where all these variable are stored? As I read before, these variables are inside kernel, so if I want to get the all of them the best way is to save them in a file then insert in /etc/sysctl.conf (e.g. sysctl -A > /etc/sysctl.conf.all). sysctl.conf acts as a file which can alter the default system variables. If there are only 3 inside, those 3 will be changed permanently. Maybe I am wrong that why I asked for support to Ubuntu forums.

---

### Post by Lars Noodén on 2014-11-04
They're in the kernel itself, but overrides for individual variables would be stored in /etc/sysctl.conf or in a .conf file in /etc/sysctl.d/  So, yes, only the variables in those files will be changed, the ones that are not listed will be left with their default settings.  

One thing to remember is that there can be some variation between kernels, so be sure to pay attention to which kernel you are making the listing for.  Ubuntu 14.04 LTS uses 3.13.0  I think that if you make a comprehensive list, yours will be the first in a long while, perhaps the first period.  So if you do it, you could post it somewhere.  However, as the README file suggest, you will probably have to dig through a bit of kerenel source to complete the list.

---

### Post by addison6 on 2014-11-04
Now I understand from where these variables are coming from. The main reason I am looking for is to secure my system and make it better in performance. Tuning these variables could improve a lot the system stability, network connection, protect from DoS attacks.

---

