---
title: "Dynamic IP and Web hosting"
date: 2006-11-28
forum: Server Platforms
---

### Post by spydrmn on 2006-11-28
Hi,

I'm wanting to make a LAMP server to serve up just my website, my connection to my ISP is a DHCP. I already own the URL and all. I just want to know if there are any special configurations or anything I need to do before I really start into this.

I have read the Server guide and it just doesn't really answer this question.

Spydr

---

### Post by KingBahamut on 2006-11-28
Resort to the use of a Dynamic DNS service would be the best. [http://dyndns.org](http://dyndns.org) is a favorite. They can give you DNS to your hostname even though your sporting a dynamic IP. 

Does this help?

---

### Post by spydrmn on 2006-11-28
I was thinking possibly DynDNS or ZoneEdit.com. Just hoping there could be a way I could do it all myself (read 'free').

It does help. Thanks. :)

---

### Post by MJN on 2006-11-28
I use ZoneEdit and can highly recommend it. For the dynamic update client, check out zoneclient.

Mathew


(Sorry for the brief reply but I've got to dash - happy to answer any more questions if required... but check out the Zoneedit FAQs first..!)

---

### Post by spydrmn on 2006-11-29
> **MJN said:**
> For the dynamic update client, check out zoneclient.
Is that something in the repositories, or something I will be getting from ZoneEdit?

Haven't looked at the FAQ's yet (just woke up), I will be shortly.

---

### Post by MJN on 2006-11-29
It's just a Python script, hence nothing to 'install' as such... just run it.

You can get it at [http://zoneclient.sourceforge.net/](http://zoneclient.sourceforge.net/)

Of course, you'll need Python installed, however this *is* in the repositories.

I call it from the following script dropped into /etc/cron.hourly/

```

#!/bin/sh
# /etc/cron.hourly/zoneclient: cron script for zoneclient
# Checks what the public IP address is (dynamically assigned from Blueyonder) by requesting a web page from zoneedit.com which in turn tells it what source address was used. If this has changed since the last check (performed hourly) then it logs into the zoneedit DNS servers and updates the records accordingly.
# Use cron to execute hourly

/full/path/to/zoneclient.py -d <working directory where zoneclient lives> -r dynamic.zone edit.com/checkip.html <zoneedit username> <zoneedit password> *.newtonnet.co.uk,newtonnet.co.uk,<and any other domains as required>

#Sends any output (i.e. failure/update, note no output if no change) to mathew
MAILTO=mathew

```Mathew

---

### Post by Mithrilhall on 2006-11-29
There is also [www.no-ip.com](www.no-ip.com) which has always worked great for me.

You can even apt-get the client.

```

sudo apt-get install no-ip

```

---

### Post by MJN on 2006-11-29
However they do charge don't they? Not that's there's anything wrong with paying (we expect everything to be free these days!) but it could be of significance to the OP.

Mathew

---

### Post by Mithrilhall on 2006-11-29
[www.no-ip.com](www.no-ip.com) has a free version actually.

---

### Post by MJN on 2006-11-29
For your own domain? (the OP already owns one)

I've been out of the loop for a while so it wouldn't surprise me.

Mathew

---

### Post by spydrmn on 2006-11-30
Sorry for the delayed reply.
> [www.no-ip.com](www.no-ip.com) has a free version actually.Unfortunately it only works on their domains. Since I have my own I'd like to stick with it.

ZoneEdit does seem to offer this, so more than likely I will go with them.

Thanks to all for your help. :)

---

### Post by TheGreatBradley on 2006-11-30
I had the same situation as you, a constantly changing IP. I found the site [www.dnsexit.com](www.dnsexit.com) and if you've got a domain already registered, just point the domain to their site:
ns1.dnsExit.com
ns2.dnsExit.com
And it'll host it for you (its free on their site). Just use a client to update your IP.

---

### Post by coxc24 on 2006-12-01
You could also foward you own domain to your no-ip domain with a framed session (if your host allows them) and the person viewing your site would see no difference.

---

### Post by chrisfay on 2006-12-01
I second the recommendation for zoneedit.com. I have been using them for dynamic dns for 8 domains along with ddclient for the client updater. DDclient has a simple config file where you list your domains, the username and password to access your zoneedit.com account and it periodically checks my WAN IP. If necessary, my zones are updated automatically.

Super easy....

Does anyone know how to configure Bind9 to accept ddclient in the same fashion? I would like to run my own DNS server again but would like ddclient to update it the same way.

---

### Post by sicofante on 2007-01-14
You probably have found a solution by now, but just in case:

I can also recommend [ZoneEdit]("http://zoneedit.com/"). Your first five domains are free and their service is very good.

Check also [FreeDNS]("http://freedns.afraid.org/") and [EveryDNS]("http://www.everydns.net/") (this one allows one dynamic IP only for all your domains, but if you only own one, that won't be a problem).

Also, you might want to check the [WebHostingTalk forums]("http://www.webhostingtalk.com/") for info. [Here's a thread]("http://www.webhostingtalk.com/showthread.php?t=552970") on free DNS hosting.

You should consider cheap hosting companies as an alternative. It will always be more reliable than a dynamic IP host. I would recommend [Hostgator]("http://www.hostgator.com/") and [Dreamhost]("http://www.dreamhost.com/") (I've used both and they're fine.) You should search for coupons for your first year on the latter. You'll be surprised... Again the [WebHostingTalk forum]("http://www.webhostingtalk.com/") is the best resource for information.

---

### Post by livinginx on 2007-01-14
I really like dyndns.org

The cool thing though, my router has a builtin updater for them :-D

Unfortunately, I only host the domain they gave me locally and not the top-level domains that I own.

---

