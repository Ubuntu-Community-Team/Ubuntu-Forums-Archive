---
title: "Ubuntu 14.04 webserver with php memcached csrf token issue"
date: 2021-03-09
forum: Server Platforms
---

### Post by hayden8.04 on 2021-03-09
Hi Everyone,

I have inherited a webserver at a new company I'm at and it's running Ubuntu 14.04 with a php site that uses memcached as its way of storing sessions along with csrf tokens ( I will get to why I'm brining this up soon).

Now I am admittedly not much of a web developer, so I may not be describing all this very well. But essentially what is happening is I have about 10 websites that are running on this webserver, they are basically clones of each other, just setup for slightly different divisions of the company. Most of the websites are able to search and traverse through webpages just fine. But 3 websites which use the exact same underlying code, don't allow for searching. 

From what I can notice, the affected websites constantly replace csrf tokens on each new header (get post calls) and the max cache gets set to 0. 

So from a long look and diagnosing the storage problems, when I disable inside the sessions.php from using memcached to "native" the search starts working again as the CSRF tokens are not being replaced on each search attempt.

But this is only happening on 3 websites not all 10. I also can't leave the temp fix on "native" because my other sites quickly run out of memory and then nothing works at all.

Any ideas are appreciated. 
Thanks!

---

### Post by CelticWarrior on 2021-03-09
Ubuntu 14.04 is out of support since April 2019, unless you have ESM. Do you?

---

### Post by Frogs Hair on 2021-03-09
Moved to ***Sever Platforms***.

---

### Post by LHammonds on 2021-03-10
Not sure I can help fix the caching issue.  I do know that you probably have a huge task ahead of you getting those sites working on the latest PHP version.  Is it a home-grown app or something like WordPress (which does have upgrade paths to current versions).

LHammonds

---

### Post by DuckHook on 2021-03-10
My advice is strictly of the non-technical sort (since I haven't the slightest tech knowledge when it comes to PHP or web stuff).

I realize that you inherited this problem (it's awful to inherit someone else's mess). You also state that fumbling around with this is not your expertise. Therefore, it seems to me that this is filled with potential pitfalls for both you and your organization.

Would it be possible to approach the CIO and say: "We are running critical infrastructure on a seven&#8209;year old OS that is out of support&#8212;or, if ESM, soon will be&#8212;therefore has massive attack surface, ancient software and likely orphaned packages. We are sitting on nitro-glycerine that gets more unstable with every passing day. I would like to bring in outside help to modernize our code base, install the most current OS and close off potential trouble. My value to you is the ability to foresee such dangers, manage the overhaul and then keep us current, productive and safe going forward. To do this, I will need such&#8209;and&#8209;such a budget and the support of you and the executive committee."

I've seen this movie so many times. The powers don't see the real picture and assume that what's worked for so long can continue to be ignored forever. It usually ends sadly for everyone. By at least raising the issue now, you bring it into the clear, open it up to a solution and cannot be blamed (or scapegoated) should it all go to pot.

---

### Post by rsteinmetz70112 on 2021-03-10
There is a reason the other guy isn't there anymore.

---

