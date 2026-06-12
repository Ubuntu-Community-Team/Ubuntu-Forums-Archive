---
title: "configuring an ubuntu 9.10 server LDAP client"
date: 2010-11-17
forum: Server Platforms
---

### Post by bluethundr on 2010-11-17
I am running Karmic 9.10 server and need to setup pam to authenticate
against LDAP.

 Is there an automatic account management tool in ubuntu that is
similar to auth-config under red hat that would allow automatic
configuration of pam to do ldap lookups for it's information?

 I followed the pam ldap wiki on the ubuntu site but no dice.

 I tried to config my pam modules by hand. Here is an example of how I
went about it with my /etc/pam.d/common-auth file:

```

auth    required        pam_group.so use_first_pass
auth    sufficient      pam_ldap.so
auth    required        pam_unix.so nullok_secure use_first_pass
#auth   [success=2 default=ignore]      pam_unix.so nullok_secure
#auth   [success=1 default=ignore]      pam_ldap.so use_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

I also tried using a script called pam-auth-update

My nsswitch is setup correctly, for example:

```

passwd files ldap

```

 and I am using getent passwd | grep test account to find a test
account that lives only in LDAP.


I'd appreciate any help you might have on this topic.

---

### Post by TSJason on 2010-11-18
I believe you're looking for the command "client-auth-config"

I use a file in conjunction with that utility to enable ldap on client workstations. My config file is as follows.

open_ldap:
```
[open_ldap]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: ldap files 
nss_sudoers=sudoers: ldap files
pam_auth=auth       required     pam_env.so
        auth       sufficient   pam_unix.so likeauth nullok
        auth       required     pam_group.so use_first_pass
        auth       sufficient   pam_ldap.so use_first_pass
        auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
        account    sufficient   pam_ldap.so
        account    required     pam_deny.so
pam_password=password   sufficient   pam_unix.so nullok md5 shadow
        password   sufficient   pam_ldap.so use_first_pass
        password   required     pam_deny.so
pam_session=session    required     pam_limits.so
        session    required     pam_mkhomedir.so skel=/etc/skel/
        session    required     pam_unix.so
        session    optional     pam_ldap.so
```

To apply it I use:
```
auth-client-config -a -p open_ldap

```

I'm using 10.04, however. I doubt it would change much between the two versions though.

---

### Post by urbushey on 2010-11-18
I'm having a problem getting a similar system implemented.

I have Active Directory set up on one machine (and I can't really adjust the settings very much) and Ubuntu Server 10.04, which I would like to use as a client.

I followed the directions at [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication), but when I get to 

```
getent passwd
``` 

I don't see anything from the LDAP, and ssh'ing into the box from an LDAP/AD username certainly doesn't work.

In addition, I've attempted to use [Webmin]("http://www.webmin.com/")'s LDAP Configuration module to configure it. I can connect to the server and can browse it with the LDAP browser with my settings, but the Webmin package doesn't recognize the users (which are organized in one of four Organizational Units (OUs) within the OU that I have as my Search Base) as users, i.e. it returns:

```

Searching for users ..
.. no users found under base OU=Office1,OU=All Offices,DC=mycompany,DC=com.

```

Does anyone have any suggestions? I'm not even sure which log files would be relevant.

---

### Post by TSJason on 2010-11-21
It's hard to tell exactly. The /var/log/messages or /var/log/syslog should capture most output - I would look for nss_ldap errors. Here's a little checklist I would go through:

[LIST]
[*]Did you start the nscd service on the client? 
[*]Have you setup your /etc/ldap/ldap.conf file properly? 
[*]I believe I have it linked to /etc/ldap.conf as well - this might be needed for compatibility between applications. 
[*]Are any needed ldap certificates in the proper location and permissions secured?
[*]Did you define the nss attributes for passwd shadow and group in the ldap.conf to your ldap objects?
[*]Does your hostname resolve properly?
[/LIST]

---

### Post by urbushey on 2010-11-21
Thanks for taking the time to respond.

I actually was able to go the lazy route and use likewise-open ([https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)) which is built specifically for authenticating Linux machines to AD domains. The directions there had me up and running in four commands.

---

