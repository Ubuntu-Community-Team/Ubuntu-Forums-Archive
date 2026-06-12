---
title: "The meaning of LTS?"
date: 2009-01-28
forum: The Cafe
---

### Post by baggins on 2009-01-28
No I am not asking for the full version of the acronym, I know that it means "Long Term Support" :D

What I am asking is what people here think it  means, or ought to mean, in practical terms that is.
I guess that I am really trying to start a debate. Not even sure that this is the right place to do that, if not point me to where it. :)

**As a home user** I am quite happy updating every 6 months, I get new software with few stability issues.
The few issues that every upgrade brings are easily solved for my two private computers, by answering questions asked by the upgrade software. In some 4-5 years of using Ubuntu a dist upgrade has gone wrong exactly three times, all to do with ATI drivers :)

**As a professional**, managing a relative large number of ubuntu desktop machines at a university (Math/CS department), the update every 6 months policy is just not a realistic option.
We use unattended installations (currently PXE + d-i + shell scripting  but migrating towards [FAI]("http://www.informatik.uni-koeln.de/fai/") + [puppet]("http://reductivelabs.com/trac/puppet"))
There is no mechanisms in place to migrate such a system from one release to another, and to my knowledge no installation system exists that has such a mechanism (Love to hear that I am wrong though)
That means that a lot of work is required, in order to go from one dist to the next. I have done that three times so far, so I have the process structured pretty well by now, but even for me it's the work of almost a month (counting man hours) to migrate, test (on all HW platforms), trouble shoot, fix hardware problems, resolve package conflicts, retest etc.
And inevitably some package, that some one need, gets left out due to changing package dependencies that I am unaware of (resulting in a lot of unhappy people knocking on my door).

The natural step is to use the LTS versions and thus update at a lower frequency. This seems like a good idea until you realize that the support level for LTS is not really that good.
For dapper LTS the main issue that stuck in my mind was that the packers of firefox didn't release firefox 2 for dapper, all the while various security advisories were telling us, that continued use of firefox 1.x were both dangerous and stupid.
We ended up rolling our own firefox 2, using a ugly home made shell script in a cron job, bad bad solution all around.
There were other packages that we had to do the same with, so we ended up with a hodge pole of programs that came from a mix of home build packages, scripting and older/outdated software from the repos.
I think that firefox 2 was back ported to dapper eventually, but by then we had taken the consequence, and upgraded to feisty.

For Dapper the situation were that the main and restricted  repositories were sporadically updated and universe and multiverse not at all (yes, yes! I know there were exceptions, but by and large it's true :) ).

For Hardy it seems that the main and restricted are supported pretty well, light years better than for Dapper in fact. But it seems that universe and multiverse are still left behind. I know that no official guaranties are given for those two repos. but still!

[INDENT]Example:
[Puppet]("http://reductivelabs.com/trac/puppet") a centralized configuration management system, this is pure gold for those of us running large systems. There is a bug ([bug #176113]("https://bugs.launchpad.net/bugs/176113")) that causes the clients to exit on start (thanks to NetworkManager).
December 1, 2008 the bug was closed because it had been fixed in Jaunty Jacalope (Ubuntu 9.04). But ... That's the development version guys, not even intrepid, the latest stable release. That seems somehow ... wrong, doesn't it?? I mean it's not like the application crashing is a minor annoyance.[/INDENT]

My thoughts are these:
The main arguments I often get against using linux in larger deployments is the administrative aspect.
It's difficult to install, configure and maintain, and most important (to the bean counters at least) it takes too many man hours.
If we want to get a foothold in the large deployment/corporate environment this is the issue to tackle.
The LTS concept is a start, if packagers and developers support it that is.
At least the software that are targeted specifically at large deployments should be supported vigorously for the entire lifespan of a LTS release.

Ubuntu is one of, if not the most user friendly linux distros, it's neigh on perfect for newbies, like freshmen students. We have plenty of students that have no previous linux experience, and no real skills with or interest in computers. They all use Ubuntu with no big problems, that seems pretty damn impressive to me!
That makes Ubuntu the perfect starting point for schools, universities and corporations alike.

If we get the big boys on board the linux train, I think the vendors of software and hardware alike will start to support linux more and more.
And that can only make life better for all linux users.

Like I said I want to have a debate about what LTS, does and should mean.
Now I would like to hear what you think. Let's hear it all :D

-- Jon

---

### Post by overdrank on 2009-01-28
Moved to the cafe. :)

---

### Post by Zimmer on 2009-01-28
[http://www.ubuntu.com/news/ubuntu-8.04.2-lts-maintenance-release](http://www.ubuntu.com/news/ubuntu-8.04.2-lts-maintenance-release)

The updates for the interim releases are not continued for as long as this...

So support for the server edition of 8.04 goes on until 2013.

---

### Post by kavon89 on 2009-01-28
LTS, in my opinion, should focus on being as stable as possible, while keeping up with the latest and greatest in some aspects. The latest kernel or video drivers would not be the best idea, however security patches and fixes would. 

New application releases which are declared stable and is no longer in a testing phase should always be available to LTS releases also. Something like Firefox 3.0 Beta 3 really shouldn't have ended up in the Hardy release, but that was probably fixed in 8.04.x anyway.

---

### Post by t0p on 2009-01-28
As far as I know, the LTS version keeps getting security updates for as long as it's being supported. So, although a Hardy user isn't running the newest, shiniest version of each app, there shouldn't be any security issues. 

I'm talking in general terms, of course. There will always be exceptions to the rule. But on one's claiming that Linux is perfect. Are they?

---

### Post by shadylookin on 2009-01-28
as a home user LTS means nothing to me. In fact I frequently use developmental versions of linux oses just to see what the latest and greatest has to offer

I can see why if you're a business you would want a stable os that lasts for at least 3 years updating dozens, hundreds, or thousands of computers would become a real pain and costly

---

### Post by ssam on 2009-01-28
ubuntu (like all projects) has limited manpower. but it is very open to outsiders helping out.

if a bug has been fixed upstream, and you know which patch fixes it, then it is not too hard to help push through a stable release update (SRU). if you know enough to patch the program yourself, then you should be able to do it.

have a read of [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

the basic sets are
1) file a bug about the problem
2) find the upstream patch that fixes it
3) create a debdiff that fixes the ubuntu package (and updates the changelog)
(good stuff to read at [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide) )
4) test it, find other people to test it
5) start the SRu process

---

### Post by swoll1980 on 2009-01-28
I think Canonical offers some commercial software that allows you to address those issues. It's not free though. For example install a new version of firefox on all your boxes at the same time. Virtualization could be a option in this situation too.

---

### Post by Keyper7 on 2009-01-29
Ubuntu LTS releases are for those who don't mind a little obsolescence here and there, as long as there are security updates. Your professional case is where LTS is suited for. Canonical is trying to improve in this aspect and the Firefox problem you mentioned is an example: despite heavy criticism, they decided to release Firefox 3 still on beta for Hardy because they knew official support for FF2 would end soon and they didn't want to repeat the same mistake they did for Dapper.

And despite all the urban legends, the "supposed to be ultra-super-uber-stable" stigma that people insist on stamping over the LTS releases is not part of the definition of LTS at all. It just happens that LTS releases are almost completely frozen in terms of features while receiving bugfixes and small stability updates, so it *ends up* more stable than usual *after some time*, at the cost of not being up-to-date in terms of features.

They did try to make Dapper an "extra stable" version on release, and that's why it was released two months late. Nowadays, it's a general consensus among the developers that those two months were not really worthy.

---

### Post by -grubby on 2009-01-29
I think that it's for businesses, so they don't have to upgrade or teach their employees/users/whatever the new system every time. It saves money.

---

### Post by snowpine on 2009-01-29
I agree with the others; stick with 8.04 LTS for your business needs. If you need newer versions of any of the apps, can't you set up your own custom repository for this purpose?

---

### Post by baggins on 2009-02-03
> **Keyper7 said:**
> Ubuntu LTS releases are for those who don't mind a little obsolescence here and there, as long as there are security updates. Your professional case is where LTS is suited for. Canonical is trying to improve in this aspect and the Firefox problem you mentioned is an example: despite heavy criticism, they decided to release Firefox 3 still on beta for Hardy because they knew official support for FF2 would end soon and they didn't want to repeat the same mistake they did for Dapper.

And they are generally doing a very good job this time around. I am not gunning for the repos Cannonical maintains directly (main/restricted). 
I just really want to know what people, and particularyt the independent package maintainers (universe and multiverse) think about the LTS concept.
Is it necessary, a good idea, stupid, useless or .. 
> **Keyper7 said:**
> 
And despite all the urban legends, the "supposed to be ultra-super-uber-stable" stigma that people insist on stamping over the LTS releases is not part of the definition of LTS at all. It just happens that LTS releases are almost completely frozen in terms of features while receiving bugfixes and small stability updates, so it *ends up* more stable than usual *after some time*, at the cost of not being up-to-date in terms of features.

What I am after is not features, but programs that works! Take my example about puppet. 
The program, as it is, doesn't work in Hardy . But the argument given for not making a new package available is that "a fix has been released for Jaunty"!
This is a universe package, and therefor not under the same level of control as either main or restricted packages. But closing a bug citing that it has been fixed in the development release is a little "wrong" in my opinion. 
If the packager had said that he no longer  had access to a machine running Hardy, I would gladly have helped out. I don't know much about packaging but with some help I could probably have made something work.
But to just brush the problem off like that gets my hackles up.
I feel that it shows that at least some package maintainers is not taking the LTS concept serious.

> **snowpine said:**
> I agree with the others; stick with 8.04 LTS for your business needs. If you need newer versions of any of the apps, can't you set up your own custom repository for this purpose?
We can and we do, mostly for proprietary licensed software, but that doesn't help others. There is no point in all of us running the same packages of private repos. All the while others that can't or won't run a private repo write off ubuntu.
Also a year after the release of Dapper we were running 15-20 packages in our own repo, not including the proprietary packages. With all that that entails in terms of time spend building, testing and just keeping up to date with the development of each package. 
Hardy is better currently we only have 3 packages (again excluding all that nasty proprietary stuff ;) ), but that's 2 packages that are broken in the official repos (plus one that was dumped after dapper).

-- jon

---

### Post by Keyper7 on 2009-02-03
> **baggins said:**
> What I am after is not features, but programs that works! Take my example about puppet. 
The program, as it is, doesn't work in Hardy . But the argument given for not making a new package available is that "a fix has been released for Jaunty"!
This is a universe package, and therefor not under the same level of control as either main or restricted packages. But closing a bug citing that it has been fixed in the development release is a little "wrong" in my opinion. 
If the packager had said that he no longer  had access to a machine running Hardy, I would gladly have helped out. I don't know much about packaging but with some help I could probably have made something work.
But to just brush the problem off like that gets my hackles up.
I feel that it shows that at least some package maintainers is not taking the LTS concept serious.

Dude, what the hell?

In the link **you** posted, there is a message from almost one month ago:

> If you need a fix for the bug in previous versions of Ubuntu, please follow the instructions for "How to request new packages" at [https://help.ubuntu.com/community/UbuntuBackports#request-new-packages](https://help.ubuntu.com/community/UbuntuBackports#request-new-packages)

Did you do that? I'm looking at the bug list and it seems you didn't.

Sorry if I sound rude, but how about learning how the packaging, SRU and backporting process works before accusing someone of not being serious?

---

### Post by MaxIBoy on 2009-02-03
[LEFT]As a home user, I'm on 100% Hardy-- in a way. I have enabled a few of the 8.10 repositories myself, using pinning to limit which packages will actually be updated (thanks to bhodi.razen for showing me a HOWTO for that technique!) I also use the getdeb repositories, which can actually be *more* up-to-date than the official repos. I update the FGLRX drivers myself. Finally, there are a number of apps I periodically update from SVN or GIT (such as Alien Arena and Compiz.) 

Why stick with Hardy? Because I'd already installed it on all three of my computers by the time Intrepid came out, and I didn't feel like anything was "broken" enough to necessitate "fixing." 

I'll be enabling 8.10 packages one by one. Each time there's something "cool" or important in the 8.10 repos, I'll add it. Eventually, I'll  be running 100% 8.10 with 8.04 branding.
[/LEFT]

---

### Post by baggins on 2009-02-03
> **Keyper7 said:**
> Dude, what the hell?

In the link **you** posted, there is a message from almost one month ago:



Did you do that? I'm looking at the bug list and it seems you didn't.


Sorry but I actually did do just that, on January 9 [Here it is]("https://bugs.launchpad.net/hardy-backports/+bug/315506") :D
Think I followed the instructions to the letter if I missed a step please do tell. I actually wondered if I should do something to attach it to the puppet package, but in the end I figured that if I just followed the guide all would be taken care of.

> **Keyper7 said:**
> 
Sorry if I sound rude, but how about learning how the packaging, SRU and backporting process works before accusing someone of not being serious?
I did try that, maybee I just didn't understand everything, but from the [SRU page when section]("https://wiki.ubuntu.com/StableReleaseUpdates#When") 
> Bugs which represent severe regressions from the previous release of Ubuntu. This includes packages which are totally unusable, like being uninstallable or crashing on startup.
Puppet crashes on startup so I guess it fits this criteria.

And I do know that the bug must be marked "fix released" before an update can be released against a stable or LTS release, marking a bug "fix released" is not necessarily the same as closing it.

I also know that there is further instructions, but as I read them they involve making a package, and lets face it 99% of all ubuntu users cant do that without some serious help. Recently I posted a question against the puppet package at launchpad asking for help. No one has answered yet, but it's not been that long so I haven't given up hope :)

And as to accusing someone of not being serious, English is not my native language. So some times I miss the finer points when either reading or writing. If some one has taken offence rest assured that none were intended, sorry.

Let me try to clarify:
By telling me that the bug is closed because a fix is out for a dist that won't be officially released for another 5 months.
I feel that I am being told that if I want too use this package I must use Jaunty. It may not be the intent but both I and my colleagues certainly perceived it that way.
Had the answer been along the lines of - "Sorry we have to test in jaunty we will get back to you, if you want to help do this ....", my reaction would have been along the lines of "Ok bummer for me, but perfectly valid! Lets see what I can do for you"

So what got me going was *not* that no one would be fixing my specific problem right here and now. It was the "jaunty only -> closed -> forgotten" thing, that I don't like. 
It's not a good signal to send to me as a regular LTS user that a bug is closed, while a problem as criticalas as the program crashing on boot still exists.

Maybe it's the bad old dapper memories that still haunts me. But once we get one or two stable releases down the road. I am very afraid that when a bug closes it stays closed, or that if a fix is released for stable releases it won't make it back to the LTS release. And one or two releases that's about now for Hardy.

So when I said "some package maintainers is not taking the LTS concept serious", what I was trying to say is that it seems that LTS is not treated as something that is special/different/given priority (Those does't really cover what I was trying to say either, but they will have to do. I really, really need to get a good dictionary :) )

For a non-LTS release if a fix gets released for the development release, but never makes it into the stable release. Worst case 6 months later the development release goes stable, almost everyone upgrades and thus gets the fix :)
For those of us stuck with LTS, for what ever reason, that worst case has a 24 months turnaround! 

Does that mean that LTS should get special treatment? Obviously I think so :)
But is that reasonable for me to expect?

-- Jon

---

### Post by MaxIBoy on 2009-02-03
I think you've got a very valid point.

---

### Post by yabbadabbadont on 2009-02-03
Well, according to the official wiki, they only agree to provide security updates, not bug fixes.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Edit: Never mind.  It would appear that the two different parts of the wiki say different things about the subject...

---

### Post by Keyper7 on 2009-02-04
> Sorry but I actually did do just that, on January 9 [Here it is]("https://bugs.launchpad.net/hardy-backports/+bug/315506")

I'm really sorry about that. I guess searching for the keyword "puppet" didn't work quite as I expected.

> Puppet crashes on startup so I guess it fits this criteria.

It does. But since the fix came in a new upstream release, if I understood correctly, it fits more on a backport.

> And I do know that the bug must be marked "fix released" before an update can be released against a stable or LTS release, marking a bug "fix released" is not necessarily the same as closing it.

Well, so what's the problem? The bug is **not** closed for Hardy. So be patient.

> I also know that there is further instructions, but as I read them they involve making a package, and lets face it 99% of all ubuntu users cant do that without some serious help. Recently I posted a question against the puppet package at launchpad asking for help. No one has answered yet, but it's not been that long so I haven't given up hope :)

No one is forcing an user to help, either. The developers just ask them to either be patient or help. What doesn't work is not being patient and not helping.

And does the puppet package have something special that guides like [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide) don't cover? Not arguing, just asking.

> By telling me that the bug is closed because a fix is out for a dist that won't be officially released for another 5 months.
I feel that I am being told that if I want too use this package I must use Jaunty. It may not be the intent but both I and my colleagues certainly perceived it that way.
Had the answer been along the lines of - "Sorry we have to test in jaunty we will get back to you, if you want to help do this ....", my reaction would have been along the lines of "Ok bummer for me, but perfectly valid! Lets see what I can do for you"
So what got me going was *not* that no one would be fixing my specific problem right here and now. It was the "jaunty only -> closed -> forgotten" thing, that I don't like. 
It's not a good signal to send to me as a regular LTS user that a bug is closed, while a problem as criticalas as the program crashing on boot still exists.


Isn't the last message almost exactly that? They said the fix was released for Jaunty and gave a link for you to make a request for backporting it to Jaunty. What more do you want? **They are clearly working on it!**

> So when I said "some package maintainers is not taking the LTS concept serious", what I was trying to say is that it seems that LTS is not treated as something that is special/different/given priority

It's not supposed to. LTS releases have as much priority as any other stable release. The difference is the longer period they receive updates.

> For a non-LTS release if a fix gets released for the development release, but never makes it into the stable release.

Wrong. It can be a SRU, regardless of being LTS or not.

> Does that mean that LTS should get special treatment? Obviously I think so :)
But is that reasonable for me to expect?

Unless you are lobbying for *changing the definition* of LTS, it's not very reasonable. The special treatment of LTS is the longer support period and that's it.

Bottom line: do not confuse "fix is taking long" with "bug is being ignored". Developers are not infinite. Their time is not infinite. They are not superhumans. If you can't wait, you can always go to the official puppet site and install the latest version on /usr/local.

---

