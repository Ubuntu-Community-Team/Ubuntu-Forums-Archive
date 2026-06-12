---
title: "sudo netstat -ptvnl"
date: 2012-07-17
forum: Security
---

### Post by gabmuks on 2012-07-17
I found this command in a thread in this forum's security section.

I ran it on my computer and here is results....


```
liz@liz:~$ sudo netstat -ptvnl
[sudo] password for liz: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1085/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      816/cupsd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      816/cupsd       
liz@liz:~$ 
```


I am concerned about the "dnsmasq".



This is from the thread I was reading....

Comment:
[I][COLOR="Purple"]In order for a rootkit to be useful it has to establish a remote connection to a host to
upload the stealer (iStealer, etc) and keylogging logs; usually though FTP so all you have
to do is run netstat checks periodically to identify unknown remote connections. Your
output shows that you have a mail client and a printer client listening, which is expected.
You're mostly interested in outbound connections to any *.no-ip.org or *.dyndns.org
address. The vast majority of trojans use these dynamic dns services to transmit the
keylogger logs.[/COLOR][/I]


Is the dnsmasq a problem?

Sorry for this post. I just did some research online and answered my question.

Please forgive my ignorance.

---

### Post by thanyawzinmin on 2012-07-18
Yes I also kinda have same concern.;)

---

### Post by CharlesA on 2012-07-18
dnsmasq is not a problem unless you are having problems with name resolution. 
See here:
[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

