---
title: "possible Hack"
date: 2012-02-03
forum: Security
---

### Post by slothy2012 on 2012-02-03
Hi,  

I run Ubuntu 10.04, Apache and MYSQL.  Now there was a a mssive attack from VPNs, Tor, Proxys etc.   Since that etherape shows a lot of Connections mostly every time.   Looks like I got hacked, and I don`t know how to fix it, or check what really is going on.

> netstat -tunp
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.2.100:54838     178.63.19.216:443       TIME_WAIT   -               
tcp        0      0 192.168.2.100:49350     83.117.170.114:80       TIME_WAIT   -               
tcp        0      0 192.168.2.100:50313     173.194.69.106:80       TIME_WAIT   -               
tcp        0      0 192.168.2.100:49349     83.117.170.114:80       TIME_WAIT   -               
tcp        0      0 192.168.2.100:54836     178.63.19.216:443       TIME_WAIT   -               
tcp        0      0 192.168.2.100:34970     66.220.149.18:443       TIME_WAIT   -               
tcp        0      0 192.168.2.100:59612     91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.2.100:49352     83.117.170.114:80       TIME_WAIT   -               
tcp        0      0 192.168.2.100:54839     178.63.19.216:443       TIME_WAIT   -               
tcp        0      0 192.168.2.100:53560     173.194.69.94:80        ESTABLISHED 29399/firefox   
tcp        0      0 192.168.2.100:54842     178.63.19.216:443       TIME_WAIT   -               
tcp        0      0 192.168.2.100:59609     91.189.94.12:80         TIME_WAIT   -               
tcp        1      0 192.168.2.100:57386     188.111.53.49:80        CLOSE_WAIT  2546/clock-applet
tcp        0      0 192.168.2.100:59610     91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.2.100:54840     178.63.19.216:443       TIME_WAIT   -               
tcp        0      0 192.168.2.100:49351     83.117.170.114:80       TIME_WAIT   -   > netstat -an
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN     
tcp        0      0 192.168.2.100:40384     213.95.41.13:80         ESTABLISHED
tcp        0      0 192.168.2.100:40385     213.95.41.13:80         ESTABLISHED
tcp        0      0 192.168.2.100:38742     137.56.163.64:443       ESTABLISHED
tcp        0      0 192.168.2.100:53477     85.112.165.75:9001      ESTABLISHED
tcp        0      0 192.168.2.100:40386     213.95.41.13:80         ESTABLISHED
tcp        0      0 192.168.2.100:40388     213.95.41.13:80         ESTABLISHED
tcp        0      0 192.168.2.100:44269     188.138.82.143:443      ESTABLISHED
tcp        0      0 192.168.2.100:41898     188.111.53.49:80        ESTABLISHED
tcp        0      0 192.168.2.100:38579     173.194.69.94:80        TIME_WAIT  
tcp        0      0 192.168.2.100:40387     213.95.41.13:80         ESTABLISHED
tcp        0      0 192.168.2.100:46539     173.194.69.94:80        ESTABLISHED
tcp        0      0 192.168.2.100:40389     213.95.41.13:80         ESTABLISHED
tcp6       0      0 ::1:631                 :::*                    LISTEN     
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:47240           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp6       0      0 :::5353                 :::*                               
udp6       0      0 :::56913                :::*  Anyone here that can help? thx

---

### Post by OpSecShellshock on 2012-02-03
So are you using this as a desktop or a server? The post indicates that Apache and MYSQL are installed and running, but the connections out are web browser traffic most likely (see that the destination ports are 80 and 443 on most of them, http and https respectively), and Firefox is the process ID of the only established connection.

In what's posted I don't see anything really suspicious though. Were you actively using the computer to browse the web during the time netstat was run?

---

### Post by slothy2012 on 2012-02-03
Hi,

I use it as a Desktop and run the Apache in the background. 

thats the problem.The first netstat is with FF running. The second posted Output was the first I requested, without FF running.
Normally Etherape shows the connections and they dissapear really fast if I stop browsing etc. 

I stopped Appache and Mysql after I saw the incoming connections from VPNs, Tor and Proxys......^^:popcorn:

One of the Connections I`ve traced comes from Wikileaks...!?? I have nothing to do with Wikileaks. 

And I`ve never visited the pages listed there, expect google. Other IPs don`t even match to a website. Nothing to see.

I`m fallen over a JS DDoS attack yesterday by just clicking a link! Target gov.. I stopped JS direct after I have seen whats going on, but some minutes later I recognized a ping or scan from the gov adress. SO yes. I am a little bit paranoid.:)

Edit: Some of the Ips I checked are blacklistet.

---

### Post by slothy2012 on 2012-02-03
BTW: Check this Ip from the list: 85.112.165.75
[http://85.112.165.75/](http://85.112.165.75/)
Newzbin... I have never visited that page, but If you look at the first four entries...
[Police Force (2011)]("http://85.112.165.75/browse/post/6485780/")
...search done, right..

:popcorn:

Edit... I deinstalled noip2, updatet iptables and restarted the router twice to get a new IP. As far as the Internetconnection was done etherape flipped out an shows outgoing connections to 20 Ips, Tor etc.. FF was closed, Apache etc. stopped. So normally nothing should happen. Maybe one or two short things to update etc,. but that was not normal. It looks like a few peoples came in watched around and went without signs. My Computer crashed once too.

So, if someone tell me that there is nothing unusual I can`t believe that. Where do I have to watch for signs?

---

### Post by Dangertux on 2012-02-03
Yeah umm honestly, I think you're being paranoid.
 
Are you running TOR? Possibly with Vidalia as a relay? It seems like you might be.

Hope this helps.

---

### Post by emiller12345 on 2012-02-03
> **Dangertux said:**
> Yeah umm honestly, I think you're being paranoid.
 
Are you running TOR? Possibly with Vidalia as a relay? It seems like you might be.

Hope this helps.

+1
Yeah it looks like you are probably running Tor.  Tor is one of those programs that is a double edge sword and you need to understand it well.  The thing is you don't really know who has control of the _Exit Nodes_ and it has the potential of causing more problems in the long run then its worth. You may consider an alternative like a reputable VPN service.

---

### Post by slothy2012 on 2012-02-04
Hi,

sure. Tor is running in the background but I don`t use it. I should take it away from the autostart applications.

It is not that I am that paranoid. I saw very suspicious traffic from many untrustable well known VPNs etc. My System crashed.

Maybe it was just a DDoS attack from a handfull people. But it wasn`t a normal situation.

If i would tell some of the names the attackers used things would be clearer @OpSec

---

### Post by 0011235813 on 2012-02-05
> **slothy2012 said:**
> Hi,

sure. Tor is running in the background but I don`t use it. I should take it away from the autostart applications.

It is not that I am that paranoid. I saw very suspicious traffic from many untrustable well known VPNs etc. My System crashed.

Maybe it was just a DDoS attack from a handfull people. But it wasn`t a normal situation.

If i would tell some of the names the attackers used things would be clearer @OpSec

To me, it sounds like you're being a little paranoid and that there isn't really anything to worry about. You might want to tighten up your firewall a bit though...  You need to edit  /etc/ufw/before.rules . You can open the file like this:
```
gksu gedit  /etc/ufw/before.rules 
```
gksu is the command that tells the system to run the program {gedit} with root privileges  (you will have to authenticate), gedit is the text editor (you can use kate & others if you wish) and the last bit is the file location. Now, scroll down in the file, and you will see something about imcp codes:
```
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```
 and "accept" in big capitals at the end of the line(s). You change those big accepts to big DROP.Example:
```
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP
```

 You can see the link here: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

PS: I've heard VPNs being mentioned, does anyone know any good VPNs? A lot of the ones I've searched for can only connect via a Windows-only client. I've tried TorVPN and ReactorVPN, but I can't connect to any of them (I disable the firewall, until I can figure out which port uses the PPTP connection).

---

### Post by Dangertux on 2012-02-05
> **0011235813 said:**
> To me, it sounds like you're being a little paranoid and that there isn't really anything to worry about. You might want to tighten up your firewall a bit though...  You need to edit  /etc/ufw/before.rules . You can open the file like this:
```
sudo gedit  /etc/ufw/before.rules 
```sudo is the syntax that tells the system to run the command as root (you will have to authenticate), gedit is the text editor (you can use kate & others if you wish) and the last bit is the file location. Now, scroll down in the file, and you will see something about imcp codes and "accept" in big capitals at the end of the line(s). You change those big accepts to big DROP. You can see the link here: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

PS: I've heard VPNs being mentioned, does anyone know any good VPNs? A lot of the ones I've searched for can only connect via a Windows-only client. I've tried TorVPN and ReactorVPN, but I can't connect to any of them (I disable the firewall, until I can figure out which port uses the PPTP connection).

Okay first things first.

First the recommended method for using gedit as root is NOT the way you posted. It is recommended to use the following.

```

gksudo gedit filename

```

The reason being is that gksudo takes your environment into account whereas sudo does not.

Secondly, dropping all ICMP traffic without rhyme or reason is a terrible idea, and will likely cause breakage in many applications. ICMP traffic is widely used for network management and quality of service, therefor if you DROP all of it there is a good chance your network performance will be extremely poor or non-existant. There is no relevant threat from leaving (even ICMP echo request) set to ACCEPT. Unless of course you're one of those who are just going for a "perfect stealth" rating on GRC which is somewhat pointless in and of itself.

As for how to allow VPN traffic you might wish to add the following iptables rules, since most PPTP VPNs are using GRE.

```

iptables -A INPUT -p 47 -j ACCEPT
iptables -A OUTPUT -p 47 -j ACCEPT
iptables -A INPUT -p tcp --dport 1723 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1723 -j ACCEPT
iptables -A INPUT -p tcp --dport 1701 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1701 -j ACCEPT
iptables -A INPUT -p tcp --dport 500 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 500 -j ACCEPT

```

And the format if you wish to place them in your /etc/ufw/before.rules file.

```

 -A ufw-before-input -p 47 -j ACCEPT
 -A ufw-before-output -p 47 -j ACCEPT
 -A ufw-before-input -p tcp --dport 1723 -j ACCEPT
 -A ufw-before-output -p tcp --dport 1723 -j ACCEPT
 -A ufw-before-input -p tcp --dport 1701 -j ACCEPT
 -A ufw-before-output -p tcp --dport 1701 -j ACCEPT
 -A ufw-before-input -p tcp --dport 500 -j ACCEPT
 -A ufw-before-output -p tcp --dport 500 -j ACCEPT

```

Hope this helps.

---

### Post by 0011235813 on 2012-02-05
> **Dangertux said:**
> Okay first things first.

First the recommended method for using gedit as root is NOT the way you posted. It is recommended to use the following.

```

gksudo gedit filename

```

The reason being is that gksudo takes your environment into account whereas sudo does not.

Secondly, dropping all ICMP traffic without rhyme or reason is a terrible idea, and will likely cause breakage in many applications. ICMP traffic is widely used for network management and quality of service, therefor if you DROP all of it there is a good chance your network performance will be extremely poor or non-existant. There is no relevant threat from leaving (even ICMP echo request) set to ACCEPT. Unless of course you're one of those who are just going for a "perfect stealth" rating on GRC which is somewhat pointless in and of itself.

As for how to allow VPN traffic you might wish to add the following iptables rules, since most PPTP VPNs are using GRE.

```

iptables -A INPUT -p 47 -j ACCEPT
iptables -A OUTPUT -p 47 -j ACCEPT
iptables -A INPUT -p tcp --dport 1723 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1723 -j ACCEPT
iptables -A INPUT -p tcp --dport 1701 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1701 -j ACCEPT
iptables -A INPUT -p tcp --dport 500 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 500 -j ACCEPT

```

And the format if you wish to place them in your /etc/ufw/before.rules file.

```

 -A ufw-before-input -p 47 -j ACCEPT
 -A ufw-before-output -p 47 -j ACCEPT
 -A ufw-before-input -p tcp --dport 1723 -j ACCEPT
 -A ufw-before-output -p tcp --dport 1723 -j ACCEPT
 -A ufw-before-input -p tcp --dport 1701 -j ACCEPT
 -A ufw-before-output -p tcp --dport 1701 -j ACCEPT
 -A ufw-before-input -p tcp --dport 500 -j ACCEPT
 -A ufw-before-output -p tcp --dport 500 -j ACCEPT

```

Hope this helps.

OK, I didn't know, is it really worth making such a fuss over *sudo gedit* vs *gksu gedit* ? 

I think I may have confused you, my original post only said PING requests, not all icmp traffic. I've disabled PING requests and haven't had any accessibility problems.

Interesting... I'll try that. But is there any way to do it with ufw commands?

---

### Post by haqking on 2012-02-05
> **0011235813 said:**
> OK, **I didn't know, is it really worth making such a fuss over *sudo gedit* vs *gksu gedit* ?** 

I think I may have confused you, my original post only said PING requests, not all icmp traffic


I wouldnt say that correcting an incorrect command is making a fuss.

There is a right way to do things and the wrong way.

as he said in explaining his point that it is to do with environment

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

as for confusing, not really as you said ICMP in general and not specifically PING

from your post

> Now, scroll down in the file, and you will see something about **imcp** codes and "accept" in big capitals at the end of the line(s). You change those big accepts to big DROP

more than ping relies on ICMP

---

### Post by Dangertux on 2012-02-05
> **0011235813 said:**
> OK, I didn't know, is it really worth making such a fuss over *sudo gedit* vs *gksu gedit* ? 

I think I may have confused you, my original post only said PING requests, not all icmp traffic. I've disabled PING requests and haven't had any accessibility problems.

Interesting... I'll try that. But is there any way to do it with ufw commands?


As far as I know there is no way to do it with UFW since the only protocols supported by UFW's front end application are TCP/UDP (I could be wrong consult the man pages) 

-p 47 is denoting the GRE protocol in case you're wondering.

As far as making a "fuss" about commands. Yes in this particular case there is a correct (meaning supported) way of doing things. On this forum we try to offer support in as much of a standardized method as possible to provide the best quality of service for those who are seeking assistance. We use things like gksu over sudo in cases like this to avoid one-offs. These types of one-offs can result in people with nonstandard configurations having breakage (for instance if their path is configured a certain way on their user but not root etc...)

For the ICMP codes bit, you were referring to this block of firewall rules I presume.

```

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT


```

Only one of these rules has anything to do with ICMP type 8 (echo request [ping]). It is this one.

```

-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

The rest serve other functions, which if you're not sure if they are needed (preferred) you should leave them alone.

I hope this helps.

---

### Post by 0011235813 on 2012-02-05
> I wouldnt say that correcting an incorrect command is making a fuss.

There is a right way to do things and the wrong way.

as he said in explaining his point that it is to do with environment

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

as for confusing, not really as you said ICMP in general and not specifically PING

from your post



more than ping relies on ICMP
Whether it's correct or not is up to debate, it does the job, and I honestly don't care which one they prefer. But I edited the post to use gksu instead, I really don't care for a debate on gksu vs sudo on a post asking for help.

> As far as I know there is no way to do it with UFW since the only protocols supported by UFW's front end application are TCP/UDP (I could be wrong consult the man pages)
I would imagine
```
sudo allow <service name>
```
would allow it through, trouble is, I don;t know what the service name of the VPN is. I don't know what port the VPNs use either, I guess I'll have to do some looking up.

> -p 47 is denoting the GRE protocol in case you're wondering.

As far as making a "fuss" about commands. Yes in this particular case there is a correct (meaning supported) way of doing things. On this forum we try to offer support in as much of a standardized method as possible to provide the best quality of service for those who are seeking assistance. We use things like gksu over sudo in cases like this to avoid one-offs. These types of one-offs can result in people with nonstandard configurations having breakage (for instance if their path is configured a certain way on their user but not root etc...)

For the ICMP codes bit, you were referring to this block of firewall rules I presume.

```

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT


```

Only one of these rules has anything to do with ICMP type 8 (echo request [ping]). It is this one.

```

-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

The rest serve other functions, which if you're not sure if they are needed (preferred) you should leave them alone.

I hope this helps.
I think if they're having trouble with something they could re-allow them, but I've never seen any difference, and my idea is that the fewer things open to possible exploit, the safer. It's one of the reasons computers have been facing such bug and malware issues, as they just get so complex it becomes harder and harder to protect, and there are more and more holes (although there's also more code, so hackers will need more time and effort).

---

### Post by Dangertux on 2012-02-05
> **0011235813 said:**
> Whether it's correct or not is up to debate, it does the job, and I honestly don't care which one they prefer. But I edited the post to use gksu instead, I really don't care for a debate on gksu vs sudo on a post asking for help.


I would imagine
```
sudo allow <service name>
```would allow it through, trouble is, I don;t know what the service name of the VPN is. I don't know what port the VPNs use either, I guess I'll have to do some looking up.


I think if they're having trouble with something they could re-allow them, but I've never seen any difference, and my idea is that the fewer things open to possible exploit, the safer. It's one of the reasons computers have been facing such bug and malware issues, as they just get so complex it becomes harder and harder to protect, and there are more and more holes (although there's also more code, so hackers will need more time and effort).

You're overly complicating things. I gave you the correct ports for PPTP VPN, and as I said GRE is a protocol not a service.

As far as the "right" way or not, I also explained the reasoning. 

However, since none of these topics relate to the original support request I urge you to start your own thread(s) in order to get the most direct support that can be offered and not to dilute the efforts of the community to support the OP's original issue.

---

### Post by haqking on 2012-02-05
> **0011235813 said:**
> Whether it's correct or not is up to debate, it does the job, and I honestly don't care which one they prefer. But I edited the post to use gksu instead, I really don't care for a debate on gksu vs sudo on a post asking for help.



on a post asking for help is where you should use correct and standardised commands and information.

There is no debate, gksudo exists for the purpose of graphical apps and is documented and been covered many times

Anyways you use whatever you choose.

Peace

@ OP my input was to correct, so remember to use gksudo for graphical apps.  Cheers

---

