---
title: "DSPAM vs SpamAssassin"
date: 2005-10-17
forum: The Cafe
---

### Post by KingBahamut on 2005-10-17
After six months of development, DSPAM v3.6 has been released. The most notable change is the series of new features added to make an anti-spam gateway appliance possible (Knoppix anyone?). Version 3.6 also includes a highly accurate alternative to Bayesian filtering known as Markovian discrimination, based on Bill Yerazunis' research. Other significant enhancements include trusted sender whitelisting, integrated Clam Antivirus and LDAP support, a centralized spam training alias, and a new dependency-free storage driver. Much of the documentation has also been rewritten to make installation easier. A change log and release notes are also available. 

External Links 
[http://dspam.nuclearelephant.com/](http://dspam.nuclearelephant.com/)
[http://dspam.nuclearelephant.com/text/relay-howto.txt](http://dspam.nuclearelephant.com/text/relay-howto.txt)


Now then, SpamAssassin, that other Spam killer software thingy has always been my choice. But im looking at the feature set described in this /. post. SpamAssassin most certainly has ClamAV integration , and Training Alias from what im aware of. Installation is easier? The Markovian aspect I find interesting. Memory serving correctly Markovian is a process based on probablities and factors. Still, I wonder what this does over Bayseain(sp?). SpamAssassin has served me well, as it has others. Though this production makes me curious, what can DSPAM do for me that S-A cannot?

---

### Post by asimon on 2005-10-20
So has anyone expierience with DSPAM? (I am currently on bogofilter)

I remember some old tests were DSPAM didn't performed well compared to bogofilter and spamassassin, but it seems a lot has since changed in DSPAM land.

I especially like DSPAM's new focus on usability, i.e. "designed with gandma in mind". I remember when I tried DSPAM last time (one or two years ago) it was a real horror to install and setup.

---

### Post by UbuWu on 2005-10-20
The main differences according to their FAQ:
> Q. How is DSPAM different from SpamAssassin?
A. While both share the common goal of eradicating spam, the two solutions bear very different philosophies.

Cocktail Approach vs. Centralized Adaptive Learning

SpamAssassin is designed with the arsenal (a.k.a cocktail or toolbox) philosophy and aggregates the results from a myriad of different spam detection tests with the hope that at least some of the components should detect an inbound spam. These different tests range from heuristic "rules" which identify specific characteristics in spam to blacklists, and finally to limited Bayesian learning. DSPAM's philosophy is based on the belief that machine-learning (basic artificial intelligence) can, in and of itself, solve the spam problem without the need for human-maintained rules, inaccurate blacklists, or any hodge-podge of solutions for that matter. DSPAM's one central spam detection function incorporates advanced, concept-based statistical analysis. This has resulted in levels of accuracy up to ten times that of a human, with very few false positives. DSPAM breaks down each email into its colloquial components, analyzes the historical data for each component, and determines the most interesting characteristics to judge an email by. While DSPAM supports many pre-filters, post-filters, and additional layers of analysis, its central function lies solely in adaptive learning and language analysis. This alone has yielded levels of accuracy peaking at 99.991%.

We feel that the justification for our philosophy is in the credits. While the SpamAssassin project requires over 100+ individuals to maintain, DSPAM manages to delivery significantly higher levels of accuracy with only one primary maintainer and a small pool of patch contributors.

Maintenance Burden

DSPAM's philosophy includes removing unnecessary human maintenance by means of its learning abilities. Users simply need to forward spam they receive into the system and DSPAM will automatically learn. There are no rules to update, no thresholds to set, and very little systems administration after DSPAM's initial integration. Through the use of various forms of community groups, even the burden of training can be significantly reduced. Forwarding spam also gives your users a sense of participation in your anti-spam efforts, reducing the number of phone calls, email, and complaints you may receive. SpamAssassin, on the other hand, pushes maintenance to the responsibility of a central systems administrator and prevents the end-user from participating in any capacity that significantly affects their filter training. This leaves many end-users with the feeling of helplessness against false positives and poor filtering results should their mail deviate from what is considered "normal". A systems administrator is required in order to update rulesets, tweak performance, and etcetera. The idea of removing end-user maintenance may be desirable by some very large implementations, and so DSPAM can also be configured to support this by allowing the systems administrator to train a global database of contextual data. DSPAM, however, doesn't require full-time maintenance.

Behavioral Philosophy

One significant difference between the two tools is their philosophy about behavioral learning. SpamAssassin's primary detection facility has been designed to use a static set of rules to service all users of the system. DSPAM's philosophy is that this presents a significant hindrance to accuracy, because one user's spam is another user's mail. DSPAM is adaptive to the behavior of each individual user on the system so that it can custom-tailor its spam detection to that of each individual. To provide "out-of-the-box" functionality, DSPAM also supports the use of merged groups, which are global databases merged (at run-time) with the user's own training data. This allows new users to receive instant, high-quality spam filtering without losing the ability to train DSPAM for their personal email behavior.

Newer versions of SpamAssassin support a form of Bayesian learning, but this doesn't appear to operate on a per-user basis (at least not without extensive configuration). The heuristic training guides also appear to hurt the level of accuracy the Bayesian component could deliver if SpamAssassin was made a pure statistical filter.

Technical Philosophy

DSPAM's technical philosophy is that of high-accuracy and high-performance in an enterprise environment. For this reason, C was chosen as the language for DSPAM. DSPAM has been implemented in systems exceeding 350,000 users and experiences execution times as low as 0.01s (real time) when tuned properly. The average system of around 100,000 users experiences around 0.06s-0.20s processing time. The philosophy behind SpamAssassin requires a focus around development effort. SpamAssassin is written in Perl, which is generally a much easier language to code the regular expressions used by SpamAssassin's heuristic rules engine. As a result, even novice developers can quickly code new rules for SpamAssassin. It's unfortunately very slow, however, compared to DSPAM and as a result, even small implementations have been known to use up all resources on the machine. Since DSPAM doesn't have any heuristic rules, it doesn't require the use of regular expressions (which are always touted as fast in Perl). DSPAM's tokenizing algorithm is, as a result, much faster then SpamAssassin's analysis engine because it does not use regular expressions. Because Perl is an interpreted language, and because of the extensive (and unnecessary, in my opinion) pattern matching it performs, SpamAssassin ends up running much slower and using many more resources than DSPAM, which uses a language compiled and assembled directly into machine code.

While we believe the philosophies we've chosen for DSPAM are better suited for the job (as evidenced by DSPAM's long-term accuracy), there are plenty of other ideas out there that produce acceptable results. 

---

### Post by Riverside on 2005-10-20
The main issue with SpamAssassin is the need to stay current.  Unscrupulous bulk emailers and writers of "spamware" of course also install SpamAssassin on test machines and fire high volumes of email at email addresses for which those test machines provide incoming MX service, and tweak their emails and/or spamware as a result of this testing to evade SpamAssassin filters as far as possible.  The SpamAssassin developers, in turn, continually update and upgrade their product, and the whole thing is something of an arms race.

SpamAssassin therefore needs to be backported quickly and often, i.e. ideally within 24-48 hours of a new release coming out.  For example, SpamAssassin 3.1.0 was released on 14 September 2005, however Breezy still ships with the previous version, 3.0.4.  A month is a lifetime in spam fighting circles, and anyone experiencing as a result what they perceive to be poor results from SpamAssassin is really experiencing the problems associated with running an out of date version.

Of course, one can upgrade SpamAssassin using CPAN etc, or compiling from source, however I suspect that most Ubuntu users would prefer to be able to apt-get install a backported version.

As for DSPAM, the principal service developer at $WORKPLACE (a large UK ISP) informs me that DSPAM as a product works very well, but is a lot more complicated to install and configure than SpamAssassin, and ventured the opinion that it may well be beyond the capabilities of all but the most technical end users.  SpamAssassin, in contrast, "just works" once installed, and comes with pattern matching rules etc.

---

### Post by mjgumbley on 2007-08-01
I agree with Riverside - DSPAM looks wonderful, but it's a royal bitch to install correctly. I'd consider myself very technical, and I've been trying to get it working as a content filter - as suggested in its own postfix integration doc - for over a week now. I've got it to the stage where I can send a retraining mail and it'll retrain, but it doesn't seem to create many of the user's data files when mail comes in - way too fiddly. I tried POPfile a few years ago; great, but POP3 is so... '80s.

There are some excellent articles on DSPAM integration, including:
[http://www.freesoftwaremagazine.com/articles/focus_spam_dspam?page=0%2C3](http://www.freesoftwaremagazine.com/articles/focus_spam_dspam?page=0%2C3)
[http://gentoo-wiki.com/HOWTO_Spam_Filtering_with_DSPAM_and_Postfix#Identity_Crisis](http://gentoo-wiki.com/HOWTO_Spam_Filtering_with_DSPAM_and_Postfix#Identity_Crisis)
[http://www.kirya.net/articles/setting-up-dspam-as-a-filter-for-postfix-on-debian-sarge/](http://www.kirya.net/articles/setting-up-dspam-as-a-filter-for-postfix-on-debian-sarge/)
[http://dspamwiki.expass.de/](http://dspamwiki.expass.de/)
[http://dspamwiki.expass.de/Installation/Postfix/NealesSetup](http://dspamwiki.expass.de/Installation/Postfix/NealesSetup)

HTH, Matt

---

