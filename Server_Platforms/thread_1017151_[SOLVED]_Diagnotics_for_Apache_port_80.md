---
title: "[SOLVED] Diagnotics for Apache port 80?"
date: 2008-12-20
forum: Server Platforms
---

### Post by R.Bucky on 2008-12-20
I have a fresh Ubuntu 8.04 install with LAMP. I have been operating LAMP for around a year now without too much problem. However, My server does not appear to be letting port 80 requests from outside the network. Localhost and [http://buckyspalace.net]("http://buckyspalace.net") works fine. Utilizing proxy.org or canyouseeme.org show blockage. **What other diagnostics can I run to determine why requests are blocked?**

My router is configured to pass port 80 requests TCP and I have a static IP (173.10.77.142). I purchased a business account with my ISP, therefore there is no potential for port 80 blocks from them. Also, I have allowed port 80 through on ufw as well.

```
mark@markserver:~$ nmap buckyspalace.net

Starting Nmap 4.53 ( http://insecure.org ) at 2008-12-20 15:34 PST
Warning: Hostname buckyspalace.net resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 1706 closed ports
PORT      STATE SERVICE
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
902/tcp   open  iss-realsecure-sensor
3306/tcp  open  mysql
8009/tcp  open  ajp13
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.177 seconds
```

Results from netstat -tulpn
```
PID/Program name
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN      6474/vmware-authdla
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5455/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      5590/smbd       
tcp        0      0 0.0.0.0:8333            0.0.0.0:*               LISTEN      7073/vmware-hostd
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      7233/perl       
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN   
```

---

### Post by freebeer on 2008-12-20
hmm... you're right.. I can't connect with a browser, but I can ping it.  I'm wondering if your router, for whatever reason, isn't letting those requests through.  Yes, I see that you forwarded your port 80, but I'm wondering if the router is failing to do so anyway.  Maybe issuing the port forward again in the router, and/or resetting it might clear up the problem.  *shrug*

---

### Post by R.Bucky on 2008-12-20
Ok, good. I am not crazy. I went back to my router to doublecheck the settings. All is well. This is a strange phenomenon indeed. Continuing to search the net for a solution...

---

### Post by MJN on 2008-12-21
What firewall rules have you got set? (on the server and router if applicable)

Have you tried moving Apache's port (and changing your port forwarding) to check it is not your router intercepting the requests on port 80?

Mathew

---

### Post by windependence on 2008-12-21
What is the output of 

```
sudo ufw status
```Try this:

```
sudo ufw disable
```To me, however, it looks like Comcast is up to their dirty tricks again. With some ISPs, even if you have a commercial account, you still have to call them and tell them to open your ports. What leads me to this conclusion is :

```
traceroute to 173.10.77.142 (173.10.77.142), 64 hops max, 40 byte packets
 1  192.168.2.1 (192.168.2.1)  2.101 ms  1.753 ms  1.626 ms
 2  phnx-dsl-gw34-226.phnx.qwest.net (67.40.227.226)  24.270 ms  24.434 ms  25.019 ms
 3  phnx-agw1.inet.qwest.net (75.160.237.9)  25.877 ms  24.121 ms  25.545 ms
 4  phx-core-01.inet.qwest.net (205.171.129.25)  24.814 ms  24.160 ms  24.349 ms
 5  lap-brdr-03.inet.qwest.net (67.14.22.74)  34.999 ms  35.882 ms  36.311 ms
 6  63.146.26.78 (63.146.26.78)  94.512 ms  180.101 ms  43.500 ms
 7  COMCAST-IP-SERVICES-LLC.Te3-3.ar4.LAX2.gblx.net (64.214.149.106)  37.035 ms  36.831 ms  36.322 ms
 8  pos-0-9-0-0-cr01.sacramento.ca.ibone.comcast.net (68.86.85.189)  48.672 ms  46.949 ms  48.571 ms
 9  pos-0-0-0-0-cr01.portland.or.ibone.comcast.net (68.86.85.198)  62.709 ms  62.424 ms  61.904 ms
10  68.86.90.222 (68.86.90.222)  66.793 ms  66.340 ms  67.590 ms
11  te-5-1-ur01.olympia.wa.seattle.comcast.net (68.86.96.9)  70.732 ms  70.022 ms  69.499 ms
12  68.85.144.82 (68.85.144.82)  68.127 ms  68.706 ms  67.529 ms
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
31  * * *
32  * * *
33  * * *
34  * * *
35  * * *
36  * * *
37  * * *
38  * * *
39  * * *
40  * * *
41  * * *
42  * * *
43  * * *
44  * * *
45  * * *
46  * * *
47  * * *
48  * * *
49  * * *

```The address where it stops is this:

```
IP address:                     68.85.144.82
Reverse DNS:                    [No reverse DNS entry per dns1.inflow.pa.bo.comcast.net.]
Reverse DNS authenticity:       [Unknown]
ASN:                            33668
ASN Name:                       DNEO-OSP7
IP range connectivity:          1
Registrar (per ASN):            ARIN
Country (per IP registrar):     US [United States]
Country Currency:               USD [United States Dollars]
Country IP Range:               68.80.0.0 to 68.95.255.255
Country fraud profile:          Normal
City (per outside source):      Troy, Michigan
Country (per outside source):   US [United States]
Private (internal) IP?          No
IP address registrar:           whois.arin.net
Known Proxy?                    No
Link for WHOIS:                 [68.85.144.82]("http://private.dnsstuff.com/tools/whois.ch?ip=68.85.144.82")
```Your A record looks correct:

```
; <<>> DiG 9.4.2-P2 <<>> buckyspalace.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 36524
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;buckyspalace.net.        IN    A

;; ANSWER SECTION:
buckyspalace.net.    7200    IN    A    173.10.77.142

;; AUTHORITY SECTION:
buckyspalace.net.    43200    IN    NS    ns52.worldnic.com.
buckyspalace.net.    43200    IN    NS    ns51.worldnic.com.

;; ADDITIONAL SECTION:
ns51.worldnic.com.    41741    IN    A    205.178.190.26
ns52.worldnic.com.    13389    IN    A    205.178.144.26

```

I think they are still blocking you. Post the output of your ufw command.



-Tim

---

### Post by R.Bucky on 2008-12-21
I think that I went crazy to make sure that ufw is open. Currently, ufw is disabled. 

```
mark@markserver:~$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
80:tcp                     ALLOW   Anywhere
80:tcp                     ALLOW   Anywhere
80:udp                     ALLOW   Anywhere
8222:tcp                   ALLOW   Anywhere
8222:udp                   ALLOW   Anywhere
8902:tcp                   ALLOW   Anywhere
8902:udp                   ALLOW   Anywhere
902:tcp                    ALLOW   Anywhere
902:udp                    ALLOW   Anywhere
8333:tcp                   ALLOW   Anywhere
8333:udp                   ALLOW   Anywhere
53:tcp                     ALLOW   Anywhere
53:udp                     ALLOW   Anywhere
67:tcp                     ALLOW   Anywhere
67:udp                     ALLOW   Anywhere
68:tcp                     ALLOW   Anywhere
68:udp                     ALLOW   Anywhere
Anywhere                   ALLOW   10.1.10.1 80:tcp
Anywhere                   ALLOW   10.1.10.1 80:udp
Anywhere                   ALLOW   173.10.77.142 80:tcp
Anywhere                   ALLOW   173.10.77.142 80:udp
Anywhere                   ALLOW   255.255.255.255 80:tcp
Anywhere                   ALLOW   255.255.255.255 80:udp
```

I did speak with a comcast rep alst night. They assured me that port 80 is not blocked, especially with a business account. The router/modem hardware they gave me is configured by default to accept connections on 80, 443, and 23. 

As the true test, I disconnected the router and ran a straight modem connection. It yielded the same negative response. The test ensured that since comcast is not blocking, and confirmed that my system is not configured properly. 

My ports.conf is standard:

```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

When I change the port to something non-tradional, Apache returns
```

Access Error: Site or Page Not Found
Cannot open URL

```

I have never ran apache on something other than 80. what other file would need to be modified? If memory servers, their is another .conf file or something with port config info.

---

### Post by windependence on 2008-12-21
Strange that my traceroute stops way short of your local IP. You might want to insist that support do their own traceroute and see what they say. If you were blocked at your firewall or your local sever IP, I should be able to walk in at least that far.

What happens of you assign your static IP to your web box without NATing it? 

-Tim

---

### Post by R.Bucky on 2008-12-21
> **windependence said:**
> 
What happens of you assign your static IP to your web box without NATing it? 


I am not quite sure how to implement your suggestion. Can you please elaborate?

I performed a traceroute on a website and it hit my box. see image
[http://picasaweb.google.com/buckman1/DNS#5282377514362450290]("http://picasaweb.google.com/buckman1/DNS#5282377514362450290")

---

### Post by R.Bucky on 2008-12-21
For the love of... someone!!! 

I made some progress. Port 80 now shows open via canyouseeme.org. I needed to add http to the port forwarding on the new hardware (the modem and router are one piece of hardware with the business account). Additionally, I had my /sites-available/default VirtualHost set to my static ip rather than the wildcard *

Good god. I hate it when stupid stuff botches everything.

I really appreciate the time everyone took to help out. 

~Mark

---

### Post by windependence on 2008-12-22
No problem. At times like these you have to just get up and walk away for a while. Have a coffee, take a smoke break, whatever. You get so frustrated that you can't see the problem right in front of you.

-Tim

---

