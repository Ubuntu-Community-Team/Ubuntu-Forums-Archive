---
title: "Ubuntu forum failure or browser hijacking?"
date: 2009-11-18
forum: Security
---

### Post by lovinglinux on 2009-11-18
Something odd just happened when I was trying to reply to a thread. Ubuntu forum address has been redirected to this:

```
http://200.171.222.97/wsc/html/redirect.html?CPURL=http%3A//ubuntuforums.org/index.php
```

The destination IP:

```
OrgName:    Latin American and Caribbean IP address Regional Registry 
OrgID:      LACNIC
Address:    Rambla Republica de Mexico 6125
City:       Montevideo
StateProv:  
PostalCode: 11400
Country:    UY

ReferralServer: whois://whois.lacnic.net

NetRange:   200.0.0.0 - 200.255.255.255 
CIDR:       200.0.0.0/8 
NetName:    LACNIC-200
NetHandle:  NET-200-0-0-0-1
Parent:     
NetType:    Allocated to LACNIC
NameServer: NS.LACNIC.NET
NameServer: NS2.LACNIC.NET
NameServer: NS-SEC.RIPE.NET
NameServer: NS2.DNS.BR
NameServer: NS3.AFRINIC.NET
NameServer: SEC3.APNIC.NET
NameServer: TINNIE.ARIN.NET
Comment:    This IP address range is under LACNIC responsibility for further
Comment:    allocations to users in LACNIC region.
Comment:    Please see http://www.lacnic.net/ for further details, or check the
Comment:    WHOIS server located at http://whois.lacnic.net
RegDate:    2002-07-27
Updated:    2009-04-29
```

The screenshot of the page it opened:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136803&stc=1&d=1258604442[/IMG]

Fortunately, I was running NoScript, but I'm not sure if my browser has been compromised or if was a glitch on Ubuntu forums. There is nothing unusual in the authentication logs.

Unfortunately, I forgot to test other addresses to see if they would be redirected. The problem has gone since I rebooted, but I also changed my IP address, rebooted my modem and stopped Ktorrent completely before rebooting.

.

---

### Post by FuturePilot on 2009-11-19
I don't know but "CaptureUser.do" sounds bad. :|

---

### Post by lovinglinux on 2009-11-19
> **FuturePilot said:**
> I don't know but "CaptureUser.do" sounds bad. :|

Yep, I thought the same thing.

I wasn't browsing any other web site, just Ubuntu forums, but I was doing some torrent download at the time the problem occurred and UPnP was enabled. So I guess it could be a router hijack or something. 

What should I do?

---

### Post by doas777 on 2009-11-19
not sure, but i think I got something like that last month.it did seem like the domain was trying to be an international portal or some such, but had a shady feel.

---

### Post by kyuubi777 on 2009-11-19
it would be pretty impressive if it was a server hack... the fact that it only happened to you (as far as we know) makes me think it was a personal attack

---

### Post by lovinglinux on 2009-11-19
I did some googling and found that page is from my ISP. I guess it was a glitch in the DNS server or something. I have opened it using another Firefox profile, but I'm still investigating to check if the web site is not fake.

---

### Post by doas777 on 2009-11-19
> **lovinglinux said:**
> Yep, I thought the same thing.

I wasn't browsing any other web site, just Ubuntu forums, but I was doing some torrent download at the time the problem occurred and UPnP was enabled. So I guess it could be a router hijack or something. 

What should I do?


well, if it was a hijacking attack (XSS/CSRF/etc), those are usually a problem that manifests in odd behavior on the site you were logged into, rather than malware download. probably changing your password, and fully logging out and back in to the forums is sufficient. usually these attacks are carried out by clicking on a bad link somewhere on the forum. usually the goal is to steal your cookie/authentication token, and with it your session. 

but then again, noscript catches lots of xss exploits so I would be supprised if it didn't warn you.

---

### Post by cdenley on 2009-11-19
If your ISP is sending you to their server which is apparently redirecting you, it sounds like some sort of captive portal to me.

---

### Post by Lars Noodén on 2009-11-20
Normally retrieving a page works like this:

```

 xhtml+css+js       xhtml+css+js            xhtml+css+js    
**You** <------------- **various networks** <------ **Ubuntu Forums**

```

It can sometimes work like this due to the characteristics of HTTP, DNS, and IPv4:

```

                    xhtml+css+js+*js2*
                      **MysteryHost**
                          +-+
xhtml+css+js+*js2*          | |                  xhtml+css+js
**You** <------------ **various**-+ +-**networks** <------ **Ubuntu Forums**

```

Partial solutions include HTTPS instead of HTTP, DNSSEC with DNS, and IPv6 with IPSec instead of IPv4.  Not running client-side scripts, is of course a good idea.   If you didn't have the script blocked it would have run.  There are a lot of problems around running randoms scripts that have been ignored or shouted down lately.  

At the bottom of it all, the HTTP protocol is not really set up to be running stateful sessions.  The WWW is a great retrieval system, and a lot can be done with server side scripts.  Client side scripting can be done with java or java applets.  However, there are a lot of issues there, but they are about the same issues as you have with the situation now, just that they were brought up when computer science dominated the development of online services rather than marketing or politics.

---

### Post by Mi11z on 2009-11-20
> **FuturePilot said:**
> I don't know but "CaptureUser.do" sounds bad. :|


i agree, and lol mexican hackers.

---

### Post by CharlesA on 2009-11-20
> **Mi11z said:**
> i agree, and lol mexican hackers.

Was that really necessary?

---

### Post by jessiebrownjr on 2009-11-20
> **CharlesA said:**
> Was that really necessary?

I was wondering what made him say that lol... Was it a random racist comment or did  Imiss something? lol

---

### Post by Lars Noodén on 2009-11-21
Ok.  We're onto something important.  Important enough for the thread is being drawn off topic.

I see the same error often when connecting to Ubuntu forums and about a third of the requests time out some days.  

One thing that will help is if scripts from third party sites are *not* included.  If the forum "needs" the yahooapis.com scripts, then serve them via an ubuntu domain.  If it is a problem to have the scripts on the ubuntu servers, then use Apache's mod_rewrite or mod_proxy to at least serve them using the Ubuntu domain.  That won't help the scripts, which are problems in and of themselves, but it might help the speed and it will simplify diagnosis of this problem.

---

### Post by CharlesA on 2009-11-22
When does that error occur? I haven't had anything like that happen on any vBullitin forums I've visited.

---

### Post by lovinglinux on 2009-11-22
> **CharlesA said:**
> When does that error occur? I haven't had anything like that happen on any vBullitin forums I've visited.

I think was a problem in my ISP. The redirected page appears to be theirs, but I couldn't confirm it. They wanted to send someone here and told me they couldn't confirm the IP address of the site by phone. I guess it was a clueless attendant, as usual. So, I said it wasn't needed.

---

### Post by OpSecShellshock on 2009-11-23
If you live in Brazil (don't actually confirm this, as it won't be necessary for anyone else to know), then it might be your ISP. The script was blocked, which is certainly a good thing. Looks like it's a Java action mapped to a class called "capture user" which would have generated an on-the-fly targeted web page. Just guessing, but it may have been a fake login screen.

---

### Post by lovinglinux on 2009-11-23
> **OpSecShellshock said:**
> If you live in Brazil (don't actually confirm this, as it won't be necessary for anyone else to know), then it might be your ISP. The script was blocked, which is certainly a good thing. Looks like it's a Java action mapped to a class called "capture user" which would have generated an on-the-fly targeted web page. Just guessing, but it may have been a fake login screen.

Yes, I'm in Brazil.

---

