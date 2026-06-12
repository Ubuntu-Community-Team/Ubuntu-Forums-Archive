---
title: "Web Bugs"
date: 2009-07-03
forum: The Cafe
---

### Post by Ubuntist on 2009-07-03
Recently I started using the Ghostery add-on for Firefox.  It shows you what web bugs are active on the pages you read.  On this very page, for example, Google Analytics is tracking my IP number, etc.

Aside from using Tor, which I often find painfully slow, is there anything one can do about web bugs?

As I understand it, a web bug is a very small image (1-pixel in size) that triggers a link when loaded.  But what I don't get is why setting NoScript to block google-analytics.com doesn't block the web bug.

Ghostery is really scary.  It seems that Google is alerted on probably well over half of the websites that I visit.  By now, it may know more about me than I do.

---

### Post by monsterstack on 2009-07-03
Ghostery finds scripts that might be doing dodgy things. It has nothing to do with tiny images. These naughty things are javascript embedded in the page and don't reveal themselves unless you look at the page source. And Noscript *does* stop them from working, so don't worry about that. Google has earned my trust, but Google Analytics has not. As far as Tor goes, I just use it every now and then when looking at sensitive things. You don't really need to use it for general browsing.

---

### Post by kagashe on 2009-07-03
Use noscript and be free of Javascript.

kagashe

---

### Post by t0p on 2009-07-03
> **monsterstack said:**
> Google has earned my trust

How have they done that?  By [helping the Chinese government]("http://www.guardian.co.uk/commentisfree/2008/jun/26/internet.china") to oppress its people?

---

### Post by monsterstack on 2009-07-03
> **t0p said:**
> How have they done that?  By [helping the Chinese government]("http://www.guardian.co.uk/commentisfree/2008/jun/26/internet.china") to oppress its people?

*Sheesh*, now that's some flamebait right there. I meant the javascript they use at Google.com, not their censorship in China.

---

### Post by t0p on 2009-07-03
> **monsterstack said:**
> *Sheesh*, now that's some flamebait right there. I meant the javascript they use at Google.com, not their censorship in China.

Okay, then how about the way they search your gmail inbox but "don't tell anyone what they find"?  Is that relevant?

---

### Post by monsterstack on 2009-07-03
> **t0p said:**
> Okay, then how about the way they search your gmail inbox but "don't tell anyone what they find"?  Is that relevant?

You mean like every email provider on the planet? Actually that's an over-statement. Many email providers certainly do tell others what they find. Your emails are scanned for spam, for spell-checking, for forwarding, for virus scanning, regardless of who hosts your mail. If it bothers you so much, why don't you set up your own ssmtp mail server?

---

### Post by Ubuntist on 2009-07-03
> **kagashe said:**
> Use noscript and be free of Javascript.

kagashe

I *do* use NoScript and I block google-analytics.com, but I still receive alerts from Ghostery that Google Analytics is tracking me.

---

### Post by mr.propre on 2009-07-03
Normally you can't.

If it's not a script then it's the apache log :lolflag:
Tracking is just part of the internetz and most companies put it in there terms. If you don't agree with it, don't visit the website.

---

### Post by t0p on 2009-07-03
> **monsterstack said:**
> If it bothers you so much, why don't you set up your own ssmtp mail server?

It bothers me, sure.  But it doesn't bother me "so much".  I am aware of (some of) what Google does, and I try to minimize the damage.  For instance, I use CustomizeGoogle with the most pro-privacy settings enabled.  I don't use GoogleGroups to post to Usenet.  I don't use Gmail for my most private email (I have a shell account on a FreeBSD server for stuff like that).  I don't use email at all for truly sensitive communications - you shouldn't send by email anything that you wouldn't feel comfortable sending written on the back of a postcard.

But the above is all irrelevant.  My point wasn't about being bothered by the stuff Google gets up to.  I was questioning the idea of *trusting* Google. I don't trust Google.

As for setting up my own mail server: I may do that.  If my ISP doesn't prevent it.  I've got smtp on my home machine already, but when I try to send mail from it I get a "delivery failed" message saying

> Mailing to remote domains not supported

I haven't explored the issue yet, but I suspect it's down to my ISP.

But anyway: Trusting Email == NoNo.  I've got "safer" accounts, and gpg, but email is not trustworthy and was never meant to be trustworthy (by which I mean "private").  But Google tries to portray itself as "trustworthy", "not evil" etc.  And some people, whether through ignorance or foolishness, *do* trust Google.  And when I hear/see someone admit to being such a person, I feel I have a duty to shout: *Nooo*!!

BTW: this is all terribly off-topic.  I apologize.  Now move on.  Nothing to see here!

---

### Post by Ubuntist on 2009-07-04
Ghostery and NoScript are Firefox add-ons that you can install very easily.  NoScript allows you to prevent site from running Java and JavaScript site by site (many sites don't work if you disallow Java or JavaScript).  As for Ghostery, well, it's pretty much the subject of this thread--it alerts you to web bugs, but doesn't stop them.  As for Google Analytics, check its website, google-analytics.com or look at Wikipedia.

---

### Post by Ubuntist on 2009-07-04
> **mr.propre said:**
> Normally you can't.
 Tracking is just part of the internetz and most companies put it in there terms. If you don't agree with it, don't visit the website.

My worry is not so much with the websites themselves, but with the fact that Google is collecting all of this information.  Many, many sites have web bugs from Google Analytics, so I figure Google is in a pretty good position to profile us all, and *that* I don't like one bit.

---

### Post by Ubuntist on 2009-07-04
OK, here's another question.  Let's say I'm running NoScript and denying all scripts.  I visit a web page that has a web bug from, say, Google Analytics.  Ghostery alerts me to the web bug.  Does the fact that I've disabled all scripts mean that even though Ghostery finds the bug, the bug doesn't actually run, i.e., Google Analytics is not alerted to my viewing of the page?

---

### Post by kagashe on 2009-07-05
> **Ubuntist said:**
> OK, here's another question.  Let's say I'm running NoScript and denying all scripts.  I visit a web page that has a web bug from, say, Google Analytics.  Ghostery alerts me to the web bug.  Does the fact that I've disabled all scripts mean that even though Ghostery finds the bug, the bug doesn't actually run, i.e., Google Analytics is not alerted to my viewing of the page?Yes, because nosript prevents running that Javascript which alerts Google Analytics.

kagashe

---

### Post by monsterstack on 2009-07-05
> **kagashe said:**
> Yes, because nosript prevents running that Javascript which alerts Google Analytics.

kagashe

That's right. I find Ghostery's notifications useful, even if running Noscript makes it somewhat redundant.

---

