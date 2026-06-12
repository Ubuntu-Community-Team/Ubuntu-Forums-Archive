---
title: "Disable shuthdown/restart/hibernate/standby on a server"
date: 2009-08-20
forum: Server Platforms
---

### Post by DonBusi on 2009-08-20
Hi all,  

I have a Ubuntu 9.04 Server at home (in the living-room) running some services, that I want to be available 24x7 (Web server, VDR...). 

So I never want to shutdown or hibernate that machine and I don't want anyone to be able to accidently shut the server down by clicking the wrong buttons.  

My question is: How do I limit all shutdown/hibernate/reboot/standby functionalities so that you have to enter the password (sudo) to initiate a shutdown/restart/hibernate/standby in any way? 

I know that a dumb user could still just pull the power-plug to turn off the machine, but that's most probably not going to happen. He/She'll remember that she/he is not supposed to turn that computer off before trying that.  

Thanx for your help, 
Don

---

### Post by tubezninja on 2009-08-20
By default, hibernate/standby is disabled on the server edition, and an administrator password (via sudo) is required for a shutdown.  As long as you don't have a GUI or window manager running, it should be already set up to stay on unless a user with root privileges issues commands to power down or reboot.

---

### Post by DonBusi on 2009-08-31
Hi [scaredpoet]("http://ubuntuforums.org/member.php?u=502724"),

(sorry for the long reply-time...holidays...:))

thanx for the tipp. unfortunately I didn't install the server edition and rather not do a full re-install of my system.

do you know how the behaviour  is accomplished in the server-edition? can I do this without re-installing my whole system?

Cheers,
Don

---

