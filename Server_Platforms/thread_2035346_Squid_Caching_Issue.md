---
title: "Squid Caching Issue"
date: 2012-07-30
forum: Server Platforms
---

### Post by sixstorm on 2012-07-30
This may be a dumb question, but after doing some heavy Squid testing today on my CIT class (I'm the instructor, never used Squid before today), I've noticed that the logs are stating that all requests are coming directly (DIRECT in the access.log) from the Internet and not from the Squid server itself.  Did I not set something up correctly?

I tried going to say CNN.com a few machines but they all appears to be loading very slowly.

My Squid conf is basically stock minus blocking some sites and allowing my local subnet.

TL|DR - Squid caching does not appear to be working as all requests in access.log say "DIRECT".  Let me know if you need a log.

---

### Post by albandy on 2012-07-30
try with 
sudo squid -z
this will regenerate cache.

Stop squid before doing this.

---

### Post by sixstorm on 2012-07-30
> **albandy said:**
> try with 
sudo squid -z
this will regenerate cache.

Stop squid before doing this.

Ok, I did that and it made some directories for me.

I also found some cache properties that were commented out.  I *think* caching is working now, but not sure how to tell 100%.  Any thoughts?  Sorry for the noob questions.

Squid is doing really well with the simple setup and simple web filtering.  May be using this for the entire school before too long!  :D

---

### Post by sixstorm on 2012-07-30
I think I got it figured out.  Caching was working but you have to setup the "refresh patterns" and check your cache size with the following command:

sudo du -sh /var/spool/squid3

Appears to be working great in my home lab, but will test more tomorrow with my class.

Too bad getting a transparent proxy isn't working that well for me . . .

---

### Post by sixstorm on 2012-07-31
Going to reopen this thread as I don't think caching is working 100%.  I know that images and such are being cached BUT when my users go through the proxy, it is not loading the cached images/pages/etc.

The reason I believe this is because when I look at the access.log, all hits are showing "DIRECT", which means it was grabbed from the origin server.  Why can they not access what is already cached?

---

### Post by SeijiSensei on 2012-07-31
> **sixstorm said:**
> The reason I believe this is because when I look at the access.log, all hits are showing "DIRECT", which means it was grabbed from the origin server.  Why can they not access what is already cached?

Look for requests that return TCP_REFRESH_UNMODIFIED responses.  These are requests for cached items.  Squid first checks upstream with the web server (hence the DIRECT request) to see if the object has been modified after it was cached.  If not, Squid returns the cached version.  So every request, even ones for cached objects, generates a web server request.  

In my logs there are only "DIRECT" entries and "NONE" entries.  The latter result from requests for objects that are blocked by one of our ACLs.

As for transparency, are you running Squid on an egress gateway?  That's by far the easiest method to build a transparent proxy.

1)  Add the keyword "transparent" to the http_port directive in squid.conf.

2)  Add the following iptables rule to the server:

```
iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 192.168.1.0/24 --destination-port 80
```

Replace the "192.168.1.0/24" with the subnet address that covers your internal hosts.

---

### Post by sixstorm on 2012-07-31
> **SeijiSensei said:**
> Look for requests that return TCP_REFRESH_UNMODIFIED responses.  These are requests for cached items.  Squid first checks upstream with the web server (hence the DIRECT request) to see if the object has been modified after it was cached.  If not, Squid returns the cached version.  So every request, even ones for cached objects, generates a web server request.  

In my logs there are only "DIRECT" entries and "NONE" entries.  The latter result from requests for objects that are blocked by one of our ACLs.

So even cached objects that get sent to the user will generate a "DIRECT" entry via access.log?  How do you even know that users are getting cached items?  I notice that some users have a LITTLE faster loading times than going straight through but it's hit and miss.

I've read that it's possibly the fact that I'm not blocking ads, even though I'm manually blacklisting them daily.  I guess in my mind, I'm expecting squid to make our horrible connection better for our sites that we frequently visit.

> As for transparency, are you running Squid on an egress gateway?  That's by far the easiest method to build a transparent proxy

I've not had the best luck running squid in transparent proxy mode, so I'm just running straight proxy right now via GP.

I just want to make sure that caching is working properly and there isn't a real way to tell that I know of lol.

---

### Post by SeijiSensei on 2012-07-31
The [Squid Cache Manager]("http://wiki.squid-cache.org/Features/CacheManager?action=show&redirect=SquidFaq%2FCacheManager") provides a lot of useful statistics about the cache including hit rates.  I run a proxy in front of about 200 client workstations.  About 20-40% of the requests are for cached objects.

Mostly the gains are going to come from graphics that are loaded repeatedly, like banners, icons, etc., from popular sites.  Actual HTML pages are less commonly cached, often because they are generated from scripts rather than existing as static pages.  The URLs for dynamic pages can often differ slightly between requests; one common situation is where a session ID is contained in the URL.

This client uses Squid much less for its caching aspects than for its ability to control web requests.  We have rules to block executable files, ad sites, known [malware sites]("http://www.malware.com.br/cgi/submit?action=list_squid"), and similar security concerns.

---

### Post by sixstorm on 2012-07-31
> **SeijiSensei said:**
> The [Squid Cache Manager]("http://wiki.squid-cache.org/Features/CacheManager?action=show&redirect=SquidFaq%2FCacheManager") provides a lot of useful statistics about the cache including hit rates.  I run a proxy in front of about 200 client workstations.  About 20-40% of the requests are for cached objects.

Mostly the gains are going to come from graphics that are loaded repeatedly, like banners, icons, etc., from popular sites.  Actual HTML pages are less commonly cached, often because they are generated from scripts rather than existing as static pages.  The URLs for dynamic pages can often differ slightly between requests; one common situation is where a session ID is contained in the URL.

This client uses Squid much less for its caching aspects than for its ability to control web requests.  We have rules to block executable files, ad sites, known [malware sites]("http://www.malware.com.br/cgi/submit?action=list_squid"), and similar security concerns.

Ok, now this example makes sense.  I knew that Squid didn't cache entire web pages, but more of the images and such for faster loading.  I did try to log into the cache manager earlier today but apparently I didn't have something configured properly; I'll try again tomorrow.

I do like the fact that Squid is able to block exec files, file type downloads, ad sites, etc.  This will really help at my school since we have students who like to download, download, download.  :D

Thanks for the help SeijiSensei!  I'll just mark this solved.

---

