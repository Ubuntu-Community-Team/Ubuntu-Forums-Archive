---
title: "ubuntu server 12.04 apt-get problem"
date: 2013-03-29
forum: Server Platforms
---

### Post by amalgamas on 2013-03-29
I have a recently installed ubuntu server 12.04.  When I run apt-get (update, upgrade or install) it does not seem to download anything and hangs on (Norwegian) Hent: xxx (Fetch: xxx ?).  ```
...
Hent:814 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]                        
Hent:815 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]                        
Hent:816 http://no.archive.ubuntu.com precise-updates/main Sources [373 kB]                    
Hent:817 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]                        
Hent:818 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]                        
Hent:819 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]                        
Hent:820 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]                        
Hent:821 http://security.ubuntu.com precise-security/restricted Sources [1 950 B]              
Hent:822 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]                        
Hent:823 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]                        
Hent:824 http://extras.ubuntu.com precise/main amd64 Packages [10,8 kB]
.....
```

Is this normal behavior in ubuntu server?  I did command line update in my (ubuntu) laptop end it went quick an smooth.  I checked sources.list on both machines and see no differences.

The server has two NICs.  
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.x.x  Bcast:192.168.x.255  Mask:255.255.255.0
          inet6 addr: .../64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5739 errors:0 dropped:1414 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:429765 (429.7 KB)  TX bytes:20215 (20.2 KB)

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.x.x  Bcast:192.168.x.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.x.x  Bcast:192.168.x255  Mask:255.255.255.0
          inet6 addr: .../64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3332894 (3.3 MB)  TX bytes:3571722 (3.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:807 (807.0 B)  TX bytes:807 (807.0 B)


```
  I removed all routes and iptables settings in the server, and internet seems to work well.  I can ping ubuntu repositories.  There is no proxy

Need help!

---

### Post by amalgamas on 2013-04-01
No answers

I reinstalled the server to get rid of the problem

---

