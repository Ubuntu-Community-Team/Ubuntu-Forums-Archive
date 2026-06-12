---
title: "vmware 6.5 's virtual network problem on ubuntu 8.04"
date: 2008-11-16
forum: Virtualisation
---

### Post by helai on 2008-11-16
I installed vm6.5 build 118166 on my ubuntu8.04,and it runs well except can't connect to the network,and when it starts ,it shows me "could not found /dev/vmnet0" ,it are using bridge method .also I can't find the corresponding modules running at the background of the OS,

even I can't open the virtual network editor from the Applications> system tools>

so who has ideas to let VM to connect the network?

thanks in advance!

Helai

---

### Post by panlm on 2008-11-23
i have the same problem 

and when i run vmware-modconfig

is said:
Logging to /tmp/vmware-panlm/setup-10398.log
Icon name must be set.


who can help us

---

### Post by darco on 2008-11-24
I had a similar problem w/6.5. First in VMWare,go to Edit/Virtual Network Preferences, make sure that vmnet0 is pointed to eth0. You can leave at auto or point it manually to eth0. If that does not work, try nat mode as it works for me vmnet8. 
good luck

darco

---

