---
title: "NoScript on Firefox?"
date: 2014-12-11
forum: Security
---

### Post by Daveski17 on 2014-12-11
Does anyone use the NoScript Security Suite extension by Giorgio Maone on Firefox (or SeaMonkey)? If so, what are the security advantages in Ubuntu? Does anyone believe it to be unnecessary on Linux?

[https://addons.mozilla.org/en-US/firefox/addon/noscript/?src=hp-dl-mostpopular](https://addons.mozilla.org/en-US/firefox/addon/noscript/?src=hp-dl-mostpopular)

---

### Post by TheFu on 2014-12-11
I run it.
The same advantages apply to Linux as to other OSes.
I believe it is necessary, but can be inconvenient.

---

### Post by Daveski17 on 2014-12-11
> **TheFu said:**
> I run it.
The same advantages apply to Linux as to other OSes.
I believe it is necessary, but can be inconvenient.

Yes, I tend to agree, but some have argued that it isn't necessary for Linux as a user can't normally run as root. I'm just curious.

---

### Post by tgalati4 on 2014-12-12
It can make pages run much faster by disabling javascript code that you don't want running.  You need to get used to staring at broken pages until you "allow" some javascript code to run from the primary website that you put in the URL.  For instance, "google-analytics" is on just about every website.  You may not want your browsing habits sent to google every time you click on a link.

---

### Post by pqwoerituytrueiwoq on 2014-12-12
I use it, thought i keep a second browser around for when i don't have time to deal with it (IE my dad is rushing me to get X done for him) on one time use websites

---

### Post by PondPuppy on 2014-12-12
I use it on Firefox, and have for donkey's years. 

I think that Javascript is used maliciously in a few different ways -- to probe for vulnerabilities, eg, unpatched Adobe, Flash, or Java packages; to attempt to load malware or trick the user into downloading it; and to implement browser hijacks. Most exploits and most malware will be tailored for Windows machines. But browser hijacks can be cross-platform, I believe.

I find that blocking Javascript speeds up page loading, and it's especially noticeable on a low-powered tablet or on a slow internet connection. 

For what it's worth.

----

Oh, and I also use a second browser with Javascript enabled,  for sites I trust -- like this one.

---

### Post by Daveski17 on 2014-12-13
> **tgalati4 said:**
> It can make pages run much faster by disabling javascript code that you don't want running.  You need to get used to staring at broken pages until you "allow" some javascript code to run from the primary website that you put in the URL.  For instance, "google-analytics" is on just about every website.  You may not want your browsing habits sent to google every time you click on a link.

It can certainly speed things up, I know many find NS a bit of a pain in the **** to use, but it is also good to have that control over individual scripts running on a page.

> **pqwoerituytrueiwoq said:**
> I use it, thought i keep a second browser around for when i don't have time to deal with it (IE my dad is rushing me to get X done for him) on one time use websites

So you think it benefits Firefox's security? What is your secondary browser, if you don't mind me asking? I use Chromium on Ubuntu as a back-up for Firefox.

> **PondPuppy said:**
> I use it on Firefox, and have for donkey's years. 

I think that Javascript is used maliciously in a few different ways -- to probe for vulnerabilities, eg, unpatched Adobe, Flash, or Java packages; to attempt to load malware or trick the user into downloading it; and to implement browser hijacks. Most exploits and most malware will be tailored for Windows machines. But browser hijacks can be cross-platform, I believe.

I find that blocking Javascript speeds up page loading, and it's especially noticeable on a low-powered tablet or on a slow internet connection. 

For what it's worth.

----

Oh, and I also use a second browser with Javascript enabled,  for sites I trust -- like this one.

Yes, I've used it on Windows for years. What I was trying to ascertain though was its efficacy on Ubuntu. Some people claim it is effectively redundant on Linux as an operating system because Linux is inherently safer and more secure. Personally, I use it on Ubuntu myself.

---

### Post by coldraven on 2014-12-13
I use NoScript **and** Ghostery. Ghostery is set to block all trackers, widgets etc. When a site won't work I let Noscript "temporarily allow all of this page". 
It is then amazing to see how many trackers pop-up in the Ghostery panel. Some sites have 20 or more of the little beasts.
Install the Lightbeam add-on to see how your data is shared between multiple marketing companies. 
I also use the BetterPrivacy add-on to delete Adobe Flash "Super cookies".
Me, paranoid? No but these dubious companies will track you even if you do not allow tracking. So I make it difficult for them.

---

### Post by open2reason on 2014-12-13
Yes, I use Noscript to examine which scripts seek permission to run and RequestPolicy to see what sites the page wishes to link with / load. BetterPrivacy also has a place when removing tracking information planted on your machine.

May I suggest visiting theguardian.com newspaper site after loading NowScript & RequestPolicy, it is Instructive to say the least to view which third-party and other sites are fighting for control of your browser.

---

### Post by Daveski17 on 2014-12-13
> **coldraven said:**
> I use NoScript **and** Ghostery. Ghostery is set to block all trackers, widgets etc. When a site won't work I let Noscript "temporarily allow all of this page". 
It is then amazing to see how many trackers pop-up in the Ghostery panel. Some sites have 20 or more of the little beasts.
Install the Lightbeam add-on to see how your data is shared between multiple marketing companies. 
I also use the BetterPrivacy add-on to delete Adobe Flash "Super cookies".
Me, paranoid? No but these dubious companies will track you even if you do not allow tracking. So I make it difficult for them.

I used Ghostery a few years ago, but I thought it was getting over-complex. Lightbeam is very interesting but I uninstalled it after a Firefox update when it started to cause problems. I'm concerned about tracking, but I really wanted to establish what security benefits NoScript brought to Linux.

> **open2reason said:**
> Yes, I use Noscript to examine which scripts seek permission to run and RequestPolicy to see what sites the page wishes to link with / load. BetterPrivacy also has a place when removing tracking information planted on your machine.

May I suggest visiting theguardian.com newspaper site after loading NowScript & RequestPolicy, it is Instructive to say the least to view which third-party and other sites are fighting for control of your browser.

I thought RequestPolicy wasn't being developed anymore. I used it on SeaMonkey a couple of years ago. I found this however:

[https://requestpolicycontinued.github.io/](https://requestpolicycontinued.github.io/)

I agree with you about The Guardian! lol

---

### Post by open2reason on 2014-12-13
^^ Many thanks. You have taught one old dog one new trick today:p

---

### Post by Daveski17 on 2014-12-13
> **open2reason said:**
> ^^ Many thanks. You have taught one old dog one new trick today:p

You're welcome.

---

### Post by bashiergui on 2014-12-14
> **Daveski17 said:**
>  I'm concerned about tracking, but I really wanted to establish what security benefits NoScript brought to Linux.Javascript exploits don't care if you're running linux or not. In some ways linux users are *more* at risk if they falsely believe linux makes them more secure.

The Noscripts site does a good job enumerating its security benefits. It blocks malicious and privacy-busting scripts, xss, click-jacking. Also read about ABE.
[https://noscript.net/faq](https://noscript.net/faq)

---

### Post by raiford on 2014-12-14
As I understand it, Application Boundaries Enforcer (ABE) actually protects SOHO routers from remote exploits. A remote attacker would have to bounce their requests off a machine inside the LAN to compromise the router, basically, and NoScript prevents that. And that's just the tip of the iceberg when it comes to ABE. So using NoScript not only protects your machine from browser-based exploits, it can make your entire LAN more secure.

---

### Post by Daveski17 on 2014-12-14
> **bashiergui said:**
> Javascript exploits don't care if you're running linux or not. In some ways linux users are *more* at risk if they falsely believe linux makes them more secure.

The Noscripts site does a good job enumerating its security benefits. It blocks malicious and privacy-busting scripts, xss, click-jacking. Also read about ABE.
[https://noscript.net/faq](https://noscript.net/faq)

OK thanks, I understand its use on Windows, but I agree with you and believe it can be a useful security option on Linux.

> **raiford said:**
> As I understand it, Application Boundaries Enforcer (ABE) actually protects SOHO routers from remote exploits. A remote attacker would have to bounce their requests off a machine inside the LAN to compromise the router, basically, and NoScript prevents that. And that's just the tip of the iceberg when it comes to ABE. So using NoScript not only protects your machine from browser-based exploits, it can make your entire LAN more secure.

Thanks, that's interesting.

---

### Post by kevdog on 2014-12-15
Use it on Windows, do not on Linux.  I don't have a good explanation.  I somehow find it to be a major pain in the *** a lot.  Not sure why.  Even when I choose to allow of this page, I need to select this option more than once.  I'm not sure if this is how it was designed or I'm doing something wrong.

---

### Post by pqwoerituytrueiwoq on 2014-12-15
> **Daveski17 said:**
> So you think it benefits Firefox's security? What is your secondary browser, if you don't mind me asking? I use Chromium on Ubuntu as a back-up for Firefox.
i think so, i also think it back up adblock+
chromium is my backup

@kevdog it allows all on the page but the ones on that page then call scripts from other sites

---

### Post by DuckHook on 2014-12-15
The six traditional pillars of browser security are:

AppArmor
NoScript
Better Privacy
Adblock Plus
WOT
A cookie manager

One can add even more than these but they start to yield painful browsing experiences with diminishing returns. For a cookie manager to be effective, I find that cookies must be defaulted to "off", whitelisted only temporarily on a site-by-site basis, and permitted persistence on only a handful of the most critical (say, your bank's).

It is an oft-repeated oversimplification that Linux is "natively" more secure than Windows. While this may even be true, it is actually meaningless in a practical sense. For example, a key logger does not need access to root&#8213;it only needs to hide in your browser and be active when your browser is&#8213;and it will log all of your bank codes, passwords, etc when you visit your banking site. You do not browse as root (at least, I sure *hope* you don't) so a sneaky snippet of javascript left resident on your browser would neatly do the trick. That's why the gurus here recommend NoScript, etc.

The sad fact of the matter is that the vigilance and patience needed to harden your browser to what I would consider even a minimally hardened state is something that the average user will not put up with. They have been so conditioned to trade their security/privacy for convenience that they will sell their birthright for a mess o' pottage. It's taken me years to convince my wife to just add Adblock Plus and default her cookies to temporary. She won't put up with the inconvenience of NoScript and is prepared to let everyone know what her surfing habits are, in part because she chooses to ignore how shamelessly that information is sold and how perniciously it is exploited. I'm afraid the vast majority of users out there conform to my wife's surfing habits and not to ours. The fact that you are posting on a security forum, and a Linux security forum at that, means that you are not just your ordinary Joe Surfer.

I used to put more effort into convincing friends and family to beef up their security, but I've largely given up. I feel like Cassandra, cursed to warn her kin and countrymen about true peril, only to be forever dismissed as an hysterical fear-monger.

---

### Post by DuckHook on 2014-12-15
> **pqwoerituytrueiwoq said:**
> ...chromium is my backup...What follows is more for general users who may happen upon this thread. You gurus are probably all aware of this option:

As a second browser, have you gone the other direction and tried some of the absolute simplest? There are a number of them, but I'm most familiar with *Links2*. It cannot even be called "stripped down" as this implies some subtractive process starting from what we normally associate with a browser. Nor is it "minimalist" as this implies similar functionality without clutter. "Primitive" probably comes closest.

Instead, the "reason for being" of a browser like Links2 is to deliver only the raw info of a web site and none of the bells or whistles. It lacks even the functionality for cookies, scripts, video, music or rich content. It started out life as a text browser for the command line and the developers later added tables and simple graphics by way of framebuffer support which they then extended to Xserver, and hence, it now renders on any DE (provided you start it with the -g flag). It's uglier than a monkey's butt and uses quirky control key combos that will have you by turns cursing or bemused, but you will never, ever, have to worry about pop-ups, in-your-face ads, rogue scripts, tracking cookies or code injections. But its sheer primitiveness yields one very significant payoff: it usually bypasses the paywalls that fence off certain websites. The NYT and Economist sites are good examples. They register the browser as a legitimate albeit unidentifiable browser, but cannot track elapsed usage because the browser lacks the required functionality. It's a good instance of the principle where less is more. And after getting used to it, I have even come to appreciate its plebeian interface: I can just read the article and not be distracted by the fluff that would surround it in a regular browser.

Of course, if your intent is to visit YouTube, then you're barking up the wrong tree, but then, that's why you are keeping Firefox around.

Try it. You might like it.

---

### Post by Daveski17 on 2014-12-15
> **kevdog said:**
> Use it on Windows, do not on Linux.  I don't have a good explanation.  I somehow find it to be a major pain in the *** a lot.  Not sure why.  Even when I choose to allow of this page, I need to select this option more than once.  I'm not sure if this is how it was designed or I'm doing something wrong.

It can be a major PITA, but I think its advantages outweigh its sometimes 'temperamental' behaviour and disadvantages. lol

> **DuckHook said:**
> The six traditional pillars of browser security are:

AppArmor
NoScript
Better Privacy
Adblock Plus
WOT
A cookie manager

One can add even more than these but they start to yield painful browsing experiences with diminishing returns. For a cookie manager to be effective, I find that cookies must be defaulted to "off", whitelisted only temporarily on a site-by-site basis, and permitted persistence on only a handful of the most critical (say, your bank's).

It is an oft-repeated oversimplification that Linux is "natively" more secure than Windows. While this may even be true, it is actually meaningless in a practical sense. For example, a key logger does not need access to root&#8213;it only needs to hide in your browser and be active when your browser is&#8213;and it will log all of your bank codes, passwords, etc when you visit your banking site. You do not browse as root (at least, I sure *hope* you don't) so a sneaky snippet of javascript left resident on your browser would neatly do the trick. That's why the gurus here recommend NoScript, etc.

The sad fact of the matter is that the vigilance and patience needed to harden your browser to what I would consider even a minimally hardened state is something that the average user will not put up with. They have been so conditioned to trade their security/privacy for convenience that they will sell their birthright for a mess o' pottage. It's taken me years to convince my wife to just add Adblock Plus and default her cookies to temporary. She won't put up with the inconvenience of NoScript and is prepared to let everyone know what her surfing habits are, in part because she chooses to ignore how shamelessly that information is sold and how perniciously it is exploited. I'm afraid the vast majority of users out there conform to my wife's surfing habits and not to ours. The fact that you are posting on a security forum, and a Linux security forum at that, means that you are not just your ordinary Joe Surfer.

I used to put more effort into convincing friends and family to beef up their security, but I've largely given up. I feel like Cassandra, cursed to warn her kin and countrymen about true peril, only to be forever dismissed as an hysterical fear-monger.

Thank you for your informative and interesting post DuckHook. I certainly agree with you about Linux security, my brother is a software engineer and takes great pains to explain much to me with regards to computer security. Alas, a lot of it is geek-speak and technical jargon to me and often resembles just so much white noise. However, I have gleaned much and utilise a fair amount of browser hardening including the utilisation of NoScript on Linux and Windows.

---

### Post by open2reason on 2014-12-15
^^ To retrn your favour might I suggest > Adblock Edge is a fork of  the Adblock Plus version 2.1.2 extension for blocking advertisements on  the web, without sponsored ads whitelist.
                                             
It does what it says on the tin and does it rather well.

---

### Post by Daveski17 on 2014-12-15
> **open2reason said:**
> ^^ To retrn your favour might I suggest 
It does what it says on the tin and does it rather well.

Thanks, but I actually do run ABE on Firefox. I prefer it to ABP for a variety of reasons.

---

