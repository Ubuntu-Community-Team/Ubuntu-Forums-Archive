---
title: "MySQL Help"
date: 2006-03-07
forum: Server Platforms
---

### Post by ClareJonsson on 2006-03-07
I know that MySQL is set only to respond to localhost, is there any way to get it to respond to external requests? If so, can I limit the IP addresses it reponds to?

---

### Post by gmclachl on 2006-03-07
I am not a MySQL expert but we use a couple of development servers in the office. In order to connect to them from other machines. We simply use 

   GRANT [WHATEVER] ON [SOMEDB] TO username@ipaddress identifed by "password"; 

 Where ipaddress is the one of the machine with which you wish to connect to MySQL with. You can also use the % wildcard, but i wouldn't recommend that (but that's just me)

George

---

### Post by gertmul on 2006-03-07
I had to change a line in the /etc/mysql/my.cnf file from

```
bind-address  = 127.0.0.1
```

to the ipaddress of the machine

```
bind-address  = 192.168.10.6
```

Remeber to do 

```
/etc/init.d/mysql restart
```

after the change.

---

