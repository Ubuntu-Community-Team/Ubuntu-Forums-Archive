---
title: "Help configuring something on MySQL"
date: 2008-11-20
forum: Server Platforms
---

### Post by Mamsaac on 2008-11-20
So, I would like to change a little my.cnf, but there seems to be a problem.

I need to allow external connections inside a wireless LAN, since I got other CPU's in my home which run some heavy scripts and access a database that is located in my laptop, and thus I changed my.cnf adding the next line:

bind-address		= 192.168.0.12

Now, that's very simple and works. Problem is, I'm a college student, and thus I use my laptop in many places. Whenever I am not in my apartment, the local IP is different (obviously... unless it was a strange coincidence) and then MySQL doesn't load.

So, for now, I just comment the line and restart the server, which of course works, but I would like to know if there's a way to make it automatic so I don't have to be changing it all the time.

Thanks in advance for the help =)

---

