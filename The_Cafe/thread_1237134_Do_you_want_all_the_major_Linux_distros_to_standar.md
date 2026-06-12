---
title: "Do you want all the major Linux distros to standardize on one packaging format?"
date: 2009-08-11
forum: The Cafe
---

### Post by CJ Master on 2009-08-11
For me, YES. I use AUR, but for major distros I think that all moving to one format (I would prefer DEB) would be the best.

---

### Post by fontis on 2009-08-11
Yes.
The differentiation should rely rather on the actual configuration rather than the file format standards.

It's just stupid to fictionalise a minimalistic community to begin with.

---

### Post by cartman640 on 2009-08-11
Yes, I think if there was a standard container (preferably deb), it would make things considerably easier for new users.

---

### Post by mcduck on 2009-08-11
No, that would never happen. You can't at the same time build an OS based on the idea of freedom, and try taking that freedom away from people.

I don't see any way it would be possible to create a packaging format that would be suitable for all the different ideas between different Linux distributions. As long as people have the freedom to develop their own stuff, somebody would just create a new packaging format that fits his needs better.

Besides, as long as software comes from repositories and is installed though package management tools, the format in which it's packaged is meaningless to the user. So if you want to make beginner's life easier, the way to go is to make sure all the software beginners want is available through package manager.

---

### Post by sdlynx on 2009-08-11
I think there should at least be a most used packaging format.  Sure, other ones can exist, but it's really annoying to find a package online and get excited that it comes for linux, however the only package they have is an RPM.

---

### Post by SunnyRabbiera on 2009-08-11
No, it will limit freedom and choice.
Besides both are simular enough to eachother to code and compile for.
But maybe more collaboration will help, its the RPM distros that make a mess of things I think as the .deb based distros are more organized... one can use a .deb made for debian in Ubuntu and vice versa most of the time.
But try to install a Redhat RPM in OpenSuse and get (dependency) hell.

---

### Post by Viva on 2009-08-11
No, they are different operating systems, run by different companies, just like Mac and Windows are. They need not have a common format just because they use the same kernel. The most popular distros will get the packaging, If they ever decide to use a standard packaging, I'll create a new one with a different format just because I can.

---

### Post by HappinessNow on 2009-08-11
> **CJ Master said:**
> For me, YES. I use AUR, but for major distros I think that all moving to one format (I would prefer DEB) would be the best.

I do like the idea of the new [standardized packaging format]("http://ubuntuforums.org/showpost.php?p=7767465&postcount=8") called: [botulism]("http://ubuntuforums.org/showpost.php?p=7767381&postcount=13")

[URL="http://ubuntuforums.org/showpost.php?p=7767381&postcount=13"]
[/URL]

---

### Post by khelben1979 on 2009-08-11
> **SunnyRabbiera said:**
> No, it will limit freedom and choice.

Agreed.

---

### Post by starcannon on 2009-08-11
I don't care, which means not yes, and not no. Free in FOSS means Libre; if I were to want to dictate what all the major distro's do or don't do with regards to package management or any other issue, I'd be involved in the killing of the very freedom that sets GNU/Linux apart from the other 2 options.

Would I enjoy more standards within the lions share of linux? Sure, there are great benefits too be had; would I ever impose that desire if I had the power? Certainly not.

---

### Post by ibutho on 2009-08-11
> **SunnyRabbiera said:**
> No, it will limit freedom and choice.
Besides both are simular enough to eachother to code and compile for.
But maybe more collaboration will help, its the RPM distros that make a mess of things I think as the .deb based distros are more organized... one can use a .deb made for debian in Ubuntu and vice versa most of the time.
But try to install a Redhat RPM in OpenSuse and get (dependency) hell.

To be frank, I don't agree that RPM based distros make a mess of stuff. You have to realise that most distros using Debs are direct descendents of Debian, which usually means that any Deb package will just work (although not always true). Many RPM based distros are not related at all (SUSE was initially based on Slackware, Red Hat built their own base, Mandriva forked from Red Hat over 10 years ago, Yoper is not directly related to the other distros I mentioned etc). Although they share the same packaging tools, it makes sense that the packages are not compatible because these distros are not built on the same base. RPM is even used in non Linux operating systems like AIX and FreeBSD (not as the main package manager, but for their Linux compatibility layer).

Personally I am not bothered about standardising on one package format. I wouldn't even spend time thinking about it, because it just won't happen. The freedom of choice in Linux and opensource projects prevents such a thing from happening.

---

### Post by 3rdalbum on 2009-08-11
What would one standard packaging format actually achieve?

Think about it. Let's say Fedora switches to Debian packages. You try to install the .deb for Skype on Fedora. It won't install, because of missing dependencies.

Oh yes, Fedora has the same libraries as Debian, but **with different package names**.

What is ACTUALLY needed is some metapackage standards across the distributions, so you can install groups of packages using the same name on any distribution.

The actual package format is the easy part; you can convert between them. But there's no Linux package manager yet today that knows that Fedora uses the name "libqt-4.0-devel" and Debian uses "libqt4-dev" for the same package, and can make allowances for this.

We need standard package **names**!

---

### Post by &#32 Greg on 2009-08-11
> **3rdalbum said:**
> 
We need standard package **names**!

Or a system transparent enough that you can just edit the dependencies to be correct...

---

### Post by ZankerH on 2009-08-11
No, damnit, that's the point of having seperate distributions, giving users the freedom of choice. Also, good luck with persuading source-based distros to adopt debs and apt, which the majority of the contributions to the poll seem to indicate. Why the hell would you want standard packaging, anyway? There already are standard packages, it's called the source code. Anything else is  distribution-specific by definition.

This thread is dumb.

---

### Post by koshatnik on 2009-08-11
> **SunnyRabbiera said:**
> No, it will limit freedom and choice.
Besides both are simular enough to eachother to code and compile for.
But maybe more collaboration will help, its the RPM distros that make a mess of things I think as the .deb based distros are more organized... one can use a .deb made for debian in Ubuntu and vice versa most of the time.
But try to install a Redhat RPM in OpenSuse and get (dependency) hell.

I tried OpenSuse 11.1 the other day, just out of interest. O-M-G. I ran back to Ubuntu pretty quickly. The package management is just appalling. debian based distro's just have it nailed. Nothings perfect I know, but christ it made me grateful for apt.

---

### Post by Simian Man on 2009-08-11
Actually according to the [Linux Standard Base]("http://www.linuxfoundation.org/collaborate/workgroups/lsb"), RPM is already the standard Linux package format :).

[quote=koshatnik]
I tried OpenSuse 11.1 the other day, just out of interest. O-M-G. I ran back to Ubuntu pretty quickly. The package management is just appalling. debian based distro's just have it nailed. Nothings perfect I know, but christ it made me grateful for apt.
[/quote]
That's just because you are used to apt.

---

### Post by koshatnik on 2009-08-11
> **Simian Man said:**
> Actually according to the [Linux Standard Base]("http://www.linuxfoundation.org/collaborate/workgroups/lsb"), RPM is already the standard Linux package format :).


That's just because you are used to apt.

I did think about that, then I thought, no, it really is a pile of crap.

---

### Post by issih on 2009-08-11
All for it...don't really care which, its a simple core system component, it should be standard. In the same way as most major distros use a pretty much standard kernel.

We need to stop wasting time and effort duplicating things that are pointless and solved, can we now get on with doing new things please?

---

### Post by RiceMonster on 2009-08-11
No, especially since it would be deb or rpm and I don't think either are that great.

---

### Post by Simian Man on 2009-08-11
> **koshatnik said:**
> I did think about that, then I thought, no, it really is a pile of crap.

OK so you don't like it, but don't propagate this myth that apt is somehow superior to other package management systems without giving any actual reasons.  It is just FUD and a lot of people here only have used Ubuntu and they will believe your BS.

---

### Post by koshatnik on 2009-08-11
> **Simian Man said:**
> OK so you don't like it, but don't propagate this myth that apt is somehow superior to other package management systems without giving any actual reasons.  It is just FUD and a lot of people here only have used Ubuntu and they will believe your BS.

I didnt propagate any myth, I stated my opinion in a public forum. You took offence to that. What are you anyway, Mr RPM? Did you invent it or something? I know apt isnt perfect, I said that, nothing is, not even me. :)  But I've used jsut about every package management going (darwin ports, portage, slapt-get, apt etc etc etc yadda yadda) and they all have their faults and nuances. But opensuse's was, for me, just fricking awful.

Now unbunch your panties grow up and deal with the fact that some people have opinions different to your own.

---

### Post by Tibuda on 2009-08-11
I don't think it would be bad, but it would require a lot a work to migrate the distros.

---

### Post by Exodist on 2009-08-11
GNU Linux Disrtos will eventually have to if they ever truly expect to surpass windows user base. Also Game developers will never take the time to release 5 or 15 different packages for a game. Wich is a hard true reason so many dont.

---

### Post by RiceMonster on 2009-08-11
> **Simian Man said:**
> OK so you don't like it, but don't propagate this myth that apt is somehow superior to other package management systems without giving any actual reasons.  It is just FUD and a lot of people here only have used Ubuntu and they will believe your BS.

Agreed. I've used both deb and rpm. I prefer Fedora to Ubuntu, but in terms of packaging systems, I find them to be about on the same level. Installing an rpm isn't any harder than installing a deb, and using yum is almost identical to using apt (yum install = apt-get install, yum remove = apt-get remove, etc). 

Neither rpm or deb are bad, but I personally prefer something simpler like pacman/abs, because it's easier to make packages.

---

### Post by Tibuda on 2009-08-11
> **Exodist said:**
> Also Game developers will never take the time to release 5 or 15 different packages for a game. Wich is a hard true reason so many dont.

They don't have to. They can use a binary auto-executable installer, just like they do in Windows (download VMWare Player if you want a freeware example). The package manager is for the distro, not for the ISVs. There are reasons why commercial software are not available for Linux, but the diversity of package formats is not one of them.

---

### Post by Simian Man on 2009-08-11
> **koshatnik said:**
> I didnt propagate any myth, I stated my opinion in a public forum. You took offence to that. What are you anyway, Mr RPM? Did you invent it or something? I know apt isnt perfect, I said that, nothing is, not even me. :)  But I've used jsut about every package management going (darwin ports, portage, slapt-get, apt etc etc etc yadda yadda) and they all have their faults and nuances. But opensuse's was, for me, just fricking awful.


My mistake, I'm just used to people giving reasons for things they say rather than passing down opinions like Moses coming down the mountain.  Do you happen to have reasons for not liking Opensuse's package management or was it just the wrong color for you?

Besides you didn't even clarify whether you meant rpm, zypper or yast.

---

### Post by ZankerH on 2009-08-11
> **issih said:**
> All for it...don't really care which, its a simple core system component, it should be standard. In the same way as most major distros use a pretty much standard kernel.

We need to stop wasting time and effort duplicating things that are pointless and solved, can we now get on with doing new things please?

Wrong, package management is not a "core" component, in fact, a lot of distros don't even use a package management system in the way ubuntu does. And the kernel is in no way standard or identical across the board, even ubuntu uses a distro-specific kernel. Stop pulling facts out of your ***.

While we're at it, why don't we just create a single "standard " GNU/Linux distro? In fact, if you want standards, we might as well all just use the de facto standard in desktop OS, and I'm sure everyone realises which one that is.

The fact is, GNU/Linux distributions were created with the express purpose of modifying the original version - ie, **not abiding to standards**. Doing the opposite defeats their purpose - giving users choice.

---

### Post by koshatnik on 2009-08-11
> **Simian Man said:**
> My mistake, I'm just used to people giving reasons for things they say rather than passing down opinions like Moses coming down the mountain.  Do you happen to have reasons for not liking Opensuse's package management or was it just the wrong color for you?

Besides you didn't even clarify whether you meant rpm, zypper or yast.

I think its a toss up between the colour, and the endless dependency BS I had to endure to install one simple package. 

Thinking about it, it was the colour. I just love dependency problems in linux.

Also, I think you need to look up what opinion means. And then I think you need to stop taking things so personally. Its a computer we're talking about here. Computers suck. They never work properly. Just some suck slightly less than others.

---

### Post by ZankerH on 2009-08-11
> **koshatnik said:**
> I think its a toss up between the colour, and the endless dependency BS I had to endure to install one simple package. 

Thinking about it, it was the colour. I just love dependency problems in linux.

The fact you're unable to get a simple piece of software thousands other users have no problems with to work properly doesn't mean it's flawed by design.

---

### Post by Simian Man on 2009-08-11
> **RiceMonster said:**
> Agreed. I've used both deb and rpm. I prefer Fedora to Ubuntu, but in terms of packaging systems, I find them to be about on the same level. Installing an rpm isn't any harder than installing a deb, and using yum is almost identical to using apt (yum install = apt-get install, yum remove = apt-get remove, etc). 

Neither rpm or deb are bad, but I personally prefer something simpler like pacman/abs, because it's easier to make packages.

I agree, pacman is a great package manager; I also like Conary (used in Foresight).

I admit that I prefer rpm mostly cause I have been using it for six years now, people here just often have a strong feeling it is inferior without really knowing what they're talking about.

[quote=koshatnik]
I think its a toss up between the colour, and the endless dependency BS I had to endure to install one simple package.
[/quote]
What package?  I actually like OpenSuse so I will try installing it and if it really is a problem, I'll file a bug.

---

### Post by koshatnik on 2009-08-11
> **ZankerH said:**
> The fact you're unable to get a simple piece of software thousands other users have no problems with to work properly doesn't mean it's flawed by design.

I dont care about thousands of other people. I only care about me.

Next time your car breaks down on an intersection and you are stuck there for hours waiting for a repair, console yourself in the fact that thousands of other people with the same car don't have your problem. That should make you feel a whole lot better about things.

---

### Post by ZankerH on 2009-08-11
> **koshatnik said:**
> I dont care about thousands of other people. I only care about me.

Not quoting the rest due to flawed car analogy.

If that's the case, do as I said - use what works for you. The fact that suse's package manager doesn't work for you is no reason to "want all major Linux[sic] distros to standardize on one packing format".

Care to elaborate why the fact that you don't like a piece of software means all similar pieces of software besides the one you do like should be replaced with the one you like? Because the way I see it, that defeats the purpose of the FLOSS community and GNU/Linux itself.

---

### Post by NovaAesa on 2009-08-11
I voted no. Different OSs should be free to do whatever they want. I betcha this thread is going to get closed :P (or at least moved to recurring discussions).

---

### Post by koshatnik on 2009-08-11
> **ZankerH said:**
> Not quoting the rest due to flawed car analogy.

If that's the case, do as I said - use what works for you. The fact that suse's package manager doesn't work for you is no reason to "want all major Linux[sic] distros to standardize on one packing format".

Care to elaborate why the fact that you don't like a piece of software means all similar pieces of software besides the one you do like should be replaced with the one you like? Because the way I see it, that defeats the purpose of the FLOSS community and GNU/Linux itself.

I love the way in forums, people only hear what they want to, despite it being very clear text in front of them :)

> 
The fact that suse's package manager doesn't work for you is no reason to "want all major Linux[sic] distros to standardize on one packing format".

I agree. Where have I said I wanted all package managers to be the same? I said, using Yast made me appreciate apt more. 

> 
Care to elaborate why the fact that you don't like a piece of software means all similar pieces of software besides the one you do like should be replaced with the one you like?

Its an opinion. In my opinion, it sucked in comparison to my experiences of using apt. Its as valid a point as any made on this thread. Its other people, including yourself, that have implied other things. Read posts properly, don't read into posts.

I've already stated why I didnt like the experience of using it.

---

### Post by Simian Man on 2009-08-11
[QUOTE=koshatnik]I love the way in forums, people only hear what they want to, despite it being very clear text in front of them :)[/quote]
Kind of like how you ignored me when I asked you which package gave you problems :)?

[QUOTE=koshatnik]
Its an opinion. In my opinion, it sucked in comparison to my experiences of using apt. Its as valid a point as any made on this thread. Its other people, including yourself, that have implied other things. Read posts properly, don't read into posts.[/QUOTE]
You didn't really present it as an opinion.  An opinion is "I personally don't like the package management system of OpenSuse, I found that it didn't handle dependencies as well as apt."  Calling something "appalling", "crap" and "fricking awful" without reasons is not.

---

### Post by RiceMonster on 2009-08-11
> **koshatnik said:**
> 
Its an opinion. In my opinion, it sucked in comparison to my experiences of using apt. Its as valid a point as any made on this thread. Its other people, including yourself, that have implied other things. Read posts properly, don't read into posts.
Well that person's opinion is that they disagree with your opinion.

---

### Post by koshatnik on 2009-08-11
> **RiceMonster said:**
> Well that person's opinion is that they disagree with your opinion.

Yeah, and what follows is a discussion. It breaks down when people take things personally. We're discussing a package management system, not someones child. :)  The discussion broke down because people read one thing, and interpretted something else. That's not my fault.

And I'd argue that crap is a valid term for describing an experience.

@simian man, yeah that was rude of me. Sorry. It was some multimedia package I was trying to install in yast that took me half an hour to do, and which took 4.5 seconds in apt. Maybe not a fair comparison, but first impressions count and I wont be rushing back to an rpm distro in a hurry. But if it works for you, cosmic. But I am allowed my opinion on it, and yeah, that has a right to be challenged too.

I think we've all arrived at a very beautiful place now.

---

### Post by RiceMonster on 2009-08-11
> **koshatnik said:**
> Yeah, and what follows is a discussion. It breaks down when people take things personally. We're discussing a package management system, not someones child. :)  The discussion broke down because people read one thing, and interpretted something else. That's not my fault.

Ok fair enough. I thought you were trying to use the "my opinion" argument as a cop-out. It drives me up the wall when people do that.

---

### Post by koshatnik on 2009-08-11
> **RiceMonster said:**
> Ok fair enough. I thought you were trying to use the "my opinion" argument as a cop-out. It drives me up the wall when people do that.

Me too. I don't take anything personally within reason. Opinions are good. So is challenge.

---

### Post by Tipped OuT on 2009-08-11
Yes, .deb

---

### Post by Simian Man on 2009-08-11
> **koshatnik said:**
> Me too. I don't take anything personally within reason. Opinions are good. So is challenge.

I agree, I was definately never offended or angry, sorry if it came across that way.  Just healthy debate :).

---

### Post by ZankerH on 2009-08-11
Well, since you've all happily agreed that a debate is actually a debate, we can continue with the topic at hand: I've yet to see a single good reason for removing the choice of packaging format. And a good rationale why source-based distros and distros who don't use packaging managers should adopt them.

The only "standard" packaging format for Linux is the source code, which is a perfectly good format if you want to install something that isn't in your distro's repositories. For everything else, there's your distro's repositories. I can't see how any normal GNU/Linux user could have a problem with that. If anything, we should work on a graphical and simple way to install from source so as not to scare new users from doing it like it's some occult ritual only programmers and unix gurus are supposed to do.

---

### Post by issih on 2009-08-11
> **ZankerH said:**
> Wrong, package management is not a "core" component, in fact, a lot of distros don't even use a package management system in the way ubuntu does. And the kernel is in no way standard or identical across the board, even ubuntu uses a distro-specific kernel. Stop pulling facts out of your ***.

While we're at it, why don't we just create a single "standard " GNU/Linux distro? In fact, if you want standards, we might as well all just use the de facto standard in desktop OS, and I'm sure everyone realises which one that is.

The fact is, GNU/Linux distributions were created with the express purpose of modifying the original version - ie, **not abiding to standards**. Doing the opposite defeats their purpose - giving users choice.

Um you might want to look up the definition of the phrase "pretty much", have a think about how similar the kernel is from distro to distro then have a nice cup of something that calms you down.

Now lets see, distros that have a package manager...

debian and all off shoots
red hat and all off shoots
suse and all off shoots
Gentoo and all off shoots

its really rare to have a package manager isn't it....I think possibly you are the one spreading FUD here... please define your usage of the word lot...I think even you are going to have to admit that the number of distros without some form of package management lies well below 5% (now that ,I admit, is a number I have pulled out of my ***, but I'm certainly not going to expend the time to prove it as you are the one making a claim that flies in the face of common sense).

As you accurately state this is linux, and people are free to do what they want, but that freedom does not mean that we SHOULD have a million ways to do the same thing just because we are free to.

The package manager is a vital part of the software system for 95-99% of all linux users, and that to my mind makes it a core software component and it should be as standardised as the kernel is across distributions (note the qualifying "as" there...it might stop you getting so stressed out!).

Finally the idea that OSS's raison d'etre is to defy standards is laughable, the majority of OSS software excels at being standards compliant, it is far better than competing proprietary software in most cases. What we suck at is defining standards, we excel at implementing them.

Let me put it this way, you have the right, the absolute right to replace the wheels on your car with any other geometric shape you want, I am not going to stop you, now....do you really want to?

---

### Post by LowSky on 2009-08-11
I use Ubuntu and Arch, and have used Fedora and OpenSuse.
I dont care how a progrma is packaged, but more importantly how it is managed. At this point in the game I should be able to downloada file and double click on it, type my password (or use a root account) to install that program. I shouldn't need to worry about a certain extension like RPM or DEB. It should just work.

So maybe instead of limiting to one method we make them all work...

Thats my stance

---

### Post by running_rabbit07 on 2009-08-11
For all distros to be limited to one type would limit the custumisability of Linux. 

(When people start taking things personally and out of context, one person usually states their opinion is the best then reports the thread to staff and gets it closed so that they have the last word. I have seen it too many times lately.)

---

### Post by running_rabbit07 on 2009-08-11
BTW .yum is missing from the poll.

---

### Post by Bodsda on 2009-08-11
Hmm, I have always thought that tarballs where the unified packaging choice. 

But hey if someone wanted to make debs, rpms and portage trees etc. compatible with everyhing then I think that would be great.

Regards,
Bodsda

---

### Post by RiceMonster on 2009-08-11
> **running_rabbit07 said:**
> BTW .yum is missing from the poll.

Well since yum uses rpm packages, isn't .yum essentially an rpm?

---

### Post by running_rabbit07 on 2009-08-11
> **RiceMonster said:**
> Well since yum uses rpm packages, isn't .yum essentially an rpm?

Why would Adobe offer Flash for rpm and yum if they are the same?

---

### Post by ubudog on 2009-08-11
Yes.  I would prefer DEB because there are already a lot of distros based off Ubuntu that use DEB. :P

---

### Post by ZankerH on 2009-08-11
> The only "standard" packaging format for Linux is the source code, which is a perfectly good format if you want to install something that isn't in your distro's repositories. For everything else, there's your distro's repositories. I can't see how any normal GNU/Linux user could have a problem with that. If anything, we should work on a graphical and simple way to install from source so as not to scare new users from doing it like it's some occult ritual only programmers and unix gurus are supposed to do.

I hate to repeat myself but some people apparently prefer to put words in my mouth rather than read what I wrote.

---

### Post by doorknob60 on 2009-08-11
No. THe debs from different distros would still be incompatible with each other (sometimes anyways) because of different versions of the libraries on your system. That's why Ubuntu and Debian packages are seperate, because they're often not compatible. Linux is about choice, and if you like deb, use a distro that uses deb, that's all there is to it.

---

### Post by SuperSonic4 on 2009-08-11
No I don't think there should be, much as I love pacman

---

### Post by Simian Man on 2009-08-11
> **running_rabbit07 said:**
> Why would Adobe offer Flash for rpm and yum if they are the same?

The rpm package is a simple package that is made to work for all rpm distros, including ones that don't use yum.

The yum package, is actually an rpm file that adds the adobe yum repository to your software sources so that, in addition to downloading FLash, you can get updates through yum and also install other software like the Adobe Reader.

Ricemonster was right, yum is a front-end for rpm just like apt is a front-end for dpkg.

---

### Post by JDShu on 2009-08-11
Yes, I don't care what kind, but it would make my life easier.

---

### Post by running_rabbit07 on 2009-08-11
> **Simian Man said:**
> The rpm package is a simple package that is made to work for all rpm distros, including ones that don't use yum.

The yum package, is actually an rpm file that adds the adobe yum repository to your software sources so that, in addition to downloading FLash, you can get updates through yum and also install other software like the Adobe Reader.

Ricemonster was right, yum is a front-end for rpm just like apt is a front-end for dpkg.

I guess that is understandable. Thanks for the explanation.

---

### Post by ZankerH on 2009-08-11
> **JDShu said:**
> Yes, I don't care what kind, but it would make my life easier.

How? You'd still have to install the package itself separately on each of the distros you run, and the repositories for different distros would still be seperate for obvious reasons. Why does it matter then what the packaging manager is?

---

