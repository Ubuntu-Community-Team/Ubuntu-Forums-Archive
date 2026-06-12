---
title: "Cannot access Tomcat on 8080 outside my lan"
date: 2010-05-24
forum: Server Platforms
---

### Post by rahuijts on 2010-05-24
On my Ubuntu 10.04 lucid lynx server edition machine I have an Apache http server listening on port 80 and today I installed the Funambol server which added an Apache Tomcat server listening on port 8080. From within my lan I can reach both servers, but from outside the lan I can only reach the http server on port 80 and not the Funambol server on port 8080. I get a time out message instead.

In my router I have setup port forwarding, such that both ports 80 and 8080 get forwarded to my server machine. Must Tomcat be told to listen to external requests? Is my server listening on port 8080 only for requests inside the lan? Or is there some authorization that fails when I try to visit from outside my lan?

Here is some netstat output, I don't know if the differences between the 80 line and the 8080 line are relevant:
```
remon@compaq:~$ sudo netstat -nlp | grep 80
tcp        0      0 0.0.0.0:8009            0.0.0.0:*               LISTEN      1778/java
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      1778/java
tcp        0      0 127.0.0.1:8005          0.0.0.0:*               LISTEN      1778/java
tcp6       0      0 :::80                   :::*                    LISTEN      719/apache2
udp        0      0 127.0.0.1:32800         0.0.0.0:*                           1762/java
udp        0      0 0.0.0.0:68              0.0.0.0:*                           809/dhclient3
```

---

### Post by cdenley on 2010-05-24
Your server which is listening on TCP 8080 is listening for connections on all interfaces. If a TCP connection cannot be established on that port, then either you configured iptables to filter it, or the traffic is not reaching your server. Perhaps your ISP filters port 8080.

---

### Post by arrrghhh on 2010-05-24
Yea, looks like you have it setup correctly... Either your router isn't forwarding the information on correctly, or your ISP is blocking the traffic.

---

### Post by rahuijts on 2010-05-24
When I do a port scan, for example on [www.pcflank.com](www.pcflank.com), then the report says both port 80 and port 8080 are open. Does this rule out an ISP filter on port 8080? If not, how would I check this? And how can I check if my iptables are configured the right or wrong way?

---

### Post by arrrghhh on 2010-05-24
Hrm... I would think that would be sufficient.

Have you tried this - turn off that other tomcat service, switch your apache or another service to 8080 (like SSH for example) and see if that works?  That would rule out ISP, which it sounds like you have...

---

### Post by rahuijts on 2010-05-24
Okay I hope tested it the right way: I shut down the Funambol/Tomcat server, then I edited apache2.conf and the sites-available/default.conf so that 80's are now 8080. Then I restarted the Apache http server. From within my lan, I now get the apache default page (saying "It works!") on port 8080 and from outside my lan, I still get the time out. Does this confirm that my ISP filters out 8080?

---

### Post by arrrghhh on 2010-05-24
Well it confirms *something* is blocking it.  Could be firewall on the Ubuntu box - do you use UFW or did you setup the firewall at all?

Also, router - double, triple, whatever-check the port forward settings there.  It sounds like you got port 80 working, compare with those settings.

The last option would be the traffic is being blocked by your provider.  I can't think of any other roadblocks at the time being, but if you're ISP isn't blocking port 80 they're almost certainly not blocking 8080...

---

### Post by rahuijts on 2010-05-24
The status of ufw is "inactive", I did not set up any firewall on the ubuntu box.

The port forwarding on my router is quite easy to set up, and in fact I copied the settings for the http server and changed the port numbers. To be sure I just quadriple checked.

---

### Post by cdenley on 2010-05-25
If an external server says port 8080 is open, then you are accepting TCP connections on that port. You should not be getting connection timeouts. When you say you cannot establish a connection a port 8080 "from outside the lan", are you actually attempting to connect from outside your LAN, os simply connecting to your router's WAN IP from inside your LAN? There is a difference between the two.

---

### Post by EmanresuusernamE on 2010-05-26
Have you tried changing Tomcat to use a different port that you know works as a test? To me, it's sounding like Tomcat is misconfigured, as Apache works on port 8080, but Tomcat does not.

Also, I agree with cdenley, if you're on your LAN and attempting to connect using your public IP address, some routers/modems don't handle the traffic properly.  Especially if it's an AT&T modem.  For the most part, they won't loop back your traffic back through itself properly from my experiences.

---

### Post by cdenley on 2010-05-26
> **EmanresuusernamE said:**
> Have you tried changing Tomcat to use a different port that you know works as a test? To me, it's sounding like Tomcat is misconfigured, as Apache works on port 8080, but Tomcat does not.


He said that he could not access either server on port 8080 from outside. He said they both gave them connection timeouts, which is inconsistent with the fact that he said a port scanning service indicated port 8080 was open, which is why I assume he isn't actually attempting to connect from outside his network as he had indicated.

---

### Post by rahuijts on 2010-05-26
If I visit my external IP with a machine inside my lan, then I indeed get results. But I use the browser of my cellphone to test. On my cellphone I can specifically choose whether to use my lan (over WiFi) or my 3G mobile phone network. As you might guess, the latter works only for the Apache server on port 80 and not for Tomcat on port 8080. Connecting over the WiFi, I can visit both, which I also considered as from within the network.

---

### Post by cdenley on 2010-05-26
> **rahuijts said:**
> If I visit my external IP with a machine inside my lan, then I indeed get results. But I use the browser of my cellphone to test. On my cellphone I can specifically choose whether to use my lan (over WiFi) or my 3G mobile phone network. As you might guess, the latter works only for the Apache server on port 80 and not for Tomcat on port 8080. Connecting over the WiFi, I can visit both, which I also considered as from within the network.

Have you tried an external connection other than your 3G network? If [www.pcflank.com](www.pcflank.com) can connect on port 8080 but your 3G network cannot, then perhaps your problem is with your 3G network. Can you access this site from your phone?
[http://hekto.med.unc.edu:8080/](http://hekto.med.unc.edu:8080/)

---

### Post by rahuijts on 2010-05-27
> **cdenley said:**
> Have you tried an external connection other than your 3G network? If [www.pcflank.com]("http://www.pcflank.com") can connect on port 8080 but your 3G network cannot, then perhaps your problem is with your 3G network. Can you access this site from your phone?
[http://hekto.med.unc.edu:8080/](http://hekto.med.unc.edu:8080/)

I get a time out on that site as well (unless I leave out the port part of the url). Does this mean my 3G network is crippled and unable to connect to any website through port 8080? Is that normal?

---

### Post by cdenley on 2010-05-27
> **rahuijts said:**
> I get a time out on that site as well (unless I leave out the port part of the url). Does this mean my 3G network is crippled and unable to connect to any website through port 8080? Is that normal?

Apparently. I don't think it is typical. I can access websites over port 8080 on my 3G network.

---

### Post by rahuijts on 2010-05-27
> **cdenley said:**
> Apparently. I don't think it is typical. I can access websites over port 8080 on my 3G network.

Thanks, I have asked my 3G network provider (Vodafone) why I can't visit sites on port 8080. As soon as they reply (should be within two working days), I will post back here. Thanks again for narrowing this down for me.

---

### Post by arrrghhh on 2010-05-27
Do you have to pipe all your web traffic thru a proxy?  I know some crappy providers like Cricket do that.  Sprint leaves me wide open, I haven't had any traffic blocked thru it.

---

### Post by rahuijts on 2010-05-27
> **arrrghhh said:**
> Do you have to pipe all your web traffic thru a proxy?  I know some crappy providers like Cricket do that.  Sprint leaves me wide open, I haven't had any traffic blocked thru it.

No, not that I know. There are some crappy providers in my country, but Vodafone has quite a good record and charges accordingly. I got an automatic response to my question, stating that I wil receive an answer within one working day. We'll see.

---

### Post by rahuijts on 2010-05-28
> **arrrghhh said:**
> Do you have to pipe all your web traffic thru a proxy?  I know some crappy providers like Cricket do that.  Sprint leaves me wide open, I haven't had any traffic blocked thru it.

Well I had actually sort of given up already and uninstalled Funambol, but you were right. Vodafone answered that their proxy might not be able to cope with port 8080 and pointed me to instructions on how to turn of the proxy. Now I can visit the URL cdenly suggested to test, so I will do a reinstall this weekend and have another try. Thanks very much for the support!

---

