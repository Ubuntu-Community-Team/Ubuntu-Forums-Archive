---
title: "Windows clients can't send or receive using email client behind my Squid3 Proxy"
date: 2011-10-18
forum: Server Platforms
---

### Post by LtPitt on 2011-10-18
I have an Ubuntu 10.04 box acting as Squid Transparent Proxy. Navigation is perfect: my windows clients have no troubles.

The problem I have now is that they are not able to send or receive mail using outlook (or any other pop3 / smtp client).
Pinging from any windows client command prompt external servers (like 208.67.222.222) doesn't work. The only thing working is navigation using proxy on 3128.
What can I do to solve the problem?

My iptables shouldn't be an issue...

iptables -L gives

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

but my nmap localhost give:

Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 997 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
3128/tcp  open  squid-http
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.15 seconds


I can add further details but I don't know what could be needed to solve the problem.

---

### Post by newbie-user on 2011-10-19
It doesn't look like there are any ports in iptables that are open for email.

---

### Post by LtPitt on 2011-10-20
I think that's the problem too...

How can I set iptables to open such ports?

I see that there are many options like ACCEPT or FORWARD and I've messed a bit (backupping everything before with iptables-save) with savage copy'n'paste suggestions coming from google but I was never able to see nmap showing open ports for 25 and 110 on localhost :/

---

### Post by LtPitt on 2011-10-27
I've tried open up ports from cli or webmin but still I can't telnet port 25 or 110...

What's wrong? :(

---

### Post by SeijiSensei on 2011-10-27
You haven't really given us enough detail to answer these questions.  I take it you have clients sitting behind the squid box.  Where is the email server located?  Is it on the same network as the clients, or is it external to your network?  

If you're trying to reach external hosts, you need more than just squid.  It only proxies requests for port 80 on remote servers; your users need access to other ports as well.  To accomplish this you need to set up "network address translation" using iptables on the same server.  See the section entitled "Ubuntu Internet Gateway Method" in [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) for details.

---

### Post by LtPitt on 2011-10-28
Hello my friend.

You got the point:

I have clients on my network ---> squid proxy ---> internet ----> my pop3 and smtp server (external).

The old squid proxy used to work without problems and I still have access to the pc (I didn't format it yet) but I can't use it because an iptables-save on the old proxy and an iptables-restore on the new one gives only errors (probably because different distros and linux kernel versions).

So I'd just like to understand how things work to "evolve" while solving the problem :)

So you think that I should set this pc as gateway too?

Isn't it a culprit when it comes to internet content filtering?

A smart user deleting the proxy details from its browser could surf the internet roaming free or not?

Thanks :)

---

### Post by SeijiSensei on 2011-10-28
Use [transparent proxying]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html").  Then you don't need to configure the browsers, and all requests will be pushed through squid automatically.

---

### Post by LtPitt on 2011-11-07
Sounds good: I'll try to implement that.

Just another question: I've read a bit about ufw and opening ports now seems very easy.

I have this nmap on my localhost:

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-11-07 14:52 CET
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 997 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
3128/tcp  open  squid-http
10000/tcp open  snet-sensor-mgmt

Then I did:


sudo ufw allow 25


And, after that, I've checked again my nmap...

Same result :/

Port 25 is not opened...
Why?

I'll solve the proxy trouble with the hint below but now I'd just like to understand how opening ports works...

---

### Post by SeijiSensei on 2011-11-07
> **LtPitt said:**
> Port 25 is not opened...
Why?

You probably don't have a server like Postfix or sendmail listening on port 25.  nmap doesn't list open ports; it lists ports to which a connection can be made.

---

### Post by LtPitt on 2011-11-07
Oh I got it...

I just though I'd be able to open ports with ufw and use nmap to check if it worked but I get what you taught me :)

Thanks!

---

### Post by LtPitt on 2012-01-20
Everything worked great until I decided to turn on user authentication (simple text file) on squid.

Now mail is not working anymore :/

I've tried:

iptables -t nat -A POSTROUTING -p TCP --dport 25 -j MASQUERADE 
iptables -t nat -A POSTROUTING -p TCP --dport 110 -j MASQUERADE
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

Absolutely no luck.

I've searched really everywhere but all the topics about this lead to nothing.

The problem is: using a squid proxy with authentication and let users receive and send mail using outlook express or similar.

It must be iptables related but I have no clues...

Please help me :(

---

### Post by SeijiSensei on 2012-01-20
What about all the other rules you need, like a rule for ESTABLISHED and RELATED traffic?  Do you have those as well?  Can we see the entire ruleset?

Squid in transparent mode only affects requests to port 80; it has no effect on requests for other ports like 25 or 143.  I don't know why this changed when you added authentication to the proxy, but I'd guess you made some other changes as well.

Are you sure you enabled IP forwarding in /etc/sysctl.conf?  Is forwarding permitted in iptables?

---

### Post by LtPitt on 2012-01-20
Ehm...

I wish I was so expert :/

What kind of data should I provide to help you to help me? :)

Here's my iptables -L:

> hain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere


---

### Post by SeijiSensei on 2012-01-20
If you're routing traffic between a LAN and the Internet you need more rules that that.  Try starting with the rules in [this article]("http://www.debian-administration.org/articles/23") and see if that helps.

I'll warn you that he uses eth1 to represent the external (Internet) interface and eth0 for the internal (LAN) interface.  If you have them reversed, as I do, you'll need to swap "eth0" and "eth1" in all the places they appear.

---

### Post by LtPitt on 2012-01-22
Great info: thanks!

The squid server has a single NIC and can get on the internet and solve names using opendns servers witout problems.

configuration on server: ip 192.168.1.210 subnet 255.255.255.0 gateway 192.168.1.5

On clients I use: ip 192.168.1.x subnet 255.255.255.0 gateway 192.168.1.210

Since I have a single NIC could I face problems?

---

### Post by SeijiSensei on 2012-01-22
How are packets passed to the Squid server?  You must have a router some place else that forwards port 80 requests to the Squid server, no?  Or are all the client machines set up manually to use the proxy?

Whether you can connect to remote ports like 25 or 143 depends on the settings in your router plus any additional limitations that your ISP might impose.  That's why I said originally that adding authentication to Squid shouldn't directly affect whether an email client like Thunderbird or Evolution can connect to a remote mail server.

Similarly if you're reading mail with a browser-based service like GMail, you're using port 443 for HTTPS.  Squid can't proxy HTTPS requests without considerable additional configuration, so if you're pushing port 443 requests through the proxy, that's a mistake.

---

### Post by LtPitt on 2012-01-23
All our clients are configured manually to proxy ip and port (3128 ) in browser settings.

I think I just need to find how to let the proxy act as gateway and forward port 25 and 110 to real gateway, right?

---

### Post by SeijiSensei on 2012-01-23
No, it can't do that.  Your machines need to talk to remote mail servers directly through the router.  Squid won't help with this at all.

If you have a router that's the default gateway for your clients, you need a set of rules on the router to forward traffic to remote sites and masquerade for them.  Please look at the ruleset I posted earlier from debian-administration to see a good starting point.

---

### Post by LtPitt on 2012-03-20
ok I admit:

I am ignorant and wasn't able to implement your correct suggestion but...

It works! :D

I did it this way:


# Port forwarding smtp
iptables -t nat -A PREROUTING -p TCP -d squidip --dport 25 -j DNAT --to smtpserverip:25
iptables -t nat -A PREROUTING -p UDP -d squidip --dport 25 -j DNAT --to smtpserverip:25

# Port forwarding pop3
iptables -t nat -A PREROUTING -p TCP -d squidip --dport 44122 -j DNAT --to smtpserverip:110
iptables -t nat -A PREROUTING -p UDP -d squidip --dport 44122 -j DNAT --to smtpserverip:110

---

