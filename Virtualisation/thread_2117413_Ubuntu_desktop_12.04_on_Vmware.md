---
title: "Ubuntu desktop 12.04 on Vmware"
date: 2013-02-18
forum: Virtualisation
---

### Post by madanforum on 2013-02-18
I have installed both server and desktop versions of Ubuntu on Vmware 7.1.2 build-301548 but I could not find the GUI of desktop version. Both server and desktop version boots up with LUI i.e: command prompt. How can I obtain the GUI of desktop version on my Vmware. 

I have attached screen shot of that problem.

---

### Post by wildmanne39 on 2013-02-18
*Thread moved to **Virtualisation**.*

---

### Post by MrKaliman on 2013-02-18
The printscreen is not uploaded successfully.
Can you retry uploading it?

---

### Post by madanforum on 2013-02-21
I have installed both server and desktop versions of Ubuntu on Vmware 7.1.2 build-301548 but I could not find the GUI of desktop version. Both server and desktop version boots up with LUI i.e: command prompt. How can I obtain the GUI of desktop version on my Vmware. 

I have attached screen shot of that problem.

---

### Post by Cheesemill on 2013-02-21
If it is Workstation v7.1.2 you are using then it doesn't support Ubuntu as a guest OS past version 9.10, as this was the most recent version available when Workstation 7.1.2 was released. This doesn't mean that later version *wont* work, just that VMware haven't tested them and not all of Workstations features will work properly.

The error you are getting usually happens when you try to use the easy install feature with an unsupported guest OS. Try doing a manual installation and see if that works.

You can see which guest OS's are supported by any particular VMware software using the compatibility guide on their site...
[http://partnerweb.vmware.com/comp_guide2/search.php?testConfig=16&deviceCategory=software](http://partnerweb.vmware.com/comp_guide2/search.php?testConfig=16&deviceCategory=software)

---

