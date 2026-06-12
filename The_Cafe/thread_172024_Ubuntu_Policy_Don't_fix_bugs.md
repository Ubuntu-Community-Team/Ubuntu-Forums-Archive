---
title: "Ubuntu Policy: Don't fix bugs"
date: 2006-05-07
forum: The Cafe
---

### Post by towsonu2003 on 2006-05-07
No, I don't mean "resolving bug reports" or similar. According to the update policy of Ubuntu, releases do NOT[1] get bug fix updates. So anything you get thru apt-get upgrade is only security fixes. Known, fixed bugs will not make their way into your computer, unless you look for them in launchpad. 

One bug fix I had experience with was about keyboard layouts not being kept after reboot. An up-to-date .deb package was ready, and all you need to do was to install it. It was not an additional package, but an update to an existing package. 

Nowadays, as I'm testing Dapper a few times a week, I keep finding and reporting bugs, which are not important enough to be fixed by package maintainers. Instead, they wait for upstream (the original coder of the package) to fix the issue. 

This basically tells that Ubuntu maintainers are either not interested in, or not able to fix bugs in source code of other applications. But that's not my point. 

The point here is that once Dapper gets released, it will not get ANY bug fixes during its suport cycle (for 5 years on the server side, and 3 years on the desktop side). Hoary and Breezy will never get bug fixes. (So, if you have bugs that really annoy you in a release, don't wait for apt-get/synaptic to fix it for you.)

Here is my question: should this policy change? 

[1] [http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291) says: 
> 
Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months. For example, if Hoary ships with Firefox 1.0.1, Hoary will remain at Firefox 1.0.1 for the entire 6-month release cycle, even if 1.0.2, 1.0.3, or 1.0.4 gets released during this time. The Ubuntu team may apply important security fixes to 1.0.1, but any new features or non-security bugfixes won't be made available to Hoary.

---

### Post by drizek on 2006-05-07
I think doing so would take time away from the dev team as they are working on packages for the next release. 

Bug fixing updates should be available, but they shouldnt be a priority. At this stage, ubuntu is pretty young and i think it is more important to focus on moving it forwards than to keep supporting the older versions.

---

### Post by endersshadow on 2006-05-07
If you need bugfixes, it's easy enough to install them without using the Ubuntu repos.

Moreover, the backports project is doing exactly this.  If this issue is important to you, please contribute to the backports project, as those repos are not maintained by Ubuntu devs, but rather the Ubuntu community does this to update software intermittently.

---

### Post by BoyOfDestiny on 2006-05-07
If there is a bug fix in an application, I'm assuming they have released a new version. Unless that was the only update, it's likely other changes could introduce new bugs. There is a reason they want to keep it "stable".

In terms of security updates, these are necessary so systems are not exploited. Valuable for most any user.

Now, if a specific app has a bug, why on earth would an Ubuntu dev be the one to fix it? Maybe they'd supply a patch, it should be the devs upstream that decide whether or not to apply it. If the bug is due to a maintainer packaging the software improperly (as with the issue I had with libbinio [missing package info or something], installing from source was my resolution to it), they should be responsible for fixing it.

If they just go applying changes instead of taking it upstream, then we would get varying ubuntu versions, duplication of work, possible other problems. I'm not saying they shouldn't submit code to fix it, I'm saying I don't want weird custom versions of various apps.

If you want a newer version of a package, build it or install it. It's as simple as that, use checkinstall and it will be a seamless upgrade too. Done that for scummvm, dosbox, and pan betas (since all of these are out of date in Dapper as is.)

---

### Post by towsonu2003 on 2006-05-07
[QUOTE=endersshadow]If you need bugfixes, it's easy enough to install them without using the Ubuntu repos.
[/quote]
Ease of use is irrelevant. But ease of finding the fix is. If bug fixes are sent thru the repos, users of one release will not have to hunt fixes for their bugged packages in launchpad. 
[QUOTE=endersshadow]
Moreover, the backports project is doing exactly this.  If this issue is important to you, please contribute to the backports project, as those repos are not maintained by Ubuntu devs, but rather the Ubuntu community does this to update software intermittently.[/QUOTE]
Backports is mainly oriented towards new features in packages, not fixing bugs in them or patching ubuntu devel-supported packages for bugs. They take newly released software, package it in a way that will not break ubuntu, and send it to backports. 
[QUOTE=BoyOfDestiny]If there is a bug fix in an application, I'm assuming they have released a new version. Unless that was the only update, it's likely other changes could introduce new bugs. There is a reason they want to keep it "stable".
[/quote]
We get "security only" updates (patches) that do not affect (theoretically) stability. Are you saying that bug-fixed package will decrease stability but a security-patched package will not? 
[QUOTE=BoyOfDestiny]
In terms of security updates, these are necessary so systems are not exploited. Valuable for most any user.
[/quote]
To my observations in the forums, stability is equally important for users as is security. 
[QUOTE=BoyOfDestiny]
Now, if a specific app has a bug, why on earth would an Ubuntu dev be the one to fix it?[/quote]
Because they have the source code, the bug report in launchpad, and the ability and the knowledge to fix it. 
[QUOTE=BoyOfDestiny]
Maybe they'd supply a patch, it should be the devs upstream that decide whether or not to apply it.
[/quote]
I agree. And what happens when an Ubuntu devel submit a code fix to the upstream and the upstream accepts it? We will not see that fix (patch) until the new Ubuntu release. 
[QUOTE=BoyOfDestiny]If the bug is due to a maintainer packaging the software improperly (as with the issue I had with libbinio [missing package info or something], installing from source was my resolution to it), they should be responsible for fixing it.
[/quote]
I don't believe distro developers are only responsible to fix their packaging of software. They are also responsible for maintaining and fixing that package as well. Why? Because the devel of that software was good enough to release it under the GPL and make it available for free for the distro devel. Wasn't the reason behind open source "anyone who wants can fix any bugs they observe"? 
[QUOTE=BoyOfDestiny]
If they just go applying changes instead of taking it upstream, then we would get varying ubuntu versions, duplication of work, possible other problems. I'm not saying they shouldn't submit code to fix it, I'm saying I don't want weird custom versions of various apps.[/quote]
this probably is just a misunderstanding. If a devel spots a bug (or spots a bug report in launchpad), s/he will let the devels of that package know of this bug. Hopefully, s/he will also contribute to the fixing of that bug. 
Once the fix is accepted by the upstream, there is no reason why that fix can be sent to us (users of the distro) as an update to the package. 

I'm not talking here about packaging the beta release of gaim or anything. What I am saying is this: imagine that:
1. you spotted a bug that crashes gaim
2. you report the bug on launchpad
3. with your input, ubuntu devel finds where that bug is, and hopefully fix it (at this point, we will not be getting any updates)
4. ubuntu devel let's upstream know of the bug and proposes the fix
5. ideally, upstream accepts the fix and incorporates it to their new release
6. ubuntu devel takes the fix (patch), applies it to the current ubuntu-release package, uploads the package to repos
7. we receive the patched package, which fixes the annoying bug you found some time ago. 

Alternatively:
1. ubuntu devel spots a bug fix in the upstream that s/he would like to incorporate in ubuntu's package
2. ubuntu devel applies patch, sends package to repo
3. we get the update thru repos. 
[QUOTE=BoyOfDestiny]
If you want a newer version of a package, build it or install it. It's as simple as that, use checkinstall and it will be a seamless upgrade too.[/QUOTE]
Again, I'm not talking about new versions. I'm also not happy to be treated like a noob (though I still am new to linux) who rants because he ants a new version of a package. To make it as clear to you as possible, here is a version numbering scheme for gaim. First one is our imagined gaim version that crashes, second is the gaim to which ubuntu devel applied the fix:
```

gaim 1:1.5.0-1ubuntu3
gaim 1:1.5.0-1ubuntu4

```
Notice that the version did not change, and we did not get any new features (and hence, no new bugs introduced by new features). 

Gaim is an example because I keep seeing posts requesting the beta version to be released. I myself cannot use gaim almost at all, because almost all the ports except 80 and 443 are blocked by my isp. 

Also, we shouldn't downplay the importance of distro developers for the open source community. They have the means and the ability to fix bugs, and they should fix bugs and send them upstream when they can. Although I can find the link to prove, the current kernel 2.6 series depend on distro developers to fix and patch the kernel for bug fixes. That is why kernel doesn't have the 2.7 development branch. Linus assumes now that distro devels will fix the kernel and send those fixes to 2.6 branch for approval. 

See slashdot for a recent news about that (kernel getting buggier, because neither the distro developers, nor the kernel developers are interested in patching old bugs in the new kernel).

I'm hoping my point is now understood.

[quote=drizek]
Bug fixing updates should be available, but they shouldnt be a priority. [/quote]
I agree. I don't see any disadvantages for them to send us the bug fixes when they are able to fix the bugs.

---

### Post by Kvark on 2006-05-08
I think the devs should fix bugs in the development release and send the patches to backports if they think older releases have the same bug. Backports should make the bug fixes from the development release available in stable releases when possible.

---

### Post by ubuntu_demon on 2006-05-08
I voted no because :

-there's backports (I hope all problems are over and backports will be released more often than was the case for breezy)
-fixing all minor bugs takes a lot of time and that time should be invested into the new release
-if there are major bugs they will fix them. See this part of the Dapper sources.list :

> 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted


---

### Post by Dr. C on 2006-05-08
I voted no. Keep the policy as it is. 

I can see this becoming a lot of extra work and there are many alternatives for users to fix minor bugs as has already being mentioned here.

---

### Post by Stormy Eyes on 2006-05-08
There are already provisions for providing fixes for major bugs to users of existing releases. What's the big deal? Chances are that most of the power users will switch to Edgy after a week in Dapper anyway. :)

---

### Post by towsonu2003 on 2006-05-08
[QUOTE=Stormy Eyes]There are already provisions for providing fixes for major bugs to users of existing releases.[/QUOTE]
I'm not sure. Here's an example: [https://launchpad.net/distros/ubuntu/+bug/24506](https://launchpad.net/distros/ubuntu/+bug/24506)

Bug in question is regarding localization (Turkish keyboard layout). Bug is fixed with a small updated .deb package for Breezy, but the updated package never went to the repos. Any Turkish keyboard layout user would have problems with this if s/he never browsed launchpad to find this particular package. 

:)

---

### Post by Stormy Eyes on 2006-05-08
[QUOTE=towsonu2003]Bug in question is regarding localization (Turkish keyboard layout). Bug is fixed with a small updated .deb package for Breezy, but the updated package never went to the repos. Any Turkish keyboard layout user would have problems with this if s/he never browsed launchpad to find this particular package. [/QUOTE]

OK, I agree that bugfixes like the one you mentioned should be in a repository. Perhaps somebody might be willing to gather debs from launchpad into a minorbugs repository for users that want it.

---

### Post by fuoco on 2006-11-06
I can understand everyone's points, but still there are yet bugs who can easily be considered major, and receive no attention. For example there's a bug that the module for activating the fan on my laptop is not autoloaded. It's well known for a long time, still wasn't fixed during dapper and not even for edgy. Even if there's an easy workaround, many people might not even know that there could be something wrong before the CPU is fried.
Another bug is 3D not working in ubuntu while it does in all other distros out of the box with open source drivers. Now this bug was introduced in Edgy - so you're telling me I have to wait 6 more months to Feisty to have it working again? and if by any chance someone misses the deadline it's gone for another 6 months? 

By the way I never found any deb or something like that to fix any of the major bugs I had with ubuntu...

---

### Post by Hobbsee on 2006-11-07
All i have to say to this:

"Remember the Xorg breakage on dapper a few months ago, where X broke due to a couple of upstream patches."

---

### Post by Lil_Eagle on 2007-01-22
Yes, I remember that xorg bug vividly.  

The problem is that bug fixes can sometimes create new bugs.  While it may be desirable to have the bugs in packages fixed, the core of the work by the Ubuntu staff should be to create the best distribution that can be created at the time of the release day, then move on to the next release.

While waiting six months for a more recent version is the official policy, users who are interested enough to look for solutions can usually find updated packages (read: hacks and patches) that can be applied.

HOWEVER, when one of the bugs is major, and the fix is known (or already done by the upstream), they should be applied and placed in the backports.  My case in point:

[http://www.ubuntuforums.org/showthread.php?t=204582]("http://www.ubuntuforums.org/showthread.php?t=204582")

Perhaps the screensaver not working isn't such a big deal to some people, but it is to me.

Who determines when a bug is major?

I can say, I learn the most about Linux by trying to fix things that shouldn't be broken in the first place.  The idea that "It just works" is fiction in all operating systems that I have tried.

But then again, if everything worked properly, what need would there be for upgrades?  One of the best taglines:  If it ain't broke, tweak it.

---

### Post by Hobbsee on 2007-01-22
Now that example is a bad one, and was a major mess.

Only Riddell has access to the website and it's repositories - whereas more people have access to the ubuntu repositories.

---

### Post by Lil_Eagle on 2007-01-23
Hobbsee: 

I agree.  I actually regret posting that howto, and thankfully it is now irrelevant.

I find that having only one person responsible for the repositories is by far too few for such a good (and popular) version of Linux.  My hat goes off to Mr. Riddell.

I actually voted No to this poll because as I stated, the developers should move on after release.  Critical bugs are a different story than updates, and to me the screensaver issue was a critical bug.  I mistakenly thought that other people might benefit from my (and _mike's) kludge.  Keep in mind that my post was a month after Mr. Riddell posted KDE 3.5.3 on [www.kubuntu.org]("http://www.kubuntu.org")

I have resolved to apply such arcane patches to my system because it is my system.  That's the reason I switched to Linux in the first place.  Because KDE is open source, I can pluck code from their website and apply it to my installation.  I would not recommend this type of action for everyone, but some people have the same attitude as I do, and do not have any programming experience to rely on.

I'm still learning, and you can be sure I learned from that episode.

---

### Post by demonhunter on 2007-01-29
I think that we should be able to choose if we want to install bug fixes or not. Synaptic could have a tab to list bug fixes.

:guitar:

---

### Post by Hobbsee on 2007-01-31
try apt-get or aptitude for that, if you wish to cherry pick.

---

### Post by Polygon on 2007-01-31
the policy is fine. It makes it so the system is more stable as a whole, as all the programs will only get security fixes , instead of feature fixes that might break the program or other programs that depend on it, etc

---

### Post by FuturePilot on 2007-05-16
I know this thread is old, but if bug fixes aren't sent to use through updates, then why does the Update Manager tell you that they do? This seems misleading:confused:

---

### Post by moe_syzlak on 2007-12-09
> **drizek said:**
> I think doing so would take time away from the dev team as they are working on packages for the next release. 

Bug fixing updates should be available, but they shouldnt be a priority. At this stage, ubuntu is pretty young and i think it is more important to focus on moving it forwards than to keep supporting the older versions.

So you're saying that system stability and user productivity in Ubuntu is unimportant?

---

### Post by Kernel Sanders on 2007-12-09
Pretty pointless to respond to a post someone made in MAY =/

---

### Post by moe_syzlak on 2007-12-09
> ***John* said:**
> Pretty pointless to respond to a post someone made in MAY =/

Well if they subscribed to this thread or allow new post notifications by email, then they should get this post.

---

### Post by mdsmedia on 2007-12-09
> **moe_syzlak said:**
> Well if they subscribed to this thread or allow new post notifications by email, then they should get this post.And if they don't, they won't, which makes it, in all probability, a pointless act.

I've probably subscribed to 3 threads in the 2 and a bit years I've been a member, and they were threads I had a vested interest in knowing about.

---

### Post by samwyse on 2007-12-09
I've experienced some regressions when updating to newer versions:

Dapper had a broken xmms (crashed if double size was used, could be fixed by adding an environmental variable)
Feisty had a broken Vice (black screen if acceleration was used, needed a newer version to be usable)
Gutsy's Pan broken (images shown partly, needed a bug fixed newer package). Also Kopete (crashed if MSN was used?), needed to download a fixed kdelibs package.

I think obvious regressions should be fixable through the updater.

---

### Post by p_quarles on 2007-12-09
It's already been stated earlier in this thread (and over a year ago): major bugs are fixed in updates. Minor bugs are usually not.

How do we decide which bugs are major and which are minor? Go over to Launchpad and participate in the process yourself.

---

