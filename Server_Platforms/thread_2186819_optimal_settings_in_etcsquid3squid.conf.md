---
title: "optimal settings in /etc/squid3/squid.conf"
date: 2013-11-09
forum: Server Platforms
---

### Post by cccc on 2013-11-09
hi

I have installed Squid3 for about 500 users and I'm looking for optimal settings in /etc/squid3/squid.conf, to get max performance.
It would be great, if someone can post his /etc/squid3/squid.conf.

---

### Post by SeijiSensei on 2013-11-09
I manage a cache for about 250 users.  Pretty much all the settings are the defaults.  We're running it on a [dual-Xeon machine]("http://www.dell.com/us/business/p/poweredge-r410/pd") with 8 GB of RAM, so performance is never an issue.  We even use [SquidClamAV]("http://squidclamav.darold.net/") to scan every downloaded object for viruses with no obvious slow downs.  We also use a lot of ACLs, including the entire "[malware block list]("http://www.malwarepatrol.net")."  All told there are over 20,000 separate ACLs.  Squid still never misses a beat.  The machine also performs a number of other tasks like scanning inbound mail with [MailScanner]("http://www.mailscanner.info/") and hosting my client's DNS and web sites.

The only things I changed from the default (CentOS) configuration were expanding the cache size and permitting more file descriptors:

```

cache_dir ufs /var/spool/squid 10000 16 256
max_filedesc 16384

```

A search for "[optimizing squid]("https://www.google.com/search?q=optimizing+squid")" brings up a lot of articles.

---

