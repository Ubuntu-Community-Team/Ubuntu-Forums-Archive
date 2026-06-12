---
title: "When UFW is enabled I can not ping"
date: 2011-07-10
forum: Server Platforms
---

### Post by pcarlos853 on 2011-07-10
Hello,

I am running Ubuntu Server 10.10. I have enabled UFW with the following rules:
```

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
22                         ALLOW       Anywhere
8080/tcp                   ALLOW       Anywhere

10.0.0.66 22/tcp           ALLOW OUT   Anywhere
80/tcp                     ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
53/udp                     ALLOW OUT   Anywhere
465/tcp                    ALLOW OUT   Anywhere
10.0.0.62 3389             ALLOW OUT   10.0.0.65
10.0.0.60 22/tcp           ALLOW OUT   Anywhere
10.0.0.90 3389             ALLOW OUT   10.0.0.65
```

I am unable to ping from the server. What do I have to add to ping from the server? Do I need to Allow from 127.0.0.1 to Anywhere? I would like this server to be as secure as possible.

Thanks,
Carlos

---

### Post by pcarlos853 on 2011-07-11
Bump  

Whenever I try to ping I get:
```
ping: sendmsg: Operation not permitted
```

However when I turn UFW off I am able to ping without any issues.

Thanks
Carlos

---

### Post by spynappels on 2011-07-11
Try 

```
sudo ufw allow icmp
```

If that does not work, you need to see whether the /etc/ufw/before.rules is blocking your ICMP packets.

EDIT:  You havn't been using Firestarter at all, have you? That can really mess stuff up too....

---

### Post by pcarlos853 on 2011-07-11
Thanks for the quick reply!

When I try sudo ufw allow icmp I get:
```
ERROR: Could not find a profile matching 'icmp'
```

before.rules is set to:
```
# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```

I have not installed firestarter. 

Thanks
Carlos

---

### Post by pcarlos853 on 2011-07-13
I am thinking about upgrading to 11.04, do you think that this would resolve the problem? The reason I need to ping out is that I am running Nagios and nagios needs the ability to ping. I also must have a firewall for security. I am having this problem on all my Ubuntu computers (including workstations (10.10)). 

Before I try install 11.04 does anyone have  any other suggestions that I can try.

Your help is MUCH appreciated!

---

### Post by pcarlos853 on 2011-07-14
I was able to solve my problem with the info below from [http://www.kelvinism.com/howtos/enable-icmp-through-ufw/](http://www.kelvinism.com/howtos/enable-icmp-through-ufw/)


                                                                                      [Enable ICMP through UFW]("http://www.kelvinism.com/howtos/enable-icmp-through-ufw/")                             **Published on Sept. 21, 2010 **

                                                                                                   I like using Ubuntu's UFW command, but today I needed to allow outgoing ICMP.  I received results as so:
  $ ping 4.2.2.2 PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data. ping: sendmsg: Operation not permitted ping: sendmsg: Operation not permitted ping: sendmsg: Operation not permitted   
 To allow outbound icmp I edited 'before.rules' and added the following lines.
 $ sudo vi /etc/ufw/before.rules 
# allow outbound icmp -A ufw-before-output -p icmp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT -A ufw-before-output -p icmp -m state --state ESTABLISHED,RELATED -j ACCEPT

---

### Post by satish_j on 2012-05-18
> **pcarlos853 said:**
> [http://www.kelvinism.com/howtos/enable-icmp-through-ufw/](http://www.kelvinism.com/howtos/enable-icmp-through-ufw/)

Thanks,that link helped me as well..:)
However,it would have been better if this can be achieved through a ufw command..

---

