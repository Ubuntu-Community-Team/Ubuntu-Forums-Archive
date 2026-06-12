---
title: "netstat -lt suddenly gots very slow today"
date: 2011-02-16
forum: Server Platforms
---

### Post by psvr on 2011-02-16
I typed 'netstat -lt' as usual today  but this time , very strangely,  after output all the normal tcp sections, it halts before outputing any 'tcp6' section.

Here it goes

```

psvr@localhost:/var/www$ netstat -lt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:mysql                 *:*                     LISTEN     
tcp        0      0 *:git                   *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 *:http-alt              *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:smtp          *:*                     LISTEN     
tcp        0      0 *:https                 *:*                     LISTEN     
tcp        0      0 *:33                    *:*                     LISTEN     
tcp        0      0 *:11300                 *:*                     LISTEN     
tcp        0      0 *:8901                  *:*                     LISTEN     
tcp        0      0 localhost:60102         *:*                     LISTEN     
tcp        0      0 *:8808                  *:*                     LISTEN    

```

this is where it halts, and after almost 20sec, it finally outputs the last 2 lines
```

tcp6       0      0 [::]:git                [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN   

```

This really confused me because netstat was really fast before. The only thing that I have done that is network related is to change my static eth1 from 192.168.1.* to 192.168.2.*, does that has anything to do with this? Morover,  If not useing '-t' option, everything outputs in a single instant, so maybe something wrong with things that relate to the -t option?

Thank you very much

---

### Post by psvr on 2011-02-16
i figured it out.  I forgot to modify /etc/resolv.conf to set 192.168.1.1 to the new 192.168.2.1

seems like somewhere during netstat -tl process  the dns server is queried for a address to text transformation.

---

### Post by jpl888 on 2011-02-16
Yeah netstat will pause like that if there are any issues resolving the DNS name of the machine you're running it on.

---

### Post by elico on 2011-02-16
dns dns dns..
use the 
netstat -nlt to make it quicker (cause who needs dns resolution?)

---

### Post by jpl888 on 2011-02-17
Nice tip. I didn't know that one. Guess that's why they say RTFM :)

---

