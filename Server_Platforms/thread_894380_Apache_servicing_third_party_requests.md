---
title: "Apache servicing third party requests??"
date: 2008-08-19
forum: Server Platforms
---

### Post by raghaven.kumar on 2008-08-19
Hi,

  I recently installed a apache2.2 in **Ubuntu 8.04 server**.
After that load became very high on our server, then i ran **apachetop** in our server.
We are running sites based CMS like Zope and Plone.
The output which is shown by apachetop doesnt contain a single request of our sites.
All are some third party requests.


```

last hit: 12:38:43         apachetop runtime:  0 days, 00:00:39             12:38:44
All:         1469 reqs (  38.7/sec)       8682.9K (  228.5K/sec)    6052.6B/req
2xx:    1125 (76.6%) 3xx:     252 (17.2%) 4xx:    60 ( 4.1%) 5xx:    32 ( 2.2%)
R ( 30s):    1186 reqs (  39.5/sec)       7527.7K (  250.9K/sec)    6499.5B/req
2xx:     912 (76.9%) 3xx:     197 (16.6%) 4xx:    50 ( 4.2%) 5xx:    27 ( 2.3%)

 REQS REQ/S    KB KB/S URL
   48  1.60 102.0  3.4*http://ad.yieldmanager.com/imp
   24  0.80 141.8  4.7 http://afe.specificclick.net/
   23  0.77 168.7  5.6 http://ypn-js.overture.com/partner/js/ypn.js
   22  0.73  34.8  1.2 http://adopt.specificclick.net/adopt.sm
   21  0.75  88.1  3.1 http://ypn-js.overture.com/d/search/p/ypn/jsads/
   20  0.69  13.6  0.5 http://ad.yieldmanager.com/iframe3
   14  0.47   0.0  0.0 login.icq.com:443
   13  0.45  41.2  1.4 http://banner.adtrgt.com/cpv_inline.js
   12  0.50   0.5  0.0 http://209.250.234.186/proxy.php
   10  0.33   0.0  0.0 http://ai.realmedia.com/
   10  0.33 431.4 14.4 http://api.widgetbucks.com/api/api.flow
    9  0.31  81.4  2.8 http://clickmycollege.com/
    9  0.30   0.0  0.0 205.188.179.233:443
    9  0.33   1.1  0.0 http://banner.addlvr.com/cpi.jsp
    8  0.27   3.1  0.1 http://media2.mediafileshost.com/images/prep_ctr.php
    7  0.24   0.3  0.0 HTTP://rmd.atdmt.com/tl/DocumentDotWrite.js
    7  0.26   4.5  0.2 http://syndication.mmismm.com/mmtnt.php
    7  0.24  94.4  3.3 http://m1.2mdn.net/951243/RHS_728x90_Animated.gif
    6  0.23   0.2  0.0 http://202.108.33.62/hits
    6  0.25   2.0  0.1 http://ads.nebuadserving.com/servlet/ajrotator/6378/0/vj
    5  0.17   0.0  0.0 http://tcla.mmismm.com/mmmss.php
    5  0.17   0.0  0.0 205.188.153.121:443
    5  0.33  21.0  1.4 http://ad.adserverplus.com/st
    5  0.20  18.3  0.7 http://ads.pointroll.com/PortalServe/
    5  0.17   0.2  0.0 http://csvta.target.com/TGTTCKDA/tdka_zag.gif
```

When i looked thru the Apache access.log it was full of 404 and 200 error messages for GET requests.

What can i do to reduce these third party requests and speed up my Apache ?

*PS: I now configured cache module in Apache to cache pages which has a significant change on the speed but the apachetop output still displays the non relevant sites only*

---

### Post by MJN on 2008-08-19
It sounds like you have configured Apache to serve as a proxy but not locked it down. The requests are likely an attempt to create revenue by getting your server to perform repeated click-throughs.
 
Mathew

---

### Post by cdenley on 2008-08-19
It sounds like they're trying to use it as a proxy, but they're not succeeding because your server isn't configured as one. Sending a GET request for "http://clickmycollege.com/" will be the equivalent of a get request for "/", which would be a 200. Sending a GET request for "http://ad.yieldmanager.com/iframe3" would be equivalent to "/iframe3", which would give you a 404. Are they all coming from the same IP address?

You can try this to block automated scripts.
```

sudo iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW -m recent --set --name apache
sudo iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name apache -j DROP

```
I never tried it on a production server, and I'm not sure if it can produce false positives (block real clients).

---

### Post by MJN on 2008-08-19
You can only confirm a 200 HTTP code is 'safe' by comparing the byte size served with that of the default page.
 
Mathew

---

### Post by cdenley on 2008-08-19
Or by testing your server
```

telnet localhost 80
GET http://ubuntuforums.org/ HTTP/1.0



```
That should give you the output of YOUR homepage, not ubuntuforums.

---

### Post by cdenley on 2008-08-19
If you want to give a 403 error instead of 404 or 200 for proxy attempts, you can add this to your vhost configuration
```

ProxyRequests On
ProxyVia On
<Proxy *>
Order Deny,Allow
Deny from all
</Proxy>

```
Then run these commands
```

sudo a2enmod proxy
sudo a2enmod proxy_http
sudo /etc/init.d/apache2 restart

```

I'm not sure if this would deter proxy scanners or reduce the server load from these attacks.

---

