---
title: "This is scary &quot;Morfeus strikes again.&quot;"
date: 2010-07-22
forum: Server Platforms
---

### Post by kevin11951 on 2010-07-22
In my apache log:

```
148.206.49.128 - - [21/Jul/2010:06:26:28 -0500] "GET /roundcubemail/README HTTP/1.1" 404 2811 "-" "Morfeus strikes again."
148.206.49.128 - - [21/Jul/2010:06:26:29 -0500] "GET /rc/README HTTP/1.1" 404 2800 "-" "Morfeus strikes again."
148.206.49.128 - - [21/Jul/2010:06:26:29 -0500] "GET /webmail/README HTTP/1.1" 404 2805 "-" "Morfeus strikes again."
148.206.49.128 - - [21/Jul/2010:06:26:29 -0500] "GET /roundcube/README HTTP/1.1" 404 2807 "-" "Morfeus strikes again."
148.206.49.128 - - [21/Jul/2010:06:26:29 -0500] "GET /mail/README HTTP/1.1" 404 2802 "-" "Morfeus strikes again."
148.206.49.128 - - [21/Jul/2010:06:26:30 -0500] "GET /email/README HTTP/1.1" 404 2803 "-" "Morfeus strikes again."
148.206.49.128 - - [21/Jul/2010:06:26:30 -0500] "GET /README HTTP/1.1" 404 2797 "-" "Morfeus strikes again."
```

And I didn't really care, until I saw what it(he?) was doing...

---

### Post by lisati on 2010-07-22
I've had visits from "Morfeus strikes again" as well, so far no damage noted.

One thing I've done on my server is to install mod-defensible. This helps keep out some of the rogues.

---

### Post by noway2 on 2010-07-22
After reading this thread I got mildly curious and checked the logs from my server.  I saw a similar one: "Toata dragostea mea pentru diavola, which apparently translates from Romanian into "all my love for the devil."

It is another one of those vulnerability scanners.  Anyway, I decided to install mod_defensible as Lisati suggested, just to put another hurdle in front of them.  I suspect that these things are slightly more dangerous than the SSH bombardment as they can locate a readme file with possible information regarding the version of an application you are running that can be used to exploit it.

One thing that I do is configure apache so that all of the 'critical' php based configuration programs like myadmin, or postfixadmin, are only available via an https link AND they are only accessible from within the local LAN.  Requiring the secure connection is a preventative measure for myself to make sure I don't accidentally transmit the passwords in clear text.  If I really want to get at them remotely, I can just socks proxy with SSH and get access.

---

### Post by cdenley on 2010-07-22
> **kevin11951 said:**
> And I didn't really care, until I saw what it(he?) was doing...

Requesting non-existent files? Not much to worry about. Any kind of server is going to get scanned by bots like this. Especially web, SSH, and FTP servers. You can try to block IP's when you see requests like this, but more importantly, don't use outdated web applications with vulnerabilities such as the ones this bot is looking for.

---

### Post by richardjh on 2010-07-22
cdenley is right. Don't be overly worried. It is just someone who has changed the User Agent description in their browser.

You can get a plug in for firefox to do this if you want called "[user agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/")", I have it installed on my work PC as some Microsoft sites require IE on Windows, so I change my user agent description to IE in Firefox so I can use the site.

You can set it to whatever you like.

Admittedly someone trying to download files that aren't there is indicative of someone sniffing about for vulnerabilities or just scraping sites, but I would be amazed if there are any servers online that do not get this type of activity all the time.

Do not panic about this, there is no need for knee jerk reactions. 

If the user agent was not set to something so obviously wrong would you be so suspicious of the activity?

Just make sure your web server has secure permissions and, as much as possible, you keep all web application code patched with security updates and keep watching the logs.

---

### Post by kevin11951 on 2010-07-23
> **richardjh said:**
> cdenley is right. [B]Don't be overly worried. It is just someone who has changed the User Agent description in their browser.
[/B]
You can get a plug in for firefox to do this if you want called "[user agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/")", I have it installed on my work PC as some Microsoft sites require IE on Windows, so I change my user agent description to IE in Firefox so I can use the site.

You can set it to whatever you like.

Admittedly someone trying to download files that aren't there is indicative of someone sniffing about for vulnerabilities or just scraping sites, but I would be amazed if there are any servers online that do not get this type of activity all the time.

Do not panic about this, there is no need for knee jerk reactions. 

If the user agent was not set to something so obviously wrong would you be so suspicious of the activity?

Just make sure your web server has secure permissions and, as much as possible, you keep all web application code patched with security updates and keep watching the logs.

I know that, the name just sparked my interest.  It was when I looked closer and saw the files he was attempting to access, when it got interesting.

---

### Post by saphil on 2011-08-09
Morfeus is still around.  Hunting for the same stack of files.

---

### Post by Habitual on 2011-08-09
it looks like an attempted cPanel hack/attack judging by "roundcube" and "webmail".

---

### Post by Hack.The.Pow. on 2011-08-09
Ahhh morfeus is still kicking around.  I remember seeing those entries in my error logs a little while back.  Doesn't mean anything unless you have those applications that he is looking for.

> **noway2 said:**
> After reading this thread I got mildly curious and checked the logs from my server.  I saw a similar one: "Toata dragostea mea pentru diavola, which apparently translates from Romanian into "all my love for the devil."

It is another one of those vulnerability scanners.  Anyway, I decided to install mod_defensible as Lisati suggested, just to put another hurdle in front of them.  I suspect that these things are slightly more dangerous than the SSH bombardment as they can locate a readme file with possible information regarding the version of an application you are running that can be used to exploit it.

One thing that I do is configure apache so that all of the 'critical' php based configuration programs like myadmin, or postfixadmin, are only available via an https link AND they are only accessible from within the local LAN.  Requiring the secure connection is a preventative measure for myself to make sure I don't accidentally transmit the passwords in clear text.  If I really want to get at them remotely, I can just socks proxy with SSH and get access.

What exactly is mod_defensible?  I understand it helps block out spammers and such but how does it work?

Also isn't ssl useless if you don't buy a certificate?  Or do you have a certificate?

---

### Post by saphil on 2011-08-09
Also looks entirely automated.  It is hitting me on machines with webservers and no fqdn. [http://rbl.botslist.ca/search](http://rbl.botslist.ca/search) says it is coming from 13 ip addresses - probably places it has cracked. 

**[_195.70.62.111_]("http://rbl.botslist.ca/lookup/195.70.62.111")**

[accept: */*]("http://rbl.botslist.ca/search?name=accept:%20%5C%2A/%5C%2A")
[accept-encoding: gzip, deflate]("http://rbl.botslist.ca/search?name=accept%5C-encoding:%20gzip%2C%20deflate")
[accept-language: en-us]("http://rbl.botslist.ca/search?name=accept%5C-language:%20en%5C-us")
[connection: Close]("http://rbl.botslist.ca/search?name=connection:%20Close")
[content-length: 0]("http://rbl.botslist.ca/search?name=content%5C-length:%200")
[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-botcaps: 12]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%2012")
[x-botserial: 07D90B1C032B05203]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007D90B1C032B05203")
[x-cracker: yes]("http://rbl.botslist.ca/search?name=x%5C-cracker:%20yes")
[x-icookies: yes]("http://rbl.botslist.ca/search?name=x%5C-icookies:%20yes")
[x-peer: 195.70.62.111]("http://rbl.botslist.ca/search?name=x%5C-peer:%20195%5C.70%5C.62%5C.111")
[x-revdns: bob.vitalcomp.hu]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20bob%5C.vitalcomp%5C.hu")
[x-timestamp: 07DA0918060A09195]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA0918060A09195")
**[_198.82.184.25_]("http://rbl.botslist.ca/lookup/198.82.184.25")**

[accept: */*]("http://rbl.botslist.ca/search?name=accept:%20%5C%2A/%5C%2A")
[accept-encoding: gzip, deflate]("http://rbl.botslist.ca/search?name=accept%5C-encoding:%20gzip%2C%20deflate")
[accept-language: en-us]("http://rbl.botslist.ca/search?name=accept%5C-language:%20en%5C-us")
[connection: Close]("http://rbl.botslist.ca/search?name=connection:%20Close")
[content-length: 0]("http://rbl.botslist.ca/search?name=content%5C-length:%200")
[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-botcaps: 12]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%2012")
[x-botserial: 07DA020C0B1133156]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007DA020C0B1133156")
[x-cracker: yes]("http://rbl.botslist.ca/search?name=x%5C-cracker:%20yes")
[x-icookies: yes]("http://rbl.botslist.ca/search?name=x%5C-icookies:%20yes")
[x-peer: 198.82.184.25]("http://rbl.botslist.ca/search?name=x%5C-peer:%20198%5C.82%5C.184%5C.25")
[x-revdns: ap1.cs.vt.edu]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20ap1%5C.cs%5C.vt%5C.edu")
[x-timestamp: 07DA091806303800F]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA091806303800F")
**[_207.182.226.244_]("http://rbl.botslist.ca/lookup/207.182.226.244")**

[accept: */*]("http://rbl.botslist.ca/search?name=accept:%20%5C%2A/%5C%2A")
[accept-encoding: gzip, deflate]("http://rbl.botslist.ca/search?name=accept%5C-encoding:%20gzip%2C%20deflate")
[accept-language: en-us]("http://rbl.botslist.ca/search?name=accept%5C-language:%20en%5C-us")
[connection: Close]("http://rbl.botslist.ca/search?name=connection:%20Close")
[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-botcaps: 12]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%2012")
[x-botserial: 07D90317163A0C0D9]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007D90317163A0C0D9")
[x-cracker: yes]("http://rbl.botslist.ca/search?name=x%5C-cracker:%20yes")
[x-icookies: yes]("http://rbl.botslist.ca/search?name=x%5C-icookies:%20yes")
[x-peer: 207.182.226.244]("http://rbl.botslist.ca/search?name=x%5C-peer:%20207%5C.182%5C.226%5C.244")
[x-revdns: esb.vel.net]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20esb%5C.vel%5C.net")
[x-timestamp: 07DA09180D183030D]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA09180D183030D")
**[_211.191.178.139_]("http://rbl.botslist.ca/lookup/211.191.178.139")**

[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-archaic: yes]("http://rbl.botslist.ca/search?name=x%5C-archaic:%20yes")
[x-botcaps: 4096]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%204096")
[x-botserial: 07DA061A0C210F000]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007DA061A0C210F000")
[x-peer: 211.191.178.139]("http://rbl.botslist.ca/search?name=x%5C-peer:%20211%5C.191%5C.178%5C.139")
[x-revdns: [-]]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20%5C%5B%5C-%5C%5D")
[x-timestamp: 07DA0918100B2F3B8]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA0918100B2F3B8")
**[_213.194.149.20_]("http://rbl.botslist.ca/lookup/213.194.149.20")**

[accept: */*]("http://rbl.botslist.ca/search?name=accept:%20%5C%2A/%5C%2A")
[accept-encoding: gzip, deflate]("http://rbl.botslist.ca/search?name=accept%5C-encoding:%20gzip%2C%20deflate")
[accept-language: en-us]("http://rbl.botslist.ca/search?name=accept%5C-language:%20en%5C-us")
[connection: Close]("http://rbl.botslist.ca/search?name=connection:%20Close")
[content-length: 0]("http://rbl.botslist.ca/search?name=content%5C-length:%200")
[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-botcaps: 12]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%2012")
[x-botserial: 07D90A0D0E1235157]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007D90A0D0E1235157")
[x-cracker: yes]("http://rbl.botslist.ca/search?name=x%5C-cracker:%20yes")
[x-icookies: yes]("http://rbl.botslist.ca/search?name=x%5C-icookies:%20yes")
[x-peer: 213.194.149.20]("http://rbl.botslist.ca/search?name=x%5C-peer:%20213%5C.194%5C.149%5C.20")
[x-revdns: ns3.hostinglmi.net]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20ns3%5C.hostinglmi%5C.net")
[x-timestamp: 07DA0918121B313C8]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA0918121B313C8")
**[_213.194.149.4_]("http://rbl.botslist.ca/lookup/213.194.149.4")**

[accept: */*]("http://rbl.botslist.ca/search?name=accept:%20%5C%2A/%5C%2A")
[accept-encoding: gzip, deflate]("http://rbl.botslist.ca/search?name=accept%5C-encoding:%20gzip%2C%20deflate")
[accept-language: en-us]("http://rbl.botslist.ca/search?name=accept%5C-language:%20en%5C-us")
[connection: Close]("http://rbl.botslist.ca/search?name=connection:%20Close")
[content-length: 0]("http://rbl.botslist.ca/search?name=content%5C-length:%200")
[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-botcaps: 12]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%2012")
[x-botserial: 07D9060D081B27195]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007D9060D081B27195")
[x-cracker: yes]("http://rbl.botslist.ca/search?name=x%5C-cracker:%20yes")
[x-icookies: yes]("http://rbl.botslist.ca/search?name=x%5C-icookies:%20yes")
[x-peer: 213.194.149.4]("http://rbl.botslist.ca/search?name=x%5C-peer:%20213%5C.194%5C.149%5C.4")
[x-revdns: ns1.hostinglmi.net]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20ns1%5C.hostinglmi%5C.net")
[x-timestamp: 07DA0918121B331C5]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA0918121B331C5")
**[_78.41.204.125_]("http://rbl.botslist.ca/lookup/78.41.204.125")**

[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-archaic: yes]("http://rbl.botslist.ca/search?name=x%5C-archaic:%20yes")
[x-botcaps: 4096]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%204096")
[x-botserial: 07DA0706011635000]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007DA0706011635000")
[x-peer: 78.41.204.125]("http://rbl.botslist.ca/search?name=x%5C-peer:%2078%5C.41%5C.204%5C.125")
[x-revdns: euroavia.colocated.redunix.net]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20euroavia%5C.colocated%5C.redunix%5C.net")
[x-timestamp: 07DA0A01080F362EE]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA0A01080F362EE")
**[_80.84.245.120_]("http://rbl.botslist.ca/lookup/80.84.245.120")**

[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-botcaps: 0]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%200")
[x-botserial: 07D90B14060F1E000]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007D90B14060F1E000")
[x-peer: 80.84.245.120]("http://rbl.botslist.ca/search?name=x%5C-peer:%2080%5C.84%5C.245%5C.120")
[x-revdns: vps02.alkeninternet.nl]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20vps02%5C.alkeninternet%5C.nl")
[x-timestamp: 07DA0A010A21163B8]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA0A010A21163B8")
**[_82.165.130.74_]("http://rbl.botslist.ca/lookup/82.165.130.74")**

[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-archaic: yes]("http://rbl.botslist.ca/search?name=x%5C-archaic:%20yes")
[x-botcaps: 4096]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%204096")
[x-botserial: 07DA051F021235000]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007DA051F021235000")
[x-peer: 82.165.130.74]("http://rbl.botslist.ca/search?name=x%5C-peer:%2082%5C.165%5C.130%5C.74")
[x-revdns: s15407755.onlinehome-server.info]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20s15407755%5C.onlinehome%5C-server%5C.info")
[x-timestamp: 07DA0A010B3220195]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA0A010B3220195")
**[_85.17.201.139_]("http://rbl.botslist.ca/lookup/85.17.201.139")**

[accept: */*]("http://rbl.botslist.ca/search?name=accept:%20%5C%2A/%5C%2A")
[accept-encoding: gzip, deflate]("http://rbl.botslist.ca/search?name=accept%5C-encoding:%20gzip%2C%20deflate")
[accept-language: en-us]("http://rbl.botslist.ca/search?name=accept%5C-language:%20en%5C-us")
[connection: Close]("http://rbl.botslist.ca/search?name=connection:%20Close")
[content-length: 0]("http://rbl.botslist.ca/search?name=content%5C-length:%200")
[user-agent: Morfeus strikes again.]("http://rbl.botslist.ca/search?name=user%5C-agent:%20Morfeus%20strikes%20again%5C.")
[x-botcaps: 12]("http://rbl.botslist.ca/search?name=x%5C-botcaps:%2012")
[x-botserial: 07D90C090731251F3]("http://rbl.botslist.ca/search?name=x%5C-botserial:%2007D90C090731251F3")
[x-cracker: yes]("http://rbl.botslist.ca/search?name=x%5C-cracker:%20yes")
[x-icookies: yes]("http://rbl.botslist.ca/search?name=x%5C-icookies:%20yes")
[x-peer: 85.17.201.139]("http://rbl.botslist.ca/search?name=x%5C-peer:%2085%5C.17%5C.201%5C.139")
[x-revdns: clickbizz3.clickbizz.eu]("http://rbl.botslist.ca/search?name=x%5C-revdns:%20clickbizz3%5C.clickbizz%5C.eu")
[x-timestamp: 07DA0A010F0A29127]("http://rbl.botslist.ca/search?name=x%5C-timestamp:%2007DA0A010F0A29127")

---

