---
title: "namecheap domain and DDNS"
date: 2012-03-15
forum: Server Platforms
---

### Post by spezticle on 2012-03-15
I'm using ubuntu server 11.10 and I use ddclient to automatically update my namecheap.com's domain name.

I had some trouble finding out how to make things work with sub-domains. I figured it out and i thought it would be a nice idea to share for others:

below is a copy of my /etc/ddclient.conf
it is owned by root and permissions are set to 600
if anyone has any thoughts or suggestions, please reply :)

```
############
# ddclient.conf
# namecheap
############
## update time in seconds, i believe
daemon=300
## you can open this file with any text editor to see what is being sent
cache=/tmp/ddclient.cache
pid=/var/run/ddclient.pid
## This line will get your public IP address if you're system is not directly connected
## to the internet, such as behind a firewall/router
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
protocol=namecheap
server=dynamicdns.park-your-domain.com
## Your Domain name
login=example.com
password= #namecheap provides this
ssl=yes
## this was the tricky part for me to figure out
## I was embarrassed with myself when I learned how easy it was
## separate each sub-domain you want to update with the IP address with a comma then space
@, forum, img, ssl, tracker, webmail, www

```

---

