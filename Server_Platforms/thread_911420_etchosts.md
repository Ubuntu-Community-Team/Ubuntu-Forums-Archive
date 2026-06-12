---
title: "/etc/hosts"
date: 2008-09-05
forum: Server Platforms
---

### Post by Vegan on 2008-09-05
Is my /etc/hosts file correct for an intranet?


127.0.0.1               localhost
127.0.1.1               ubuntu.contract-developer.dyndns.biz ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Krupski on 2008-09-05
> **Vegan said:**
> Is my /etc/hosts file correct for an intranet?


127.0.0.1               localhost
127.0.1.1               ubuntu.contract-developer.dyndns.biz ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Don't quite know what you mean by "for an intranet"... but the purpose of a HOSTS file is to resolve IP addresses to names that don't get resolved via ordinary DNS.

Here's a copy of the hosts file on my network file server box:

```

root@storage:/etc# cat hosts
################################################################
# hosts file for tcp/ip
#
# for example:
#
#   ip address          host name       # comment
#   ----------          ---------       ---------
# 102.54.94.97          rhino.acme.com  # source server
#  38.25.63.10          x.acme.com      # x client host
################################################################

127.0.0.1       localhost       # loopback

192.168.0.1     router          # lan: 00:1e:2a:3c:xx:xx  static
                                # wan: 00:1e:2a:3c:xx:xx  dhcp

192.168.0.10    michael         # 00:16:76:b6:xx:xx     dhcp
192.168.0.11    storage         # 00:1c:c0:21:xx:xx     dhcp
192.168.0.12    laptop          # 00:16:cf:29:xx:xx     dhcp
192.168.0.13    ps3             # 00:1d:0d:ae:xx:xx     dhcp
192.168.0.14    jenna           # 00:16:76:b5:xx:xx     dhcp
192.168.0.15    brian           # 00:14:bf:79:xx:xx     dhcp
192.168.0.16    stargate        # 00:1c:c0:2f:xx:xx     dhcp
192.168.0.190   printer         # 00:14:38:df:xx:xx     static
192.168.0.191   wireless        # 00:14:6c:5f:xx:xx     static


# the following lines are desirable for ipv6 capable hosts
::1             ip6-localhost   ip6-loopback
fe00::0         ip6-localnet
ff00::0         ip6-mcastprefix
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters
ff02::3         ip6-allhosts

```

Note that all it does is provide IP addresses for my LOCAL Intranet computers, printer and wireless access point.

Even though some are marked "DHCP", they are really assigned these fixed addresses by the router. The computers USE DHCP, but the router always forces them to take the same IP.

Name resolution (in Linux and in Windows) doesn't always work for local machines. For example, if I ping my son's computer (Netbios name "jenna") it may or may not show up. But with a hosts file, it always shows up.

Hope this info and example help.

-- Roger

---

### Post by bab1 on 2008-09-06
> Name resolution (in Linux and in Windows) doesn't always work for local machines. For example, if I ping my son's computer (Netbios name "jenna") it may or may not show up.

Be careful here.  NetBIOS names are **not** the same as DNS hostnames.  Hostnames (and DNS) started as a IP concept while NetBIOS (computer name) was a IBM LanManager (later Windows) concept.  NetBIOS names use lmhosts files or a WINS server for resolution while hostnames use hosts files or a DNS server for hostname resolution.

**Edit:**> but the purpose of a HOSTS file is to resolve IP addresses to names that don't get resolved via ordinary DNS
Actually the first use of DNS was with host files only.  It didn't scale well and DNS was born (at USC). See [[COLOR="Red"]Jon Postel[/COLOR]]("http://en.wikipedia.org/wiki/Jon_Postel")

---

### Post by windependence on 2008-09-06
NetBIOS is usually NOT a good idea. besides the scaling already mentioned, it's not very secure either. Personally, I would turn it off.

-Tim

---

### Post by Krupski on 2008-09-06
> **bab1 said:**
> Be careful here.  NetBIOS names are **not** the same as DNS hostnames.  Hostnames (and DNS) started as a IP concept while NetBIOS (computer name) was a IBM LanManager (later Windows) concept.  NetBIOS names use lmhosts files or a WINS server for resolution while hostnames use hosts files or a DNS server for hostname resolution.

**Edit:**
Actually the first use of DNS was with host files only.  It didn't scale well and DNS was born (at USC). See [[COLOR="Red"]Jon Postel[/COLOR]]("http://en.wikipedia.org/wiki/Jon_Postel")

I know it's not the same thing... but why complicate a simple explanation with details?

The point is... if I want to connect to my son's machine, it's easier to connect to "jenna" than it is to remember "192.168.0.14".

Even though it's not DNS, it acts "like" DNS and comparing it to DNS probably makes it easier to understand.

Heck... when NASA has a launch abort, they always say "caused by a dust plug left in a fuel line". The public says "ah OK I get it" and that's the end of it.

Imagine if, instead, they reported "Engine number 3 experienced unstable combustion during the start transient and accelerometer 2 went offscale low, triggering a set launch sequencer abort".

99.9% of the people would still be scratching their heads...

Get my point?

---

### Post by Vegan on 2008-09-06
I installed BIND, but have not set it up yet. Could I us it to assign sub net names to various machine son the LAN.

---

### Post by bab1 on 2008-09-06
@Krupski
> I know it's not the same thing... but why complicate a simple explanation with details?...

...Even though it's not DNS, it acts "like" DNS and comparing it to DNS probably makes it easier to understand.

Not to be argumentative, but the blurring of the two naming conventions is what causes a lot of users of this forum endless grief.  It doesn't help at all to be vague. NetBIOS is a dead end.  DNS is the current standard.  My point is that we **should** be correct and not just casually mixing the terms.  I **do** realize that we are only talking about IP to name resolution.  I believe in this situation it is helpful to be correct, not just almost right.

**~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~**

@Vegan
> I installed BIND, but have not set it up yet. Could I us it to assign sub net names to various machine son the LAN.

BIND is capable of assigning names to hosts in sub-domains.  You would pick the name of the sub-domain.  Let's say your domain was:```
[COLOR="Green"]food.org[/COLOR]
```

You could then create a sub-domain called fruit.  The FQDN would look like this: > [COLOR="DarkGreen"]**fruit**[/COLOR].[COLOR="Green"]food.org[/COLOR]

Now let's add a host to the sub-domain.  We will call it peach.  The FQDN would be:> **[COLOR="DarkOrange"]peach[/COLOR]**.[COLOR="DarkGreen"]**fruit**[/COLOR].[COLOR="Green"]food.org[/COLOR]

Let's go back to the the domain [COLOR="Green"]food.org[/COLOR].  You could have hosts here also.  An example of this is: > [COLOR="Purple"]**skillet**[/COLOR].[COLOR="Green"]food.org[/COLOR]

It does look confusing but to DNS a name is a name.  The user (organization) should be able to tell what is a sub-domain and what is a hostname.  Just remember to keep it simple and have a copy of the domain hierarchy handy until you get used to your naming conventions.

Although you have not asked, I will point out that the use of sub-domains is usually more for dividing up administrative duties.  

Let's say you are the admin of the fruit division of food.org, but not the vegetable division.  You assigned hostnames in your division like: mail, backup and images.  Your co-worker  running the fruit division could also have these same hostnames and still have a unique FQDN, ie; It is possible to have [COLOR="Green"]backup.fruit.food.org[/COLOR] and a [COLOR="Blue"]backup.vegatable.food.org[/COLOR].  Both hosts are immediately identified and are unique.

---

