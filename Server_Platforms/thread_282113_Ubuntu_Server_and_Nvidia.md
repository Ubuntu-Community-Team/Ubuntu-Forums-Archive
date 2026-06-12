---
title: "Ubuntu Server and Nvidia"
date: 2006-10-22
forum: Server Platforms
---

### Post by mg3kc on 2006-10-22
Hi,

I've just installed a LAMP server (and have the linux kernel 2.6.15-27-server installed), along with ubuntu-desktop. The purpose of my server is so that other slower computers can connect via NX or XDMCP and run from my quick computer. I have installed the graphical environment because I want to run a graphical interface, but I can't get the nvidia drivers to install (it forces me to install linux kernel 2.6.15-27-386). 

Any advice on what I should do would be greatly appreaciated.

Thanks.

---

### Post by divague on 2006-10-22
you could try downloading and installing manually the driver from the nvidia web page

---

### Post by az on 2006-10-22
> **mg3kc said:**
> Hi,

I've just installed a LAMP server (and have the linux kernel 2.6.15-27-server installed), along with ubuntu-desktop. The purpose of my server is so that other slower computers can connect via NX or XDMCP and run from my quick computer. I have installed the graphical environment because I want to run a graphical interface, but I can't get the nvidia drivers to install (it forces me to install linux kernel 2.6.15-27-386). 

Any advice on what I should do would be greatly appreaciated.

Thanks.

The server kernel is not a desktop kernel.  Much of the desktop hardware will not work.  

I highly doubt any sane sysadmin would want to run a proprietary, binary-only kernel driver on a production box.

After having installed the ubuntu-desktop package, the only difference between a regular desktop install and the route you took to install is that you have a different kernel.

Just install the linux-386 package.

The desktop kernel is less optimised for web servers, but I suppose that is not the kind of server you want to run anyway. You can run any application that you would run on a server kernel on the desktop kernel.  There is no problem.

---

