---
title: "virtualization server"
date: 2009-02-05
forum: Server Platforms
---

### Post by eamgoo on 2009-02-05
I want to use Ubuntu to create a virtualization server, i have some experience with ubuntu but none with virtualization.
First the hardware description:
2 x IBM System X 3650 - with this configuration:
       2 x Intel Xeon Quad core
       8gb RAM
       2 x 500gb hard drive
1 x IBM System X 3550 - with this configuration:
       2 x Intel Xeon Quad core
       8gb RAM
       2 x 250gb hard drive
1 x Berkeley NetApp FAS 2020 Filer Storage

I need to rpovide the following services:
Active Directory (i dont know if this is possible with linux)
DNS-DHCP (linux or windows)
WEB-FTP (linux)
Database (linux)MySQL or Postgree
File Server now is windows 2003 r2 but with a single PC as server
Print Server (several usb printers, 3 x HP500 design jet ploters)

I will like to use virtualization because i want to install 2 AD servers one on each phisical server for redundance and security so maybe the guest os will be windows 2003 r2
Maybe XEN virtualization is a good idea

Please advise me
Thanks

---

