---
title: "Server blocked by my modem login"
date: 2006-11-30
forum: Server Platforms
---

### Post by shane2peru on 2006-11-30
Ok, I have read this thread [here ]("http://www.ubuntuforums.org/showthread.php?t=306524")and it is a bit over my head.  I think I have a similar situation, but need more specific help.  I have a ZTE modem.  It has great options, and even includes an option to use it with dyndns.org - which I'm registered and using.  Here is that option from the modem setup screen: > Dynamic DNS Configuration
                         
                                      This page allows you to provide Internet users with a domain name (instead of an IP address)
to access your virtual servers. This DSL router supports dynamic DNS
 provided by the provider  'http://www.dyndns.org'. Please register this
 service at 'www.dyndns.org'.             

The user name is configured when you register the service and then
 the password will be sent to you via email.   Domain name is allocated
 to you by 'www.dyndns.org'.                                          

                              I filled all that out, and when I go to my registered Domain name, I get the Modem sign in thing, asking for user name, and password.  ?  I know there is a way to configure this, but I'm not sure how.  Please be patient, as I am a complete newbie to servers and hosting a web page.  
Here is my setup ```

             __________________
             |Internet - WWW |
             |_________________|
                            |
              ________|______
              |Modem (ZTE)|    
              |______________|
                  I
         _____I_______________
         |Router (Hawkings)|
         |___________________|
         /              I                   \
____/____      __I_____        __\__________
|   PC1   |     |Vonage|     | Ubu Server|
|______._|     |________|     |_MY PC          |_
```Any help would greatly be appreciated by this server newbie!  :-k
When I go to my local IP address (on my computer) the web page comes up.  When I go to 127.0.0.1 my web page comes up.  When I go to my registered domain name, Modem login, when I go the public IP address - Modem Login. ???

Shane

---

### Post by shane2peru on 2006-12-01
Ok, now when I go to [www.shanerice.gotdns.com](www.shanerice.gotdns.com) (my donmain for dnydns.org)  I get server not found. - So at least I'm not getting my modem now.  I have forwarded port 80 to my internal IP address.  Any ideas as to why it still is not coming up?  Thanks.

Shane

---

### Post by MJN on 2006-12-01
There's nothing in the DNS for that record...
 
```

 ; <<>> DiG 9.3.2 <<>> @localhost www.shanerice.gotdns.com A
 ; (2 servers found)
 ;; global options:  printcmd
 ;; Got answer:
 ;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 48005
 ;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0
 
 ;; QUESTION SECTION:
 ;www.shanerice.gotdns.com.    IN    A
 
 ;; AUTHORITY SECTION:
 gotdns.com.        1800    IN    SOA    ns1.dyndns.org. hostmaster.dyndns.org. 2039793442 10800 1800 604800 1800
 
 ;; Query time: 97 msec
 ;; SERVER: 127.0.0.1#53(127.0.0.1)
 ;; WHEN: Fri Dec  1 16:48:52 2006
 ;; MSG SIZE  rcvd: 103

```
 
(Note the lack of an answer section)
 
Indeed, it looks the whole domain shanerice.gotdns.com doesn't exist - are you sure you've registered it with them?
 
Mathew

---

### Post by shane2peru on 2006-12-01
Yep, just triple checked, and it is registered through them.  In normal DNS it takes up to 48 hours to propagate in the USA.  I read somewhere on there site that theres was very quick, I think because it is a subdomain that is redirected to the web page?  at any rate it is registered.  When I ping it it seems to respond correctly.  Thanks.


Shane

---

### Post by MJN on 2006-12-01
It's got nothing to do with propogation, I checked all five of the authoritive servers for dyndns.org:

```

ns5.dyndns.org [63.170.10.81]     [Reports no A record (NXDOMAIN)]    15ms
ns1.dyndns.org [63.208.196.90]    [Reports no A record (NXDOMAIN)]    13ms
ns2.dyndns.org [204.13.249.81]    [Reports no A record (NXDOMAIN)]    30ms
ns4.dyndns.org [213.155.150.205]    [Reports no A record (NXDOMAIN)]    91ms
ns3.dyndns.org [204.13.250.81]    [Reports no A record (NXDOMAIN)]    92ms

```If none of the above know about your domain, then noone else will either.

Can you show me the output of **dig [www.shanerice.gotdns.com]("http://www.shanerice.gotdns.com") A**   ? And what do you mean my 'when I ping it seems to respond correctly'? Can you post the output (including the command you entered)? Are you using the name or IP address?

Don't be misled by the 'server not found' error - it's actually meaning the IP address for the URL has not been found, and not your server itself.

Mathew

---

### Post by shane2peru on 2006-12-02
Matthew,

```

shane@shane-laptop:~$ dig www.shanerice.gotdns.com A

; <<>> DiG 9.3.2 <<>> www.shanerice.gotdns.com A
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 12643
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;www.shanerice.gotdns.com.      IN      A

;; AUTHORITY SECTION:
gotdns.com.             1800    IN      SOA     ns1.dyndns.org. hostmaster.dyndns.org. 2039818325 10800 1800 604800 1800

;; Query time: 129 msec
;; SERVER: 200.48.225.130#53(200.48.225.130)
;; WHEN: Fri Dec  1 23:51:17 2006
;; MSG SIZE  rcvd: 103

```
That is a really cool command.  This is very interesting to me, because my real web page has been hacked and spammers have been controlling my dns through a subdomain so I ran that command on my well, no it is my old domain [www.rices2peru.com](www.rices2peru.com) - Came up with a mixed results.   - that is another story for another day.
The ping command I have been using is ```
ping -v www.shanerice.gotdns.com 
``` - the results I get is the same as when I go to [www.whatismyip.com](www.whatismyip.com).  Well, at least it did yesterday.  Today, when I ping it nothing.  This is weird.  I know that the other day I ping-ed it and it showed my external IP address.  I don't know what is going on, but it seems like my IP changes more frequently now too.  Now, I just pinged it again, and it worked.  I enabled wildcard on my the dyndns.org site.  I think that may have been the problem.  Ok, now we are back to the modem log in.  Give it a try now.

Thanks for the help!
Shane

---

### Post by MJN on 2006-12-02
Okay, the zone is populated now and we're getting a result (the delay was not propogation, as these were the authoritive servers for the parent domain, but rather they were what you might call 'administrative' delays - i.e. just a delay with gotdns/dyndns putting the info into the zones):

```

mathew@rugrat:~/NewtonNet/htdocs$ dig www.shanerice.gotdns.com A

; <<>> DiG 9.3.1 <<>> www.shanerice.gotdns.com A
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12338
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.shanerice.gotdns.com.      IN      A

;; ANSWER SECTION:
www.shanerice.gotdns.com. 43110 IN      CNAME   shanerice.gotdns.com.
shanerice.gotdns.com.   60      IN      A       190.41.71.180

;; Query time: 230 msec
;; SERVER: 62.31.176.39#53(62.31.176.39)
;; WHEN: Sat Dec  2 09:42:14 2006
;; MSG SIZE  rcvd: 72

```However, whilst this is good I think you've gone off on a tangent with this DNS issue as it's got nothing to do with your modem serving pages on port 80. Indeed, far better to just stick with IP addresses at the moment as adding a layer of naming on top just clouds the issue!

So, back to IP, when you connect to [http://190.41.71.180](http://190.41.71.180) **from the outside** (i.e. not your own LAN as this can bring its own complications which we'll cover later... specifically NAT loopback) what do you see? From here, at the time of writing, I see nothing but I'm guessing we're in different time zones and you might not be connected 24/7?

Mathew

P.S. I'm intrigued by you saying the DNS for rices2peru.com has been hacked - if that's the case how have you put up a holding page? That must mean **you've** got control of the DNS and the web server your records are pointing to... :confused:

---

### Post by MJN on 2006-12-02
P.P.S. to the above - Thanks for the PM explanation re your other domains - what a palava... hope you get it all sorted soon!

---

### Post by shane2peru on 2006-12-03
Ok, yet another long story made short.  I had to switch back to my original modem.  I was having waaay to many connections problems with that modem and my wife's PC.  Mine was connected fine, but her's wasn't.  I just couldn't get the modem configured right.  I was told this modem doesn't have port forwarding, however it does have a NAT configuration section, and I blocked outside users from configuring the modem, so if requests to my IP bypass my modem I know my router has configuration for port forwarding.  Here is my modem model:  HUAWEI SmartAX MT880.  There web page is supposed to be [www.huawei.com]("http://www.huawei.com") according to the manual, but I haven't had any luck getting the page up.  If you can get the page up, you can see the manual.  

Shane

Ok, I have been brainstorming.  What if I **bridge** my modem to my router, and let my router do all the l internet setup stuff (it has the ability, to sign in via the proper avenues)  Would this get me past the modem?

---

