---
title: "Can not connect to Mailinator through CenturyLink"
date: 2013-08-05
forum: The Cafe
---

### Post by d0006 on 2013-08-05
I can not connect to Mailinator. CenturyLink is my ISP. When I try to connect the connection times out.  I can connect through a proxy.  I have cleared my browser cache.

I am using a ZyXEL PK5000Z DSL modem.  I have searched but I can not find a way to change the DNS.  The current DNSs are: 
[TABLE]
[TR]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
I had no problem connecting before Mailinator changed it's website.

 I am using 12.04 LTS 64-bit. Any ideas how to fix this?
Thanks

---

### Post by Paqman on 2013-08-05
If you can't change your DNS through your router then you can do it in the OS. Click on the network icon and go to your current connection's IPv4 tab. Select "Automatic (DHCP) addresses only" from the drop-down box and enter the DNS you want to use (such as 8.8.8.8 for Google). Then disconnect and reconnect, and you should be using the new DNS.

---

### Post by jonkers2 on 2013-08-05
> **d0006 said:**
> I can not connect to Mailinator. CenturyLink is my ISP. When I try to connect the connection times out.  I can connect through a proxy.  I have cleared my browser cache.

I am using a ZyXEL PK5000Z DSL modem.  I have searched but I can not find a way to change the DNS.  The current DNSs are: 
[TABLE]
[TR]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
I had no problem connecting before Mailinator changed it's website.

 I am using 12.04 LTS 64-bit. Any ideas how to fix this?
Thanks

Find out if it is a DNS problem or a routing problem/block:

Do:
```

wget www.mailinator.com

```
and post the output here.

Here's mine:

```

$ wget www.mailinator.com
--2013-08-05 11:09:34--  http://www.mailinator.com/
Resolving www.mailinator.com (www.mailinator.com)... 207.198.106.56
Connecting to www.mailinator.com (www.mailinator.com)|207.198.106.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘index.html.20’


    [ <=>                                                                                     ] 8,548       --.-K/s   in 0s      


2013-08-05 11:09:35 (35.2 MB/s) - ‘index.html.20’ saved [8548]



```

---

### Post by d0006 on 2013-08-06
Thanks for the replies!
```
foobar@foobar:~$ wget www.mailinator.com
--2013-08-05 23:43:21--  http://www.mailinator.com/
Resolving www.mailinator.com (www.mailinator.com)... 207.198.106.56
Connecting to www.mailinator.com (www.mailinator.com)|207.198.106.56|:80... failed: Connection timed out.
Retrying.

--2013-08-05 23:44:25--  (try: 2)  http://www.mailinator.com/
Connecting to www.mailinator.com (www.mailinator.com)|207.198.106.56|:80... failed: Connection timed out.
Retrying.

--2013-08-05 23:45:30--  (try: 3)  http://www.mailinator.com/
Connecting to www.mailinator.com (www.mailinator.com)|207.198.106.56|:80... 

```
Etc.

Also, if I change the DNS in my OS, how can I check if my requests are actually being sent to the new DNS and not just being sent to the CenturyLink DNS by the router?

Thanks

---

### Post by Paqman on 2013-08-06
Depends which DNS you use. I know OpenDNS have a [test page]("https://www.opendns.com/welcome/") you can hit to see if you're on their system. I'd recommend OpenDNS actually, they're really good for doing your own filtering.

---

### Post by jonkers2 on 2013-08-06
> **d0006 said:**
> Thanks for the replies!
```
foobar@foobar:~$ wget www.mailinator.com
--2013-08-05 23:43:21--  http://www.mailinator.com/
Resolving www.mailinator.com (www.mailinator.com)... 207.198.106.56
Connecting to www.mailinator.com (www.mailinator.com)|207.198.106.56|:80... failed: Connection timed out.
Retrying.

--2013-08-05 23:44:25--  (try: 2)  http://www.mailinator.com/
Connecting to www.mailinator.com (www.mailinator.com)|207.198.106.56|:80... failed: Connection timed out.
Retrying.

--2013-08-05 23:45:30--  (try: 3)  http://www.mailinator.com/
Connecting to www.mailinator.com (www.mailinator.com)|207.198.106.56|:80... 

```
Etc.

Also, if I change the DNS in my OS, how can I check if my requests are actually being sent to the new DNS and not just being sent to the CenturyLink DNS by the router?

Thanks

So: [www.mailinator.com]("http://www.mailinator.com") resolves nicely to it's correct IP address, so your setup has no DNS problem.

As you can't connect on IP-level, someone/something is blocking it. They might be your ISP. Oh, wait, you are on your personal Internet, not on a company or some organisation network?

Here's how to it further analyse it:

```

mtr -nrc2 www.mailinator.com

```

Post the output here. Here's mine:

```

sander@R540:~$ mtr -nrc2 www.mailinator.com
HOST: R540                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    1.6   1.7   1.6   1.8   0.1
  2.|-- 62.45.112.2                0.0%     2    2.6   2.6   2.6   2.6   0.0
  3.|-- 62.45.30.225               0.0%     2    9.7   6.1   2.5   9.7   5.1
  4.|-- 62.45.254.162              0.0%     2    4.9   4.8   4.6   4.9   0.2
  5.|-- 62.45.254.162              0.0%     2    4.6   4.4   4.2   4.6   0.3
  6.|-- 195.69.145.209             0.0%     2    6.3   5.2   4.0   6.3   1.6
  7.|-- 216.187.115.121            0.0%     2  108.3 108.3 108.2 108.3   0.1
  8.|-- 216.187.115.38             0.0%     2  121.8 121.8 121.8 121.8   0.0
  9.|-- 216.187.120.225            0.0%     2  122.1 122.2 122.1 122.2   0.1
 10.|-- 216.187.124.117            0.0%     2  141.7 141.7 141.7 141.8   0.1
 11.|-- 216.187.124.133            0.0%     2  142.3 142.2 142.1 142.3   0.2
 12.|-- 216.187.124.121            0.0%     2  178.5 178.7 178.5 178.8   0.2
 13.|-- 216.187.88.46              0.0%     2  183.0 184.5 183.0 186.1   2.2
 14.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
 15.|-- 207.198.106.56            50.0%     2  180.1 180.1 180.1 180.1   0.0
sander@R540:~$ 

```

---

### Post by d0006 on 2013-08-06
```
foobar@foobar:~$ mtr -nrc2 www.mailinator.com
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1               50.0%     2    1.5   1.5   1.5   1.5   0.0
  2.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
  3.|-- 71.222.249.121            50.0%     2  117.8 117.8 117.8 117.8   0.0
  4.|-- 67.14.24.114              50.0%     2  107.7 107.7 107.7 107.7   0.0
  5.|-- 63.146.26.134              0.0%     2  112.5 141.5 112.5 170.6  41.1
  6.|-- 4.69.147.94               50.0%     2  117.8 117.8 117.8 117.8   0.0
  7.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
  8.|-- 4.69.148.141              50.0%     2  197.7 197.7 197.7 197.7   0.0
  9.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
 10.|-- 4.69.137.30                0.0%     2  164.2 162.2 160.1 164.2   2.9
 11.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
 12.|-- 216.187.89.41              0.0%     2   91.4  89.8  88.2  91.4   2.3
 13.|-- 216.187.88.46              0.0%     2   77.8  94.8  77.8 111.9  24.1
 14.|-- 216.187.88.138             0.0%     2   62.1  79.1  62.1  96.1  24.1
 15.|-- 207.198.106.56             0.0%     1   74.2  74.2  74.2  74.2   0.0
```

This looks bad.  Is this bad?

I am running some torrents so I paused all of them and ran the command 10 times.  I got this every time:
```
foobar@foobar:~$ mtr -nrc2 www.mailinator.com
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    1.6   1.5   1.4   1.6   0.1
  2.|-- 67.42.200.48               0.0%     2   62.5  43.7  24.9  62.5  26.5
  3.|-- 71.222.249.121             0.0%     2   35.7  30.6  25.6  35.7   7.1
  4.|-- 67.14.24.114               0.0%     2   35.0  58.4  35.0  81.8  33.1
  5.|-- 63.146.26.134              0.0%     2   34.6  34.9  34.6  35.3   0.5
  6.|-- 4.69.147.94                0.0%     2   60.1  60.8  60.1  61.5   0.9
  7.|-- 4.69.132.57                0.0%     2   60.0  60.2  60.0  60.4   0.3
  8.|-- 4.69.148.141               0.0%     2   59.9  60.0  59.9  60.1   0.1
  9.|-- 4.69.148.201               0.0%     2   60.0  60.1  60.0  60.3   0.2
 10.|-- 4.69.137.30                0.0%     2   60.0  60.0  59.9  60.0   0.1
 11.|-- 4.69.144.206               0.0%     2   61.0  60.3  59.6  61.0   1.0
 12.|-- 216.187.89.41              0.0%     2   60.9  60.4  59.9  60.9   0.7
 13.|-- 216.187.88.46              0.0%     2   60.8  61.1  60.8  61.5   0.5
 14.|-- 216.187.88.138             0.0%     2   61.7  61.7  61.6  61.7   0.1
 15.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0


```
:confused:
I still can not connect to mailinator.
Thanks for all the help!

---

### Post by sanderj on 2013-08-07
The first mtr looks good, the second does not. How can they be different?

---

### Post by d0006 on 2013-08-08
The ONLY difference between the mtr reports is pausing the torrents.

I was able to connect to mailinator once yesterday but today I can not connect and I get about the same mtr report
```
foobar@foobar:~$ mtr -nrc2 www.mailinator.com
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    1.6   1.5   1.4   1.6   0.1
  2.|-- 67.42.200.48              50.0%     2  611.2 611.2 611.2 611.2   0.0
  3.|-- 71.222.249.121             0.0%     2  712.5 696.8 681.2 712.5  22.1
  4.|-- 67.14.24.114               0.0%     2  718.1 662.7 607.3 718.1  78.4
  5.|-- 63.146.26.134              0.0%     2  663.0 671.5 663.0 680.1  12.1
  6.|-- 4.69.147.94                0.0%     2  660.7 682.1 660.7 703.4  30.2
  7.|-- 4.69.132.57                0.0%     2  628.2 647.2 628.2 666.2  26.8
  8.|-- 4.69.148.141               0.0%     2  503.8 611.2 503.8 718.6 151.9
  9.|-- 4.69.148.201               0.0%     1  682.6 682.6 682.6 682.6   0.0
 10.|-- 4.69.137.26                0.0%     1  605.7 605.7 605.7 605.7   0.0
 11.|-- 4.69.144.142               0.0%     1  679.7 679.7 679.7 679.7   0.0
 12.|-- 216.187.89.41              0.0%     1  716.9 716.9 716.9 716.9   0.0
 13.|-- 216.187.88.46              0.0%     1  640.5 640.5 640.5 640.5   0.0
 14.|-- 216.187.88.138             0.0%     1  523.6 523.6 523.6 523.6   0.0
 15.|-- ???                       100.0     1    0.0   0.0   0.0   0.0   0.0
```
From what little I know about ip/tcp it looks like all the packets I am sending to (or receiving from?) mailinator are dropped at the last hop.
I did find this post but I am not sure if it is relevant:
[http://forums.cox.com/forum_home/internet_forum/f/5/t/1197.aspx](http://forums.cox.com/forum_home/internet_forum/f/5/t/1197.aspx)
Just for fun I put the last few routers into mtr.
This looks very weird:
```
foobar@foobar:~$ mtr -nrc2 216.187.88.138
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    1.6   1.5   1.5   1.6   0.1
  2.|-- 67.42.200.48              50.0%     2  616.1 616.1 616.1 616.1   0.0
  3.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
foobar@foobar:~$ mtr -nrc2 216.187.88.46
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2  157.5 134.6 111.7 157.5  32.4
  2.|-- 67.42.200.48              50.0%     2  652.3 652.3 652.3 652.3   0.0
  3.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
foobar@foobar:~$ mtr -nrc2 216.187.89.41
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    1.4   1.4   1.4   1.5   0.0
  2.|-- 67.42.200.48              50.0%     2  467.3 467.3 467.3 467.3   0.0
  3.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
```
Any suggestions are appreciated.
Thanks!

---

### Post by d0006 on 2013-08-08
I ran mtr a few more times on some of the other ip addresses.  
67.42.200.48 is owned by Quest which is owned by CenturyLink.
```
foobar@foobar:~$ mtr -nrc2 67.42.200.48
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    1.5   1.5   1.4   1.5   0.0
  2.|-- 67.42.200.48              50.0%     2  425.8 425.8 425.8 425.8   0.0
foobar@foobar:~$ mtr -nrc8 67.42.200.48
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     8    1.4   1.5   1.4   1.8   0.1
  2.|-- 67.42.200.48              50.0%     8  447.3 533.9 447.3 679.0 100.6
foobar@foobar:~$ mtr -nrc128 67.42.200.48
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%   128    1.5   3.1   1.4 113.6  11.4
  2.|-- 67.42.200.48              55.5%   128   55.0 389.2  55.0 692.8 109.7
foobar@foobar:~$ mtr -nrc2 71.222.249.121
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    2.3   1.9   1.4   2.3   0.6
  2.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
  3.|-- 71.222.249.121            50.0%     2  557.5 557.5 557.5 557.5   0.0
foobar@foobar:~$ mtr -nrc2 71.222.249.121
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    1.4   2.0   1.4   2.6   0.8
  2.|-- 67.42.200.48              50.0%     2  569.4 569.4 569.4 569.4   0.0
  3.|-- 71.222.249.121            50.0%     2  577.7 577.7 577.7 577.7   0.0
foobar@foobar:~$ mtr -nrc2 71.222.249.121
HOST: foobar                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.0.1                0.0%     2    1.6   1.5   1.5   1.6   0.0
  2.|-- 67.42.200.48              50.0%     2  567.0 567.0 567.0 567.0   0.0
  3.|-- 71.222.249.121            50.0%     2  604.5 604.5 604.5 604.5   0.0
```

---

