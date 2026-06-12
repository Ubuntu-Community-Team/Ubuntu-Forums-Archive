---
title: "how do web hosting companies run their business"
date: 2010-08-15
forum: Server Platforms
---

### Post by jamesbon on 2010-08-15
I always used to wonder how do web hosting companies host their websites.
My problem is I saw some one having their website.I have a degree in Computer Science.
I am not clear as how do these web hosting companies give the logins to their users as root.
Meaning how can a hosting provider provide root login to say 1000 users and each having a different IP address.

---

### Post by mdlueck on 2010-08-15
If said provider is able to provide clients with root access, then either the client's environment is a VPS (Virtual Private Server) or a truly dedicated server which comes with full root access.

---

### Post by jflaker on 2010-08-15
most web servers use apache and use virtual hosting or otherwise known as SHARED HOSTING.  That is, many websites run off of the same computer or cluster of computers (server farm with load balancing).  

The other consumer option is DEDICATED hosting in which there could be server farm with many virtual computers.  For dedicated hosting, you are purchasing the use of ONE virtual computer host to run your website.

A third option is co-location, where you place YOUR server in their rack on their power solution and network backbone.....YOU are completely responsible for that server's health and uptime as it is YOUR hardware.

---

### Post by jamesbon on 2010-08-17
So what is the difference between Virtual Private Server and Shared hosting?

---

### Post by mdlueck on 2010-08-17
> **jamesbon said:**
> So what is the difference between Virtual Private Server and Shared hosting?

Shared Web Hosting gives you a heavilly restricted account which you may upload files to in order to put a web site together. The provider gives you a VirtualSite within their Apache configuration, etc... No perms to install packages to the entire system. If you are able to compile code, then you must do so using --prefix and specify the bin directory to be somewhere within your home directory.

Virtual Private Server means the provider has some sort of virtual machine environment, they are responsible for keeping it working and you have full responsibility to the OS running in the virtual environment. Here you end up with full root perms.

---

