---
title: "Squid3 Won't start Deny cache and Allow SSL"
date: 2014-03-17
forum: Security
---

### Post by andrew102 on 2014-03-17
Ok I had the Squid3 proxy running on the LAN and at least visible to the outside WAN

It was refusing connections though (verified in log file)

Problem I'm having now is the service won't start at all. Did a lot of reading and can't work it out.

DO I NEED TO ADD ANYTHING?

Here's my config:
```

#    STOP ALL CACHING
cache deny all

acl SSL_ports port 443
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
acl localnet src 10.1.1.1/32

https_access allow SSL_ports
#follow_x_forwarded_for deny all

http_access allow localnet

http_access allow manager localhost
http_access deny manager

http_access deny !Safe_ports

http_access deny CONNECT !SSL_ports
#http_access deny to_localhost

http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

icp_access deny localhost


# Squid normally listens to port 3128
http_port 3128


access_log /var/log/squid3/access.log squid

#cache_effective_group proxy
```

---

### Post by andrew102 on 2014-03-17
Follow up: Commented out a lot of that to get it to start. Still not accepting connections though.
Anyone know if the TCP_DENIED in the log means the config file needs to be change or is it a routing issue (I've set up inbound and outband LAN-to-WAN) I can see my remote client IP so I'm guessing I need to somehow "allow" connections properly.

---

### Post by cariboo on 2014-03-17
this may be a better place for your thread.

---

### Post by SeijiSensei on 2014-03-18
> **andrew102 said:**
> Ok I had the Squid3 proxy running on the LAN and at least visible to the outside WAN

It was refusing connections though (verified in log file)

Let's take a step back here.  What do you mean by "visible to the outside WAN?"  Do you want to able to use the proxy from outside your local network?  That would create a major security problem unless you restrict access to known external IP addresses. What exactly do you want squid to do?

I'm also unclear what you mean when you say the service "won't start at all?"  When you start it with "sudo service squid start" what errors do you see?  Does it not appear if you run "ps ax | grep squid"?

SSL is another story entirely.  Because of the way SSL uses certificates and encryption, there is little or nothing squid can do with an HTTPS request.  The most recent releases of [SSLBump]("http://wiki.squid-cache.org/Features/SslBump") provide some clever solutions to this problem, but they require complex configurations using an SSL certificate on the proxy and installation of compatible certificates on any browser using the proxy for HTTPS.

---

### Post by ant2ne on 2014-03-18
Pretty sure squid has a log file. Or can be grepped out of the log files.

---

### Post by andrew102 on 2014-03-23
> **SeijiSensei said:**
> Let's take a step back here.  What do you mean by "visible to the outside WAN?"  Do you want to able to use the proxy from outside your local network?  That would create a major security problem unless you restrict access to known external IP addresses. What exactly do you want squid to do?

I'm also unclear what you mean when you say the service "won't start at all?"  When you start it with "sudo service squid start" what errors do you see?  Does it not appear if you run "ps ax | grep squid"?

SSL is another story entirely.  Because of the way SSL uses certificates and encryption, there is little or nothing squid can do with an HTTPS request.  The most recent releases of [SSLBump]("http://wiki.squid-cache.org/Features/SslBump") provide some clever solutions to this problem, but they require complex configurations using an SSL certificate on the proxy and installation of compatible certificates on any browser using the proxy for HTTPS.

Basically we have a web-server that we block access to everyone except the work/office IP. (i.e. we don't want it visible to the public) We would have liked to allow people to work from home. The issue is people at home have dynamic IP's, so it's not simple enough to add them to the "allow" list. 

Our first solution was a VPN (for login authentication) unfortunately it wasn't returning pages properly (some content not viewable, etc.)

So my other option was to use a proxy (with an authentication_helper)

I'll have another look at the log tomorrow. I know there were no errors from the terminal after "sudo service squid3 start" just a "sudo service squid3 status" returned 'stopped/not running'.

So you're saying squid won't simply parse SSL connections. The certificates are no problem seeing as we use a self-signed one anyway.

Is there possibly another proxy solution that natively works with https requests?

---

