---
title: "SARG: Squid Proxy Server report generation"
date: 2018-07-03
forum: Server Platforms
---

### Post by ariz1993 on 2018-07-03
Hello Everyone,

Good day!

Hoping someone could be able to assists.

I'm using Ubuntu 16.04 LTS with Webmin/Squid Proxy Server/Sarg.

However, just today, I'm about to generate report from Squid using SARG, I clicked **Generate Report Now,** and shows me the below error.

sarg -f /etc/sarg/sarg.conf -l /var/log/squid/access.log.1 /var/log/squid/access.log /var/log/squid/access.log.2.gz -d 02/07/2018-02/07/2018
SARG: Decompressing log file "/var/log/squid/access.log.2.gz" with zcat
SARG: Period covered by log files: 02/07/2018-02/07/2018
SARG: (grepday) Fontname "/usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf" not found [COLOR=#EEEEEC]SARG: Unknown option resolve_ip[/COLOR] 
SARG: Unknown option resolve_ip


I already tried to restart both squid server and webmin service as first aid solution but failed to suffice.

Hoping someone could help me out, this is my first post.

thanks a lot for your time!

---

### Post by SeijiSensei on 2018-07-03
Is apache configured to log connections by IP address or hostname?  If the latter, you shouldn't need to resolve the IPs in SARG.  If you log only IPs, consider changing the apache configuration.  Unless you have a very busy server, it shouldn't affect performance much to resolve the names when logging the connections.

It's been many years since I ran SARG, so I'm trying to come up with an end-around solution.

---

### Post by cariboo on 2018-07-04
Moved to Server Platforms

---

### Post by ariz1993 on 2018-07-07
Hi Seiji,

Thanks for your response, I didn't touched anything from apache webserver in webmin, Currently it is still under unused modules,

Webmin/Squid/Sarg are all freshly installed.

I'll try first to install apache, Maybe that's what I'm missing.

I'll let you know the result.

thanks!

---

### Post by SeijiSensei on 2018-07-07
I was in another world when I wrote that! Apache obviously has nothing to do with this issue!

I'm guessing you want to turn off name resolution for the clients' IP addresses when SARG reads Squid's access.log. Even with dozens of clients that doesn't impose much of a performance hit because DNS queries are cached. Another option if the assigned addresses are pretty fixed is to use the /etc/hosts file and list the clients' names and addresses there. Linux and SARG will look there first to resolve names before querying a DNS server.

resolv_ip is a valid option for SARG's configuration file. Take a look at what you have for that option in /etc/sarg/sarg.conf.

From [https://sourceforge.net/p/sarg/wiki/USER%20and%20IP%20options/](https://sourceforge.net/p/sarg/wiki/USER%20and%20IP%20options/)

resolve_ip ( dns | exec | no)

Possible values: yes, dns, no, exec.

If you have a DNS server in your network you can set this option to dns (yes is also possible, left for compatibility). Then you will see domain name of your computers. Otherwise, you will see only IP adresses.
There is no special options for pointing to DNS server in sarg.conf. It should be set up in your operating system.

no does nothing.

exec choose this argument if you want the external program to resolve an IP address.

---

