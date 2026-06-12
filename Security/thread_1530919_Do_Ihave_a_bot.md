---
title: "Do Ihave a bot?"
date: 2010-07-14
forum: Security
---

### Post by greybeard62 on 2010-07-14
I'm not a guru, user for three years.  Three laptops Ubuntu, 2 are 9.10, this one 10.04.  I have something constantly sending requests to 2 ip addresses, 174.129.241.144 and 174.129.193.12,port 443,HTTPS.

For time being I used Firestarter because it was easy to block to the 174.129.0.0-174.129.255.255.  This is the amazonaws cloud ec2 junk.  Reporting to them is worthless.  

My question is how to find the bot and remove it.  I've searched log files (don't really know what to look for), occasionally I see 2 users not 1 when only I am using the machines.  Whatever it is it is blocked but constantly generating connect attempts to these 2 addresses. 

Jul 14 10:23:33 billbo-laptop kernel: [ 3218.270346] Outbound IN= OUT=wlan0 SRC=192.168.1.103 DST=174.129.193.12 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=47533 DF PROTO=TCP SPT=40691 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 14 10:23:36 billbo-laptop kernel: [ 3221.268049] Outbound IN= OUT=wlan0 SRC=192.168.1.103 DST=174.129.193.12 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=47534 DF PROTO=TCP SPT=40691 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 14 10:25:36 billbo-laptop kernel: [ 3341.598852] Outbound IN= OUT=wlan0 SRC=192.168.1.103 DST=174.129.241.144 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=20495 DF PROTO=TCP SPT=34821 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 14 10:25:39 billbo-laptop kernel: [ 3344.596049] Outbound IN= OUT=wlan0 SRC=192.168.1.103 DST=174.129.241.144 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=20496 DF PROTO=TCP SPT=34821 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 14 10:27:39 billbo-laptop kernel: [ 3464.730213] Outbound IN= OUT=wlan0 SRC=192.168.1.103 DST=174.129.241.144 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=58592 DF PROTO=TCP SPT=34824 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul 14 10:27:42 billbo-laptop kernel: [ 3467.732158] Outbound IN= OUT=wlan0 SRC=192.168.1.103 DST=174.129.241.144 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=58593 DF PROTO=TCP SPT=34824 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 



Thanks for any help.

---

### Post by wacky_sung on 2010-07-14
Are you using any browser connecting to any of the encrypted webpage?

> DPT=443

Destination Port Transmission : 443 

[http://en.wikipedia.org/wiki/HTTP_Secure](http://en.wikipedia.org/wiki/HTTP_Secure)

---

### Post by uRock on 2010-07-14
Does the other host return any ack packets? Do you have SNORT installed? If yes, does snort give an alert?

---

### Post by yeleek on 2010-07-14
Both of those addresses are Amazon EC2.

You ever setup cloud computing?  messed around with the ubuntu cloud installations?

[http://www.ubuntu.com/cloud/public](http://www.ubuntu.com/cloud/public)

Done anything even in dev with Amazon's EC2 services?

Are you using Ubuntu one?

---

### Post by yeleek on 2010-07-14
Not an ubuntu one user myself, but [https://174.129.193.12/](https://174.129.193.12/) is using a godaddy cert issued to fs-2.one.ubuntu.com

Going out on a limb ;-) - not really sounding like a bot.

edit - and the other address's cert is '  fs-1.one.ubuntu.com , [www.fs-1.one.ubuntu.com](www.fs-1.one.ubuntu.com)  '

---

### Post by greybeard62 on 2010-07-14
no
and yes, port 443, HTTPS

---

### Post by greybeard62 on 2010-07-14
Yes, both these addresses are amazon ec2 and yes, I have ubuntu one cloud turned one and used.  BTW, the cloud works with the entire range 174.129.0.0-174.255.255 blocked for outbound traffic and service denied this range for port 443.

---

### Post by yeleek on 2010-07-14
So... why do you think you have a bot?  And if you want to use the service why are you blocking access to its ranges?

---

### Post by greybeard62 on 2010-07-14
> **yeleek said:**
> Not an ubuntu one user myself, but [https://174.129.193.12/](https://174.129.193.12/) is using a godaddy cert issued to fs-2.one.ubuntu.com

Going out on a limb ;-) - not really sounding like a bot.

edit - and the other address's cert is '  fs-1.one.ubuntu.com , [www.fs-1.one.ubuntu.com](www.fs-1.one.ubuntu.com)  '
OK, so ubuntu one cloud is through amazon ec2 servers?  Doing a search on the domain name returned a lot of supposed abuse by amazonaws servers; ie open ports, not secure, security violations logged.  No problem here, don't really need ubuntu one cloud, simply shared some pics with a friend this way and a few non-important files for recipes etc - all secured per instructions and pswd.- I didn't find the cert, that's a heads up, thanks.

---

### Post by yeleek on 2010-07-14
Fair enough

FYI - you want to check in the future.

You know this is running 443 i.e. https.  So all i did was a whois and then a wget like this

wget [https://174.129.193.12](https://174.129.193.12)
--2010-07-14 17:28:05--  [https://174.129.193.12/](https://174.129.193.12/)
Connecting to 174.129.193.12:443... connected.
ERROR: cannot verify 174.129.193.12's certificate, issued by `/C=US/ST=Arizona/L=Scottsdale/O=GoDaddy.com, Inc./OU=http://certificates.godaddy.com/repository/CN=Go Daddy Secure Certification Authority/serialNumber=07969287':
  Unable to locally verify the issuer's authority.
ERROR: certificate common name `**fs-2.one.ubuntu.com**' doesn't match requested host name `174.129.193.12'.
To connect to 174.129.193.12 insecurely, use `--no-check-certificate'.

---

