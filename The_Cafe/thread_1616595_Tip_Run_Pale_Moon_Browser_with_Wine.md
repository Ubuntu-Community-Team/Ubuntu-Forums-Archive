---
title: "Tip: Run Pale Moon Browser with Wine"
date: 2010-11-08
forum: The Cafe
---

### Post by Darth Penguin on 2010-11-08
[COLOR=RoyalBlue][Pale Moon Browser]("http://www.palemoon.org")[/COLOR] is Firefox optimized for Windows. It's lighter, uses less RAM and is faster than regular Firefox, nearly as fast as Chrome. It runs just as fast on Linux with Wine and has all the functions Firefox has on Windows(i.e. selects the entire URL when you click on the address bar).



Also, since it's running on Wine any malware that affects the browser will not affect your Linux OS and it's a sandbox.

---

### Post by howefield on 2010-11-08
Moved to Cafe.

---

### Post by FuturePilot on 2010-11-08
> **Darth Penguin said:**
>  and has all the functions Firefox has on Windows(i.e. selects the entire URL when you click on the address bar).

Not Windows specific

browser.urlbar.clickSelectsAll True

---

### Post by Joeb454 on 2010-11-08
> **FuturePilot said:**
> Not Windows specific

browser.urlbar.clickSelectsAll True

Awesome, thanks FuturePilot, I didn't even know about that. I just got used to double clicking :)

---

### Post by aktiwers on 2010-11-08
What happened to SwiftFox?

---

### Post by FuturePilot on 2010-11-08
> **Joeb454 said:**
> Awesome, thanks FuturePilot, I didn't even know about that. I just got used to double clicking :)

So have I. ;)

---

### Post by medic2000 on 2010-11-08
Is it faster then Swiftfox and other variants?

---

### Post by Helkaluin on 2010-11-08
> **medic2000 said:**
> Is it faster then Swiftfox and other variants?

Honestly, the difference in these such re-branded custom builds are minimal at best. Simply because there's an '-O3' and a 'march=prescott' CFLAG won't really do THAT much of a difference. The diff that, for example, Swiftfox supplies lists only common configurations such as enabling pipelining and increasing the max per domain connections.

The main advantages of building for custom processors is the enabling of extra instruction sets - most of which benefit floating point stuff, and not really that much relevant to the web browsing things that Firefox does.

PGO, on the other hand, might do a bit more. But Swiftweasel is rather dead now. Or you can compile yourself.

With all that said, the fact is that the most performance you will increase is with the JM+TM that is still brewing in Firefox 4 nightlies. JM+TM is now 'officially' faster than both Webkitcore and V8 on Sunspider now. Actual code difference makes much more impact than the several percents of performance you can squeeze out by compilation flags. If you really want speed I suggest looking into the daily mozilla PPA instead of these custom builds.

---

### Post by zer010 on 2010-11-08
I've heard that FF4 is blazing fast, almost or just as fast as Chrome. I might wait a little longer until I try it out though. With the new UI coming out, it looks great, but last I heard, the Linux build didn't have the new UI yet and still has a way to go. The fact that they pushed the release date to sometime in 2011, is somewhat of a bummer, but I'd rather see a complete release rather than one that's "slapped together".

---

### Post by Darth Penguin on 2010-11-09
I like that it uses less RAM, not just that it's fast. There will be a Pale Moon build for Firefox 4 once the code is stable.

---

