---
title: "Blocking DDoS attacks"
date: 2010-04-26
forum: Server Platforms
---

### Post by eXDee on 2010-04-26
We've been attacked multiple times by several hundred IP's. This causes our VPS server to overload.
Now we're moving to Ubuntu from CentOS in anticipation of more support.
We use Apache.

The method being used is simple yet effective - its HTTP based. Many 'bots' are reloading our main page over and over, causing excessive server load and excessive bandwidth usage, saturating our 100mbit pipe. This is being done on both dynamic pages, and directly on large filesize images.

Example access log:
```
12.48.220.131 - - [20/Apr/2010:09:00:06 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
94.40.93.93 - - [20/Apr/2010:09:00:06 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
82.40.32.83 - - [20/Apr/2010:09:00:06 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
94.194.44.184 - - [20/Apr/2010:09:00:06 -0500] "GET /forums/ HTTP/1.0" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
91.86.17.251 - - [20/Apr/2010:09:00:06 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
208.95.51.144 - - [20/Apr/2010:09:00:06 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
208.95.51.144 - - [20/Apr/2010:09:00:07 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
84.105.131.184 - - [20/Apr/2010:09:00:07 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
87.176.180.49 - - [20/Apr/2010:09:00:07 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
92.12.43.233 - - [20/Apr/2010:09:00:07 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
85.201.82.80 - - [20/Apr/2010:09:00:07 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
93.86.77.129 - - [20/Apr/2010:09:00:07 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
84.108.90.205 - - [20/Apr/2010:09:00:07 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
163.117.160.167 - - [20/Apr/2010:09:00:07 -0500] "GET /forums/ HTTP/1.1" 500 7463 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR"
```

Basically, i need to somehow block clients that request too many times per minute/second. HOWEVER i do not want to block valid clients - keeping in mind our website would have less than 200 visitors at any one time.

I found this, however it would not work under the version of iptables in CentOS, resulting in "iptables: Unknown error 4294967295"
```
   1. /usr/sbin/iptables -N DDOS_CHECK    
   2. /usr/sbin/iptables -I INPUT -p tcp --dport 80 --syn -j DDOS_CHECK      
   3. /usr/sbin/iptables -A DDOS_CHECK -m hashlimit --hashlimit 100/sec --hashlimit-burst 30 --hashlimit-mode srcip --hashlimit-name apache_DDOS --hashlimit-htable-expire 30000 --hashlimit-htable-max 65535 -j ACCEPT    
   4. /usr/sbin/iptables -A DDOS_CHECK -j LOG --log-level 4 --log-prefix DDOS --log-tcp-sequence --log-tcp-options  
   5. /usr/sbin/iptables -A DDOS_CHECK -j DROP  
```

Mod evasive is of no use. Its not multithreaded.

We implemented DoS Deflate which works partially, but due to the fact that it only checks every minute(a CRON limitation), it still becomes quite overloaded.
[http://deflate.medialayer.com/](http://deflate.medialayer.com/)

Does anyone have any suggestions or solutions? Once 10.04 is released, we will change to Ubuntu, however we need this issue fixed.

---

### Post by uberlinuxnerd on 2010-04-26
Apache mod_evasive will work around this type of attack. 

EDIT: Scrap that...

---

### Post by v8YKxgHe on 2010-04-26
Take a look at Shorewall, you can configure it up to block them. Far easier than using iptables directly.

---

### Post by eXDee on 2010-04-26
> **uberlinuxnerd said:**
> Apache mod_evasive will work around this type of attack. 

EDIT: Scrap that...

I thought the same thing. See here:
[http://www.dslreports.com/forum/r20353461-apache-modevasive-sucks-as-antiddos-protection](http://www.dslreports.com/forum/r20353461-apache-modevasive-sucks-as-antiddos-protection)

---

### Post by dragos2 on 2010-04-26
Maybe mod_security?
[http://www.modsecurity.org/](http://www.modsecurity.org/)

---

### Post by eXDee on 2010-04-26
Mod security looks promising. Anyone got any guides?

I also found HTTPD Guardian which seems to work in combination with it.

---

### Post by zmigliozzi on 2010-04-27
> 

We implemented DoS Deflate which works partially, but due to the fact that it only checks every minute(a CRON limitation), it still becomes quite overloaded.
[http://deflate.medialayer.com/](http://deflate.medialayer.com/)

Does anyone have any suggestions or solutions? Once 10.04 is released, we will change to Ubuntu, however we need this issue fixed.

If you are looking to configure deflate you can edit the cron file 

```
locate ddos.cron
```

And use this link to set up cron expressions if you would like for the script to run more frequently than 1 minute.
[http://en.wikipedia.org/wiki/CRON_expression](http://en.wikipedia.org/wiki/CRON_expression)

---

### Post by ky5u on 2010-04-27
Just do a simple shell script to do what kron does, i.e. checks for the time every X ticks.  If X>than your argument (how often to run) it runs the stuff.  Sorry if I am missing something.. not the sharpest tool in the shed here.

---

### Post by eXDee on 2010-05-04
I am literally ripping my hair out over this.

I installed mod-security and can confirm that works. I installed http-guardian, and linked mod-security to it. However using another server, i ran
```
while [ 1 ]; do wget --user-agent=Mozilla/5.0 'http://MYIPHERE';done
```
to simulate a dos attack.

However i managed 1000 successful requests of the main page and it was not blocked at all.

Then i found this to use directly with mod security
```

	# ignore requests from localhost or some other IP
	SecRule REMOTE_ADDR "^127\.0\.0\.1$" "phase:1,nolog,allow"

	# for all urls count requests per second per ip
	SecRule REQUEST_BASENAME "phase:1,nolog,pass,initcol:ip=%{REMOTE_ADDR},setvar:ip.requests=+1,expirevar:ip.requests=1"
	
	# if there where more than 5 requests per second for this IP
	# set var block to 1 (expires in 5 seconds) and increase var blocks by one (expires in an hour)
	SecRule ip:requests "@eq 5" "phase:1,pass,nolog,setvar:ip.block=1,expirevar:ip.block=5,setvar:ip.blocks=+1,expirevar:ip.blocks=3600"
	
	# if user was blocked more than 5 times (var blocks>5), log and return http 403
	SecRule ip:blocks "@ge 5" "phase:1,deny,log,logdata:'req/sec: %{ip.requests}, blocks: %{ip.blocks}',status:403"
```
But this does not work. Once again, i can repeatedly request a file over and over and over.

Does anyone have any method to prevent this?

---

### Post by bobbobagan on 2010-05-04
I ended up playing around with this some more (FYI: Me and eXDee manage the same server). I ended up finding out blacklist wasn't configured correctly, and wasn't set to use IP tables (information found out from here: [http://www.commandlineisking.com/2009/05/rate-limiting-and-dos-protection-in-mod.html](http://www.commandlineisking.com/2009/05/rate-limiting-and-dos-protection-in-mod.html))

Anyway, I still couldn't get the script to ban me if I ran the following command
```
while [ 1 ]; do wget --user-agent=Mozilla/5.0 '[http://MYIPHERE]("http://myiphere/")';done
```

However if I ran this command:
```
while [ 1 ]; do wget '[http://MYIPHERE]("http://myiphere/")';done
```

I would be presented with a 403 error. Eventually, after setting up the blacklist script correctly (under /sbin) I was banned, but only because I ran the later command first.

Does this help anyone with more understanding of our problem?

---

### Post by ghost_ryder35 on 2010-05-04
look into mod_limitipconn, this apache module does just what it says.  You can limit the number of open connections any IP has to your apache server.  I would use this in connection with this iptable configuration.

```

## Any other connection on 80 send to the input chain HTTP_WATCHING
-A ufw-before-input -p tcp --dport 80 -m state --state NEW -j HTTP_WATCHING
## Set the name that will be used to keep track of offenders in /proc/net/ip_*
-A HTTP_WATCHING -p tcp --dport 80 -m state --state NEW -m recent --set --name HTTP_ATTACK
## Keep track of connections, if 4 connections have been hit, log any attackers
-A HTTP_WATCHING -p tcp --dport 80 -m state --state NEW -m recent --update --seconds 3 --hitcount 5 --rttl --name HTTP_ATTACK -j ufw-logging-deny
## Drop the packet, dont let the attacker know we are listening anymore
-A HTTP_WATCHING -p tcp --dport 80 -m state --state NEW -m recent --update --seconds 3 --hitcount 5 --rttl --name HTTP_ATTACK -j DROP
## Accept any HTTP connections that have not violated the rules
-A HTTP_WATCHING -p tcp --dport 80 -m state --state NEW -j ACCEPT

```

Obviously adjust the thresholds to your sites needs.

---

### Post by windependence on 2010-05-04
To do this correctly, it should be done at the firewall level and the firewall being a totally separate box. Trying to block attacks on your server consumes resources as you have seen and can easily lead to the box being brought down even if blocking is successful as all an attacker has to do is send enough traffic to your host to overload the CPU and they have effectively done what they set out to do. 

Your server should be behind a hardware based firewall or a dedicated security server like pfsense, monowall, or shorewall as has been suggested. That way, the attack is purely on the firewall box and those packets can simply be filtered and dropped.

-Tim

---

### Post by cdenley on 2010-05-04
> **windependence said:**
> Your server should be behind a hardware based firewall or a dedicated security server like pfsense, monowall, or shorewall as has been suggested. That way, the attack is purely on the firewall box and those packets can simply be filtered and dropped.


How can PFSense filter attacks like the one in the original post?

---

### Post by windependence on 2010-05-04
There are numerous ways to do this in pfsense, or in many other products. If it were me I would set up squid to do some filtering, but I am sure there are plenty of other ways. Also, if this is an enterprise class web site, I would think an investment in something like watchdog or cisco pix might be a good idea. Sure, you can't filter legitimate requests, but once you know where they are coming from it is much better to block those IPs or IP blocks from the firewall box rather than using resources on your server, don't you agree?

-Tim

---

### Post by windependence on 2010-05-04
Just in case I wasn't clear, squid can be set up right from the pfsense box and it works great that way. You can set up caching proxy or reverse proxy right in the pfsense GUI.

-Tim

---

### Post by cdenley on 2010-05-04
> **windependence said:**
> There are numerous ways to do this in pfsense, or in many other products. If it were me I would set up squid to do some filtering, but I am sure there are plenty of other ways. Also, if this is an enterprise class web site, I would think an investment in something like watchdog or cisco pix might be a good idea. Sure, you can't filter legitimate requests, but once you know where they are coming from it is much better to block those IPs or IP blocks from the firewall box rather than using resources on your server, don't you agree?


I specifically asked about the attack in the original post because the requests come from all different IP's from different countries. Maybe if more of the log was posted, there might have been 20 or 30 IP's, and the attacker is cycling through them. Or maybe the attacker was spoofing his IP. Blacklisting IP's in a hardware firewall or PFSense doesn't seem like it would work in this case. I think the only filtering which would work, since the attacker seems to be using a request that could match a legitimate user and there is no pattern to the source IP, would be to filter based on the same repeated request using the same useragent string, or possibly by comparing all HTTP headers to differentiate between the attacker and legitimate users, assuming the attacker's headers never change. Perhaps squid could do this?

---

### Post by eXDee on 2010-05-04
> **bobbobagan said:**
> However if I ran this command:
```
while [ 1 ]; do wget '[http://MYIPHERE]("http://myiphere/")';done
```

I would be presented with a 403 error. Eventually, after setting up the blacklist script correctly (under /sbin) I was banned, but only because I ran the later command first.

Does this help anyone with more understanding of our problem?
FYI this is blocking you because of a blank useragent. If you check the logs you'll find that mod security blocks this. Thats why i had to set a useragent.

We don't have access to a 2nd box as its a VPS.
I'll try ipconlimit also.

The attacks i don't think are large enough to cause the firewall to be overwhelmed however.

---

### Post by windependence on 2010-05-04
> **cdenley said:**
> I specifically asked about the attack in the original post because the requests come from all different IP's from different countries. Maybe if more of the log was posted, there might have been 20 or 30 IP's, and the attacker is cycling through them. Or maybe the attacker was spoofing his IP. Blacklisting IP's in a hardware firewall or PFSense doesn't seem like it would work in this case. I think the only filtering which would work, since the attacker seems to be using a request that could match a legitimate user and there is no pattern to the source IP, would be to filter based on the same repeated request using the same useragent string, or possibly by comparing all HTTP headers to differentiate between the attacker and legitimate users, assuming the attacker's headers never change. Perhaps squid could do this?
To be honest, I see this stuff in my logs all the time and I never get so many that the system is slow, but I have gotten them trying passwords and ports every second or so. This is why IMHO there may be another problem as I don't even filter that stuff unless I can identify the IP block like say from China or another problem area. I don't like to filter by IP because I could be filtering legitimate requests. Load balancing would probably be better to mitigate this type of thing. Many inexperienced web admins THINK they are being attacked when I see this traffic ALL the time and don't pay much attention to it.

-Tim

---

### Post by ghost_ryder35 on 2010-05-04
> **eXDee said:**
> FYI this is blocking you because of a blank useragent. If you check the logs you'll find that mod security blocks this. Thats why i had to set a useragent.

We don't have access to a 2nd box as its a VPS.
I'll try ipconlimit also.

The attacks i don't think are large enough to cause the firewall to be overwhelmed however.
exdee i thought this at first but wget uses 'User-Agent: Wget/*version*' if no user agent is passed as an argument.  to null out user agent use 
```

while [ 1 ]; do wget --user-agent="" 'http://MYIPHERE';done

```
then modsecurity would be blocking based on missing useragent string

---

### Post by eXDee on 2010-05-05
> **ghost_ryder35 said:**
> exdee i thought this at first but wget uses 'User-Agent: Wget/*version*' if no user agent is passed as an argument.  to null out user agent use 
```

while [ 1 ]; do wget --user-agent="" 'http://MYIPHERE';done

```
then modsecurity would be blocking based on missing useragent string
I saw this also, when i read the documentation for wget. But if you see the 
```
[Tue May 04 15:30:08 2010] [error] [client MYIPHERE] ModSecurity: Access denied with code 403 (phase 2). Match of "rx ^apache.*perl" against "REQUEST_HEADERS:User-Agent" required. [file "/etc/apache2/conf.d/modsec.v2.rules.conf"] [line "329"] [id "990011"] [msg "Request Indicates an automated program explored the site"] [severity "NOTICE"] [tag "AUTOMATION/MISC"] [hostname "MYIPHERE"] [uri "/"]

```
So i suppose it just means it blocked wget by its useragent, rather than a blank one. Whoops. Same effect and irrelevant anyway.

> **scoott271 said:**
> I also found HTTPD Guardian which seems to work in combination with it.[/url]
Yes. This is what im having trouble with - HTTPD Guardian isnt actually doing anything!
If you know how to get it going, i'd love to know.

---

