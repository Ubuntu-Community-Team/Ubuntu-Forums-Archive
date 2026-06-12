---
title: "VMware for Small Business Virtualisation thread"
date: 2011-09-01
forum: Virtualisation
---

### Post by Kalibur on 2011-09-01
Hello People

I recently experienced a disaster recovery situation and if it weren't for Virtual Machine Manager I would have failed miserably.  For more about the disaster see my blog at [sdkalibur.blogspot.com]("http://sdkalibur.blogspot.com").

Anyway after that experience am now thinking of virtualizing the business starting with the servers and eventually virtualize all the workstations as well.  I have been looking at Citrix Xenserver, XenDesktop and Xenclient but I would like to know what my options are, the easier to maintain the better and some graphical user interface tips.

Also the subject of OS and application licenses.  I know that most software requires that an application with a single license be loaded in the RAM of one machine at any given time.  But if I only need one image of windows 7 that multiple thin client can boot from at the same time, legally what is my position and what legal steps do I need to be on the legitimate side of licensing?

I would appreciate any input thank you.

---

### Post by rickyjones on 2011-09-01
> **Kalibur said:**
> Hello People

I recently experienced a disaster recovery situation and if it weren't for Virtual Machine Manager I would have failed miserably.  For more about the disaster see my blog at [sdkalibur.blogspot.com]("http://sdkalibur.blogspot.com").

Anyway after that experience am now thinking of virtualization the business starting with the servers and eventually virtualize all the workstations as well.  I have been looking at Citrix Xenserver, XenDesktop and Xenclient but I would like to know what my options are, the easier to maintain the better and some graphical user interface tips.

Also the subject of OS and application licenses.  I know that most software requires that an application with a single license be loaded in the RAM of one machine at any given time.  But if I only need one image of windows 7 that multiple thin client can boot from at the same time, legally what is my position and what legal steps to I need to be on the legitimate side of licensing?

I would appreciate any input thank you.

Virtualizing the servers and services is a great idea and one that I highly recommend. My employer makes heavy use of VMWare and Xen for the Windows and Unix/Linux environments. Great way to leverage hardware and simplify backups and disaster recovery.

For small business I would also call it a win. A company can spend the same amount on hardware and get the ability to safely virtualize most all of their necessary services, while keeping everything central for backup and recovery. That, and moving to new hardware becomes a breeze. The VMs will not care about the host OS, only that the VM Software is there.

In terms of desktop virtualization I would caution you to look into it, but don't push too heavily on it for small clients. A large organization can make some use of it. For example, we use desktop virtualization (VMWare View with thin clients) for a very specific type of user. Everyone else is provided a regular desktop or laptop. Most users will want their fat client. In addition, the server infrastructure that you would need to support full desktop virtualization is outside the budget of most small organizations. 

Hope this helps you!

Thanks,
Richard

---

### Post by Kalibur on 2011-09-01
> **rickyjones said:**
> Virtualizing the servers and services is a great idea and one that I highly recommend. My employer makes heavy use of VMWare and Xen for the Windows and Unix/Linux environments. Great way to leverage hardware and simplify backups and disaster recovery.

For small business I would also call it a win. A company can spend the same amount on hardware and get the ability to safely virtualize most all of their necessary services, while keeping everything central for backup and recovery. That, and moving to new hardware becomes a breeze. The VMs will not care about the host OS, only that the VM Software is there.

In terms of desktop virtualization I would caution you to look into it, but don't push too heavily on it for small clients. A large organization can make some use of it. For example, we use desktop virtualization (VMWare View with thin clients) for a very specific type of user. Everyone else is provided a regular desktop or laptop. Most users will want their fat client. In addition, the server infrastructure that you would need to support full desktop virtualization is outside the budget of most small organizations. 

Hope this helps you!

Thanks,
Richard

Thank you for you help Richard, yes I agree on the client side it is a bit sensitive I mean a small network problem could bring the render a work station unworkable so the fat client wins on that front, but from an admin and maintainence angle thin clients are a breeze.

---

### Post by rickyjones on 2011-09-01
You're welcome! I do agree that thin clients / desktop virtualization can be a breeze... until they stop working for some reason. It is nice being able to modify a single template and have those changes propagate the next time a user logs in.

Thanks,
Richard

---

