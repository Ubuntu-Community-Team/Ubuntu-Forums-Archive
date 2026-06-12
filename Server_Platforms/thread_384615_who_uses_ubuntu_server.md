---
title: "who uses ubuntu *server* ?"
date: 2007-03-14
forum: Server Platforms
---

### Post by eddgy on 2007-03-14
My employer is considering Ubuntu LTS Server.  We are not early "early adopter" though and certainly don't want to be alone in our choice of OS.  The purpose will be to host a JEE website with lots of boxes (80 count, multiple sites).

Obviously, Ubuntu on the desktop is very predominant... But who uses Ubuntu Server?  I asked Canonical for any customer reference's and they explained their concern for the sensitivity of customers' privacy and would not disclose.  And so, logically, I come to the community to ask.

Are there any large installs out there yet?  Actual money-earning companies depending on it?  What are the experiences, how's the support from Canonical, did you migrate from another vendo, etc..

I also came across a nice article which more than articulates my interest: [http://ubuntu.wordpress.com/2006/12/25/ubuntu-dedicated-servers-and-server-administrators/](http://ubuntu.wordpress.com/2006/12/25/ubuntu-dedicated-servers-and-server-administrators/)

and so I am re-asking "Who uses Ubuntu Server?"

THANKS!!
-Eddgy.

---

### Post by zipperback on 2007-03-17
> **eddgy said:**
> My employer is considering Ubuntu LTS Server.  We are not early "early adopter" though and certainly don't want to be alone in our choice of OS.  The purpose will be to host a JEE website with lots of boxes (80 count, multiple sites). 


We have Ubuntu 6.10 installed from the server edition cd and we are running it in a live deployment environment. I can't give the actual specific details of the company, however overall the results have been very positive.

---

### Post by nix4me on 2007-03-17
i use 6.10 server on a production box.  Works very nicely.

nix4me

---

### Post by rok3 on 2007-03-17
I'm using Ubuntu 6.06 LTS server for a LAMP box that holds the databases for the custom point of sale and customer reservation system at my job.  It's stable, quick, easy to update and as you can see the support available through the forums alone is amazing.

---

### Post by elst on 2007-03-17
The VPS host that I use offers Ubuntu as an option, alongside RHEL and Debian. IIRC, the Server flavour of Ubuntu only appeared with Dapper, so I'd guess that a lot of places already have a favoured distribution, although they may have started to use Ubuntu in a small or experimental way as an applications server. Ubuntu is probably better established as desktop or thin client system at this point.

For some reason, Java is a bit of a world of it's own - you may get more relevent info on how to tackle a deployment of this size by asking about host OSes on a Java forum.

---

### Post by Blond_Knight on 2007-03-17
I use 6.10 server in my bank.  I converted from Enterprise Redhat a few months ago.  Its running FTP, some samba, a network syslog monitoring script, and Im currently testing Splunk on it as well.

---

### Post by Brazen on 2007-03-18
We use Dapper Server at work.  We have a few routers, Apache server, and MySQL server that have been in production use for several months now with no problems.  Plus I am working on setting up a Nagios server on Dapper and probably move our DNS and DHCP servers to Dapper.  We also use Debian Etch for a file server (I tried Dapper, but there was a problem with Samba and I needed the newer version that was in Etch).

Also, you are doing the right thing going with the LTS release.  Your life as a server admin will go much smoother if you stick with the LTS releases.

---

### Post by cfyves on 2007-03-19
I have been setting up a LAMP server here in our organisation.
It will be used as a secondary server...

But, I am already running the server edition on another server. This server is our main Email server and has kind of an ironic configuration.

Ubuntu Server powering VMWare.
- VMWare OS Windows 2003 that powers MS Exchange and some 3rd party filtering software.

So..... Ubuntu running Exchange!

:) 

(Close enough)

That box has run perfectly since about last July when we set it up.

---

### Post by alamba on 2007-03-19
I've 5-6 boxes that I setup as "servers" on ubuntu. Primary applications used:
1. File server
2. Mail server
3. VPN Server (OpenVPN)
4. Apps - Gallery2, SugarCRM, (Damn I can't remember the name accounting package), ERP
5. Firewall/Proxy/Gateway
6. "Security" Server - ntop, nessus

A

---

### Post by astrogazer on 2007-03-19
Small software/hardwarecompany with 10 employees
Switched from SuSE to Ununtu 6.06 LTS last November.

1st box
 DNS,www,smtp,sftp,samba
2nd box
DNS, Java/JBoss, MySQL, this box keeps real time traffic data from about 500 vehicles
3rd box
Asterisk

1st & 2nd are dual processor, SCSI RAID

It works great!!!

---

### Post by Brazen on 2007-03-19
> **cfyves said:**
> I have been setting up a LAMP server here in our organisation.
It will be used as a secondary server...

But, I am already running the server edition on another server. This server is our main Email server and has kind of an ironic configuration.

Ubuntu Server powering VMWare.
- VMWare OS Windows 2003 that powers MS Exchange and some 3rd party filtering software.

So..... Ubuntu running Exchange!

:) 

(Close enough)

That box has run perfectly since about last July when we set it up.

yeah, that's a pretty cool idea.  Even if you only have one virtual machine running on it, you still gain some neat features running under VMWare (like being able to take snapshots, make backups of the virtual machine files for disaster recovery, and being able to easily move to new hardware, just to name a few).

---

### Post by cfyves on 2007-03-19
> **Brazen said:**
> yeah, that's a pretty cool idea.  Even if you only have one virtual machine running on it, you still gain some neat features running under VMWare (like being able to take snapshots, make backups of the virtual machine files for disaster recovery, and being able to easily move to new hardware, just to name a few).

Making a complete backup was the main reason.

And it always gives the option to create another virtual machine if needed.

---

### Post by JLTB on 2007-03-19
I manage and develop [www.projectopus.com](www.projectopus.com).  We are running a few DELL servers with Ubuntu Dapper LTS.

Works great, and as an added bonus most Debian S/W runs on the systems too.

James.

---

### Post by zillos on 2007-03-20
ubuntu 6 server with LAMP and outside: in balcony
[IMG]http://zillos.myftp.org/images/server5.png[/IMG]

---

### Post by smdeep on 2007-03-20
We are a small software company developing software for IBO international schools. Our development server is Ubuntu 6.06 LTS. We have the same config for our client schools.

---

### Post by jenhsun on 2007-03-20
I think Google might use Ubuntu too. But not sure desktop or server.
Here is the link:
[http://en.wikipedia.org/wiki/Goobuntu](http://en.wikipedia.org/wiki/Goobuntu)

---

### Post by punong_bisyonaryo on 2007-05-01
> **JLTB said:**
> I manage and develop [www.projectopus.com](www.projectopus.com).  We are running a few DELL servers with Ubuntu Dapper LTS.

Works great, and as an added bonus most Debian S/W runs on the systems too.

James.

Are you using the normal Ubuntu Dapper LTS or the "server" version that everybody else seems to be using?

I'm using Dapper (not the server edition, just plain old dapper) for use with WebDAV with SSL, so far seems to work great but I will have to defend my choice of distribution for this server. So any pros and cons that can help me will really be appreciated.

PS. I hope somenone replies really quick.

---

### Post by elst on 2007-05-02
@jenhsun: I've read that Goobuntu is for desktops, and that Google use an internally maintained distribution for servers.

@punong_bisyonaryo: Probably the best thing to is to post a new thread, with some background about the environment and which other operating systems are in use - it's very hard to do good OS comparisons without context. Generally, tagging questions on an existing thread significantly reduces the number of people who read your question.

---

### Post by prodsacnetworking on 2007-05-02
I now have 8 Ubuntu Servers (6.06)

- 4 load balanced web servers (apache, php, ncftp)
- 2 MySQL (x64)
- 2 mail servers.

Behind a chekpoint firewall

Before that I used solaris, but the lack of community and bizarre errors got me to try Ubuntu.. And I love it now.

---

