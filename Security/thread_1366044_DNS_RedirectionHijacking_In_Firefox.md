---
title: "DNS Redirection/Hijacking In Firefox"
date: 2009-12-28
forum: Security
---

### Post by UltraZone on 2009-12-28
This might be a mozilla-specific bug, but I thought I would post this here anyway since you guys are in the know.

Basically the problem I get is this DNS redirection in Firefox while in Linux.  I booted into Vista and Firefox and Safari there do not have this problem.  My iPod Touch doesn't have this problem either.

Here's a screenshot of the annoying results:

[http://tinypic.com/r/t6royp/6](http://tinypic.com/r/t6royp/6)
[IMG]http://tinypic.com/r/t6royp/6[/IMG]

this problem is very random, it comes and goes.  Do you guys know  what's going on?

Actually this problem might also occur in other OSs just as well, due to the random nature of this thing maybe I just haven't hit on it.... :confused:

---

### Post by Jekshadow on 2009-12-28
Its not a bug, you should thank your ISP for that. Here is what I get:

[http://i.imgur.com/UArPf.png](http://i.imgur.com/UArPf.png)

---

### Post by UltraZone on 2009-12-28
I thought that it may have been Juno's fault all along, however how come it's such a random problem?  Also, when I get this problem in Firefox, I load up the same page in Chrome and it works, go back to Firefox: no cigar.  Until some minutes later then it's as if nothing happened..... :confused:

---

### Post by ibuclaw on 2009-12-28
> **UltraZone said:**
> I thought that it may have been Juno's fault all along, however how come it's such a random problem?  Also, when I get this problem in Firefox, I load up the same page in Chrome and it works, go back to Firefox: no cigar.  Until some minutes later then it's as if nothing happened..... :confused:

Try **Ctrl+F5** to force refresh the page.

Might also want to clear temporary internet session Files too (Cookies, Files, etc). To see if that vindicates the problem.

---

### Post by zey on 2009-12-28
> **tinivole said:**
> Try **Ctrl+F5** to force refresh the page.

Might also want to clear temporary internet session Files too (Cookies, Files, etc). To see if that vindicates the problem.


maybe you're right..

---

### Post by lovinglinux on 2009-12-28
Perhaps is taking too much time to get the correct address from the DNS server and your ISP is redirecting to the search page. Try to disable ipv6 in Firefox. That should improve DNS queries.

To do that, type **about:config** in the address bar, then type **ipv6** in the filter field and then set the option **network.dns.disableIPv6** to **true**.

Also take a look at [this](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/).

---

### Post by BkkBonanza on 2009-12-28
I don't use my ISP DNS servers any more. Thery are often flaky and intermittant. I haven't had them redirect queries yet but if they did I wouldn't stick around either.

You can replace the DNS server that you use in /etc/resov.conf or in your router if you use one, depending on how things are setup. I use a combination of opendns and google now instead.

Google has DNS at 8.8.8.8 and 8.8.4.4 (easy to remember!)

---

