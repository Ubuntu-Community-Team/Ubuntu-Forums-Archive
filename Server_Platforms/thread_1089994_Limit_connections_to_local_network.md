---
title: "Limit connections to local network"
date: 2009-03-07
forum: Server Platforms
---

### Post by chowse on 2009-03-07
Hi,
I have services listening for connections from any host:

charles@shemp:~$ netstat -ant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.254.5:22        192.168.254.3:52207     ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     

How can I limit those connections to local network hosts only?
i.e.: 192.168.254.0/24

Thanks,
Charles

---

### Post by mrsteveman1 on 2009-03-07
You could edit the config files for the individual services so that they only respond to requests from local IP addresses, or you could use the hosts.allow and hosts.deny files but thats a bit much.

If you have a firewall and the ports aren't forwarded you shouldn't have a problem with outsiders gaining access to those services.

---

### Post by chowse on 2009-03-08
> **mrsteveman1 said:**
> You could edit the config files for the individual services so that they only respond to requests from local IP addresses, or you could use the hosts.allow and hosts.deny files but thats a bit much.

If you have a firewall and the ports aren't forwarded you shouldn't have a problem with outsiders gaining access to those services.

Hi, thanks for the reply.
hosts.allow and hosts.deny isn't a bad idea.  I may resort to that if I get a headache. ;)

After over half a day I finally have ProFtpd behaving properly.
Still working on OpenSsh and Dovecot.

I do in fact have a home router, and am not forwarding those ports, but prefer the extra layer of security.  Seems like I've heard sob stories of those routers being hacked...?

---

### Post by Dr Small on 2009-03-08
> **chowse said:**
> I do in fact have a home router, and am not forwarding those ports, but prefer the extra layer of security.  Seems like I've heard sob stories of those routers being hacked...?
Yup, for those who allow remote administration with default usernames/passwords.

---

