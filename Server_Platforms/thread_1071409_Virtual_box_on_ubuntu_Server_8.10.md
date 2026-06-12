---
title: "Virtual box on ubuntu Server 8.10"
date: 2009-02-16
forum: Server Platforms
---

### Post by thenetduck on 2009-02-16
Hello, 

I would like to install VirtualBox onto a server I am currently running so I can install other OS on that server without affecting my main machine. 

Would anyone be able to point to to a good guide that will show me how to install VirtualBox or VMware on a ubuntu server, then set up a guest OS? I am trying to install a Rails server. 

Thanks! 
The Net Duck

---

### Post by asel_ on 2009-02-16
> **thenetduck said:**
> Hello, 

I would like to install VirtualBox onto a server I am currently running so I can install other OS on that server without affecting my main machine. 

Would anyone be able to point to to a good guide that will show me how to install VirtualBox or VMware on a ubuntu server, then set up a guest OS? I am trying to install a Rails server. 

Thanks! 
The Net Duck


Hi, I think ,first , you should install x-windows and any gui (i.e gnome or kde).

---

### Post by sahabcse on 2009-02-16
Hi

Try to install SunXVM, It is good and easy to manage.

=======================================
[http://www.howtoforge.com/installing-virtualbox-2.0.0-on-ubuntu-8.04-desktop](http://www.howtoforge.com/installing-virtualbox-2.0.0-on-ubuntu-8.04-desktop)
======================================

Regards,
Sahab

---

### Post by kdcoetzee on 2009-02-16
So far i can understand, you can run virtualbox headless.

and then just rdesktop into the started life environment.

But never done it...

---

### Post by unixeducation on 2009-02-17
I use VMware Server 2 on Ubuntu Server 8.04, and it has proven to be a great solution to my development virtualization needs. I run five to ten VPS nodes at a time on a very lightly used single processor AMD64 machine will almost zero issues.

---

