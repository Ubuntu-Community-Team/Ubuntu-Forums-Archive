---
title: "Can't stop browser tracking anymore for some browsers"
date: 2019-04-08
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2019-04-08
> Going forward, if privacy is important to you and you want to reduce the risk of being tracked online, then you will need to use Firefox or Brave.
[https://www.bleepingcomputer.com/news/software/major-browsers-to-prevent-disabling-of-click-tracking-privacy-risk/](https://www.bleepingcomputer.com/news/software/major-browsers-to-prevent-disabling-of-click-tracking-privacy-risk/)
> 
Newer versions of Chrome, Safari, and Opera will no longer allow you to disable hyperlink auditing, which is a concern for those seeking maximum privacy. It also applies to MSFT's Edge browser.

Does anyone actually care about privacy online?

---

### Post by DuckHook on 2019-04-08
> **TheFu said:**
> …Does anyone actually care about privacy online?
Thanks for the updates.

Short answer: no

Slightly more long-winded answer: those like you who value privacy keep their ear to the ground (like you just did with above warning) and have long since taken measures to preserve it. For the vast majority: don't know, don't care, can't be bothered to learn.

---

### Post by Rubi1200 on 2019-04-08
And using addons whether AdBlock, uBlock Origin, AdGuard etc. is essentially useless in this scenario?

---

### Post by huff2 on 2019-04-08
TheFu ... Thanks for the info. I really wish people took the time to understand internet basics like they intuitively know to lock their door, etc. To most people, it just isn't real until its physically in front of them. A shame.

---

### Post by TheFu on 2019-04-08
Facebook didn't encrypt their logins with https until the "[Wall-of-Sheep]("https://krebsonsecurity.com/tag/wall-of-sheep/")" showed up at security conferences.  Nobody was screaming about the issue until then.

An addon that shows this extra tracking, as discussed in post #1 is needed to make normal people see it, security people complain, and the companies performing the tracking "fix" their methods, and hopefully the W3C fix the standard to prevent this going forward.  But for the next 6-12 months, most people are screwed.

---

### Post by poorpockets-mcnewhold on 2019-04-09
> **Rubi1200 said:**
> And using addons whether AdBlock, uBlock Origin, AdGuard etc. is essentially useless in this scenario?
Well, all of those are mostly usefull too protect yourself against advertisement tracking and some other tracking methods in general.
However, choosing the right Adblocker can have it´s importance, as for example, Adblock and uBlock (The original, not the Origin one) had been supported by other companies and advertising companies to unblock some of their advertisement.
For personal privacy ethics, I´ll suggest either of those three following ones : uBlock Origin (The ultimate reference)
Adnauseam (Fork of uBlock Origin, having quite an interesting concept being it, by confusing your tracking data grabbed by trackers companies, making your data, completly useless by other companies)
Nano Adblocker (Again, a fork of uBlock Origin, being mostly praised for it´s experimental features, like features to block anti-blocker scripts)

---

### Post by poorpockets-mcnewhold on 2019-04-09
> **TheFu said:**
> Facebook didn't encrypt their logins with https until the "[Wall-of-Sheep]("https://krebsonsecurity.com/tag/wall-of-sheep/")" showed up at security conferences.  Nobody was screaming about the issue until then.

An addon that shows this extra tracking, as discussed in post #1 is needed to make normal people see it, security people complain, and the companies performing the tracking "fix" their methods, and hopefully the W3C fix the standard to prevent this going forward.  But for the next 6-12 months, most people are screwed.

> **huff2 said:**
> TheFu ... Thanks for the info. I really wish people took the time to understand internet basics like they intuitively know to lock their door, etc. To most people, it just isn't real until its physically in front of them. A shame.The major issue there, is that a lot of companies just has been able to people give up on their privacy, and it still make them in a psychology of [QUOTE=My mom by example]¨Who cares that they are consulting what i do on the internet, I’ve got nothing to hide, and you can’t do anything about that anyway.¨[/QUOTE] And despite the huge lot of Privacy news on different services and companies, and showing her how i´ve been able to protect my privacy, and in her case, how she can limit her (Because, combo Google,Facebook, amazon etc...) [https://www.privacytools.io](https://www.privacytools.io)

---

### Post by TheFu on 2019-04-09
Until there is a mandatory opt-in law, it won't get better.  
Opt-out is a failure.
If I don't want any of the top 500 tracking companies to track me, most want me to allow a cookie.  It needs to be the opposite.  If the cookie isn't installed, then they aren't allowed, legally, to track me.
Plus we need a way to get all the data they have on us, for free, 2x a year.  That's the law for credit reports here - 2x a year, free.  If there are any errors, we have the right to dispute them, since a bad credit report can impact interest rates paid and charged.

And why are Apple users shown slightly higher prices for the same stuff on Amazon and at other stores?  

The EFF put out a tool years ago [https://panopticlick.eff.org/](https://panopticlick.eff.org/) that will show how unique your browser is in the world. If I was in Australia, they'd be able to get mine down to 3 people anywhere in the country.  With just 1 more data point, they'd know exactly which of those 3 people I was.  To get it working, I had to enable javascript, which I generally don't do for normal browsing.

---

### Post by Rubi1200 on 2019-04-09
Unfortunately, I failed the test on 2 levels:

[https://prnt.sc/n9qe9m](https://prnt.sc/n9qe9m)

But it does say that I > have strong protection against Web tracking, though your software isn&#8217;t checking for Do Not Track policies.

How do I deal with the DNT policies?

---

### Post by TheFu on 2019-04-09
> **Rubi1200 said:**
> Unfortunately, I failed the test on 2 levels:

[https://prnt.sc/n9qe9m](https://prnt.sc/n9qe9m)

But it does say that I 

How do I deal with the DNT policies?

Nobody honors DNT. Nobody. Until it becomes the default in a webserver, nobody will. IMO.

Did you look at the fingerprint output? How unique was your browser? 1:5 or 1:250,000?  With javascript enabled, they can use timing techniques combined with other hardware aspects like battery levels on laptops and screen resolutions (plus about 30 other things), to pretty well nail your browser down, especially within a reverse Geo-IP lookup.  If you run inside a VM, not full screen, then the screen resolution will likely be funky/unique helping track you around the web no matter what else you do.

---

### Post by huff2 on 2019-04-09
TheFu - I've never known too much about the detailed technical HOW of being tracked and so forth. I've only ever worked with the details on a different level: who, what, when, where, maybe why. Any good tutorials out there you recommend or good sites to follow for news and latest developments?

---

### Post by DuckHook on 2019-04-09
> **TheFu said:**
> Nobody honors DNT. Nobody. Until it becomes the default in a webserver, nobody will. IMO.

Did you look at the fingerprint output? How unique was your browser? 1:5 or 1:250,000?  With javascript enabled, they can use timing techniques combined with other hardware aspects like battery levels on laptops and screen resolutions (plus about 30 other things), to pretty well nail your browser down, especially within a reverse Geo-IP lookup.  If you run inside a VM, not full screen, then the screen resolution will likely be funky/unique helping track you around the web no matter what else you do.
The results are indeed eye-opening.

I first tried it on my desktop FF which has Noscript enabled by default. Fingerprinting was pretty much useless. I'm well protected so long as I don't enable javascript for any site but those that I'm absolutely, positively sure that I trust not to track me.

Then I ran it on my tablet. The results came back "unique": in other words, out of all the users out there, it was child's play to pin my set of quanta down to precisely me and no one else.

Thanks for this tool (hitherto, I did not know it existed). It has now been added to my war chest.

---

### Post by Rubi1200 on 2019-04-10
@TheFu 

Fingerprinting; not encouraging I would say: [https://prnt.sc/n9v0x5](https://prnt.sc/n9v0x5)

But then I installed ScriptSafe (in addition to what I already had) and the test page just hangs. I assume this is because the scripts are being blocked?

Does this make me safer, more private?

---

### Post by TheFu on 2019-04-10
> **huff2 said:**
> TheFu - I've never known too much about the detailed technical HOW of being tracked and so forth. I've only ever worked with the details on a different level: who, what, when, where, maybe why. Any good tutorials out there you recommend or good sites to follow for news and latest developments?

I attend OpSec conferences.  Many post videos.  Join your local DefCon group.  There aren't any centralized places, because every security researcher basically posts their own stuff 6 months after they discover it.  IronGeek posts links to conference videos. He's been doing that for over a decade. Thousands of videos posted by now.

It is a mindset.  Instead of thinking about that you've heard someone doing, think about what **could** be done based on your knowledge of programming, OSes, networking and common sense.  If you can think of a method that something, like tracking, could be done, then rest assured, someone is doing it that way.  That "advertising cookie" that google ads to their browsers and all Android devices?  Why do you think they have it?  How might you make it useless?

Some common sense: If you don't want something to be known over the internet, then don't put it on the internet. Don't allow some app/program to take it from you.  The choice between convenience and privacy and security are yours to make.  Humans learn from herds many things. This has helped us to thrive, but when it comes to the internet, fewer than 500K people in the world really understand that the other 6B are asleep, giving away all their private data, being tagged with bells just like cows and sharks with gps tags in their fins.  They do this voluntarily.

Think about the underlying goal from the team providing any software. Be suspicious, regardless of what they claim. Very few organizations are doing things for world peace at their core. I like to think that more aren't trying to be evil, but we all know that data wants to be used for something.  These days, divorce lawyers first rule is to ask for google, facebook, and cell data to find embarrassing data for their clients.  People never realized that when a phone rings, that is just a kindness. The ringing isn't necessary. There isn't a physical switch anymore.

There are many, many, creepy companies selling tracking technologies in the open market. You and I have never heard of these companies.  Remember the "super cookie" that Verizon used?  [https://www.theverge.com/2016/3/7/11173010/verizon-supercookie-fine-1-3-million-fcc](https://www.theverge.com/2016/3/7/11173010/verizon-supercookie-fine-1-3-million-fcc)  - they were caught because they are big and didn't notify, not because they were tracking everyone.  1 sentence got added to their 45 page "privacy policy" to address the notification about the tracking.  They aren't alone in that solution.

---

### Post by huff2 on 2019-04-11
TheFU - Very nice post. Thank you for pointing me in the right direction. You've been helpful in other areas on these forums and I certainly appreciate that too.

---

### Post by #&amp;thj^% on 2019-04-11
How many of you seen this: Firefox users who have the content blocker uBlock Origin installed receive a permission prompt currently when uBlock Origin is updating.
"Ad-blockers are storing lists of elements they should block."
[https://www.ghacks.net/2019/03/27/why-ublock-origin-requests-to-store-unlimited-data-in-firefox/](https://www.ghacks.net/2019/03/27/why-ublock-origin-requests-to-store-unlimited-data-in-firefox/)
I had a friend send me a message that uBO was now a data-miner, I laughed a bit then showed him this by the Developer: [https://github.com/gorhill/uBlock/wiki/Can-you-trust-uBlock-Origin%3F](https://github.com/gorhill/uBlock/wiki/Can-you-trust-uBlock-Origin%3F)
But now days, TheFu is right, privacy is a fairytale now. (Just to much driven by money)

---

### Post by pogba65 on 2019-04-27
The best way to stay secure on internet these days is, Stop using the platforms which track like Facebook and also use Encryption to create a Encryption tunnel between your internet and the network you are connected with, so your ISP and other software's can track you and if they the data will be encrypted.

---

