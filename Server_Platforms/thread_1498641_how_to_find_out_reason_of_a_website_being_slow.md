---
title: "how to find out reason of a website being slow"
date: 2010-06-01
forum: Server Platforms
---

### Post by tapas_mishra on 2010-06-01
I am having a website on a reverse proxy environment which is running slow.
Here are a few statistics

 recorded the website loading time in the Chrome developer tools time line section and
based on what I observed

following page elements take more than 100 ms on the website
jquery checks
113 ms [http://192.168.1.5:8080/eduCommons/p...achekey0517.js](http://192.168.1.5:8080/eduCommons/p...achekey0517.js)

244ms [http://192.168.1.5:8080/eduCommons/p...achekey1443.js](http://192.168.1.5:8080/eduCommons/p...achekey1443.js)
247ms [http://192.168.1.5:8080/eduCommons/p...chekey5402.css](http://192.168.1.5:8080/eduCommons/p...chekey5402.css)

like this there are some more css and page elements which have taken
100ms or 200ms in their GET request from server.

on this link
[http://www.chicagostyleseo.com/2010/...-site-is-slow/](http://www.chicagostyleseo.com/2010/...-site-is-slow/)
they mentioned what Google has defined as a slow website following
words are mentioned.

"Google has made it clear that any process that takes more than 100
milliseconds (1/10 of a second) is too long"

So that means the website is slow.


I have attached a snapshot 
[http://farm5.static.flickr.com/4048/...87025551_b.jpg](http://farm5.static.flickr.com/4048/...87025551_b.jpg)
you can see results of page elements loading slow.
In fact I have asked a few people to access the website on internet and they too reported the same.


One thing which I observed was the webserver where the site is hosted if I try to do an SSH to it ,it takes a longer time than any other server.

Also I checked LAN speed on Server A on above diagram.
ethtool eth2 | less
```

Settings for eth2:
       Supported ports: [ TP ]
       Supported link modes:   10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Full
       Supports auto-negotiation: Yes
       Advertised link modes:  10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Full
       Advertised pause frame use: No
       Advertised auto-negotiation: Yes
       Link partner advertised link modes:  Not reported
       Link partner advertised pause frame use: No
       Link partner advertised auto-negotiation: No
       Speed: 100Mb/s
       Duplex: Full
       Port: Twisted Pair
       PHYAD: 1
       Transceiver: internal
       Auto-negotiation: on
       MDI-X: Unknown
       Supports Wake-on: g
       Wake-on: g
       Link detected: yes

```

and speed of LAN here shows to be 100Mbps
```

ethtool eth2 | grep -i speed
       Speed: 100Mb/s 
```

and the webserver (192.168.1.5 in above diagram)where the site has been hosted 
```

ethtool eth0 
Settings for eth0:
No data available

```
and
ethtool eth0 | grep -i speed
did not gave any output you can see above it is clear.

Is there a way I can find out how much time it takes to connect via SSH on my server also 
the site is slow because of the data transfer being slow or the webserver being giving a slow response that is what is coming to my mind.

What more should I do to check it and how can I over come this problem?

---

### Post by tapas_mishra on 2010-06-01
In a step by step way again

1) The site [http://site5.abc.com](http://site5.abc.com) was loading slowly 
(Some page elements showed 411ms in Google Developer tools snapshot [here]("http://farm5.static.flickr.com/4018/4659120495_b53bf97a58_b.jpg"))
2) From my laptop checked [http://192.168.1.5:8080/eduCommons](http://192.168.1.5:8080/eduCommons) 

( got a few page elements 211 ms and one was 770 ms a snapshot for the 700 ms attached [here]("http://farm5.static.flickr.com/4042/4658588197_f4dd59b9fd_b.jpg"))

3) Then to check if the site is loading slow on CentOS server itself I did


ssh -L 8080:localhost:8080 root@192.168.1.5

4) Then from my laptop when above ssh connection on step 3 was alive

  [http://localhost:8080/eduCommons](http://localhost:8080/eduCommons)
and saw a page element loading at 411 ms.


If I am not wrong then by step 4 it is confirming that site is slow on server itself.
I would like to clear that the server is not running any thing other than eduCommons .

---

### Post by cdenley on 2010-06-01
I'm not familiar with educommons. What exactly do those times represent? The time the server takes to process the request? The time it takes for the server to receive the request, process it, then send the response? The time it takes for the browser to parse the downloaded file? I believe the "100ms or 200ms" standard you were referring to relates server-side processing, and doesn't include data transfer or browser execution/parsing.

By the way, the links in your first post are broken.

---

### Post by tapas_mishra on 2010-06-01
I am running the site5.abc.com where educommons is installed on an internal IP which is behind a reverse proxy.
The configuration is like this 

```

                                |--------------192.168.1.1
                                |           (site1.abc.com)
                                |         (Ubuntu 10.04 JeOS)Guest OS on Ubuntu KVM
                                |           
                                |            
  (Public IP )                  |
     (KVM)                      |
            A-------------------|
(reverse proxy server)          |
  (192.168.1.25)                |
(Ubuntu 10.04 JeOS)             |--------------192.168.1.5
                                |             
                                |           (site5.abc.com)
                                |          (CentOS 5.5 JeOS)Guest OS on Ubuntu KVM
                                |            
                                |--------------192.168.1.19
                                             (My Laptop) 
                                            (Ubuntu 9.04)


```
JeOS == Just Enough Operating System


> **cdenley said:**
> I'm not familiar with educommons. 
eduCommons is a content management system
real time use can be seen here on a correctly set up site. 
[http://ocw.nd.edu/](http://ocw.nd.edu/)
The above is not my website but I am trying to achieve some thing similar.
[http://educommons.com/](http://educommons.com/)
I could  not find a .deb package so I had to create a CentOS guest on Ubuntu server.
Check the installation page here 
[http://educommons.com/documentation/how-to/installation-instructions](http://educommons.com/documentation/how-to/installation-instructions).
> **cdenley said:**
> 
What exactly do those times represent? The time the server takes to process the request? The time it takes for the server to receive the request, process it, then send the response? The time it takes for the browser to parse the downloaded file?
These times were observed on a client browser on LAN from my Ubuntu Laptop
 when I tried to access a page in a format like 
http://<IP of eduCommons server:8080>/eduCommons
My laptop has Ubuntu 9.04 and the Dell Server where this site has been hosted
 using Ubuntu server 10.04 with KVM.
Have multiple guest Operating systems.


> **cdenley said:**
> 
 I believe the "100ms or 200ms" standard you were referring to relates server-side processing, and doesn't include data transfer or browser execution/parsing
Yes as google defines a website as slow 

"Google has made it clear that any process that takes more than 100
milliseconds (1/10 of a second) is too long"

> **cdenley said:**
> 
By the way, the links in your first post are broken.

For  links  starting with [http://192.168.1.5](http://192.168.1.5) leave that they are just internal IPs.
Site site5.abc.com is just a dummy name.
So it obviously will not work.

Check the flikr photo snapshot links they should be working.
This is the snapshot to 703 ms
[http://farm5.static.flickr.com/4042/4658588197_f4dd59b9fd_b.jpg](http://farm5.static.flickr.com/4042/4658588197_f4dd59b9fd_b.jpg)
and 411 ms 
[http://farm5.static.flickr.com/4018/4659120495_b53bf97a58_b.jpg](http://farm5.static.flickr.com/4018/4659120495_b53bf97a58_b.jpg)

One of the Guest OS is CentOS 5.On which eduCommons is installed.


On Server A 
I have a virtual host for eduCommons server which has some entries like this 
```


 ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>
        ProxyPass / http://192.168.1.5:8080/eduCommons
        ProxyPassReverse / http://192.168.1.5:8080/eduCommons

```

and on CentOS machine where I actually have the website you can browse it locally or on LAN
[http://192.168.1.5:8080/eduCommons](http://192.168.1.5:8080/eduCommons)
the 411 ms and 701 ms snapshot I reported are taken from LAN only using Google Chrome Developer tools.

When I tried to access the site in Chrome from my laptop running Ubuntu 9.04

---

### Post by cdenley on 2010-06-01
> **tapas_mishra said:**
> 
These times were observed on a client browser on LAN from my Ubuntu Laptop
 when I tried to access a page in a format like 
http://<IP of eduCommons server:8080>/eduCommons
My laptop has Ubuntu 9.04 and the Dell Server where this site has been hosted
 using Ubuntu server 10.04 with KVM.
Have multiple guest Operating systems.

That still doesn't answer my question. If those times include network latency, that makes a huge difference! Also, when you're talking about milliseconds, perhaps tunneling the data over a layer of encryption would increase the latency.

Also, the links in your first post are still broken, including your reference about the google standard.

---

### Post by tapas_mishra on 2010-06-01
> **cdenley said:**
> That still doesn't answer my question. If those times include network latency, that makes a huge difference! 

Sorry about that these times do not include network latency.Or may be I am not able to explain clearly.
If I open [www.ubuntuforums.org](www.ubuntuforums.org) in my laptop running Ubuntu 9.04 in Chrome 
and in before opening the forum I press Control+Shift+I 
I will get same time lines as I have mentioned.
If you want to know more about these times you can check these youtube videos

	
[	 http://www.youtube.com/watch?v=RhaWYQ44WEc&feature=player_embedded#!]("http://www.youtube.com/watch?v=RhaWYQ44WEc&feature=player_embedded#!")
[	http://www.youtube.com/watch?v=OxW1dCjOstE&feature=player_embedded]("http://www.youtube.com/watch?v=OxW1dCjOstE&feature=player_embedded")

> **cdenley said:**
> 
Also, when you're talking about milliseconds, perhaps tunneling the data over a layer of encryption would increase the latency.

Also, the links in your first post are still broken, including your reference about the google standard.
I am giving the link again
[http://www.chicagostyleseo.com/2010/03/caffeine%E2%80%99s-need-for-speedhow-to-know-if-your-site-is-slow/]("http://www.chicagostyleseo.com/2010/03/caffeine%E2%80%99s-need-for-speedhow-to-know-if-your-site-is-slow/")

In case you are not able to get to the link still in Google type following words
"Google has made it clear that any process that takes more than 100milliseconds (1/10 of a second) is too long"
the first link is the one which I am referring to.
[URL="http://www.google.co.in/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=Google+has+made+it+clear+that+any+process+that+takes+more+than+100milliseconds+(1/10+of+a+second)+is+too+long"]
http://www.google.co.in/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=Google+has+made+it+clear+that+any+process+that+takes+more+than+100milliseconds+(1/10+of+a+second)+is+too+long
[/URL]

Let me know if you are not able to get them.
I got your tunneling through an encrpyted layer is there any other way I should do that?
If links are still not working let me know I will paste bin them.

---

### Post by cdenley on 2010-06-01
> **tapas_mishra said:**
> Sorry about that these times do not include network latency.Or may be I am not able to explain clearly.
If I open [www.ubuntuforums.org](www.ubuntuforums.org) in my laptop running Ubuntu 9.04 in Chrome 
and in before opening the forum I press Control+Shift+I 
I will get same time lines as I have mentioned.


Any load times calculated on the client-side would include network latency. It would be more of a test of how fast the browser can receive the data, not how fast a server can process a request.

---

### Post by tapas_mishra on 2010-06-01
> **cdenley said:**
> Any load times calculated on the client-side would include network latency. It would be more of a test of how fast the browser can receive the data, not how fast a server can process a request.

Ok even I was thinking the same.
Even then 700ms it should not take this much time to load a page element at least on LAN.
What can I do to check the connection so that it does not loads slow on the host.
Or if you can suggest me some thing that can be tried I will do that.

---

### Post by cdenley on 2010-06-01
> **tapas_mishra said:**
> Ok even I was thinking the same.
Even then 700ms it should not take this much time to load a page element at least on LAN.
What can I do to check the connection so that it does not loads slow on the host.
Or if you can suggest me some thing that can be tried I will do that.

Well, I couldn't help you to improve data transfers over your network. I would try logging the time it takes to serve requests in apache, send it some requests on 127.0.0.1 using netcat or wget, then check those response times to eliminate network latency from your testing.

add this to your vhost configuration
```

LogFormat "%a %D %>s %B" resp
CustomLog /var/log/apache2/resp.log resp

```

then (replacing "/jquery-cachekey0517.js" with whatever file you want to request)
```

sudo /etc/init.d/apache2 reload
echo -e "GET /jquery-cachekey0517.js HTTP/1.0\n"|nc -q 1 127.0.0.1 80 > /dev/null
tail /var/log/apache2/resp.log

```
The last line should show you:
```

127.0.0.1 [response time in microseconds] 200 [response data size in bytes]

```

---

### Post by BobVila on 2010-06-01
I don't mean to be frustratingly vague, but I haven't seen any data from you from which I could derive a more specific answer. If both web requests and ssh are slow, I think you need to take a look at your DNS settings... I had the same problem with a reverse proxy setup. It was caused by improper DNS configs by one of my ISPs.

---

### Post by Vegan on 2010-06-01
There could be any of 100 places that make serving web pages slow. If a part is coming from a server that is saturated the browser will wait for it to surface.

A lot of sites use multiple servers to provide content. Any one of them can affect overall performance.

---

### Post by tapas_mishra on 2010-06-02
> **cdenley said:**
> Well, I couldn't help you to improve data transfers over your network. I would try logging the time it takes to serve requests in apache, send it some requests on 127.0.0.1 using netcat or wget, then check those response times to eliminate network latency from your testing.

add this to your vhost configuration
```

LogFormat "%a %R %>s %B" resp
CustomLog /var/log/apache2/resp.log resp

```

I did what you suggested above on Server A (reverse proxy server) and when restarted apache2 I got an error 
/etc/init.d/apache2 restart
```

 * Restarting web server apache2
 * We failed to correctly shutdown apache, so we're now killing all running apache processes.
 This is almost certainly suboptimal, so please make sure your system is working 
as you'd expect now!
 ... waiting Syntax error on line 22 of /etc/apache2/sites-enabled/site5.abc.com:
Unrecognized LogFormat directive %R

```

Let me know if there is some thing more I can try.I will.


> **BobVila said:**
> I don't mean to be frustratingly vague, but I haven't seen any data from you from which I could derive a more specific answer. If both web requests and ssh are slow, I think you need to take a look at your DNS settings... I had the same problem with a reverse proxy setup. It was caused by improper DNS configs by one of my ISPs.

What data do you need can you tell me some thing specific I would try to post.I do not have 
a DNS for the machine where these things are hosted.All this is happening on a LAN which is in same subnet as my Laptop.

To do ssh I do not do 
ssh site5.abc.com
rather on LAN I type
ssh 192.168.1.5 -l root
and other Ubuntu Guest Vms on KVM I login by this
ssh 192.168.1.4 -l root 




> **Vegan said:**
> There could be any of 100 places that make serving web pages slow. If a part is coming from a server that is saturated the browser will wait for it to surface.

A lot of sites use multiple servers to provide content. Any one of them can affect overall performance.
Can you tell me any few of those 100 possibilities.That will help.
I am right now trying to understand a tool Cacti to test network latency I do not know whether it is right or wrong
but I will search a few more.
But in the configuration for which I am reporting the problem CentOS is running as KVM guest operating system on physically same server where Ubuntu 10.4 is installed on same hard disk.
We are not using the image from SAN or so.

I will try to post what ever you wish to have a look at.
Let me know what do you want to be tested.


To give a better picture 
picking the KVM host, a physically different host connected to the same LAN, one KVM Ubuntu guest and the Centos guest. That's four hosts in total which could help get a better picture.



The IP of KVM host 
192.168.1.25
a physically different host connected to same lan that is my laptop its IP is
192.168.1.19
one KVM Ubuntu Guest IP 192.168.1.3
one CentOS KVM Guest IP 192.168.1.5
Gateway of our LAN is 192.168.1.100
Broadcast address 192.168.1.255


this is the output of ifconfig -a on KVM host  IP 192.168.1.25 
 ```

br0       Link encap:Ethernet  HWaddr 00:26:b9:82:42:38  
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe82:4238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:708557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:539011259 (539.0 MB)  TX bytes:35527402 (35.5 MB)

eth0      Link encap:Ethernet  HWaddr 00:26:b9:82:42:34  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:36 Memory:d6000000-d6012800 

eth1      Link encap:Ethernet  HWaddr 00:26:b9:82:42:36  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 Memory:d8000000-d8012800 

eth2      Link encap:Ethernet  HWaddr 00:26:b9:82:42:38  
          inet6 addr: fe80::226:b9ff:fe82:4238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1379925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:231617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:648807177 (648.8 MB)  TX bytes:46621420 (46.6 MB)
          Interrupt:32 Memory:da000000-da012800 

eth3      Link encap:Ethernet  HWaddr 00:26:b9:82:42:3a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Memory:dc000000-dc012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2068028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2068028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:520647177 (520.6 MB)  TX bytes:520647177 (520.6 MB)

virbr0    Link encap:Ethernet  HWaddr 2e:39:f6:fb:0d:97  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::2c39:f6ff:fefb:d97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:130708 (130.7 KB)

vnet0     Link encap:Ethernet  HWaddr 7a:b9:fd:d5:7f:d5  
          inet6 addr: fe80::78b9:fdff:fed5:7fd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1119769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:185492 (185.4 KB)  TX bytes:527473740 (527.4 MB)

vnet1     Link encap:Ethernet  HWaddr 8e:73:62:8a:b3:a0  
          inet6 addr: fe80::8c73:62ff:fe8a:b3a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1174609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:9763076 (9.7 MB)  TX bytes:578656367 (578.6 MB)

vnet2     Link encap:Ethernet  HWaddr 4e:5a:28:fb:e9:48  
          inet6 addr: fe80::4c5a:28ff:fefb:e948/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1119750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:206935 (206.9 KB)  TX bytes:527458567 (527.4 MB)

vnet3     Link encap:Ethernet  HWaddr 0e:36:c3:be:06:4d  
          inet6 addr: fe80::c36:c3ff:febe:64d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1120644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:292858 (292.8 KB)  TX bytes:527910427 (527.9 MB)


```


Then the output of ifconfig -a on CentOS virtual machine IP 192.168.1.5
```

eth0      Link encap:Ethernet  HWaddr 52:54:00:7F:22:31  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fe7f:2231/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1179960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:581017267 (554.1 MiB)  TX bytes:9768881 (9.3 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3383153 (3.2 MiB)  TX bytes:3383153 (3.2 MiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

output of ifconfig -a on Ubuntu Guest on KVM host IP 192.168.1.3
```

eth0      Link encap:Ethernet  HWaddr 52:54:00:24:7c:2d  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fe24:7c2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:460440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:487608416 (487.6 MB)  TX bytes:300613 (300.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2279453 (2.2 MB)  TX bytes:2279453 (2.2 MB)

virbr0    Link encap:Ethernet  HWaddr a6:39:19:8d:b5:74  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::a439:19ff:fe8d:b574/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2663 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:90785 (90

```

output of ifconfig -a on another host attached to same LAN that is my laptop 192.168.1.19

```

eth0      Link encap:Ethernet  HWaddr 00:23:ae:38:83:0d  
          inet addr:192.168.1.19  Bcast:192.168.1.255 
            Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe38:830d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10195166 (10.1 MB)  TX bytes:1065810 (1.0 MB)
          Interrupt:251 Base address:0x8000 



eth1      Link encap:Ethernet  HWaddr 00:26:5e:30:1f:a5  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe30:1fa5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:654
          TX packets:21 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1168 (1.1 KB)  TX bytes:5703 (5.7 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158 (158.0 B)  TX bytes:158 (158.0 B)

pan0      Link encap:Ethernet  HWaddr 82:5e:3f:02:d1:74  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 9a:1e:04:2b:3b:8d  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::981e:4ff:fe2b:3b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:4030 (4.0 KB)


```


output of route -n from Ubuntu host which is running KVM (IP 192.168.1.25)
```


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0    0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
0.0.0.0         192.168.1.100  0.0.0.0         UG    100    0        0 br0

```

and output of arp -a  from the ubuntu host running KVM which on page 1 of this post is server A
is (IP 192.168.1.25) 
```

site4 (192.168.1.5) at 52:54:00:7f:22:31 [ether] on br0
? (192.168.100.100) at 00:17:5a:d9:99:3f [ether] on br0
site3.local (192.168.1.3) at 52:54:00:1f:df:11 [ether] on br0
site2.local (192.168.1.2) at 52:54:00:24:7c:2d [ether] on br0
tapas-laptop.local (192.168.1.19) at 00:23:ae:38:83:0d [ether] on br0
site1.local (192.168.1.1) at 52:54:00:58:dc:c0 [ether] on br0

```



arp -a on the CentOS guest (192.168.1.5)

```

? (192.168.1.100) at 00:17:5A:D9:99:3F [ether] on eth0
server.site.com (192.168.1.25) at 00:26:B9:82:42:38 [ether] on eth0
? (192.168.1.19) at 00:23:AE:38:83:0D [ether] on eth0

```





and route -n on this CentOS guest 192.168.1.5
```

 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.100  0.0.0.0         UG    0      0        0 eth0

```




arp  -a on Ubuntu Guest on KVM


```

arp -a
tapas-laptop.local (192.168.1.19) at 00:23:ae:38:83:0d [ether] on eth0
server.site.com (192.168.1.25) at 00:26:b9:82:42:38 [ether] on eth0

```

on my laptop IP 192.168.1.19

arp -a 
```

arp -a
server.site.com (192.168.1.25) at 00:26:b9:82:42:38 [ether] on eth0
site1.local (192.168.1.1) at 52:54:00:24:7c:2d [ether] on eth0
site5.local (192.168.1.5) at 52:54:00:7f:22:31 [ether] on eth0
? (192.168.1.100) at 00:17:5a:d9:99:3f [ether] on eth0

```

and route -n on my laptop IP 192.168.1.19
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
172.17.100.0    0.0.0.0         255.255.252.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.100  0.0.0.0         UG    0      0        0 eth0

```
To resolve this I tried to use netcat


one the CentOS server
when I executed
```

nc -v -v -l -n -p 2222
usage: nc [-46DdhklnrStUuvzC] [-i interval] [-p source_port]
	  [-s source_ip_address] [-T ToS] [-w timeout] [-X proxy_version]
	  [-x proxy_address[:port]] [hostname] [port[s]]

```
Then I tried this on CentOS server 
```

nc -v -v -n  -l 2222 > /dev/null 
Connection from 192.168.1.19 port 2222 [tcp/*] accepted

```
From my laptop 
```

 time yes | nc -v -v -n 192.168.1.5 2222
Connection to 192.168.1.5 2222 port [tcp/*] succeeded!
^C

real	0m33.522s
user	0m0.316s
sys	0m0.064s

```
but here I could not understand what is the amount of data transferred (as above tutorial says it to multiply by 8) so that I can measure the network speed.

Let me know what ever is needed I will post the output here.
I have to get this problem resolved.I will post a solution once this gets resolved.

---

### Post by tapas_mishra on 2010-06-02
To measure response time on*[http://site5.abc.com](http://site5.abc.com)
*(is it because reverse proxy is taking longer time to contact plone (that is what educommons is running on)
as compared to other hosts which are running apache
*or there is some thing actually which is making it slow.)

I  disabled educommons  * temporarily that disabled plone.
Then I accessed [http://site5.abc.com](http://site5.abc.com) (Now only apache was running on this CentOS server)

and the response time this time was similar to the response which you will get if you access other vhosts 
running on reverse proxy. 

So this now leads to following conclusion
 reverse proxy is taking longer time to contact plone as
compared to time it takes to contact when CentOS server was running on  apache
this is what is making slow.


There are many other webservers running on different KVM Guest Operating Systems using apache and I do not have any such problem on them.

Just wanted to confirm if this correct or I should try some thing else.
How can I find response time from a web server or what exactly I do need to do to be able to find response time.
In the above post cdenly mentioned a format but it gave error so some thing was what I missed let me know if some one has any suggestion.
I feel I am a bit closer to the solution.

---

### Post by tapas_mishra on 2010-06-02
> **cdenley said:**
> Well, I couldn't help you to improve data transfers over your network. I would try logging the time it takes to serve requests in apache, send it some requests on 127.0.0.1 using netcat or wget, then check those response times to eliminate network latency from your testing.

add this to your vhost configuration
```

LogFormat "%a %R %>s %B" resp
CustomLog /var/log/apache2/resp.log resp

```

After getting some error as you said I 
Googled and came across this [link]("http://www.ducea.com/2008/02/06/apache-logs-how-long-does-it-take-to-serve-a-request/")
I added 
```

LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %T/%D" combined

```
if this is what you were referring to.But there was nothing in resp.log after I tried to access the site.
Or there is some thing else I should check.
I did above on CentOS machine I had to add in httpd.conf
and the Reverse Proxy server in apache2.conf or should this be done in vhost configuration file?

---

### Post by cdenley on 2010-06-02
Sorry, that should be "%D", not "%R".
[http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats)

---

### Post by tapas_mishra on 2010-06-03
I enabled %D as you said in /etc/httpd/conf/httpd.conf
```

LogFormat "%a %D %>s %B" resp
CustomLog /var/log/httpd/site_in_question-resp_log resp

```
but after hitting the website from different ISPs I saw there was no log in
```

/var/log/httpd/site_in_question-resp_log resp
```
as expected.
I thought that it might be permission so it I changed
```

chown apache:apache /var/log/httpd/site_in_question-resp_log
```
I did in vhost configuration of file on CentOS Guest OS on Ubuntu Server 10.04

On the other hand I tried to do the same on reverse proxy server 
and then apache failed to restart.
Upon checking I found
a2enmod mod_log_config
```


ERROR: Module mod_log_config does not exist!

```
[Searched]("http://www.google.co.in/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=ERROR:+Module+mod_log_config+does+not+exist!") but any thing fruitful did not came.
As per your apache documentation page I searched for this file
```

find / -name mod_log_config.c
```
but it was not there.
eduCommons uses a Webserver Plone to host it is not running on apache so I think we need to measure response time of plone.

It is like this 

 ```

  Server A --------------------Server B (site running eduCommons on Plone)
(running apache reverse        (back end server)
 proxy) 

```

Server A and B are on same physical machine.
B is a guest Operating System on A.

---

### Post by tapas_mishra on 2010-06-03
Ok after reading [this page ]("http://prefetch.net/blog/index.php/2007/01/02/measuring-apache-request-processing-time/")

I added 
```

<IfDefine RequestTime>
     Header set X-Request-Received: %t
     Header set X-Request-Processing-Time: %D
</IfDefine>

```

I am able to see some response log. in /var/log/httpd/site-in-question-resp
Now tell me what should I post 

```


192.168.1.5 3062 403 5043
192.168.1.5 2826 403 5043

```
What does this tell me ?

After this I tried 
```


echo -e "GET /jquery-cachekey0517.js HTTP/1.0\n"|nc -q 1 127.0.0.1 80 > /dev/null
nc: invalid option -- q
usage: nc [-46DdhklnrStUuvzC] [-i interval] [-p source_port]
	  [-s source_ip_address] [-T ToS] [-w timeout] [-X proxy_version]
	  [-x proxy_address[:port]] [hostname] [port[s]]
-bash: echo: write error: Broken pipe

```
As you said in a previous reply.
I checked the man page of nc there was no option -q
I also checked this page
http://linux.die.net/man/1/nc

---

### Post by cdenley on 2010-06-03
> **tapas_mishra said:**
> Ok after reading [this page ]("http://prefetch.net/blog/index.php/2007/01/02/measuring-apache-request-processing-time/")

I added 
```

<IfDefine RequestTime>
     Header set X-Request-Received: %t
     Header set X-Request-Processing-Time: %D
</IfDefine>

```

I am able to see some response log. in /var/log/httpd/site-in-question-resp
Now tell me what should I post 

```


192.168.1.5 3062 403 5043
192.168.1.5 2826 403 5043

```
What does this tell me ?

After this I tried 
```


echo -e "GET /jquery-cachekey0517.js HTTP/1.0\n"|nc -q 1 127.0.0.1 80 > /dev/null
nc: invalid option -- q
usage: nc [-46DdhklnrStUuvzC] [-i interval] [-p source_port]
	  [-s source_ip_address] [-T ToS] [-w timeout] [-X proxy_version]
	  [-x proxy_address[:port]] [hostname] [port[s]]
-bash: echo: write error: Broken pipe

```
As you said in a previous reply.
I checked the man page of nc there was no option -q
I also checked this page
[http://linux.die.net/man/1/nc](http://linux.die.net/man/1/nc)

With lucid, it comes with netcat-openbsd, which won't work without the "q" option. Hardy came with netcat-traditional, which doesn't use the "q" option, but it should just ignore it. What are you using?
```

apt-cache policy netcat-openbsd
apt-cache policy netcat-traditional

```

Apparently your LAN requests take 3ms. That doesn't seem too bad.

What kind of apache configuration is that? Are you using ubuntu?

---

### Post by tapas_mishra on 2010-06-03
> **cdenley said:**
> With lucid, it comes with netcat-openbsd, which won't work without the "q" option. Hardy came with netcat-traditional, which doesn't use the "q" option, but it should just ignore it. What are you using?
The Site in Question is hosted on a CentOS server running as Guest Operating System on Ubuntu 10.04 as KVM host.
They are running on same physical machine.

 CentOS Guest OS lets call B
and Ubuntu 10.04 (server edition with Eucalyptus)
 lets call A (it is running a hypervisor KVM)

> **cdenley said:**
> 
```

apt-cache policy netcat-openbsd
apt-cache policy netcat-traditional

```

Which server should I run this command ?
CentOS does not comes with apt-cache.
I executed on Server A
```

 apt-cache policy netcat-openbsd
netcat-openbsd:
  Installed: 1.89-3ubuntu2
  Candidate: 1.89-3ubuntu2
  Version table:
 *** 1.89-3ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status

```
and second command also on Ubuntu 10.04 server edition.
```

apt-cache policy netcat-traditional
netcat-traditional:
  Installed: (none)
  Candidate: 1.10-38
  Version table:
     1.10-38 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/universe Packages

```

On Ubuntu 10.04 (server edition) which is host for all the Guest Operating Systems
There are many websites running like this using Guest Operating Systems.On same physical machines.
Response time of all of them is satisfactory.They all are running on apache2 on Ubuntu 10.04 server edition.
Only this one about which I am asking is a problem.
> **cdenley said:**
> 
Apparently your LAN requests take 3ms. That doesn't seem too bad.

Please tell me how or which output string in my reply tells you this.

> **cdenley said:**
> 
What kind of apache configuration is that? 
It is reverse proxy Apache2.

You can understand it better by following diagram

```

 Server A --------------------Server B (site running eduCommons on Plone)
(running apache reverse        (back end server)
 proxy)
```

Server A and B are on same physical machine.
B is a guest Operating System on A.

Operating System on Server B is CentOS 5.5 
Operating System on Server A is Ubuntu 10.04 server edition.
eduCommons is a content management system.
You check about it [here.]("http://educommons.com/documentation/faq/question-1")

So for the site to be accessible on internet on Server A in above diagram
I have in /etc/apache2/sites-enabled/site5.abc.com
```

ProxyPass / http://192.168.1.5:8080/eduCommons
ProxyPassReverse / http://192.168.1.5:8080/eduCommons

```



> **cdenley said:**
> Are you using ubuntu?
Yes all Operating system including Guest are Ubuntu 10.04 server editions.
This one about which I am asking is running on CentOS.
Educommons is using Plone as a webserver and not Apache2.
It responds on Lan by 
```

http://192.168.1.5:8080/eduCommons

```


I am also giving one more output
```

webcache in following output is referring to port 8080
[code]

# netstat -tap 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address               Foreign Address             State       PID/Program name   
tcp        0      0 site5.siteinquestion.:xprint-server *:*                         LISTEN      5224/python2.4      
tcp        0      0 *:hello-port                *:*                         LISTEN      1742/rpc.statd      
tcp        0      0 *:sunrpc                    *:*                         LISTEN      1706/portmap        
tcp        0      0 *:webcache                  *:*                         LISTEN      5229/python2.4      
tcp        0      0 site5.abc.com:smtp        *:*                         LISTEN      2036/sendmail: acce 
tcp        0      0 site5.siteinquestion:x11-ssh-offset *:*                         LISTEN      18012/0             
tcp        0      0 site5.siteinquestion.:xprint-server site5.abc.com:56072       ESTABLISHED 5224/python2.4      
tcp        0      0 192.168.1.5:webcache     192.168.1.19:60533        ESTABLISHED 5229/python2.4      
tcp        0      0 site5.abc.com:56072       site5.siteinquestion.:xprint-server ESTABLISHED 5229/python2.4      
tcp        0      0 192.168.1.5:webcache     serverA.siteinquestion.com:55012 ESTABLISHED 5229/python2.4      
tcp        0      0 192.168.1.5:webcache     serverA.siteinquestion.com:44424 ESTABLISHED 5229/python2.4      
tcp        0      0 192.168.1.5:38380        someserver.siteinquestion.com:domain TIME_WAIT   -                   
tcp        0      0 192.168.1.5:38381        someserver.siteinquestion.com:domain TIME_WAIT   -                   
tcp        0      0 192.168.1.5:38378        someserver.siteinquestion.com:domain TIME_WAIT   -                   
tcp        0      0 192.168.1.5:38379        someserver.siteinquestion.com:domain TIME_WAIT   -                   
tcp        0      0 192.168.1.5:webcache     blackberry-e63a.somdomain.:35588 ESTABLISHED 5229/python2.4      
tcp        0      0 *:http                      *:*                         LISTEN      18140/httpd         
tcp        0      0 *:ssh                       *:*                         LISTEN      1984/sshd           
tcp        0      0 localhost6.l:x11-ssh-offset *:*                         LISTEN      18012/0             
tcp        0      0 *:https                     *:*                         LISTEN      18140/httpd         
tcp        0      0 ::ffff:192.168.1.5:ssh   jishnub08:53195             ESTABLISHED 18012/0             

```

Above 192.168.1.19 is my laptop
192.168.1.5 is Server B
192.168.1.1 is Server A
by default eduCommons uses a webserver known as Plone it is running on Port 8080.
Will it make sense If I try to make apache listen to port 8080.
On Server B.
I observed if I disabled eduCommons and only apache was running on CentOS in this setup the response time was comparable with my other websites which are running on Ubuntu 10.04 Guest Operating System.In this reverse Proxy Setup.
I faced a similar problem in past when I tried on one of the hosts another server i.e. Geronimo and the result of the website where I used it was response time was similarly slow.

I did read complete [documentation you posted.]("http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats")

After this  in file 
```

/etc/httpd/conf/httpd.conf 

```
on the CentOS Guest OS I added
```


LogFormat "%{X-Forwarded-For}i %D %t %T %v %O %b %A %B" resp

```
and also in <VirtualHost> definition on CentOS server
added  a line 
```


CustomLog /var/log/httpd/site5.abc.com-resp_log resp

```
but there was no  log on CentOS server in 
```

/var/log/httpd/site5.abc.com-resp_log 
```

The behaviour of disabling eduCommons and  Apache running on CentOS is based on user experience.The response was fast.
I wish if I can log the response time in both the cases so I could have posted here.
Let me know if you have any suggestion.

---

### Post by cdenley on 2010-06-03
I already told you the format of the log.
```

192.168.1.5 **3062** 403 5043
192.168.1.5 **2826** 403 5043

```
%D is the response time in microseconds. See the link I posted earlier.

---

### Post by tapas_mishra on 2010-06-03
Ok I was getting confused with the numbers 403 and other.
Thanks for clearing that out.
But the question remains same.

---

### Post by cdenley on 2010-06-03
What question? You can configure that logging for whatever apache server you want to test the response of. If netcat works differently on CentOS, I can't help you with that. Perhaps try leaving out the "q" option. Also, you should probably try sending requests which don't give a 403 error (access denied).

---

### Post by tapas_mishra on 2010-06-03
After reading documentation
[url=http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats]Apache
Log Format documentation[/url]

I added in
```

/etc/httpd/conf/httpd.conf

```
a Line

```

LogFormat "%v %{X-Forwarded-For}i %D %l %u %t \"%r\" %>s %b" resp

```

and in VirtualHost section added
```

CustomLog /var/log/httpd/site_in_question-resp_log resp

```

restarted httpd and checked the logs
to my surprise I did not found any thing in
```

CustomLog /var/log/httpd/site_in_question-resp_log resp

```
when I tried to browse from internet.
Did I do some mistake above ?
Or what is the correct way to get timestamp.

As you are saying.

---

### Post by cdenley on 2010-06-03
Anytime you have a line like:
```
CustomLog /var/log/httpd/site_in_question-resp_log resp
```
it should follow a line like
```

LogFormat "whatever format you want" resp

```
within the same scope. If you put it in a vhost section, both lines go in a vhost section. I don't know how vhosts are configured in CentOS, so I can't be more specific.

---

### Post by tapas_mishra on 2010-06-03
Thanks for clearing that out.
I will try.Just one doubt eduCommons is running on Zope can that be a problem.
Here is a log from zeoserver.

```


2009-10-20T20:09:33 daemonizing the process
2009-10-20T20:09:33 set current directory: '/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zeoserver'
2009-10-20T20:09:33 daemon manager started
2009-10-20T20:09:33 spawned process pid=17397
2009-10-20T20:09:33 (17397) created PID file '/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/var/zeoserver.pid'
2009-10-20T20:09:33 (17397) opening storage '1' using FileStorage
2009-10-20T20:09:33 (17397) StorageServer created RW with storages: 1:RW:/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/var/filestorage/Data.fs
2009-10-20T20:09:33 (17397) listening on ('127.0.0.1', 8100)
2009-10-20T20:09:52 (17397) new connection ('127.0.0.1', 50127): <ManagedServerConnection ('127.0.0.1', 50127)>
2009-10-20T20:09:52 (127.0.0.1:50127) received handshake 'Z303'
2009-10-20T20:09:52 (127.0.0.1:50127) loadEx() raised exception: 0x00
Traceback (most recent call last):
  File "/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zope2/lib/python/ZEO/zrpc/connection.py", line 535, in handle_request
    ret = meth(*args)
  File "/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zope2/lib/python/ZEO/StorageServer.py", line 254, in loadEx
    return self.storage.loadEx(oid, version)
  File "/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zope2/lib/python/ZODB/FileStorage/FileStorage.py", line 523, in loadEx
    pos = self._lookup_pos(oid)
  File "/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/parts/zope2/lib/python/ZODB/FileStorage/FileStorage.py", line 514, in _lookup_pos
    raise POSKeyError(oid)
POSKeyError: 0x00
2009-10-20T20:11:47 (17397/127.0.0.1:50127) disconnected
2009-10-20T20:11:48 (17397) terminated by SIGTERM
2009-10-20T20:11:48 (17397) closing storage '1'
2009-10-20T20:11:48 (17397) removed PID file '/home/brent/rpms/SOURCES/eduCommons-3.2.1-final/var/zeoserver.pid'
2009-10-20T20:11:48 pid 17397: exit status 0
2009-10-20T20:11:48 Exiting
2010-05-25T19:27:22 daemonizing the process
2010-05-25T19:27:22 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-25T19:27:22 daemon manager started
2010-05-25T19:27:22 spawned process pid=2542
2010-05-25T19:27:22 (2542) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-25T19:27:22 (2542) opening storage '1' using FileStorage
2010-05-25T19:27:22 (2542) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-25T19:27:22 (2542) listening on ('127.0.0.1', 8100)
2010-05-25T19:27:32 (2542) new connection ('127.0.0.1', 46505): <ManagedServerConnection ('127.0.0.1', 46505)>
2010-05-25T19:27:32 (127.0.0.1:46505) received handshake 'Z303'
2010-05-25T19:34:03 daemon manager killed by SIGTERM
2010-05-25T19:34:03 (2542) terminated by SIGTERM
2010-05-25T19:34:03 (2542) closing storage '1'
2010-05-25T19:34:03 (2542) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-25T19:35:09 daemonizing the process
2010-05-25T19:35:09 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-25T19:35:09 daemon manager started
2010-05-25T19:35:09 spawned process pid=2145
2010-05-25T19:35:09 (2145) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-25T19:35:09 (2145) opening storage '1' using FileStorage
2010-05-25T19:35:09 (2145) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-25T19:35:09 (2145) listening on ('127.0.0.1', 8100)
2010-05-25T19:35:19 (2145) new connection ('127.0.0.1', 51546): <ManagedServerConnection ('127.0.0.1', 51546)>
2010-05-25T19:35:19 (127.0.0.1:51546) received handshake 'Z303'
2010-05-27T11:16:55 Unlinking stale socket /opt/eduCommons-3.2.1/var/zeo.zdsock; sleep 1
2010-05-27T11:16:56 daemonizing the process
2010-05-27T11:16:56 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:16:56 daemon manager started
2010-05-27T11:16:56 spawned process pid=2171
2010-05-27T11:16:56 (2171) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:16:56 (2171) opening storage '1' using FileStorage
2010-05-27T11:16:56 (2171) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:16:56 (2171) listening on ('127.0.0.1', 8100)
2010-05-27T11:21:42 (2171) terminated by SIGTERM
2010-05-27T11:21:42 (2171) closing storage '1'
2010-05-27T11:21:42 (2171) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:21:42 pid 2171: exit status 0
2010-05-27T11:21:42 Exiting
2010-05-27T11:21:43 daemonizing the process
2010-05-27T11:21:43 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:21:43 daemon manager started
2010-05-27T11:21:43 spawned process pid=2336
2010-05-27T11:21:44 (2336) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:21:44 (2336) opening storage '1' using FileStorage
2010-05-27T11:21:44 (2336) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:21:44 (2336) listening on ('127.0.0.1', 8100)
2010-05-27T11:22:21 (2336) terminated by SIGTERM
2010-05-27T11:22:21 (2336) closing storage '1'
2010-05-27T11:22:21 (2336) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:22:21 pid 2336: exit status 0
2010-05-27T11:22:21 Exiting
2010-05-27T11:22:22 daemonizing the process
2010-05-27T11:22:22 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:22:22 daemon manager started
2010-05-27T11:22:22 spawned process pid=2349
2010-05-27T11:22:22 (2349) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:22:22 (2349) opening storage '1' using FileStorage
2010-05-27T11:22:22 (2349) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:22:22 (2349) listening on ('127.0.0.1', 8100)
2010-05-27T11:22:43 (2349) terminated by SIGTERM
2010-05-27T11:22:43 (2349) closing storage '1'
2010-05-27T11:22:43 (2349) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:22:43 pid 2349: exit status 0
2010-05-27T11:22:43 Exiting
2010-05-27T11:22:50 daemonizing the process
2010-05-27T11:22:50 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:22:50 daemon manager started
2010-05-27T11:22:50 spawned process pid=2363
2010-05-27T11:22:50 (2363) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:22:50 (2363) opening storage '1' using FileStorage
2010-05-27T11:22:50 (2363) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:22:50 (2363) listening on ('127.0.0.1', 8100)
2010-05-27T11:23:44 daemon manager killed by SIGTERM
2010-05-27T11:23:44 (2363) terminated by SIGTERM
2010-05-27T11:23:44 (2363) closing storage '1'
2010-05-27T11:23:44 (2363) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:24:47 daemonizing the process
2010-05-27T11:24:47 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:24:47 daemon manager started
2010-05-27T11:24:47 spawned process pid=2116
2010-05-27T11:24:47 (2116) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:24:47 (2116) opening storage '1' using FileStorage
2010-05-27T11:24:48 (2116) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:24:48 (2116) listening on ('127.0.0.1', 8100)
2010-05-27T11:27:52 (2116) terminated by SIGTERM
2010-05-27T11:27:52 (2116) closing storage '1'
2010-05-27T11:27:52 (2116) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:27:52 pid 2116: exit status 0
2010-05-27T11:27:52 Exiting
2010-05-27T11:27:52 daemonizing the process
2010-05-27T11:27:52 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:27:52 daemon manager started
2010-05-27T11:27:52 spawned process pid=2292
2010-05-27T11:27:52 (2292) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:27:52 (2292) opening storage '1' using FileStorage
2010-05-27T11:27:52 (2292) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:27:52 (2292) listening on ('127.0.0.1', 8100)
2010-05-27T11:28:27 pid 2292: terminated by SIGKILL
2010-05-27T11:28:27 spawned process pid=2299
2010-05-27T11:28:27 (2299) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:28:27 (2299) opening storage '1' using FileStorage
2010-05-27T11:28:27 (2299) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:28:27 (2299) listening on ('127.0.0.1', 8100)
2010-05-27T11:28:32 (2299) terminated by SIGTERM
2010-05-27T11:28:32 (2299) closing storage '1'
2010-05-27T11:28:32 (2299) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:28:32 pid 2299: exit status 0
2010-05-27T11:28:32 Exiting
2010-05-27T11:28:32 daemonizing the process
2010-05-27T11:28:32 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:28:32 daemon manager started
2010-05-27T11:28:32 spawned process pid=2309
2010-05-27T11:28:32 (2309) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:28:32 (2309) opening storage '1' using FileStorage
2010-05-27T11:28:32 (2309) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:28:32 (2309) listening on ('127.0.0.1', 8100)
2010-05-27T11:31:23 (2309) terminated by SIGTERM
2010-05-27T11:31:23 (2309) closing storage '1'
2010-05-27T11:31:23 (2309) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:31:23 pid 2309: exit status 0
2010-05-27T11:31:23 Exiting
2010-05-27T11:31:23 daemonizing the process
2010-05-27T11:31:23 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:31:23 daemon manager started
2010-05-27T11:31:23 spawned process pid=2330
2010-05-27T11:31:23 (2330) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:31:23 (2330) opening storage '1' using FileStorage
2010-05-27T11:31:23 (2330) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:31:23 (2330) listening on ('127.0.0.1', 8100)
2010-05-27T11:55:57 (2330) terminated by SIGTERM
2010-05-27T11:55:57 (2330) closing storage '1'
2010-05-27T11:55:57 (2330) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:55:57 pid 2330: exit status 0
2010-05-27T11:55:57 Exiting
2010-05-27T11:55:57 daemonizing the process
2010-05-27T11:55:57 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T11:55:57 daemon manager started
2010-05-27T11:55:57 spawned process pid=2438
2010-05-27T11:55:57 (2438) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T11:55:57 (2438) opening storage '1' using FileStorage
2010-05-27T11:55:57 (2438) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T11:55:57 (2438) listening on ('127.0.0.1', 8100)
2010-05-27T12:00:56 (2438) terminated by SIGTERM
2010-05-27T12:00:56 (2438) closing storage '1'
2010-05-27T12:00:56 (2438) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T12:00:56 pid 2438: exit status 0
2010-05-27T12:00:56 Exiting
2010-05-27T12:00:56 daemonizing the process
2010-05-27T12:00:56 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T12:00:56 daemon manager started
2010-05-27T12:00:56 spawned process pid=2474
2010-05-27T12:00:56 (2474) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T12:00:56 (2474) opening storage '1' using FileStorage
2010-05-27T12:00:56 (2474) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T12:00:56 (2474) listening on ('127.0.0.1', 8100)
2010-05-27T12:05:32 (2474) terminated by SIGTERM
2010-05-27T12:05:32 (2474) closing storage '1'
2010-05-27T12:05:32 (2474) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T12:05:32 pid 2474: exit status 0
2010-05-27T12:05:32 Exiting
2010-05-27T12:05:32 daemonizing the process
2010-05-27T12:05:32 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T12:05:32 daemon manager started
2010-05-27T12:05:32 spawned process pid=2514
2010-05-27T12:05:32 (2514) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T12:05:32 (2514) opening storage '1' using FileStorage
2010-05-27T12:05:32 (2514) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T12:05:32 (2514) listening on ('127.0.0.1', 8100)
2010-05-27T12:24:58 (2514) terminated by SIGTERM
2010-05-27T12:24:58 (2514) closing storage '1'
2010-05-27T12:24:58 (2514) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T12:24:58 pid 2514: exit status 0
2010-05-27T12:24:58 Exiting
2010-05-27T12:24:58 daemonizing the process
2010-05-27T12:24:58 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T12:24:58 daemon manager started
2010-05-27T12:24:58 spawned process pid=2709
2010-05-27T12:24:58 (2709) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T12:24:58 (2709) opening storage '1' using FileStorage
2010-05-27T12:24:58 (2709) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T12:24:58 (2709) listening on ('127.0.0.1', 8100)
2010-05-27T12:41:16 (2709) terminated by SIGTERM
2010-05-27T12:41:16 (2709) closing storage '1'
2010-05-27T12:41:16 (2709) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T12:41:16 pid 2709: exit status 0
2010-05-27T12:41:16 Exiting
2010-05-27T12:41:19 daemonizing the process
2010-05-27T12:41:19 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T12:41:19 daemon manager started
2010-05-27T12:41:19 spawned process pid=2766
2010-05-27T12:41:19 (2766) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T12:41:19 (2766) opening storage '1' using FileStorage
2010-05-27T12:41:19 (2766) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T12:41:19 (2766) listening on ('127.0.0.1', 8100)
2010-05-27T16:11:28 (2766) terminated by SIGTERM
2010-05-27T16:11:28 (2766) closing storage '1'
2010-05-27T16:11:28 (2766) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T16:11:28 pid 2766: exit status 0
2010-05-27T16:11:28 Exiting
2010-05-27T16:11:33 daemonizing the process
2010-05-27T16:11:33 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T16:11:33 daemon manager started
2010-05-27T16:11:33 spawned process pid=3278
2010-05-27T16:11:33 (3278) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T16:11:33 (3278) opening storage '1' using FileStorage
2010-05-27T16:11:33 (3278) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T16:11:33 (3278) listening on ('127.0.0.1', 8100)
2010-05-27T16:12:00 (3278) terminated by SIGTERM
2010-05-27T16:12:00 (3278) closing storage '1'
2010-05-27T16:12:00 (3278) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T16:12:00 pid 3278: exit status 0
2010-05-27T16:12:00 Exiting
2010-05-27T16:24:11 daemonizing the process
2010-05-27T16:24:11 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T16:24:11 daemon manager started
2010-05-27T16:24:11 spawned process pid=3360
2010-05-27T16:24:11 (3360) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T16:24:11 (3360) opening storage '1' using FileStorage
2010-05-27T16:24:11 (3360) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T16:24:11 (3360) listening on ('127.0.0.1', 8100)
2010-05-27T17:44:29 daemon manager killed by SIGTERM
2010-05-27T17:44:29 (3360) terminated by SIGTERM
2010-05-27T17:44:29 (3360) closing storage '1'
2010-05-27T17:44:29 (3360) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T17:45:35 daemonizing the process
2010-05-27T17:45:35 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-27T17:45:35 daemon manager started
2010-05-27T17:45:35 spawned process pid=2115
2010-05-27T17:45:36 (2115) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-27T17:45:36 (2115) opening storage '1' using FileStorage
2010-05-27T17:45:36 (2115) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-27T17:45:36 (2115) listening on ('127.0.0.1', 8100)
2010-05-28T10:58:47 (2115) terminated by SIGTERM
2010-05-28T10:58:47 (2115) closing storage '1'
2010-05-28T10:58:47 (2115) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-28T10:58:47 pid 2115: exit status 0
2010-05-28T10:58:47 Exiting
2010-05-28T10:58:51 daemonizing the process
2010-05-28T10:58:51 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-28T10:58:51 daemon manager started
2010-05-28T10:58:51 spawned process pid=5057
2010-05-28T10:58:51 (5057) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-28T10:58:51 (5057) opening storage '1' using FileStorage
2010-05-28T10:58:51 (5057) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-28T10:58:51 (5057) listening on ('127.0.0.1', 8100)
2010-05-28T10:59:09 (5057) terminated by SIGTERM
2010-05-28T10:59:09 (5057) closing storage '1'
2010-05-28T10:59:09 (5057) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-28T10:59:09 pid 5057: exit status 0
2010-05-28T10:59:09 Exiting
2010-05-28T10:59:25 daemonizing the process
2010-05-28T10:59:25 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-28T10:59:25 daemon manager started
2010-05-28T10:59:25 spawned process pid=5079
2010-05-28T10:59:25 (5079) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-28T10:59:25 (5079) opening storage '1' using FileStorage
2010-05-28T10:59:25 (5079) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-28T10:59:25 (5079) listening on ('127.0.0.1', 8100)
2010-05-28T10:59:52 (5079) terminated by SIGTERM
2010-05-28T10:59:52 (5079) closing storage '1'
2010-05-28T10:59:52 (5079) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-28T10:59:52 pid 5079: exit status 0
2010-05-28T10:59:52 Exiting
2010-05-28T11:21:23 daemonizing the process
2010-05-28T11:21:23 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-28T11:21:23 daemon manager started
2010-05-28T11:21:23 spawned process pid=5193
2010-05-28T11:21:23 (5193) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-28T11:21:23 (5193) opening storage '1' using FileStorage
2010-05-28T11:21:23 (5193) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-28T11:21:23 (5193) listening on ('127.0.0.1', 8100)
2010-05-28T11:21:43 (5193) new connection ('127.0.0.1', 52319): <ManagedServerConnection ('127.0.0.1', 52319)>
2010-05-28T11:21:43 (127.0.0.1:52319) received handshake 'Z303'
2010-05-31T14:29:42 Unlinking stale socket /opt/eduCommons-3.2.1/var/zeo.zdsock; sleep 1
2010-05-31T14:29:43 daemonizing the process
2010-05-31T14:29:43 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-05-31T14:29:43 daemon manager started
2010-05-31T14:29:43 spawned process pid=2140
2010-05-31T14:29:43 (2140) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-05-31T14:29:43 (2140) opening storage '1' using FileStorage
2010-05-31T14:29:43 (2140) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-05-31T14:29:43 (2140) listening on ('127.0.0.1', 8100)
2010-06-01T10:05:40 (2140) terminated by SIGTERM
2010-06-01T10:05:40 (2140) closing storage '1'
2010-06-01T10:05:40 (2140) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-06-01T10:05:40 pid 2140: exit status 0
2010-06-01T10:05:40 Exiting
2010-06-01T10:05:40 daemonizing the process
2010-06-01T10:05:40 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-06-01T10:05:40 daemon manager started
2010-06-01T10:05:40 spawned process pid=5204
2010-06-01T10:05:41 (5204) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-06-01T10:05:41 (5204) opening storage '1' using FileStorage
2010-06-01T10:05:41 (5204) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-06-01T10:05:41 (5204) listening on ('127.0.0.1', 8100)
2010-06-01T10:06:13 (5204) terminated by SIGTERM
2010-06-01T10:06:13 (5204) closing storage '1'
2010-06-01T10:06:13 (5204) removed PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-06-01T10:06:13 pid 5204: exit status 0
2010-06-01T10:06:13 Exiting
2010-06-01T10:06:23 daemonizing the process
2010-06-01T10:06:23 set current directory: '/opt/eduCommons-3.2.1/parts/zeoserver'
2010-06-01T10:06:23 daemon manager started
2010-06-01T10:06:23 spawned process pid=5224
2010-06-01T10:06:23 (5224) created PID file '/opt/eduCommons-3.2.1/var/zeoserver.pid'
2010-06-01T10:06:23 (5224) opening storage '1' using FileStorage
2010-06-01T10:06:23 (5224) StorageServer created RW with storages: 1:RW:/opt/eduCommons-3.2.1/var/filestorage/Data.fs
2010-06-01T10:06:23 (5224) listening on ('127.0.0.1', 8100)
2010-06-01T10:06:37 (5224) new connection ('127.0.0.1', 56072): <ManagedServerConnection ('127.0.0.1', 56072)>
2010-06-01T10:06:37 (127.0.0.1:56072) received handshake 'Z303'

```

---

### Post by tapas_mishra on 2010-06-04
I have finally found the reason for the website to be slow.

Since the server did not had a GUI on which the above site is hosted so 
I had to login to it
```

ssh -L 8080:localhost:8080 root@siteinproblem

```

then in browser 
```

http://localhost:8080/eduCommons

```

The site was working properly. 


But when I checked it as follows 
```

http://localhost:8080/VirtualHostBase/http/localhost:80/VirtualHostRoot/eduCommons

```
then all the CSS and images were broken. 
[This is]("http://farm5.static.flickr.com/4005/4677405173_303fd33e0f_b.jpg") what is going on internet.

So when a client browser requests eduCommons website after Reverse Proxy has forwarded the request to Zope server some how it does not reaches Zope WebServer and eventually the request dies and the time it takes to load the website is sum total of all such requests which are dying.
This is what is making  my website slow.

VirtualHostBase refers to a protocol Zope uses and VirtualHostRoot is Document Root  of Zope
more details about it can be read here
[http://wiki.zope.org/zope2/ZopeAndApache#introduction-to-rewriterules-and-virtualhostmonster]("http://wiki.zope.org/zope2/ZopeAndApache#introduction-to-rewriterules-and-virtualhostmonster")

---

