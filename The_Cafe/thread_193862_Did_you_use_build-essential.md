---
title: "Did you use build-essential?"
date: 2006-06-10
forum: The Cafe
---

### Post by aysiu on 2006-06-10
I'm just curious, since there's a debate about whether to include it in the regular Ubuntu installation or not.

By the way, I voted "yes" for a program outside the repositories. I needed it for VMPlayer.

---

### Post by Stormy Eyes on 2006-06-10
[QUOTE=aysiu]I'm just curious, since there's a debate about whether to include it in the regular Ubuntu installation or not.[/QUOTE]

I've used it, but there's no need to include it in the base install for my sake as long as I can apt-get it from universe. On the other hand, some unfortunate with a WinModem might need to compile drivers, and if build-essential isn't on the CD then he's screwed.

---

### Post by aysiu on 2006-06-10
Well, that's why I included the specific uses for it--for wireless, for dial-up.

If most people need it for non-internet related compiling, then you may be right.

---

### Post by user1397 on 2006-06-10
I just used it to install the program tovid, but I also used checkinstall.  Is the "./configure" and the "make" commands part of the build-essential package, and the "sudo checkinstall" command part of the checkinstall package, or can all of the commands be part of the checkinstall package? (P.S. I don't use sudo make install, i only use sudo checkinstall)

---

### Post by kripkenstein on 2006-06-10
People who need it for wireless are, in my opinion, reason enough to include it. The alternative - which might be better - is what people suggest now and then on these boards, to have a 'bigger' version, say a 5-CD/1-DVD version, for people who don't have internet connections at install time. Sadly I haven't heard of any progress in this direction.

---

### Post by mostwanted on 2006-06-10
I needed it for an AudioScrobbler plugin for Muine not found anywhere in the repos, but also because I needed to compile some homebrew programs.

---

### Post by XQC on 2006-06-10
Hm, I don't think that the poll is really representative since most users who are registered AND hang out in the community forum likely are more experienced and tried to compile something at one time.

---

### Post by Perfect Storm on 2006-06-10
It's one of the first thing I install. Mostly because I like to compile stuff, like multimedia stuff (mplayer, vlc etc.) and games and game related applications which aren't in the repo.

---

### Post by aysiu on 2006-06-10
[QUOTE=XQC]Hm, I don't think that the poll is really representative since most users who are registered AND hang out in the community forum likely are more experienced and tried to compile something at one time.[/QUOTE] Point well-taken, but what can you do--track down the new users who posted only five posts and left and say, "Hey, fill out this poll"? We do what we can.

---

### Post by XQC on 2006-06-10
[QUOTE=aysiu]Point well-taken, but what can you do--track down the new users who posted only five posts and left and say, "Hey, fill out this poll"? We do what we can.[/QUOTE]
Make a pop-up that appears when newbies want to leave the forums that says
"Fill out the poll or your PC will be set upped a bomb"

lol, I think there isn't really anything you can do about it...

---

### Post by BoyOfDestiny on 2006-06-10
[QUOTE=aysiu]I'm just curious, since there's a debate about whether to include it in the regular Ubuntu installation or not.

By the way, I voted "yes" for a program outside the repositories. I needed it for VMPlayer.[/QUOTE]

I've installed and used it...

In addition, installed: automake, autoconf, and several things ending in -dev... 

I guess it depends on the scenario of the user... For a base install, it wasn't needed for me to get any extra functionality...

Just for apps either not in the repo, or apps that have old versions in the repo...

---

### Post by cstudent on 2006-06-10
I'm studying C & C++ programming, so I have a use for it.

.

---

### Post by nalmeth on 2006-06-10
By the amount of times I've had to direct people to install it, and the amount of people I've seen shocked that this basic stuff isn't included by default, I'd have to say yes, it ought to be included.

---

### Post by G Morgan on 2006-06-10
I looked for yes I need it to code but that option wasn't there so I picked for some other reason.

---

### Post by jasay on 2006-06-10
I just feel like someone should point out that build-essential *is* on the cd, but simply not installed.  So even if you don't have internet access, it is still just an apt-get away.  

And yes, I use it because I'm a sucker for anything new and shiney.

---

### Post by Piggah on 2006-06-10
I use it quite often. I always prefer to compile a program to have the latest release. I probably use it at least once or twice a week just installing software. 

I would be upset myself if I had to compile for wireless or for a winmodem. That would not be good.

---

### Post by halfvolle melk on 2006-06-10
I don't need it, but I like to play around with things that are not necesarily needed or usefull.

---

### Post by bullethead on 2006-06-10
Yes it's essential.  But not for the distro "package".  It easy to install via the network.

---

### Post by matthew on 2006-06-10
I installed it because I like to play around with C programming...not that I'm any good at it, though. :) I've also been known to compile my own kernel once in a while, but only for laughs.

---

### Post by CronoDekar on 2006-06-10
I actually installed it just the other day so I could compile Audacious and the latest version of DOSBox.  But really, neither of these were things I needed, I mainly installed them just to have an excuse to build something from source so I could learn something.

---

### Post by Jucato on 2006-06-10
For those interested, here's the thread about the debate: [http://www.ubuntuforums.org/showthread.php?t=192840](http://www.ubuntuforums.org/showthread.php?t=192840)

Also, aysiu, you could probably ask the admin/mods to make a global announcement for this poll so that everyone could see it. I think this is a very important issue since it affects everyone (specially regarding the security risk debate) and because this discussion might eventually lead to changes in the installation of Ubuntu. It's time to get the community's views into the development process.

As for my answers: In Breezy, I used it to both compile packages not included in the repositories and to compile a more up-to-date version. However, dapper has nicely included those packages and have updated those apps that I have no use for them now. I'll probably uninstall it later if it really is such a security risk. I might also reinstall it if I plan to play around with programming.

---

### Post by Luggy on 2006-06-10
I needed build-essentials for gcc/g++. How am I supposed to write my own c++ code without it?

---

### Post by T313C0mun1s7 on 2006-06-10
I voted for four things.

I installed apps that needed it, I knew I usually at some point build a kernel, I needed it to build something not in the repos, and I knew before I needed it that at some point I  might - so I installed it.

---

### Post by fluffington on 2006-06-11
I write software for a living, which kind of necessitates having a compiler. As with most of the other tools I use, though, I can just apt-get install it. Not a big deal.

And slightly off-topic, I really wish build-essential was on the live CDs. I have to use the alternate CD because I have to compile my own network drivers, which means I need to have access to a compiler before the network is up and running.

---

### Post by Jucato on 2006-06-11
@fluffington: In the thread I linked to, azz mentioned that you can install build-essential from the Live CD by inserting it after installation. I'm can't verify that as I have not tried it.

---

### Post by fluffington on 2006-06-11
[QUOTE=Fenyx]@fluffington: In the thread I linked to, azz mentioned that you can install build-essential from the Live CD by inserting it after installation. I'm can't verify that as I have not tried it.[/QUOTE]

It's not on the CD I downloaded on the 2nd. I'm downloading again right now to see if they've changed it.

Edit: build-essential is indeed on the desktop CD now. I'll quit complaining.

---

### Post by Arktis on 2006-06-11
[QUOTE=aysiu]I'm just curious, since there's a debate about whether to include it in the regular Ubuntu installation or not.[/QUOTE]
Why is it even a question in the first place?  It should always be in the default install.  It is integral to one's freedom/ability to install their software of choice.  Not only that,  but the ability to customize that software as one sees fit.  I think it's laughable that there should be any debate about this at all in an open source community.

---

### Post by aysiu on 2006-06-11
It looks like close to 94% of the poll answers in the thread install *build-essential* for whatever reason.

Someone brought up a good point that the sample bias is in favor of people who are more likely to compile software, but 94% is still a huge percentage regardless.

---

### Post by GreyFox503 on 2006-06-11
[quote=Arktis]Why is it even a question in the first place?  It should always be in the default install.  It is integral to one's freedom/ability to install their software of choice.  Not only that,  but the ability to customize that software as one sees fit.  I think it's laughable that there should be any debate about this at all in an open source community.[/quote]

This is more what I was thinking:  how can they *not* include it? So useful, so fundamental, so basic... it is that from which all other software floweth.

I know they are probably leaving it out because they need all the space they can get on a CD, but this is *not* something to cut.  How can you have a Unix-like system without a C compiler?

---

### Post by aysiu on 2006-06-11
The thread where people are debating whether or not it should be included is right [here](http://ubuntuforums.org/showthread.php?t=192840).

---

### Post by GreyFox503 on 2006-06-11
I read through that other thread, and found out that build-essentials is already included on the CD.

This is really starting to confuse me.  Why would the devs take up oh-so-precious space on the install CD by including a package that is not installed anyway?

If its already on the CD, the obvious answer is of course it should be installed.

---

### Post by aysiu on 2006-06-11
Apparently, out of the blue, the package is "a security concern," even though I've **never** in the past year of using Ubuntu and these forums heard of *build-essential* being a security concern.

All of a sudden, despite Ubuntu's strong security model, just having *build-essential* installed means that attackers can compile stuff on your computer or whatever.

I don't know if I buy this, but if it **is** true, there should be a big-*** warning when you try to install *build-essential* that say, "You are about to install a package that's unsafe. Use it and then uninstall it immediately afterwards."

And if it's not true, *build-essential* should **definitely** come installed since the majority of users... use it at one point or another.

---

### Post by Christmas on 2006-06-11
I needed it for programs not in the repositories and up-to-date software. The thing is, from all the software I tried to compile and install, only about 20% worked. Always missing libraries, which if I don't find in the repos I don't bother searching for them on the net. Now I say build-essential package contains lots of libraries and programs, but I most often use gcc and g++ for compiling simple C/C++ code for school.

---

### Post by Gtaylor on 2006-06-11
Yes, I use it for software development. Absolutely critical to have :)

---

### Post by benplaut on 2006-06-11
i'm a bleeding-edge tweaker

---

### Post by Jucato on 2006-06-11
[QUOTE=aysiu]Apparently, out of the blue, the package is "a security concern," even though I've **never** in the past year of using Ubuntu and these forums heard of *build-essential* being a security concern.

All of a sudden, despite Ubuntu's strong security model, just having *build-essential* installed means that attackers can compile stuff on your computer or whatever.

I don't know if I buy this, but if it **is** true, there should be a big-*** warning when you try to install *build-essential* that say, "You are about to install a package that's unsafe. Use it and then uninstall it immediately afterwards."

And if it's not true, *build-essential* should **definitely** come installed since the majority of users... use it at one point or another.[/QUOTE]

It also makes me wonder, if other distros **install** these by default, since some "outsiders" seem to think that Ubuntu's a pain because it doesn't have build-essential **installed** by default. If other distros have done it, how come no one is singing the "having build-essential installed is a security risk" song from them? This thread has really made me curious.

(Sorry I had to put "installed" in boldface, just to emphasize what the real issue is. Included but not installed).

---

### Post by mstlyevil on 2006-06-11
The security issue argument is way overused on a lot of things. I find it ridiculous that anyone can argue that having build-essential installed is a security risk with a straight face. 

If these people are so concerned about security then make Ubuntu force people to use strong passwords before it will even install. Also have a Windows XP type tour when you first fire up the operating system that forces people to sit through a video tutorial on how to properly secure ones computer and how to use proper security practices.

Better yet Ubuntu can be installed with no way to connect to the net so these people can guarantee the computer is secure. If you can not connect to the net there is no way for a person to install anything on a computer without being physically in the room with it.

How far are the devs going to take the average user is too stupid to properly use their computer. This is the way I look at it. It is **my computer**. If I want to use it in a insecure manner, that is my choice. I do not want or need someone holding my hand and telling me how to use my own computer.

There is **no good argument** as to why build-essential is not in the default install. Most Ubuntu users use build-essential at one time or another. As far as I am concerned it should be a part of the default installation.

---

### Post by matthew on 2006-06-11
[quote=Fenyx]It also makes me wonder, if other distros **install** these by default, since some "outsiders" seem to think that Ubuntu's a pain because it doesn't have build-essential **installed** by default. If other distros have done it, how come no one is singing the "having build-essential installed is a security risk" song from them? This thread has really made me curious.[/quote]Let me clarify...it is an extremely small security risk, especially as Ubuntu is set up by default having no ports open. However, there are real exploits in the wild. This probably isn't enough of a reason not to include build-essential by default, though. I think the thought on the developers' minds (okay, I'm just guessing...I'm not really a mind reader) is whether they will get more flak for including it--they are already accused of bloat in the distro as things are. Who chooses what to include and not to include? Who decides what is useful and what is bloat? 

I think the developers just took a guess that because the typical desktop user could install Ubuntu and never need build-essential they would not include it in the default install, but for those who are going to want it right away they put in on the install disk so it could be included without internet access needed. It seems to be a "let's cut the difference and see what happens" sort of solution. The fact that they are asking for input means they want to be responsive to real needs rather than make all their decisions in a vacuum. 

The mailing list discussions are going into much greater technical depth than here on the forums because the user base there tends to be even more techy than here...for the deeper perspective I suggest looking there. For more on that see the discussion thread: [http://ubuntuforums.org/showthread.php?t=192840](http://ubuntuforums.org/showthread.php?t=192840)

---

### Post by mstlyevil on 2006-06-11
Matthew, you make some valid points but it still does not justify the nanny attitude of some of the devs. If security is the issue then Ubuntu needs a better security model and not crippled functionality. I dare say most users at one point or another use build-essential and it should be installed by default.

---

### Post by G Morgan on 2006-06-11
Does this compiler security issue mean that Gentoo boxes are automatically exploit friendly. I never had an issue when running Gentoo and always install the build tools straight off in Ubuntu and have had no issues there either.

---

### Post by drizek on 2006-06-11
[quote=aysiu]It looks like close to 94% of the poll answers in the thread install *build-essential* for whatever reason.

Someone brought up a good point that the sample bias is in favor of people who are more likely to compile software, but 94% is still a huge percentage regardless.[/quote] 
The option to pick more than one option means that the people who install build essential are represented several times in the poll. there are 163 votes for it, even though only 100 people voted.

Personally i installed it for enlightenment 17 and to compile initng. i see no reason why it should be installed by default though because most people will never do either one of these things, and installing build essential is part of the how-tos for them anyway.

---

### Post by aysiu on 2006-06-11
Okay, drizek. Let's assume that all of those multiple-choice votes were overlaps (they probably all were *not* overlaps, but let's assume they were).

That's still at least 62 out of 105 respondees who use it, which is 59%, as opposed to a maximum of 10 who don't (it could be as little as 3), which would be almost 10% who don't.

---

### Post by Virogenesis on 2006-06-11
[QUOTE=aysiu]Okay, drizek. Let's assume that all of those multiple-choice votes were overlaps (they probably all were *not* overlaps, but let's assume they were).

That's still at least 62 out of 105 respondees who use it, which is 59%, as opposed to a maximum of 10 who don't (it could be as little as 3), which would be almost 10% who don't.[/QUOTE]
aysiu if your granddad was running ubuntu would he read the ubuntu forums? 
Because those that don't will not get their vote added and sure I do use them but I also use cvs and I'm sure others do should we include cvs as standard aswell?
Because thats pretty much the same alot use build-essential for bleeding edge not all want bleeding edge

---

### Post by aysiu on 2006-06-11
What percentage of Ubuntu users do you think are granddads who just picked it up themselves and didn't register for these forums?

And what percentage of Ubuntu users do you think are the kind who do register for these forums and get help... and install and configure Ubuntu themselves?

Are you honestly trying to tell me your grandpas are the majority?

I think, too, you'd be surprised at the variety of folks we get here at the forums. I, for example, do not want bleeding edge applications. I pretty much use what's in the repositories. I did install *build-essential* for VMPlayer, but I didn't have to resolve dependencies or do a make make install and all that. I just did ```
sudo ./vmplayer_install
``` and that was it. Answered a few questions by pressing Enter.

---

### Post by fluffington on 2006-06-11
[QUOTE=Virogenesis]aysiu if your granddad was running ubuntu would he read the ubuntu forums? 
Because those that don't will not get their vote added and sure I do use them but I also use cvs and I'm sure others do should we include cvs as standard aswell?
Because thats pretty much the same alot use build-essential for bleeding edge not all want bleeding edge[/QUOTE]

Most of the Linux-running granddads I know use gcc and cvs to write and maintain their own software.

---

### Post by Virogenesis on 2006-06-11
[QUOTE=fluffington]Most of the Linux-running granddads I know use gcc and cvs to write and maintain their own software.[/QUOTE]
I'm talking about those who lack linux experience maybe granddad was a bad example how about grandmum then

---

### Post by Virogenesis on 2006-06-11
[QUOTE=aysiu]What percentage of Ubuntu users do you think are granddads who just picked it up themselves and didn't register for these forums?

And what percentage of Ubuntu users do you think are the kind who do register for these forums and get help... and install and configure Ubuntu themselves?

Are you honestly trying to tell me your grandpas are the majority?

I think, too, you'd be surprised at the variety of folks we get here at the forums. I, for example, do not want bleeding edge applications. I pretty much use what's in the repositories. I did install *build-essential* for VMPlayer, but I didn't have to resolve dependencies or do a make make install and all that. I just did ```
sudo ./vmplayer_install
``` and that was it. Answered a few questions by pressing Enter.[/QUOTE]
Its an example, thats all not all will compile, some will just use whats added to the repos. 
Doesn't ubuntu promote the use of the repos & Why promote compiling programs when the repos is huge?
My point is how many have installed ubuntu for family members?

---

### Post by Alpha_toxic on 2006-06-11
I needed to compile some stuff several times (for example: once there was an off_by_one error somewhere in WINE affecting a program I was trying to run, so I had to recompile).
But this in NOT the main reason.
You see, I'm studying Informatics... and what is a programmer without a compiler...?

---

### Post by G Morgan on 2006-06-11
If we are going down the path of a live installer and an alternative installer. Whats to stop the devs from giving options on the alternative installer while keeping the live one as pure traditional Ubuntu. Personally I don't use the live installer anyway, the ncurses one makes much more sense generally.

---

### Post by egon spengler on 2006-06-11
[QUOTE=mstlyevil]  How far are the devs going to take the average user is too stupid to properly use their computer. This is the way I look at it. It is **my computer**. If I want to use it in a insecure manner, that is my choice. I do not want or need someone holding my hand and telling me how to use my own computer.[/QUOTE]

I agree with that 100% but if you apply this right to all people and not just yourself wouldn't it mean that the devs have a right to author their distro as they see fit without you holding their hand and telling them how they should do it? 

It seems that you think YOUR choice is all important and must be respected (and you do have the choice seeing as it's on the cd and you don't even need to dl it) but you don't need to extend that same respect to anyone else

---

### Post by xXx 0wn3d xXx on 2006-06-11
Yes, I installed build-essential. I installed it because I use it to compile newer packages. (gaim, gnomebaker, ect.)

---

### Post by aysiu on 2006-06-11
[QUOTE=Virogenesis]Its an example, thats all not all will compile, some will just use whats added to the repos. 
Doesn't ubuntu promote the use of the repos & Why promote compiling programs when the repos is huge?
My point is how many have installed ubuntu for family members?[/QUOTE] You're not promoting compiling programs--you're allowing people to compile programs.

It won't hurt people to have *build-essential* installed if they don't use it.

A lot of people *do* use it.

It's already on the disk, anyway, so it wouldn't take up any extra disk space.

Other distros have it, so instructions for .tar.gz's often do not tell you you need to install it. We just get confused users who say, "Why do I get *make: command not found* when I try to do this?"

---

### Post by phillywize on 2006-06-11
So reads the "official" description I grabbed from synaptic:

> If you do not plan to build Debian packages, you don't need this
package.  Moreover this package is not required for building Debian
packages.

This package contains an informational list of packages which are
considered essential for building Debian packages.  This package also
depends on the packages on that list, to make it easy to have the
build-essential packages installed.

If you have this package installed, you only need to install whatever
a package specifies as its build-time dependencies to build the
package.  Conversely, if you are determining what your package needs
to build-depend on, you can always leave out the packages this
package depends on.

This package is NOT the definition of what packages are
build-essential; the real definition is in the Debian Policy Manual.
This package contains merely an informational list, which is all
most people need.   However, if this package and the manual disagree,
the manual is correct.

After reading it through, I am cross-eyed, my head is spinning, and my stomach hurts.

Being kind of new-ish, I haven't compiled anything in Ubuntu, and only ever compiled a few kernels in Fedora.  Which is not all that hard.  Who knows...I think Ubuntu is fine without it in the ISO.  If the target audience is people who are not so into hacking as to be able to compile their own stuff, let those who are technically inclined grab it themselves.  Unless, of course, it's necessary to something...did I read a few posts back that this package makes certain wireless configs go?  If so, then by all means, leave it in.  So long as people like me never need to really mess with it, and it just does its thing.

---

### Post by az on 2006-06-11
[QUOTE=aysiu]The thread where people are debating whether or not it should be included is right [here](http://ubuntuforums.org/showthread.php?t=192840).[/QUOTE]

There is no debate as to whether it should be included or not.  It will be included on the cd as it always has been.

The debate is whether is should be *installed* by default.

It's an extra step to install the package from the cd.  It may be a security risk to install stuff you don't need.  The debate is about whether the inconvenience of having to install it from the cd to compile stuff is greater than the security risk of having it installed on every ubuntu system - even those who don't use it.



Oh!  Aysiu!  Vmplayer and it's kernel modules is already built for you -  you didn't need build-essential after all!

It's in multiverse:
[http://packages.ubuntu.com/dapper/misc/vmware-player](http://packages.ubuntu.com/dapper/misc/vmware-player)

---

### Post by xtacocorex on 2006-06-11
Here is my opinion, since build-essential is on the cd's already, just not installed by default, we should make a concerted effort to let people know it's there. If it's too much work to change a line in the installer to install it, then don't change it. 

As for the security issue, I read the other thread when it was started and yes, it can be an issue, but it's that important especially since the OS has closed ports by default. One of my coworkers in our Info Systems department is going to put Dapper on his new desktop and laptop because of the ports being closed.

On to my poll response and I need to explain since I picked other.

I use the packages in build-essential almost everyday. I haven't needed to compile that many programs specifically for the OS since I moved to Dapper and Gnome, but I do have about 50 or so codes that I've written that include makefiles for compilation. Due to the makefiles for compiling, I need make. I also need some of the libraries that are installed with it for these programs to run. 

I could, in theory, compile the programs without the makefiles, but it's a lot more work and when the codes are custom and you have to modify them to change the problem I'm trying to solve, then it becomes really handy.

---

### Post by Buffalo Soldier on 2006-06-11
Yes, I needed it for some other reason... for compiling c programs, assignments and etc.

---

### Post by az on 2006-06-11
...And the poll is definitely skewed.  The poll leads people to think that they (the Man) want to take build-essential away from you.  This is not the case, of course.

I, myself, would have to answer yes, since I used build-essential in Debian, and for a number of reasons in the various flavours of ubuntu.

However, to install and run Dapper on the three computers I use here at home, I don't need build-essential at all.

My point (I said that only 1 percent of ubuntu users need build-essential) was that you rarely need build-essential to get your box up-and-running and fully-functional.
[http://ubuntuforums.org/showpost.php?p=1117844&postcount=30](http://ubuntuforums.org/showpost.php?p=1117844&postcount=30)
"What is being discussed, however, is whether the risk is significant enought to warrant the inconvenience to about 1 percent of users who will have to install it from the cd before they use it instead of it being preinstalled on every ubuntu box."

---

### Post by aysiu on 2006-06-11
I'm not denying it's skewed. In fact, if you look back at my posts, you'll see I acknowledge that it is. To say that it's 1%, even after seeing a *skewed* poll like this is just putting your head in the sand--I'm sorry.

I've still yet to here a convincing case that's a huge risk to users, especially since other distros include compiling tools.

I just think it's annoying that when people get instructions from READMEs in .tar.gz's that tell them to ./configure make make install that they get *bash make: command not found* instead of just being able to do what they want to do.

P.S. Thanks for the tip about VMPlayer--[I see, though, that that's new for Dapper.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=vmplayer&searchon=name&subword=1&version=all&release=all)

---

### Post by drizek on 2006-06-12
Its not a huge risk, but theres no point in bloating the distro with it. If someone cant apt-get it then they have no hope in hell of being able to compile an app from scratch.

---

### Post by aysiu on 2006-06-12
I don't see how it's "bloat."

It doesn't make Ubuntu load any more slowly.

Users who don't use it won't know it's there (it doesn't take up space on the screen or fill up the menus).

Users who need it will just have that one extra step to get it. And many users, coming from other distros, know how to *apt-get* and compile, but they haven't had to *apt-get* some metapackage in order to compile in other distros.

So they sign up for a forum. Post a new thread. Then they wait for a reply where someone tells them, "Install *build-essential*." Then they apt-get it. What a pain for that person.

Couldn't we just assume that anyone who would be in a situation where it *would* be a security risk would know about this risk and know to uninstall it after they've compiled what they need to compile? We don't all run servers here.

By the way, to the people who keep reminding me that this poll is skewed (I know it's skewed), do you have a better idea besides making up statistics out of thin air (like only 1% of users use *build-essential*)? How can you actually know how many install it?

I think more energy should be put into finding out how many people would be exposed to these supposed security risks and educating those people about those risks instead of putting *build-essential* on the disk and not installing it.

Why don't we just put Assistive Technology Support on the disk but not install it? Isn't that bloat, since most users don't use it?

If we just install only what is the most popular, you're basically going to have Firefox, Gnome, and that's it. More people probably use *build-essential* than Assistive Technology Support.

So, even though I do believe (however skewed the sample group is) that this poll indicates a lot of people *do* use *build-essential*, majority use shouldn't be the main issue--accessibility should be... basics should be. And a lot of people (especially those coming from other distros) basically expect those compiling tools to be there.

The only issue should really be this supposed security issue.

---

### Post by drizek on 2006-06-12
It is bloat because it is extra stuff most people dont need. Its why we dont have -dev packages of everything, because they are useless to most people and the people that know about them are more than capable of installing them.

I think the biggest advantage in not including it is it forces people to use apt. When i first switched to linux i used mandrake and i used to compile everything from scratch. Then when i switched to mepis, there was an app i couldnt get to compile so i asked on a forum. Someone told me to type in apt-get install xxxx and that was my "ok, im switched" moment.

---

### Post by Perfect Storm on 2006-06-12
I think it's fine it isn't installed by default. It isn't hard to smack the CD in CD-rom and write a one commandline to get it. It's no diffrent from other packages you want to install. The main thing it's on the CD for those who need it but doesn't have internet-connection.

So I can hardly see what all the fuss is about.

---

### Post by Zdravko on 2006-06-12
I am very angry because of this thread. As a programmer I need g++ in order to compile my programs. First of all I don't see such a possibility in the poll!
I have no good explanation why the compiler isn't installed by default. I don't know whether it could be found in the CD. Nobody informed me about this. I have to type "sudo apt-get install build essential" so that I can have it. Why? Linux has only one purpose for me - it is a stable workstation... for developing new application. Why there are so many games, screensavers and so on? Who needs this stuff? Kids? Excuse me, but I am a serios man and I don't like my OS to be bloated with useless programms. G++ is on of the most brilliant things programmers created. Everything else shouldn't be installed by default!

---

### Post by Jucato on 2006-06-12
That's not a very nice thing to say. Just because you don't need something doesn't mean it doesn't deserve to be on the OS. Don't use your standards as the standard by which all others should be deemed worthy or worthless. Not everyone who comes to Linux are programmers. Not everyone who comes to Linux for development. Please don't go around here saying those things, because it really goes against what Ubuntu is working for.

Also, Ubuntu is only one of the distros (perhaps the only one?) who doesn't install build-essential by default. There are other distributions out there who install it by default, other distributions who might cater to your needs/wants as a developer who does not need stuff like games, screensavers, and perhaps even GUIs.

So please, don't go about saying "everything else shouldn't be installed by default!" just because you have no need for them. That is not what Ubuntu is about.

---

### Post by drizek on 2006-06-12
actually, most distros dont ship with build-essential.

---

### Post by Jucato on 2006-06-12
Well, I'm probably wrong. But it makes me wonder why some reviewers of Ubuntu like to say that it doesn't install build-essentials by default. But even if most distros don't, Gentoo or Slackware would, right? It seems that those kinds of "no-nonsense" distros (at least, no-nonsense for him probably), would cater to his tastes more.

But again, the real issue isn't whether Ubuntu should or should not ship build-essential. The fact is that it is already there. The question remains is if it should be installed by default.

---

### Post by Stormy Eyes on 2006-06-12
[QUOTE=Fenyx]The question remains is if it should be installed by default.[/QUOTE]

No. I think the current situation is fine: keep it on the CD for those who need or want it, but don't install it by default. If you must, add an option to the installer so that those who want the compiler can get it installed during setup.

---

### Post by Perfect Storm on 2006-06-12
[QUOTE=Zdravko]I am very angry because of this thread. As a programmer I need g++ in order to compile my programs. First of all I don't see such a possibility in the poll!
I have no good explanation why the compiler isn't installed by default. I don't know whether it could be found in the CD. Nobody informed me about this. I have to type "sudo apt-get install build essential" so that I can have it. Why? Linux has only one purpose for me - it is a stable workstation... for developing new application. Why there are so many games, screensavers and so on? Who needs this stuff? Kids? Excuse me, but I am a serios man and I don't like my OS to be bloated with useless programms. G++ is on of the most brilliant things programmers created. Everything else shouldn't be installed by default![/QUOTE]

I'll answer with a blunt answers. Perhaps Ubuntu isn't for you? There's 200+ or more distros out there for every taste and shape. 
Still I don't understand why you get angry that build essential isn't install when it's so easy to get with one commandline, don't you think you're shooting sparrows with cannons?
There's always stuff people want to be install by default and other things they think is a waste.

---

### Post by Zdravko on 2006-06-12
I adore Ubuntu. I like its simplicity and stability. But sometimes an Internet connection can be difficult to obtain. There is no real reason why gcc shouldn't be installed by default.

---

### Post by fluffington on 2006-06-12
[QUOTE=Zdravko]I adore Ubuntu. I like its simplicity and stability. But sometimes an Internet connection can be difficult to obtain. There is no real reason why gcc shouldn't be installed by default.[/QUOTE]

But you don't need an Internet connection at all to install build-essential; it's on the CD.

---

### Post by Zdravko on 2006-06-13
What CD exactly? Where on the cd? How to install it from there?

---

### Post by fluffington on 2006-06-13
[QUOTE=Zdravko]What CD exactly? Where on the cd? How to install it from there?[/QUOTE]

It's on all of the *ubuntu CDs. Just apt-get install build-essential with the CD repo turned on.

EDIT: forgot to give the location. The .deb file should be in /pool/main/b/build-essential/

---

### Post by aysiu on 2006-06-13
If it's on the Desktop CD, how do you get to it? I've had no luck adding the Desktop CD as a repository--as far as I know, it *can't* be added as a repository.

Don't you need the Alternate Install CD?

---

### Post by Zdravko on 2006-06-13
I need a good explanation.

---

### Post by Jucato on 2006-06-13
[QUOTE=aysiu]If it's on the Desktop CD, how do you get to it? I've had no luck adding the Desktop CD as a repository--as far as I know, it *can't* be added as a repository.

Don't you need the Alternate Install CD?[/QUOTE]

according to azz, it can be done. Though I'm not sure how. I also haven't had any luck adding the Desktop CD as a repository through apt-cdrom. Maybe he could explain the details.

@fluffington: I see the deb file. But that's only a .deb. How will it resolve dependencies?

---

### Post by aysiu on 2006-06-13
Well, for the Alternate Install CD, I can tell you. I don't know about the Desktop CD.

Pop the CD in your drive.
In a terminal, paste the command: ```
sudo apt-cdrom add
``` Now it's a source. ```
sudo aptitude update
sudo aptitude install build-essential
``` And if you believe people that it's a security threat, then right after you're finished using it ```
sudo aptitude remove build-essential
``` Personally, I think it being a security threat is a crock of s**t--just leave it installed unless you're running a server.

---

### Post by fluffington on 2006-06-13
[QUOTE=aysiu]If it's on the Desktop CD, how do you get to it? I've had no luck adding the Desktop CD as a repository--as far as I know, it *can't* be added as a repository.

Don't you need the Alternate Install CD?[/QUOTE]

I never had a problem using the desktop CD as a repo; it just worked out of the box.

---

### Post by aysiu on 2006-06-13
[QUOTE=fluffington]I never had a problem using the desktop CD as a repo; it just worked out of the box.[/QUOTE] Can you be more specific than "out of the box"? What exactly did you do to make it a repository? You had to have done *something*. You can't modify the /etc/apt/sources.list unless you have root privileges.

**Edit**: I just popped the Desktop CD in my CD-ROM drive. It appears on my desktop, but I don't see it in my sources.list.

When I try to add it as a source in Synaptic, I get this error.

---

### Post by fluffington on 2006-06-13
[QUOTE=aysiu]Can you be more specific than "out of the box"? What exactly did you do to make it a repository? You had to have done *something*. You can't modify the /etc/apt/sources.list unless you have root privileges.[/QUOTE]

Didn't have to do anything at all; the CD was enabled by default.

---

### Post by aysiu on 2006-06-13
So when you tried to install stuff, it asked for the CD, and you popped in the Desktop CD, and it didn't complain?

---

### Post by Jucato on 2006-06-13
Update: aysiu, I was able to successfully add the Desktop CD as a repository.
```
sudo apt-cdrom -d /media/cdrom1 add
```
Since I put the CD in a drive mounted on /media/cdrom1. This is the output I got:

>  sudo apt-cdrom -d /media/cdrom1 add
Using CD-ROM mount point /media/cdrom1/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d251c204c5513e9470c11bf645950d27-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
Found label 'Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
This disc is called:
'Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wednesday, 31 May, 2006 11:33:59 AM PHT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.

Then I disabled all repositories in sources.list except the cdrom repo (it might cause conflicts). I had to put the CD into cdrom0, though. This is the output I got trying to install build-essentials:

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libstdc++6-4.0-dev make
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libstdc++6-4.0-dev
  make
0 packages upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8141kB of archives. After unpacking 29.3MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package binutils.
(Reading database ... 88763 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2_i386.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.0.3-1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2) ...

Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...

Take note that I have no repository enabled other than the cdrom repository.
EDIT: I also ran apt-get clean and autoclean before installing

---

### Post by aysiu on 2006-06-13
Maybe it works at the command-line and not from Synaptic?

---

### Post by Zdravko on 2006-06-13
So... is it possible to have gcc installed from CD? Yes or no?

---

### Post by aysiu on 2006-06-13
Yes.

---

### Post by Jucato on 2006-06-13
[quote=Zdravko]So... is it possible to have gcc installed from CD? Yes or no?[/quote]
From the Alternate Install CD? Absolutely yes

From the Desktop CD? We're still testing that.

@aysiu: I'm not really sure as I have not added CD repositories using Synaptic.

---

### Post by Zdravko on 2006-06-13
Okay, now I feel better. At least I won't need anymore the Internet.

---

### Post by az on 2006-06-13
[QUOTE=aysiu]
When I try to add it as a source in Synaptic, I get this error.[/QUOTE]

It works fine for me.  You need to use the final release cd and not an earlier beta or RC release, since the repo was put there about five days before relase.

You can also just instert the cd and follow the instructions on screen as shown:

or just run

sudo apt-cdrom add

---

### Post by fluffington on 2006-06-13
[QUOTE=aysiu]So when you tried to install stuff, it asked for the CD, and you popped in the Desktop CD, and it didn't complain?[/QUOTE]

I already had the CD in, so there was no asking. And since people are takling about Synaptic now, I have no idea if it works in Synaptic or not, as I use the terminal for everything.

---

