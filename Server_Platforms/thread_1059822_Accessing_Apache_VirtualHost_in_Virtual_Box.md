---
title: "Accessing Apache VirtualHost in Virtual Box"
date: 2009-02-04
forum: Server Platforms
---

### Post by supergrover1981 on 2009-02-04
Hi gang,

I'm doing some local dev work on a site that depends heavily on URLs ([www.xyz.com](www.xyz.com)) to direct to pages. In Ubuntu, I've got around this by redirecting [www.xyz.com](www.xyz.com) to my VirtualHost in /etc/hosts/, but I need to test in XP VirtualBox (IE 7) and it's proving a bit of a pain. So far I've got the front page working, but nothing else.

The attempt so far:

Within the XP VM, I've added "192.168.0.101 www.xyz.com" to c:/WINDOWS/system32/drivers/etc/hosts & in Ubuntu, I've added "192.168.0.101 www.xyz.com" to /etc/hosts/ ...This gives me access to the front page, but nothing else.

Server = Apache2, OS = 8.10, VirtualBox = 2.04 running XP SP3.

Any cape-wearing heroes able to help me out with this one? Any suggestions very appreciated.

Cheers,
       - JB

---

### Post by Masuran on 2009-02-04
So you access the frontpage but not other pages? Could you tell a bit more about the software / server setup? 

Normally you should have good access to the server once you can see the frontpage of your website.

---

### Post by supergrover1981 on 2009-02-05
Hi Masuran, thanks for the reply.

Sadly, impatience won out on this one - I redirected my sites-enabled default folder to that of the project, and everything went smoothly. Not an ideal solution, but we needed a v.quick turnaround.

I haven't looked too heavily into the code for the project, it's quite large. The error on none-homepages was a 404, but not the customised 404 error which should have come up.

Cheers,
       - JB

---

