---
title: "VLAN in Ubuntu 12.04 not working."
date: 2012-05-24
forum: Server Platforms
---

### Post by allanmair on 2012-05-24
Hi,

i can´t make VLAN work in 12.04 server, at same computer ubuntu 10.04 works great, i followed this steps:
 
[http://ubuntuforums.org/showthread.php?p=4375149&mode=threaded]("http://ubuntuforums.org/showthread.php?p=4375149&mode=threaded")

Is there something different to do in 12.04?

```
lsmod | grep 8021q
8021q                  22168  0
garp                    7689  1 8021q

ifconfig
eth0      Link encap:Ethernet  EndereÃ§o de HW 6c:f0:49:fb:82:e0
          endereÃ§o inet6: fe80::6ef0:49ff:fefb:82e0/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  MÃ©trica:1
          pacotes RX:64494 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1843 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:1000
          RX bytes:5465512 (5.4 MB) TX bytes:77838 (77.8 KB)
          IRQ:17

eth0.2    Link encap:Ethernet  EndereÃ§o de HW 6c:f0:49:fb:82:e0
          inet end.: 172.24.255.247  Bcast:172.24.255.255  Masc:255.255.255.0
          endereÃ§o inet6: fe80::6ef0:49ff:fefb:82e0/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  MÃ©trica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1837 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:0
          RX bytes:0 (0.0 B) TX bytes:77370 (77.3 KB)


cat /proc/net/vlan/config
VLAN Dev name    | VLAN ID
Name-Type: VLAN_NAME_TYPE_RAW_PLUS_VID_NO_PAD
eth0.2         | 2  | eth0

cat /proc/net/vlan/config/eth0.2
eth0.2  VID: 2   REORDER_HDR: 1  dev->priv_flags: 1
         total frames received            0
          total bytes received            0
      Broadcast/Multicast Rcvd            0

      total frames transmitted         1852
       total bytes transmitted        78000
Device: eth0
INGRESS priority mappings: 0:0  1:0  2:0  3:0  4:0  5:0  6:0 7:0
 EGRESS priority mappings:



```

Thanks in advanced.


Solution.
I changed my network card and it works.

---

