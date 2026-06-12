---
title: "Why are there not multiple companies that make parallel (unrelated) versions of WINE"
date: 2012-04-21
forum: The Cafe
---

### Post by venom104 on 2012-04-21
Here is a quote from the page on the wine wiki... [http://wiki.winehq.org/ImportanceOfWine](http://wiki.winehq.org/ImportanceOfWine)

**Supply diversification**

 Diversifying your supply is universally considered to be an important aspect of risk management. 
Yet, The US Department of Justice has "[found]("http://www.usdoj.gov/atr/cases/f3800/msjudgex.htm#iiia")"  that Microsoft Windows is run by more than 95% of personal computers.  Even taking Apple's Mac OS into account, Microsoft Windows is still  present on more than 80% of computers, and this is likely also true in  most other countries, not just in the US. Thus governments, companies  and home users all over the world ultimately depend on a single  provider: Microsoft. 
The  question is not whether Microsoft has evil intents, or whether it may  go out of business, but whether its plans match yours. A company may  want to deploy thin clients to simplify administration and save money on  per-client Windows licenses. But is Microsoft going to make it viable  and undercut its Windows market? Where is the alternative if Microsoft  implements its software subscription model? If Microsoft is not  interested in catering to your market, then you have no other provider  to turn to.

To understand more about my question, you should probably read the entire page. Currently, the only compatibility layers that exist (that I know of) are either wine or a derivative of wine (codeweavers, cedega, ect). 

Why aren't there multiple companies producing their own versions of WINE? According to the article, 80% of computers run windows, so it would BENEFIT the unix like OSes if they could have multiple versions of "WINE", so that we could run programs that wouldn't work in one version.

I'm not saying WINE does a bad job of running windows programs; I'm saying that we could probably expect more programs to run if there were some other way of running windows programs on a unix like system.

---

### Post by grahammechanical on 2012-04-21
You seem to have missed the word "Yet" in that page.

The Wine people are arguing that if diversification of supply is so important as everybody says, then why do they run Windows and not much else.

The failure to diversify the OS means that there is a need for Wine.

The issue is that Windows is a proprietary OS. It does not release code. The Wine people and the commercial company backing them up have to work out ways of doing what they do without copying from Microsoft.

By the way, could you please ask the Moderators to move this post into the community Cafe. You should not put posts like this in the Help Sections of the forum.

When people do that I begin to think that they are looking for an argument which would not be allowed in the Cafe, so they try to bypass the safe guards.

But you are not doing that. so, I look forward to seeing this post in the Community Cafe.

Regards.

---

### Post by oldos2er on 2012-04-21
Not an Ubuntu support question; moved to Community Cafe.

---

### Post by haqking on 2012-04-21
same discussion here almost [http://ubuntuforums.org/showthread.php?t=1961653](http://ubuntuforums.org/showthread.php?t=1961653)

I said it in there and i will say it again in here

You cant put a VHS tape into a DVD player ;-)

---

### Post by del_diablo on 2012-04-21
Why are not there several companies making their own compitablity layer? The reason is quite simple: On the commerical side the lawyer mentality is one thing, another one is that a shop usually also have money to waste, which means that they will use them on licenses for applications(Adobe, 3D Max, etc) and Windows. Another small thing about is that beyond having money to spare, they also know for a fact that if they for example want to emulate Windows they can ignore the EULA and just use a copy for dedicated emulation purposes.
Secondly, there was a dedicated effort for emulating Windows back in the day, but that sort of died when Windows got mainstream and x86 got high performance.
As for another important reason why there is Wine, and its forks: A compitablity layer is a extremely complex piece of software, especially when it comes to something as large and full of legacy as Windows. Reinventing the wheel is a extremely cumbersome process, and its usually easier to get a good deal with a company who owns a application or API, than to hire a bunch of coders for a dedicated and long time period, to achive exactly the same. 

Summary:
-A compitablity layer is a easy thing to achive, if you are targetting a console, due limited API and roughly no legacy.
-Windows have this insane amount of API, undocumented API, legacy, and a lot of special hardware workarounds. Its basically too large. Its a extremely niche marked due the size, and the size alos serves as a too large barrier of entry for commercial enteties, especially with the lack of OS fragmentation today.
-Emulators is a lot more cost effective at this point, so is thin clients. Emulators with a bit if hacks runs at roughly native performance too, so there goes that issue
-And then there is stuff like React OS, which is a extremely cumbersome project that attempts to clone Windows 2000 and lot more. Its more or less the exact same as Wine, just on OS level instead of translating API calls. So there is a separate effort.

---

### Post by venom104 on 2012-04-22
I think that concludes the information I needed. Thank you all!

---

