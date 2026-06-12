---
title: "Bind9 and NSUpdate problem"
date: 2008-07-30
forum: Server Platforms
---

### Post by WickedImp on 2008-07-30
Hey there and greetings to the community!

I use Ubuntu 8.04 on an old AMD Athlon. It's both Desktop and Domain Controller. The goal was to have a PDC and WINS running with Samba (no problem at all) and also update the local DNS (Bind9 installed with no problems - using my zone with some static entries) using nsupdate and the 'wins hook' parameter in /etc/samba/smb.conf.

I followed some HOW-TOs on nsupdate to set it up. Means I generated a HMAC-MD5 key using 'dnssec-keygen -a HMAC-MD5 -b 512 -n HOST blackhole.thirdgate.'. Added a key-section to the named.conf.local named 'blackhole.thirdgate.' with secret set exactly to what is in the Kblackhole.thirdgate.+157+19064.key after the initial 'blackhole.thirdgate. IN KEY 512 3 157'. Restarted the server with no problems.

Now I started 'nsupdate -k Kblackhole.thirdgate.+157+19064.private' to manually test the settings and the functionality. On the nsupdate command line I wrote the server I want to send it to the prereq stuff, some update delete and update add. and finally a send command. Query is going out to the named-process (always tailing the syslog).

I get something like this:
```
Jul 30 15:07:38 blackhole named[7947]: client 192.168.204.2#48243: updating zone 'thirdgate/IN': delete all rrsets from name 'WICKEDIMP.thirdgate'
Jul 30 15:07:38 blackhole named[7947]: client 192.168.204.2#48243: updating zone 'thirdgate/IN': adding an RR at 'WICKEDIMP.thirdgate' A
Jul 30 15:07:38 blackhole named[7947]: /etc/bind/db.thirdgate.jnl: open: permission denied
Jul 30 15:07:38 blackhole named[7947]: client 192.168.204.2#48243: updating zone 'thirdgate/IN': error: journal open failed: unexpected error
Jul 30 15:07:38 blackhole kernel: [582509.856311] audit(1217423258.142:12): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::w" name="/etc/bind/db.thirdgate.jnl" pid=7948 profile="/usr/sbin/named" namespace="default"
```

seems the kernel audit makes funny things with my system?!?! btw... I manually created an empty db.thirdgate.jnl in /etc/named and set it to user root.bind and permissions to 0666, because creating the file did fire up an equal error.

Ok... now what's going on? What did I do wrong? The named.conf and named.conf.options are the original from the bind9 package. Just edited named.conf.local.

Here some debug info:

keys are in /etc/bind/private/

named.conf.local:
```
key blackhole.thirdgate. {
        algorithm HMAC-MD5;
        secret "EaDTOoUSZFan7ZXiyDAuN/ra7m1aWW3a4tjv5fbx9RyD2U2bjgq+Ggms rudsU5Ahl6vKMwVUaLs6dzEdKRea1w==";
};

zone "thirdgate" {
        type master;
        file "/etc/bind/db.thirdgate";
        allow-update { key blackhole.thirdgate.; };
};
```

db.thirdgate:
```
$TTL    604800
@               IN      SOA     thirdgate. blackhole.thirdgate. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      blackhole.thirdgate.
@               IN      A       192.168.204.2
blackhole       IN      A       192.168.204.2
ziz             IN      A       192.168.204.1
```

---

