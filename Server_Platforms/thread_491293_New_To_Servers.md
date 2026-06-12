---
title: "New To Servers"
date: 2007-07-03
forum: Server Platforms
---

### Post by cranshinibon on 2007-07-03
Alright, I'm currently in Network + and my final class for college and without any linux server experience am thrown into it without knowing much than linux basics, but forgetting them after long months of Exchange Server. 

I need help with a few of the following:

I am running Ubuntu 7.10 on my PC with Webmin working perfectly as well as ClamAV  (everything i need help with is required)

I need help trying to set up FTP on my Server so the other computers connected to the switch can use it. Here are a few problems I need assistance with.

(1) how to configure gFTP to run from my computer so it'l function correctly and be able to be used by the other computers running Fedora Core 5, Windows Server 2003, and Windows XP.

(2) how do you set up your server with NFS? 

(3) how do you set up your server with HTTP?

(4) how do you permanently set your IP so you can access the internet over the switch from the DC on Windows Server 2003 running NAT?

(5) how do you add yourself to a workgroup so you are on the same network as the computers running windows?

---

### Post by meatpan on 2007-07-03
I strongly suggest looking over the server guide, which has detailed instructions for many of your requests: [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

In general, the first thing you will do is install the server software packages via apt-get or synaptic.  Next (this is where 99.9% of your time should be), is setting up and configuring the software.   You will have to read quite a bit of apache and samba documentation to get comfortable with the server parameters and misc settings.

---

### Post by cranshinibon on 2007-07-03
alright well i read through the information and it was a huge help but im still running into a few problems.

So far I can connect to the internet through NAT routing on the Windows Server though I'm still running into some nooks.

I have vsftpd and nfs installed but I can't figure out how to configure them for others use.

with the ftp how do I have others on my network be able to access it. i dont know what to give them so they can log in nor do i know how to give them a login and password

with the nfs and http i dont know how to set them up and see if they're working nor how to configure them for the others to utilize them.

please help lol i am a complete noob with this :(

---

### Post by murraymca on 2007-07-03
Hi,

What are the nooks you were running into?

This section of the guide (posted earlier) [http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html) details how to set up apache.  For other users to connect you really don't have to do anything special, just install and start.  The ubuntu documentation should be more than enough for that, but the apache site has plenty of info also:  [http://httpd.apache.org/docs/](http://httpd.apache.org/docs/)

To check if it is running you could run "netstat -tn" and you should see something listening on port 80.

Good luck, and if you get stuck don't forget about the ubuntu server guide posted earlier, that should get you going!

---

