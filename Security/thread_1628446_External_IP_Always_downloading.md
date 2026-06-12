---
title: "External IP Always downloading"
date: 2010-11-22
forum: Security
---

### Post by Apot on 2010-11-22
For some reason for the past 15 days a computer from an external IP has been downloading files from one website on the server. I hadn't checked my server's activity enough to notice it. It has had my CPU in full use and using most of my bandwidth.

I blocked the IP and hope to hear nothing more of it.

Why is this other computer doing this? Is this some sort of security risk? It would seem it just caused me problems.

---

### Post by magnatron on 2010-11-23
Did you do a whois lookup and a traceroute on the other IP, it's a shame you cut it off before anallising what it was doing with the command tcpdump -i eth0 -v -w tcpcap.log

Example:

Host: ubuntuforums.org
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.12) Gecko/20101027 Firewater/3.6
Accept: image/png,image/*;q=0.8,*/*;q=0.5
Accept-Language: en-gb,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive

Yahoo for some reason sees my connection as hidden, what can I say I love tweaking my routing table! If it's impossible for yahoo, do the hackers stand a chance?

---

### Post by Apot on 2010-11-23
Ye i did analyse it with tcpdump. It was just downloading pages from a site. All HTML files and PHP files that were available on the web server.

It was an IP from the Ottawa area, that is as much info I got about it and that it looked like a windows computer. I didn't try to get more info about it because I didn't want this guy to think it was some game of hacking between us and he does something that damages files on the server.

I am just trying to figure out why he was doing that so I can asses if it a security risk.

---

### Post by magnatron on 2010-11-23
It sounds like he was profiling your server. Google bot does something similar. But if it was consuming CPU resources he was asking your server a lot of questions in a short space of time looking for answers. Not a security risk, but has the potential to become one if what he was profiling for was vulnerabilities.

---

