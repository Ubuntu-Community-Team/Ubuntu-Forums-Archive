---
title: "Virtual Machine Linux as a Web Server?"
date: 2009-01-21
forum: Server Platforms
---

### Post by liquidfunk on 2009-01-21
I have a project to make a website for my University course, I'm wondering if it's possible to use some Linux distro in a VM as a web server?

 Anyone know how to do it?

---

### Post by ejschaefer on 2009-01-21
Hello, 

You can absolutely use any flavor of Linux within a VM. If your looking to do this as inexpensively as possible, you can get Vmware Server for free ([http://vmware.com/products/server/](http://vmware.com/products/server/)). It is available for both Windows and Linux host machines. VMWare server is pretty easy to use too, the interface is rather intuitive.  

This will give you a few different network options as well. You can configure "host only" networking, which will allow you configure your VM to serve web sites but they'll only be accessible by you from the host machine (ie. your laptop). You can also configure your VM with "bridged" networking. In this case the VM will essentially share the host machines NIC and will be accessible through that network and will show up as a completely separate machine on the network. 

For speed of deployment, you might want to check out the pre-built appliances here: [http://vmware.com/appliances/](http://vmware.com/appliances/)

There are a number of appliances available with various flavors of Linux and different "roles" (ie. Apache Web server).

Let me know if you have any other questions

Edward Schaefer
Support Supervisor
[http://www.hostmysite.com/?utm_source=bb](http://www.hostmysite.com/?utm_source=bb)

---

