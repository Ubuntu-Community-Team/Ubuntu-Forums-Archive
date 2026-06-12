---
title: "[SOLVED] shared folder problem for windows guest"
date: 2008-12-01
forum: Virtualisation
---

### Post by luckydeveloper on 2008-12-01
hi,


i have Intrepid Ibex in my PC. I have just set up a Virtualbox virtual machine for windows XP. i want it to share a folder with ubuntu. but in the settings, when i clicked the shared folders icon, the following error comes. 


```
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}
```

what should i do. the same error comes with my pen drive as well.

please help

---

### Post by Dedoimedo on 2008-12-02
Are you using the ose version of virtualbox?
Dedoimedo

---

### Post by luckydeveloper on 2008-12-02
nope. i am using the standard edition... i desperately want to share some folders with ubuntu host...

please help

---

### Post by Dedoimedo on 2008-12-03
Did you install guest addons?
Without them, you won't be able to share folders.
Dedoimedo

---

### Post by luckydeveloper on 2008-12-03
yep, the problem is solved...

---

