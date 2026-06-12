---
title: "unable to ping or access websites on ubuntu 18.4LTS on Virtual box"
date: 2019-01-09
forum: Virtualisation
---

### Post by rahimmawani on 2019-01-09
Hey guys

total newbie here, got fed up with windows world and gone over to the dark side :)

yesterday i installed ubuntu 18.4 LTS on a Virtual box with bridge connections.

it seems i can ping ip addresses internally, ping with ip addresses externally but when i try and resolve hostnames or websites, i cant

```
rahim@websrv01ubuntu:~$ ping -c3 192.168.0.1PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=3.20 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=9.16 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=7.38 ms


--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 3.206/6.584/9.164/2.497 ms
rahim@websrv01ubuntu:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=121 time=34.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=121 time=22.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=121 time=27.8 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 22.980/28.526/34.788/4.849 ms
rahim@websrv01ubuntu:~$ ping -c3 websvr01ubuntu
ping: websvr01ubuntu: Temporary failure in name resolution
rahim@websrv01ubuntu:~$ ping -c3 www.google.com
PING www.google.com(ams16s32-in-x04.1e100.net (2a00:1450:400e:80c::2004)) 56 data bytes


--- www.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2042ms


rahim@websrv01ubuntu:~$



```

I know 18.4 uses netplan and this is how it the 50-cloud-init.yaml file is configured for static ip address.
```


network:
   version: 2
   renderer: networkd
   ethernets:
         enp0s3:
           dhcp4: no
           addresses: [192.168.0.200/24]
           gateway4: 192.168.0.1
           nameservers:
             addresses: [8.8.8.8,8.8.4.4]



```

any help will be appreciated as i begin my journey into linux world

Thanks
Rahim

---

### Post by slickymaster on 2019-01-09
Thread moved to **Virtualisation** for a better fit

---

### Post by QIII on 2019-01-09
Hello!

yaml is very strict about 2 space indentations.  That is part of its specification.

Try cleaning up your indentation as a start.

Cheers!

---

### Post by rahimmawani on 2019-01-09
```
# This file is generated from information provided by the datasource.  Changes $# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: no
      addresses: [192.168.0.200/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]

rahim@websrv01ubuntu:~$ ping -c3 google.com
PING google.com(ams16s32-in-x0e.1e100.net (2a00:1450:400e:80c::200e)) 56 data bytes


--- google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2038ms


rahim@websrv01ubuntu:~$ ping -c3 www.google.com
PING www.google.com(ams15s21-in-x04.1e100.net (2a00:1450:400e:800::2004)) 56 data bytes


--- www.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2034ms


rahim@websrv01ubuntu:~$ ping -c3 www.servingyoubetter.co.uk
PING fwd3.hosts.co.uk (85.233.160.22) 56(84) bytes of data.


--- fwd3.hosts.co.uk ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2055ms


rahim@websrv01ubuntu:~$






```

thanks and noted

 still no joy...im assuming its not a dns issue as it is resolving address, just not pinging them

what else am i missing
thanks
Rahim

---

