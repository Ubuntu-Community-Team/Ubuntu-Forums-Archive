---
title: "virtualize ubuntu on  a win 7 host using vmware!"
date: 2012-02-05
forum: Virtualisation
---

### Post by soshiant on 2012-02-05
Hey guys!

I installed WMware workstation on a win 7 host and then tried to run ubuntu as guest ! the first time everything goes well , but when I shut it down with "sudo shutdown now" , I can't come back becase I see a black page with a dash flushing.....any ideas ????:confused:

---

### Post by uRock on 2012-02-05
Hello and welcome to the forums,

Moved to *"Virtualization"*.

---

### Post by soshiant on 2012-02-06
Thanks urock!!!

---

### Post by drmrgd on 2012-02-06
I'm running Kubuntu with VMware Player on my Windows 7 work computer.  Usually it seems that CLI reboot and / or shutdowns seem to be OK, although I have seen the system hang once or twice and I've had to click the VMware Player Power Off button.  I'm guessing, however, you're talking about when you try to restart the system, and I've not seen any problems like that in my environment.  My only suggestion is to make sure you've installed the VMware Tools, and they do interact with the kernel.  In fact, each time you update the system, you should run the script just to be sure that everything is working well together.

---

### Post by soshiant on 2012-02-06
> **drmrgd said:**
> I'm running Kubuntu with VMware Player on my Windows 7 work computer.  Usually it seems that CLI reboot and / or shutdowns seem to be OK, although I have seen the system hang once or twice and I've had to click the VMware Player Power Off button.  I'm guessing, however, you're talking about when you try to restart the system, and I've not seen any problems like that in my environment.  My only suggestion is to make sure you've installed the VMware Tools, and they do interact with the kernel.  In fact, each time you update the system, you should run the script just to be sure that everything is working well together.


Thanks my friend 

I'll try to give you more information about the issue and then I'll ask some questions 

as I said ,Windows 7 as host and Ubuntu server as guest (with no desktop installed) , I can use ubuntu server just once and when I power off and try to run the machine again I see these pics below :
[http://www.4shared.com/photo/0Pjh7av-/1_online.html](http://www.4shared.com/photo/0Pjh7av-/1_online.html)
[IMG]http://www.4shared.com/photo/0Pjh7av-/1_online.html[/IMG]

and then:
[IMG]http://www.4shared.com/photo/Nw509FWU/2_online.html[/IMG]
[http://www.4shared.com/photo/Nw509FWU/2_online.html](http://www.4shared.com/photo/Nw509FWU/2_online.html)
[IMG]http://www.4shared.com/photo/Nw509FWU/2_online.html[/IMG]


and the questions :
1-what is CLI ?
2-how should I know if the VMware is interacting with the kernel ? what are the scripts?

---

