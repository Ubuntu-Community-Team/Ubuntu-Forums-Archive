---
title: "What's the rationale that Ubuntu now wants to install everything in a snap package?"
date: 2020-04-29
forum: The Cafe
---

### Post by kevdog on 2020-04-29
Snaps -- argh. Love them or hate them.

I'm aware Ubuntu's been trending toward installing everything in the form of snap packages.
What's behind this philosophy?

---

### Post by rbmorse on 2020-04-29
Makes life easier for distribution maintainers.  Anything inside a snap is someone else's problem.

This is not a criticism.  I fully understand they need to put the responsibility for maintaining application packages back on the developers.

---

### Post by Tadaen_Sylvermane on 2020-04-29
I'm not sure I'm educated enough to answer this question. But from my perspective I'd guess they want more software available. Universal packaging does just that. Since the dependencies are self contained it also reduces the work of distro maintainers as people can package their own snaps. The downside though is that these self contained dependencies could very easily be very out of date, and have holes in them. I'm not sure if there is a way to check that type of thing.

I prefer normal repositories and the current method of having everything relying on a single library. Find a problem, update the library, problem solved for every app that relies on that library. You lose that with snaps. Regrettably I have to use them to keep the newest version of LXD. I've debated going back to Debian, maybe CentOS and using a straight LXC simply so I can avoid snaps, but I'm fairly lazy. One of these days I'll probably attack it. For now I don't care too much. I think ultimately though that universal packages are the future either way. You see people asking for "big name" software on linux regularly. That is the only way it will happen. With so many different distros and ways of doing things no one can possibly package for every single variation.

---

### Post by EuclideanCoffee on 2020-04-29
> 
[COLOR=#000000]Makes life easier for distribution maintainers. Anything inside a snap is someone else's problem.

[/COLOR]
Absolutely this.

This makes trusting the supply chain less obvious however. :(

---

### Post by kevdog on 2020-04-29
Snaps though seem to run slower than their non-snap counterparts.  

Idk -- maybe its just me but one of the things I like about linux was I kind of "knew" what was running on my system.  I find this with Arch Linux particularly where I had the choice what base packaged I wanted to add to make the arch iso.  With snaps -- it is kind of a black box.  I'm not sure its comparable but I run a lot of docker images which use Ubuntu as a base.  In many cases the when I exec into the container, I see that although the base is running Ubuntu 18.04, the system level packages haven't been updated in over 6 months -- sometimes longer.  I hypothesizing here, but that doesn't seem to me very good security practice.  I wonder if snaps are very much the same in this regard.

---

### Post by DuckHook on 2020-04-29
> **rbmorse said:**
> Makes life easier for distribution maintainers.  Anything inside a snap is someone else's problem.

This is not a criticism.  I fully understand they need to put the responsibility for maintaining application packages back on the developers.
This is one of the reasons. But also:

Pros:

[LIST]
[*]The ability to run current apps instead of stuff that may be so old as to be nearly obsolete. Example: in Xenial, LibreOffice was so broken as to be almost unusable. It wouldn't save files over NFS shares without a config hack. The old workaround was adding PPAs—likely the single worst Ubuntu security hole I can think of.
[*]Allow the running of older apps that may break on current system libraries. Example: in Trusty, GNUcash couldn't open files created in Precise.
[*]Limited sandboxing of apps for higher security.
[/LIST]
Cons:

[LIST]
[*]Way more bloat and cruft.
[*]Succumbing to ridiculous feature creep. As I discovered recently, prior to Focal, something as simple as the calculator was hived off to a snap. :roll:
[*]Invites shirking of responsibility. In Focal, LibreOffice help is borked, whereas the snap version works. The devs have known about this for months, but still no fix in sight.
[*]Loss of control. The snap version of LXD is harder to configure than the repo version. It sometimes involves arcane measures to work around its snap confinement whereas the repo version just works.
[/LIST]

---

### Post by grahammechanical on 2020-04-29
Sandboxing of applications. That is the benefit to the user. See a comparison between Appimage, Flatpack & Snap. 

[https://www.ostechnix.com/linux-package-managers-compared-appimage-vs-snap-vs-flatpak/](https://www.ostechnix.com/linux-package-managers-compared-appimage-vs-snap-vs-flatpak/)

Now investigate why there is a need for the X-Server to be replaced. Notice the potential for security vulnerabilities. Then do the same for Redhat's RPM package format and Debian's deb package format. 

Motivation, as I see it, is an application that can be installed and run on any Linux distribution and on any version of that distribution; The developer can update the application and get the update out to the user without the delay caused by a distribution's developer team having to audit the source code before allowing it into the distribution's repositories: Applications can be sandboxed to severely limit access to the system.

Regards

---

### Post by Frogs Hair on 2020-04-29
> The developer can update the application and get the update out to the  user without the delay caused by a distribution's developer team having  to audit the source code before allowing it into the distribution's  repositories.

Ideally, this is great, but my experience with _some_ snaps reveals that this doesn't happen. Like many projects people move on and don't follow through and maintain them.

---

### Post by DuckHook on 2020-04-29
> **grahammechanical said:**
> …The developer can update the application and get the update out to the user without the delay caused by a distribution's developer team having to audit the source code before allowing it into the distribution's repositories…
But this just trades one vulnerability for another: the idea behind the repos was that stuff there had been vetted and therefore earned a higher level of trust. Yes, this meant that they couldn't be brand-spanking-new, but the principle was that trading older apps for security and stability was a worthwhile tradeoff. Mainlining apps straight into the bloodstream from each developer is what has caused so much security trouble in the proprietary sphere.

Don't get me wrong: I'm not naysaying Snaps. There's clearly a place for many apps to be packaged as snaps. After all, I'm the guy who usually goes on ad nauseum about sandboxing. But there's also a point at which it turns into silliness. Is Ubuntu heading towards a future where everything except the kernel is a Snap?

Thanks for the link BTW. Very interesting article.

---

### Post by Hwæt on 2020-05-01
IIRC Canonical maintains a lion's share of Debian packages. Migrating these over to snaps helps reduce the weirdness you get when testing with different system configurations, update stages, etc. So it drives down QA costs.

It's a respectable decision, despite some of the issues with snaps. Realistically snap performance is varied in my experience. I recall having issues with one particular snap package, but the unofficial discord snap ran like a dream.

---

### Post by bvz on 2020-05-10
I am just now starting with snaps. Prior to this I wound up "rolling my own" app management system (not package system) to be able to run multiple otherwise incompatible versions of apps on my Manjaro system.

I very much look forward to the concept of apps being self contained. The number of library conflicts and missing versions that kept me spending all of my time managing app installs vs. doing real work was getting EXTREMELY irritating.

Prior to snaps, my only experience with this kind of run anywhere packages in Linux was AppImage. It was amazing. I could have multiple versions of the same app on my system. The amount of time I spent managing these apps is measured in minutes vs. hours or more for other apps. Getting the latest version of an application was always immediate (sometimes fixing significant bugs in previous versions).

Snaps, so far, have been a bit of a letdown. The biggest issues I have with them is that 

a) I can't seem to force multiple versions to co-exist at the same time. I have to look into the parallel branch option a bit more, but at first glance the auto-updating is going to be an issue for me. I like to have my apps updated - but with parallel versions so that I can revert back not just one version, but multiple - especially in cases where I don't use an app all that much and it may update 10 times between runs - meaning a single rollback is not adequate (assuming I understand this mechanism correctly).

b) (and this is the deal breaker for me), I have to now "rewire" my entire network topology in order for my snap applications to "see" my files. The level of absurdity in this is something I find hard to believe. I have mounts that live outside of the few "blessed" mount points that are hard-coded into the snap system. This means that I cannot actually use the applications that I have installed via snap. I have, apparently, two options - either change the structure of my entire network (for every machine on the network including my linux boxes and MacOS machines) and rewrite a ton of python code that makes up my long running pipeline to keep a few snap applications happy, or forgo using snaps alltogether in favor of either AppImage (my preferred system, but it lacks the breadth of applications) or flatpak (something I am trying out now, but it suffers from some of the same deficiencies), or to go back to my own application management system.

It seems that if these new package management systems are going to become the standard then they really have to figure out a way to handle the sandboxing in a way that actually allows end users to configure their machines in a way that isn't limited to what the snap team thinks works for them.

Ok, I'm off to try to figure out how to poke a hole into the flatpak sandbox so I can actually do some work.

---

### Post by Perfect Storm on 2020-05-11
On eOS the flatpack is supported by default. Tried it and left it. It takes too much time for the apps to start up.

---

### Post by Shibblet on 2020-05-11
Sometimes it depends on how the Snap package is maintained vs. the PPA.

Take MakeMKV for example:  The Snap package will not allow me to change the directory to where I want the MKV date to go.  The PPA works perfectly.

Is this a Snap problem?  Or is this how the system manages the Snap that is the problem?  No one seems to know.

---

### Post by DuckHook on 2020-05-11
> **Shibblet said:**
> Sometimes it depends on how the Snap package is maintained vs. the PPA.

Take MakeMKV for example:  The Snap package will not allow me to change the directory to where I want the MKV date to go.  The PPA works perfectly.

Is this a Snap problem?  Or is this how the system manages the Snap that is the problem?  No one seems to know.
Snaps are supposed to be a form of sandboxing—along with its other "benefits"—so it won't allow you unfettered access to your whole directory tree unless the dev initially packaged it that way. Personally, I'm somewhat comforted by the fact that it has such sandboxing, though I acknowledge that it's sometimes a pain.

---

### Post by Erik1984 on 2020-05-11
> **DuckHook said:**
> Snaps are supposed to be a form of sandboxing—along with its other "benefits"—so it won't allow you unfettered access to your whole directory tree unless the dev initially packaged it that way. Personally, I'm somewhat comforted by the fact that it has such sandboxing, though I acknowledge that it's sometimes a pain.

Yes that's a nice feature of snaps but can be annoying depending on your setup. For example I was trying Clementine (music player) as snap. It works but my music is not in ~/Music. Well it is there but as symlink to another directory outside ~. So it could not access my music unless I put the snap in development mode, but that defeats the purpose.  But in general I agree it's a good thing. Especially since you can just a flip a switch (literally in the UI or through quite intuitive command) to disable access to all folders except those specific to the snap.

---

### Post by DuckHook on 2020-05-11
> **bvz said:**
> &#8230;It seems that if these new package management systems are going to become the standard then they really have to figure out a way to handle the sandboxing in a way that actually allows end users to configure their machines in a way that isn't limited to what the snap team thinks works for them.

Ok, I'm off to try to figure out how to poke a hole into the flatpak sandbox so I can actually do some work.
Consider the technique in the link in my sig: Sandboxing Apps with LXD

It might meet some of your requirements, but be forewarned that it might create intractable problems of its own.

---

### Post by EuclideanCoffee on 2020-05-11
I've warmed up to snaps, but I think the team tackling the problem are very ambitious. I foresee the platform either succeeding or failing before 22.04 LTS is released.

God speed, snapd team.

---

### Post by TheFu on 2020-05-11
About 80% of snaps that I&#8217;ve installed don't work.  They fail to run.

When they install, the size is usually just under 1G for a 50MB program due to all the dependencies. We used to send people on travel using cheap chromebooks with 16G of storage and 2G of RAM running Ubuntu.  With snaps, that idea is completely impossible.  Storage gets full and running 2 apps uses all the RAM.

The ones that do run, block access to our network storage and /tmp/.  it is as though the people behind the design of snaps came from designing apps for single-user cell phones, not Unix workstations on a corporate network.

What seems to happen is that snaps are created and forgotten by the snap package creators. Now we have another place to check for updates, but this time, there aren't any PPA versions, so Canonical holds the keys and sets the rules for what is and is not allowed.  Surely, nothing bad could ever happen when only one company has the control.

---

### Post by DuckHook on 2020-05-11
> **TheFu said:**
> About 80% of snaps that I&#8217;ve installed don't work.  They fail to run.
Not my experience, but then, I haven't installed that many.
> When they install, the size is usually just under 1G for a 50MB program due to all the dependencies. We used to send people on travel using cheap chromebooks with 16G of storage and 2G of RAM running Ubuntu.  With snaps, that idea is completely impossible.  Storage gets full and running 2 apps uses all the RAM.
Agreed. Absurd bloat is one of its biggest drawbacks
> The ones that do run, block access to our network storage and /tmp/.  it is as though the people behind the design of snaps came from designing apps for single-user cell phones, not Unix workstations on a corporate network.
[LIST=1]
[*]It takes time to fine-tune these things and,
[*]To some extent, this assessment of poor design is true
[/LIST]
> What seems to happen is that snaps are created and forgotten by the snap package creators.
This is very true and already happening. But this sword has two edges&#8212;the reverse is also true. I use Telegram. The repo version is multiple versions behind; the snap version is right up to date. Users forced to use Zoom can only download one with proven security holes from the repos, but will have the most current one with far better security through the snap store.
> Now we have another place to check for updates,
Actually, the most irritating drawback here is that snaps will automatically update and *there's no way to turn this automated behaviour off*. As a guy who likes complete control of my system, this is a big drawback. It's almost a deal-breaker (but not quite).
> but this time, there aren't any PPA versions, so Canonical holds the keys and sets the rules for what is and is not allowed.  Surely, nothing bad could ever happen when only one company has the control.
&#8593;+1&#8593;

This may be my single biggest reservation about snaps. It's more than halfway to being a proprietary silo. If I wanted that, I would have gladly succumbed to the Apple siren a long time ago.

---

### Post by bvz on 2020-05-11
> **TheFu said:**
> About 80% of snaps that I’ve installed don't work.  They fail to run.

When they install, the size is usually just under 1G for a 50MB program due to all the dependencies. We used to send people on travel using cheap chromebooks with 16G of storage and 2G of RAM running Ubuntu.  With snaps, that idea is completely impossible.  Storage gets full and running 2 apps uses all the RAM.

The ones that do run, block access to our network storage and /tmp/.  it is as though the people behind the design of snaps came from designing apps for single-user cell phones, not Unix workstations on a corporate network.

What seems to happen is that snaps are created and forgotten by the snap package creators. Now we have another place to check for updates, but this time, there aren't any PPA versions, so Canonical holds the keys and sets the rules for what is and is not allowed.  Surely, nothing bad could ever happen when only one company has the control.

I am still very new to snaps and was excited to use them - only for that excitement to turn to disappointment when I realized I cannot actually open any of my files, or prevent automatic updates. 

Personally I don't care about the size of the snaps. For me the cost of additional SSD storage and RAM vs. the cost of managing conflicting packages is a completely easy tradeoff to make. That is just me though. No comments on your workflow - I fully understand your complaints.

The fact that snaps are forgotten by the creators does not make much sense to me. Snaps should be maintained by the software developers. That was supposed to be one of the big advantages. No more waiting for a distro to update its repos to the latest release of an app. Is it an issue that the developer has not actually released the snap, but rather that a third party is maintaining the snap?  That seems like it is a recipe for disaster. If snaps are going to work at all (and I am hopeful that they will - but they have a LONG way to go) then they are going to have to be both released by the original software authors AND not limited to a single snapcraft store - which isn't even properly curated it seems.

---

### Post by DuckHook on 2020-05-11
> **bvz said:**
> …The fact that snaps are forgotten by the creators does not make much sense to me. Snaps should be maintained by the software developers. That was supposed to be one of the big advantages. No more waiting for a distro to update its repos to the latest release of an app. Is it an issue that the developer has not actually released the snap, but rather that a third party is maintaining the snap?  That seems like it is a recipe for disaster. If snaps are going to work at all (and I am hopeful that they will - but they have a LONG way to go) then they are going to have to be both released by the original software authors AND not limited to a single snapcraft store - which isn't even properly curated it seems.
Snaps *are* maintained by their developers, not by the Canonical Ubuntu team. As already noted, this is a double-edged sword. If the developer is diligent and conscientious, the app will be more current and more secure than the traditional methodology of relying on the distro maintainers. If the developer stops maintaining the app, then it will be orphaned with all the downsides that come with such offloading.

Frankly, this was a predictable outcome. For a similar evolution, we have only to look at the Launchpad PPA experience: it too is filled with some PPAs that offer the most current versions of the most popular apps, and it is also filled with piles of dead PPAs that have gone unmaintained for years. Another double-edged sword. The difference is that PPAs rely on system libraries shared by your base install and if they required an older or newer library, they wouldn't function. They also sometimes broke dpkg and created dependency hell. Not least, they are notoriously insecure because they are installed with no sandboxing. Speaking personally, I would never install a PPA unless it is constrained within a VM or container of some kind.

Snaps have a high potential to be orphaned. But then, so does every app in the Linux-sphere (consider the once&#8209;great Amarok), so I suppose that everything needs to be assessed with realistic expectations.

---

### Post by EuclideanCoffee on 2020-05-11
I think what people aren't acknowledging is that you CAN have your own snap store with your own version control and snap management. You can also confine snaps differently. The control isn't totally gone, but you are given a default configuration via Ubuntu, which should work for the normal users.

---

### Post by DuckHook on 2020-05-11
> **EuclideanCoffee said:**
> I think what people aren't acknowledging is that you CAN have your own snap store with your own version control and snap management. You can also confine snaps differently. The control isn't totally gone, but you are given a default configuration via Ubuntu, which should work for the normal users.
Not to be argumentative, but the essential truth of this observation is mitigated by the following:

[LIST=1]
[*]Spinning up our own snap is not remotely a trivial exercise. As a parallel, it has been possible to spin up our own PPAs for years. Almost no end users do so. The processes in both cases are impossibly technical for the average user and so this capability remains in the realm of the theoretically possible but the pragmatically impossible. Most of us have to resign ourselves to making do with what others so graciously provide.
[*]While the snap client side is FOSS, the server side is not. This is a serious concern to many of us.
[*]Speaking only personally, I have always had misgivings about Canonical's penchant to go off on tangents. Unity proved to be a dead end. So did Upstart. At best, they were noble but doomed experiments. At worst, they were distracting, wasted resources and fragmented Linux community effort.
[*]They are an invitation to peremptory and silly decisions—snaps for the sake of snaps. Example: I only found out a few days ago that, from 19.04 to 19.10, the simple and default calculator applet had been made a snap, only to come back to the sanity of being a basic repo app in 20.04.
[/LIST]
As stated, I'm not trying to be argumentative. I have a number of snaps installed on all of my machines and enjoy the currency of those apps versus the frustration of living with the version rot to which I had resigned myself in the past. But the concerns won't disappear through the offering of convenience and currency alone. I hope to see Canonical responding positively to these concerns in the next few months. Otherwise, I predict that Snapcraft will join Unity and Upstart as footnotes in the Linux story.

---

### Post by EuclideanCoffee on 2020-05-12
Actually it is open source.

[https://ubuntu.com/blog/howto-host-your-own-snap-store](https://ubuntu.com/blog/howto-host-your-own-snap-store)

The problem is that it’s still yet too new and unproven. Just as I mastered Debian packaging and repository hosting, now I have to learn this. &#129322;

---

### Post by bvz on 2020-05-12
> **DuckHook said:**
> Snaps *are* maintained by their developers, not by the Canonical Ubuntu team. As already noted, this is a double-edged sword. If the developer is diligent and conscientious, the app will be more current and more secure than the traditional methodology of relying on the distro maintainers. If the developer stops maintaining the app, then it will be orphaned with all the downsides that come with such offloading.

Frankly, this was a predictable outcome. For a similar evolution, we have only to look at the Launchpad PPA experience: it too is filled with some PPAs that offer the most current versions of the most popular apps, and it is also filled with piles of dead PPAs that have gone unmaintained for years. Another double-edged sword. The difference is that PPAs rely on system libraries shared by your base install and if they required an older or newer library, they wouldn't function. They also sometimes broke dpkg and created dependency hell. Not least, they are notoriously insecure because they are installed with no sandboxing. Speaking personally, I would never install a PPA unless it is constrained within a VM or container of some kind.

Snaps have a high potential to be orphaned. But then, so does every app in the Linux-sphere (consider the once&#8209;great Amarok), so I suppose that everything needs to be assessed with realistic expectations.

But if a software developer orphans an app, isn't it simply orphaned everywhere (i.e. it will not be updated in the official repository of any of the distros as well, right?)

I thought (and I may be wrong here) that the issue was that some snaps appear to be packaged up by third parties. With the official distro repository I trust the maintainers. With a snap created by the original software developer, I also tend to trust them (with doing a tiny bit of due diligence - I don't simply trust ANY developer). But if there are snaps that are simply put together by an un-vetted third party and put up on the snap store - I get nervous. Again, I am new to snaps and not 100% sure I understand all of the nuances (correction: I am 100% sure I am not even close to understanding all of the nuances), but I think I have certainly seen snaps that are not maintained by the original developer - and to top it off, there does not seem to be any way to tell for sure who actually supplied the snap.

And that was what I thought you were referring to when you said snaps get orphaned. I thought a software project may still be going strong, but whoever was repackaging it as a snap stopped keeping up.

---

### Post by DuckHook on 2020-05-12
> **EuclideanCoffee said:**
> Actually it is open source…I thought the Snap Store is closed source. Does this Wikipedia article have it wrong? [https://en.wikipedia.org/wiki/Snap_(package_manager)](https://en.wikipedia.org/wiki/Snap_(package_manager))

I was also under the impression that contributors to the snap store had to sign [this CLA]("https://ubuntu.com/legal/contributors/agreement").

Perhaps my info is outdated.

---

### Post by DuckHook on 2020-05-12
> **bvz said:**
> But if a software developer orphans an app, isn't it simply orphaned everywhere (i.e. it will not be updated in the official repository of any of the distros as well, right?)
No. The two are not necessarily connected. See below.
> I thought (and I may be wrong here) that the issue was that some snaps appear to be packaged up by third parties. With the official distro repository I trust the maintainers. With a snap created by the original software developer, I also tend to trust them (with doing a tiny bit of due diligence - I don't simply trust ANY developer). But if there are snaps that are simply put together by an un-vetted third party and put up on the snap store - I get nervous. Again, I am new to snaps and not 100% sure I understand all of the nuances (correction: I am 100% sure I am not even close to understanding all of the nuances), but I think I have certainly seen snaps that are not maintained by the original developer - and to top it off, there does not seem to be any way to tell for sure who actually supplied the snap.

And that was what I thought you were referring to when you said snaps get orphaned. I thought a software project may still be going strong, but whoever was repackaging it as a snap stopped keeping up.
Your general thrust is correct:

[LIST=1]
[*]Even a project that is still going strong has no obligation to keep snaps properly updated. The LibreOffice devs could, for example, decide that snap maintenance is just not worth their while and "abandon" it. This would be a severe case and so high-profile that Canonical would likely do something about it, but a little-known app could very well get orphaned with no one bothering to deal with it.
[*]To my knowledge, so long as they don't violate any licenses, snaps can be packaged by third-parties, though I cannot attest to this as fact.
[*]A snap could be offered by one member of a development team who then has a falling out with the other devs, which leads to its abandonment.
[*]An app doesn't have to actually be orphaned to cause trouble. The devs could mistakenly upload a buggy version or an unstable one. The ability to keep snaps more current cuts both ways. By divorcing snaps from the traditional repository vetting process, the distro maintainers pass on those responsibilities to outside parties. Passing on responsibilities also mean passing on control.
[/LIST]
These sorts of desynchronisations happen all the time. They are a hazard of the trade. On Android, I frequently get more current apps in FDroid than those on the Google App store, and vice versa. As another parallel, there are tons of abandoned apps in FDroid that haven't been touched in years.

---

### Post by EuclideanCoffee on 2020-05-12
I&#8217;m so confused. I guess it is closed source. I will have to build the server and get back to you. Here&#8217;s a little rant from Ubuntu in why we should be grateful for them to not release the source for snaps. Annoying.

[https://www.google.com/amp/s/amp.reddit.com/r/Ubuntu/comments/fgnggx/why_isnt_the_ubuntu_snap_store_open_source/](https://www.google.com/amp/s/amp.reddit.com/r/Ubuntu/comments/fgnggx/why_isnt_the_ubuntu_snap_store_open_source/)

Update.

[https://github.com/noise/snapstore](https://github.com/noise/snapstore)

Yep. This is garbage. Canonical should pull the earlier article. I'll complain.

Update II.

Looks like you can create a snap store yourself, but it requires someone to actively develop something.

[https://dashboard.snapcraft.io/docs/v2/en/index.html](https://dashboard.snapcraft.io/docs/v2/en/index.html)

---

### Post by anotherChris on 2020-05-12
> **kevdog said:**
> I'm aware Ubuntu's been trending toward installing everything in the form of snap packages.
What's behind this philosophy?

When I upgraded from 17.10 to 20.04 recently, I started hearing about snaps, and so I went Googling and ended up on a chat site (now I lost it) where there was an argument that purported to be be between two Canonical employees.  My impression from that argument is that snaps have less to do with any technical issues *per se* (such as security or testing) than with making Ubuntu able to capture larger share of the OS market--by making more programs available but mostly by decreasing the amount of knowledge users have to have about "what's under the hood" in order to use Ubuntu.

---

### Post by bvz on 2020-05-12
> **DuckHook said:**
> No. The two are not necessarily connected. See below.

Your general thrust is correct:

[LIST=1]
[*]Even a project that is still going strong has no obligation to keep snaps properly updated. The LibreOffice devs could, for example, decide that snap maintenance is just not worth their while and "abandon" it. This would be a severe case and so high-profile that Canonical would likely do something about it, but a little-known app could very well get orphaned with no one bothering to deal with it.
[*]To my knowledge, so long as they don't violate any licenses, snaps can be packaged by third-parties, though I cannot attest to this as fact.
[*]A snap could be offered by one member of a development team who then has a falling out with the other devs, which leads to its abandonment.
[*]An app doesn't have to actually be orphaned to cause trouble. The devs could mistakenly upload a buggy version or an unstable one. The ability to keep snaps more current cuts both ways. By divorcing snaps from the traditional repository vetting process, the distro maintainers pass on those responsibilities to outside parties. Passing on responsibilities also mean passing on control.
[/LIST]
These sorts of desynchronisations happen all the time. They are a hazard of the trade. On Android, I frequently get more current apps in FDroid than those on the Google App store, and vice versa. As another parallel, there are tons of abandoned apps in FDroid that haven't been touched in years.

Ah. I see. That makes a lot of sense. Thanks.

---

### Post by kevdog on 2020-05-13
> 
Your general thrust is correct:

Even a project that is still going strong has no obligation to keep snaps properly updated. The LibreOffice devs could, for example, decide that snap maintenance is just not worth their while and "abandon" it. This would be a severe case and so high-profile that Canonical would likely do something about it, but a little-known app could very well get orphaned with no one bothering to deal with it.
To my knowledge, so long as they don't violate any licenses, snaps can be packaged by third-parties, though I cannot attest to this as fact.
A snap could be offered by one member of a development team who then has a falling out with the other devs, which leads to its abandonment.
An app doesn't have to actually be orphaned to cause trouble. The devs could mistakenly upload a buggy version or an unstable one. The ability to keep snaps more current cuts both ways. By divorcing snaps from the traditional repository vetting process, the distro maintainers pass on those responsibilities to outside parties. Passing on responsibilities also mean passing on control.


If these statements are indeed true, it seems like the entire concept of snaps is a really really bad idea.

---

### Post by vicsar on 2020-05-13
Yeah... this is the kind of stuff that makes me wonder if I should still use this distro. It has been a long journey with it but I am thinking about it more and more.

---

### Post by bvz on 2020-05-13
> **kevdog said:**
> If these statements are indeed true, it seems like the entire concept of snaps is a really really bad idea.

I don’t see how this is unique to snaps though. All of these issues could affect ppa’s or .deb or even tarballs. They could even affect the actual repo in a distro as well in that the repo isn’t updated very often. 

Ultimately you are relying on someone maintaining a release of a software package. If nobody does, or it gets forked because one maintainer only likes flatpak and so apt gets left behind and no longer updated, you are in a similar place. And if you rely on the distro maintainers to provide all of your software, there is no technical reason (other than the inherent limitations of snap packages) that they couldn’t do so via snap versus apt or some other package manager.

To me the concept of snaps currently seems to be completely fulfilled in that they are (somewhat) portable and more or less distribution agnostic. 

Where they fail is in the overly restrictive sandboxing, and the fact that the snap store is both centralized and yet not curated enough.

If the store were decentralized, or if it were curated to the point that there was a verification that the person uploading the snap was identifiable as the developer (not limited to original developers, but to ensure at least that I know who uploaded the snap) then it would be much easier to trust them.

And if the snaps themselves had the ability to either see the entire file system if I so choose, or be more like flatpaks in that I can tell them explicitly which paths they can see, then their utility would match applications installed via tarballs for example. 

But that an application can be abandoned or its distribution method forked does not seem to be a unique problem to snaps, or invalidate the concept behind them.

---

### Post by EuclideanCoffee on 2020-05-13
> 
[COLOR=#000000]To me the concept of snaps currently seems to be completely fulfilled in that they are (somewhat) portable and more or less distribution agnostic.[/COLOR]
[COLOR=#000000][/COLOR]

[COLOR=#000000]I see that .deb packages seem "distribution specific," but the purpose of a distribution is to deliver software that is compliant with the system, hence ubuntu and debian maintain archives that are documented in a way that represents if the project "maintains" the build or if it provides it as a convenience. How they are portable simply relies on how your system is configured. You could have a Linux computer that processes debian packages, but then it would install software in a particular way meant for debian platforms with all the software it pre-packages. If you've gone through the work of creating a Linux computer, why not just use Debian?[/COLOR]

Then how do snaps work better than packages?

They simply require less work from the distribution to maintain compliance, as they run on a sub-system in a way.

However you should expect a cost in performance... and there is a cost in operation security. How do I lock down snaps? Documentation says I can confine them, but if my requirements are to keep certain systems away from developers, there are easy ways to work around modifying snap installs to include apache or ftp when I don't want those services available on systems pushed out to customers who will not know about the security vulnerabilities, etc.

---

### Post by DuckHook on 2020-05-13
> **bvz said:**
> I don&#8217;t see how this is unique to snaps though&#8230; that an application can be abandoned or its distribution method forked does not seem to be a unique problem to snaps, or invalidate the concept behind them.
I agree with your above analysis, with the exception of one critical omission:

Currently, apps in the repos are compiled from source. This means that it's the Canonical maintainers who decide which apps become repo packages and they (or anyone for that matter) can parse through the source code at any time. While I'm positive that Canonical doesn't do so&#8212;after all, at last count there are 60,000 pkgs in the repos&#8212;the sheer fact that source code must be posted serves as a tremendously effective deterrent to malicious apps being foisted upon us.

But the snap ecosystem is different. It doesn't require source code to be posted. As said, it's whole modus operandi is to offload responsibility for maintenance to the developer. So, malicious or questionable apps have a much easier time sneaking into the Snap ecosystem than the repos. It's already happened: [https://www.omgubuntu.co.uk/2018/05/ubuntu-snap-malware](https://www.omgubuntu.co.uk/2018/05/ubuntu-snap-malware)

Since then, Canonical has taken great pains to prevent a recurrence, but consider the following scenario:

Community Carmen produces a good clean weather checking applet that is useful to a subset of Ubuntu users and posts it in the snap store. It even has a source tree so that diligent users can examine it. She maintains it for a year, but then, life intervenes so she has to pass it on. She finds Cursory Cathy who agrees to take it over. However, Cursory Cathy does not adhere to the same standards. She maintains the applet well enough but can't be bothered with the source tree, so eliminates it. After another year. she too has to pass it on.

Enter Devious Dan. He represents himself as a good member of the community and, for the first year, maintains the applet with all due care. But the applet now has three years of solid provenance. It has become an accepted part of the ecosystem and people no longer think twice about installing it. Devious Dan decides to add cryptomining to the applet. It still does its purported job as well as it ever did, but it now siphons off a portion of your resources to enrich Devious Dan. Moreover, Devious Dan implements the cryptomining in such a way that the resource hit is never high enough to draw attention to itself and the constant IP traffic is not questioned because it is in the nature of the applet function itself.

How does one guard against this sort of thing?

I can't code to save my life, so the existence of source code is of no direct use to me, but I *am* surrounded by a community of coding gurus like all of you to whom source code is actually decipherable. Your collective expertise is the most priceless of all resources to the greater Linux ecosystem and are what guys like me rely on to keep this ecosystem safe. My biggest concern with snaps is not that apps might get orphaned, but the way it short-circuits this proven safeguard. 

Years ago, I made the jump from the proprietary world to the FOSS world in large part because of these sorts of considerations. That jump was not easy. It involved a lot of short-term pain for the promise of long-term gain. That trade has more than worked out and has returned me benefits in spades, but if the future of Ubuntu is entirely towards snaps, then I too will be forced to consider my options.

What I'm counting on is that snaps will be treated as a supplemental ecosystem and not a replacement one. If they are meant to be simply a sandboxed version of PPAs, then I can live with that. But if Canonical is ultimately migrating everything to snaps, then that's a deal-breaker. So far, I don't have enough info to tell either way, so I'm keeping my eyes open and my ears to the ground.

---

### Post by Shibblet on 2020-05-15
It's an ideal, isn't it?  All of your apps run in their own little sandboxed container?

---

### Post by DuckHook on 2020-05-15
> **Shibblet said:**
> It's an ideal, isn't it?  All of your apps run in their own little sandboxed container?
Although the provisional answer is "Yes", the details make all the difference in the world.

[LIST]
[*]If the contained app is opaque and no longer follows FOSS principles, then the advantage from it being technically contained is outweighed by the disadvantage of it now being suspect (my above posted example).
[*]I want to be able to fine tune those container parameters; not have those parameters be forced on me from on high.
[*]I want the option to *not* contain an app should I so choose. Example: in Focal, Chromium is only available as a Snap. This is the FOSS version of the most popular browser in with world, yet it is now missing from the repos.
[*]Many apps and applets make no sense being confined. LUKS doesn't belong in a sandbox. Neither does the file manager, nor the system editor. Hundreds more come to mind. Yet there is a tendency to snap them just&#8230; because. Beware the hammer syndrome: when one has a shiny new hammer, every app looks like a nail.
[/LIST]

---

### Post by EuclideanCoffee on 2020-05-16
So I was sitting with some folks, and we were talking about deploying Nextcloud. And I mentioned you could "deploy Nextcloud in a snap." At this moment, we all realized the true reason why Canonical is going with snaps in 20.04 LTS. Fun way to describe a technical procedure.

---

### Post by uRock on 2020-05-16
I see lots of great points brought up here. The waste of storage space is a big issue for me. Most of my SSDs are smaller than 100 GB. My primary machine only has ~60GB.  If there was a way to move the snap folder to one of the HDDs, then I'd like it more. Installing applications on secondary drives is very easy in Windows. Maybe this is possible, as I haven't looked into it.

---

### Post by Cheese Sandwich on 2020-05-16
> **DuckHook said:**
> ...Moreover, Devious Dan implements the cryptomining in such a way that the resource hit is never high enough to draw attention to itself and the constant IP traffic is not questioned because it is in the nature of the applet function itself.

How does one guard against this sort of thing?


I wonder if the sandbox could also include CPU & network limits and/or monitoring to flag questionable app behavior. For example, a snap package's configuration would need to post the expected limits of CPU and network traffic. If the snap's developer posted unreasonable expectations, people would see it. If they don't post it, then attempting to exceed it would be caught by the sandbox.

---

### Post by Erik1984 on 2020-05-16
Also the sandbox is potentially very powerful but the default for most snaps will probably still be home access. You can turn this off as a user (as mentioned before I tested this with Chromium) but this requires manual intervention. My point is that your home folder will likely contain your most valuable personal data and a malicious snap could access that by default. So the sandboxing is good but does not undo the malware in the snap store argument made by Duckhook.

---

### Post by grahammechanical on 2020-05-16
> What I'm counting on is that snaps will be treated as a supplemental  ecosystem and not a replacement one. If they are meant to be simply a  sandboxed version of PPAs, then I can live with that. But if Canonical  is ultimately migrating everything to snaps, then that's a deal-breaker.  So far, I don't have enough info to tell either way, so I'm keeping my  eyes open and my ears to the ground. 				

Who knows? Certainly not me. I do not fault Mark Shuttleworth (Canonical) for wanting to shakeup Linux development by trying new ideas or doing things differently. True, some of the projects have had to be abandoned. I do not see that as a basis for criticism or scorn. I would have been happy to buy a tablet PC running Ubuntu mobile with Unity 8. I wanted such a tablet that could become a desktop PC when connected to a LED TV screen, mouse and keyboard. Alas, it was not to be. But the idea was a good one. It would have shaken up the smartphone/tablet commercial system.

I did experiment with Ubuntu Desktop Next and Ubuntu Personal. Now Ubuntu Personal could be installed on a hard drive. You could boot into it from Grub and so you could dual boot. It ran on the Mir display server. It used Unity 8. It was a snap based OS. There was a method by which an OS update would never break the installation. It all worked. So, what was wrong with it. The app store had Click packages and they would not work. There were no snap apps to install through the app store. There was a Ubuntu web browser but that caused the desktop to freeze and it was based on 15.10 Ubuntu code and never progressed to 16.04 code. Otherwise I would still be testing it. As a proof of concept it worked.

We do have Ubuntu Core. That is a snap based OS meant for the Internet Of Things. It has no desktop environment. One would have to be a snap to work on Ubuntu Core. I did install it on a second hard drive but I could not run it. It does not boot from Grub. You log into to it using SSH from a running install of Ubuntu. And we cannot have two OS running on the same machine. It has to be on a device that you connect to over a network. I just wanted to see if I could have an up to date version of Ubuntu Personal. I still like that idea.

So, the ground work has been laid but I think the enthusiasm is no longer there.

As for malicious code in apps. The Apple app store has had that problem. There are I believe Android apps that you should avoid like Covid 19. And if your device manufacturer does not update Android you never get an updated version of Android. That would not have been the case with a Ubuntu smartphone or tablet.

Regards.

---

### Post by Hwæt on 2020-05-17
> **Erik1984 said:**
> Also the sandbox is potentially very powerful but the default for most snaps will probably still be home access. You can turn this off as a user (as mentioned before I tested this with Chromium) but this requires manual intervention. My point is that your home folder will likely contain your most valuable personal data and a malicious snap could access that by default. So the sandboxing is good but does not undo the malware in the snap store argument made by Duckhook.

Isn't this also true for debian packages?

---

### Post by DuckHook on 2020-05-17
> **Hwæt said:**
> Isn't this also true for debian packages?
If Canonical changed their policy and required source code for all Snaps, and compiled all snap apps themselves, that one change would enhance the trustworthiness of Snaps to the same level as apps in the repos. Otherwise, at least when it comes to security, there is no comparison between Snaps and Debian pkgs. That's the central point of my earlier posts.

---

### Post by DuckHook on 2020-05-17
> **Cheese Sandwich said:**
> I wonder if the sandbox could also include CPU & network limits and/or monitoring to flag questionable app behavior. For example, a snap package's configuration would need to post the expected limits of CPU and network traffic. If the snap's developer posted unreasonable expectations, people would see it. If they don't post it, then attempting to exceed it would be caught by the sandbox.
This could be difficult.

[LIST]
[*]For example, the MakeMKV snap app ranges over a wide swath of behaviours. When it gets up a good head of steam, it can eat up 100% of the CPU cycles of as many cores as it can lay its hands on. GIMP will consume RAM like I consume ice cream. Torrenting is notorious for its bandwidth demands as well as its profligate port and table hogging. A typical modern game can legitimately take the GPU from idling to full tilt in a fraction of a second. What criteria does the system use to decide when such apps are acting normally or abnormally?
[*]We already have lots of tools that do this. Apparmor, SELinux, Firejail, Taskset, VMs, LXD's resource allocations, modern file systems' quotas, etc. It's a legitimate question to ask why we need yet another?
[*]Devious Dan is the one who will define the app's parameters in the first place and this renders the exercise pointless. It is asking the fox to guard the henhouse.
[/LIST]

---

### Post by Artim on 2020-05-18
I'm still on 18.04 (and will be probably 'til it reaches EOL), but I'm curious if the user can disable snaps in 20.04 and just use .debs from the repos.  Can that be done?

---

### Post by EuclideanCoffee on 2020-05-18
It is possible.

What is difficult is that some apt calls will try to download a snap version instead.

To disable, you simply need to uninstall snapd and add it to an apt block list.

After you've blocked snapd, any attempt to install snaps from apt will fail.

Uninstall the snap-store, and then add third-party repositories of the applications that attempt to install snap, such as Chromium.

---

### Post by DuckHook on 2020-05-18
> **Artim said:**
> …I'm curious if the user can disable snaps in 20.04 and just use .debs from the repos.  Can that be done?
Certainly possible as per EuclideanCoffee's method above, but two things to consider:

[list=1]
[*]Trying to uninstall packages that are so tightly bound into the guts of a distro is a fraught exercise. It frequently breaks functionality. Far better to start with the mini.iso, which lacks snaps, and then build upwards from there.
[*]This strategy is unsustainable. Take LXD. As of Eoan, LXD would no longer be kept current unless installed as a Snap. If Canonical decides that everything is going to be snapped, then even if one momentarily finds a way around Snaps, one does so at the cost of drifting further behind to eventually recede into irrelevance.
[/list]

---

### Post by Artim on 2020-05-19
I guess snaps are the future, but they are too new to be the default, I would think.

---

### Post by Artim on 2020-05-19
This looks like a deal breaker for me.

---

### Post by Erik1984 on 2020-05-20
> **Hwæt said:**
> Isn't this also true for debian packages?

Certainly, but with the deb packages from the repos I don't expect any sandboxing. 

So the snap situation is an improvement if we just consider sandboxing but could be even better. It would be awesome if the snap permission system became more fine grained regarding folders in home. Imagine a Downloads interface for example, that would be useful for browsers. There is a way now to disable home interface and give each snapped browser an individual downloads folder but Firefox and Chromium snap cannot share that folder afaik.

---

### Post by irv on 2020-05-21
I just watch this video and it refutes some of the comments being made here about snap packages.
[https://www.youtube.com/watch?v=ixWuE1hhZfw]("https://www.youtube.com/watch?v=ixWuE1hhZfw")

---

### Post by RabbitWho on 2020-05-22
assuming:
1. I don't want snaps for a reason I am too dense to be talked out of
2. I will find any solution difficult 

how do I avoid snaps when I upgrade from bionic (i got rid of the snaps, don't remember how)? Will I just finally go Linux Mint? Do all the Ubuntu flavours have snaps? Am I off topic?


> **EuclideanCoffee said:**
> It is possible.

What is difficult is that some apt calls will try to download a snap version instead.

To disable, you simply need to uninstall snapd and add it to an apt block list.

After you've blocked snapd, any attempt to install snaps from apt will fail.

Uninstall the snap-store, and then add third-party repositories of the  applications that attempt to install snap, such as Chromium.

oh my god i am in awe of your lack of lazy

---

### Post by Artim on 2020-05-23
> **RabbitWho said:**
> assuming:
1. I don't want snaps for a reason I am too dense to be talked out of
2. I will find any solution difficult 

how do I avoid snaps when I upgrade from bionic (i got rid of the snaps, don't remember how)? Will I just finally go Linux Mint? Do all the Ubuntu flavours have snaps? Am I off topic?

Snaps are "the future," so they say.  You can maybe *forestall* their intrusion for awhile by blocking them in Ubuntu (and it's flavors) and in the Ubuntu-based OSes like Mint, Linux Lite, ElementaryOS, Zorin, and dozens of others.  But snaps will reach them all as well, and any distro that is based on Ubuntu 20.04 and above.

[CENTER][SIZE=6]OR,[/SIZE]
[/CENTER]

You could change to a non-Ubuntu-based distro that doesn't use snaps (at least not by *default*, as Ubuntu does).  Snaps depends on systemd, so a good way to avoid it *long-term* is to use a systemd-free distro (Slackware, MX-Linux, antiX, or my favorite, PCLinuxOS).

---

### Post by RabbitWho on 2020-05-23
Cool, thanks. They would be grand if i had a TB of space but snaps are like tribbles, growing and growing, every time i make space for the it works for a few days and then they take up more space again until my computer suddenly doesn't boot unless in safe mode. I only have like 100gb, i can't have 40gb of fricken snaps and duplicates of snaps!

I'm so used to Ubuntu now I'm afraid if I use anything else it will mean relearning everything

---

### Post by RabbitWho on 2020-05-23
ufff, following instructions for blocking snapd broke everything, i  can't install anything at all now. Isn't Ubuntu for everyone? even those  who aren't computer savvy? but I can't use snaps, they make copies of themselves to the point where my computer won't turn on, and when I try  to do something about that I break everything. I wish we could choose  whether we want them or not by clicking a box on installation. this is  way too advanced for me

---

### Post by Erik1984 on 2020-05-23
I do not understand why people bother with removing the snap system, especially if they claim to be lazy. The proper lazy solution is to do nothing. If you don't install any snaps manually there won't be many snaps on your system (maybe Chromium if you had that installed before 20.04 as deb), so the space argument is moot.

---

### Post by RabbitWho on 2020-05-23
so if i don't use the "software" thing I'll never have to worry about snaps? Just keep using sudo apt and finding debs online, then I won't have any snaps?

---

### Post by ajgreeny on 2020-05-23
If you really must do so you can always either compile chromium yourself, or search for the PPA which does exist, but there are risks to using it so only do so if you're aware of those potential risks.

I have to admit that I'm trying it at the moment with no problems and it has overcome the problems I had using the snap version which could not see nor use several of the folders in my home which I use for various file types; from memory only Downloads was usable, not even any subfolders of Downloads. That seems just a ridiculous and unnecessary restriction to me.
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)

---

### Post by RabbitWho on 2020-05-23
ufff i forgot how many problems snaps caused the last time I upgraded and now it's all coming back to me, my / is already full up and i can't do anything, can't even remove programs or snaps, because i can't write anything to the disk because / is full up, i'm going to have to do another clean install, the third today, i don't see how to fix this otherwise

---

### Post by grahammechanical on 2020-05-23
> Snaps depends on systemd, so a good way to avoid it *long-term* is to use a systemd-free distro

Are you sure? Systemd is Redhat software. Debian developers working for Redhat pushed for its inclusion into Debian. As Ubuntu is based on Debian we get SystemD in Ubuntu.

[https://en.wikipedia.org/wiki/Systemd](https://en.wikipedia.org/wiki/Systemd)

Snap applications need snapd which is installed by default in newer versions of Ubuntu

[https://snapcraft.io/docs/installing-snap-on-ubuntu](https://snapcraft.io/docs/installing-snap-on-ubuntu)

The argument in Debian over SystemD was so fractious that a group of Debian developers who lost the argument left Debian and forked the code. Canonical employees working on Debian were ordered by Mark Shuttleworth not to get involved in the discussions. Even though it was Canonical code that was dropped from Debian in favour of SystemD Ubuntu continued to be built on Debian and so we are using a distribution that has SystemD by default. And now SnapD.

Lets us not rewrite history. There is enough of that going on in the media.

Regards

---

### Post by RabbitWho on 2020-05-23
So what you are saying is... snaps... are a conspiracy?

---

### Post by VMC on 2020-05-23
> **Artim said:**
> ...  Snaps depends on systemd, so a good way to avoid it *long-term* is to use a systemd-free distro (Slackware, MX-Linux, antiX, or my favorite, PCLinuxOS).

I'm using Arch Linux, it has systemd, and snaps are not installed by default

---

### Post by 1clue on 2020-05-24
Snaps, docker and kubernetes (**SDK** from now on) all change the type of responsibility for the developer, and all require more space on the host to implement an application.

They also, unlike a regular VM, use the kernel of the host. So all this talk of "any version, any age, any computer" is not really correct. There is a kernel compatibility level that must be met.

Each app has its own toolchain, they may share a specific version of a library or they may have a separate one. This is the two-edged sword.

On the one hand, each app developer can have the best tool chain to run their specific app without interference from some other app's requirements. If you're talking about a mission critical application with lots of development resources then that's great, because you could test the heck out of it, have a third party audit of your SDK container, and then certify that the container has a certain guaranteed quality. On the other hand, if the app developer drops the ball then it makes the app certifiably junk.

SDK are all terrible in terms of an end user trying to do a security audit. If you're trying to get a web site up with, say, a credit card payment system, you need a certification for your site. You have third party audits, you need to answer questions that are difficult and irritating to answer on a traditional system, and a nightmare to answer when using SDK. But if the app developer certifies the container then suddenly it's all golden for the end user again.

---

### Post by Hwæt on 2020-05-24
> **1clue said:**
> all require more space on the host to implement an application.

I don't think that this is really a major concern for server or desktop. Space is cheap.


I think this is only really a problem for embedded which, I don't imagine Canonical is going to ship glibc as a snap anytime soon.

---

### Post by VMC on 2020-05-24
"_Space is cheap._" That's Windows motto for sure. My Windows install takes up **23 gigabytes**. My snapless Arch less than **5 gigabytes**. I have more tools on my Arch than my Windows has. 
Lots of redundant keepsake.

Just because you have the space, doesn't mean you need to fill it. Years and years ago, I remember having limited filder names(8?). Once that was solved people got crazy with folder names.

Guess I'm too old and conservative for that nonsense.

---

### Post by 1clue on 2020-05-24
> **Hwæt said:**
> I don't think that this is really a major concern for server or desktop. Space is cheap.


I think this is only really a problem for embedded which, I don't imagine Canonical is going to ship glibc as a snap anytime soon.

You're right, space is cheap. But even embedded equipment has ridiculous storage capabilities right now. So my only disagreement is that "normal" new and future embedded systems will be every bit as capable of this type of thing.

For the record, the thread is about snaps. Snaps are typically apps that people might see, where docker/kubernetes focuses on "invisible" services. Same idea, but embedded doesn't really do desktop stuff, so we're diverging the discussion by pursuing that line of thought.

> **VMC said:**
> "_Space is cheap._" That's Windows motto for sure. My Windows install takes up **23 gigabytes**. My snapless Arch less than **5 gigabytes**. I have more tools on my Arch than my Windows has. 
Lots of redundant keepsake.

***Just because you have the space, doesn't mean you need to fill it. Years and years ago, I remember having limited filder names(8?). Once that was solved people got crazy with folder names.***

Guess I'm too old and conservative for that nonsense.

I'm old and conservative too, and don't really see the need for all this on just somebody's pc.

Back in the early days of DOS/Windows <99, every app shipped DLLs of a particular version, or hacked somewhat to make their app work. What sucked is that there was no mechanism to distinguish which DLL belonged to which app, and every app looking for a DLL with that name either got the right one, the wrong one or a bunch of them with no way to decide. So I'm saying that SDK (snaps, docker and kubernetes) solves this issue if no other.

The real way to answer "snap or no snap" is to ask another question: What are you trying to accomplish?
[LIST=1]
[*]It is still possible to build most software traditionally, with very few apps requiring special versions or modifications to resources. The more apps your system has, the harder it is to achieve this because not all app developers are worried about keeping things up to date. Most modern operating systems have a way to specify specific libraries by version, and have multiple versions or even variants (modified code from standard) and keep track of all that.
[*]The traditional mechanism gives the app developer less control over the environment they're in. So that method makes testing more difficult for them.
[*]Full virtualization definitely has its place, especially if you need security between apps. It's a proven and ubiquitous technology.
[*]SDK offers a solution of a reliable, reproducible environment for the app developer and a simple black box packaging strategy for the end user.
[*]The problem with SDK is when you care what's in the box. We need better ways to control what goes in there and verify/certify what's inside for a particular use not anticipated by the app developer.
[/LIST]

This SDK approach is relatively new, and while I think it's ready for real work it's not completely ready for mission critical stuff unless the site implementers really know what they're doing.

The elephant in the room is, what do we have to do differently in order to make this type of arrangement work? When is it worthwhile to do this, and when should we leave it alone?

We also need to realize that each administrator will have different answers to these last questions and possibly each will have different answers depending on which system they're administering.

All these things are likely here to stay in some form.

---

### Post by CatKiller on 2020-05-25
> **DuckHook said:**
> This may be my single biggest reservation about snaps. It's more than halfway to being a proprietary silo. If I wanted that, I would have gladly succumbed to the Apple siren a long time ago.

You would probably find [this video](https://youtu.be/x8MgktKqjsU) useful, which is a segment from [a much longer interview](https://youtu.be/_XcoWKoubjE). It covers a lot of things that have been talked about in this thread.

---

### Post by CatKiller on 2020-05-25
> **Erik1984 said:**
> So the snap situation is an improvement if we just consider sandboxing but could be even better. It would be awesome if the snap permission system became more fine grained regarding folders in home. Imagine a Downloads interface for example, that would be useful for browsers. There is a way now to disable home interface and give each snapped browser an individual downloads folder but Firefox and Chromium snap cannot share that folder afaik.

The snap [sandbox interfaces](https://snapcraft.io/docs/supported-interfaces) are fairly fine-grained in general. A lot of problems that people have been having in the forums are because they seem to be configured too conservatively with regards to *removable-media* for the use-cases that people actually have, which is the kind of thing that will hopefully get picked up after real-world usage. I could also see a case for a standard access to ~/Public only in addition to the full "access non-hidden files in the home directory."

---

### Post by CatKiller on 2020-05-25
To answer the OP's question:

> **kevdog said:**
> I'm aware Ubuntu's been trending toward installing everything in the form of snap packages.
What's behind this philosophy?

Not, as others have suggested, to make things easier for the developers, really. Ultimately, to make things better for the users.

Snaps were developed for the Ubuntu Phone. By the time that was discontinued, having containerised applications was also useful for the desktop and server.

Let's say that you're only interested in open source software and you don't care about version numbers, just that it gets security updates. No problem, that can be in the repositories and everyone's happy. You download it from the Software Store, or use apt, and it's all fine. Software gets updated automatically and it's as discoverable as you like.

Now let's say that you want *new* open source software. Well, you're SOL. You're either on the upgrade treadmill so that you have to upgrade *everything* every six months to get software that's a bit newer, or you have to wait 2 years for the LTS to upgrade. Too bad, so sad. *Or*, you learn about PPAs, which aren't discoverable - at all - and are really a security nightmare and upgrade pain. But, if you learn about them, find one that has what you need, don't get in a tangle with dependencies (especially at upgrade time), and cross your fingers about the fact that the PPA maintainer can put *literally anything* on your computer, then the software in them will get updated along with everything else as part of your standard package management. Which is nice.

Now let's say that you want proprietary software (or stuff that doesn't get put in a PPA for whatever reason). The developers aren't interested in all the different distros with all their different libraries. If it's all distros or no distros then they're going to choose no distros. But if they *did* make it work on one version of Linux then having a way to abstract away all those differences and have it work anywhere is a much more attractive proposition. The libraries and underlying OS don't matter; the software can update on its own cadence, and the OS can update on its own different cadence. The developer can just point people to the container, and you can display the containers to users just the same as packages. You get the security benefits from sandboxing as a result of making it so that things work regardless of distro.

So, that's why snaps exist. Or flatpacks. Or appimages. Ubuntu went with snaps because they were created for Ubuntu and they think snaps have advantages over the alternatives (which are two different things: Ubuntu had their own upstart as an alternative to init, but systemd was better, so they dropped upstart).

As to why snaps are in Ubuntu and not just the Software Centre, there aren't many. There's a gnome-libraries one, so that snaps can access that rather than either accessing the underlying OS (which would be bad) or duplicating Gnome's libraries in every snap (which would also be bad); they had some small applications (like the calculator) as snaps for dogfooding, which is no longer the case for 20.04; and the controversial one of chromium. The [rationale]("https://snapcraft.io/blog/chromium-in-ubuntu-deb-to-snap-transition") for that last one was > In summary: there are several factors that make Chromium a good candidate to be transitioned to a snap:
    
[LIST]
[*]It&#8217;s not the default browser in Ubuntu so has lower impact by virtue of having a smaller user-base 
[*]Snaps are explicitly designed to support a high frequency of stable updates 
[*]The  upstream project has three release channels (stable, beta, dev) that  map nicely to snapd&#8217;s default channels (stable, beta, edge). This  enables users to easily switch release of Chromium, or indeed have  multiple versions installed in parallel 
[*]Having the application strictly confined is an added security layer on top of the browser&#8217;s already-robust sand-boxing mechanism 
[/LIST]


Now I don't personally use snaps. And we see the two big downsides here in the forums all the time: they take a long time to start up because their internal file representation needs to be unpacked the first time they're run, and they're sandboxed away from being able to access the files that the user wants them to. But I can see their benefits, too: they make it so that people are more willing to make their software available on Linux, regardless of any real or perceived fragmentation; they make it so that users can actually *find* that software, install it, have it updated, and so on; and it's likely to be more secure: I already trust the Ubuntu project to vet and manage the software on my computer, otherwise I wouldn't have installed Ubuntu in the first place: some random person on the Internet that manages to throw up a PPA hasn't done as much to earn that trust.

---

### Post by CatKiller on 2020-05-25
> **Hwæt said:**
> I don't think that this is really a major concern for server or desktop. Space is cheap.


I think this is only really a problem for embedded which, I don't imagine Canonical is going to ship glibc as a snap anytime soon.

[https://docs.ubuntu.com/core/en/](https://docs.ubuntu.com/core/en/)

---

### Post by Hwæt on 2020-05-25
> **CatKiller said:**
> [https://docs.ubuntu.com/core/en/](https://docs.ubuntu.com/core/en/)

While that's a lot more than I thought, I don't think glibc itself is in a snap. At least, the one the system is using. From what I know, that doesn't seem possible.

---

### Post by grahammechanical on 2020-05-26
Ubuntu core does not have a desktop environment. A DE would have to be a snap to install on ubuntu core. An IoT device running one application would not need a full DE and may not have the RAM and CPU power anyway. Let us not forget that snap packages can include all the libraries needed. Here is a 2 year old post showing how to run the snap of Chromium on ubuntu core running in a VM.

[https://discourse.ubuntu.com/t/snaps-to-develop-a-web-kiosk-on-ubuntu-core-using-wayland/6424](https://discourse.ubuntu.com/t/snaps-to-develop-a-web-kiosk-on-ubuntu-core-using-wayland/6424)

A criticism of snap packaging is that it duplicates libraries. What if you like playing a game that has not been upgraded to the latest version of Linux or Ubuntu. Here are some retro games that have been made as snaps to show that the problem can be overcome when libraries are included in the snap package.

[https://snapcraft.io/blog/retro-style-games-on-linux](https://snapcraft.io/blog/retro-style-games-on-linux)


[https://linuxx.info/7-best-games-available-in-snap/](https://linuxx.info/7-best-games-available-in-snap/)

Regards

---

### Post by mastablasta on 2020-05-28
> **grahammechanical said:**
> 
A criticism of snap packaging is that it duplicates libraries. What if you like playing a game that has not been upgraded to the latest version of Linux or Ubuntu. 


this si the main reason that snaps got me excited. i play a lot of old (DOS, windows) games. and i found how simply repackaging the old games in snap would solve many issues. on linux i tried a quake4. while it still works, something should be removed or sometimes not used. this can be solved with snap. same goes for some other older applications that still do the work well and are not a security risk, but are no longer maintained or won't work on newer libraries. 


in my windows days at the end of previous century i had a task to redesign and move an old book written in some ancient word processor. first mission was to open the file (you couldn't just import it as it was proprietary data file) . and windows has this backwards compatibility through libraries (that are added to the application). sure it makes them bulky but i was able to get the writer going and after some fiddling open a 20 year old file. then i had to copy the data to MS Word and then i was editing it and improving it. with some help a really nice and much improved product was made that went into printing and is still used to this day for teaching.
my point is sometimes or many times it is good if you can easily run old things in new OS. especially in business. until about 5 years ago we were still (on occasion) using 20+old data to help customers resolve their issues. we made many people happy as they were able to cheaply repair their beloved home appliances. i never really understood people's connection with the washing machine...

---

### Post by RabbitWho on 2020-05-28
What a great post! I have a friend who's an archivist with a town hall and he'd be delighted with that idea. Somehow keeping everything you will need to open the file, ever, with the file. That's the dream.   Also, a friend's grandfather refuses to have any of the old appliances replaced because he associates them with his late wife. Emotionally he has located a little piece of her in every corner, nook, and cranny of the house, and not one thing can be changed for any reason. So you are doing a really beautiful thing repairing people's washing machines

---

### Post by 1clue on 2020-05-29
These last few posts is exactly the sort of thing that would be fantastic for snaps and preservation of antique functionality.  Not just games.

I can't count how many times I had to deal with a really old system that was getting flaky. It's running some sort of software that won't run on a modern system, and it's indispensable. Often you wind up installing a brand new software package that doesn't do the job the right way, hopefully before the old system goes belly up.

But if you could take that system and clone it into a VM (pick your antique CPU) or a snap on a VM, you could preserve that functionality. If the app wouldn't be secure today, then you could jail it to limit network access or whatever else needed to happen. A modern CPU is many times faster than the old one was, so it would be a small load on the new system even if it was full non-native emulation.

Snaps allow freezing the library list in a way that a whole VM can't. But if you have an old cpu and need to limit the new system so it runs old or even alien (non-native) code, a VM would take care of that part.

---

### Post by kevdog on 2020-06-09
I've done some more reading on snaps over at reddit, and it seems far and away the largest complaint about snaps is that snaps are only distributed from Ubuntu.  There isn't an alternative Snap-store as there could be when using Flatpack. So basically in the end cannonical controls the distribution of snaps.  

I've been thinking about this since many have brought up security concerns regarding this model, and the fact it tends to run counter to the "linux-mantra" of providing an open-source for product distribution. Linux Mint has stated they don't want to support the use of snaps and would be in favor of using flatpacks although I saw a story late last night of Ubuntu reaching out to Mint developers to see if they could somehow rectify the situation with this future decision.

It would seem at this time Ubuntu is kind of facing an uphill battle with their snap distribution model, many comparing their model to Microsoft's software store model. I'm sure there are many more issues I'm not aware of, but this is kind of turning out to be a very long turf war battle.

---

### Post by EuclideanCoffee on 2020-06-09
There is not a Linux mantra but a GNU obligation. Ubuntu tends to walk around GNU, and this isn't far off from expected behavior.

---

### Post by VMC on 2020-06-09
I read recently that Linuxmint will remove all snap files. Regarding Chromium, Mint will have a location to install it without snap.

---

### Post by QIII on 2020-06-09
Why should there be a GNU obligation?  

Linus happened to use GNU tools when developing Linux, but that doesn't oblige Linux to GNU.  Other way around, perhaps.  Had there been no Linux, GNU would still be in the wilderness of obscurity searching for a Hurd.

---

### Post by EuclideanCoffee on 2020-06-09
There is a literal GNU legal obligation. It has little to do with Hurd being a bad operating system while Linux is a good one. I could talk for hours about this.

---

### Post by QIII on 2020-06-12
There is an obligation to observe the proforma GPL.

---

### Post by EuclideanCoffee on 2020-06-13
Oh that is right. I am sorry. GNU has nothing to do with GPL.

---

### Post by QIII on 2020-06-13
Well, it is the "***GNU General Public License***" and was written by the FSF, but that carries no obligation to GNU or the FSF directly.  It does oblige people to acknowledge and give credit to anyone whose code is folded into a new project.

Just for clarity.

---

