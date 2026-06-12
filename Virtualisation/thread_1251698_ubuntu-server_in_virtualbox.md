---
title: "ubuntu-server in virtualbox"
date: 2009-08-28
forum: Virtualisation
---

### Post by bterminalx on 2009-08-28
I'm not new at this, but I hate redownloading VMWARE-SERVER so I got VirtualBox. I'm use to VirtualBox on Mac and windows, but on linux, I just draw a blank because I just back INTO it. Ubuntu is my main os, etc..


Okay here's the thing, I want to run a local, yet public virtual server (ubuntu server) in virtualbox. I am using Bridge for the network connected to my wlan0 device. I can login locally perfectly. Now, I'm setting up ZNC + ZNC-WebAdmin via the repository, it's all setup, running, however, I cannot connect to it. 

[http://192.168.1.3:8088/](http://192.168.1.3:8088/) (8088 is the port I use)


Here's the information extracted from "ifconfig"
```

eth0      Link encap:Ethernet  HWaddr 08:00:27:53:21:66  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe53:2166/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50017572 (50.0 MB)  TX bytes:2011999 (2.0 MB)


```


I'm really not sure what to do at this point, any help would be apreciated on this subject. :)

---

### Post by firen on 2009-08-28
Are you using DSL Modem? Is it on NAT? Have you enabled Port forwarding on modem for port 8080 ?

---

### Post by bterminalx on 2009-08-28
I am using wireless (It's good enough for me)

```
wlan0     Link encap:Ethernet  HWaddr 00:14:6c:69:61:a0  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe69:61a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:739442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:461909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1092802827 (1.0 GB)  TX bytes:44777001 (44.7 MB)

```


I don't need to port forward 8088 if I'm accessing it locally, right?

---

### Post by firen on 2009-08-28
This line confuses me actually

"I want to run a local, yet public virtual server (ubuntu server) in virtualbox. I am using Bridge for the network connected to my wlan0 device. I can login locally perfectly."

If possible elaborate on this.

Are you able to ping 192.168.1.3 ?

---

### Post by bterminalx on 2009-08-28
Yeah, not only that, some things actually work right. Apache will load, and I can SSH (Locally). However, Webmin and ZNC Webadmin give me this firefox message


```

Connection Interrupted

The connection to the server was reset while the page was loading.
The network link was interrupted while negotiating a connection. Please try again.
```

---

### Post by firen on 2009-08-28
Are you sure there is not firewall rule blocking your request? on both Host and guest machine. Im running out of Ideas now :P

---

### Post by khurramsehgal1 on 2009-08-28
[<script type="text/javascript"><!-- google_ad_client = "pub-4865507857939878"; /* 728x90, created 8/27/09 */ google_ad_slot = "8490635747"; google_ad_width = 728; google_ad_height = 90; //--> </script> <script type="text/javascript" src="http://pagead2.googlesyndication.com/pagead/show_ads.js"> </script>]("<script type="text/javascript"><!-- google_ad_client = "pub-4865507857939878"; /* 728x90, created 8/27/09 */ google_ad_slot = "8490635747"; google_ad_width = 728; google_ad_height = 90; //--> </script> <script type="text/javascript" src="http://pagead2.googlesyndication.com/pagead/show_ads.js"> </script>")

---

### Post by khurramsehgal1 on 2009-08-28
> **khurramsehgal1 said:**
> [<script type="text/javascript"><!-- google_ad_client = "pub-4865507857939878"; /* 728x90, created 8/27/09 */ google_ad_slot = "8490635747"; google_ad_width = 728; google_ad_height = 90; //--> </script> <script type="text/javascript" src="http://pagead2.googlesyndication.com/pagead/show_ads.js"> </script>]("<script type="text/javascript"><!-- google_ad_client = "pub-4865507857939878"; /* 728x90, created 8/27/09 */ google_ad_slot = "8490635747"; google_ad_width = 728; google_ad_height = 90; //--> </script> <script type="text/javascript" src="http://pagead2.googlesyndication.com/pagead/show_ads.js"> </script>")
whats that wrongly pasted

---

### Post by bterminalx on 2009-08-28
> **firen said:**
> Are you sure there is not firewall rule blocking your request? on both Host and guest machine. Im running out of Ideas now :P
Uhm. My host is Ubuntu 9.04 Desktop Edition. The virtual server can access the web and such, but some things aren't working when it comes to ports and forwarding.

---

### Post by firen on 2009-08-28
try this from Host terminal

```
curl http://192.168.1.3:8088
```

and post the output here

---

### Post by bterminalx on 2009-08-28
Nah, nevermind, I fixed it throughout alot of trial and error, but I managed. Thanks for the help. :)

---

