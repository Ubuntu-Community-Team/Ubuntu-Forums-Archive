---
title: "From Mark Shuttleworth's blog: meta-cycles"
date: 2009-04-17
forum: The Cafe
---

### Post by Tobine on 2009-04-17
Anybody care to share their opinions on this? Do you think that regular quick releases hinder major changes or do they still come over time?

Discuss

> 

Six-month cycles are great. Now let&#8217;s talk about meta-cycles: broader release cycles for major work. I&#8217;m very interested in a cross-community conversation about this, so will sketch out some ideas and then encourage people from as many different free software communities as possible to comment here. I&#8217;ll summarise those comments in a follow-up post, which will no doubt be a lot wiser and more insightful than this one :-)

Background: building on the best practice of cadence

The practice of regular releases, and now time-based releases, is becoming widespread within the free software community. From the kernel, to GNOME and KDE, to X, and distributions like Ubuntu, Fedora, the idea of a regular, predictable cycle is now better understood and widely embraced. Many smarter folks than me have articulated the benefits of such a cadence: energising the whole community, REALLY releasing early and often, shaking out good and bad code, rapid course correction.

There has been some experimentation with different cycles. I&#8217;m involved in projects that have 1 month, 3 month and 6 month cycles, for different reasons. They all work well.

..but addressing the needs of the longer term

But there are also weaknesses to the six-month cycle:

    * It&#8217;s hard to communicate to your users that you have made some definitive, significant change,
    * It&#8217;s hard to know what to support for how long, you obviously can&#8217;t support every release indefinitely.

I think there is growing insight into this, on both sides of the original &#8220;cadence&#8221; debate.

A tale of two philosophies, perhaps with a unifying theory

A few years back, at AKademy in Glasgow, I was in the middle of a great discussion about six month cycles. I was a passionate advocate of the six month cycle, and interested in the arguments against it. The strongest one was the challenge of making &#8220;big bold moves&#8221;.

&#8220;You just can&#8217;t do some things in six months&#8221; was the common refrain. &#8220;You need to be able to take a longer view, and you need a plan for the big change.&#8221; There was a lot of criticism of GNOME for having &#8220;stagnated&#8221; due to the inability to make tough choices inside a six month cycle (and with perpetual backward compatibility guarantees). Such discussions often become ideological, with folks on one side saying &#8220;you can evolve anything incrementally&#8221; and others saying &#8220;you need to make a clean break&#8221;.

At the time of course, KDE was gearing up for KDE 4.0, a significant and bold move indeed. And GNOME was quite happily making its regular releases. When the KDE release arrived, it was beautiful, but it had real issues. Somewhat predictably, the regular-release crowd said &#8220;see, we told you, BIG releases don&#8217;t work&#8221;. But since then KDE has knuckled down with regular, well managed, incremental improvements, and KDE is looking fantastic. Suddenly, the big bold move comes into focus, and the benefits become clear. Well done KDE :-)

On the other side of the fence, GNOME is now more aware of the limitations of indefinite regular releases. I&#8217;m very excited by the zest and spirit with which the &#8220;user experience MATTERS&#8221; campaign is being taken up in Gnome, there&#8217;s a real desire to deliver breakthrough changes. This kicked off at the excellent Gnome usability summit last year, which I enjoyed and which quite a few of the Canonical usability and design folks participated in, and the fruits of that are shaping up in things like the new Activities shell.

But it&#8217;s become clear that a change like this represents a definitive break with the past, and might take more than a single six month release to achieve. And most important of all, that this is an opportunity to make other, significant, distinctive changes. A break with the past. A big bold move. And so there&#8217;s been a series of conversations about how to &#8220;do a 3.0&#8243;, in effect, how to break with the tradition of incremental change, in order to make this vision possible.

It strikes me that both projects are converging on a common set of ideas:

    * Rapid, predictable releases are super for keeping energy high and code evolving cleanly and efficiently, they keep people out of a deathmarch scenario, they tighten things up and they allow for a shakeout of good and bad ideas in a coordinated, managed fashion.

    * Big releases are energising too. They are motivational, they make people feel like it&#8217;s possible to change anything, they release a lot of creative energy and generate a lot of healthy discussion. But they can be a bit messy, things can break on the way, and that&#8217;s a healthy thing.

Anecdotally, there are other interesting stories that feed into this.

Recently, the Python community decided that Python 3.0 will be a shorter cycle than the usual Python release. The 3.0 release is serving to shake out the ideas and code for 3.x, but it won&#8217;t be heavily adopted itself so it doesn&#8217;t really make sense to put a lot of effort into maintaining it - get it out there, have a short cycle, and then invest in quality for the next cycle because 3.x will be much more heavily used than 3.0. This reminds me a lot of KDE 4.0.

So, I&#8217;m interesting in gathering opinions, challenges, ideas, commitments, hypotheses etc about the idea of meta-cycles and how we could organise ourselves to make the most of this. I suspect that we can define a best practice, which includes regular releases for continuous improvement on a predictable schedule, and ALSO defines a good practice for how MAJOR releases fit into that cadence, in a well structured and manageable fashion. I think we can draw on the experiences in both GNOME and KDE, and other projects, to shape that thinking.

This is important for distributions, too

The major distributions tend to have big releases, as well as more frequent releases. RHEL has Fedora, Ubuntu makes LTS releases, Debian takes cadence to its logical continuous integration extreme with Sid and Testing :-).

When we did Ubuntu 6.06 LTS we said we&#8217;d do another LTS in &#8220;2 to 3 years&#8221;. When we did 8.04 LTS we said that the benefits of predictability for LTS&#8217;s are such that it would be good to say in advance when the next LTS would be. I said I would like that to be 10.04 LTS, a major cycle of 2 years, unless the opportunity came up to coordinate major releases with one or two other major distributions - Debian, Suse or Red Hat.

I&#8217;ve spoken with folks at Novell, and it doesn&#8217;t look like there&#8217;s an opportunity to coordinate for the moment. In conversations with Steve McIntyre, the current Debian Project Leader, we&#8217;ve identified an interesting opportunity to collaborate. Debian is aiming for an 18 month cycle, which would put their next release around October 2010, which would be the same time as the Ubuntu 10.10 release. Potentially, then, we could defer the Ubuntu LTS till 10.10, coordinating and collaborating with the Debian project for a release with very similar choices of core infrastructure. That would make sharing patches a lot easier, a benefit both ways. Since there will be a lot of folks from Ubuntu at Debconf, and hopefully a number of Debian developers at UDS in Barcelona in May, we will have good opportunities to examine this opportunity in detail. If there is goodwill, excitement and broad commitment to such an idea from Debian, I would be willing to promote the idea of deferring the LTS from 10.04 to 10.10 LTS.

Questions and options

So, what would the &#8220;best practices&#8221; of a meta-cycle be? What sorts of things should be considered in planning for these meta-cycles? What problems do they cause, and how are those best addressed? How do short term (3 month, 6 month) cycles fit into a broader meta-cycle? Asking these questions across multiple communities will help test the ideas and generate better ones.

What&#8217;s a good name for such a meta-cycle? Meta-cycle seems&#8230;. very meta.

Is it true that the &#8220;first release of the major cycle&#8221; (KDE 4.0, Python 3.0) is best done as a short cycle that does not get long term attention? Are there counter-examples, or better examples, of this?

Which release in the major cycle is best for long term support? Is it the last of the releases before major new changes begin (Python 2.6? GNOME 2.28?) or is it the result of a couple of quick iterations on the X.0 release (KDE 4.2? GNOME 3.2?) Does it matter? I do believe that it&#8217;s worthwhile for upstreams to support an occasional release for a longer time than usual, because that&#8217;s what large organisations want.

Is a whole-year cycle beneficial? For example, is 2.5 years a good idea? Personally, I think not. I think conferences and holidays tend to happen at the same time of the year every year and it&#8217;s much, much easier to think in terms of whole number of year cycles. But in informal conversations about this, some people have said 18 months, others have said 30 months (2.5 years) might suit them. I think they&#8217;re craaaazy, what do you think?

If it&#8217;s 2 years or 3 years, which is better for you? Hardware guys tend to say &#8220;2 years!&#8221; to get the benefit of new hardware, sooner. Software guys say &#8220;3 years!&#8221; so that they have less change to deal with. Personally, I am in the 2 years camp, but I think it&#8217;s more important to be aligned with the pulse of the community, and if GNOME / KDE / Kernel wanted 3 years, I&#8217;d be happy to go with it.

How do the meta-cycles of different projects come together? Does it make sense to have low-level, hardware-related things on a different cycle to high-level, user visible things? Or does it make more sense to have a rhythm of life that&#8217;s shared from the top to the bottom of the stack?

Would it make more sense to stagger long term releases based on how they depend on one another, like GCC then X then OpenOffice? Or would it make more sense to have them all follow the same meta-cycle, so that we get big breakage across the stack at times, and big stability across the stack at others?

Are any projects out there already doing this?

Is there any established theory or practice for this?

A cross-community conversation

If you&#8217;ve read this far, thank you! Please do comment, and if you are interested then please do take up these questions in the communities that you care about, and bring the results of those discussions back here as comments. I&#8217;m pretty sure that we can take the art of software to a whole new level if we take advantage of the fact that we are NOT proprietary, and this is one of the key ways we can do it.


[http://www.markshuttleworth.com/archives/288](http://www.markshuttleworth.com/archives/288)

---

### Post by Skripka on 2009-04-17
It is a tough call.

Especially with Ubuntu's stated theories regarding what gets into official repos, what only gets backported, and what is called 'stable" when.

-Shorter monolithic release cycles are good, as people get newer, and theoretically better software sooner.  They are bad because devs have less time to fix things, less time to develop things....and *very* bad because end users only just get used to their old system before the new release comes--which theym may *need* for 3rd party softwares X,Y, and Z.  I will say, that I always hate having to reinstall OSes to get the new stuff-it always involves time and or headaches.

-Longer monolithic cycles are good, as people have time to fix and develop ideas...but conversely end-users must back port more and more...and eventually the official repos are so dated that things cannot get backported due to newer depends.

-And as Shuttleworth points out, it gets even more messy, as Ubuntu packages Debian, amongst many other packages form other devs...who more likely than not will not have a monolithic release schedule synced with Ubuntu's.  So no matter what you do, you cannot hope to catch all or most of the eggs.

So, which do you choose-and how do you balance it?

The root of the problem stems from the monolithic release strategy.  Of course, I know making Ubuntu a rolling release system is not a valid or acceptable answer.

-6 months as it is, is best for the end-user.  Methinks.  Every distro release doesn't lag too far behind other major projects.

but

-For the devs, methinks they could use and need more than 6 months to draft, develop, and test new ideas extensively.


Of course, we are also speaking of Gnome here.  The problem being fundamentally-I think there's probably a majority of end-users who are basically happy with Gnome as it is-with no desire to remake the wheel.  But, to get more users o'er from blingy OSes such as WinVista/7 and OSX-they'll want more eyecandy.  

So, it boils down in the long runt to who do you try to please, and why---and how do you keep the other population (that didn't get their way) happy....especially since in FOSS community, if people don't like something they have no qualms about going elsewhere.

---

### Post by ubuntu27 on 2009-04-17
The OP's quote is from

[http://www.markshuttleworth.com/archives/288](http://www.markshuttleworth.com/archives/288)

---

### Post by ghindo on 2009-04-17
[http://ubuntuforums.org/showthread.php?t=1128372](http://ubuntuforums.org/showthread.php?t=1128372)

---

### Post by blastus on 2009-04-17
Shorter development cycles with incremental releases provide a tighter feedback loop. Such feedback is essential in Agile driven development and facilitates refactoring and continuous integration. Longer development cycles increase the risk of product failure; for example, Windows Vista.

---

### Post by gnomeuser on 2009-04-18
I think if you cannot break your big change into bits that can be implemented and tested in 6 month cycles then your design has serious problems. If you can do the work required in 3 months then use the remaining 3 to write test suites to ensure correctness and performance is good. There is no reason that the major project shouldn't release every 6 months.

One of the reasons why 6 month cycles have been so successful is that it's short enough to let us do many changes and have them out in peoples hands for testing. The feedback loop is narrowed considerably and progress has been very fast paced in the last few years. Stability has also not been affected adversely. Demands for an enterprise distribution are a little different, there are certification processes to complete to be able to prove that you can do what you claim. There is that extra testing that goes into making sure a product is supportable for 7 years (10 in special cases for Red Hat's Enterprise releases).

There are different demands for the two deployment types, however your enterprise product relies heavily on continued development to roll fixes and updates into the enterprise products. This is what we pay Red Hat to do, e.g. they don't rebase the kernel, they backport large amounts of code to keep the API stable. This is not a good tactic for a 6 month cycle powered largely by volunteers. 

I think a testament to what you can do in 6 month cycles is GNOME 3.0. Everything leading up to 3.0 has been done in 6 month cycles. Projects that have needed longer time have piped in required changes over the cycles to provide new features and API. Then we drop in functionality one bit at the time. Evolution doesn't stop because we have releases, it just forces us to do manageable sized changes.

I am extremely frightened everytime someone starts thinking we should go back to the way we used to develop the kernel with long unstable versions followed by a flag day. It will never work as well as quick releases with corrective feedback. In the same sense I am worried when we start wondering if we need more time to do big changes. It smells of poor design and implementation if we cannot do it in little manageable and testable bits. Poor design that will bite us on the rear, quickly.

If I might recommend reading Richard Dawkins' Climbing Mount Improbable to anyone who thinks otherwise.

---

### Post by blastus on 2009-04-18
> **gnomeuser said:**
> I think if you cannot break your big change into bits that can be implemented and tested in 6 month cycles then your design has serious problems. If you can do the work required in 3 months then use the remaining 3 to write test suites to ensure correctness and performance is good. There is no reason that the major project shouldn't release every 6 months.

Actually testing is not one big separate task that you do at the end but it should be an integral part of the development cycle. Ideally, you write a test case first, see it fail, write or refactor just enough code to make the test pass, then go back and write another test case etc... Spending 3 months writing a feature then 3 months writing unit tests for it is not a good way to develop because...

1. You'll almost certainly write code that is not amenable to being tested (a.k.a. god classes/functions, tightly coupled components etc...)
2. You'll just write tests against the code that are designed to pass instead of writing code that is designed to conform to a test specification

---

### Post by 4th guy on 2009-04-18
One solution would be to keep the 6-month release cycle.

Use the *.04 version to tweak the OS, update packages, (simple) new functionality)
Use the *.10 version to test out more "radical" things like completely new functions and new (non default) themes, minor tweakage and (of course) update packages.

I'm not saying that the *.10 release should be some sort of beta test, but more of a feedback thing. Maybe someone else would perhaps give their input on this.

---

### Post by Tobine on 2009-04-18
> **ubuntu27 said:**
> The OP's quote is from

[http://www.markshuttleworth.com/archives/288](http://www.markshuttleworth.com/archives/288)

Thanks. Completely forgot the link.

> **ghindo said:**
> [http://ubuntuforums.org/showthread.php?t=1128372](http://ubuntuforums.org/showthread.php?t=1128372)

Sorry, didn't see your post

---

### Post by MikeMLP on 2009-04-19
I have a legit comment that keeps getting flagged by the spam filter on Mark's blog - go figure.  So, I'm going to post here:

It seems to me that Mark's post, and much of the discussion so far is rather detail-heavy when maybe the discussion should be a little more broad. For example, Mark asks how would project X fit into distro Y, and if any individual _projects_ have best practices for coordinating releasees. Suppose we find that certain projects do, or, even more likely, that projects make major and minor releases whenever their communities and codebases decide that it is time to do so, and they coordinate with other projects through ad-hoc communication. What then? What is the next step? I think that’s a major question that his post leaves unasked. 

If everyone across the community can generally agree that fixing bug number one is their primary goal, or, at least that increasing linux platform marketshare rapidly is a shared fundamental goal, then why not try to get the great weight of the community behind a “linux core platform” idea - for the desktop, that would include the stack from X on down, a single package system, plus maybe a choice of KDE (pitched for programmers, enthusiasts and the like) or gnome (for government and business officeworkers)? 

I think the Ubuntu model of 6-month releases plus an LTS has worked well - There’s a reason why Ubuntu is a leader - customers love the predictability. Keeping the ‘customer satisfaction’ idea in mind, that should be grafted onto the release of a “linux core platform” by the community as a whole -eg: ‘these are the versions of these software projects that will be our baseline supported releases for the next 2-3 years, and we’re calling it ‘linux core platform 1.0,’ or something of that nature. Keep the 6-month releases for testers, enthusiasts, and for responding quickly to the competition, so that they never gets more than a 6 month window to have a feature we don’t have.

This would accomplish two goals which have already been discussed by those responding on Mark's blog, both relating to fundamental weaknesses - fragmentation. 

First, a core platform that the community pushes with one voice would greatly simplify the information gathering and marketing process to potential growth markets. Right now, every distro does that on their own, and each distro is relatively small. The message to potential customers is confusing, varied, and difficult to keep track of. What’s a Fedora, an Ubuntu, a Suse, a Red Hat? Why should I choose one over the other? I think that complexity turns a lot of people away. People want to know what they’re getting, when they’re getting it, and how it will make their lives easier. That’s all. If it is at all difficult to find that out, or if that information must be found by sifting through technobabble, they’ll move on to someone who can make a better, simpler pitch.

At the distro level, why not combine resources, working together on research and marketing for the linux platform as a whole, and have each distro devote itself to competing on services and specialty solutions for specific customers or groups of customers? Isn’t this the business model right now anyway? 

Second, if there were some ‘linux core platform,’ with a single message, and a community-wide release schedule that everyone was aware of, then that alone would be enough to kick the community’s focus into high gear. I think right now people don’t really know who they’re writing software for. If we could focus creative energy on certain groups of people who need their software to do certain types of things, then we’d do a better job at giving customers systems of tools that work together, doing what they want when they want it. I don’t think individual project autonomy on releases would go by the wayside, but if everyone, say, had ‘what are we going to do for core platform 2.0?,’ 'how will our software x work with y in the core platform to provide a more efficient environment for [programmer/office worker/ enthusiast] in this core release?,' in their head, then that in itself would be enough to kick development up to the next level. And that’s really what Mark wants, I think, isn’t it?

P.S. I highly recommend “Mastering the Dynamics of Innovation” by James M. Utterback, and “The Visible Hand” by Alfred D. Chandler.” Mastering, focusing, and driving the open source model is precisely what Mark, and a lot of other free software leaders and entrepreneurs are trying to do. No one’s quite mastered it yet on the platform-level scale, so that’s why I don’t think Mark will necessarily find any ‘best practices’ for what he really wants to do.

---

