---
title: "Comparing Apple to Oranges... (Why Linux needs an Apple of it's very own)"
date: 2007-05-20
forum: The Cafe
---

### Post by Adamant1988 on 2007-05-20
> I've many times written about what I think is going on in the Linux world, or what it needs.  Well now I'm going to write what I'm thinking again (like I'm supposed to do) and while not a highly new statement, I intend to show why Linux needs an Apple of it's very own.

First, you might ask why I'm bringing this up?  This is simple, Linux is growing, rapidly, but I don't feel it will be ANY of the major current players that truly bring it 'to the desktop'.  Let's look at the current recipe for desktop success, first...


[ Linky](http://opinunix.blogspot.com/2007/05/comparing-apple-to-oranges-why-linux.html)

As always, comments are welcome.  I normally don't post about these, but I'm kind of interested in hearing YOUR opinions about the matter.  

As always, FLAME ON!

---

### Post by maniacmusician on 2007-05-20
I kind of skimmed over it and on a general level, most of the stuff makes sense. Writing about it is fine and all, but you don't propose any actual solutions.

For example, consider the part about the inclusive packaging format. It would definitely be easier to have one....but as long as Linux keeps its current file heirarchy, it's not going to happen. Properly built deb packages have to refer to certain dependencies, certain libraries that it needs. Other programs are likely going to be using older versions of that library. If you keep adding stuff, there will eventually be conflicts and things will stop working. As long as we have shared iibraries, an inclusive packaging format can't work. An option would be to forego the shared libraries and have each program contain its own libraries, no matter how repetitive it gets or how much space is wasted. This will result in bigger file sizes, etc etc. 

To be honest, I'm not fond of the Ubuntu release system either. Having to build for specific releases is a major pain. We really should be following Debian in repo management; one stable branch that rarely changes, one up to date branch, and one testing branch. What does this mean for the end user?

It means that if they want to stick with one version of Ubuntu, they pick an LTS. If they pick any of the other versions (Edgy, Feisty, non-LTS releases), it should be with the understanding that they will have to upgrade with each new release. It would make things so much simpler.

---

### Post by Adamant1988 on 2007-05-20
> **maniacmusician said:**
> I kind of skimmed over it and on a general level, most of the stuff makes sense. Writing about it is fine and all, but you don't propose any actual solutions.

**For example, consider the part about the inclusive packaging format. It would definitely be easier to have one....but as long as Linux keeps its current file heirarchy, it's not going to happen. Properly built deb packages have to refer to certain dependencies, certain libraries that it needs. Other programs are likely going to be using older versions of that library. If you keep adding stuff, there will eventually be conflicts and things will stop working. As long as we have shared iibraries, an inclusive packaging format can't work. An option would be to forego the shared libraries and have each program contain its own libraries, no matter how repetitive it gets or how much space is wasted. This will result in bigger file sizes, etc etc. **

To be honest, I'm not fond of the Ubuntu release system either. Having to build for specific releases is a major pain. We really should be following Debian in repo management; one stable branch that rarely changes, one up to date branch, and one testing branch. What does this mean for the end user?

It means that if they want to stick with one version of Ubuntu, they pick an LTS. If they pick any of the other versions (Edgy, Feisty, non-LTS releases), it should be with the understanding that they will have to upgrade with each new release. It would make things so much simpler.

I mentioned that in my post (under the Inclusive format section) 

> Now why would an inclusive packaging format be good for users?  Well, firstly is it makes the distributor, the distributor. Availability of the newest application is ALWAYS there, just go to the site, download the file, and you have it.  Next is that it makes most of the software dependency points moot, and unimportant, because it's inclusive.  It has most of the dependencies met, you run into the occasional error but it's usually not a huge deal.  Apple's .dmg is the status quo here.

The cons are that it's bloated of course... applications may load slower, will take up more space, etc.


As for proposing solutions, I don't have the technical skills to make mock-versions, if that's what your suggesting I do. I did try to point out examples of proper execution wherever possible, though.

---

### Post by maniacmusician on 2007-05-20
> **Adamant1988 said:**
> I mentioned that in my post (under the Inclusive format section) 



As for proposing solutions, I don't have the technical skills to make mock-versions, if that's what your suggesting I do. I did try to point out examples of proper execution wherever possible, though.
well neither do I. But, think about it.Fluid, mandatory releases would basically take care of half of the things that you talked about. Of course, it would require a huge effort on behalf of everyone involved with Ubuntu to do something that big, and sadly, they will probably never do it.

---

### Post by Adamant1988 on 2007-05-20
> **maniacmusician said:**
> well neither do I. But, think about it.Fluid, mandatory releases would basically take care of half of the things that you talked about. Of course, it would require a huge effort on behalf of everyone involved with Ubuntu to do something that big, and sadly, they will probably never do it.

Yeah, and it is sad.  This is why my theory is that the future 'Linux desktop' company hasn't even shown itself.

---

### Post by karellen on 2007-05-20
I've read your article and I found it well writen and constructive. unfortunately I don't think that much can be done about the issues you brought in discussion...the reasons not are many and well-known to all linux lovers

---

### Post by cody50 on 2007-05-20
now that the article mentions it, perhaps a release every 6th months for ubuntu is a little overkill. I'd rather they did one per year but made it all the more rock solid and polished.

---

### Post by Adamant1988 on 2007-05-20
> **karellen said:**
> I've read your article and I found it well writen and constructive. unfortunately I don't think that much can be done about the issues you brought in discussion...the reasons not are many and well-known to all linux lovers

Well, I see a couple of possibilities on how to reach this location: 

1) Novell will do it. 

Novell has a well known history of going off and doing their own thing (see: XGL) and then magically releasing it. Ta-DA!

2) Another Vendor will appear, perhaps someone with a vested interest in operating systems of some kind, or perhaps not, we'll see. 

Either way, the group that does this are going to distance themselves from the community as much as possible, but they'll play nice legally.  It will take a company with muscle to make hardware vendors pay attention to them, etc.  So we'll see.

---

### Post by maniacmusician on 2007-05-20
Well, I'm sure there are people around that know Mark personally. Perhaps they need to jostle him to consider a better upgrade system like the one I came up with (which was just an example; it could be worked on and developed more as a spec). 

I'm sure that if the right people brought this up it may get somewhere, as long as it's presented with a rational argument.

---

### Post by karellen on 2007-05-20
> **Adamant1988 said:**
> Well, I see a couple of possibilities on how to reach this location: 

1) Novell will do it. 

Novell has a well known history of going off and doing their own thing (see: XGL) and then magically releasing it. Ta-DA!

2) Another Vendor will appear, perhaps someone with a vested interest in operating systems of some kind, or perhaps not, we'll see. 

Either way, the group that does this are going to distance themselves from the community as much as possible, but they'll play nice legally.  It will take a company with muscle to make hardware vendors pay attention to them, etc.  So we'll see.

I hope so. and novell & red hat are definitely in the position of doing something "heavy" in the dektop market. maybe canonical too

---

### Post by Adamant1988 on 2007-05-20
> **karellen said:**
> I hope so. and novell & red hat are definitely in the position of doing something "heavy" in the dektop market. maybe canonical too

It's on Novell, Red Hat is too busy with other things.

---

### Post by aysiu on 2007-05-20
I agree with a lot of the points, but I don't understand what "inclusive" means. Is it really difficult, for example, for Opera and Skype, for example, to make .deb files for Ubuntu? They make them--I'm just wondering if that's somehow more difficult for them than to make .exe or .dmg files.

I got a little excited when I read the thread title because I thought you were proposing having someone *make* Linux-compatible hardware. One of the things I like about Apple is their approach of tying together the hardware and software--Apple computers for Mac OS X and OS X for Apple computers. Now, I *don't* like the fact that Apple says "You can't legally install OS X on a non-Apple computer," but it'd be nice if there were computers built for a particular Linux distro and that same particular Linux distro built for a set of four of five hardware models. It is too much to ask Linux developers to make the kernel work with every piece of hardware in existence. If it *does* work, that's a bonus, but with no set of made-for-Linux hardware, Linux developers are currently expected to have Linux be compatible with *everything*. Not fair, and it makes Linux look as if it doesn't "just work" and that Mac does "just work."

As for what you call *backward compatibility*, I just call that *common sense*. I've seen it happen only a few times on these forums, but when it does happen, it boggles my mind. Why would a certain hardware be detected and work in Breezy and suddenly stop working in Dapper? Or work perfectly fine in Edgy and then not work in Feisty?

There are a few distros that do have corporate backing, though--Red Hat, SuSE, Ubuntu.

Some interesting ideas. Don't know where, practically speaking, to go from there, though.

---

### Post by Adamant1988 on 2007-05-20
> **aysiu said:**
> I agree with a lot of the points, but I don't understand what "inclusive" means. Is it really difficult, for example, for Opera and Skype, for example, to make .deb files for Ubuntu? They make them--I'm just wondering if that's somehow more difficult for them than to make .exe or .dmg files.

I got a little excited when I read the thread title because I thought you were proposing having someone *make* Linux-compatible hardware. One of the things I like about Apple is their approach of tying together the hardware and software--Apple computers for Mac OS X and OS X for Apple computers. Now, I *don't* like the fact that Apple says "You can't legally install OS X on a non-Apple computer," but it'd be nice if there were computers built for a particular Linux distro and that same particular Linux distro built for a set of four of five hardware models. It is too much to ask Linux developers to make the kernel work with every piece of hardware in existence. If it *does* work, that's a bonus, but with no set of made-for-Linux hardware, Linux developers are currently expected to have Linux be compatible with *everything*. Not fair, and it makes Linux look as if it doesn't "just work" and that Mac does "just work."

As for what you call *backward compatibility*, I just call that *common sense*. I've seen it happen only a few times on these forums, but when it does happen, it boggles my mind. Why would a certain hardware be detected and work in Breezy and suddenly stop working in Dapper? Or work perfectly fine in Edgy and then not work in Feisty?

There are a few distros that do have corporate backing, though--Red Hat, SuSE, Ubuntu.

Some interesting ideas. Don't know where, practically speaking, to go from there, though.

Aysiu, it's great to hear your thoughts on my post, I have a great respect for your opinions as they're usually VERY solid.  What I meant by 'inclusive' is "dependencies included" (similar to the .dmg file)  I took the opportunity to look at the difference in the opera .exe, .dmg, and .deb files and this is what I found: 

Opera's Windows .exe files for English only is 4.7 mb.  the default international is 6.3 megabytes. 
The .deb file for opera is 5.4 MB
and the .dmg file for opera weighs in at 11.3 MB


Now, seemingly the .deb being the lightest includes less dependency wise, but I would be interested in seeing how it was packaged.  Perhaps the reason for Opera's heavy .dmg file is that it needs to be inclusive enough to run without actually being installed(so all major dependencies met).  I typically think of the.exe standard as fairly inclusive but I'm guessing that perhaps it's not as inclusive as .dmg in terms of dependencies..

---

### Post by aysiu on 2007-05-20
With our current model, would it be advisable to encourage application developers to make .deb files that include all the necessary dependencies? And, if so, would it be possible for the package manager to then still keep only one version of each library (so if the libraries included with the .deb are newer, they get updated, and if they're older, they don't get installed)?

Even if people don't think "inclusive" packaging is a desirable objective in general, it certainly would benefit users who are currently without internet. Right now, these people have to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and track down all the dependencies individually--kind of annoying.

---

### Post by Adamant1988 on 2007-05-20
> **aysiu said:**
> With our current model, would it be advisable to encourage application developers to make .deb files that include all the necessary dependencies? And, if so, would it be possible for the package manager to then still keep only one version of each library (so if the libraries included with the .deb are newer, they get updated, and if they're older, they don't get installed)?

Even if people don't think "inclusive" packaging is a desirable objective in general, it certainly would benefit users who are currently without internet. Right now, these people have to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and track down all the dependencies individually--kind of annoying.

If the dependencies for a .deb file could be included in the .deb itself (which I'm still not convinced that Opera DOES) then I would absolutely applaud application developers packaging inclusive .deb files, even if they are much larger.

---

### Post by Rhox on 2007-05-20
Slowing the releases down won't really do anything. It's not hard to support Linux because it changes so fast. It's hard to support Linux because it varies so much between distros. In fact it's pretty foolish to expect the people who make applications to provided even 20 packages.

---

### Post by aysiu on 2007-05-20
Well, that point is moot, actually. Most of the time, they'll make one .deb package and one .rpm package and that's about it. If Ubuntu becomes *the* dominant desktop distro, all they'll need to make is a .deb.

---

### Post by Adamant1988 on 2007-05-20
> **Rhox said:**
> Slowing the releases down won't really do anything. It's not hard to support Linux because it changes so fast. It's hard to support Linux because it varies so much between distros. In fact it's pretty foolish to expect the people who make applications to provided even 20 packages.

Hardware vendors do not need to support 'Linux' they need to support a single 'desktop' distribution.  However, it costs time and money to certify an entire line of PC hardware against a distribution that operates on a 6 month release schedule.  

Using Inclusive packaging will make the age of the distribution irrelevant, allowing for slower, more feature rich releases.

---

### Post by Rhox on 2007-05-20
> **Adamant1988 said:**
> Hardware vendors do not need to support 'Linux' they need to support a single 'desktop' distribution.  However, it costs time and money to certify an entire line of PC hardware against a distribution that operates on a 6 month release schedule.  

Using Inclusive packaging will make the age of the distribution irrelevant, allowing for slower, more feature rich releases.

A vendor wouldn't need to certify hardware for a distro just kernels. Debs are inclusive (at least at the distro level).

---

### Post by Adamant1988 on 2007-05-20
> **Rhox said:**
> A vendor wouldn't need to certify hardware for a distro just kernels. Debs are inclusive (at least at the distro level).

I was completely unaware that .deb files had the ability to contain dependencies of the application they held. 

Also, yes, a vendor needs to certify against distributions, it is a rare thing for a distribution to use a stock kernel.  Ubuntu's kernel has about 200 MB (Correct me if I'm wrong) of additional drivers, modules, etc.

---

### Post by FuturePilot on 2007-05-20
You made a lot of good points, one thing I disagree with is the need for a universal package format. Although it would unify Linux a lot more, it would be too Windows-ish were people go around downloading random files off the internet.

---

### Post by hanzomon4 on 2007-05-20
Nice article, I agree for the most part. OSX is good example of taking OSS to a new level. However it would be a waste to the community if this "Company" did the apple thing and close source it's neat innovations like Apple did with the lovely Aqua gui. The one thing I really like in your blog, and from apple, is the Appdir/.dmg thing. Somethings like klik, rox appdirs, and Gobolinux already give us this kind of functionality but, like you mentioned, these solutions don't feel like they're a part of TheSystem... more like half fitting puzzle pieces.  

But I don't really see this as something Gnu/linux needs, in this case I view linux as a resource said "company" could rely on to make a killer product

---

### Post by Rhox on 2007-05-20
> **Adamant1988 said:**
> I was completely unaware that .deb files had the ability to contain dependencies of the application they held. 

Also, yes, a vendor needs to certify against distributions, it is a rare thing for a distribution to use a stock kernel.  Ubuntu's kernel has about 200 MB (Correct me if I'm wrong) of additional drivers, modules, etc.

I'm not referring to vanilla kernels just kernels.

---

### Post by Adamant1988 on 2007-05-20
> **FuturePilot said:**
> You made a lot of good points, one thing I disagree with is the need for a universal package format. Although it would unify Linux a lot more, it would be too Windows-ish were people go around downloading random files off the internet.

No no no no no no no no no no no no no no no no no no no no NO!
I DID NOT ask for a universal packaging format.  I do not even care if one single other distribution chooses to adopt an inclusive packaging format, SO LONG as 'THE' distribution is using an inclusive packaging format.  I don't expect .dmg files to be working on Free-BSD, why should I expect this format to do any different? 

But you are right, for this one distribution, people would go around downloading random things off of the internet.  But that's the price you pay.

---

### Post by FuturePilot on 2007-05-20
> **Adamant1988 said:**
> No no no no no no no no no no no no no no no no no no no no NO!
I DID NOT ask for a universal packaging format.  I do not even care if one single other distribution chooses to adopt an inclusive packaging format, SO LONG as 'THE' distribution is using an inclusive packaging format.  I don't expect .dmg files to be working on Free-BSD, why should I expect this format to do any different? 

But you are right, for this one distribution, people would go around downloading random things off of the internet.  But that's the price you pay.
Ah, now I see. I misunderstood you;)

---

### Post by Rhox on 2007-05-20
> **FuturePilot said:**
> You made a lot of good points, one thing I disagree with is the need for a universal package format. Although it would unify Linux a lot more, it would be too Windows-ish were people go around downloading random files off the internet.

They wouldn't install stuff more randomly...

---

### Post by Adamant1988 on 2007-05-20
> **Rhox said:**
> They wouldn't install stuff more randomly...

It doesn't seem to have damaged Macs much.

---

### Post by hanzomon4 on 2007-05-21
Can someone pry open an .exe and .dmg file to see whats in it?

---

### Post by PartisanEntity on 2007-05-21
Good post Adam, I am in agreement with the points you raise. Especially the one about an open repository as opposed to a closed one which IMO seems to really limit the possibilities.

---

### Post by mech7 on 2007-05-21
> **FuturePilot said:**
> You made a lot of good points, one thing I disagree with is the need for a universal package format. Although it would unify Linux a lot more, it would be too Windows-ish were people go around downloading random files off the internet.

Yeah this does not happen now offcourse nobody downloads stuff randomly with a dozen or so formats to install something 0_o

---

### Post by Adamant1988 on 2007-05-21
> **hanzomon4 said:**
> Can someone pry open an .exe and .dmg file to see whats in it?

these files include their dependencies to differing degrees. Apparently the .dmg file includes prety much everything.

---

### Post by Adamant1988 on 2007-05-21
> **aysiu said:**
> I agree with a lot of the points, but I don't understand what "inclusive" means. Is it really difficult, for example, for Opera and Skype, for example, to make .deb files for Ubuntu? They make them--I'm just wondering if that's somehow more difficult for them than to make .exe or .dmg files.

I got a little excited when I read the thread title because I thought you were proposing having someone *make* Linux-compatible hardware. One of the things I like about Apple is their approach of tying together the hardware and software--Apple computers for Mac OS X and OS X for Apple computers. Now, I *don't* like the fact that Apple says "You can't legally install OS X on a non-Apple computer," but it'd be nice if there were computers built for a particular Linux distro and that same particular Linux distro built for a set of four of five hardware models. It is too much to ask Linux developers to make the kernel work with every piece of hardware in existence. **If it *does* work, that's a bonus, but with no set of made-for-Linux hardware, Linux developers are currently expected to have Linux be compatible with *everything*. Not fair, and it makes Linux look as if it doesn't "just work" and that Mac does "just work."**

As for what you call *backward compatibility*, I just call that *common sense*. I've seen it happen only a few times on these forums, but when it does happen, it boggles my mind. Why would a certain hardware be detected and work in Breezy and suddenly stop working in Dapper? Or work perfectly fine in Edgy and then not work in Feisty?

There are a few distros that do have corporate backing, though--Red Hat, SuSE, Ubuntu.

Some interesting ideas. Don't know where, practically speaking, to go from there, though.

Right, this is the exact reason I proposed striking a deal with a hardware vendor.  Trying to force linux to run on everything on God's green earth is just too much, hardware support would be flawless for this hardware company's products.

---

### Post by PartisanEntity on 2007-05-21
It's going to be quite hard at the moment, to strike a deal with hardware vendors. But what could be done, is for the developers to select several motherboards, sound cards, graphics cards etc. and say "These are the officially supported bits of hardware, if you want a fully functioning system buy these".

---

### Post by Adamant1988 on 2007-05-21
> **PartisanEntity said:**
> It's going to be quite hard at the moment, to strike a deal with hardware vendors. But what could be done, is for the developers to select several motherboards, sound cards, graphics cards etc. and say "These are the officially supported bits of hardware, if you want a fully functioning system buy these".

This is precisely the reason that I said the company that does this will have some serious financial muscle.

---

### Post by ablaze on 2007-05-21
> **Adamant1988 said:**
> these files include their dependencies to differing degrees. Apparently the .dmg file includes prety much everything.

Just wanted to make clear that a .dmg-file is simply a disk image. The dmg-file format has nothing to do with Apple's app packages. Non-commandline apps on the Mac are practically a folder with everything in it tha application needs, including the executable binary, icons, interface etc. In the GUI the folder is interpreted as "the app". You can access the package though with control-clicking on it and  selecting "Show package contents". 
The package depends on the system's frameworks, though. It can be possible that some application uses API from Tiger and therefor cannot be run on Panther.

The real benefit of the app bundles/packages of the Mac is, that they are executable anywhere. You have an app on the desktop. Simply double-click it and it will run. Moreover most applications don't need any installation at all. They can be run from CD or from inside the diskimage (dmg-file). 

It would indeed be a great step for Linux if there would be a good solution for this on some kind of distribution. But I guess this should be decided at the Linux Foundation (LSB).

---

### Post by Adamant1988 on 2007-05-21
> **ablaze said:**
> Just wanted to make clear that a .dmg-file is simply a disk image. The dmg-file format has nothing to do with Apple's app packages. Non-commandline apps on the Mac are practically a folder with everything in it tha application needs, including the executable binary, icons, interface etc. In the GUI the folder is interpreted as "the app". You can access the package though with control-clicking on it and  selecting "Show package contents". 
The package depends on the system's frameworks, though. It can be possible that some application uses API from Tiger and therefor cannot be run on Panther.

The real benefit of the app bundles/packages of the Mac is, that they are executable anywhere. You have an app on the desktop. Simply double-click it and it will run. Moreover most applications don't need any installation at all. They can be run from CD or from inside the diskimage (dmg-file). 

It would indeed be a great step for Linux if there would be a good solution for this on some kind of distribution. But I guess this should be decided at the Linux Foundation (LSB).

Oh I see, I'll need to learn more about the format and what it does.

---

### Post by deepwave on 2007-05-21
Err... I liked your article.  Its well written but slightly misguided.

First of all, the definition of platform in the software industry is: a technology that does not provide a concrete solution, but can be extended to do so.  Hence every OS, database and web framework is a platform.  Therefore Linux already is a platform.

Second, hardware vendors only need to communicate with the Linux kernel developers.  At most vendors need to talk to userspace library developers (DBUS, HAL) that connect the kernel libraries to higher level applications.  What Linux needs are hardware vendors willing to cooperate with F/OSS developers.  This means open specs or Linux drivers.

This article from the FSF explains the problem and solution more eloquently.[http://www.fsf.org/resources/hw/how_hardware_vendors_can_help.html]("http://www.fsf.org/resources/hw/how_hardware_vendors_can_help.html")

Third, there are just three popular packages for Linux.  The first two being debs and rpms, that already handle dependencies fairly well.  The third being the source packages for F/OSS, so that distributions that use different packages can compile and re-package the software for their distribution.

Fourth, corporate backing for Linux already exists.  But what really Linux needs more market penetration.  Its a chicken-and-egg problem that every technology (and startup) needs to overcome, called the crossing the chasm.  Linux will only get more popular when we move from early adopters to more pragmatic users.  For most users, Linux already can just work.  Its more of a matter of marketting Linux to the larger, more pragmatic userbase.  Ubuntu and other distributions are already doing that.

I would say Linux does not need to emulate Apple.  Apple still holds a market minority.  What Linux is to meet and surpass the experience that Windows user expect:
[LIST=1]
[*]Hardware that Just Works. Solution: see above.
[*]Games to Run. Needs: Larger market.
[*]Well-known Applications (Photoshop) to Run. Needs: Larger market.
[/LIST]

What I want to say is that there is no "magic bullet" or fix that will make Linux suddenly more popular.  People  just need more exposure to Linux.  Also people need to understand that Linux is not Windows, just like most understand that experience on a Mac is much different than Windows. Not worse, just different. And the real problems of Linux apps need to be addressed: user-unfriendly UIs, lack of documentation, driver insanity.

Sorry in advance for the long rambling post.

---

### Post by karellen on 2007-05-21
>    1. Hardware that Just Works. Solution: see above.
   2. Games to Run. Needs: Larger market.
   3. Well-known Applications (Photoshop) to Run. Needs: Larger market.

I know...it's like a catch-22. we need hardware that works for getting a larger market share (let's be serious, the only real fact that's stopping the hardware manufactures supporting linux it's the simple fact that it has a very little market share) and getting a bigger market share depends of hardware that works and applications. well-know and familiar.
the sad part is that I see no solution for this crucial matter in the near future (even if a move like Dell's is benefical)

---

### Post by igknighted on 2007-05-21
> **cody50 said:**
> now that the article mentions it, perhaps a release every 6th months for ubuntu is a little overkill. I'd rather they did one per year but made it all the more rock solid and polished.

haha, ask Mandriva how that worked out...

You make valid points, and I do personally prefer a rolling release type of distro.  But the stability would never be there.  And I don't think linux wants to move in the direction of every app coming packaged with all dependencies.  To much redundancy, not really the linux way.  I am curious as to how Sabayon's Entropy is going, as that might be something worth looking into.  Also autopackages.  I do want to hit each of his points here:

Monolithic releases: Good for end users who don't want to get involved, but most current linux users wont be pleased.  I like to play with new stuff, and despise Dapper due to its ancient-ness, and its less than a year old.  I know I am not alone here.

Platform:  If you can find a way to distribute the LSB in a release form instead of the kernel, you might be on to something.  The problem here is the modularity of the OS.  In windows, the GUI is built in, you can't do anything about it.  In linux you can.  Same for many other "apps".  The only way to make it a "platform" is to get the distros to release the same LSB.  Not terribly likely, and I'm not sure its a good thing.  But probably worth looking into.  If "linux 2.6.21" meant the whole LSB it would make it much easier for 3rd parties to build on.

Hardware Support: The way to go is to release working hardware with the OS... that is in an OEM setup.  Once people buy a linux computer that "just works" and costs less, theres your in.  But you need a real advertising campaign, idk if Dell has the backbone to do that.  I wish Mark would spend his money on that rather than ANOTHER distro, TBH.  I like Ubuntu, but its one more amongst thousands.  A good advertising campaign and an OEM would do wonders.

Overall, linux is in a good place.  Popularity is growing, Dell is now on board, ATI might open their drivers... Lets be honest, why do we want a market majority?  All it will lead to is corruption of the linux ideals.  Lets make our product and make it as good as we can, and let people use it as they want.  But lets not make the OS to trick the average joe into using it.  Lets make it good like we want it.  And if joe wants to, he can use it too.

---

### Post by Adamant1988 on 2007-05-21
> **deepwave said:**
> Err... I liked your article.  Its well written but slightly misguided.

First of all, the definition of platform in the software industry is: a technology that does not provide a concrete solution, but can be extended to do so.  Hence every OS, database and web framework is a platform.  Therefore Linux already is a platform.  

I completely understand this point, but I'm going to argue that a platform that is in constant motion is more difficult to develop for, much more difficult.  This is why I suggested slower, more feature rich releases in combination with an inclusive packaging format the makes the age of the version of Linux itself nearly irrelevant. 

> Second, hardware vendors only need to communicate with the Linux kernel developers.  At most vendors need to talk to userspace library developers (DBUS, HAL) that connect the kernel libraries to higher level applications.  What Linux needs are hardware vendors willing to cooperate with F/OSS developers.  This means open specs or Linux drivers.
Unfortunately, this is not happening at all.  There needs to be an arrangement for at least one distribution to get solid hardware support, even if it's tightly integrated like Apple's stuff. 

> 
Third, there are just three popular packages for Linux.  The first two being debs and rpms, that already handle dependencies fairly well.  The third being the source packages for F/OSS, so that distributions that use different packages can compile and re-package the software for their distribution.

Which is why this distribution will need a 4th, more inclusive format.  People who develop for this platform distribution would NOT be developing for Linux altogether but strictly this distribution.  .dmg is the status-quo here. 
> 
Fourth, corporate backing for Linux already exists.  But what really Linux needs more market penetration.  Its a chicken-and-egg problem that every technology (and startup) needs to overcome, called the crossing the chasm.  Linux will only get more popular when we move from early adopters to more pragmatic users.  For most users, Linux already can just work.  Its more of a matter of marketting Linux to the larger, more pragmatic userbase.  Ubuntu and other distributions are already doing that.

What I mean by this is that this distribution will need a strong company to push it forward, and seriously make it work. 

> I would say Linux does not need to emulate Apple.  Apple still holds a market minority.  What Linux is to meet and surpass the experience that Windows user expect:
Apple is the status quo for desktop success and ease of use, not Windows.  Apple currently has the most powerful combination of software and hardware available to do the most demanding things that your computer can do.  Along with ridiculous ease of use and 'click and drag'-ability. 

> [LIST=1]
[*]Hardware that Just Works. Solution: see above.
[*]Games to Run. Needs: Larger market.
[*]Well-known Applications (Photoshop) to Run. Needs: Larger market.
[/LIST]

1) It is asking too much for the kernel to support everything.  Going the apple route and supporting very specific hardware configurations from hardware manufacturers will provide a stable, trouble free, system.
2) Show me proof that games are that big of a deal.  Consoles are the number one gaming platform out there. 
3) OR we can make our own applications.  No one said that the status quo application of today is going to be tomorrow, open source has the potential, why not harvest that? 
> 
What I want to say is that there is no "magic bullet" or fix that will make Linux suddenly more popular.  People  just need more exposure to Linux.  Also people need to understand that Linux is not Windows, just like most understand that experience on a Mac is much different than Windows. Not worse, just different. And the real problems of Linux apps need to be addressed: user-unfriendly UIs, lack of documentation, driver insanity.

You seem to misunderstand my goals here.  I am not asking for Linux to get popular, in fact, I would rather it didn't.  What I am suggesting happen is that a company do as Apple has done with BSD.  Notice that BSD is still the same ol' community despite Apple's success, it is my hope that this would be a similar deal for the Linux community.  One distribution would see widespread success and probably NEVER mention that it's got Linux underpinnings unless absolutely necessary or if that's what the consumer is obviously interested in.  The rest would continue on about their business.  

Linux is never going to grow past what it's become and becoming, and waiting around for every distribution known to man to magically get more popular is folly.  A strong company can rise out of the mess and really stand out, or maybe an outside company can leverage the power of Linux to build a new operating system, we'll see.  

--------------------------------------------------------------------------------------
[quote=igknighted]
haha, ask Mandriva how that worked out...

You make valid points, and I do personally prefer a rolling release type of distro. But the stability would never be there. And I don't think linux wants to move in the direction of every app coming packaged with all dependencies. To much redundancy, not really the linux way. I am curious as to how Sabayon's Entropy is going, as that might be something worth looking into. Also autopackages. I do want to hit each of his points here:

[/quote]

Again, I'm not proposing this should happen for every Linux distro or Linux in general.  Linux as we know it will always have a niche market that desires it to remain the same. Servers benefit from the lean-mean style of package management that exists today, etc.  Linux in general doesn't have to be 'ready for the desktop', nor should it be.  But the potential for one company, person, or group to make ONE distribution a desktop success is certainly there, and honestly I would prefer that. 

> Monolithic releases: Good for end users who don't want to get involved, but most current linux users wont be pleased. I like to play with new stuff, and despise Dapper due to its ancient-ness, and its less than a year old. I know I am not alone here.

Monolithic, slow, releases could work JUST fine with this distribution using an inclusive packaging format.  You would see many more feature rich developments happen because of this slow, big, release style. 

> Platform: If you can find a way to distribute the LSB in a release form instead of the kernel, you might be on to something. The problem here is the modularity of the OS. In windows, the GUI is built in, you can't do anything about it. In linux you can. Same for many other "apps". The only way to make it a "platform" is to get the distros to release the same LSB. Not terribly likely, and I'm not sure its a good thing. But probably worth looking into. If "linux 2.6.21" meant the whole LSB it would make it much easier for 3rd parties to build on.

Any and all attempts to 'reign in' the Linux community at large, or even just the largest of distributions have failed miserably, and most distributions are half-assing support for the LSB.  Doing the bare minimum.  Again, we're talking about a single distribution doing their own thing, the public would probably never have a CLUE that it was Linux unless they asked.  This distribution would become it's own platform, Linux be-damned, so to speak. Software would be written with DistroX in mind, etc. 
> 
Hardware Support: The way to go is to release working hardware with the OS... that is in an OEM setup. Once people buy a linux computer that "just works" and costs less, theres your in. But you need a real advertising campaign, idk if Dell has the backbone to do that. I wish Mark would spend his money on that rather than ANOTHER distro, TBH. I like Ubuntu, but its one more amongst thousands. A good advertising campaign and an OEM would do wonders.

A large, powerful corporation or even just a respected one could reign in some kind of OEM support for this distribution.  Perhaps (like Apple) it will be a hardware vendor like DELL who CREATES this distribution, we'll see. 

> Overall, linux is in a good place. Popularity is growing, Dell is now on board, ATI might open their drivers... Lets be honest, why do we want a market majority? All it will lead to is corruption of the linux ideals. Lets make our product and make it as good as we can, and let people use it as they want. But lets not make the OS to trick the average joe into using it. Lets make it good like we want it. And if joe wants to, he can use it too.

Oh definitely, the life for true Linux users is certainly improving.  It should remain on track.  One single company creating a strong competitor to Apple and Microsoft out of Linux underpinnings would probably not have a negative effect on our community as they would probably just try to ignore us as much as possible.  Theoretically this company would do for Linux what Apple did for BSD.  Quietly walk away and do their own thing in a corner somewhere and turn it into a success, leaving everyone else to play happily in their sandbox.

---

### Post by koenn on 2007-05-21
Adam, you got it all wrong. 

The main design principle behind Linux is source code, not binaries. By looking at Linux from a binary based point of view, no wonder you find problems. I'll come back to that later. 
When looking at Linux from a "source code" point of view, it already does everything you say it should do. It provides a platform for applications to be **compiled and** run on : you can get any application (that you have the source code for) : you're not limited to repositories, you can choose whatever version is avalaible, and so on.
 That covers ponts 1,2,and 3. The other points are pretty much distro-problems, and distro's are a binary take on a source-oriented reality so I'll ignore them for now. Backward compatibility is not a law set in stone. Take ipchains. It got replaced by iptables. ipchains is going to die, because it was impossible to make it better. To make it better, iptables had to be created. There's no point in maintaining both. This has nothing to do with how Ubunti manages to get something working in one release, and break it again 6 months later - that is just bad. 

Now of course, you're not interested in a "source code point of view", because you're thinking of desktop penetration and the (non ICT technical) end user's Out Of The Box Experience. 
That's what all distro's have been trying to accomplish. To name just a few exemples : 
-- Red Hat invented de binary package to circumvent the "end users don't want to compile" problem
-- Debian set up the "multi-track" repository system: a frozen, stable repo for those who require stability, an ever changing 'testing' and 'unstable" repo where you can get the newer stuff, and even a mechanism to combine packages from each 3 branches on the same system. 
-- Ubuntu's '2 speed' release cycle : the fast and furious 6 months cycle in a (failing ?) attempt to offer the user relatively new software, and the slow-paced LTS releases for stability at the expense of a 'staler' system as time goes by. 
-- Gentoo's "compile to install" approach : deliver binaries by compiling source on demand,  transparant to the user. 

So, when you say "The burden of creating the software package for EVERY other operating system is NOT on the distributor of that system, it is on the developer of the application" - that is only true for a developer who distributes his work in binary form. He will have to provide an installer that installs his binary application on the target OS because there's no other way to install it. For software that is distributed in the form of source code, the native install procedure is : compile it on your system. If a distro decides it wants to deliver binaries to its users/costumors, the burden of packaging is indeed on the distributor. 

You'll understand then that distro's and packaging etc. are workaropunds to deliver binaries in a world that evolves around source code, and therefore they will always have serious downsides.  I'm not convinced that what you're proposing is any better. It's different, and might be better in some cases, but it is by no means a recipy for desktop success. 
In fact, debian comes closest to your goal of a "platform" : once packaged, an application is installable if the repository can satisfay that packages dependencies. Usually, it can. Ubuntu does worse in this respect because, apparently, the set such unnecessary strict versions on dependencies that a package compiled and build for one release will not install on a release of 6 months earlier, while technically, it could. 
So, maybe a new distro should emerge and tackle things the way you propose. Or maybe Ubuntu should revise its packaging standards, methods, and policy. 
That's where I agree with you :   "Currently, the only way to get software out for Ubuntu users, is to get it in the Ubuntu repos, and even then it's only available for people who use THAT version of Ubuntu and who's repos can satisfy the dependencies of your software.  This is problematic.". It's also (just) bad management.

---

### Post by Adamant1988 on 2007-05-21
> **koenn said:**
> Adam, you got it all wrong. 

The main design principle behind Linux is source code, not binaries. By looking at Linux from a binary based point of view, no wonder you find problems. I'll come back to that later. 
When looking at Linux from a "source code" point of view, it already does everything you say it should do. It provides a platform for applications to be **compiled and** run on : you can get any application (that you have the source code for) : you're not limited to repositories, you can choose whatever version is avalaible, and so on.
 That covers ponts 1,2,and 3. The other points are pretty much distro-problems, and distro's are a binary take on a source-oriented reality so I'll ignore them for now. Backward compatibility is not a law set in stone. Take ipchains. It got replaced by iptables. ipchains is going to die, because it was impossible to make it better. To make it better, iptables had to be created. There's no point in maintaining both. This has nothing to do with how Ubunti manages to get something working in one release, and break it again 6 months later - that is just bad. 

Now of course, you're not interested in a "source code point of view", because you're thinking of desktop penetration and the (non ICT technical) end user's Out Of The Box Experience. 
That's what all distro's have been trying to accomplish. To name just a few exemples : 
-- Red Hat invented de binary package to circumvent the "end users don't want to compile" problem
-- Debian set up the "multi-track" repository system: a frozen, stable repo for those who require stability, an ever changing 'testing' and 'unstable" repo where you can get the newer stuff, and even a mechanism to combine packages from each 3 branches on the same system. 
-- Ubuntu's '2 speed' release cycle : the fast and furious 6 months cycle in a (failing ?) attempt to offer the user relatively new software, and the slow-paced LTS releases for stability at the expense of a 'staler' system as time goes by. 
-- Gentoo's "compile to install" approach : deliver binaries by compiling source on demand,  transparant to the user. 

So, when you say "The burden of creating the software package for EVERY other operating system is NOT on the distributor of that system, it is on the developer of the application" - that is only true for a developer who distributes his work in binary form. He will have to provide an installer that installs his binary application on the target OS because there's no other way to install it. For software that is distributed in the form of source code, the native install procedure is : compile it on your system. If a distro decides it wants to deliver binaries to its users/costumors, the burden of packaging is indeed on the distributor. 

You'll understand then that distro's and packaging etc. are workaropunds to deliver binaries in a world that evolves around source code, and therefore they will always have serious downsides.  I'm not convinced that what you're proposing is any better. It's different, and might be better in some cases, but it is by no means a recipy for desktop success. 
In fact, debian comes closest to your goal of a "platform" : once packaged, an application is installable if the repository can satisfay that packages dependencies. Usually, it can. Ubuntu does worse in this respect because, apparently, the set such unnecessary strict versions on dependencies that a package compiled and build for one release will not install on a release of 6 months earlier, while technically, it could. 
So, maybe a new distro should emerge and tackle things the way you propose. Or maybe Ubuntu should revise its packaging standards, methods, and policy. 
That's where I agree with you :   "Currently, the only way to get software out for Ubuntu users, is to get it in the Ubuntu repos, and even then it's only available for people who use THAT version of Ubuntu and who's repos can satisfy the dependencies of your software.  This is problematic.". It's also (just) bad management.

Well, this distribution would (of course) be based on Binaries, as source installations are problematic and take far too long.  I'm suggesting a Binary corporate distribution should exist, akin to Apple's use of BSD (hence the title).  Linux in general should be left alone to do what it does best, let a company harvest that and turn it into something mass marketable.

---

### Post by saulgoode on 2007-05-21
> **Adamant1988 said:**
> Linux in general should be left alone to do what it does best, let a company harvest that and turn it into something mass marketable.

Isn't that what Canonical/Ubuntu is attempting to do?

---

### Post by Adamant1988 on 2007-05-21
> **saulgoode said:**
> Isn't that what Canonical/Ubuntu is attempting to do?

Not from what I've seen.  Canonical and Ubuntu seem to be "just another distro" (TM) by the looks of things.  Same type of package management, fast release schedule, stock gnome, etc.

---

### Post by thunderkyss on 2007-05-22
Cool thread.. good discussion.

But IMHO, I think you're missing the boat all together.

If we want Linux to really compete for the desktop market, I think the main points a distro like Ubuntu will have to address, are Branding, Marketing, and Utiliity.

Branding first and foremost, that's what set Microsoft apart from Appel, Intel from AMD, and Dell apart from Acer. But, branding is going to be difficult for Ubuntu, Red Hat, Suse, or whatever distro, because they don't have a face. They're Linux, and as far as I'm concerned, and the public as well, IMHO is that they're all the same. When you look at a PC running linux, you don't see the distro, you see KDE, Gnome, Xfce... 

Say I'm at the watercooler, I'm telling my buddy how I just recieved my Ubuntu Dell. He proceeds to tell me about his debian powered homebuilt, and all the custom this & that & whatnot's he's got on his computer... & I'm left thinking I didn't get the "real" linux.

Marketing. I don't see how Ubuntu can compete with Apple(those are some great commercials) & Microsoft. Does Ubuntu make any money?? Is Ubuntu even an entity, or is it more a collective??

Utility. When I bought my first PC, I wanted to make sure I'd be able to do something with it. Way back then, there weren't but so many things a person could do with a computer. I went to all the computer outlet & electronics stores in my area, to see what kind of applications were available. I was told since birth, that Macs were better, that they just worked, & that they were easy to operate. But of all the places I visited, only one place had an Apple computer on display(two I think). and it was the only place I could buy programs to run on it. There were 8 aisles, front & back full of PC applications. there was half of one side of one aisle with Apple compatible software. I decided to buy the PC, and never looked back. 

It didn't matter, that I had to fight the thing to get it to work. That I had to boot into DOS to install some applications, and Windows to install others. It didn't matter that I could only run some programs in DOS(DOS mode was a godsend). It didn't matter that I basically spent $1200 for a calculator/typewriter. 

What mattered was that if someone was going to write a program that would allow a home user to publish a professional looking newsletter on the cheap, I'd be able to run down to best buy, & buy the program.

Now, Ubuntu(and Apple) have got the utility thing down. Ubuntu just needs to market it. 

Even after I spent all that time typing about how somethings didn't matter, I'm going to say this one little thing does matter.

When folks have already bit the bullit, and installed Ubuntu on their PCs, and come here to ask for help on how to get this to work, or how to install that, it would be nice if the instructions were something like, "Open synaptic, select  program, click apply"  instead of "sudo apt-get program,   sudo apt-install program" I know it's easier for you guys to do the command line thing, but it's not mainstream, and never will be. 

I can imagine how many people came here for help, & left after learning how "cryptic" this OS really is. Just like K said. A person is smart, people are stupid.

---

### Post by Adamant1988 on 2007-05-22
> **thunderkyss said:**
> Cool thread.. good discussion.

But IMHO, I think you're missing the boat all together.

If we want Linux to really compete for the desktop market, I think the main points a distro like Ubuntu will have to address, are Branding, Marketing, and Utiliity.

Branding first and foremost, that's what set Microsoft apart from Appel, Intel from AMD, and Dell apart from Acer. But, branding is going to be difficult for Ubuntu, Red Hat, Suse, or whatever distro, because they don't have a face. They're Linux, and as far as I'm concerned, and the public as well, IMHO is that they're all the same. When you look at a PC running linux, you don't see the distro, you see KDE, Gnome, Xfce... 

Say I'm at the watercooler, I'm telling my buddy how I just recieved my Ubuntu Dell. He proceeds to tell me about his debian powered homebuilt, and all the custom this & that & whatnot's he's got on his computer... & I'm left thinking I didn't get the "real" linux.

Marketing. I don't see how Ubuntu can compete with Apple(those are some great commercials) & Microsoft. Does Ubuntu make any money?? Is Ubuntu even an entity, or is it more a collective??

Utility. When I bought my first PC, I wanted to make sure I'd be able to do something with it. Way back then, there weren't but so many things a person could do with a computer. I went to all the computer outlet & electronics stores in my area, to see what kind of applications were available. I was told since birth, that Macs were better, that they just worked, & that they were easy to operate. But of all the places I visited, only one place had an Apple computer on display(two I think). and it was the only place I could buy programs to run on it. There were 8 aisles, front & back full of PC applications. there was half of one side of one aisle with Apple compatible software. I decided to buy the PC, and never looked back. 

It didn't matter, that I had to fight the thing to get it to work. That I had to boot into DOS to install some applications, and Windows to install others. It didn't matter that I could only run some programs in DOS(DOS mode was a godsend). It didn't matter that I basically spent $1200 for a calculator/typewriter. 

What mattered was that if someone was going to write a program that would allow a home user to publish a professional looking newsletter on the cheap, I'd be able to run down to best buy, & buy the program.

Now, Ubuntu(and Apple) have got the utility thing down. Ubuntu just needs to market it. 

Even after I spent all that time typing about how somethings didn't matter, I'm going to say this one little thing does matter.

When folks have already bit the bullit, and installed Ubuntu on their PCs, and come here to ask for help on how to get this to work, or how to install that, it would be nice if the instructions were something like, "Open synaptic, select  program, click apply"  instead of "sudo apt-get program,   sudo apt-install program" I know it's easier for you guys to do the command line thing, but it's not mainstream, and never will be. 

I can imagine how many people came here for help, & left after learning how "cryptic" this OS really is. Just like K said. A person is smart, people are stupid.

A lot of those points are really solid, really.  I can agree with most of them, but again I'm going to point back to what seems to be the recipe that current successful desktop systems are utilizing on my blog.  Branding should have been included, a heavy brand is very important.  Perhaps, like with Apple, we'll see a hardware company step in and start making this OS.  Perhaps.

---

### Post by aysiu on 2007-05-22
As far as I know, Ubuntu is not currently making a profit. But, also as far as I know, Ubuntu has not expected to make a profit in its first few years. I do believe it makes money from support (some companies and governments are already using Ubuntu), but with the cost of development and free CD shipping, I'm sure most of the gross profits get eaten away and more keeps coming out of the Ubuntu Foundation and Mark Shuttleworth's pockets.

But Ubuntu is not Linux. Red Hat, for example, makes hundreds of millions of dollars. IBM, Sun, and a bunch of other companies all have something invested in Linux and/or open source development.

Frankly, at this point, I wouldn't market desktop Linux, for a couple of reasons. 

1) There is no major OEM selling it preinstalled--at least not until Thursday... and even that is only in the United States and Canada. Why would you want to market something that people have to download, burn, install, and configure themselves? Good luck with that.

2) Ubuntu and other Linux distros are in a pretty good place now. They have live CDs. They have a lot of good hardware detection. They have more GUI frontends for tasks than ever before. They have package management. They have basic functionality and then some (email, web, music, pictures, word processing, iPod support). **But** they don't yet have the market share yet that will bring in the kinds of third-party support people expect (iTunes, peripherals compatibility labeling, etc.). Ubuntu and desktop Linux in general will continue to grow organically without marketing... at a certain critical mass point (I'd say when the "average computer user" knows at least two people who use desktop Linux regularly), then marketing would be appropriate an extremely beneficial. Right now, it's like pissing money down the drain. Might as well use that money for developing GIMP or OpenOffice.

Don't get me wrong. If people do market desktop Linux or Ubuntu, I won't protest (except for that whole Tux500 thing... don't even get me started on that again) if it's done well, but I do think it'd be more appropriate later.

---

### Post by dca on 2007-05-22
Ubuntu has the same business model as Novell & Red Hat.  Take something that's free and provide service/support for it for a yearly fee.  RedHat & Novell proved this is a viable source of income.  The reason I prefer Ubuntu over the other(s) is they put their money where their mouth is.  For a desktop solution from Novell (SLED10) or RedHat (RHEL5) would cost you over $80 per seat per year.  The same thing from Ubuntu on their LTS releases is free across the board.  You don't have to pay for the support just to get the da*n updates & security patches...

---

### Post by dca on 2007-05-22
...oh, and on a server...
 
$2,499 per year RHEL5
$0 Ubuntu
 
I mean, let's face it, a lot of the bigger shops now have in-house admins for support...

---

### Post by koenn on 2007-05-22
> **saulgoode said:**
> Isn't that what Canonical/Ubuntu is attempting to do?
I kinda had the same feeling. I don't agree with Adam 'an inclusive package format' is necessarily a key to desktop success or even 'turning an OS into a platform'. My point is that the fast release cycle was Ubuntu's attempt to be able to deliver reasonably new software (6 months is fast, given that open source apps usually go by 'release early, release often' - there's a lot of 'beta' out there, and waiting 6 months for a more mature version is fine), 
but it kinda backfired when the unofficial best practise for a version upgrade became : do a clean install. That's what's stopping ubuntu from being  what  Adam calls a platform and turns it in "fast an unexiting releases".

---

### Post by Enverex on 2007-05-22
He said "slower releases are better". I assume he's not aware that binary distros normally version freeze. Which means if you use a 3 year old version of a distro, all the software on it (other than fixes and patches) will be 3 years old. Just think of all the new features you'd be missing out on considering how fast Linux is changing.

---

### Post by igknighted on 2007-05-22
> **Enverex said:**
> He said "slower releases are better". I assume he's not aware that binary distros normally version freeze. Which means if you use a 3 year old version of a distro, all the software on it (other than fixes and patches) will be 3 years old. Just think of all the new features you'd be missing out on considering how fast Linux is changing.

You missed his point.  He wants a package type that would allow users to update apps at will, while leaving their release version at whatever one they installed.

---

### Post by Enverex on 2007-05-22
> **igknighted said:**
> You missed his point.  He wants a package type that would allow users to update apps at will, while leaving their release version at whatever one they installed.

That works now, just grab the newer deb from anywhere. Only time it will fail is if it needs libraries that are a newer version and there's no way around that.

---

### Post by koenn on 2007-05-22
[QUOTE=Opinunix]Releases need to be slower, more feature packed, and more exciting, in my opinion[/QUOTE]. To me, that translates to  "fast and unexiting releases [should be avoided] " or something along those lines. 
[QUOTE=Enverex]Which means if you use a 3 year old version of a distro, all the software on it (other than fixes and patches) will be 3 years old.[/QUOTE]
Not with
- a repo that is updated continously, eg Debian Testing or Debian Unstable, OR
- transparant (invisible to the user) version upgrades. 
The latter is what happens when you track 'Debian stable' in stead of named releases. If you point sources.list to "stable", you were installing from Debian Sarge a few months back, but now you get whatever is in Debian Etch (except some core packages that require an explicit dist-upgrade). Translate that to Ubuntu's 6 months release cycle without the breakage, and you see what I'm getting at.

---

### Post by Enverex on 2007-05-22
Yeah, that's what I liked about Debian and why I used Sid for a while. I just wish Ubuntu had a rolling release then it would be perfect. I dislike having to switch to an alpha and "not recommended for use... at all" pre-release of Ubuntu :(

---

### Post by PatrickMay16 on 2007-05-22
Adam. 
I can't really comment on your article because I did not read it, and I did not read it because the subject is about something I don't really have any strong opinions on. However, something really struck me about the design of your website. 
Over half the screen is unused and all the text is stuck in a small column around the middle. This makes a page annoying to read (at least for me). You might want to consider widening that column or something.

---

### Post by thunderkyss on 2007-05-22
> **dca said:**
> ...oh, and on a server...
 
$2,499 per year RHEL5
$0 Ubuntu
 
I mean, let's face it, a lot of the bigger shops now have in-house admins for support...

ah?? So it's not the same business model.. obviously, if RH & Novell have income streams Ubuntu doesn't.

---

### Post by thunderkyss on 2007-05-22
> **igknighted said:**
> You missed his point.  He wants a package type that would allow users to update apps at will, while leaving their release version at whatever one they installed.

OK, I didn't understand that point originally. Being new to this whole Linux/Ubuntu thing, I had no idea. 

So, in the Windows world, the need to upgrade is fabricated, where in the Linux world, it's a reality. 

Question. Does Ubuntu put any effort into maintaining old repos?? for say like a year or two, maybe three after a new releas??

If I'm happy with what my computer does everything I need it to do now, Is there any reason I can't continue to use FeistyFawn for the next 10 years, or as long as my current hardware will allow me??

---

### Post by Rhox on 2007-05-22
nvm this post.

---

### Post by maniacmusician on 2007-05-22
> **thunderkyss said:**
> OK, I didn't understand that point originally. Being new to this whole Linux/Ubuntu thing, I had no idea. 

So, in the Windows world, the need to upgrade is fabricated, where in the Linux world, it's a reality. 

Question. Does Ubuntu put any effort into maintaining old repos?? for say like a year or two, maybe three after a new releas??

If I'm happy with what my computer does everything I need it to do now, Is there any reason I can't continue to use FeistyFawn for the next 10 years, or as long as my current hardware will allow me??
It's not recommended. The only updates you'll get after Gutsy comes out will be security updates. After support for Feisty ends, you'll get nothing. I wish Ubuntu had a rolling release as well, or something like it. A suitable solution would be to make the upgrades from one version to the next a little smoother and make them "highly recommended" instead of just "optional".

---

