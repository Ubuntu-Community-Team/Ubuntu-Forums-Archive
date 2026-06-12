---
title: "Noscript is not enough!"
date: 2009-09-27
forum: The Cafe
---

### Post by Xbehave on 2009-09-27
So recently (or not so recently depending on how fast posts get moderated around here (I've been a :twisted:bad:twisted: boy)) reddit was hit by a javascript attack that made its own readers (a relativly tech informed crowd) attackers, many like myself use noscript to prevent this kind of thing.

Unfortunately NoScript comes from a broken way of thinking, "you can identify attacking sites and trusted sites", the attack code for this was coming from reddit.com (a site you have to allow in order to use reddit). The only way this sort of bug can be protected against is by use of javascript filtering tools such as controldescripts that filter javascript request by type and domain, with such a tool it would be possible to protect yourself much more effectively.

using such tools complex rulesets could do something like this:
mouseclick is submitting info -> allow
mouseover is requesting data -> allow
mouseover is submitting data -> request user confirmation
javascript function is doing something weird -> request user confirmation 
javascript is trying to use a known exploit* -> deny and notify user
...etc

You could also combine this with domain checking to have lists of pages where you allow 
[LIST]
[*]no-js (untrusted), 
[*]simple-JS (google, youtube, etc) but [it might allow functionality but could prevent tracking], 
[*]complex-js (facebook, etc) [all the ajax stuff means simple-JS wouldn't work]
[*]all-JS (fancynewsite.com) [even the complex list of functions you allow just isn't enough]
[/LIST]
such tools could also help the paranoid among us use website that require JS while disabling mousetracking and sending of data on non-click actions.

*rulesets could significantly reduce the impact of 0-days

Why am i posting here? Well I've been saying this stuff to anybody that will listen for a while, but now reddit (a fairly big tech orientated site has been hit and no-script sat idly by) so maybe somebody might listen.
Why am I not using it myself if I'm so clever? I'm not and i know very little about JS so my attempts at rule-sets were useless!

---

### Post by kevdog on 2009-09-28
Off topic but I hate reddit

---

### Post by coldReactive on 2009-09-28
Extensions are mainly open-source, have you thought of making a fork?

---

### Post by -grubby on 2009-09-28
You may wish to contact the maintainer of NoScript about this.

---

### Post by Xbehave on 2009-09-28
> Extensions are mainly open-source, have you thought of making a fork? 
I think i addressed this with:
> Why am I not using it myself if I'm so clever? I'm not and i know very little about JS so my attempts at rule-sets were useless!
This makes my chances of making the extension (which AFAIK are mainly written in JS) and the rulesets next to nil. I think the extension is pretty much already there in the form of [control de scripts]("http://controledescripts.mozdev.org/help/welcome.xhtml") but I don't know enough about JS to make useful rulesets. I also don't think its possible to do automatic per domain stuff (like noscripts allow TLD by deafult)

---

### Post by kirsis on 2009-09-28
You repeatedly imply that somehow "tech oriented crowds" are supposed to be insusceptible to JavaScript XSS annoyances. Being "tech oriented" does not mean one will start avoiding JavaScript. 

I for one have always considered such extensions to be too paranoid already.

---

### Post by doas777 on 2009-09-28
ghostery will at least show you the domains behind the site you are on. yeah, if a site has XSS wholes in it, it is stupid to allow it in noscripts. thats a no-brainer. if you allow somthing, then you have...well...allowed it.

---

### Post by jrusso2 on 2009-09-28
Thanks for the information.

---

### Post by Xbehave on 2009-09-28
> **doas777 said:**
> ghostery will at least show you the domains behind the site you are on. yeah, if a site has XSS *holes* in it, it is stupid to allow it in noscripts. thats a no-brainer. if you allow somthing, then you have...well...allowed it.The problem is without access to a websites source code and detailed knowledge of the language they use its  impossible to tell if a website is vulnerable to XSS until it gets hit. 

> You repeatedly imply that somehow "tech oriented crowds" are supposed to be insusceptible to JavaScript XSS annoyances. Being "tech oriented" does not mean one will start avoiding JavaScript. My point is that in the past those seeking security turned to tools like noscript to defend themselves against the [evils code]("http://www.milw0rm.com/search.php") on the internet, which does not provide nearly as much protection as they assume, but does make general web browsing much more difficult. "Tech oriented" people are likely to want the option of browsing securely, noscript is not the right tool for this.

---

### Post by FunkyRes on 2009-09-28
NoScript is an excellent tool.
If you allow a site it generally allows any script from that domain (though it does do some blocking) but it does not guarantee XSS security. It is one of many technologies that help.

My browser crashes far less often with NoScript enabled, it's worth it to me just for that.

---

### Post by handy on 2009-09-28
In the past I have read on the TOR site, their recommendations for people not to use NoScript.  As they considered it too complex, & in their view, most people would be doing themselves more harm than good by using NoScript.

That was some time ago, perhaps NoScript has developed beyond that complexity & become easier for people to set up correctly?  I don't know. 

I just use Privoxy on IPCop & manually accept or reject every cookie I'm offered; all with java/javaScript turned on. I also use Scroogle to search the web, which I believe protects my personally identifiable data from Google's monstrous & ever growing database.

---

### Post by Pogeymanz on 2009-09-28
> **handy said:**
> In the past I have read on the TOR site, their recommendations for people not to use NoScript.  As they considered it too complex, & in their view, most people would be doing themselves more harm than good by using NoScript.

That was some time ago, perhaps NoScript has developed beyond that complexity & become easier for people to set up correctly?  I don't know. 

I just use Privoxy on IPCop & manually accept or reject every cookie I'm offered; all with java/javaScript turned on. I also use Scroogle to search the web, which I believe protects my personally identifiable data from Google's monstrous & ever growing database.

You use privoxy all the time? How does that affect your browsing speed?

I use NoScript and manually accept/reject cookies and also use scroogle.

---

### Post by handy on 2009-09-28
> **Pogeymanz said:**
> You use privoxy all the time? How does that affect your browsing speed?

I use NoScript and manually accept/reject cookies and also use scroogle.

I had used Privoxy on various desktops in the past, & there was a quite noticeable speed penalty.

I have been using Privoxy via the Copfilter, IPCop add-on, which brings brilliant Privoxy configuration scripts & (most importantly) because it is running on the headless IPCop firewall/router, it does not slow our internet down.  I don't really understand why there is no speed penalty running Privoxy this way, but that is how it is, & yes Privoxy is doing its job, very well.

If you are interested have a look at the IPCop website?  It is really quite quick & easy to set up, (depending on your background knowledge) & an old PII with 256MB RAM & 8GB HDD is all you need.  I'm using a PIII Dell Optiplex from the local tip, it cost me $5-.

Once installed you do other configuration & observation via a browser from a client.

[I]**[Edit:]**  Here is a link or two that should quickly expand your understanding of IPCop:

[http://ubuntuforums.org/showpost.php?p=6303994&postcount=29](http://ubuntuforums.org/showpost.php?p=6303994&postcount=29)

This page has the story & useful links in it:

[http://ubuntuforums.org/showthread.php?t=1005192](http://ubuntuforums.org/showthread.php?t=1005192)[/I]

---

### Post by aysiu on 2009-09-28
Do you define *enough* as making your computer invincible? If so, then obviously nothing is "enough."

But if *enough* means protection against 99.9% of browser exploits (present and future), then NoScript is enough... probably more than enough.

There is no such thing as invincibility or absolute security. There are, however, best practices and good balances between usability and security.

---

### Post by Xbehave on 2009-09-28
> **aysiu said:**
> But if *enough* means protection against 99.9% of browser exploits (present and future), then NoScript is enough... probably more than enough.
Actual My point is it provides very little actual security because its very hard to judge if a website is safe or not. Malicious sites do not give you a warning and non-malicious sites often get exploited! It's much better to allow a safe subset of JS to operate on most sites than 0 or 100% depending on if you trust the domain.

---

### Post by aysiu on 2009-09-28
> **Xbehave said:**
> Actual My point is it provides very little actual security because its very hard to judge if a website is safe or not. It gives you a choice to decide after you've visited the site. No pop-up is going to surprise me before I even realize it.

Someone who just whitelists everything is obviously going to get no protection from it. It's a tool, and the tool has to be used properly. But for those of us who do use it properly, it allows you to enable JavaScript functionality only when it is needed.

There are plenty of sites I "trust" that I visit often... that are also still not whitelisted on NoScript. Why? Because I had no need to whitelist them. JavaScript (or Flash, or whatever else) is unnecessary to those sites' functionalities.

And many sites contain other websites' embedded stuff (Flash animation ads). So even if ad.doubleclick.net gets compromised, at least you only whitelisted abc.com. If abc.com gets compromised, well, then you're screwed, of course. But that doesn't mean NoScript has no use.

If you assume that even trusted websites will get compromised, then the only safe thing to do is not visit any websites.

---

### Post by Xbehave on 2009-09-28
It is a PITA to go round whitelisting ever site before you use it (even if its just temp) and how on can you tell if a site is trust worthy without manually inspecting every site you go to's code?

> **aysiu said:**
> If you assume that even trusted websites will get compromised, then the only safe thing to do is not visit any websites.
No my point is that for sites that only use simple JS, e.g ubuntuforums, reddit, etc (i suspect 90% of sites use at most simple JS) you can allow just a subset of JS that is safe, so when they get exploited they can't do any damage or exploit any holes in your browser! 

Think of it like only giving a user rbash because its enough for their work while protecting you from potential holes in bash or the kernel settings to execute only safe  untrusted bytecode. The practice of using safe subsets when you can is well established and much more effective in real world use than yes/no choices.

---

