---
title: "Web content filter and logging?"
date: 2011-01-03
forum: Server Platforms
---

### Post by kynov on 2011-01-03
Hey all,

We offer free wifi here and our web filter appliance just broke.  I got the idea that I could replace the device temporarily/permanently with one of our 1U rack servers just lying around with ubuntu 10.04 on it.  A quick search of the internet basically only came up with dansguardian and squid.  I figured squid would be the defacto transparent proxy software, but is Dansguardian the only content filtering available?  

Thanks!

---

### Post by lykwydchykyn on 2011-01-03
Dansguardian is the only one I know of, and I've looked around a good bit.  But quite frankly, it's top-notch.  The only thing lacking is a decent GUI/web interface.

You might want to look at something like ClearOS or Zentyal, which come out-of-the-box with dansguardian set up and a spiffy web interface for it.  Zentyal (formerly ebox) is based on Ubuntu server anyway.

---

### Post by woodman231 on 2011-01-03
I agree.  Squid + Dansgaurdian is a pretty good combo.

Thanks,
Sean W.

---

### Post by liverpoolatnight on 2011-01-10
Well i use squid 3 and works Fab! = sudo apt-get install squid3

The way i done it is maded a blockedsite.txt
[COLOR="Red"]
[B]porn
xxx
sex
shag
****
fanny
*****[/B][/COLOR]

and any other keywords in that list you wonna block.

put this into squid.conf at /etc/squid3/squid.conf

acl blockedsites url_regex -i "/etc/squid3/blockedsite.txt"
http_access deny blockedsites

And if you wonna block **malware sites**
[http://malware.hiperlinks.com.br/cgi/submit?action=list_sguard](http://malware.hiperlinks.com.br/cgi/submit?action=list_sguard)
acl malware_block_list url_regex -i "/etc/squid3/malware_block_list.txt"
http_access deny malware_block_list
deny_info [http://malware.hiperlinks.com.br/denied.shtml](http://malware.hiperlinks.com.br/denied.shtml) malware_block_list

To have an up-to-date block list, create a cron job to run every 4 hours, pointing to a script like this:
#!/bin/sh
wget -O - [http://malware.hiperlinks.com.br/cgi/submit?action=list_squid](http://malware.hiperlinks.com.br/cgi/submit?action=list_squid) > /etc/squid/malware_block_list.txt
squid -k reconfigure

then reset squid proxy server. Then tested it out yourself to see if it meets your needs :) if you have blocked a malware website it should redirect to [http://malware.hiperlinks.com.br/denied.shtml](http://malware.hiperlinks.com.br/denied.shtml) however you can change the domain to whatever you wont. But if you change the squid.conf or blockedsite.txt or malware_blocked_sites.txt you always gonna restart the squid proxy

Hope that helped :)

EDIT:
Heres my backup of squid.conf & text files for squid 3.
[www.francisprojects.co.uk/squid](www.francisprojects.co.uk/squid)

---

