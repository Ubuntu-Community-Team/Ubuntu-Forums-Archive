---
title: "Can't open ports with iptables"
date: 2015-02-17
forum: Server Platforms
---

### Post by markus22 on 2015-02-17
I'm trying to open some port for a [gameserver]("http://pzwiki.net/wiki/Multiplayer_FAQ"), which is running on my [COLOR=#000000][FONT=Arial]Linux vServer (Ubuntu 14.04 LTS 64bit). According to the WIKI the game communicates through the following ports:
[/FONT][/COLOR]```
16261 (UDP)
16262 (TCP) // Player 1
16263 (TCP) // Player 2
16264 (TCP) // Player 3
16265 (TCP) // Player 4
// ...
```

[COLOR=#000000][FONT=Arial]Since I'm not really experienced with Linux, I searched for some ways to open ports on Ubuntu. I followed [these steps]("http://www.putorius.net/2011/05/basic-of-iptables-opening-ports-on.html") and entered the following commands:
[/FONT][/COLOR]```
iptables -I INPUT -p udp --dport 16261 -j ACCEPT
iptables -I INPUT -p tcp --dport 16262 -j ACCEPT
```

[COLOR=#000000][FONT=Arial]To make sure that it worked I checked iptables with "[/FONT][/COLOR]iptables -L"[COLOR=#000000][FONT=Arial] and got a list like that:
[/FONT][/COLOR]```
Chain INPUT (policy DROP)
num  target     prot opt source               destination         
1    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:16262
2    ACCEPT     udp  --  anywhere             anywhere             udp dpt:16261
3    ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
4    REJECT     tcp  --  anywhere             anywhere             tcp flags:!FIN,SYN,RST,ACK/SYN state NEW reject-with tcp-reset
5    DROP       all  --  anywhere             anywhere             state INVALID
6    ACCEPT     all  --  anywhere             anywhere            
7    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8443
8    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8880
9    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
10   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
11   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp
12   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
13   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp
14   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:urd
15   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:pop3
16   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:pop3s
17   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imap2
18   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imaps
19   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:poppassd
20   DROP       tcp  --  anywhere             anywhere             tcp dpt:mysql
21   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:postgresql
22   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:9008
23   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:9080
24   ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-ns
25   ACCEPT     udp  --  anywhere             anywhere             udp dpt:netbios-dgm
26   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
27   ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
28   ACCEPT     udp  --  anywhere             anywhere             udp dpt:openvpn
29   DROP       udp  --  anywhere             anywhere             udp dpt:domain
30   DROP       tcp  --  anywhere             anywhere             tcp dpt:domain
31   ACCEPT     icmp --  anywhere             anywhere             icmptype 8 code 0
32   ACCEPT     all  --  anywhere             anywhere   

```

[COLOR=#000000][FONT=Arial]The two new entries are in fact in the list, but when I [/FONT][/COLOR][checked]("http://www.yougetsignal.com/tools/open-ports/")[COLOR=#000000][FONT=Arial] to see if the two ports are open it said that b[/FONT]oth ports (16261/26262) are still closed. If I use "[/COLOR][COLOR=#000000][FONT=Consolas]netstat -ntulp" the ports also don't shop up. [/FONT][/COLOR][COLOR=#000000]What am I[FONT=Arial] doing wrong? A Teamspeak 3 and CS:GO server are already running without problems...[/FONT][/COLOR]

---

### Post by darkod on 2015-02-17
The traffic destination is the same machine right? Because if you need port forwarding to another machine you need additional iptables commands.

The game/service is listening on those ports? Note that iptables will only allow the packets to enter but the service needs to be active and listening on those ports.

Also, since your input policy is drop, did you configure iptables to let related and established traffic in or you just added the two lines you mentioned?

To check running services and ports:
netstat -plunt

---

### Post by darkod on 2015-02-17
I just looked more closely at the rules. You do have the related and established traffic rule.

But what is the task of rules number 6 and 32? They seem to be accepting all traffic which beats the point of iptables firewall. Is that for test only? Note that you are probably not protected while you have those rules active.

---

### Post by markus22 on 2015-02-17
Actually I just added the two lines I mentioned. All the other rules were there as default... I guess. I think I should probably delete rules 6 and 32 then? But as far as I can tell that wouldn't solve my actual problem. So I think I first make sure that this "Project Zomboid" gameserver is running on my vServer before deleting these rules. 

 It's the first time I've been using iptables to be honest. I'm not at all experienced with Linux, I just need a server for Games/Teamspeak. For the Teamspeak 3 and CS:GO server everything went just fine without doing anything. But for this new gameserver I can't connect to the server ("Connection failed"), although I can see and use the console without problems. I thought it might be the ports. So I checked the ports on this site ([http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)) and they are in fact closed and still are, even after adding these two lines to iptables.

The gameserver (I guess that's what you meant with "service that is listening to those ports") is currently not running since it didn't work anyway. Does it need to be running in order to check the ports with [http://www.yougetsignal.com/tools/open-ports/?](http://www.yougetsignal.com/tools/open-ports/?)

I'm not really sure what you mean with "[COLOR=#000000]The traffic destination is the same machine right?[/COLOR]". But since I'm only using one hosted Linux vServer I guess it is the same machine.

---

### Post by darkod on 2015-02-17
I don't know how that website checks the ports. It might expect for a service to be running on that port to confirm it's open. That might be a reason why it says they are closed.

The iptables commands you used are correct so the traffic destined to those ports should be let through.

I suggest you prepare the services and activate them, and only then check the ports and deal with any possible issues.

---

### Post by markus22 on 2015-02-17
I just started the gameserver and checked both "netstat -ntulp" and "netstat -plunt" and 

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
...
tcp6       0      0 :::80                   :::*                    LISTEN      10234/apache2 
udp        0      0 0.0.0.0:9987            0.0.0.0:*                           2455/ts3server_linu
udp        0      0 0.0.0.0:16261           0.0.0.0:*                           27686/java 
```  

 is showing up in both of them. The online port checking tool still says that the port is closed though. I will try to connect to the server this evening (I'm not at home currently to check it) and report back if it worked out or not.

---

### Post by markus22 on 2015-02-17
It worked, I could connect to the server, although this online tool says that the ports are closed. it seems that it's not really reliable. Anyway, thank you for your help!

---

### Post by volkswagner on 2015-02-17
FYI, that online tool only works if the server is listening on the port.
As you stated the ports did not show as listening when running netstat.
I'm not familiar with the game service, so there may be some prerequisites for
the server to start listening on the port user ports.

---

