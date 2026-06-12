---
title: "Need Assistance Setting Up A Central Syslog Server"
date: 2009-12-08
forum: Server Platforms
---

### Post by NoSalt on 2009-12-08
Hello All

    I am running several Ubuntu 9.10 servers. I would like to dedicate a single server to be a centralized Syslog server so that I can use Splunk. I have done some Googling to see if I could find any tutorials I could follow, but they all seem to be like the following:

[http://news.softpedia.com/news/Setting-Up-a-Central-Syslog-Server-44063.shtml](http://news.softpedia.com/news/Setting-Up-a-Central-Syslog-Server-44063.shtml)

That tutorial talks about ```
/etc/init.d/sysklogd
``` but the only entries in ```
/etc/init.d
``` I can find are **rsyslog** entries

Does anybody know if there is a current how-to on this topic?

Thanks for reading, and have a great day.  :)

---

### Post by de0xyrib0se on 2009-12-08
Ubuntu (currently) is using rsyslog, all it takes to make it central is to enable TCP/IP within the config (/etc/rsyslog.conf) as such;

```
$InputTCPServerRun 514
$AllowedSender TCP, 127.0.0.1, 192.168.100.0/24

$UDPServerRun 514
$AllowedSender UDP, 127.0.0.1, 192.168.100.0/24
```

As for the senders, well thats pretty easy; within their /etc/syslog.conf insert the following line at the top;

 ```
*.*;mail.none   @192.168.100.55
```

If they use rsyslog then alter the rsyslog config.

The rest (as well as this) is in the man page for rsyslog (quite powerful as it can write to an array of databases).

---

### Post by NoSalt on 2009-12-08
de0xyrib0se

Thanks for the info ... I believe it works now. The only issue now is that I believe there are permission problems but I think I may be able to take care of that with the command:

```
iptables -I INPUT -p udp -i eth0 -s 192.168.1.2 -d 192.168.1.1 --dport 514 -j ACCEPT
```

I'll give it a try and report back in the morning.


Thank you again for reading and replying. Have a good one.  :)

---

### Post by NoSalt on 2009-12-09
Yep ... the IPTables rules seems to have fixed it up for me. Thank you all for reading.  :)

---

