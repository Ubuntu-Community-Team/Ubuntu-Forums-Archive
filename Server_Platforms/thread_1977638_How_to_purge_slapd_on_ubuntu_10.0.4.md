---
title: "How to purge slapd on ubuntu 10.0.4 ?"
date: 2012-05-10
forum: Server Platforms
---

### Post by cheikhou on 2012-05-10
I'm trying to configure a PDC ldap server with samba  following this tuto [http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html) So after entering :

 >                                    
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.ldif  
 i want to completely remove the slapd installation because i got some errors in the backend.ldif loaded file so i did :


>                          
 sudo apt-get purge  slapd ldap-utils libpam-smbpass smbldap-tools

sudo rm -rf /var/lib/ldap/*

sudo apt-get install  slapd ldap-utils libpam-smbpass smbldap-tools 
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.ldif 
but i have the same error                                     
ldap_add: Other (e.g., implementation specific) error (80)

PLEASE HELP !!!!!!

---

### Post by kennethconn on 2012-05-10
Try:
 
$sudo apt-get --purge remove slapd

---

### Post by cheikhou on 2012-05-11
i have try 
> 
$sudo apt-get --purge remove slapd 	
sudo apt-get install  slapd ldap-utils libpam-smbpass smbldap-tools 
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif


and still having errors like

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=inetorgperson,cn=schema,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
    additional info: olcObjectClasses: AttributeType not found: "audio"

it seems there was a bug report in [https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/583372](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/583372)
i have also try 
> 
sudo dpkg-reconfigure slapd


---

### Post by kennethconn on 2012-05-11
That might be a problem with the contents of the ldif file(s) themselves.

---

### Post by cheikhou on 2012-05-12
OK. So I will format the disk  and retry with a fresh install

---

### Post by kennethconn on 2012-05-12
Shame to have to do a complete install.
 
I used [https://help.ubuntu.com/11.10/serverguide/openldap-server.html](https://help.ubuntu.com/11.10/serverguide/openldap-server.html)
 
which is different from your version, so I never had to use
 
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif
 
I never had an install problem following the guide. If you are going to do a new install, upgrade everything.

---

### Post by cheikhou on 2012-05-13
OK thanks . i will try your link . hope i will work correctly on my 10.04

---

