---
title: "postfix, unbound smtp from local server"
date: 2019-01-31
forum: Server Platforms
---

### Post by lister171254 on 2019-01-31
Running a small web app (Nextcloud) and my home mail server on the same box with Unbound DNS Resolver.

Webserver (can access the site), mailserver(can send and receive mail)  and unbound all work.

Found an issue when setting my mail server as the smtp server for Netxcloud. Initially thought that this was a Nextcloud issue, but it's not

pinging my domain from the server translates to 127.0.1.1

Issue is that nothing for that ip address listens on the required port
 ```
sudo netstat -tulpn | grep 587
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      20957/master        
tcp        0      0 173.212.231.229:587     0.0.0.0:*               LISTEN      20957/master        
tcp6       0      0 ::1:587                 :::*                    LISTEN      20957/master        

```

```
telnet smtp.myserver.com 587
Trying 127.0.1.1...
telnet: Unable to connect to remote host: Connection refused

```

Do I need to add something to the postfix config?

Thanks

---

### Post by SeijiSensei on 2019-01-31
Postfix is bound to 127.0.0.1, the traditional localhost address. Ubuntu has taken to assigning the host's own name to 127.0.1.1 (confusing to old hands like me).  What if you try to connect to 127.0.0.1 instead?

If that works, I would edit /etc/hosts to assign your external address the name "smtp.myserver.com" since I assume telnet connections to 173.212.231.229 work correctly, yes?

```

173.212.231.229     smtp.myserver.com 

```

---

### Post by lister171254 on 2019-02-01
Thanks for your help.
That works

---

