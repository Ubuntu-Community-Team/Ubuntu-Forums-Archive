---
title: "squid and dansguardian"
date: 2007-08-26
forum: Server Platforms
---

### Post by knorr.orange on 2007-08-26
I am currently using squid and squidguard for proxy and filtering.  I am interested in changing to squid/dansguardian though to take advantage of the content rating system.  I have one other requirement though:  bandwidth and website restrictions for certain machines (IP's.)

I will be doing this using squid acl's and delay pools.  That requires that I identify the user's ip address.  Is it possible to do that with dansguardian?  As I understand it, all the requests coming into squid will look like they came from a local web browser, which is actually just dansguardian.  Does anyone have any experience with such a setup?

I am open to any methods to get my desired features:
-bandwidth restrictions per IP
-website restrictions per IP
-dansguardian content filter
-caching

---

### Post by knorr.orange on 2007-08-27
Found an answer to my question about the ip's making it through to squid.  It was in the dansguardian FAQ:
> 
9. Since using DansGuardian my squid ACLs no longer work.

That is correct. The source ip of the request to squid is localhost as it is DansGuardian making the request which is running locally on the server. There are two solutions. One is to put squid in front of DansGuardian and have DansGuardian use an uprstream proxy such as the ISPs. The other is to install the patch available to make squid use the X-Forwarded-For entry from DansGuardian which would make the ACLs work again. 

Ubuntu builds of squid do not include the option, so a recompile is required.  This post seems to cover that:
[http://marc.info/?l=squid-users&m=117517445629357&w=2](http://marc.info/?l=squid-users&m=117517445629357&w=2)

---

