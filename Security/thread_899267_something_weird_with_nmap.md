---
title: "something weird with nmap"
date: 2008-08-24
forum: Security
---

### Post by thehungrylobster on 2008-08-24
Hello , i am starting a server and noticed something wrong : 


```
# nmap -p 5432 XXX.XX.XXX.XXX
	PORT     STATE  SERVICE
	5432/tcp closed postgres

# nmap -p 5432 localhost 
	PORT     STATE SERVICE
	5432/tcp open  postgres

# netstat -an | grep "LISTEN " 
tcp        0      0 127.0.0.1:5432  0.0.0.0:*   LISTEN

```


What should I do to make port 5432 OPEN on the server IP ?

---

### Post by rogeriopvl on 2008-08-24
Your netstat output command tells that postgres is only listening for connections locally.

What ip address are you giving to nmap? local? or a public one?

Try this:```
nmap -p 5432 localhost
```

It should show up now as open.

---

### Post by thehungrylobster on 2008-08-25
Hi rogeriopvl, you are just stating something i wrote :)
This is in fact a PostgreSQL pg_hba.conf problem, as I am trying to conect from home and found my own IP has changed ..

---

### Post by rogeriopvl on 2008-08-25
Exactly I just answered according to thread's title :)

It's definitely a postgreSQL config problem. Have you configured to listen connections from outside?

What do you mean by "your own ip has changed"? the server's ip? or the client's ip?

---

