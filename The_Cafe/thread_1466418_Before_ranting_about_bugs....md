---
title: "Before ranting about bugs..."
date: 2010-04-30
forum: The Cafe
---

### Post by 3rdalbum on 2010-04-30
I'd just like to advise users here: If you've been using Ubuntu for a year or more, and you've just upgraded to 10.04, and you **complain** or **rant** that Ubuntu 10.04 is buggy... well, I'm going to ask you if you did your duty and actually helped test the betas.

Bugs in Ubuntu can't be fixed if nobody knows about them.

If you do come across bugs in Ubuntu 10.04 and want to report them for possible inclusion in Post-Release-Updates, then I'd recommend you use the "apport-bug" command; for instance, for a bug in GDM, you'd run:

```
apport-bug gdm
```

It will automatically grab log files and relevant information about your system and attach it to the bug report, which makes the developer's job easier.

---

### Post by Endolith on 2010-04-30
Reporting bugs is a lot of work, and basically futile.  Unless you expect everyone to go to school for computer science for 4 years, it's not something we can fix.  So we try to do the right thing and report bugs, we sit back, and... nothing happens.  The bugs go unfixed and the bug reports go ignored for years.  So what's the point?  You can even get yelled at for making a mistake in your report, or not reconfiguring your entire system so you can do a stack trace, or filing a duplicate bug report even though you searched very carefully beforehand.

---

### Post by 3rdalbum on 2010-04-30
I've never been yelled at for a duplicate bug report. The Ubuntu triagers are very respectful. It's not hard to file a bug report either - the apport-bug utility collects all relevant information to attach, all you have to do is describe what you're doing when the problem occurs.

There are bugs in Lucid that I have reported and that have not been fixed or even commented-on. If somebody complains about those bugs, then fair enough - they've been reported and not fixed, probably not even looked at. But many bug reports have been looked at and fixed - yours might be one of them, if only you'd reported it.

But people who are well able to test SHOULD. It's in all of our best interests to. Ubuntu is free, and this is a chance to give something back not only to Ubuntu, but to the whole community.

---

### Post by julianb on 2010-04-30
> well, I'm going to ask you if you did your duty and actually helped test the betas.

I tested the betas, but I disagree that it is a "duty" to do so. 

You are right on the money with your statement that bugs that are never reported are never fixed, though. So:

If you find a bug, report it!

AND if you want to make it easy to report bugs, help us make sure the [Reporting Bugs documentation]("https://help.ubuntu.com/community/ReportingBugs") is clear and concise!

---

### Post by pazuzuthewise on 2010-04-30
> **3rdalbum said:**
>  I'm going to ask you if you did your duty and actually helped test the betas.

Ubuntu's motto was "Linux for Human Beings" and not "Linux for people with computer know-how", and not even "for linux enthusiasts" so testing beta-software is not a duty, but a personal option, limited by the user's knowledge and available time. If one has to work on a system, having to meet a deadline etc., that person cannot be reasonably expected, at the same time, to test betas.

---

### Post by cariboo on 2010-04-30
Testing, may not be a duty, but because of all the different hardware configurations, it would be nice if more people took part in testing. You don't have to be a computer whiz to do it. Bug reporting has become pretty automated. As the op stated using the bug reporting feature really helps make Ubuntu better.

One of the reason some bugs go a long time with out any attention, is that if it only affects one or two people, there has to be really good documentation eg: what you did yo do to create the failure, complete computer specs and an other information you think will solve the problem.

Another reason some bugs seem to have no action, is because Ubuntu relies on the upstream to repair bugs too. For example, a few releases back there was a bug where the screensaver would start up while watching a movie using vlc, the maintainer of the screensaver flat out refused to fix the problem, as it didn't affect him, fortunately others have stepped up to the plate and created work arounds, so this is no longer a problem.

We don't pay Canonical anything to use Ubuntu, so in return it would be nice if the users gave something back, and bug reporting is one of the simplest ways.

---

### Post by aysiu on 2010-04-30
> **3rdalbum said:**
> I'd just like to advise users here: If you've been using Ubuntu for a year or more, and you've just upgraded to 10.04, and you **complain** or **rant** that Ubuntu 10.04 is buggy... well, I'm going to ask you if you did your duty and actually helped test the betas. I did, and none of those bugs has been fixed.

Here's one from September 2008:
[network manager slow to reconnect after suspend/resume](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405)

It got confirmed a while ago and it appeared to be somewhat fixed in Karmic but has come up again in Lucid and never got fixed before final release.

Here's another one I reported back in October 2009:
[Internal mic doesn't work with default settings (need to use line-in) ](https://bugs.launchpad.net/ubuntu/+bug/441480)

Never got fixed or even confirmed. No one asked me questions about it.

From October 2009 (not fixed for Karmic or Lucid):
[bcmwl kernel source needs to be reinstalled for Broadcom 4312 to work](https://bugs.launchpad.net/jockey/+bug/441492)

Odd that Broadcom 4312 works out of the box with Ubuntu 9.04. Regression much?

Related: [Lucid Alpha 3: hardware drivers can't fetch STA drivers for Broadcom](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/534824)

Reported in March:
[Network Manager prompts for already saved password upon resume (makes me click Connect without re-entering password)](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/538614)

No response.

Reported a couple of weeks ago:
[Official Ubuntu Documentation wiki pages Inaccessible from Android](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/566728)

No acknowledgement.

Hey, I know the developers work hard. I know it's a thankless job. But I don't like people insinuating that those who complain have not filed bugs. Filing bugs doesn't magically make those bugs go away. In fact, I've found the vast majority of bugs I've filed have been completely ignored.

---

### Post by 23meg on 2010-04-30
> **aysiu said:**
> But I don't like people insinuating that those who complain have not filed bugs. Filing bugs doesn't magically make those bugs go away. In fact, I've found the vast majority of bugs I've filed have been completely ignored.

I don't think anyone is saying that filing bug reports makes bugs go away. 

Filing bug reports is a *necessary* condition of bugs getting fixed; not a *sufficient* condition.

---

### Post by Irihapeti on 2010-04-30
I think ranting is a waste of time, anyway. It solves nothing. It only raises the blood pressure and annoys other people.

---

### Post by aysiu on 2010-04-30
> **23meg said:**
> I don't think anyone is saying that filing bug reports makes bugs go away. 

Filing bug reports is a *necessary* condition of bugs getting fixed; not a *sufficient* condition.
But the problem is not bugs not being reported. The problem is bugs not getting fixed. Some are upstream bugs. Some the developers just can't get to in time. That's fine. I understand that.

I just don't see the issue being "Hey, we could have put out a better release if people had just reported more bugs."

There are enough bug reports.

---

### Post by wilee-nilee on 2010-04-30
I think the problem is it is very difficult to try and help somebody who rants, rather then asks for help. A rant is a one sided view some of the time and may be filled with user error and misunderstanding of the OS. It is part of human nature though to vent so, if we can get to the issue in a problem together in the end we all learn from the experience.

---

### Post by cariboo on 2010-04-30
The Broadcom 4312 bug probably wasn't fixed, as you now install it through the restricted drivers. I agree it should be included on the Live CD, but the only way that's going to happen is if Broadcom open sources the driver.

---

### Post by 23meg on 2010-04-30
> **aysiu said:**
> But the problem is not bugs not being reported. The problem is bugs not getting fixed. Some are upstream bugs. Some the developers just can't get to in time. That's fine. I understand that.

I just don't see the issue being "Hey, we could have put out a better release if people had just reported more bugs."

I don't think the issue is being framed as a casual relation between the ratio of bugs reported vs. bugs encountered and release quality. That would indeed be incorrect, but nobody is saying that. There are too many other factors affecting release quality for us to be able to test such a possible relation.

The main point in encouraging people to report bugs rather than / before ranting about them should be cultural, not practical. We shouldn't say to people "Had you reported more bugs, more bugs would have been fixed". We shouldn't use "Did you report it? If not, shut up." as a retort against complaints, no matter how immature. We should simply describe in simple terms *why* reporting bugs is a necessary condition for bugs getting fixed, and encourage people to *get better at reporting bugs*; not necessarily file more bug reports. 

My naive observation is that on average, good bug reporters report significantly *less* bugs than inexperienced and/or incompetent ones who are equally active (since good reporters know how to look for duplicates, how to add information to an existing bug, when and how to go upstream, when *not* to report a bug, etc.) but their contribution is much more valuable.

> **aysiu said:**
> There are enough bug reports.

However, there aren't enough well reported, complete, actionable bug reports, and that does have an impact on quality, as opposed to the mere number of bugs reported. The responsibility for this situation is shared between reporters, triagers, developers and people who are in a position to educate new users on good participation practices.

---

### Post by Irihapeti on 2010-04-30
My experience is that most of the bugs I've reported have been actioned, if not resolved yet.

One thing I've learned is to look around for similar bugs. That may give a clearer idea of what's happening and also suggest further tests to do, which can then be added to one's original bug report.

Maybe I'm just fortunate, or I'm able to do the kind of analytical thinking that helps sort out problems. Not sure.

---

### Post by sixthwheel on 2010-04-30
Why is it that we need a new release every 6 months?
Wouldn't it be better to have a relatively bug free release when it is actually ready to be released, then just pushing these things out the door every 6 months?

What would happen if a release was late coming out every once in a while?
Would a volcano erupt in Iceland or sumpin? :confused:

---

### Post by WinterRain on 2010-04-30
> **Irihapeti said:**
> I think ranting is a waste of time, anyway. It solves nothing. It only raises the blood pressure and annoys other people.

This.

---

### Post by WinterRain on 2010-04-30
> **sixthwheel said:**
> Why is it that we need a new release every 6 months?


Because if they didn't, it would be debian, which you are free to use.

Besides, there are going to be 4 point releases for lucid. Just because something gets released, doesn't mean you have to use it. Wait until it's been out a while, and there you have it, your ultra stable distro.

---

### Post by sixthwheel on 2010-04-30
> Because if they didn't, it would be debian, which you are free to use.
I don't understand your answer, and why should I use this Debian thing?

---

### Post by WinterRain on 2010-04-30
> **sixthwheel said:**
> I don't understand your answer, and why should I use this Debian thing?

Ubuntu is based heavily on Debian, which has been around since '93. And they have a very lengthy development process before releasing a final version. But by doing so, packages are a bit older than some may like.

---

### Post by 3rdalbum on 2010-04-30
If you report bugs and they don't get fixed or even commented on, then rant away.

If you are able to test betas and report bugs, and you don't, then you shouldn't rant when there are bugs. Bugs only exist because good people don't report them.

---

### Post by DeMus on 2010-05-01
> **sixthwheel said:**
> Why is it that we need a new release every 6 months?
Wouldn't it be better to have a relatively bug free release when it is actually ready to be released, then just pushing these things out the door every 6 months?

What would happen if a release was late coming out every once in a while?
Would a volcano erupt in Iceland or sumpin? :confused:

My thoughts exactly:

Make a new release every year to have a fixed date for the release
Support it 2 years instead of 1-1/2 for normal or 3 for LTS versions. This way there are just 3 versions active. For example:
9.04, 10.04 and the start for 11.04
Now we have 5 versions active:
8.04 (LTS), 9.04, 9.10, 10.04 and soon 10.10
There is more time to test and test again. Now in 6 months a release has to be shipped with all the catastrophic results we see here in the forums.
The relationship with the Iceland volcano is not that bad chosen, thank you for that.

---

### Post by Kangarooo on 2010-05-09
Im tryng to live every day as last- fully completly do as much possible.
on updating from 9.10 to 10.04 im unable to work fully theres a lot bugs i got witch i want to report. :)
And for Programmers- i cant understand how its possible to make bug go away then solve another bug and with that make 2 new bugs. Thats happening with a lot programms or packages. If developer is making program hi knows this programm completly. Who are thouse who removes bugs and makes a new bug. Who are they?
If i fill a bug why theres any questions? Programmer doesnt know his programm? "Where in my programm im making is a bug?" Like even not any ideas what could possibly make bug. Like they not even tryng to check if there is a bug.
Even if theres files uploaded using ubuntu-bug packagenam or updating bug with apport-collect bugname it looks like that info isnt helping understand bug. Or is there any programmer of programm looking at that info?
Also theres no need to make more bug reports. They are not fixed or fixed with adding new bug. Something like conspiracy like inceting vacine witch makes organism to be sick with new mutated disease or trying to make desease feel imune from that vacine.
There wont also be all bug reports since not all users are coming to LP to report bug they dont know about it. Usual users.
But thouse who have come to LP and added more then 50 bugs i think are seeing theres no use to post bugs since programmers dont know their programm and ask where what and how went wrong. Ive also sometimes making screenshots. Now im also making videos. Also not helpfull since bugs arent fixed by videos.
Programmers want more bugs? Integrate LP as programm in Ubuntu and every usual user will overflood LP with bugs only problem wont be solved with that. Problem is bugs not being fixed. And first of all already reported bugs needs to be fixed before asking for more bug reports.
What does it mean report more bugs? Like someone who makes ubuntu puts all together doesnt do his job testing and just ask for all users to just post? That like training monkeys to do that job.
Programmers i know personaly- they know what they programm they test and then only make release. And it works.
So now ill post some more bugs again thinking they will be fixed and hoping that no buggy fixes are made.
Also ive seen many patches witch arent put to updates i hope to seen them coming with fixes.
Also im starting to learn how to make bug fixes so learning also programming languages and i want to find best way with easiest programms to get packages make fix and post to projects.


-----Update
i did what is written here [https://wiki.ubuntu.com/Apport#How%20to%20enable%20apport](https://wiki.ubuntu.com/Apport#How%20to%20enable%20apport)
2 commands
```
sudo service apport start force_start=1
sudo nano /etc/default/apport
... and change enabled from "0" to "1". 
and then to save and exit ctrl+shift+z or x
```
and while i made something to eat i got 4 apport bug reports witch i dont know about what to report becouse for me all is working but these crash reports were waiting for my guidance.
I know i would have some x screenaver by default and maybe not disabling it would not make these apport bug reports becouse i disbled somekind gnome scrensaver when i was asked do i want to disable when i entered xfce screensaver section witch has changed since upgrade.
So apport enabling i hope is working and will finally make ubuntu and xubuntu working when making upgrade

---

### Post by uRock on 2010-05-09
> **3rdalbum said:**
> I'd just like to advise users here: If you've been using Ubuntu for a year or more, and you've just upgraded to 10.04, and you **complain** or **rant** that Ubuntu 10.04 is buggy... well, I'm going to ask you if you did your duty and actually helped test the betas.

Bugs in Ubuntu can't be fixed if nobody knows about them.

If you do come across bugs in Ubuntu 10.04 and want to report them for possible inclusion in Post-Release-Updates, then I'd recommend you use the "apport-bug" command; for instance, for a bug in GDM, you'd run:

```
apport-bug gdm
```It will automatically grab log files and relevant information about your system and attach it to the bug report, which makes the developer's job easier.
My system got buggier instead of less buggy when the release came out. I beta tested with very few issues. Now Lucid is unusable on my nVidia system.

---

### Post by uRock on 2010-05-09
> **23meg said:**
> However, there aren't enough well reported, complete, actionable bug reports, and that does have an impact on quality, as opposed to the mere number of bugs reported. The responsibility for this situation is shared between reporters, triagers, developers and people who are in a position to educate new users on good participation practices.
I blame apport for being junk. Half of the bugs I have reported were followed by inquiries directing me to documentation that had nothing to do with getting the right answers. The dev sent me a link to a doc explaining how to get more info on the bug, but he sent me the wrong link and gave me **** for not getting the results he wanted. Luckily when the bug was fixed for Rhythmbox, it fixed the equivalent bug in audacious2.

---

### Post by Old_Grey_Wolf on 2010-05-09
> **WinterRain said:**
> Ubuntu is based heavily on Debian, which has been around since '93. And they have a very lengthy development process before releasing a final version. But by doing so, packages are a bit older than some may like.

True :)

People need to learn about a distro before using it. Some are intended to be bleeding edge, and others are intended to be very stable. Then there are those somewhere in the middle.

I've seen people rant because the Ubuntu repository has old versions of OpenOffice.org for example. However if they switched to a distro with a rolling release they would rant about the constant breakage. 

Linux is a place were you have choices. If you want something that is very stable you can choose a distro for that. If you want the newest of everything, you can choose a distro for that as well. You need to understand the consequences of your choice.

However, people seem to pick a distro; then, expect it to magically change its philosophy to satisfy their desires. They are only one user of the distro, when there are other people using it with possibly different expectations.

---

### Post by uRock on 2010-05-09
The reason you see those complaints here is because ubuntu is by far the best system for newer users. People want stability and newer programs. Ubuntu aims to do both, hence the 6 month cycle.

---

### Post by Old_Grey_Wolf on 2010-05-09
> **uRock said:**
> The reason you see those complaints here is because ubuntu is by far the best system for newer users. People want stability and newer programs. Ubuntu aims to do both, hence the 6 month cycle.

That is what **you think people expect**. For some users, Ubuntu may not be the best system. Some users may have different expectations from yours.

---

### Post by Irihapeti on 2010-05-09
> **Old_Gray_Wolf said:**
> ... I've seen people rant because the Ubuntu repository has old versions of OpenOffice.org for example. However if they switched to a distro with a rolling release they would rant about the constant breakage.

I suspect that some people just like to rant. If there wasn't anything to rant about, they'd think something up. :)

/hides

---

### Post by uRock on 2010-05-09
> **Old_Gray_Wolf said:**
> That is what you think people expect. For some users, Ubuntu may not be the best system. Some users may have different expectations from yours.
No, I don't think that. I have asked people, so I have a small taste of what people may or may not want. I am not saying everyone want the same thing. I just want an OS that works and after testing, I went back to Karmic and installed the programs I needed newer versions of from source. I soon plan to move to Debian, because I am feeling more confident in my maintaining capabilities.

> **Irihapeti said:**
> I suspect that some people just like to rant. If there wasn't anything to rant about, they'd think something up. :)

/hides
We see that every release, right?

---

### Post by MarcusW on 2010-05-10
Doesn't really seem fair to expect regular users to report bugs. This section does kinda give users "permission" to complain.

---

### Post by 3rdalbum on 2010-05-10
> **MarcusW said:**
> Doesn't really seem fair to expect regular users to report bugs. This section does kinda give users "permission" to complain.

Ubuntu makes it so easy to do, though.

I agree that Apport leaves a lot to be desired, but it's handy for getting all relevant data before submitting a bug report.

---

### Post by MarcusW on 2010-05-10
> **3rdalbum said:**
> Ubuntu makes it so easy to do, though.

I agree that Apport leaves a lot to be desired, but it's handy for getting all relevant data before submitting a bug report.

The problem I have is that I don't really want to look if someone else already found the bug, if it's really not a bug just my hardware drivers etc. I mean, reporting bugs that are already reported or aren't anything the Ubuntu team can change seems kinda counter-productive.

You have a good point with Apport though, seems to make things alot easier. Is apport just for Ubuntu?

---

### Post by Ms_Angel_D on 2010-05-10
This thread has descended into a discussion, to avoid closure I have moved it to the cafe, as Testimonials & Experiences is not a discussion area of the forum.

Angel

---

### Post by gabriella on 2010-05-10
> **cariboo907 said:**
> Testing, may not be a duty, but because of all the different hardware configurations, it would be nice if more people took part in testing. You don't have to be a computer whiz to do it. Bug reporting has become pretty automated. As the op stated using the bug reporting feature really helps make Ubuntu better.

One of the reason some bugs go a long time with out any attention, is that if it only affects one or two people, there has to be really good documentation eg: what you did yo do to create the failure, complete computer specs and an other information you think will solve the problem.

Another reason some bugs seem to have no action, is because Ubuntu relies on the upstream to repair bugs too. For example, a few releases back there was a bug where the screensaver would start up while watching a movie using vlc, the maintainer of the screensaver flat out refused to fix the problem, as it didn't affect him, fortunately others have stepped up to the plate and created work arounds, so this is no longer a problem.

We don't pay Canonical anything to use Ubuntu, so in return it would be nice if the users gave something back, and bug reporting is one of the simplest ways.

I agree with most this but would just add. I've reported a couple of bugs which were likely to only affect a small number of people. Since I'm still learning I was aware that I probably needed to provide more information. I added in the initial report "tell me what additional info to provide and I'll do so" But I never ever got anything back! :(

---

### Post by CharlesA on 2010-05-10
> **gabriella said:**
> I agree with most this but would just add. I've reported a couple of bugs which were likely to only affect a small number of people. Since I'm still learning I was aware that I probably needed to provide more information. I added in the initial report "tell me what additional info to provide and I'll do so" But I never ever got anything back! :(

Same here. I ended up reporting a bug I ran into on 5/5/10 after a kernel upgrade and all I got was 2 other people that had the same problem. The bug is still listed as "incomplete" since there has been no direction from the developers as to what specific information they need.

Not to mention that the problem was on the server kernel and I really don't want to screw around with "upstream kernels" when I need the server up and running instead of broken and not doing its job. I did try installing one of the "testing" kernels and it didn't fix anything, but caused more problems.

My solution was to just do a clean install and see what happens and that fixed the problem (for me), but that doesn't fix the bug.

---

### Post by RiceMonster on 2010-05-10
No one has a "duty" to do beta testing. Yes it is very helpful, but it is certainly not required in any way that they do so.

---

### Post by uRock on 2010-05-10
> **RiceMonster said:**
> No one has a "duty" to do beta testing. Yes it is very helpful, but it is certainly not required in any way that they do so.
You're wrong, you're wrong, you're wrong! Just kidding, you are right. :P

Some people may not like using the bug reporting software(apport), because they are paranoid that more info is being uploaded about their system than they prefer, such as that Windows one that tells you nothing about what it is doing. Or, they just may not want to create the launchpad account.

We must remember that not everyone can read the technical output that shows up on the launchpad page to know if it is even correct.

This is why I just recommend people who want a stable system to stay a few months behind the release schedule. Look at all of those problems people were having with Jaunty and Karmic. Those two are unbreakable on my system nowadays.

---

### Post by Frogs Hair on 2010-05-10
I have encountered two bugs in 10.04 both of which have been reported by others , so there is nothing to be done but wait. I would only download a beta release if I intended to participate in testing or if I knew it was fairly stable.

---

### Post by aysiu on 2010-05-10
> **uRock said:**
> Or, they just may not want to create the launchpad account. I think in the long run, if Ubuntu ever becomes some semblance of mainstream (the way Mac OS X is), the bug reporting process has to be amended. You cannot expect everyday users trying to auto-report a bug after a crash to create a Launchpad account, determine if their bug is a duplicate of an already existing bug, and then add in more details.

I think it'd make more sense for you to simply see the name of the bug that's generated and if a duplicate is detected a notification that you are the Nth person to experience that problem and that the developers will be notified with your report and relevant information from your system (which would be an expandable arrow, so you could see exactly what information is being sent to the developers--it would, of course, be gibberish to most users, but for the power users who care, it would offer some measure of comfort that Ubuntu isn't spyware).

With all due respect to 3rdalbum, I'm still not sure I get the point of this thread. If your customer service is overrun with support calls, you don't put an advertisement out asking for more support calls so people can get a busy signal. If you're out of stock of a sales item, you don't put out a new ad in the paper advertising that people must come now to get it before it's out of stock. Likewise, if there are already thousands of unanswered or unsolved bug reports, you don't ask people to file more bug reports. You could encourage people to refine existing bug reports (put in more details and terminal output). You could tell people to click "this bug affect me also" so the developers have a better sense of how prevalent a bug is. You could tell folks who have any programming skills to submit patches.

But asking for more bug reports at this juncture will not get Ubuntu anywhere.

---

### Post by Ebere on 2010-05-10
I tested the beta.

I tried to file bug reports.

All that happened was hours of confusion, and ultimately frustration. 

As the program wanted to update this and that and the other, then complained that the updates were done wrong. Do them again. 

Then they are not enough, more is needed. 

And in the end... still impossible for me to file a bug report, and my system was now wonkier than ever because of all the changes.

~~~

If you want bug reports, make them so simple that a kindergarden student could do them.

And I agree with aysiu. If a bug has already been reported, there should be some way to get on a list as someone having the same problem. And who will get reports of progress, if any, in fixing the bug.

~~~

Also: seems a bit confusing to tell people to look to see if a bug is already reported, and if it is, do not make a report... 

Then to say that a bug isn't/wasn't fixed, because there were not enough people affected by it.

---

### Post by uRock on 2010-05-10
> **Ebere said:**
> Also: seems a bit confusing to tell people to look to see if a bug is already reported, and if it is, do not make a report... 

Then to say that a bug isn't/wasn't fixed, because there were not enough people affected by it.
What is meant by don't report is not to start a new bug, but just click the this affects me button and if you have more info to add to the bug report, then scroll down and add it.

Hopefully the process will get more refined and get to a point where they won't need you to have an account to file. I think that one of the reasons they require an account is so that they can contact you to get more info, if needed. It also keeps trollers from being able to create B.S. bugs easily. If the troller makes a bunch of bogus bug reports, then they can be more easily tracked and ignored.

---

### Post by KiwiNZ on 2010-05-10
Saying someone is "ranting" seems to be the new dismissive like "fanboi"

Applying dismissives is just another avoidance . Recognize , accept , fix and move on, and then you have a win.

---

### Post by 23meg on 2010-05-10
> **aysiu said:**
> I think in the long run, if Ubuntu ever becomes some semblance of mainstream (the way Mac OS X is), the bug reporting process has to be amended. You cannot expect everyday users trying to auto-report a bug after a crash to create a Launchpad account, determine if their bug is a duplicate of an already existing bug, and then add in more details.


That's a non-issue, since "everyday users" using preinstalled (or otherwise somewhat "mainstream"ed) Ubuntu would be using stable releases, and Apport is disabled by default in stable releases.

[QUOTE=aysiu]With all due respect to 3rdalbum, I'm still not sure I get the point of this thread. If your customer service is overrun with support calls, you don't put an advertisement out asking for more support calls so people can get a busy signal. If you're out of stock of a sales item, you don't put out a new ad in the paper advertising that people must come now to get it before it's out of stock. Likewise, if there are already thousands of unanswered or unsolved bug reports, you don't ask people to file more bug reports. You could encourage people to refine existing bug reports (put in more details and terminal output). You could tell people to click "this bug affect me also" so the developers have a better sense of how prevalent a bug is. You could tell folks who have any programming skills to submit patches.

But asking for more bug reports at this juncture will not get Ubuntu anywhere.[/QUOTE]

However, [as I said before]("http://ubuntuforums.org/showpost.php?p=9205980&postcount=13"), asking more people to be active and more proficient in testing isn't necessarily asking for more bug reports. And we should emphasize that distinction. 

And no, we shouldn't be asking *everyone* to to join testing and file bug reports; more is not necessarily merrier. The problem is not that not every user who is having a problem is filing bug reports; it's that lots of people who are clearly *capable of* taking concrete steps in the way of making Ubuntu better are instead just ranting about bugs in Ubuntu releases. And this is a cultural problem: it's mainly due to their past experience with the proprietary software consumerism paradigm, where complaining about a product and not choosing to buy it are the the two things you can do that can have an effect on the future of the product.

That's not how things work in free software, and we should make that *known*; not enforce it as if it were a rule upon everyone. We should let people know that they have other, much more effective options than merely complaining and choosing something else.

---

### Post by Ebere on 2010-05-10
> **uRock said:**
> What is meant by don't report is not to start a new bug, but just click the this affects me button and if you have more info to add to the bug report, then scroll down and add it.

Hopefully the process will get more refined and get to a point where they won't need you to have an account to file. I think that one of the reasons they require an account is so that they can contact you to get more info, if needed. It also keeps trollers from being able to create B.S. bugs easily. If the troller makes a bunch of bogus bug reports, then they can be more easily tracked and ignored.

Ah.

Thank you.

I never got that far.

---

### Post by Ebere on 2010-05-10
> **KiwiNZ said:**
> Saying someone is "ranting" seems to be the new dismissive like "fanboi"

Applying dismissives is just another avoidance . Recognize , accept , fix and move on, and then you have a win.

Well said.

---

### Post by aysiu on 2010-05-10
23meg, I'm addressing the original OP: > Bugs in Ubuntu can't be fixed if nobody knows about them.

Developers have plenty of bugs to know about. Ranting is fine, especially if you have already filed bugs that have been ignored or have not yet been fixed.

But ranting and doing something productive are not mutually exclusive. [I certainly encourage people to be productive](http://ubuntuforums.org/showthread.php?t=78741), but that doesn't preclude ranting.

---

### Post by wieman01 on 2010-05-10
> **3rdalbum said:**
> I'd just like to advise users here: If you've been using Ubuntu for a year or more, and you've just upgraded to 10.04, and you **complain** or **rant** that Ubuntu 10.04 is buggy... well, I'm going to ask you if you did your duty and actually helped test the betas.
A couple of comments though... 

**A)** Reporting bugs through Launchpad is a nightmare, even for advanced users like me.
**B)** Advanced users have pointed out that their bug reports have been ignored. Some of those sit on the board of these forums.
**C)** Reporting bugs isn't mandatory, it's a choice, a right. If users can't expect a reasonably stable software without doing their part, they have a right to complain and they should be carefully listened to, because they represent the majority of users, like it or not.

---

### Post by KiwiNZ on 2010-05-10
> **wieman01 said:**
> A couple of comments though... 

**A)** Reporting bugs through Launchpad is a nightmare, even for advanced users like me.
**B)** Advanced users have pointed out that their bug reports have been ignored. Some of those sit on the board of these forums.
**C)** Reporting bugs isn't mandatory, it's a choice, a right. If users can't expect a reasonably stable software without doing their part, they have a right to complain and they should be carefully listened to, because they represent the majority of users, like it or not.

Agreed

---

### Post by nothingspecial on 2010-05-10
I don`t like the fact that your launchpad password **_has_** to have an uppercase letter in it.

Is that a bug?

---

### Post by Irihapeti on 2010-05-10
I'll say +1 to wieman01 as well. I'll also add that a curt comment from a dev or someone telling you that you haven't done the reporting process properly isn't exactly encouraging.

I strongly dislike the idea that because Ubuntu is "free", we have no right to complain/critique/whatever. It may be "free" for some, but for many of us, it is NOT free. It costs us in the time taken to file bug reports, test things and so on.

---

### Post by Mark Phelps on 2010-05-10
> **23meg said:**
> ... more is not necessarily merrier... 

Thank you for saying that.

And, that is plainly evident in the final few weeks before a release when legions of folks who know NOTHING about testing software, download and install the latest "beta" -- and then rant on about all the problems they're having -- when most, if not all of those, are already covered in the Testing subforum.

Look at all the traffic that merely moving the window buttons to the left has generated.  Every day, it seems that there are more posts asking the same thing -- how to move them to the right -- and the answers have been posted again, and again, and again.

In a community of "enthusiasts" (or "hobbyists" if you prefer that term), the culture is one of looking for solutions first, and then asking if you don't find what you need.  In a community that Ubuntu is (unfortunately) evolving into -- you whine first, don't even both to TRY to find a solution, and then rant on if the answer isn't some simple point-and-click solution.

Unfortunately, I think this "ranting" is only going to get a lot worse, not better.

---

### Post by Ebere on 2010-05-10
> **Mark Phelps said:**
> Unfortunately, I think this "ranting" is only going to get a lot worse, not better.

And ranting about the ranting is going to help...

---

### Post by gabriella on 2010-05-11
> **nothingspecial said:**
> I don`t like the fact that your launchpad password **_has_** to have an uppercase letter in it.

Is that a bug?

It would be easier if you didn't HAVE to create a launchpad acct. I would imagine that puts some people off. Not limited to just Ubuntu I loose track of all the accounts/User ID's /passwords I create and tend to avoid creating new ones.

---

### Post by 3rdalbum on 2010-05-11
> **aysiu said:**
> 23meg, I'm addressing the original OP: 

Developers have plenty of bugs to know about. Ranting is fine, especially if you have already filed bugs that have been ignored or have not yet been fixed.

If my (sadly neglected at the moment) project has a bug, I'd much prefer to be told first and given a chance to fix it, before somebody rants and says that my program is a piece of poop.

If you file a bug report early enough and it just gets ignored I wouldn't blame you for having a bit of a rant.

---

### Post by mcooke1 on 2010-05-11
Rant Rant (r[a^]nt), v. i. [imp. & p. p. Ranted; p. pr. &
 vb. n. Ranting.] [OD. ranten, randen, to dote, to be
 enraged.]
 To rave in violent, high-sounding, or extravagant language,
 without dignity of thought; to be noisy, boisterous, and
 bombastic in talk or declamation; as, a ranting preacher.

Why people need to rant on the internet on any subject totally escapes me, I simply do not understand.

---

### Post by CharlesA on 2010-05-11
Because the are annoyed/frustrated by something.

Would anyone give a rat's behind if someone was bitching and moaning about something called "Ubuntu" in the 'real world' ?

---

### Post by uRock on 2010-05-11
> **3rdalbum said:**
> If my (sadly neglected at the moment) project has a bug, I'd much prefer to be told first and given a chance to fix it, before somebody rants and says that my program is a piece of poop.

If you file a bug report early enough and it just gets ignored I wouldn't blame you for having a bit of a rant.
I think I can agree with this. If they act like Ford and fix their issues upon knowing they exist, then all is well. If they pull a Toyota and ignore a show stopper, then there is reason to rant.
> **CharlesA said:**
> Because the are annoyed/frustrated by something.

Would anyone give a rat's behind if someone was bitching and moaning about something called "Ubuntu" in the 'real world' ?
Nope.

---

### Post by nothingspecial on 2010-05-11
[[COLOR="Magenta"]A fine example of effective bug testing/reporting/fixing.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by 23meg on 2010-05-15
> **aysiu said:**
> 23meg, I'm addressing the original OP: 

Developers have plenty of bugs to know about.

Since [bugs are not technical debt]("http://www.rants.org/2010/01/10/bugs-users-and-tech-debt/"), more well-reported, actionable bug reports does not mean more backlog. It means better awareness of existing issues, and that is welcome regardless of how many bug reports you might already have in your bug tracker.

The thing to do if you have too many bug reports and you aren't coping well with them is to get more people to work on triaging and fixing them, and make adjustments to your procedures; not advising people to refrain from reporting bugs.

> **aysiu said:**
> Ranting is fine, especially if you have already filed bugs that have been ignored or have not yet been fixed.

But ranting and doing something productive are not mutually exclusive. [I certainly encourage people to be productive](http://ubuntuforums.org/showthread.php?t=78741), but that doesn't preclude ranting.

Ranting is perhaps fine (and mostly unavoidable) on an individual level, when one is very disappointed with something. It's not fine if it has become the de facto mode of communication of an entire group (some would call it "community") of users of a piece of software, to the extent that it defines their culture.

I'm not concerned about otherwise productive people blowing off some steam every once in a while; I do it myself. I'm concerned about the whole culture around Ubuntu and other groups of people who are new to free software turning into one of constant complaints, rants, mudslinging and infighting.

---

### Post by Kangarooo on 2010-06-02
First ill rant about what i want and then second part my responses to last 3 week posts.
1. my part)
Video drivers- will all cards drivers be made to work or slowly theyr drivers are beeing removed? Couse some of cards were working and not anymore like with latest Nvidia-177 my card is not there but already with Nvidia-173 witch my card should work- its already in middle of working and beeing removed- acting like working but actually not. And also maybe motherboard is the reason maybe some Xorg config. Omg i need to now start learning coding and understanding to make OS work my hardware?
Im having 7 video cards and im affected by problems thery drivers regresion and not solutions have. Whats with that?
I really believe Linux drivers should work faster then Windows drivers but i dont see that with theese 7 cards. Whats with that?
Heres Confuzius [http://www.friesian.com/confuci.htm](http://www.friesian.com/confuci.htm)
> Yì may be broken down [Analects IV:15] into:  zhong1, doing one's best, conscientiousness, "loyalty" [2]; and shù, "reciprocity," altruism, consideration for others, "what you don't want yourself, don't do to others" [Analects XV:24 or 23].

So with Confuzius my MSG to video developers who made my cards not work:I want all to work so im learning how to make something work and i want to know so im letting to know but dont make something regress to not work so you dont want something to not work.

2. responses part)
> **uRock said:**
> My system got buggier instead of less buggy when the release came out. I beta tested with very few issues. Now Lucid is unusable on my nVidia system.
This bug affects you and 1 more person.
Im even affected by one card never having a solution in linux.

> **MarcusW said:**
> Doesn't really seem fair to expect regular users to report bugs. This section does kinda give users "permission" to complain.
Here in forum ppl are already not-regular users so they report bugs. At least some portion of them.
Thouse who makes attention to problem by submitin info here and then not coming back and not making bug reports thouse are only regular users.

> **RiceMonster said:**
> No one has a "duty" to do beta testing. Yes it is very helpful, but it is certainly not required in any way that they do so.
Thats right so that should be made as voulentiering so all systems would work. Every hardware to be tested everyhardware needs to be accesible or its results either LP as bug reports or hardware checksite.

> **uRock said:**
> You're wrong, you're wrong, you're wrong! Just kidding, you are right. :P

Some people may not like using the bug reporting software(apport), because they are paranoid that more info is being uploaded about their system than they prefer, such as that Windows one that tells you nothing about what it is doing. Or, they just may not want to create the launchpad account.

We must remember that not everyone can read the technical output that shows up on the launchpad page to know if it is even correct.

This is why I just recommend people who want a stable system to stay a few months behind the release schedule. Look at all of those problems people were having with Jaunty and Karmic. Those two are unbreakable on my system nowadays.
Making no hardware bugs accesible to debuggers by telling everyone to stay away as long as possible from release will make release newer usable for thouse systems witch arent tested. That look true as we see now but that is really wrong couse making involvement in project would need to be envolvement in making project work for everyone and not only the envolved one. How can that be done? Maybe some hardware info site so best solution could be made or rewriten from zero maybe.. maybe (couse everything is possible) could make better solutions.

> **Ebere said:**
> 
If you want bug reports, make them so simple that a kindergarden student could do them.

And I agree with aysiu. If a bug has already been reported, there should be some way to get on a list as someone having the same problem. And who will get reports of progress, if any, in fixing the bug.
Yes bug report need to be easy understandable. Im tryng to make very simply understandable. In possible misunderstandings even provide Screenshot or video so theres no possibility to say its invalid.


> **Ebere said:**
> 
Also: seems a bit confusing to tell people to look to see if a bug is already reported, and if it is, do not make a report... 

Then to say that a bug isn't/wasn't fixed, because there were not enough people affected by it.
It would be better to maybe arrange bug reports by installations. If using ubuntu-bug would show for specific programm version reported bugs with the same problem name maybe would help developers and easyr to immidiatly be checked as Affects me too. But that affects me too as we know by most Colorite bugs about new ubuntu menu affect me too no one takes in mind even if bug reporter has really unbreakable arguments they also are not taken seriously and also bugs with only 2 affected ppl gets done with no debates. (just an idea i dont know whaat i just wrote) :)


> **gabriella said:**
> It would be easier if you didn't HAVE to create a launchpad acct. I would imagine that puts some people off. Not limited to just Ubuntu I loose track of all the accounts/User ID's /passwords I create and tend to avoid creating new ones.
If on password change i wont have free posibility to choose my password as i want thats against... and bad..
But without LP account posting bugs is bad since reported cant be contacted to make more info and time then is wasted for both (reporter since no progress results he cant get and debugger to read useles for him info) but thats only for now for the system witch doesnt report enought info. And also no LP acount reporting can give spam access without identifying Spamer couse registration requires email and email has id-ip. Without reg spam can be made and ip can be blocked but next ip can be used and harder to catch spamer. So that is more + for LP having an acount only posting and disabling no acount posting. Also this was used as wrong bug id getting wrong package bug reports.


> **nothingspecial said:**
> [[COLOR="Magenta"]A fine example of effective bug testing/reporting/fixing.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")
A fine idea for seeing all bugs in one place if developer knows what he is doing couse he knows all his code and if he is one. Not a fine example for checking if bug reported so bug or wishlist can be put many times(dublicating in lp). If he did everything everybody asked then only it was fine way. Also bug testing that way is not easy to see ifs someone has already posted the same test. That all is fine only for developer if he is alone doing all. Thats a big one topic with a lot pages not easy to manage. What if he stops developing this project and another will come in his position? Read all code and all topic. For the project there its mentioned its effective couse all is read by one developer and he checks his topic but what if some libraries change and all works for hime but not for someone else? Where to post to ubuntu-bug with Core Dump with a lot numbers and something understandable only by.. someone (including that developer).?

---

