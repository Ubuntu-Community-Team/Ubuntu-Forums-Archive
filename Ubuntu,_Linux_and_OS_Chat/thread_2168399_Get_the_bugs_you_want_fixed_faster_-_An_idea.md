---
title: "Get the bugs you want fixed faster - An idea"
date: 2013-08-17
forum: Ubuntu, Linux and OS Chat
---

### Post by trevm999 on 2013-08-17
I am not a programmer, and whenever I need to fix something in Ubuntu, I Google it and rely on those who have gone before me to find a solution. However, when I encounter a bug that has not been fixed, and I can't find a solution for, I want to do something about it. Especially if the bug has been around since 2010. I don't think I'll be learning to program any time soon, but I would like to see a way for me to possibly significantly speed up the fixing of a bug. What I think would help is if there was a way to financially contribute to the fixing of a certain bug. For example, I could pledge $10 to the fixing of a bug. If someone else wanted the same bug fixed, they could pledge $10 too and so on. When the pot gets big enough, someone who has the ability to fix the bug will want to. When they figure out a fix for the bug that get into software update, they get the money.

What do you think? Or am I misunderstanding how the big fixing process works?

---

### Post by tgalati4 on 2013-08-17
That's a good idea.  In Las Vegas, they have fancy cars on pedestals surrounded by slot machines.  If you play enough, you might win a car.

And that is probably a better chance than getting your particular bug fixed.

Such offers for programming are called bounties.  It might be a useful feature in launchpad to have the bounty displayed as part of the bug tracking process.  If two bugs are combined, the bounties could be combined as well.  Part of the issue is the modularity of Ubuntu.  If there is a kernel bug, you need the kernel developers to review, test, and apply the patch before it is released to the masses.  If it is a Gnome3 bug, then you are at the mercy of the Gnome3 developers.  If it is an Ubuntu desktop issue, then perhaps an Ubuntu developer will fix it.

Many bugs get labeled as "Won't Fix" because someone has determined that the issue is not a bug, but a design decision.

Give us a link about a specific bug and very quickly it will be clear as to why it was not fixed.

---

### Post by trevm999 on 2013-08-17
I came across this one a couple weeks ago [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/606365](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/606365)

---

### Post by vasa1 on 2013-08-17
As tgalati4 wrote, there's a chance this particular bug is a GNOME thing (upstream). Still, someone should have said so but it's only affected people who've posted there and there's no input from devs.

Which brings up the next point ... the bug-handling infrastructure is a bit overloaded. My guess is that there's a shortage of competent volunteers, even at the initial stage of triaging.

BTW, how can one tell if a bug has been triaged?

---

### Post by tgalati4 on 2013-08-18
When you post a bug, you are automatically subscribed to that bug and you will get an email everytime there is a status update, or if someone adds comments to the bug.  It's interesting to see the ping-pong effect as the bug gets passed around.

The referenced bug is a good example.  A bug must be confirmed for it remain alive in the system passed 60 days.  Confirmation means that it is repeatable, affects several users (by evidence of the comments submitted), and a clear description of the problem, how to trigger it, and sufficient log files attached to start the digging.

But, for this bug, it was never assigned an importance value (I'm not sure how that is done) nor were there any developers assigned to this bug, even though it effects business uers--presumably a market that Canonical wants to support.

There are several work-arounds posted.  Because of that, perhaps the bug is not worth fixing.  I don't know.

A bounty system would only work if there is someone on the Ubuntu side to take the patch offered by the bounty seeker and incorporate it into the code base.  This is a process not unlike assigning a developer to the bug.  So it's possible that the bounty will hang around because there is no one to actually incorporate the patch into the current or next Ubuntu release.

There used to be a Brainstorm website for submitting ideas to Ubuntu--but it was shut down for reasons that are not clear to me--other than suggestions were submitted and then not processed--for years.  Not unlike many bug reports.  They hang around for years.

But progress has been made, Bug #1 was closed out recently.  I think the status went from Confirmed to Won't Fix.

---

### Post by ian-weisser on 2013-08-18
Brainstorm was closed because it was ineffective. Users loved the idea of a room full of programming monkeys, waiting to do their bidding. Developers hated being characterized as lazy monkeys or free labor. Without a meeting of the minds, the ideas could go nowhere. It was simply not a great venue for constructive collaboration or idea development.

I encourage users to learn how to triage bugs with the Ubuntu Bug Squad ( [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad) ). You don't need to be a programmer, or a guru. Just go through the training on the wiki, join the team, and start asking questions on the IRC page.

You will find lots of bugs that are not really bugs. You can close them.
You will find lots of bugs that need more information. You can ask the reporter for more information, and close the abandoned ones.
You will find lots of bugs that need to be reported upstream. You can do that, too.

You can keep developer attention focused on the bugs we want them to address instead of spending their valuable time triaging.

---

### Post by cariboo on 2013-08-18
There isn't a lot of information in the initial report, using apport is the preferred method of reporting bugs, and in all cases adds much more information to the report. My feeling is that the bug should be reported upstream to gnome in order to get it fixed in a timely manner, although the first bug I ever reported upstream, took 3 years before it was finally fixed.

---

### Post by tgalati4 on 2013-08-18
And I think that is the point.  It just takes sooo long to get some of these bugs fixed.

---

### Post by cariboo on 2013-08-18
Unfortunately, because Canonical only produce a small part of the distribution, we have to rely on upstream to fix bugs. A huge way to get bugs fixed, is to report them in the correct place. The bug reports for Ubuntu packages that I report, are usually fixed fairly quickly, so the first step in reporting a bug, is to find where it should be reported, 

I'd suggest that the majority of bug reports are sent to the wrong place and along with poor reporting procedures make it look like it takes forever to get a bug fixed.

---

### Post by trevm999 on 2013-08-19
So probably the best way for me to help is to join the bug squad and just financially contribute to Ubuntu via the official contribution page. Which option would be the best to vote for with my money if I would like bugs to be fixed more effectively, Community participation in Ubuntu development?

---

### Post by vasa1 on 2013-08-19
> **trevm999 said:**
> So probably the best way for me to help is to join the bug squad and just financially contribute to Ubuntu via the official contribution page. Which option would be the best to vote for with my money if I would like bugs to be fixed more effectively, Community participation in Ubuntu development?
I'm sorry but I suggest you forget the money route for obvious reasons (unless you are acting on behalf of a corporate). You could try interacting with the developers of GNOME's network manager via mailing lists or chat.

---

### Post by ian-weisser on 2013-08-19
Without knowing your interests and aptitudes, it's hard to gauge the best way for you to help.

For example, I enjoy helping people and doing basic bug triage. You might hate those but enjoy writing documentation or translating or leading a LoCo. Everybody is different.

Voting with your money is not a very effective tool in this community. It's not structured as a market. Many developers have no way to receive your contribution nor to know that you are offering a bounty. If you really want to use money, any good search engine can tell you several good bounty sites.

Generally, I find that positive feedback works really well, too. Everybody likes to know their effort and contribution is appreciated.

For the example bug #606365: 
Somebody (a user, like you or me) should see if the specific list of broken imports has been reported to the upstream bug tracker at bugs.gnome.org. If so, link the launchpad bug to it.
Also, test the latest upstream version of Network Manager (VMs are handy for testing) to ensure the problem has not already been fixed in a recent release.
If the problem still exists, open an upstream bug on it that clearly lists the missing import settings, and includes a file of test settings that don't import. Link the Launchpad bug to it.

---

### Post by cariboo on 2013-08-19
Community participation in Ubuntu development, would probably be the best place, although making the desktop more awesome would also seem a good choice.

---

### Post by craig10x on 2013-08-19
I would have to say that it is a bit amazing to me that an obvious bug like the touchpad levers in systems settings not remembering the change you make on the sliders and always going back to default when you close the window has not only not been fixed in 13.04 but not even in 13.10 development...i am sure most here have noticed it and you would think some if not most of the developers that work on ubuntu would have noticed it and corrected by now...I reported this bug many MANY months ago and so have others but nothing ever seems to happen with it...

Oh, i am sure it will get fixed someday...maybe by the LTS release...no, not 14.04 but 16.04 :D ;)

---

### Post by ian-weisser on 2013-08-19
> **craig10x said:**
> ...I reported this bug many MANY months ago and so have others but nothing ever seems to happen with it...

If you refer to a bug report that you want looked at by other humans, please link to it. Or at least provide the bug report number and which tracker you reported it upon.

If it's ignored, then it has either been determined to be of quite low priority, or the report is insufficient for developers to duplicate and locate the issue, or the issue is blocked by another known bug. Low priority can cover a lot of territory - no users have cared enough to Triage it, no users have cared enough to submit a patch, the code has been superseded by a new upstream release, the impact of the bug is too small to worry about while critical and data-loss bugs are in the developers' queue, etc.

My first bug took two years to fix. It was low-priority with an easy workaround. After a year of waiting for somebody else to do the work, I pulled the source code and found the bug myself. Then I learned how to patch it, and attached the patch to the upstream bug report. The developer noticed. He had higher-priority stuff in his queue, but took a few minutes because I showed interest and made an effort. He politely fixed my crummy patch, and sent it back to me for testing. I tested it. Then he tested it. Then he committed it. Then it took Ubuntu six months to catch up with the new upstream commit. But now it's FIXED, properly, permanently. And I'm proud that I helped contribute.

---

### Post by PaulW2U on 2013-08-19
> **ian-weisser said:**
> After a year of waiting for somebody else to do the work, I pulled the source code and found the bug myself. Then I learned how to patch it, and attached the patch to the upstream bug report.

You make it sound so easy. ;)

The day I switched from using a 6502 based BBC Micro to using a 486DX PC was the day that my programming knowledge was effectively wiped out and it's been that way ever since as I'm much too old to learn how to read and understand modern day source code. I'm sure there are many others here that think the same as I do.

> **ian-weisser said:**
> I encourage users to learn how to triage bugs with the Ubuntu Bug Squad ( [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad) ). You don't need to be a programmer, or a guru. Just go through the training on the wiki, join the team, and start asking questions on the IRC page.

That's where I am at the moment but due to other commitments I haven't done nearly as much as I had intended to do by now.

---

### Post by ian-weisser on 2013-08-19
> **PaulW2U said:**
> You make it sound so easy.

It was not easy at all. That's why I'm so proud I accomplished it.

The source file turned out to be a shell script that relied upon a bash-specific feature. It was failing in a dash environment.
I did a little search-engine-fu and discovered how to make it dash-compatible.
Lots of bugs are like that.

Had it been in C, I would have been lost, and promptly turned to the community for help.
Today, I still barely know enough C to ask where the bathroom is...and would still need help from the community to parse out the reply struct.

---

### Post by tgalati4 on 2013-08-19
The bug collection systems have vastly outweighed the methods to fix them (1/2 a million according to the BugSquad wiki).  We have several frameworks to collect bugs and report log files when programs crash.  What is missing is a better method to triage and actually fix bugs.  I think the staged rollouts of updates will help, by reducing exposure to updates that break things.

Bounties may not work well in an open source community, but beans and karma and other such positive points do seem to have a place.  The BugSquad is a good start, but it seems heavy, with lots of layers and hoops--not unlike how current linux development is structured.  I'm not sure how to simplify it, but generally simpler is faster.

---

### Post by craig10x on 2013-08-19
[QUOTE=ian-weisser;12761966]If you refer to a bug report that you want looked at by other humans, please link to it. Or at least provide the bug report number and which tracker you reported it upon.

Here it is:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1118719](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1118719)

By the way, i have seen other bug reports on it, and according to one, it was fixed by gnome developers, but if that is true, it never made it to ubuntu...
This is why i have a feeling that this will get fixed at some point, but not for a long time...I wish i knew how to patch it but i am not technically oriented enough to do that...

---

### Post by ian-weisser on 2013-08-19
Okay, that particular bug is in software provided by Gnome upstream. They have their own bug tracker at bugs.gnome.org.
Have you reported it to the Gnome bug tracker? There's no link to an upstream bug.
So you have indeed reported it...on a venue that Gnome developers don't use.

An Ubuntu volunteer triager can upstream the bug for you...or you can simply do it yourself. It's easy.

If you have seen duplicate reports, did you mark them as duplicates? You can, you know. It helps. Everybody shares the same information, and everybody finds out when it's fixed or when the developer needs information or help testing. It also prevents old orphaned bugs that were long fixed by a duplicate, but nobody marked them fixed (a huge waste of everybody's time). 

It-was-fixed-but-the-fix-never-made-it-to-Ubuntu is either a support request or another bug...or impatience. If you locate the announced fix, please link to it. Upstream updates can easily be tracked through Gnome, Debian, and the pre-release version of Ubuntu. They take time, since each organization must test the new version and fit it into their release calendar. For example, both Gnome and Ubuntu usually roll all the small fixes into the next major release instead of immediately. That means October at the earliest for Ubuntu, if Gnome really did fix it..

---

### Post by mamamia88 on 2013-08-20
I really like this idea.  Give kids who are interested in this stuff incentive to get started or people who just might need a little extra cash working on fixing bugs.  Kind of like that new fiverr website except in reverse where the people needing the service advertise

---

