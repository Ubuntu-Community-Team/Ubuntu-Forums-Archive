---
title: "Need help with multiple Ubuntu server setup."
date: 2011-05-23
forum: Server Platforms
---

### Post by kalyptos on 2011-05-23
Hello all.

Iknow this is a longshot and maybe not possible, but then again if its not i can stop trying.
ANY help on this matter would be appreciated :) look at my image for what im aiming for.

noted that my main problem is in the main server and rerouting.

[IMG]http://www.revanchist.com/serverenviroment.jpg[/IMG]

---

### Post by spynappels on 2011-05-23
The easiest bit first.
To get SSH access to all servers on the LAN, use the main server as an OpenVPN server and route traffic to and from LAN through VPN when you are remote.

Does your modem take an IP from the LAN or does it pass the Public IP to the server?

---

### Post by volkswagner on 2011-05-23
For one external ip with more than one web server, you need [reverse proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") or check out this solution using [ProxyPass]("http://ubuntuforums.org/showthread.php?t=1739832&highlight=web+servers")

Check out this how to, adding Nginx as your [reverse-proxy]("http://www.ubuntugeek.com/using-nginx-as-a-reverse-proxy-to-get-the-most-out-ofyour-vps.html")

Search around for the best solution for your specific situation.

---

### Post by spynappels on 2011-05-23
I was going to suggest that you use your main server as a router with 2 NICs and forward all port 80 traffic to the first webserver. Set this webserver up with however many virtual hosts and use the reverse proxy module to redirect all other requests to the other webservers. 

Not sure how the mail servers would work though........

---

### Post by SeijiSensei on 2011-05-23
I'd run Apache in reverse proxy mode on ns1 to forward web traffic to the correct machine based on the virtual domain being served.  

For mail, you can either forward port 25 directly back to the mail server using iptables or an application-level TCP proxy like [this one]("http://freshmeat.net/projects/tcpproxy/"), or you can run something like sendmail or postfix to accept inbound mail and forward it along to the mail server.  As long as the nameservers have an MX record for the domain that points to the mail server, this should work fine.

I actually run a hoary old store-and-forward SMTP daemon called [smtpd]("http://ftp2.ie.netbsd.org/mirrors/download.sourceforge.net/pub/sourceforge/s/project/sc/scamail/smtpd/smtpd%202.0/") on my Internet-facing mail server.  It does nothing but accept mail from machines granted access by an anti-spam ruleset, then invokes sendmail to forward accepted messages on to the actual mail server.

---

