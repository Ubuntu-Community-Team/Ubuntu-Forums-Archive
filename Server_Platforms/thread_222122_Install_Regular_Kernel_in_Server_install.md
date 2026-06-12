---
title: "Install Regular Kernel in Server install?"
date: 2006-07-24
forum: Server Platforms
---

### Post by rot on 2006-07-24
Is it somehow possible to install a regular ubuntu kernel with the server package profile?

I am trying to install an ubuntu media center on an epia me6000 (i586 machine) and i want to install only the core packages by default so i deiced to switch to server. After install i get constant reboots after the kernel was unpacked.

The desktop install was no problem and worked fine. Everything was smooth till i decided to reinstall the whole thing with server to make it lean an nice.

Anyone got an idea if this is possible? Or any other explanation for my reboot phenomenon?

cheers
roman

---

### Post by rot on 2006-07-25
Or is it possible to do a live install of the server version? Maybe it does not work due to the regular installer?

---

### Post by lamego on 2006-07-25
I thinkg your best option is to use the Alternate CD and install using the "server" option.
This will give you a minimal installation just like the server install but using the desktop kernel version.

---

### Post by wifiabc on 2006-07-25
Isn't the kernel the same whether it is the desktop version or the server version??:confused:

---

### Post by lamego on 2006-07-25
wifiabc,
the kernel version itself is the same but not the options used to compile them, the server kernel has some options which are good for server services but not so good for desktop applications, also the server kernel has some specific hw options like suport for memory sizes >= 4GBs .

---

### Post by az on 2006-07-25
> **wifiabc said:**
> Isn't the kernel the same whether it is the desktop version or the server version??:confused:

No, there is a server-optimised kernel which only gets booted once installed.  It only runs on 686 pr better CPUS.  The installer uses the 386 kernel to run, which is why you can successfuly boot the installer cd.

You would need to chroot into your server before the install finishes and type

sudo apt-get install linux-386

You can also boot the installer cd, chroot into your server install and do that now.

You can always install using the alternate cd and then install the LAMP stack afterwards.  The server install from the alternate cd installs the linux-386 package.
 
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

---

