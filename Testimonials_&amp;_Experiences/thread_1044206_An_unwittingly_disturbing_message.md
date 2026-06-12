---
title: "An unwittingly disturbing message"
date: 2009-01-19
forum: Testimonials &amp; Experiences
---

### Post by dawynn on 2009-01-19
I read through this article:
[The Secret Lives of Ubuntu and Debian Users]("http://itmanagement.earthweb.com/osrc/article.php/12068_3796126_1/The-Secret-Lives-of-Ubuntu-and-Debian-Users.htm")

Really, there's nothing harmful intended in the article, but I'm disturbed by one of the figures that comes out here.  Follow me on this.

Late in the article, they indicate the use of video drivers, and indicate that roughly 86% of Ubuntu users use the proprietary nVidia driver.  I would think its safe to assume that roughly 86% have an nVidia card, and want it to work.

I've been thinking of starting a volunteer community effort to recycle computers to give to non-profit groups and disadvantaged students.  But figures like this disturb me.  Why? Because of Intrepid.  Because of Jaunty.

Intrepid introduced large changes to Xorg -- changes that broke compatability with the nVidia drivers.  Now, as far as I am aware, nVidia finally did fix everything, but I know the legacy drivers were not fixed at the time Intrepid went live.  No, it took a couple extra months.

OK, fine.  Things happen.  Problem was, from what I'm seeing, we haven't learned our lesson.  I need the legacy drivers because of the age of my own computer (no SSE instructions -- which are used in the 173 and 180 series).  And the nVidia legacy driver that works with Xorg (96.43.09) is currently in test mode (according to nVidia).  nVidia's latest "stable" driver (96.43.05) does not work with Intrepid's Xorg.

But in Jaunty, we've again moved in an Xorg that breaks functionality with nVidia.  Surely, there must be *someone* that is testing these things before we throw them into Ubuntu (perhaps the Xorg team?).  And if we find that it doesn't work on an nVidia system yet, surely we could delay changes to Xorg until nVidia has responded to the Linux community.  (Note: last I heard, the 180 series may be working in Jaunty, others are still waiting)

Now this is just one example.  But, I'm personally concerned with trying to release Ubuntu PC's into the wild when upgrades, even to stable releases (again, remember Intrepid) will, knowingly, break machines -- in some cases, 86% of the Ubuntu machines in use.

Have we forgotten the idea of Ubuntu letting your computer "just work"?  

Maybe I'm overreacting, but I'm a computer programmer, and I realize the struggles that *I'm* having with keeping my PC working right under Ubuntu.  I'm willing to put up with some issues.  What about those not so technically savvy who run into these glitches?

I'd be interested in hearing others' stories as to how they may have installed Ubuntu for less technically savvy friends, relatives, and neighbors.  What have you told them about upgrading?  What lessons have you learned in your own efforts to convert others to Ubuntu?

---

### Post by armandh on 2009-01-19
early adopters should know YMMV .... and,
putting a recent release on a mission critical machine is foolish.

the real problem is
someone has to go first .... and, 
there is no profit in fixing what ain't broke yet.

.

---

### Post by stalkingwolf on 2009-01-19
> the real problem is
someone has to go first .... and,
there is no profit in fixing what ain't broke yet.

I have 2 Issues with this.
First, on my desktop.  Some update in the last few days, And yes I actually check to see what the updates are.  But inspite of my best efforts, somthing has SNAFU'ed my top panel. I can no longer see my shut down button or clock.

Second, after an update, ( I was away from home, in a Motel) I can no longer access this site from firefox. ( havent tried other sites yet).  No problem with Opera or my EEE.  And Yes I believe this to be something to do specifically with firefox, although I have done several updates on my desktop and EEE without any untoward results since.

Just for the record I run 8.04.1 on my desktop, dual booted with 8.10, 8.04.1 on my HP 8200 ( actually I have 2 of these. Mine and My wifes).

At this time it appears that this is related to a specific laptop, Even though My wifes laptop and mine are identical as far as I can tell.  I will update this if necessary in a couple hours, her laptop is updating as I post.

---

### Post by uberdonkey5 on 2009-01-19
Main problem with linux is initial set up, which is usually long and sometimes difficult.

I think for new users the best thing is to install all the necessary drivers, codecs etc so they have a fully functional machine, and check it all works. They can then be shown how the menu system works, how to get to the terminal and what its fucntion is, how synpatic works, and where ubuntu forums is, and then everything is up to them.

If there are instability issues or other problems with later releases on a particular computer, I think early versions should be used.

However, I AGREE with what you are saying about compatability. Its a bad road to go down if new releases are incompatable with major pieces of hardware. OK, so you can currently install early versions of ubuntu, but what happens when these are no longer supported?? We still need to make sure the latest versions are 'light', effective, compatable with older computers and compatable with new hardware.

---

### Post by BIGtrouble77 on 2009-01-19
This is why Ubuntu has LTS releases.  Those releases are supposed to be very stable and not incorporate updates that can break the system in the way you describe.  The problem is that Canonical is not  executing their LTS releases well.  They should have never released things like Pulse Audio in the Hardy release which broke audio terribly.

I think every year Canonical should release an LTS along with a normal release so they don't get behind on their release schedule and can keep up with the other distros.  The reality is that people will move to other distros if Ubuntu isn't in the bleeding edge on each release.

I only deploy ubuntu machines to people I can support.  It's much easier to suport than windows, but I do think it should stil be easier.

-bt

---

### Post by jrusso2 on 2009-01-19
> **BIGtrouble77 said:**
> This is why Ubuntu has LTS releases.  Those releases are supposed to be very stable and not incorporate updates that can break the system in the way you describe.  The problem is that Canonical is not  executing their LTS releases well.  They should have never released things like Pulse Audio in the Hardy release which broke audio terribly.

I think every year Canonical should release an LTS along with a normal release so they don't get behind on their release schedule and can keep up with the other distros.  The reality is that people will move to other distros if Ubuntu isn't in the bleeding edge on each release.

I only deploy ubuntu machines to people I can support.  It's much easier to suport than windows, but I do think it should stil be easier.

-bt

The only thing LTS means here is that its supported much longer.

---

### Post by wolfen69 on 2009-01-19
> **jrusso2 said:**
> The only thing LTS means here is that its supported much longer.

longer support also means more things will get fixed. 

support for newer hardware and all updates rolled up isn't exciting? wow. 8.04.2/.3/.4/ will be awesome.

---

### Post by wolfen69 on 2009-01-19
> Maybe I'm overreacting, but I'm a computer programmer, and I realize the struggles that *I'm* having with keeping my PC working right under Ubuntu.how many computers have you tried ubuntu on? works great for me and everyone i know.

> What have you told them about upgrading? i'm not stupid enough (not saying you are) to let them have that option. i turn off the option. upgrades with any OS is dicey at best.
[B]
The Secret Lives of Ubuntu and Debian Users[/B] i didn't need to read this. the title tells all. i don't have a secret life. wysiwyg.

---

### Post by solwic on 2009-01-19
> **wolfen69 said:**
> 
**The Secret Lives of Ubuntu and Debian Users** i didn't need to read this. the title tells all. i don't have a secret life. wysiwyg.

You mean you're not secretly a Microsoft employee subtly employing reverse psychology to redirect a whole subset of the PC market back to buying Windows products?

Damn, I thought I had you all figured out.  

:biggrin:

---

### Post by cardinals_fan on 2009-01-19
> **jrusso2 said:**
> The only thing LTS means here is that its supported much longer.
Yes, but since no new software is included, most bugs are fixed long before the end of a LTS release cycle.

---

### Post by stchman on 2009-01-19
I read the article and I cannot understand what secret life it is trying to convey.

Any rate I run Hardy 3 PCs and 2 laptops and they all run very well.  The laptop and 2 desktops are 64 bit.  All the desktops have nvidia cards (8800GT, 7600GT, 5700 Ultra) and the proprietary drivers run smooth as glass.  The laptop has an Intel X3100.

I have an Acer Aspire One with Intrepid as the wireless has better support with the Intrepid kernel.  The laptop has an Intel 945 graphics card.  I look at the Ubuntu HCL before I purchase.

---

### Post by solwic on 2009-01-19
> **stchman said:**
>   I look at the Ubuntu HCL before I purchase.

If you're talking about the one on the wiki, it's not reliable.  It lists 2D/3D support for my ATI X1300 PCI-E card, but doesn't state that 3D is only available without desktop effects.  It doesn't list the conditions for compatibility.  

Best way to check hardware compatibility is to ask around on the forums; try to find someone who has the hardware and has it working.  Their word would be more reliable than the wiki HCL.

My .02 anyway.  :P

---

### Post by Tamlynmac on 2009-01-19
If Windows had a 6 month or one year release mandate would you purchase the upgrade every time a new release occurred?  Would you confirm compatibility prior to installing? If not, why not?

This concept that one must upgrade on every new release has baffled me for quite some time. Not to mention, why someone wouldn't confirm compatibility prior to installing said upgrade? Complaining about Ubuntu's lack of stability without assuming personal responsibility for upgrading is (IMHO) foolish. Each new release of Ubuntu (since I first installed) has been accompanied by the soothsayers predicting doom and gloom. Yet Ubuntu acceptance has increased. If one migrates to Ubuntu expecting a Windows clone, I truly believe they will be extremely disappointed.

I agree that the LTS releases appear to be much more stable and release issues appear to be resolved quicker. However, that's just my perception.

By turning off the option to upgrade when installing Ubuntu on a new user's system, I doubt you will accomplish isolating that particular system (unless the user lives in a bubble). As immediately upon release of an Ubuntu upgrade, this forum and much of the internet is aware. Especially, Google.

---

### Post by solwic on 2009-01-19
> **Tamlynmac said:**
> If Windows had a 6 month or one year release mandate would you purchase the upgrade every time a new release occurred?  Would you confirm compatibility prior to installing? If not, why not?


I wouldn't, but I think a lot of people do this with Linux looking for hardware compatibility.  For instance, when Jaunty comes out I was going to upgrade immediately.  Why?  It uses the new kernel, which if I understand correctly will have the DRI2 support which should let ATI cards work properly with composite rendering (desktop effects, for instance).  It'll be buggy as hell, no doubt, but I'll sacrifice software stability for full hardware functionality.

Of course, I'm going to be buying an nVidia card before that, so this isn't an issue for me.  But I can see how someone sitting around with an ATI card and an ugly desktop, which also doesn't let them play games with Wine (many games won't work with Wine because of ATI's drivers.  Elder Scrolls: Oblivion is the first that comes to mind, along with Guild Wars) would want to upgrade to Jaunty right away, praying their video will finally, after all the long years since Ubuntu was released, work with 100% functionality.  

Like I said, it'd make me upgrade.  

Anyway....  :)

---

### Post by jrusso2 on 2009-01-19
> **wolfen69 said:**
> longer support also means more things will get fixed. 

support for newer hardware and all updates rolled up isn't exciting? wow. 8.04.2/.3/.4/ will be awesome.

The updates on any Ubuntu release are security fixes.  Once the software is locked in and finalized there are no new versions just cause its fixed or better.

---

### Post by 3rdalbum on 2009-01-20
What you might not know is that Ubuntu were aware of the legacy driver not being compatible with Intrepid, and wrote a special script into the Update Manager that recognised the presence of a legacy card and automatically switched the new install to the 2D driver. No breakage. There are no problems when you're talking about donating machines to the needy, as the needy don't need 3D acceleration. In fact, many Ubuntu users don't need acceleration but they use it because it's available.

Xorg is responsible for implementing new features, fixing bugs, and supporting open-source drivers. Xorg even supports and guarantees the operation of the 'nv' driver, which is technically open-source but actually heavily obfuscated by Nvidia's engineers to try and prevent the release of their IP.

The best solution is for Nvidia to open-source their driver or release the specifications and documentation for their cards under an open license (with no NDA needed). If Nvidia's driver was open-source, then Xorg developers would automatically patch the driver to be compatible with new Xorg versions. If Xorg's ABI changes, the driver would also be changed along with it.

If Nvidia released the specifications for their cards and chips, then Xorg themselves would develop a driver (in association with lots of companies that support open-source). Hey, ATI have released specifications for some of their cards already, and there is an open-source 3D driver available for certain ATI cards, that gets maintained whenever there are changes in X.

---

### Post by Vince4Amy on 2009-01-20
I agree with the X changes, apparently they're going to become a lot more frequent which means that every time a new distro release upgrades X the proprietary drivers aren't going to work until they're upgraded. The only solution I can think of is having an option on install to choose an older version of X if required, it would make sense to do this.

---

### Post by stalkingwolf on 2009-01-21
UPdate:
> Second, after an update, ( I was away from home, in a Motel) I can no longer access this site from firefox. ( havent tried other sites yet).

I just took my HP out of the case again last evening to use it.  First time
since we got home.  Now all seems fine.  I was all over the net including here with no problems.  Maybe it was the hotels connection blocking something.  Who knows.

---

### Post by dardack on 2009-01-22
> **stalkingwolf said:**
> UPdate:


I just took my HP out of the case again last evening to use it.  First time
since we got home.  Now all seems fine.  I was all over the net including here with no problems.  Maybe it was the hotels connection blocking something.  Who knows.

I travel a lot and find hotels suck with internet connections.  One night all websites work, next some do some don't.  I've even had (on a windows laptop for work) were once I back to work, my intel wireless program thing wouldn't find any (and I mean ANY) secured wireless networks, only unsecurred.  So i couldn't connect.  I uninstalled and reinstalled an updated one, still nothing.  Had to reinstall XP eventually.  No idea how this happened.  Coiencidence?  maybe but I don't believe in those much.

---

### Post by ugm6hr on 2009-01-23
> **jrusso2 said:**
> The only thing LTS means here is that its supported much longer.

I don't think that is true.

There was some publicity prior to the Hardy launch about conflict between Canonical, who were keen to keep late innovations to a minimum and the Ubuntu community developers who were in favour of bleeding edge.

---

