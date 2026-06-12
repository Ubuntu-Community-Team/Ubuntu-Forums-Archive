---
title: "Ubuntu, Plesk DNS failing to resolve on ns1"
date: 2013-03-22
forum: Server Platforms
---

### Post by Gorlist on 2013-03-22
Hi, just posting here as no one over an the plesk forums have given any suggestions.

I run a webs server, Ubuntu 12.04 LTS is installed and fully up to date, with Plesk 11.09. About 10 domains hosted.

Approximately three/four weeks ago Plesk updated, my postfix ceased working and as I was in a rush at the time rolled back to Qmail - ive had to do it  on a number of occasions temporarily.

Turns out Postfix was fine, it appears the plesk update has effected my DNS server which ive only just discovered. (postfix was failing on the milter service from the primary IP).

I have two IP address, one dedicated and one shared. None of my settings have visibly been changed for the name server/domain DNS setting are still the same, prior failure.

So, basically ns1 fails to resolve consistently, effects different hosted domains on different occasions (so the webpage seems to point back to the registrar). ns2 however is working fine. You tend to find if you visit a domain alias then it kick starts the main hosted domain ns1 and it starts to resolve.

DNSTools are complaining about no glue, however that's recent since failure.

I'm lost on how to approach the problem, there's no apparent errors in the log, especially considering so many weeks have passed. Bind is running, ive tried turning off the firewall for a short period, so I can only assume its an internal ip address config problem?

Any suggestions on how to resolve this?

[B][I][COLOR="#A9A9A9"]Another example, I normally connect to my Teamspeak via a hosted domain URL, however I now have use the primary ip. If a Ping, or nslookup only get a reply from ns2.
[/COLOR][/I][/B]
Many thanks,

---

