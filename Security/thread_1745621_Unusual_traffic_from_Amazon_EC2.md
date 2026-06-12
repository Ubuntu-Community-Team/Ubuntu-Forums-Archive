---
title: "Unusual traffic from Amazon EC2"
date: 2011-05-01
forum: Security
---

### Post by chris0161 on 2011-05-01
p { margin-bottom: 0.21cm; }  Has anyone else seen this:
 

 Last night my old Sony Vaio laptop which connects via wired Ethernet and runs Ubuntu 10.10 started hammering the network out onto the Internet.
 

 Fired up Wireshark and found lots of traffic between my machine and 174.129.193.12 which I did a whois on and found belonged to Amazon EC2 Cloud Server. The port on my machine was an unknown 5000+ but the port on the remote system was 443 the port used by https, however no browser was running.
 

 Did a search and put together a couple of iptable commands to block this IP address which stopped the traffic.
 

 I then used nmap and netstat and found port 3000 open and another connection to IP address 91.189.89.76 which I also blocked. Unusually no info exists on this IP when you do a whois.
 

 At first I thought it might be some sort of sync as this machine has Ubuntu One running on it, however it could also be something else.
 

 Any ideas / comments on this most welcome.

---

### Post by relay_man on 2011-05-01
The IP 174.129.X.X is in fact amazon.

IP 	:	174.129.193.12 	    Neighborhood
Host 	:	ec2-174-129-193-12.compute-1.amazonaws.com    OK
Country 	:	United States   


The other IP you listed is:

IP 	:	91.189.89.76 	    Neighborhood
Host 	:	grape.[COLOR="Red"]**canonical**[/COLOR].com    OK
Country 	:	United Kingdom


Amazon doesn't bother me,


 but the second one may be suspect..... ;)   ;) 

I like this site for looking up basic IP info:

[http://ip-lookup.net/index.php](http://ip-lookup.net/index.php)

---

### Post by chris0161 on 2011-05-01
Thanks [relay-man]("http://ubuntuforums.org/member.php?u=750638") for the link and looking up the IP. That is a good site I will use it again.

The connection generated a lot of packets and slowed my web connection right down.

I don't know why Amazon would be transmitting so much data to my computer.

Unfortunately I can't look at the packets as they are encrypted.

---

### Post by rookcifer on 2011-05-01
> **chris0161 said:**
> I don't know why Amazon would be transmitting so much data to my computer.

Because Ubuntu One uses Amazon for it's cloud hosting.  Therefore, if you have anything synchronized using Ubuntu One, then it will be connecting to the Amazon servers quite often (it probably does it periodically even if you have nothing synchronized).

Maybe there should be a sticky that includes this info.  This is the 2nd thread about it in the last two days.

---

