---
title: "Is my HTTP traffic filtered ?"
date: 2008-11-13
forum: Security
---

### Post by Mba7eth on 2008-11-13
Morning all, 

     I have linksys wireless router. unfortunately i can't access admin page or see the config. However, Each time i try to visit a HTTP page it goes forever and at the end fail. If i try the same page from a proxy server everything goes fine. All other protocal can connect normally. i.e. HTTPS, IRC, FTP, Torrents, MSN. 
I just want some one to help me to make sure that my packets are not filters. 

I have captured some http traffic with tcpdump. 
Please check this link [http://pastebin.com/m2f6a708f]("http://pastebin.com/m2f6a708f")I hope it will be useful. I really didn't understand much of it. 

If this tcpdump output is not enough or such problem can't be discovered with it. please If you can, guide me for a tool. 


Thanks alot. :)

---

### Post by rosv on 2008-11-13
Is the problem still there if you use an external proxy server that accepts connections on port 80?

---

### Post by Dr Small on 2008-11-13
Could I suggest restarting the router? I used to have this problem every time I attempted to access the admin console for it, and it has just recently got over that epidemic...

---

### Post by Mba7eth on 2008-11-13
rosv 
 yes this is the only i can connect to port 80. i use a proxy with port 3128. 

Dr Small 
    i did that once and today ... but still same problem

---

### Post by rosv on 2008-11-13
Did I understand you correctly if http traffic on any other port than 80 is ok?

---

### Post by Dr Small on 2008-11-13
> **Mba7eth said:**
> rosv 
 yes this is the only i can connect to port 80. i use a proxy with port 3128. 

Dr Small 
    i did that once and today ... but still same problem
What happens if you try to connect to it without going through the Squid proxy?

---

### Post by Kinstonian on 2008-11-13
```
...
12:28:54.312412 IP wiki.answers.com.http > 192.168.1.114.49490: P **2897:2921(24)** ack 666 win 65535 <nop,nop,timestamp 12305701 814638490>
12:28:54.312491 IP 192.168.1.114.49490 > wiki.answers.com.http: . **ack 1** win 65535 <nop,nop,timestamp 814638492 12305700>
12:28:54.725341 IP wiki.answers.com.http > 192.168.1.114.49490: P **11609:11668(59)** ack 666 win 65535 <nop,nop,timestamp 12305702 814638492>
12:28:54.725417 IP 192.168.1.114.49490 > wiki.answers.com.http: . **ack 1** win 65535 <nop,nop,timestamp 814638493 12305700>
12:28:54.749274 IP wiki.answers.com.http > 192.168.1.114.49490: . 1449:1461(12) ack 666 win 65535 <nop,nop,timestamp 12305702 814638493>
12:28:54.749334 IP 192.168.1.114.49490 > wiki.answers.com.http: . **ack 1** win 65535 <nop,nop,timestamp 814638493 12305700>
...
```

I'm no expert in traffic analysis, but from the looks of it your computer isn't getting some traffic sent by the web server and the web server isn't resending it.  The first packet containing data sent by the webserver was bytes 2897:2921 (24 bytes sent total) but what about bytes 1:2896?  Those were never seen and your computer continues to say ACK 1 saying it acknowledges byte 1 and asking for a retransmission of missing data but never gets it, the server just continues sending retransmissions of bytes 1449:1461.  I could be completely wrong though, I'm no expert.  Maybe someone else has a different take.

Posting the firewall rules if enabled would be of use.  Also what happens if you type in a terminal.

```
$telnet www.google.com 80
$GET / HTTP/1.1
$<ENTER>
$<ENTER>
$<ENTER>
```

Do you see the HTML code?

---

### Post by cariboo on 2008-11-13
Have you reset your router by holding the reset button located on the back of the router, I believe you have to hold the button for about a minute to get the device to reset.

Jim

---

### Post by Mba7eth on 2008-11-13
rosv : 
   I have changed the proxy config of my browser. and i use ip address of external proxy and port 3128 instead of the default port 80. thngs work perfectly when the proxy configs are on. otherwise i can't receive port 80 traffic.  

Dr small 
   i can't open any http page. and some times i get only partial of the html. 
   However, HTTPS works perfectly always. 

Cariboo907 
   i can't reset it to default sittings for some reasons. but i may only reboot it. and i did that several times.


Kinstonian 
   thanks for the usefull info :)

---

### Post by Mba7eth on 2008-11-16
> **Kinstonian said:**
> ```
...
12:28:54.312412 IP wiki.answers.com.http > 192.168.1.114.49490: P **2897:2921(24)** ack 666 win 65535 <nop,nop,timestamp 12305701 814638490>
12:28:54.312491 IP 192.168.1.114.49490 > wiki.answers.com.http: . **ack 1** win 65535 <nop,nop,timestamp 814638492 12305700>
12:28:54.725341 IP wiki.answers.com.http > 192.168.1.114.49490: P **11609:11668(59)** ack 666 win 65535 <nop,nop,timestamp 12305702 814638492>
12:28:54.725417 IP 192.168.1.114.49490 > wiki.answers.com.http: . **ack 1** win 65535 <nop,nop,timestamp 814638493 12305700>
12:28:54.749274 IP wiki.answers.com.http > 192.168.1.114.49490: . 1449:1461(12) ack 666 win 65535 <nop,nop,timestamp 12305702 814638493>
12:28:54.749334 IP 192.168.1.114.49490 > wiki.answers.com.http: . **ack 1** win 65535 <nop,nop,timestamp 814638493 12305700>
...
```

I'm no expert in traffic analysis, but from the looks of it your computer isn't getting some traffic sent by the web server and the web server isn't resending it.  The first packet containing data sent by the webserver was bytes 2897:2921 (24 bytes sent total) but what about bytes 1:2896?  Those were never seen and your computer continues to say ACK 1 saying it acknowledges byte 1 and asking for a retransmission of missing data but never gets it, the server just continues sending retransmissions of bytes 1449:1461.  I could be completely wrong though, I'm no expert.  Maybe someone else has a different take.

Posting the firewall rules if enabled would be of use.  Also what happens if you type in a terminal.

```
$telnet www.google.com 80
$GET / HTTP/1.1
$<ENTER>
$<ENTER>
$<ENTER>
```

Do you see the HTML code?

No I didn't receive any html code if the link is not congested.
However, if the link is congested I do some times receive HTML code. I think this because the Access point is not that robust to grantee 100% blocking a specific service. IF it is very busy it will not check some packets received. This is my own conclusion. :) 


So can i assure that Port 80 is filtered based on the above info.

---

### Post by Kinstonian on 2008-11-16
I was curious about whether telnet worked because if it did, it would suggest that perhaps there is some odd problem with your web browser.  Since telnet seems to work as much as FireFox, maybe the problem is with your OS.  Some odd OS configuration might be the problem if other computers on your network have no problem accessing web sites.  I just think it would be odd for your router to only be causing HTTP problems for one computer on your network.  Is that what's happening?  Does the problem affect other computers, or if you boot to a LiveCD and surf the web from that?

From what you just posted, it seems like you're saying your router has the ability to monkey with HTTP traffic.  Have you been able to verify that by reading the manual or logging in to it?  Generally routers are able to carry out the filtering or other features they offer without causing problems.  If there is some kind of HTTP filter, I don't think it would of let so much HTTP traffic from the web server to your computer, or have let you establish a connection then make it fail.  So from the packet data you provided, I don't think it's purposely filtering HTTP.

---

