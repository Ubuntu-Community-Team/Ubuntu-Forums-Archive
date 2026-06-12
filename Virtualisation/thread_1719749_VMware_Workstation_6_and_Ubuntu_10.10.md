---
title: "VMware Workstation 6 and Ubuntu 10.10"
date: 2011-04-02
forum: Virtualisation
---

### Post by UKBB on 2011-04-02
I'm trying to install Ubuntu 10.10 on a VMware Workstation 6 virtual machine. When I start the machine up I see a purple screen, but not the splash screen. This on is just solid purple with a couple of icons at the bottom center. One looks like a keyboard the other a star in a circle. After about 15 or 20 seconds the screen changes to a text screen scrolling line after line of code that is counting up on the left hand side. I let it run for about an hour last night and it never did anything different except to be counting up. 

Any help on this? The host machine is Windows 7.

---

### Post by vincent_kelly on 2011-04-03
> **UKBB said:**
> I'm trying to install Ubuntu 10.10 on a VMware Workstation 6 virtual machine. When I start the machine up I see a purple screen, but not the splash screen. This on is just solid purple with a couple of icons at the bottom center. One looks like a keyboard the other a star in a circle. After about 15 or 20 seconds the screen changes to a text screen scrolling line after line of code that is counting up on the left hand side. I let it run for about an hour last night and it never did anything different except to be counting up. 

Any help on this? The host machine is Windows 7.

"count up"? can you be more specific on this? It seems a problem with the vmware-tools, check out this link: [http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html)

Maybe you also want to install gnome
```
sudo apt-get install ubuntu-desktop
```

Let me know how it goes

---

### Post by UKBB on 2011-04-03
See the attached screen pics. As I said the numbers on the left just keep increasing.

---

### Post by UKBB on 2011-04-03
Here is the initial purple screen I see.

---

### Post by UKBB on 2011-04-05
Anybody?

---

### Post by UKBB on 2011-04-29
:-(

---

### Post by Kevkill on 2011-05-03
Workstation 6.x does not support either Windows 7 as a host or Ubuntu 10.10 as a guest. I would suggest you upgrade to Workstation 7.x as it supports both of these OS's.

The VMware compatibility guide can be found here:

[http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software](http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software)

-Kevkill

---

### Post by UKBB on 2011-06-06
Thanks Kevkill!

---

### Post by UKBB on 2011-06-10
> **Kevkill said:**
> Workstation 6.x does not support either Windows 7 as a host or Ubuntu 10.10 as a guest. I would suggest you upgrade to Workstation 7.x as it supports both of these OS's.

The VMware compatibility guide can be found here:

[http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software](http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software)

-Kevkill

I uninstalled Workstation 6 and installed VMWare Player (free!) and it is working fine now. Thanks again for the help.

---

