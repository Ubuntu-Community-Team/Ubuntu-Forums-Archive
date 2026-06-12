---
title: "Akamai Issue, undesired connections, speed down, ..."
date: 2012-08-09
forum: Security
---

### Post by expcoderxrrg on 2012-08-09
Amazing Akamai Issue have a really smart technology to jump firewall restriction. I have make a white list for may firewall it mean nothing get out. This solution stop Akamai for some days, but now it is connected again jumping the firewall white list. Akamai install a new process server on my computer and send info to Akamai  server using different ip to my computer assigned ip to jump firewall. Akamai Issue have a proved advanced technologies to jump firewall. 

History:
 Day X
 Akamai detected jumping firewall again white list created



 Akamai blocked ok
 


 Day X+1
 
 Akamai fin a way to open a connection jumping firewall:
 


 More references:
 [http://www.matveev.se/net/akamai.htm](http://www.matveev.se/net/akamai.htm)
 
 [http://www.linuxquestions.org/questions/general-10/contact-at-akamai-akamaitechnologies-for-complaints-831481/](http://www.linuxquestions.org/questions/general-10/contact-at-akamai-akamaitechnologies-for-complaints-831481/)

 [http://ubuntuforums.org/showthread.php?t=1717448&highlight=akamai](http://ubuntuforums.org/showthread.php?t=1717448&highlight=akamai)


[URL="http://ubuntuforums.org/showthread.php?t=1717448&highlight=akamai"]
[/URL]

---

### Post by claracc on 2012-08-09
I don't understand what your problem is.

Is this a support question?

Please explain clearly the problem in order to get help, if it is what you are looking for.

---

### Post by expcoderxrrg on 2012-08-09
Problem: I have slow connection and setup a firewall to increase speed but some softwares try jump firewall restrictions and connect.

For example one of there gnome-panel weather software:

Tcpdump >>>

    0x0000:  0000 0200 0000 0000 0000 0000 0000 0800  ................
    0x0010:  4500 01b7 4250 0000 3a11 76a9 c837 8003  E...BP..:.v..7..
    0x0020:  c837 b5ca 0035 a983 01a3 70ed 94c9 8180  .7...5....p.....
    0x0030:  0001 0004 0008 0008 0777 6561 7468 6572  .........weather
    0x0040:  046e 6f61 6103 676f 7600 0001 0001 c00c  .noaa.gov.......
    0x0050:  0005 0001 0000 0384 0020 0777 6561 7468  ...........weath
    0x0060:  6572 046e 6f61 6103 676f 7609 6564 6765  er.noaa.gov.edge
    0x0070:  7375 6974 6503 6e65 7400 c02e 0005 0001  suite.net.......
    0x0080:  0000 3735 0011 0561 3137 3131 0167 0661  ..75...a1711.g.a
    0x0090:  6b61 6d61 69c0 49c0 5a00 0100 0100 0000  kamai.I.Z.......
    0x00a0:  1400 0417 43f3 19c0 5a00 0100 0100 0000  ....C...Z.......
    0x00b0:  1400 0417 43f3 12c0 6000 0200 0100 002f  ....C...`....../
    0x00c0:  2f00 0603 6e30 67c0 62c0 6000 0200 0100  /...n0g.b.`.....
    0x00d0:  002f 2f00 0603 6e36 67c0 62c0 6000 0200  .//...n6g.b.`...
    0x00e0:  0100 002f 2f00 0603 6e33 67c0 62c0 6000  ...//...n3g.b.`.
    0x00f0:  0200 0100 002f 2f00 0603 6e34 67c0 62c0  .....//...n4g.b.
    0x0100:  6000 0200 0100 002f 2f00 0603 6e32 67c0  `......//...n2g.
    0x0110:  62c0 6000 0200 0100 002f 2f00 0603 6e35  b.`......//...n5
    0x0120:  67c0 62c0 6000 0200 0100 002f 2f00 0603  g.b.`......//...
    0x0130:  6e37 67c0 62c0 6000 0200 0100 002f 2f00  n7g.b.`......//.
    0x0140:  0603 6e31 67c0 62c0 cd00 0100 0100 0006  ..n1g.b.........
    0x0150:  ff00 04cc 02f1 acc0 bb00 0100 0100 0031  ...............1
    0x0160:  3200 04cc 02f1 adc0 9700 0100 0100 0031  2..............1
    0x0170:  3200 04c8 3e2c 23c0 f100 0100 0100 0085  2...>,#.........
    0x0180:  8e00 04cc 02f1 aec0 df00 0100 0100 0085  ................
    0x0190:  8e00 04c1 6c58 c3c1 0300 0100 0100 0006  ....lX..........
    0x01a0:  ff00 04cc 02f1 a5c0 a900 0100 0100 0031  ...............1
    0x01b0:  3200 04cc 02f1 aec1 1500 0100 0100 0006  2...............
    0x01c0:  ff00 04cc 02f1 af                        .......



    0x0000:  0000 0200 0000 0000 0000 0000 0000 0800  ................
    0x0010:  4500 01b7 e113 0000 3a11 d7e5 c837 8003  E.......:....7..
    0x0020:  c837 b5ca 0035 828e 01a3 1b20 118c 8180  .7...5..........
    0x0030:  0001 0004 0008 0008 0777 6561 7468 6572  .........weather
    0x0040:  046e 6f61 6103 676f 7600 0001 0001 c00c  .noaa.gov.......
    0x0050:  0005 0001 0000 0384 0020 0777 6561 7468  ...........weath
    0x0060:  6572 046e 6f61 6103 676f 7609 6564 6765  er.noaa.gov.edge
    0x0070:  7375 6974 6503 6e65 7400 c02e 0005 0001  suite.net.......
    0x0080:  0000 3735 0011 0561 3137 3131 0167 0661  ..75...a1711.g.a
    0x0090:  6b61 6d61 69c0 49c0 5a00 0100 0100 0000  kamai.I.Z.......
    0x00a0:  1400 0417 43f3 19c0 5a00 0100 0100 0000  ....C...Z.......
    0x00b0:  1400 0417 43f3 12c0 6000 0200 0100 002f  ....C...`....../
    0x00c0:  2f00 0603 6e35 67c0 62c0 6000 0200 0100  /...n5g.b.`.....
    0x00d0:  002f 2f00 0603 6e31 67c0 62c0 6000 0200  .//...n1g.b.`...
    0x00e0:  0100 002f 2f00 0603 6e32 67c0 62c0 6000  ...//...n2g.b.`.
    0x00f0:  0200 0100 002f 2f00 0603 6e30 67c0 62c0  .....//...n0g.b.
    0x0100:  6000 0200 0100 002f 2f00 0603 6e33 67c0  `......//...n3g.
    0x0110:  62c0 6000 0200 0100 002f 2f00 0603 6e36  b.`......//...n6
    0x0120:  67c0 62c0 6000 0200 0100 002f 2f00 0603  g.b.`......//...
    0x0130:  6e37 67c0 62c0 6000 0200 0100 002f 2f00  n7g.b.`......//.
    0x0140:  0603 6e34 67c0 62c1 1500 0100 0100 0006  ..n4g.b.........
    0x0150:  ff00 04cc 02f1 acc0 df00 0100 0100 0031  ...............1
    0x0160:  3200 04cc 02f1 adc0 cd00 0100 0100 0031  2..............1
    0x0170:  3200 04c8 3e2c 23c0 9700 0100 0100 0085  2...>,#.........
    0x0180:  8e00 04cc 02f1 aec0 bb00 0100 0100 0085  ................
    0x0190:  8e00 04c1 6c58 c3c1 0300 0100 0100 0006  ....lX..........
    0x01a0:  ff00 04cc 02f1 a5c0 f100 0100 0100 0031  ...............1
    0x01b0:  3200 04cc 02f1 aec0 a900 0100 0100 0006  2...............
    0x01c0:  ff00 04cc 02f1 af                        .......

---

### Post by expcoderxrrg on 2012-08-10
Akamai servers are also used by faceboock, gnome-pannel and a lot of other common used app. Clouds services tend to be confused with intrusions often, for example my gnome-pannel try to use akamai clouds to get weather info. Also I have verify, a normal behavior in clouds is asap as it receive a request, try to find open ports in host, reverse dns.
 

 It works at this way:
 

 gnome-panel weather software or other akamai based softwares try connect to clouds jumping firewall if possible asap as connection to Internet detected on system. Then cloud akamai services detect host requests, call dns-rollback and begin try open connection from akamai to host searching open ports in ranges not commonly used  452620 &#8230;  452670 for example. This is a normal pattern in cloud services, I have see the same in other could services. But this patter is the same as a Trojan intrusion.
 

 In my case I don't care what they see or monitor, but slow down the Internet speed with unrequested connections.

---

### Post by Wim Sturkenboom on 2012-08-13
They don't jump firewalls; what you block will be blocked, end of story. As explained in the first article you linked to, they use multiple ip addresses. The solution for you is simple; add the new IP addresses (and / or ports) to iptables.

On a side note:

I did notice this type of behavior with a site a while ago (I think it was facebook, but not 100% sure) that I wanted to block using iptables.

The 'problem' is that iptables is ip address based and not name based. Using firestarter as my GUI frontend to iptables and using hostnames in the configuration of firestarter result in a DNS lookup of the host names. The ip addresses that are returned define what is blocked; in the case of the earlier mentioned site, I found that the results of the DNS lookup could change between starts of firestarter (as earlier mentioned site has multiple servers).

---

### Post by expcoderxrrg on 2012-08-13
Akamai is a CDN it could be useful in some case the best solution is a firewall by applications.

Issue solution (Thanks to unSpawn from linuxquestions.org ):

[Program Guard]("http://pgrd.sourceforge.net/") *was* an application level firewall for GNU/Linux as were [FireFlier]("http://fireflier.sourceforge.net/") and [TuxGuardian]("http://tuxguardian.sourceforge.net/"). They've all gone.  The only remaining one AFAIK is [LeopardFlower]("http://leopardflower.sourceforge.net/"). I won't comment on them (*apart from taking obsolescence as an indication of lack of actual use*) and I've never needed to use them. Maybe they work for you.

Full story
[http://www.linuxquestions.org/questions/showthread.php?p=4751643#post4751643](http://www.linuxquestions.org/questions/showthread.php?p=4751643#post4751643)
[http://www.linuxquestions.org/questions/showthread.php?p=4751643#post4751643](http://www.linuxquestions.org/questions/showthread.php?p=4751643#post4751643)

---

### Post by expcoderxrrg on 2012-08-14
A propose to global monitoring network:
 

 CDN and other Clouds based services are often used in all the places I guess at least 90 % of Internet user access every day one or two of the main providers.
 

 Solution:
 

 Store user IP, user-dns, time and session information of facebook, weather services, gmail, yahoo, hotmail, &#8230; and any other services that uses Clouds. This will provide a digital identity for one person.
 

 Handle huge volume of data will be important, and some optimizations will be useful.
 

 Use case, how monitor a single user (concrete example):
 

 Suppose Ronald login on facebook, Akamai CDN will store:
 

 Ronald digital ID, stored on Cloud:
 +++++++++++++++++++++++++++++++++++++++++++++++++++++++
 IP: 152.10.27.175
 user-dns: var15.ppp9.ispprovider.es
 time: 11/27/2012 15:03:25
 facebook session id: jhfs3fd345dfsdf9898948rf767udst73shf74wr8
 +++++++++++++++++++++++++++++++++++++++++++++++++++++++
 

 Now is important know the same user continue online with the same session at least.
 So we should made a trick and with small frequency verify  session id and update digital ID.
 

 Trick solutions:
 
[LIST=1]
[*]Leave a thread on 	browser requesting service to akamai or cloud posting session ID.
[*]In client software 	app(chat messengers) is more easy, just send periodically session 	data.
[/LIST]
 

 Now we can know about Roland user:
 

 Start connection day 11/27/2012 15:03:25 with IP 152.10.27.175 and remains online 2 hours. One day latter get connected again  11/28/2012 11:22:20 with IP 12.107.27.17.
 

 But we have more about Roland: Facebook name, email address, other facebook and emails and accounts used, &#8230;.
 

 Suppose Roland is a bad person and we have rights to track it, as soon we detect it is online we can now request to Roland ISP capture all info.

---

