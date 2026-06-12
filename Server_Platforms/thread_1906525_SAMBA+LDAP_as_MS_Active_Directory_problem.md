---
title: "SAMBA+LDAP as MS Active Directory problem"
date: 2012-01-09
forum: Server Platforms
---

### Post by MakroSiroki on 2012-01-09
Hello to all!

I am trying to setup SAMBA+LDAP as MS Active Directory, so Windows boxes will be able to login into SAMBA Domain. I have two questions:
1) In smb.conf file, there is variable workgroup, which value if name of network domain. Does this workgroup variable refers to Windows Domain or Windows Workgroup in Windows Terminology
2) I am following Ubuntu SAMBA+LDAP Server Guide and I am stuck at following step:```
Adding Samba LDAP objects

Next, configure the smbldap-tools package to match your environment. The package comes with a configuration script that will ask questions about the needed options. To run the script enter:

sudo gzip -d /usr/share/doc/smbldap-tools/configure.pl.gz
sudo perl /usr/share/doc/smbldap-tools/configure.pl
```Iam stuck at the perl command, which returns:```
Global symbol "$SID" requires explicit package name at /usr/share/doc/smbldap-tools/configure.pl line 350.
Execution of /usr/share/doc/smbldap-tools/configure.pl aborted due to compilation errors.
```I opened conflicting file and and replaced SID value with domain SID, but error persists. Can someone help me please with this error?

---

### Post by luvshines on 2012-01-09
> **MakroSiroki said:**
> Hello to all!

1) In smb.conf file, there is variable workgroup, which value if name of network domain. Does this workgroup variable refers to Windows Domain or Windows Workgroup in Windows Terminology

It should refer to the Windows Workgroup in windows terminology. When your Samba is setup properly, the server should be visible as a part of this workgroup

> 
I am stuck at the perl command, which returns:```
Global symbol "$SID" requires explicit package name at /usr/share/doc/smbldap-tools/configure.pl line 350.
Execution of /usr/share/doc/smbldap-tools/configure.pl aborted due to compilation errors.
```I opened conflicting file and and replaced SID value with domain SID, but error persists. Can someone help me please with this error?

We were trying to solve this on a similar thread [http://ubuntuforums.org/showthread.php?t=1885017](http://ubuntuforums.org/showthread.php?t=1885017)

See if the syntax errors which I corrected in my last post works for you

---

### Post by Vegan on 2012-01-09
Do you have a domain controller?

You will need one.

---

### Post by MakroSiroki on 2012-01-09
> **Vegan said:**
> Do you have a domain controller?

You will need one.I've setup SAMBA as domain controller, I think ...

---

### Post by Merganser on 2012-01-09
I'm in the process of doing the same thing you are, creating a windows dc.  The samba workgroup name IS the widnows domain name.  The examples all show it as just a netbios name but it can be a fully qualified name as well, eg. mydomain.local.  What ever you use thats what your windows boxes willl see as the domain name.  I've gotten far enough to whitness this.  

I did not have the pl problem...

---

### Post by MakroSiroki on 2012-01-09
> **Merganser said:**
> I'm in the process of doing the same thing you are, creating a windows dc.  The samba workgroup name IS the widnows domain name.  The examples all show it as just a netbios name but it can be a fully qualified name as well, eg. mydomain.local.  What ever you use thats what your windows boxes willl see as the domain name.  I've gotten far enough to whitness this.  

I did not have the pl problem...Which version of ubuntu server are you running that you did not have pl problem!

---

### Post by MakroSiroki on 2012-01-10
> **Vegan said:**
> Do you have a domain controller?

You will need one.Did you mean by setting workgroup variable in smb.conf? If so, I did that.

---

### Post by MakroSiroki on 2012-01-10
When I try to add Windows 7 Ultimate box into my domain, I get on the server side (/var/log/syslog) following errors:```
slapd[3320]: conn=1006 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (uid) not indexed
slapd[3320]: conn=1007 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: conn=1008 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (sambaSID) not indexed
slapd[3320]: conn=1009 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: conn=1010 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (sambaSID) not indexed
slapd[3320]: conn=1011 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: conn=1012 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (sambaSID) not indexed
slapd[3320]: conn=1013 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: SASL [conn=1014] Failure: no secret in database
slapd[3320]: conn=1015 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (sambaSID) not indexed
slapd[3320]: conn=1016 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: conn=1017 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (uid) not indexed
```

What do they mean? That my LDAP database is ok, but SAMBA is not filled with data from LDAP?

---

### Post by MakroSiroki on 2012-01-10
> **MakroSiroki said:**
> When I try to add Windows 7 Ultimate box into my domain, I get on the server side (/var/log/syslog) following errors:```
slapd[3320]: conn=1006 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (uid) not indexed
slapd[3320]: conn=1007 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: conn=1008 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (sambaSID) not indexed
slapd[3320]: conn=1009 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: conn=1010 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (sambaSID) not indexed
slapd[3320]: conn=1011 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: conn=1012 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (sambaSID) not indexed
slapd[3320]: conn=1013 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: SASL [conn=1014] Failure: no secret in database
slapd[3320]: conn=1015 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (sambaSID) not indexed
slapd[3320]: conn=1016 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: conn=1017 op=0 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"
slapd[3320]: <= bdb_equality_candidates: (uid) not indexed
```What do they mean? That my LDAP database is ok, but SAMBA is not filled with data from LDAP?No one can help me with my problem?? :confused:

---

