---
title: "www8 address instead of www"
date: 2011-08-27
forum: The Cafe
---

### Post by vehemoth on 2011-08-27
This is weird, I went to visit the HP website and it redirected me to a URL starting with www8
[http://www8.hp.com/nz/en/home.html](http://www8.hp.com/nz/en/home.html)

---

### Post by dniMretsaM on 2011-08-27
That's about the oddest thing I've seen today.

---

### Post by IWantFroyo on 2011-08-27
I've seen this before, but only with HP's websites.

This is the weirdest HP one I've seen so far:
h41112.www4.hp.com

---

### Post by coolbrook on 2011-08-27
A subdomain likely to relieve the load or to target your geo location or both.

---

### Post by Barrucadu on 2011-08-27
Some busy sites have several servers operating under different subdomains, and you get redirected to one of them when you first load the site.

---

### Post by juancarlospaco on 2011-08-27
Its the Upcomming IPv8.

*Just kidding* :P

---

### Post by sujoy on 2011-08-28
Its just a sub-domain. Whats so weird about it!

---

### Post by vehemoth on 2011-08-28
> **sujoy said:**
> Its just a sub-domain. Whats so weird about it!
I've just never seen it done before.
Here's a bit of an explanation [https://secure.wikimedia.org/wikipedia/en/wiki/Subdomain#Server_cluster](https://secure.wikimedia.org/wikipedia/en/wiki/Subdomain#Server_cluster)

---

### Post by hewbert on 2011-08-28
Not unusual at all, actually.  Another reason you might see this, which I doubt is the motive behind HP's setup, is parallel downloads.  See [http://www.websiteoptimization.com/speed/tweak/parallel/]("http://www.websiteoptimization.com/speed/tweak/parallel/") for a little information on that.
> 
So most web browsers are effectively throttled by this limit on parallel downloads if the objects in the web page they download are hosted on one hostname.


So if you have a single web server, e.g. [www.example.com](www.example.com), you can assign other CNAMEs to it (e.g. www1, www2, ...) and reference them for content in your site to parallelize downloads, adding a potential performance benefit.

---

### Post by sffvba[e0rt on 2011-08-28
I guess not everyone has been using the Internet for that long...


404

---

### Post by haqking on 2011-08-28
it is normal.

They probably have 8 or more servers running www services for load balancing or failover etc.

It is common for web servers to be numbered with a digit after the www service.

just a subdomain, looks like www8 is New Zealand

---

### Post by Artemis3 on 2011-08-29
The subdomain word can be anything you want, it has no obligatory significance.

---

### Post by snip3r8 on 2011-08-29
> **juancarlospaco said:**
> Its the Upcomming IPv8.

*Just kidding* :P

pity i was hoping for md5 style IPs

---

### Post by aaaantoine on 2011-08-29
The important, crucial, unwavering part of the URL is hp.com/.  Everything else is just fluff.

the www subdomain is common, but not required.  For instance, the URL of this thread is 

[http://ubuntuforums.org/showthread.php?t=1834677](http://ubuntuforums.org/showthread.php?t=1834677)

No www.

Just as long as you're not visiting www8.hp.ebilhackarsitez89.net (or .ru, .cn, .nz, and so forth).

---

