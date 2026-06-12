---
title: "WordPress Installation without root"
date: 2017-03-14
forum: Server Platforms
---

### Post by acpguedes on 2017-03-14
Hi,

I'm trying to install wordpress on a server without root privileges. 

So, first I use `apt-get source [package]` to download each of this sources: nginx, mysql-server, php5-mysql and php5-fps.
After I try to compile setting `prefix` to my home to each package.
[PHP]
./configure --prefix=$HOME
make 
make install
[/PHP]
But, when I run make the compiler return this message:

[PHP]
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/home/CEFAP/acpguedes/sources_wordpress/nginx-1.4.6'
make: warning:  Clock skew detected.  Your build may be incomplete.
[/PHP]

All, package return this message.

Does anyone know how to solve this problem?

Thanks,

Obs: I don't want to use to external access, I know that I'll need to use other port.

---

### Post by QIII on 2017-03-14
Moved to Server Platforms for a better fit.

Installation & Upgrades is for questions about installing and upgrading the OS, not software packages.

Cheers!

---

### Post by SeijiSensei on 2017-03-14
> **acpguedes said:**
> I'm trying to install wordpress on a server without root privileges. 
That's going to be exceeding difficult as you have discovered.  Do you not have a server on which you can have root privileges?  

Compilation alone isn't enough.  You'll need to have root access to configure the servers as well.  HTTP servers in particular require root access since they bind to port 80.  Ports below 1024 are reserved for the root user and cannot be opened by ordinary users.

If you can't have root on this server, can you install a virtualization platform on the machine like VirtualBox, VMware, or KVM?  Then you could create a virtual machine into which you can install Ubuntu and have root privileges.

---

### Post by LHammonds on 2017-03-16
If the machine doesn't already have a web server (apache or ngnix) and database (mysql or mariadb), then you would be hard-pressed getting those installed without root rights in the OS.

However, if the server already has them and you have rights to create databases and place files on the web folders, you should be able to extract an instance of wordpress PHP files on the web server, and then create an empty wordpress database and configure wordpress to point to that database.

LHammonds

---

### Post by mastablasta on 2017-03-17
what the want is kind of like XAMPP is on windows. you just upack it and excecute. works well for local use (not connected to internet). while ther eis XAMPP for linux the install is a bi tmore tricky if you want to do it without root. 

but anyway. investigate XAMPP for linux to see if there is a way to have it installed without the root privileges for local use (by local i mean it would be beneficial only if sevrer has the desktop available).

---

