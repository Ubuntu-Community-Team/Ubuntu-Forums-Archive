---
title: "Canonical should write its own OS"
date: 2010-12-25
forum: The Cafe
---

### Post by Shining Arcanine on 2010-12-25
At present, Canonical repackages the GNU Operating System userland, the Linux kernel, the X11 Windowing system, a few other things; calls it Ubuntu and ships it.

Many people want to see Canonical compete with Microsoft. If Canonical is serious about competing with Microsoft, it should stop repackaging other people's software and write its own. That would give it meticulous control over the development process and allow them to guide the creation of a potential successor to Windows as the world's desktop operating system, much like what Apple has been doing to great success.

That would mean writing:

[LIST]
[*]A boot loader
[*]An OS kernel
[*]A compiler
[*]Core System Libraries
[*]A command shell
[*]An init system - they have Upstart
[*]Daemons
[*]A desktop environment - they have Unity
[/LIST]

There is an abundance of people with the skills to write an operating system that would love the opportunity to do it. It would not be difficult for Canonical to hire them, have them draft a design for the operating system and then have them write it. A great deal of the hard work has already been done for them in the Single Unix Specification.

A big task will be writing drivers for the OS kernel. Canonical is large enough that many companies would likely write drivers for Canonical's operating system. Legacy hardware could be handled by writing some glue code so that old drivers from Linux could used to operate them. As a contingency plan, they could design their OS so that the Linux kernel could be used in place of their kernel. That way if the driver situation is a problem, they can always fallback on Linux. It worked for Richard Stallman.

Writing an operating system from scratch yields several benefits, not the least of which is the possibility to design an operating system with hardware virtualization in mind such that each application could run in a separate virtual machine. An even greater benefit would be that Canonical's developers would only have to worry about their own design decisions, so they would no longer have to decipher code made by other organizations that had different ideas in mind for how an OS should be designed.

Tablets (iOS), smart phones (Android) and netbooks (Google Chrome OS) are posed to replace desktops and laptops as the computing devices of choice, such that it is inevitable that Windows hegemony will end within 10 years. If Canonical does not write is own OS like what Google is doing, I think that what is left of the desktop market will go from Windows hegemony to Mac OS X hegemony. Adopting Google's model where OS development is done in-house and the code is only open sourced upon release, Mac OS X will never fall behind Ubuntu. Why would it when Steve Jobs knows what Canonical will have a year before it has it?

With that in mind, Mark Shuttleworth should hire at least a few dozen talented developers and have them write an OS. It could replace both Ubuntu Linux and stand a chance against Mac OS X, which is increasingly starting to look like the future of the desktop.

---

### Post by Lucradia on 2010-12-25
Why? (I did read your little rant, by the way.)

---

### Post by cascade9 on 2010-12-25
LMAO. 

You honestly think that it would be possible for 'a few dozen developers' to write a kernel?  Lets alone all the other stuff you've listed. 

Besides from the sheer amount of work needed, IMO a lot of ubuntu users would leave if it stopped being a GNU/linux OS.

---

### Post by Spr0k3t on 2010-12-25
I'm one of those people who do not fall under the "many" category.  I would rather Canonical compete with other Linux distributions.  To compete with Microsoft or OSX it has to first become like them... not something I want to see happen.

I don't like the direction going of 11.04 just yet... however, since it's not released yet... I don't have any room to talk.

Besides, what's the time frame to build, test, and release a stable microkernel?  Then there's the change in licensing which would possibly move away from GPL... kind of against what Shuttleworth is wanting in a free operating system.

---

### Post by Dj Melik on 2010-12-25
you better be trolling son.

---

### Post by Shining Arcanine on 2010-12-25
> **Lucradia said:**
> Why? (I did read your little rant, by the way.)

Every other major company marketing operating systems does vertical integration to a large degree. The only time when they truly deviate from that behavior is when they fork other people's software. Microsoft developed Windows and has significant NIH syndrome, which needs no explanation. Apple forked BSD. Google forked Linux and the various userland components that it did not develop on its own. RedHat forks Linux every time it does a release.

Even less prominent groups developing operating systems are doing it in-house. DragonFly BSD, FreeBSD, NetBSD and OpenBSD forked BSD and they develop all of the software needed for their forks within their respective organizations. Haiku does all of its development in house. ReactOS did all of its work in-house too, until recently when it worked out a deal to do code sharing with the WINE project given that they had similar goals and in many areas were developing the same thing.

The groups making Linux distributions are quite small and each have their own special interest. If Canonical is aiming for Microsoft's market position, they will need to write an OS so that they will be in charge of their own destiny. Otherwise, as bloated as Windows, it will be far more agile than Ubuntu. Even when/if Windows dies, Mac OS X would replace it.

If that does not clarify the need for Canonical to write its own OS, then just ignore this thread. I cannot explain it to you.

> **cascade9 said:**
> LMAO. 

You honestly think that it would be possible for 'a few dozen developers' to write a kernel?  Lets alone all the other stuff you've listed. 

Besides from the sheer amount of work needed, IMO a lot of ubuntu users would leave if it stopped being a GNU/linux OS.

I think it is possible for a single developer to write an OS kernel in the span of a month. It would not be a substitute for Linux, but it would fit the definition of a kernel. The first Linux kernel was not particularly fancy, although with a proper development team and sufficient time, it would be possible to design something fairly sophisticated that works well. If you give a dozen people a few years, you could be amazed by the things that they do.

OS development is something that is often taught as part of Computer Science curricula, so it is easier for a group of people to write an OS than you would think.

---

### Post by Spr0k3t on 2010-12-25
> **Shining Arcanine said:**
> Even when/if Windows dies, Mac OS X would replace it.

This is where I think you might want to stop and look at the progression of operating systems everywhere.  Draw the conclusion that is already present and relevant.  It's possible that in a couple years, there isn't going to be an operating system anymore.  It's going to be a common unified platform capable of running applications designed by one software house or another.  There is so much meat in the background showing this progression that a vegetarian would starve.  These giants called "App Stores" are cross pollinating apps like crazy.  One app built for one store gets compiled and rehashed for another, sometimes they aren't even renamed.  The direction we are going to see in the future of computing is going more towards mobile systems.  Tablets are generating more buzz than smartphones did when they first hit the scene.  Granted this universal platform isn't going to kill the desktop, laptop, or smartphones... but the common netbook may be all but gone once the onslaught hits after the CES.  Even Google has started their gamble in the game as a forerunner in the field.  It's not going to be cloud computing... the cloud is out there but it won't work for everyone.  The direction is going to be an operating environment with modules you can plug in for new or different functionality.  I'd say by Windows 8, Microsoft is going to be using a type of repository system complete with leasing or rental terms for most of their products.

You know it's going to happen.

---

### Post by Shining Arcanine on 2010-12-25
> **Spr0k3t said:**
> This is where I think you might want to stop and look at the progression of operating systems everywhere.  Draw the conclusion that is already present and relevant.  It's possible that in a couple years, there isn't going to be an operating system anymore.  It's going to be a common unified platform capable of running applications designed by one software house or another.  There is so much meat in the background showing this progression that a vegetarian would starve.  These giants called "App Stores" are cross pollinating apps like crazy.  One app built for one store gets compiled and rehashed for another, sometimes they aren't even renamed.  The direction we are going to see in the future of computing is going more towards mobile systems.  Tablets are generating more buzz than smartphones did when they first hit the scene.  Granted this universal platform isn't going to kill the desktop, laptop, or smartphones... but the common netbook may be all but gone once the onslaught hits after the CES.  Even Google has started their gamble in the game as a forerunner in the field.  It's not going to be cloud computing... the cloud is out there but it won't work for everyone.  The direction is going to be an operating environment with modules you can plug in for new or different functionality.  I'd say by Windows 8, Microsoft is going to be using a type of repository system complete with leasing or rental terms for most of their products.

You know it's going to happen.

An operating system is "a common unified platform capable of running applications designed by one software house or another". That is the definition of an operating system.

Furthermore, cloud computing is "a common unified platform capable of running applications designed by one software house or another".

I do not see how the creation of "App Stores" changes things. An App Store is a package manager that requires a credit card. Steam is an excellent example of this.

---

### Post by isoscelesrectangle on 2010-12-25
> much like what Apple has been doing to great success.

APPLE WROTE THEIR OWN OPERATING SYSTEM? 
HAHAHAHAHAHHA 
You sir, have just made my day. Merry Christmas to you too!

---

### Post by Spice Weasel on 2010-12-25
They barely manage to repackage Debian once every 6 months, never mind from scratch.

---

### Post by OgreProgrammer on 2010-12-25
You win by making friends, not alienating allies. You win by eliminating competition, not by adding competitors. 

The idea is wholly impractical and its made worse by the fact that you want to throw away strength in numbers. To push the other linux distros away makes them competitors whereas right now they are cooperative allies. Family might squabble, but they unify against outsiders. 

What linux is doing now is great. We are into the PC market. We are in the smart phones. Linux product is strong in the gaming console market. We dominate the servers. 90% of supercomputers run unix/linux. Linux is starting to appear in televisions, in toasters, in refrigerators. 

How many mp3 players run windows? One brand. How many run OS X? One brand. What do you think the others run on? What about all those digital picture frames? 

Linux dominates the embedded device market. 

And you want Canonical to step away from all that because you think going it alone is somehow stronger? You would throw that all away?

No. your idea is ill conceived.

---

### Post by koenn on 2010-12-25
> **Shining Arcanine said:**
> At present, Canonical repackages the GNU Operating System userland, the Linux kernel, the X11 Windowing system, a few other things; calls it Ubuntu and ships it.

Many people want to see Canonical compete with Microsoft. If Canonical is serious about competing with Microsoft, it should stop repackaging other people's software and write its own. [...] .

Canonical's aim is to deliver (existing, already available) free and open source software to its customers. 
starting over from scratch would be the exact opposite of that goal.

---

### Post by andymorton on 2010-12-25
One of the things that attracted me to Linux, including Ubuntu, is the fact that it's supported by a community of people all over the world. If Canonical ditches Linux and then attempts to monopolise computer operating systems the way Microsoft has then I don't want to be a part of it and I imagine a lot of other users would feel the same way.

As has already been said, it's wholly impractical. But aside from that it seems to be against the spirit of Linux, i.e. people working together in an open, transparent way.

---

### Post by mikewhatever on 2010-12-25
This idea is a bunch of ignorant nonsense, so much so, it's not even worth discussing. :rolleyes:

---

### Post by cguy on 2010-12-25
This must be one of the worst ideas in history.

---

### Post by Swagman on 2010-12-25
Ask any Amigan... The problem isn't so much that of the kernel... It's the compatibility of the apps.

No apps = death

---

### Post by Twitch6000 on 2010-12-25
> **isoscelesrectangle said:**
> APPLE WROTE THEIR OWN OPERATING SYSTEM? 
HAHAHAHAHAHHA 
You sir, have just made my day. Merry Christmas to you too!

Yes they really did,so I do not see what you are laughing at unless you mean Canonical instead of apple. Then I understand the joke.

---

### Post by unknownPoster on 2010-12-25
> **Shining Arcanine said:**
> 

I think it is possible for a single developer to write an OS kernel in the span of a month. It would not be a substitute for Linux, but it would fit the definition of a kernel. The first Linux kernel was not particularly fancy, although with a proper development team and sufficient time, it would be possible to design something fairly sophisticated that works well. If you give a dozen people a few years, you could be amazed by the things that they do.

OS development is something that is often taught as part of Computer Science curricula, so it is easier for a group of people to write an OS than you would think.

This post shows how little you know about OS development and programming in general. If your ideas are true, why is GNU/Hurd not successful, or why is Haiku not successful. The simple fact is that it has taken hundreds of developers 20 years to get the Linux kernel to where it is now. How can you possibly expect "a dozen people" to develop a robust kernel in a "few years"?

> 

 If you give a dozen people a few years, you could be amazed by the things that they do.



No, I won't, because they won't have anything substantial in that amount of time.

---

### Post by madjr on 2010-12-25
@Shining Arcanine , dude chill and enjoy xmas, the ubuntu guys are already hard at work doing what they **really** need to, not what *you* think they need to:

[http://www.linuxinsider.com/story/71234.html](http://www.linuxinsider.com/story/71234.html)

[http://www.youtube.com/watch?v=GT5fUcMUfYg](http://www.youtube.com/watch?v=GT5fUcMUfYg)

with your approach they'll just waste years and years of valuable time and in the end it might just become vaporware like i.e *Duke nukem forever*... :D

there are tons of stuff they can do with the resources they have available to them **now**.

Sure we all want ubuntu to be lots more successful, but something that radical is not the best approach.

---

### Post by wojox on 2010-12-25
Unity, Wayland, have you not been following the direction Ubuntu is going in?

---

### Post by Spice Weasel on 2010-12-25
> **isoscelesrectangle said:**
> APPLE WROTE THEIR OWN OPERATING SYSTEM? 
HAHAHAHAHAHHA 
You sir, have just made my day. Merry Christmas to you too!

MacOS < 10?

---

### Post by kgarbutt on 2010-12-25
They kind of are moving in that direction with unity & the notification area.

---

### Post by asifnaz on 2010-12-25
OP I am with you . I dont understand why everybody started flaming you . Bunch of dedicated engineers (not volunteers)  can make a working kernel within 1 year .

Haiku has very small number of developers (all volunteers ) and its already looking stable and promising .

One OS is really required to replace Windows .

Dont worry Linux wont die

---

### Post by Ric_NYC on 2010-12-25
Enough forks already!

Who do you think we are? Guinea pigs?


Well...

---

### Post by andymorton on 2010-12-25
> **Spice Weasel said:**
> MacOS < 10?

Based on Unix rather than being made from scratch.

---

### Post by johntaylor1887 on 2010-12-25
This is one of the most ridiculous threads I've ever seen.

---

### Post by Spice Weasel on 2010-12-25
> **andymorton said:**
> Based on Unix rather than being made from scratch.

You misunderstand me. Apple wrote the entire of Mac OS themselves prior to Mac OSX.

---

### Post by Shining Arcanine on 2010-12-25
> **OgreProgrammer said:**
> You win by making friends, not alienating allies. You win by eliminating competition, not by adding competitors. 

I thought about that too. Canonical already has Stallman et al's official condemnation, so there really is no point in trying to appease them.

[http://www.gnu.org/distros/common-distros.html#Ubuntu](http://www.gnu.org/distros/common-distros.html#Ubuntu)

I cannot think of any major group that would be alienated that Canonical has not already alienated that would be alienated if Canonical wrote its own OS.

> **unknownPoster said:**
> This post shows how little you know about OS development and programming in general. If your ideas are true, why is GNU/Hurd not successful, or why is Haiku not successful. The simple fact is that it has taken hundreds of developers 20 years to get the Linux kernel to where it is now. How can you possibly expect "a dozen people" to develop a robust kernel in a "few years"?

I am a computer science major. What sort of qualifications do you have to tell me that I know "little about OS development and programming in general"?

Anyway, two guys wrote QNX in a year:

[http://en.wikipedia.org/wiki/QNX](http://en.wikipedia.org/wiki/QNX)

GNU/Hurd took an approach to making an OS that was incredibly difficult to do given the design tools that existed at the time. Very few people are working on it and those that are working on it are working within the existing framework.

The majority of Linux kernel development has been on writing device drivers and features for exotic hardware that people do not use. It would be impossible for Canonical to duplicate that, but they likely would have no need to duplicate it. If they ever find a need, they could do what Richard Stallman did and use Linux in place of their kernel.

> **Swagman said:**
> Ask any Amigan... The problem isn't so much that of the kernel... It's the compatibility of the apps.

No apps = death

That is why all major operating systems in use even in specialized applications are some derivative of either Windows or UNIX. Rather than reinventing the wheel, Canonical could write a new UNIX OS and all of the applications already available for Ubuntu would be available for their new operating system.

---

### Post by 3Miro on 2010-12-25
> **johntaylor1887 said:**
> This is one of the most ridiculous threads I've ever seen.

+1. I don't even know what to comment, listing all the things that are wrong here would simply be a waste of time.

---

### Post by wojox on 2010-12-25
> **Spice Weasel said:**
> You misunderstand me. Apple wrote the entire of Mac OS themselves prior to Mac OSX.

+1 The first graphical user interface was developed at the Xerox PARC (Palo Alto Research Center) in the 1970s for the Xerox Alto computer.  Steve Jobs visited there when the interface was under development and saw it as the future of computing, incorporating it into the Apple Lisa’s software platform which eventually led to the Macintosh.

---

### Post by Shining Arcanine on 2010-12-25
> **wojox said:**
> +1 The first graphical user interface was developed at the Xerox PARC (Palo Alto Research Center) in the 1970s for the Xerox Alto computer.  Steve Jobs visited there when the interface was under development and saw it as the future of computing, incorporating it into the Apple Lisa’s software platform which eventually led to the Macintosh.
Apple wrote their own code. The only thing that they copied was the idea. It was a good thing considering that Xerox had no intention of commercializing the idea and would have been content to bury it.

At the same time, I do not see what that has to do with the idea that Canonical should write its own OS.

---

### Post by kaldor on 2010-12-25
Canonical is a new company, and Ubuntu is still young. It's only been around since 2004 and is only now starting to take shape and branch off. Give it time and eventually Ubuntu will be much different; the software centre and Unity are proving this so far. In a few years, Ubuntu will be much more on its own than it is now.

---

### Post by madjr on 2010-12-25
@Shining Arcanine,

sorry, i read your first post several times and i still see no benefit of writing their own os, versus all the stuff they're starting to do now...

can you make a pro / con (whats right and whats wrong) of everything they are doing now versus writing their own os?

---

### Post by Jay Car on 2010-12-25
> **Shining Arcanine said:**
> ...At the same time, I do not see what that has to do with the idea that Canonical should write its own OS.

Your post brought to mind an old saying:
"There are none so blind as those who will not see."

---

### Post by aytech on 2010-12-25
> **Shining Arcanine said:**
> 
Many people want to see Canonical compete with Microsoft. If Canonical is serious about competing with Microsoft, it should stop repackaging other people's software and write its own. That would give it meticulous control over the development process and allow them to guide the creation of a potential successor to Windows as the world's desktop operating system, much like what Apple has been doing to great success.

Isnt that against the whole idea of open source and freedom? If Canonical does just that, it will be another Microsoft, probly the OS they produce will not be free anymore..

---

### Post by BrokenKingpin on 2010-12-25
Why reinvent the wheel? The Linux kernel and a lot of the stuff piled into it is already stable and well known. I could see maybe changing the user interface to be different from other distros (which they are starting to do with Unity I guess), but there is no need to write another kernel.

---

### Post by jshepherd on 2010-12-25
> **aytech said:**
> If Canonical does just that, it will be another Microsoft, probly the OS they produce will not be free anymore..

I was just thinking the same. A team of developers, programmers and marketers would have to be paid. Besides, Shuttleworth is no mug, he knows how to make money and I'm pretty sure a man like that wouldn't give something away he'd invested money in.

---

### Post by Austin25 on 2010-12-25
I don't think they should stop distributing software that was intended to be redistributed. It would be very impractical do rewrite everything.

---

### Post by smellyman on 2010-12-25
> **asifnaz said:**
> OP I am with you . I dont understand why everybody started flaming you . Bunch of dedicated engineers (not volunteers)  can make a working kernel within 1 year .

Haiku has very small number of developers (all volunteers ) and its already looking stable and promising .

One OS is really required to replace Windows .

Dont worry Linux wont die

Already?  Haiku started in t 2001

---

### Post by Barrucadu on 2010-12-25
I'm not sure what you're suggesting. You suggest that they write an OS, but then mentioned:

> Canonical could write a new UNIX OS and all of the applications already available for Ubuntu would be available for their new operating system.

You also said:
> If they ever find a need, they could do what Richard Stallman did and use Linux in place of their kernel.

So what, exactly, do you suggest they make? If you go by those suggestions, Canonical *have* written their own OS. They're using the Linux kernel to provide a UNIX-compatible OS so stuff can be re-used.

---

### Post by MooPi on 2010-12-25
> **Twitch6000 said:**
> Yes they really did,so I do not see what you are laughing at unless you mean Canonical instead of apple. Then I understand the joke.

Apple repackaged BSD ? How is that any different than Canonical repackaging Linux to fit their need ? Needless to say the entire thread is misguided folly. Sure it would be nice that Canonical could write everything from scratch but like many others have said, WHY. The beauty and strength of Linux is the adaptability of it's kernel to everything from super computers to mobile phones. To throw that aside is ludicrous. Besides we are all here or for the most part Linux users enjoying our favorite distro.

---

### Post by phrostbyte on 2010-12-25
> **Spice Weasel said:**
> You misunderstand me. Apple wrote the entire of Mac OS themselves prior to Mac OSX.

The Mac OS kernel was perhaps it's biggest weakness pre-OSX. It didn't even support multitasking or threading in the sense we understand it today. Apple was very right to throw away that code and build upon better FOSS foundations.

Writing a kernel is no joke, and the Linux kernel is an awesome piece of software, which at a technical level no kernel proprietary or open can really compete. If Canonical was to rewrite anything, it should be the monster we call X.org :)

---

### Post by Spr0k3t on 2010-12-25
> **phrostbyte said:**
> If Canonical was to rewrite anything, it should be the monster we call X.org :)

Yeah, where is Wayland when you need him?

---

### Post by mikewhatever on 2010-12-25
> **Shining Arcanine said:**
> ...

I am a computer science major. What sort of qualifications do you have to tell me that I know "little about OS development and programming in general"?

---

Computer science major, that's grand. What have you been smoking when in college? :p

---

### Post by MasterNetra on 2010-12-25
> **Spr0k3t said:**
> Yeah, where is Wayland when you need him?

+1 
-------------------------------------------------------------------------

@OP

Canonical is pushing in it own direction to some degree. They're in the process of producing Wayland, which is to replace x11 and is supposedly going to be better to make and use apps on, amongst whatever the other benefits are. Additionally Fedora plans to use Wayland at some point as I understand it. Granted its still at least a couple years away, but still...

---

### Post by Khakilang on 2010-12-25
Are you talking about Canonical doing something like Debian or Red Had where they create their own software packaging like .rpm and .deb? And maybe create their own software packages call .can? Maybe even their own window manager, desktop manager, file manager etc...? Sorry I may have skim through the thread. But to create an OS from scratch is humongous order. Like some one say why reinvent the wheel. They may do all the above but it is still base on Linux kernel and under GPL.

---

### Post by alaukikyo on 2010-12-26
> **Shining Arcanine said:**
> Canonical is aiming for Microsoft's market position, they will need to write an OS so that they will be in charge of their own destiny.

the codes GPLed and open-sourced so they still are in charge of their own desktiny.
they can control anything in ubuntu

---

### Post by shuttleworthwannabe on 2010-12-26
OS X is not just the software--it is best seen as a hardware-software marriage made in heaven!

Linux as a general rule, works on any hardware as long as there are drivers available; and if not then there are work arounds. 

For Canonical to invent a new OS (based on linux kernel) and brand it as much, will require them to support a huge hardware footprint officially, driver-wise that is, so I guess the idea of new OS is not going to be cost-effective. Leave the development to the worldwide community and let the pace be dictated by what people want, rather than what a company wants for itself. That is what makes Linux based OS so versatile and universal.

Good discussion BTW.

S

---

### Post by MartyBuntu on 2010-12-27
> **shuttleworthwannabe said:**
> OS X is not just the software--**it is best seen as a hardware-software marriage made in heaven!**



If your idea of "heaven" is a locked-down, proprietary, *our-way-or-the-highway* type of heaven.

---

### Post by Twitch6000 on 2010-12-27
> **andymorton said:**
> Based on Unix rather than being made from scratch.

Everything was originally based on unix ... Even windows ...  That don't mean it can't be built from scratch.

Look at FreeBSD and Solaris for instance...

---

### Post by Twitch6000 on 2010-12-27
> **MooPi said:**
> Apple repackaged BSD ? How is that any different than Canonical repackaging Linux to fit their need ? Needless to say the entire thread is misguided folly. Sure it would be nice that Canonical could write everything from scratch but like many others have said, WHY. The beauty and strength of Linux is the adaptability of it's kernel to everything from super computers to mobile phones. To throw that aside is ludicrous. Besides we are all here or for the most part Linux users enjoying our favorite distro.

They did not just repackage BSD. If that was true their kernel would be Monolithic instead of a Mach kernel.

---

### Post by radar920 on 2010-12-27
I have nothing to contribute i just want to say this thread has been an enjoyable read, i hope it continues.

---

### Post by psusi on 2010-12-27
> **Shining Arcanine said:**
> 
I think it is possible for a single developer to write an OS kernel in the span of a month. It would not be a substitute for Linux, but it would fit the definition of a kernel. The first Linux kernel was not particularly fancy, although with a proper development team and sufficient time, it would be possible to design something fairly sophisticated that works well. If you give a dozen people a few years, you could be amazed by the things that they do.

OS development is something that is often taught as part of Computer Science curricula, so it is easier for a group of people to write an OS than you would think.

Depending on how loosely you define it, you can write a tiny kernel in an afternoon in under 1000 lines of code.  It won't be anything even remotely resembling something a desktop user can use to run their pc though.  For that you need to hire 1000 developers and spend a few years on it.

It sounds like you are straight out of high school looking at your college course books for the first time.  Go take some of those operating systems classes and you will find out that they teach fundamental theory, which is a far cry from practical implementation.  Your position is like claiming that if they teach physics 101, then any college grad should be able to build a large hadron collider and produce antimatter.

FYI, I am a regular contributor to Ubuntu, the Linux kernel, and other projects, and spent some time working on the ReactOS kernel a few years ago so I have some idea what it is like.

---

### Post by sffvba[e0rt on 2010-12-27
... wow ... best thread ever...


404

---

### Post by MooPi on 2010-12-27
> **Twitch6000 said:**
> They did not just repackage BSD. If that was true their kernel would be Monolithic instead of a Mach kernel.

Upon reading more in depth I'd like to add that Apple bought the OS and didn't develop the OS in house as you suggest. It is a UNIX variant developed by NeXT (Steve Jobs company later purchased by Apple) with bits and pieces from NetBSD and FreeBSD.
> Yes they really did,so I do not see what you are laughing at unless you mean Canonical instead of apple. Then I understand the joke.
I imagine the final implementation was tweaked and changed to Apples specs but not written completely in house.

---

### Post by zekopeko on 2010-12-27
> **MooPi said:**
> Upon reading more in depth I'd like to add that Apple bought the OS and didn't develop the OS in house as you suggest. It is a UNIX variant developed by NeXT (Steve Jobs company later purchased by Apple) with bits and pieces from NetBSD and FreeBSD.

I imagine the final implementation was tweaked and changed to Apples specs but not written completely in house.

They did write the whole GUI layer of the OS. There is probably more in the GUI layer this days then in what was NeXT.

---

### Post by Twitch6000 on 2010-12-27
> **MooPi said:**
> Upon reading more in depth I'd like to add that Apple bought the OS and didn't develop the OS in house as you suggest. It is a UNIX variant developed by NeXT (Steve Jobs company later purchased by Apple) with bits and pieces from NetBSD and FreeBSD.

I imagine the final implementation was tweaked and changed to Apples specs but not written completely in house.

NeXT was not purchased by Apple they merged back together . There is a difference ;).

They did not but mac os either, mac started in apple and stayed with apple.

NeXT was made by steve jobs when he left apple. Infact the only features that were made in NeXT that are still in MaC is the dock.

Mac sprouted from Apples old Os known as Lisa OS.

---

### Post by Dustin2128 on 2010-12-27
GNU/Linux is an extremely viable operating system, portable to loads of architectures. Why would anyone want to break something that's free and works beautifully on a wide range of systems, to reinvent an entire operating system, taking years, just to change the name? It's like the most anti-hacker thing you can do, especially since you'll end up with the exact same thing after loosing 10 years to the march of progress. Then slackware will be poised to take over the newbie linux user market ;). Also, don't these threads pop up every 10 minutes give or take? Why isn't this in recurring?

---

### Post by madjr on 2010-12-27
> **zekopeko said:**
> They did write the whole GUI layer of the OS. There is probably more in the GUI layer this days then in what was NeXT.

well thats the *less hard* part.

But ubuntu is already doing this:

-Unity/dash
-compiz
-Wayland

---

### Post by mikewhatever on 2010-12-28
> **Twitch6000 said:**
> NeXT was not purchased by Apple they merged back together . There is a difference ;).

...

Merged or purchased, don't get bogged down on the language. The point is that Apple payed 429 million for it.
[https://secure.wikimedia.org/wikipedia/en/wiki/NeXTSTEP](https://secure.wikimedia.org/wikipedia/en/wiki/NeXTSTEP)

---

### Post by Gremlinzzz on 2010-12-28
As long as its not the same old stuff.with a new name.

---

### Post by asifnaz on 2010-12-29
> **smellyman said:**
> Already?  Haiku started in t 2001

I take part in Haiku development  . There are developer fewer than fingers on my left hand . 

Dedicated developers can write a kernel within 2 years . I insist my point .

---

### Post by rg4w on 2010-12-29
> **MartyBuntu said:**
> If your idea of "heaven" is a locked-down, proprietary, *our-way-or-the-highway* type of heaven.
One man's "heaven" is another man's "Stockholm Syndrome". ;)

---

### Post by alaukikyo on 2010-12-29
> **shuttleworthwannabe said:**
> OS X is not just the software--it is best seen as a hardware-software marriage made in heaven!



GET IT STRAIGHT.
OSX IS ALL SENSES IS JUST THE SOFTWARE .
osx is designed to runn of a mac(or apple hardware)
if you assemble a computer with high standard cabinet and good quality components fully compaiable with linux.then you will get the SAME (or higher quality).
for laptops there is not much choice but going for system76 bonobo proffesional:guitar:

---

### Post by shuttleworthwannabe on 2010-12-29
> **rg4w said:**
> One man's "heaven" is another man's "Stockholm Syndrome". ;)

It is important to note that when big players (Apple and now Google) started getting into the OS arena, they have done this by integrating the software with the hardware--marrying the 2 is what will make OS's stand-out. 

S

---

### Post by Johnsie on 2010-12-29
I dont think it should be its own OS. I think Ubuntu should switch from Debian and become and Android based OS.

---

### Post by m4tic on 2010-12-29
> **Johnsie said:**
> I dont think it should be its own OS. I think Ubuntu should switch from Debian and become and Android based OS.

For tablets, maybe

---

### Post by smellyman on 2010-12-29
> **asifnaz said:**
> I take part in Haiku development  . There are developer fewer than fingers on my left hand . 

Dedicated developers can write a kernel within 2 years . I insist my point .

after two years if they have a "working" kernel it will be light years a way from the maturity of Linux, bsd, Mac or Windoes and will be able to comptete with nobody.

---

### Post by Bitrate on 2010-12-29
> **Johnsie said:**
> I dont think it should be its own OS. I think Ubuntu should switch from Debian and become and Android based OS.

What ?

Android is not a pure implementation of GNU/Linux and has very serious security issues to boot. Going down this route is not only misguided but downright dangerous.

Google can not in any way be trusted with the privacy and security of one's data, let alone be the source for a client operating system. This is why I have serious reservations about ChromeOS and many of Google's other nefarious projects. The whole philosophy behind cloud computing and Google's push for centralized computing is just insidiously reckless. It's staggering to see how ill-informed many people are about the massive security implications this entails.

---

### Post by Kirboosy on 2010-12-29
Writing their own OS from scratch would take way to much time and effort. They have a successful OS now. Why would they want to walk away from it and venture into new territory? Besides they would probably have to charge for their new OS to cover the expenses invested in it. They would also have custom applications and drivers written.

Mac OsX isn't the future of desktops. Its a **dictatorial,** dishonest, greedy company run by Steve Jobs. There have been numerous tests that show Windows is faster than Mac. Linux is faster than Windows, therefor Linux > Mac. The two aren't in the same class....ever! Linux is about free will and sharing. Mac is about money, fashion and whatever Steve Jobs pulls out his *** for the year. Mac claiming that OSx is designed for its hardware is totally bullcrap. My Hackintosh blows circles around real Macs out there. And my computer cost less than $1000. 

Apple needs to be shot for starting those commercials "I'm a Mac" and "I'm a PC" I hate to break the Mac users hearts but they are still using a PC (unless its their work computer ;) ) Apple wants to create a sense of superiority and brainwash its users. It has done a very good job at it because Mac users can't see the problem with it.

I work IT and from what I've seen, Windows users generally know more about their computer and how to operate it than the typical Mac user. When someone switches to Mac and I ask them why they switched they generally reply "because its fashionable" or "its *supposed* to be better". When you buy Apple its like a never ending pit that you have to keep buying into. Apple nickles and dimes you for everything. Windows isn't perfect but its at least reasonably priced and has more uses. I can do everything a Mac can on Ubuntu (Linux) and then some all for free!

As a hacker I've seen numerous security flaws but Apple doesn't address it. They simply keep it on the down low and patch it. Mac is always the first to fall at a hacking competition which always makes me smile. To say Mac is more secure than Linux and Windows is just absurd. BSD is at the backbone of OSx but its so modified that they created security holes.

---

### Post by 98cwitr on 2010-12-29
lurk moar OP

---

### Post by salemboot on 2011-01-11
Colleges do teach Operating System development.  You generally can choose the right classes and end up being able to build your own operating system.  

I took one Graduate level course that taught how to write compilers.  We had a working parser and lexer by the end of the course.  Extra credit was generating a binary.  

I suspect it would only take an experienced developer two weeks to write a kernel.

Somebody needs to press hard against the constant changes of the function calls.  There isn't always documentation available.  

2.6.26+ had a set way of creating device drivers and 2.6.30+ changed that with only a mention on the Linux Kernel Mailing list.


I was trying to port Microsoft's Hyper-V driver over to a 2.6.33 kernel.  I was doing fine until I got to the network interface code.

I'm not one that likes control to the point I can't change things but I know as an artist if my palette and canvas keeps changing I'll never be able to create anything.

---

### Post by mdshann on 2011-01-11
The biggest problem I see with this isn't so much getting a usable working kernel as getting a usable working kernel that runs on the millions of possible combinations of hardware out in the wild. If you have been running Linux for any length of time you will have had problems with getting various devices to work such as wireless cards, sound devices, video cards, I/O controllers, etc. Linux has been around since 1991 and still is not supported by many hardware manufacturers! If canonical were to do this they may as well change their name to Pear Computer Corporation and sell hardware certified to work with their O/S otherwise there will be tons of users that cannot use all of their hardware devices. There already are tons of users with problems with various devices just spend some time on this forum and that will be plain as day! Even when hardware manufacturers do support a less popular O/S they do not usually provide drivers for all of the capabilities of their devices. For example most Broadcom cards still cannot be put into monitor mode and tons of people still rely on ndiswrapper to get online. If it were as easy as having the kernel developers write the drivers don't you think we would have working free/oss 3d drivers for our ATI and Nvidia cards by now?

Canonical would be destroyed by this. Hardware manufacturers are going to say "You want me to provide drivers for WHAT?" A company with the capital and market presence of Microsoft can get away with this, and in fact they did when Vista came out with it's new kernel. Hardware manufacturers HAD to write drivers for Vista otherwise they would not have been able to sell their hardware! This would not be true if Canonical came out with CANBUNTU or whatever you want it to be called.

Apple can get away with rewriting their O/S as they control the sales of their hardware, unlike Microsoft and canonical. When Apple comes out with a new O/S they make sure it works with the 5 different machines they sell and then charge a premium for it. This is why my Creative X-Fi does not work in my Hackintosh, Apple doesn't sell or write drivers for Creative hardware.

tldr; writing a kernel and gui apps may not be too bad, but hardware sucks

---

### Post by Johnsie on 2011-01-12
Based on the recent decision to go to Unity I would question Canonicals ability to lead a serious operating system project. Unity might be pretty for the home user, but it's by no means professional or suitable for the workplace.

---

### Post by NCLI on 2011-01-12
> **Johnsie said:**
> Based on the recent decision to go to Unity I would question Canonicals ability to lead a serious operating system project. Unity might be pretty for the home user, but it's by no means professional or suitable for the workplace.

And how are you qualified to judge that based on an alpha release?

---

### Post by WorfSOM on 2011-01-12
> **NCLI said:**
> And how are you qualified to judge that based on an alpha release?

I was going to say the same thing. We aren't even well into the Alpha stage yet and yet people are ready to moan about it.

Unity in 10.10 was terrible for sure, but it wasnt meant for the desktop user and mutter did not help matters. 

The progress made already is outstanding in my opinion.

---

### Post by salemboot on 2011-01-12
Unity is stripping away the non-essentials.
Linux kernel could do good to do the same.  I believe we've all put up with a few bugs that could have been fixed years ago.

As I said in my other post.  It's down right aggravating trying to port drivers just because some developer thought the interfaces were written the wrong way.   

The absolute fact is that there is no right way to do anything!  Just the momentary agreed upon solution.

I've got this saying that goes.  "If doing it the right way ends up breaking everything then do it the wrong way."

anyway

---

### Post by themarker0 on 2011-01-12
I doubt it'd work.

---

### Post by OldBoy44 on 2011-01-12
> **psusi said:**
> Depending on how loosely you define it, you can write a tiny kernel in an afternoon in under 1000 lines of code.  It won't be anything even remotely resembling something a desktop user can use to run their pc though.  For that you need to hire 1000 developers and spend a few years on it.

It sounds like you are straight out of high school looking at your college course books for the first time.  Go take some of those operating systems classes and you will find out that they teach fundamental theory, which is a far cry from practical implementation.  Your position is like claiming that if they teach physics 101, then any college grad should be able to build a large hadron collider and produce antimatter.

FYI, I am a regular contributor to Ubuntu, the Linux kernel, and other projects, and spent some time working on the ReactOS kernel a few years ago so I have some idea what it is like.

Hear, hear!  :)

---

### Post by slackthumbz on 2011-01-13
> **Twitch6000 said:**
> Everything was originally based on unix ... Even windows ...  That don't mean it can't be built from scratch.

Look at FreeBSD and Solaris for instance...

PRO-TIP: FreeBSD was not written from scratch.

> The first CD-ROM (and general net-wide) distribution was FreeBSD 1.0, released in December of 1993. This was based on the 4.3BSD-Lite (&#8220;Net/2&#8221;) tape from U.C. Berkeley, with many components also provided by 386BSD and the Free Software Foundation. It was a fairly reasonable success for a first offering, and we followed it with the highly successful FreeBSD 1.1 release in May of 1994. - [http://www.freebsd.org/doc/handbook/history.html](http://www.freebsd.org/doc/handbook/history.html)

And neither was Solaris.

> On September 4, 1991, Sun announced that it would replace its existing BSD-derived Unix, SunOS 4, with one based on SVR4. This was identified internally as SunOS 5, but a new marketing name was introduced at the same time: Solaris 2.[11] While SunOS 4.1.x micro releases were retroactively named Solaris 1 by Sun, the Solaris name is almost exclusively used to refer to the SVR4-derived SunOS 5.0 and later.[12] - [http://en.wikipedia.org/wiki/Solaris_(operating_system)#History](http://en.wikipedia.org/wiki/Solaris_(operating_system)#History)

And neither was Windows. Windows was originally a primitive graphical shell built on DOS. It wasn't until the advent of XP and the NT kernel that Windows really got away from its DOS roots (and even then you couldn't create a folder called 'nul' or 'con', if you have XP try it and see). The closest to 'based on Unix' that one can suggest about Windows is that the NT kernel borrows a few concepts from VMS. This is unsurprising as the NT kernel was written by some of the original VMS developers.

[http://en.wikipedia.org/wiki/History_of_Microsoft_Windows](http://en.wikipedia.org/wiki/History_of_Microsoft_Windows)

Learn a little history.

---

### Post by psusi on 2011-01-13
> **slackthumbz said:**
> (and even then you couldn't create a folder called 'nul' or 'con', if you have XP try it and see).

Actually you can.  The kernel doesn't mind one bit, but the win32 libraries do some path parsing to emulate dos devices, among other things.  You can disable this by escaping the path.  This will create a file named con in c:\:

echo foo > \\?\c:\con

---

### Post by slackthumbz on 2011-01-13
> **psusi said:**
> Actually you can.  The kernel doesn't mind one bit, but the win32 libraries do some path parsing to emulate dos devices, among other things.  You can disable this by escaping the path.  This will create a file named con in c:\:

echo foo > \\?\c:\con

I stand (well.. sit really) corrected ;)

---

### Post by DangerOnTheRanger on 2011-01-13
> **Shining Arcanine said:**
> At present, Canonical repackages the GNU Operating System userland, the Linux kernel, the X11 Windowing system, a few other things; calls it Ubuntu and ships it.

Many people want to see Canonical compete with Microsoft. If Canonical is serious about competing with Microsoft, it should stop repackaging other people's software and write its own. That would give it meticulous control over the development process and allow them to guide the creation of a potential successor to Windows as the world's desktop operating system, much like what Apple has been doing to great success.

That would mean writing:

[LIST]
[*]A boot loader
[*]An OS kernel
[*]A compiler
[*]Core System Libraries
[*]A command shell
[*]An init system - they have Upstart
[*]Daemons
[*]A desktop environment - they have Unity
[/LIST]

There is an abundance of people with the skills to write an operating system that would love the opportunity to do it. It would not be difficult for Canonical to hire them, have them draft a design for the operating system and then have them write it. A great deal of the hard work has already been done for them in the Single Unix Specification.

A big task will be writing drivers for the OS kernel. Canonical is large enough that many companies would likely write drivers for Canonical's operating system. Legacy hardware could be handled by writing some glue code so that old drivers from Linux could used to operate them. As a contingency plan, they could design their OS so that the Linux kernel could be used in place of their kernel. That way if the driver situation is a problem, they can always fallback on Linux. It worked for Richard Stallman.

Writing an operating system from scratch yields several benefits, not the least of which is the possibility to design an operating system with hardware virtualization in mind such that each application could run in a separate virtual machine. An even greater benefit would be that Canonical's developers would only have to worry about their own design decisions, so they would no longer have to decipher code made by other organizations that had different ideas in mind for how an OS should be designed.

Tablets (iOS), smart phones (Android) and netbooks (Google Chrome OS) are posed to replace desktops and laptops as the computing devices of choice, such that it is inevitable that Windows hegemony will end within 10 years. If Canonical does not write is own OS like what Google is doing, I think that what is left of the desktop market will go from Windows hegemony to Mac OS X hegemony. Adopting Google's model where OS development is done in-house and the code is only open sourced upon release, Mac OS X will never fall behind Ubuntu. Why would it when Steve Jobs knows what Canonical will have a year before it has it?

With that in mind, Mark Shuttleworth should hire at least a few dozen talented developers and have them write an OS. It could replace both Ubuntu Linux and stand a chance against Mac OS X, which is increasingly starting to look like the future of the desktop.

You tried making your own POSIX kernel yet? I don't think so. I have.
It takes *years *to write a kernel, let alone a *complete userland*.
Quit it with your delusional dreams. We all like Ubuntu Linux, and it's good enough.

EDIT: Android uses a modified version of the Linux kernel. That's not from scratch, either. And, Linux already has hardware virtualization. Google KVM.

---

### Post by Eddie Wilson on 2011-01-13
> **Johnsie said:**
> Based on the recent decision to go to Unity I would question Canonicals ability to lead a serious operating system project. Unity might be pretty for the home user, but it's by no means professional or suitable for the workplace.

That is nonsense. Canonicals ability to lead a serious operating system project cannot be questioned with any kind of seriousness. Ubuntu is successful and will continue to be so. You might want to wait for Unity to grow up a little before making it go out on it's own.:D

---

