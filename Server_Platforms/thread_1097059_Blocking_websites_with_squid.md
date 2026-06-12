---
title: "Blocking websites with squid?"
date: 2009-03-15
forum: Server Platforms
---

### Post by linuxisevolution on 2009-03-15
I simply cannot get it to work. I have firefox setup to use my squid server, so I know it's working. Should I have firefox connected to the server's ip or my router's ip? If I set it to the server's then all websites are bocked, but no so with the router... (the router forwards to the server)

here is my squid.conf:
```

acl lan src 192.168.1.1 192.168.2.0/24
http_access allow lan  
acl wan src 0.0.0.0/24
http_access allow wan
acl bad url_regex "/etc/squid/squid-block.acl"
http_access deny bad

```

In squid-block.acl I have:

```

.redtube.com

sex

```

But redtube and any sites containing the word sex is not blocked...:(

---

### Post by MJWitter on 2009-03-15
Try putting the "deny bad" entry above the allow lan acl?
ie:
```

acl bad url_regex "/etc/squid/squid-block.acl"
http_access deny bad
acl lan src 192.168.1.1 192.168.2.0/24
http_access allow lan  
acl wan src 0.0.0.0/24
http_access allow wan

```

---

### Post by linuxisevolution on 2009-03-15
> **MJWitter said:**
> Try putting the "deny bad" entry above the allow lan acl?
ie:
```

acl bad url_regex "/etc/squid/squid-block.acl"
http_access deny bad
acl lan src 192.168.1.1 192.168.2.0/24
http_access allow lan  
acl wan src 0.0.0.0/24
http_access allow wan

```

Thank you sooo much! It works, but sites with certain words are still not blocked.. Why is that?

---

### Post by MJWitter on 2009-03-15
Glad to help!
Adding -i into the expression will also mean that it is not case sensitive(ie, Sex or sex or seX should be blocked) as follows:
```
acl bad url_regex -i "/etc/squid/squid-block.acl"

```

I am not sure why else it is not blocking sites.

---

### Post by linuxisevolution on 2009-03-15
> **MJWitter said:**
> Glad to help!
Adding -i into the expression will also mean that it is not case sensitive(ie, Sex or sex or seX should be blocked) as follows:
```
acl bad url_regex -i "/etc/squid/squid-block.acl"

```

I am not sure why else it is not blocking sites.

That still did not work. It will only block exact urls.. :(

---

### Post by Kluttz on 2009-03-16
I'm needing to do the same thing. (my teenager discovered the internet has an endless supply of porn).

I am interested  in doing this in webmin.  I have tried a few settings, but nothing seems to work.  The websites are still accessible.

I would like to block actual domain names including all sub-domains.

And is re-directing possible.  I was hoping to re-direct the requested porn sites to another url.

thank you

---

### Post by BkkBonanza on 2009-03-16
I'm not familiar with squid but it looks like you are telling it to use regex. If so, then the expressions you use to filter probably need to be regex expressions. So read up on regex and learn how to write valid expressions. For example, to block any site with sex in the name you would need something like,

.*sex.* 

where the .* means any char 0 or more times, thus allowing chars before and after the letters sex. There are a number of wildcards and modifiers but putting just plain chars means to match those chars only and exactly.

Perhaps start here: [http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)

---

### Post by nelskurian on 2009-03-16
```
acl BlockExt url_regex -i \.mp3$ \.asx$ \.wma$ \.wmv$ \.avi$ \ wav$ \.exe$ 
```
 

checkout this for more squid related queries.
[http://linuxlight.blogspot.com/search/label/squid]("http://linuxlight.blogspot.com/search/label/squid")
[http://www.linux-faqs.com/Forum/viewtopic.php?t=28]("http://www.linux-faqs.com/Forum/viewtopic.php?t=28")

---

### Post by nelskurian on 2009-03-16
[COLOR="DarkOrange"]SafeSquid [/COLOR]is the answer

---

### Post by nelskurian on 2009-03-16
[COLOR="DarkOrange"]SafeSquid[/COLOR] has lots of content filtering features, that allows you
to granularly distribute 'Profiled' Internet access. It gives
you 'Total Access Control' and 'Total Content Control' of your
HTTP traffic.

The best part is that it has a browser based GUI interface. This
makes it very easy to configure, even with minimal knowledge of
Linux. It is being used in Companies like American Home Finance,
Valeo, Bell (Canada), Voltas, Goodlass Nerolac, Hexaware,
Pantaloon, etc.

It also has a full-featured free version which is used world-wide
by thousands of users.

Blocking Websites:

1. URL Filter - allows you to define domains & URLs that you
would like to allow or deny to users / groups. You just have to
mention the websites in the 'Host' field like
(site1.com|site2.net|site3.org) or .*(sex|mail).*

2. Keyword filter - analyzes the text content of a website in
real time and blocks it if it contains certain predefined words
and phrases. A very intelligent way of blocking pron sites,
without depending on any database. And it is intelligent enough
to differentiate between 'sex' and 'sensex'. It blocks porn
sites, even when a user tries to access it through an external
anonymous proxy. The free version comes with predefined rules
for blocking porn sites.[URL="http://www.safesquid.com/html/viewtopic.php?t=2007"]
http://www.safesquid.com/html/viewtopic.php?t=2007[/URL]


3. URL Blacklist - is a categorized database of websites (about
70+ cats). You can define the categories that you would like to
block to users / groups, like porn, adult, sports,
entertainment, jobsearch, etc. SafeSquid supports the use of URL
Blacklist, but you need to subscribe the service at
[http://www.urlblacklist.com/](http://www.urlblacklist.com/) for updates. You can also create
you own custom categories.

Apart from the above features, SafeSquid has many other filters
like Cookie Filter, Mime Filter, Header Filter, DNS Blacklist,
Bandwidth management, URL Redirect, Real-time document rewrite,
etc.

It also as built-in connectivity to many Anti Virus like Clam,
F-Prot, Sophos, Avast, Kaspersky, NOD32, etc.

It has a universal ICAP client to connect to ICAP based security
products like Dr. Web, Kaspersky & Symantec.


[http://wiki.squid-cache.org/SquidFaq/SquidAcl]("http://wiki.squid-cache.org/SquidFaq/SquidAcl")

---

### Post by mistypotato on 2009-08-22
I checked out squid and found that it did not contain the latest Spamming domains such as (at this moment 66.96.251.0 - Volumedrive.com)

I'm looking for a way to add dynamic, up to the moment IP blocking based on up to the minute blacklists of IP addresses from which spam has been sent.

These are the same IP addresses that can be found if you go to mxtoolbox.com and enter the IP address in the Blacklist search box.

Anyone know how to do this on Ubuntu 8.10 Server?

---

