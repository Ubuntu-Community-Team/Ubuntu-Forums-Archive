---
title: "OpenVPN Server GUI Interface"
date: 2010-05-04
forum: Server Platforms
---

### Post by suryaubunteroz on 2010-05-04
hello,

my name is Surya Handika Putratama. this is my first post on ubuntu forums.:popcorn:

i am looking for OpenVPN Server Gui interface. I am now developing an OpenVPN Server and I need a GUI Interface, especially for managing OpenVPN certificates, bandwidth, connect/disconnect users, etc. Do you know WinBox for MikroTik? I hope someone know a software similar to WinBox, but to manage OpenVPN server.

Thank you.:D

---

### Post by spynappels on 2010-05-04
If you are running an OpenVPN server on Ubuntu Server Edition, you configure it using conf files, there is no GUI. There is a GUI for OpenVPN on Windows, but AFAIK it does not have the functionality you are looking for.

The WinBox you mention only works with RouterOS and gives the same sort of functionality as that given by most routers as webpages. I don't think the same is available for OpenVPN

---

### Post by doogy2004 on 2010-05-06
> **suryaubunteroz said:**
> hello,

my name is Surya Handika Putratama. this is my first post on ubuntu forums.:popcorn:

i am looking for OpenVPN Server Gui interface. I am now developing an OpenVPN Server and I need a GUI Interface, especially for managing OpenVPN certificates, bandwidth, connect/disconnect users, etc. Do you know WinBox for MikroTik? I hope someone know a software similar to WinBox, but to manage OpenVPN server.

Thank you.:D

Check out OpenVPN-AS - [http://openvpn.net/index.php/access-server/download-openvpn-as.html](http://openvpn.net/index.php/access-server/download-openvpn-as.html)

OpenVPN-AS does have a web GUI and is easy to setup and deploy.

---

### Post by lonetree on 2010-05-14
> **spynappels said:**
> If you are running an OpenVPN server on Ubuntu Server Edition, you configure it using conf files, there is no GUI. There is a GUI for OpenVPN on Windows, but AFAIK it does not have the functionality you are looking for.

The WinBox you mention only works with RouterOS and gives the same sort of functionality as that given by most routers as webpages. I don't think the same is available for OpenVPN

Although this is not a discussion on Windows, I found this tools which I tried to administrate the openvpn server on windows, but I wasn't able to get it through, and have no much interest to study into it.You might want to have a look.

[http://www.mertech.com.au/mertech-products-openvpnusermanager.aspx](http://www.mertech.com.au/mertech-products-openvpnusermanager.aspx)

---

### Post by lonetree on 2010-05-14
> **suryaubunteroz said:**
> hello,

my name is Surya Handika Putratama. this is my first post on ubuntu forums.:popcorn:

i am looking for OpenVPN Server Gui interface. I am now developing an OpenVPN Server and I need a GUI Interface, especially for managing OpenVPN certificates, bandwidth, connect/disconnect users, etc. Do you know WinBox for MikroTik? I hope someone know a software similar to WinBox, but to manage OpenVPN server.

Thank you.:D

Hi Suryaubunteroz,

you may want to refer to this article, which I have previously used to configure for my client. You may also want to install webmin and openvpn module to administrate your openvpn server. You have to co-reference to the article from Baker. Hope it helps.

Alternatively, in ubuntu 10.04, there is this package call ebox, which can do many administrative task to your server. I have not personally use it, so I can't say it will work.

Good luck. Post your story to share with the community if you success.

Regards,

---

