---
title: "DNS propagation error"
date: 2010-02-01
forum: Server Platforms
---

### Post by innerspaceproductions on 2010-02-01
I have a new dedicated server (Ubuntu 8.04.04 LTS) which came very cheaply but with the most restrictive control panel I have ever seen.
We were provided the root password to control things ourselves but at the expense of losing all technical support.

I now have everything set up and seemingly working but I am unable to get domain names to resolve.

The server is running Bind9, with webmin and virtualmin ontop.

I have setup several virtualservers and alias virtualservers in virtualmin and these are working fine. 
The site with a dedicated IP works fine when I access by IP.

my /etc/resolve.conf file displays 
nameserver 127.0.0.1
nameserver xx.xx.xx.xx
nameserver xx.xx.xx.xx

resolving these 2 IP addresses gets
ns3.xxxxdns.co.uk
ns4.xxxxdns.co.uk

I pointed several domains (setup in virtualmin) to these nameservers almost 2 days ago now.

Doing a dig command for one of these domains using dns on my server returns my ip and my server as the authoritive answer. As I expect.

However doing a dig for the same domain to my nameserver returns 
; <<>> DiG 9.3.2 <<>> @ns3.xxxxdns.co.uk xxxxxxwedding.com A
 ; (1 server found)
 ;; global options:  printcmd
 ;; connection timed out; no servers could be reached

A DNS lookup for the domain shows the name server that I queried above.

So I figure the problem is that my server is not sending its DNS records to the nameservers listed in resolve.conf properly.

Is there a step that I have missed or a way to check that things are configured correctly?

---

### Post by terazen on 2010-02-01
Update the serial number of one of your records just to test and run `sudo rndc reload` or `sudo /etc/init.d/bind9 restart`.

Then check /var/log/syslog for dns transfers.  You should see something like this:

Feb  1 08:56:26 name0 named[10273]: zone xxxx/IN/external: loaded serial 2010020101
Feb  1 08:56:26 name0 named[10273]: zone xxxx/IN/external: sending notifies (serial 2010020101)
Feb  1 08:56:26 name0 named[10273]: client 1.2.3.4#59295: view external: transfer of 'xxxx/IN': AXFR-style IXFR started
Feb  1 08:56:26 name0 named[10273]: client 1.2.3.4#59295: view external: transfer of 'xxxx/IN': AXFR-style IXFR ended
Feb  1 08:56:27 name0 named[10273]: client 2.3.4.5#33850: view external: transfer of 'xxxx/IN': AXFR-style IXFR started
Feb  1 08:56:27 name0 named[10273]: client 2.3.4.5#33850: view external: transfer of 'xxxx/IN': AXFR-style IXFR ended

If everything looks ok on your side, and your server is resolving the new zones, you need to see if ns3 and ns4 are configured as slaves for your new zones and have the correct master ip address.

---

