---
title: "Two reviews of 13.10. Interesting take on things."
date: 2013-10-17
forum: Ubuntu Development Version
---

### Post by philinux on 2013-10-17
[http://www.zdnet.com/ubuntu-13-10-saucy-salamander-review-smart-scopes-in-mir-out-7000022022/](http://www.zdnet.com/ubuntu-13-10-saucy-salamander-review-smart-scopes-in-mir-out-7000022022/)

[http://arstechnica.com/information-technology/2013/10/ubuntu-13-10-review-the-linux-os-of-the-future-remains-a-year-away/](http://arstechnica.com/information-technology/2013/10/ubuntu-13-10-review-the-linux-os-of-the-future-remains-a-year-away/)

---

### Post by grahammechanical on 2013-10-17
Considering that Mark did not want any Interim releases any more, I guess this comment in the first review is valid

> [COLOR=#252525][FONT=Georgia]*Ubuntu 13.10, rather than being a stepping-stone on the way to form-factor convergence with 14.04, seems more like an obligatory release.*[/FONT][/COLOR]

But how accurate is this comment in the second review?

> [COLOR=#263034][FONT=Arial]Unity 8 is expected to arrive on the desktop in Ubuntu 14.04, at which time Unity 7 will likely be retired from further development. [/FONT][/COLOR]

I am not disagreeing with the point that Unity 7 has reached the high point of its development but I heard that 14.04 would have Unity 7 with Unity 8 coming in 14.10. In my opinion, without Unity and the convergence strategy Ubuntu would have reached the 'obligatory release' situation long before now.

Regards.

---

### Post by philinux on 2013-10-17
Hi Graham,

I would have though for an LTS that unity 8 would be a step too far. But if they've got a lot of developers on it and it gets tested well then who knows. UDS next month will tell I guess.

---

### Post by Stinger on 2013-10-17
good read, especially the last one from Ars Technica, lots of facts about Wayland, Mir and Unity7-8 on [page 2]("http://arstechnica.com/information-technology/2013/10/ubuntu-13-10-review-the-linux-os-of-the-future-remains-a-year-away/2/").
I personally still think that Canonicals creation of thier own Mir protocol is a waste of good developer resources and I guess the same could be said about the transition from Unity7 to Unity8, the whole thingie has to be rewritten in QT. But only the future can tell ;)
The final comment on this article sums it up pretty well.


> It&#8217;s hard to get excited about the 13.10 release, but there are some major changes on the horizon that should make the next few major Ubuntu releases a lot more interesting.  

---

### Post by kansasnoob on 2013-10-17
> **grahammechanical said:**
> Considering that **[COLOR="#FF0000"]Mark did not want any Interim releases any more[/COLOR]**, I guess this comment in the first review is valid



But how accurate is this comment in the second review?



I am not disagreeing with the point that Unity 7 has reached the high point of its development but I heard that 14.04 would have Unity 7 with Unity 8 coming in 14.10. In my opinion, without Unity and the convergence strategy Ubuntu would have reached the 'obligatory release' situation long before now.

Regards.

I don't think it's true that SABDFL did not want interim releases. As I recall he stated something just opposite to that :)

As I recall some of the devs wanted to eliminate interim releases altogether and SABDFL fought that tooth-n-nail ............ then there was finally an agreement to just shorten the interim release support cycle to 9 months so the devs could focus on the [Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") in the LTS releases.

Edit: In support of what I said above please read this:

[http://www.markshuttleworth.com/archives/1228](http://www.markshuttleworth.com/archives/1228)

> The &#8216;rolling release&#8217; meme has been a popular one for years in Ubuntu. It&#8217;s one of the top requests from members of our user community. And it&#8217;s popular with Canonical team members too (who, largely, come from the community and share its values).

The problem for me is straightforward: a rolling release isn&#8217;t actually a release at all. It offers little certainty for those who need certainty. And we essentially accommodate the need for daily crack with our development releases, which have become highly usable (for developers) because of the strong commitment the Canonical and community teams made to daily quality throughout the release cycle.

So I haven&#8217;t personally given any air time to the topic of rolling releases over the years.

This year, the topic bubbled up again, and given the level of interest I supported that the core Canonical engineering team do a deep assessment of what it would actually mean, in hard pro&#8217;s and con&#8217;s, and how we might implement it, so that a straw man proposal (&#8216;one you can poke holes in&#8217;) could be presented. Rick put forward that proposal last week. It should be clear that Rick is a strong and sincere proponent of the idea, hence the passion with which the case is made, but he is not the sole decision maker.

It&#8217;s nonsense to portray Rick&#8217;s position as a final position for Ubuntu. The TB have not weighed in,  the CC (who were briefed that the assessment was being made and that a straw man would be proposed) are still considering their perspective, and I&#8217;m not convinced either. So, for those inclined to melodrama, you may want to calm down and join the conversation.
Some unexpected findings

In the course of Rick&#8217;s team&#8217;s assessment, several interesting and (to me) unexpected findings emerged.

First, there&#8217;s real confusion around interim releases. Between 12.04 LTS and 14.04 LTS there will be three interim releases on our current approach, and lots of people will find that confusing. Should ISVs target quantal AND raring AND ssssss? In practice, we have lots of data to say they can&#8217;t and won&#8217;t. PPAs are often inconsistent between interim releases. That suggests that having an &#8216;edge&#8217; release (for which PPAs would over time build up a rich source of extra software) and LTS releases may be easier on that segment of the community.

Second, we have proven the LTS point release mechanism, which brings new hardware support and new software to the LTS releases. The cloud archive, for example, brings the latest OpenStack release to 12.04 LTS, and is by far the most popular way to deploy OpenStack. Point releases have brought fresh kernels, fresh OpenStack, and fresh Unity to 12.04 LTS, and there is no reason why we could not broaden that commitment. It&#8217;s worth discussing whether that doesn&#8217;t become a better mechanism to meet the needs of people who care about a stable release.

Third, the daily quality story really has been impressive. The amazing work of a sizable quality team has transformed the widespread expectations of participants and contributors in Ubuntu &#8211; raring is really useful, every day, with little risk of unproductive hours when things go wonky. That&#8217;s grown the number of *developers* running raring, and boosted Ubuntu in other ways as a result. I&#8217;m not convinced it&#8217;s good enough for end-users, but it&#8217;s worth digging in to see how it could get there.
Some unrealistic expectations

In the commentary I&#8217;ve seen during the course of the discussion, some of the expectations expressed by stakeholders strike me as unrealistic.

Ben Collins&#8217; perspective, which addresses the need of a PowerPC OEM, is an example. Ben is a friend and former colleague, I&#8217;d like to be supportive, but the real cost of supporting an architecture is way outside the scope of Ubuntu&#8217;s non-commercial commitments. IBM and Canonical discussed bringing Ubuntu to the PowerPC architecture some years ago and chose not to; the gap is not something Canonical will close alone. I&#8217;m delighted if Ubuntu is useful for Ben, and pretty certain it will remain the best platform for his work regardless, but we should not spend millions of dollars on that rather than cloud computing or mobile, which have a much broader impact on both society and our commercial prospects.
Some unwarranted melodrama

The sky is not falling in.

Really.

Ubuntu is a group of people who get together with common purpose. How we achieve that purpose is up to us, and everyone has a say in what they can and will contribute. Canonical&#8217;s contribution is massive. It&#8217;s simply nonsense to say that Canonical gets &#8216;what it wants&#8217; more than anybody else. Hell, half the time *I* don&#8217;t get exactly what I want. It just doesn&#8217;t work that way: lots of people work hard to the best of their abilities, the result is Ubuntu.

The combination of Canonical and community is what makes that amazing. There are lots of pure community distro&#8217;s. And wow, they are full of politics, spite, frustration, venality and disappointment. Why? Because people are people, and work is hard, and collaboration is even harder. That&#8217;s nothing to do with Canonical, and everything to do with life. In fact, in most of the pure-community projects I&#8217;ve watched and participated in, the biggest meme is &#8216;if only we had someone that could do the heavy lifting&#8217;. Ubuntu has that in Canonical &#8211; and the combination of our joint efforts has become the most popular platform for Linux fans.

If you&#8217;ve done what you want for Ubuntu, then move on. That&#8217;s normal &#8211; there&#8217;s no need to poison the well behind you just because you want to try something else.

It&#8217;s also the case that we&#8217;ve shifted gear to leadership rather than integration.

When we started, we said we wanted to deliver the best of open source on a cadence. It was up to KDE, GNOME, XFCE to define what that was going to look like, we would just integrate and deliver (a hard problem in itself). By 2009 I was convinced that none of the existing free software communities could create an experience that could challenge the existing proprietary leaders, and so, if we were serious about the dream of a free software norm, we would have to lead.

The result is Unity, which is an experience that could become widely adopted across phones, tablets, PCs and other devices. Of course, that is a disruptive change, and has caused some members of existing communities to resent our work. I respect that others may prefer different experiences, so we remain willing to do a large (but not unlimited) amount of work to enable KDE, GNOME, and other DEs to thrive inside the broader Ubuntu umbrella. We also take steps to accommodate developers who want to support both Unity and another DE. But if we want to get beyond being a platform for hobbyists, we need to accelerate the work on Unity to keep up with Android, Chrome, Windows and Apple. And that&#8217;s more important than taking care of the needs of those who don&#8217;t share our goal of a free software norm.
A once-in-a-lifetime opportunity

Everyone that I care about in open source has a shared dream: they want free software to become the norm, not the exception. And Ubuntu is the only way I can see for that to happen, which is why I spend all my time on it, and why so many other people spend huge amounts of time on it too.

I simply have zero interest in the crowd who wants to be different. Leet. &#8216;Linux is supposed to be hard so it&#8217;s exclusive&#8217; is just the dumbest thing that a smart person could say. People being people, there are of course smart people who hold that view.

What I&#8217;m really interested in is this once-in-a-lifetime opportunity to create a free and open platform that is THE LEADER across both consumer and enterprise computing.

With Ubuntu (and Unity) we have that. It&#8217;s amazing. Think about it &#8211; unlike years gone by, a free software platform is actually winning awards for innovative leadership in the categories that count: mobile, cloud. Investing your time and energy here might have a truly profound impact on the world. That&#8217;s worth digging into. Just roll your eyeballs at the 1337 crowd, roll up your sleeves, find something interesting to improve, and join in. To the extent that you can master a piece, you will get what you want. If you think the grand vision should follow your whims, you won&#8217;t.

If we work hard, and work together, Ubuntu will become a widespread platform for phones, tablets and PCs. You&#8217;ll have the satisfaction of designing, building and fixing tools that are used every day by millions of people. That&#8217;s meaningful. And it&#8217;s worth looking hard at our practices to ask the question: how best to achieve that goal? Of those practices, interim releases are just as subject to evaluation and revision as any other.
Going faster

So, rolling releases are not real releases.

But cadence is good, releases are good discipline even if they are hard. In LEAN software engineering, we have an interesting maxim: when something is hard, DO IT MORE OFTEN. Because that way you concentrate your efforts on the hard problem, master it, automate and make it easy. That&#8217;s the philosophy that underpins agile development, devops, juju and loads of other goodness.

In the web-lead world, software is moving faster than ever before. Is six months fast enough?

So I think it IS worth asking the question: can we go even faster? Can we make even MORE releases in a year? And can we automate that process to make it bulletproof for end-users?

That&#8217;s where I think we should steer the conversation on rolling releases:

    Can we make the update process from point to point really bulletproof? Upgrading today is possible, but to keep the system clean over multiple successive upgrades requires an uncommonly high level of skill with APT.
    Can we strengthen the definition of point releases in the LTS so that interim releases are obviously less relevant?
    Can we do a reasonable amount of release management on, say, MONTHLY releases that they are actual releases rather than just snapshots?

Daily quality has made the Ubuntu development release perfectly usable for developers. That&#8217;s a huge accomplishment. Now let&#8217;s think carefully about the promises we&#8217;re making end-users, and see if it isn&#8217;t time to innovate again, just as we innovated when we created Ubuntu on a six month cadence.

---

### Post by craig10x on 2013-10-17
Yeah...actually the developers final decision at the conference was that as far as they were concerned DEVELOPMENT is the official rolling release...there won't be a "stable" version of rolling.... and i believe Mark goes along with this too... But they have one of the developers working on a symlink (Colin as i described in another thread) to make it easy to transition or "roll" into each new development release without having to manually change source lists...

However, there is some bugs in it that he has to work out and based on his e-mail reply to me, it doesn't sound like it will be ready for the 14.04 transition...

As an ubuntu developer he has a lot of things he has to work on, and i would imagine this is just a side project he works on when he has the time...

---

