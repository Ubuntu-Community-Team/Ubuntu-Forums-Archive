---
title: "Apache being used as proxy?"
date: 2010-10-06
forum: Server Platforms
---

### Post by WorMzy on 2010-10-06
Hi there, I've got some strange looking requests in my access_log which I don't much like the look of. Can someone take a look and let me know if 1) it's possible for other people to use my server as a proxy, and 2) how I can stop them.

```
[COLOR="DarkGreen"]85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 1606
85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 1606[/COLOR]
[COLOR="DarkRed"]85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "GET http://vlad-tepes.bofh.it/proxy.txt HTTP/1.0" 404 1955
85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "GET http://vlad-tepes.bofh.it/proxy.txt HTTP/1.0" 404 1955[/COLOR]
[COLOR="DarkGreen"]85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 1606
85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 1606[/COLOR]
[COLOR="DarkRed"]85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "POST http://vlad-tepes.bofh.it/proxy.txt HTTP/1.0" 404 1955[/COLOR]
[COLOR="DarkGreen"]194.109.21.230 - - [06/Oct/2010:14:32:56 +0100] "CONNECT 194.109.153.5:11111 HTTP/1.0" 200 1606[/COLOR]
[COLOR="DarkRed"]194.109.21.230 - - [06/Oct/2010:14:32:56 +0100] "GET http://194.109.153.3/proxycheck.txt HTTP/1.0" 404 1955[/COLOR]
[COLOR="DarkGreen"]208.100.20.98 - - [06/Oct/2010:14:33:51 +0100] "POST http://204.8.34.130:7000/ HTTP/1.0" 200 1606
208.100.20.98 - - [06/Oct/2010:14:33:51 +0100] "PUT http://204.8.34.130:7000/ HTTP/1.0" 200 1606
208.100.20.98 - - [06/Oct/2010:14:33:51 +0100] "CONNECT 204.8.34.130:7000 HTTP/1.0" 200 1606[/COLOR]

```

In this case I know where the connections have come from, and was informed about the probe before it took place, but I don't like how some of the requests succeeded.

Any help is appreciated.

---

### Post by dtfinch on 2010-10-06
[http://ubuntuforums.org/showthread.php?t=288783](http://ubuntuforums.org/showthread.php?t=288783)

It looks like it ignores the host/port, so it saw all those urls as "/" (except the 404s where a specific file was requested) and returned your front page.

---

### Post by WorMzy on 2010-10-06
Thanks for the response. I'll create a proxy.txt file in my server's root directory and let the probe run again. If it returns a 200 response then it'll confirm that it's ignoring the external host and just returning my local pages.

Will post the result when I know. :)

---

### Post by SeijiSensei on 2010-10-06
> **WorMzy said:**
> Hi there, I've got some strange looking requests in my access_log which I don't much like the look of. Can someone take a look and let me know if 1) it's possible for other people to use my server as a proxy, and 2) how I can stop them.

```
[COLOR="DarkGreen"]85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 1606
85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 1606[/COLOR]
[COLOR="DarkRed"]85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "GET http://vlad-tepes.bofh.it/proxy.txt HTTP/1.0" 404 1955
85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "GET http://vlad-tepes.bofh.it/proxy.txt HTTP/1.0" 404 1955[/COLOR]
[COLOR="DarkGreen"]85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "CONNECT 213.92.8.7:31204 HTTP/1.0" 200 1606
85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 1606[/COLOR]
[COLOR="DarkRed"]85.190.0.3 - - [06/Oct/2010:14:32:55 +0100] "POST http://vlad-tepes.bofh.it/proxy.txt HTTP/1.0" 404 1955[/COLOR]
[COLOR="DarkGreen"]194.109.21.230 - - [06/Oct/2010:14:32:56 +0100] "CONNECT 194.109.153.5:11111 HTTP/1.0" 200 1606[/COLOR]
[COLOR="DarkRed"]194.109.21.230 - - [06/Oct/2010:14:32:56 +0100] "GET http://194.109.153.3/proxycheck.txt HTTP/1.0" 404 1955[/COLOR]
[COLOR="DarkGreen"]208.100.20.98 - - [06/Oct/2010:14:33:51 +0100] "POST http://204.8.34.130:7000/ HTTP/1.0" 200 1606
208.100.20.98 - - [06/Oct/2010:14:33:51 +0100] "PUT http://204.8.34.130:7000/ HTTP/1.0" 200 1606
208.100.20.98 - - [06/Oct/2010:14:33:51 +0100] "CONNECT 204.8.34.130:7000 HTTP/1.0" 200 1606[/COLOR]

```

In this case I know where the connections have come from, and was informed about the probe before it took place, but I don't like how some of the requests succeeded.

Any help is appreciated.

I'm concerned about those CONNECT requests to random high TCP ports like 31204.  They get 200 replies from the server which would only happen if Apache actually replies on those ports.  Did you open them yourself?  Are you running WebDAV?  This machine does have a firewall installed on it, yes?  

According to /etc/services, port 7000 is for fileservers running the Andrew File System; 11111 and 31204 have no services defined.

If I were you I'd get a copy of nmap (from the repos, or the Windows version at [http://www.insecure.org/](http://www.insecure.org/)) and scan your server from a machine outside your network.  What ports does it report being open? You should know why each port it can connect to is open.  If this is a web server, everything other than 80 and perhaps 22 for ssh should be closed.  If you're providing mail services, then ports like 25, 587, 110, and 143 might also be needed.

Take a look in /tmp and see if there's anything there you don't recognize, especially files marked executable.

---

### Post by WorMzy on 2010-10-06
No need to worry about those ports: my router is set up to only forward incoming requests on port 80 to my server, requests on those ports would never reach it. I might set up a rule for port 22 at some point, but I've never needed to use SSH before.

I do have IPTables set up though, and am mostly using it to drop requests from IP addresses which keep spamming me with various /phpmyadmin requests.

The probe picked up the proxy.txt this time, which seems to prove the earlier theory, so I'm happy enough to mark this as solved.

Thanks for your input, guys.

---

### Post by James78 on 2010-10-14
I know you marked this as solved, but I have a little bit of information for you. You can stop them by using the Apache module mod_security. I have it setup (took a long time), and it blocks all these stupid people. And it also catches people trying to exploit, bad bots, all that stuff. It's really nice. Also, if you do open SSH port, or FTP, or anything, you should look into fail2ban, because you will probably start getting lots of people who are trying to break into the server, like I do. Fail2ban detects all the failed logins and bans the IP, so that all the stuff they're trying to do does nothing and times out, serves them right! :)

---

### Post by WorMzy on 2010-10-14
Thanks for suggesting those, I'll look into setting them both up. :)

---

### Post by James78 on 2010-10-15
So you don't have to fumble around for days (like I did), trying to find rules for mod_security2, and trying to figure all this out, I'll link you to 2 major rulesets, and some information, which should be sufficient for anything; just to get you started out. If you come across false positives in mod_security, you'll have to disable the rule or write an exception. It's tough, but worthit.

Rules:
[http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project](http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project) (I suggest using the latest version in SVN, otherwise you might get an error which is fixed in the latest SVN version)
[http://downloads.prometheus-group.com/delayed/rules/](http://downloads.prometheus-group.com/delayed/rules/) *

Setting up:
* See [http://www.atomicorp.com/wiki/index.php/Atomic_ModSecurity_Rules#Installing_the_rules](http://www.atomicorp.com/wiki/index.php/Atomic_ModSecurity_Rules#Installing_the_rules) to set them up properly
(Mod_security2 documentation)
[http://www.modsecurity.org/documentation/modsecurity-apache/2.5.12/modsecurity2-apache-reference.html](http://www.modsecurity.org/documentation/modsecurity-apache/2.5.12/modsecurity2-apache-reference.html)

Stopping small DOS/DDOS attacks:
[http://www.mydigitallife.info/2007/12/13/prevent-and-stop-dos-or-ddos-attacks-on-web-server-ddos-deflate/](http://www.mydigitallife.info/2007/12/13/prevent-and-stop-dos-or-ddos-attacks-on-web-server-ddos-deflate/)
[http://www.linuxsecurity.com/content/view/121960/49/](http://www.linuxsecurity.com/content/view/121960/49/) (Look at the mod_evasive, Implement Sysctl protection against DDOS, sections)

Fail2ban:
(Checks fail2ban log to catch persistent "hackers" and ban them for a much longer time than the default 10 minutes)
[http://whyscream.net/wiki/index.php/Fail2ban_monitoring_Fail2ban](http://whyscream.net/wiki/index.php/Fail2ban_monitoring_Fail2ban)

P.S. You'd be surprised how many people try to break into your server. I found this out after checking my access logs, not just for Apache, but for SSH, and even my mail system, dovecot (imap, pop3, etc). Today, I got 10 attempts to break in, and 10 peoples attacks consistently timed out on them because of what they did. The timing out is awesome, because it wastes their resources. They try to get in, and each try does nothing for about 30 seconds before saying it timed out. :)

And, as a bonus, here is some stuff from my apache error log regarding what your log said about the proxy stuff. As you can see, my system detects and blocks them. :)
```
[Wed Oct 13 21:42:17 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLaKKcCoAXgAABIJqREAAAAM"]
[Wed Oct 13 21:42:17 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "213.92.8.7"] [uri "/"] [unique_id "TLaKKcCoAXgAABIDigQAAAAG"]
[Wed Oct 13 21:42:17 2010] [error] [client 85.190.0.3] ModSecurity: Warning. Operator LT matched 20 at TX:inbound_anomaly_score. [file "/etc/apache2/mod_security.d/base_rules/modsecurity_crs_60_correlation.conf"] [line "31"] [msg "Inbound Anomaly Score (Total Inbound Score: 15, SQLi=, XSS=): Request Missing a User Agent Header"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLaKKcCoAXgAABIJqREAAAAM"]
[Wed Oct 13 21:42:17 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLaKKcCoAXgAABIGmNkAAAAJ"]
[Wed Oct 13 21:42:17 2010] [error] [client 85.190.0.3] ModSecurity: Warning. Operator GE matched 20 at TX:inbound_anomaly_score. [file "/etc/apache2/mod_security.d/base_rules/modsecurity_crs_60_correlation.conf"] [line "35"] [msg "Inbound Anomaly Score Exceeded (Total Inbound Score: 25, SQLi=, XSS=): Request content type is not allowed by policy"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLaKKcCoAXgAABIGmNkAAAAJ"]
[Thu Oct 14 01:05:31 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLa5y8CoAXgAADN@T3oAAAAC"]
[Thu Oct 14 01:05:31 2010] [error] [client 85.190.0.3] ModSecurity: Warning. Operator GE matched 20 at TX:inbound_anomaly_score. [file "/etc/apache2/mod_security.d/base_rules/modsecurity_crs_60_correlation.conf"] [line "35"] [msg "Inbound Anomaly Score Exceeded (Total Inbound Score: 25, SQLi=, XSS=): Request content type is not allowed by policy"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLa5y8CoAXgAADN@T3oAAAAC"]
[Thu Oct 14 01:05:31 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLa5y8CoAXgAADWdi2AAAAAG"]
[Thu Oct 14 01:05:31 2010] [error] [client 85.190.0.3] ModSecurity: Warning. Operator LT matched 20 at TX:inbound_anomaly_score. [file "/etc/apache2/mod_security.d/base_rules/modsecurity_crs_60_correlation.conf"] [line "31"] [msg "Inbound Anomaly Score (Total Inbound Score: 15, SQLi=, XSS=): Request Missing a User Agent Header"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLa5y8CoAXgAADWdi2AAAAAG"]
[Thu Oct 14 01:05:36 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLa5y8CoAXgAADN-Vf0AAAAD"]
[Thu Oct 14 01:05:36 2010] [error] [client 85.190.0.3] ModSecurity: Warning. Operator LT matched 20 at TX:inbound_anomaly_score. [file "/etc/apache2/mod_security.d/base_rules/modsecurity_crs_60_correlation.conf"] [line "31"] [msg "Inbound Anomaly Score (Total Inbound Score: 15, SQLi=, XSS=): Request Missing a User Agent Header"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLa5y8CoAXgAADN-Vf0AAAAD"]
[Thu Oct 14 01:05:36 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "213.92.8.7"] [uri "/"] [unique_id "TLa5y8CoAXgAADN8QvAAAAAA"]
[Thu Oct 14 18:42:38 2010] [error] [client 58.53.128.61] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "proxyjudge1.proxyfire.net"] [uri "/fastenv"] [unique_id "TLexjcCoAXgAAHUnq0gAAAAA"]
[Thu Oct 14 22:51:04 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "213.92.8.7"] [uri "/"] [unique_id "TLfryMCoAXgAACVHupcAAAAD"]
[Thu Oct 14 22:51:04 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLfryMCoAXgAACVGspoAAAAC"]
[Thu Oct 14 22:51:04 2010] [error] [client 85.190.0.3] ModSecurity: Warning. Operator LT matched 20 at TX:inbound_anomaly_score. [file "/etc/apache2/mod_security.d/base_rules/modsecurity_crs_60_correlation.conf"] [line "31"] [msg "Inbound Anomaly Score (Total Inbound Score: 15, SQLi=, XSS=): Request Missing a User Agent Header"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLfryMCoAXgAACVGspoAAAAC"]
[Thu Oct 14 22:51:04 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLfryMCoAXgAACWhCcYAAAAF"]
[Thu Oct 14 22:51:04 2010] [error] [client 85.190.0.3] ModSecurity: Warning. Operator GE matched 20 at TX:inbound_anomaly_score. [file "/etc/apache2/mod_security.d/base_rules/modsecurity_crs_60_correlation.conf"] [line "35"] [msg "Inbound Anomaly Score Exceeded (Total Inbound Score: 25, SQLi=, XSS=): Request content type is not allowed by policy"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLfryMCoAXgAACWhCcYAAAAF"]
[Thu Oct 14 22:51:04 2010] [error] [client 85.190.0.3] ModSecurity: Access denied with code 400 (phase 2). Pattern match "^\\w+:/" at REQUEST_URI_RAW. [file "/etc/apache2/mod_security.d/optional_rules/modsecurity_crs_20_protocol_violations.conf"] [line "74"] [id "960014"] [msg "Proxy access attempt"] [severity "CRITICAL"] [tag "PROTOCOL_VIOLATION/PROXY_ACCESS"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLfryMCoAXgAACVIvYAAAAAE"]
[Thu Oct 14 22:51:04 2010] [error] [client 85.190.0.3] ModSecurity: Warning. Operator LT matched 20 at TX:inbound_anomaly_score. [file "/etc/apache2/mod_security.d/base_rules/modsecurity_crs_60_correlation.conf"] [line "31"] [msg "Inbound Anomaly Score (Total Inbound Score: 15, SQLi=, XSS=): Request Missing a User Agent Header"] [hostname "vlad-tepes.bofh.it"] [uri "/proxy.txt"] [unique_id "TLfryMCoAXgAACVIvYAAAAAE"]

```

---

### Post by SeijiSensei on 2010-10-15
> **James78 said:**
> You'd be surprised how many people try to break into your server.

Most of those "people" are robots.  They just scan huge blocks of IP addresses each day looking for exploitable holes.

---

### Post by MechaMechanism on 2010-10-15
Using a2enmod and a2dismod, you disable or enable the mods.

Just try disabling mod proxy if you don't need it.

---

### Post by James78 on 2010-10-15
> **SeijiSensei said:**
> Most of those "people" are robots.  They just scan huge blocks of IP addresses each day looking for exploitable holes.
Mmhmm, a security threat if you're not protected nonetheless.

---

### Post by SeijiSensei on 2010-10-15
I wasn't implying that there's no threat involved, just pointing out that there's usually no human on the other end of the probe.  My guess is that most automated attacks develop lists of vulnerable hosts that are then examined further by humans after discovery.

Exploits of open SMTP relays are probably more automated.  It doesn't take much effort to determine whether a machine relays mail.  Once it's discovered it's a simple matter to start pushing spam through it.  I've been exploited twice in this manner, the last time being many years ago now.  I use a store-and-forward proxy for inbound SMTP which supports rulesets to permit or deny mail based on SMTP characteristics.  In the two cases I mentioned, I had edited the ruleset and accidentally broke it so that the final deny rule didn't come into play.  It didn't take more than 48 hours before the vulnerability was spotted, and my server was busily forwarding spam all over the planet.

---

### Post by James78 on 2010-10-15
I wasn't trying to imply that you meant there's no threat involved lol. Anywho, when I said people trying to break into the server, I meant whatever bad traffic you get, including bots. :)

---

