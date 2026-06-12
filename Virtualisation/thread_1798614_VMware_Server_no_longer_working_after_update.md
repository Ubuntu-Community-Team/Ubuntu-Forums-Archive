---
title: "VMware Server no longer working after update"
date: 2011-07-06
forum: Virtualisation
---

### Post by GOSSSAMER on 2011-07-06
I had a working VMware server 2.0 running on an Ubuntu 10.10 64-bit server 
(2.6.35-30-server).
 
after doing an "aptitude safe-upgrade" VMware server no longer works. 
 
I've searched everywhere online and have done countless suggestions and still no working VMware server. Ive tried re-installing using the same scripts I used prior however, they dont seem to work anymore. 
 
really need help getting VMware server 2 working again.
 
Any help will be greatly appreciated.

---

### Post by GOSSSAMER on 2011-07-07
:(

---

### Post by CharlesA on 2011-07-07
Was there a kernel update included with the update you did?

---

### Post by GOSSSAMER on 2011-07-07
> **CharlesA said:**
> Was there a kernel update included with the update you did?
 
I think so, from 2.6.35-28-server to 2.6.35-30-server.

---

### Post by CharlesA on 2011-07-08
> **GOSSSAMER said:**
> I think so, from 2.6.35-28-server to 2.6.35-30-server.
Can you check to see if the VMware kernel modules are loaded? I haven't really used it on a linux box, but if it's the same as Vbox, then you might have to compile the kernel modules.

---

### Post by HermanAB on 2011-07-08
Hmmm, when you run VMware (or any custom servers for that matter), you basically got to turn updates off and just re-install the whole kaboodle once a year or three.

I usually install my servers, lock them down and then leave them alone with zero updates till the hardware fails in 5 to 7 years.  Doing updates is just a form of 'job creation' and I got better things to do than that.

To get VMware working again, you got to re-install Vmware.  The VMware installer will recompile everything and then it will work again, if all the gods are smiling kindly upon you...

---

### Post by GOSSSAMER on 2011-07-08
> **HermanAB said:**
> Hmmm, when you run VMware (or any custom servers for that matter), you basically got to turn updates off and just re-install the whole kaboodle once a year or three.
 
I usually install my servers, lock them down and then leave them alone with zero updates till the hardware fails in 5 to 7 years. Doing updates is just a form of 'job creation' and I got better things to do than that.
 
To get VMware working again, you got to re-install Vmware. The VMware installer will recompile everything and then it will work again, if all the gods are smiling kindly upon you...
 
I completely agree with you on how the updates.  
 
How can I lock the server from getting updates?

---

### Post by CharlesA on 2011-07-08
> **GOSSSAMER said:**
> I completely agree with you on how the updates.  
 
How can I lock the server from getting updates?
Just don't allow automatic updates, if you have it:

installed:[https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html](https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html)

---

