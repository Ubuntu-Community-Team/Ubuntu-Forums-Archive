---
title: "Static vs dynamic linking of libraries"
date: 2007-04-02
forum: The Cafe
---

### Post by zugu on 2007-04-02
Hello everyone.

I decided to open this thread after having a discussion with a friend of mine about what's better:

Model 1 - distributing software "in a box", containing all the necessary dependencies (Windows, OS X, PC-BSD)
Model 2 - distributing only the core, solving dependencies is left to the user (most, if not all major Linux distributions)

In our opinion, these two models have the following advantages:

Model 1 - software "just works" regardless of what's installed or not on the operating system. Most proprietary Linux software is distributed this way (Skype, Picasa, neroLINUX, Cedega, Crossover Office etc.). No dependency hassle. No conflicts.
Model 2 - user can use various tools to automate the dirty work: apt-get, yum, emerge etc.

Disadvantages:

Model 1 - having same or different versions of the same library scattered throughout the file system is not desirable: redundancy ensues, more disk space is used, same library loaded many times into RAM; if a security problem is discovered in a certain library, each version and copy of it would have to be updated manually.
Model 2 - having a centralized software database/repository. While this is not a disadvantage for many, installing software from outside the repository might break the whole software ecosystem. Most distributions offer security backports only, newer software is not available. A lot of QA work has to be done, in order to certify that 20 000+ pieces of software are compatible with each other.

While the list is not nearly complete, I am hoping you will add to it. Share your opinions!

---

### Post by zugu on 2007-04-02
I personally prefer static linking. IMO, the success of commercial operating system is partially based on the way they understand to deliver their software. While the *NIX world has still problems in standardizing core aspects of the OS, everyone rejects this approach.

Invariably, the arguments are: *it takes a lot of HDD space/RAM* and *it's a security problem waiting to happen*.

First, HDD space and RAM are not a luxury nowadays. We're not in the '80s anymore. Of course, software blobs could still reach 200 MB, due to the sheer number of libraries used in software development.

However, would the programmers and developers have this problem of space, they would DO something about it. They would cleanup the code, try to eliminate bloat and the myriad of programming languages would add another factor to their "natural selection" process.

If two programs use the exact same version of a certain software library, they should be allowed to share it. A dynamic system to manage this could be designed and written, if it hadn't been already done.

Security issues could be rendered to non-issues, if only the updates would be made at application level and not at system level. Application developers could be "coerced" this way to keep their creations up to date. They would become more responsible, more aware of the users. In the current state, developers develop, distributions package, users use. What about distibutions focusing more on their internals and less on the applications?

IMO, the greatest mistake is trying to provide all the possible software to your users (see Debian, Gentoo). How about wiping these monstrosities out of the equation? Isn't it the time someone designed a Linux OS that lasts at least three years? And how about installing whatever we want in this time, even afterwards?

I am sick of being stuck in some repository. Look at Ubuntu: it's all whistles and bells until one realizes one cannot install new software. Please don't tell me to upgrade, it's NOT NORMAL to upgrade the whole distro just to have a newer version of the web browser.

Gee.

---

### Post by darrenm on 2007-04-02
I'm with you dude. Static is best these days. Dynamic was great when you didn't have much disk space. Bit redundant now.

---

### Post by zugu on 2007-04-02
I forgot to add that PC-BSD is trying something with their PBI packaging system. So there is hope.

---

### Post by Jussi Kukkonen on 2007-04-02
> Security issues could be rendered to non-issues, if only the updates would be made at application level and not at system level. Application developers could be "coerced" this way to keep their creations up to date. They would become more responsible, more aware of the users. In the current state, developers develop, distributions package, users use.

We had a discussion about this earlier, and I still disagree :) A typical application may use dozens of libraries -- in the "everything is static" model every  application developer is expected to stay current on the development of all the libraries they use, and deeply understand them (that is a requirement for making sound decisions on when and how to patch possible vulnerabilities, after all).

EDIT: Forgot to mention: the static model also breaks the nice chain-of-trust in the current ubuntu model: At the moment I only need to decide that I trust Ubuntu and that they screen all of the software in the repositories (I'm generalising here, but you get the point). If applications are provided as monolithic packages, I don't think that's possible -- even if the packages were provided by Ubuntu, which they probably wouldn't if the development model was what you suggest. I'd have to make a decision to trust the packager of each and every piece of software and upgrade... This model easily leads to  chaos as people just aren't able to make informed decisions in situations like this (see the world of Windows software installation for examples).

---

### Post by 23meg on 2007-04-02
[QUOTE=zugu]
Model 1 - distributing software "in a box", containing all the necessary dependencies (Windows, OS X, PC-BSD)
Model 2 - distributing only the core, solving dependencies is left to the user (most, if not all major Linux distributions)[/QUOTE]

Distributing the dependencies in the box doesn't necessarily mean static linking. Almost all Windows software is dynamically linked. Ever heard the term "DLL hell"? DLL stands for Dynamic Link Library. 

And many (if not most) recent Windows applications have "Common Files" folders in which they install system-wide components that are shared by software from the same vendor. And VB has had runtime libraries ever since it existed. And the .NET framework requires a huge runtime which is quite an effort to curb DLL hell by centralizing it.

---

### Post by zugu on 2007-04-02
> **23meg said:**
> Distributing the dependencies in the box doesn't necessarily mean static linking. Almost all Windows software is dynamically linked. Ever heard the term "DLL hell"? DLL stands for Dynamic Link Library. 

And many (if not most) recent Windows applications have "Common Files" folders in which they install system-wide components that are shared by software from the same vendor. And VB has had runtime libraries ever since it existed. And the .NET framework requires a huge runtime which is quite an effort to curb DLL hell by centralizing it.

Yeah, whatever, I'm sure you got my point. Sorry for my English.

---

### Post by zugu on 2007-04-02
> **Jussi Kukkonen said:**
> We had a discussion about this earlier, and I still disagree :) A typical application may use dozens of libraries -- in the "everything is static" model every  application developer is expected to stay current on the development of all the libraries they use, and deeply understand them (that is a requirement for making sound decisions on when and how to patch possible vulnerabilities, after all).

Considering this, it's a wonder commercial software made it this far. Consider a programmer having a deep understanding of the software he/she writes. Unimaginable.

---

### Post by Nonno Bassotto on 2007-04-02
Understanding what you are writing is completely different from understanding how the libraries that you use work. If not, there wouldn't be almost any need for libraries at all. Do you know what a library is?

---

### Post by 23meg on 2007-04-02
Your English is quite fine; it's not a language problem, but a common misconception. The title of the thread and the poll options don't reflect what you actually want to discuss. You want to discuss whether it's better to distribute software as monolithic blocks, or as fragmentary bits that depend on each other, not whether it's better to link statically or dynamically. The former is a question of packaging, and the latter is a question of software design. Sure, they're intertwined to a certain extent, but still they're separate areas.

As for my opinion, the way to overcome the limitations of the centralized repository model isn't to get rid of it altogether, but to reinforce it with other means of installing software that in no way interferes with the way repositories work.

---

### Post by Jussi Kukkonen on 2007-04-02
> **zugu said:**
> Considering this, it's a wonder commercial software made it this far.
I thought we were talking about dynamically linked versus static and not commercial versus non-commercial? 
> **zugu said:**
> Consider a programmer having a deep understanding of the software he/she writes. Unimaginable.
I just read my post again and I think I was pretty clear in my words, but maybe I wasn't (I do have a habit of going on at a tangent, sorry if that was the problem). Simplified, the issue is this: If a developer has to keep track of security issues for a library she uses, she must be very familiar with the library and keep constant watch on the library and any possible vulnerabilities. This is a *lot* of work, and the developer wouldn't have to do it if she used a shared lib maintained by someone else.

---

### Post by saulgoode on 2007-04-02
Memory usage is always a concern. The Linux kernel will use any memory that is not tied up by applications or libraries for disk caching and unless your hard drive is as fast as your memory or the amount of memory in your machine exceeds the amount of storage on your drives, you will benefit from reduced memory usage. Load times for software are also of concern -- just look at the hoops Vista is jumping through to reduce startup times of large (some may say bloated) applications.

That is not to say that shared libraries are always the best approach to conserve memory. If your application is only using a few functions from a library then it might very well be better to use static linking so that just those functions get loaded (as opposed to loading the entire library for just a couple things). 

In short, there is no one-size-fits-all answer and my own opinion is that binary level compatibility across distros is hardly a goal worth burdening developers with or undermining system performance for.

---

### Post by Shin_Gouki2501 on 2007-04-02
Hi!
maybe this could interest u :
[http://en.wikipedia.org/wiki/Global_Assembly_Cache](http://en.wikipedia.org/wiki/Global_Assembly_Cache)

If i remeber correct u can configure where the application should search first for a libary. Its quite nice. too bad its not open source ;)

wbr Shin Gouki

---

### Post by TheSqueak on 2007-04-02
> **zugu said:**
>  Please don't tell me to upgrade, it's NOT NORMAL to upgrade the whole distro just to have a newer version of the web browser.

Gee.

You know, i'm fairly certain that I upgraded Firefox just a little while ago, and I definitely don't remember upgrading my entire OS just to do this.


And in fact, the nice little adept_notifier app sits in my taskbar and regularly notifies me that there are updated versions of various applications for me to install, all without having to upgrade my entire OS, so i'm really not sure what the hell you're talking about here.

---

### Post by Teg_Navanis on 2007-04-02
You're talking about security updates.

I guess you're using either Edgy or Feisty. Firefox 2.0.X is in both of their repositories, and security updates will come in every now and then. If you're using Dapper, however, you're stuck with Firefox 1.5.X if you neither want to update your distribution nor install it manually.

---

### Post by rai4shu2 on 2007-04-02
It seems to me that the major advantages of static libraries aren't really advantages:

- Fewer problems with dependencies? What problems? I'm testing Feisty and I've only briefly seen one of those.
- More package tools to choose from? Do I really want to use yum or yast with Ubuntu?

Maybe this is a bit pedantic, but doesn't using static libraries defeat the purpose of calling it a "library"?

---

### Post by zugu on 2007-04-02
> **23meg said:**
> Distributing the dependencies in the box doesn't necessarily mean static linking. Almost all Windows software is dynamically linked. Ever heard the term "DLL hell"? DLL stands for Dynamic Link Library. 

And many (if not most) recent Windows applications have "Common Files" folders in which they install system-wide components that are shared by software from the same vendor. And VB has had runtime libraries ever since it existed. And the .NET framework requires a huge runtime which is quite an effort to curb DLL hell by centralizing it.
> **zugu said:**
> Yeah, whatever, I'm sure you got my point. Sorry for my English.

1. I am sure you have already gotten my point when you posted that. Telling me how what I think doesn't necessarily mean what I think it means was uncalled for. It's like telling someone something bad might happen to them if they cross the street.
2. I commented on how solid packaging helped commercial software thrive over time. Your FOSS-only ego commented on how MS is also using shared libraries. Since when was this thread about MS vs Linux? I smell troll here.

> **Jussi Kukkonen said:**
> We had a discussion about this earlier, and I still disagree :) A typical application may use dozens of libraries -- in the "everything is static" model every  application developer is expected to stay current on the development of all the libraries they use, and deeply understand them (that is a requirement for making sound decisions on when and how to patch possible vulnerabilities, after all).
> **zugu said:**
> Considering this, it's a wonder commercial software made it this far. Consider a programmer having a deep understanding of the software he/she writes. Unimaginable.

I posted this ironic statement because I fail to understand how modern commercial software developers keep their mental health in place, given those circumstances. **Fact**: in dynamic linking model programmers have to keep track of the upstream developments in the libraries they use. **Fact**: they manage to do it, someway. So it can be done. Why can't FOSS developers do the same?

> **23meg said:**
> Your English is quite fine; it's not a language problem, but a common misconception. The title of the thread and the poll options don't reflect what you actually want to discuss. You want to discuss whether it's better to distribute software as monolithic blocks, or as fragmentary bits that depend on each other, not whether it's better to link statically or dynamically. The former is a question of packaging, and the latter is a question of software design. Sure, they're intertwined to a certain extent, but still they're separate areas.

As for my opinion, the way to overcome the limitations of the centralized repository model isn't to get rid of it altogether, but to reinforce it with other means of installing software that in no way interferes with the way repositories work.

After going off-topic in your previous post, you're finally back on-topic. Congrats.

> **Jussi Kukkonen said:**
> I thought we were talking about dynamically linked versus static and not commercial versus non-commercial? 

I just read my post again and I think I was pretty clear in my words, but maybe I wasn't (I do have a habit of going on at a tangent, sorry if that was the problem). Simplified, the issue is this: If a developer has to keep track of security issues for a library she uses, she must be very familiar with the library and keep constant watch on the library and any possible vulnerabilities. This is a *lot* of work, and the developer wouldn't have to do it if she used a shared lib maintained by someone else.

I had already explained my irony. Also, this was never a discussion about commercial vs non-commercial software.

> **TheSqueak said:**
> You know, i'm fairly certain that I upgraded Firefox just a little while ago, and I definitely don't remember upgrading my entire OS just to do this.


And in fact, the nice little adept_notifier app sits in my taskbar and regularly notifies me that there are updated versions of various applications for me to install, all without having to upgrade my entire OS, so i'm really not sure what the hell you're talking about here.

Yeah? Well then, try installing Firefox 2.0.0.3 on Ubuntu Dapper without using a 3rd party deb or tutorial. I mean from the official repositories. Now you see my problem?

---

### Post by zugu on 2007-04-02
> **rai4shu2 said:**
> It seems to me that the major advantages of static libraries aren't really advantages:

- Fewer problems with dependencies? What problems? I'm testing Feisty and I've only briefly seen one of those.
- More package tools to choose from? Do I really want to use yum or yast with Ubuntu?

Maybe this is a bit pedantic, but doesn't using static libraries defeat the purpose of calling it a "library"?

They might be non-issues for you. But they are for Joe Sixpack.

I recommended Ubuntu to a friend of mine. This was back when I had no idea it's doing the same as Debian: stucking users inside a repo.

My firend like the OS very much, I set it up for him. Everything was in place and performing admirably. However, we soon found out that only security updates are backported. Cause, you know, adding new features might break the WHOLE fracking system. The next day he was back on Windows, where he can install Firefox 2.0.0.3 without upgrading to Vista - because this is the equivalent.

How is this supposed to be Linux for masses?

I say it again: Joe Sixpack want an OS that lasts for two years, at least. He also wants to be able to install every piece of new software that appears in this time span.

---

### Post by rai4shu2 on 2007-04-02
Your friend was impatient. In his case, I would recommend using a Mac.

When I recommend Ubuntu to people, and they try it out for a few months, if they go back to Windows, it's because of hardware issues or because they already prefer some other distro.

---

### Post by zugu on 2007-04-02
> **rai4shu2 said:**
> Your friend was impatient. In his case, I would recommend using a Mac.

When I recommend Ubuntu to people, and they try it out for a few months, if they go back to Windows, it's because of hardware issues or because they already prefer some other distro.

Impatient? How come? Firefox 2 will never hit Dapper's repos. I already recommended him a Mac, but this leaves me wondering: how come they can do it and the OSS community cannot? It's a design decision. Yet, Mac OS X chose differently and won.

Here's a link to a discussion where the user is using Debian sarge and want to be able to use the latest version of OpenOffice.org: [http://www.debianhelp.org/node/3563](http://www.debianhelp.org/node/3563) . In the end it all resumes to dist-upgrade, with some problems on behalf of the X server. This is NOT the way to go for the masses.

---

### Post by NyquistLimit on 2007-04-02
Zugu, I totally agree with you. I also wanted to install the latest versions of software without having to dist-upgrade but unfortunately this isn't how the linux world works. Its a strange ideology because it means that you have to upgrade your whole operating system if you want to get the latest version of an application. Pretty crazy stuff.

Unless you're willing to manually compile software you're gonna have to stick to the versions inside the repositories. From what I've read on these forums Ubuntu users are quite happy using old software for 6 months until they can do a clean install of the operating system. Also, the fact that I have to do a clean install every 6 months is just sooooo completely inconvenient. I thought people moved away from windows because it was causing inconvenience? But you're happy with reinstalling your OS twice a year?!

I've given up on linux for now until the ideology changes. Being tied into repositories because of system wide libraries is such a hindrence to software deployment. Have fun compiling and/or hunting for deb files...

---

### Post by Cloudy on 2007-04-02
> **zugu said:**
> 
Yeah? Well then, try installing Firefox 2.0.0.3 on Ubuntu Dapper without using a 3rd party deb or tutorial. I mean from the official repositories. Now you see my problem?

I, um, have 2.0.0.3 and didn't have to upgrade my distro or use a 3rd party .deb or tutorial. Just thought I'd say. I was notified that I had updates waiting and Firefox was one of them - I just checked and I'm using 2.0.0.3.

Also worth noting that I'm using Edgy Eft, not Feisty - I downgraded just to get Beryl working (I'm so vain).

---

### Post by NyquistLimit on 2007-04-02
> **Cloudy said:**
> I, um, have 2.0.0.3 and didn't have to upgrade my distro or use a 3rd party .deb or tutorial. Just thought I'd say. I was notified that I had updates waiting and Firefox was one of them - I just checked and I'm using 2.0.0.3.

Also worth noting that I'm using Edgy Eft, not Feisty - I downgraded just to get Beryl working (I'm so vain).
Firefox 2 is included in the edgy repositories. It is not in the dapper repositories. The updates you receive for firefox are security updates. If firefox 3 is released you'll have to upgrade your distro to get it, or find a 3rd party deb.

In fact, if Firefox 3 is released after the release of Feisty you'll have to find a 3rd part deb for feisty too.

---

### Post by Cloudy on 2007-04-02
Even then what's the big deal? It's just a .deb. It doesn't take anything to install from a .deb..

---

### Post by NyquistLimit on 2007-04-02
lol! the point is that sometimes, depending on the popularity of the application, it's very difficult to find a working deb. If applications included all the required dependencies the software developer could provide an installer on their website.

Oh and also, Ubuntu gurus generally discourage the use of 3rd party repositories and debs because they're not official and might cause problems.

---

### Post by koenn on 2007-04-02
Hmmmm ... flame bait ..... 

I agree with meg23 that this is a discussion on the advantages / disadvantages of a software distribution system and a packaging system, and has only little to do with dynamically or static linked libraries. 

Then, to rectify some of the misconceptions that have been passed of as **FACT**  here and there : 

> **zugu said:**
> 
*Considering this, it's a wonder commercial software made it this far. Consider a programmer having a deep understanding of the software he/she writes. Unimaginable.*

I posted this ironic statement because I fail to understand how modern commercial software developers keep their mental health in place, given those circumstances. **Fact**: in dynamic linking model programmers have to keep track of the upstream developments in the libraries they use. 
**Fact**: they manage to do it, someway. So it can be done. Why can't FOSS developers do the same?

Typically, when you use a library (while programming), you write against the interface (the API - Apllication Prigram Interface) of that library, i.e. you call functions that are implemented in that library. The library can be patched, updated, modified or completely rewritten - as long as the interface remains the same, the application developper doesn't even need to be aware of the changes. So your 'facts'  :  > **Fact**: in dynamic linking model programmers have to keep track of the upstream developments in the libraries they use. 
**Fact**: they manage to do it, someway. So it can be done. Why can't FOSS developers do the same? are completley beside the point. 


>  I commented on how solid packaging helped commercial software thrive over time. Your FOSS-only ego commented on how MS is also using shared libraries. Since when was this thread about MS vs Linux? I smell troll here.
> Also, this was never a discussion about commercial vs non-commercial software.

fact:  That would be Dynamically Linked Libraries - not necessarily shared libraries. 
And the point was that your poll about "Model 1 - distributing software "in a box", containing all the necessary dependencies (**Windows**, OS X, PC-BSD)" or "Model 2 - distributing only the core, solving dependencies is left to the user (most, if not all major Linux distributions)" - and you seem to call the Windows/OS X/... approach "static linking". Well, that's wrong  (fact !) - as said before, Windows uses DLL's (D for Dynamic :) )  - as pointed out before
fact:  your issues with the packaging have nothing to do with the choice between static or dynamic linking - also pointed out before, but dismissed as comments form a " FOSS-only ego ". 


> While the list is not nearly complete, I am hoping you will add to it. Share your opinions!
You didn't really mean that, did you. Or maybe you thought you'd only get supporting opinions ?

---

### Post by ddaedalus on 2007-04-02
I might be completely of the track, misunderstanding something. BUT, you guys know that actually freezing the repositories of ubuntu is a design decision, now way a model all projects follow, and HELL no a F/OSS ideology. 
(Besides, F/OSS ideology is something that brought Linux, GNU and generally most OSS-Projects where they actually stand. Determinism in doing something your way no matter what is very important in F/OSS). 

I am sure you know Arch, Gentoo and Sabayon. 
Their way of packaging is staying bleeding-edge. Packages are provided asynchronously and there are no *ACTUAL* releases of the system, since it is /rolling/ . I think this something you would like. 
And there also is GOBOLinux giving you the possibility to use multiple versions of a program.

And there is also something called ubuntu-backports, where packages are updated to the newest version, well they should be at least...

Therefore I'd like to add, that freezing the repos is a decision which ubuntu made. IMHO a right one. 
And using Debian to stay bleeding-edgy is sick, really. Debian is great if you want a ultra-stable system. 

just my 2c

---

### Post by 23meg on 2007-04-02
> **zugu]1. I am sure you have already gotten my point when you posted that. Telling me how what I think doesn't necessarily mean what I think it means was uncalled for. It's like telling someone something bad might happen to them if they cross the street.[/QUOTE]

It wasn't about me understanding your point or not said:**
> 2. I commented on how solid packaging helped commercial software thrive over time. Your FOSS-only ego commented on how MS is also using shared libraries. Since when was this thread about MS vs Linux? I smell troll here

My comments were entirely along technical lines, not political ones, as were yours. I didn't say anything at all about "MS vs Linux" so that's a straw man; I merely said that most Windows applications are dynamically compiled, and that there's an increasing tendency to centralize library usage in the Windows environment. I didn't even mention MS; I was talking about application delivery and design on the Windows platform in general; the only reason I touched on Windows at all was that you did so in the first place, since I was addressing your post. That's enough to invalidate your personal attacks, which I'll refrain from addressing.  

[QUOTE=zugu]After going off-topic in your previous post, you're finally back on-topic. Congrats.[/QUOTE]

My first post was as on topic as a post can be. Actually, it's your reply to my "on-topic" (according to you) post that was way off topic and flammable.

If you want to discuss something, that involves a willingness to accept potential corrections to your inaccurate statements in a civil manner, since no person will be 100% right all the time, and there's nothing wrong with being wrong. If you'd like to be right all the time, and anyone who deprives you of that pleasure is either off topic, a troll, or has a "FOSS only ego", have a nice time discussing with those who accept your terms; I won't.

---

### Post by rai4shu2 on 2007-04-02
> **zugu said:**
> It's a design decision. Yet, Mac OS X chose differently and won.

It's a decision made with respect to quality assurance. The issues have nothing to do with libraries, but rather with features that are unfinished or are flawed in ways that create problems for serious users.

If the masses don't care about quality assurance, that's because they've been brainwashed by certain marketing execs. That doesn't mean marketing execs are right, but that people for the most part are gullible and confused. This argument isn't improving that situation.

In the end, people can be dazzled by sales pitches into making unwise choices, but even they will still want a product that works. The whole early adopter mindset only leads to more frustration and rejection of your product in the long run.

---

### Post by jrusso2 on 2007-04-02
What I would like is if frequently upgraded applications were static linked.  That way we could just download them right away when a security or update occurs.

These programs would include email programs and web browsers and other applications where security issues cause frequent upgrades

Opera offers static deb files and when a new version comes out I can just go upgrade, where as with firefox I have to wait and hope they updgrade the repostitory or take a chance of whether it supports my current library's

---

### Post by zugu on 2007-04-03
@koenn & 23meg: You are right, I went over the top. 23meg, please accept my apologies. It was never meant to be a personal attack.

At least the thread is now going in the right direction.

---

### Post by VON_CAPO on 2008-07-08
Just a ex user's point of view:

I left Linux aside just because of the dynamic linking.

It is a nightmare each time a new Ubuntu version come out.

I have to expend a lot of hours in forums and software home pages plus many emails to the developers, to make my programs (sometimes obscure ones) to work again. 

This has worth if I want to learn about Linux mechanic, but also I consider that my time has value.

My only desire is to use the system, not to get dirty with it.  

Sorry my grammar.

---

### Post by madjr on 2008-07-08
> **VON_CAPO said:**
> Just a ex user's point of view:

I left Linux aside just because of the dynamic linking.

It is a nightmare each time a new Ubuntu version come out.

I have to expend a lot of hours in forums and software home pages plus many emails to the developers, to make my programs (sometimes obscure ones) to work again. 

This has worth if I want to learn about Linux mechanic, but also I consider that my time has value.

My only desire is to use the system, not to get dirty with it.  

Sorry my grammar.

i would agree dynamic linking is more of a problem than a solution lately. Totally agree with the OP's first, second post and [#20]("http://ubuntuforums.org/showpost.php?p=2390596&postcount=20").

but a combination of both would be desirable.

in linux you never find anything in the middle, it's always one tip of the iceberg or the other. **Developers way or the highway**



anyway this thread is kind of old, it might get closed, but would be good to continue this discussion as it's very interesting to see what solutions we could come up with.

---

### Post by madjr on 2008-07-10
hmm, is there any linux version that uses static libraries for most of it's programs?

something similar to pc-bsd's .pibs?

or some kind of similar system for linux?

and would be good if this was moved to recurring discussions

---

### Post by 23meg on 2008-07-10
Dynamic vs. static linking and dependencies included vs. dependencies not included are two different issues, or non-issues, depending on how one looks at it. See post #6.

[QUOTE=madjr]and would be good if this was moved to recurring discussions[/QUOTE]

It would be good if you read at least some of the past posts before posting.

---

### Post by lzfy on 2008-07-10
Isn't this possible?
- Create packages with all their dependencies in the package.
- During install check first for already installed binary's.
- If a required binary is installed, skip it.
- if not, install it

This way you only would have large packages but who cares about that.

Ps. I'm not an Linux expert, so I don't even know if this is possible or not.

---

### Post by bruce89 on 2008-07-10
> **lzfy said:**
> Isn't this possible?
- Create packages with all their dependencies in the package.
- During install check first for already installed binary's.
- If a required binary is installed, skip it.
- if not, install it

This way you only would have large packages but who cares about that.

Ps. I'm not an Linux expert, so I don't even know if this is possible or not.

They would be incredibly large packages. Your average GUI program requires huge numbers of libraries:

```
bruce@Scooby-Dum:~$ ldd /usr/bin/epiphany-browser 
	linux-gate.so.1 =>  (0xb7f85000)
	libavahi-gobject.so.0 => /usr/lib/libavahi-gobject.so.0 (0xb7f69000)
	libavahi-glib.so.1 => /usr/lib/libavahi-glib.so.1 (0xb7f66000)
	libenchant.so.1 => /usr/lib/libenchant.so.1 (0xb7f5e000)
	libplds4.so.0d => /usr/lib/libplds4.so.0d (0xb7f5b000)
	libplc4.so.0d => /usr/lib/libplc4.so.0d (0xb7f57000)
	libnspr4.so.0d => /usr/lib/libnspr4.so.0d (0xb7f24000)
	libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0xb7f09000)
	libdbus-1.so.3 => /usr/lib/libdbus-1.so.3 (0xb7ed3000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb7e71000)
	libxslt.so.1 => /usr/lib/libxslt.so.1 (0xb7e3d000)
	liblaunchpad-integration.so.1 => /usr/lib/liblaunchpad-integration.so.1 (0xb7e39000)
	libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0xb7e21000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7d02000)
	libgnome-desktop-2.so.2 => /usr/lib/libgnome-desktop-2.so.2 (0xb7cdf000)
	libgnomeui-2.so.0 => /usr/lib/libgnomeui-2.so.0 (0xb7c57000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb7c4f000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7c37000)
	libbonoboui-2.so.0 => /usr/lib/libbonoboui-2.so.0 (0xb7bd9000)
	libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0xb7b80000)
	libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb7b4f000)
	libgnome-2.so.0 => /usr/lib/libgnome-2.so.0 (0xb7b3a000)
	libpopt.so.0 => /lib/libpopt.so.0 (0xb7b32000)
	libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0xb7ad7000)
	libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0xb7ac3000)
	libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0xb7a71000)
	libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb7a5a000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb76e3000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb765f000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7645000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb762d000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7623000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb75e6000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb7584000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7514000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb74ff000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb74d5000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb74b1000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb74a9000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb73c2000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb7399000)
	libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0xb7369000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb7364000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb735a000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7356000)
	libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0xb734d000)
	libpython2.5.so.1.0 => /usr/lib/libpython2.5.so.1.0 (0xb7218000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7200000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb71fc000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb71f7000)
	libffi.so.4 => /usr/lib/libffi.so.4 (0xb71f1000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb71b5000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7104000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7011000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6fec000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6fe0000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6e91000)
	libavahi-common.so.3 => /usr/lib/libavahi-common.so.3 (0xb6e86000)
	libavahi-client.so.3 => /usr/lib/libavahi-client.so.3 (0xb6e77000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb6e5f000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb6e45000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb6e37000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb6e34000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb6e2c000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb6e26000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb6e1c000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb6e19000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6e16000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6e11000)
	libgnome-keyring.so.0 => /usr/lib/libgnome-keyring.so.0 (0xb6e01000)
	libgnutls.so.13 => /usr/lib/libgnutls.so.13 (0xb6d8a000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb6d77000)
	libgailutil.so.18 => /usr/lib/libgailutil.so.18 (0xb6d70000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb6d49000)
	libesd.so.0 => /usr/lib/libesd.so.0 (0xb6d3f000)
	libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb6d19000)
	libORBitCosNaming-2.so.0 => /usr/lib/libORBitCosNaming-2.so.0 (0xb6d14000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6cf3000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6cf1000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6cd8000)
	/lib/ld-linux.so.2 (0xb7f86000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb6cb1000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6cae000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0xb6c9e000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0xb6c50000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb6b8d000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6b88000)
	libgpg-error.so.0 => /lib/libgpg-error.so.0 (0xb6b84000)
```

---

### Post by lzfy on 2008-07-10
> **bruce89 said:**
> They would be incredibly large packages. Your average GUI program requires huge numbers of libraries:

```
bruce@Scooby-Dum:~$ ldd /usr/bin/epiphany-browser 
	linux-gate.so.1 =>  (0xb7f85000)
	libavahi-gobject.so.0 => /usr/lib/libavahi-gobject.so.0 (0xb7f69000)
	libavahi-glib.so.1 => /usr/lib/libavahi-glib.so.1 (0xb7f66000)
	libenchant.so.1 => /usr/lib/libenchant.so.1 (0xb7f5e000)
	libplds4.so.0d => /usr/lib/libplds4.so.0d (0xb7f5b000)
	libplc4.so.0d => /usr/lib/libplc4.so.0d (0xb7f57000)
	libnspr4.so.0d => /usr/lib/libnspr4.so.0d (0xb7f24000)
	libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0xb7f09000)
	libdbus-1.so.3 => /usr/lib/libdbus-1.so.3 (0xb7ed3000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb7e71000)
	libxslt.so.1 => /usr/lib/libxslt.so.1 (0xb7e3d000)
	liblaunchpad-integration.so.1 => /usr/lib/liblaunchpad-integration.so.1 (0xb7e39000)
	libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0xb7e21000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7d02000)
	libgnome-desktop-2.so.2 => /usr/lib/libgnome-desktop-2.so.2 (0xb7cdf000)
	libgnomeui-2.so.0 => /usr/lib/libgnomeui-2.so.0 (0xb7c57000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb7c4f000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7c37000)
	libbonoboui-2.so.0 => /usr/lib/libbonoboui-2.so.0 (0xb7bd9000)
	libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0xb7b80000)
	libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb7b4f000)
	libgnome-2.so.0 => /usr/lib/libgnome-2.so.0 (0xb7b3a000)
	libpopt.so.0 => /lib/libpopt.so.0 (0xb7b32000)
	libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0xb7ad7000)
	libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0xb7ac3000)
	libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0xb7a71000)
	libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb7a5a000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb76e3000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb765f000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7645000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb762d000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7623000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb75e6000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb7584000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7514000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb74ff000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb74d5000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb74b1000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb74a9000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb73c2000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb7399000)
	libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0xb7369000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb7364000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb735a000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7356000)
	libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0xb734d000)
	libpython2.5.so.1.0 => /usr/lib/libpython2.5.so.1.0 (0xb7218000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7200000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb71fc000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb71f7000)
	libffi.so.4 => /usr/lib/libffi.so.4 (0xb71f1000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb71b5000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7104000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7011000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6fec000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6fe0000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6e91000)
	libavahi-common.so.3 => /usr/lib/libavahi-common.so.3 (0xb6e86000)
	libavahi-client.so.3 => /usr/lib/libavahi-client.so.3 (0xb6e77000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb6e5f000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb6e45000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb6e37000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb6e34000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb6e2c000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb6e26000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb6e1c000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb6e19000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6e16000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6e11000)
	libgnome-keyring.so.0 => /usr/lib/libgnome-keyring.so.0 (0xb6e01000)
	libgnutls.so.13 => /usr/lib/libgnutls.so.13 (0xb6d8a000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb6d77000)
	libgailutil.so.18 => /usr/lib/libgailutil.so.18 (0xb6d70000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb6d49000)
	libesd.so.0 => /usr/lib/libesd.so.0 (0xb6d3f000)
	libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb6d19000)
	libORBitCosNaming-2.so.0 => /usr/lib/libORBitCosNaming-2.so.0 (0xb6d14000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6cf3000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6cf1000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6cd8000)
	/lib/ld-linux.so.2 (0xb7f86000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb6cb1000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6cae000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0xb6c9e000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0xb6c50000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb6b8d000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6b88000)
	libgpg-error.so.0 => /lib/libgpg-error.so.0 (0xb6b84000)
```

If you create a package for, let's say Ubuntu 8.04, you know that that distro comes with most of these packages by default. You only include the one which doesn't come with a default install.

---

### Post by bruce89 on 2008-07-10
> **lzfy said:**
> If you create a package for, let's say Ubuntu 8.04, you know that that distro comes with most of these packages by default. You only include the one which doesn't come with a default install.

Still, that's a lot of libraries.

What's wrong with APT's dependency management?

---

### Post by VON_CAPO on 2008-07-11
> **bruce89 said:**
> 
What's wrong with APT's dependency management?
Actually nothing is wrong if you only depends of the official repository.

But, when I switched to Linux I did it after I considerated all the equivalent software (only some of them is in the official repository).

Soon I realized that is only matter of time and luck for the software I selected to stop working. Then I came back to Windows.

The only hope is the developer or some volunteer's will to keep updating the code to make it work with the current distro version.

Asking for help to the developers they pointed out that a static version of the software is only a temporal relief because soon or later the distros change the way the software must be installed. Also they stressed the idea that is painful for them to make packages for different distros, so they release the source code and is up the user to afford the pain to compilate it against his distro. 

Because my English is not so eloquent, I would like to point to the following address, this guy explain the subject in a very clear way:
 ---> [http://www.kornelix.com/linuxopinion](http://www.kornelix.com/linuxopinion)

---

### Post by lzfy on 2008-07-11
> **VON_CAPO said:**
> Actually nothing is wrong if you only depends of the official repository.

But, when I switched to Linux I did it after I considerated all the equivalent software (only some of them is in the official repository).

Soon I realized that is only matter of time and luck for the software I selected to stop working. Then I came back to Windows.

The only hope is the developer or some volunteer's will to keep updating the code to make it work with the current distro version.

Asking for help to the developers they pointed out that a static version of the software is only a temporal relief because soon or later the distros change the way the software must be installed. Also they stressed the idea that is painful for them to make packages for different distros, so they release the source code and is up the user to afford the pain to compilate it against his distro. 

Because my English is not so eloquent, I would like to point to the following address, this guy explain the subject in a very clear way:
 ---> [http://www.kornelix.com/linuxopinion](http://www.kornelix.com/linuxopinion)

+ Try installing apps in an Ubuntu box which isn't connected to the internet. You download the app somewhere else, put it on a usb stick, come home to install it and realize that you  need to download other packages to install it. I had this problem when I was offline for 3 months. Ubuntu was pretty useless for me.

---

### Post by madjr on 2008-07-11
> **23meg said:**
> 

It would be good if you read at least some of the past posts before posting.

i did read them before posting

but you didn't read mine #34

---

### Post by LaRoza on 2008-07-11
> **lzfy said:**
> + Try installing apps in an Ubuntu box which isn't connected to the internet. You download the app somewhere else, put it on a usb stick, come home to install it and realize that you  need to download other packages to install it. I had this problem when I was offline for 3 months. Ubuntu was pretty useless for me.

Some applications are static linked. It is the same problem with Windows.

I started using Ubuntu when I had no internet (Dapper, even) and I found it useful (as useful as it can be without the net)

---

### Post by bruce89 on 2008-07-11
> **VON_CAPO said:**
> Actually nothing is wrong if you only depends of the official repository.

But, when I switched to Linux I did it after I considerated all the equivalent software (only some of them is in the official repository).

Soon I realized that is only matter of time and luck for the software I selected to stop working. Then I came back to Windows.

The only hope is the developer or some volunteer's will to keep updating the code to make it work with the current distro version.

Asking for help to the developers they pointed out that a static version of the software is only a temporal relief because soon or later the distros change the way the software must be installed. Also they stressed the idea that is painful for them to make packages for different distros, so they release the source code and is up the user to afford the pain to compilate it against his distro.

Contrary to popular belief, developers tend to only care that their source compiles. It's up to someone else to package it for all the distros. Also, non-official packages tend to be badly made.

---

### Post by madjr on 2008-07-11
> **LaRoza said:**
> Some applications are static linked. It is the same problem with Windows.


some examples?

---

### Post by LaRoza on 2008-07-11
> **madjr said:**
> examples?

Of what?

I am not going to go spend the time to look up specific projects. Many Windows apps use the Windows API (which is part of Windows) so their dependencies are reduced and many Windows installers install dependencies just like .deb's do (install something, then go see how many DLL's it added). Windows wasn't designed the same way as Linux. Linux is network oriented and Windows isn't. Linux has repositories; Windows has stores that sell licenses to use shiny disks. 

The required libraries for Windows are often GTK+, wxWidgets, ActivePerl, ActivePython, wxPython, etc.

---

### Post by KingTermite on 2008-07-11
Like anything, you should use the right tool for the right job. It's not an apples to apples comparison really.

Basic rule (*my* basic rule anyway) is that if I create a library that may be used by future apps because it is so generic, it should be dynamic so I can easily use it. Also, others could potentially use it if its there.

If its something that's really unique to my own project, then making it dynamic isn't really going to buy me anything (unless its something that only rarely needs to be used/loaded).

That all being said, the term "DLL Hell" didn't derive for no good reason. Managemnt can by ugly. To me if you want dynamic libraries, still keep them in "your" place, not in global space for everybody.

Example, if I wanted to create KTApp, I might strucutre installation like:

/etc/KTSoftware/KTApp

with

/lib/KTSoftware for libraries *(or wherever dynamic libraries generally go...I'm still a bit new with *nix directory structure)*

---

### Post by 23meg on 2008-07-11
> **madjr said:**
> i did read them before posting

but you didn't read mine #34

I can't not have read it, since I quoted you from that post. Again, it rehashes an already addressed point: you mistake a form of packaging for a choice of programming convention.

---

### Post by bruce89 on 2008-07-11
> **madjr said:**
> some examples?

I wrote a small GTK+ program on Windows. The executable was ~0.5 MB. Something must be statically linked there.

---

### Post by FyreBrand on 2008-07-11
> **23meg said:**
> Dynamic vs. static linking and dependencies included vs. dependencies not included are two different issues, or non-issues, depending on how one looks at it. See post #6.
Maybe it would be good if you explained monolithic vs. distributed and static vs. dynamic.  I totally agree with your posts and a lot mixing is going on in this thread.

> **bruce89 said:**
> Contrary to popular belief, developers tend to only care that their source compiles. It's up to someone else to package it for all the distros. Also, non-official packages tend to be badly made.That's not entirely true.  Developers tend to care first that their source compiles and runs well on their primary target(s).  It's not that developers don't care about other platforms or custom environments but that they don't have the time and resources to test every type of environment or scenario.

> **LaRoza said:**
> Of what?

I am not going to go spend the time to look up specific projects. Many Windows apps use the Windows API (which is part of Windows) so their dependencies are reduced and many Windows installers install dependencies just like .deb's do (install something, then go see how many DLL's it added). Windows wasn't designed the same way as Linux. Linux is network oriented and Windows isn't. Linux has repositories; Windows has stores that sell licenses to use shiny disks. 

The required libraries for Windows are often GTK+, wxWidgets, ActivePerl, ActivePython, wxPython, etc.Linux doesn't have repositories, some distributions create repositories of packages they have tested.  These are just networked stores of applications.  Windows does have one repository, Microsoft, that it can query for Windows update.  Many many Windows applications have their networked repositories.  The difference is that Windows doesn't have a centralized management system for OS updates and installed applications.  This has nothing to do with statically linked libraries for applications at compile time and dynamically linked libraries referenced at run time.  Both systems use this.

> **bruce89 said:**
> I wrote a small GTK+ program on Windows. The executable was ~0.5 MB. Something must be statically linked there.If you linked it at compile time and it's part of your executable then it was static.  If you link to a location at run time it's dynamic.  If you package the dynamically linked libraries with your application in a place that only your application references then your install is monolithic.  If you link to libraries available to all applications or the system then your application is distributed.  It's possible to have any combination of those but often apps that are completely statically linked are monolithic.  This can cause confusion when talking about the two.

My opinion:  Debian style package management and dynamically linked distributed installs is one of its biggest strengths and selling points.  This is especially true because of its application repository store.

---

### Post by LaRoza on 2008-07-11
> **bruce89 said:**
> I wrote a small GTK+ program on Windows. The executable was ~0.5 MB. Something must be statically linked there.

Not GTK+ though..

> **FyreBrand said:**
> 
Linux doesn't have repositories, some distributions create repositories of packages they have tested.  These are just networked stores of applications.  Windows does have one repository, Microsoft, that it can query for Windows update.  Many many Windows applications have their networked repositories.  The difference is that Windows doesn't have a centralized management system for OS updates and installed applications.  This has nothing to do with statically linked libraries for applications at compile time and dynamically linked libraries referenced at run time.  Both systems use this.


Ok. Linux distros have repositories. My point was Linux is built on using the largest network. After its initial code base, it was all networked work.

That is why dependencies are not statically linked, because there is the presumption that the connection to the network exists. If **online** sources were targetting computers without network connections, they wouldn't be online.

---

### Post by madjr on 2008-07-11
> **23meg said:**
> I can't not have read it, since I quoted you from that post. Again, it rehashes an already addressed point: you mistake a form of packaging for a choice of programming convention.

i know it's a form of packaging

---

### Post by madjr on 2008-07-11
> **LaRoza said:**
> 

Ok. Linux distros have repositories. My point was Linux is built on using the largest network. After its initial code base, it was all networked work.

That is why dependencies are not statically linked, because there is the **presumption that the connection to the network exists**. If **online** sources were targetting computers without network connections, they wouldn't be online.

exactly, you just pointed out the problem.

i don't know if you agree with the OP or not, but clearly **he has a problem**:

[http://ubuntuforums.org/showpost.php?p=2390596&postcount=20](http://ubuntuforums.org/showpost.php?p=2390596&postcount=20)

if you read that post the only suggestion given was to go use a **Mac**...


maybe we should start steering users to mac.. like Dell recommends windows **Vista** at the Ubuntu section.


> **FyreBrand said:**
> 

Linux doesn't have repositories, some distributions create repositories of packages they have tested.  These are just networked stores of applications.  Windows does have one repository, Microsoft, that it can query for Windows update.  Many many Windows applications have their networked repositories.  The difference is that Windows doesn't have a centralized management system for OS updates and installed applications.  This has nothing to do with statically linked libraries for applications at compile time and dynamically linked libraries referenced at run time.  Both systems use this.

If you linked it at compile time and it's part of your executable then it was static.  If you link to a location at run time it's dynamic.  If you package the dynamically linked libraries with your application in a place that only your application references then your install is **monolithic**.  If you link to libraries available to all applications or the system then your application is distributed.  It's possible to have any combination of those but often apps that are completely statically linked are **monolithic**.  This can cause confusion when talking about the two.

excellent clarification

i wonder if **klik** is like this (monolithic)

[http://klik.atekon.de/](http://klik.atekon.de/)

---

### Post by FyreBrand on 2008-07-11
Not having a network connection can be a big problem.  When I first used Ubuntu I was on dial up and had a WinModem.  It was a real deal breaker.  On the up side it was the motivation for us to change from dial up to DSL.  Not everyone has that option though.

---

### Post by LaRoza on 2008-07-11
> **madjr said:**
> exactly, you just pointed out the problem.

i don't know if you agree with the OP or not, but clearly **he has a problem**:

[http://ubuntuforums.org/showpost.php?p=2390596&postcount=20](http://ubuntuforums.org/showpost.php?p=2390596&postcount=20)


Or she could just get the Repos on disk like I did.

---

### Post by madjr on 2008-07-11
> **LaRoza said:**
> Or she could just get the Repos on disk like I did.

the op didn't had a problem with internet connection (well many do)

he had a problem with full **dist-upgrade** just to get a few binaries (as they were **not backported** either):

> Isn't it the time someone designed a Linux OS that lasts years? And how about installing whatever we want in this time, even afterwards?

I am sick of being stuck in some repository. Look at Ubuntu: it's all whistles and bells until one realizes one cannot install new software. Please don't tell me to upgrade, it's NOT NORMAL to upgrade the whole distro just to have a newer version of the web browser.

Gee.

> 
Impatient? How come? Firefox 2 will never hit Dapper's repos. I already recommended him a Mac, but this leaves me wondering: how come they can do it and the OSS community cannot? It's a design decision. Yet, Mac OS X chose differently and won (the user).

Here's a link to a discussion where the user is using Debian sarge and want to be able to use the latest version of OpenOffice.org: [http://www.debianhelp.org/node/3563](http://www.debianhelp.org/node/3563) . In the end it all resumes to dist-upgrade, with some problems on behalf of the X server. This is NOT the way to go for the masses.

also, as i understand **monolithic packages** could work on different distros (hence 1 package for all distros?).

---

