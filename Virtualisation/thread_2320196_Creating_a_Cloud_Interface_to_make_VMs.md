---
title: "Creating a Cloud Interface to make VMs"
date: 2016-04-11
forum: Virtualisation
---

### Post by DRG71 on 2016-04-11
Hello, 

I am new to Ubuntu and hosting but am looking to provide a service.  I am a teacher for application development and I have an Ubuntu Server available.  I would like my students to be able to go to a portal that is on the web -> select from dropdowns to create a VM on the Server (i.e. Windows, RHEL, SQL, Ubuntu, MySQL, etc) so they can build a VM they way they would like. -> I would like them to ten be able to enter the box within their environment and code apps according to requirements I have provided -> once complete I would like to be able to go into the box as an admin and review all of their code and applications. 

Anyone have any idea how I could do this?   Or, would using something like AWS be easier?  If so, would I still be able to control the portal where they select what the want to deploy as a VM?

Thank you!!!
Grant

---

### Post by TheFu on 2016-04-12
Welcome to the forums.

Use AWS or any of the cheaper, better VPS.  AWS is kinda expensive.  You don't want to build this yourself. There are many, tiny, security considerations that are not intuitively obvious. This is especially true when any web-interface is added for admin tools. Heck, even the pros at creating these tools often have issues.

If you want to have some fun and see what has already been made - "perfect server" websearch will find a how-to guide to make a DNS/Web/email/FTP server on shared hosting. The resulting solution might be good for a house, but not in a hostile environment connected to the internet or any college network, IMHO.

If you want to make a self-serve VPS provider, openstack is what you need, but the complexity of the setup isn't worth it without 10+ nodes. This must be part of the reason why Ubuntu's instructions assume 10 nodes minimal.  [http://www.ubuntu.com/cloud/maas](http://www.ubuntu.com/cloud/maas) [https://help.ubuntu.com/lts/clouddocs/en/Installing-MAAS.html](https://help.ubuntu.com/lts/clouddocs/en/Installing-MAAS.html)  

Juju can be fun, but you seem to want cross platform solutions. Juju is Ubuntu-only.
[https://jujucharms.com/docs/stable/about-juju](https://jujucharms.com/docs/stable/about-juju)

Another option that will work for smaller setups is proxmox. Not really an Ubuntu thing (base OS is debian I think). Mostly about creating a VPS web front-end. Nothing for inside the VMs after installation, is my understanding.

If you want RHEL, they make a nice VM management tool called oVirt. Also, has huge overhead and huge complexity and not really useful for 1 box installs. Plus, I don't think it works on any Debian hosts.

"sql" is a language, not any specific software or server. Pet peeve of mine.  MS didn't invent the language nor the server.  If you ask me for a "sql server", I'd load up postgres, unless Oracle RDBMS is specified.
MySQL is MariaDB these days too.  Haven't deployed mysql in years.

OWASP Top 10 lists [https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project) 
Do not use passwords for authentication after the first login.  Pretty much nobody hacks (through the front door) on systems using key-based authentication.
ssh and sftp are a way of life.  Plain FTP died with telnet in the mid-1990s.  VNC/RDP aren't secure without full VPNs.  vnc-server has a localhost option to force all remote connections through some other method, hopefully secure, to be used.  Or just use an NX protocol for this stuff if ssh isn't good enough.

Hope you don't mind my extra shares. I'm involved with a few local universities CS, Security and IT training and it seems many of the faculty don't have time to keep up with important trends in IT and security. After all, teaching is hard - really hard and definitely more than a full-time job.  Plus the offensive security departments really keep me on my toes! ;)

---

### Post by slickymaster on 2016-04-12
*Moved to the ***Virtualisation*** sub-forum*

---

