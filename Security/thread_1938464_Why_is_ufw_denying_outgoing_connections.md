---
title: "Why is ufw denying outgoing connections?"
date: 2012-03-09
forum: Security
---

### Post by Paqman on 2012-03-09
I have just enabled ufw on my VPS, and it's now blocking several things from working (mail, a couple of Wordpress plugins)
My current rules are:
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
22                         ALLOW IN    Anywhere
25/tcp                     ALLOW IN    Anywhere
8443                       ALLOW IN    Anywhere

```

So if it's supposed to allow outgoing, why am I hitting a brick wall? Everything works fine with ufw disabled. Web pages are being served fine, and I can connect to ports I've specifically allowed (ie: SSH and 8443). I've tried explicitly allowing the IPs that one of my Wordpress plugins requires, but even that made no difference.

---

### Post by kevdog on 2012-03-09
My guess is that your are still blocking ports that your programs need to send packets through.  Your list of allowed incoming ports is really small.

---

### Post by Ms. Daisy on 2012-03-10
I don't see DNS port 53, don't you need that?

You may want to look at this thread
[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

I've also found it helpful to look at my firewall logs when I'm trying to run something that is blocked.  It will list the port numbers the service is trying to use.

---

### Post by Dangertux on 2012-03-10
> **Paqman said:**
> I have just enabled ufw on my VPS, and it's now blocking several things from working (mail, a couple of Wordpress plugins)
My current rules are:
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
22                         ALLOW IN    Anywhere
25/tcp                     ALLOW IN    Anywhere
8443                       ALLOW IN    Anywhere

```So if it's supposed to allow outgoing, why am I hitting a brick wall? Everything works fine with ufw disabled. Web pages are being served fine, and I can connect to ports I've specifically allowed (ie: SSH and 8443). I've tried explicitly allowing the IPs that one of my Wordpress plugins requires, but even that made no difference.

Make sure your VPS hosts doesn't block mail, some will but most don't. What worpdress plugins actually create a socket outside of httpd? 

Are you sure this is your firewall blocking these instead of maybe just a bad config. Meaning do they work if you disable your firewall?

```

sudo ufw disable

```

You might also need to allow imap ports depending on what your mailserver is. 

If you can provide more info I can probably help better, but realistically that configuration shouldn't be denying any outbound connections (per the outbound allow all policy you have set)

Hope this helps.

---

### Post by Paqman on 2012-03-10
> **Dangertux said:**
> Make sure your VPS hosts doesn't block mail, some will but most don't. What worpdress plugins actually create a socket outside of httpd? 


The plugin is Akismet, and all it requires is [TCP on 80]("http://blog.akismet.com/akismet-hosting-faq/"). 

> 
Are you sure this is your firewall blocking these instead of maybe just a bad config. Meaning do they work if you disable your firewall?


Yep, everything works lovely with ufw down.

> 
If you can provide more info I can probably help better, but realistically that configuration shouldn't be denying any outbound connections (per the outbound allow all policy you have set)


Hence my confusion. I have added in DNS btw, that was an oversight after resetting my rules and starting from scratch. Syslog does spit out the fact that the mailserver is failing CNAME lookup, so I'd already made sure all was ok in DNSland previously. Not quite sure where to go with this. I'm pretty n00bish when it comes to servers, but it's not like I'm trying to do anything complicated.

---

### Post by kevdog on 2012-03-10
The best thing I can advise you is to log the dropped packets.  I'm not sure how to turn on logging of dropped or rejected packets via ufw, however I'm sure a simple search will help you.  Once you have logging on the rejected packets, its probably fairly easy to track down what port is being blocked.

---

### Post by Ms. Daisy on 2012-03-11
> **kevdog said:**
> The best thing I can advise you is to log the dropped packets.  I'm not sure how to turn on logging of dropped or rejected packets via ufw, however I'm sure a simple search will help you.  Once you have logging on the rejected packets, its probably fairly easy to track down what port is being blocked. I believe the default logging level low will report those, but if not you can bump it up to medium or high
```
sudo ufw logging high
```

---

### Post by Paqman on 2012-03-11
This is exasperating, I've set logging to high, but I'm not seeing anything in the logs except from UFW itself. I get the failed CNAME lookup from qmail.

---

### Post by kevdog on 2012-03-11
I tell you what -- I'll write an iptables script for you if you want.  

What incoming ports do you want open?  I'll make sure all your output ports are open if you want.

---

### Post by sammiev on 2012-03-11
I see he's allowing the ports in but are there any ports open to allow out? If the out is set for deny, then he would have to open the desired ports out as well.

---

### Post by Dangertux on 2012-03-11
No, OP has a default outbound policy to ACCEPT.. 

This still doesn't make sense to me, I'm not saying you're wrong but I'm having a hard time figuring out how this is a firewall issue.

Did you add any custom rules to /etc/ufw/before.rules or /etc/ufw/after.rules?

---

### Post by Paqman on 2012-03-11
No custom rules. As a further bit of faultfinding I just tried pinging one of the servers for my Wordpress plugin:
[LIST]
[*]ufw disabled = ping ok
[*]ufw enabled = ping failed
[*]ufw enabled and rule added to explictly allow out to that IP = ping failed
[/LIST]

So even though my default policy is allow out, ufw is blocking outgoing, even if I add a rule allowing it. Also, I though ufw's default was to allow pings regardless.

If this isn't a ufw problem, how come everything is fine with ufw disabled?

---

### Post by emiller12345 on 2012-03-11
UFW is a handler for iptables, and it might be easier to see what is actually going on if you dump the iptables rules directly
```
sudo /sbin/iptables-save
```
will list the available iptables rules currently loaded.

---

### Post by Paqman on 2012-03-11
With ufw enabled I get this:
```
# Generated by iptables-save v1.4.4 on Sun Mar 11 20:28:26 2012
*mangle
:PREROUTING ACCEPT [161:13992]
:INPUT ACCEPT [161:13992]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [128:42099]
:POSTROUTING ACCEPT [128:42099]
COMMIT
# Completed on Sun Mar 11 20:28:26 2012
# Generated by iptables-save v1.4.4 on Sun Mar 11 20:28:26 2012
*filter
:INPUT DROP [4:196]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [36:24139]
:ufw-after-forward - [0:0]
:ufw-after-input - [0:0]
:ufw-after-logging-forward - [0:0]
:ufw-after-logging-input - [0:0]
:ufw-after-logging-output - [0:0]
:ufw-after-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-before-input - [0:0]
:ufw-before-logging-forward - [0:0]
:ufw-before-logging-input - [0:0]
:ufw-before-logging-output - [0:0]
:ufw-before-output - [0:0]
:ufw-logging-allow - [0:0]
:ufw-logging-deny - [0:0]
:ufw-reject-forward - [0:0]
:ufw-reject-input - [0:0]
:ufw-reject-output - [0:0]
:ufw-skip-to-policy-forward - [0:0]
:ufw-skip-to-policy-input - [0:0]
:ufw-skip-to-policy-output - [0:0]
:ufw-track-input - [0:0]
:ufw-track-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-user-input - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
:ufw-user-logging-forward - [0:0]
:ufw-user-logging-input - [0:0]
:ufw-user-logging-output - [0:0]
:ufw-user-output - [0:0]
-A INPUT -j ufw-before-logging-input 
-A INPUT -j ufw-before-input 
-A INPUT -j ufw-after-input 
-A INPUT -j ufw-after-logging-input 
-A INPUT -j ufw-reject-input 
-A INPUT -j ufw-track-input 
-A FORWARD -j ufw-before-logging-forward 
-A FORWARD -j ufw-before-forward 
-A FORWARD -j ufw-after-forward 
-A FORWARD -j ufw-after-logging-forward 
-A FORWARD -j ufw-reject-forward 
-A OUTPUT -j ufw-before-logging-output 
-A OUTPUT -j ufw-before-output 
-A OUTPUT -j ufw-after-output 
-A OUTPUT -j ufw-after-logging-output 
-A OUTPUT -j ufw-reject-output 
-A OUTPUT -j ufw-track-output 
-A ufw-after-logging-forward -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-after-logging-input -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-after-logging-output -j LOG --log-prefix "[UFW ALLOW] " 
-A ufw-before-forward -j ufw-user-forward 
-A ufw-before-input -j ufw-user-input 
-A ufw-before-logging-forward -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW AUDIT] " 
-A ufw-before-logging-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW AUDIT] " 
-A ufw-before-logging-output -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW AUDIT] " 
-A ufw-before-output -j ufw-user-output 
-A ufw-logging-allow -j LOG --log-prefix "[UFW ALLOW] " 
-A ufw-logging-deny -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-skip-to-policy-forward -j DROP 
-A ufw-skip-to-policy-input -j DROP 
-A ufw-skip-to-policy-output -j ACCEPT 
-A ufw-track-output -p tcp -m state --state NEW -j ACCEPT 
-A ufw-track-output -p udp -m state --state NEW -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 53 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 53 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 25 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 25 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 110 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 110 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 143 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 143 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 22 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 22 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 80 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 80 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 443 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 443 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 67 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 67 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 68 -j ACCEPT 
-A ufw-user-input -p udp -m udp --dport 68 -j ACCEPT 
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] " 
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable 
-A ufw-user-limit-accept -j ACCEPT 
COMMIT
# Completed on Sun Mar 11 20:28:26 2012
# Generated by iptables-save v1.4.4 on Sun Mar 11 20:28:26 2012
*nat
:PREROUTING ACCEPT [17:872]
:POSTROUTING ACCEPT [14:896]
:OUTPUT ACCEPT [14:896]
COMMIT
# Completed on Sun Mar 11 20:28:26 2012

```

---

### Post by emiller12345 on 2012-03-11
One thing that I'm not noticing is the loopback adapter rules.  This might help, but it's not a UFW solution. Maybe someone else can figure it out how to fix this in UFW.

```
$ sudo iptables -I INPUT 1 -i lo -j ACCEPT
$ sudo iptables -I OUTPUT 1 -o lo -j ACCEPT
```

if this works then the lo may be the issue

---

### Post by Paqman on 2012-03-13
> **emiller12345 said:**
> One thing that I'm not noticing is the loopback adapter rules.  This might help, but it's not a UFW solution. Maybe someone else can figure it out how to fix this in UFW.

```
$ sudo iptables -I INPUT 1 -i lo -j ACCEPT
$ sudo iptables -I OUTPUT 1 -o lo -j ACCEPT
```

if this works then the lo may be the issue

What would the absence (or presence) of this actually do?

---

### Post by spynappels on 2012-03-14
> **Paqman said:**
> What would the absence (or presence) of this actually do?

The presence of a "lo allow" rule allows the box to essentially talk to itself using TCP/IP and is normally very important.

I also do not see any RELATED/ESTABLISHED rules, could it be that the outbound connection is allowed, but the reply is dropped?

It might be better to just spend a little bit of time looking at iptables directly and writing your own firewall script, rather than using ufw, just don't try to use both at the same time.

I'm sure one (or more) of us could help you write a little iptables script to do exactly what you need.

---

### Post by JKyleOKC on 2012-03-14
In post number 14 above, the "ufw-before-output" rule jumps to a target of "ufw-user-output" but no rule appears in the listing to be added to that chain, which leaves that chain empty! I would expect this to cause the rule to return to the OUTPUT chain and then the default policy for the OUTPUT chain to send packets to the ACCEPT target, but I'm not certain that this would happen. The packets might be getting lost, instead.

Perhaps adding a rule that creates a rule in "ufw-user-output" to jump to ACCEPT would solve things. Adding a ufw rule to accept "any" to "any" for output should take care of such an addition to iptables...

Hope this helps!

---

### Post by Paqman on 2012-03-15
> **JKyleOKC said:**
> 
Perhaps adding a rule that creates a rule in "ufw-user-output" to jump to ACCEPT would solve things. Adding a ufw rule to accept "any" to "any" for output should take care of such an addition to iptables...


I just did:
```
sudo ufw allow out from any to any
```
...no change unfortunately.

---

### Post by l0co on 2012-03-27
I have the same problems with my UFW but at openvz server. This might be a problem with firewall initialization. Someone could check if this might be one of the problems mentioned there [http://blog.bodhizazen.net/linux/how-to-use-ufw-in-openvz-templates/](http://blog.bodhizazen.net/linux/how-to-use-ufw-in-openvz-templates/). I will be able only at the end of the week to play around this.

---

