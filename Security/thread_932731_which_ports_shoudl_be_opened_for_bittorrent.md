---
title: "which ports shoudl be opened for bittorrent?"
date: 2008-09-28
forum: Security
---

### Post by narf y akim on 2008-09-28
Hello, I have a problem with bittorrent. Does anyone knows what ports should I keep open? In firestarter I have opened the default 6881-6889 for this application, but nothing happens, no connection, althoug a lot of ip's appear triying to connect to the port 49089. Should I open this last one?

---

### Post by steveneddy on 2008-09-28
From this website:

[http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html](http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html)
[SIZE=3]**[URL="http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html"]```
Linux Iptables open Bittorrent tcp ports 6881 to 6889
```[/URL]**[/SIZE]


You may want to read that article.

---

### Post by lovinglinux on 2008-09-28
> **narf y akim said:**
> Hello, I have a problem with bittorrent. Does anyone knows what ports should I keep open? In firestarter I have opened the default 6881-6889 for this application, but nothing happens, no connection, althoug a lot of ip's appear triying to connect to the port 49089. Should I open this last one?

Ports 6881-6889 are the default ports for torrent, but I don't have to use them. It is not even recommended, since several ISP's cap the bandwidth on those ports. Use a single port between 49152 and 65535. No matter which port you choose, you need to configure the torrent application to listen to the port chosen,  the firewall to allow inbound connections on the same port and if you have a router, it must forward the port to your machine.

You are receiving connection attempts on port 49089 probably because the torrent application is configured to listen on this port. Check your torrent configuration and change the listening port as you wish.

Remember that we are talking about inbound connections, so other peers can connect to you using the port you choose. But you also need to request connections, so you have to create outbound rules in the firewall. Since the torrent client will connect to the port the peer choose, you should configure the firewall to "Permissive by default" in the outbound policy, otherwise you will have to create a rule for every single peer you try to connect.

---

### Post by kevdog on 2008-09-29
Not sure how you configure your firewall, but since I'm not running a large corporation, all of my outbound ports are open by default.  Only the inbound ports are filtered.

---

### Post by hyper_ch on 2008-09-29
is there a reason you installed firestarter and hence altered your default rules?

---

### Post by narf y akim on 2008-09-29
I finally could start Deluge. I've read good commentaries about it. I followed the advice of lovinglinux and open in Firestarter 6 ports, from 49200 to 49205. I'm not sure about the number of open ports, but in portforwading.com it said to enable one port for each download, then if I want to download 2 files at a time I would have to open 2 ports. That's right, isn't it? 
Another issue was to enable ports in my wireless router. I found it quite difficult but I think I could forward the 6 ports to my laptop ip. But I'm still concerned about security. It is possible that someone hack me by this open ports?
Thanks all of you for your feedback, specially to lovinglinux, I found a very good post from him.


> Not sure how you configure your firewall, but since I'm not running a large corporation, all of my outbound ports are open by default. Only the inbound ports are filtered.

Yes, the main problem is the inbound police.


> is there a reason you installed firestarter and hence altered your default rules? 

Actually, one of the reasons I abandon Win completely at home was for security issues, and when I installed Firestarter I did some changes looking for max security, but I don't know if the Bittorrent ports were open by default.

---

### Post by lovinglinux on 2008-09-29
> **narf y akim said:**
> I finally could start Deluge. I've read good commentaries about it. I followed the advice of lovinglinux and open in Firestarter 6 ports, from 49200 to 49205. I'm not sure about the number of open ports, but in portforwading.com it said to enable one port for each download, then if I want to download 2 files at a time I would have to open 2 ports. That's right, isn't it?

No, no, no.  You only need one port open, no matter how many files you are downloading. All incoming connections will pass through the same port, besides the torrent client can listen to only one port anyway. Open Deluge preferences and in the Network tab set the "TCP active port" from 49200 to 49200. Then create a rule in Firestarter to allow inbound connections on port 49200 and configure the router to forward port 49200 to your machine (internal IP).

> **narf y akim said:**
> I found it quite difficult but I think I could forward the 6 ports to my laptop ip. But I'm still concerned about security. It is possible that someone hack me by this open ports?

I guess every time you have an open port and an application listening on that port (Deluge in this case) your are at risk of being hacked, but I'm not an security expert. As far as I understand, the risk will depend on the application and the OS vulnerabilities. Nevertheless, you are more secure than using Windows anyway.

What I recommend is to open the port in the router and in Firestarter only when you are sharing files. There is no need to keep the port open all the time if you are not using it, so the risk will be reduced.

---

### Post by hyper_ch on 2008-09-30
it seems to me that altering the default rules on iptables isnt necessary for you at all.

---

### Post by narf y akim on 2008-09-30
> **lovinglinux said:**
> No, no, no.  You only need one port open, no matter how many files you are downloading. All incoming connections will pass through the same port, besides the torrent client can listen to only one port anyway. Open Deluge preferences and in the Network tab set the "TCP active port" from 49200 to 49200. Then create a rule in Firestarter to allow inbound connections on port 49200 and configure the router to forward port 49200 to your machine (internal IP).



I guess every time you have an open port and an application listening on that port (Deluge in this case) your are at risk of being hacked, but I'm not an security expert. As far as I understand, the risk will depend on the application and the OS vulnerabilities. Nevertheless, you are more secure than using Windows anyway.

What I recommend is to open the port in the router and in Firestarter only when you are sharing files. There is no need to keep the port open all the time if you are not using it, so the risk will be reduced.

Ok, now I got it! Thanks again. I'm going to open only one port in the router and I'm going to forward it to my IP. I really appreciate your attention. I'm going to test it tonight at home, and if everything goes well I think this thread could be considered as SOLVED.

In response to hyper_ch, I'm thinking in going back to the default options of Firestarter, to see if the torrent client can run. Thanks for your comments.

---

### Post by hyper_ch on 2008-09-30
you can't go back to the default options. Default iptables layout was to let everything pass. Firestarter changed that.

---

### Post by kevdog on 2008-09-30
If you want to go back to the default rules, do the following

sudo iptables -F
sudo iptables -X

That should reset the default policy.

You can check by

sudo iptables -L

There should be default acceptance on the INPUT, OUTPUT, and FORWARD chains.

---

### Post by narf y akim on 2008-09-30
Well, editing IP tables with the terminal is far beyond my knowlege for the moment and I'm afraid of doing it wrong. Anyway, I remuve the rule in Firestarter to accept inbound traffic from port 49200 (I have it open in my router) and I can still download with Deluge. But the new downloads I started only receive stream and don't send any byte (and Firestarter refuses lots of connections attemps to 49200), then I think I became a full leach, not so good for sharing. For that reason I think I should open it again.

Do you think we could tag this thread as SOLVED?, because I think my first problem (how to download torrents without high security risk) is closed. Thank you guys!

---

### Post by lovinglinux on 2008-09-30
> **narf y akim said:**
> Well, editing IP tables with the terminal is far beyond my knowlege for the moment and I'm afraid of doing it wrong. Anyway, I remuve the rule in Firestarter to accept inbound traffic from port 49200 (I have it open in my router) and I can still download with Deluge. But the new downloads I started only receive stream and don't send any byte (and Firestarter refuses lots of connections attemps to 49200), then I think I became a full leach, not so good for sharing. For that reason I think I should open it again.

Do you think we could tag this thread as SOLVED?, because I think my first problem (how to download torrents without high security risk) is closed. Thank you guys!

Did you applied the rule after creating it on Firestarter? If you created a rule on Firestarter to allow inbound connections on port 49200 it shouldn't block any connections on this port.

---

### Post by lovinglinux on 2008-09-30
Please tell me the Lenght and Protocol of blocked connections on port 49200.

If you cannot see this info on the [COLOR="Red"]**Blocked Connections**[/COLOR] list, hit CTRL+8 and CTRL+0 to display them.

How many connections blocked do you consider a lot?

Do you see connections which have your internal IP (192.168.x.x) as [COLOR="Red"]**destination**[/COLOR] in the [COLOR="Red"]**Active Connections**[/COLOR] list?

Do you see connections which have your internal IP (192.168.x.x) as [COLOR="Red"]**source**[/COLOR] in the [COLOR="Red"]**Active Connections**[/COLOR] list?

---

### Post by kevdog on 2008-10-01
I'm going to try being nice, but if you want to allow traffic on one inbound port, writing iptables rules by hand is really easy.

If you run this script you will see:

#!/bin/sh
#

IPTABLES=/sbin/iptables
MODPROBE=/sbin/modprobe

TORRENT_PORT=49920

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_nat_ftp

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


### ACCEPT rules

# Torrent Rule
$IPTABLES -A INPUT -p tcp --dport $TORRENT_PORT --syn -m state --state NEW -j ACCEPT

# Ping Rule
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

echo "Done.."
exit
### EOF ###

I'm not saying you have to run this script, however just give it a try once.  Copy this to a file, make the file executable, and then simply run the script. See if you can use bittorrent or whatever client you are using successfully.  This may not be your preferred method, however just give it a shot.  If you are planning on running servers from your machine, such as ssh or torrent or ftp, you are going to quickly find that firestarter is extremely limited.  When learning how to write iptables rules by hand, the task at first seems daunting.  It is.  However only expand your knowledge as needed.  Meaning learn in steps.  Once you have this problem solved forget about it for a while until you need to write another rule to open a port up for a different server.  You don't have to be an iptables expert and know it inside and out to write successful rules.

---

### Post by narf y akim on 2008-10-01
> **lovinglinux said:**
> Please tell me the Lenght and Protocol of blocked connections on port 49200.

If you cannot see this info on the [COLOR="Red"]**Blocked Connections**[/COLOR] list, hit CTRL+8 and CTRL+0 to display them.

How many connections blocked do you consider a lot?

Do you see connections which have your internal IP (192.168.x.x) as [COLOR="Red"]**destination**[/COLOR] in the [COLOR="Red"]**Active Connections**[/COLOR] list?

Do you see connections which have your internal IP (192.168.x.x) as [COLOR="Red"]**source**[/COLOR] in the [COLOR="Red"]**Active Connections**[/COLOR] list?

Well, I'm getting a bit confused about this. I always thought that if you want to download things with a bittorrent client you have to open a port, but actually this is not the case. It seems that without any open port I still can download, though I don't upload any byte.

Now I am running Deluge, and firestarter is blocking 30 - 40 IP's attempts to connect to the port I've just closed yesterday. Before closing it I think I had the same number of IP's connected. The length depends on the IP, for example 48, 131, 134, 52, 95, 64, 84, 75, etc. The protocols are TCP and UDP, even for the same IP connection attempt (I wonder what does the length mean).

In the Active Connections list now I see only my IP as the source and it doesn't appear in the destination column.

As you see I don't know much about these stuffs, but I think I should set the port open again if I want to download another file. Do you agree?

---

### Post by narf y akim on 2008-10-01
> **kevdog said:**
> I'm going to try being nice, but if you want to allow traffic on one inbound port, writing iptables rules by hand is really easy.

If you run this script you will see:

#!/bin/sh
#

IPTABLES=/sbin/iptables
MODPROBE=/sbin/modprobe

TORRENT_PORT=49920

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_nat_ftp

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


### ACCEPT rules

# Torrent Rule
$IPTABLES -A INPUT -p tcp --dport $TORRENT_PORT --syn -m state --state NEW -j ACCEPT

# Ping Rule
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

echo "Done.."
exit
### EOF ###

I'm not saying you have to run this script, however just give it a try once.  Copy this to a file, make the file executable, and then simply run the script. See if you can use bittorrent or whatever client you are using successfully.  This may not be your preferred method, however just give it a shot.  If you are planning on running servers from your machine, such as ssh or torrent or ftp, you are going to quickly find that firestarter is extremely limited.  When learning how to write iptables rules by hand, the task at first seems daunting.  It is.  However only expand your knowledge as needed.  Meaning learn in steps.  Once you have this problem solved forget about it for a while until you need to write another rule to open a port up for a different server.  You don't have to be an iptables expert and know it inside and out to write successful rules.

If I run this script the changes it does are permanent?, or after restarting the system turns back to the previous state? I'm afraid to mess things up. Do you know where could I find something basic to read about editing IP tables with the command line?

---

### Post by lovinglinux on 2008-10-01
> **narf y akim said:**
> Well, I'm getting a bit confused about this. I always thought that if you want to download things with a bittorrent client you have to open a port, but actually this is not the case. It seems that without any open port I still can download, though I don't upload any byte.

You don't necessarily need a port open to download, but this will slow down your connection and you will be leeching much more than seeding, because you will connect only to those peers that your client (Deluge) requests. Let's explain how bittorrent works:

- when you go to a download site you don't download the file you want, you just download a .torrent file, which is a "recipe" containing the name of the actual file you want, how many pieces the file has and at least a tracker

- a tracker is a server that stores information about files being shared and peers sharing them. When you start a .torrent file, your client (Deluge) will scrape the tracker and add your IP and listening port to the list, allowing other peers (users) to connect to you. At the same time, your client will retrieve the lists of peers/ports sharing that file, so you can connect to them.

- if you do not open a port, you will be able to request connections to other peers, but won't be able to receive requests. You still can download files, but you will connect to less peers than with a port open and you won't be able to seed. This is not necessarily bad for you, but is bad for the swarm.

> **narf y akim said:**
> It seems that without any open port I still can download, [COLOR="Red"]**though I don't upload any byte**[/COLOR].

This is not necessarily true. You are confusing connection requests with download/upload. If you don't have a port open you just don't accept incoming requests, but you can upload to the peers that your client connect to. Opening a port is just for accepting incoming requests, but the data exchange can happen both ways (up/down) after the connection is established, no matter which client requested the connection. 

When your torrent completes, then you probably won't upload anymore, because you will not accept any incoming requests. Since your file is already completed, your client will not try to request more connections, but it should accept requests. In this situation (when you are a seeder) the other peers in the swarm will try to connect to you. If you have no open port, then you will not seed.

> **narf y akim said:**
> Now I am running Deluge, and firestarter is blocking 30 - 40 IP's attempts to connect to the port I've just closed yesterday. Before closing it I think I had the same number of IP's connected. The length depends on the IP, for example 48, 131, 134, 52, 95, 64, 84, 75, etc. The protocols are TCP and UDP, even for the same IP connection attempt (I wonder what does the length mean).

First of all, you are receiving a lot of blocked connections (even with the port open) because Deluge does not handle UDP protocol. You need to check your forwarded port configuration in the router and make sure you forward only TCP protocol. If you don't do that, you will have a lot of UDP connections blocked. Additionally, open Deluge configuration and disable DHT. This should reduce the number of blocked connections considerably.

The length is the size of the packet being transfered. Lower numbers usually means some kind of ping request and not necessarily torrent pieces. I'm not an expert on this, so I could be wrong, but I get a lot of blocks with 40, 56 or 72 in length and ICMP protocol. This means the remote computer sent me a ping to check if my computer is still receiving packets. They are blocked because I have configured Firestarer to drop ICMP requests. 

There are conflicting opinions if you should block ICMP requests or not, but if you want to be stealth using those [[COLOR="Red"]**Firewall tests** [/COLOR]]("http://www.pcflank.com/scanner1.htm") then you have to block ICMP requests. Some tutorials explain that when someone is scanning your ports trying to hack your machine and you reply to ICMP requests, than the hacker knows your machine exists and will proceed probing your ports. Other tutorials explains that the hacker will know when you block ICMP requests, because there is a delay in the "unavailable" response. Maybe someone reading this thread gives us more info about this.

Nevertheless, sometimes I get blocked packets with lengths that correspond to the torrent pieces and TCP protocol. I'm not sure why they are blocked, but they are much less common than ICMP blocks.

> **narf y akim said:**
> In the Active Connections list now I see only my IP as the source and it doesn't appear in the destination column.

That's because the port you client (Deluge) is listening is closed and you are not accepting connection requests. If you open the port again you should see your IP as destination too.

> **narf y akim said:**
> As you see I don't know much about these stuffs, but I think I should set the port open again if I want to download another file. Do you agree?

Yes, you should.

---

### Post by narf y akim on 2008-10-02
I'm really glad to read so wonderful explanation. It's very clear and helpful, thaks again.

---

### Post by neilevan814 on 2009-08-10
The lights are green on some things now and yellow on others....It is very strange behavior...Not that it is affecting the performance of Vuze for my purposes, BUT I just wanted to KNOW why this is happening....

---

### Post by cariboo on 2009-08-10
I have no idea what you are talking about, please start a new thread with more information.

---

