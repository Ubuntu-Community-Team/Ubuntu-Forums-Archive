---
title: "Server Hostname"
date: 2009-10-03
forum: Server Platforms
---

### Post by danielw1020 on 2009-10-03
Hello,

What I would like to do is have a hostname for my server which is running in a virtual machine using bridged networking.

For example, **websvr**.mydomain.co.uk where **websvr**.mydomain.co.uk will be able to be accessed for SSH, SFTP and maybe even using a web server from the internet.

I have a domain I purchased from 123-reg (daniel-wiltshire.co.uk), being a newbie to Ubuntu Server and DNS records, any help would be appreciated. 

Thanks, 

Daniel

---

### Post by undecim on 2009-10-03
unless you have an internet IP address for each server, I don't think its possible to do that.

Though I could be wrong... I know with HTTP, there is the "Host: " option in the header that lets one server run two domains or know what subdomain is being used... I don't know if ssh does that, but even if it did, you would need to set up your router or another host to forward the connection based on the host...

Your other option would be to use different ports. Some routers allow you to route one external port to a completely different internal port. If your router doesn't do that, then you would need to configure each ssh server to use different ports and map each port to each server (starting with something like 222... the default port 22 gets attacked a lot.) Then you could access each one with your hostname and the -p option.

ssh -p 222 daniel-wiltshire.co.uk

or, for file transfer clients that just need a URI (like nautilus sftp) you could use:

sftp://daniel-wiltshire.co.uk:222/

---

### Post by hessiess on 2009-10-03
You could use Apache as a reverce proxy.

---

### Post by Bachstelze on 2009-10-03
IPv6 ftw!

---

### Post by danielw1020 on 2009-10-03
Thanks for your fast replies =P

To [undecim]("http://ubuntuforums.org/member.php?u=623644"), As I am only using a consumer home connection (10mb package from Virgin Media) .. sighs =[, I am not sure if they would serve out multiple IPv4 addresses. I don't really want to find out, their customer service is appalling! I have an Airport Extreme and I have noticed no way of forwardding an external port to an internal port not unless I supply a port after the defined internal IP like 10.0.1.2:8888 for instance. I will hopefully, be soon getting a dedicated box where I could host a media server on (SMB) and use SSH on that as well.

To [hessiess]("http://ubuntuforums.org/member.php?u=289016"), Thanks for the suggestion, I don't have much knowledge with Apache and setting it to use a proxy server sounds kinda complicated. =P

To [[COLOR=#D40000]**Bachstelze**[/COLOR]]("http://ubuntuforums.org/member.php?u=51114"), Wish Virgin Media would start supplying IPv6 addresses now. The Airport Extreme takes care of internal ones which is nice. =P

---

