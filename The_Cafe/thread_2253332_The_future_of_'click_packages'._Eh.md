---
title: "The future of 'click packages'. Eh?"
date: 2014-11-19
forum: The Cafe
---

### Post by Roasted on 2014-11-19
Hello friends. I've been doing some reading on click packages but I still feel like I'm having some difficulty wrapping my brain around it. I understand some of these questions may be shooting a bit far off into the future, but at the same time, maybe not. So the basic premise behind the click package system is so developers can bundle all of their dependencies and whatnot into the click package. The process itself from a dev standpoint sounds easy, but I'm left feeling a little gray on a few areas. 

For starters, what does this mean for updates? If a dev pushes an update, then what? Do I get it? Is it part of the regular system updates or is it signified separately in some sort of notification menu?

Likewise, what sort of items can go into a click package? Can we expect to see bigger applications, like Gimp, Libre Office, etc, packaged as a click package? Or is there something about their size/type of build that would, in theory, effectively only allow smaller items to be "click packaged"?

Is there anything exclusive to the click package system? Or is this something other distros can pick up accordingly?

Thanks for your help!

---

### Post by buzzingrobot on 2014-11-19
The primary target right now seems to be phones and devices, where people expect this kind of application installation/deletion functionality.  

What happens with desktop Ubuntu is down the road, I'm sure.

---

### Post by ian-weisser on 2014-11-19
> **Roasted said:**
> what does this mean for updates? If a dev pushes an update, then what? Do I get it? Is it part of the regular system updates or is it signified separately in some sort of notification menu?

One of the purposes of click packages is to make updates *easier*. And more frequent for some.
Click packages will have many of the same benefits as a PPA...but easier for the packager, and won't cause apt conflicts the way many PPAs currently do.
The specific settings, and how they fit in with Software Updater, are still to be decided. I suspect that click updates will be part of System Updater - it will update your deb packages, then it will update your click packages.


> **Roasted said:**
> Likewise, what sort of items can go into a click package? Can we expect to see bigger applications, like Gimp, Libre Office, etc, packaged as a click package? Or is there something about their size/type of build that would, in theory, effectively only allow smaller items to be "click packaged"?

There is no size or complexity limitation to click packages. 
Click packages are *intended* for smaller applications that interact with the system using the Ubuntu SDK API instead of direct shared library use. Games and apps that need access to Contacts, GPS, Network, etc.
Click packages offer an *advantage* to applications with update needs that don't match Ubuntu's cycle well.

Example: LibreOffice is already deb-packaged for Debian, and it will still be included as the default office work application bundle in Ubuntu as a deb. Some people want a newer version of Libreoffice, they can click-package the newer version (alternative to PPA). The user can choose either version.


> **Roasted said:**
> Is there anything exclusive to the click package system? Or is this something other distros can pick up accordingly?

There is nothing exclusive to the click package system. Deliberately. Any distro can use it.

---

### Post by buzzingrobot on 2014-11-19
> **ian-weisser said:**
> 
Click packages are *intended* for smaller applications that interact with the system using the Ubuntu SDK API instead of direct shared library use. Games and apps that need access to Contacts, GPS, Network, etc.
Click packages offer an *advantage* to applications with update needs that don't match Ubuntu's cycle well.

Example: LibreOffice is already deb-packaged for Debian, and it will still be included as the default office work application bundle in Ubuntu as a deb. Some people want a newer version of Libreoffice, they can click-package the newer version (alternative to PPA). The user can choose either version.


In the case of existing apps that do not use the Ubuntu SDK API, can they be packaged as Click apps without altering their shared library dependencies?  If so, does this mean Canonical will be repackaging some of the packages brought over from Debian in Click format?

Is there any possibility of a user-side tool that would allow real-time conversion of traditional shared library packages in the repos to Click format at the point and time of installation?  That is, let's say the install tool gives me an option to install traditional Package X in Click format.  If I check it, that traditional package and all its dependencies are acquired, converted to Click format, installed in Click format, and the system henceforth treats it as a Click package for updates, etc.

---

### Post by Roasted on 2014-11-19
> **ian-weisser said:**
> 
There is nothing exclusive to the click package system. Deliberately. Any distro can use it.

Ahh, beautiful. That's awesome to hear. This does make me wonder a bit though, because, well, I'm a curious person and that's what I do. Would click packages (by their current understanding) eliminate any sort of RPM vs DEB builds that are currently needed? As in, if a dev packages all needed dependencies for the application, then there wouldn't be much need for a specific RPM or a specific DEB build, would there? I mean, everything needed for the package itself would be already bundled, so specific builds such as RPM would be unnecessary at that point, eh?... is my understanding accurate?

Likewise, what is it that makes a distro click package compatible? Is there work to be done on the actual distro/OS itself so it will accept click packages? As in, could I fire up my trusty old 10.04 install and have it accept click packages? Or must a distro build itself to intentionally fit the click package paradigm in order to accept them accordingly? If a distro must be built to accommodate click packages, is it a monumental amount of work? Or is it something that is so easy, it's a no brainer so just do it? After all, we all know that Unity can be technically ported to other distros, but we've seen how well that turned out, since due to the work involved to make it even halfway fly, nobody bothered. 

I also wonder about some other things, such as how the application launcher picks up the app as available to the system. As in, let's say I install the Audacity click package. If it's self contained, how does the system suddenly know that Audacity is available if I search in the Unity dash? Or the Cinnamon menu? Or Gnome activities/applications?

I fully understand this might be drawing up more questions than what we have answers to yet since we're early in the click package game, but I figured why we were already rocking a solid click package discussion, I'd do a brain dump of what I'm curious about and see what you folks have to say.

Thanks for your time! :guitar:

---

### Post by grahammechanical on 2014-11-19
Read from someone who knows.

[http://beuno.com.ar/archives/334](http://beuno.com.ar/archives/334)

[http://askubuntu.com/questions/485401/what-security-differences-are-between-click-and-deb-package](http://askubuntu.com/questions/485401/what-security-differences-are-between-click-and-deb-package)

> [COLOR=#000000]Can we expect to see bigger applications, like Gimp, Libre Office, etc, packaged as a click package? [/COLOR]

All things are possible, but someone has to do the work. In Ubuntu + Mir + Unity 8 it will be possible to install both Click packaged apps and deb packaged apps for years to come.

I have Ubuntu Desktop Next (Vivid) installed. Which is the Ubuntu phone UI running on Mir. There are two update processes, one for the system and one for installed click packaged apps. This morning I got an update to the music app. The system update does not work and I think that is because the intention is for Ubuntu phones to have image updates and not package updates as we have at present on desktop Ubuntu. So, I update the system using apt-get in a tty. It proves the separation of click app updates from system updates.

I also heard during the recent online summit that apps like Gimp and Libreoffice will run on a rootless X server that in turn runs on Mir. That is how I understand it. The other month it was said that Mir+Unty 8 would be default by 16.04. Then during the online summit I heard that Mir+Unity 8 will be an option for 16.04 users. Nothing is fixed in stone. Except the need to provide Ubuntu users will the desktop experience that they expect from Ubuntu.

The future of Click packaging is tied in with the future of Ubuntu. I have not seen the slightest hint that there is any intention to lock in or lock out anyone. There is the obvious intention of making Ubuntu phones and tablets profitable contenders in the mobile device market. Users of those kind of devices need apps, lots of apps and online services. They may not be too aware of it but they also need secure devices.

In my opinion, the Ubuntu security team have set a high standard for user security in their conditions for the building of the Click utility. That should give Click a future. But humans are funny people. and I do not mean funny --- Ha, Ha!

Regards.

---

### Post by grahammechanical on 2014-11-19
> [COLOR=#000000]As in, could I fire up my trusty old 10.04 install and have it accept click packages? [/COLOR]

Can you at the moment run an application on a system that does not have the correct libraries installed? For example, if the developer used a specific GUI tool kit and the distribution did not have the libraries for that tool kit.

Ubuntu developers have to include various libraries in the distribution. That applies to any Linux distribution. Why expect it to be different with the Click packaging method? Think of the benefit to those distributions built on Ubuntu. The work will already be done for them, as it is at present.

Regards.

---

### Post by Roasted on 2014-11-19
> **grahammechanical said:**
> Read from someone who knows.

[http://beuno.com.ar/archives/334](http://beuno.com.ar/archives/334)

[http://askubuntu.com/questions/485401/what-security-differences-are-between-click-and-deb-package](http://askubuntu.com/questions/485401/what-security-differences-are-between-click-and-deb-package)

The other month it was said that Mir+Unty 8 would be default by 16.04. Then during the online summit I heard that Mir+Unity 8 will be an option for 16.04 users. Nothing is fixed in stone. 

I know you said nothing is fixed in stone, but this caught my eye. Given that Unity 8 + Mir was supposedly going to be an option for 15.04, I figured they would easily have it in 16.04. If that gets pushed back again... sad face.

---

### Post by craig10x on 2014-11-19
So the, I take it that if say, VLC Media Player or Pidgin Messenger or Rhythmbox (just to throw out a few examples) didn't make a "click package" then we still would not get newer versions of their applications and then we would still have to either add ppas for them or install the newer version manually?

If so, then the after convergence and Unity 8 arrives in 16.04, Ubuntu still would not be a fully rolling style release because only those apps or functions that click packages were developed for would actually roll into newer versions?  Or is it likely that most will go the "click package" route for all the conveniences it would bring?

Also, what about say, kernels? would they be click packages too? 
If Ubuntu really is planning on eliminating the 6 month release and make it a sort of rolling style version,  then one would expect most things to get updated with newer versions periodically and not stay stagnant over the long run...

---

### Post by ian-weisser on 2014-11-19
> **buzzingrobot said:**
> In the case of existing apps that do not use the Ubuntu SDK API, can they be packaged as Click apps without altering their shared library dependencies?

Click packages can use ONLY dependencies in the default install (informally called Ubuntu Base; think Ubuntu-desktop metapackage).
Click packages can NOT trigger apt, and have no way to import deb dependencies. That's why they must have all non-Ubuntu-Base dependencies included with them. 

  > **buzzingrobot said:**
> If so, does this mean Canonical will be repackaging some of the packages brought over from Debian in Click format?

No. Debs are debs, and will remain debs, and will remain in the Ubuntu repositories for debs.
If someone else wants to click-ify software, they are welcome to do so if that license permits.

> **buzzingrobot said:**
> Is there any possibility of a user-side tool that would allow real-time conversion of traditional shared library packages in the repos to Click format at the point and time of installation? That is, let's say the install tool gives me an option to install  traditional Package X in Click format.  If I check it, that traditional  package and all its dependencies are acquired, converted to Click  format, installed in Click format, and the system henceforth treats it  as a Click package for updates, etc.

Not planned. It's not prohibited - someone can create that tool if they really want it.

I'm not sure why users would want that - most users won't (and shouldn't) know the difference.
Click is more than just a different format. The Ubuntu implementation includes lots of developer-side integration - accounts, metadata, and build tools on developer.ubuntu.com. You need that upstream integration for updates to work. If you create a fresh click package without it, the system won't know where to seek updates from.

---

### Post by ian-weisser on 2014-11-19
> **craig10x said:**
> So the, I take it that if say, VLC Media Player or Pidgin Messenger or Rhythmbox (just to throw out a few examples) didn't make a "click package" then we still would not get newer versions of their applications and then we would still have to either add ppas for them or install the newer version manually?

Correct.
Application debs will continue to be imported from Debian on the 6-month release cycle. That's the discussion I have seen.
Community members and teams that want to publish newer versions can use click packages and/or PPAs, and publish updates whenever they wish.


> **craig10x said:**
> If so, then the after convergence and Unity 8 arrives in 16.04, Ubuntu still would not be a fully rolling style release because only those apps or functions that click packages were developed for would actually roll into newer versions?

Correct.


> **craig10x said:**
> Also, what about say, kernels? would they be click packages too?
Debs remain debs, the heart of the system. Click packages must fit on top of the working system (made up entirely of debs), and interface with the system only through the published API. Click packages are not trusted by the system.
To me, the kernel seems quite unsuitable for click. The existing kernel update security, testing, and distribution channel seems to work well enough.

---

### Post by craig10x on 2014-11-19
Thanks ian-weisser...that gives me a much CLEARER picture on how it will work ;)
I would imagine that, as far as kernels go, if the 6 month version was eliminated and replaced with that new version, then ubuntu would periodically update the kernel (through the software updater) for newer versions (using a deb package of course)...Also very likely, major used default apps like libreoffice, vlc player, pidgin, rhythmbox, etc would probably set up click packages...

---

### Post by ian-weisser on 2014-11-19
> **craig10x said:**
> Also very likely, major used default apps like libreoffice, vlc player, pidgin, rhythmbox, etc would probably set up click packages...

Perhaps, and perhaps not. You might want some of those applications' features to remain in the core.
Click packages are not shared. Interaction and data-sharing is limited to what's available in the Ubuntu API. Core services cannot depend on transient click apps.

Example: If a developer wants to display or export tabular data, it's a lot easier if the developer can trust that a core service capable of importing that data into a spreadsheet is available.

---

### Post by user1397 on 2014-11-19
I think I missed something...what exactly are you guys talking about?  I haven't heard anything about click packages or their relationship to ubuntu...  :/

---

### Post by craig10x on 2014-11-19
That has to do with when unity 8 becomes the default desktop (either in 15.10 or definitely by 16.04) At that point, there will be convergence between desktop/tablet/phone (the others were already done, desktop is being worked on)...part of it will be a new packaging system added (That's called click packages but they are not referred to by name in the article i linked below)...At that point, there is a pretty good chance the 6 month version of ubuntu will be eliminated and replaced by a version that will sort of "roll" in the sense that the desktop will be able to get new stuff much like say, your android phone does...And that's because the coding for all ubuntu versions will be the same even though the actual interface will vary according to the type of device it is installed on...

This article will give you a better idea:
[http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml](http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml)

---

### Post by ian-weisser on 2014-11-19
> **ubuntuman001 said:**
> I think I missed something...what exactly are you guys talking about?  I haven't heard anything about click packages or their relationship to ubuntu

Debian packages build an awesome, stable desktop system, but have drawbacks for use on a phone.
- The review and testing of new submissions takes too long, and won't scale up to thousands of new mobile apps.
- Debian packaging is complex; many developers don't want to learn how to make debs.
- Updates only every six months.
- Requires admin password.
- Handles namespace collisions poorly.

Click packages are a new package format that address some of these shortcomings.
Click packages _do_not_ replace debs. Your system is still built with debs. Click packages are user-level, user-facing applications that interface with the Unity API instead of with system shared libraries.
- They are initially intended for small-screen, limited function apps (weather app, contacts app, small games, etc).
- They are installed without sudo.
- They are installed to /opt.
- They cannot cannot install or remove any deb dependencies.
- They update when the packager pushes an updated package; totally independent of Ubuntu's six-month cycle.
- Ubuntu provides and supports a small set of Core Apps ([https://wiki.ubuntu.com/Touch/CoreApps](https://wiki.ubuntu.com/Touch/CoreApps)) only. External developers will push the rest. Those developers don't need to become Ubuntu members or learn deb packaging.

---

### Post by user1397 on 2014-11-20
> **craig10x said:**
> That has to do with when unity 8 becomes the default desktop ...

> **ian-weisser said:**
> Debian packages build an awesome, stable desktop system ...
Thanks both of you, I understand now.

---

### Post by craig10x on 2014-11-20
You are very welcome ;)

By the way, ian-weisser: You know, if you carefully read this paragraph from the article i linked (the quote from ubuntu desktop developer Will Cooke, He appears to be saying that the new version of ubuntu WOULD get most (not just some) of the new stuff as it becomes available, instead of having to wait 6 month periods to get it (when traditionally, the next 6 month version would come out)...and that includes the apps as well...

Which actually makes sense, because if only some of the stuff would get updated, and the rest would stay stagnant, what would be the point?  Mark Shuttleworth said he agrees with the developers that this will allow them to replace the 6 month version with this new, sort of rolling style version...

**Why the new Ubuntu desktop is so special**

[COLOR=#000000][FONT=museo_sans]You might think that it's just another update to the desktop environment, but Unity 8 is actually more than that. Because of the way Unity 8 is built, users will be able to get the latest version of most of the packages included in the OS right when they are released. They will no longer have to wait for a new version of Ubuntu to get a fresh build of an important application or library.[/FONT][/COLOR]

[COLOR=#000000][FONT=museo_sans]"Traditionally a given release of Ubuntu has shipped with the versions of the applications available at the time of release. Important updates and security fixes are back-ported to older releases where required, but generally you had to wait for the next release to get the latest and greatest set of applications. The new desktop packaging system means that application developers can push updates out when they are ready and the user can benefit right away," says Will Cooke.[/FONT][/COLOR][COLOR=#000000][FONT=museo_sans]
[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-11-20
I think we're reading into his words differently. And there's a bit or marketing spin in there, too.

Yes, applications can be updated more frequently. No more waiting for the next release of Ubuntu to update to the bleeding edge release of an application...if those applications are click-ified and maintained by somebody not-Canonical.

Nobody has committed to Ubuntu as a rolling release after Click packages  go live. The term 'sort of rolling' applies to Click-packaged  applications only. It's going to be huge for users - I'm thinking of the  number of PPAs that can be replaced by Click packages.

Nobody said anything about the 6-month testing and release cycle changing for the kernel, shared libs, system services, and applications that are all provided by debs, and will continue to be provided by debs.

Sure, Will was positive on Click. I am too.

---

### Post by craig10x on 2014-11-20
Oh, i see what you are saying....so then the "click packages" can be used by the developers as a substitute for ppas...In that case, i would think that many of the major apps we use (like pidgin, video player, vlc media player, rhythmbox and so forth) would probably do it, so that's how we could more easily get new versions of apps...meanwhile, ubuntu itself will be doing updates on it's general structure, new kernels, etc...So, potentially, it could still develop into a kind of rolling ubuntu in a very "natural way" as it were ;) :)

Found another interesting softpedia article, this one specifically about click packages:
[http://news.softpedia.com/news/Ubuntu-s-Click-Packages-Might-End-the-Linux-Packaging-Nightmare-464271.shtml](http://news.softpedia.com/news/Ubuntu-s-Click-Packages-Might-End-the-Linux-Packaging-Nightmare-464271.shtml)

---

