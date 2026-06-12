---
title: "Apache unable to bind to port"
date: 2012-02-02
forum: Server Platforms
---

### Post by vuetrip on 2012-02-02
Hi folks, anyone have any ideas in this case:

var/log/apache2/error.log:
```
(98)Address already in use: make_sock: could not bind to address 192.168.0.2:80
no listening sockets available, shutting down
Unable to open logs
```


sudo netstat -tulpn:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      973/mysqld      
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      731/dovecot     
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      731/dovecot     
tcp        0      0 192.168.0.2:53          0.0.0.0:*               LISTEN      755/named       
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      755/named       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1086/cupsd      
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1060/master     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      755/named       
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      731/dovecot     
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      731/dovecot     
tcp6       0      0 :::110                  :::*                    LISTEN      731/dovecot     
tcp6       0      0 :::143                  :::*                    LISTEN      731/dovecot     
tcp6       0      0 :::21                   :::*                    LISTEN      2233/proftpd: (acce
tcp6       0      0 :::53                   :::*                    LISTEN      755/named       
tcp6       0      0 ::1:631                 :::*                    LISTEN      1086/cupsd      
tcp6       0      0 ::1:953                 :::*                    LISTEN      755/named       
tcp6       0      0 :::993                  :::*                    LISTEN      731/dovecot     
tcp6       0      0 :::995                  :::*                    LISTEN      731/dovecot     
udp        0      0 192.168.0.2:53          0.0.0.0:*                           755/named       
udp        0      0 127.0.0.1:53            0.0.0.0:*                           755/named       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1939/dhclient   
udp        0      0 0.0.0.0:49877           0.0.0.0:*                           485/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           485/avahi-daemon: r
udp6       0      0 :::53                   :::*                                755/named       
udp6       0      0 :::56968                :::*                                485/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                485/avahi-daemon: r

```

I have checked /etc/apache2/ports.conf and there is only the "listen 80" and the if:listen 443 directives.

What could be in the way of apache binding?

---

### Post by Gibbs on 2012-02-02
> Unable to open logs

Are you sure this isn't a permissions related issue? It might be failing to actually create the socket as opposed to it already being in use.

---

### Post by SeijiSensei on 2012-02-02
Do you have any iptables rules on this machine?  If so, are you certain there's a rule permitting traffic to 192.168.0.2 on port 80?  If iptables doesn't permit traffic to that IP/port combination, Apache won't bind to it.

---

### Post by Dangertux on 2012-02-02
> **SeijiSensei said:**
> Do you have any iptables rules on this machine?  If so, are you certain there's a rule permitting traffic to 192.168.0.2 on port 80?  If iptables doesn't permit traffic to that IP/port combination, Apache won't bind to it.

Umm no. (see attachment)

I agree that you have a permissions problem , what user/group is apache running as?

It is important to understand that iptables does not restrict access to the socket file itself.

---

### Post by SeijiSensei on 2012-02-03
> **Dangertux said:**
> Umm no. (see attachment)

I fail to see what that attachment is supposed to show.  The error reported there isn't the one the OP reports.  Also that example binds to localhost, not to an IP with an external address.

I'm speaking from experience here, Dangertux.  If there's an iptables rule that blocks port 80 on a particular interface, you'll get the error the OP reports.  That may not be the reason in his case, but it is one possible reason for the error.

---

### Post by Dangertux on 2012-02-03
> **SeijiSensei said:**
> I fail to see what that attachment is supposed to show.  The error reported there isn't the one the OP reports.  Also that example binds to localhost, not to an IP with an external address.

I'm speaking from experience here, Dangertux.  If there's an iptables rule that blocks port 80 on a particular interface, you'll get the error the OP reports.  That may not be the reason in his case, but it is one possible reason for the error.

It doesn't matter by your logic it would not be able to bind to any address (from those rules). You are correct in saying traffic wouldn't occur but you can set it however you want.

 As I said before, iptables can not and will not affect the socket file. It's a permissions problem.

I'm sorry you're incorrect in this case, test it yourself if you don't believe me.

---

### Post by vuetrip on 2012-02-03
this machine is only on the local network as a dev machine for my websites so i haven't setup iptables on it and the user/group is still the default, any further help is greatly appreciated.

---

### Post by Dangertux on 2012-02-03
could you post the output of 

```

ps -ef | grep apache2

```

---

### Post by vuetrip on 2012-02-04
Hi folks,

finally got to the bottom of this, some of the php software that i've been trying out has added itself a conf file in /etc/apache2/sites-enabled and as part of that conf said "listen 192.168.0.2:80" so duplicating the default config's listen statement, which as soon as i deleted the second listen statement and restarted apache it works.

note for future self: check sites-enabled!

Thanks for all the help offered!

Craig.

---

