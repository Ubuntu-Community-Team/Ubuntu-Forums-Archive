---
title: "Samba using ONLY tcp6 (IPV6) fail"
date: 2012-10-31
forum: Server Platforms
---

### Post by mbuell on 2012-10-31
I think I have a problem with samba trying to use ONLY IPV6, and refusing connections because of it. Read on.

Over the past few months I have had a "connection refused" problem between my client machines and my home server [Ubuntu 10.04]. I somehow managed to get it back running each time. At one point, I thought it was something weird with the samba.conf, and I was making tweaks. But now I think that it was shutting things down and turning them back on until it worked. 

As a result of Hurricane Sandy, I powered everything down. On restoring power, the problem occurred. Since I had already tweaked the samba config, I went looking elsewhere and found this VERY odd (to me) result:

```
mark@ubuntu-server:~$ sudo netstat -apn | grep LISTEN | grep smb
[sudo] password for mark: 
tcp6       0      0 fe80::20c:f1ff:fe7f:445 :::*                    LISTEN      1169/smbd       
tcp6       0      0 fe80::20c:f1ff:fe7f:139 :::*                    LISTEN      1169/smbd       
```

This didn't seem like it should be. Only tcp6? I stopped and restarted Samba. Same results. ```
mark@ubuntu-server:~$ sudo netstat -apn | grep LISTEN | grep smb
tcp6       0      0 fe80::20c:f1ff:fe7f:445 :::*                    LISTEN      1169/smbd       
tcp6       0      0 fe80::20c:f1ff:fe7f:139 :::*                    LISTEN      1169/smbd   
```

But, since the process # was the same, I think for some reason it did not properly stop and restart. IDK.

So I stopped and started the server.  
Logged back in, and then restarted samba. This time, I got:```
mark@ubuntu-server:~$ sudo netstat -apn | grep LISTEN | grep smb
tcp        0      0 172.16.0.104:445        0.0.0.0:*               LISTEN      2456/smbd       
tcp        0      0 172.16.0.104:139        0.0.0.0:*               LISTEN      2456/smbd       
tcp6       0      0 fe80::20c:f1ff:fe7f:445 :::*                    LISTEN      2456/smbd       
tcp6       0      0 fe80::20c:f1ff:fe7f:139 :::*                    LISTEN      2456/smbd       
```

That looked better, and it worked better. Now all the machines are connecting again. 

What is going on with Samba? Why is it trying to use only IPV6 addresses? And what should I do to prevent this?

---

### Post by lemming465 on 2012-11-01
What's your samba version?  (e.g. run *testparm --version*).  I think this might be more of an issue at 3.5.8 and below.

---

### Post by mbuell on 2012-11-01
3.4.7

Have you heard of Samba doing this? I didn't find any reference to it - I found lots of reference to error 111, connection refused, but that is a completely different animal.

---

### Post by lemming465 on 2012-11-02
There were some occasional references to such problems in a web search I did; most of my actual samba servers are redhat rather than ubuntu and IPv4 only, so I haven't run into the problem personally.  The most typical workaround suggested was to be explicit about interfaces and v4 addresses, e.g. to adjust /etc/samba/smb.conf with:```
bind interfaces only
interfaces 127.0.0.1 www.xxx.yyy.zzz

```
The general advice to people who actually want to use IPv6 with Samba seems to be doing that from version 3.6 or higher.

---

### Post by mbuell on 2012-11-02
Thanks. I don't want the IPv6 addies. No need for them - this is an internal server. So I'll check the samba conf and update as you suggest. The problem has been intermittent - which itself is weird and points to some bug. Anyway, at least now I have some idea of what is going on when this happens. It may not be "solved" yet - but I know more than I did!

---

### Post by lemming465 on 2012-11-02
> I don't want the IPv6 addies
Then **sysctl -w net.ipv6.conf.all.disable_ipv6=1** might be your friend.

Dual-stack applications which bind() sockets with address family AF_INET6 but without setsockopt() option IPV6_IPV6ONLY can do mapped IPv4 (0::FFFF:a.b.c.d/128 ) from their v6 socket as well as native IPv6 (2000::/3)  A buggy dual-stack samba might be trying to do that, but failing.

---

