---
title: "query w.r.t OpenVswitch on ubuntu 12.10"
date: 2014-06-05
forum: Virtualisation
---

### Post by c-vijaya-durga on 2014-06-05
Hi All,

I am a bit lost here. I have posted the query on askubuntu and asking the same here.

[FONT=trebuchet ms][SIZE=2][COLOR=#333333]I have read that ubuntu 12.10 comes with a default openvswitch module  and I remember verifying the same. 
But at the same time, I also find lot of resources out there which install openvswitch on ubuntu 12.10..[/COLOR]
[COLOR=#333333]I am currently running 12.10 , and want to understand the appropriate way of getting openvswitch up and running, unfortunately the openvswitch official website is down and I am unable to extract any further information[/COLOR][/SIZE][/FONT]

---

### Post by TheFu on 2014-07-05
So, I'm a little late and don't have the answer you want. 12.10 is NOT supported anymore. No patches. That makes is a less-than-great idea to run it. Reference: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

14.04 or 12.04 are the best choices today. Both are LTS supported.

I used it on a 12.04 machine, but didn't find the extra effort worth the extra hassle or 5% performance gain over normal Linux bridges. It has been about 7 months, but I vaguely recall a number of kernel module dependencies that were not handled automatically.  Sorry I'm not anymore help.

---

