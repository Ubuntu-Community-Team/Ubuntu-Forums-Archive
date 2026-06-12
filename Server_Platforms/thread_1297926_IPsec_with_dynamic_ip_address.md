---
title: "IPsec with dynamic ip address"
date: 2009-10-22
forum: Server Platforms
---

### Post by ragnator on 2009-10-22
Hi all,

I have an ipsec tunnel going from my hardy gateway to a sonicwall firewall with a static IP address. I am using an ADSL line with dynamic IP, so my IP keeps changing often.

Tunnel get's established without problems initially, but when the ADSL line goes down and IP changes the tunnel doesn't come back up.

racoonctl shows me the following after a IP change, seems to indicate that the old SA's are not deleted.

```

root@ubuntu:~$ sudo racoonctl ss isakmp
Destination            Cookies                           Created
67.221.256.46.500      7bbb54cb9d35712c:ba13bf18daf0befb 2009-10-22 18:36:59
97.34.18.242.500       5a8822053b69c999:76c982679e4c454b 2009-10-22 18:36:04
67.221.256.46.500      05615456125e9a98:9441d995120f33b5 2009-10-22 18:06:04
67.221.256.46.500      dfaa5e414c6a84a6:710aad570ff3e4bb 2009-10-22 18:06:11
97.34.18.242.500       5bbbaefd910f79c3:80babab33396ad8f 2009-10-22 18:05:59

```There are duplicate isakmp and the corresponding esp and Ipsec entries.

Also, a racoon/setkey restart clears the entries and starts new SA negotiations, but I've found this doesn't work all the time. The logs show that the SA has been established but no packets go through. When this happens I usually stop racoon and wait for some time before starting it again and this time the tunnels come up without problem.

My racoon.conf and ipsec-tools.conf

**racoon.conf **
```

remote 67.221.256.46 {
        exchange_mode main;
        nat_traversal off;
        initial_contact on;
        my_identifier fqdn "network1.test";
        proposal {
                encryption_algorithm 3des;
                hash_algorithm sha1;
                authentication_method pre_shared_key;
                dh_group 2;
        }
}

sainfo subnet 192.168.56.0/24[any] any subnet 192.168.25.0/24[any] any {
        encryption_algorithm 3des;
        authentication_algorithm hmac_sha1;
        compression_algorithm deflate;
}

```**ipsec-tools.conf**
```

flush;
spdflush;

spdadd 192.168.56.0/24 192.168.25.0/24 any -P out ipsec
                esp/tunnel/192.168.56.254-67.221.256.46/require;
spdadd 192.168.25.0/24 192.168.56.0/24 any -P in ipsec
                esp/tunnel/67.221.256.46-192.168.56.254/require;


```

Any solution other the a racoon/setkey restart  or maybe I need to set some racoon parameter :confused:

---

