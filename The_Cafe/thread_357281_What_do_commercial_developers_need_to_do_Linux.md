---
title: "What do commercial developers need to do Linux?"
date: 2007-02-09
forum: The Cafe
---

### Post by sicofante on 2007-02-09
In my view, Ubuntu or OpenSuse are mature enough desktops OSs. Open source apps are OK for a number of tasks and some are simply better than their commercial competitors. But in some realms well established commercial apps are truly needed. I'm thinking of image processing, desktop publishing, music or video editing because these are areas that I live close to, but I'm sure other people have other needs that open source doesn't cover properly and commercial developers are not willing to tackle under Linux. (Device drivers are another big area that probably applies to the following considerations as well.)

I think there are a number of issues we need to iron out to win the trust of commercial developers:

1- Hostility against closed source has to cease. We must understand both models, open and closed, have virtues and flaws. Ubuntu forums are a special place because very little anti Microsoft flames are held here, and this community is respectful to everyone. But this is an exception. Almost everywhere else you have to be very careful if you're going to write the word "Microsoft" or "Windows". (By the way, this is the reason why I have Ubuntu installed and care about Linux at all now.)

2- Gnome vs KDE. Choice for users, nightmare for developers. While keeping two (or ten) desktop environments is feasible in the open source world, it's unsustainable for a business to care for both (or more) and it's too risky to develop just for one alone. Fortunately, major desktop distros are supporting one of these two over the other, so maybe developers have less of a problem with that in the future.

3- RPM vs DEB. Just go to a download page for binaries and you'll find several debs, several rpms... Commercial developer's can't make and support three or four different binaries. Take a look at what Apple did with their move to Intel: provide tools for the developers to package what they now call "universal binaries". Since rpms and debs now are both mature and offer great reliability, some sort of agreement should be reached among developers to adopt just one or make them totally transparent for the user (so any system would install flawlessly any of the two).

4. Distros. Distros should be just flavours of Linux, not incompatible systems. The "multiple binaries disease" mentioned above should make us reflect on the way we are seen from the outside world. It's OK to offer different packaging (as long as it's universally supported) and different functionality or orientation (speciality distros like Ubuntu Studio are a great idea). It's not OK to have apps installed in different places depending on which distro we use, or different structures for the whole OS. I know Linux is just the kernel. I'm claiming it should go a little bit further and establish a more standardised way to structure system directories and files.

Since I'm no Linux expert I might be wrong in my appreciations, so please comment on them. (And keep in mind I'm no English native speaker, so maybe I haven't used the most accurate wording.)

---

### Post by Adamant1988 on 2007-02-09
#1 is never going to go away (fortunately most of the hostility comes from a vocal minority), the LSB 2-4 moot points.

---

### Post by saulgoode on 2007-02-09
> **sicofante said:**
> I think there are a number of issues we need to iron out to win the trust of commercial developers:

I am much more concerned about maintaining the trust of Free Software developers.

---

### Post by Adamant1988 on 2007-02-09
> **saulgoode said:**
> I am much more concerned about maintaining the trust of Free Software developers.

Then go be concerned about it somewhere else, this thread is about commercial software vendors.  You can either try to co-exist or you can badger them when they start trying to sell things on Linux.  Either way, stop hijacking the thread now!

Anyway, again, the LSB is really a huge deal for this as it handles most of your issues, making the differences between systems unimportant as long as they're LSB compliant.

---

### Post by az on 2007-02-09
> **sicofante said:**
>  I'm sure other people have other needs that open source doesn't cover properly and commercial developers are not willing to tackle under Linux. (Device drivers are another big area that probably applies to the following considerations as well.)

There is no real distinction between a volunteer developer and a commercial one.  There is no reason that those areas have not been tackled.  There just has been not enough reason for someone to tackle them.

What I am trying to say is that the problem will solve itself when the need becomes big enough - this is how it works.  You can't motivate a community around an open source project just by paying a few people to write code.  You need people to "scratch their own itch."  And doing that does not preclude them from making money from it.

That's a big differnece in how open source is developed.  There is no "master plan"  It is what it is.

> **sicofante said:**
> 
I think there are a number of issues we need to iron out to win the trust of commercial developers:


Free-libre open-source software is already a multi-billion dollar indusrty...

> **sicofante said:**
> 
1- Hostility against closed source has to cease. We must understand both models, open and closed, have virtues and flaws. Ubuntu forums are a special place because very little anti Microsoft flames are held here, and this community is respectful to everyone. But this is an exception. Almost everywhere else you have to be very careful if you're going to write the word "Microsoft" or "Windows". (By the way, this is the reason why I have Ubuntu installed and care about Linux at all now.)

More and more, FLOSS is being accepted in the marketplace by people in suits.  If it's not Sun open sourcing Solaris or Java, it's WM making a deal with Novell to improve interoperability with GNU/linux.  As more proprietary software vendors become less hostile towards FLOSS (and realize that they, too, can make a buck or two from it) the open-source people will tend to become friendlier.

Both sides are rude.

> **sicofante said:**
> 
2- Gnome vs KDE. Choice for users, nightmare for developers. While keeping two (or ten) desktop environments is feasible in the open source world, it's unsustainable for a business to care for both (or more) and it's too risky to develop just for one alone. Fortunately, major desktop distros are supporting one of these two over the other, so maybe developers have less of a problem with that in the future.

Since you can run a gnome application on KDE and vice versa, that point is irrelevant.  You can do this with windowmaker, icewm, xfce, etc... More and more, the infrastructure for making these all applications look the same is improving.

> **sicofante said:**
> 
3- RPM vs DEB. Just go to a download page for binaries and you'll find several debs, several rpms... Commercial developer's can't make and support three or four different binaries. Take a look at what Apple did with their move to Intel: provide tools for the developers to package what they now call "universal binaries". Since rpms and debs now are both mature and offer great reliability, some sort of agreement should be reached among developers to adopt just one or make them totally transparent for the user (so any system would install flawlessly any of the two).

Binary compatibilty is not important.  What's important is that the software be compatible on the source level.  Anything more than that can slow down (often significantly) development and should be avoided.  Performing the steps of compiling the apps and making them available to the end-user is the responsability of the distribution.  

Third-party apps that are not part of the software archive are few and far between.  If they are not included in the archive, it's usually because thay are non-free.


> **sicofante said:**
> 
4. Distros. Distros should be just flavours of Linux, not incompatible systems. The "multiple binaries disease" mentioned above should make us reflect on the way we are seen from the outside world. It's OK to offer different packaging (as long as it's universally supported) and different functionality or orientation (speciality distros like Ubuntu Studio are a great idea). It's not OK to have apps installed in different places depending on which distro we use, or different structures for the whole OS. I know Linux is just the kernel. I'm claiming it should go a little bit further and establish a more standardised way to structure system directories and files.

Since I'm no Linux expert I might be wrong in my appreciations, so please comment on them. (And keep in mind I'm no English native speaker, so maybe I haven't used the most accurate wording.)

Distros are exactly what you need.  The software is too vast.  The development model is dependant on source-code compatibility.  The development is dependant on there not being a single direction.  The development is dependant on the community being able to have a great deal of choice.

Having differnent distributions of linux is a strenght, not a problem.

---

### Post by saulgoode on 2007-02-09
> **Adamant1988 said:**
> Then go be concerned about it somewhere else, this thread is about commercial software vendors.  You can either try to co-exist or you can badger them when they start trying to sell things on Linux.  Either way, stop hijacking the thread now!

While I'm certain the chafing can get quite uncomfortable, even the most severe cases of diaper rash do not justify such verbal tantrums.  I'm sure we can find some people willing to chip in and buy you some talcum powder.

---

### Post by Adamant1988 on 2007-02-09
> **saulgoode said:**
> While I'm certain the chafing can get quite uncomfortable, even the most severe cases of diaper rash do not justify such verbal tantrums.  I'm sure we can find some people willing to chip in and buy you some talcum powder.

I'd fire back with a witty retort, but it's easier in the long run to block you *and stop hijacking the thread*.

---

### Post by kanem on 2007-02-09
#1: No deal! :)

#2: Just support one toolkit. Google's products use QT don't they? I don't complain, even though I use Gnome. I don't *have* to have my apps looking the same. Like Az(z? what's going on?) said, you can run an app from any desktop environment on any other desktop environment.

#3: Static binaries. I think this is a big misconception that needs to be cleared up. There seems to be the popular opinion that if you release a closed source binary it has to be a .deb or .rpm or .whatever and that it has to utilize libraries that are already on the user's system. Any company can make a universal binary package with no dependencies. They just have to bundle everything the app might need in the download. This is what Google does, and is why the Google Earth download is so huge relative to other Linux apps.

4#: Sorry, nothing anybody can ever do about that. Someone will always want to be different and roll their own distro. But anyway, use static binaries, and this isn't a problem either.

I think it's mostly an issue of how much money they think they'll make. Until there's some more profit motive, most companies won't bother. Note that I said '*think* they'll make', not '*will* make'.

Edit: Oh, I just saw your sig, Az.. But, how is Az pronounced? I would say it the same way I say Azz.

---

### Post by Brainfart on 2007-02-09
> **kanem said:**
> #1: No deal! :)
I'm personally undecided on this issue.  On the one hand, it'd be nice for more apps (especially games) on Linux, but on the other hand it would suck if closed-source apps started pushing open-source out...

> #2: Just support one toolkit...
++

> #3: Static binaries. I think this is a big misconception that needs to be cleared up. There seems to be the popular opinion that if you release a closed source binary it has to be a .deb or .rpm or .whatever and that it has to utilize libraries that are already on the user's system. Any company can make a universal binary package with no dependencies. They just have to bundle everything the app might need in the download. This is what Google does, and is why the Google Earth download is so huge relative to other Linux apps.

4#: Sorry, nothing anybody can ever do about that. Someone will always want to be different and roll their own distro. But anyway, use static binaries, and this isn't a problem either.
Aside from the horrible waste of memory associated with static binaries, that's true.  However, said waste will add up over time (one benefit of windows - or any consistent environment - is that you can expect certain shared libraries).

---

### Post by saulgoode on 2007-02-09
I suspect the original poster is open-minded enough that he would be willing to hear discussions whether or not they agree with his concerns.

> **sicofante said:**
> 1- Hostility against closed source has to cease.

I think the main "hostility" only occurs when the authors of Free Software become concerned that their copyright license terms are being violated. Beyond that, someone stating that they have no wish to use closed software is not hostility and stating that they will not support a distribution that promotes closed software is not hostility; that is just free market consumerism.

> **sicofante said:**
> 2- Gnome vs KDE. Choice for users, nightmare for developers.

If a Free Software developer has spent the last five years writing software using GTK (or QT, or FLTK, etc), he might very well consider it a "nightmare" if he were forced to learn to write code for a new interface. 

> **sicofante said:**
> 3- RPM vs DEB. Just go to a download page for binaries and you'll find several debs, several rpms... Commercial developer's can't make and support three or four different binaries.

Free software developers generally focus on writing the software and providing the source code. Again, there really is no way to "demand" that they use a specific package system (or compiler, or versioning system, etc) and you will probably find "but it will make it easier on closed source developers" to be a fairly ineffective argument.

> **sicofante said:**
> 4. Distros. Distros should be just flavours of Linux, not incompatible systems. 

Linux runs on systems from as small as a portable music player to the world's fastest and most powerful supercomputers. There are "flavors" of Linux for desktops, firewalls, webservers, embedded devices, cellphones, ad infinitem. Even on the same hardware and for the same general purpose, systems need to be optimized for different tasks. The fact that there is no one-size-fits-all is a benefit for Linux, not a liability.

> **sicofante said:**
> The "multiple binaries disease" mentioned above should make us reflect on the way we are seen from the outside world.

We should also look at it from the perspective of the "inside" world.

Microsoft is a crippled dinosaur that will soon collapse under its own weight. The business model of end user licensing agreements is horrendously suited to meet the needs of multi-core processors and virtualization. Proprietary file formats are increasingly being rejected in favor of open standards and the courts of several nations are rethinking the efficacy of software patents.

Now is not the time for Linux to adopt the business practices of a system that is self-limiting. Free Software is about sharing knowledge and innovation. It is about building upon that already learned. Free Software is the "science" in "computer science". Just as open sharing of discoveries, methods, and conclusions is the critical foundation of other scientific fields (such as biology, mathematics, chemistry, physics, etc.), contributors to Free Software feel that the greatest benefit stems from the sharing of the results of their own explorations in the field of computing.

Let the corporations worry about profits, stockholders, and market share -- their problems needn't concern us. Let us focus on advancing the science of computing.

---

### Post by sicofante on 2007-02-09
I find most replies interesting but I think I must clarify my starting position. I'm trying to sit in the chair of the guy who has to convince Adobe management (to name one important player) to port Adobe Creative Suite to Linux. Yes there is the market share issue, but looking at Mac's market share, that wouldn't be a tough one. So next question I probably would be asked is: "So what are the APIs we must use for Linux": I would have to answer Qt or GTK. Before Suse and Ubuntu I would have a tough time. Despite all the claims that you can run any app under any DE, the people at Adobe want to follow clear usability patterns and each DE has its own. Now that Gnome seems to be settling in the corporate desktop, I would answer go for Gnome (all this is just hypothetical, of course I don't know what Adobe really thinks!!). So next would be decide the packaging. Packing everything looks easier, but also bulkier. Is that what Linux users want? If you say yes, so we'll package every single library in a RPM package. I understand Ubuntu users won't care. So we finally release our CS2 for Linux in an RPM containing everything. Are we targeting the Linux market. Really?

Now let's imagine I'm an individual software developer. I love open source but I need food in my plates and pay the rent each month so, no matter how much I regret it, I must close my app and ask for money. Some suggested I go to Novell or Canonical and ask for sponsorship. I don't like that route so much. I'd rather sell my app directly for a few dollars through my own website. Besides having to read rants against my personal stance in Linux forums, I still must decide on pretty the same questions as Adobe: if I want to target non-technical people, which API do I choose (in Windows and Mac that is very clear)? which packaging? which distro? After reading this thread I finally decide to go KDE and Deb. I go to sleep pretty sure that I'm missing some chunk of the Linux user base out there. Synaptic in Ubuntu won't take my RPMs and OpenSUSE won't take DEBs "out of the box" either, so I should probably release two or three binaries to be sure...

Please understand commercial developers must target potential buyers. This is absolutely a major difference to typical volunteers. They also must target non-technical customers. This is a segment typically ignored by Linux developers. Not even Ubuntu or OpenSUSE, being definitely non-tech oriented, are still very complete regarding that.

I believe open source will always exist and provide tools and apps as well as being the "science" in "computer science" (that's a nice one). I believe different DEs will exist in the future and, as the ground for new developments, I hope they do exist. I don't really know if there's a benefit from the structural differences between distros but if there's any, be it welcome. All I'm saying is that if we want to see a third download link in most commercial software out there, developers of that software need a number of issues sorted out before.

I've been trying Ubuntu for about a year now (can't use it regularly because of the lack of apps, go figure...). I have also OpenSUSE installed and have played with Fedora for a while. I've been trying to figure out which way would I go if I started my own software project. I'm not happy taking the open source route because I want to make a living out of my code and I don't like being hired by Novell, Canonical or RedHat. I'm not happy creating a KDE app for Gnome users (I don't like KDE apps in my Gnome desktop). I would love having my app being installed by Synaptic or a similar package manager, which provide a significant advantage over Windows or Mac installation, so I better decide if it's RPM or DEB. It seems I don't have to care that much about which particular distro my users have, once I made my RPM/DEB decision... It's easy to be stuck before these decisions.

We are all knowledgeable people and we know our way from choosing a distro to installing a non-native app. I'm saying that commercial developers need a stable landscape filled with standard procedures, which we in the Linux world lack in almost every area. Some argue this is an advantage. Maybe. I'm sustaining this is preventing both Adobe and myself to even thinking of developing for Linux. Of course, some people even think nobody needs Adobe in Linux (let alone me!)...

EDIT: I understand that "different distros for different needs" thing. I'm just talking about PC desktops here, which is where I mostly feel the need for commercial apps to be ported.

EDIT2: I don't think LSB solves really the issues with different desktops, packaging or distros. I hope I made my point on this.

---

### Post by az on 2007-02-09
> **sicofante said:**
>  I'm trying to sit in the chair of the guy who has to convince Adobe management (to name one important player) to port Adobe Creative Suite to Linux. Yes there is the market share issue, but looking at Mac's market share, that wouldn't be a tough one. So next question I probably would be asked is: "So what are the APIs we must use for Linux": I would have to answer Qt or GTK. Before Suse and Ubuntu I would have a tough time. Despite all the claims that you can run any app under any DE, the people at Adobe want to follow clear usability patterns and each DE has its own. Now that Gnome seems to be settling in the corporate desktop, I would answer go for Gnome (all this is just hypothetical, of course I don't know what Adobe really thinks!!). So next would be decide the packaging. Packing everything looks easier, but also bulkier. Is that what Linux users want? If you say yes, so we'll package every single library in a RPM package. I understand Ubuntu users won't care. So we finally release our CS2 for Linux in an RPM containing everything. Are we targeting the Linux market. Really?
Well, that's a bad idea from the start.

It's not a good idea to port an application to linux unles syou have some clear advantage to do it.

FLOSS is a services industry.  If you think you can make money in it by selling an application, you are wrong.  If you think you are contributing to the linux space by providing a proprietary app for it, you are wrong as well.

If Adobe want to contribute to the GNU/linux space by porting their app to linux, they should just release some source code and let the community do the rest.  Whatever usability standards they have in mind are most probably going to fly in the face of what is best for building a healthy community around their project.  The same goes for packaging.

I don't even know what the application you mentioned actually does, but if Adobe wanted to get their feet wet, the smartest way they could do it is find an application that does a similar function in linux and get behind it.  And do that in an open way.



> **sicofante said:**
> 
Now let's imagine I'm an individual software developer. I love open source but I need food in my plates and pay the rent each month so, no matter how much I regret it, I must close my app and ask for money. Some suggested I go to Novell or Canonical and ask for sponsorship. I don't like that route so much. I'd rather sell my app directly for a few dollars through my own website. Besides having to read rants against my personal stance in Linux forums, I still must decide on pretty the same questions as Adobe: if I want to target non-technical people, which API do I choose (in Windows and Mac that is very clear)? which packaging? which distro? After reading this thread I finally decide to go KDE and Deb. I go to sleep pretty sure that I'm missing some chunk of the Linux user base out there. Synaptic in Ubuntu won't take my RPMs and OpenSUSE won't take DEBs "out of the box" either, so I should probably release two or three binaries to be sure...

1.  90 percent of software developers in europe work for projects that do not release code.  That means that only one out of ten developers works for a project that has to sell a shrink-wrapped version to make money.  The other nine write code to make computers do stuff - they get paid for writing the code - that's a service, not a product.

2.  You should not even need to release binaries, just the source.  I wouldn't install a binary from a thrird-party anyway, that's not safe.  Your app is binary-only?  Good bye!


> **sicofante said:**
> 
Please understand commercial developers must target potential buyers. This is absolutely a major difference to typical volunteers. They also must target non-technical customers. This is a segment typically ignored by Linux developers. Not even Ubuntu or OpenSUSE, being definitely non-tech oriented, are still very complete regarding that.

Well, you should have seen things five years ago.  Things are almost completely different from even just two years ago...

> **sicofante said:**
> 
All I'm saying is that if we want to see a third download link in most commercial software out there, developers of that software need a number of issues sorted out before.

You mean proprietary, not commercial.  And actually, no, I don't really want to see that.  What I want is a free-libre version of that software.

If I wanted to run prorietary apps, I would stick with a proprietary OS.

If the proprietary applications are having difficulty adapting to how things work in the open source world, this is not a reason to degrade how open source works.  I don't want to have the shortcomings of the proprietary worl in the free-libre world just for the sake of some applications that I won't even run.

Don't get me wrong, I'm not telling you what you should run on your computer.  There are more than enough ways for proprietary apps to get distributed to linux users.  Just don't try to tell me that the way it works on a proprietary OS is the way it should work on this one, because there is no justification for it, and many good reasons to avoid it.  

> **sicofante said:**
> 
I want to make a living out of my code and I don't like being hired by Novell, Canonical or RedHat. ...

... It's easy to be stuck before these decisions.

Wanna make a living out of FLOSS?  Sell services and support.  Don't sell software.  

You will not make a living selling free software.  Period.

> **sicofante said:**
> 
I'm saying that commercial developers need a stable landscape filled with standard procedures, which we in the Linux world lack in almost every area. 

As it is, the landscape is pretty rich, with the ability to use databases, web technology, clustering, hosting, etc... all for free....

---

### Post by Adamant1988 on 2007-02-09
> 
EDIT2: I don't think LSB solves really the issues with different desktops, packaging or distros. I hope I made my point on this.

The LSB makes the differences in distribution moot.  the LSB is planning to construct an API on top of everything so that any LSB compliant distribution can install your software as easily as they would do in Windows.  Good no?

---

### Post by sicofante on 2007-02-09
Az: are you saying there's no place for closed source software in Linux?

Adamant1988: I don't think we will go any further just by saying "it does not", "yes it does", so I'll leave it there. I just said I find unfortunate the way Qt apps look and feel inside Gnome and as long as I can't install RPMs from Add/Remove programs, the word "moot" can't be used to describe my points.

Can you guys step back a bit and see things in perspective? It's not about what YOU can or want to do with a computer. It's about what non-computer-science people, ordinary people want to do with their computers.

And PLEASE this is NOT about servers or embedded devices. I'll say it again: it's about software for the desktop and ordinary users, not COMPUTER PEOPLE. Sorry for not being clear enough about that in my original post. I hope it's clear now.

FYI: Adobe Creative Suite is a collection of software tools which can be considered standard for any desktop publishing work. Almost everybody in the market agrees that having Adobe onboard would increase Linux market share almost instantly. Now I might understand you don't care about Linux market whatsoever. Well I do, I assume I'm not alone and I intended this thread to be about that, not the philosophy behind open source which I understand very well. I also understand there's a lot of people who find that having less market penetration is actually good for Linux. I just happen to not think so.

---

### Post by Adamant1988 on 2007-02-09
> **sicofante said:**
> Az: are you saying there's no place for closed source software in Linux?

Adamant1988: **I don't think we will go any further just by saying "it does not", "yes it does", so I'll leave it there. I just said I find unfortunate the way Qt apps look and feel inside Gnome and as long as I can't install RPMs from Add/Remove programs, the word "moot" can't be used to describe my points.**

Can you guys step back a bit and see things in perspective? It's not about what YOU can or want to do with a computer. It's about what non-computer-science people, ordinary people want to do with their computers.

And PLEASE this is NOT about servers or embedded devices. I'll say it again: it's about software for the desktop and ordinary users, not COMPUTER PEOPLE. Sorry for not being clear enough about that in my original post. I hope it's clear now.

FYI: Adobe Creative Suite is a collection of software tools which can be considered standard for any desktop publishing work. Almost everybody in the market agrees that having Adobe onboard would increase Linux market share almost instantly. Now I might understand you don't care about Linux market whatsoever. Well I do, I assume I'm not alone and I intended this thread to be about that, not the philosophy behind open source which I understand very well. I also understand there's a lot of people who find that having less market penetration is actually good for Linux. I just happen to not think so.

The portland project (I believe) is working towards making things look better cross GUI environment... 

[http://en.wikipedia.org/wiki/Portland_Project](http://en.wikipedia.org/wiki/Portland_Project)


But here, since you're not seeing what I mean, I'll detail 2-4 more.

2-  Covered by the portland project.  As you can see in the wikipedia link I just sent. 
3-  Not going to matter with the LSB.  Another format will probably arise as an installation for LSB compliant distributions, which is what ISVs will hopefully write for. 
4-  Again, the LSB deals with this.  ISVs will be able to write software for ANY distribution that is LSB compliant.  

It's been shown that ISVs want to treat Linux as a single platform, the way they would windows.  By making it easier for them to write software for Linux, they'll be more likely to do so.  Be it closed, or open software, it will be available.   Companies will have a much easier time porting things to Linux this way, and we'll generally see a lot more software coming in from professional companies, and not *just* open source hobbyist programs.

---

### Post by sicofante on 2007-02-09
Thanks for the info on the Portland Project. I've been reading a bit after that info and it looks nice. We're obviously not there yet and I can't see Ubuntu mentioned in the news about the project, but I understand it's heading in the right direction regarding some of my points.

---

### Post by Adamant1988 on 2007-02-09
> **sicofante said:**
> Thanks for the info on the Portland Project. I've been reading a bit after that info and it looks nice. We're obviously not there yet and I can't see Ubuntu mentioned in the news about the project, but I understand it's heading in the right direction regarding some of my points.

Ubuntu (to my knowledge) is striving to be LSB compliant, if the portland project becomes part of the LSB then it will become part of Ubuntu as well.

---

### Post by sicofante on 2007-02-09
BTW: This article [http://gnomejournal.org/article/43/the-portland-project](http://gnomejournal.org/article/43/the-portland-project) describes pretty well most of my concerns.

---

### Post by Adamant1988 on 2007-02-09
Yeah, that's covered under the LSB pretty much. 

[http://en.wikipedia.org/wiki/Linux_standard_base](http://en.wikipedia.org/wiki/Linux_standard_base)

more information for you.

---

### Post by DrainBead on 2007-02-09
> **sicofante said:**
> In my view, Ubuntu or OpenSuse are mature enough desktops OSs. Open source apps are OK for a number of tasks and some are simply better than their commercial competitors. But in some realms well established commercial apps are truly needed. I'm thinking of image processing, desktop publishing, music or video editing because these are areas that I live close to, but I'm sure other people have other needs that open source doesn't cover properly and commercial developers are not willing to tackle under Linux. (Device drivers are another big area that probably applies to the following considerations as well.)

I think there are a number of issues we need to iron out to win the trust of commercial developers:

1- Hostility against closed source has to cease. We must understand both models, open and closed, have virtues and flaws. Ubuntu forums are a special place because very little anti Microsoft flames are held here, and this community is respectful to everyone. But this is an exception. Almost everywhere else you have to be very careful if you're going to write the word "Microsoft" or "Windows". (By the way, this is the reason why I have Ubuntu installed and care about Linux at all now.)

Agreed, and no one from the old school will even argue about these matters, it's the new "converts" that feel "enlightened".

> 2- Gnome vs KDE. Choice for users, nightmare for developers. While keeping two (or ten) desktop environments is feasible in the open source world, it's unsustainable for a business to care for both (or more) and it's too risky to develop just for one alone. Fortunately, major desktop distros are supporting one of these two over the other, so maybe developers have less of a problem with that in the future.

It's not really a problem, GTK apps run just fine in KDE (and look just like any other KDE program if you got the right packages installed) and QT apps work just fine in Gnome too. It's about choice, remove it and tell me what the point of FLOSS would be for the users.

> 3- RPM vs DEB. Just go to a download page for binaries and you'll find several debs, several rpms... Commercial developer's can't make and support three or four different binaries. Take a look at what Apple did with their move to Intel: provide tools for the developers to package what they now call "universal binaries". Since rpms and debs now are both mature and offer great reliability, some sort of agreement should be reached among developers to adopt just one or make them totally transparent for the user (so any system would install flawlessly any of the two).

Use the package management, it's not that different between the distros, especially if you integrate something like SMART that would handle most any binary packages including the RPM's of Fedora/Red Hat and SuSE or the TGZ's from Slackware or even debs from various distros using them. RPM's and DEB's or TGZ's doesn't really matter, it's all in the package manager.

> 4. Distros. Distros should be just flavours of Linux, not incompatible systems. The "multiple binaries disease" mentioned above should make us reflect on the way we are seen from the outside world. It's OK to offer different packaging (as long as it's universally supported) and different functionality or orientation (speciality distros like Ubuntu Studio are a great idea). It's not OK to have apps installed in different places depending on which distro we use, or different structures for the whole OS. I know Linux is just the kernel. I'm claiming it should go a little bit further and establish a more standardised way to structure system directories and files.

If that is what it comes down to then thanks but no thanks.

It is also impossible, you think Patrick Volkerding would agree to put stuff in his distro that was not stable as in "always stable branch"? Slackware still uses the stable kernel releases which is still 2.4

> Since I'm no Linux expert I might be wrong in my appreciations, so please comment on them. (And keep in mind I'm no English native speaker, so maybe I haven't used the most accurate wording.)

What you are suggesting is "make Linux like Windows is made" and if that ever happened there would be no point in using Linux except that it was free.

Linux is made by programmers for programmers and when it's made to please users the programmers will not be there anymore, they will be working on some BSD or something instead. The only reason why Linux is so great and moves forward so fast is because of the community of programmers behind it, remove that initiative and you are left with users who have nothing to use.

---

### Post by sicofante on 2007-02-09
> **DrainBead said:**
> if you integrate something like SMART that would handle most any binary packages including the RPM's of Fedora/Red Hat and SuSE or the TGZ's from Slackware or even debs from various distros using them
I'm that's so I really hope that SMART thing is used everywhere all the time.

> What you are suggesting is "make Linux like Windows is made"I'm not suggesting that at all. I'm sorry that you have come to that conclusion but you're just wrong.

>  Linux is made by programmers for programmers and when it's made to please users the programmers will not be there anymoreThank's God this is far from being true any more. While I agree this has been precisely one of the big problems with Linux in the recent past, the very existence of Ubuntu is showing that some programmers do care about users before themselves. There's plenty of room for everyone. I know there will always be "guru distros" and programmers-only will be happy with them. But the time for user-first Linux distros has come quite a while ago. I'm obviously talking about it all the time.

---

### Post by az on 2007-02-09
> **Adamant1988 said:**
> The LSB makes the differences in distribution moot.  the LSB is planning to construct an API on top of everything so that any LSB compliant distribution can install your software as easily as they would do in Windows.  Good no?

[http://www.linux-foundation.org/en/LSB](http://www.linux-foundation.org/en/LSB)

I don't think there is an API, just a few things like filesystem and package management.  I don't think a distro that is LSB-compliant is supposed to be binary-compatible with another one that is.


> **sicofante said:**
> Az: are you saying there's no place for closed source software in Linux?

I am saying two things.  
1.  You will not make any money by selling a closed-source product for linux.
2.  The demand and usefulness of closed-source applications on linux is dwindling.

So, yeah.

> **sicofante said:**
> 
Can you guys step back a bit and see things in perspective? It's not about what YOU can or want to do with a computer. It's about what non-computer-science people, ordinary people want to do with their computers.

Whether an application is FLOSS or proprietary has nothing to do with whether it appeals to geeks or ordinary users.  It's called usability and linux is getting more and more usable every day.  Notice this is happening while the proprietary applications of the past are either becoming obsolete or open sourced.

> **sicofante said:**
> 
And PLEASE this is NOT about servers or embedded devices. I'll say it again: it's about software for the desktop and ordinary users, not COMPUTER PEOPLE. Sorry for not being clear enough about that in my original post. I hope it's clear now.

The key to the GNU/linux desktop becoming more popular is not by attracting more proprietary applications, IMHO.  Just the opposite.  This is what has been happening for the last five or ten years.  

> **sicofante said:**
> 

Almost everybody in the market agrees that having Adobe onboard would increase Linux market share almost instantly. 

Never heard that from anybody. 

> **sicofante said:**
> 
Now I might understand you don't care about Linux market whatsoever. Well I do, I assume I'm not alone and I intended this thread to be about that, not the philosophy behind open source which I understand very well.

What?  Marketshare is key.  GNU/linux' marketshare has increased steadily over the past few years.  It won't take much longer before we hit the inflection point (most people think it's ten percent) where hardware vendors and ISVs take notice and fully support it..


> **sicofante said:**
> 
 I also understand there's a lot of people who find that having less market penetration is actually good for Linux. I just happen to not think so.

Who says this?


> **Adamant1988 said:**
> Ubuntu (to my knowledge) is striving to be LSB compliant, if the portland project becomes part of the LSB then it will become part of Ubuntu as well.

To my knowledge, Ubuntu doesn't strive to be LSB compliant.  They happen to include a package that brings in LSB-compliance, but it is not a specified goal.  Rather, just something that is trivial to implement.

I beleive that the official position that Ubuntu takes up on LSB is "whatever."

[http://packages.ubuntu.com/feisty/misc/lsb](http://packages.ubuntu.com/feisty/misc/lsb)
"The intent of this package is to provide a best current practice way of installing and running LSB packages on Debian GNU/Linux. Its presence does not imply that we believe that Debian fully complies with the Linux Standard Base, and should not be construed as a statement that Debian is LSB-compliant."

---

### Post by DrainBead on 2007-02-09
> **sicofante said:**
> I'm that's so I really hope that SMART thing is used everywhere all the time.

I'm not suggesting that at all. I'm sorry that you have come to that conclusion but you're just wrong.

Thank's God this is far from being true any more. While I agree this has been precisely one of the big problems with Linux in the recent past, the very existence of Ubuntu is showing that some programmers do care about users before themselves. There's plenty of room for everyone. I know there will always be "guru distros" and programmers-only will be happy with them. But the time for user-first Linux distros has come quite a while ago. I'm obviously talking about it all the time.

Heh, Ubuntu is perhaps one of the less shining examples of what you are talking about, a much better one would be Fedora/Red Hat but i digress.

At the base it's still the same thing though, the spit and shine doesn't really do much if the leather isn't there and the leather are the programmers who are programming for other programmers.

There are not that many programmers who work for Ubuntu, most of it is just repackaged binaries from Debian and they compile and check the work of other programmers for that distro, Ubuntu will have to do with what Debian packagers provide that other programmers program for other programmers.

---

### Post by Adamant1988 on 2007-02-09
> **az said:**
> [http://www.linux-foundation.org/en/LSB](http://www.linux-foundation.org/en/LSB)

I don't think there is an API, just a few things like filesystem and package management.  I don't think a distro that is LSB-compliant is supposed to be binary-compatible with another one that is.
[http://www.linux-foundation.org/en/Packaging](http://www.linux-foundation.org/en/Packaging)

---

### Post by DrainBead on 2007-02-09
> **Adamant1988 said:**
> [http://www.linux-foundation.org/en/Packaging](http://www.linux-foundation.org/en/Packaging)

RPM might be the preferred packaging format but it's not something all that many agree on, the Linux community has a problem with enforced standards like no other.

LSB has the backing of not so many and it's not really gaining either.

---

### Post by Adamant1988 on 2007-02-10
> **DrainBead said:**
> RPM might be the preferred packaging format but it's not something all that many agree on, the Linux community has a problem with enforced standards like no other.

LSB has the backing of not so many and it's not really gaining either.

Would you mind actually reading the link before you correct me?

---

### Post by DrainBead on 2007-02-10
> **Adamant1988 said:**
> Would you mind actually reading the link before you correct me?

"The LSB Packaging workgroup is working to establish standards that make third party software easier to install and manage on the Linux platform. It was founded after the first FSG Packaging Summit in December 2006. Our work initially aims to create an API to the Linux package systems, so that ISVs can interact with those package systems in a lightweight manner without requiring Linux specific development effort (e.g., RPM support)."

No Linux distro besides RH and SLED follows this anyway so?

---

### Post by DrainBead on 2007-02-10
> **Adamant1988 said:**
> Would you mind actually reading the link before you correct me?

Oh, and i didn't "correct" you, that was another poster.

---

### Post by Adamant1988 on 2007-02-10
> **DrainBead said:**
> Oh, and i didn't "correct" you, that was another poster.

You went on a tangent about how not all distros support RPM... the only mention of RPM in that quote is as an example of a packaging format that isn't going to need to be worried about with the API in place.   

Red Hat and Suse obviously strive for working with the LSB, but I'm willing to bet most big distributions will have the API in place to install programs to the system, in effect making them "Compliant enough".

---

### Post by macogw on 2007-02-10
Universal binaries: autopackage--works for every distro in existence

---

### Post by Adamant1988 on 2007-02-10
> **macogw said:**
> Universal binaries: autopackage--works for every distro in existence

Autopackage is kind of messy as I understand it, and it's use can create some problems. Feel free to correct me, this was just what I've been told by many people when I suggested that autopackage was a good idea.

---

### Post by DrainBead on 2007-02-10
> **Adamant1988 said:**
> You went on a tangent about how not all distros support RPM... the only mention of RPM in that quote is as an example of a packaging format that isn't going to need to be worried about with the API in place.   

Red Hat and Suse obviously strive for working with the LSB, but I'm willing to bet most big distributions will have the API in place to install programs to the system, in effect making them "Compliant enough".

No i didn't "go on a tangent".

The point is that LSB supports RPM as the preferred format, that is all.

The distributions do what? They package the code written by programmers, the programmers could just pack up and leave Linux any day they want to, distros do come and go, mandrake was once king of the hill, now they are not even on the top 20.

The point i'm trying to make is that Ubuntu, as good of a distro as it is (and it is) is just a distro, the programmers are the ones who decide, and if they would say "screw it, i'm moving to BSD" one day there wouldn't be a distro the next day.

So LSB may be grand and nice but it's not going to be like the closed source world because NO ONE will decide what all these millions of programmers do.

---

### Post by DrainBead on 2007-02-10
> **Adamant1988 said:**
> Autopackage is kind of messy as I understand it, and it's use can create some problems. Feel free to correct me, this was just what I've been told by many people when I suggested that autopackage was a good idea.

Do you understand how packages are built?

And i prefer checkinstall but autopackage does it's job pretty well.

---

### Post by Adamant1988 on 2007-02-10
> **DrainBead said:**
> Do you understand how packages are built?

And i prefer checkinstall but autopackage does it's job pretty well.

I have a basic understanding of Checkinstall, and I know what I've read/heard about autopackage.

---

### Post by Adamant1988 on 2007-02-10
> **DrainBead said:**
> The distributions do what? They package the code written by programmers, the programmers could just pack up and leave Linux any day they want to, distros do come and go, mandrake was once king of the hill, now they are not even on the top 20.

The point i'm trying to make is that Ubuntu, as good of a distro as it is (and it is) is just a distro, the programmers are the ones who decide, and if they would say "screw it, i'm moving to BSD" one day there wouldn't be a distro the next day.

So LSB may be grand and nice but it's not going to be like the closed source world because NO ONE will decide what all these millions of programmers do.

I don't know how that's is relevant... 

The LSB is working to provide a set of standard libraries and such so that one installation idea (probably a brand new package type) can be used across any LSB compliant distribution.  They're trying to talk ISVs into supporting any distribution that chooses to have this API in place, and writing for those first and foremost.  It's not an enforced standard, distributions that don't want it won't use it.  But I suspect that the biggest among distributions will at the very least put the API in place to keep their user base happy.

---

### Post by DrainBead on 2007-02-10
> **Adamant1988 said:**
> I have a basic understanding of Checkinstall, and I know what I've read/heard about autopackage.

Ok, so you build your package using checkinstall, distribute it as a tgz,rpm,deb or whatever you'd like, does that really even matter seeing as the metadata in each repo will only work well with the distro you are using?

I'm trying to figure out why a standard would be meaningful in that case, i mean, SuSE, Slackware, Debian and Red Hat (and all of the derivatives there of) use their own repos and while you could use SuSE packages in Slackware it would deviate from the Slackware idea and if you do i'd question why you would not just move to SuSE instead.

They ARE different and 100 years from now they will be MORE different and more numerous.

FLOSS is about choice, you don't get a prepackaged "suits you because it's what you get" offer, you have choices, if one distro doesn't tickle your fancy you can move on to another one or another one or another one.

The section about different distros pretty much proves me right.

---

### Post by Adamant1988 on 2007-02-10
> **DrainBead said:**
> Ok, so you build your package using checkinstall, distribute it as a tgz,rpm,deb or whatever you'd like, does that really even matter seeing as the metadata in each repo will only work well with the distro you are using?

I'm trying to figure out why a standard would be meaningful in that case, i mean, SuSE, Slackware, Debian and Red Hat (and all of the derivatives there of) use their own repos and while you could use SuSE packages in Slackware it would deviate from the Slackware idea and if you do i'd question why you would not just move to SuSE instead.

They ARE different and 100 years from now they will be MORE different and more numerous.

**FLOSS is about choice, you don't get a prepackaged "suits you because it's what you get" offer, you have choices, if one distro doesn't tickle your fancy you can move on to another one or another one or another one.**

The section about different distros pretty much proves me right.
This sentence has convinced me to stop debating this with you.  Obviously if you believe Linux as a platform should be scattered and difficult, then by all means, I'll leave you with that idea.  I disagree though.

---

### Post by DrainBead on 2007-02-10
> **Adamant1988 said:**
> I don't know how that's is relevant... 

The LSB is working to provide a set of standard libraries and such so that one installation idea (probably a brand new package type) can be used across any LSB compliant distribution.  They're trying to talk ISVs into supporting any distribution that chooses to have this API in place, and writing for those first and foremost.  It's not an enforced standard, distributions that don't want it won't use it.  But I suspect that the biggest among distributions will at the very least put the API in place to keep their user base happy.

The point i'm making is that there is no such thing as an LSB compliant distro and there never will be and that that is A GOOD THING.

API=AdvancedProgrammingInterface, explain to me how this does not work throughout any distro seeing as they all use the Linux kernel.

And the API the programs are written for has absolutely nothing to do with the format they are packaged in.

---

### Post by DrainBead on 2007-02-10
> **Adamant1988 said:**
> This sentence has convinced me to stop debating this with you.  Obviously if you believe Linux as a platform should be scattered and difficult, then by all means, I'll leave you with that idea.  I disagree though.

No, i believe that Linux should be about what it has always been about, choice.

If you believe differently and would have our way, this entire community would pretty swiftly be a BSD community instead.

FLOSS is about choice and if you don't like choice, then use what MS tells you is your choice.

---

### Post by Adamant1988 on 2007-02-10
> **DrainBead said:**
> No, i believe that Linux should be about what it has always been about, choice.

If you believe differently and would have our way, this entire community would pretty swiftly be a BSD community instead.

FLOSS is about choice and if you don't like choice, then use what MS tells you is your choice.

That's your opinion and you're welcome to it.  I disagree, I think having a single installation and package format work cross-distro is important for getting Linux taken seriously by ISVs.  There won't be anything stopping you from switching to another distro that doesn't use the LSB API, you just won't get the cool software that was written for it.

---

### Post by DrainBead on 2007-02-10
> **Adamant1988 said:**
> That's your opinion and you're welcome to it.  I disagree, I think having a single installation and package format work cross-distro is important for getting Linux taken seriously by ISVs.  There won't be anything stopping you from switching to another distro that doesn't use the LSB API, you just won't get the cool software that was written for it.

Well there are such things as ISV certifications that do not limit any distros.

I still don't get what the LSB API is, could you explain that to me?

---

### Post by az on 2007-02-10
> **Adamant1988 said:**
>  the LSB is planning to construct an API on top of everything so that any LSB compliant distribution can install your software as easily as they would do in Windows.  

I thought you were talking about binary-compatibility, here.  This is not the case.

> **Adamant1988 said:**
> [http://www.linux-foundation.org/en/Packaging](http://www.linux-foundation.org/en/Packaging)
Our work initially aims to create an API to the Linux package systems,

That's a universal package manager, not a universal API for linux applications.  Very different.
> **macogw said:**
> Universal binaries: autopackage--works for every distro in existence

Not really.  Autopackagre requires every single upstream project to buy-into the concept, which all of them don't.


> **DrainBead said:**
> Do you understand how packages are built?

And i prefer checkinstall but autopackage does it's job pretty well.

Checkinstall is for source tarballs, not binary packages.  They are completely different.  And half the time, checkinstall doesn't work.

> **Adamant1988 said:**
>  But I suspect that the biggest among distributions will at the very least put the API in place to keep their user base happy.

Like Debian and Ubuntu, it's in place, but probably does not work 100 percent of the time.  That's useless.

> **Adamant1988 said:**
>  Obviously if you believe Linux as a platform should be scattered and difficult, then by all means, I'll leave you with that idea.  I disagree though.

Scattered does not mean difficult.  And binary-compatibility makes things difficult for developers which has a negative impact on innovation and new code.

---

### Post by Adamant1988 on 2007-02-10
> **az said:**
> I thought you were talking about binary-compatibility, here.  This is not the case.



That's a universal package manager, not a universal API for linux applications.  Very different.




Sorry for the misunderstanding, could you explain it to me further?  My understanding mostly comes from Ian Murdocks blog. 

[Software installation on Linux: Today, it sucks (part 1)](http://ianmurdock.com/?p=388)

[Software installation on Linux: Tomorrow, it won't (with some cooperation) (part 2)](http://ianmurdock.com/?p=391)

---

### Post by macogw on 2007-02-10
az, Ubuntu doesn't have those 2 little autopackage files in there by default, but the first time you use it, it downloads them.  According to them, no matter what distro you try to install on, it'll work.  I know not all projects use it, very few do, but if you're a dev who doesn't feel like building for RH, Debian, Puppy, etc, having just autopackage is easy enough.

---

### Post by sicofante on 2007-02-10
Linux has been steadily growing in the server market. In the Internet, Apache almost doubles Microsoft's IIS figures. But Linux presence in the desktop is simply marginal. Why is that? IMO is just the "programmers developing for programmers" thing what better explains this situation. Servers are directly used by administrators, which is people that understand computers. Desktops on the other side, are used by ordinary people that don't usually know what's inside a computer or how it works. You can get away with just programmers for a server. You need user interaction designers (who DON'T program a line of code) to go anywhere with desktops. There are very few user interaction designers in the world. Most of them are hired by big companies. There are simply too little user interaction experts working for Linux. Most programmers, especially open source developers, don't want to follow rules from above. That's part of the rebel inside each of them. But without user interaction design, desktops can't go very far. Why Mr. Shuttleworth, Novell or RedHat don't invest in user interaction design is beyond me (Novell seems to be doing some stuff. That new Gnome main menu is the result of a study with real people. That's a good sign.)

There's one company that has always put interaction design before programming (it's called Apple) and their desktops are impeccable. Even if their market share is little, they get attention from the big names in desktop software development because they still matter even after the market has been swept away by Microsoft's business practices.

Now: do we want those big names in software development add a third link to their downloads page or not? If you don't that's OK with me, but I really don't get why would you like to discuss this thread (apart from stating you don't need any closed source software in your computer). If you, like myself, believe those closed source apps are desperately needed in Linux, that the programmers-only approach can't go very far, that user interaction designers are just a few and very hard to find and we need the design coming the from proprietary software firms they work for, then I really would appreciate your ideas regarding how to make ISVs care about Linux.

LSB is a good idea. The Portland project is a good idea. Autopackage is a great idea. These projects indicate a need for standardisation. Of course many won't need those standards, but closed source definitely needs them and IMO also open source would benefit from them. Many choices are not always the best choice.

[quote="Az"]You will not make any money by selling a closed-source product for linux.[/quote]
This is just silly. [This guy]("http://www.kanzelsberger.com") is an individual happily making money from selling software to Windows, Mac and Linux users (Linux is his second market). Avid, Discreet Logic and other big names in audiovisual software are making a lot of money selling closed source apps with no serious competition from open source. That market was owned by Silicon Graphics (IRIX) before, then went to Windows, now is moving "back" to Linux.

Adamant1998: thanks for the great links.

---

### Post by az on 2007-02-10
> **Adamant1988 said:**
> Sorry for the misunderstanding, could you explain it to me further?  My understanding mostly comes from Ian Murdocks blog. 

[Software installation on Linux: Today, it sucks (part 1)](http://ianmurdock.com/?p=388)

[Software installation on Linux: Tomorrow, it won't (with some cooperation) (part 2)](http://ianmurdock.com/?p=391)

You should read up on Ian Murdock's previous "let's all agree to (my) one standard project" called the DCC alliance.  It, too, flopped.  It had magnificent buy-in from all the big Debian players (Mepis, Xandrox, Linspire, etc...)  They all quietly pulled out after a short while.

That sort of compatibility is a distraction.  There is very little benefit to it and the cost is (obviously) too high.

> **macogw said:**
> According to them, no matter what distro you try to install on, it'll work.  I know not all projects use it, very few do, but if you're a dev who doesn't feel like building for RH, Debian, Puppy, etc, having just autopackage is easy enough.

1.  That's the thing.  Not everybody is going to use it upstream.
2.  I certainly would never trust some third-party binary-only app to install itself when I click on it.  The fact that the open source model provides a layer of pretection is important to the end-user, and not a real inconvenience.  In fact, the fact that the repos are centralised makes things by-and-large a lot easier for the end-user.  The fact that the software is uploaded ther ein source form is also a safety factor.  You know that what was uploaded was built by the Ubuntu autobuilder and not the developers computer.  No spyware would last for very long under those circumstances.

If something is offered to me in binary-only form, you have to convince me that it isn't malware.

> **sicofante said:**
> But Linux presence in the desktop is simply marginal. Why is that? IMO is just the "programmers developing for programmers" thing what better explains this situation. .... There are very few user interaction designers in the world. Most of them are hired by big companies. There are simply too little user interaction experts working for Linux. Most programmers, especially open source developers, don't want to follow rules from above. That's part of the rebel inside each of them. But without user interaction design, desktops can't go very far. Why Mr. Shuttleworth, Novell or RedHat don't invest in user interaction design is beyond me (Novell seems to be doing some stuff. That new Gnome main menu is the result of a study with real people. That's a good sign.)

You don't know what you are talking about.  Gnome has done extensive usability studies (Nat Freidman and Miguel de Icaza created Ximian and helped build Gnome before they were bought by Novell.  Jeff Waugh was the second person hired by Canonical and he left his position at Canonical to go back to the Gnome Foundation as well as doing private consultation in the IT field)  KDE has started to do some amazing usability stuff as well.  Ubuntu picked Gnome as their default desktop because it was ahead of the game at the time in comparison to KDE.

Ever heard of the Gnome HIG?  [http://developer.gnome.org/projects/gup/hig/](http://developer.gnome.org/projects/gup/hig/)

And why is the desktop a difficult goal for linux?  Because of the catch-22 of the desktop being disparate and there is not enough marketshare for every need to be properly addressed.

> **sicofante said:**
> 
Now: do we want those big names in software development add a third link to their downloads page or not? If you don't that's OK with me, but I really don't get why would you like to discuss this thread (apart from stating you don't need any closed source software in your computer). If you, like myself, believe those closed source apps are desperately needed in Linux, that the programmers-only approach can't go very far, that open source designers are just a few and very hard to find and we need the design coming the from proprietary software firms they work for, then I really would appreciate your ideas regarding how to make ISVs care about Linux.

What I am saying is that having these ISVs support linux is not the key to linux gaining marketshare.  It's the other way around.  Once linux gains marketshare, ISVs will be able to make real money by properly supporting linux.  And that will probably mean providing services, and not selling software.

> **sicofante said:**
> 
This is just silly. [This guy]("http://www.kanzelsberger.com") is an individual happily making money from selling software to Windows, Mac and Linux users (Linux is his second market). Avid, Discreet Logic and other big names in audiovisual software are making a lot of money selling closed source apps with no serious competition from open source. That market was owned by Silicon Graphics (IRIX) before, then went to Windows, now is moving "back" to Linux.


Whatever.  Firefox used to be netscape.  Netscape used to not be free.  Now it is.  OpenOffice used to be StarOffice.  StarOffice is still not free, but OpenOffice is much better.  Whatever happened to Wordperfect on linux?  It was never free.

Did you know that ten years ago, you would have to *pay* for a proprietary X server (the whole thing) to get your hardware to work?  Now that is unheard of.

My point is that sooner or later, a free-libre implementation of the software comes along, and if your company is not behind it, you are gone.

Sure Oracle sells software and a lot of it is stuff that runs linux.  Sure there are high-end movie-animation rendering applications that are used, etc, but those are again mostly a services-based model for making money.  The model of the software as a product on linux is by-and-large not sustainable.  Beyond the anecdotal cases, it's not a smart move.

---

### Post by sicofante on 2007-02-10
Az: I understand you don't want closed source apps in your computer. Great.

Nat Freidman, Miguel de Icaza and Jeff Waugh are programmers, not user interaction designers. If you want to know more about real user interaction designers I'll be happy to help.

Now can we go on with the discussion on how to bring independent ISVs to Linux? Thanks.

---

### Post by Adamant1988 on 2007-02-10
> **sicofante said:**
> Az: I understand you don't want closed source apps in your computer. Great.

Nat Freidman, Miguel de Icaza and Jeff Waugh are programmers, not user interaction designers. If you want to know more about real user interaction designers I'll be happy to help.

Now can we go on with the discussion on how to bring independent ISVs to Linux? Thanks.

Make them able to treat Linux as a single platform, and that will help a lot.

---

### Post by maxamillion on 2007-02-10
[http://pseudogen.blogspot.com/2006/07/commercial-linux-software-what-it.html](http://pseudogen.blogspot.com/2006/07/commercial-linux-software-what-it.html)

---

### Post by az on 2007-02-10
> **sicofante said:**
> Az: I understand you don't want closed source apps in your computer. Great.

This is not about what I prefer.  This is about what will succeed.  Apple sells computers and they sell software.  Regardless of their marketshare, they will still sell software because their users will buy it.  

The way to make money in FLOSS is different.  Many have tried, few are still around and almost none are still doing business in that way.

Very few GNU/linux users will buy software, and this is not going to change.

> **sicofante said:**
> 
Nat Freidman, Miguel de Icaza and Jeff Waugh are programmers, not user interaction designers. If you want to know more about real user interaction designers I'll be happy to help.

Gnome 2.0 (circa 2001) was made to tackle usability issues.  Extensive user interaction studies were (and still are being) done.  Those guys made it all happen.  Xgl/Beryl/Copiz are all usability improvements at the core.  

Ever heard of Seth Nickell?  Probably not.
[http://www.gnome.org/~seth/blog/xshots](http://www.gnome.org/~seth/blog/xshots)

> **sicofante said:**
> 
Now can we go on with the discussion on how to bring independent ISVs to Linux? 

We are.  You just dissagree with me.  That's fine.  No reason to be rude, though.

---

### Post by sicofante on 2007-02-11
> **az said:**
> We are.  You just dissagree with me.  That's fine.  No reason to be rude, though.
The thread is about how to bring closed source software into Linux. This thread is NOT about whether that itself is a good idea or not. That is a whole different discussion. I hope you understand that.

---

### Post by saulgoode on 2007-02-11
> **sicofante said:**
> The thread is about how to bring closed source software into Linux. This thread is NOT about whether that itself is a good idea or not. That is a whole different discussion. I hope you understand that.

Actually, the thread title would indicate that that the topic concerns the needs of commercial developers. To suggest that they might need to adjust their business model to suit that of Free Software is perfectly relevant.

---

### Post by sicofante on 2007-02-11
Then I must apologize for the confusion. The thread title assumes it's Linux responsibility to attract established software vendors, not the opposite. After this assumption, my post was asking what, in the view of those who agree on that basic assumption, has to be done from the Linux side to make these developers care for Linux.

---

### Post by spoot on 2007-02-18
Great topic, thanks for sharing it :)

I think too it should be easier for commercial software to be made for linux. The more I read and learn about developing software, the more questions arise on how to do that properly for linux systems. I think the largest factor in here is the gap between "upstream" and the distributions. This is very different from the Windows way of releasing things, where you follow upstream very closely and simply download the new release. I know the core of your linux installation will never work this way, nor would I want to, but it would be nice if it was easier for companies to support linux, and so reducing the amount of Windows-only applications.

I believe there will always be software that just requires too much of an investment to be freely shared as open source, such as video games and a lot of software for professionals (Adobe products, development suites, whatever.). History teaches us that games are largely Windows-only, with some Mac versions probably becoming more standard? If it's such an effort to maintain a Mac version, trying to maintain a gazillion different linux distributions is impossibly hard almost, but it's good to read there is some effort being made appearantly. I would be perfectly happy with a mix of a good open source core system and applications wherever possible and closed source commercial software to fill in the gaps.

---

### Post by sicofante on 2007-02-18
> **spoot said:**
> I would be perfectly happy with a mix of a good open source core system and applications wherever possible and closed source commercial software to fill in the gaps.
Exactly. I find many open source apps are unbeatable (Firefox and almost every FLOSS audio/video player are just two examples that come to mind) but it also seems like Linux users will never have the chance to enjoy games or Adobe products, as you mention. Obsession to have every single byte in your system coming from open source has probably developed into this. That's a shame.

I've been reading a little since the last time I posted here and it looks like the "distro model" (as opposed to "platform model") won't make things easier any time soon. Source maybe open but every distro is pretty "closed" in terms of what you install there. This means Linux is not a platform but a multitude of them. That might be fine for the server, but makes things far too complicated for desktops. While that's so, commercial closed-source developers won't even think of entering the Linux desktop.

---

### Post by cprofitt on 2007-04-11
I feel bad for the heat that the OP is taking as his points are valid; the Linux community may not care about them, but they are valid.

Selling services is all that matters?

Please!

I guess people that make tables should give them away and just sell the services to refinish them or perhaps they should just sell you the raw uncut unfished wood and you could build it yourself.

Creating software for ENDUSERS that is EASY to use has value to the end user. The is no reason it should be free. If the programmers wants to donate their software that is fine, but there is no reason that it must be free. A developer produces a valuable product and that product is their CODE.

One person here said that programmers in europe write code that is not sold it just make computers do stuff... was that a point? They actually DID sell their code to their employer for a paycheck... got it? The company doesn't sell the software because they use it internally. The programmer GOT paid though. If programmers didn't get paid very few people would pursue it as a career.

I guess there are two options -- but solid pre-packaged software with a support contract and free updates...

or

Download free uncompiled code with no support contract and the need to recompile updates...

Yeah... the typical end user with GENERIC requirements will get the prior 9 out of 10 times.

/rant off

---

### Post by salsafyren on 2007-04-12
For packaging, why not use [zeroinstall]("http://0install.net/") instead of making yet another way to install things?

Zeroinstall is not 100% done yet, but it seems like a good idea. It does not touch /usr like autopackage does which means that the distros will likely support it.

I have tried to make some zeroinstall feeds but compiling almost every desktop app and the dependencies that those have is a very big task.

For binary compatibility see [http://autopackage.org/docs/devguide/ch07.html]("http://autopackage.org/docs/devguide/ch07.html")

apbuild makes it possible to produce a binary that works on many distros.

It would be great to combine the openSUSE build service with zeroinstall.

---

