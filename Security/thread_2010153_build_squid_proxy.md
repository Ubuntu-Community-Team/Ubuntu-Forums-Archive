---
title: "build squid proxy"
date: 2012-06-25
forum: Security
---

### Post by watts3000 on 2012-06-25
Guys I would like to build a proxy using Squid below are my requirements I don't even know if what I want is possible through a non commercial offering. Also should I be using Squidguard or Dans Guardian for this project? BTW I looked at other solutions such as Untangle and Astaro security gateway products but they seemed to be incomplete especially when it came to Youtube filtering which is huge to me. 
 
 
1. Force safe searches on Google, Bing, Yahoo and Youtube.
2. Tie this back into Microsoft AD so filtering is performed by user groups for example safe searches will be forced on group a but group b has wide 
open internet access.
3. Configure a transparent proxy

---

### Post by SeijiSensei on 2012-06-25
> **watts3000 said:**
> 1. Force safe searches on Google, Bing, Yahoo and Youtube.

That's an interesting problem.  Wouldn't you have to rewrite the outgoing URLs to append the appropriate "safe search" option depending on the destination?  I don't know that Squid has a convenient way to do this, but it might.  You'd have to write ACL rules that key on the destination domain.

Update: Yep, you can do this with "[Redirectors](http://wiki.squid-cache.org/Features/Redirectors)".  [This implementation](http://squirm.foote.com.au/), though old, might be appropriate as a starting point.

> 2. Tie this back into Microsoft AD so filtering is performed by user groups for example safe searches will be forced on group a but group b has wide 
open internet access.

It's easy to do if users have relatively fixed IP addresses.  Then you can write rules that apply some ACLs to some subnets or address lists and different rules to another list of addresses.  We do this at one client's site.  The IP addresses reside in files that are referenced in ACLs.  Webmin has a pretty good Squid interface so relatively untrained admins can add or delete addresses from the lists and restart Squid using a browser interface.

I don't know of any way you could use AD usernames for this task.  I doubt Squid even knows the username associated with a specific request.

> 3. Configure a transparent proxy

Requires only an iptables rule and a configuration line in squid.conf.  There are lots of pointers about how to set up transparent squid proxies if you search Google.  It's easiest to configure if the proxy is the final gateway router to the Internet, but there are other methods you can use as well.

---

