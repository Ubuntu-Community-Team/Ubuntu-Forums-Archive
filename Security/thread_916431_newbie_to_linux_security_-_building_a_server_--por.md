---
title: "newbie to linux security - building a server --portal for internet users"
date: 2008-09-10
forum: Security
---

### Post by adhg on 2008-09-10
I know I'm asking a big question but I'll take the risk...:)


I have a server with ubuntu (8.), the purpose of the server is a website that users request and receive information (50 users of the company all over the US). I have the followings:

1. Mysql 
2. php
3. Apache
4. Tomcat

other service that must be open:
SSH

that’s it!


Since this will be open to the web, I know I should close other ports (ftp,telnet) and Install a firewall.

1. I read about lokkit and it sounds very much simple, is this a good application to use for a server? if not, what is recommended?

2. In what file can I restrict other user to access the application (can I have a range of ips or open very specific ips?


Thank you very much, any other thoughts of how to secure this server would be appreciated.

---

### Post by cariboo on 2008-09-11
You could try using /etc/hosts.allow and /etc/hosts.deny to allow and restrict access. Have a look at this this page

[http://sumith.net/blog/?cat=3&paged=2](http://sumith.net/blog/?cat=3&paged=2)

scroll down to tcpwrappers

Jim

---

