---
title: "Can't access server outside of intranet"
date: 2008-10-01
forum: Server Platforms
---

### Post by BlueScotch on 2008-10-01
Hello,

I recently installed apache, ssh, and ftp tools onto an ubuntu 8.04 desktop edition machine.  I have this computer behind a router, and have ports 20-22 and 80 forwarded to a static internal ip assigned to this particular computer.  

I have my external IP associated with a domain name through the DynDNS.org service.

This setup works fine when I am within the University Internet and am accessing the server from a machine that has a university IP address.  However, when I am outside of the university with a non-uni IP, I cannot access my machine through the web.  I assume that I cannot access it through ftp or ssh either, but since I do not have my own computer with that software I cannot attempt that.

At first I thought this issue was related to my setting in iptables.  I installed lokkit, and opened up the restrictions for http, ssh, and ftp, and it still does not work.  Is there any apache or ubuntu system setting that I am forgetting about that would cause this issue?

Thanks in advance for taking the time to read through my problem.

---

### Post by cariboo on 2008-10-02
Try [canyouseeme]("http://www.canyouseeme.org/") to see if your university is blocking ports 20-22 and port 80

Jim

---

### Post by windependence on 2008-10-02
If your university runs all of their students natted behind their router, you are going to have problems because they will have to forward the ports for you which as you know won't happen. What is the internal IP scheme you are using?

-Tim

---

