---
title: "OpenLDAP + Samba DC and fileserver"
date: 2009-01-20
forum: Server Platforms
---

### Post by wiz561 on 2009-01-20
Hi!

I setup my server using the instructions at the following URL...

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)
 Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller  

This seems to work fairly well but I am in permission hell with NFS.  Instead of fixing this, I thought I would just share this out using samba.  

The only problem is that it seems like openldap does not have a 'cn=config' in the directory tree.  I was trying to follow the instructions on the wiki here...

[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html)

and get...

ldapadd -x -D cn=admin,cn=config -W -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}samba.ldif 
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)

I am new to openldap, but I have a feeling that it is using the old style slapd.conf file instead of storing the configuration in the directory tree.  But again, I'm new to this so I don't know for sure.  

I am running...

slapd                                 2.4.9-0ubuntu0.8.04.1       OpenLDAP server (slapd)

But it seems like the latest in the ubuntu repo is 2.4.9, which is what I'm running.

Just seeing what's going on and how I can do this.  *ULTIMATELY*, my goal is to have my fileserver box (which is different than the openldap / 'dc' box) serve up my files with samba and use domain authentication.


Thanks!

---

### Post by HermanAB on 2009-01-20
You should read the "Official Howto" at the Samba web site.  They also have a howto specific to Ubuntu.

Cheers,

Herman

---

### Post by wiz561 on 2009-01-20
Thanks; I will check it out.  Official sites always scare me because there's usually a lot to read.  I admit that I'm a little lazy when it comes to documentation...that's usually why I just do the howto's.  

But I will check it out.  


Thanks!

---

