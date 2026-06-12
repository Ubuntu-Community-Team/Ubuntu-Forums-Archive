---
title: "LDAP directory working, but not logins"
date: 2007-11-30
forum: Server Platforms
---

### Post by roussel@uleth.ca on 2007-11-30
I'm running Open Directory on a Mac (running OS X Server Edition 10.4, in case that matters). I would like to serve out passwords from the Mac so that my users don't have multiple passwords on our little network. In addition to the Macs, I have two Ubuntu workstations running 6.06 (LTS). I looked at [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) and followed these instructions. I can see the password file if I do "getent password" on the Ubuntu machines, but I can't login. If I try to su to one of the LDAP accounts, I get the following message:

su: Authentication service cannot retrieve authentication info.

If I understand the relationships between various bits of software correctly, that means that LDAP is working OK, but PAM isn't. All the PAM configuration files are like those in the help page mentioned above, so I won't bother to copy them here. Any ideas what I might look at to get this going? I did search the forums before posting and I saw at least one similar question, but I didn't see a solution. Obviously, if someone can refer me to some particular past thread or online instructions, that would be fine.

---

### Post by gpredrag on 2007-12-01
It might be the nsswitch problem, where you as root are able to perform getent passwd lookups, but not as regular user.
Does your LDAP server really allows anonymous logons? Do you have settings for authentication in libnss-ldap.conf for users or for local root.
What are file permissions for libnss-ldap.conf. I have find that file must be world readable for user to authenticate.
Are there any messages in /var/log/auth.log or /var/log/syslog?

---

### Post by sciurus on 2007-12-02
[This howto]("http://wiki.freaks-unidos.net/linux%20ldap%20howto") may be helpful.

---

### Post by roussel@uleth.ca on 2007-12-03
> **gpredrag said:**
> It might be the nsswitch problem, where you as root are able to perform getent passwd lookups, but not as regular user.

getent passwd works for an ordinary user. (I don't have an actual root account, and I didn't use sudo with getent passwd.)

> **gpredrag said:**
> Does your LDAP server really allows anonymous logons?

I tried setting
rootbinddn cn=admin,dc=a,dc=b,dc=c,dc=ca
(actual values changed for obvious reasons) in /etc/libnss-ldap.conf and putting the admin password in /etc/ldap.secret. That doesn't seem to help.

> **gpredrag said:**
> Do you have settings for authentication in libnss-ldap.conf for users or for local root.

I'll admit that what I know about LDAP wouldn't fill a very large corner of a piece of paper. I'm not sure what exactly is being asked here. What configuration options should I be looking at?

> **gpredrag said:**
> What are file permissions for libnss-ldap.conf. I have find that file must be world readable for user to authenticate.
Are there any messages in /var/log/auth.log or /var/log/syslog?

The file permissions are 644, so that should be OK.

As for the logs, my latest login attempt generated the following messages in auth.log:
```

Dec  3 09:17:13 localhost sshd[7012]: Invalid user roussel from 142.66.42.124
Dec  3 09:17:13 localhost sshd[7012]: Failed none for invalid user roussel from 142.66.42.124 port 54938 ssh2
Dec  3 09:17:16 localhost sshd[7012]: pam_ldap: error trying to bind (Invalid credentials)
Dec  3 09:17:16 localhost sshd[7012]: (pam_unix) check pass; user unknown
Dec  3 09:17:16 localhost sshd[7012]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=poincare.chem.uleth.ca 
Dec  3 09:17:19 localhost sshd[7012]: Failed password for invalid user roussel from 142.66.42.124 port 54938 ssh2
Dec  3 09:17:21 localhost sshd[7012]: pam_ldap: error trying to bind (Invalid credentials)
Dec  3 09:17:21 localhost sshd[7012]: (pam_unix) check pass; user unknown
Dec  3 09:17:23 localhost sshd[7012]: Failed password for invalid user roussel from 142.66.42.124 port 54938 ssh2
Dec  3 09:17:25 localhost sshd[7012]: pam_ldap: error trying to bind (Invalid credentials)
Dec  3 09:17:25 localhost sshd[7012]: (pam_unix) check pass; user unknown
Dec  3 09:17:28 localhost sshd[7012]: Failed password for invalid user roussel from 142.66.42.124 port 54938 ssh2

```
There was a similar message in syslog. The invalid credentials thing is probably what's hanging me up, but then why does getent passwd work?

I very much appreciate the help.

---

### Post by gpredrag on 2007-12-03
Apparently you have got nsswitch side ok, but not libpam-ldap.
On Debian in Ubuntu libpam-ldap reads its configuration from /etc/pam_ldap.conf which in most configurations is identical to libnss-ldap.conf.
Also in both files there are setings for rootbinddn and rootpw which are used when effective user id is 0 (root) and separate binddn and bindpw for all others.
LDAP itself might not allow anonymous binds so it might be necessary to set bindn and bindpw in those files.
Binddn should refer to some existent low privilege user in ldap (for example cn=proxyuser,uo=.....)
You might try to generate appropriate pam_ldap.conf by running "sudo dpkg-reconfigure libpam-ldap"

---

### Post by roussel@uleth.ca on 2007-12-04
> **gpredrag said:**
> Apparently you have got nsswitch side ok, but not libpam-ldap.
On Debian in Ubuntu libpam-ldap reads its configuration from /etc/pam_ldap.conf which in most configurations is identical to libnss-ldap.conf.

This turned out to be the key clue: I had a look at /etc/pam_ldap.conf and at /etc/libnss-ldap.conf and they had one important difference: The latter had bind_policy set to soft (as suggested in [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)), but the former didn't.

> **gpredrag said:**
> Also in both files there are setings for rootbinddn and rootpw which are used when effective user id is 0 (root) and separate binddn and bindpw for all others.
LDAP itself might not allow anonymous binds so it might be necessary to set bindn and bindpw in those files.

I was in fact able to comment out rootbinddn (and not set binddn), i.e. use anonymous binding.

Thanks a lot for the advice. I *really* appreciated the help as I went through this process. It's really great to have this working.

Perhaps I can ask one more question while I'm here: If /etc/pam_ldap.conf and /etc/libnss-ldap.conf should be the same in normal configurations, is there any reason why I can't replace one of them by a symbolic link?

---

### Post by gpredrag on 2007-12-04
There are separate files, because, technically, one could be using pam_ldap and not nsswitch-ldap or other way around, so those two files belong to different packages. I believe one file can be made symlink to other, and some people make that arrangement, but I don't.
Reason: I am not sure what would happened during upgrades, or if I accidentally uninstall  one of them. I just don't feel like messing around with package system, it is just perfect as it is

---

