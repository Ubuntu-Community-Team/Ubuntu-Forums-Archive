---
title: "Apache 2.2.16 .htaccess file problem"
date: 2011-01-05
forum: Server Platforms
---

### Post by HypNemes on 2011-01-05
Hello all

I'm just getting started with hosting/building my website 
- [sort of teach myself project] - 
and I'm using the lamp setup.

I've had good success so far, and have managed to put basic php control scripts together  and some basic user interaction pages with mysql working in the background.

Thing is though - as is probably the norm when anyone starts working with a webserver - after monitoring the logs for a few weeks/months over xmas - ive noticed the bots and trawlers hitting the server and looking for stuff like "phpmyadmin, sqlmanager" etc.

So I decided to go with some .htaccess files for now as nothing interesting on my server anyways.

Ive only got the basic apache2 site setup running - the basic 1 vhost 000-default.

Inside the .htaccess file I plcaed the following,

SetEnvIf User-Agent "^ZmEu$" bad_bot
<Directory /var/www>
	Order Deny,Allow
	Allow from all
	Deny from env=bad_bot
</Directory>

SetEnvIf User-Agent "^Morfeus ****ing Scanner$" bad_scan
<Directory /var/www>
	Order Deny,Allow
	Allow from all
	Deny from env=bad_scan
</Directory>

I thought this would be fine - and block only the traffic that had the headers "ZmEu"  and "^Morfeus ****ing Scanner" [APPOLOGIES FOR THE LANGUAGE THERE but thats how it appaears, im sure many have seen it in their access.log before.

The thing is, those SetEnvIf's seem to block all traffic, I cant even get to my site from localhost when I put that in the .htaccess file.
When I delete those entries - all is fine again.
I dont understand why theyre blocking all traffic.

Can anyone shed any light on the problem for me please?

Many thanks in advance.

Hyp

---

### Post by truant on 2011-01-05
In all honesty, what I'd do is just ignore them.

For every bot you block, you'll get more to do later.  If they're malicious scanners, they'll be spoofing/randomising UA headers in no time anyway.

I used to worry about this sort of thing, but it's such a low overhead on Apache to deliver a 404, it's just not worth it.  If your webserver can't handle a bit of bot action, it's going to struggle with a spike in real-world traffic too.  That said, I dropped apache a while ago for nginx anyway.  Nginx rocks - you can throw tens of thousands of reqs/sec at it and it barely blinks.

If you really want to try to block these bots, perhaps try a rewrite solution, as described here: [http://healyourchurchwebsite.com/2008/05/27/how-to-block-spambots-by-user-agent-using-htaccess/](http://healyourchurchwebsite.com/2008/05/27/how-to-block-spambots-by-user-agent-using-htaccess/)

There's more comprehensive stuff here, including setEnv as you've used: [http://www.askapache.com/htaccess/blocking-bad-bots-and-scrapers-with-htaccess.html](http://www.askapache.com/htaccess/blocking-bad-bots-and-scrapers-with-htaccess.html)

---

### Post by wongo888 on 2011-01-05
```

SetEnvIf User-Agent "^ZmEu$" BadBot=1
Order allow,deny
Allow from all
Deny from env=BadBot

```

Stolen from

[http://httpd.apache.org/docs/2.2/howto/access.html#env](http://httpd.apache.org/docs/2.2/howto/access.html#env)

---

### Post by HypNemes on 2011-01-06
hrmm - well ill try adding the =1 to the end of the SetEnvIf and see if that works.

Also take a look atnginx.

Ty
Hyp

---

### Post by James78 on 2011-01-06
No one ever seems to know this, but the way to stop these bots/hackers/exploiters is not to block them via htaccess or any method like that. Sure, you blocked that morfeus thing, but that's just 1. You know how many more there are? It seems like there's no solution, but there indeed is. Use [mod_security2]("http://www.modsecurity.org/download/") (libapache-mod-security). For rules, use [OWASP]("http://sourceforge.net/projects/mod-security/files/modsecurity-crs/0-CURRENT/") (or their [homepage]("http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project")), and [Atomic ModSecurity rules]("http://updates.atomicorp.com/channels/rules/delayed/") (and their [setup/homepage/wiki]("http://www.atomicorp.com/wiki/index.php/Atomic_ModSecurity_Rules") thing).

Trust me, mod-security is ALL you will EVER need. It blocks all these types of things automatically, and also secures your server and applications from things like SQL vulnerabilities, and the list goes on and on, there's too much too list. Of course, as antivirus does, it can find false positives. The majority of those are simply watching the server logs and fixing it per-application (per virtualhost). You won't regret it. :)

---

### Post by HypNemes on 2011-01-06
Think i will take a look at Mod-Security/modsecurity just to see if its something i could learn to use, i was looking at snort and similar anyways.

Besides - adding the following to a .htaccess file blocks my server root dir from everything trying to access it - exactly the opposite of what i wanted.


SetEnvIf User-Agent "^ZmEu&" bad_bot=1
<Directory /var/www>
	Order Allow,Deny
	Allow from all
	Deny from env=bad_bot
</Directory>

SetEnvIf User-Agent "^Morfeus ****ing Scanner&" bad_scan=1
<Directory /var/www>
	Order Allow,Deny
	Allow from all
	Deny from env=bad_scan=1
</Directory>

For some reason - adding that to a .htaccess file blocks all traffic to /var/www - instead of jsut blocking the relevant hits from "ZmEu" etc.

Thats not whats supposed to happen lol.

Hyp

---

