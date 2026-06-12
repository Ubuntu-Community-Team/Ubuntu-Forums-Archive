---
title: "Linux Standard Base adoption/development in the Linux Community"
date: 2017-10-08
forum: Ubuntu, Linux and OS Chat
---

### Post by panaman67 on 2017-10-08
Why doesn't the Linux Community support or care about the Linux Standard Base (LSB)? The whole point of it is to help the Linux community grow and get rid of completely unnecessary fracturing. Does anyone else want the distros of the community to start supporting it so that developers can start to migrate to Linux? In my opinion, Flatpak and Ubuntu Snaps seem like a terrible "fix" for incompatibility between distributions and the "build once, deploy everywhere" goal.

---

### Post by ian-weisser on 2017-10-08
> **panaman67 said:**
> Why doesn't the Linux Community support or care about the Linux Standard Base (LSB)?

LSB has many advantages...but also many disadvantages.

---

### Post by panaman67 on 2017-10-08
> **ian-weisser said:**
> LSB has many advantages...but also many disadvantages.

[COLOR=#000000]I understand, but with how important the purpose of the project is, and how many people are in the Linux Community, why doesn't anyone care to work on it and fix the disadvantages??[/COLOR]

---

### Post by ian-weisser on 2017-10-08
We all know why the LSB project was important back in the days of the distro wars.
All the important distros today are LSB-compliant, or seem lacking only around some less-important edges.
Is some distro wandering away from LSB? If so, how?

---

### Post by panaman67 on 2017-10-08
> **ian-weisser said:**
> We all know why the LSB project was important back in the days of the distro wars.
All the important distros today are LSB-compliant, or seem lacking only around some less-important edges.
Is some distro wandering away from LSB? If so, how?

If they are compliant, I cant find any record of compliance. Also, its not a very robust standard if things like Snaps and Flatpak exist. Jumping from distro to distro is painful with each distro having a different packaging manager and way of doing things. Look at the VLC homepage and download links. [https://www.videolan.org/vlc/index.html](https://www.videolan.org/vlc/index.html)

10 different download links for Linux. From my experience, nobody develops for Linux, they develop for a single distro. Why cant we come together and figure out a single package manager and promote development for the ENTIRE Linux user base.

[https://lwn.net/Articles/658809/](https://lwn.net/Articles/658809/)

Debian drops LSB compliance. The mother distro seems to not care.

---

### Post by ian-weisser on 2017-10-08
Are you saying that you want to volunteer your time and effort to resurrect and maintain explicit Debian LSB compliance?

Debian and other distros were together fully LSB compliant for many years, during which the number of package managers did not decrease.
Why do you think this was?
Why do you think that restoring LSB compliance will be different this time?

---

### Post by QIII on 2017-10-09
Can you articulate for us the primary benefit of adhering to the Standard Base?  What is the end state desired?  Why?

---

### Post by panaman67 on 2017-10-09
> **ian-weisser said:**
> Are you saying that you want to volunteer your time and effort to resurrect and maintain explicit Debian LSB compliance?

Debian and other distros were together fully LSB compliant for many years, during which the number of package managers did not decrease.
Why do you think this was?
Why do you think that restoring LSB compliance will be different this time?


The amount of package managers did not INCREASE. As you know, the Linux community is very stubborn and if the LSB was talked about and developed by the major distros like Ubuntu and Red Hat and SUSE, then the standard would have more traction. And like ANYTHING in the Linux community, change takes time. Especially this low level kind of change. 

I think this time it CAN be different if the community realize how important this project is and outs real time, money, and energy to making it a standard that is robust and something we can all agree on.

---

### Post by QIII on 2017-10-09
What can we all agree on?  Which package manager should be chosen?  rpm/dnf? deb/apt? rpm/zypper?

---

### Post by panaman67 on 2017-10-09
> **QIII said:**
> Can you articulate for us the primary benefit of adhering to the Standard Base?  What is the end state desired?  Why?

My end state desired is a world where you can truly develop for Linux instead of having to package your app 20 different times for each distro you want to target and each specific version of that distro. 

Flatpak and Snaps just seem like a perfect case study of the problem at hand. 

And for a world where people can transfer from distro to distro without feeling helpless and like you need to learn Linux all over again because of how different everyone is. 

Build for ALL of Linux, ONCE, and deploy to EVERYONE. Without have to package ALL of your dependencies with the application.

---

### Post by QIII on 2017-10-09
Then people should not be able to develop for their own ends and purposes as they choose?

I would submit that the reason this standard has not been widely adopted is precisely because of what people like about Linux:  Choice.

I've never felt like I had to learn Linux over again over the many distros I use.

---

### Post by panaman67 on 2017-10-09
> **QIII said:**
> What can we all agree on?  Which package manager should be chosen?  rpm/dnf? deb/apt? rpm/zypper?

That is the question that needs to be answered in my opinion. Right or wrong, as a community we need to unite on some standards to make the Linux platform more developer friendly and user friendly, because only then can we start to see real progress in market share and wide spread use. The famous "Year of the Linux Desktop" wont EVER be a thing until the ENTIRE Linux community unites together and works on their differences. 

To be clear, I dont think that we should all migrate to a single distro. That would be awful. What im saying is that we need to really become this community and "de-fracture" ourselves.

Diversity in the distros is something that makes Linux amazing. But we cant have everyone doing everything there own unique way because that is not "Diversity", its "Fractured". ANd we wont see any sort of real widespread adoption on the Desktop and no real mass of development from developers until we unite.

---

### Post by QIII on 2017-10-09
I knew that "market share" was the end game in your query.

What?  Compete against Windows on the desktop?  Not going to happen.  Too much inertia.  Besides, if Linux is fighting Microsoft, Linux has already won.  There are, by an order of magnitude, more devices running Linux than anything from Redmond.

Many of us old hands don't really care about the idea of "market share".  It has always been a pipe dream.  The "Year of the Linux Desktop" is never going to happen.  It never was.

---

### Post by panaman67 on 2017-10-09
> **QIII said:**
> Then people should not be able to develop for their own ends and purposes as they choose?

I would submit that the reason this standard has not been widely adopted is precisely because of what people like about Linux:  Choice.

I've never felt like I had to learn Linux over again over the many distros I use.


I hope I am not coming off as an ass in this debate. I want to extend my deepest respect for you. Just trying to learn from like minded people.

I would like to respectfully disagree with that. With everyone taking there own direction on how to do things, there is no unity on what the true direction is and the community winds up reinventing the wheel over and over again.

I would also like to say that with there being no development standard, choice is completely taken away from the user because the only choice he/she has is the only one that works on his/her system.

With development, filesystem, and packaging standards, people can make all kinds of programs and be assured that their app will work on any computer with Linux on it that is compliant with the Linux standard (Hopefully all of them one day). 

Look at Windows. It SUCKS....like a LOT... but you cant deny that they gave developers the ultimate platform to develop for. And choice is abundant because while some apps are better than others, they all at least work.

---

### Post by panaman67 on 2017-10-09
> **QIII said:**
> I knew that "market share" was the end game in your query.

What?  Compete against Windows on the desktop?  Not going to happen.  Too much inertia.  Besides, if Linux is fighting Microsoft, Linux has already won.  There are, by an order of magnitude, more devices running Linux than anything from Redmond.

Many of us old hands don't really care about the idea of "market share".  It has always been a pipe dream.  The "Year of the Linux Desktop" is never going to happen.  It never was.


I didnt mean to infer that market share was my end goal, I would like to think i am less shallow than that. I however think Linux is really cool, but can also see that there are a lot of problems with it. Most people in Linux that i have come across HATE admitting Linux has ANY problems whatsoever. 

I couldnt care less what market share Linux is at. I do care however how good the Linux platform is and where it could be. 

I again convey my respect and thank you for having this discussion with me. I am enjoying the back and forth and the learning experience and different perspective i am getting from it.

---

### Post by QIII on 2017-10-09
Linux has all manner of problems.  So do most things fabricated by humans.  

I, for one, don't want Ubuntu to be hardly distinguishable from Fedora or SUSE.  I enjoy the differences -- which I do not believe to be as great a chasm as you appear to.  I think we are talking about a $100 fix to a $10 problem.

If this is a goal to which you aspire, then by all means do not be discouraged.  But be realistic.

Edit:  It occurs to me that you may not see the world from my perspective.  The desktop is really only a very small part of "the computer world".  The most interesting parts of that world lie beyond the desktop.  The real fun has gone far beyond to the point that the desktop has become hardly more than a boring portal.

---

### Post by panaman67 on 2017-10-09
> **QIII said:**
> Linux has all manner of problems.  So do most things fabricated by humans.  

I, for one, don't want Ubuntu to be hardly distinguishable from Fedora or SUSE.  I enjoy the differences -- which I do not believe to be as great a chasm as you appear to.  I think we are talking about a $100 fix to a $10 problem.

If this is a goal to which you aspire, then by all means do not be discouraged.  But be realistic.

Edit:  It occurs to me that you may not see the world from my perspective.  The desktop is really only a very small part of "the computer world".  The most interesting parts of that world lie beyond the desktop.  The real fun has gone far beyond to the point that the desktop has become hardly more than a boring portal.

I see your point, and I do agree that the real "meat" or fun of computing lies beyond the desktop: Servers, embedded, etc.. I am glad we can discuss our differences in opinion about the desktop aspect of personal computing. I will always have the desktop as a passion of mine, but i also cant wait to get into the server and beyond. Thank you for talking with me and i apologize for seeming like an ass.

EDIT: I enjoy the differences between the distros as well. Its one of the things that make Linux so awesome. I guess from our talk, I see the differences as a widening gap that needs to be controlled and that the gap impacts the viability of good development. As someone who is still learning about the Linux ecosystem, I know i have a lot to learn and i hope I find more people like you willing to talk and have a good debate/ conversation. I would VERY much like to challenge my beliefs about Linux so that i can remain educated about this project that i have become so passionate about.

Thank you again!

---

### Post by mastablasta on 2017-10-09
i too think some standards would be good to have. at least for basic things. 

but then again source code is open so one can always compile.

i don't think it's just the desktop that is hit. there are many small differences to do things on server. like for example default Apache user is different in Ubuntu and Fedora, is that really necessary? does the difference bring anything to the table or is it there just so that one has a "choice"?

luckily most apps are the same across distros. so there is at least that.

---

### Post by QIII on 2017-10-09
There are dangers in an ecosystem that prizes the ability for each to go his own way.  Who do we elect to populate the standards body?  What is their mandate?  What enforcement agency do they have?  Does their mandate supercede the Linux Consortium/Linux Foundation?  Is Linus bound by their decisions as he decides what should and should not be rolled into the kernel?  Is the standards body bound to Linus' decisions and must they consult with Lake Oswego before making a move?

There is already the standard of the mainline kernel an Linus' control of that.  From that point forward, the entire ecosystem is based on the freedom of all to change and publish code to suit their own ends.  To the extent that we allow restrictions to that, as in the case of standardization, we diminish the wonderful freedom of Linux.

I do not count the minor differences in such things as servers to be so great a difficulty as to require "fixing".  I use both Ubuntu and Red Hat family servers.  As far as I am concerned, the differences are dialectical.  As in human languages, dialects are a naturally occuring phenomenon between cultures that speak the same "language".  Culture is what we are talking about here. 

Apache?  I use Nginx.  Am I to be "standardized" away from that so that developers need only deal with one?

I think standardization by a group who appoint themselves as the arbitors of the standard runs counter to the greater Linux culture.  So back to the nature of the standards body.  Do we call on the ISO, IEEE or SAE to formulate an independent standard?  Does the world want the "American" standard that the SAE might impose?

If there is a Linux community standardizatiin  body, how is it formulated?  It can certainly not be partisan as the LSB is.  From where do we draw candidates?  What are their qualifications?  How do we establish the electorate?  What is the process of debate/decision?  Does the community take part in that, or is it representative and conducted solely within the standards body?  What relief is there for the developer whose product is suddenly "non-standard"? Windows is highly standardized and the "Made for Windows" badge is subject to the decree of Redmond.  Will "Made for Linux" be the same?  Is compliance with the standard to be required before a product may be released?

What if the 600lb gorilla that is Red Hat decides to pack the standards body?  The 1800lb gorilla that is Oracle?

---

### Post by yoshii on 2017-10-09
This is pretty much why I distro hop; to try and figure out which tools are better than others.  Nobody seems to have all the best stuff in one spot.  
But distrowatch at least describes the differences somewhat.

---

### Post by grahammechanical on 2017-10-09
So, we are all agreed then. What Linux needs is a monolithic commercial entity that owns the OS and denies access to the source code to anyone not employed by it and only allows its employees access to blocks of source code.

And that is where Richard Stallman found himself all those years ago and the frustration of it gave birth to the concept of Free and Open Source Software. The application of which gave the motivational push to the development of Linux and the various desktop environments and user interfaces that we enjoy whatever our tastes in the look of the OS.

Regards.

---

### Post by SeijiSensei on 2017-10-09
> **panaman67 said:**
> My end state desired is a world where you can truly develop for Linux instead of having to package your app 20 different times for each distro you want to target and each specific version of that distro.

You as a developer don't have to do any packaging.  The standard practice is to release the source code and let the various distro maintainers package the software for their distributions.

---

### Post by mörgæs on 2017-10-09
Failure to follow standards is not the same as adding choice. It gives no added benefit to engineers or anyone else that some parts of the world measure length in inches (and in various definitions of inches, to make things even worse) and some in centimeters. It's only a burden to people and it costs real money:

[http://edition.cnn.com/TECH/space/9909/30/mars.metric.02/](http://edition.cnn.com/TECH/space/9909/30/mars.metric.02/)

Market share is everything. Without market share it's impossible to attract developers. Even Microsoft wasn't able to create market share for their phones and had to shut down the project. Market share is not less important just because the project is open source.

Anyone remembers what Bug #1 is about? 

The GNU/Linux community suffers from the Not Invented Here-syndrome. People invent the wheel again in stead of acknowledging that other projects are better. This led Canonical to venture out into building their own display server Mir when everybody else agreed upon Wayland - now, after wasting an unknown number of man-hours Mir is abandoned and also Canonical supports the Wayland standard. My respect for admitting a mistake and learning from it.

---

### Post by QIII on 2017-10-09
Bug #1 is closed.  The world beyond the desktop, the much larger world, does not belong to Microsoft.  In that world, Microsoft's market share is anemic.

I'm not saying standards are necessarily evil in and of themselves.  What I am saying is that arbitrary standards imposed by a self-declared governing body are just that:  arbitrary.

Wayland is not an imposed standard.  It has been driven forward as the standard by acclamation.  A better mousetrap. An evolved standard.

---

### Post by mörgæs on 2017-10-09
I know about bug #1 being closed. Just wanted to remind us all about what started the entire Ubuntu project: Market share.

---

### Post by QIII on 2017-10-09
:)

Mark's dream ended up being a pair of pants that chafed too many waistlines.  I said way back then that striking out in that direction was risky and I doubted its wisdom.

Mark is young, enthusiastic, brilliant and visionary.  He got a dose of reality, which is the soil in which wisdom takes root.

But even "standard pants" will chafe many.

Standardization does not drive adoption.  It is the reverse.  It is my contention that the single largest detriment to the adoption of Linux is the zealous notion of getting people to "switch" as if were an either/or proposition.  We shoot ourselves in the foot with that.

---

### Post by mörgæs on 2017-10-09
Yes, Mark's dream. Mir was most certainly driven forward by a self-declared governing body, the SABDFL. Again, respect to him for learning from a mistake. 

Anyway, that's not the point. What matters is that standards give freedom for real creativity because it frees people from wasting time on considering stuff that should be a routine. Since many in the open source community mistake freedom for anarchy some guidelines are necessary.

---

### Post by QIII on 2017-10-09
The guidelines will come when someone produces a breakout product compelling enough for others to emulate.

The decree "Ever shalt thou yoke the horse behind the cart" is detrimental, but it frees you from having to worry about which end to put the cart on.

---

### Post by panaman67 on 2017-10-10
> **mörgæs said:**
> Failure to follow standards is not the same as adding choice. It gives no added benefit to engineers or anyone else that some parts of the world measure length in inches (and in various definitions of inches, to make things even worse) and some in centimeters. It's only a burden to people and it costs real money:

[http://edition.cnn.com/TECH/space/9909/30/mars.metric.02/](http://edition.cnn.com/TECH/space/9909/30/mars.metric.02/)

Market share is everything. Without market share it's impossible to attract developers. Even Microsoft wasn't able to create market share for their phones and had to shut down the project. Market share is not less important just because the project is open source.

Anyone remembers what Bug #1 is about? 

The GNU/Linux community suffers from the Not Invented Here-syndrome. People invent the wheel again in stead of acknowledging that other projects are better. This led Canonical to venture out into building their own display server Mir when everybody else agreed upon Wayland - now, after wasting an unknown number of man-hours Mir is abandoned and also Canonical supports the Wayland standard. My respect for admitting a mistake and learning from it.


This is more or less what I was trying to say. Thank you for summing it up nicly. I agree.

---

### Post by panaman67 on 2017-10-10
> **mörgæs said:**
> Yes, Mark's dream. Mir was most certainly driven forward by a self-declared governing body, the SABDFL. Again, respect to him for learning from a mistake. 

Anyway, that's not the point. What matters is that standards give freedom for real creativity because it frees people from wasting time on considering stuff that should be a routine. Since many in the open source community mistake freedom for anarchy some guidelines are necessary.

I think I love you. I agree. I dont mean that imply that Linux become monotonous and a slave to standards. What we are saying is that freedom and anarchy are 2 different things. Windows has flaws, but as pointed out, some semblance of standards really are helpful. 

Pushing forward the idea that standards kill creativity and choice needs to stop. I think a middle ground between standards and freedom need to be met, but complete freedom is just as bad as dominating standards.

---

### Post by panaman67 on 2017-10-10
> **QIII said:**
> There are dangers in an ecosystem that prizes the ability for each to go his own way.  Who do we elect to populate the standards body?  What is their mandate?  What enforcement agency do they have?  Does their mandate supercede the Linux Consortium/Linux Foundation?  Is Linus bound by their decisions as he decides what should and should not be rolled into the kernel?  Is the standards body bound to Linus' decisions and must they consult with Lake Oswego before making a move?


I would think with a name like the Linux Foundation, they would be the one to post the standards/guidelines. And the community to vote and create it. Standards shouldn't be outsourced or maintained by some group outside the community.

---

### Post by montag dp on 2017-10-11
IMO, you can't have choice and complete standardization. So many times people come bemoaning how segmented Linux is, without realizing that that's what makes it great. Package management is one of those things that people have very different opinions about, and that's part of the reason why there are so many different distros. Standardizing Linux package management is simply not going to happen for that reason. It's a non-starter. 

In short, stop trying to turn Linux into Windows.

---

### Post by panaman67 on 2017-10-11
> **montag dp said:**
> IMO, you can't have choice and complete standardization. So many times people come bemoaning how segmented Linux is, without realizing that that's what makes it great. Package management is one of those things that people have very different opinions about, and that's part of the reason why there are so many different distros. Standardizing Linux package management is simply not going to happen for that reason. It's a non-starter. 

In short, stop trying to turn Linux into Windows.

I would never want to turn Linux into Windows, thats not what i want at all. But there is still a LOT of room for improvement. And COMPLETE standardization is not the goal we should be aiming for. Low level standards in libraries. file systems, and package FORMAT is the goal. Then with good reasonable and helpful standards there, distros and developers can actually use there creativity to do amazing stuff. 

You can have a lot of package managers who all deal with a single package format. 

Realizing Linux has faults and trying to improve on what that all these people are passionate about, including me, doesnt mean im tring to "turn Linux into Windows". It just means im trying to get people talking and working on making Linux better.

---

### Post by ian-weisser on 2017-10-11
The single package format has been done several times, and has never really taken off.
Package and repo convergence has been seriously suggested several times, without notable traction.

You really need to dig into the history: How and why the different package managers (and the corresponding repo infrastructure) developed, and why they didn't naturally converge 10-20 years ago.
There's a lot of history that's based on the basic goals of Debian vs Red Hat, many of which are incompatible or irrelevant to the other.

You're poking at stuff that the survivors of the distro wars have some mighty deep feelings and opinions about.
Beware the flames if you're not appropriately sensitive.

---

### Post by panaman67 on 2017-10-12
> **ian-weisser said:**
> The single package format has been done several times, and has never really taken off.
Package and repo convergence has been seriously suggested several times, without notable traction.

You really need to dig into the history: How and why the different package managers (and the corresponding repo infrastructure) developed, and why they didn't naturally converge 10-20 years ago.
There's a lot of history that's based on the basic goals of Debian vs Red Hat, many of which are incompatible or irrelevant to the other.

You're poking at stuff that the survivors of the distro wars have some mighty deep feelings and opinions about.
Beware the flames if you're not appropriately sensitive.

Fair enough. I understand I have a lot to learn. Im going to do more research on the so called "Distro wars". Could it be that with this time passed, that the Linux community and the people here since the beginning are willing to give it another shot? Im very interested in Linux and want to learn all i can.

---

### Post by ian-weisser on 2017-10-12
You can convince anybody to do just about anything...if you have enough patience to be careful about your application of psychology.
Sure, it's *possible* to convince the management of Red Hat and the voting majority of Debian Developers to invest a great deal of resources together on a single package system.
But it sure won't be easy.
I think that implementing (yet another) standard from anyone else will be ignored (again).

There's a lot of issues to consider: Backwards compatibility, broken scripts, angry users...and for us, all the extra support requirements of all three of those.
It's not like .debs and .rpms are perfect systems. Any cruise through help forums will demonstrate that they are not. PackageKit, Snaps, Flatpacks, AppImages, and more are distro-agnostic software-management systems that try to overcome the problems with older package methods.

---

### Post by vasa1 on 2017-10-12
> **panaman67 said:**
> ... Im very interested in Linux and want to learn all i can.
Are you interested in _learning how to use_ Linux or in _learning about_ Linux? You can do the latter without the former. If you want to learn how to use Linux, test out various distros and pick the one you like most and start using it :)

BTW, Linux is about freedom; people may not want to be told what they should or shouldn't do or what they should or shouldn't think.

---

### Post by pauljw on 2017-10-13
> **vasa1 said:**
> Are you interested in _learning how to use_ Linux or in _learning about_ Linux? You can do the latter without the former. If you want to learn how to use Linux, test out various distros and pick the one you like most and start using it :)

BTW, Linux is about freedom; people may not want to be told what they should or shouldn't do or what they should or shouldn't think.

Exactly, who would be deciding which of us is no longer allowed to create a distro?  Or design yet another method of handling packages.  Freedom is messy, and requires the end user to invest a lot of time figuring out what choice is best for him.  

And regarding "standards" and MS, what about things like open document standards and web standards both of which MS agreed to but ignore on a regular basis.

I much prefer the chaos of freedom and free choice to any centralized standard.  I also prefer PC's to cloud computing, but I'm a dinosaur and remember when we first moved from mainframe/terminal to personal computing.  I don't want to go back.

---

