---
title: "Windows 2003 Vmed on Ubuntu? or Ubuntu Vmed on Server 2003?"
date: 2007-06-29
forum: Server Platforms
---

### Post by thenetduck on 2007-06-29
Hi Guys,
   I am setting up a business with a server that will have VMware running on it. One VM will have either have Windows Server 2003 on it and Ubuntu running as the base install or Windows Server 2003 as the base install and Ubuntu as the VM Os. I needed some expert opinions on what would be the best to run as the base system. Is Ubuntu more stable and more secure than Windows 2003? 

One the windows server I will be remote login into it Via Windows Terminal Server to do my Point of Sale and accounting. On the Ubuntu side I will be having a LAMP server set up for my websites etc. Thank you I trust the opinions on this board thus why I am asking Thank you.

The Net Duck

---

### Post by gaten on 2007-06-29
I'd love to jump up and down and proclaim that Ubuntu is far supiror to W2k3 server in security and stability, but I can't. 2003 server is a VERY solid OS, and also very secure. 

I do believe however, that Ubuntu requires less maintenance (no defragging, no anti-virus or anti-spyware sweeps etc), and uses less resources. 

I know that 2003 can run well inside VMware Server under Ubuntu, but I havn't really done anything to intensive with it. I also know Ubuntu runs well inside VMware (although I've never tried your configuration with Windows as the host).

I would suggest a Linux host and Windows VM. And you might just want to think about Debian as the host. Ubuntu is great, but Debian has more concentration on security and has a history of server stability (I know I know, this is an Ubuntu forum).

---

### Post by thenetduck on 2007-06-30
It's interesting that you say that I should use a Debian Server (I will look into it) because I thought that Ubuntu was based on Debian so assumed it had basically everything Debian has. I decided to use the Linux as the base or host because I know I am going to have to restart windows every little while and don't wanna have my server down every  time I do that. What is the latest Debian release? Also how easy is Debian to install on a server? 

The Net Duck

---

### Post by rickyjones on 2007-06-30
Personally, for a small business, I would install Ubuntu and run VMWare on top of it. Where I work, a large global corporation, we have VMWare ESX hosting hundreds of Windows 2003 servers. ESX server is basically a custom built linux server if I recall correctly.

Set up the Ubuntu server correctly the first time and create VMs to hold everything else. It is probably the safest way to run and manage multiple servers. Be sure to make the physical box power/ethernet redundant as well if you have the ability to.

-Richard

---

### Post by gaten on 2007-06-30
> It's interesting that you say that I should use a Debian Server (I will look into it) because I thought that Ubuntu was based on Debian so assumed it had basically everything Debian has. I decided to use the Linux as the base or host because I know I am going to have to restart windows every little while and don't wanna have my server down every time I do that. What is the latest Debian release? Also how easy is Debian to install on a server? 

Ubuntu is based on Debian, but Debian is more proven in the server market. Of course, maybe you could help change that by using a Ubuntu server instead ;)

The latest debian release is 4.0 or Etch. The install is easy, but not quite as easy as Ubunut

---

