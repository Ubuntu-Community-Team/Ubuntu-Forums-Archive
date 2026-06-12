---
title: "Citrix xencenter console connection to xcp-xapi - no keyboard / keypress events"
date: 2012-07-21
forum: Virtualisation
---

### Post by gopher2x on 2012-07-21
while connecting to my xen server with citrix xencenter, everyhting works fine except when i open a console window. I can see the machine startup and everything looks good but keypresses are not registering on the VM..

everything i hit a key i get this in my xcp-xapi log

```
[20120721T17:17:20.330Z|debug|xen|509 INET 127.0.0.1:80|Connection to VM console R:73c96b23cdd8|console] Proxy exited
[20120721T17:17:20.484Z|debug|xen|675 INET 127.0.0.1:80|Connection to VM  console R:d4603aa93052|console] VM  OpaqueRef:29595b00-e209-bb8a-c093-cccfc3f57746 console port: Some 5901
[20120721T17:17:20.485Z|debug|xen|675 INET 127.0.0.1:80|Connection to VM  console R:d4603aa93052|console] Connected; running proxy (between fds:  26 and 27)
```Currently running XenCenter 6.0.2 on Windows XP, Xen 6.0, Xcp 1.3.2
Any Ideas?

---

### Post by gopher2x on 2012-08-01
anyone?
Have this issue only with HVM domu's, PVM work fine. No help from xen-users - hopefully someone can help me here???????

---

### Post by jcamel2k5 on 2012-08-10
Yes, I'm having this issue. I believe nearly everyone using XCP-XAPI is experiencing this issue.

Seems only XCP (the standalone build) works properly.

Thanks,

Joe

---

### Post by brainyron on 2012-08-13
I too am experiencing this issue.  Only workaround I've found is to modify the vncwrapper script to allow connections from other sources directly.

---

