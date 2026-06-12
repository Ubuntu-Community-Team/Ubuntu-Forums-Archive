---
title: "Confused over which web browser is most secure"
date: 2016-07-27
forum: Security
---

### Post by giga+bytes on 2016-07-27
My family is mostly familiar with Chrome from our Windows computers, but I do not like what I sometimes read about their data collection. Now that we are gradually switching to Ubuntu (solely Ubuntu computers, no Windows at all) I want to have the most secure computers possible, so I am trying to find out if we should change web browser. I have heard a lot of good things about Firefox, but I have also read about it being one of the less secure browsers (from antivirus forums and news articles) and the most attacked and hacked/infected of them all. From what I have seen Chrome is the most secure and best at patching vulnerabilities fast, with Chromium a little behind, and Firefox rated as much less secure than either and slow to fix vulnerabilities (saw a comment from a supposed expert claiming known vulnerabilities in Firefox went unpatched for many months or even years). Like I said, I am confused.

Getting away from all the main data-harvesting programs and services is my goal, but not if it means putting us at greater risk, so I could really use some expert clarification!

---

### Post by uNoubu8a on 2016-07-27
Hmmm, never read that Firefox is anymore unsecure than any of the other major browsers.  If there was a concern it wouldn't be the default in Ubuntu (and in many other distributions).

With sober and secure surfing habits and the correct plugins you will be as safe as anything.

---

### Post by TheFu on 2016-07-27
If you allow javascript, game over.
If you allow flash, game over.
If you allow java applets, game over.
If you allow page icons, game over. There have been viruses injected via page icons in Windows.
If you allow images ... er ... well, on Windows, game over. There have been viruses injected through image viewing.

So ... the most secure browser doesn't support any of those things.  **Lynx**.  Lynx is a great little browser, but won't win any awards for usability or working with all websites.

There isn't any absolute security.  Our choices and what we click matter more than anything else.  Security is about making the correct decision 10,000 times a day, without fail. If we fail (and we all do), then we hope the next level of protection will save us.  If that fails, we hope the next level of protection saves us.  

I won't use chrome. Just don't trust the largest advertising company in the world to NOT access private data displayed in their browser.  I do use chromium, but only for specific, trusted, financial websites and only when run in a separate container - away from other applications and without any direct access to permanent storage.  **Firejail** is how to accomplish that, but it isn't perfect either; just provides another layer of protection.  My day to day browser is firefox - with all the issues it has, but I disable javascript, java, flash, and remove all locally stored tracking objects nightly.  Also only allow session cookies and never allow 3rd party cookies.  With all this stuff disabled, the web is a very different place. Many websites don't work, which is fine. I don't need to visit them.  There are exceptions, of course. Each is taken into consideration carefully.  I stopped visiting lifehacker due to their abusive tracking and abusive javascript, IMHO. Basically, if there are more than 3 javascript sites required for a webpage to work, I don't need to visit it.

I use NoScript, but understand there is a serious flaw in the firefox addon architecture which makes any addon have the ability to see all data from all websites. Each isn't limited to just the viewing tab as we would hope. This is a serious flaw for all addons in firefox.  I get the feeling this aspect is very difficult to address without a nearly complete re-write and breaking all current addons. [http://arstechnica.com/security/2016/04/noscript-and-other-popular-firefox-add-ons-open-millions-to-new-attack/](http://arstechnica.com/security/2016/04/noscript-and-other-popular-firefox-add-ons-open-millions-to-new-attack/) has more accurate description of the issue. It is a big deal, IMHO.  Plus NoScript has a default white-list for certain advertisers. Be certain to check whether you want to leave those as allowed or not.

If you don't want to be tracked, check out this article: [http://blog.jdpfu.com/pages/hosts-for-security](http://blog.jdpfu.com/pages/hosts-for-security) - republished by lifehacker a few years ago. It is still valid and works. In fact, short of running your own DNS and blocking all the tracking on your home network that way, I don't see any other way to prevent internet tracking. If you ever leave the house and connect to the internet away from home, you'll still want the /etc/hosts file setup.  Be certain to block google, twitter, facebook, pineinterest, and all the other social networking sites which are tracking everyone, everywhere they go online.  You can still use google for search - just go their an anonymous proxy first ... like startpage.

Often, security is a trade-off between convenience and being secure. 

Oh ... and watch out using lastpast. They [had a web flaw which made it possible for any website to pretend to be any other website and capture the automatically filled in credentials]("https://labs.detectify.com/2016/07/27/how-i-made-lastpass-give-me-all-your-passwords/").  THAT specific bug was fixed, but ... how many others do they have in their javascript?  All programs have bugs. All of them.

---

### Post by &amp;KyT$0P# on 2016-07-27
The most secure web browser is [SeaMonkey]("http://www.seamonkey-project.org/") + [NoScript]("https://noscript.net/").  SeaMonkey is like Firefox minus certain "features" that have significant security and privacy concerns.  NoScript is a security suite that's explicitly designed for protecting against various attack scenarios on the Web.
However, some people find there to be a non-trivial learning curve in figuring this out.  As a user of SeaMonkey and NoScript, I can help you learn it and set it up to your tastes if you'd like to try it.

Second to this is probably Chromium, which is basically Chrome minus tracking and proprietary components.  Since you already know Chrome, you're already familiar with it and how to set it up securely, so I guess having Chromium would be the easy option for you.

Also, you can make any browser more secure using Firejail sandboxing (Firejail is available in the standard Ubuntu 16.04 package repositories).


Note: my assessment here is based mostly on personal experience.  I am not a security professional.
That being said, I've visited malicious sites before and I know for a fact that it is not luck that I have never had malware infection on my computer.

---

### Post by &amp;KyT$0P# on 2016-07-27
Oops, posting at the same time as TheFu.

> **TheFu said:**
> I use NoScript, but understand there is a serious flaw in the firefox addon architecture which makes any addon have the ability to see all data from all websites. Each isn't limited to just the viewing tab as we would hope. This is a serious flaw for all addons in firefox.  I get the feeling this aspect is very difficult to address without a nearly complete re-write and breaking all current addons. 
What you say here about Firefox addons is true but maybe it would be better not to follow it up with FUD.  Please see [this article]("https://hackademix.net/2016/04/08/crossfud-an-analysis-of-inflated-research-and-sloppy-reporting/") for an explanation.

> Plus NoScript has a default white-list for certain advertisers. Be certain to check whether you want to leave those as allowed or not.
This is the default whitelist in the current NoScript dev version (line-wrapped for readability):
```
about:blank about:pocket-signup about:pocket-saved addons.mozilla.org persona.org mozilla.net google.com gstatic.com ajax.googleapis.com
maps.googleapis.com paypal.com paypalobjects.com securecode.com securesuite.net firstdata.com firstdata.lv
yahoo.com yimg.com yahooapis.com youtube.com ytimg.com googlevideo.com
netflix.com nflxext.com nflximg.com nflxvideo.net noscript.net
hotmail.com passport.com passport.net passportimages.com live.com live.net outlook.com
afx.ms gfx.ms sfx.ms wlxrs.com
ajax.aspnetcdn.com bootstrapcdn.com code.jquery.com yandex.st tinymce.cachefly.net
```
Which of those sites do you consider as advertisers?

---

### Post by giga+bytes on 2016-07-27
@work-work: I would not have thought so either, but since I have read about it I figured I should ask, and it appears there might be some truth to it.

@TheFu & halogen2: Thanks for the quick replies and abundance of information and advice! Apparently I have at least been *partially* protecting my family. Also, I forgot to mention I am using Ubuntu 14.04, if that makes any difference.

So there is Firefox with modifications, SeaMonkey which is based on it, and Chromium. Chromium would seem to be the ideal choice as it is basically the same as what we are familiar with, but TheFu does not seem that trusting of it, and said nothing about SeaMonkey. I would like to know more about your opinions of these 3 choices, if you do not mind.

Edit: Why do I not see that post about NoScript and the Firefox flaw by TheFu that halogen2 just posted about? I have noticed this kind of thing before, and do not know the reason.

Anyways, sounds like maybe I should take Firefox off the list. That flaw will only nag at me otherwise.

---

### Post by &amp;KyT$0P# on 2016-07-27
> **giga+bytes said:**
> So there is Firefox with modifications, SeaMonkey which is based on it, and Chromium. Chromium would seem to be the ideal choice as it is basically the same as what we are familiar with, but TheFu does not seem that trusting of it, and said nothing about SeaMonkey. I would like to know more about your opinions of these 3 choices, if you do not mind.
A friend and I had tried to make a custom Firefox build removing just ONE dubious "feature", and it took days of fighting weird issues before we got anything that was even minimally usable.  So Firefox is certainly not an option for the average user looking for real security or privacy.

SeaMonkey, like Firefox, is powered by the Gecko engine.  And Gecko's extensions system is currently by far the most powerful of all browser engines, thus there is the most possibility of getting good security.  In fact, the disparity is so large that it is not even technically possible for NoScript to be ported to other browser engines, simply because they don't offer enough functionality to extensions.
Plus, SeaMonkey being a volunteer project where the developers are all users, it focuses as much as possible on what the users need and want, not what some single entity decides is "best" :roll:.
So I recommend SeaMonkey, because it offers the greatest capability to protect you.

The Chromium available in the Ubuntu packages is open-source software designed by Google and compiled by Canonical, so how trusting of it you should be depends mostly on how trusting you are of Google.  No one can decide for you.
That's my opinion from a security perspective.  As far as privacy perspective, well, keep in mind that Google is in the business of data-mining...

> Edit: Why do I not see that post about NoScript and the Firefox flaw by TheFu that halogen2 just posted about?
TheFu edited it in the middle of their existing post after the fact, and I didn't see TheFu's post right away.  It's still there.

> That flaw will only nag at me otherwise.
It's not a flaw.  It's by design.  All extensions are deliberately given the same privileges as the browser itself, thus they have the same privileges as every other extension.
As long as you don't install any malicious extensions, there is nothing to be concerned about.

Again, please see the article I linked above for more information on why this really isn't a problem.

---

### Post by Bucky Ball on 2016-07-28
VPN through Tor. Not sure it can get much more secure than that without being impractical for day to day, average computer users. And I found that sluggishly slow and impractical for my day to day use. Your other option is running a virtual machine in Virtualbox. Very secure, but as you have a number of users, also impractical. 

Personally, I use Firefox with UBlock Origin, duckduckgo as search engine most of the time and that is it. I've used other addons in the past (NoScript which I found just got in the way). Never had an issue but I'm very careful where I click. Just lately I've set up a basic Kubuntu virtual machine to play with and I have been using that more and more for web surfing, banking and paying bills and the like. 

You should consider emails of equal, if not more, concern. A casual click on an unsolicited email or attachment there and, to use TheFu's terminology, game over.

Internet security is as much about education as anything else, IMHO. Make sure all users are aware they should not be randomly clicking on anything. You might have some protection when surfing the net with Ubuntu when it comes to that, but forget it when it comes to emails, regardless of OS.

---

### Post by &amp;KyT$0P# on 2016-07-28
I'm getting concerned that we're conflating privacy and security here.

Privacy and security are orthogonal.  Sometimes privacy and security go hand-in-hand, other times it's a trade-off between privacy and security.  For example -

> **Bucky Ball said:**
> VPN through Tor. 
Tor is great for privacy but terrible for security.  Too much chances of malicious node compromising everything you do.  I don't like security that depends on a lottery.

> Personally, I use Firefox with UBlock Origin, duckduckgo as search engine most of the time and that is it. I've used other addons in the past (NoScript which I found just got in the way).
+1 to the recommendation of uBlock Origin, it's a great addon and I use it next to NoScript.  But keep in mind that uBlock Origin provides completely different type of protection from NoScript.  Mostly it's useful for privacy, but it can be a useful supplement to other type of security if you add subscriptions like Malware Domains.

uBlock Origin is a blacklist-based approach - if you're relying exclusively on uBlock Origin for security, you're relying on not encountering any not-yet-known threat sources.  Again, depending security on a lottery.
Also, uBlock Origin doesn't have the specialised threat protection of NoScript such as XSS filtering, router hijacking prevention, and MIME enforcement.  So NoScript is needed anyway for full security.

Also, to note, uBlock Origin is available for Chromium as well as Firefox & SeaMonkey.  Whichever browser you choose, I'd say uBlock Origin is definitely worthwhile.

---

### Post by TheFu on 2016-07-28
Good discussions here.

Yes, I edited a previous reply. If I don't guess the OP has already read the thread, I'll often edit posts. Sometimes I get it wrong. Never believe the emailed updates about a post. Those are almost always updated online, IME.

I also use uBlock Origin.  Blocking ads is a necessary step for security these days. Ad networks are most interested in "views", "impressions", and "clicks."  Security is an afterthought for those marketing companies.

XSS filtering is good, but all software has bugs. Nothing is 100%. We need to be cautious.  Plus, all the included javascript from 20 different companies has to be self-contained, bug-free, AND work together with whatever the main company puts out - or 500 companies put out without knowing what they will publish in advance. It is amazing there aren't more issues, bugs, crashes of browsers. 

TOR is for privacy. Nothing else. Plus, if you need 100% privacy, using TOR isn't enough. Every week, we learn about some bug in a tool that was "trusted" with an important flaw that was just fixed.  How many months, years, decades did that flaw exist and for how long was it exploited without anyone knowing?  Governments are capturing as much encrypted traffic as they can and storing it for later analysis when decrypting it will be possible. I try to use encryption and key lengths that will last 50 yrs from today. Figuring that by then, I won't care if the data is decrypted. ;)  Even if I'm off 50% (which is likely!), 25 yrs isn't too bad either.

If you care about security, use **Lynx** as your browser.  Nobody tries to hack lynx and it ignores so much from the web that only basic text gets thru.  

I know people that use **dillo** as their main, simple, browser, but it has critical flaws.  It doesn't authenticate SSL certs [http://www.dillo.org/FAQ.html](http://www.dillo.org/FAQ.html).  Sorta important, don't you think?

I'm considering my browser policy again now.  Think using chromium inside firejail will continue to be my "secure" browser choice when I have to allow high-risk features like javascript, cookies, html5. The use is very limited.

There is a Linux distro which takes compartmentalization to a new level - Qubes [https://www.qubes-os.org/](https://www.qubes-os.org/) .  Basically, they put all applications into separate workspaces (which are really just VMs).  I use VMs all the time - constantly actually, but they aren't foolproof. They are just another layer of security, but even proven VM hypervisors have been found to have old, buggy, code that was abused. How many layers do you need?  That's a personal decision and your risk factors will guide it.  If I spent all day doing risky things online, I'd dedicate a physical machine for it and add another segment to my network which appears like it is outside all my firewalls, basically, on the internet.  For the really paranoid, consider these steps:
a) Run Qubes as the base OS. You can probably use Ubuntu with KVM and virt-manager, but it won't be as seamless. The WAF will be low.
b) Put the browser into a private workspace (separate VM) just for the browser
c) Run firejail in --private mode with the browser of your choice.  Firejail provides access to Linux containers which are more than sandboxes, but not quite full VMs.  Containers have multiple layers to "contain" processes and try to prevent those from escaping to interfere with other processes. They aren't perfect; just another layer.
d) No not use this workspace for anything else. Be very careful about copy/paste between any different workspaces on Qubes.

Anyway, that's what I'd do.  Hopefully, it isn't too much babble and coherent thoughts.

Oops - forgot to say which of those things I consider advertisers. Sorry.  google definitely is. Yahoo is. All the Microsoft stuff is too. Actaully, all of them except bootstrapcdn.com code.jquery.com are advertisers.

---

### Post by &amp;KyT$0P# on 2016-07-28
> **TheFu said:**
> c) Run firejail in --private mode with the browser of your choice.  
The option [FONT=Courier New]--overlay-tmpfs[/FONT] (requires Ubuntu 14.04 or better) is also fun :D

> **TheFu said:**
> Oops - forgot to say which of those things I consider advertisers. Sorry.  google definitely is. Yahoo is. All the Microsoft stuff is too. Actaully, all of them except bootstrapcdn.com code.jquery.com are advertisers.
Ok, if you put it that way (thinking only in terms of owners rather than exact domains) I'm glad I asked, I fully agree with this assessment from a privacy perspective.  Thanks.

[This FAQ]("https://noscript.net/faq#qa1_5") explains the reasoning behind the default-whitelisted items.  To reiterate: if you care about privacy and want to use NoScript, you would be best off to evaluate all the sites on the default whitelist and remove anything you don't absolutely need - because, again, much of those sites are operated by advertisers.

---

### Post by QDR06VV9 on 2016-07-28
Thanks TheFu! I always gain valuable info in your detailed posts.
I for one would miss these...and wanted you to know.
Regards

---

### Post by giga+bytes on 2016-07-28
This thread has turned out to be terrific! Lots of facts and options, no arguments and some laughs!

I currently have uBlock Origin on the laptop, though I may not have it configured ideally. It has been mentioned by members of the family that they like how it blocks a lot of ads that had previously annoyed them, so that is a good sign. I had been under the impression that uBlock Origin and NoScript are basically the same, so only one is needed, but apparently I was mislead. Now I know better!

I am going to have to read over this a couple times to fully understand, but I think I have a general idea of what I am looking for now. With SeaMonkey + NoScript + uBlock Origin, will I still be able to shop at my main online vendors? That would be Amazon and Newegg mostly. If so, I think that combination is a good starting point for me, then when I get familiar enough with these 3 I can add an extra layer or two (as TheFu put it) if I want or feel the need. Sound good to all of you?

---

### Post by giga+bytes on 2016-07-28
Also, I noticed SeaMonkey is an all-in-one suite with email. This may be better starting another thread for, but is that email equally recommended over most of the competition? I currently use hotmail/outlook, and am looking to change that too if possible. I have read before that all-in-one suites tend to have one or two features they concentrate their efforts on while the rest of the included features are typically substandard, so am curious is this may be different?

---

### Post by QDR06VV9 on 2016-07-28
I flat love my seamonkey...and as halogen2 I run it in a Sandbox (Firejail) if you do a search in the forums you should see a couple of ways to install Seamonkey.

---

### Post by &amp;KyT$0P# on 2016-07-28
> **giga+bytes said:**
>  With SeaMonkey + NoScript + uBlock Origin, will I still be able to shop at my main online vendors? That would be Amazon and Newegg mostly. 
Well, last I checked, Amazon can be made to work without much effort, and doesn't require tweaking settings all the time once it's set up to work.

Other shopping sites might be more problematic, I don't know.  So here are some generic DOs and DON'Ts for maximizing reliability of shopping online with that setup:
 - DO completely quit, and restart, the browser before visiting any shopping sites.  Same after you're done.
 - DO temporarily set NoScript in Allow Scripts Globally mode, so that it has the least chance of interfering with a payment (you trust the people you're paying your money to, don't you? ;) )
 - DON'T visit other sites in the same browser session as where you're doing the shopping
 - DON'T necessarily use as restrictive a uBlock Origin configuration when shopping as otherwise (keep only filter lists such as Malware Domains, disable all others - for more information see [here]("https://easylist.to/2010/10/29/filter-subscriptions-and-important-internet-transactions.html") and [here]("https://easylist.to/2011/06/09/cashback-schemes-and-easyprivacy.html"))
 - And of course, DO remember to revert shopping-related changes to NoScript settings and uBlock Origin settings before going back to normal browsing the Internet.

I think that should be enough to ensure that a shopping site works.  If the site is still being blocked, it might be unsafe to use...

---

### Post by giga+bytes on 2016-07-28
@runrickus: thanks for the extra thumbs-up for SeaMonkey, and the tips!

@halogen2: I will keep that list in mind. Well that pretty much settles it then: when I have my build finished I will take you up on your offer, in post #4, for assistance setting these 3 up. I will try it for a while and see how it goes and what I think of it.

Thanks for all the help everyone!

---

### Post by TheFu on 2016-07-28
> **giga+bytes said:**
> This thread has turned out to be terrific! Lots of facts and options, no arguments and some laughs!

I currently have uBlock Origin on the laptop, though I may not have it configured ideally. It has been mentioned by members of the family that they like how it blocks a lot of ads that had previously annoyed them, so that is a good sign. I had been under the impression that uBlock Origin and NoScript are basically the same, so only one is needed, but apparently I was mislead. Now I know better!

I am going to have to read over this a couple times to fully understand, but I think I have a general idea of what I am looking for now. With SeaMonkey + NoScript + uBlock Origin, will I still be able to shop at my main online vendors? That would be Amazon and Newegg mostly. If so, I think that combination is a good starting point for me, then when I get familiar enough with these 3 I can add an extra layer or two (as TheFu put it) if I want or feel the need. Sound good to all of you?

There isn't a one-size-fits-all solution.  Perhaps using different browsers for different purposes would make the most sense?  Think about risk levels:
* High - banking, brokerage, paypay, legal stuff - where you need all the defaults and probably want ZERO blocking.
* Medium - trusted sites - newegg, amazon, netflix, apple - sites where you have a financial interest in the relationship - you PAY THEM.
* Low - social networks. Places who sell your information to make a profit.  Google, Microsoft, Yahoo, Facebrace, tweeter, any "news" site, places you don't pay.
* Underbelly - the places you should never visit.  Anywhere your kids go.  redtube, school websites, places you don't want any trace left on the computer that you were ever there and don't want the ability to download anything from.

Your list of trusted, important, underbelly are probably different from mine. The hard part is being vigilant about these different levels.  Using different browsers can serve as a reminder.  

Why are the kids places _underbelly_?  All the kids I know have virii all over their systems.  In fact, if their parents are on the same subnet, those virii get passed over to their PCs too.  If you can, put the kids devices/PCs on their own subnet. This will make *incentives* easier to apply to them as well when internet can be removed as you like without impacting your internet.

Basically, treat high and underbelly the same - actually I do. Both get run inside firejail with --private mode which uses the tmpfs overlays so nothing will actually be written to disk - no bookmarks, no cookies, no local objects, no settings. The browser appears to be pristine and new. I start the container, do what I need to do, shut down the container. Both levels have risks and I'd rather not have any record of visiting either. Just never do it in the same session. Would be smart to use different userids as well (which I don't do today).

Medium and Low are probably where ad-blocking and selectively preventing javascript are most important. These are where multi-session and 3rd party cookies become convenient, but we should probably block them along with local-objects from flash and html5.  It is a hard thing to decide and harder to implement. I struggle myself with this level.

Doing 2 levels becomes second nature.  For other users, having 1 that is paranoid might be best. I dunno.

---

### Post by giga+bytes on 2016-07-28
Point taken, thanks for the reminder! But.. I am unsure what you mean by banking and such being high risk level, while social networks are low risk level? Should they not be the opposite? Or do you mean that banking information is a serious problem if compromised, while the information from social networks are not so vital so not as serious a problem if compromised?

For now I am just going to try this new combination for a while to see how it might fare with everyone else in the house, and what areas of our online activity it is best suited for. Then I will revisit this thread to re-read and figure out what might be ideal for a second browser for the rest of our online activity, as you suggest. I have a lot to learn at once for now (Ubuntu, new browser, security add-ons/extensions).

---

### Post by Bucky Ball on 2016-07-28
I don't mind if someone steals my Facebook identity (if I had one) or some other identity on a social networking site. A hassle, yes, but I do care *much* more if someone steals my banking details. There is a BIG difference and if you're divulging things during social networking you don't want others to know or that could threaten your machine's computer it's time to you re-think what you divulge on social networks. :)

One of the reasons I've been banking on a virtual machine. If I'm wanting to use the forums, on the other hand, doesn't really make any diff to me. When you're banking you have no choice but to give out sensitive information. When you're social networking you have a choice regarding what information you share. 

I use Thunderbird for email.

---

### Post by uNoubu8a on 2016-07-28
Have a look at [QubesOS]("https://www.qubes-os.org/").

---

### Post by yoshii on 2016-07-29
firefox has it's issues but so do chrome and chromium.  i forget which one it was, but there was a security study done of one of the chrom*s vs firefox and it found that the SSL certificate blacklisting only blacklisted about a dozen sites total instead of dynamically allocating more blocks to hundreds of malware sites.  but I still can't figure out why firefox installs certificates which have already expired.  i tried deleting the old ones, but then i couldn't get into some of the sites i need using https, including this one.  it's so dumb.

---

### Post by giga+bytes on 2016-07-31
@work-work: Qubes does look promising. I may consider trying it sometime, depending how things go with what I have chosen for now. Thanks for pointing it out!

@yoshii: Beats me, browsers and such is not my area of tech expertise. I would like to know the reason for what you describe, though, so I know that much more about this stuff.

---

