---
title: "Closing java ports"
date: 2010-08-20
forum: Server Platforms
---

### Post by fenrisW0lf on 2010-08-20
Hi all,

I ran this command:
```
sudo netstat -tupl
```And it spit out this:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      780/mysqld
tcp        0      0 *:www                   *:*                     LISTEN      795/apache2
tcp        0      0 *:ssh                   *:*                     LISTEN      683/sshd
tcp6       0      0 [::]:xmpp-client        [::]:*                  LISTEN      731/java
tcp6       0      0 [::]:5223               [::]:*                  LISTEN      731/java
tcp6       0      0 [::]:5229               [::]:*                  LISTEN      731/java
tcp6       0      0 [::]:7443               [::]:*                  LISTEN      731/java
tcp6       0      0 [::]:xmpp-server        [::]:*                  LISTEN      731/java
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      683/sshd
tcp6       0      0 [::]:7070               [::]:*                  LISTEN      731/java
tcp6       0      0 [::]:7777               [::]:*                  LISTEN      731/java
tcp6       0      0 [::]:9090               [::]:*                  LISTEN      731/java
tcp6       0      0 [::]:9091               [::]:*                  LISTEN      731/java
udp        0      0 *:mdns                  *:*                                 651/avahi-daemon: r
udp        0      0 *:60412                 *:*                                 651/avahi-daemon: r
udp        0      0 *:bootpc                *:*                                 577/dhclient3
```I was wondering how to close all ports that the java service was listening on except for xmpp-client and xmpp-server as I have openfire running to service jabber IM?

I am running ubuntu server lucid lynx.

Thanks!

---

### Post by spynappels on 2010-08-20
Are you using IPv6? All the Java instances are running on IPv6 so if you do not have it active, there should be no problem.

---

### Post by cdenley on 2010-08-20
The same process (PID 731) is listening for connections on all those ports. If you don't want to listen on those ports, then you either have to configure that process not to, or stop the process from running. Or you could just filter those ports with a firewall, but you shouldn't run a server if you can't even control what ports it listens on.

---

### Post by fenrisW0lf on 2010-08-21
I am not running ipv6 but am annoyed that I can't figure out how to tell the java process to stop listening.

> **cdenley said:**
> <snip> but you shouldn't run a server if you can't even control what ports it listens on.

cdenley, thanks for the enthusiasm - my firewall filters those ports just fine. It is a personal server that I use to learn with, hence the question. I was wondering about information on how to close those ports (or at least where to look) and I thought that this was the right place to ask. I guess not...

---

### Post by cdenley on 2010-08-22
> **fenrisW0lf said:**
> cdenley, thanks for the enthusiasm - my firewall filters those ports just fine. It is a personal server that I use to learn with, hence the question. I was wondering about information on how to close those ports (or at least where to look) and I thought that this was the right place to ask. I guess not...

Well, you never even told us what the java process is, so how can we tell you how to configure which ports it listens on? There is no universal way to tell a process to stop listening on a particular port. You typically edit a configuration file for that specific application, then the application chooses which ports to listen on based on that configuration. You may be able to create an apparmor rule to restrict the process from listening on a particular port, but if that is possible, I suspect it would cause your java application to fail to start after it fails to listen on that port.

---

