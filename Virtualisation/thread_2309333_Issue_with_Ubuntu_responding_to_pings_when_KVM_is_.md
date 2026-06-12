---
title: "Issue with Ubuntu responding to pings when KVM is installed"
date: 2016-01-09
forum: Virtualisation
---

### Post by xrctp1 on 2016-01-09
[FONT=tahoma]I'm not 100% this is a KVM issue but I have a server with a couple of virtual machines installed that will not respond to pings. The configuration is as follows:
[/FONT]
```


[FONT=lucida console]|--------------|    |------------------|
|Host eth5     |    |                  |
| 192.168.1.45 |    | Bridged eth3     |
|--------------|    |------------------|
                                    |
                                    |
                         |------------------|
                         |      vmbr1       |
                         | 192.168.1.30     |
                         |------------------|
                                 |
                                 |
                     |------------------|
                     |       guests     |
                     |------------------|[/FONT]

```

[FONT=tahoma]In this configuration neither eth5 nor vmbr1 respond to pings from outside the vlan. I did a tcpdump on incoming and outgoing icmp requests for eth5 and found that although the pings are getting TO the server, the server does not send a response. I am able to ping everything on the vlan except for this host from outside.[/FONT]

---

### Post by xrctp1 on 2016-01-09
Now I feel stupid, the default gateway was set to 0.0.0.0 which prevented the server from returning requests.

---

