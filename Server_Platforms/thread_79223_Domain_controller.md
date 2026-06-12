---
title: "Domain controller"
date: 2005-10-19
forum: Server Platforms
---

### Post by billiejoex on 2005-10-19
Hi all. Is there a simple tutorial where I can learn how can I run my Ubuntu like a Primary Domain Controller? 
I need a centralized client authentication.

Thanks in advance.

---

### Post by billiejoex on 2005-10-20
Up

---

### Post by LordHunter317 on 2005-10-20
The Official Samba HOWTO (samba.org) is fine, but you can only run a domain at NT4 PDC level, which is pretty much crap.

---

### Post by pmjdebruijn on 2005-11-25
Hi,

Take a look at this:
[http://www.xs4all.nl/~bruijn9/docs/sambapdc/sambapdc.pdf](http://www.xs4all.nl/~bruijn9/docs/sambapdc/sambapdc.pdf)

I didn't write that for Ubuntu, but most of it is easily adaptable to Ubuntu.

Good Luck,
Pascal de Bruijn

---

### Post by s0c0 on 2005-11-27
If you have the money I'd by the Samba 3 book put out by O'Reilly press, other than that the Samba How to guide is the best I've been able to find.

---

### Post by kejar31 on 2005-12-06
You can just simplify the whole thing by just downloading the script on this site. It is made for ubuntu as well. It will setup a samba3 PDC/Ldap server with roaming profiles and home directories in about 10 min.

[http://majen.net/smbldap/](http://majen.net/smbldap/)

---

### Post by bendigo on 2006-01-09
OK, Kejar31 I will try your script and let you know how it goes. ;)

---

### Post by kejar31 on 2006-01-09
its not my script but it does work. That  script was writen by Matt Oquist ( Nice fellow :D  ) Although I have just finished a script. My script is not for Ubuntu though :( but it does do some nice stuff. :cool:  

heres the run down on my script.

This installer is based off the lx-office groupware installer by Peter Haufschild. I have change what i consider alot. It is all in engish, as I am Ameican and that is the only language I understand.

Most of this work was done late at night, so forgive my bad gramer and spelling.


Included with the installer is:

1. Open-Xchange - Open-Xchange includes an email server using Postfix. Open-Xchange also offers Shared Calendaring, Shared Tasks, Shared Contacts and more. Access tp Open-Xchange features can be either accessd through the web interface or through your favorite client. Open-Xchange even sells an Outlook plugin for 25 US dollars per seat

2. Samaba PDC - Samba is configured and setup as a PDC ( NT Primary Domain Controller ). Included within the default config are roaming profiles, roaming home drives, start up scripts and a print server.

3. OpenLDAP- Both Samba and Open-Xchange use the same LDAP back end. ( LDAP is the Directory Server )

4. BIND - You will also receive a configured DNS Server.

5. IDEALX smbldap-tools with mkntpwd all configured and ready to go. ( Although you will want to user the AVA-adduser script included, to add a new user. )

6. PHPLDAPADMIN – Phpldapadmin helps you administer ldap accounts. Most importantly change a users samba group id and password.

7. Webmin – Webmin is a web based administration tool. With Webmin, administrators can remotely configure and administer the system.

The one drawback is that it is for Scientific Linux only at this moment Scientific Linux is a RHEL Clone - Its a good one to.

I do plan on porting it to Ubuntu though. 

there is also a screenshot by screenshot how-to as well

here it the link to that how-to 
[ftp://ns1.facettech.com/AVA-INSTALL-HOWTO.pdf](ftp://ns1.facettech.com/AVA-INSTALL-HOWTO.pdf)


Good luck with Matt's script though it works very well.

---

### Post by 1oki on 2006-02-17
Well not sure if anyone is reading this thread... but I used a realy easy step by step domain controller HOWTO, comes with pictures for those who want to see what is going on! Check it out:

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

Hope this helps!:D

---

