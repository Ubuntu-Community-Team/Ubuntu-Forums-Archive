---
title: "Are firefox extensions safe?"
date: 2014-08-14
forum: Security
---

### Post by markodd on 2014-08-14
Hey there,

I'm wondering if firefox extensions are safe to use? Are they reviewed? Is their code available?

I ask because of an extension called "Lastpass";

Using LastPass, there are two types of sites, sites we trust LastPass to remember the information and sites that are too important for a web-based platform (such as bank accounts, imo). When in the second type of sites, we can opt to click on "Don't save password for this domain". Now the question is, does it really not save the password? Can I be sure that the password is not sent to LastPass' servers? Or do we need to trust them that LastPass is not a big keylogger that sends them everything we type?

---

### Post by TheFu on 2014-08-14
Yes and no.  Some are safe, others are not. Buyer beware, as in all things free.  How does each extension make money? That is the real question. Just because it is free in cost, doesn't mean they aren't tracking you or getting paid some other way.  

Lastpass has appeared to be a reputable company over the years. When there appeared to be an issue a few years ago, the company management seemed to do all the right things - they announced the issue, said what they knew and what they didn't and followed up publicly.  It was impressive to see a corporation *do the right things* related to security reporting without being forced into it.

So - I wouldn't worry too much about Lastpass. A few friends who work as security consultants use it for their personal data - not just passwords.  They do backup archival data from it weekly, so when/if the webservice dies and disappears without any notice, they aren't stuck without access to their login credentials. That is a danger of any cloud-based service - here today, gone this evening - literally.

I prefer to use **KeePassX** on Linux and KeePass v1 on Windows and KeePassDroid on Android.  In this way, the encrypted password DB never leaves my direct control.  The DB between these 3 systems is compatible. I use a Linux machine as the read-write location and Windows/Android as read-only. Daily rsync jobs keep the other machines current with the primary DB copy.  KeePassX on Linux supports "autotype" - which is awesome. [http://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](http://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager) explains that password managers are not just for passwords.

---

### Post by cogset on 2014-08-15
Also,take your time to read the extension reviews on [https://addons.mozilla.org](https://addons.mozilla.org) because chances are that if an extension is malicious it will spotted and someone will report there (it has happened in the past),not to mention you can inspect the source code from there.
Another rule would be to preferably download/install always from [https://addons.mozilla.org](https://addons.mozilla.org) (a.k.a AMO) instead of third-party websites,which is not always possible as for variuos reasons some extension are not hosted on the official site (HTTPS Everywhere being the first one that comes to mind).
It is not always a case of how do they make money,as most addons are really put there for free or ask for a small voluntary contribution,but in general I would be wary of anything coming from a private company or sending data to external services.

---

### Post by markodd on 2014-08-16
Thanks for the replies, both of you.

It seems that as long as the extensions are in "AMO", they're safe as their code has been audited, right?

---

### Post by TheFu on 2014-08-16
Audited? Probably not.  Feel free to audit the code yourself - most extensions are just javascript.

---

### Post by thnewguy on 2014-08-16
> **markodd said:**
> Thanks for the replies, both of you.

It seems that as long as the extensions are in "AMO", they're safe as their code has been audited, right?

No, defintely not. If you want the code audited, you need to do it yourself (or hire someone to do it for you).

---

### Post by uRock on 2014-08-16
There are a few extensions that were advertised to do something only to find it to be wrong. The one  remember most is when I read about [Disconnect]("https://disconnect.me/"). I installed and ran it in Chrome while on Windows and at first glance I thought it was awesome. I went to use it while running PeerBlock and found that every search tried to start a TCP session with Amazon, which was blocked by PeerBlock and caused the searches to fail. I have found a few other "free" programs that Amazon has their hands into.

---

### Post by TheFu on 2014-08-16
> **uRock said:**
> ...  I have found a few other "free" programs that Amazon has their hands into.

Amazon has a platform that rewards people with CASH who redirect to their website IF you buy something. The rates of reward are published.  Canonical does that with their Unity Lens stuff - as an alternate revenue stream.  Not certain if what you are seeing is from the extension OR from Canonical.  I purge the Canonical stuff, because they didn't ask FIRST. This wasn't the first time they did something like that either.

If we want free tools, then we have to be willing, as a community at large, to pay.  If we are unwilling to pay, expect the Android "advertising culture" to take over on the OS too. Companies still need to pay their people so mortgages get paid, kids go to school, groceries get bought, etc.

---

### Post by uRock on 2014-08-16
> **TheFu said:**
> Amazon has a platform that rewards people with CASH who redirect to their website IF you buy something. The rates of reward are published.  Canonical does that with their Unity Lens stuff - as an alternate revenue stream.  Not certain if what you are seeing is from the extension OR from Canonical.  I purge the Canonical stuff, because they didn't ask FIRST. This wasn't the first time they did something like that either.

If we want free tools, then we have to be willing, as a community at large, to pay.  If we are unwilling to pay, expect the Android "advertising culture" to take over on the OS too. Companies still need to pay their people so mortgages get paid, kids go to school, groceries get bought, etc.

Very true. I haven't tested Disconnect in Linux. As soon as I replicated the issue a few times in Windows, while using peerblock, I decided to remove the extension, because in my opinion the app was negating its principal purpose of making searches anonymous.

---

### Post by markodd on 2014-08-18
> **thnewguy said:**
> No, defintely not. If you want the code audited, you need to do it yourself (or hire someone to do it for you).

Ah ok. I guess maybe the word "audited" was chosen  poorly. The code is available to review though, right? There are no "secrets" in an extesion, as long as someone takes the time to read the code, am I correct?

---

### Post by TheFu on 2014-08-18
> **markodd said:**
> Ah ok. I guess maybe the word "audited" was chosen  poorly. The code is available to review though, right? There are no "secrets" in an extesion, as long as someone takes the time to read the code, am I correct?

No.  It depends on the extension.  There are no easy answers.

Some are 100% javascript but that doesn't mean you or I have the skill to review it. It also doesn't mean that the code wasn't filtered through an "obfuscation tool" to make reverse engineering possible.

Others can have compiled parts - that we cannot see. [https://stackoverflow.com/questions/851109/what-programming-language-required-to-created-a-firefox-plugin](https://stackoverflow.com/questions/851109/what-programming-language-required-to-created-a-firefox-plugin) explains that part.

---

### Post by vasa1 on 2014-08-18
> **TheFu said:**
> No.  It depends on the extension.  There are no easy answers.

Some are 100% javascript but that doesn't mean you or I have the skill to review it. It also doesn't mean that the code wasn't filtered through an "obfuscation tool" to make reverse engineering **possible**.
...

Did you mean *difficult* instead?

One very, very popular script blocker for Firefox comes to mind. From comments by another extension developer, I got the impression that the author of the script blocker took much effort to make it difficult to understand the code. Anyway, all said and done, this script blocker is very popular with the "security-conscious".

---

### Post by cogset on 2014-08-18
If I've got it right about the popular script blocker you're referring to,at this year's SXSW conference (if memory serves) Snowden said it was the most effective protection tool you could use in Firefox.I guess he had a look at what it actually does,although the complexity of it is evident just looking at the interface.

---

### Post by TheFu on 2014-08-18
Used too many not, double, negatives, to be understood - perhaps not?
;)

---

### Post by markodd on 2014-08-19
There's an update for the lastpass firefox-addon in their site ([www.lastpass.com](www.lastpass.com)), however, in the firefox add-ons site ([https://addons.mozilla.org/en-US/firefox/](https://addons.mozilla.org/en-US/firefox/)) it's still not showing the latest version. 

Should I update using their site?

---

### Post by cogset on 2014-08-19
> **TheFu said:**
> Used too many not, double, negatives, to be understood - perhaps not?
;)

Maybe so ;) for starters,were you answering to my post above or someone else's ?

---

