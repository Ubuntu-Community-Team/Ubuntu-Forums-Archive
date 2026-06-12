---
title: "Lost DNS"
date: 2010-05-25
forum: Server Platforms
---

### Post by sipickles on 2010-05-25
Hi,

I have had a little Ubuntu server running for a while. Its mainly a Subversion and Redmine server.

Suddenly, the server has lost DNS. I noticed because the SVN post-commit email notifications stopped working.

I get errors like this:

```
Completed: At revision: 62  
Error: post-commit hook failed (exit code 22) with output:  
Error: Unable to create Net::SMTP_auth object: Invalid argument at /usr/share/perl5/SVN/Notify.pm line 2375.
```  

I tracked it down to DNS, getting errors like this:

```
simon@urth-webserver:~$ ping google.com
ping: unknown host google.com
```

My /etc/resolv.conf file is empty. Is that normal? I tried entering the address of my router, and also tried adding OpenDNS addresses, restarting networking, but no effect.

How can I restore DNS lookup? Thanks

Simon

---

### Post by HermanAB on 2010-05-25
Howdy,

dhclient will rewrite the resolv.conf file, set the IP address, netmask and default route:
$ sudo dhclient eth0

Otherwise, don't use dhclient and simply hard code resolv.conf with an editor and set the route manually.

---

### Post by clrg on 2010-05-25
Your /etc/resolv.conf should look something like

> 
domain mydomain.tld
search mydomain.tld anotherdomain somemoredomains
nameserver 1.2.3.4
nameserver 2.3.4.5


Using DHCP on a *Server *is probably not the best solution, depending on its configuration it could also change your IP, which usually is undesirable on a Server platform.

---

