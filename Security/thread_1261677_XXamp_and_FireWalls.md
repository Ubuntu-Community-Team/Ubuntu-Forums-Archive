---
title: "XXamp and FireWalls?"
date: 2009-09-09
forum: Security
---

### Post by Irvine_himself on 2009-09-09
I am a Ubuntu noob who is currently running XP and setting up,  as my second machine, (a freebie secondhand Dell Optiplex GX270,) to run Ubuntu. The aim being when my, many times repaired, beat-up, crippled old laptop finally dies, I will migrate full time to a Ubuntu.

I do a bit of amateur web design and have XXamp installed in XP and am installing XXamp on the Ubuntu box. I have installed Gufw and was wondering if it is possible to block outbound traffic from the Mysql/Apache installation of XXamp using Gufw.

Also, I was looking at TuxGuardian which seems perfect for someone migrating from XP type firewalls. Does anyone have experience with TuxGuardian? Is the project still alive? Does it work as claimed?

Thanks in advance

Irvine

PS

I am not good with IPtables.

---

### Post by Bachstelze on 2009-09-09
> **Irvine_himself said:**
> 
I do a bit of amateur web design and have XXamp installed in XP and am installing XXamp on the Ubuntu box. I have installed Gufw and was wondering if it is possible to block outbound traffic from the Mysql/Apache installation of XXamp using Gufw.

Do you really need to? Your two computers are probably on a LAN behing a router, so unless you forward ports on it, your server won't be accessible from the outside world.

---

### Post by Irvine_himself on 2009-09-09
Not always the case, I have a friendly local business man who gives me a free Internet connection through a business line and modem to his office.  He also runs a free Wifi-hotspot to a different ISP.  The Wifi is definitely not behind his network and, unfortunately, he can tinker with things without notice!    For example, The network was behind a hard firewall separate from the network controller. Without telling me he decided the hard firewall was superfluous...      On another occasion, I went to access some sites I keep on his server and for which I have a modified  hosts file. Being unable to get to the sites, I phoned him to say that the server was down, only to be told that he had temporarily switched me over to the other ISP as he was having problems propagating a new DNS for his essential business interests.  (Basically what passes for his system administrator was having a nervous breakdown trying to maintain two competing DNS plus my modem connection.)    Anyway, I am sure you can see why firewalls make nervous

---

### Post by cdenley on 2009-09-09
UFW (and GUFW) can only filter inbound traffic. There has never been much need to filter outbound traffic. The only situation I can think of (besides a network gateway/firewall) is if you are concerned about malware or spyware phoning home. This is not an issue with ubuntu because all software is installed from the repository and can be trusted. Of course if you go and install unsupported software you pulled from a website, such as XXamp, then it might become an issue. I suggest you use the supported LAMP server configuration.

If you need advanced configuration of iptables such as outbound filtering, you can either configure it directly...
```

man iptables

```
or you may be able to use another frontend such as firehol, webmin, or firestarter.

A better method of controlling your traffic is to not configure your system to produce or listen for unwanted traffic.

---

### Post by airtonix on 2010-01-28
I don't think we should be questioning or trying to preach about the type of software one should keep on their computer.

No one ends up hearing you anyway.

What I do think overall is far more productive is to get something equivilant to tuxguardian running again for ubuntu and provided in the offical repos.

Few things about tuxguardian : 

+ identifies (via md5 hash of the program bin) individual processes that make network connections.
+ maintains deny/allow rules to ip subnets /ports based on those md5 hash keys.


These two aspects are fairly essential considering that wine has become mature enough to accommodate most naive users.

---

### Post by cariboo on 2010-01-29
We shouldn't preach about what software someone should use, but where that software comes from, should be a topic of concern. Remember what happened at Gnome-Look.

Tuxguardian hasn't been maintained for 3 years, and from the looks of it never finished.

---

