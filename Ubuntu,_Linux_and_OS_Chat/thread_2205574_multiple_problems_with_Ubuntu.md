---
title: "multiple problems with Ubuntu"
date: 2014-02-14
forum: Ubuntu, Linux and OS Chat
---

### Post by beansdad on 2014-02-14
Been using Ubuntu since 2005 and found it to be very good with great improvements in user friendliness up to 2010. Since then it seems to be getting more & more difficult to use with a lot of problems being encountered.

Examples are the inability of 2011 onwards versions to easiy recognise my HP all in one scanner; updates repeatedly over-riding my settings; updates repeatedly causing crashes; Firefox insisting on starting with the last page accessed despite setting its preferences to always open on my home page; sound not automatically switching off the speakers when earphones are plugged in (reboot is necessary).

I've tried various versions of Ubuntu itself and Linx Mint and keep getting these annoying problems and am wondering if there may be some malicious activity involved to drive users away from Ubuntu!

Can anyone explain what is going on or recommend a user friendly alternative?

---

### Post by wildmanne39 on 2014-02-14
*Thread moved to **Ubuntu, Linux and OS Chat**.*

If you decide you want help fixing these issues please start a thread with one issue per topic, with an descriptive title.
Thanks

---

### Post by bc.haynes on 2014-02-14
Hello,** beansdad**, 
I believe Ubuntu is moving as fast as it can to alleviate these "problems." The hardware changes  and the software (Ubuntu) has to change. This doesn't happen overnight, but is a process that takes months and thousands of programmers. Your issues may be solved in the next kernel. In the mean time, post your problems here, and people will be happy to help you solve them. As **Wild Man** said, Post one problem at a time and give specifics. I, for one, have come to Ubuntu for good. Windows just doesn't have adequate security, and I won't go back to it. Good luck with your problems and your posts.

---

### Post by beansdad on 2014-02-14
Thanks for responses.

I have found the forums to be absolutely brilliant helping with specific problems for the most part, but there are some that have been rolling on for a long time.

My post was not to try to deal with the individual problems one at a time because there are too many and I don't really have the time. It was to comment on the apparent change in usefulness or increase in problems of Ubuntu since 10.04, both of which sem to be commented on in a number of posts, and I was wondering why this was happening and if there was a viable alternative.

---

### Post by wildmanne39 on 2014-02-14
Hi, I have been using 12.04 since it came out and the only issue I had was getting the nividia driver working which only took a short time but I use the classic desktop and stay away from unity.

It sounds like you may have done an upgrade instead of a fresh install and that will cause all kinds of problems because there is just so many differences between 10.04 and 12.04.

Without knowing the specifics of your system that is all I can say about what is most likely happening.

Also xubuntu is a good one to try if you do not want unity.

---

### Post by beansdad on 2014-02-14
Hi, tried 10.10, 11.10, 12.04, Linux Mint all fresh installs (don't like upgrades as they tend to fail!) on both my desktop and laptop and with unity, classic and cinnamon. With a v slow internet connection, as we're quite a way from the exchange, have tried downloads and various free CDs/DVDs from magazines for installs. Get a few less problems with the laptop. Tried Fedora but that seems to have similar problems.

Moved away from commercial system due to constant blue screens, long upadtes & v slow systems but seem to be getting back to this with Ubuntu. Really don't want to move away but need to spend a lot more time using the computer and less maintaining/problem solving. At the moment the balance is not acceptable.

Am tempted to go back to 10.04 and stay there until I feel confidant in any new version.

Will look again at Xubuntu & see what happens.

Thanks again, much appreciated.

---

### Post by cariboo on 2014-02-14
It looks like some of your problems may be due to inattention on your part, when doing updates, always check what is going to be installed/removed before clicking continue. I'm personally running Trusty on my main system for daily use, I update a minimum of twice a day, and aside from one problem that really had nothing to do with the OS, things have been running so smoothly that it's almost boring. Also keep in mind that Ubuntu has nothing to do with HP drivers, and there may be an older version of Hplip in the repositories, so I'd suggest downloading and installing them directly from the manufacturer.

I'd suggest that you stay away from 10.04 desktop, unless you don't plan on connecting to the internet. It has come to the end of it's life cycle, and security updates are no longer available

---

### Post by beansdad on 2014-02-15
Interesting response. Alas, several of my attempts have had multiple problems from a clean install without updates for different versions of Ubuntu and from different sources. Yes, many times the problems have started after updates but I can't see how being selective with updates causes things like Firefox refusing to accept starting from my homepage instead of the last page accessed and similar configuration settings being ignored by the system.

I would be interested to know how I would know which updates I need to be selective about so I could be less "inattentive"? Aren't the updates supposed to be only for the programs I have installed and are to improve these?

---

### Post by cariboo on 2014-02-16
The one thing to stay away from is partial updates, as at time there will be updates that come through that are still waiting for dependencies to be built. The best way to check updates, is to read the change logs. I don't use the Software Centre, so I'm not sure if you can check change logs, but both synaptic, or apt get allow you to download them before actually setting the upgrade process in motion. Another suggestion, that is only my personal opinion, but never use Update Manager to do updates.

---

### Post by beansdad on 2014-02-17
New, clean install of 12.10 from different source & with no updates installed has now started with the "system problem detected" messages for assorted programs, so I've wasted enough time with Ubuntu. Will try using Mint for a while & see what happens but not holding my breath.

While I greatly appreciate the work done by the developers, if it continually fails it's of no use to me. I can't afford the time to try to resolve individual problems, some of which have been around for years, only to find that another system update has reset things and I have to it all over again!

---

### Post by buzzingrobot on 2014-02-18
> **beansdad said:**
> New, clean install of 12.10 from different source & with no updates installed has now started with the "system problem detected" messages for assorted programs, so I've wasted enough time with Ubuntu. Will try using Mint for a while & see what happens but not holding my breath.


Ubuntu defaults to enabling the Apport tool, which generates those "system problem detected" errors.  Other distributions use similar tools. In my experience, in almost all cases I would not have known an "error" had occurred if that popup had not been generated.  I.e., nothing unusual happened. 

Here's the point:  Some distributions do not use Apport or similar tools. But, the absence of error popups does not mean an absence of errors. 

If a distro does not report the errors, it creates an illusion that they are not happening. 

Meanwhile, 12.10 is an old release.  Best to move on.

---

### Post by CitadelUniversal on 2014-02-18
To disable the apport crash reports you must do the following in the gnome-terminal  -  sudo -i "s/enabled=1/enabled=0/g" '/etc/default/apport'  - this disables the crash errors, I've used it countless times on Ubuntu though now I use Kubuntu......

---

### Post by Erik1984 on 2014-02-18
> **buzzingrobot said:**
> Ubuntu defaults to enabling the Apport tool, which generates those "system problem detected" errors.  Other distributions use similar tools. In my experience, in almost all cases I would not have known an "error" had occurred if that popup had not been generated.  I.e., nothing unusual happened. 

Here's the point:  Some distributions do not use Apport or similar tools. But, the absence of error popups does not mean an absence of errors. 

If a distro does not report the errors, it creates an illusion that they are not happening. 

Meanwhile, 12.10 is an old release.  Best to move on.

Good point. The error popus do cause a lot of confusion, people think their Ubuntu installs are broken etc. Maybe it would be better if an error is silently reported to Canonical, only the first time it occurs. Although that will stir up the whole "Canonical is violating our privacy" debate again.

---

### Post by SeijiSensei on 2014-02-18
I think apport should only be installed upon request.  Add another check box to the installer along with the one for restricted-extras.  Ordinary users should never see a dialog box like that.  The system should be able to determine if the error is serious enough to warrant reporting upstream.  As buzzingrobot suggests, most of the time when apport reports a problem I see no effect on the system's performance.

Perhaps apport should be the default on development releases, but it should not be active on LTS releases like 12.04 or the upcoming 14.04.

---

### Post by buzzingrobot on 2014-02-18
> **SeijiSensei said:**
> I think apport should only be installed upon request...

I use Apport on developmental releases so the feedback is generated. I don't use it after a release because I don't believe I've ever encountered an unreported bug. 

It could stand to be more seamless.  I.e., just automatically send in the bug report without requiring any attention by the user. On first use, explain what's going on and offer a chance to opt out or opt in to future use.  (Fedora 20 has something that is worth a look.)

If someone sees privacy concerns in this, I guess it just has to be accepted.  But, don't tell them about referrers. ;)

---

### Post by beansdad on 2014-02-18
Very good, but does not resolve the multiple problems that I am getting. Yes, Apport reports errors followed by the error becoming clearly apparent by the reported program not working. I do not seem to get programs not working with other distros. So presumably the programs do not have the errors in those distros. Continuous errors stopping programs working doesn't make for a useful system.

I still don't see any reason to continue with a system that refuses to work for me & insists that I work for it i.e. non stop error correction.

---

### Post by QIII on 2014-02-18
I see no reason for that, either.  You are certainly having a very unusually difficult time with Ubuntu.  Who can account for gremlins?

Don't waste your time on something that's more trouble than it's worth for you.  You have other choices and it's nobody else's business if you decide to exercise choice.  I'm no Ubuntu evangelist, so I'm not going to try to sell you a bill of goods.

Find something that works for you.  It's silly to do otherwise.

---

### Post by buzzingrobot on 2014-02-19
> **beansdad said:**
> ...does not resolve the multiple problems...

No help resolving your "multiple problems" can be attempted without knowing the specifics of those problems. 

Ubuntu  users are not, en masse, complaining about "continuous" errors.  The  issues you are reporting, then, must be triggered by something specific  to your system.

Generically speaking, since we know no specifics,  the usual approach is to remove all unsupported software such as PPA's,  undo any specific alterations you have made, return the installation as  close as possible to the base post-install setup, check logs for error  information, let Apport display what it thinks is wrong rather than  ignoring it, and go from there. Be sure all your hardware is supported. If you have installed a proprietary video driver, consider disabling it temporarily.

---

### Post by neel3 on 2014-02-22
I knew something was wrong with the default Ubuntu UI...
[http://www.theregister.co.uk/Print/2013/06/03/thank_microsoft_for_linux_desktop_fail/](http://www.theregister.co.uk/Print/2013/06/03/thank_microsoft_for_linux_desktop_fail/)

(I was trying to find the best menu UI overlay for Ubuntu, when I found this)

---

### Post by buzzingrobot on 2014-02-22
> **neel3 said:**
> I knew something was wrong with the default Ubuntu UI...
[http://www.theregister.co.uk/Print/2013/06/03/thank_microsoft_for_linux_desktop_fail/](http://www.theregister.co.uk/Print/2013/06/03/thank_microsoft_for_linux_desktop_fail/)

(I was trying to find the best menu UI overlay for Ubuntu, when I found this)

Thoroughly debunked at the time.

---

### Post by beansdad on 2014-02-27
Buzzingrobot

As I've stated above, I'm not trying to deal with the individual problems because there are too many. It's not my system as I'm getting problems with both desktop and laptop and have used assorted installs from assorted sources. Can't find a common denominator other than Ubuntu.

The object of the post was to try to find out why a previously excellent operating system has, since 10.04, started giving all these problems and to, perhaps, influence the developers to stop what appears to be a mad rush forward without sufficient tetsing & proving of the new systems.

I really don't want to leave Ubuntu and lose the excellent support for individual problems from the forums but, as I've said, I need to use the system not spend hours trying to resolve individual problems.

---

### Post by buzzingrobot on 2014-02-27
> **beansdad said:**
> 
The object of the post was to try to find out why a previously excellent operating system has, since 10.04, started giving all these problems and to, perhaps, influence the developers to stop what appears to be a mad rush forward without sufficient tetsing & proving of the new systems.


You have described problems I haven't had with Ubuntu, or any other Linux distribution, on a variety of hardware.

If your printer/scanner requires a proprietary driver from HP -- and many do -- it will not work in in Ubuntu and any other Linux I am aware of until you install that driver. Perhaps 3 or 4 years ago Ubuntu packaged that driver. But, Ubuntu packages no proprietary HP drivers now.

I can only suggest you look for solutions that are specific to your hardware and your environment, because i suspect that's the problem. (I'd also suggest increasing RAM, because 1G is very marginal these days. I have Firefox, Thunderbird and an RSS reader open on 13.10 and current RAM use is 1.2 gigs.

To reiterate something said earlier, developers do not frequent this site. It's pretty much SOP that developers do not frequent any *user* forums.

If you would open separate threads with specifics about each of your problems, people here are likely to address them. Absent that, there's little useful to be done.

---

### Post by beansdad on 2014-03-09
Yes, it does appear that I've been unfortueate enough to have these problems with multiple versions of Ubuntu from multiple sources and on both my desktop and my laptop. Tried installing drivers from HP 7 whereas Fedora and other distros recognise my scanner on my HP multifunction device Ubuntu does not. Nor does Ubuntu switch audio output from speaker to earphones when these are plugged in. Etc, etc, etc.

If I had nothing else to do I would work through each and every problem one at a time but I have to earn a living in the meantime. As I've stated above, I do not see how it can be my hardware as I have similar problems on desktop and laptop both running with 2GB memory (I believe can't update my profile until I have enough beans).

Reading through lots of other threads on the forums I get the impression that I'm not alone in having some of these problems and some don't seem to be curable.

Wish I knew what the problem was which is why I started this thread. Alas, it seems to come back to solving each and every individual problem until the next update/new distro resets everything back and then go through the whole process again.

Going to mark this as "Solved" now as there is no resolution to the multiple problems situation other than to find a different version of Linux that does work. Mint isn't so bad, Fedora seems more stable but slower, waiting for SolydXK disk to arrive to try that.

Thanks all for reading this.

---

