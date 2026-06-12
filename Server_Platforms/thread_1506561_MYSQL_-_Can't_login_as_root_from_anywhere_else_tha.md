---
title: "MYSQL - Can't login as root from anywhere else than localhost"
date: 2010-06-10
forum: Server Platforms
---

### Post by nikomo on 2010-06-10
When I try to access the root user on my homeserver on MySQL I get this:
1045 -  Access denied for user 'root'@'192.168.0.110' (using password: YES)

I can login from a user I made but I get an error when I try to login as root.

I know this is a typical safety feature (disallow logins to root from outside localhost to enhance security) but my Google-fu failed me and I can't remember how to disable it.



Edit:

I somehow magically managed to fix it.
I installed webmin and played around with it for a while and noticed you can control the MySQL server with it. Went on, user permissions, created a user called root with hosts as Any and selected all permissions and I managed to log on the server.

---

