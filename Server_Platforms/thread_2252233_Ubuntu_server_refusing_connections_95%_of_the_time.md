---
title: "Ubuntu server refusing connections 95% of the time"
date: 2014-11-10
forum: Server Platforms
---

### Post by liste on 2014-11-10
Hello,

I have a server running Ubuntu 14.04, and have installed all the latest updates available.  It is running as a guest inside of VirtualBox on a CentOS 6.5 server.  The network adapter is Bridged Adapter named eth0 with Promiscuous Mode set to Deny and obviously the cable is connected.

On my router I have port 80 forwarding to the virtual machine's IP.  I have double-checked the Ubuntu server VM's IP, and it is the same one that the router is forwarding to.

I'm getting the following error when trying to access my website in Chrome 95% of the time: Failed to load resource: net::ERR_CONNECTION_REFUSED 

However, on a rare occasion it will just randomly work and I'll see the website I'm connecting to.  The setup was working fine before the weekend and that I have never had these issues with it.

If I change my hosts file on my computer to point the domain to the VM on the CentOS server, it works 100% of the time.

What could be causing this problem?  As I mentioned, it has been working up until now.

Thanks!

---

### Post by nerdtron on 2014-11-10
> On my router I have port 80 forwarding to the virtual machine's IP.  I have double-checked the Ubuntu server VM's IP, and it is the same one that the router is forwarding to.

I'm getting the following error when trying to access my website in Chrome 95% of the time: Failed to load resource: net::ERR_CONNECTION_REFUSED 

Where are testing this? from the same LAN? or outside on the public internet?


> If I change my hosts file on my computer to point the domain to the VM on the CentOS server, it works 100% of the time.


What do you put in the hosts file? The private internal IP of the VM or the Public IP of the router with port forward?

---

### Post by liste on 2014-11-10
> **nerdtron said:**
> Where are testing this? from the same LAN? or outside on the public internet?

I'm testing this from the same LAN, but I've also tried to access it from a proxy with the same results (website not available).

> **nerdtron said:**
> What do you put in the hosts file? The private internal IP of the VM or the Public IP of the router with port forward?

I pointed the hosts file to the internal IP of the VM.

For now, I have enabled the firewal (sudo ufw enable) and opened port 80 and everything seems to be working again all of the time*, but I'm not convinced yet.  I did not realise that Ubuntu server does not enable the firewall by default!

***EDIT:** it is not working after all.  I'm still having the same problem.  Sometimes I can access the site, sometimes I can't.

---

### Post by liste on 2014-11-10
Just a quick update: I've installed [FONT=arial]nmap and sometimes it is declaring port 80 to be opened and other times not.  What would cause that?[/FONT]

---

### Post by houstonbofh on 2014-11-10
Are you sure nothing is causing filtering problems in Centos?

Where I would start is setting up continuous loops of netcat on the Ubuntu server, the centos server and the desktop to port 80 of the ubuntu server and see for sure where the break is.

---

### Post by nerdtron on 2014-11-11
Look at the ufw logs. I think firewall settings of Ubuntu has a rate-limit by default.

---

