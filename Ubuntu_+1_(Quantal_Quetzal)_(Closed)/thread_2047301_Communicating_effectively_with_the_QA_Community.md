---
title: "Communicating effectively with the QA Community"
date: 2012-08-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-08-24
This again is a re-post from the ubuntu-qa list. This is a really important topic close to many of you, and I wanted to make sure you knew what was happening on the subject. I don't consider what happened this month to be the status quo for testing, and I think we can all work to fix it.

--

Hello everyone! Recently I know many of you have had a rocky August with the changes landing in quantal. On top of this, the testing needs this cycle have never been greater with lots of requests for testing and milestones occurring. To complicate matters further, changes landed in quantal that caused many of you grief -- and for the most part without warning. Indeed, this issue has occurred as well during iso-testing events with confusion occurring on when and what we are testing.

First, I wanted everyone to know I consider this critical to the future success of our team and indeed the greater ubuntu community. I've undertaken the steps to start the conversation, but this will be a process with bumps along the way. To start the conversation, I approached the topic with the release team during there weekly meeting. The release team coordinates all ubuntu releases, and helps oversee the milestone testing events as well as the changes that go into the archive after feature freeze. I then followed up with a discussion on the ubuntu-release mailing list. You can find my reply here:
[https://lists.ubuntu.com/archives/ubuntu-release/2012-August/001817.html](https://lists.ubuntu.com/archives/ubuntu-release/2012-August/001817.html)

I summarized what I believe was a typical experience for some of you. Namely, the issues with the removal of unity2d and the xorg changes meant you couldn't test in a VM or on your real hardware. And further, you didn't know of this was going to occur, and maybe even spent time troubleshooting your setup to no avail. This is a failure to adequately communicate what was happening in development.

So what can be done? Is there good news? Indeed there is! I have both a shorter-term and a longer-term idea for tackling this communication issue. I'd love your hear your ideas as well! Please do share! In addition, I hope to continue to shape the overall development process to make the qa community play a more central role. That dream cannot be realized without the excellent work and support from you all.

As to the short term idea, in general I try to get wind of impactful changes and share them with all of you. I think perhaps this could be made into a more official bit of news with information coming out on pending changes at regular intervals. This will require some changes with ensuring I can get more information to digest and share, but I think it's a good idea that we can implement right now.

The longer term idea is to pursue a technical solution that could run on your development desktop. The information would be the same, simply delivered to you instead of you needing to go find it :-) The idea is still very early; I have no spec, though I share a few more details in the post above. If your interested in helping make this happen, please do get in touch with me.

So in closing, I want you to know I consider this issue of extreme importance. I am sorry for the bad experiences you may have had, and I want to do everything I can to prevent them in the future. You can help by thinking critically about how we as a team communicate and what we can do to give you and everyone else testing a better experience.

Thank you, and as always Happy! Testing.

Nicholas

---

### Post by effenberg0x0 on 2012-08-24
I don't feel like brainstorming anymore, but maybe you want to discuss this idea at UDS:

**roadmap.ubuntu.com** project

A page where all projects can post their roadmap and status, thus allowing:
- Testers to be prepared for changes, plan to participate (or not) in specific moments;
- The community to decide if it will adopt Ubuntu, invest to deploy it or drop it.

- Projects must be registered at Launchpad;
- "Project roadmap" on LP will be a link to roadmap.ubuntu.com/ProjectLPName;
- Project leaders (I refuse the term project owners) are able to edit the roadmap
- Current Blueprints can be moved to items with specific start_date, end_date in the timeline of the roadmap.
- Editing the roadmap will consist in filling in a table with 4 columns: start_date, end_date, action, status

Examples:
The ReleaseTeam admin could add to their roadmap:
roadmap.ubuntu.com/ReleaseTeam
start_date | end_date | action | status
"01082012" | "31082012" | "Push the latest Xorg xserver to quantal main repos. This will cause nvidia users to be locked out of their desktops. Not advisable for testers." | "Done"

Unity Dev Team admin could add to their roadmap:
roadmap.ubuntu.com/Unity
"01092012" | "08092012" | "Replace launcher for something else. Expect breakage"
"SomeStartDate" | "SomeEndDate" | "We will do this and that to Unity" | "Not started"

OpenSource PHP libs can be used to render this table into charts (look for PHP Gantt Class)

roadmap.ubuntu.com root can be designed to allow filters. A user can filter specific projects and see whats planned to happen this week, this month, etc.

Knowing what lies ahead would make me feel more comfortable with investing my time in Ubuntu. Transparency is important in a huge project such as Ubuntu.

Regards,
Effenberg

---

### Post by cariboo on 2012-08-24
I'd suggest even a couple of days advance notice from the release manager would have helped a bit. Enough of us are subscribed to the qa, ubuntu-devel and unity-dev mailing lists that we can give the rest of the community forum members a heads up before things go south.

---

### Post by ventrical on 2012-08-24
> **cariboo907 said:**
> i'd suggest even a couple of days advance notice from the release manager would have helped a bit. Enough of us are subscribed to the qa, ubuntu-devel and unity-dev mailing lists that we can give the rest of the community forum members a heads up before things go south.


+1

!

---

### Post by effenberg0x0 on 2012-08-24
> **cariboo907 said:**
> I'd suggest even a couple of days advance notice from the release manager would have helped a bit. Enough of us are subscribed to the qa, ubuntu-devel and unity-dev mailing lists that we can give the rest of the community forum members a heads up before things go south.

I completely agree it would be a good start and could help greatly.

Ubuntu is huge. We have a lot of different projects, with many different people, from many countries, with different languages, which may or may not communicate, using many different ubuntu-related media (forums, mailing-lists, IRC, AskUbuntu, international websites and usenet groups, etc). Aligning expectations and knowing where we're heading helps keep things transparent, increase our knowledge of the large Ubuntu universe, help us plan, understand things better, decide where to focus and be more efficient. It reinforces the "sense of belonging" that is missing for so long now, strengthens our community, minimizes conflict by reducing information asymmetry.    

But, considering all the differences I mentioned, it will never happen without method. We need open and public communication tools that establish a formal process. 

The only thing we all have in common is that testers are registered to LP and so are developers, packagers, projects, their staff, etc. 

If we had a simple website, like the one I suggested, to parse and display information posted by project leaders in a Gantt Chart format (or whatever fits), it could be very helpful for all contributors and even users. It overcomes (mis)communication challenges with a formal tool/process.

Example: I have supported Ubuntu for a long time, I stood for Unity when hell broke loose (you guys remember those days). I love this OS. I have influenced people and companies to migrate to it. But, right now, I just don't know anymore. I don't know what's gonna happen, where we're heading. I don't know what is planned and when it will happen. My only option is to browse a ridiculous large amount of websites, mailing-lists, archives, try to reach certain people, try to get info (and trust it is reliable info) here and there about many projects, to try to create a scenario in my head and make a decision. I honestly don't know what will happen till the end of QQ, what Ubuntu will look like in 6 months, 1 year, etc. I'd like to know, I think it would be fair.  

Regards,
Effenberg

---

### Post by ventrical on 2012-08-24
> **effenberg0x0 said:**
> I don't feel like brainstorming anymore, but maybe you want to discuss this idea at UDS:

**roadmap.ubuntu.com** project

A page where all projects can post their roadmap and status, thus allowing:
- Testers to be prepared for changes, plan to participate (or not) in specific moments;

Regards,
Effenberg

   I need to get something clarified. It seems to me that there are two groups of testers.

 The first group is a control group that more or  less is an upper echelon of Canonical or other Ubuntu support groups. They will relay most predicted results to developers. Results that developers have already anticipated. Then, there is this group, here, at Ubuntuforums  where the results reported are not of the norm, that may perhaps be more contrary to the control group. I have seen it written more that once that Canonical devs do not visit or participate in ubuntu_forums.   So then  it concerns me  as to why then we are all working so hard to shoulder unnecessary downtime to help developers, especially if they are going to diss the reports that we send up or ignore our discussions  that we have here.

 Personally I do not have much problems with breakage and I know it is expected but recently it has made it impossible to test ubuntu on certain hardware platforms.

---

### Post by effenberg0x0 on 2012-08-24
> **ventrical said:**
> I need to get something clarified. It seems to me that there are two groups of testers.

 The first group is a control group that more or  less is an upper echelon of Canonical or other Ubuntu support groups. They will relay most predicted results to developers. Results that developers have already anticipated. Then, there is this group, here, at Ubuntuforums  where the results reported are not of the norm, that may perhaps be more contrary to the control group. I have seen it written more that once that Canonical devs do not visit or participate in ubuntu_forums.  So then  it concerns me  as to why then we are all working so hard to shoulder unnecessary downtime to help developers, especially if they are going to diss the reports that we send up or ignore our discussions  that we have here.

Personally I do not have much problems with breakage and I know it is expected but recently it has made it impossible to test ubuntu on certain hardware platforms.

I agree Dale. 

This has been discussed extensively in the past, you remember that. 

There's testing as in "following a script and posting to a tracker in specific dates, following specific rules, focusing on specific packages, etc" and *everything else*. Everything else generally was Ubuntu+1 - the guys that actually use the development release as their primary/production OS and so are able to catch stuff that is not in any test-case, won't ever be simply because it is impossible to write that many test cases. 

As it was also discussed in the past, it doesn't really matter if we'll post reports to LP or to any other tracker, as long as devs recognize our activity as valuable contribution in testing and agree to look at our reports. Otherwise, it does seem pointless.

What happened with the Release Team + proposed + Xorg xserver + nvidia problem was more drastic than usual and was the tip of the iceberg for some testers. But if you think about, it's just a case of lack of communication. We know nothing about what's coming in updates. We know nothing about what was changed from yesterday or last week to today, what will remain in Ubuntu and what will be dropped. The people in Release Team probably also didn't knew that if they break testers installs, we automatically stop testing/reporting not only xserver but all packages. I think conflict and misuse of our potential contribution to Ubuntu, dissatisfaction by our people (like the nautilus, xerver threads) start when there's no formal info/plans posted anywhere. And I don't mean forum posts, blog posts, IRC sessions, OMGUbuntu, etc. I think it's time we grow more professional here, adopt a central/unified solution - which is a roadmap.

Effenberg

---

### Post by balloons on 2012-08-24
> **effenberg0x0 said:**
> I don't feel like brainstorming anymore, but maybe you want to discuss this idea at UDS:

**roadmap.ubuntu.com** project

A page where all projects can post their roadmap and status, thus allowing:
- Testers to be prepared for changes, plan to participate (or not) in specific moments;
- The community to decide if it will adopt Ubuntu, invest to deploy it or drop it.

- Projects must be registered at Launchpad;
- "Project roadmap" on LP will be a link to roadmap.ubuntu.com/ProjectLPName;
- Project leaders (I refuse the term project owners) are able to edit the roadmap
- Current Blueprints can be moved to items with specific start_date, end_date in the timeline of the roadmap.
- Editing the roadmap will consist in filling in a table with 4 columns: start_date, end_date, action, status

Examples:
The ReleaseTeam admin could add to their roadmap:
roadmap.ubuntu.com/ReleaseTeam
start_date | end_date | action | status
"01082012" | "31082012" | "Push the latest Xorg xserver to quantal main repos. This will cause nvidia users to be locked out of their desktops. Not advisable for testers." | "Done"

Unity Dev Team admin could add to their roadmap:
roadmap.ubuntu.com/Unity
"01092012" | "08092012" | "Replace launcher for something else. Expect breakage"
"SomeStartDate" | "SomeEndDate" | "We will do this and that to Unity" | "Not started"

OpenSource PHP libs can be used to render this table into charts (look for PHP Gantt Class)

roadmap.ubuntu.com root can be designed to allow filters. A user can filter specific projects and see whats planned to happen this week, this month, etc.

Knowing what lies ahead would make me feel more comfortable with investing my time in Ubuntu. Transparency is important in a huge project such as Ubuntu.

Regards,
Effenberg

This idea has a lot of merit, but your correct. It's not something that will happen overnight or easily. I don't have the information that would go on that site.. I would venture to say no one person does, but I'm sure you can understand the release's team giant task of trying to pull all that information from the disparate sources. It's not an easy task, and I think we ultimately do need to move to a place where the information is being pushed to everyone, rather than us needing to go get it.

---

### Post by mc4man on 2012-08-24
As far as the Xorg/nvidia issue
The xserver packages were in proposed for quite some time & well known to anyone that used them with nvidia that it would break.

Yet at no time while in proposed was anything done to solve or escalate to nvidia. That wasn't done till after release & came from a bug filed on Firefox. Within 2 days Nvidia found the issue & fix.

Numerous apport crash reports  on Xorg were filed while the packages were still in proposed, all were invalidated due to missing symbols ( one set that I don't think even exist..

So this problem may have been adverted if any testing of the proposed packages had been done ( and a fix may have been in nvidia already

---

### Post by balloons on 2012-08-24
> **effenberg0x0 said:**
> I agree Dale. 

This has been discussed extensively in the past, you remember that. 

There's testing as in "following a script and posting to a tracker in specific dates, following specific rules, focusing on specific packages, etc" and *everything else*. Everything else generally was Ubuntu+1 - the guys that actually use the development release as their primary/production OS and so are able to catch stuff that is not in any test-case, won't ever be simply because it is impossible to write that many test cases. 

As it was also discussed in the past, it doesn't really matter if we'll post reports to LP or to any other tracker, as long as devs recognize our activity as valuable contribution in testing and agree to look at our reports. Otherwise, it does seem pointless.

What happened with the Release Team + proposed + Xorg xserver + nvidia problem was more drastic than usual and was the tip of the iceberg for some testers. But if you think about, it's just a case of lack of communication. We know nothing about what's coming in updates. We know nothing about what was changed from yesterday or last week to today, what will remain in Ubuntu and what will be dropped. The people in Release Team probably also didn't knew that if they break testers installs, we automatically stop testing/reporting not only xserver but all packages. I think conflict and misuse of our potential contribution to Ubuntu, dissatisfaction by our people (like the nautilus, xerver threads) start when there's no formal info/plans posted anywhere. And I don't mean forum posts, blog posts, IRC sessions, OMGUbuntu, etc. I think it's time we grow more professional here, adopt a central/unified solution - which is a roadmap.

Effenberg

Effernberg, Dale; I know of no such hierarchy.. Certainly I don't advocate nor participate in one. One of the goals stemming from UDS was that QA was disparate and was really hard to follow or track. This isn't a "special blessed group" vs not. The qatracker was adopted to be that clearinghouse of information -- not forever, but for this cycle :-) We can evaluate it again next cycle. I want a central place where all information on QA is taking place -- no matter the activity. It's really a need, and I believe we're building towards having that.

Now, IMHO the qatracker has performed it's function well, and results for testing are now transparently available to anyone curious to see what's going on when we have a call for testing. You can see the results, you can see the bugs reported, all in realtime. I'm not claiming it's the best system, but it is a huge improvement in my mind (heh, not hard to improve on what we had). It's enabled us to be more organized.

Now, you may remember my experiment with trying to apply the qatracker to general u+1 activities. Tracking that is still an untackled problem, but it would be good for those doing the work to be able to track and measure what's going on amongst themselves.

Now as to the work being valuable. Why of course it is! It's more than a "nice to have" it's extremely important. Not everyone understands that but I know you've been around long enough to see the changes that have come about the last 2 cycles. People are actually taking about QA and quality.. It's become mainstream to some extent. Heh, when ideas go mainstream and everyone's an expert, you can end up with a little chaos. Still, people start to get the importance now. What they are missing is the right way to do it.. That's where we can help.

---

### Post by effenberg0x0 on 2012-08-24
> **guitara said:**
> This idea has a lot of merit, but your correct. It's not something that will happen overnight or easily. I don't have the information that would go on that site.. I would venture to say no one person does, but I'm sure you can understand the release's team giant task of trying to pull all that information from the disparate sources. It's not an easy task, and I think we ultimately do need to move to a place where the information is being pushed to everyone, rather than us needing to go get it.

Hi Nick,

Well, it's a matter of opinion. IMO it's very doable, much simpler than a lot of things Ubuntu and Canonical have been doing. LP paid coders can do it alpha in a week. Apache, PHP+MySQL, SSO. Simple queries. It's no different than everything else. I'd like to write a full spec of this idea, but I am not doing it anymore this cycle for obvious reasons.

I agree tasks in Ubuntu are always huge, but that makes me believe even more in the need for processes, tools. I know you agree to that (i.e. qa tracker).

I think we need transparency, public info, not things that are pushed to devs and testers. Users, new and old, potential testers we recruit, people that Google for the future of Ubuntu-related projects, Ubuntu itself, should be able to go to one location and understand where we are, where we're heading.

I do understand that such a tool could possibly decrease the flexibility of benevolent dictatorships, maybe also kill the possibility of "surprising" the market (market, not community) with new stuff (as in a new programs, features, partnerships that were not developed together with the community but pushed to Ubuntu just because or for commercial reasons), etc. 

Maybe UDS-R is a good time to rethink this stuff. Can there really be FOSS without communication and transparency and with no investments and efforts to recruit, integrate, support, empower, recognize a community? Can Ubuntu continue to evolve without adopting the practices that are usual to the proprietary software industry?

I know it's not CoC-Charming to talk about these things but I feel it's overdue.

Regards,
Effenberg

---

### Post by balloons on 2012-08-24
> **mc4man said:**
> As far as the Xorg/nvidia issue
The xserver packages were in proposed for quite some time & well known to anyone that used them with nvidia that it would break.

Yet at no time while in proposed was anything done to solve or escalate to nvidia. That wasn't done till after release & came from a bug filed on Firefox. Within 2 days Nvidia found the issue & fix.

Numerous apport crash reports  on Xorg were filed while the packages were still in proposed, all were invalidated due to missing symbols ( one set that I don't think even exist..

So this problem may have been adverted if any testing of the proposed packages had been done ( and a fix may have been in nvidia already

Good point, and it's well noted. This hearkens to how development is done, and is a conversation we need to have with the larger community.

---

### Post by ventrical on 2012-08-24
Perhaps my comments then are unfair. I do not intend to chide developers into  rendering quick work-a-rounds but it sure may seem that way. But , of course I agree with you Al that there is a diverse group or programmers that are contributing here. That may be be both a blessing and a curse. You have also mentioned 'trust' several times and that is a key element in our daily testing. Back over a year and a half ago I had some serious bugs with Natty and someone suggested that "it's only the devs having some fun with you" (Trust me .. the reply is somewhere on the Ubuntuforums forums! :) Sure .. I can take a joke but then it is time to get serious. Then the trust factor can really make testing very dicey because, as you had mentioned in forums past, it is hard to discern and authenticate who and where these programs are originating from. Ok .. that is a higher tier of access  vs security  that I am not privy to (nor do I wish to be).

  I think then that some type of centralization between volunteer testers (such as ourselves) and the devlopers need to be employed. I know that this is the core of your own idea which you have just suggested. I know also that guitara has worked tirlessly to try and advocate our concerns to the Release Team and etc.. That is a real bonus indeed and I hope Nick continues  Ad Opus Dilligenter !

  In my own situation I had committed to contribute to the U+1 wiki as best as I could and I feel I have fallen short there and have been remiss in my duties, those things which I had agreed to take on. There are no excuses.  I have been busy, indeed and this summer , I can write three novels about .. but I am called away almost daily.

  I still have tremendous faith that this will work out. Somehow it always does but I do hope that some take up some of your ideas (and also Cariboos suggestion) that we could have sometype of heads up when critical changes take place, If we are to do this extra work of searching the internet over for hints and clues and needles in the haystack then our work is greatly diminished as testers as we are called on to take a double duty which should be shouldered by the Release team or whichever team that responsibility is delegated to. There has got to be some common ground here. If  it were not for mac4man and harry33 and their nvidia/xserver expertise the problem would be ten-fold times worse.IMO.

 Regards, ventrical

---

### Post by cariboo on 2012-08-25
mc4man is right, we (those that check this sub-forum often) did know about he problem, before anything actually happened, but it's those that run a development version but aren't active here or elsewhere, that only posted here after the problem had arisen, that we have to find a way of notifying.

I don't mind the extra threads, but I should have been a bit more proactive, and merged them with the existing threads as they appeared, instead of allowing several threads on the same subject to be posted.

We already ready have part of the infrastructure in place with the U+1 testing team, maybe we should have sent a warning to the list, with the hopes that they would help spread the word to their friends and others. Between the qa team and the U+1 team we should be able to cover the majority of them users testing Quantal, and versions beyond.

---

### Post by grahammechanical on 2012-08-26
I hope you do not mind me jumping in?

I do not disagree with any of the comments made about communication but I see things a bit differently.

I think that we (Ubuntu) have Quality Assurance without much Quality Control.

This would not matter so much if the Development branch were kept "in house," as it is said, with the development branch only being available to a closed group.

But Ubuntu is very big on community and the development branch is available to anyone who cares to download it.

I think that it is time to

a) do away with the daily ISO image

b) keep one ISO image that works until it can be replaced by another ISO image that has been proven to work (that is, tested)

c) collect updates over a period of a few days, stick them in a Special Testing ISO image that is made available to registered Community Testers for testing and who follow a control testing program

d) if the Special Testing ISO image is proven to work then it becomes the standard development branch ISO image for download by anyone.

I guess I am talking about a form of cadence testing where the code is tested either weekly or two weekly before it is accepted as passing Quality Control and put in an ISO image.

Remember, a working ISO image is the ultimate fall back for testing the installed development branch. It is called Re-install. And at the moment that is not available. Re-install is the only roll back we have.

Imagine a company that sells a product but where Quality Control begins with Customer Complaints. Bug reporting is a bit like customer complaints. Quality control should end when the product (in this case Ubuntu) is put in the storehouse (in this case the repositories) for distribution (download) to the customer (the user).

Just some of my thoughts as I try to work off the frustration of yet another failure to re-install. I must be crazy. If not then I am sure getting there.

Regards

---

### Post by jerrylamos on 2012-08-26
> **grahammechanical said:**
> 
I think that it is time to

a) do away with the daily ISO image

b) keep one ISO image that works until it can be replaced by another ISO image that has been proven to work (that is, tested)
Tester 101:

I keep back partitions that work and back .iso that work.

No way Development has the diversity of setups and hardware that we have, so that's what we're doing is testing.

Now I do get upset when major features and functions I was using vanish forever - if we were warned I somehow missed it.  Also I may not realize the impact of big changes in Unity, Compiz, Xorg, Nautilus, you name it.

So after I steam about it for a while I learn a little bit more about linux and do a workaround which may or may not get me back to where I was.

---

### Post by balloons on 2012-08-27
> **grahammechanical said:**
> I hope you do not mind me jumping in?

I do not disagree with any of the comments made about communication but I see things a bit differently.

I think that we (Ubuntu) have Quality Assurance without much Quality Control.

This would not matter so much if the Development branch were kept "in house," as it is said, with the development branch only being available to a closed group.

But Ubuntu is very big on community and the development branch is available to anyone who cares to download it.

I think that it is time to

a) do away with the daily ISO image

b) keep one ISO image that works until it can be replaced by another ISO image that has been proven to work (that is, tested)

c) collect updates over a period of a few days, stick them in a Special Testing ISO image that is made available to registered Community Testers for testing and who follow a control testing program

d) if the Special Testing ISO image is proven to work then it becomes the standard development branch ISO image for download by anyone.

I guess I am talking about a form of cadence testing where the code is tested either weekly or two weekly before it is accepted as passing Quality Control and put in an ISO image.

Remember, a working ISO image is the ultimate fall back for testing the installed development branch. It is called Re-install. And at the moment that is not available. Re-install is the only roll back we have.

Imagine a company that sells a product but where Quality Control begins with Customer Complaints. Bug reporting is a bit like customer complaints. Quality control should end when the product (in this case Ubuntu) is put in the storehouse (in this case the repositories) for distribution (download) to the customer (the user).

Just some of my thoughts as I try to work off the frustration of yet another failure to re-install. I must be crazy. If not then I am sure getting there.

Regards

Graham, I'll just reply here to everything :-)

I think your thoughts line up very much with my own. Ubuntu has grown and changed, and we've gotten bigger. We are upstream for more and more code each cycle. And our processes for releasing, testing, developing, etc no longer align well with our current situation.

Sine we're no longer just passive consumers of software (as a distribution), we're actively writing and maintaining code. This means we need testing more than ever! To test effectively as a large community, a well defined process and schedule that everyone understands and follows is important. And as you say, while we need access to these testing packages, having a stable base with which to test from is also important.

Thanks for your thoughts! We are in a unique position to help shape ubuntu and QA in the future.. Let's keep the ideas flowing.

---

### Post by balloons on 2012-08-27
> **effenberg0x0 said:**
> Hi Nick,

Well, it's a matter of opinion. IMO it's very doable, much simpler than a lot of things Ubuntu and Canonical have been doing. LP paid coders can do it alpha in a week. Apache, PHP+MySQL, SSO. Simple queries. It's no different than everything else. I'd like to write a full spec of this idea, but I am not doing it anymore this cycle for obvious reasons.

I agree tasks in Ubuntu are always huge, but that makes me believe even more in the need for processes, tools. I know you agree to that (i.e. qa tracker).

I think we need transparency, public info, not things that are pushed to devs and testers. Users, new and old, potential testers we recruit, people that Google for the future of Ubuntu-related projects, Ubuntu itself, should be able to go to one location and understand where we are, where we're heading.

I do understand that such a tool could possibly decrease the flexibility of benevolent dictatorships, maybe also kill the possibility of "surprising" the market (market, not community) with new stuff (as in a new programs, features, partnerships that were not developed together with the community but pushed to Ubuntu just because or for commercial reasons), etc. 

Maybe UDS-R is a good time to rethink this stuff. Can there really be FOSS without communication and transparency and with no investments and efforts to recruit, integrate, support, empower, recognize a community? Can Ubuntu continue to evolve without adopting the practices that are usual to the proprietary software industry?

I know it's not CoC-Charming to talk about these things but I feel it's overdue.

Regards,
Effenberg


Effenberg, now is the time to have the discussion if we want the R cycle to be different. At the UDS-R we need to be able to hit the ground running on what we've already hashed over. In regards to this site, I'm concerned it's pitching a tool to be built to solve a broken process. In other words, even if the tool existed, it wouldn't have any data populated in it.

I tread carefully when pitching a tool to fix something that is broken. Tools should make things simpler; if I am unable to define and use a good process a tool will only make it worse. (That's not to say we might not need some tool to make this happen, but it's a secondary issue imho)

---

### Post by effenberg0x0 on 2012-08-27
Hi Nick, I think we have to start somewhere. There's no data to populate a tool, but there won't ever be if the tool is not created. If a communication tool is not available, people won't ever use it to communicate.

But, after reading the [thread about dropping alternate ISO]("http://ubuntuforums.org/forumdisplay.php?f=416"), I feel like no tool can save us. 

People on the other end have no idea we need a barely working OS in order to test the entire OS - all packages. It's not just about installing the OS, it has never been. They would know if they ever looked to Launchpad. Apparently they still see testing as "burn ISO, boot ISO, answer basic questions, Good Ubuntu has no bugs". That's the side effect of pushing and reinforcing the ISO-Testing insanity as the basis for QA. I told you my opinion about that many times, we agreed to disagree. I think the problem is becoming more evident now.

The alternate ISO thing is the Nvidia mess all over again. We know people depend on the alternate. Apparently they don't. It's all about communication, roadmap, transparency.

If there's no process tool to establish communication between testers and devs, my opinion is that people should stop wasting their time with testing in this cycle. Simply stop testing and reporting, until a process is defined and some understanding arises. It's counterproductive to keep doing it this way. 

If Canonical will not make use of 100 or more testers willing to work for free out of love for the OS, things went so wrong that we should stop and rethink the whole thing. This is throwing approximately 100 * 12 * $8,000.00 ($9,6 Million/Year) instead of investing much, much less (like $10,000) in proper tools to help these people make Ubuntu better. 

Regards,
Effenberg

---

### Post by kansasnoob on 2012-08-28
> But, after reading the thread about dropping alternate ISO, I feel like no tool can save us. 

I know this will sound harsh, but adding to that, IMHO you just can't expect to maintain a qualified and ambitious QA team when development seems to ignore the testers :(

Take for instance 12.04.1, remember that was the first point release of a 5 year LTS, but how many bugs were not even addressed or failed to be fixed:

[https://bugs.launchpad.net/ubuntu/+source/pango1.0/+bug/1038573](https://bugs.launchpad.net/ubuntu/+source/pango1.0/+bug/1038573)

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

Mind you that those are only my personal pet bugs, but one effects the upgrade path from Lucid to Precise, and another effects the installer!

The natural conclusion is that Canonical no longer cares about quality ](*,)

---

