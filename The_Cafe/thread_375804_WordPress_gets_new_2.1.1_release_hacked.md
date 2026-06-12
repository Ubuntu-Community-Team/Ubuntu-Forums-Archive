---
title: "WordPress gets new 2.1.1 release hacked"
date: 2007-03-04
forum: The Cafe
---

### Post by Kobalt on 2007-03-04
Hey you guys,

I'm sure many of you use WordPress to blog. For those using they're own hosting with WP, I hope you're aware of that bad news : 
> Longer explanation: This morning we received a note to our security mailing address about unusual and highly exploitable code in WordPress. The issue was investigated, and it appeared that the 2.1.1 download had been modified from its original code. We took the website down immediately to investigate what happened.

It was determined that a cracker had gained user-level access to one of the servers that powers wordpress.org, and had used that access to modify the download file. We have locked down that server for further forensics, but at this time it appears that the 2.1.1 download was the only thing touched by the attack. They modified two files in WP to include code that would allow for remote PHP execution.
There is a new 2.1.2 release that fixes the problem, you can have all the info [over there]("http://wordpress.org/development/2007/03/upgrade-212/").

---

