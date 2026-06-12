---
title: "Why such bizarre spam?"
date: 2012-07-11
forum: Security
---

### Post by Paddy Landau on 2012-07-11
The contact form on my website does not have a CAPTCHA (it stopped working), but it rejects any messages containing banned words — including "http". This makes it useless for spammers, and indeed I receive very few spams from my website; just a few a month.

The thing is, the only spam I ever receive is garbage. Today's example:

**Name:** Umtptmo
** Email:** [noparse]inzzxlobol@gmail.com[/noparse]
** Subject:** OhwLfgBbai
** Message:** DM7fpx Grguch alien ant farm tabs unfolding main herbal eyebright  christopher stabbed nearby latrodectus diaguita snakes checked glipizide  glucotrol private studied pf changs lettuce wraps energies cause  arrive.

Now, what I want to know is: Why would anyone bother to send such garbage? Is this meant to contain some surreptitious subliminal message that I unconsciously respond to? (Of course not.)

But, really, what a waste of time for the spammer! I am curious why this happens.

---

### Post by CharlesA on 2012-07-11
I assume they thought it was a blog comment form or something.

Are you using Wordpress or something else?

I'm got a simple PHP contact form on my site, I can give you a link to it if you like.

---

### Post by Paddy Landau on 2012-07-11
> **CharlesA said:**
> I assume they thought it was a blog comment form or something.
LOL.

> **CharlesA said:**
> Are you using Wordpress or something else?

I'm got a simple PHP contact form on my site, I can give you a link to it if you like.
It's a Joomla site, which I intend to convert one of these days. Thanks for your kind offer, but I really get very little spam from the site, maybe one a week. I am just puzzled as to why anyone would spam such junk. It could be an automated bot, of course, trying to test out websites.

---

### Post by blueshead on 2012-07-11
It is actually the secret language of French Quarter drunks in New Orleans..

You're on to us now.. :)

---

### Post by houseworkshy on 2012-07-11
I once had something similar, several years ago when using winXP.  Soon after it came from random garbage names @ my email address.  Never found out the point of it but it turned out someone had regestered my email name as their domain, the isp wasn't co-operative so I ended up  changing providors as there was nothing else I could do to stop it.  No idea if this is the prequil to something similar but it may be worth making absolutely sure it isn't self generated; thinking probing to zombie your machine/site and attack others perhaps?  So try rkhunter, wireshark, tyger and similar diagnostics to find out ( I had similar mails bounce back at me sent when my only machine was actually turned off and I didn't even have a site so it had got to my account at the isp.  Mention this to your ISP just in case.  This is probably not the same thing, which I never really understood anyway ( as in WHY?  ) ,  it's just that the part one sounds identical and the part two was a horror.   The headers on those email would be interesting, are they cc or just to you?   Worth looking for the origin of it on the ARIN database and similar.  Just had a quick look for arin as I haven't used it for years, since the windows days actually when this problem happened ( I was a newbie anyway so shouldn't really blame the OS ) and I got cross about it.   This site uses it so may be of use [http://itools.com/tool/arin-whois-domain-search](http://itools.com/tool/arin-whois-domain-search).    If you find the origin of it ( after bouncing all over the place my lot turned out to be from  somewhere in Poland I recall )  , report it as it mucks up the internet for everyone.  The number of spam emails got so big it took ages to find the real ones and I ended up dumping the email account along with the ISP, annoying for domestic PC me but what if it'd been a hostpital machine or some other critical thing  for example.  Hope you're not in for the same.  Go get them! If you find them report them to their own ISP as well as your own.  Google may take an interest in this one too.

---

### Post by Paddy Landau on 2012-07-11
> **blueshead said:**
> It is actually the secret language of French Quarter drunks in New Orleans..

You're on to us now.. :)
Gotcha!

> **houseworkshy said:**
> I once had something similar...

That's an interesting story! Thanks for sharing,

In my case, though, I know it is coming from my website because of other parts of the email that I had not inserted into the original post.

---

### Post by Irihapeti on 2012-07-13
One theory is that this is to "poison" spam filters. [http://www.tectite.com/fmdoc/attack_detection_junk.php?WWWTECTITE=kt784s66uok32so71rp4m0b3s1](http://www.tectite.com/fmdoc/attack_detection_junk.php?WWWTECTITE=kt784s66uok32so71rp4m0b3s1) has a bit more detail. (It's a web form that I'm seriously thinking of using.)

---

### Post by Paddy Landau on 2012-07-13
> **Irihapeti said:**
> One theory is that this is to "poison" spam filters.
Thank you. That's the first time I've heard the term "poison". [Wikipedia explains why]("http://en.wikipedia.org/wiki/Bayesian_poisoning") spammers are doing it; I shall mark this thread as solved.

---

### Post by pe7er on 2012-07-13
I get the same sort of weird nonsense spam messages. It doesn't matter what CMS you are using as the spam bots just submit all forms they find.

I think that they are trying to find blogposts with comment forms to create backlinks to their spam sites.

You can decrease the spam by using a captcha in your form (Joomla 2.5 has it by default) but it might make it more difficult for real users to use your contact form too...

---

