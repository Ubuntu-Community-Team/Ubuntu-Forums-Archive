---
title: "Bind - Loading master file - file not found"
date: 2014-09-25
forum: Server Platforms
---

### Post by scojopa on 2014-09-25
I just setup my first ubuntu server and am learning linux. when I setup the server I called it server01 and no domain was configured. 

I am trying to setup bind. I have configured my zone and reverse lookup in named.conf.local but there are no master zone or reverse zone files created? What do i have to do for the server to create the mater file it is looking for - running 14.04 bind9



Sep 25 13:41:27 boss named[1020]: loading configuration from '/etc/bind/named.conf'
Sep 25 13:41:27 boss named[1020]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Sep 25 13:41:27 boss named[1020]: set up managed keys zone for view _default, file 'managed-keys.bind'
Sep 25 13:41:27 boss named[1020]: zone 5.168.192.in-addr.arpa/IN: loading from master file var/lib/bind/5.168.192.rev failed: file not found
Sep 25 13:41:27 boss named[1020]: zone test.com/IN: loading from master file var/lib/bind/test.com.hosts failed: file not found
me@boss:~$ 



Thanks - Scott

---

### Post by scojopa on 2014-09-25
I can reload bind9 without error but var/lib/bind does not have any master file  - I have configured the zones in named.conf.local - 

> Does bind need permissions to /var/lib/bind/ currently it is owned by root?

Sep 25 16:30:59 boss named[1024]: using default UDP/IPv6 port range: [1024, 65535]
Sep 25 16:30:59 boss named[1024]: sizing zone task pool based on 7 zones
Sep 25 16:30:59 boss named[1024]: reloading configuration succeeded
Sep 25 16:30:59 boss named[1024]: reloading zones succeeded
Sep 25 16:30:59 boss named[1024]: zone domain.com/IN: loading from master file var/lib/bind/domain.com.hosts failed: file not found
Sep 25 16:30:59 boss named[1024]: zone domain.com/IN: not loaded due to errors.
Sep 25 16:30:59 boss named[1024]: zone 5.168.192.in-addr.arpa/IN: loading from master file var/lib/bind/5.168.192.rev failed: file not found
Sep 25 16:30:59 boss named[1024]: zone 5.168.192.in-addr.arpa/IN: not loaded due to errors.
Sep 25 16:30:59 boss named[1024]: all zones loaded

---

### Post by Doug S on 2014-09-25
> **scojopa said:**
> I am trying to setup bind. I have configured my zone and reverse lookup in named.conf.local but there are no master zone or reverse zone files created? What do i have to do for the server to create the mater file it is looking for - running 14.04 bind9The server doesn't create those files, you do.
What are you using as a reference? I would suggest the [Ubuntu serverguide]("https://help.ubuntu.com/14.04/serverguide/dns-configuration.html").
Please post your named.conf.local file.

---

### Post by scojopa on 2014-09-26
Yes I figured it out - basically out of frustration - and then realized in linux world get used to doing it yourself... thats the whole point isn't it.

---

