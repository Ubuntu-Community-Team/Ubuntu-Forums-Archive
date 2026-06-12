---
title: "Configuring Apache2 for Rails on Ubuntu 12, Xen VPS"
date: 2013-11-10
forum: Server Platforms
---

### Post by alexander.s.farley on 2013-11-10
[COLOR=#333333][FONT=Verdana]Hi, [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]I've installed Apache2 on an Ubuntu 12 VPS. My goal is to serve a Rails application but right now I am being redirected to a placeholder page. [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]Some background: I have an existing copy of my site running on shared hosting using Site5 (rsearch.ca). I've just purchased a separate VPS through Site5 and set the domain to dev.rsearch.ca. [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]The VPS root URL (dev.rsearch.ca) is redirecting to dev.rsearch.ca/cgi-sys/cgi-sys/defaultwebpage.cgi which is a default Site5 placeholder. [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]Is there any way for me to figure out where this default page is being served from without the assistance of the hosting provider (Site5)? [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]My expectation was that I would get a "no response" or something similar until I had properly configured Apache2/Rails/etc on the server, so I'm not sure where this default page could be coming from. The VPS does not come with Apache installed so I don't see how it could actually be serving anything. Where am I going wrong here? [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]A related question: at what layer does the request path branch when I make a request to rsearch.ca, vs dev.rsearch.ca? The thing that confuses me is that even with my original shared hosting account (just the rsearch.ca computer) I was able to set up subdomains like dev.rsearch.ca, so how does each computer know whether to handle a request? [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]When I make a request for dev.rsearch.ca/index.html, how come I don't get a response from the rsearch.ca computer (saying that the subdomain dev.* wasn't found) plus a response from dev.rsearch.ca saying that the index page wasn't found because no server is installed? [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]I wouldn't normally think of this as an Apache-specific question but the hosting provider has suggested that the problem lies in my Apache configuration, or lack thereof. Any guidance would be appreciated - is this an Apache/Xen/Ubuntu config/hosting provider problem or what? Where should I start? Thanks.[/FONT][/COLOR]

---

### Post by sandyd on 2013-11-10
> **alexander.s.farley said:**
> [COLOR=#333333][FONT=Verdana]Hi, [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]I've installed Apache2 on an Ubuntu 12 VPS. My goal is to serve a Rails application but right now I am being redirected to a placeholder page. [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]Some background: I have an existing copy of my site running on shared hosting using Site5 (rsearch.ca). I've just purchased a separate VPS through Site5 and set the domain to dev.rsearch.ca. [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]The VPS root URL (dev.rsearch.ca) is redirecting to dev.rsearch.ca/cgi-sys/cgi-sys/defaultwebpage.cgi which is a default Site5 placeholder. [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]Is there any way for me to figure out where this default page is being served from without the assistance of the hosting provider (Site5)? [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]My expectation was that I would get a "no response" or something similar until I had properly configured Apache2/Rails/etc on the server, so I'm not sure where this default page could be coming from. The VPS does not come with Apache installed so I don't see how it could actually be serving anything. Where am I going wrong here? [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]A related question: at what layer does the request path branch when I make a request to rsearch.ca, vs dev.rsearch.ca? The thing that confuses me is that even with my original shared hosting account (just the rsearch.ca computer) I was able to set up subdomains like dev.rsearch.ca, so how does each computer know whether to handle a request? [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]When I make a request for dev.rsearch.ca/index.html, how come I don't get a response from the rsearch.ca computer (saying that the subdomain dev.* wasn't found) plus a response from dev.rsearch.ca saying that the index page wasn't found because no server is installed? [/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]I wouldn't normally think of this as an Apache-specific question but the hosting provider has suggested that the problem lies in my Apache configuration, or lack thereof. Any guidance would be appreciated - is this an Apache/Xen/Ubuntu config/hosting provider problem or what? Where should I start? Thanks.[/FONT][/COLOR]

Checking the DNS shows that dev.rsearch.ca still points towards the shared hosting site IP, ask the provider (or change it in CPanel) to change the A record in the dns of dev.rsearch.ca to the IP of your VPS.
```
root@chloe:/opt/openlitespeed/lsphp5/lib# dig dev.rsearch.ca

; <<>> DiG 9.8.5-P2-geoip-1.3 <<>> dev.rsearch.ca
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58171
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;dev.rsearch.ca.                        IN      A

;; ANSWER SECTION:
dev.rsearch.ca.         3600    IN      A       50.22.11.20

;; Query time: 63 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sun Nov 10 15:52:21 EST 2013
;; MSG SIZE  rcvd: 48

You have new mail in /var/mail/root
root@chloe:/opt/openlitespeed/lsphp5/lib# dig rsearch.ca

; <<>> DiG 9.8.5-P2-geoip-1.3 <<>> rsearch.ca
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43499
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;rsearch.ca.                    IN      A

;; ANSWER SECTION:
rsearch.ca.             3600    IN      A       50.22.11.20

;; Query time: 65 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sun Nov 10 15:52:25 EST 2013
;; MSG SIZE  rcvd: 44

```

---

