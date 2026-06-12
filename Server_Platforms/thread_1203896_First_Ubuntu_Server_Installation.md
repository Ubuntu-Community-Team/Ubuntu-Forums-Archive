---
title: "First Ubuntu Server Installation"
date: 2009-07-03
forum: Server Platforms
---

### Post by Brindle7211 on 2009-07-03
Hi guys I've been a big fan of Ubuntu for a while but now I have reached a point where the help my friends can offer me is no longer adequate so I am going to "hit the forums"

Now, as the title states I'm working on my first Ubuntu Server edition. At this time my server is the acting router for my home network configured as such through iptables, I use a samba share to backup my movies and music too and I have SSH running on it so I can tunnel while on my work's restricted network.

Eventually I plan to host 3-4 businesses websites off of my server which is why I am now turning to the folks here.

First Issue: I'm running 9.04 right now and am considering reinstalling with 8.04 LTS as it has 6 months more of updates. However I am attracted to the feature in 9.04 that offers cloud computing. Correct me if I'm wrong but in simple terms wouldn't this mean I could just build another server and start a small cloud instead of having to rebuild or upgrade the current server?

Second Issue: I'm trying to add rules to iptables > filter > input so I can "secure" my server and thus my local network as well. After reading online and developing an intermediate working knowledge of iptables I decided to block port 80 on my server with this command: *sudo iptables -I INPUT -i eth0 -p tcp -m tcp --dport 80 -j DROP*. However it doesn't work but when I check the current ruleset with *sudo iptables -t filter --line-numbers -n -L* I see what seems to be a rule that drops port 80 from any interface.

Included is the output of: sudo iptables -t filter --line-numbers -n -L
*note*(rule 1 in the forward chain is the port forward for uTorrent running on a separate PC in my home)*/note*
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
2    ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53
3    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
4    ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67
5    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:67

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     tcp  --  0.0.0.0/0            192.168.1.*        tcp dpt:*****
2    ACCEPT     all  --  0.0.0.0/0            192.168.122.0/24    state RELATED,ESTABLISHED
3    ACCEPT     all  --  192.168.122.0/24     0.0.0.0/0
4    ACCEPT     all  --  192.168.1.0/24       0.0.0.0/0
5    ACCEPT     all  --  0.0.0.0/0            192.168.1.0/24      state RELATED,ESTABLISHED
6    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
7    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable
8    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination


Third Issue: Well this is more of a question is a program like webmin or ISPConfig a good idea as they seem to take the quesswork and learning curve out of server administration. I personally would like to not have to rely on a web gui as I feel that it's another program that could be exploited by those with "unfriendly" desires.

I know this is a lot and I certainly do appreciate and thank anyone who can offer any assistance in advance.

---

### Post by juancarlospaco on 2009-07-04
First Issue: Cloud Computing is oriented to medium/experts users i think.

Second Issue: Try UFW, because is uncomplicated firewall :)

Third Issue: Whats the problem?

*Learn about KVM and Virtualization, this can help you, sandboxing, snapshots, live migration, etc*

---

### Post by swerdna on 2009-07-04
Regarding this:> However I am attracted to the feature in 9.04 that offers cloud computing. Correct me if I'm wrong but in simple terms wouldn't this mean I could just build another server and start a small cloud instead of having to rebuild or upgrade the current server?
I think you are saying that you will uase some kind of cloud computing to serve "3-4 businesses websites off of my server". Maybe I can't interpret what you said correctly.

Did you know that you can server any number of different domains off of the one server, no need for clouds, you just use Apache's Virtual Hosts function. I've got five sites served off of my home broadband connection as we speak. Check out Name Virtual Hosts on Google.

Or a bit more here: [http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)
or a bit here: [http://opensuse.swerdna.org/suseapache.html](http://opensuse.swerdna.org/suseapache.html)

Or maybe I misunderstood you.

---

### Post by Flash858 on 2009-07-04
I think you may be misinterpreting what the "cloud" does. It hosts applications so they do not have to be installed on a particular system in order to run.

I'm not sure if this affects websites, or the hosting thereof, but I would not think so. Perhaps someone with a bit more server knowledge could shed some light...

---

### Post by Brindle7211 on 2009-07-04
juancarlospaco: I'll certainly look in UFW, I also know that there's firestarter as well but I've hear good and bad things about firestarter. As far as the "Third Issue" I was wondering if it'd be a good idea to use a program like webmin or ISPConfig so I'd be able to get up and running more quickly.

swerdna: I wouldn't be using a cloud to host for 3-4 businesses I was thinking that with a cloud I'd be able to expand the processing power and storage space of my server once the server couldn't be upgraded anymore due to hardware limitations. I do apologize for being unclear.

Flash858: I agree with you I'm fairly certain I don't completely understand what a "cloud" does. I guess I'd like to know "basically" how someone would setup a "Server Farm" for the hosting of a very large website or database. However, I don't think I'll need that kind of ability anytime in the foreseeable future so we don't need to worry about that one.

---

### Post by Brindle7211 on 2009-07-04
Well due to the fact that I had to work on the 4th and it's very slow today at work. I did some digging and figured out my firewall problems. I'll go ahead and say this thread is closed I appreciate the help.

You'll be seeing me more around the forums because I've got a lot of other topics I'd like to tackle as my end goal is to have a fully functional Linux Server that can do everything if not more than a windows box but those topics are going to be qualified under other topics.

THANKS GUYS!!! :p

---

### Post by Brindle7211 on 2009-11-24
I though I'd post an update giving a good description of where my first Ubuntu Server installation is at right now.

Currently the Firewall is only allowing a select few ports communicate in and out of the local network so only the games I play, my torrents, xbox live an standard web traffic are allowed.

I have configured the tc command to prioritize and limit specific ports allowing me to let my torrents run at all available bandwidth while still being able to browse the my favorite websites with little to no interruption.

Since the first post of this thread I have setup a raid 5 using 3 250GB drives, and have shared the volume using Samba so I have a good backup medium for all the data I care about.

I am currently in the process of creating a local DNS server w/ a rather large cache to slightly speed up my internet. I am also looking into hosting a wireless network with a pci wireless card, as well as cloud computing. 

I'm especially excited about the wireless network I'm planning on hosting directly off of my server as it will eliminate another piece of hardware on my network, and I'll be able to severly limit the internet traffic to the wireless users to only 1Mbit down and 100Kbit up with only ports 20, 21, 80, and 443 open. This is so I can encourage website traffic only, although I do understand how an intermediate to advanced user could use ssh tunneling to easily get around this (that's what the speed caps are for :D).


:P:P:P On A side note since I gave up on windows server OSs I have never looked back as the amount of free software and community support available to a linux user of any distro is so large that you'd have to suffering from a lack of a pulse to see that linux is by far a better solution to any Windows based Server OS! :P:P:P

---

