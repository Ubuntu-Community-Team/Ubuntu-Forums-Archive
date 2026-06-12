---
title: "vsftpd problem : can't login with some users"
date: 2005-05-24
forum: Server Platforms
---

### Post by doni on 2005-05-24
hi there

i've installed vsftpd after this howto [http://www.debianhowto.de/howto-archiv/de/vsftpd/installation_konfiguration.html](http://www.debianhowto.de/howto-archiv/de/vsftpd/installation_konfiguration.html) 

now i'm having two problems
[list=1]
[*]I can't login with the user created with the addftpuser script. even tough he is in the user_allow file
[*]I can't login over the internet. Even with the user that it works locally (i havent created him with the addftpuser script)....shouldn't be  a problem of port forwarding, because port forwarding for port 80, 22 and 23 do work!
[/list] 

if i try to login over internet it looks like this
```
#ftp castilio.homelinux.org
Connected to castilio.homelinux.org
``` 

and after some time

```
421 Service not available, remote server has closed connection.
``` 

i don't even get to the login prompt...

any ideas?

thanks 
doni

---

### Post by LanceRushing on 2006-02-02
Same problem

Check your /etc/passwd make sure the users have a valid shell.

After much hair pulling, and trying proftpd with the same results, I noticed proftpd gave me an error in /var/log/auth about an invalid shell.  This error didn't show with vsftpd.

---

### Post by deBaas on 2006-02-02
It apears your behind a router or firewall. If so, did you forward the right ports? Port 21 and the ports in you passiveport range. And is your server aware of your outside IP?

P.S. a valid shell is not needed.

---

