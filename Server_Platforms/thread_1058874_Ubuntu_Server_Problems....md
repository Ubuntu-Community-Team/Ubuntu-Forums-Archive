---
title: "Ubuntu Server Problems..."
date: 2009-02-03
forum: Server Platforms
---

### Post by joeladams on 2009-02-03
Hello all,

I have Ubuntu server installed on VMware server console and I'm having a problem with my server going down, my server is live to the web with my IP address, I port forwarded my ports to 80, problem is my IP address keeps going down I don't know why, it seems it cant find the server, it does stay live for about half-hour then it just randomly goes down, then after 5 to 20mins or so it comes back up, I have wireless internet and I don't really know why it goes down.

Is there anything I need to change in my router settings to make it stay up or is it just Ubuntu or VMware?

I've been searching around the internet for a similar problem but just couldn't find it. Hope you help,

Thanks.

---

### Post by bapoumba on 2009-02-03
Moved to Servers.

---

### Post by Poleh on 2009-02-03
when the server ip "goes down" can you log into the VM and check that it can communicate with the host machine, and also see if you can ping it from the host machine.

If you're running a VM, then unless you have power management configured on the host to shutdown/sleep then it should stay up. 

My advice would be to diagnose the problem internally first, i.e. ping to/from the VM when the problem is ocurring, and THEN diagnose externally. I doubt this problem is related to your router/wireless but it could be so if you can verify that it's working on the host then you know it's your router/wireless.

---

