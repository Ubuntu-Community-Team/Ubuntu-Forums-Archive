---
title: "Ubuntu Server Functionality"
date: 2010-06-04
forum: Server Platforms
---

### Post by simonw2008 on 2010-06-04
[SIZE=3]Newbie so sorry if very basic questions. [/SIZE]
 
[SIZE=3]I need a server for a small business. I don’t want to pay Bill Gates any more money and I worked with SVR5.4 about 15 years ago so I'm sure I can pick Ubuntu up, but before I dive into using and learning Ubuntu Server I just want to check it can do everything I need. [/SIZE]
 
[SIZE=3]The company has 4 Windows Vista Pro PC’s and 1 Windows 7 Pro laptop currently in a very simple Microsoft workgroup with one of the desktops acting as a file server. Its horrible because you have to have the same usernames and passwords on all the PC’s to get the file sharing working seamlessly. Also its impossible to easily control who can access what. Mail currently is handled by a third party.[/SIZE]
 
[SIZE=3]I want to install Ubuntu Server on a fairly powerful old desktop and use it for permission based file serving but I'm not sure is if Ubuntu Server can act as the domain controller and handle user accounts in the same way as a Windows Active Directory DC. Can Ubuntu act as the DC with Windows PC’s joining an Ubuntu domain and then handle file permissions based on the logged on users id and group membership?[/SIZE]
 
[SIZE=3]On the same single server I also will want to run DNS, DHCP etc. – and also if possible a mail server. Does the mail server which comes with Ubuntu work with MS Outlook?[/SIZE]
 
[SIZE=3]When I come to install Ubuntu there is an option for Enterprise Cloud – what’s that please.[/SIZE]
 
[SIZE=3]Sorry if drawn out and if I've posted this on the wrong forum but thanks if you can help me.[/SIZE]
 
[SIZE=3]Simon[/SIZE]

---

### Post by volkswagner on 2010-06-06
> **simonw2008 said:**
> [SIZE=3]Newbie so sorry if very basic questions. [/SIZE]
 

 
[SIZE=3]I want to install Ubuntu Server on a fairly powerful old desktop and use it for permission based file serving but I'm not sure is if Ubuntu Server can act as the domain controller and handle user accounts in the same way as a Windows Active Directory DC. Can Ubuntu act as the DC with Windows PC’s joining an Ubuntu domain and then handle file permissions based on the logged on users id and group membership?[/SIZE]

Samba as a PDC.  I have not done this, but you can easily try it out with a [prebuilt appliance]("http://www.turnkeylinux.org/domain-controller") from [TurnkeyLinux]("http://www.turnkeylinux.org/").  You will not get a linux replacement for ActiveDirectory.
 
> **simonw2008 said:**
> [SIZE=3]On the same single server I also will want to run DNS, DHCP etc. – and also if possible a mail server. Does the mail server which comes with Ubuntu work with MS Outlook?[/SIZE]

You should have no problem running those services.  You may consider using virtualization to breakup tasks on several VM's for administration purposes.  What specific features are you needing between mail and Outlook?  For ease of install and admin mail servers such as Zimbra and Citadel are great packaged systems.

---

### Post by HermanAB on 2010-06-06
Howdy,

I also suggest installing a virtualizer such as VMware Player or Virtualbox.  Then make multiple VMs, one per major service.  A business either grows or dies - it never stays static - hopefully, yours will grow.  So in 3 years you would want to migrate the system to new hardware and virtual machines will make that a snap.

---

