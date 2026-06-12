---
title: "Why won't shorewall let me apt-get upgrade?"
date: 2008-06-02
forum: Server Platforms
---

### Post by Twizzle on 2008-06-02
I installed Shorewall firewall using [this]("http://flurdy.com/docs/postfix/") guide and it seems to work fine. I can SSH in and use webmin and I can install and remove new programs. However, if I 'sudo apt-get update', I get a long list of 'failed to fetch [http://.](http://.)....'

If I stop shorewall it works. I am assuming there is a simple setting I have missed. My rules are:
```
#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/	MARK
#							PORT	PORT(S)		DEST		LIMIT		GROUP
#SECTION ESTABLISHED
#SECTION RELATED
SECTION NEW
SSH/ACCEPT	all	$FW
Ping/ACCEPT	net	$FW

#Permit all ICMP traffic FROM the firewall To the net zone
ACCEPT	$FW	net	icmp
# mail lines
SMTP/ACCEPT	net	$FW
SMTPS/ACCEPT	net	$FW
Submission/ACCEPT	net	$FW
IMAP/ACCEPT	net	$FW
IMAPS/ACCEPT	net	$FW

#web
Web/ACCEPT	net	$FW
Webmin/ACCEPT	net	$FW

#SMB
#SMB/ACCEPT	$FW	all
#SMB/ACCEPT	loc	$FW
SMB/ACCEPT	net	fw
SMB/ACCEPT	fw	net
Web/ACCEPT	fw	net
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

Can any one help? I really don't want to remove shorewall just yet as I don't believe in my router firewall 100%  :)

---

### Post by gpredrag on 2008-06-02
```

SMB/ACCEPT	net	fw
SMB/ACCEPT	fw	net
Web/ACCEPT	fw	net

```

What's "fw". Shouldn't it be $FW?
What are your shorewall zones called?

---

### Post by Twizzle on 2008-06-02
I think shorewall automatically sets fw and $FW for the firewall.

Anyway, I used webmin to set SMB up and it works. Not sure if it would make a difference if I changed it but if it ain't broke.... (the Samba part that is!)

My zones are fw and net

---

### Post by quelx on 2008-06-02
> **Twizzle said:**
> I think shorewall automatically sets fw and $FW for the firewall.

Anyway, I used webmin to set SMB up and it works. Not sure if it would make a difference if I changed it but if it ain't broke.... (the Samba part that is!)

My zones are fw and net

It is my understanding that **fw** is not a zone like **net** or **loc**, since it is one address.  You need to use **$FW** in place of **fw** as suggested by gpredrag.

from *[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)*
> In the two-interface sample, the line below is included but commented out. If you want your firewall system to have full access to servers on the internet, uncomment that line.

#```
SOURCE    DEST        POLICY      LOG LEVEL    LIMIT:BURST
$FW        net         ACCEPT
```

and from *[http://www.shorewall.net/manpages/shorewall-zones.html](http://www.shorewall.net/manpages/shorewall-zones.html)*

> firewall

    Designates the firewall itself. You must have exactly one 'firewall' zone. No options are permitted with a 'firewall' zone. The name that you enter in the ZONE column will be stored in the shell variable $FW which you may use in other configuration files to designate the firewall zone.

---

### Post by gpredrag on 2008-06-03
Also, what about allowing DNS from firewall to the net?
How is resolving DNS names, like
```

dig www.google.com

```
or
```

nslookup www.google.com

```
working when shorewall is on

---

### Post by Twizzle on 2008-06-04
OK, I have changed them to $FW as recommended and I have done a bit more reading on shorewall (I guess I should have done that before blindly following a guide!)

However, it still won't work. This is now my rules:

```
SECTION NEW
SSH/ACCEPT	all	$FW
Ping/ACCEPT	net	$FW

#Permit all ICMP traffic FROM the firewall To the net zone
ACCEPT	$FW	net	icmp
# mail lines
SMTP/ACCEPT	net	$FW
SMTPS/ACCEPT	net	$FW
Submission/ACCEPT	net	$FW
IMAP/ACCEPT	net	$FW
IMAPS/ACCEPT	net	$FW

#web
Web/ACCEPT	net	$FW
Webmin/ACCEPT	net	$FW

#SMB
SMB/ACCEPT	net	$FW
SMB/ACCEPT	$FW	net
DNS/ACCEPT	$FW	net
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

I added the DNS rule but when I tried nslookup... I got a connection time out error.

---

### Post by quelx on 2008-06-04
Is your DNS server in the **loc** or **net** zone?

This line disappeared from your most recent post, you'll need it for apt-get to work over http
 ```
Web/ACCEPT	$FW	net
```

For giggles try 
```
ACCEPT	$FW	all
```

---

### Post by Twizzle on 2008-06-05
I assume my DNS server is in the net zone (I have no loc zone) My setup is:

cable modem - router - two PC's (one server and one desktop)

It is the server that I am trying to make as secure as possible with shorewall.

I have two zones, net and fw.

I tried
```
Web/ACCEPT	$FW	net
```

again and still get the same error.

If I add
```
ACCEPT	$FW	all
```

When I check the firewall I get an error that says

```
ACCEPT fw net is a POLICY and should be moved to the policy file
```

I take it all it would do is let **all** traffic out of the server. I may be being naive but are there any security issues with this?

(And yes I am prepared to be slammed for not understanding the firewall system! But hey, I have been using Linux for about three months now :) )

---

