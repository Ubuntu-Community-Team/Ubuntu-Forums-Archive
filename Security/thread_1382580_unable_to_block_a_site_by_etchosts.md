---
title: "unable to block a site by /etc/hosts"
date: 2010-01-16
forum: Security
---

### Post by piyush.neo on 2010-01-16
i am using Ubuntu 9.10.
i have read that site can be blocked by  adding the entry in /etc/hosts file like this
```
127.0.0.1        orkut.com
```i have added the line but still i am able to surf orkut.com..
am i missing something??

---

### Post by BugBuster on 2010-01-16
Specify the fully qualified domain name (FQDN) of the site like;

127.0.0.1       [www.orkut.com](www.orkut.com)
OR
0.0.0.0         [www.orkut.com](www.orkut.com)

and try again.I hope this works.

---

### Post by piyush.neo on 2010-01-16
still not working....:(
Any more mistakes i can made?????

---

### Post by bodhi.zazen on 2010-01-17
Are you using a proxy server to access the web ?

---

### Post by JackRock on 2010-01-17
> **piyush.neo said:**
> still not working....:(
Any more mistakes i can made?????

I saw the post and thought I'd give it a try.  I entered in the FQDN, but it didn't work until I restarted Firefox.  Did you restart the browser, or edit the file and hit "reload"?

---

### Post by bodhi.zazen on 2010-01-17
> **JackRock said:**
> I saw the post and thought I'd give it a try.  I entered in the FQDN, but it didn't work until I restarted Firefox.  Did you restart the browser, or edit the file and hit "reload"?

Rather then re starting your browser, clear your cache ;)

---

### Post by piyush.neo on 2010-01-17
> **bodhi.zazen said:**
> Are you using a proxy server to access the web ?

**yes!!! i am using a proxy a server**..do i need to do something else for proxy server?????

---

### Post by bodhi.zazen on 2010-01-17
> **piyush.neo said:**
> **yes!!! i am using a proxy a server**..do i need to do something else for proxy server?????

Depends on your proxy. 

1. configure your proxy. Use this option if your proxy is performing ad block (squid/dansguardian or privoxy or bfilter), add the site to restricted content.

2. Add the site to /etc/hosts on the proxy server.

Use this option if the proxy is running on 192.168.0.100 and you are connecting to it from multiple clients on the LAN.

3. If your proxy is on your client, is it a caching proxy (suqid, bfilter)? In that case you need to clear your (proxy) cache.

---

### Post by piyush.neo on 2010-01-17
> **bodhi.zazen said:**
> Depends on your proxy. 

1. configure your proxy. Use this option if your proxy is performing ad block (squid/dansguardian or privoxy or bfilter), add the site to restricted content.

2. Add the site to /etc/hosts on the proxy server.

Use this option if the proxy is running on 192.168.0.100 and you are connecting to it from multiple clients on the LAN.

3. If your proxy is on your client, is it a caching proxy (suqid, bfilter)? In that case you need to clear your (proxy) cache.

so i need to add the sites on proxy server also...actully i am using the college LAN..so i can't edit my proxy server settings...Anyway thanks for help...:o

---

