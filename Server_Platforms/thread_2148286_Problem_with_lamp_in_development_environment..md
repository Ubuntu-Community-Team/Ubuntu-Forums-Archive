---
title: "Problem with lamp in development environment."
date: 2013-05-24
forum: Server Platforms
---

### Post by heretic381 on 2013-05-24
Hi,
I've installed Ubuntu 12.04 LTS on my laptop: Pentium(R) Dual-Core CPU T4300 @ 2.10GHz × 2 , 4G of RAM.
I'm using it from time to time as a development OS for web sites. At the moment, I'm working on a Drupal 7 site, and I'm having trouble to make it work correctly. The issue is the speed and the heavy CPU load. 

Although I have mpm-prefork activated, I can see only one apache process on launching localhost sites. Every local cms has a heavy load on CPU. Drupal takes both CPU core to 100%. WIth only one apache process. I don't understand what's going on. I've tried to change some apache settings in /etc/apache2/apache2.conf, but it seems that apache ignores it. Same with OP code caches like APC and Memcache. It doesn't make any difference at all.

Could someone provide an information of where to look for the possible solution?

Thanks in advance.

I will of course provide all helpful information.

---

### Post by heretic381 on 2013-05-25
Can someone tell me if having only one apache and mysql process is normal behavior for the desktop ubuntu version on which I manually installed the server, php and db?

---

### Post by stmiller on 2013-05-25
One mysql process - yes.

Apache - no something is not right. Should see many.

With apache, you will typically see on process running as root, then many other child processes running by say, www-data.

Top should look something like this on a LAMP box:

[ATTACH=CONFIG]243030[/ATTACH]

For your setup I'd suggesting using these settings for /etc/apache2/apache2.conf:

```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients           150
    MaxRequestsPerChild   1000
</IfModule>

```

---

### Post by heretic381 on 2013-05-25
Thanks for your reply.  I have alredy seen multiple mysql process too.  Tried some apache2.conf tweaks, but nothing changes.  ???  How can I figure out what's going wrong here?

---

