---
title: "Snort error"
date: 2008-05-22
forum: Security
---

### Post by borkborkbork on 2008-05-22
Im new to linux, and seeing as security is my area of interest I thought I'd try and install some of the applications listed in the main security sticky. I chose snort, installed it using:

        "sudo apt-get install snort"
      
Everything installed fine, I guess. It was suggested that one starts out with the "-v" command when first using it. I ran the command and this is what happens:

             --== Initializing Snort ==--
Initializing Output Plugins!
Verifying Preprocessor Configurations!
ERROR: Failed to lookup for interface: no suitable device found. Please specify one with -i switch
Fatal Error, Quitting..


Can anyone help me out here? Have I missed some major aspect?

---

### Post by Monicker on 2008-05-22
The error message is pretty clear.

add
```
-i eth0
```

for example, or adjust your snort.conf and make sure the proper network interface is specified there.  What active network interfaces do you have on the machine?

---

### Post by borkborkbork on 2008-05-22
Here is what the active networks appeared as after using netstat


```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 utnubu.local:35657      oam-m19a.blue.aol.c:aol ESTABLISHED
tcp        0      0 utnubu.local:57803      205.188.7.205:aol       ESTABLISHED
tcp        0      0 utnubu.local:44723      a216.151.140.80.dep:www ESTABLISHED

```

---

### Post by The Tronyx on 2008-05-22
> **borkborkbork said:**
> Here is what the active networks appeared as after using netstat


```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 utnubu.local:35657      oam-m19a.blue.aol.c:aol ESTABLISHED
tcp        0      0 utnubu.local:57803      205.188.7.205:aol       ESTABLISHED
tcp        0      0 utnubu.local:44723      a216.151.140.80.dep:www ESTABLISHED

```

Could you please tell us what the command, 'ifconfig' shows?

---

### Post by jba6511 on 2008-05-22
to start snort in interactive mode (runs in the terminal)
sudo snort -i eth0 -c /etc/snort/snort.conf

where eth0 is the interface you use and /etc/snort/snort.conf is the path to your snort.conf file.

to start snort quietly
sudo /usr/sbin/snort -c /etc/snort/snort.conf -i eth0 -g root -D

to stop snort
sudo /etc/init.d/snort stop

More than likely if you only have one NIC card installed than it will be assigned to eth0, but the results from ifconfig will confirm this.

---

### Post by borkborkbork on 2008-05-23
```

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:b1:db:d7  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:feb1:dbd7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141512 (138.1 KB)  TX bytes:61440 (60.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131900 (128.8 KB)  TX bytes:131900 (128.8 KB)

```


anyone?

---

