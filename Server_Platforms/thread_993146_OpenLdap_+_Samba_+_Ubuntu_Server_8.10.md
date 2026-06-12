---
title: "OpenLdap + Samba + Ubuntu Server 8.10"
date: 2008-11-25
forum: Server Platforms
---

### Post by johnybgood11 on 2008-11-25
Hi there,

I have Ubuntu Server installed in a desktop computer and I'm trying to use it for controlling a domain which will be used for windows machines authentication and file sharing.

I followed this tutorials:
[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)
[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html#samba-ldap-installation](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html#samba-ldap-installation)

My domain is welka.local and I can see it in ldapsearch but when I try to connect from my windows machine to the welka domain using root user and pass I get "access is denied" error.

Any ideas why?

I've attached:
smb.conf
smbldap.conf
ldap.conf

Thanks in advance.

---

### Post by HermanAB on 2008-11-25
There are many reasons why it won't work, but the most common issue is that the time on the client and server is different, so then Kerberos won't work.

See this link for some debug help:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by Coreigh on 2008-11-25
Some sanity-check questions.

Did you get all the way through all 3 pages of the tutorial? You didn't mention bind or your bind.conf.

Are you using XP Pro? Home will not work as they cannot join a Domain. Are the computers Domain members? Or is that where you are getting the denied error? Sometimes it is possible to enter credentials differently to authenticate. Instead of just user it could be DOMAIN\user or user@domain.

The how-to does not mention kerberos, but I know to connect the other way Ubuntu client to Windows domain you need kerberos to authenticate.

Have you looked up any other how-tos on this subject?
[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows))

I see that most of the Google links simply point to copies of the how-to that you used.

---

### Post by johnybgood11 on 2008-11-26
Hi there Coreigh,

First of all I'm running Windows XP Pro SP3 on the client. I had used this two tutorials once and was able to successfuly join my domain with the same windows xp client until I eventually messed up the configs because samba was not storing windows profile configs. Then restarted from scratch.

I went all the three pages and you can see the named.conf in attachement. 


The error I got was "Access Denied". I tried the following for my domain welka:

root
pass

welka\root

root@welka

[email]root@welka.loca[/email]l

All gave the same answers.

I'll try to work my way around that tutorials and see where I stand. Anyway, I never used kerberos. Do I really need it? Where to start?

Thanks once again

---

### Post by johnybgood11 on 2008-11-26
Problem solved.

I had an error in smb.conf had to change:

ldap admin dn= cn= admin, dc=example, dc=local
ldap suffix =dc=example, dc=local

for the correct domain in my case:
changing example to welka did the trick

---

