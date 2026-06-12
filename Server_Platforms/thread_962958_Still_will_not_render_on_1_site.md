---
title: "Still will not render on 1 site"
date: 2008-10-29
forum: Server Platforms
---

### Post by Vegan on 2008-10-29
All my apache conf files are identical except for path and domain. All folder are 777 so that is not a problem.

4 sites work fine, only 1 will not cooperate. Thoughts?

---

### Post by Vegan on 2008-10-29
This is bizarre, go outside and try it and it works, through the LAN no joy.

---

### Post by alienprdkt on 2008-10-29
that is odd, you reboot your machines? (maybe its stuck in cache)

---

### Post by jpeddicord on 2008-10-29
Make sure you reloaded your Apache configuration.

```
sudo /etc/init.d/apache2 reload
```

If it doesn't work after that, post your virtualhosts here and we'll try to figure this out. :)

---

### Post by Vegan on 2008-10-29
I think its a IE 8 beta 2 defect, what did expect from Redmond????

I went to the library and the sites all came up properly. Go figger.

So I have Ubuntu 8.10 graunched into use, what a headache managing a server with limited manuals and resources.

Good thing I have an IQ > lettuce.

I have rebooted everything. So time to work on the IE problems.

---

### Post by dmizer on 2008-10-30
Add the local ip (192.168.x.x) and domain to /etc/hosts like so:
```
127.0.0.1       localhost
127.0.1.1
[COLOR="Red"]192.168.0.10    yourhost1.yourdomain.com yourhost2.yourdomain.com yourhost3.yourdomain.com yourhost4.yourdomain.com[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Vegan on 2008-10-30
I was planning on using BIND for some functionality.

Here is my hosts file:

127.0.0.1		localhost
127.0.1.1		contract-developer.dyndns.biz ubuntu
64.59.160.13		nsc1.cv.gv.shawcable.net
64.59.160.15		nsc2.cv.gv.shawcable.net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by dmizer on 2008-10-30
Correctly configuring bind will probably solve all your problems: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

Basically, your router is not intelligent enough to loop your domain back to a local ip, so unless you have a domain server on your local network your clients have no way of finding your servers. The way I've been getting around this (I only have 2 domains) is by configuring the hosts file on all the clients so it points to the server's IP instead of trying to resolve by DNS.

On Ubuntu clients, the hosts file is in /etc/hosts, on Windows clients, the hosts file is in %SystemRoot%\system32\drivers\etc\hosts

---

### Post by Vegan on 2008-10-30
Is there a simple configuration option or bind9?

[http://contract-developer.dyndns.biz](http://contract-developer.dyndns.biz)
[http://computer-chess.dyndns.biz](http://computer-chess.dyndns.biz)
[http://econ.dyndns.biz](http://econ.dyndns.biz)
[http://vegan.dyndns.biz](http://vegan.dyndns.biz)
[http://web-developer.dyndns.biz](http://web-developer.dyndns.biz)

5 in total for now, more to come

Would like to have mail stuffed into it too and anything else relevant.

I installed postfix and dovecot so far.

---

### Post by dmizer on 2008-10-30
Bind is extremely powerful and robust. For that reason, it is not simple, sorry.

Here's a postfix howto which includes specific directions for incorporating gmail (useful for dynamic domains so your email doesn't get blacklisted): [http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps](http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps)

---

### Post by Vegan on 2008-10-30
I was wanting to use mail based on my domains. I wanted to abandon, gmail etc.

In any event, I need to clean up my hosts.

The Linux box has a staic IP of 192.168.7.250 so the port forwarding knows where to go.

---

### Post by dmizer on 2008-10-30
You have to use gmail with a dynamic host, otherwise all your sent mail will get spam blocked. All you would be using your gmail account for would be as an invisible SMTP relay.

---

### Post by Vegan on 2008-10-30
Someone sent me a DNS root file, so where does it go?

;       This file holds the information on root name servers needed to
;       initialize cache of Internet domain name servers
;       (e.g. reference this file in the "cache  .  <file>"
;       configuration file of BIND domain name servers).
;
;       This file is made available by InterNIC 
;       under anonymous FTP as
;           file                /domain/named.root
;           on server           FTP.INTERNIC.NET
;       -OR-                    RS.INTERNIC.NET
;
;       last update:    Feb 04, 2008
;       related version of root zone:   2008020400
;
; formerly NS.INTERNIC.NET
;
.                        3600000  IN  NS    A.ROOT-SERVERS.NET.
A.ROOT-SERVERS.NET.      3600000      A     198.41.0.4
A.ROOT-SERVERS.NET.      3600000      AAAA  2001:503:BA3E::2:30
;
; formerly NS1.ISI.EDU
;
.                        3600000      NS    B.ROOT-SERVERS.NET.
B.ROOT-SERVERS.NET.      3600000      A     192.228.79.201
;
; formerly C.PSI.NET
;
.                        3600000      NS    C.ROOT-SERVERS.NET.
C.ROOT-SERVERS.NET.      3600000      A     192.33.4.12
;
; formerly TERP.UMD.EDU
;
.                        3600000      NS    D.ROOT-SERVERS.NET.
D.ROOT-SERVERS.NET.      3600000      A     128.8.10.90
;
; formerly NS.NASA.GOV
;
.                        3600000      NS    E.ROOT-SERVERS.NET.
E.ROOT-SERVERS.NET.      3600000      A     192.203.230.10
;
; formerly NS.ISC.ORG
;
.                        3600000      NS    F.ROOT-SERVERS.NET.
F.ROOT-SERVERS.NET.      3600000      A     192.5.5.241
F.ROOT-SERVERS.NET.      3600000      AAAA  2001:500:2f::f
;
; formerly NS.NIC.DDN.MIL
;
.                        3600000      NS    G.ROOT-SERVERS.NET.
G.ROOT-SERVERS.NET.      3600000      A     192.112.36.4
;
; formerly AOS.ARL.ARMY.MIL
;
.                        3600000      NS    H.ROOT-SERVERS.NET.
H.ROOT-SERVERS.NET.      3600000      A     128.63.2.53
H.ROOT-SERVERS.NET.      3600000      AAAA  2001:500:1::803f:235
;
; formerly NIC.NORDU.NET
;
.                        3600000      NS    I.ROOT-SERVERS.NET.
I.ROOT-SERVERS.NET.      3600000      A     192.36.148.17
;
; operated by VeriSign, Inc.
;
.                        3600000      NS    J.ROOT-SERVERS.NET.
J.ROOT-SERVERS.NET.      3600000      A     192.58.128.30
J.ROOT-SERVERS.NET.      3600000      AAAA  2001:503:C27::2:30
;
; operated by RIPE NCC
;
.                        3600000      NS    K.ROOT-SERVERS.NET.
K.ROOT-SERVERS.NET.      3600000      A     193.0.14.129 
K.ROOT-SERVERS.NET.      3600000      AAAA  2001:7fd::1
;
; operated by ICANN
;
.                        3600000      NS    L.ROOT-SERVERS.NET.
L.ROOT-SERVERS.NET.      3600000      A     199.7.83.42
;
; operated by WIDE
;
.                        3600000      NS    M.ROOT-SERVERS.NET.
M.ROOT-SERVERS.NET.      3600000      A     202.12.27.33
M.ROOT-SERVERS.NET.      3600000      AAAA  2001:dc3::35
; End of File

---

