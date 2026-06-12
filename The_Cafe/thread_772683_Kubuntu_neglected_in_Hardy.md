---
title: "Kubuntu neglected in Hardy?"
date: 2008-04-28
forum: The Cafe
---

### Post by aysiu on 2008-04-28
I know people tend to think Kubuntu gets the short end of the stick in development, but this time it's really happened.

I've been trying to slowly update my Psychocats tutorials, and I noticed that Ubuntu comes with all the major repositories enabled (Universe, Multiverse), but Kubuntu has only Main and Restricted enabled with no KMenu entry for Software Sources (both Ubuntu and Xubuntu have a Software Sources entry in the System menus).

Is this a bug? Why would they do this?

---

### Post by LaRoza on 2008-04-28
> **aysiu said:**
> I know people tend to think Kubuntu gets the short end of the stick in development, but this time it's really happened.

I've been trying to slowly update my Psychocats tutorials, and I noticed that Ubuntu comes with all the major repositories enabled (Universe, Multiverse), but Kubuntu has only Main and Restricted enabled with no KMenu entry for Software Sources (both Ubuntu and Xubuntu have a Software Sources entry in the System menus).

Is this a bug? Why would they do this?

Kubuntu 8.04 isn't LTS, so it may be due to that.

They did this because they didn't want to hold back on KDE.

---

### Post by FuturePilot on 2008-04-28
Did it ever have an entry for Software Sources? I don't seem to recall one, but maybe I'm wrong. Whenever I tried Kubuntu, to manage repositories I always went through Adept&#8594;Manage Repositories.

---

### Post by aysiu on 2008-04-28
So LTS means that it would have extra repositories enabled?

In any case, regardless of whether it has Software Sources or not, why wouldn't it have Universe and Multiverse enabled by default?

---

### Post by aysiu on 2008-04-28
So LTS means that it would have extra repositories enabled?

In any case, regardless of whether it has Software Sources or not, why wouldn't it have Universe and Multiverse enabled by default?

---

### Post by samwyse on 2008-04-28
I expected a complain of something less trivial. I didn't know they were supposed to be enabled. How about KDM dying everytime logging out using the restriced NVidia drivers?

It needs a sudo /etc/init.d/kdm restart to get it back. Luckily I don't need to log out often.

---

### Post by bobbocanfly on 2008-04-28
Kubuntu development has been hard this release cycle due to people toiling over whether you want to run KDE 4 (Less stable, not great for LTS) or 3.x (More stable, but probably wont be still getting patched/supported by the next LTS).

One of the problems is that development has been less focussed as basically 2 versions were being built. I dont know much about KDE/Kubuntu but im going to guess that the default KDE apps in 3.x differ to the KDE apps in 4.x which means there are basically two sets of packages to maintain which doubles the workload on the developers and Kubuntu devs are a little thin on the ground compared to Ubuntu standard.

(Back to the point) It wasnt 'neglected' but the KDE4 stuff happened at a really awkward time which made development much harder for the Kubuntu devs. I also think that more emphasis was put onto making the standard variant most stable as it is the one most people (read big companies etc.) will probably be using.

---

### Post by LaRoza on 2008-04-28
> **aysiu said:**
> So LTS means that it would have extra repositories enabled?

In any case, regardless of whether it has Software Sources or not, why wouldn't it have Universe and Multiverse enabled by default?

I don't know.

I am not familiar with what is enabled by default. I never actually used Kubuntu, so I don't know what it is like.

I have used KDE on Ubuntu though.

---

### Post by acelin on 2008-04-28
I think problems like this could be solved.

Get rid of Kubuntu. 

What would be the best way to get the devs to make Ubuntu have Gnome by default, but somewhere in the installation make it where knowledgeable users could choose KDE?

---

### Post by aysiu on 2008-04-28
> **acelin said:**
> I think problems like this could be solved.

Get rid of Kubuntu. 

What would be the best way to get the devs to make Ubuntu have Gnome by default, but somewhere in the installation make it where knowledgeable users could choose KDE?
Ubuntu already does have Gnome by default, and it already makes it so knowledgeable users can choose KDE (by downloading Kubuntu... or by doing a command-line install and then picking what components they want to add).

---

### Post by Polygon on 2008-04-28
> **samwyse said:**
> I expected a complain of something less trivial. I didn't know they were supposed to be enabled. How about KDM dying everytime logging out using the restriced NVidia drivers?

It needs a sudo /etc/init.d/kdm restart to get it back. Luckily I don't need to log out often.

again, you cant blame ubuntu for bugs introduced by CLOSED SOURCE DRIVERS. if you look at the restricted drivers manager (if kubuntu even has one) it says that restricted drivers cannot be supported by ubuntu

so take your complaint to nvidia ;)

---

### Post by TeraDyne on 2008-04-28
> **acelin]I think problems like this could be solved.

Get rid of Kubuntu. [/QUOTE]

If this happens, you'll be the first that I blame. XD

Just kidding.

[QUOTE=Polygon said:**
> again, you cant blame ubuntu for bugs introduced by CLOSED SOURCE DRIVERS. if you look at the restricted drivers manager (if kubuntu even has one) it says that restricted drivers cannot be supported by ubuntu

so take your complaint to nvidia ;)

Kubuntu has a restricted drivers manager. 

For the record, This just isn't about proprietary drivers. Here's the launchpad bug report: [https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)

In my comment there, I mention that my laptop doesn't even run the restricted drivers, and still has the bug. This is in KDM itself through some change\regression. It doesn't exist in Gutsy, which is what I'm using on my desktop right now.

I don't think it was Kubuntu being neglected. It's just that there wasn't enough developers and testers to properly go through everything. The majority seem to be working with GNOME on Ubuntu instead, and that puts a strain on those working with Kubuntu proper.

Just my $0.02 USD

---

### Post by acelin on 2008-04-28
> **aysiu said:**
> Ubuntu already does have Gnome by default, and it already makes it so knowledgeable users can choose KDE (by downloading Kubuntu... or by doing a command-line install and then picking what components they want to add).

No But have it where both packages are installed, so the best of Gnome and K applications are on the same OS- You just choose one or the other on startup. That way devs are more likely to work on both-

---

### Post by samwyse on 2008-04-28
> **TeraDyne said:**
> For the record, This just isn't about proprietary drivers. Here's the launchpad bug report: [https://bugs.launchpad.net/ubuntu/+bug/38915](https://bugs.launchpad.net/ubuntu/+bug/38915)
Seems like a different problem than mine. Using the free drivers logout worked everytime. Using the restricted drivers KDM dies, but I can log in to the terminal and restart KDM. Reboot and Shutdown work normally. Everything worked fine in Gutsy and the versions before it, this is Hardy bug.

The desktop speed is visibly slower using the free drivers thus I choose to use the restricted ones and live with the new log out weirdness. I'm going to file a bug report later.

---

### Post by maniacmusician on 2008-04-28
> **acelin said:**
> No But have it where both packages are installed, so the best of Gnome and K applications are on the same OS- You just choose one or the other on startup. That way devs are more likely to work on both-

geh...please learn a little more about the way software development, especially OSS development, and even more especially Ubuntu development works before making comments like these. 

Also, Gnome and KDE applications aren't restricted to their respective DEs, so they can be mixed and used together anyways.

Ubuntu has chosen to use Gnome as its main platform, and that's not going to change. That's why Kubuntu is created and maintained as a community distribution, though of course with generous support from canonical.

---

### Post by doorknob60 on 2008-04-29
Hmm, So I'm not the only one with the Kubuntu Hardy KDM nVidia bug...Maybe I'll just use GDM until it gets fixed or something.

---

### Post by Micool on 2008-05-06
> **samwyse said:**
> I expected a complain of something less trivial. I didn't know they were supposed to be enabled. How about KDM dying everytime logging out using the restriced NVidia drivers?

It needs a sudo /etc/init.d/kdm restart to get it back. Luckily I don't need to log out often.

Cool, I found some one who has the same problems than me with the proprietary drivers: KDM and KDE dying at firts start, restarting X or KDM is needed...
My video card is a nvidia 8800 GTX... proprietary drivers with 7.10 worked very well.

---

### Post by pluviosity on 2008-05-06
Kubuntu Hardy performed terribly on my computer...had to go back to Gutsy.  Hardy took much longer to boot, was very laggy, would maximize windows randomly when I tried to move them, crashed on me a couple times, ran much hotter (my fan was a lot louder than on Gutsy), and would hang on shutdown or reboot as has been previously mentioned.  I tried using GDM for a while to see if that was the issue, but I still had some issues (especially the crashing).  I guess this is due to my ATI card...at least I still have Gutsy :)

---

### Post by vishzilla on 2008-05-06
With each release i am tempted to try Kubuntu but it hard(l)y impresses me. It looks uncooked all the time. On the other hand, OpenSuse are doing a good job with KDE4. Kubuntu (Canonical) should learn from them.

---

### Post by 23meg on 2008-05-06
I feel a strong urge to interpret this thread as the barometer of the amount of sanity and common sense that's left in these forums.

I mean, if aysiu, of all people, can reach the conclusion that "Kubuntu has been neglected in Hardy" because his sources.list didn't have Universe and Multiverse enabled, apparently without doing a search or investigating the matter otherwise, all the lack of reason, logic and common sense and understanding that has dominated this place suddenly becomes much more understandable.

Temperature must be dropping rapidly in hell, and it will probably freeze in a few hours unless aysiu just bursts out "Come on, I was kidding!"..

---

### Post by awakatanka on 2008-05-07
> **23meg said:**
> I feel a strong urge to interpret this thread as the barometer of the amount of sanity and common sense that's left in these forums.

I mean, if aysiu, of all people, can reach the conclusion that "Kubuntu has been neglected in Hardy" because his sources.list didn't have Universe and Multiverse enabled, apparently without doing a search or investigating the matter otherwise, all the lack of reason, logic and common sense and understanding that has dominated this place suddenly becomes much more understandable.

Temperature must be dropping rapidly in hell, and it will probably freeze in a few hours unless aysiu just bursts out "Come on, I was kidding!"..
i expect that aysiu has done te research we all been used from him

---

### Post by koenn on 2008-05-07
> **awakatanka said:**
> i expect that aysiu has done te research we all been used from him
post #1 doesn't show any indication of research, just a mention of 2 community repo's not enabled by thefault, two questions without answers, and a conclusion :
> I know people tend to think Kubuntu gets the short end of the stick in development, but **this time it's really happened**

I think 23meg has a point.

---

### Post by Half-Left on 2008-05-07
I just dont understand why they dont just leave KDE as default look like Slackware does and just package it, then just make the Ubuntu UI tools Qt for KDE.

Is it really that much work, I mean KDE dont have a ton of devs for KDE4 anyway.

---

### Post by aysiu on 2008-05-07
Before people slam me for not doing my research, I haven't heard any evidence to the contrary of what I've said.

* Ubuntu has extra repos enabled by default and Kubuntu does not.

* Ubuntu has Software Sources in the menus, and Kubuntu does not.

Does anyone want to deny these observations as not being grounded in fact?

---

### Post by Half-Left on 2008-05-07
> **aysiu said:**
> Before people slam me for not doing my research, I haven't heard any contentions to the contrary of what I've said.

Ubuntu has extra repos enabled by default and Kubuntu does not.

Ubuntu has Software Sources in the menus, and Kubuntu does not.

Does anyone want to deny these observations as not being grounded in fact?

I really dont think those two points really qualify as "neglected" in my view but at the same time other distros do neglect other DE based on how centric they are to one an other. SUSE has neglected GNOME for years, it's only the last few releases where GNOME has got alot better integration with it's services like YaST.

---

### Post by koenn on 2008-05-07
> **aysiu said:**
> Before people slam me for not doing my research, I haven't heard any evidence to the contrary of what I've said.

* Ubuntu has extra repos enabled by default and Kubuntu does not.

* Ubuntu has Software Sources in the menus, and Kubuntu does not.

Does anyone want to deny these observations as not being grounded in fact?
I can't deny or conform those observations; I didn't check, and I'm not planning to. 

My reference to lack of research was clearly in reply to awakatanka's "i expect that aysiu has done te research". You yourself call it, more adequately, _observations._

Aside from that, noticing a couple of missing GUI elements in Kubuntu and concluding that "Kubuntu neglected : this time it's really happened" is jumping to conclusions, and i must say it sounded like flame-bait the first time I read it.

---

### Post by aysiu on 2008-05-07
> **koenn said:**
> 
Aside from that, noticing a couple of missing GUI elements in Kubuntu and concluding that "Kubuntu neglected : this time it's really happened" is jumping to conclusions, and i must say it sounded like flame-bait the first time I read it. Well, that's where I disagree with you. At this point in Ubuntu's development, most of the improvements users notice are just a couple of GUI elements. And actually the enabling of extra repositories by default is not a GUI element at all. It's about having sensible defaults that allow users to immediately have more software available for installation instead of having to jump through hoops to get easily installable software.

And I don't think saying Kubuntu is neglected is flame-bait. I said it's neglected, and it clearly is. I didn't say Kubuntu sucks or is unusable. I didn't say Ubuntu developers want Kubuntu to fail or hate Kubuntu. I just said it's neglected.

---

### Post by ubuntu-freak on 2008-05-07
Multiverse and Universe should be enabled by default in ALL Ubuntu varients, as Ubuntu is Ubuntu - no matter how it's dressed up. I'd have to agree with those who say GUI differences and certain software sources not being enabled by default, does not equate to Kubuntu being neglected however, as the decision is down to the Kubuntu devs themselves.
 
Perhaps new users, starting their Ubuntu journey with Kubuntu may feel neglected. I was completely unaware that Multiverse and Universe were not enabled by default in Kubuntu  (are they enabled in Xubuntu?) and had to update and revise my how-to accordingly. It was also an oversight on my part though.
 
Nathan

---

### Post by koenn on 2008-05-07
> **reassuringlyoffensive said:**
> Multiverse and Universe should be enabled by default in ALL Ubuntu varients, as Ubuntu is Ubuntu - no matter how it's dressed up. I'd have to agree with those who say GUI differences and certain software sources not being enabled by default, does not equate to Kubuntu being neglected however, as the decision is down to the Kubuntu devs themselves.

Agreed.
 If I remember well, Universe and Multiverse were nor enabled by default in Dapper either, because they're not official, community mainteined repos. Maube the ubuntu devs considered that a sane default. Or maybe it's a bug. Or an oversight. 
There's a bug report on launchpad with comments that suggested that Multiverse and Universe are added to sources by default only if an internet connection was detected during the initial setup - also a sane decision cause without internet access, one can only use the repository on the install CD. 

If number of bugs is an indication of neglect, all ubuntu flavours can be considered neglected.

---

### Post by aysiu on 2008-05-07
> **koenn said:**
> 
There's a bug report on launchpad with comments that suggested that Multiverse and Universe are added to sources by default only if an internet connection was detected during the initial setup - also a sane decision cause without internet access, one can only use the repository on the install CD.  I haven't confirmed this with my own testing, but based on some of the sources.list files I've seen from some new users without working internet connections, it appears Ubuntu comments out all sources except for the CD if you don't have a connection during installation. Maybe I'm wrong about that, though.

---

### Post by PartisanEntity on 2008-05-07
> **aysiu said:**
> I haven't confirmed this with my own testing, but based on some of the sources.list files I've seen from some new users without working internet connections, it appears Ubuntu comments out all sources except for the CD if you don't have a connection during installation. Maybe I'm wrong about that, though.

I don't think that's correct, I installed Hardy on my Macbook without connecting it to the router (nor was wifi working due to broadcom) and did not have to turn on any repos post-installation.

---

### Post by aysiu on 2008-05-07
> **PartisanEntity said:**
> I don't think that's correct, I installed Hardy on my Macbook without connecting it to the router (nor was wifi working due to broadcom) and did not have to turn on any repos post-installation.
Hm. So who are these people who have all their sources commented out that I sometimes see in the support forums?

**Edit**: I just did a search on support threads with empty sources.lists, and most appear to have been from 2006, around the time that Breezy was in use:
[so lost with installing any apps on kubuntu](http://ubuntuforums.org/showthread.php?p=1139373#post1139373)
[how install extra programs with adept?](http://ubuntuforums.org/showthread.php?p=820303#post820303)
[installing programs like thunderbird](http://ubuntuforums.org/showthread.php?p=678775#post678775)

Maybe that's the way it worked back then and Ubuntu changed it for later releases?

---

### Post by FuturePilot on 2008-05-07
> **aysiu said:**
> I haven't confirmed this with my own testing, but based on some of the sources.list files I've seen from some new users without working internet connections, it appears Ubuntu comments out all sources except for the CD if you don't have a connection during installation. Maybe I'm wrong about that, though.

It used to in Gutsy. After Gutsy was released there was tons of threads where people couldn't find various packages because the sources.list was commented out by the installer. I think that has been fixed in Hardy though.

---

### Post by ubuntu-freak on 2008-05-07
> **aysiu said:**
> I haven't confirmed this with my own testing, but based on some of the sources.list files I've seen from some new users without working internet connections, it appears Ubuntu comments out all sources except for the CD if you don't have a connection during installation. Maybe I'm wrong about that, though.

 
That happened to me last month. I think it must happen when it detects a connection during installation, but then the connection fails and it can't verify the sources. My connection failed and everything but the CD-ROM source was commented out. 
 
Nathan

---

### Post by aysiu on 2008-05-07
> **FuturePilot said:**
> It used to in Gutsy. After Gutsy was released there was tons of threads where people couldn't find various packages because the sources.list was commented out by the installer. I think that has been fixed in Hardy though.
Ah, that makes sense.

---

### Post by koenn on 2008-05-07
I just finished installing Kubuntu 8.04 (Alternate CD).
Universe an Multiverse appear in the sources.list as normal, not commented.
Repos can be managed from Adept: menu Adept : Manage Repositories. Universe and Multiverse are enabled bu default. 
I'm not familiar with KDE /Kubuntu so I don't know if Adept is the expected location for enabling/disabling repos, but it sure looks fine to me.

---

### Post by aysiu on 2008-05-07
> **koenn said:**
> I just finished installing Kubuntu 8.04 (Alternate CD).
Universe an Multiverse appear in the sources.list as normal, not commented.
Repos can be managed from Adept: menu Adept : Manage Repositories. Universe and Multiverse are enabled bu default. 
I'm not familiar with KDE /Kubuntu so I don't know if Adept is the expected location for enabling/disabling repos, but it sure looks fine to me.
I haven't tried the Alternate CD, but they're commented out definitely on the Desktop CD - that I did try.

---

### Post by ubuntu-freak on 2008-05-07
> **aysiu said:**
> I haven't tried the Alternate CD, but they're commented out definitely on the Desktop CD - that I did try.

 
Perhaps the devs saw this thread.
 
Nathan

---

### Post by koenn on 2008-05-07
> **reassuringlyoffensive said:**
> Perhaps the devs saw this thread.
Nathan ..., fixed the bugs, created a new .iso without a version number change, and published it with no mention of bug fixes since previous release. Hm. Sounds unlikely.

---

### Post by koenn on 2008-05-07
> **aysiu said:**
> I haven't tried the Alternate CD, but they're commented out definitely on the Desktop CD - that I did try.
I assumed you used the Desktop CD, that's why i chose Alternate : I was working on the assumption that your observations were correct, so if those flaws were not present in the alternate CD, that would suggest a bug / oversight in the Desktop CD, rather than neglect. 
So, if you can reproduce an install with those repos missing (possibly with|without internet during setup), you can make a constructive contribution like report a bug or ask the devs whether this was a deliberate decision, and their rationale.

---

### Post by aysiu on 2008-05-07
> **koenn said:**
> I assumed you used the Desktop CD, that's why i chose Alternate : I was working on the assumption that your observations were correct, so if those flaws were not present in the alternate CD, that would suggest a bug / oversight in the Desktop CD, rather than neglect. 
So, if you can reproduce an install with those repos missing (possibly with|without internet during setup), you can make a constructive contribution like report a bug or ask the devs whether this was a deliberate decision, and their rationale.
Is that the kind of bug they'd fix for an already-released distro, or would this be for fixing in Intrepid Ibex?

---

### Post by ubuntu-freak on 2008-05-07
> **koenn said:**
> ..., fixed the bugs, created a new .iso without a version number change, and published it with no mention of bug fixes since previous release. Hm. Sounds unlikely.

 
What do you mean? It's not a bug at all.
 
Nathan
 
Edit: Unless the Live CD still has those sources disabled, sorry.

---

### Post by koenn on 2008-05-07
> **aysiu said:**
> Is that the kind of bug they'd fix for an already-released distro, or would this be for fixing in Intrepid Ibex?
I'm not a dev or a packager so I don't really know. It's not critical (packahe management is functional, Main is enabled, universe and multiverse are community maintained so maybe not a high priority,there's a workaround for adding other repos, e.g. editing sources.list, ...) so my guess is they mark it as "workaround exists" and fix it in the next release, unless there's an other reason to release an update for apt (or whatever package sources.list comes with) and they add a fix there (although possibly sources.list is created during install rather than delivered as part of a package, and then fixing it in the next release is even more likely)

---

### Post by aysiu on 2008-05-07
This may sound dumb, but I can't find the "report a bug" button for Kubuntu on Launchpad. Can someone post a link?

---

### Post by koenn on 2008-05-07
I can't even find Kubuntu on Launchpad.
Maybe try [https://launchpad.net/bugs/+filebug](https://launchpad.net/bugs/+filebug)
There's no Kubuntu in the list of distributions (or I didn't see it) but there are some kubuntu items under "projects". maybe check those ?

---

### Post by aysiu on 2008-05-07
> **koenn said:**
> I can't even find Kubuntu on Launchpad.
Maybe try [https://launchpad.net/bugs/+filebug](https://launchpad.net/bugs/+filebug)
There's no Kubuntu in the list of distributions (or I didn't see it) but there are some kubuntu items under "projects". maybe check those ?
I found Kubuntu on Launchpad, just not a way to file a new bug:
[https://launchpad.net/~kubuntu-team/+packagebugs](https://launchpad.net/~kubuntu-team/+packagebugs)

---

### Post by koenn on 2008-05-07
If you look at the kubuntu team's bugs, you can tell/guess that they are filed as ubuntu bugs;
> [https://bugs.launchpad.net/~kubuntu-team/+packagebugs-search?field](https://bugs.launchpad.net/~kubuntu-team/+packagebugs-search?field).**distribution=ubuntu**&field.sourcepackagename=**kubuntu-default-settings**&search=Search I suppose they'll get assigned to or picked up by the Kubuntu Team on Launchpad. 
[https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

edit: maybe you could file a bug against "kubuntu-desktop" in stead.

---

### Post by 23meg on 2008-05-07
> **aysiu]And I don't think saying Kubuntu is neglected is flame-bait. I said it's neglected, and it clearly is.[/QUOTE]

While it isn't flame-bait by definition, because it was posted by an established forum member who would be the last person to make a post with such an intention, it also isn't necessarily true. It could just as well have been (and still may be) a broken ISO, an error on your part, or something related to changing conditions (network?) gone awry during installation. It isn't necessarily a sign of Kubuntu being neglected. What I was surprised about was that you rushed to that conclusion, without pointing to any likely evidence other than your own singular experience, in the very first post. People have had issues of similar gravity with Ubuntu Hardy too said:**
> Is that the kind of bug they'd fix for an already-released distro, or would this be for fixing in Intrepid Ibex?

If it's a genuine bug that affects everyone, or a large percentage of users (which isn't the case, as far as I can deduce from the non-existent bug reports so far), it would be fixed in the stable release(s). 

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

[QUOTE=aysiu]I found Kubuntu on Launchpad, just not a way to file a new bug:
[https://launchpad.net/~kubuntu-team/+packagebugs](https://launchpad.net/~kubuntu-team/+packagebugs)[/QUOTE]

Kubuntu draws all its packages from the same archive as Ubuntu, so bugs are kept in the same place and way as well. 

software-properties-kde is part of the software-properties source package, so bug reports for it would go [here]("https://launchpad.net/ubuntu/+source/software-properties/+bugs"), and the other bug should probably be filed in [dpkg]("https://bugs.launchpad.net/ubuntu/+source/dpkg/"). However, you may want to post support requests at [answers.launchpad.net]("http://answers.launchpad.net") (make sure you file it in the respective packages) before filing a bug.

---

