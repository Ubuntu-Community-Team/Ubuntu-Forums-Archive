---
title: "Firefox 3 out, scrolling on facebook still slow as a snail"
date: 2008-06-12
forum: The Cafe
---

### Post by hanzomon4 on 2008-06-12
What gives?

---

### Post by Tom Mann on 2008-06-12
It's a release candidate, official release on the 17th I think.

---

### Post by barbedsaber on 2008-06-12
works fine 4 me

---

### Post by andrewabc on 2008-06-12
Maybe you should post more info such as your computer specs.
Does it only happen at facebook? Does it only happen on pages with lots of stupid apps?

Do you have compiz enabled?

Firefox 3 is not out. It will be released June 17.

---

### Post by hanzomon4 on 2008-06-12
Mine says firefox 3.0 in the about me and in the update I got last night, I have the proposed repos open. This isn't a support thread cause one is already open. Compiz doesn't make a difference, I have a macbook pro with 2 gigs of ram and a nvidia card so I doubt it's the hardware. It works fine in opera and no, turning off smooth scrolling makes no difference. and Yes it's only on facebook, this is not just annoying it's unusably slow.

---

### Post by timcredible on 2008-06-12
make sure you update xulrunner-1.9 and then reboot, took care of the problem for me with gmail.

---

### Post by Swarms on 2008-06-12
Uh what a horror :)

But post more specs so we can help you.

---

### Post by DigitalDuality on 2008-06-12
d

---

### Post by Anessen on 2008-06-12
I have no problems on Facebook using Firefox 3.0.

Are you running any extensions?

---

### Post by xlash on 2008-08-01
Same happens here.

I did extensive tests.

Most pages runs very fast. Some pages like 
[http://www.facebook.com](http://www.facebook.com)
[http://cyberpresse.ca](http://cyberpresse.ca)

Are slow when we need to scroll. Same Firefox version on a Windows laptop less powerful gives better results.

My computer : 
Intel QuadCore Q6600
Tried a few kernels, currently running the Real-time one.
Computer 100% up-to-date
Firefor 100% up-to-date

I tried with all plugins disabled. No luck either.

I tried the Swiftfox version also optimized for my CPU without success. I did many tweakings in the about:config section of FF without help either.

I notice that 1 of my 4 cores get loaded to 100% while scrolling. This clearly seems to me like an unoptimization of the firefox version, rendering/scrolling feature to use all CPU power in a concurrent mode.

Any help/thoughts on this?

---

### Post by FlyingIsFun1217 on 2008-08-01
Those sort of things (at least for me) depend on the quality of the graphics driver (and the hardware for that matter)...

FlyingIsFun1217

---

### Post by andrewabc on 2008-08-02
> **xlash said:**
> Same happens here.

I did extensive tests.

Most pages runs very fast. Some pages like 
[http://www.facebook.com](http://www.facebook.com)
[http://cyberpresse.ca](http://cyberpresse.ca)

Are slow when we need to scroll. Same Firefox version on a Windows laptop less powerful gives better results.

My computer : 
Intel QuadCore Q6600
Tried a few kernels, currently running the Real-time one.
Computer 100% up-to-date
Firefor 100% up-to-date

I tried with all plugins disabled. No luck either.

I tried the Swiftfox version also optimized for my CPU without success. I did many tweakings in the about:config section of FF without help either.

I notice that 1 of my 4 cores get loaded to 100% while scrolling. This clearly seems to me like an unoptimization of the firefox version, rendering/scrolling feature to use all CPU power in a concurrent mode.

Any help/thoughts on this?

You could try installing greasemonkey and install one of the scripts to remove facebook apps/ads.

could try
[http://userscripts.org/scripts/show/13787](http://userscripts.org/scripts/show/13787)
[http://userscripts.org/scripts/show/11992](http://userscripts.org/scripts/show/11992)

---

### Post by xlash on 2008-08-02
I did find out that it's the extensive stuff on the page which makes it slow. 

When I'm turning off loading all the images, the scrolling of [http://www.cyberpresse.ca](http://www.cyberpresse.ca) is very fast.

And I don't think I'm the only one on Ubuntu/firefox that 1 core of its cpu got lock down while browsing, but the others aren't.

Isn't there a way to build/configure firefox/swiftfox to use all 4 cores?

---

### Post by bengibbs on 2008-09-24
On a core-duo Vaio running without any preferences->appearance->visual effects makes facebook slow for me.  Changing this to normal makes facebook run just fine.

HTH

(2.6.27-4-generic - ubuntu 8.10)

---

### Post by Steve Fisher on 2008-09-24
I *had* problems with Facebook making my processor max out, causing the site to appear to run really slowly. I tracked the cause down to the latest RC of Flash. Going back to the old Flash 9 solved it for me.

And, yeah, visual effects will also affect scrolling for me too.

---

