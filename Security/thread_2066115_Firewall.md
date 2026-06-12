---
title: "Firewall"
date: 2012-10-03
forum: Security
---

### Post by mbm1234 on 2012-10-03
Hello, I want to know if Ubuntu version 12.04 has a Firewall and IpTable, I found this article:

[http://mylinuxbook.com/linux-iptables/](http://mylinuxbook.com/linux-iptables/)

I'm interested to use this feature, if it's possible to enable this option in Ubuntu version 12.04, please if somebody can show me how to do it, thanks in advance.

---

### Post by mbm1234 on 2012-10-03
I found this article about Ubuntu:

[http://www.infoworld.com/d/data-center/ubuntu-has-bigger-problem-its-amazon-blunder-203467](http://www.infoworld.com/d/data-center/ubuntu-has-bigger-problem-its-amazon-blunder-203467)

After I read this article, I don't know if Ubuntu is a trust Operating System.

---

### Post by AndyOpie150 on 2012-10-03
After reading the article I'm very hesitant about the 12.10 version, but, as of yet I see no security concerns to be worried over with 12.04 that I don't create myself (installing windows programs that might have an embedded virus).

I know this doesn't answer you question, It's really just posted to put you at ease with your security concerns for the 12.04 version.

As far as Firewalls: Open up Ubuntu Software Center and type in "Firewall" into the search bar. You will come up with a firewall builder and a firewall configuration.

---

### Post by raja.genupula on 2012-10-03
Read these two things

[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

### Post by cariboo on 2012-10-03
As usual, the press, creates these types of articles, to generate page reads. You can turn of the shopping feature in 12.10 (Quantal Quetzl) in less than 1 minute. 

Iptables is a part of the Linux kernel, and can be used in all versions of Ubuntu, it is controlled via the command line via [ufw]("https://help.ubuntu.com/community/UFW"), or graphically via [gufw]("https://help.ubuntu.com/community/Gufw"). Gufw isn't included in the default install, but can be installed using the Software Centre.

If you have further questions about firewalls, have a look at the [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") sub-forum, as there is extensive help already available.

**Edit:** I see the thread was moved while I was posting. :)

---

### Post by mbm1234 on 2012-10-04
Hello, thank you AndyOpie150, raja.genupula, and cariboo907 for replying, I want to learn Firewall by command line via ufw, thank you everybody this information is very helpful.

---

### Post by mbm1234 on 2012-10-04
cariboo907 how can I Join the U+1 Development Releases Testing Team?, which level of knowledge do I need to be part of the U+1 Development Releases Testing Team?, and do I have to take some exam?, thanks in advance.

---

### Post by NadirPoint on 2012-10-04
> **cariboo907 said:**
> As usual, the press, creates these types of articles, to generate page reads. You can turn of the shopping feature in 12.10 (Quantal Quetzl) in less than 1 minute.
How many users do you believe would check that box in the global privacy manager if it were an "opt-in" feature?

Unauthorized or unintended outbound connections, regardless of their origin or intent are by definition a "bad" thing in the network world.  I hope Cannonical is not on the road to becoming a commercial spyware vendor.

---

### Post by Hungry Man on 2012-10-04
Outbound connections are fine. This isn't a big deal if it gets handled properly and in a secure manner - ie: not being sent over plaintext and only accepting packets from Canonical.

I'm not sure how many would opt into this. Most users are dumb and don't have a clue what they actually want.

---

### Post by NadirPoint on 2012-10-04
> **Hungry Man said:**
> Outbound connections are fine.
Really?  Unauthorized, unintended outbound connections?  Even when their contents may contain personal data you were searching for on your local machine?  Golly gee, take me back a decade ago when the Windows firewall controversy got started.  (cough, cough)

> **Hungry Man said:**
> Most users are dumb and don't have a clue what they actually want.
That is EXACTLY what Canonical is banking on.

---

### Post by Hungry Man on 2012-10-04
> Really? Unauthorized, unintended outbound connections? Even when their contents may contain personal data you were searching for on your local machine? Golly gee, take me back a decade ago when the Windows firewall controversy got started. (cough, cough)
I mean that there's nothing inherently dangerous about an outbound connection. Yes, you can send data using an outbound connection but that isn't *strictly* dangerous, programs do it all the time and it doesn't really get taken advantage of by attackers (unlike inbound connections, which are inherently dangerous and have to have steps taken to mitigate the dangers).

> That is EXACTLY what Canonical is banking on.

It's what the trillion dollar advertising industry is built on - the same industry that allows us to view the internet for free.

Yes, ads are a pain. We're given the choice to opt out but plenty of people may find it incredibly useful. Moves like this grow products, it's Ubuntu's first step to being a viable operating system in terms of a proper business model.

It's Linux - you're never going to be locked into anything. You'll always have an opt out no matter how convoluted.

---

### Post by offgridguy on 2012-10-04
I'm not sure how many would opt into this. Most users are dumb and don't have a clue what they actually want.[/QUOTE]

HungryMan, even if this is an accurate statement, I don't think it is in good taste to post it,
doesn't it it say something about being polite in the forum conduct rules?

---

### Post by NadirPoint on 2012-10-04
> **Hungry Man said:**
> I mean that there's nothing inherently dangerous about an outbound connection.
What this tells me you mean is you either do not understand the issue or simply refuse to address it from a security standpoint.

---

### Post by Hungry Man on 2012-10-04
> 
HungryMan, even if this is an accurate statement, I don't think it is in good taste to post it,
doesn't it it say something about being polite in the forum conduct rules?
I'm not implying anyone on this board is stupid. I'm just trying to say that for the most part users are uninformed and uninterested in how their systems operate.

> What this tells me you mean is you either do not understand the issue or simply refuse to address it from a security standpoint.

Explain it to me.

---

### Post by cariboo on 2012-10-05
> **mbm1234 said:**
> cariboo907 how can I Join the U+1 Development Releases Testing Team?, which level of knowledge do I need to be part of the U+1 Development Releases Testing Team?, and do I have to take some exam?, thanks in advance.

We have team members of all skill levels, no test, and everyone is welcome. Go [here]("https://launchpad.net/~u+1"), to join.

---

### Post by cariboo on 2012-10-05
> **NadirPoint said:**
> How many users do you believe would check that box in the global privacy manager if it were an "opt-in" feature?

Unauthorized or unintended outbound connections, regardless of their origin or intent are by definition a "bad" thing in the network world.  I hope Cannonical is not on the road to becoming a commercial spyware vendor.

None, and I would suggest that most new users won't see it as a problem, until one of their searches result in a picture of a naked person, and depending on what country they are from, I expect some will find it funny, and others will find it outrageous.

This is more a privacy issue than a security issue, most of those that don't want their details broadcast to the world, have already taken actions to stop that from happening, and those that come into the Ubuntu world and are worried about such things will do what any normal user would do, do a Google search, and find enough information available to easily disable the function.

---

### Post by NadirPoint on 2012-10-05
> **cariboo907 said:**
> ...and those that come into the Ubuntu world and are worried about such things will do what any normal user would do, do a Google search, and find enough information available to easily disable the function.
But they won't, because there are no such thing as a "normal" user.  By not making it opt in or notifying the user in any way Canonical is taking advantage of the fact that a large number of them will either be oblivious or just not care.

This reeks to high heaven.

Funny, I can't seem to remember the last timew I saw an Ubuntu Privacy Policy notice.  It would be interesting to see how they draft that now.   :confused:

And the simple fact that they "would" do this makes it a security issue as well, by virtue of Shuttlworth's flippant remak about ostensibly having "root."  There is no trust anymore, as far as I am concerned.

---

### Post by Hungry Man on 2012-10-05
If you don't have trust now you never should have. They do have root on your system, you get packages directly from them, and if you don't trust them now you never should have.

About the NWS stuff I think that was solved. (yep [http://www.omgubuntu.co.uk/2012/10/ubuntu-adds-amazon-results-off-switch-fixes-nsfw-issues](http://www.omgubuntu.co.uk/2012/10/ubuntu-adds-amazon-results-off-switch-fixes-nsfw-issues) )

This is a privacy issue and it doesn't even have to be because:
1) Canonical acts as a proxy between you and Amazon. They can easily strip out information that could be used to personally identify you, they could do this locally as well.

2) There's an opt out.

Why not an opt in? Because most users, again, have no idea what they want. They'd never opt in and they'd never know whether they actually would find it useful or not.

It's a business model. When it comes to Linux you don't really get to charge for the OS you have to either charge for support or come up with a new model.

From a security standpoint nothing has changed. Outbound connections aren't scary - they don't point to a vulnerable service like an inbound connection and in terms of a local attack there's already ports to choose from. Canonical has always had 'root' on your system and you've always trusted them to package binaries for you.

---

### Post by NadirPoint on 2012-10-05
> **Hungry Man said:**
> If you don't have trust now you never should have. They do have root on your system, you get packages directly from them, and if you don't trust them now you never should have.
Trust is a concept you also appear to not understand very well.  It is not a black/white all or nothing proposition in many cases.  It can be like for example between 2 spouses, but certainly not this one.  There is complete trust, blind trust, limited trust, and various others.  What trust do you put in Canonical?

Before, I trusted them to update packages with the implicit understanding that was what they did, within the framework of their development requirements, little more.  I did not, (nor do I believe you will find anyone) trust them to install software that broadcast my searches across the Internet without my knowledge.  Did you?

Good luck with that.  Like I said, the limited trust that was there is now gone.

---

### Post by Hungry Man on 2012-10-05
Nah, I think I understand plenty. You're blowing this situation out of proportion.

---

### Post by NadirPoint on 2012-10-05
Don't worry, nothing to see here, move along now.  Keep your head in the sand and everything will be fine!  ;)

---

### Post by mbm1234 on 2012-10-05
Thank you everybody and cariboo907 to reply, thank you everybody for help me with this issues, I appreciate.

---

### Post by 3rdalbum on 2012-10-13
> **NadirPoint said:**
> 
Unauthorized or unintended outbound connections, regardless of their origin or intent are by definition a "bad" thing in the network world.  I hope Cannonical is not on the road to becoming a commercial spyware vendor.

I love it. This is hilarious.

For nearly a year now, Ubuntu has sent your Dash search queries to the Ubuntu One Music Store (run by 7Digital) to give you search results of music you can buy, as part of the Music lens. Nobody raised any objections.

For the last six months, Ubuntu has sent your Dash search queries to various other companies who deal in on-demand and "catch-up" video services, to give you search results of videos you can watch online, as part of the Videos lens. Nobody raised any objections - in fact, people quite liked the feature.

Now your search queries get sent to a big, well-known company as part of the Shopping lens, and people are raising all sorts of objections. Let's face it: Few people, probably nobody, would have raised any objections if the Shopping lens was powered by Dealsdirect or Thinkgeek. But since it's Amazon, it's a total invasion of privacy and a security risk, and completely unacceptable. Apparently.

So Canonical writes in a setting that stops the Dash from touching the Internet at all... and no, that's apparently not good enough either. All the objectors still want their search queries splattered halfway across the world to TV catchup services and music stores that most have never heard of, but just not to any well-known companies that make a lot of money.

I'm no fan of Amazon for a number of reasons, but I find it incredible that the privacy advocates didn't raise a peep back when Dash started sending search queries - they're only objecting a year later when the service is expanded to include just one more company.

---

### Post by NadirPoint on 2012-10-13
> **3rdalbum said:**
> For nearly a year now, ...they're only objecting a year later when the service is expanded to include just one more company.
People catch on when they do it surreptitiously, for the wrong reasons.

Thanks for confirming that Canonical intends to become a commercial spyware vendor!

---

### Post by Hungry Man on 2012-10-13
Wow. Not being hyperbolic at all, are we?

---

### Post by cariboo on 2012-10-13
> **NadirPoint said:**
> People catch on when they do it surreptitiously, for the wrong reasons.

Thanks for confirming that Canonical intends to become a commercial spyware vendor!

You can turn it off, by going to System Settings->Privacy. Instead of making baseless statements, why not try some research first.

---

### Post by NadirPoint on 2012-10-13
> **cariboo907 said:**
> You can turn it off, .
Why should I have to turn it off?  I never turned it on in the first place.

Is yours turned on?

---

### Post by NadirPoint on 2012-10-13
> **3rdalbum said:**
> I love it. This is hilarious.
You have an odd sense of humor.
> **3rdalbum said:**
> ...sent your Dash search queries to the Ubuntu One Music Store (run by 7Digital) to give you search results of music you can buy,
Music search goes to music source.  Ya think?
> **3rdalbum said:**
> For the last six months, Ubuntu has sent your Dash search queries to various other companies who deal in on-demand and "catch-up" video services, to give you search results of videos you can watch ...
Video search looks in video sources.  Hmmm.  Wonder why...
> **3rdalbum said:**
> Now your search queries get sent to a big, well-known company as part of the Shopping lens, and people are raising all sorts of objections.
Any and all searches get sent out through Canonical.  To wherever they want.  Without your intention.  Unbeknownst to you.

I fail to see the similarity.  Must be my lack of that odd sense of humor.  Sorry you don't parse that.

---

### Post by Hungry Man on 2012-10-13
Weird that you can understand music going to a music source and videos going to a video source but... you're not getting this feature.

---

### Post by NadirPoint on 2012-10-15
> **cariboo907 said:**
> why not try some research first.
I did.  maybe that is the part you don't get.

---

### Post by NadirPoint on 2012-10-18
> **cariboo907 said:**
> Instead of making baseless statements, why not try some research first.
The other part you don't seem to get is that they deliberately violate their own privacy policy by doing this.  

Maybe you are the one who needs to do some research?

---

### Post by cariboo on 2012-10-18
> **NadirPoint said:**
> Why should I have to turn it off?  I never turned it on in the first place.

Is yours turned on?

Yes it is. Are you even using 12.10?

---

### Post by Hungry Man on 2012-10-18
Most hyped issue ever. Someone tell me what exactly they're typing into the dash that's so private.

I don't know about you guys but I don't type in my credit card info or sexually deviant confessions to my dash. Maybe I'm just doing it wrong.

---

### Post by NadirPoint on 2012-10-19
> **cariboo907 said:**
> Yes it is. Are you even using 12.10?
I am presently seriously reconsidering my use of ANY Ubuntu.  I am reticent to use software produced by people who disrespect their users in this manner, freely engaging in the redistribution of P-II in violation of their own privacy policy with zero regard to their users or customers in the quest for easy advertising revenue.

---

### Post by Hungry Man on 2012-10-19
So don't. Sounds like you're having a serious fit about this and I'd say the simplest solution is to use another distro rather than, oh I don't know, think critically about the situation or take a pill.

---

### Post by cariboo on 2012-10-19
> **Hungry Man said:**
> So don't. Sounds like you're having a serious fit about this and I'd say the simplest solution is to use another distro rather than, oh I don't know, think critically about the situation or take a pill.

With that, I thinks it's time to close this thread before it degenerates into something else. Thread Closed.

---

