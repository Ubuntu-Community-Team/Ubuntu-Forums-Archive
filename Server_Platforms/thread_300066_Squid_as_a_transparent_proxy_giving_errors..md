---
title: "Squid as a transparent proxy giving errors."
date: 2006-11-15
forum: Server Platforms
---

### Post by hazza96 on 2006-11-15
I have just upgraded my server two versions to Edgy. On the server I **had** squid working perfectly as a transparent proxy with the iptables rule:

```
$IPTABLES -t nat -A PREROUTING -i $INT_IF -p tcp --dport 80 -j REDIRECT --to-port 3128
```

If I set the client browser to use the server as the proxy everything works fine. The problem with that is there are other utility's and stuff that you can't set a proxy.

My squid.conf file looks like this:
> #
# Squid normally listens to port 3128
http_port 3128

#We recommend you to use at least the following line.
hierarchy_stoplist cgi-bin ?

#We recommend you to use the following two lines.
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY

# Apache mod_gzip and mod_deflate known to be broken so don't trust
# Apache to signal ETag correctly on such responses
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache

cache_mem 32 MB

#
#Default:
# cache_dir ufs /var/spool/squid 100 16 256

#  To log the request via syslog specify a filepath of "syslog"
access_log /var/log/squid/access.log squid


# OPTIONS FOR EXTERNAL SUPPORT PROGRAMS
# -----------------------------------------------------------------------------

#
#Suggested default:
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320


# ACCESS CONTROLS
# -----------------------------------------------------------------------------

#Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563	# https, snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443 563	# https, snews
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT

#
#Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
http_access deny manager

# Only allow purge requests from localhost
http_access allow purge localhost
http_access deny purge

# Deny requests to unknown ports
http_access deny !Safe_ports

# Deny CONNECT to other than SSL ports
http_access deny CONNECT !SSL_ports

# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

# Example rule allowing access from your local networks. Adapt
# to list your (internal) IP networks from where browsing should
# be allowed
acl our_networks src 192.168.1.0/24
http_access allow our_networks
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

#
# and finally allow by default
http_reply_access allow all

#Allow ICP queries from everyone
icp_access allow all


# ADMINISTRATIVE PARAMETERS
# -----------------------------------------------------------------------------

#
#Default:
# coredump_dir none
#
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid



I have researched my error:
> 192.168.1.1 TCP_DENIED/400 1279 GET error:invalid-request - NONE/- text/html

Everything I have read indicates I should have in my squid.conf the following lines:
> httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on

The only problem with that is when I try and start squid it complains those lines are  unrecognized. Has anyone got squid working with transparent proxy on Edgy?

---

### Post by hazza96 on 2006-11-16
No one has any ideas?

---

### Post by bb002 on 2006-11-16
I use dapper, myself. My guess is that edgy uses a new version of squid and the squid maintainers changed the config options.

Run "squid -v" in a terminal. This will cause squid to output it's version and the options passed to "./configure" when it was compiled. I just want the version number.

On my system the squid version is 2.5.STABLE12

I'll see if there is a newer version out and what the options have changed to if anything.

---

### Post by bb002 on 2006-11-16
I found this, i saw else where that this is the same for squid v3.0, not sure if 3.0 is released though..... 
[http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s2](http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s2)

seems to be the cause of your problems....:)

Most of your old lines seem to change to some form of http_port. I just can't find any documentation on to what it is supposed to look like. Atleast it is a step in the right direction...I hope so anyways.

---

### Post by hazza96 on 2006-11-17
Since I was not getting much response to the question here I emailed the HUMBUG mailing list and they provided *part* of the answer.

The line *http_port 3128* needs to have **transparent** added to the end.

Problem was when I did that I struck this bug:
[http://www.squid-cache.org/bugs/show_bug.cgi?id=1650](http://www.squid-cache.org/bugs/show_bug.cgi?id=1650)

As it says in the notes of that bug report you add to your squid.conf the line:
always_direct allow all

It all works now, yeah!!!!

---

### Post by hazza96 on 2006-11-17
> **bb002 said:**
> I found this, i saw else where that this is the same for squid v3.0, not sure if 3.0 is released though..... 
[http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s2](http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s2)
Thanks for your help but as I said in the previous post I found the exact answer I needed. That FAQ page demonstrates the problem with techos/programmers writing FAQ's:
> http_port

    Now takes a list of options in addition to the port address, specifying the purpose of this http_port. Default is plain Internet proxy as usual

Wow it takes other options!! Fantastic, lets just pluck out of our arse what they could possibly be... umm let me try the option "aunt beryl's Internet Explorer proxy", that's it's purpose no? What about I try "monkey pole rider" named after the FAQ writer, that doesn't work either... oh I know lets just find a random word generator and write a script to try every word in the English and French dictionary.

I am glad I found the answer before I hit that page because I would have read it and went **....and....?????**

---

### Post by hazza96 on 2006-11-17
Ah I am a ranting idiot, I scrolled up a bit to:
[http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s1](http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s1)

The first point in that section is:
> the keywords "accelerated" and "transparent" can be specified after each port

I will go take my medication now.....

---

### Post by bb002 on 2006-11-17
> **hazza96 said:**
> Ah I am a ranting idiot, I scrolled up a bit to:
[http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s1](http://sunsite.bilkent.edu.tr/pub/infosystems/Squid/Versions/v2/2.6/squid-2.6.STABLE1-RELEASENOTES.html#s1)

The first point in that section is:
> the keywords "accelerated" and "transparent" can be specified after each port

I will go take my medication now.....

Don't worry about it. I was left going "**.....and....?**" myself. I was just hoping that page would be a step in the right direction. :) Glad you got it going!

---

### Post by hazza96 on 2006-11-18
> **bb002 said:**
> Don't worry about it. I was left going "**.....and....?**" myself. I was just hoping that page would be a step in the right direction. :) Glad you got it going!
Well that FAQ is not as bad as some I have read, when I first started in Linux it was no where as user friendly and there were no where near as many resources for beginners as there is now.

That FAQ could be improved by repeating what the two options are for that config line. I know it's repetition but when people are told to RTFM and the manual is 38 pages long and contains the one small gem you need hidden inside a paragraph that takes two screens, people give up.

Thankfully the learning curve for Linux no longer requires Carabiners, climbing shoes, a helmet and a harness. Now the lucky bastards just put on their walking shoes, grab a backpack for their water bottle and camera in case they see something scenic on the way.

Dam it, you Ubuntu people should stop letting people download it unless they can certify with a Statutory Declaration they have compiled a kernel **and** all their devices worked, Bloody slackers... stroll in the forest indeed... even my wireless card inside my late model IBM laptop worked immediately, don't these Ubuntu jokers know that the best way to learn is when things to go wrong?

Ubuntu is so good nothing goes wrong and people don't learn, start leaving things out, keep the bugs in.... oh wait.....

---

