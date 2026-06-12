---
title: "Deny ldap users the abitiy to log-in to the physical machine locally?"
date: 2014-08-26
forum: Server Platforms
---

### Post by richard51 on 2014-08-26
Is it possible to allow ldap users access to my **NFS** server (*auto-mounts*) but deny ldap users the ability to log-in to the physical machine locally?

Currently to allow ldap users access to the shares on my NFS server, and to map the ldap users correctly, I have installed the following packages on the NFS server: **ldap-auth-client, libpam-krb5, krb5-user & libsasl2-modules-gssapi-mit.**

I also created the following auth-client-config file to update both **pam** and **nsswitch**:```
[krb_ldap]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: ldap
pam_auth=auth      sufficient   pam_krb5.so
    auth       sufficient   pam_unix.so use_first_pass
    auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
    account    sufficient   pam_krb5.so
    account    required     pam_deny.so
pam_password=password   sufficient     pam_unix.so nullok obscure md5
    password   sufficient   pam_krb5.so use_first_pass
    password   required     pam_deny.so
pam_session=session    required     pam_unix.so
```This allows ldap clients to authenticate with **Kerberos** and auto-mount the **NFS** shares, but also allows ldap users to log-in to the physical machine locally (*which I don't want*).

Is there a way to stop ldap users from logging-in to the physical machine locally? Maybe a nsswitch.conf edit that still uses the ldap users and groups databases, but prevents log-in?

---

### Post by cj13579 on 2014-08-26
Could you change the LDAP users shell to be /bin/false. This *I think* should prevent people from being able to login to the system but should allow authentication for NFS and other services to happen.

```
sudo usermod -s /bin/false ldap_user
```

---

### Post by richard51 on 2014-08-27
Hi Chris,

  	 	 	 	   Changing the login shell on a per user basis isn't feasible for all my ldap users. I don't believe it's possible to use the **-s** switch on a group either? I could use **ldapscripts** to set the default login shell for new users, but this would effect all machines, also not feasible.

---

### Post by cj13579 on 2014-08-27
I found [this post]("http://serverfault.com/questions/133983/override-ldap-shell") which suggests that you could edit /etc/ldap.conf with the below line to file which would override the shell value stored in LDAP for just that particular machine:

```
nss_override_attribute_value loginShell /bin/false
```

---

### Post by richard51 on 2014-08-27
> **cj13579 said:**
> I found [this post]("http://serverfault.com/questions/133983/override-ldap-shell") which suggests that you could edit /etc/ldap.conf with the below line to file which would override the shell value stored in LDAP for just that particular machine:

```
nss_override_attribute_value loginShell /bin/false
```

I edited the **/etc/ldap.conf** file, adding the above line, unfortunately this didn't work... BUT, I have **sudo_ldap** installed which defaults to using **/etc/ldap/ldap.conf**, and adding the above line to that file, does work! Strangely though, it accepts the log-in, then denies you access and logs you out.

Even though, the above post **does** answer my question... is there a way to allow a ldap group (*say ldapadministrator*) to login, but still deny the other ldap groups and users? ;)

---

### Post by cj13579 on 2014-08-27
> **richard51 said:**
> I Strangely though, it accepts the log-in, then denies you access and logs you out.

That is the expected behaviour. You have technically authenticated successfully, but as you have don't have a real shell (/bin/false) a session can't be started and you are logged out.

It may be better in this situation to change */bin/false* to */sbin/nologin*. You will get the same behaviour: successfully authenticate, then logout, but with /sbin/nologin you will be able to present a friendly notice saying "This account is not available". Also, you can customise this using the */etc/nologin* file.

---

### Post by cj13579 on 2014-08-27
Also, sorry, no idea about how do the above on a per-group basis!

---

### Post by richard51 on 2014-08-27
> **cj13579 said:**
> Also, sorry, no idea about how do the above on a per-group basis!

Not a problem, you have been more than helpful... Thanks ):P

---

