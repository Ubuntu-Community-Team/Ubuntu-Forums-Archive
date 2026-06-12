---
title: "Chrome web store developers must now pay one-time 5$ fee. Discuss."
date: 2010-08-20
forum: The Cafe
---

### Post by Dustin2128 on 2010-08-20
[Article in question.]("http://news.softpedia.com/news/Chrome-Extension-Developers-Will-Pay-a-5-One-Time-Fee-153004.shtml")
I like and dislike the idea at the same time. On the one hand, I don't think you should have to pay to get your extensions featured in the official gallery for a FOSS browser. On the other hand, I see why they did this; to block potential spyware add-ons. However, if you write a program that steals sensitive info like bank account passwords, the 5$ fee will be recouped quite quickly.

---

### Post by NCLI on 2010-08-20
I think it's fair enough. I mean, seriously, 5 USD?

---

### Post by Dustin2128 on 2010-08-20
> **NCLI said:**
> I think it's fair enough. I mean, seriously, 5 USD?

when you're a poor student developing extensions as a hobby....

---

### Post by su-37 on 2010-08-20
Im not a fan of it but i can see the point.

---

### Post by Austin25 on 2010-08-20
Well then, I guess if I'm going to develop an extension, I'm going to do it for Firefox.

---

### Post by Dustin2128 on 2010-08-20
> **Austin25 said:**
> Well then, I guess if I'm going to develop an extension, I'm going to do it for Firefox.
big +1 here, I don't think this was a bright idea for a browser trying to rival firefox in extensibility.

---

### Post by gnomeuser on 2010-08-20
> **Dustin2128 said:**
> when you're a poor student developing extensions as a hobby....

It only applies to Web Applications not extensions for Chromium.

If you setup any kind of web app you will have expenses, hosting, development e.g. at least to get to a level where you'd want it featured in the Web app gallery. 5$ there isn't much added to any such budget even for a hobby developer.

---

### Post by lovinglinux on 2010-08-20
Perhaps a merge is in order (even considering I was ignored :))

[http://ubuntuforums.org/showthread.php?t=1556690](http://ubuntuforums.org/showthread.php?t=1556690)

> **gnomeuser said:**
> It only applies to Web Applications not extensions for Chromium.

[It applies to extensions too.]("http://blog.chromium.org/2010/08/security-improvements-and-registration.html")

> **Dustin2128 said:**
> On the other hand, I see why they did this; to block potential spyware add-ons.

Google solely relies on the extension API security model, which is similar to the [next generation of Firefox's extensions]("http://lovinglinuxblog.blogspot.com/2010/08/meet-next-generation-of-firefox.html"), except or the fact that they don't review any extensions published on their gallery, like Mozilla does. Mozilla reviews every new extension submitted for approval and every new version of already approved extensions, while Google reviews only plugins or extensions that access local files. 

This is a major flaw in Google's approach in my opinion and as we can see, it doesn't seem to be working as expected. The problem is that while Chrome extensions use the concept of least privilege and privilege separation to control what the extension can do, a malicious extension would be able to attribute the necessary permissions to itself. So as Google say... "[if you install a malicious extension, all bets are off]("http://www.youtube.com/watch?v=DO-nzPqhdXw")". 

I have read once on the Google extensions blog or documentation (can't find it right now), that one of the benefits of their gallery over Mozilla's is the fact that extensions are available immediately, since there is no review process. So developers don't need to wait for their extensions to be approved. I wonder what they have to say about that now, that developers must pay to upload.

I know I'm "a little" biased, but in my opinion Chrome extensions will never catch up Firefox and now looks to me that Google is shooting themselves in the foot. Some might argue that Google extensions don't require browser restart and don't suffer from upgrade incompatibilities, but Mozilla Jetpack covers all that, they use the same least privilege concept and they are bundled with the necessary APIs, allowing them to use the powerful Firefox API framework with the benefits of Chrome extensions. Additionally, Mozilla is developing an [online extension builder]("https://builder.mozillalabs.com/") that is pretty awesome. They will continue to review Jetpack extensions like they do now.

> **Dustin2128 said:**
> However, if you write a program that steals sensitive info like bank account passwords, the 5$ fee will be recouped quite quickly.

Not to mention that such person would probably use a stolen identity and credicard.

---

### Post by Dustin2128 on 2010-08-21
> **lovinglinux said:**
> Perhaps a merge is in order (even considering I was ignored :)
Huh, I figured that *someone* would get to this before me, but I did a quick search and didn't see your thread. You may be a bit biased, but I have to agree with you 100% that this move has put chrome far behind the curve for browser extensibility. I'm considering swapping back to FFox myself if the speed in the 4.0 beta meets my needs. And if they start adding features like multitouch to linux instead of focusing all their time on windows development....

---

