---
title: "trying to understand LTS and backport philosophy"
date: 2009-08-31
forum: The Cafe
---

### Post by AlanRick on 2009-08-31
Hi,
Apologies, but I come from the windows camp where apps mattered more than OS and I updated apps (firefix, openoffice...) on a frequent or automatic basis without touching the OS.

So when I moved to Ubuntu I was expecting/hoping for something similar and backport seemed to offer the prospect of upgrading packages delivered with ubuntu without updating the whole system. 

However, now I'm in the situation where I've noticed the apps are getting a bit long in the tooth (e.g. ff 3.5 is faster than 3.0...) and after researching a bit it seems that the backport repository won't update LTS-delivered packages after all. [E.g. mozilla sources are excluded ]("https://bugs.launchpad.net/bugs/395167")even though for many of us the browser is the most important aspect of a pc.

I also found a post from [Mark Shuttleworth]("http://www.markshuttleworth.com/archives/288") suggesting 2-3 year synchronized cycles but in practice this could make the situation even worse. I'd be forced to use old apps that had just missed the release date for another 3 years. 

Upgrading apps outside the ubuntu repository forfeits the stability offered by ubuntu (and judging from most posts seems to be trial and error according to which repository and method you select based on nothing more consistent than ad hoc forum responses). That's not really an option.

I can't image the situation is as hopeless as this so I must have misunderstood something along the way.

What is the best-practice approach to keeping apps up-to-date without investing huge effort? 

Alan

---

### Post by Moop on 2009-08-31
I'd suggest using a ppa to install newer apps. You can add the ppa to your repositories and the app will be installable with Synaptic and will also get updated. Or you can usually just get a deb from the ppa.

There is a ppa for firefox 3.5 that will work with hardy. 
[https://launchpad.net/~fta/+archive/ppa]("https://launchpad.net/~fta/+archive/ppa")

---

### Post by running_rabbit07 on 2009-08-31
Firefox can be updated from the Mozilla website using this [site's]("http://www.psychocats.net/ubuntu/firefox") method.

And,

Openoffice can be updated using this [site's]("http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04") method.

Both fixes are pretty simple. The best way to find out how to upgrade a program is to search Google with the words upgrade, Ubuntu, and the name of the program. Such as "[upgrade openoffice Ubuntu]("http://www.google.com/search?q=upgrade+openoffice+Ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")" and the link will take you to Google's search results for upgrading openoffice.

Or,

Go to the program's website to see what they have out. Most of them have the tar.gz and instructions on how to install them.

---

### Post by snowpine on 2009-08-31
Moop is correct; using PPAs is (arguably?) the best method to have the latest apps in Ubuntu. I'll also point out that Karmic Koala is coming out in October and will have lots of new apps (including FF3.5 as the default browser). Ubuntu tends to "lump together" all the major upgrades every six months (with a new release). Within the six-month cycle, you only get security updates and bug fixes (if you stick with the standard repositories). The LTS (long term support) releases (currently 8.04 Hardy Heron--which stands for "April 2008") are for conservative users who value stability above all else and are okay with using apps that are a year or two out of date. Keep in mind that Ubuntu is a descendant of Debian, which is prized for its stability but has a very slow "it's ready when it's ready" cycle.

Lots of people like to use "rolling release" distros (such as Arch or Sidux), which update to the newest apps as soon as they are available. Neither approach is better/worse; it just depends on what kind of user you are. Ubuntu is targeted more towards stability and usability ("Linux for human beings") than being the most "bleeding edge" distro. If you want new apps as soon as they are available, Hardy is arguably one of the worst distros you could choose.

---

### Post by AlanRick on 2009-09-01
Thanks for your responses. But it's not the technical aspect I was after (I'd googled for firefox packages and found a 3.5 package for hardy which by and large worked). It's the philosophy I don't understand.

> **snowpine said:**
> Ubuntu is targeted more towards stability and usability ("Linux for human beings") ...
But for joe public it's the usability of the apps that counts most whereas almost all hardy backport packages relate to developers and administrators and people who want to tinker with the OS - but there are very few apps backports. Ubuntu comes with apps (e.g. ff, thunderbird, openoffice) so why do the backports ignore them?

> **snowpine said:**
> Karmic Koala is coming out in October...
Updating the OS is a risk and often involves significant downtime before it runs again (I have to recompile a driver, jaunty failed to boot.. risking serious trouble twice a year is not an option). My experience of users (mothers in law, mates...) is that they are most happy leaving the OS alone (e.g. windows XP, MAC OS) but grateful to be able to accept the automatic app updates as they appear. Even if the app fails - there's always a workaround.

I was hoping for a similar experience with Ubuntu (but safer) and my impression is not only that it's not there yet (ubuntu bug #1) and that it's going in a different direction - aiming more for admins, tinklers and developers rather than commonal garden apps users.

I'm hoping to be pursuaded that the opposite is true.

---

### Post by snowpine on 2009-09-01
Why does an app suddenly become "unusable" just because a newer version comes out? You can still browse the web perfectly well with FF3.0. :)

It sounds like you're having trouble wrapping your head around exactly what a "Linux distribution" means. Here is an analogy: Most people look at a car and think "2009 Honda Civic." They don't see the individual parts (what type of tires, spark plugs, headlights, etc.) because everything is designed and tested to work well together. A minority of drivers are "into" cars and may swap out some of the old parts for new parts for a variety of reasons. If they know what they are doing, they get a performance boost, but if they don't follow the directions, the car won't run.

Basically the question you are asking is "Why doesn't a 2008 Honda come with 2009 tires?" Ubuntu 8.04 is the April 2008 version, so it uses the most stable browser as of April 2008. For the majority of Ubuntu users, it more "usable" to think "I'm using Ubuntu 8.04" rather than "I'm using FF3.0, OpenOffice 2.4, Totem 2.22, etc."
 For a sizable minority, however, hot-rodding the various parts is fun, and fortunately, there are a variety of easy and reliable tools to do this. :)

Bottom line is, I think you are missing the point of a Long Term Support release. It is supposed to be conservative and super-stable with very few updates. Nobody is going to persuade you that the opposite is true. ;)

---

### Post by AlanRick on 2009-09-01
Fair enough. The analogy is good.
My mind set is focusing more on the OS as a house and the apps as furniture which are worth renewing now and them (more often than the house).

I'm still not prepared to update the OS more often than necessary and if there was a ubuntu-maintained table showing which apps are delivered as part of the distro and the "arguably" best place to go for upgrades (with no guarantees) for the impatient that would be ideal. Maybe the app description could contain a reference to the source repository to add to the package updater for the "conservative reckless".

Thanks,
Alan

---

### Post by snowpine on 2009-09-01
> **AlanRick said:**
> if there was a ubuntu-maintained table showing which apps are delivered as part of the distro and the "arguably" best place to go for upgrades (with no guarantees) for the impatient that would be ideal. Maybe the app description could contain a reference to the source repository to add to the package updater for the "conservative reckless".


I think launchpad.net is as "official" as you'll find.

For example, for Firefox: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by AlanRick on 2009-09-12
I've mulled for a week but I still don't get it.
Snowpine, What you describe is Ubuntu pure but not not Backporting. And I get the feeling backporting is a serious inducement to use ubuntu but it is quietly being neglected.

Using your analagy...
My neighbour's car (Windows) allows the engine to be replace periodically (firefox, openoffice...) for free which boosts it's performance without the need to replace the car. I *can* do this for ubuntu, *but*  at my own risk :(  Alternatively I have to periodically *replace the whole car*.

Backporting was Ubuntu's equivalent of simply upgrading the  engine.
Ubuntu documentation on backport:
> For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain... 
This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is ...security AND....providing new versions of some programs... such as your web browser, word processor, IRC client, or IM client. 
**These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.**


That's exactly what is attractive about ubuntu but exactly the examples given by the ubuntu documentation are being neglected. Instead, backport in LTS is only being applied to admin stuff and applications of relatively little appeal (e.g. kstars - desktop planetarium).

I believe that neglecting the Backport channel seriously undermines the value of Ubuntu.

Alan

---

### Post by juancarlospaco on 2009-09-12
**The very last Version != The most Stable Version**
*as simple as that...*

---

### Post by ugm6hr on 2009-09-12
New versions of an application can (and do) introduce new bugs along with their new features.  Hence, while the OS stability may not be affected, the application's stability may be.

From Ubuntu's point of view, users see a bug in OpenOffice or Firefox, and blame Ubuntu, since these applications are part of Ubuntu's default applications.  LTS is designed to ensure this doesn't happen.

Comparing to Windows (pre-7), Internet Explorer is not automatically updated; there are plenty of people still using Explorer 6 out there.  As in Windows, a new browser is available in Ubuntu (if you choose to install it), but is not part of the standard update process.

As for the car analogy: you can replace your engine, but may find the new one more temperamental than the old, even though it makes you go faster when it works.

Backports is not in line with the Ubuntu 6-monthly release cycle and maintenance of bug / security fixes only.  You have not given a reference for the "documentation" you quote, but I suspect it is from the wiki rather than the official documentation.

While I personally agree it would be nice to have the latest features, Ubuntu LTS is being targeted at enterprise desktops, which require no downtime, and don't want to have to retrain people frequently to use new versions.  Consider how many offices still use Windows 2000 (or XP), and also Office 2003; they don't care that there is a new version out.

If you want a hybrid of stability of LTS vs new applications of latest OS, then use PPAs for whichever application you want.  The importance is choice and availability; if Ubuntu's philosophy doesn't fit you (even with PPA availability), then pick a Linux distro that does.

I can assure you that Mr Shuttleworth will not change his long term strategy because you don't agree with him.  This is in fact a recurring discussion, and will likely continue there if it does indeed continue for long.

---

### Post by markbuntu on 2009-09-12
The way the distribution scheme works is that once a distribution is released it will only update for compelling reasons like security and bug fixes. This insures maximum stability and shared library compatibility. 

Major changes are accomplished through distribution upgrades. Application version changes are not always so simple. The reason for this is that they often involve upgrading shared libraries, kernel modules etc which can break other applications, the kernel, etc.

Distribution upgrades are used to coordinate these changes across the platform to ensure compatibility and stability. Some distributions like Debian are stability focused while others like Fedora are focused on providing the newest features quickly. Ubuntu is somewhere in between. 

Then there are the rolling releases which try to maintain a steady upgrade path in a sort of piecemeal fashion which is not always so easy.

The least safe way to upgrade an application is installing it yourself from a deb or tarball. These are not recognized by the package manager and so can create library incompatibilities and other problems.

If you want to upgrade an application the safest way is through a PPA. The PPA will be handled by the package manager as a regular repository and can preclude the problems mentioned above.

---

### Post by snowpine on 2009-09-12
> **AlanRick said:**
> I've mulled for a week but I still don't get it.
Snowpine, What you describe is Ubuntu pure but not not Backporting. And I get the feeling backporting is a serious inducement to use ubuntu but it is quietly being neglected.

Using your analagy...
My neighbour's car (Windows) allows the engine to be replace periodically (firefox, openoffice...) for free which boosts it's performance without the need to replace the car. I *can* do this for ubuntu, *but*  at my own risk :(  Alternatively I have to periodically *replace the whole car*.

Backporting was Ubuntu's equivalent of simply upgrading the  engine.
Ubuntu documentation on backport:


That's exactly what is attractive about ubuntu but exactly the examples given by the ubuntu documentation are being neglected. Instead, backport in LTS is only being applied to admin stuff and applications of relatively little appeal (e.g. kstars - desktop planetarium).

I believe that neglecting the Backport channel seriously undermines the value of Ubuntu.

Alan

Hi Alan, it is pretty simple really... Linux is all about freedom and choice. Your posts give the impression the Ubuntu developers are forcing you to use older software, when in fact, it is a decision you made yourself by choosing an 18 month old, long term support distribution. Don't drive a Toyota if what you really want is a Ford; it's that easy. :)

---

### Post by Bölvaður on 2009-09-12
I'm not really happy about the replies you have been given AlanRick, even though some of them have been good.

This will probably hit you pretty hard, but an operating system is nothing but a bunch of software, like firefox, pidgin, gnome-terminal, lshw and so on.
What I am saying there is no sense in making a car or house analogies as they do not hold. All software is software and identifying them either as part of a house or furniture is not going to be easy, they are all just software in the end.

Ubuntu is based on packages, every part of the operating system is a package. The kernel is a package, the file manager is a package and every single package can be replaced by another package that does the same and no package can be considered to be more or less part of the operating system for the same reason why people argue that the kernel is the only part that can be called an operating system but some say it is either system tools and or preinstalled applications.
It's all just packages.

Now you should be able to see why you cannot say that you dont want to get a new house every half a year, as there is no house. The house is not distinguishable from the furniture.


Ubuntu is updated frequently, like the kernel has updates every week, but they dont all make it into the ubuntu repositories. So if you want to really have this house analogy then you are switching houses way more often than furniture.

now I have become the worst post in this thread... man.. I suck at explaining :(

---

### Post by SunnyRabbiera on 2009-09-12
This all goes down to "latest and greatest" vs "stable and reliable and known to work"
Most people want the latest version of something, in the Windows world its always common practice to update constantly to stay ahead of things like viruses, malware, and stuff like that.
The Linux approach is different, its more like "update when needed"
You dont need Firefox 3.5 for example, or even Open Office 3.1, so to leave Firefox 3.0 and Open Office 2 as default makes perfect sense.
If its a security thing well thats mostly taken care of, most major security patches are made via backports to keep you safe.
Security is very critical to Ubuntu and its developers, you might not get "latest and greatest" software, but you do get software that is both safe and stable.
For those who want bleeding edge PPA's are there to help, PPA's are safe and secure.

---

### Post by AlanRick on 2009-09-12
> **ugm6hr said:**
> You have not given a reference for the "documentation" you quote, but I suspect it is from the wiki rather than the official documentation.
You're right. It was the [community documentation ]("https://help.ubuntu.com/community/UbuntuBackports").
The "official ubuntu book" (3rd edition - Hill et al) does mention Backport as one of the 5 ubuntu repositories but makes it clear it is a community repository. 
I understand about the risks of change and the effort needed for QA (which is why I'm a happy camper on LTS) and I understand that the Backport repository is community driven and can weaken the stability. 
I guess I'm just expressing a feeling that the Ubuntu Backport repository is a very useful asset for Ubuntu and it would be brilliant if there were 100 times as many generous individuals working on it. That there are not, and that silver can't be turned to gold are simple facts of life that I can live with :)

Many thanks for every single explanation,
Alan

PS: Snowpine - it's because of the freedom of choice that I'm asking :) Do I look for another another repo? I did. But I'm sticking with Ubuntu.

---

