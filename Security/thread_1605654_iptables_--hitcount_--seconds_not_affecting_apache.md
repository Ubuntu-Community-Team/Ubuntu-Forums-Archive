---
title: "iptables --hitcount --seconds not affecting apache2"
date: 2010-10-25
forum: Security
---

### Post by gewone on 2010-10-25
Hi!

```
sudo iptables -A INPUT -i eth1 -p tcp --dport 22 -m state --state NEW -m recent --set
sudo iptables -A INPUT -i eth1 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 30 --hitcount 2 -j DROP

```
That limits inbound SSH connections to 2/30s, check.

```
sudo iptables -A INPUT -i eth1 -p tcp --dport 411 -m state --state NEW -m recent --set
sudo iptables -A INPUT -i eth1 -p tcp --dport 411 -m state --state NEW -m recent --update --seconds 30 --hitcount 2 -j DROP

```
That limits inbound connection on my DC server to 2/30s, check.

```
sudo iptables -A INPUT -i eth1 -p tcp --dport 80 -m state --state NEW -m recent --set
sudo iptables -A INPUT -i eth1 -p tcp --dport 80 -m state --state NEW -m recent --update --seconds 30 --hitcount 2 -j DROP

```
That does _not_ drop connections betyond the 2nd in a 30s interval. Oh no, no limitations at all seem to apply. What am I doing wrong here?


Ty in adv~

---

### Post by CharlesA on 2010-10-25
How are you testing it?

---

### Post by gewone on 2010-10-26
I'm setting the rule via SSH on a remote server that runs Apache2. Then I'm entering [http://remoteadress](http://remoteadress) on client-side Firefox; where I'm pressing F5 (CTRL+R) repeatedly. Page loads every time! ;/

---

### Post by CharlesA on 2010-10-26
Tested it on my test machine and it's not blocking the connections, but I have a feeling it's due to how the apache handles connections - everything is transfering in a sinple "session" and not muliple "hits" like the other services use.

---

### Post by bodhi.zazen on 2010-10-26
> **gewone said:**
> I'm setting the rule via SSH on a remote server that runs Apache2. Then I'm entering [http://remoteadress](http://remoteadress) on client-side Firefox; where I'm pressing F5 (CTRL+R) repeatedly. Page loads every time! ;/

You would need to post ALL your rules. I assume you are accepting connections earlier in your rule set (the rules you posted work as expected on my server).

If you want to limit DOS attacks try something like this :

```
#Accept RELATED and ESTABLISHED connections.
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Limit new connections
sudo -A INPUT -p tcp --dport 80 -m state --state NEW -m limit --limit 50/minute --limit-burst 5 -j ACCEPT

#Use either a policy of DROP or DROP the rest.
sudo -A INPUT -p tcp --dport 80 -j DROP
```

If you mash on the f5 button with those settings you will see the connection slow.

Apache should be able to handle these settings easily (your hit count is way too restrictive).

---

### Post by tapas_mishra on 2010-10-27
> **bodhi.zazen said:**
> 


# Limit new connections
sudo -A INPUT -p tcp --dport 80 -m state --state NEW -m limit --limit 50/minute --limit-burst 5 -j ACCEPT

I was following this thread so asking I checked man page of iptables 
> --limit-burst number
              Maximum initial number of packets to match: this number gets recharged by one every time the limit specified above is not reached, up to  this  num&#8208;
              ber; the default is 5.


I could not understand what it is doing.
What exactly you did by the --limit-burst parameter.

---

### Post by bodhi.zazen on 2010-10-27
> **tapas_mishra said:**
> I was following this thread so asking I checked man page of iptables 


I could not understand what it is doing.
What exactly you did by the --limit-burst parameter.

I am not sure if you are asking why I specified a --limit-burst of 5 if 5 is the default or if you are asking about --limit and --limit-burst.

For the former, educational purposes, to encourage people to read and learn more :twisted:

For the latter see this page:

[http://netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-7.html](http://netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-7.html)

Scroll down to the section on limits (it is in section 7.3).

---

### Post by bodhi.zazen on 2010-10-27
> **tapas_mishra said:**
> I was following this thread so asking I checked man page of iptables 


I could not understand what it is doing.
What exactly you did by the --limit-burst parameter.

See also : [http://blog.bodhizazen.net/linux/prevent-dos-with-iptables/](http://blog.bodhizazen.net/linux/prevent-dos-with-iptables/)

---

### Post by tapas_mishra on 2010-10-28
I checked both the links you gave
from your blog
```

&#8220;--limit-burst&#8221; is a bit confusing, but in a nutshell 200 new  connections (packets really) are allowed before the limit of 50 NEW  connections (packets) per minute is applied.

```are you referring to 200 New connections from same IP and the condition is 50 connections in a minute.
What I understand from the netfilter page and your blog is IPTABLES would see first if the request to the web server in question is coming and if more than 200 requests come (from same IP) then it will limit to 50 connections per minute(to that IP where 200 limit is applied).First the 200 request condition is checked.

So the rule 50 connections per minute will be applied only when the client request crosses 200 connections limit.
Is that right?

---

### Post by bodhi.zazen on 2010-10-28
> **tapas_mishra said:**
> So the rule 50 connections per minute will be applied only when the client request crosses 200 connections limit.
Is that right?

Yes. Keep in mind, by default, browsers make multiple connections. I think Firfox is set at 24 connections per server, and many people increase this to increase speed.

Google search "improve firefox performance connections per server" and you will find a plethora of blogs/posts advising much higher numbers connections.

Here is but one:

[http://www.technical-assistance.co.uk/kb/ffconfig.php](http://www.technical-assistance.co.uk/kb/ffconfig.php)

Using iptables for such things requires a lot of consideration, what port ? Apahce is NOT the same as ssh.

What for ? ssh - do you use scp ? SVN over ssh ? tunneling ? all these variables will influence how you apply rules in iptables.

While it may seem confusing at first, with a little practice it is actually not *that* difficult.

With that said, most of this does not apply to the vast majority of desktop users and these settings are much more useful server side.

---

### Post by tapas_mishra on 2010-10-28
> **bodhi.zazen said:**
> Yes. Keep in mind, by default, browsers make multiple connections. I think Firfox is set at 24 connections per server, and many people increase this to increase speed.

I understand this point.

[]("http://www.technical-assistance.co.uk/kb/ffconfig.php")
> **bodhi.zazen said:**
> 
Using iptables for such things requires a lot of consideration, what port ? Apahce is NOT the same as ssh.

I have used IPTABLES to NAT ,DNAT etc not to do use it the way you suggested can you suggest some where I can look some default rules(of course I will modify according to use) some sort of best practises or templates.For example for using SSH
following link
[http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html](http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)
mentions some good point similarly for admins who are not that experienced to prevent DOS attacks as a measure of precaution the default rules or guidelines which suggest what are good practices for Apache when it comes to IPTABLES.

---

### Post by bodhi.zazen on 2010-10-28
> **tapas_mishra said:**
> I understand this point.

[]("http://www.technical-assistance.co.uk/kb/ffconfig.php")

I have used IPTABLES to NAT ,DNAT etc not to do use it the way you suggested can you suggest some where I can look some default rules(of course I will modify according to use) some sort of best practises or templates.For example for using SSH
following link
[http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html](http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)
mentions some good point similarly for admins who are not that experienced to prevent DOS attacks as a measure of precaution the default rules or guidelines which suggest what are good practices for Apache when it comes to IPTABLES.

Google =)

[http://httpd.apache.org/docs/2.0/misc/security_tips.html](http://httpd.apache.org/docs/2.0/misc/security_tips.html)

As far as iptables goes and apache, assuming it is a public server, IMO there is nothing special you need to do with iptables. Allow access to port 80, block everything else.

Setting a limit, as in this thread, is icing on the cake and will not add much.

---

