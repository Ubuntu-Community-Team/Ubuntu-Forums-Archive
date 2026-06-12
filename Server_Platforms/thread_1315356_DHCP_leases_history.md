---
title: "DHCP leases history"
date: 2009-11-05
forum: Server Platforms
---

### Post by wwoollff on 2009-11-05
Hi. I have a small company server, running Ubuntu Server 9.10, that acts as a software router. Now...my question is...is there a way I can record all the leases of the DHCP server? /var/lib/dhcp3/dhcpd.leases records only the last machine that had that IP, but I cannot know what machine had that IP a day ago.

also,one more issue:
although I have in my /etc/dhcp3/dhcpd.conf something like
```

host name {
hardware ethernet 00:00:00:00:00:00; //sorry,I can't post real MAC
fixed address 192.168.1.5;
}

```
the DHCP server sends a random IP address, as if this allocation wouldn't exist. Any ideas?

---

### Post by mpokrywka on 2009-11-05
Check /var/log/daemon.log for dhcp server logs, there are entries like:

Nov  1 09:45:44 myserver dhcpd: DHCPDISCOVER from 00:00:00:00:00:01 via eth0
Nov  1 09:45:44 myserver dhcpd: DHCPOFFER on 192.168.7.209 to 00:00:00:00:00:01 via eth0
Nov  1 09:45:44 myserver dhcpd: DHCPREQUEST for 192.168.7.209 from 00:00:00:00:00:01 via eth0
Nov  1 09:45:44 myserver dhcpd: DHCPACK on 192.168.7.209 to 00:00:00:00:00:01 via eth0


About fixed-address: maybe your "host" declaration(s) are inside wrong "subnet" declaration?

---

### Post by wwoollff on 2009-11-05
Thx man. Well, there's no subnet...It's just one big private network. I've rechecked the dhcpd.cfg, but everything seems ok... anything else that could be the problem?

---

### Post by koenn on 2009-11-05
> **wwoollff said:**
> Thx man. Well, there's no subnet...It's just one big private network. I've rechecked the dhcpd.cfg, but everything seems ok... anything else that could be the problem?

there has to be a subnet declaration in your dhcp conf file (even if it covers your enrire networ, which would not be unusual) - that's what mpokrywka is referring to.

Maybe post your dhcpd.cfg anyway ? 
There's not much that can go wrong with a dhcp configuration that isn't in the dhcp configuration file,

Or we could just do random guesses at the cause of the problem : cosmic rays, daylight savings time, crosstalk on your wires, your dhcp server decided to get creative in stead of just stand there and do as it is told, ...

---

### Post by wwoollff on 2009-11-06
ok...here's the /etc/dhcp3/dhcpd.conf :

```

option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
#option ip-forwarding off;
option domain-name-servers 208.67.222.222, 208.67.220.220;
option domain-name "motu.motu";
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
}
host b1 {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.49;
}
host ma {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.65;
}
host cr {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.18;
}
host un {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.87;
}
host ur {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.41;
}
host cal {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.81;
}
host mu {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.83;
}
host ga {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.52;
}
host ne {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.14;
}
host uj {
hardware ethernet 00:00:00:00:00:00;
fixed-address 192.168.1.84;
}

```

---

### Post by koenn on 2009-11-06
hmmm, ...
I'd expect those host declariations to be inside the subnet declaration, since you expect them to get addresses from the range you declared for that subnet, 
something like
```

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.100;

    host b1 {
        hardware ethernet 00:00:00:00:00:00;
        fixed-address 192.168.1.49;
    }

}

```

---

### Post by wwoollff on 2009-11-06
wow...you might be right. I'm gonna try this tomorrow. Thanks alot!

---

