---
title: "https issue (squid 3.x)"
date: 2012-01-17
forum: Server Platforms
---

### Post by dbdev999 on 2012-01-17
Dear all 
 
        I have issue about squid 3.x can't allow https such as url [https://mail.google.com](https://mail.google.com) 
        my server environment 
 
        1. Ubuntu OS
        2. Squid 3.0.stable19
        3. Tranparent Proxy 1 Nic (IP : 192.168.0.3  & Gateway IP : 192.168.0.100). Normally client can access website(http) through proxy OK.
        4. Sarg installed
 
 
How to fix and allow https ?  
For more config Include Nat table & squid.conf & interface-config & iptable rule . please see attach file.

 
Thanks :O)

---

### Post by SeijiSensei on 2012-01-17
HTTPS and proxies don't mix.  Putting a proxy between the browser and a remote HTTPS site [makes the proxy look like a "man-in-the-middle" attack]("http://wiki.squid-cache.org/Features/SslBump").  [There are ways around this]("http://dvas0004.wordpress.com/2011/03/22/squid-transparent-ssl-interception/") with Squid, but you'll need to create a self-signed SSL certificate for the proxy to use and install it on all the browsers.

If you're doing this to proxy traffic for an entire network of users, you need to think about the privacy issues involved.  Decrypting SSL requests at the proxy gives you the power to read the information being exchanged like credit-card or banking numbers.  If this is for an organization, the powers-that-be should determine whether this is a policy they find acceptable, and whether the staff needs to be notified about the potential privacy threat.

---

### Post by dbdev999 on 2012-01-17
> **SeijiSensei said:**
> HTTPS and proxies don't mix.  Putting a proxy between the browser and a remote HTTPS site [makes the proxy look like a "man-in-the-middle" attack]("http://wiki.squid-cache.org/Features/SslBump").  [There are ways around this]("http://dvas0004.wordpress.com/2011/03/22/squid-transparent-ssl-interception/") with Squid, but you'll need to create a self-signed SSL certificate for the proxy to use and install it on all the browsers.

If you're doing this to proxy traffic for an entire network of users, you need to think about the privacy issues involved.  Decrypting SSL requests at the proxy gives you the power to read the information being exchanged like credit-card or banking numbers.  If this is for an organization, the powers-that-be should determine whether this is a policy they find acceptable, and whether the staff needs to be notified about the potential privacy threat.
Thanks :O)

---

