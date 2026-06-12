---
title: "emc-server client - how do I S 'n D this puppy?"
date: 2010-01-02
forum: Security
---

### Post by Baffled Lemming on 2010-01-02
I'm caught on the arc of a rather steep learning curve. 

I apparently have a nasty virtual server of some kind put on my system by some naughty hacker.    I noticed from Wireshark a lot of randomized UDP ports going in and out of the computer. 

It was all coming out of IPv6 UDP, but it seems these were just a variety of spoofed ports.  So I blocked all IPv6 and what came up in Wireshark a whole lot of these came up:  

10.101.13.157 (me) 74.125.47.109 (google) emc-gateway > pop3s [ACK] Seq=418 Ack=1975 Win=8767 Len=0   

This is on Port 1273 which is apparently the port the media server from EMC uses.  I force my email through google's secure server by IP address via port 995.   I should also note that after trying to mess around with IPTables/UFW/Shorewall/the usual suspects I have a situation where I can get gmail, but can't get a web page up in Firefox or email from a pop3 domain from a regular domain I use.   Can't ping or tracert out either.    

How can I find this Virtual server that appears to be on my system and remove it, and block the hole that apparently let it in?     Prior to blocking UDP, Nessus also noted that I have a few things which I don't know what they are  
itelsesrverport on (3719/udp 
nms_topo_server at 1486/tcp
mdns (5353/udp)  

I should note I'm a relative noobe.  Everything I learned about Wireshark, Nessus, nc, and netstat has been gained in the last week or two.    Any help gratefully accepted.   

Lem

---

### Post by Baffled Lemming on 2010-01-03
Anyone?  

Even if you don't know, help suggestions on where to find X shell session scripts that launch at startup would be helpful, particularly as this appears to be what launches this server.

---

### Post by BkkBonanza on 2010-01-03
Let's back up a step. How are you determining this information? That packet you mention above could just be part of an email check. Outgoing on port 1273 has nothing in particular to do with emc. Common port usage is for incoming traffic and is not at all definitive. Anything could be using any port especially when you don't know what it is.

Start by showing us output "netstat -lntpu" to see what processes are actually listening on any ports.

Also current connections by "netstat -ntp" would be useful, though maybe a bit long for here if a lot is going on.

From that we can zero in on interesting activity.

(If you start looking at wireshark logs you are likely to see a lot of generic activity anyway - there will be arp traffic, udp traffic for dhcp and dns and who knows what else not necessarily bad...)

---

### Post by Baffled Lemming on 2010-01-05
Thanks for your response!  

when I do netstat -grpu I get the screenshot below.  

I looked up port numbers and saw that it was an emc server of some kind and then saw that that was what it said in Wireshark.  

Nessus discvoered a big hole in my security which I passed, but I am still getting this interesting link-local connection to the gateway--isn't that a LAN thing?  I am wondering because I'm not on a LAN.  

I have a couple of questions you might be able to help me with.  

1. This may seem like a silly question, but how do I connect to a particular port to see what is going through it?  So if you have a UDP port of 58354 on 127.0.0.8, what utility, and what are the commands to see what's going through just that port?  

2.  How do I either configure SSH to reject any connections from the Internet or alternately attack superstrong encryption onto it, so it can't be accessed without my knowledge?  Also, can I limit access to SSH to just my computer, for example?  Or disable it all together?

3.  I am looking for a secure way to have an IRC channel thorugh which I can do secure instant messaging, but without letting any old IP in the door.  Can you suggest something? 

4.  Likewise for Skype, is there a way to filter skype so that you just get your VOIP channel and not the fifteen IPs that seem to come streaming in the door with it?  

Thanks very much for your help and advice. 

Lem

---

### Post by BkkBonanza on 2010-01-05
> **Baffled Lemming said:**
> 
when I do netstat -grpu I get the screenshot below.  

This isn't a very useful command for this purpose. It shows your routing table not your open/listening ports. For that information use the ones I suggested.
> 
I looked up port numbers and saw that it was an emc server of some kind and then saw that that was what it said in Wireshark.  

There are lists of what ports are used by what services but for the most part they are irrelevant. It's possible for services to be configured for any port and many applications use ports randomly. Never assume that connections on some port are what they are "listed" to be. 
> 
Nessus discvoered a big hole in my security which I passed, but I am still getting this interesting link-local connection to the gateway--isn't that a LAN thing?  I am wondering because I'm not on a LAN.  

If you are connected to a router (gateway) then that is still a LAN, just a LAN with only two nodes. I don't think link-local is a problem. It probably indicates your router isn't configured for dhcp.
> 
1. This may seem like a silly question, but how do I connect to a particular port to see what is going through it?  So if you have a UDP port of 58354 on 127.0.0.8, what utility, and what are the commands to see what's going through just that port?  

You can use Wireshark or tcpdump with filter options. Both can display or log data through chosen ports. But you need to learn more about how networks work before either will make sense. To learn which options read "man tcpdump" and use google to find tutorials on these topics. 
> 
2.  How do I either configure SSH to reject any connections from the Internet or alternately attack superstrong encryption onto it, so it can't be accessed without my knowledge?  Also, can I limit access to SSH to just my computer, for example?  Or disable it all together?

ssh encryption is very strong as is by default. Your main vulnerability with ssh is using weak passwords. Use key authentication instead to improve that. Again google about how to setup key authentication. If you do not need ssh then certainly don't run it at all. 

sudo apt-get remove openssh-server

will remove it. You ccan always put it back later if you decide.
> 
3.  I am looking for a secure way to have an IRC channel thorugh which I can do secure instant messaging, but without letting any old IP in the door.  Can you suggest something? 

I have no idea how to run irc securely. I never use it. It seems to me like something that has no place on a secured server but maybe I'm wrong.
> 
4.  Likewise for Skype, is there a way to filter skype so that you just get your VOIP channel and not the fifteen IPs that seem to come streaming in the door with it?  

Skype is peer-2-peer based so this is normal behavior for it. If you don't want it doing that then configure your firewall to ensure the port it listens on is closed. For me this is enough to cut it down to one connection usually.

Hope this helps out.

---

### Post by Baffled Lemming on 2010-01-05
BKKBonanza,

Here are a couple of useful screen shots.   They are the netstat you asked for the other is of a netstat just after I was attacked by hackers. 

Here is what has been happening. 
- After Nessus noted there was a big security hole I wiped the hard disk anled Ubuntu.   This is of course not ideal.  Reinstalled everything and blocked ftp and now port 53 (after this attack).  
-  WHile I was running wireshark a hacker came in and apparently changed the permissions on a lot of stuff including the file I was working on--the result was a blank screen in wireshark but I still managed to save the file and another one that wasn't blank.  I just couldn't read them until I figured out how to do chmod. 
- They seem to be using google ips as proxies--I know you can do that with a search by choosing cache in a search.
- all this is going in and out of UDP I think.  There was a lot of dns lookup on port 53 so I blocked it.  

As you can see I have been having a "Windows moment" although I must say Ubuntu is much better than Windows in that I am gradually grasping what is wrong.  Also got lots of incriminating packets from that last wireshark scan--its European tonight.  

Lem

---

### Post by BkkBonanza on 2010-01-06
You need to run netstat as sudo, ie. "sudo netstat -lntpu" otherwise it doesn't show what process is using the port.

Your second screen appears to be just a few connections to web servers. My guess is when you run it as sudo you'll see that Firefox is using those connections.

If you block port 53 (outgoing) then you will have a hard time using the web. It's used for DNS and any program that needs to resolve names will use it. For example, when wireshark wants to add name info to the traffic log it will do a series of DNS lookups. Even netstat will use DNS if you don't use the -n option.

So far I haven't seen any indication that anything unusual is going on or that you have any idea what you're talking about when you describe being hacked.

Are you running Wireshark as sudo? To be able to capture any traffic it needs to have root privileges. 

I have never heard of any kind of proxies at google. Are you sure you're not just setup for using google dns services? I don't see how this has any connection with cached searches there. The statements you make are baffling, for sure.

---

