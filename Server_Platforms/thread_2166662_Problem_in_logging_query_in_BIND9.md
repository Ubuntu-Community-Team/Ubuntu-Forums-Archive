---
title: "Problem in logging query in BIND9"
date: 2013-08-10
forum: Server Platforms
---

### Post by Profark on 2013-08-10
I have successfully installed DNS and DHCP servers on same Ubuntu machine. It is working fine and logging queries. But I mistakenly restart the server. After login i have noticed that my queries are not logging. /var/log/my_logs/default.log. After some research I entered the command 

```
sudo rndc querylog
```
Ya ya it's working again. 

[B][SIZE=3]Now my question is
[/SIZE][/B]
**Is there any method that, it start logging query automatically after when server restart. **

---

### Post by bsamim on 2013-08-11
I believe this post will answer your questions.
 
[http://stackoverflow.com/questions/11153958/how-to-enabled-named-bind-dns-full-logging](http://stackoverflow.com/questions/11153958/how-to-enabled-named-bind-dns-full-logging)

---

