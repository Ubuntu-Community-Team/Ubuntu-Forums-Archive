---
title: "Security Questions (sorry)"
date: 2007-06-13
forum: Server Platforms
---

### Post by tdrusk on 2007-06-13
I have been reading through all of the security threads, and quite frankly, I'm overwhelmed. I have all of these options and programs that I could install I just don't know what to do. I am running a Ubuntu Desktop with LAMP. I have followed [this]("http://www.debuntu.org/2006/07/30/77-how-to-apache-web-server-basic-security-measures") guide to make it harder for hackers to see what I am running, but I need more. I feel insecure. I am afraid to release my site because I don't want to get hacked and loose everything that I have because I don't know what I'm not advanced in security.

Any certain programs or guides that I should use to make my machine secure enough?

---

### Post by Frosty Cold Drink on 2007-06-13
> **fuzzyhair said:**
> I have been reading through all of the security threads, and quite frankly, I'm overwhelmed. I have all of these options and programs that I could install I just don't know what to do. I am running a Ubuntu Desktop with LAMP. I have followed [this]("http://www.debuntu.org/2006/07/30/77-how-to-apache-web-server-basic-security-measures") guide to make it harder for hackers to see what I am running, but I need more. I feel insecure. I am afraid to release my site because I don't want to get hacked and loose everything that I have because I don't know what I'm not advanced in security.

Any tips?

Tips, huh?

Well first off, what that article suggests isn't going to help you much, espicaly considering the fact that if you are compromised, it will probably be a blind attack.

There are plenty of articles and discussions out there that will help you make things a bit more solid. You just have to spend a little time looking for them.

Anyway, I only have two tips, which are sadly absent from must of what you will find out there.

The information security world is filled with those afflicted by [FAS]("http://www.vmyths.com/fas/fas1.cfm"). Worse still, the begginner to intermadiate computer user is often inundated with oversimplifed rules of thumb, which become mantra. The end result is a lot of bad advice, even from those who you'd think would know what they are talking about. Logic trumps all.

Isolation is your friend. Bad things will happen. When they do, make sure there are as many barriers as possible to prevent one bad thing from causing another.

---

### Post by tdrusk on 2007-06-13
> **Frosty Cold Drink said:**
> Tips, huh?

Well first off, what that article suggests isn't going to help you much, espicaly considering the fact that if you are compromised, it will probably be a blind attack.

There are plenty of articles and discussions out there that will help you make things a bit more solid. You just have to spend a little time looking for them.

Anyway, I only have two tips, which are sadly absent from must of what you will find out there.

The information security world is filled with those afflicted by [FAS]("http://www.vmyths.com/fas/fas1.cfm"). Worse still, the begginner to intermadiate computer user is often inundated with oversimplifed rules of thumb, which become mantra. The end result is a lot of bad advice, even from those who you'd think would know what they are talking about. Logic trumps all.

Isolation is your friend. Bad things will happen. When they do, make sure there are as many barriers as possible to prevent one bad thing from causing another.

Thanks for the tips!

Are there any programs or guides I should use to make my machine secure enough?

---

### Post by elst on 2007-06-13
FWIW, I wrote this a while ago as an attempt at explaining practical security:

[http://www.elsn.org/main/LinuxSecurityBasics]("http://www.elsn.org/main/LinuxSecurityBasics")

FAS is a problem, but what *really* frustrated me was that most security advice is given without a good sense of proportion - the biggest risks are often caused by failing to do small, simple things.

---

### Post by tdrusk on 2007-06-13
> **elst said:**
> FWIW, I wrote this a while ago as an attempt at explaining practical security:

[http://www.elsn.org/main/LinuxSecurityBasics]("http://www.elsn.org/main/LinuxSecurityBasics")

FAS is a problem, but what *really* frustrated me was that most security advice is given without a good sense of proportion - the biggest risks are often caused by failing to do small, simple things.

That is awesome. Thanks! I will definitely use this!

---

### Post by Mr. C. on 2007-06-15
I agree with FCD and Elstl.  I'll supplement with my own high-level perspectives, which talk to the concerns you've expressed:

[LIST=1]
[*]Fear is your friend - it warns you of possible harm.  Listen to it, proceed with caution, but don't lock up with fear.

[*]Knowledge is more useful than rumor, anecdote, or FUD.  Continue educating yourself about computer security.

[*]Expect and prepare for security to be an ongoing process of refinement

[*]Don't ever expect that you'll outfox the fox; eventually the inevitable will happen.  How you prepare for that eventuality, and how you deal with it is as important as prevention.

[*]Perform you own basic risk / reward analysis.  Determine what you can tolerate and what must be prevented at all costs.
[/LIST]

So, start by learning the basics, deploy one step at a time, and become very familiar with your logs, traffic patterns, and start asking lots of questions.

Best of luck,
MrC

---

### Post by tdrusk on 2007-06-15
> **Mr. C. said:**
> I agree with FCD and Elstl.  I'll supplement with my own high-level perspectives, which talk to the concerns you've expressed:

[LIST=1]
[*]Fear is your friend - it warns you of possible harm.  Listen to it, proceed with caution, but don't lock up with fear.

[*]Knowledge is more useful than rumor, anecdote, or FUD.  Continue educating yourself about computer security.

[*]Expect and prepare for security to be an ongoing process of refinement

[*]Don't ever expect that you'll outfox the fox; eventually the inevitable will happen.  How you prepare for that eventuality, and how you deal with it is as important as prevention.

[*]Perform you own basic risk / reward analysis.  Determine what you can tolerate and what must be prevented at all costs.
[/LIST]

So, start by learning the basics, deploy one step at a time, and become very familiar with your logs, traffic patterns, and start asking lots of questions.

Best of luck,
MrC
So, since I don't know that much atm, I will just keep backing up my wordpress database. That way if anything were to happen I could reformat and have it all back.
thanks

---

### Post by az on 2007-06-15
> **fuzzyhair said:**
> I have been reading through all of the security threads, and quite frankly, I'm overwhelmed. I have all of these options and programs that I could install I just don't know what to do. I am running a Ubuntu Desktop with LAMP.

Keep up-to-date with security updates.  Don't run anything you don't need to be running (like ssh, or a desktop....)  Any way you could get your hands on a cheap, old computer and run it without a GUI?  That's what I have in my basement.  That would be a simple way to avoid running unnecessary software.


> **fuzzyhair said:**
> 
 I have followed [this]("http://www.debuntu.org/2006/07/30/77-how-to-apache-web-server-basic-security-measures") guide to make it harder for hackers to see what I am running, but I need more. 

To be honest, not revealing what OS your running is not a very relevant thing.  

> **fuzzyhair said:**
> 
I feel insecure. I am afraid to release my site because I don't want to get hacked and loose everything that I have because I don't know what I'm not advanced in security.


Keep an eye on your logs, and if you ever need to run something on your site that is a little bit more involved (such as credit card transactions) buy web hosting and let them worry about security.

But seriously, if you are running wordpress using PHP5 (not php4) on Ubuntu, and you don't have much else running, there isn't a heck of a lot a hacker has to go with, you know?  It's not like you have secret launch codes,either.

---

### Post by elst on 2007-06-16
> **az said:**
> 
Keep an eye on your logs, and if you ever need to run something on your site that is a little bit more involved (such as credit card transactions) buy web hosting and let them worry about security.


Web hosting is a good thought - you have to accept the features that your host provides you (or switch hosts), but it moves the responsibility for system maintenance to a team that specialise in it, and that can be the right tradeoff. It is important to pick a host with a good reputation though - there are some excellent providers, and some very poor ones.

> 
But seriously, if you are running wordpress using PHP5 (not php4) on Ubuntu, and you don't have much else running, there isn't a heck of a lot a hacker has to go with, you know?  It's not like you have secret launch codes,either.


I don't agree with this point. What crackers usually want is to have control of as many Internet-connected systems as possible, and the normal way to get that is to run automated tools that scan literally thousands of addresses looking for systems whose software and configuration match up with known exploitable vulnerabilities. Writing these tools may require some skill, but running them requires very little.

PHP adds real risk because vulnerabilities are now regularly being publicised for it. Wordpress has also had security issues. A story made Slashdot about a whitehat scanning publicly available systems, and claiming that they found that almost all the probed Wordpress installations used versions and configurations that had known vulnerabilities:

[http://it.slashdot.org/article.pl?sid=07/05/24/167223]("http://it.slashdot.org/article.pl?sid=07/05/24/167223")

This is actually one of the things that I had in mind when I talked about simple things being important. For various reasons, some products have several times more vulnerabilities discovered for them than for other equivalent software, so it is very important to do your research when you select products for your systems. That doesn't mean that you shouldn't use certain products, just that you must be aware of the risks attached to your choices, and how to minimise them.

---

### Post by az on 2007-06-16
> **elst said:**
> Web hosting is a good thought - you have to accept the features that your host provides you (or switch hosts), but it moves the responsibility for system maintenance to a team that specialise in it, and that can be the right tradeoff. It is important to pick a host with a good reputation though - there are some excellent providers, and some very poor ones.

And it doesn't take away your responsibility to keep your web application up to date and secure, regardless of where it is running.

You can make your home server as tight as fort Knox, but if you allow your web application to write all over your filesystem, you're screwed.

> **elst said:**
> 
That doesn't mean that you shouldn't use certain products, just that you must be aware of the risks attached to your choices, and how to minimise them.

To me, in the context of running a wordpress web application on your Ubuntu server at home, that still boils down to keeping up-to-date with security updates (from Ubuntu as well as your wordpress install) as well as keeping an eye on the logs.

I mean, it's not as simple as:

sudo apt-get install *web-server-security*

but on the other hand, unless your hosting many sites with many different php scripts with lax security lying around, your not giving someone a lot to work with.

So I guess my point is no, you will never be safe;  never assume that, but don't lose any sleep over this.  There is not a whole lot to do to keep safe, except to keep an eye on things.

---

### Post by elst on 2007-06-16
> **az said:**
> And it doesn't take away your responsibility to keep your web application up to date and secure, regardless of where it is running.


Well, it reduces the list of stuff to worry about, and provides a source of support and advice - some of the big names hosts run forums etc. for users to help each other, as well as the usual support channels. For newbies the list of stuff that you are supposed to know to maintain a public server can be intimidating.

> 
To me, in the context of running a wordpress web application on your Ubuntu server at home, that still boils down to keeping up-to-date with security updates (from Ubuntu as well as your wordpress install) as well as keeping an eye on the logs.


That's probably as much as you can do at that point. I beat people over the head a bit with the "choose carefully" thing because of zero-day exploits. If vulnerabilities keep being found in a product then it implies that there are coding or design issues, and that you will always be on the back foot, having to worry about being hit before you are even aware that there is a new vulnerability.

I agree that for a home server this still isn't a big deal - subscribe to US-CERT and ubuntu-security-announce, keep up with the updates, and the risk is fairly low. With corporate networks it's less easy to roll out updates quickly, and a problem product can become a real nuisance.

---

### Post by Cheese Sandwich on 2007-06-19
Here's something interesting on PHP vulnerabilities:

[http://www.sklar.com/page/article/owasp-top-ten](http://www.sklar.com/page/article/owasp-top-ten)

---

