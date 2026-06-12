---
title: "My thoughts on Snappy and the future of software distribution"
date: 2016-11-27
forum: Ubuntu, Linux and OS Chat
---

### Post by mintmag on 2016-11-27
So I've tried using a bit of the Snappy system and so far it looks interesting though I think it's too early to tell. I've posted a few threads both here and other places expressing on how I prefer using .exes to install programs; and I still do though on reflection I'm not sure a exe-like system would work in Linux. For Linux specifically my preferred method for the most part is apt. I've also tried pacman and dnf/yum. 

What I like the most about apt is that there's a lot tools and programs for it, allowing you to do some rather interesting things. One of which is creating a local repository without having to use any tools like apt-mirror. I like to create a local repository and save it to an external hard drive with a few added PPA's for good measure. This allows me to take all my programs and drivers as well as theme packs with me wherever I go. You can also write interesting bash scripts for it to change how it behaves as well. Anyway my main issue with Snap packages is that once again it feels like Canonical are re-inventing the wheel here. Snappy will be good for developers that want to make agnostic programs as well as sandbox said programs. But what does this mean for the future of apt? Will it stop being used? I just started getting the hang of it and don't particularly like the idea of having to learn a whole new system. I'd like to see more tools and programs developed for apt as well down the track. apt is mostly controlled with config files and terminal. I'd like to see GUI alternatives appear and no I don't mean synaptic and software center. What are you thoughts.

---

### Post by ian-weisser on 2016-11-27
The differences between apt and snappy, and the roadmap for both, were *thoroughly* hashed out in the community two years ago

Debian will continue to use apt. Ubuntu will continue to be based upon Debian. Ubuntu Desktop will continue to use apt.
Ubuntu Desktop 18.04 is currently planned be available in both apt and snappy flavors.

Snappy was developed to overcome several design problems with the design of late-1990s packaging systems (including rpm and deb).
debs and rpms don't work well on limited-resource devices (phones, tablets, embedded), and are inconvenient for offline devices and some cloud configurations.

Your seemingly-offhand phrase "*[COLOR=#000000]once again it feels like Canonical are re-inventing the wheel here[/COLOR]*" treads quite close to trolling.
A better approach might be for you to ask questions like: 'Why Snappy instead of apt or flatpack or packagekit or other tools?'
There are, in fact, very good answers to those questions.

---

### Post by mikodo on 2016-11-27
> **ian-weisser said:**
> 

Debian will continue to use apt. Ubuntu will continue to be based upon Debian. Ubuntu Desktop will continue to use apt.
Ubuntu Desktop 18.04 is currently planned be available in both apt and snappy flavors.

It is going to be fun to have two installs. One for snappy and one for dpkg.  It's going to be an adventure.

---

### Post by mintmag on 2016-11-27
> **ian-weisser said:**
> 
Your seemingly-offhand phrase "*[COLOR=#000000]once again it feels like Canonical are re-inventing the wheel here[/COLOR]*" treads quite close to trolling.


How so. A better wording might be to say that Linux keeps reinventing the wheel. I don't know the full history of Linux but I know it's not consistent, and Ubuntu is one of the most influential distros. Seriously though why the troll thing?

---

### Post by QIII on 2016-11-27
Some might call it "reinventing the wheel".  Others "experimentation and innovation".

Let us take care to choose our words wisely beforehand, thereby avoiding the need to say "a better wording might be ...".  All the better to avoid even the least appearance of standing in the shadows of bridges.

Let us also keep the thread strictly to the subject rather than allowing it to drift lazily into editorial commentary about parties involved.

---

### Post by Geoffrey_Arndt on 2016-11-28
The innovation in Linux promotes the concept of "Survival of the Fittest" . . . . in this case, software methodologies.   It's too bad MS didn't have more of that spirit of innovation you get with software freedom.   It's a real thing, and Linus Torvalds has many interesting comments about how the open and diverse nature of Linux can be messy but in the end it tends to bring out the best.   

There's plenty of room for several methods to use, depending on your circumstances  . . . A couple recent examples of this are VLC and Etcher . . one using snap, the other using AppImage.   Both work, and both have their place.

---

### Post by mintmag on 2016-11-28
> **Geoffrey_Arndt said:**
> The innovation in Linux promotes the concept of "Survival of the Fittest" . . . . in this case, software methodologies.   It's too bad MS didn't have more of that spirit of innovation you get with software freedom.   It's a real thing, and Linus Torvalds has many interesting comments about how the open and diverse nature of Linux can be messy but in the end it tends to bring out the best.   

There's plenty of room for several methods to use, depending on your circumstances  . . . A couple recent examples of this are VLC and Etcher . . one using snap, the other using AppImage.   Both work, and both have their place.


I guess I was hopping that apt would have more tools made for it. I just created a mini repo designed to update it and took me a while because I miss-typed a character in the configuration file. apt.conf.d is a powerful tool but it's all file and command-line driven. A GUI based set of tools for apt.conf.d would be great. I don't' have a problem with snappy, but I am conserned it will be the only way to install some programs. Can you install from a local snappy file? Every time I try I just get errors and can't launch the program.

---

### Post by Geoffrey_Arndt on 2016-11-28
Yes of course, snaps can be installed locally.    If you can develop Snaps . . . I'd say the odds are high you don't need to be logged in to a snap repo (like Ubuntu Software store).  The snaps must be installed with admin/root authority in that case (local snap) .

But this "newish" technology, like most tech/math/science and so on does require at least the "old College Try" via reading & prep IF you want or actually NEED to understand what the underlying tech is. 

  So, here is one good site to read thoroughly and then put your key notes into a db (like Zim wiki, or DocuWiki) for reference.

Also, here's the info you need to _**before**_ pre-deciding if snaps are good/bad or somewhere in between  . . . . [http://snapcraft.io/](http://snapcraft.io/)

Have a LOT of fun . . . let us know how it goes!  (I think this is really cool stuff, have only installed a few snap-apps, (_**but they work great**_).

---

### Post by ian-weisser on 2016-11-28
> **mintmag said:**
> A GUI based set of tools for apt.conf.d would be great.

One of the really wonderful features of the open-source and Linux communities is that anyone can write software that scratches their itch.
And distribute it to the world.

If you think that there's a demand for more or better apt tools (if so, I agree with you), you can recruit a team of like-minded fellows, collaborate, and create those tools.
You don't need to ask anybody's permission.
All of the Debian and Ubuntu code, collaboration, distribution, and infrastructure tools are free for you and your team to use.

Or, you can join the current apt developers, and help them to improve apt and to implement the features you want.They are not a club or a company - they are an open and welcoming mix of paid software engineers and highly-skilled volunteers. Contributors come and go. They welcome new contributors.
Clarification: 'contributors' means contributing code and patches. They rarely work other people's wishlist ideas.



> **mintmag said:**
> I don't' have a problem with snappy, but I am conserned it will be the only way to install some programs.

Another of the really wonderful features of the open-source and Linux communities is that the developer need not be responsible for distribution...unless they want to be.
Distros distribute. Distros are good at it.

Most of the software in Debian/Ubuntu is contributed by a *package maintainer*, who is rarely the developer.
The developer develops.
The maintainer provides a liaison between developer and distro. The maintainer creates the packages for the distro and triages/upstreams bugs from the distro to the developer.  

If anybody (not the developer) is interested enough is getting the software into apt or snappy, they can learn how and start right away.
There are many teams of volunteers in Debian and Ubuntu doing most of the packaging and maintaining.

---

### Post by sonicwind on 2016-11-29
Ian (or anybody else),

I'm fairly new to Ubuntu and I don't program or anything. I'm strictly an end user, having come from Windows.

I've been reading about snaps recently. One of my questions is what happens to older programs, even those that are still used but maybe no longer have much support.

Am I understanding you correctly that anyone that knows how, can take a program and make a snap of it (for themselves or others) ? If so, I'm guessing we'll eventually see a LOT of existing software made into snaps? I read about how to create a snap but it is above my pay grade.

I also didn't realize that we're eventually going to have to make a choice between an apt or snap version of Ubuntu. Snaps sound interesting but I guess I'd wait until all the programs I use were available as snaps.

Thanks for creating this thread. I hope my questions make sense.

---

### Post by ian-weisser on 2016-11-29
> **sonicwind said:**
> I've been reading about snaps recently. One of my questions is what happens to older programs, even those that are still used but maybe no longer have much support.

Best practice is to migrate away from orphaned software toward supported software.
Debian and Ubuntu regularly drop unsupported software from their repositories.

Anyone can join an open-source software project (or fork it), learn the code, and help maintain it. That's one of the purposes of open-source licences - to encourage community contribution and discourage orphaned code. 

This is very different from other ecosystems where development companies view the code as an owned asset, and are merely selling the use of the compiled binary to you. 
Here, you are not a customer - you are a *participant*. The community encourages participation: Documentation writing, bug triage, testing, packaging, support, etc. We need non-developer volunteers to do all those tasks to make Ubuntu work.



Wait, let's take a step back and talk about the concept of 'support'. Support could mean many things from answering questions to triaging and patching bugs to QA/QC testing.

In the apt ecosystem, most support is handled by volunteers (like this forum, 'answering questions'). Debian and Ubuntu consider a 'supported' package to be 'upstream developers that respond to triaged bug reports'.  Debian and Ubuntu volunteers do the packaging, answering, triaging, upstream the bugs to the developer, and test the patches. Identifying an orphaned package is easy - the developer stops responding to bugs, and the Debian package maintainer notices the absence (Ubuntu gets most packages from Debian, so does not have many maintainers).

Snaps are different, since the distro isn't really involved anymore with testing and integration. Who handles questions and configuration problems and bug reports? How to tell when a snap should be withdrawn because a security vulnerability is discovered or the upstream is abandoned? Those answers have not been hashed out yet.






> **sonicwind said:**
> Am I understanding you correctly that anyone that knows how, can take a program and make a snap of it (for themselves or others) ? If so, I'm guessing we'll eventually see a LOT of existing software made into snaps?

Yes, if the source code license permits.

Example: My favorite game is licensed under an obscure license ('Artistic License') that permits _only_ free redistribution. I can deb-package it, I can snap it. I can contribute the deb and snap to Debian and/or Ubuntu (, Fedora, Suse, etc). I don't need anybody's permission to do any of that - permission is already granted in the license. 
I cannot, however, charge money for the deb or snap under any circumstances. That is specifically prohibited by that particular license.
This is why the license a project chooses matters.



> **sonicwind said:**
> I also didn't realize that we're eventually going to have to make a choice between an apt or snap version of Ubuntu.
Perhaps you have misunderstood.

You can install snaps alongside debs in (apt-based) Ubuntu 16.10 easily and securely, and [I]nobody has proposed changing that!
[/I]It took a lot of work to make that interoperability possible. Use it.
I'm using LibreOffice (Snap) in my 16.04 (apt) Desktop right now. It's great.

You cannot use apt within an (experimental) all-snap version of Ubuntu Desktop, for several reasons. Apt makes assumptions about a Debian-based system that are not valid in an all-snap environment. Maybe that will change, maybe it won't - one of the reasons for the experiment is to find out what works and what doesn't.

---

### Post by sonicwind on 2016-11-29
Thank you so much. I love this forum.

---

### Post by bluemagoo on 2016-11-30
I have Ubuntu Software Center & Software Boutique.  I have found whatever I have needed.  What is the issue that people see with it?  It works, I use it.

---

### Post by mastablasta on 2016-12-01
> **ian-weisser said:**
> 
Debian and Ubuntu regularly drop unsupported software from their repositories.


if they would, then the games section would be nearly empty :)

seriously though they should clean it up a bit. 

as for how it all works - it is exactly as you said.

---

