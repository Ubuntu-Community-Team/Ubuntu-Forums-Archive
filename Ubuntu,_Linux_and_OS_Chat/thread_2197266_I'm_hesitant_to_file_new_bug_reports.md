---
title: "I'm hesitant to file new bug reports"
date: 2014-01-03
forum: Ubuntu, Linux and OS Chat
---

### Post by ardchoille422 on 2014-01-03
I found a huge bug in an app - vital a text box was missing from the app window. I filed a bug about this and you can find the bug report [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-contacts/+bug/1249947").

1) This app couldn't have been tested before being deployed in a major GNU/Linux distro - the missing text box would have been noticed (you can't miss it!) had the app been tested.

2) Filing bugs appears to be a waste of time for the end user because the bug reports go unnoticed. What other conclusion should I reach after filing a bug report for the above bug and the report seems to have been ignored for two months? This could be why more bug reports aren't filed - the end user thinks it's a waste of their time.

3) I feel that this bug would never have made it into the hands of the end user had the developer checked his/her code, or at least tested it, before deploying the app.

The bug described/linked above is just one example, there are likely thousands more.

I think part of the problem is that there is no incentive for  improvement. The typical independent developer in the Linux world  doesn't have shareholders looking over his/her shoulder reminding  him/her that he/she may lose their job if things don't improve.  Developers for some other major desktop operating systems have quite a  bit of incentive for improvement.

Now, buckle your safety belts, I'm going off on a tangent.. try to keep an open mind.

Some folks seem to think that a large number of bugs are accpetable. It it a mistake to think this way - if I expect something bad to happen and something bad does happen, then I likely won't take steps to resolve the problem or to keep it from happenning in the future. Have you ever heard the phrase "garbage in, garbage out"? Do you see the psychology involved in this? If we expect bugs, and bugs appear in the software, no one is going to take steps to reduce the number of bugs in future software revisions.. or bug reports are simply going to be ignored like mine was.

We need to change our way of thinking from "bugs are an unavoidable part of software for the end user" to "we need to make sure the end user never sees another bug". If bugs exist in the current revision, then future revisions should not be allowed to be worked on until the bugs are resolved in the current revision. It's called "accepting responsibility for one's actions".. or "fixing one's own mistakes".

The developers know the code better than anyone, so they should know where all of the bugs are. Do people not see that releasing software that is full of bugs does nothing more than give the developers a bad name and ruin reputations?

Silly bugs like this are part of the reason there will never be a "year of Linux on the desktop".

Now, the community has a few options here:
1) Get on the defensive and come up with numerous excuses to protect the status quo
2) Continue to ignore the problem.. thinking "maybe it will go away"
3) Keep an open mind and actually bring about changes

What will your choice be?

---

### Post by deadflowr on 2014-01-03
Bugs are only addressed when they are confirmed.
It takes at least two to mark it as affecting them to become confirmed.
As of right now, no one else has added that they are affected, so it is still unconfirmed.
Hence, why it is not being addressed.

---

### Post by Bucky Ball on 2014-01-03
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request.

---

### Post by ardchoille422 on 2014-01-03
> **deadflowr said:**
> Bugs are only addressed when they are confirmed.
It takes at least two to mark it as affecting them to become confirmed.
As of right now, no one else has added that they are affected, so it is still unconfirmed.
Hence, why it is not being addressed.

Could the reason for the lack of reports from other users be that the other users see that some bugs go untouched for years so they feel it's a waste of time to file a report? I have another bug report that I filed in 2010 that hasn't been touched.

Perhaps the bug handling process needs to be upgraded? It might be a good idea to try and think of why things happen the way they do rather than just try to come up with an explanation for the outcome itself.

---

### Post by Bucky Ball on 2014-01-03
Did you ever post here about this bug to see if it was effecting anyone else prior to the bug report? I've honestly never seen it. I'm not using gnome (it concerns Gnome-contacts? correct me if I'm wrong) so can't see if I can duplicate. If you give me the exact details of your software setup (13.10 and gnome fallback for instance) I might be able to duplicate it here and see if I can replicate the problem. If so, I'll post a bug report there, too. 

Can anyone using gnome-contacts replicate this bug?

You're forgetting that many of these projects are small scale and there's no 'paid staff' who are going to jump to it when some user has a bug. They have other lives. See here:

[https://wiki.gnome.org/Design/Apps/Contacts](https://wiki.gnome.org/Design/Apps/Contacts)

Hasn't been updated since April 2013 and most of the info on there are older than that. That's just the way it is. You can rally community action, but who ya gonna tell? Possibly a couple of coders who are not working on the project because they are trying to make ends meet some other way.

If the bug was there for everyone, I guess that would have been filtered out of the release.

---

### Post by Jonor on 2014-01-03
Strangely, the address input boxes are present on a machine that has 13.10 but absent on a machine with 12.04.

---

### Post by grahammechanical on 2014-01-03
There is something else that we need to understand. If we file a bug in Ubuntu Launchpad then a member in the Ubuntu triaging team will investigate and if it is in code from an upstream project such as Gnome, then all they can do is pass the bug report to those upstream developers. It is then up to that project's developers to fix it.

Linux developers have always used users as testers. It is the way that free and open source code is developed. Ubuntu has a Quality and Assurance team that runs all kinds of tests on Ubuntu development code. Volunteers have been very busy this last year writing these tests and developing an automated test system. The results of these tests are not secret.

[http://ci.ubuntu.com/smokeng/trusty/touch/](http://ci.ubuntu.com/smokeng/trusty/touch/)

And if you are thinking "that's for Ubuntu Touch." Then take a look at the results for the desktop

[http://ci.ubuntu.com/smokeng/trusty/desktop/](http://ci.ubuntu.com/smokeng/trusty/desktop/)

And this is for code that will be in the next release of Ubuntu (14.04). Now, that is a different way of doing things. Furthermore, the Ubuntu bug squad team has recently been merged with the Ubuntu Q and A team.  That will have a benefit on Ubuntu quality. And if we are really concerned about bugs not getting fixed we can always get involved in testing and may be even going so far as getting involved in triaging bugs ourselves.

[https://wiki.ubuntu.com/QATeam/Roles/](https://wiki.ubuntu.com/QATeam/Roles/)

There is another aspect of Linux development that says if you do not like something do not just complain. No, get involved in fixing it.

Regards.

---

### Post by deadflowr on 2014-01-03
> **ardchoille422 said:**
> Could the reason for the lack of reports from other users be that the other users see that some bugs go untouched for years so they feel it's a waste of time to file a report?

Simpler answer is that others don't have the reported problem.
I don't, at least.

---

### Post by lykwydchykyn on 2014-01-03
I remember discussing this before.  I have observed this bug too, though it doesn't technically affect me, so I confirmed the bug.  We'll see what happens.

I think you said it yourself:  there's no incentive to fix some of these bugs.  But it's not for lack of "shareholder looking over their shoulder"; Canonical is still a business, they still have a profit motive.  Gnome is largely developed by RedHat developers, and they have share holders.  

The problem is that nobody really has *desktop linux* as a product.  Canonical's business efforts are focused on mobile and cloud services, RedHat is focused on the server.  If there is someone out there in the wider developer community for whom this is an issue, they will probably get it fixed.  If it's not, they probably won't.

---

### Post by hoopia on 2014-01-03
Bug reporting and management is very complicated, especially when you have a lot of hands stirring the pot. It's perfectly normal for certain bugs to be backlogged and not addressed. That doesn't mean they are being ignored, it just means they are not a high enough priority to be fixed yet. Developers can only allocate a finite amount of time to work on bugs and features, and it's always a constant battle for which bugs will be fixed and which ones will be backlogged or delayed. I would say keep on submitting bug reports, and make them as accurate as possible. It's better to get it into the system than ignoring the bug.

---

