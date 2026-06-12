---
title: "Connection from Ubuntu client to existing LDAP server via SSSD not working"
date: 2021-04-15
forum: Server Platforms
---

### Post by petyb on 2021-04-15
Hello friends,

I'd like to ask you for a help. I'm facing the strange behavior...

I need to connect one Ubuntu server (20.04 LTS) to the existing LDAP server. 
I've followed this tutorial: [https://kifarunix.com/configure-sssd-for-ldap-authentication-on-ubuntu-20-04/](https://kifarunix.com/configure-sssd-for-ldap-authentication-on-ubuntu-20-04/)
But can't manage it like that in my case :(

There shouldn't be a problem with LDAP server, since I'm able to connect to it from RHEL servers without any problems..

**What I tried already:**
1. **SSSD** configured **without TLS** -> I can see the users from LDAP, but impossible to login via SSH 
```

root@infra4:~# id pbarczi
uid=208973(pbarczi) gid=44346(SK001852) groups=44346(SK001852)
root@infra4:~# ssh pbarczi@localhost
pbarczi@localhost's password:
Connection closed by 127.0.0.1 port 22

```

2. **SSSD** configured **with TLS** -> I can not even see the LDAP users, seems like issue with TLS, can not download certificate from LDAP server:
```

root@infra:~# openssl s_client -connect 160.118.26.136:389 -starttls ldap -showcerts < /dev/null | openssl x509 -text | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p'
write:errno=0
unable to load certificate
140532498875712:error:0909006C:PEM routines:get_name:no start line:../crypto/pem/pem_lib.c:745:Expecting: TRUSTED CERTIFICATE

```

When I try the same from RHEL client, there is no such problem.. Login **[COLOR=#008000]successful[/COLOR]** (both without TLS + with TLS)


Any idea what could cause such problems?

Many thank in advance!
Peter

---

### Post by TheFu on 2021-04-15
The root account is never, ever, allowed to use remote credentials.

If you run **getent passwd pbarczi**,. does that work?
What about **sudo getent shadow pbarczi**?

I've never used sssd to connect to LDAP. Always just configured PAM to point at the LDAP POSIX scheme. But with ssh, we don't allow password-based logins after the first 5 minutes.  From that point on, they are required to use ssh-keys or ssh-certs.

I doubt any of this will be helpful. Sorry.

---

### Post by petyb on 2021-04-15
I've tested it also via other local non-root account, but still the same.
Yes, the getent passwd works..

We just use only SSSD in order to authenticate towards LDAP, it works like a charm on RHEL servers, but in this case we need to connect Ubuntu..

Never mind, thanks for your post..

---

