---
title: "Ldap: Ssh &amp; pam"
date: 2012-10-31
forum: Server Platforms
---

### Post by Scarex on 2012-10-31
I'm trying to set up a Ubuntu Server 12.04 in order user to login using credentials coming from ActiveDirectory.

I've followed this guide: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) but in the end I failed to make it works.

The problem I experiencing is that pam tries to bind the user against LDAP server making a bindRequest, but if the user is not already a local account, "INCORRECT" password is sent to LDAP server instead of the password provided by the user, failing of course the authentication. (I sniffed the packet using tshark).
On the contrary, if the user is already local (previously added with useradd command), the password is sent correctly and the authentication is made successfully.

This is the auth.log
```
Oct 31 14:10:49 taiba sshd[6620]: Invalid user XXXXXX from 10.XXX.XX.XX
Oct 31 14:10:49 taiba sshd[6620]: input_userauth_request: invalid user XXXXXX [preauth]
Oct 31 14:10:52 taiba sshd[6620]: pam_ldap: error trying to bind as user "XXXX" (Invalid credentials)
Oct 31 14:10:52 taiba sshd[6620]: pam_unix(sshd:auth): check pass; user unknown
Oct 31 14:10:52 taiba sshd[6620]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=XXXXXXXX 
Oct 31 14:10:52 taiba sshd[6620]: pam_ldap: error trying to bind as user "XXXXXXX" (Invalid credentials)
Oct 31 14:10:54 taiba sshd[6620]: Failed password for invalid user XXXXXX from 10.XXX.XX.XX port 51831 ssh2
```

So I realized that the problem is when the account is not present.

Does anyone have a suggestion of what I have to change o modify in order to solve this problem? I can post the content of conf files you think could be useful.

Thank you and best regards :)

---

### Post by Scarex on 2012-11-05
Does anyone have an idea where I can look for a solution?

---

### Post by luvshines on 2012-11-12
> 14:10:49 taiba sshd[6620]: Invalid user XXXXXX from 10.XXX.XX.XX
Does 'id' command for the LDAP username work on your system ?

---

### Post by sandyd on 2012-11-12
> **Scarex said:**
> I'm trying to set up a Ubuntu Server 12.04 in order user to login using credentials coming from ActiveDirectory.

I've followed this guide: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) but in the end I failed to make it works.

The problem I experiencing is that pam tries to bind the user against LDAP server making a bindRequest, but if the user is not already a local account, "INCORRECT" password is sent to LDAP server instead of the password provided by the user, failing of course the authentication. (I sniffed the packet using tshark).
On the contrary, if the user is already local (previously added with useradd command), the password is sent correctly and the authentication is made successfully.

This is the auth.log
```
Oct 31 14:10:49 taiba sshd[6620]: Invalid user XXXXXX from 10.XXX.XX.XX
Oct 31 14:10:49 taiba sshd[6620]: input_userauth_request: invalid user XXXXXX [preauth]
Oct 31 14:10:52 taiba sshd[6620]: pam_ldap: error trying to bind as user "XXXX" (Invalid credentials)
Oct 31 14:10:52 taiba sshd[6620]: pam_unix(sshd:auth): check pass; user unknown
Oct 31 14:10:52 taiba sshd[6620]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=XXXXXXXX 
Oct 31 14:10:52 taiba sshd[6620]: pam_ldap: error trying to bind as user "XXXXXXX" (Invalid credentials)
Oct 31 14:10:54 taiba sshd[6620]: Failed password for invalid user XXXXXX from 10.XXX.XX.XX port 51831 ssh2
```

So I realized that the problem is when the account is not present.

Does anyone have a suggestion of what I have to change o modify in order to solve this problem? I can post the content of conf files you think could be useful.

Thank you and best regards :)
does the server require a bindpw by any chance?

---

