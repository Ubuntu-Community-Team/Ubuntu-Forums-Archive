---
title: "Unable to access home server from internet"
date: 2013-03-31
forum: Server Platforms
---

### Post by russcore on 2013-03-31
Hi, I’ve spent the last 6 hours trying to make my home server (Unbuntu, 12.10 quantal) accessible from the internet.  [I teach math in China – wanted to try webwork to give them homework] No problems accessing it from my own network using local or public IPs.
 
When I run netstat –tulpn, I get
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -              
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -              
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -              
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -              
tcp6       0      0 :::22                   :::*                    LISTEN      -              
tcp6       0      0 ::1:631                 :::*                    LISTEN      -              
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -              
udp        0      0 0.0.0.0:51481           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:43696           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -              
udp6       0      0 :::54267                :::*                                -              
udp6       0      0 :::52269                :::*                                -              
udp6       0      0 :::5353                 :::*                                -   
---
I have UFW disabled.    I am behind a router (unfortunately, it’s all in Chinese, but to the best of my knowledge I have established a static local ip for my server (192.168.1.105), and have port forwarding for ports 22, 80 and 8080 to that IP address, and I have DMZ (not even sure what that is) on associated with the local ip 192.168.1.105.

When I use [www.whatsmyip.org/port-scanner](www.whatsmyip.org/port-scanner) , I get that ports 80 and 8080 are blocked (timeout), but 22 is open?  Other ports are just closed.  From what I’ve read, it seems maybe my ISP is blocking ports (that’s why I tried opening port 8080)?  Or maybe I somehow made a mistake with my router ?  

Any help would be greatly appreciated.  If I can provide any more information, let me know.

---

### Post by lincoln32 on 2013-03-31
it is common for ISP's to block port 80 and 25 to keep users from running home servers. 22 is for fstp. DMZ is internet access but not local. you can assign another port to the webserver and try (external IP):(port#) and you should be able to see from outside your home.

---

### Post by chadk5utc on 2013-03-31
I will agree with lincoln32 on this this is common practice to block residential addresses. I would have someone that speaks the language fluently check the router settings? and if they can be modified? Port forwarding?
 Also given that you mention that you teach math in "China" if you are non-native they will likely restrict/censor/monitor/block anything at any time without reason.
 Again if you are non-native and memory serves me correctly you may be able to request this through your liaison officer or get approval through the school?

---

### Post by russcore on 2013-03-31
I tried port 8080 and port 5555, no success.  I was able to access port 22 from my phone using something like putty  (using 3G -- with the same phone, can't access the websites).

It seems like there should be some ports open -- for example, I have no trouble playing online games or using bittorrent clients.   Is it possible to change port 22 to an HTTP port? After I finish setting up the server, I won't need to use remote shell access outside my network. 

About censoring -- there is some -- for example, if you use google and click on a forbidden link, it will block that link and google for a while [[this happens a lot, I will search for something, find a blog post, click on the blogpost and get blocked out google for a few minutes because blogs without verified ID are censored]]   But in general, not too much -- and a VPN allows me to work around it.

---

### Post by darkod on 2013-03-31
If you can't find open ports, you can't do much about it. This doesn't necessarily have much to do with China, I remember few years back in the UK when I went to a colleagues home to check why his work laptop can't connect to our Exchange we found out the ISP was blocking the port we were using for authentication. Even after his insisting they didn't want to open it, so eventually he had to change the ISP.

Blocking service ports to residential customers is a practice in many countries.

Is there any chance the school to give you some space on their web servers, if there are such? You can put the application there maybe.

Another option is to keep looking for open ports, and then set up either the router to change for example port 8888 to 80, or the port of your services on the server to be 8888.

---

### Post by russcore on 2013-03-31
Thank you guys for taking the time to reply.   I'm glad said something -- I've already spent 7 hours now trying to figure it out, and I probably would have kept trying.   I will ask a friend to call my ISP and see if there's a web hosting option. 

Thanks again

---

### Post by d4m1r on 2013-04-01
Just buy cheap webhosting or a Ubuntu based VPS from the U.S/Canada and save yourself the trouble :)

---

