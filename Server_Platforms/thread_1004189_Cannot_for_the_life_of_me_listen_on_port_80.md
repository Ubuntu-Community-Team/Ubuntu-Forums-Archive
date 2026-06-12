---
title: "Cannot for the life of me listen on port 80"
date: 2008-12-07
forum: Server Platforms
---

### Post by codemyster on 2008-12-07
I switched back to Abyss Web Server from Apache simply because of preference. I went through the rigmarole of getting rid of Apache in it's entirety, but for some reason, Abyss will not listen on port 80. I checked with netstat and there doesn't seem to be anything else listening on port 80, so I cannot figure out what is wrong.

Here is the output from netstat:

```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      5775/mysqld     
tcp        0      0 localhost:submission    *:*                     LISTEN      7756/sendmail: MTA:
tcp        0      0 *:9999                  *:*                     LISTEN      7838/abyssws    
tcp        0      0 *:ftp                   *:*                     LISTEN      5932/vsftpd     
tcp        0      0 *:8118                  *:*                     LISTEN      7838/abyssws    
tcp        0      0 localhost:ipp           *:*                     LISTEN      5873/cupsd      
tcp        0      0 localhost:smtp          *:*                     LISTEN      7756/sendmail: MTA:
tcp6       0      0 [::]:5900               [::]:*                  LISTEN      7232/vino-server
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      5651/sshd    

```

As you can see, I'm forced to run Abyss on port 8118, as it won't listen on port 80. Does anyone know what's going on here?

Thanks in advanced.

EDIT: No, Apache is not running. :)

---

### Post by bp1509 on 2008-12-07
d

---

### Post by Dr Small on 2008-12-07
Are you starting the server as root, so it has priviledges to run on port 80?

---

### Post by codemyster on 2008-12-07
> **Dr Small said:**
> Are you starting the server as root, so it has priviledges to run on port 80?

Oh my god. 

I cannot believe I made such a rookie mistake. I guess Apache ran as root automatically, so I kinda took that for granted. Thanks for the help :D

---

