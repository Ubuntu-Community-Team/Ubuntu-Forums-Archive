---
title: "Squid ncsa_auth not working"
date: 2013-05-11
forum: Server Platforms
---

### Post by umfunix on 2013-05-11
Please help....  I've added the following configurations to my /etc/squid3/squid.conf file.  I'm using Ubuntu server 12.04 32bit and installed squid and dansguardian.  I have not yet configured anythong on dansguardian.

First I've created a passwd file

```
htpasswd /etc/squid/squid_passwd myname
New password: Re-type new password: 
```
I then added this to the auth_param section of squid.conf
```
auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/squid_passwd 
```

And to the bottom of the ACL section...
```
acl ncsa_users proxy_auth REQUIRED 
```

And to the top of the http_access section
```
http_access allow ncsa_users 
```

Before I used the ncsa_auth option, my squid worked like a charm from clients.

Since the auth_param, I don't get access from clients, which I understand, but I do not get the option to insert a username and password.
```
The client response in firefox is: The procy server us refusing connections.  Firefox is configured to use a proxy serer that is refusing connections. 
```

Why?  Do I still miss something?

Thanks

---

### Post by umfunix on 2013-05-15
Solved it!

---

