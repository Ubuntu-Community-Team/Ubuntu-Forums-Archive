---
title: "join Ubuntu Server 14.04 to domain, Only AD administrator is able to login"
date: 2016-04-28
forum: Server Platforms
---

### Post by wzjjanet on 2016-04-28
Hello all,
I am new to Ubuntu. I am building a Ubuntu server (14.04) and need to join it to the domain.
I followed this link, everything works very well. 
[http://www.unixmen.com/how-to-join-an-ubuntu-desktop-into-an-active-directory-domain/](http://www.unixmen.com/how-to-join-an-ubuntu-desktop-into-an-active-directory-domain/)

no errs, and I can see the server in domain.

But I noticed, I could NOT login to the Ubuntu server with any domain user account, except the domain built-in administrator account. User accounts in domain admin group doesn't work also.
If I run id domainuser, it gives me no such user err. 
all these related services are up and running, but just can't login to domain with domain user accounts (except administrator) and can't use 'su - domainuser' to switch user account also..

Please help me...

Thank you

---

### Post by wzjjanet on 2016-04-28
or any .log file or configuration file I should post here&#65311;

---

### Post by slickymaster on 2016-04-28
*Thread moved to **Server Platforms**.*

---

### Post by wzjjanet on 2016-04-29
Here is the sssd.conf

[sssd]
domains = MYDOMAIN.COM
config_file_version = 2
services = nss, pam


[domain/MYDOMAIN.COM]
ad_domain = MYDOMAIN.COM
krb5_realm = mydomain.com
realmd_tags = manages-system joined-with-adcli
cache_credentials = True
id_provider = ad
krb5_store_password_if_offline = True
default_shell = /bin/bash
ldap_id_mapping = True
use_fully_qualified_names = True
fallback_homedir = /home/%d/%u
access_provider = ad

---

### Post by wzjjanet on 2016-04-29
I built another new box this morning. Same issue. I can see the server is listed in Active directory...But I just can't login with any domain user except buildin domain administartor.

---

### Post by darkod on 2016-04-29
Have you tried the samba + winbind alternative? I know samba is quite better joining windows domains.

The tutorial you used looks simple enough but you say it doesn't work for you. Also, it never mentions if all domain users can be used or only the new ones created after you have joined the server to the AD. Maybe that's the reason it works only with the Administrator account.

---

### Post by wzjjanet on 2016-04-29
Thank you for your reply...We have the multiple trusted Domain (Domain A, Domain B). I built anther one, and it joined to the Domain B, works perfect. Doesn't matter new AD users or existing AD users. By default, after joining to domain , The box should be access by any domain users.

The one which joined to domain A, all the same steps, only administrator can login to the box. 

Here are part of the logs in auth.log:

Apr 29 14:46:25 ubuntutest login[2388]: pam_unix(login:auth): check pass; user unknown
Apr 29 14:46:25 ubuntutest login[2388]: pam_unix(login:auth): authentication failure; logname=rrc uid=0 euid=0 tty=/dev/tty1 ruser= rhost=
Apr 29 14:46:25 ubuntutest login[2388]: pam_sss(login:auth): authentication failure; logname=rrc uid=0 euid=0 tty=/dev/tty1 ruser= rhost= user=MYDOMAIN.COM
Apr 29 14:46:25 ubuntutest login[2388]: pam_sss(login:auth): received for user academic.rrc.ca: 10 (User not known to the underlying authentication module)
Apr 29 14:46:27 ubuntutest login[2388]: FAILED LOGIN (1) on '/dev/tty1' FOR 'UNKNOWN', Authentication failure
Apr 29 14:46:49 ubuntutest login[2388]: pam_unix(login:auth): authentication failure; logname=rrc uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=administrator@MYDOMAIN.COM
Apr 29 14:46:54 ubuntutest login[2388]: pam_sss(login:auth): authentication success; logname=rrc uid=0 euid=0 tty=/dev/tty1 ruser= rhost= user=administrator@MYDOMAIN.COM
Apr 29 14:46:55 ubuntutest login[2388]: pam_unix(login:session): session opened for user [email]administrator@MYDOMAIN.COM[/email] by rrc(uid=0)

---

### Post by wzjjanet on 2016-04-29
Apr 29 15:16:18 ubuntutest login[2551]: pam_unix(login:auth): check pass; user unknown
Apr 29 15:16:18 ubuntutest login[2551]: pam_unix(login:auth): authentication failure; logname=administrator@MYDOMAIN.COM uid=0 euid=0 tty=/dev/tty1 ruser= rhost=
Apr 29 15:16:18 ubuntutest login[2551]: pam_sss(login:auth): authentication failure; logname=administrator@MYDOMAIN.COM uid=0 euid=0 tty=/dev/tty1 ruser= rhost= user=MYDOMAIN.COM
Apr 29 15:16:18 ubuntutest login[2551]: pam_sss(login:auth): received for user MYDOMAIN.COM: 10 (User not known to the underlying authentication module)
Apr 29 15:16:21 ubuntutest login[2551]: FAILED LOGIN (1) on '/dev/tty1' FOR 'UNKNOWN', Authentication failure

---

### Post by wzjjanet on 2016-04-29
I don't understand the log, I login as [email]A@MYDOMAIN.COM[/email], but shows the logname=administrator@MYDOMAIN.COM...What this mean?
Thank you

---

