---
title: "Transparent Squid3 tweaking"
date: 2012-05-01
forum: Server Platforms
---

### Post by Zebisnz on 2012-05-01
Hi all,

I am a beginner to Linux and Ubuntu, and I have setup a transparent proxy using the 12.04 Server 64-bit release of Ubuntu, Squid3 3.1.19. This is for a school environment with ~300+ clients and a 100Mbit/100Mbit fibre connection.

I just followed a simple guide with the bare minimum setup, and it appears to be working well. I easily get 80+ Mbit sustained throughput via the proxy.

My proxy server is: 
HP ML350 G5
2 x Quad Core E5420
4x146GB SAS 15,000RPM disks in RAID 10 (P400 controller)
16GB RAM

I have a 240GB partition /squid for cache (ext3)

Currently I have squid set to:
cache ufs /squid 150000 16 256
cache_mem 8192 MB

Looking at TOP, 12G of 16G RAM is used, squid is using 30% of the memory. CPU hardly goes above 10%, sits at 1-3%

Should I change anything?
Looks like cache_mem may need to be reduced - I will watch this.
/squid is only 5.4G full of 240G (150G allocated in squid.conf)
(Is the 10MB RAM per 1GB disk cache correct here?)
/squid is ext3, should I try reiserfs?
Maybe add more RAM?

It really seems to work well, but want to make sure I am doing it right. Its an old server that's out of warranty so thought Id try a project other than the Windows environment I use everyday.

Cheers

Matt

---

### Post by newbie-user on 2012-05-01
8GB for cache_mem is kinda big, but then again, you've got a seriously powerful machine for a squid box. I've got between 200-300 users going through an Atom-based squid box.

As for using Reiserfs, I haven't seen anything concrete about the supposed performance benefits for squid cache servers. I just hear a lot of "may do this or that". But the last server I had running reiserfs died due to file system problems, prompting me to switch to ext3/4. 

You might want to look at your cache replacement settings to see what might work best for your setup.

Other than that, I package up my squid logs daily so that I can more easily search through them if I need to.

---

### Post by SeijiSensei on 2012-05-01
I wouldn't spend much time on the performance issues unless you observe some problems in that department.

Instead I'd focus on writing ACL's and maybe installing [SquidClamAV]("http://squidclamav.darold.net/").  If the clients are all running Windows, then you may want to block certain file types like '.exe'.  Here's our list of blocked file extensions:
```
\.exe\?$
\.cab\?$
\.exe$
\.cab$
\.bat$
\.msi$
\.ade$
\.adp$
\.bas$
\.chm$
\.cmd$
\.cpl$
\.crt$
\.dll$
\.hlp$
\.hta$
\.inf$
\.ins$
\.isp$
\.jse$
\.lnk$
\.mdb$
\.mde$
\.msc$
\.msp$
\.mst$
\.ocx$
\.pcd$
\.pif$
\.pot$
\.reg$
\.scr$
\.sct$
\.shb$
\.shs$
\.sys$
\.vb$
\.vbe$
\.vbs$
\.wsc$
\.wsf$
\.wsh$

```

We also scan every object with SquidClamAV.  We're using that on a similarly hefty proxy using dual Xeons, and it hardly breaks a sweat, even running alongside MailScanner which is scanning all inbound mail for spam and viruses. 

If this is a school, I'd think you'd want to be blocking things like .xxx domains and the like.  We also blacklist URLs in the "[Malware Block List]("http://malware.hiperlinks.com.br/")" and update it hourly using this script:

```

#!/bin/sh

# download squid malware list

cd /etc/squid/ACL
wget http://malware.hiperlinks.com.br/cgi/submit?action=list_squid -O /tmp/urimalware.txt
[ -s /tmp/urimalware.txt ] && mv -f /tmp/urimalware.txt /etc/squid/ACL/malware_block_list.
txt 

# use new list
/usr/sbin/squid -k reconfigure

```

We block these sites with an ACL like this:

```
acl malware_block_list url_regex -i "/etc/squid/ACL/malware_block_list.txt"
```

The /ACL/ directory is custom to our site; I put a number of different ACL lists in there.

For us, the caching aspect of Squid is secondary to the abilities it provides us for managing users' browsing behavior.

For log management, I wrote a custom app that loads each night's logs into a PostgreSQL database and provides a web interface to examine browsing patterns by a variety of parameters.  You can also use [SARG]("http://sarg.sourceforge.net/") to summarize the logs; it's pretty easy to configure.

---

### Post by sourchier on 2012-05-02
You could change the squid settings from ufs to aufs. The squid doc and howto is here:

[http://www.squid-cache.org/Doc/config/cache_dir/]("http://www.squid-cache.org/Doc/config/cache_dir/")

---

