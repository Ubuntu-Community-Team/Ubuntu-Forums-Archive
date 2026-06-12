---
title: "squid proxy issues with Ubuntu"
date: 2014-11-10
forum: Server Platforms
---

### Post by Osayidan on 2014-11-10
Hello,
I've recently made the switch for all my servers from CentOS 5.5 to Ubuntu 14.0.4.
Everything is working perfectly except my Squid proxy.

The problem is that it takes a very long time to establish a connection to a website. Once the website content loads however the speed appears to be normal.


For example if I go to youtube.com and open a video, it will take a good 15 - 30 seconds to open the page and start playing the video. However once the session seems to be established the video will load just fine and not have any loading/buffering problems.


On the old server this issue did not occur.
The new server is in the same datacenter, on the same hardware, just the OS and Squid version has changed.


Here's the config info:

**Details of old server**
Centos 5.5
Squid 2.6.STABLE21


**New server**
Ubuntu 14.0.4
Squid 3.3.8 (this is what you get with "apt-get install squid")

**squid.conf**
(edited some info for privacy)
The squid config is copied from a backup of the CentOS server. Nothing has been changed except for the location of the ncsa_auth file and the passwd file to match the new paths on the Ubuntu system.

```

auth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid3/passwd
auth_param basic children 5
auth_param basic realm Proxy
auth_param basic credentialsttl 2 hours
visible_hostname edited.for.privacy.com


http_port server.public.ip.address:5432
acl all src all
acl ncsa_users proxy_auth REQUIRED


http_access allow ncsa_users
http_access deny all
cache deny all


#cache_dir null /tmp
memory_pools off
shutdown_lifetime 0


#disable logs
access_log none
cache_store_log none
cache_log /dev/null

```



The only message I get when launching squid is the following:
```
2014/11/09 20:01:28| WARNING: (B) '::/0' is a subnetwork of (A) '::/0'2014/11/09 20:01:28| WARNING: because of this '::/0' is ignored to keep splay tree searching predictable
2014/11/09 20:01:28| WARNING: You should probably remove '::/0' from the ACL named 'all'

```
From the research I did on those warnings people are saying it's a bug in 3.3.8 and to just ignore it until a fix is available on my package manager's repositories. Not sure if that's true or not, don't know enough about squid, I just want to install it and forget it exists which is hard to do when it loads pages so slow :)
Thanks,

---

### Post by SeijiSensei on 2014-11-12
I'd check to make sure DNS resolution is working properly on the proxy server for a start.  Open a browser on the proxy and navigate to a site that loads slowly.  Is it slow there as well?

Are these pure HTTP sessions being proxied?  No HTTPS via SSLBump?

Also 
```
http_port server.public.ip.address:5432
```
Port 5432 is reserved for the PostgreSQL server.  Did someone just choose that one by accident?  What's wrong with the standard 3128?

---

### Post by Osayidan on 2014-11-12
> **SeijiSensei said:**
> I'd check to make sure DNS resolution is working properly on the proxy server for a start.  Open a browser on the proxy and navigate to a site that loads slowly.  Is it slow there as well?

Are these pure HTTP sessions being proxied?  No HTTPS via SSLBump?

Also 
```
http_port server.public.ip.address:5432
```
Port 5432 is reserved for the PostgreSQL server.  Did someone just choose that one by accident?  What's wrong with the standard 3128?

It was indeed a DNS issue. The datacenter had pushed their own crappy DNS servers in the */etc/resolvconf/resolv.conf.d/original* file.
A quick change to openDNS and all is good. So thanks for leading me in that direction.

As for port 5432, since we don't use postges and we use port 54321 for another user-facing service, we decided to just use 5432 so it's easier on users, and we don't use the default ports on anything unless it's a public-facing service.
Doesn't have any impact other than not respecting the port of an application we don't use.
I would have personally put 54322 or something but I didn't do the original setup, and now this is what about 50 PCs are configured with so too late.

Also have not had issues with HTTPs using that config. We use Squid specifically for that since we first tried nginx (since we were already using nginx for something else) but nginx doesn't support forward proxy https.

---

