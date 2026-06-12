---
title: "Real life Ubuntu server experience"
date: 2007-09-08
forum: Server Platforms
---

### Post by mistrial on 2007-09-08
I have started working for a mid-size company that does not have much experience with Linux, which I think is a a shame. I really want to do something about it and I am about to setup a general server with which I hope to impress and convince them. 

I have some Fedora server experience, but would like to try Ubuntu server since I have been so impressed with the Ubuntu desktop edition. I am interested in hearing others opinions and experiences with Ubuntu servers. How does it compare with other Linux distro servers e.g Fedora? 

Thank you all for your input. Have a nice weekend!:)

---

### Post by arkopII on 2007-09-10
Hello, 

I have been working with ubuntu servers for about two years, for me Ubuntu is a very good OS for servers as it is very easy to install services and there's plenty of documentation about it.

I have heard about other distributions like Gentoo and I also work with Fedora, but those need much more knowledge and experience.

I have about 9 servers with ubuntu and my next step is virtualization :-)

Well, If you want to impress without having to dedicate lots of hours of system administration is a good choice.

Regards

---

### Post by p_quarles on 2007-09-10
Ubuntu and Fedora are distros that are focused on desktop usage. They both work adequately as servers, but you might also want to try more server-focused distros (Debian, CentOS).

---

### Post by thavid on 2007-09-11
I work for a company that is changing to Linux (Ubuntu was the chosen one). Besides the workstations (some with Dapper, others with Feasty), we are also migrating the servers (wich include MS Exchange, Active Directory, VPN, File Server). Here is a list of some services migrated to Ubuntu as a server platform, that run with no problems:

- Terminal Server
We had a Win2003 Terminal Server for all the low ressource workstations... Now the are working in a PXE Dapper Server, where they can do all their tasks (Mail, Web, OpenOffice, IBM iSeries Access) faster than in Windows, and the good thing is that now they boot from the network!!!

- Update Server
Formely known as WSUS (Windows Software Update Server), know it's a simple mirror (thanks to apt-mirror) of /dapper and /feisty and it runs on a PIII@800mhz with 512MB of RAM... Imagine WSUS running on that....

- VPN
Cisco PIX + Windows Server Pix management software... Now a dapepr server (low ressource machine) acting as IPSec (OpenVPN) Server... Works better, allows the clients to be connected to the VPN and surfing the web.

Except for the Terminal Server (Dapper "normal" 6.06.1), all other systems are using Dapper Server 6.06.1

---

### Post by Brazen on 2007-09-11
> **p_quarles said:**
> Ubuntu and Fedora are distros that are focused on desktop usage. They both work adequately as servers, but you might also want to try more server-focused distros (Debian, CentOS).

Ubuntu is ok to use as a server distro, just be sure to stick with the LTS releases of the server version.  The latest non-LTS release should only be used for testing or if there is a software update that is an absolute requirement.  But for production use, you'll want to stick with the LTS releases if at all possible.

Other than that I would say Ubuntu is definately my favorite server distro.  However, I put Redhat on all my servers at work because we have several software apps that only support RedHat (I was actually able to get them to run on Ubuntu, just for testing, but it would not be covered under our support contracts).

At home though, I use Ubuntu.  Not to say that Ubuntu is more suited to home use than enterprise use.  For my work it was just an issue of third-party compatibility and that is only because RedHat has been around longer and has better third-party support penetration.  Ubuntu is catching up on this though (I wouldn't be surprised if 3 years from now anyone who supports RedHat also supports Ubuntu).

So just what are you planning to "wow" them with?  A web server? database server? file server?  I was first able to "wow" management by using Apache to consolidate and tie together a few different sites and servers using virtual hosts and reverse proxying.  I then "wow" them even more by replacing our Windows 2000 file server with Samba and using shadow_vol to retrieve files rather than having to restore from backup tape.

---

### Post by Parama on 2007-09-11
We are currently running 5 Ubuntu servers at our colocation and 2 at the office (all Feisty). 
The best thing about the Ubuntu servers compared to the CentOS and Trustix Linux servers we used to have is that Ubuntu is so versatile yet stable and fast. 
Our servers run a variety of server applications such as the usual MySQL databases and Courier mail server but also Apache with PHP+PECL that executes stored procedures(!) on MS SQL servers(!) getting binary data as result(!). The latter was not the least possible on CentOS and Trustix but in Ubuntu it just works :)
The servers have been running for about one and a half year now with no other downtime than the planned service windows.
So, to my experience as a sys admin with half and half of Windows and Linux servers, Ubuntu is a winning ticket when it comes to server O/S (as well). 
And my boss who is a classic/regular Windows loves to tell customers and business partners about how good the Ubuntu servers perform and behave. And the same goes for my otherwise skeptical collegues.

---

### Post by mistrial on 2007-09-15
Thank you all for sharing your experience with Ubuntu servers and for asuring me about my choice. Also thank you for giving me new ideas!

I am looking forward to impressing my colleagues!!  :)

---

### Post by maddog39 on 2007-09-15
I think Ubuntu makes a brilliant server. It does most of the configuration work for you and has good skeleton configuration files. I think its far easier than Fedora and definately easier than CentOS. I've had nightmares setting up CentOS servers.

---

### Post by SteveHillier on 2007-10-04
> **Brazen said:**
> 

So just what are you planning to "wow" them with?  A web server? database server? file server?  I was first able to "wow" management by using Apache to consolidate and tie together a few different sites and servers using virtual hosts and reverse proxying.  I then "wow" them even more by replacing our Windows 2000 file server with Samba and using shadow_vol to retrieve files rather than having to restore from backup tape.

This is the sort of thinking I am looking for.  Opportunities to replace windows server offerings (2000 & 2003) with a Linux alternative.  I would like to know how to achieve this and invite Brazen to help point me in the right direction.

---

