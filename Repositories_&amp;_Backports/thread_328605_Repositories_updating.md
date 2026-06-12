---
title: "Repositories updating"
date: 2006-12-31
forum: Repositories &amp; Backports
---

### Post by evilc on 2006-12-31
Could someone tell me why many of the programs (packets) in edgy are out of date. I have seen the comments they only have stable packets but to me that don't ring true, for example (off the top of my head) Gimp and Firefox both have been updated but not in the repo's. I know the latest Firefox and others have been updated in the Feisty reps?    Sure you can d/l the latest versions and install into a folder of your choice usually opt, which then gives you 2 versions which is a waste of space. I would have thought as Feisty is still in development, any updates should be in Dapper/Edgy Repo's first as they are supposed to be stable.

---

### Post by 23meg on 2006-12-31
Packages in the stable releases of Ubuntu only get security updates. > any updates should be in Dapper/Edgy Repo's first as they are supposed to be stable.That's exactly why regular upstream updates *don't* happen there: they're stable. Feature updates typically bring unstability.

---

### Post by evilc on 2006-12-31
So what you are saying by using Dapper/Edgy you only use updates via update manager, don't worry about programs like FireFox and probably others that have been updated because of security reasons?  If that's the case what's the point of Synaptic other than d/l programs deemed stable by Ubuntu? When programs update because of security they should be added within days of availability, not just put into the next Ubuntu unstable release version.

---

### Post by DJ_Peng on 2006-12-31
This is pat of why I switched and got Firefox straight from Mozilla within two days of switching to Ubuntu from Windows. As a member of their testing community I was used to getting nightly updates (or seemingly any extension) but couldn't with the version of Firefox that shipped with Ubuntu Edgy. For my money if I think a program will get updated (lke Wine or OpenOffice) I'm not even wanting to bother with what comes from Edgy's repositories. Of course I think this is a grave disservice to their users to keep them from updates liek this. Maybe I should have gone with Dapper LTS instead of Edgy?

---

### Post by hikaricore on 2006-12-31
> **DJ_Peng said:**
> Maybe I should have gone with Dapper LTS instead of Edgy?

Dapper's software is pretty much version set in stone unless there is a bugfix or security update that is absolutely needed.  This is the only viable way to provide long term support.  If they were to update every package possible to the most bleeding edge versions it would rendered stability a useless goal.  This is why many members of the community and even some software development groups provide their own repositories for updated versions of software for those of us that can't live without the latest and greatest features.

---

### Post by DJ_Peng on 2006-12-31
Thanks, hikaricore, that's what I thought. I guess those of us who want the updates (security and otherwise) faster will have to get more of our software from the source instead of from the repository. I do understand that merging every upate into the repository would be a massive undertaking, but in the case of Firefox I'm pretty sure that the 2.0.1 security and stability update didn't appear in the repository for a couple of weeks after Mozilla released it and started pushing it out to the rest of their users via Automatic Updates. There's got to be a tradeoff that will benefit everyone, I just haven't come up with it yet.

And evilc, I'm sorry about hijacking your thread.

---

### Post by evilc on 2006-12-31
[quote=DJ_Peng;1952682  evilc, I'm sorry about hijacking your thread.[/quote]

 No problem we are both thinking along the same lines.  With regards to getting programs from source in the case of say firefox, gimp and open office, the problem I have seen is you end up with 2 versions on computer. Many would say well it's only 20mg or so but when you add them up you could be talking 100's plus the possible conflict problem that can occur.

---

### Post by DJ_Peng on 2006-12-31
Yeah, right now I'm trying to get OpenOffice 2.1 working properly with the right icons. I haven't even thought about needing to do that with Gimp yet. Although I do tend to do most of my image work in Fireworks via Wine. I need to break that habit one of these days. As it is I found out that dome of my HTM(L) files were still tied to the "Firefox Web Browser" rather than the Firefox 2.0 (now Bon Echo 2.0.2pre) that I've set as my default browser. I hate to say this, but this is one area where Microsquish has Ubuntu beat, in being able to use newer versions of programs without making us jump through all these damned hoops. Maybe Feisty will fix some of that once it comes out, although truth be told I'm not looking forward to that upgrade..

---

### Post by hikaricore on 2006-12-31
> **DJ_Peng said:**
> I hate to say this, but this is one area where Microsquish has Ubuntu beat, in being able to use newer versions of programs without making us jump through all these damned hoops. Maybe Feisty will fix some of that once it comes out, although truth be told I'm not looking forward to that upgrade..

That's because there's a standard method of installation for windows software installation.  There are more than several hundred different distros of linux using atleast 25 different packaging methods and not all of them are cross compatible.  The solution would fall more on software development groups working on releasing ubuntu or at the very least debian packages of their software.  This is still alot of work as many of them already build half a dozen other packages for various cpu types and system bases.  Honestly it's just not feisable under most circumstances, but if YOU yourself are willing to donate your time and can handle building from source for several different ubuntu distributions/cpu types, contacting the software developers with your packaged builds would be a step in the right direction.

---

### Post by Sef on 2007-01-01
> That's because there's a standard method of installation for windows software installation. There are more than several hundred different distros of linux using atleast 25 different packaging methods and not all of them are cross compatible.

There is [autopackage]("http://autopackage.org") which is Linux platform free.   It does have its limitations, but it is a good start.

---

### Post by DJ_Peng on 2007-01-01
> **hikaricore said:**
> Honestly it's just not feisable under most circumstances, but if YOU yourself are willing to donate your time and can handle building from source for several different ubuntu distributions/cpu types

I may be too much of a noob to do much there. I hardly know what to do to get software installed on my own comp sometimes. But one of these days, who knows?

---

### Post by 23meg on 2007-01-01
[QUOTE=evilc]So what you are saying by using Dapper/Edgy you only use updates via update manager, don't worry about programs like FireFox and probably others that have been updated because of security reasons?[/QUOTE]Assuming Application is part of the Main component of Ubuntu, it typically goes like this: 

If you're using Application version 2.0 and by the time 2.1 comes out, the security fixes that have gone into Application 2.1 will have already been made available through the official Ubuntu repositories, and if a few haven't been for some reason, they will as soon as the release is out. But if there are any feature updates, those will be left out. So even if your Application reports itself as version 2.0 in its "About" window, if you've updated it regularly, it will have all the security fixes that Application 2.1 has. You can check and verify this by looking at the package version with apt-cache or Synaptic (it will be something like 2.0-ubuntu3) and reading the changelogs at [http://packages.ubuntu.com](http://packages.ubuntu.com) .

---

### Post by 23meg on 2007-01-01
[QUOTE=hikaricore]Dapper's software is pretty much version set in stone unless there is a bugfix or security update that is absolutely needed. This is the only viable way to provide long term support.[/QUOTE]Not just for long term support, but for support of all sorts, and for stability in general, this is feasible. This is the case for every release of Ubuntu, not just LTS releases.[QUOTE=evilc]When programs update because of security they should be added within days of availability, [/QUOTE]They already are. 
[QUOTE=evilc]not just put into the next Ubuntu unstable release version.[/QUOTE]
That's not the case; it's never been. But it can be easier to do a bug fix in the development version and then move it to the stable release, so they may show up in the development version shortly beforehand.

---

### Post by DJ_Peng on 2007-01-02
This may be a little OT, but considering the discussion in this thread I thought I'd share it here. I saw an article on Linux-Watch that should make the installation problems easier: *[Linux software installation to improve]("http://www.linux-watch.com/news/NS4586903228.html")*

---

### Post by evilc on 2007-01-02
> **DJ_Peng said:**
> This may be a little OT, but considering the discussion in this thread I thought I'd share it here. I saw an article on Linux-Watch that should make the installation problems easier: *[Linux software installation to improve]("http://www.linux-watch.com/news/NS4586903228.html")*

 Now that look's like a move in the right direction, from what I have seen there are too many variations for installing.

---

