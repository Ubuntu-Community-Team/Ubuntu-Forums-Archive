---
title: "Need help. Virtualization on ubuntu using virtualbox"
date: 2010-11-08
forum: Virtualisation
---

### Post by ubles on 2010-11-08
Hi! I'm need to install a Web server Apache and a DB server MySql and i want to try virtualization. I think install ubuntu desktop 10, then virtualbox, and then create VMs with ubuntu server to install Apache and MySql (or perhaps other apps/services). The server will be used for 20 web users (max). Is this a correct way to implement it?

I'm new and i'm just beginning to explore virtualization techniques.

Thanks

---

### Post by bluelamp999 on 2010-11-08
> **ubles said:**
> Hi! I'm need to install a Web server Apache and a DB server MySql and i want to try virtualization. I think install ubuntu desktop 10, then virtualbox, and then create VMs with ubuntu server to install Apache and MySql (or perhaps other apps/services). The server will be used for 20 web users (max). Is this a correct way to implement it?

I'm new and i'm just beginning to explore virtualization techniques.

Thanks

That's pretty much it!

I've done it before and it's very easy, there are a few good tutorials out there in Google-land...

One of the installation options for Ubuntu server is a full LAMP stack so all that stuff is automatically done for you.

I find VirtualBox excellent and the documentation is also very good - Let's just hope that Oracle don't kill it!

---

### Post by snowpine on 2010-11-08
Sounds like a good plan. You'll find a lot of good information here:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)


Good luck!

---

### Post by ubles on 2010-11-08
I've a lot of material and tutorials but my big question is whether to use ubuntu desktop as OS host to virtualize ubuntu server (and other applications) or not. Maybe some other solution is better or more appropriate (or not).

Thanks

---

### Post by ubles on 2010-11-08
Another question, Should i install the database server and web server in the same or two different VM?

---

### Post by snowpine on 2010-11-08
> **ubles said:**
> I've a lot of material and tutorials but my big question is whether to use ubuntu desktop as OS host to virtualize ubuntu server (and other applications) or not. Maybe some other solution is better or more appropriate (or not).

Thanks

Do you plan to use Ubuntu Desktop as your everyay operating system? If so, then the plan you describe is ideal in my opinion. You certainly can run all the server services you need from a Desktop install, but separating them into a virtual machine will insulate the server activities from the desktop activities. If the server crashes, your desktop work will not be interrupted, and you can easily reboot the virtual machine server without actually rebooting the physical machine.

If you don't use Ubuntu Desktop as your primary operating system then I'm not sure I understand why you would do this.

---

### Post by Dr. C on 2010-11-09
> **ubles said:**
> Another question, Should i install the database server and web server in the same or two different VM?

This can make sense if the VMs are on different hard drives. Installing VMs on different hard drives from each other and from the host OS is one way I have found to improve performance.

---

