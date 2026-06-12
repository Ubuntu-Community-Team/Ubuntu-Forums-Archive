---
title: "UbuntuForums server has been really slow the last few days"
date: 2023-08-21
forum: The Cafe
---

### Post by TheFu on 2023-08-21
Is there a hardware failure about to happen?
Can anyone look at the logs?

My last post took over a minute to finish.  This post was normal, about 2 seconds.

---

### Post by oldfred on 2023-08-21
I was also slow. Had issue before and mtr showed it was servers at Canonical. 
When I complained they said it was not them.

[FONT=monospace][COLOR=#000000]mtr [www.ubuntuforums.org](www.ubuntuforums.org)  [/COLOR]
This time it goes from my Hotwire (Florida) and seems to have issues on this side of pond.
Looks like Miami & New York servers.

```
[/FONT][FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ mtr -c5 -r www.ubuntuforums.org  [/COLOR]
Start: 2023-08-21T10:50:45-0400 
HOST: Z170-jammy                  Loss%   Snt   Last   Avg  Best  Wrst StDev 
  1.|-- _gateway                   0.0%     5    0.3   0.4   0.3   0.5   0.1 
  2.|-- 170.250.172.1.hwccustomer  0.0%     5    3.5   2.9   1.5   4.1   1.1 
  3.|-- 10.96.0.45                 0.0%     5    2.5   3.0   1.8   4.5   1.0 
  4.|-- 10.82.0.25                 0.0%     5    4.9   3.1   2.1   4.9   1.1 
  5.|-- 10.96.0.26                 0.0%     5   14.4  14.6  13.2  15.2   0.8 
  6.|-- 170.250.254.41.hwccustome  0.0%     5   13.2  14.0  13.2  14.9   0.7 
  7.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0 
  8.|-- 100ge0-38.core3.ash1.he.n 80.0%     5   35.1  35.1  35.1  35.1   0.0 
  9.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0 
 10.|-- port-channel3.core2.nyc4. 60.0%     5   38.6  38.7  38.6  38.7   0.1 
 11.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0 
 12.|-- port-channel1.core1.lon6.  0.0%     5  106.7 106.5 106.1 107.0   0.4 
 13.|-- swp9.il3-core1.canonical.  0.0%     5  104.2 105.0 104.2 106.7   1.0 
 14.|-- ubuntuforums.org           0.0%     5  109.3 108.8 108.3 109.3   0.3

[/FONT][FONT=monospace]
```[/FONT]

---

### Post by #&amp;thj^% on 2023-08-21
Same here for about 2 days:
```
mtr -c5 -r www.ubuntuforums.org  
Start: 2023-08-21T09:18:06-0600
HOST: LVM-etx4                    Loss%   Snt   Last   Avg  Best  Wrst StDev

```
This is from New York, I've not tried Miami yet.
This is defiantly on Canonical side, I have no other problem elsewhere
and this:

```
Forbidden

You don't have permission to access this resource.
Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443
```
I'm losing faith........
Shouldn't this be in Forum Feed Back???

---

### Post by tea for one on 2023-08-21
On Sunday 20 August 2023 (UK resident), the forums were either slow, unresponsive or entirely inaccessible.
Today Monday 21 August, seems back to normal.

---

### Post by #&amp;thj^% on 2023-08-21
> **tea for one said:**
> On Sunday 20 August 2023 (UK resident), the forums were either slow, unresponsive or entirely inaccessible.
Today Monday 21 August, seems back to normal.
+1 mine began late Saturday, but yes today seems ok.
Hello from Miami :P

---

### Post by ajgreeny on 2023-08-21
There were a few problems noted yesterday (Aug 20th) as shown in the website at [https://status.canonical.com/](https://status.canonical.com/) (scroll about half way down the page for the history and you will see several problems listed though no detail of what the problem was.

So far today all seems OK again to me.

---

### Post by Doug S on 2023-09-12
My access to ubuntuforums has been mostly excruciatingly slow the last couple of days (September 11th and 12th). Sometimes it even times out. But at times the response time is fast. I am not familiar with the "mtr" utility mentioned in some posts, but I'll look into it. I don't observe anything in the website at [https://status.canonical.com/](https://status.canonical.com/) which was mentioned in an earlier post.
I am in the vicinity of Vancouver, Canada.

EDIT:

```
doug@s19:~/adrestia$ mtr -c5 -r www.ubuntuforums.org
Start: 2023-09-12T17:08:56-0700
HOST: s19                         Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- -my-gateway-         0.0%     5    0.4   0.3   0.3   0.4   0.0
  2.|-- 100.122.29.1               0.0%     5    1.7   1.3   0.9   1.7   0.3
  3.|-- 154.11.15.107              0.0%     5    2.1   1.6   1.3   2.1   0.3
  4.|-- QUBCPQAJDR02.bb.telus.com  0.0%     5    3.0   5.2   2.0  15.9   6.0
  5.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0
  6.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0
  7.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0
  8.|-- 100ge0-71.core2.tor1.he.n 40.0%     5   51.4  50.7  50.1  51.4   0.7
  9.|-- 100ge0-73.core2.nyc4.he.n 60.0%     5   59.7  61.7  59.7  63.7   2.8
 10.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0
 11.|-- port-channel1.core1.lon6.  0.0%     5  126.7 126.1 125.5 126.7   0.5
 12.|-- swp9.il3-core2.canonical.  0.0%     5  125.2 125.0 124.9 125.2   0.2
 13.|-- ubuntuforums.org           0.0%     5  133.7 133.9 133.7 134.0   0.1
```
And:
```
doug@s19:~/adrestia$ nslookup swp9.il3-core2.canonical.com
Server:         127.0.0.53
Address:        127.0.0.53#53

Non-authoritative answer:
Name:   swp9.il3-core2.canonical.com
Address: 216.66.89.222
Name:   swp9.il3-core2.canonical.com
Address: 2001:470:1:c31::2

doug@s19:~/adrestia$ ping 216.66.89.222
PING 216.66.89.222 (216.66.89.222) 56(84) bytes of data.
64 bytes from 216.66.89.222: icmp_seq=1 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=2 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=3 ttl=59 time=135 ms
64 bytes from 216.66.89.222: icmp_seq=4 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=5 ttl=59 time=135 ms
64 bytes from 216.66.89.222: icmp_seq=6 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=7 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=8 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=9 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=10 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=11 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=12 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=13 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=14 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=15 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=16 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=17 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=18 ttl=59 time=136 ms
64 bytes from 216.66.89.222: icmp_seq=19 ttl=59 time=135 ms
64 bytes from 216.66.89.222: icmp_seq=20 ttl=59 time=136 ms
^C
--- 216.66.89.222 ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 19011ms
rtt min/avg/max/mdev = 135.346/135.703/136.031/0.224 ms
```

---

### Post by TheFu on 2023-09-13
Yep, yesterday was bad.  Lots and lots of dropped connections which appeared to be inside Canonical's routers.  OTOH, we had some thunderstorms here and some other internet connections were problematic too.
Right now, tracepath is getting lost trying to find this server. Running into a "too many hops" error and no reply after getting close:
```
 9:  ae-9.edge4.Atlanta2.Level3.net                       26.433ms asymm 10 
10:  swp10.il3-core1.canonical.com                       104.036ms asymm 23 
11:  il3-fw2.canonical.com                               103.805ms asymm 24 
12:  il3-fw2.canonical.com                               104.223ms asymm 24 
13:  no reply
14:  no reply
15:  no reply
```

Perhaps Canonical disabled ICMP?  ping is stuck too. 
Update: that last post happened fast, even while ping was failing. I'm guessing Canonical's firewalls are blocking ICMP.

---

### Post by Doug S on 2023-09-13
> **TheFu said:**
> Perhaps Canonical disabled ICMP?  ping is stuck too. 
Update: that last post happened fast, even while ping was failing. I'm guessing Canonical's firewalls are blocking ICMP.

Yes, seems fine for me this morning also. I was finally able to edit my post (wanted to obfuscate my gateway name), which I was unable to complete yesterday ("forbidden" and timeout and gateway error and ...).

Yes, I never got a ping reply from "ubuntuforums.org", but I did from "swp9.il3-core2.canonical.com".

---

### Post by #&amp;thj^% on 2023-09-13
Still godawful slow here for me...4 mins just to login, and 2 disconnects.
This would be a great place to open a ubuntuforums.org site. :P
> Secure Connection Failed

An error occurred during a connection to ubuntuforums.org. PR_END_OF_FILE_ERROR

Error code: PR_END_OF_FILE_ERROR

    The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
    Please contact the website owners to inform them of this problem.
```
Ubuntuforums.org Server Status Check
ubuntuforums.org screenshot
Ubuntu ForumsWebsite Name:
ubuntuforums.orgURL Checked:
no responseResponse Time:
~5 minsDown For:
DOWN
Ubuntuforums.org is DOWN for everyone.
It is not just you. The server is not responding...
```

---

### Post by Doug S on 2023-09-13
I spoke to soon. Access to ubuntuforums is very bad for me now.

---

### Post by MAFoElffen on 2023-09-13
@Doug S -- I am near you (near Seattle, WA, USA)...

Yesterday was bad. Early this morning was great.  Now is unusable. About twice as slow as yesterday!

This is what I get at the moment:
```

mafoelffen@msi-ubuntu:~$ mtr -c5 -r www.ubuntuforums.org
Start: 2023-09-13T11:29:28-0700
HOST: msi-ubuntu                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- _gateway                   0.0%     5   51.4  35.9   2.7  84.8  34.3
  2.|-- 96.120.101.109             0.0%     5   13.1  13.3  12.8  14.8   0.8
  3.|-- 24.153.81.253              0.0%     5  137.4  94.7  13.7 137.4  48.2
  4.|-- 69.139.161.185             0.0%     5   26.1  16.3  11.5  26.1   5.7
  5.|-- be-306-arsc1.seattle.wa.s  0.0%     5  124.3  93.1  17.3 173.0  60.3
  6.|-- lag-39.ear2.Seattle1.Leve  0.0%     5   36.4 128.0  20.3 481.9 198.8
  7.|-- [COLOR=#ff0000]ae1.3110.ear4.London2.lev[/COLOR] 80.0%     5  238.4 238.4 238.4 238.4   0.0
  8.|-- swp10.il3-core1.canonical  0.0%     5  153.9 226.1 153.9 287.6  66.3
  9.|-- ubuntuforums.org           0.0%     5  153.3 163.3 153.3 187.5  14.0
mafoelffen@msi-ubuntu:~$ mtr -c5 -r www.ubuntuforums.org
Start: 2023-09-13T11:30:03-0700
HOST: msi-ubuntu                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- _gateway                   0.0%     5    2.1   2.1   1.6   3.2   0.6
  2.|-- 96.120.101.109             0.0%     5   12.0  11.6  10.3  12.9   1.0
  3.|-- 24.153.81.245              0.0%     5   11.0  12.1   9.9  17.9   3.3
  4.|-- 24.124.128.42              0.0%     5   11.1  11.7  11.0  13.3   1.0
  5.|-- 69.139.161.185             0.0%     5   11.2  11.3  10.7  12.8   0.8
  6.|-- be-306-arsc1.seattle.wa.s  0.0%     5   17.3  15.7  14.4  17.3   1.2
  7.|-- lag-39.ear2.Seattle1.Leve  0.0%     5   24.5  18.1  14.9  24.5   3.9
  8.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0
  9.|-- swp10.il3-core1.canonical  0.0%     5  158.5 156.5 155.1 158.5   1.5
 10.|-- ubuntuforums.org           0.0%     5  155.1 155.0 154.6 155.5   0.3
mafoelffen@msi-ubuntu:~$ mtr -c5 -r www.ubuntuforums.org
Start: 2023-09-13T11:30:25-0700
HOST: msi-ubuntu                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- _gateway                   0.0%     5    1.3   2.2   1.3   5.1   1.6
  2.|-- 96.120.101.109             0.0%     5   10.8  12.0  10.8  14.3   1.4
  3.|-- 24.153.81.253              0.0%     5   11.9  15.9  10.7  34.1  10.2
  4.|-- 69.139.161.185             0.0%     5   13.8  15.1  11.3  25.0   5.6
  5.|-- be-306-arsc1.seattle.wa.s  0.0%     5   14.2  18.0  14.2  25.5   4.4
  6.|-- lag-39.ear2.Seattle1.Leve  0.0%     5   15.6  22.6  15.6  42.0  11.1
  7.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0
  8.|-- swp10.il3-core1.canonical  0.0%     5  151.8 152.4 150.7 155.4   1.8
  9.|-- ubuntuforums.org           0.0%     5  155.2 153.0 152.1 155.2   1.3

```
My ISP connection is testing as 247MiB/s dl & 6.25MiB/s ul. I see the current bottleneck in London, right before it gets to Canonical... IDK. (Outside anything that can be controlled.)

---

### Post by ajgreeny on 2023-09-13
It has just taken me about 2 minutes to get to this from the Activity Page link top left of forum pages and most forum pages simply are not loading, or perhaps I'm just getting too impatient and going elsewhere.
It was almost as bad yesterday but not quite.
I have tried out the [https://www.isitdownrightnow.com](https://www.isitdownrightnow.com) site a few times as well as using command ```
ping ubuntuforums.org
``` which I believe is what that website uses and both show that it is the same for everybody.
No doubt it will all come back again to normal speed, but we do seem to have these problems more and more just recently; anyone have ideas why that may be so?

---

### Post by #&amp;thj^% on 2023-09-13
OMG London is under Attack, Now is the time for all good Buntu-er's to come to the Aide of our Forum...
Disclaimer: The above line is not true, it's a joke.
EDIT:Now: 05:32PM Forums seem normal again.

---

### Post by Rubi1200 on 2023-09-14
It has been so painfully slow I was almost ready to throw my laptop at the wall (glad I didn't).

I tried using various VPN servers without success.

Excuse my ignorance, but is there a way to escalate this to Canonical?

---

### Post by Doug S on 2023-09-14
I am getting a lot of these errors today:

```
Proxy Error

The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request

Reason: Error reading from remote server

Additionally, a 502 Bad Gateway error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443
```

and:

```
Service Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.

Additionally, a 503 Service Unavailable error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443
```

I do not know how to escalate to Canonical.

EDIT: response seems good at this moment.

---

### Post by Rubi1200 on 2023-09-14
@Doug S

I also had those the last few times the site has been slow.

---

### Post by MAFoElffen on 2023-09-14
Additional to those, I could not send any PM's last night. It would say: "Forbidden. You do not have permission to use that resource. Error 443.

---

### Post by ajgreeny on 2023-09-14
All seems OK at he moment, 18:45 hrs UTC, but earlier today the site was again unusable for me and could not be pinged just like it was last night when I posted #13.

---

### Post by #&amp;thj^% on 2023-09-14
> **MAFoElffen said:**
> Additional to those, I could not send any PM's last night. It would say: "Forbidden. You do not have permission to use that resource. Error 443.

I got it this morning, tried to reply, but that was like spitting into the wind...LOL
All is well so far.

---

