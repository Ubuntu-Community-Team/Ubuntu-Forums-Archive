---
title: "Restrict outgoing traffic per IP to max 50KB/sec"
date: 2012-01-22
forum: Server Platforms
---

### Post by ZnoteOT on 2012-01-22
[img]http://dl.dropbox.com/u/12304631/proxything.jpg[/img]

Do anyone have a recommended program that will help me restrict outgoing traffic on my Ubuntu Server to 50KB/sec per IP?

I have found alternatives, but they seem to only work on etc HTTP (port 80) and so on(I think Squid only work with HTTP), I want a program that restricts all forms of outgoing traffic on all ports to max 50KB/sec per IP. 

Please explain how I shall do this, and etc recommend what programs I need. I am pretty noob at linux but this would be extremely useful as I have 70/10Mbps network and want to avoid wasting my upload speed on regular DoS noobs. :P

That way, at least over 25 connections is required to take down my upstream network. I guess I cant restrict my downstream under such attacks but 70Mbit holds alot better than 10Mbps.

---

### Post by ZnoteOT on 2012-01-23
90 views and no response? :(

I cant believe I am the only one here with this problem.

---

### Post by SeijiSensei on 2012-01-23
[http://lartc.org/](http://lartc.org/)

[http://linux-ip.net/articles/Traffic-Control-HOWTO/](http://linux-ip.net/articles/Traffic-Control-HOWTO/)

---

### Post by bouncingwilf on 2012-01-23
Regretfully, I have no first hand experience of this but the query "restricting traffic by ip linux"  yielded this [http://atmail.com/kb/2009/throttling-bandwidth/](http://atmail.com/kb/2009/throttling-bandwidth/) as the first hit. It uses the Linux command tc (traffic control). It may serve as a starting point if you get no other replies.

Bouncingwilf

---

### Post by ZnoteOT on 2012-01-26
thanks. :)

---

