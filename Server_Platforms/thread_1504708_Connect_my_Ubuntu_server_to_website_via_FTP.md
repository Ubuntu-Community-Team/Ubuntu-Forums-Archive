---
title: "Connect my Ubuntu server to website via FTP"
date: 2010-06-08
forum: Server Platforms
---

### Post by QuackPot10 on 2010-06-08
I have a an ubuntu server with some files on it and I was wanting to upload them to my website (proper online website) via FTP. But can this be done. I have the book "Beginning Ubuntu LTS Server Administration" and it doesn't provide much help on how to set up FTP.


Please can someone help. I really need to get this complete.


Cheers.

---

### Post by unmole on 2010-06-08
Take a look at [this.]("http://www.faqs.org/docs/Linux-mini/FTP.html#s3")

---

### Post by Detonate on 2010-06-08
If you have Firefox installed on the server, simply install the "Fireftp" extension.  Works great.

---

### Post by unmole on 2010-06-08
> **Detonate said:**
> If you have Firefox installed on the server, simply install the "Fireftp" extension.  Works great.

I believe he installed Ubuntu server edition, without X or Firefox. Right?

---

### Post by Detonate on 2010-06-08
Probably, but if he has firefox on the computer he is using to manage the server and has the directory on the server mounted on that computer it would still work.

---

### Post by QuackPot10 on 2010-06-08
> **unmole said:**
> I believe he installed Ubuntu server edition, without X or Firefox. Right?

I'm running Ubuntu Server 9.10s on Oracle Virtual Box 3.2 on Windows 7 x64. 

I can't get SSH to work for some reason which is causing me a whole load up problems and stress. I really need my files from my virtual ubuntu server on my Windows PC. And since SSH doesn't work I thought FTP would.

---

### Post by arrrghhh on 2010-06-08
Hrm... perhaps we should debug those issues.  Assuming you installed the packages for ssh, did you enable UFW and open the port?  If you didn't enable UFW it shouldn't block the traffic...

Can you connect to the VM in any other way?

---

### Post by QuackPot10 on 2010-06-08
I have the ufw firewall off and yet I still can't connect when using putty or WinSCP.

Is there any other setting anywhere that can allow SSH?

Or even a simple ftp?

---

### Post by arrrghhh on 2010-06-08
You need to install a package for ftp - proftp, vsftp, etc.

See [this](https://help.ubuntu.com/community/SSH) to a guide on SSH.

---

