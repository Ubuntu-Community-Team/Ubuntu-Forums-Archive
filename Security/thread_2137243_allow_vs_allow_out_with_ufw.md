---
title: "allow vs allow out with ufw"
date: 2013-04-20
forum: Security
---

### Post by clearski on 2013-04-20
Hello!

This is rather a network question, but it's really basic stuff, so I'm posting it up here.

I am using ufw as my firewall. Until recently I've only used GUFW to edit rules, but today I tried some manual config and it worked perfectly. And it was really cool. Actually, I realised that ufw was active and rules were applied without having to start GUFW. Nice! :)

But I've got a question.

What is the difference between these two statements:

[I]To                                              From
--                                                --[/I]
*192.168.1.1 465      ALLOW       192.168.1.50*

and

*192.168.1.1 443   ALLOW OUT   192.168.1.50*


I am not talking about the ports, but the "OUT" statement (.50 is my machine, and .1 is the router).

Both rules allow connections from my machine to the gateway and then out to WAN. Everything works fine. But what does that "OUT" mean, how is it different from simple "ALLOW"?

Thank you!

---

### Post by coldraven on 2013-04-20
Have a look here and see if it makes sense.   [http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html)

> 
**ufw** supports both ingress and egress filtering and users may optionally        specify a direction of either **in** or **out** for either incoming or outgoing        traffic.  If  no  direction  is  supplied, the rule applies to incoming        traffic.
 Eg:           
ufw allow in http          
ufw reject out smtp

---

### Post by clearski on 2013-04-20
> **coldraven said:**
> Have a look here and see if it makes sense.   [http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ufw.8.html)


I am a bit confused because I did a *netstat* and there are no 465 or 443 ports open on my machine, so I am not sure I understand what incoming traffic means. What other incoming traffic could be allowed, besides the connections which originate and are established from my machine out and then back in as a response (ALLOW OUT)? Is it possible to have traffic to 465 / 443 if my machine is not the source of such connection? How does it affect me if I'm not running any servers with 465 / 433 as open ports?

I feel like I'm not having a right perspective on this...

Thank you.

---

### Post by coldraven on 2013-04-20
I don't know for sure, I too am a bit confused by ports.
My best guess would be to use the OUT to anticipate running a program that wants to connect to the internet.
Recently I was tempted to install a .deb file from a foreign video streaming site. I aborted the install when the "Do you trust this file?" message appeared.
If I had installed it, but had previously blocked all unnecessary ports using the OUT format, I suppose it would prevent my data being stolen.

Hopefully someone else will enlighten us on this subject.

---

### Post by clearski on 2013-04-20
I gave some thought about it and I think that an explanation would be:

**ALLOW OUT** means that an application / service that originates from me (with a local ip and/or port specified) is allowed through the firewall outside.

**DENY OUT** means that an application / service that originates from me (with a local ip and/or port specified) is not allowed through the firewall outside even to the router, but it's simply blocked as soon as it's trying to pass to the outer edge (firewall) of my machine.

**DENY IN** means that an application / service that comes from WAN or (through) my gateway is not allowed through the firewall, but it's blocked on the outside edge of my machine (given my local IP and/or port is specified).
[B]
ALLOW (IN)[/B] means that an application / service which eventually comes from WAN through my router / gateway (or even from the router itself) and which isn't necessary a response to a request started from my machine, but wants to reach my machine through my local IP or any specified port on my localhost is allowed to pass through the firewall. However, I am not sure that such an unwanted application or service could open up any port on my localhost as long as I'm not running any server, that is as long as the ports are closed?

Yes, it would be great to have somebody confirm my thoughts or give a clearer perspective on this.

---

### Post by wildmanne39 on 2013-04-20
*Thread moved to **Security Discussions**.*

---

### Post by The Cog on 2013-04-21
I think you understand nicely, but I don't like the terminology - I always thing of a service being something that listens for incoming connections. So I prefer to talk about connections originating from somewhere. With that, I'll just rephrase what you wrote:

ALLOW OUT means that a connection that originates from me (with a local ip and/or port specified) is allowed through the firewall to the outside.

DENY OUT means that a connection that originates from me (with a local ip and/or port specified) is not allowed through the firewall to the outside even to the router, but it's simply blocked as soon as it's trying to pass to the outer edge (firewall) of my machine.

DENY IN means that a connection that comes from other machines (on my local network or on the internet) not allowed through the firewall, but it's blocked on the outside edge of my machine (given my local IP and/or port is specified).

ALLOW (IN) means that a connection which eventually comes into my machine and which isn't necessary a response to a request started from my machine, but wants to reach my machine through my local IP or any specified port on my localhost is allowed to pass through the firewall. 


You are right, allowing incoming connections doesn't mean they will work - there still has to be an application or server that has opened the port. If not, the connection will be refused by the OS (port unreachable).

The default for ufw is to allow all outgoing connections but refuse all incoming connections. 

There is one oddity that I know of - an outgoing FTP connection can ask an FTP server to connect back to you to send you data. This is the normal way FTP works, and in order to not break FTP, a firewall has to monitor all outgoing FTP requests and allow the requested incoming data connections through. This behaviour means that sometimes connections are allowed in even thought the general policy is to deny incoming connections.

---

### Post by kevdog on 2013-04-21
Speaking of the FTP exception, I'm not exactly sure how ufw handles specific FTP connections, however in older versions of iptables there was an ftp conntrack module that would keep track of the ftp connections and would automatically let back in the connection.  I think in modern versions of iptables, this module is built back in and does not to be explicitly loaded in a configuration file.  Since ufw runs on top of iptables, I believe this behaivor should probably work. I don't use ufw, so I've never tested this assumption (in fact I dont really use ftp much now-a-days anyway).

---

### Post by clearski on 2013-04-21
> **The Cog said:**
> I think you understand nicely, but I don't like the terminology - I always thing of a service being something that listens for incoming connections. So I prefer to talk about connections originating from somewhere. With that, I'll just rephrase what you wrote:

  Thank you.  

Yes, I know the terminology isn't right at this time because I just started learning and I don't still discriminate easily between processes/servers/applications/protocols etc. I can make some differences, but it will require some reading, asking and time spent to dig all these. So, I appreciated your corrections.  

However, an established connection originating from an applications which opened up port 443 on localhost (as I am now connected to ubuntuforums.org) allows replies back, otherwise I couldn't read this page. I understand that packets are counted and marked through every node they have to pass so the reply knows the way back. I guess that's pretty secure, isn't it? I guess I don't have to worry that someone "on the way" could intercept and redirect packets and make them look like they're coming from the destination they were supposed to belong to, but instead receive a sort of "trojan horse".  

Here's my final ufw config after a few days of reading, including bodhizazen's guide. .R is the router through which I'm going out, and .W is my workstation's internal address.   I have no servers running except cups (which only listens to 127.0.0.1).               

To_______________                   Action___________                               From
        [ 1] 192.168.R______ALLOW OUT______192.168.W 53/udp (out) 
[ 2] 192.168.R______ALLOW OUT______192.168.W 993/tcp (out) 
[ 3] 192.168.R______ALLOW OUT______192.168.W 993/udp (out) 
[ 4] 192.168.R______ALLOW OUT______192.168.W 465/tcp (out) 
[ 5] 192.168.R______ALLOW OUT______192.168.W 443/tcp (out) 
[ 6] 192.168.R______ALLOW OUT______192.168.W 80/tcp (out) 
[ 7] 192.168.R______ALLOW OUT______192.168.W 80/udp (out) 
[ 8] 192.168.R______ALLOW OUT______192.168.W 3689/tcp (out) 
[ 9] 127.0.0.1______ DENY IN__________Anywhere 
[10] 192.168.W_____ DENY IN_________Anywhere  


Basically, I only allowed DNS traffic to router, Gmail traffic through secure ports, web (secure and normal ports) and of course Rhythmbox (3689). Any other connections are refused.  I am not sure that the rule [1] is necessary because I inserted it a few hours ago, but I'd been able to connect with my applications even if it wasn't specified that the firewall should let UDP/53 packets out, somehow the localhost knew how to reach the router. But I read on the forum the 53 out should be allowed, so I wrote that rule.  Does anyone see anything wrong about this config? 

 Thanks a lot and have fun!

---

### Post by The Cog on 2013-04-21
An established connection does indeed allow packets in both directions. So a request to a web server and the response will both happen on the same connection. The connection is outgoing from you to the web server, but since you started it, response packets from the server are allowed in. Ftp is unusual in that it starts a second connection to transfer the data - the response is never sent over the "control" connection that requests the data.

I don't think I like your ufw config. Firstly, line 9 is breaking cups. Even users on your local PC will not be able to use the cups print server any more.

Second, I don't think you need the ALLOW OUT lines. I think ufw allows outgoing connections by default anyway.

Thirdly, even if the ALLOW OUT lines were needed, I think they're wrong. In general, when a client connects to a server, the client will use a random high port at his end of the connection, and will connect to the well-known-number port that the server is listening on. For example if there is a web server on 1.1.1.1, it will be listening on port 80 (these numbers are listed in file /etc/services). But if 2.2.2.2 were to connect to the web server, he would use a random port number (e.g. 1357) for the port number his end, and may well use a different port number for every request. Bearing this in mind, line 7 for example would allow outgoing connections from the web server on 192.168.W to 192.168.R, despite the fact that no-one on 192.168.R is even allow to make incoming connections to it.

---

### Post by clearski on 2013-04-21
Don't ask me how it's possible, but I was able to print with rule [9] active. I only got one account on my computer and that's me.

Yes, I noticed (but I had other things to ask first :) ) that are always high-numbered ports that applications using TCP open on localhost when they establish a connection to a remove server. And these numbers are different for every request to a server.

A netstat result:

tcp        0      0 192.168.W:52009     some_address:443             ESTABLISHED
tcp        0      0 192.168.W:46397     some_other_address:443    ESTABLISHED


Basically I understand that what you're saying is to let any application choose a random high port of its own (and don't tell it to connect through 80, 443 etc) if it wants to connect to a WAN address for basic browsing and email? Because I don't have any server running local except cups. And only use ports and protocols rules in case I'm running a server or do some forwarding, NAT etc?

So my ufw config rules should be:

sudo ufw insert 1 allow proto tcp/udp from 192.168.W to any
sudo ufw insert 2 deny from any to 192.168.W ?

---

### Post by The Cog on 2013-04-22
> So my ufw config rules should be:

sudo ufw insert 1 allow proto tcp/udp from 192.168.W to any
sudo ufw insert 2 deny from any to 192.168.W ? 
I can't speak exactly for ufw because I've never used it. 
But I do know that if you just use "sudo ufw enable" without any other ufw configuration, it allows all connections outgoing, denies all connections incoming, and allows all local processes to connect to each other. I think this default configuration is fine for most usage. I don't know how you return ufw to its default configuration after it's been altered though.

I think you are at a lever now where you are probably able to use
```
sudo iptables -nvL
```
and figure out what ufw is doing and why.

---

### Post by clearski on 2013-04-22
I took your advice and let UFW do its default job, accept outgoing connections and deny incoming ones.

If the ufw configuration file has been altered, here's a way to bring it back to default rules.

First of all, all user-added rules must be deleted.

```
sudo ufw delete 1 
``` 

This command must be repeated for every rule (1 to X) until *sudo ufw status* returns no rule. 

Then we flush the old rules, set the new ones (incoming & outgoing) and restart the firewall to its default settings.

```

sudo ufw reload
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw reload 
```

Now *sudo ufw status* will show that the firewall is active. The  incoming & outgoing rules are active, but not shown, all we got from  querying the status is: "Active".

I will start looking, reading and playing with IPtables, because sudo ufw enable / disable isn't too funny. :smile:

*Thank you for you help and information!*

I think the subject of this thread received an answer, so it could be marked as SOLVED.

---

