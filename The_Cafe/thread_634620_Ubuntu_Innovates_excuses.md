---
title: "Ubuntu Innovates excuses?"
date: 2007-12-07
forum: The Cafe
---

### Post by loell on 2007-12-07
from [http://www.oreillynet.com/linux/blog/2007/12/ubuntu_innovates_excuses.html?CMP=OTC-0O724Z062301&ATT=Ubuntu+Innovates+Excuses]("http://www.oreillynet.com/linux/blog/2007/12/ubuntu_innovates_excuses.html?CMP=OTC-0O724Z062301&ATT=Ubuntu+Innovates+Excuses")  

and

[http://shallowsky.com/blog/linux/ubuntu-aumix.html]("http://shallowsky.com/blog/linux/ubuntu-aumix.html")

Apparently both articles criticizes ubuntu for not fixing the **Aumix** package after a launchpad  bug report, Instead a response was made pointing out the **SRU policy** as the reason that it can't be fixed. 

the articles said the fix was to   just recompile the package and nothing more.

your opinions?

---

### Post by Vadi on 2007-12-07
I did see several unsatisfactory answers on Launchpad, yes.

But they aren't that big of a deal to make a whole story about.

---

### Post by blithen on 2007-12-07
In my opinion this really isn't that big of a deal.
It just adjusts an audio mixer...[http://www.jpj.net/~trevor/aumix.html](http://www.jpj.net/~trevor/aumix.html)
Really..come on. Two articles on it?
They probably just came up with an excuse 'cause they didn't feel like doing something that tedious.

---

### Post by 23meg on 2007-12-07
[QUOTE=blithen]They probably just came up with an excuse 'cause they didn't feel like doing something that tedious.[/QUOTE]

It's not an excuse; it's policy. If policy is adhered to too strongly, that displeases people at times. It's not possible to make everyone happy all the time, and keep things healthy at the same time.

---

### Post by hanzomon4 on 2007-12-07
Why don't they just fix(recompile) the damn thing?

---

### Post by ruibernardo on 2007-12-08
I think the "excuses" or SRU policies suck sometimes. Don't know about the links, but I know about firehol (feisty and gutsy).

 If a security release is done (firefox or other thing), it gets to updates or security and is applied to everyone.

If a bug of an application that never worked, not even while the development and the bug is fixed later, it gets to backport (not supported updates) when it does get there, because sometimes it's just in the next release.

If there was an error or problem during the development of the release, why don't the solutions appear in the normal repositories to solve the bug? That would be a thing to get stability.

What is the stability of an OS when an application doesn't work and all users apply different solutions they find on the internet. I think that is not stability, it's a pandemonium.

---

### Post by 23meg on 2007-12-08
[QUOTE=epimeteo]If there was an error or problem during the development of the release, why don't the solutions appear in the normal repositories to solve the bug?[/QUOTE]

They don't?

---

### Post by boast on 2007-12-08
I guess I'll stop sending bug reports relating to ubuntu.

---

### Post by 23meg on 2007-12-08
> **boast said:**
> I guess I'll stop sending bug reports relating to ubuntu.

Why? Because someone you don't even know commented on an article that "filing bugs is useless", without even providing any reasoning?

Don't just take everyone's word.

---

### Post by ruibernardo on 2007-12-08
Oh, I'm terribly sorry. My bad. Firehol was [recently fixed]("https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017") and got to updates. I'm not using it anymore because of the bug, so I've missed that. 

But I know another one (qemu: [https://bugs.launchpad.net/bugs/144368](https://bugs.launchpad.net/bugs/144368)) and this one is included on the SRU policies (will not get to updates). 

EDIT: sorry for this edit. Qemu still hasn't a solution, but it's already saying that it will not be included on the updates.

---

### Post by hanzomon4 on 2007-12-08
> **23meg said:**
> Why? Because someone you don't even know commented on an article that "filing bugs is useless", without even providing any reasoning?

Don't just take everyone's word.

Well, If the devs won't fix the problem why bother?

---

### Post by Serenitude on 2007-12-08
How many people are still greeted with "Monitor cannot display this video mode" or something similar due to the splash screen being incorrectly configured? Bug reports were filed on this before Gutsy was even released. The causes and solutions were posted, in forums and on launchpad. Using "startup manager" or correctly running initramfs after setting the correct resolution corrects the problem and can shave alot of time off of your boot, to, well, boot :lolflag:

The first thing I always have to do when installing Gutsy for a windows refugee with an LCD monitor is explain that Linux/Ubuntu isn't buggy, geek-oriented, and crapware because the first thing they see is this screen, and my CLI work, which they then fear they won't have to learn just to use the OS. 

And yet, still no fix :confused: Have to agree with the article. Reporting bugs doesn't seem to do a whole lot of good. LOVE the OS, don't get me wrong, but bug reporting seems a useless excersize. It's more of "I hope they actually decide to fix this problem/package someday."

---

### Post by Dimitriid on 2007-12-08
Gutsy is a big regression overall and it broke a lot of working things. Im not gonna waste my time reporting bugs on a distro that uses such an unreasonable approach to policy adherence. Specially when they ASK for bugs and problems by doing things like putting compiz-fusion enabled by default.

---

### Post by adam.tropics on 2007-12-08
> **Dimitriid said:**
> Gutsy is a big regression overall and it broke a lot of working things. Im not gonna waste my time reporting bugs on a distro that uses such an unreasonable approach to policy adherence. Specially when they ASK for bugs and problems by doing things like putting compiz-fusion enabled by default.

Pretty sure the Ubuntu folk never made a secret of the fact that they would be pushing bleeding(ish) edge stuff and generally more up to date version packages etc. Added to that, with the one exception, they only have the 6 month release cycle. So what do you want? Maybe stick to LTS versions? I know many do, it suits their needs better, and for most of them this is exactly why.

As for not reporting more bugs, well that smacks of the whole baby and bathwater thing, and frankly helps nobody, least of all, you.

---

### Post by 23meg on 2007-12-08
> **hanzomon4 said:**
> Well, If the devs won't fix the problem why bother?

Do you have a way of divining that they won't before filing the bug?

---

### Post by subs on 2007-12-08
personally .... i havent had any such problems with launchpad.....

but this does make u think.....

---

### Post by Krydahl on 2007-12-08
No, the story is nonsense.

The basic policy makes sense.

There are a limited numbers of devs. They have a six month release cycle to cope with. Once the official built is out of the door, they don't want to break it completely by trying to fix something minor.

So, simple policy, don't fix things in that release unless they're critical. Always test the fix in the development branch first to make sure it doesn't screw things up.

I've worked in a big software company trying to coordinate multiple versions of software and it can be a nightmare. This sort of policy is just common sense. I'll bet that they use that standard phrase (quoted in the stories) whenever they find a bug that breaks this policy - regardless of what the bug is.

Now you might say that in this case it's a trivial fix, but what you have to bear in mind is that someone has to sit down with that bug, check that whoever claims you can just recompile is right, install it, do some sort of regression test to make sure nothing else is upset and then put the recompile into the repos.

Now multiply that by the number of bugs they've got to manage and you start to see why the answer is, "this breaks policy. It will be sorted in Hardy." 

If these folk want to help, they'd be better off doing the recompile themselves and putting it in a third party repo instead of displaying their ignorance of basic quality control principles by writing silly stories.

---

### Post by saulgoode on 2007-12-08
> **Krydahl said:**
> So, simple policy, don't fix things in that release unless they're critical. Always test the fix in the development branch first to make sure it doesn't screw things up.

Having binary builds and source code out-of-sync should be considered a security problem (how do you trust the binary has not been compromised en route?) and a potential violation of the copyright licensing (melodramatic? yes, but should Ubuntu place itself in such a position). Both of these would be, in my opinion, "critical" issues.

---

### Post by Krydahl on 2007-12-08
And I'm sure there's a system by which you can argue that to the devs. If you do, perhaps they will reconsider for this particular bug.

My point is that saying that the policy is a mistake or is "making up excuses" demonstrates a lack of understand of the scale of the issue being managed here.

---

### Post by ruibernardo on 2007-12-08
I like Ubuntu, but Ubuntu seems to be stuck between Debian unstable and a stable distro policy.
> **Krydahl said:**
> If these folk want to help, they'd be better off doing the recompile themselves and putting it in a third party repo instead of displaying their ignorance of basic quality control principles by writing silly stories.
> **saulgoode said:**
> Having binary builds and source code out-of-sync should be considered a security problem (how do you trust the binary has not been compromised en route?) and a potential violation of the copyright licensing (melodramatic? yes, but should Ubuntu place itself in such a position). Both of these would be, in my opinion, "critical" issues.
 All this leads to third party repositories with packages compiled by god knows who and with what sources. and completely escapes to the quality system that the official policy wants to assure. That is the "pandemonium" I was talking about.

The policy is somewhat inconsistent.

---

### Post by saulgoode on 2007-12-08
> **Krydahl said:**
> My point is that saying that the policy is a mistake or is "making up excuses" demonstrates a lack of understand of the scale of the issue being managed here.

Neither of the weblog authors called the *policy* a mistake. And misapplying the policy in response to a bug report could justifiably be termed "making up excuses" (though I would probably be more reserved myself).

Actually, I think it is the Ubuntu developers who are demonstrating a lack of understanding of the scale of this issue. 

Why is it that three different reports that rebuilding the sources corrects the problem is not sending up a red flag calling for an investigation? If the users employed different build flags than the automated package builder, should not those differences and their consequences be researched? If the binaries somehow became corrupted *after *compilation then should not it be of utmost importance to determine where and how that happened? 

I fully understand the importance of efficiently managing development resources and the policy of reluctance to backport non-essential bug fixes. But in this case, Bug #145805 suggests the potentiality of a problem endemic to the Ubuntu build or delivery process. It is critical that the Ubuntu developers investigate these concerns.

---

### Post by 23meg on 2007-12-08
The bug has never been rejected. Its status is "Triaged", which means that it's as accepted as can be. What was rejected was the nomination for a SRU.

And it's now been indicated on the bug that the rejection of the nomination was incorrect. The main basis of the rejection was that the bug wasn't fixed in Hardy yet, and it now is, thanks to a new version. So it's been accepted again. The policy is not to reject a nomination unless there's an obvious reason not to deploy a fix. Here there wasn't one; it was just that the status of the bug at the time of the nomination didn't qualify for a SRU. 

What's the big deal? Does this mishap justify blowing the issue out of proportion with a statement like "Ubuntu's lack of quality control"? It's just that someone's pet package is broken, and until it was broken, things were all fine, as it were.

People setting wrong statuses, incorrectly rejecting nominations and the like are things that happen occasionally in the bug tracker. Sure, high standards need to be maintained, but nobody is perfect; people do make mistakes. The MOTU SRU policy is [undergoing a transition]("https://lists.ubuntu.com/archives/ubuntu-devel/2007-November/024776.html"), which might have something to do with the mishap, and which in any case indicates that processes are being tweaked constantly to optimize the results. 

[QUOTE=Krydahl]Now multiply that by the number of bugs they've got to manage and you start to see why the answer is, "this breaks policy. It will be sorted in Hardy."

If these folk want to help, they'd be better off doing the recompile themselves and putting it in a third party repo instead of displaying their ignorance of basic quality control principles by writing silly stories.
[/QUOTE]

The MOTU team has tens of thousands of packages and bugs on their hands, and they consist of 80 people, not all of whom are active all the time, so they're in constant need of help; people who aren't MOTUs can actually perform all MOTU tasks through sponsorship of a MOTU. It's just a case of whether you want to actually help, or just make a noise. These people chose to do the latter; they just wanted to make sensational blog posts, and they wanted their own problem fixed.

---

### Post by Krydahl on 2007-12-08
> **saulgoode said:**
> Neither of the weblog authors called the *policy* a mistake.

From the second of the linked blogs:

> I've been running on Ubuntu's latest, "Gutsy gibbon", for maybe a month now. Like any release, it has its problems that I've needed to work around. Like many distros, these problems won't be fixed before the next release. But unlike other distros, it's not just lack of developer time; it turns out Ubuntu's developers point to an official policy as a reason not to fix bugs.

Take the case of the aumix bug.

How is that not an attack on the general policy using this bug as an example?

---

### Post by tehet on 2007-12-08
> **23meg said:**
> It's just that someone's pet package is broken, and until it was broken, things were all fine, as it were.
Yeah that's pretty typical. Everything is nice and dandy until they have a personal gripe and then all of a sudden the entire distro is rotten. But most of all these folks need something to write about and it was a slow news day.

Also reminds me of the day light saving thingy in Debian a while back, which was a non-issue because the patch was available in volatile.

---

### Post by Vadi on 2007-12-08
> **tehet said:**
> Yeah that's pretty typical. Everything is nice and dandy until they have a personal gripe and then all of a sudden the entire distro is rotten.

I think that's the real issue. Some people just cannot understand that there are limited resources, and that there are way more bugs marked as "critical" than of one app not launching. That's just really poor form.

And where were those geniuses during the alphas, betas, and release candidates?

---

### Post by Serenitude on 2007-12-08
Reporting bugs, in some cases, which remain unfixed to this day. Still using Ubuntu, loving it, not blogging "Ubuntu sucks". But getting increasingly frustrated at the bug %. Ubuntu is the 700 pound gorilla of Linux. Ubuntu wants to take the world from Microsoft. And yet, even this thread rather makes a point for the blathering bloggers - lots of excuses, reasons why *buntu ships with so many bugs, why they go vastly unfixed, etc... This is a frustrating read for those of us that DO want a stable Ubuntu OS to promote to friends, family, and help poise to take over the world ;-)

BTW: Installed Dapper last night, and all is well :-)

---

### Post by hanzomon4 on 2007-12-08
> **Vadi said:**
> I think that's the real issue. Some people just cannot understand that there are limited resources, and that there are way more bugs marked as "critical" than of one app not launching. That's just really poor form.

And where were those geniuses during the alphas, betas, and release candidates?

A broken app that's in the repos is a big deal. How can you jump on these authors for pointing out that Ubuntu won't fix things that are completely broken? 

And who cares where they were during the alphas, betas, and release candidates, are only testers of the pre-releases suppose to file bugs?  You guys have to stop jumping on people that criticize Ubuntu.

---

### Post by popch on 2007-12-08
> **Serenitude said:**
> Ubuntu wants to take the world from Microsoft. 

Who said that when and where?

> **Serenitude said:**
> 
reasons why *buntu ships with so many bugs, why they go vastly unfixed, etc...

Some facts:

There is no software free of errors, probably not even most 'hello world' programs.

If any software publisher delayed publishing his software until it was free of known bugs, he would be a software non-publisher.

By deciding not to release a new version because of known bugs you also decide not to fix more important bugs in the preceding release and to not publish your improvements.

One question:

How many bugs did Ubuntu fix, how many not?

---

### Post by Vadi on 2007-12-08
Wait, why can't I critisize someone else? :|

---

### Post by tehet on 2007-12-08
> **hanzomon4 said:**
> How can you jump on these authors for pointing out that Ubuntu won't fix things that are completely broken?
Because they failed to read up on the release policy. Fixes will only be applied for vulnerabilities in the interest of stability. This is a given. If they don't like that they can use breakmygentoo.net and make it as bleeding edge as they want.
Also, the devs **will** fix it, probably in 8.04.

---

### Post by Dimitriid on 2007-12-08
> **adam.tropics said:**
> Pretty sure the Ubuntu folk never made a secret of the fact that they would be pushing bleeding(ish) edge stuff and generally more up to date version packages etc. Added to that, with the one exception, they only have the 6 month release cycle. So what do you want? Maybe stick to LTS versions? I know many do, it suits their needs better, and for most of them this is exactly why.

As for not reporting more bugs, well that smacks of the whole baby and bathwater thing, and frankly helps nobody, least of all, you.

Except its far from delivering "bleeding-edge" on a 6 month release cycle. Arch has a much smaller team and community and gets the whole "bleeding edge" thing right. My personal opinion is that is not an user-friendly distro trying to have every single useless package under the sun readily available. It doesn't tries to marry to opposite concepts where Ubuntu tries ( "bleeding edge" which requires lots of troubleshooting and "user friendly" which requires some degree of stability in order to make sure the unecessary levels of complexity added to make things friendlier actually work ).

If you are gonna have little updates and 6 month release cycles, you outta make sure the release at least its a step forward, not sideways and call it "bleeding-edge" cause it has higher version numbers and mroe things that previously worked gone south.

---

### Post by hanzomon4 on 2007-12-08
> **Vadi said:**
> Wait, why can't I critisize someone else? :|

Go ahead it just starts to look bad when every Ubuntu criticism is invalidated and made to be the fault of someone/thing other then the mighty Ubuntu. 

> **tehet said:**
> Because they failed to read up on the release policy. Fixes will only be applied for vulnerabilities in the interest of stability. This is a given. If they don't like that they can use breakmygentoo.net and make it as bleeding edge as they want.
Also, the devs **will** fix it, probably in 8.04.

What is bleeding edge about packages that actually work!!!

---

### Post by Dimitriid on 2007-12-08
> **Vadi said:**
> I think that's the real issue. Some people just cannot understand that there are limited resources, and that there are way more bugs marked as "critical" than of one app not launching. That's just really poor form.

And where were those geniuses during the alphas, betas, and release candidates?

The scope of the problem its important enough to asign some of those "limited resources". No, the real issue is that many people here are doing just the opposite: they are closing themselves to criticism asuming that "It works for me and it works now, this won't affect me, the Distro is fine quit crying"

People trying to deny or shun criticism that points outs important flaws that should be addressed is the fastest way to end up with a huge mess of failed binaries and all shorts of quality problems.

---

### Post by Dimitriid on 2007-12-08
> **tehet said:**
> Because they failed to read up on the release policy. Fixes will only be applied for vulnerabilities in the interest of stability. This is a given. If they don't like that they can use breakmygentoo.net and make it as bleeding edge as they want.
Also, the devs **will** fix it, probably in 8.04.

This has been pointed out already, please refute this or change your argument.

> Actually, I think it is the Ubuntu developers who are demonstrating a lack of understanding of the scale of this issue.

Why is it that three different reports that rebuilding the sources corrects the problem is not sending up a red flag calling for an investigation? If the users employed different build flags than the automated package builder, should not those differences and their consequences be researched? If the binaries somehow became corrupted after compilation then should not it be of utmost importance to determine where and how that happened? 

---

### Post by tehet on 2007-12-08
> **hanzomon4 said:**
> What is bleeding edge about packages that actually work!!!
This is not about some software mixer for which there are 10 replacements. Have you read and understood the SRU policy? Offcourse anyone is free to disagree with that policy, but that anyone should then perhaps move on to another distro. The policy was there to see for everyone before installing Ubuntu. That the authors of the respective articles are illinformed is not the fault of Ubuntu or its devs.

@dimitriid, I don't see how that makes it an undeniable certainty that it's a security issue if that's what you're getting at. In fact I highly doubt it is altough I cannot confirm or deny it.

---

### Post by 23meg on 2007-12-08
[QUOTE=hanzomon4]How can you jump on these authors for pointing out that Ubuntu won't fix things that are completely broken? [/QUOTE]

Nobody has ever said that the bug won't be fixed. The bug's status is "Triaged", which means it will be fixed. The problem has been with communicating this to people.

[QUOTE=hanzomon4]You guys have to stop jumping on people that criticize Ubuntu.[/QUOTE]

I reserve the right to "jump on" people who jump on Ubuntu like this. This isn't criticism; it's mudslinging. Criticism is always welcome.

---

### Post by 23meg on 2007-12-08
[QUOTE=tehet]Also, the devs will fix it, probably in 8.04.[/QUOTE]

No, it will be fixed in the current stable release, 7.10. And it was **never** said that it wouldn't be fixed in 7.10. The rejection of the nomination made it look, rightly, like that.

---

### Post by cluepon on 2007-12-08
I think, by and large, complaining about one src/bin mismatch is a bit much. How many of this ***specific*** kind of problem exist? That would be a better question. 

5? 10? 15? There are some 25,000 packages listed in my adept manager. If the ratio of a busted compile and src/bin mismatch is 1:25000...then I would venture to say that's pretty good.** Even 50:25000 would be decent. **

In that context, it's really difficult to whine about. And, from a perspective of a fbsd/ports user,  I could say, this is what you get from a bin dependant system. If you don't like the ratio of 1:25000 in regards to bin/mismatches...go to a system where you can build everything from source. But, let me just tell you, fbsd is not a turnkey desktop OS. It's more roll your own. And by roll your own...think slackware circa mid 90's. =)

As someone who uses the right tool for the job (or tries to), I use kubuntu for my personal desktop machine, and fbsd for server work. 

But, here's the deal folks: nitpicking about *this* type of bug is silly. Yes, it needs to be fixed. Yes, it should have been fixed for gusty. Do I think the canonical model of development is perfect? No. Out of that imperfection, a few things slip through the cracks. This is one of them. You can't please all of the people all of the time. 

The policies in place to try and insure that critical things get fixed in a quick timeframe. Yes, there could be issues of security in having a src/bin mismatch...but come on...that's stretching it a bit, dont you think? And anyone who tells me that this aumix bug is a complete showstopper is on some good drugs. Let's not toke too hard on the pipe please. 

So, instead of whining and nitpicking about this, which is what alot of this is, perhaps some ***constructive*** criticism is in order. If you don't like it, suggest alternatives. Suggest ways to make the policy better. Suggest ways to plug the holes in the QA process. 

There is a difference between constructive criticism, and whining. Whining is when you simply point out flaws. Constructive criticism is when you state the problem, and propose an idea to fix the problem. 

Linux is the ultimate manifestation of constructive criticism. Just ask Microsoft. 

Let's stop crying over spilt milk.

---

### Post by hanzomon4 on 2007-12-08
Say what you will but this looks like Ubuntu criticism will always be seen as whining...

---

### Post by Frak on 2007-12-08
So it is Ubuntu's problem, but it is also Open-Source. So, while people can make unuseful yet extremely cool programs, others can fix where others fail. Just look at GetDeb.net.

I see where Debian has a release solely placed for stability, but they stand up and take the hammer to their mistakes. Ubuntu, though, too needs to also stand up and correct their faults.

---

### Post by Serenitude on 2007-12-08
> **popch said:**
> Who said that when and where?

Bug #1 in a nutshell.



[quote="popch"]Some facts:

There is no software free of errors, probably not even most 'hello world' programs.[/quote]

Gee, thanks for that nugget of wisdom. It means, exactly, what? That known bugs can be ignored because we know that theoretically software can be buggy?

[quote="popch"]If any software publisher delayed publishing his software until it was free of known bugs, he would be a software non-publisher.[/quote]

Again, this means, exactly, what? Who here expects a bug-free release of anything? Links or cites, please? Why is it that these **_strawmen_** come out any time someone has a complaint that Ubuntu, however great, is not as great as it could be? 

[quote="popch"]By deciding not to release a new version because of known bugs you also decide not to fix more important bugs in the preceding release and to not publish your improvements.[/quote]

Again, relevance? Please don't quote me and then answer your own strawman and red herring questions as if they reflected me own thoughts. I'd appreciate it. 

[quote="popch"]One question:

How many bugs did Ubuntu fix, how many not?[/QUOTE]

I don't know, and you'd have me there. How well does Sidux do, with daily snapshots of Sid and 1 eleventy billionth of the resources? Pretty damn good. Why is that?

---

### Post by Frak on 2007-12-09
> **Serenitude said:**
> I don't know, and you'd have me there. How well does Sidux do, with daily snapshots of Sid and 1 eleventy billionth of the resources? Pretty damn good. Why is that?

Thank Debian, not Sidux. Sidux is just Debian Unstable that has been pre-configured. Sidux does 1% of the bug fixes and it is to its own package interface.

---

### Post by popch on 2007-12-09
> **Serenitude said:**
> Again, this means, exactly, what? Who here expects a bug-free release of anything? Links or cites, please?  (...) Again, relevance? Please don't quote me and then answer your own strawman and red herring questions as if they reflected me own thoughts. I'd appreciate it. 

Here:

> Reporting bugs, in some cases, which remain unfixed to this day. Still using Ubuntu, loving it, not blogging "Ubuntu sucks". But getting increasingly frustrated at the bug %. Ubuntu is the 700 pound gorilla of Linux. (...) lots of excuses, reasons why *buntu ships with so many bugs, why they go vastly unfixed, etc... 

My reasoning was and still is:

[LIST]
[*]Every piece of software has errors.
[*]Every piece of software has known errors.
[*]The people responsible for releasing a new version of a piece of software have to decide on a trade-off between old unfixed errors, new unfixed errors, fixed errors and supporting new functions (such as supporting more hardware devices).[/LIST]
I know that this decision procedure can be difficult. You can apply some metrics and ranking methods which help you. It is impossible to arrive at a decision which pleases all. 

This is not idle talk. It is backed by several years worth of experience as software engineering manager.

Canonical has made that decision. I back that decision by using their latest release. It works better for me than the one before.

You speak of large percentages of known errors gone unfixed. You speak of 700 pound hominids by which I presume you mean that Ubuntu linux is bloatware.

The most prominent example of 'negligently unfixed bug' in this thread appears to be some annoyance in an audio mixer. That has not been a show stopper for me and - obviously - a lot of users. 

I would advise a bit more serenity. I would also advise not to proclaim too loudly that you have looked into the gift horse's mouth and are displeased.

---

### Post by loell on 2007-12-09
> **23meg said:**
> 
The MOTU team has tens of thousands of packages and bugs on their hands, and they consist of 80 people, not all of whom are active all the time, so they're in constant need of help; people who aren't MOTUs can actually perform all MOTU tasks through sponsorship of a MOTU.

I really did not know that the MOTU is just this small , I was thinking more like 500+ people are involved. I feel like considering a sponsorship of one of the small packages.

I see some interesting grievances were aired too, and so far **23meg**'s responses were very satisfactory.


before the discussion deviates  lower  ,  I now would like to request for the closing of the thread.

---

### Post by 23meg on 2007-12-09
> **hanzomon4 said:**
> Say what you will but this looks like Ubuntu criticism will always be seen as whining...

In other words, "No matter how well reasoned an explanation of why exactly this particular case is mudslinging rather than criticism you present, I won't listen to you, and I'll continue to assert that criticism of Ubuntu will always be seen as whining". Cool.

In that case, I surrender; say what you will. Say that Ubuntu "innovates excuses" because someone (who is otherwise extremely competent and has put an incredible amount of work into Ubuntu QA so far) incorrectly denied a SRU nomination. Say that people who point out where exactly things went wrong and why denounce every criticism of Ubuntu as whining.

---

### Post by Vadi on 2007-12-09
Ubuntu sucks, they still didn't fix a usplash bug on my laptop. I had to manually edit 2 values to get it working.

That's it, I'm going back.

---

### Post by Serenitude on 2007-12-09
@popch: I don't have 1 1/1000th of the knowledge you have in Linux - I'll state off the top. However, I do need to clear up a few points:

By "700 pound gorilla" (hominid if you're trying to be clever", I am saying that Ubuntu is THE major player in home user Linux at the moment. All reasonable standards of measure show around a 40%ish market share. That is what this statement means. I'm not sure how you got "bloatware" out of that, but if I gave that impression, I apologize ;-)

As for the "displeased" remark - I have consistently stated how much I love Ubuntu. I use it now. I am commenting on a single aspect I think could be better. I have no intention of NOT using it. Frankly, your comment sounds rather fascist - "You will not acknowledge any flaws in or shortcoming of Ubuntu!" - said with best Cnl.Klink accent ;-) I use and will continue to use Ubuntu. I just agree that the bug system can be better. Whatever consequences flow from that, so be it.

@Vadi - very sarcastically clever. You must be proud. And if we were on the Slackware forum, it might be appropriate. However, for those who've never heard of Linux, let alone Ubuntu, before, until someone like me burns them a CD and passes it to them, it's as much as a showstopper as anything. For the same reason pretty backgrounds, etc... can turn them back to Windows. 

So make fun all you want, but if you have no CLI knowledge, don't know the proper commands, and watch your OS seemingly refusing to work immediately after install, and you have no idea that it IS working, and that a few CLI lines will fix it, then yes, I'd call that a showstopper. 

So be smug if you want to. You and I know how to fix it easily enough, but gramma or your neighbor who's never heard of Linux doesn't, and this isn't going to be a good first impression. And by the way, simply manually editing two values alone doesn't fix it ;-) Try it if you don't believe me ;-) Oh, and thanks for making a strawman of my point, as well. Very classy. I love Ubuntu, and have no intention of using anything else. But thanks for the classless shot ;-)

---

### Post by popch on 2007-12-09
@serenitude

Just for the record: I did not deny that Ubuntu Linux has flaws. In fact, my post clearly stated that I expected it to have flaws (or bugs, if you will). I did, however, state as well that I found Gutsy Gibbon an improvement over the previous release. This also means that the previous release was less good for me than this one.

If I gave the impression that I was fluent in CLI, I am sorry. In fact, I scarcely ever use that interface. When I do it is mostly to run commands given to me by helpful people in this forum. 

No one is sore at you for not understanding why some errors get fixed at a later time than you would have thought fit. I think most of us understand when you are a bit put off when things do not run properly which are important to you. Some of us just think your way of expressing your ignorance just a wee bit impolite.

---

### Post by Vadi on 2007-12-09
Yeah, that will be a showstopper. But usually people just... ask for help. I got a whole bunch of people on ubuntu now, and when they need help, they just ask me. While I myself don't know much, ubuntu wiki + google have solved everything so far... if what, there's always the IRC channel. And then to do your duty you dig on launchpad and submit the problem if it is one.

So, we understand that we're all humans here, and make mistakes?

---

### Post by 23meg on 2007-12-09
[QUOTE=loell]I really did not know that the MOTU is just this small , I was thinking more like 500+ people are involved. I feel like considering a sponsorship of one of the small packages.
[/QUOTE]

Here's a good place to start: [https://wiki.ubuntu.com/SponsorshipProcess](https://wiki.ubuntu.com/SponsorshipProcess)

[QUOTE=loell]I see some interesting grievances were aired too, and so far 23meg's responses were very satisfactory.

before the discussion deviates lower , I now would like to request for the closing of the thread.[/QUOTE]

Good to know I've been useful. But I don't think there's any reason to close the thread.

People who want to **make** the bug situation better instead of talking about how much it sucks may want to [join the Bug Squad]("https://wiki.ubuntu.com/BugSquad/GettingInvolved") and [help]("https://wiki.ubuntu.com/HelpingWithBugs"). People who want to contribute new packages and fix existing ones can do so via the [sponsorship process]("https://wiki.ubuntu.com/SponsorshipProcess").

---

### Post by Serenitude on 2007-12-10
@popch - I can accept that ;-) Tact isn't usually one of my stronger points ;-) If I didn't love Ubuntu so much, and run into those issues when trying to bring people over to it from Windows, it wouldn't bother me enough to argue about online ;-) I'll try to rephrase things better in the future.

@Vadi - agreed, mate :-)

@23meg - if awareness of how we can all contribute to make things better, and not just gripe, is all that comes out of this thread, then the effort has been well worth it. I'm willing to give back however I can to the distro that has given so much to myself, my family, and freinds. I hope we can all agree that is worthwhile ;-)

ETA: And a big sorry to all if I come across as abrasive. It isn't my intention. I just have a passion for Ubuntu, like everyone here, and want it to be the best. Sometimes too much, as far as realistic expectations? Yes, it's likely. But nothing was meant as derogatory. I've been spreading it around quite a bit on my own dime, and will continue to do so ;-) However, online here, I'll try to be more constructive, and less agressive. My best :-)

---

### Post by popch on 2007-12-10
> **Serenitude said:**
> @popch -  If I didn't love Ubuntu so much, and run into those issues when trying to bring people over to it from Windows, it wouldn't bother me enough to argue about online ;-) I'll try to rephrase things better in the future.

OK. Do this and you will be very fine here.

---

### Post by quinnten83 on 2007-12-10
would it be possible for the possible for the people @ canonical to introduce a small bug and a big bug team?
A group which tries to solve these little grievances for allready exsisting releases, while the regular team focusess on solving issues in the next release? I know this will require more volunteers, but perhaps it is a way?
The big bug team could then implement the solutions of the small bug team whenever possible.

---

### Post by 23meg on 2007-12-10
> **Serenitude said:**
> 
@23meg - if awareness of how we can all contribute to make things better, and not just gripe, is all that comes out of this thread, then the effort has been well worth it. 

In a sense, I agree. But then, this person could have said "Hmm, Ubuntu seems to be failing to fix some small bugs, and some quality assurance people aren't doing their job correctly at times. What can be done to improve this situation?", and made a blog (or even better, mailing list) post in that tone. Had she done that, it would have gone way further in improving things, and it would also be welcome by everyone, instead of agitating lots of people and giving her a foul reputation. 

That said, being a bit bitter at times and giving a gentle nudge to processes that seem to have been stuck can have its uses. But this was clearly an overdose, and while the way the bug situation is handled has its problems, it does not deserve an overstatement like "Ubuntu's lack of quality control", and the kind of baseless and inflammatory generalizations in the rest of the post.

> **quinnten83 said:**
> would it be possible for the possible for the people @ canonical to introduce a small bug and a big bug team?
A group which tries to solve these little grievances for allready exsisting releases, while the regular team focusess on solving issues in the next release? I know this will require more volunteers, but perhaps it is a way?
The big bug team could then implement the solutions of the small bug team whenever possible.

You can form such a team yourself, if you think it will be useful. If it's going to consist of volunteers, what does Canonical have to do with it? You don't need Canonical's blessing to create new ways of improving Ubuntu.

---

### Post by boast on 2007-12-10
> **23meg said:**
>  Had she done that, it would have gone way further in improving things, and it would also be welcome by everyone, instead of agitating lots of people and giving her a foul reputation. 


or would have been ignored...

---

### Post by 23meg on 2007-12-10
> **boast said:**
> or would have been ignored...

I've seen many critical posts with a sane and polite tone in ubuntu-devel and ubuntu-devel-discuss, and every time, they've sparked constructive discussions that have led to action. I've never seen one that's ignored. 

If you start out attacking people and making silly generalizations, you have a far greater chance of being ignored.

---

