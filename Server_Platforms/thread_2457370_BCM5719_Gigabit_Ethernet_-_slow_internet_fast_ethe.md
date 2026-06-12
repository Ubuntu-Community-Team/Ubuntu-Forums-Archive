---
title: "BCM5719 Gigabit Ethernet - slow internet fast ethernet speed"
date: 2021-01-31
forum: Server Platforms
---

### Post by josedb on 2021-01-31
Ho, i am running 20.04 server on a Prolian dl380p g8 server. Samba service works fast as ethernet speed (1gbs, or 114MB/s copying files), but i noticed something strange when downloading files from the nextcloud app. I am capped to 2.4Mbytes/s of download speed (from outside), while internet connection is 300/300mbs . So i tried downloading files via sftp and surprissely i have the same speed 2.4MB/s. Looks like internet connection is the problem. The nic is BCM5719 Gigabit Ethernet , and i have two cables, one is directly connected to a VM, where i am running windows 10, and the internet speed is ok there (300/300).
speedtest-cli reports different speeds every run even with no activity at all in the server. But never higher than 150mbs (both upload and download). Download speed from outside is always the same 2.4MB/s no matter what speedtest-cli is reporting.

I see no errors in dmesg either in device statics

```
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.5  netmask 255.255.255.0  broadcast 192.168.0.255
        ether --:--:--:--:--:--  txqueuelen 1000  (Ethernet)
        RX packets 431237  bytes 282078032 (282.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 779177  bytes 978921673 (978.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 50

```

Internet speed in others machines is ok, even in the vm. I have never install or set up any kind of QOS software (nor in the router where i run pfsense)

So i am kinda lost here, been searching in websites with no luck, just see cable problems and drivers problem but this might not be the case

Do you mind giving me any directions? it would be very appreciated

---

