---
title: "sshd - over internet"
date: 2005-11-14
forum: Server Platforms
---

### Post by edwardexe on 2005-11-14
I've exposed sshd on an ubuntu server in my dmz to the Internet.  I'm having a problem getting ssh to authenticate.  I beleive the problem is the ssh daemon doesn't like that I'm connecting from another alias so it is disallowing the connection.  I can't figure out how to adjust the settings though.


My config:
ubuntu 192.168.x.2
external dns [www.domainname.com](www.domainname.com) is IP 24.x.x.x and translates to 192.168.x.2 which is ubuntu server fqdn ubuntu.internal.com


When connecting, ssh appends a suffix to the account name, ex. logging in as admin to server [www.domainname.com](www.domainname.com) will result in an ssh login id of [email]admin@www.domainname.com[/email].  This login ID is rejected whereas admin@192.168.x.2 or [email]admin@ubuntu.internal.com[/email] is accepted.

I'm guessing I need an entry in the sshd_config, but I haven't had luck.  Anyone have an idea here?

Thanks

---

### Post by nagilum on 2005-11-14
I don't know of any specific configuration option for this. I'm running a similar setup, an external domain and my router forwards all SSH connections to an internal machine in my DMZ. I can login without any problems.
Can you describe how exactly you are trying to login? I didn't fully understand what you meant with the different login-ID.

---

