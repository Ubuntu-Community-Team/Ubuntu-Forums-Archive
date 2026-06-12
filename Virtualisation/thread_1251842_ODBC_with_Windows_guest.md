---
title: "ODBC with Windows guest?"
date: 2009-08-28
forum: Virtualisation
---

### Post by WitchCraft on 2009-08-28
Hi, question:

In my free time I have always been using Linux.

But at work I have to use Windows Vista.
Unfortunately, it's VistaX64, and with the latest security updates, the instability has now reached a point where it becomes virtually impossible to work.

(And it's already virus infested, although an anti-virus program runs (McAffee, I call it McMonkey) )


Now, in about two weeks from now I will be in the military for 3 weeks, so this is THE ideal time to reinstall.

Now, I've used virtualization before, but never in a critical situation: 

So, here my question:
If I install Linux on this computer, and then install Windows in a virtual machine on this computer (HP, 2GHz IntelCentrino 2 64Bit QuadCore, 4GB RAM), will an ODBC connection work in the virtualized Windows (without configuring them on Linux).


Also, which virtualization is the best?
I have always used VirtualBox, because it's simple, but probably a paravirtualized Xen Hypervisor is better.

Any ideas, experiences, or links thereto ?

---

### Post by WitchCraft on 2009-08-30
bump

---

### Post by Ghostbear121 on 2009-08-30
Sure, easy too.  Just bridge the network connection you have, so the virtual machine gets an IP address from your router, and not from virtualbox itself.  IE: under the Network settings for your virtual machine, Attached To: "Bridged Adapter"  instead of "NAT".

So then it's just a matter of connecting to that IP address.  You can assign a virtual machine a static IP too if you want.  (Use "Bridged adapter", and then after booting windows go into control panel and give the connection a static IP.)

I've used this method to code websites (on a mac) using dreamweaver which connects to an MS SQL database running on a virtual windows machine in the background.  Works fine.

---

### Post by WitchCraft on 2009-09-01
> **Ghostbear121 said:**
> 
I've used this method to code websites (on a mac) using dreamweaver which connects to an MS SQL database running on a virtual windows machine in the background.  Works fine.

Good. Bridging is clear, and the above is all I wanted to know.

Thank you!

---

