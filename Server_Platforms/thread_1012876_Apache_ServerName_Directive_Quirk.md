---
title: "Apache ServerName Directive Quirk"
date: 2008-12-16
forum: Server Platforms
---

### Post by Ashly on 2008-12-16
Hi all,

I'm having trouble setting up a virtualhost for one of my domains: ash.ms. [www.ash.ms](www.ash.ms) works fine, but for some reason ash.ms is just not working.

The following works fine:

```
<VirtualHost *>
	ServerName www.ash.ms
	DocumentRoot /var/www/ash.ms/html/

```

The following just show me the default page:

```
<VirtualHost *>
	ServerName ash.ms
	DocumentRoot /var/www/ash.ms/html/

```

With the next one, [www.ash.ms](www.ash.ms) shows the right page, but ash.ms still shows the default Apache page.

```
<VirtualHost *>
	ServerName www.ash.ms
	ServerAlias ash.ms
	DocumentRoot /var/www/ash.ms/html/

```


I'm using Apache2 and a completely updated 8.04. I'm just wondering is there something blatant I've missed, or is this a big of some kind. It's driving me nuts.

Any help would be appreciated.

---

### Post by MJN on 2008-12-16
Both [www.ash.ms]("http://www.ash.ms") and [ash.ms]("http://ash.ms") both resolve to the same page/site ('Ashley Kyd') for me.

Perhaps you need to check (clear) your browser cache?

Mathew

---

### Post by Ashly on 2008-12-16
Thanks,

I should have mentioned that this is using internal DNS. if you set your HOSTS file to point these to 203.98.84.225, you can see the server I'm working with.

The following is the configuration I'm using.

[LIST]
[*][http://pastebin.com/m4fe21563](http://pastebin.com/m4fe21563) &#8592; Default config, pretty standard.
[*][http://pastebin.com/m10e2693f](http://pastebin.com/m10e2693f) &#8592; All virtualhosts catted together.
[/LIST]

---

### Post by Ashly on 2008-12-17
Oooookay, I've worked out what the problem is — the server name is ash.ms, so for some reason Apache's overriding my virtualhost and pointing ash.ms to the main/default site instead.

I changed the machine's hostname and just reloaded the config to find that ash.ms was working, but it'd knocked out kyd.com.au. That's really annoying.

---

### Post by MJN on 2008-12-17
The config you've posted doesn't quite match up.

I've added manual mappings for [www.ash.ms]("http://www.ash.ms") and ash.ms to 203.98.84.225 and requesting [www.ash.ms]("http://www.ash.ms") results in a 301 permanent redirect to ash.ms. The delivered document (index.html) is zero bytes in length.

Your config makes no mention of redirects (other than for [www.kyd.com.au]("http://www.kyd.com.au")) so either you've changed it since posting or you're confused about which config is responsible for this site.

Incidentally, your machine name has nothing to do with Apache's operation if you use Servername directives.

Mathew

---

### Post by Ashly on 2008-12-18
Sorry, you're right. I've updated the config since, so that I'm not serving up duplicate content.

It does seems like the system's hostname is affecting the virtualhosts though. It started as "ash.ms" which was the affected domain. I changed the hostname to "kyd.com.au" as my webhost had set the default other one, and after a config reload kyd.com.au started doing the same thing whereas ash.ms was fine.

It's a bit weird, and it's messed up my directory structure somewhat, but I can work with it. :)

Edit: I did post something like this yesterday, but for some reason the system ate it. :-/

---

