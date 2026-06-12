---
title: "Ubuntu Server"
date: 2019-03-07
forum: Server Platforms
---

### Post by astreb06 on 2019-03-07
[COLOR=#2A2A2A][FONT=&quot]Hello all,[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=&quot]  My newness to the world of Servers can be encapsulated within the last 10 months.  You can say this responsibility has been tossed onto my plate. I have learned a lot since then and manage to find solutions to my problems by "Google Searching" my way out with the offline network that I now maintain.  I now seek help because I am working backwards in software. [/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=&quot] I "inherited" a Windows Server 2012 R2 that has a VM [FONT=Calibri]Ubuntu 16.04 Server on it.  On Ubuntu was created a intranet Web Server. [/FONT] What I am wanting to do is copy the Ubuntu Server with the Web Server content and put it on Windows Server 2008 R2 on its Hyper-V. [/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=&quot]How can I accomplish this task?  WS 2012 R2 has the replication feature, but WS 2008 R2 does not. I don't want to export it either as I want the web server on both. Could I use a 3rd-party software to copy the VM Ubuntu?  What would you recommend?  Any other suggestions or ideas?  [/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=&quot]Thanks for your help.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2019-03-08
Is this a simple set of  HTML documents, or an application that relies on code and maybe a database? If the former, just copy the files to the corresponding directory on Windows. If this is an application, you need to speak to the developers.

---

### Post by LHammonds on 2019-03-08
If it were me, I would just setup a new VM and try to set it up in such a way that it could replace that server.  This would give you the confidence of knowing that application and what is needed to make it viable from one server to the next.

I would also find out if the components of the site could work on the most current version of the server (Ubuntu Server 18.04.1 LTS) or if it was specific to 16.04.  Keep in mind that even if you need an older version of PHP than what is available by default in the repositories, there are ways to make older versions work on new operating systems.

Also, it sounds odd going from a Win2012 to Win2008 operating system.  Sounds like you are moving backwards.

This all starts with researching and documenting what you currently have:

* Ubuntu Server 16.04
* Apache 2.4.18?
* PHP 7.0.22?
* MySQL or MariaDB?
* Credentials for connecting to the DB
* User/Group permissions on the web files/folders.
* Installed web/php libraries (phpinfo is helpful with this)
* Is the site WordPress?  Specific version? Installed plugins? etc.

LHammonds

---

