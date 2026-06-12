---
title: "New to web servers. Is Centos any safer than Ubuntu for ECommerce?"
date: 2009-02-26
forum: Server Platforms
---

### Post by rs2k on 2009-02-26
I am going to setup a server and run it from our main business office. I need to make sure I do it right but it is something I will definitely do. Right now I am hosted by liquid web on a dedicated server which has CentOS, Apache, MySQL, Cpanel, and WHM.

I am more familiar with Ubuntu than I am with CentOS. Is CentOS any safer than Ubuntu? Would it be a good idea to get a 3rd party to management service for the server?

---

### Post by E_K on 2009-02-26
it depends how you configure your server, you can configure anything to be as tight as it can get, the important thing is to get all the configurable variable that relate to what you are doing, and dont give any more permissions out to anything than it actually needs, and check out fail2ban and snort

---

### Post by ilrudie on 2009-02-26
As E_K said either can be configured to be secure if you have the know-how and put in the effort.  I think the main draw of CentOS is that it is designed first and foremost to be an enterprise server (its just redhat ES recompiled and rebranded).  Ubuntu is primarily known for bringing near-cutting-edge Linux to the desktop.  Ubuntu's upgrade and update schedule may create more work for you as an admin.  If you are comfortable with Ubuntu but don't need the latest packages, Debian is a great choice for servers which will be more familiar to you.

---

### Post by HermanAB on 2009-02-26
Linux is Linux is Linux...

Deep down all versions of Linux are the same.  Differences are superficial.  So use the version you like, which obviously is Ubuntu.

Cheers,

Herman

---

### Post by pparks1 on 2009-02-26
I'm personally a CentOS server user and Ubuntu desktop user.  I think both are fine systems and could handle the tasks that you want to do without any trouble.  I wouldn't necessarily say either is more secure or safer than the other...it all depends upon how you set it up.

I'd say to go with the one you are most familiar with.  This will help you to get things up and running more quickly since you have familiarity with it.

---

### Post by PilotJLR on 2009-03-01
I have a similar setup, pparks1.

I like CentOS for servers because RHEL (and also CentOS) offer very good support for SELinux. Very basic SELinux is available for Ubuntu, and I'm not sold on the idea that AppArmor is even real.  :-)

---

### Post by rs2k on 2009-03-01
Wow! Thanks for all the suggestions. I tried CentOS 5.2 and had some trouble so I switch to Ubuntu 8.10 LTS. So far I've had an easier time with Ubuntu.

---

### Post by bigbearomaha on 2009-03-01
8.04 is LTS, not 8.10.

---

### Post by rs2k on 2009-03-01
You're right, sorry about that, I meant 8.04 LTS.

---

### Post by binbash on 2009-03-01
Centos is better than Ubuntu Server in my opinion.I have around 3 servers, i am both using CentOS

---

### Post by Yashiro on 2009-03-02
Why is it better?

---

### Post by rs2k on 2009-03-02
I wish I was more familiar with Linux in general. I am used to cpanel but I only use it for about 5 things.

Create user and website.
create email
generate CSR
install SSL
phpmyadmin
webalizer

Where can I learn to do these things without cpanel?
1. Create user and website.
2. create email
3. generate CSR
4. install SSL
5. Create and run name server


I have a few months before I have to make this sever production ready and I want to be ready.

---

### Post by Vantrax on 2009-03-03
CentOS is better in my opinion for servers.

Its effectively Redhat rebadged with better package controls (so updates dont break things).


That being said, if you are comfortable with Ubuntu, dont we worried about using Ubuntu, at the end of the day its just a choice between two different package management styles, and two different hardening methods (AppArmor, and SELinux).

---

### Post by cb951303 on 2009-03-03
> **rs2k said:**
> I wish I was more familiar with Linux in general. I am used to cpanel but I only use it for about 5 things.

Create user and website.
create email
generate CSR
install SSL
phpmyadmin
webalizer

Where can I learn to do these things without cpanel?
1. Create user and website.
2. create email
3. generate CSR
4. install SSL
5. Create and run name server


I have a few months before I have to make this sever production ready and I want to be ready.

you can install a Cpanel like package
Some OSS alternatives are
[ISPConfig]("http://www.ispconfig.org/")
[Webmin]("http://webmin.com/")

EDIT: A distribution's contribution to security of a server depends on the security vulnerability fixes on packages like apache2, php, mysql, ssh etc.
For this reason I think CentOS is more secure than 8.04 LTS because it's been around longer than 8.04. The team had much more time to fix bugs on these important packages.

Other than this, security depends highly on you, configuring your system to be secure. You might want to start with learning iptables.

You may also try Debian Stable (5.0) which is always a safe bet.

---

