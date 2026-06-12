---
title: "squid3 keeping log of various connections"
date: 2013-08-07
forum: Server Platforms
---

### Post by sophie_horner on 2013-08-07
Hello,

I've been trying to configure squid3, concentrating on how to keep as many access logs as possible - for now i can only log http on the 3128 port...
**I would like to know if it's possible to keep logs of https requests and other types of service - at least basic information - on a transparent proxy configuration.**

I've installed Ubuntu 13 with squid3 - i imagine i will need to --enable-ssl to make this work anyway... i have 2 network cards :
eth0 for WAN internet and eth1 for LAN.

i've set up iptables to redirect http to 3128 port for squid listening - so i was thinking of doing the same for each type of service ?

the basic use is to keep trace of connections for authorities to identify any criminal misuse of internet by inhabitants on the premisses who use our internet connection for free.

Thank you if anyone can help me :)

---

### Post by newbie-user on 2013-08-07
You can't really capture SSL traffic on a transparent squid proxy without doing what is essentially a man-in-the-middle attack. Check here for more information: [http://wiki.squid-cache.org/Features/SslBump](http://wiki.squid-cache.org/Features/SslBump)

---

### Post by sophie_horner on 2013-08-08
Thank you. Very clear. Https are usually trusted sites anyway so I guess it's useless to keep trace... I still wonder if I should keep trace of other services like ftp ? Otherwise I'll stick to just http ports. 
thanks in any case.

---

### Post by SeijiSensei on 2013-08-08
At one of my client's sites, we track HTTPS usage using iptables.

```

/sbin/iptables -A INPUT -p tcp --dport 443 -j LOG --log-prefix SSL_request

```

will log every outbound request for an SSL connection to /var/log/syslog.  The log-prefix directive attaches a label to these entries which makes it easier to parse the log.

I have been experimenting with transparent SSL proxying using Squid 3.3.  You would need to build this from [source]("http://www.squid-cache.org/Versions/") with the "--enable-ssl" and "--enable-ssl-crtd" switches enabled.  This method requires creating a server certificate and installing it in every browser, though.  The details are provided in the SSLBump document cited above.

---

### Post by sophie_horner on 2013-08-10
Thanks also. Does the iptables entry only keep trace of which site + which local IP  ? Because that's all I would want to keep... If so that's cool :) I'll try it out with my own PC for now anyway....

---

