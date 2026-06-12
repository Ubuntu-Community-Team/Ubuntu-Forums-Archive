---
title: "Info on configuring Web server, Webmail etc on Ubuntu server?"
date: 2008-07-23
forum: Server Platforms
---

### Post by TonyUb on 2008-07-23
Folks,

My Web site is currently hosted with an ISP and I'd like to move it to a box at home in the router's DMZ. I'd also like to configure a Webmail server (https?) so that both Webmail and the Web site are accessible over the Internet and while I'm about it why not a file server too.

Being a newbie this exercise is dangerous from a security point of view and likely to be complicated without the assistance of a preconfigured system.

There are preconfigured systems which assist this task greatly e.g. SME ([www.smeserver.org](www.smeserver.org)), ClarkConnect ([www.clarkconnect.com](www.clarkconnect.com)) but they're based on CentOS/Red Hat or Red hat respectively. Is there a similar thing based on Ubuntu server? Also, is there a set of guides somewhere that takes one from start to finish on configuring this lot step by step?

Regards,

Tony

---

### Post by mbeach on 2008-07-23
any specific reason you are going to put it in the DMZ and not forward just the ports on your router that are required?

---

### Post by songshu on 2008-07-23
i think the closest would be ebox, never used it myself, but it looks promising.

[http://ebox-platform.com/download/](http://ebox-platform.com/download/)

---

### Post by cariboo on 2008-07-23
Have a look at webmin too:

[http://www.webmin.com/](http://www.webmin.com/)

Jim

---

### Post by TonyUb on 2008-07-23
> **mbeach said:**
> any specific reason you are going to put it in the DMZ and not forward just the ports on your router that are required?

Well, if I do port forwarding on the router to the Web server should an attack to the Web server computer be successful then my other machines (desktop) on the LAN would be vulnerable wouldn't they? Is there an optimum way of doing this e.g. maybe port forwarding and use a second router between the desktop machines and the other router i.e. a second gateway?

---

### Post by cariboo on 2008-07-23
Have a look here for an Ubuntu server security howto:

[http://www.linuxsecurity.com/content/view/133913/171/](http://www.linuxsecurity.com/content/view/133913/171/)

Jim

---

