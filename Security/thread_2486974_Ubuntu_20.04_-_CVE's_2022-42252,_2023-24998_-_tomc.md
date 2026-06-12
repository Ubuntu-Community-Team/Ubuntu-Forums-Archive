---
title: "Ubuntu 20.04 - CVE's 2022-42252, 2023-24998 - tomcat9"
date: 2023-05-18
forum: Security
---

### Post by bturnbough2 on 2023-05-18
Hi Everyone,

Not here to complain, but Id like to point some things out about these CVE's.  

CVE-2022-42252 was published on 11/1/2022
CVE-2023-24998 was published on 02/20/2023

I'm being called onto the carpet by management because they want to know why these vulnerabilities are still unpatched.  I of course know why they aren't -- the vendor hasn't released a patch.

That brings me to my next point... why are these two vulnerabilities still unpatched (6 mths & 3 mths old)?  Also, looking at the Ubuntu CVE xref site, it appears they're still basically untouched in terms of being worked on.  Why is that?  Seems to me as if Ubuntu has gotten lax on things like this over the years (I've been a user since around 7.04).  Using other distros seems more and more compelling due to issues Im more frequently seeing.  

Now, I know you're going to say .. we'll it's FREE, what do you expect?   Well, to counter that point.. say I HAVE paid for 20.04 support.  That doesn't change the fact that these two CVE's are still unpatched.

What's everyones take on this?

---

### Post by QIII on 2023-05-18
It appears that each of those can be resolved by modifying configurations.  That may be why there is no rush to fix them.  Canonical is a pretty small company and may simply not have the resources to modify its Apache packages and test them thoroughly ... and they might have to do that all over again if Apache puts out a new release.  Maybe the purveyors of distributions are squawking at Apache.  Who knows?

Maybe you could cool the management by showing them the CVE and how you rectified it? 

(Just a point of interest with regard to CVEs:  It appears that Apache has had 1943 vulnerabilities reported over the years, while Nginx has had, uh, two.)

---

