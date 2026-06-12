---
title: "Fedora Silverblue's Concept"
date: 2019-07-29
forum: The Cafe
---

### Post by Shibblet on 2019-07-29
I just read a very interesting article about Fedora Silverrblue here:  [https://fedoramagazine.org/what-is-silverblue/]("https://fedoramagazine.org/what-is-silverblue/")

What they have done is created a system referred to OSTree, which keeps the Operating System independent of any additional packages that are installed.  All software is installed via Snap or FlatPak, and the dependencies are built in.  
 
This is a really great concept. In theory, it seems incredibly stable, and cannot be messed up by installing, or removing, a (un)neccessary package.

 Do you think Ubuntu has any plans to do this in the future?

---

### Post by TheFu on 2019-07-29
These things are good for a tiny subset of needs.  OTOH, if you have a 20th generation Core i7 and 256 GB of RAM, there might be a use.
But if you have a 15 yr old PC with 1.5G of RAM (or any low-end sub-$300 laptop), then these are terrible solutions due to the added overhead for every program to load all libraries into separate memory space, no ability to share code (CS) between different programs, and basically negating the entire reason that shared libraries were created decades ago.  There is a very good reason for shared libraries over using static linked libraries.

snaps and flatpaks have issues when you need programs to work together. Because they are segmented off from each other, the default is for them not to work together.  Perhaps an expert might be able to enter some magic incantation to get 2 snap programs to talk.  Grandma doesn't need that.  Normal users don't need that.  Solutions need to work for normal people, out of the box.

ChromeOS works with an immutable OS, but without all the compartmentalization.  This means it is a highly secure OS, as the boot is validated using TPM hardware and the OS can't be modified from the running OS.  The main issue with ChromeOS isn't security, it is privacy.

BSD-based routers also use an even/odd OS installation method.

Cubes has been around a long time, though I don't recall if they use containers or full VMs to split off different programs.

Good to watch what researchers are trying, but be very cautious when anyone is over zealous about anything new until it is proven for a year or two without ANY issues. Snaps, as deployed by Canonical, are breaking all sorts of workflows, today.  They are planning to force them onto Ubuntu more and more until snaps are the only supported packages.  
New features that break, old workflows without any possible replacement angry users.  

As you say, "it seems like a great concept", but we've seen that snaps are less than a great concept in many cases already.

---

### Post by sevendogs1337 on 2019-07-29
FreeBSD (not a Linux distro) does this but doesn't use flatpaks, snaps, whatever they are. The core OS is virtually separated from all end user software. All end user software gets installed under 
"/usr/local" instead of being mixed in with the OS like Linux does. I prefer this to anything I have seen in Linux. However...it doesn't make as easy a desktop as Linux does so that's why I only use it for servers.

Not sure the security implications of flatpaks, snap, etc. Probably fine if the distributor keeps them updated but I am not sure how that happens as I don't use them.

---

### Post by #&amp;thj^% on 2019-07-29
The FreeBSD Capsicum framework is used for sandboxing and compartmentalizing file descriptor rights for applications.
As far as automatic deployment of sandboxed applications, this can be somehow tied to a pkg, but I think the apps themselves would need to incorporate the 'Capability mode' APIs in FreeBSD. I'm not sure though.
Flatpaks/Snaps really have no place on a FreeBSD system. It's a band-aid to a more fundamental problem in Linux IMHO.

---

### Post by sevendogs1337 on 2019-08-02
Exactly.

---

### Post by cruzer001 on 2019-08-02
Snaps came out of the oven too soon.  This Silverblue is sounding real interesting to me, RedHat tends to plan and execute more cautiously than Canonical IMO giving them the better product at times.  Have to see how it goes.

---

### Post by TheFu on 2019-08-02
> **sevendogs1337 said:**
>  All end user software gets installed under 
"/usr/local" instead of being mixed in with the OS like Linux does.

Please don't blame "Linux" for things that are a package management choice, which has NOTHING TO DO WITH LINUX.  In the olden days, and still with some distros, software packages are installed into /usr/local/.  We'd upgrade versions just by moving a symbolic link.  Lots of slackware people still do it that way. Some use a tool called epkg, which should work on any Unix-like OS.

The packaging complaint seems to be about Debian and RHEL and Arch and SuSE.  I completely understand, since I disliked how package storage use was split into programs, settings, and data into /usr/, /etc/, and /var/ respectively on those specific systems.  It was a distro choice, not "Linux."

If we install using the source, then we can place the installation anywhere we like.  By letting the package management tools handle the locations for files, we can install meta-packages that integrate apache, php, mariadb with 1 package install command.  That's pretty sweet for many admins.  People who want to have 100% control over those integrated parts probably dislike the "magic" of the metapackage.  The **tasksel** tool can really save time for an admin.

Clearly, I'm not a fan of most of these snap/flatpak package solutions, but I care more about RAM use than many people.  Most of my "servers" have 384MB - 1GB of RAM, so blowing 800MB to run a single flatpak tool is a total failure to me.  I've worked places, before we mandated the move to virtual servers, that had server average utilization of 13%.  After mandating the use of virtualization, we would have servers running at 60-80% utilization, a huge win for the business to get the most value from their hardware investments, not to mention the power, cooling, and physical space savings that came with virtualization.  

These include-the-kitchen-sink packaging solutions will destroy much of the savings achieved the last decade.

---

### Post by sevendogs1337 on 2019-08-02
Not blaming the OS, just stating it is done differently. I have not had a problem with either system frankly: Linux or BSD. The BSD way just seems "cleaner" but again, it's just a different way of doing things. Flatpak/snap is more of the way Apple does things, but that isn't bad really either, just different. I prefer normal package installs the way either BSD or Linux does them and not how they are implemented in flatpak/snap.

I am exactly the opposite on RAM: I used to fret over ram utilization, now I just buy as much ram as I can afford and don't care any more. My PC has 32GB and my FreeBSD build server has 96GB. I don't run servers for a living though so if I did, I would have to worry about it more I am sure.

---

### Post by #&amp;thj^% on 2019-08-02
I see no Blame being placed here, just modest user opinions. (To be noted only)
I've not seen any higher ram usage with FreeBSD servers. (But I live by the K.I.S.S rule)
In fairness and NOTE:>>**"IMHO"**:
So, which one is the &#8220;best&#8221;? Well, it will depend on what do you want to achieve. AppImages are the best choice for end user content distribution and desktop oriented computing. Flatpak will shine when you use only one desktop environment, whereas Snappy is the best choice for IoT devices on which the vendor must ensure that the device will work without or with small user interaction; and snaps implement automatic updates.
I can fully appreciate TheFu's point, but again "It's a band-aid to a more fundamental problem in Linux"IMHO
In all honesty I get jaded at times by the Authors of the mentioned systems applications. :( ...(Not a good thing admittingly)

---

### Post by Geoffrey_Arndt on 2019-08-02
Well . . . I read the linked thread closely, and then all the comments from users,, devs, sysadmins, etc.    It seems a large majority (80-90 percent) of the power users, devs, admins, devops, systems engineers & kernel team folks are not excited about using Silverblue.   

Linux and Unix users like control and flexibility.  SB looks like a solution looking for a problem.

Of the three new methods for installing & managing packages - - the least disruptive and intrusive to the system seems to me ,. . . . to be AppImages (and they're the easiest to remove without disrupting the core OS).   Even then, these kind of tools should be used only as supplemental ways to create/install/update programs and related (imho).

---

### Post by cruzer001 on 2019-08-02
> **TheFu said:**
> 
These include-the-kitchen-sink packaging solutions will destroy much of the savings achieved the last decade.
Not all is repackaged.  Dependencies are shared between flatpak's, I don't know how snap works it.

---

### Post by Shibblet on 2019-08-05
> **TheFu said:**
> Please don't blame "Linux" for things that are a package management choice, which has NOTHING TO DO WITH LINUX.  In the olden days, and still with some distros, software packages are installed into /usr/local/.  We'd upgrade versions just by moving a symbolic link.  Lots of slackware people still do it that way. Some use a tool called epkg, which should work on any Unix-like OS.

The packaging complaint seems to be about Debian and RHEL and Arch and SuSE.  I completely understand, since I disliked how package storage use was split into programs, settings, and data into /usr/, /etc/, and /var/ respectively on those specific systems.  It was a distro choice, not "Linux."

If we install using the source, then we can place the installation anywhere we like.  By letting the package management tools handle the locations for files, we can install meta-packages that integrate apache, php, mariadb with 1 package install command.  That's pretty sweet for many admins.  People who want to have 100% control over those integrated parts probably dislike the "magic" of the metapackage.  The **tasksel** tool can really save time for an admin.

Clearly, I'm not a fan of most of these snap/flatpak package solutions, but I care more about RAM use than many people.  Most of my "servers" have 384MB - 1GB of RAM, so blowing 800MB to run a single flatpak tool is a total failure to me.  I've worked places, before we mandated the move to virtual servers, that had server average utilization of 13%.  After mandating the use of virtualization, we would have servers running at 60-80% utilization, a huge win for the business to get the most value from their hardware investments, not to mention the power, cooling, and physical space savings that came with virtualization.  

These include-the-kitchen-sink packaging solutions will destroy much of the savings achieved the last decade.

As much as I agree with you, the word "Linux" is known more as a terminology than a kernel.  Much like Stallman's attempt to increase awareness for the GNU, by calling it GNU/Linux.  Whereas I agree with this ideology, I think it is more for increasing awareness among those who use it.  Which is actually what you've done by increasing the awareness on a specific distro's forum.  ;-)  Most people don't even know what a Kernel is, let alone a Desktop Environment, File Structure, or the GNU.  To them, it's all just an OS.  To most, it's just "computer."

It is easier to call it all "Linux."  However, once a person becomes interested in the inner workings of any distro, they quickly realize what "Linux" truly is.  As a matter of fact, when you go to software websites that support Linux, the software is usually found under the title of "Linux," and not distro specific.

Examples:  Select the driver you need at: [https://www.geforce.com/drivers]("https://www.geforce.com/drivers")
This one at least has the title Ubuntu, next to the .DEB file (and not Debian.) [https://handbrake.fr/downloads.php]("https://handbrake.fr/downloads.php")

Currently, it is used a general idea of all distributions that use the Linux Kernel.  It's akin to saying "Kleenex" when you may be reaching for a "Puffs," or "Band-Aid" when all you have is a "Curad."  IMHO, I think that name recognition is what has furthered Linux's cause, and allowed it reach to where it is today.  Windows and MacOS are the two most dominant PC Operating Systems.  However, people have heard of Linux.  Not many have heard of BSD, Haiku (BeOS), or Solaris.

---

