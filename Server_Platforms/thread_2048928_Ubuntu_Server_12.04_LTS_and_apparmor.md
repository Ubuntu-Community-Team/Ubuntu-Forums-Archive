---
title: "Ubuntu Server 12.04 LTS and apparmor"
date: 2012-08-27
forum: Server Platforms
---

### Post by Tobeus on 2012-08-27
Hi all,

Hopefully this is the best forum for this question, so forgive me if I am off.  Anyway, I am learning to create a web server from scratch using a basic Ubuntu Server 12.04 LTS install and was thinking about trying zPanel.  I was researching this tool and it says that the install script is going to remove app armor.  Now I have decided to download and print the manual for apparmor since it is a default install with Ubuntu server and was curious why they would uninstall it for a tool like zPanel.

Then I started checking other software and there are a bunch of people that basically say something along the lines of, "apparmor?  Uninstall that crap."  So I was curious if anyone could help me understand exactly what apparmor does, and whether I should or should not be concerned about removing apparmor.

I didn't think it was really anything more than an access control kind of software, so I just wasn't sure.  I'm looking to make this web server secure for public access as well (hosting a webpage eventually) and want to make sure I'm doing the right thing.

Thanks in advance for any help/knowledge anyone can give.

-Tobeus

---

### Post by LHammonds on 2012-08-27
In general, it is recommended that you understand and know how to secure whatever services you are running.

If you are running an Apache web server, you need to understand how it works and how to secure it.

AppArmor ([here is a tutorial]("http://ubuntuforums.org/showthread.php?t=1008906")) is like most other services...you need to learn, understand and know how it interacts with your system/services.  If you do not become intimately familiar with it, it will very-likely come back and byte you when you least expect it...especially with Apache (see tutorial).

Several tutorials are focused on just the service they are trying to tell you how to install...not give you additional tutorials on AppArmor, Firewalls, antivirus systems, routers, etc.  If you are not familiar with or do not have time to learn it, it is recommended that you do not use such a service (any service actually).  However, if you learn how to work the system, you can probably ignore that part of application tutorials that say to disable it since you know how to make it work.

LHammonds

---

### Post by Tobeus on 2012-08-27
Very nice tutorial, thanks for the reference LHammonds.  At least now I have a better understanding as to what apparmor does on a system.  I will begin reading the manual and see what makes it tick.

-Tobeus

---

