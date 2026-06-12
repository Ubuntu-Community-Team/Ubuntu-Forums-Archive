---
title: "Does Linux offer developers much at all?"
date: 2009-09-23
forum: The Cafe
---

### Post by haemulon on 2009-09-23
Linux is just not coming together on the desktop, and for desktop applications.

What the Linux community still doesn't understand is that it's all about the applications. 

All too often one is yet again reminded that linux is a kernel, not an operating system.

What does Linux offer developers really anyway?

Not much at all.


All the different distros with different libraries and in different directories, with different versions, even with different names.

So if you are working on a Suse computer one day and try to test on a Ubuntu or Slackware computer the next, nothing will work.

It really is a big mess.

You write an application on Windows and it just works on ALL versions of Windows, and your software is available to a HUGE number of users with the possibility to even make a few dollars from the work.

Maybe a better alternative to Windows will come around, Linux is a big disappointment on the desktop, as it's quite difficult to develop applications that aren't tied to specific distributions.

Linux really should just be for business computing projects (in house development projects).

On the desktop leave to hobbyists and those with lots of free time.

---

### Post by hoppipolla on 2009-09-23
I personally believe the best thing we can offer at the moment is Qt 4 :)

And OpenGL for gaming but it does need a little bit of work o.O


EDIT -- I also totally disagree with your later points... believe me give it a bit more time and you will too! hehe ^_^

---

### Post by Nevon on 2009-09-24
Actually, I think developing in Linux is great. Yes, there are issues with packaging and distributing. But those are overshadowed by the fact that there's so many free tools and libraries out there that you can use in your applications, saving you incredible amounts of time that would otherwise go to reinventing the wheel.

---

### Post by hessiess on 2009-09-24
Developing on Linux is a hell of a lot easier, things are far more standardised than you seam to beleave. Common libs are available on all major distros with the same or very simmaler package names. Theare are also standardised build systems which you can rely on always being avalable, with no equivalent on windows.

The only reason that Windows seams `standardised' is becouse every program ships the libuerys it needs with itself, which results in a huge amount of unneeded duplication and quite frankly, defeats the object of shared libs.

Windows is a horrable platform to develop for.

---

### Post by Chronon on 2009-09-24
It doesn't sound like you're speaking from experience.  As long as you have a build environment set up with compilers and a common set of libraries then you should be able to build your source in any linux environment.

---

### Post by mehaga on 2009-09-24
This is interesting. I'd really like to hear more detailed opinions.

Think of a fairly complex business application. It is based on a database with 50-100 tables. Imagine that one of requirements is a good looking GUI. A fairly common request is that the application needs to be able to work with some kind of office files - text docs, spreadsheets, so let's add that too. Finally, let's say you think this app needs about 4-5 months of work, but you only get 3 to complete it. With all that in mind, please answer following questions.

What programming language(s) would you choose?
What GUI toolkit?
What tools would you use (IDEs, editors, database design tools, GUI designers, build tools etc.)
How would you deal with office stuff?
How would you deal with data access and presentation?
How would your environment help you meet the unfair deadline?
How does the documentation available for your environment compare to MSDN?

For each question, make a comparison to choices usually made by a Windows developer (what makes your choice superior/inferior to his).

Thanks in advance.

---

### Post by hessiess on 2009-09-24
> 
What programming language(s) would you choose?

C++

> 
What GUI toolkit?

GTK, though I do truly hate writing GUI applications.

> 
What tools would you use (IDEs, editors, database design tools, GUI designers, build tools etc.)

Vim + automake.

> 
How would you deal with office stuff?

Pull the relevant code out of OpenOffice, its not the fault of the open source community that MS likes to make vendor lock in file formats.

> 
How would you deal with data access and presentation?

Use a real database (MySQL, postgresql ...) and GTK (again).

> 
How would your environment help you meet the unfair deadline?

Huge number of free libs which could be used.

> 
How does the documentation available for your environment compare to MSDN?

Google ant the open source community are very helpful, regarding documentation generation, Doxygen isn't bad.

Thease points outline perfectly why I have no intention or interest in getting into programming professionally.

---

### Post by bowens44 on 2009-09-24
.

---

### Post by mehaga on 2009-09-24
> **hessiess said:**
> 
C++
GTK, though I do truly hate writing GUI applications.
Vim + automake.
Pull the relevant code out of OpenOffice, its not the fault of the open source community that MS likes to make vendor lock in file formats.
Use a real database (MySQL, postgresql ...) and GTK (again).
Huge number of free libs which could be used.
Google ant the open source community are very helpful, regarding documentation generation, Doxygen isn't bad.


Thanks a lot for your answer, but you missed the comparison part. 

Why are your choices better than those of Windows developer? Few people said (incl. you, IIRC) that developing on Linux is easier/better... Why?

How do Vim + automake compare to Visual Studio for this kind of app?
How would "pulling the code out of OpenOffice" compare to using MS Office in Windows (especially re. the deadline)? 
Why is using MySql or PostgreSQL on Linux better than MySql/PostgreSQL on Windows, or SQL Server? What would you use instead of Management Studio (deadline again)? 
How would data presentation with GTK compare with, say, Windows Forms? Is any sort of data binding available (deadline)? 
When you say "huge number of libs...", does that mean equivalent libs are not available for Windows? 
And I don't understand the last answer - you can Google/ask community when developing for Windows, too...

---

### Post by blueturtl on 2009-09-24
> All the different distros with different libraries and in different directories, with different versions, even with different names.

You gave yourself away, Edgar!

[IMG]http://dezignstuff.com/images/mib324.jpg[/IMG]

---

### Post by hessiess on 2009-09-24
> **vekaz said:**
> Thanks a lot for your answer, but you missed the comparison part. 
How do Vim + automake compare to Visual Studio for this kind of app?

Moe personal preference, but I *HATE* IDE's, they have a tendency to massavly overcomplicate everything and waste a tun of screen space. Theares also the point that automake is *ALWAYS* available on almost any Linux and UNIX computer, which is not true of VS.

> 
How would "pulling the code out of OpenOffice" compare to using MS Office in Windows (especially re. the deadline)?

As stated earlier, this is an unfair comparison because of vendor lock in file formats, use open standards instead.

>  
Why is using MySql or PostgreSQL on Linux better than MySql/PostgreSQL on Windows, or SQL Server? What would you use instead of Management Studio (deadline again)? 

In the original response I was mainly referring to the likes of MS Assess, however I wouldn't trust running any kind of server on any version of windows to be secure and the `drive based' file system works horribly in a networked environment compared to the UNIX single tree model. Also on a UNIX server you can throw out the GUI to save resources, not so with windows.

> 
How would data presentation with GTK compare with, say, Windows Forms? Is any sort of data binding available (deadline)? 

GTK is resolution independent, scalable, and highly theamable. win forms is resolution dependent, not theable and looks awfual.

> 
When you say "huge number of libs...", does that mean equivalent libs are not available for Windows?

They are available, but they are tied to one platform, platform dependence is *BAD*.

>  
And I don't understand the last answer - you can Google/ask community when developing for Windows, too...
Sure you can, but try getting hold of the original developer of a library on Windows.

The primary reason why I will not develop for Windows is that I refuse to write software which is tied to one OS, end of.

---

### Post by HavocXphere on 2009-09-24
> **haemulon said:**
> Linux is just not coming together on the desktop, and for desktop applications.
That is an opinion, not a fact.

My opinion is that it *is* coming together nicely...its just not quite there yet. Small, but crucial difference.

[QUOTE=hoppipolla]And OpenGL for gaming but it does need a little bit of work o.O[/QUOTE]
I read the release info on the new ATI gfx yesterday and what really stood out is all the new DX11 features they implemented. I don't think OGL was even mentioned (OpenCL was though) Seems like *nix is falling further behind in this area.:|

---

### Post by Xbehave on 2009-09-24
******* lol!
[LIST]
[*]There are no toolkits QT/GTK/etc 
[*]There are no frameworks KDE/GNOME/XFCE
[*]There is no expandability in XUL/Kross
[*]There are not many libraries that are compatible in multiple languages
[*]All the big distros ship with the differnt libs 
[*]Libraries and APIs changes are never backwards compatible
[*]There are no tools to assist secure IPC (dbus,dcop,etc)
[/LIST]

Oh no wait none of that is true, in reality most stuff from the most trivial to the most complex will work across multiple versions of multiple distros, and dependancy management can be automatically handled by frameworks (be they distro dependant or language dependend (RoR, perl, etc)

---

### Post by VertexPusher on 2009-09-24
> **haemulon said:**
> You write an application on Windows and it just works on ALL versions of Windows
This is not true, and you know it. The term "DLL hell" was coined by Windows users for a reason.

Version incompatibility in libraries exists on both Windows and Linux alike. It's unavoidable. So how does Windows deal with the problem?

The answer is: Not at all. If you overwrite a system-wide DLL with a different version, you risk breaking a number of applications. Windows developers work around this by **bundling applications with their required DLLs.** Of course this defeats the whole idea of "shared libraries" because nothing is shared any more.

As a result, there will be multiple versions of the same DLL scattered all across the system. This may be OK if you have enough RAM to load them all side by side, if required. But as soon as a security issue occurs with one of these DLLs, you'll find yourself in a world of pain, because Microsoft will only patch system-wide DLLs and those that come with MS Office. 3rd party applications that bring their own versions of these DLLs will still be vulnerable, and you won't realize it. And even if you do, you can't replace the DLLs manually without breaking the applications. So for each affected application you will have to rely on the original developer to release an update that is compatible with the latest version of the DLL. Good luck with that.

You know, people keep wondering: Why is Linux more secure than Windows? Well, this is one of the reasons.

> Linux is a big disappointment on the desktop
You are wrong. Linux, especially in the form of Ubuntu, is a huge success on the desktop.

---

### Post by doas777 on 2009-09-24
@OP:
I can't agree with most of your statements. as a windows developer, I find linux to be a good bit more transparent, and predictable than windows from a dev perspective.

if you wanna complain about oss, then what you need to do is donate. if there is any real lacking in applications, its that the devs get bored (or their personal lives too busy) and never completely finish the app. if you are paying them though, it becomes a differant story.

---

### Post by Simian Man on 2009-09-24
> **hessiess said:**
> Moe personal preference, but I *HATE* IDE's, they have a tendency to massavly overcomplicate everything and waste a tun of screen space. Theares also the point that automake is *ALWAYS* available on almost any Linux and UNIX computer, which is not true of VS.
Guess what I use to program on Windows...gvim and command line tools!  They are all available and perfectly usable on Windows.  And Linux has several great IDEs including Eclipse.

And you can't depend on the user having automake installed.  I believe Ubuntu does not come with it installed by default.  Of course you can have them install it, but you that's asking a bit much of your users.



> **hessiess said:**
> GTK is resolution independent, scalable, and highly theamable. win forms is resolution dependent, not theable and looks awfual.
You're right, too bad there is no GTK+ on Windows!  Oh wait there is, and they also have QT, wxwidgets and other great GUI libraries.


> **hessiess said:**
> They are available, but they are tied to one platform, platform dependence is *BAD*.

The primary reason why I will not develop for Windows is that I refuse to write software which is tied to one OS, end of.

It is perfectly possible to write cross-platform software on Windows.  I had a few games and other apps I wrote on Windows before I really used Linux much and they built and ran perfectly under Linux within an hour of work.  And this was 20K+ lines of code.

Your arguments that developing under Linux is nicer than developing under Windows are kind of moot because nearly all of our great Unix tools exist under Windows as well.  I prefer developing under Linux but because we have workspaces, transparent terminals and so on.  Not because of tools.

Besides, the issue was not so much about developing applications so much as *distributing* them.  The wealth of distributions and package management systems are AWESOME for Linux users but they really suck for independent Linux developers.  If you write something really cool and get your app picked up by the distro pacakgers, you're good but if you want to distribute it yourself it is a headache.

I recently packaged one of the old games I wrote for Fedora (my distro of choice) to learn how to build packages.  I tried installing the rpm under Mandriva under a VM to see if it would work and it failed at dependency resolution.  The reason was because Mandy calls the library "libSDL" instead of "SDL" which is what Fedora uses.  I could make that little change to my spec file and rebuild the rpm for Mandriva and offer both choices, but the number of distros make this too much hassle.  Not to mention my game is ~9 megabytes which means my freewebs account can't hold a dozen different versions of it and you see it really is a headache.

---

### Post by forrestcupp on 2009-09-24
> **haemulon said:**
> 
All the different distros with different libraries and in different directories, with different versions, even with different names.

So if you are working on a Suse computer one day and try to test on a Ubuntu or Slackware computer the next, nothing will work.
Not true.  As long as the dependencies are met, a binary file will run on any distro because they all use the Linux kernel.  The problem is with using packaging, but a straight binary file will work on any distro.  That's why you can use some .run installation scripts on any distro.  It's because it usually just generically installs the binaries and other needed files to your /home folder, and it doesn't matter what the file hierarchy is like.

And don't say Windows never has dependencies.  It's becoming increasingly necessary when you want to run .net stuff and you never know which version it is programmed for.  That's just one example.

> **haemulon said:**
> You write an application on Windows and it just works on ALL versions of Windows, and your software is available to a HUGE number of users with the possibility to even make a few dollars from the work.Have you honestly never run into an XP or Win98 program that didn't work in Vista?

The real problem is just that you can't accept that developing in Linux is different than in Windows.  But MacOsX is so popular and viable, and developing for Mac is different from Windows, too.  Nobody trashes Mac because they use Objective C instead of C or C++, and they have their own GUI system instead of Win32.

Also, like Simian Man said, I program in C++ using wxWidgets for GUI stuff, SFML for 2D gaming and audio, Ogre3D for 3D gaming, and I can compile anything I write for use in Windows *or* Linux.  I can write the same code in Visual Studio or any one of many capable IDE's that work in Linux.  And that is just my personal example.

Linux is known to be good for developing.  Don't trash something that you don't know about.

---

### Post by credobyte on 2009-09-24
Many of RPM's can be alienated, so .. saying that if it works on SUSE, it will not work on Ubuntu, is irresponsible.

---

### Post by 1clue on 2009-09-24
I tried but I can't stay out of this one!

I'm a professional software developer writing commercial software.  My company has 3 developers, we're small.  Those three developers are all using platform of choice.  We include a Windows user, a Linux user (me) and a Mac user.

From the perspective of developing for an OS, we don't.  We write to the Java virtual machine.  It's just what works best for our market.

I'm going to expand the question of the OP, because IMO Linux is a small part of Open Source.  Without Linux and the similar *nix OS operating systems, the free tools you guys are talking about probably would not have caught on nearly as well as they have.  Some of the OS projects that many people associate with Linux have become the most commonly used tool of that type in the world, on any operating system from a cell phone to a supercomputer.

The fact that you can run MySql on Windows, Mac and Linux means that *OPEN SOURCE WORKED!*  Linux and OS is not about making Linux better.  It's about freedom of choice.  There is no such thing as one size fits all.  That's Microsoft's sales pitch, and the folks who really started Linux and OS were all about having something different, not just about avoiding Windows.  Ask most of the OS guys, and they'll tell you that they're not trying to put Microsoft out of business, they just want people to be able to choose which environment they want.  *Edit:  OK, maybe don't ask Richard Stallman.*  :)

The fact that you can run MySql and Apache and OpenOffice on Windows and Mac also means that good apps can really work well cross-platform, and still be very high performance and so easy to set up that OS databases are used for a huge number of commercial vendors, not because the software doesn't cost anything but because it's simply a better product for the use case.  The fact that VMware runs as well on Linux as it does on anything else says that Linux is both a stable environment with a valid use anywhere someone might want it, AND that it's a significant market share.

Development tools:
Hands down, the best text editor for developers is Textmate on the Mac.  I have been a hardcore Vim user for more than a decade.  I finally switched to Eclipse, and am giving IntelliJ a look too.  I know a few developers personally who have bought a Mac just so they could get Textmate, and for no other reason.  They find out later that the fonts on a Mac are far better, and the auto-find-doohickey that opens whatever you start typing is pretty cool too -- and better than what Linux or Windows has to offer.

Personally, I have issues with the way Apple does a lot of things, so I don't use a Mac.  I also have issues with the way Microsoft does things, which is why I don't use Windows.  I strongly agree with the Open Source community and how they do things, so I use Linux.  Sometimes the UI is a pain in the rear, but it's not so much of one that it gets in the way too often.

There are things with programming Java and Groovy that vim and ctags just can't cope with at all, let alone easily or automatically.  I still use Vim a lot, but when it comes down to dealing with the complicated stuff it's an IDE that gets the job done faster.

So we come to the main point of my post:  It's not about the operating system at all, it's about the tools you need to get the job done.  Use what appeals to you.  Look to where those tools came from and support the people who gave you the tools you use.  If you like Windows better, then go use that, and have my blessing.

*Edit again:*
One issue with Microsoft is their licensing terms.  At one point years ago, I read a Microsoft licensing agreement for one of the software development products, that I never bought.  It said (I'm paraphrasing) that by using that software, you agree to never port the software written using that tool to any non-Microsoft platform.  Talk about Big Brother.

---

### Post by koenn on 2009-09-24
> **haemulon said:**
>  Linux is a big disappointment on the desktop, as it's quite difficult to develop applications that aren't tied to specific distributions.

that sentence alone is enough to show that you suffer from one of the following conditions :

1- you have absolutely no idea what you're talking about. 
2- you're a troll
3- you're new to linux, you did not succeed at something you tried to do, so now you have to make all this noise and put the blame on linux because you can't admit that you know less about computers than you thought you did.

---

### Post by Tibuda on 2009-09-24
> **haemulon said:**
> as it's quite difficult to develop applications that aren't tied to specific distributions.

[http://en.wikipedia.org/wiki/Static_build](http://en.wikipedia.org/wiki/Static_build)

Packaging is sure the worst part for ISVs, but they can just ignore this part and provide an auto-executable installer like **they do for Windows**.

---

### Post by Mateo on 2009-09-25
Agree with the original post.  The biggest disappointment with linux development is:

1) Poor documentation. It is sporadic.  Official documentation is usually outdated because there isn't anyone who's exclusive job is documentation.  Unofficial documentation (blog posts, forum posts) can be good, but often contradicts other sources.

2) Poor debugging.  It's 2009, visual debugging makes development 1000% faster.

3) Lack of guaranteed compatibility (as the topic starter said).

4) Lack of high-level compiled languages. There is no (good) linux equivalent to Objective C or C#.

---

### Post by RiceMonster on 2009-09-25
Edit: nevermind

---

### Post by Simian Man on 2009-09-25
> **Mateo said:**
> 4) Lack of high-level compiled languages. There is no (good) linux equivalent to Objective C or C#.

I agree with your other points, but not this one.  Mono is quite mature and is a really good C# implementation which integrates nicely into Gnome.  There is also my favorite language, Objective Caml, which is awesome but maybe a little too obscure for you.

---

### Post by Tibuda on 2009-09-25
> **Mateo said:**
> 4) Lack of high-level compiled languages. There is no (good) linux equivalent to Objective C or C#.

What about: [Objective C]("http://www.linuxjournal.com/article/6009") or [C#]("http://www.mono-project.com/Main_Page")?

---

### Post by Perfect Storm on 2009-09-25
> Maybe a better alternative to Windows will come around, Linux is a big disappointment on the desktop, as it's quite difficult to develop applications that aren't tied to specific distributions.

Have you heard about static binary?

---

### Post by koenn on 2009-09-25
> **Mateo said:**
> Agree with the original post.  The biggest disappointment with linux development is:

1) Poor documentation. It is sporadic.  Official documentation is usually outdated because there isn't anyone who's exclusive job is documentation.  Unofficial documentation (blog posts, forum posts) can be good, but often contradicts other sources.
You have access to all source code so you can read what the software does, how it does it, how to interact with it, ...  And that is insufficient ? 

> **Mateo said:**
> 
2) Poor debugging.  It's 2009, visual debugging makes development 1000% faster.
I've heard of symbolic debuggers and machine-language debugger, but I don't know what you mean with 'visual debugging' - unless you're referring to  a point and click environment - IDE's are available for those who prefer them. 


> **Mateo said:**
> 
3) Lack of guaranteed compatibility (as the topic starter said).
This has been proven wrong by several posts throughout this thread. Maybe you should read them.

> **Mateo said:**
> 
4) Lack of high-level compiled languages. There is no (good) linux equivalent to Objective C or C#.
Gnome is written in Objective C, so what do you mean no support ? they build Gnome on Windows machines ? 
C# is available in Mono. 
Support for GW-Basic leaves something to be desired.


----
All in all, your post sounds like
A/ you don't know what you're talking about
B/ you're trolling

---

### Post by Simian Man on 2009-09-25
[QUOTE=koenn]You have access to all source code so you can read what the software does, how it does it, how to interact with it, ...  And that is insufficient ? [/QUOTE]
Umm...are you kidding?  I have had to refer to the source for documentation many times and it SUCKS compared to actual hyperlinked documentation.  Compare [this]("http://library.gnome.org/devel/gtk/stable/") to this
```
git clone git://git.gnome.org/gtk+
```
And tell me honestly which one you would prefer to deal with when a deadline is approaching!

[QUOTE=koenn]I've heard of symbolic debuggers and machine-language debugger, but I don't know what you mean with 'visual debugging' - unless you're referring to  a point and click environment - IDE's are available for those who prefer them. [/QUOTE]
Sadly gdb is kind of a mess.  It sort of works OK by itself, but the guis for it (including those that come with IDEs) have to work around its limitations.  I understand it has a much tougher Job than Windows debuggers because it supports so many different architectures, but it still leavers a lot to be desired.


[QUOTE=koenn]This has been proven wrong by several posts throughout this thread. Maybe you should read them.[/QUOTE]
There are ways around the issue as people pointed out, but modern Linux is built on package management which *is* a pain to deal with.  Look at most non-free Linux apps like Skype, VirtualBox etc.  They provide a dozen different downloads for each distribution because that's how you make a polished Linux app, but it is a pain.


[QUOTE=koenn]Gnome is written in Objective C, so what do you mean no support ? they build Gnome on Windows machines ? 
C# is available in Mono. 
Support for GW-Basic leaves something to be desired.[/QUOTE]
LOL Objective C is not the same thing as C (which is what Gnome is mostly written in).  But you are right about Mono.

[QUOTE=koenn]All in all, your post sounds like
A/ you don't know what you're talking about
B/ you're trolling[/QUOTE]
Funny I was thinking the same thing about you.  You are clearly not a professional programmer at any rate.

---

### Post by koenn on 2009-09-25
> **Simian Man said:**
> 
Funny I was thinking the same thing about you.  You are clearly not a professional programmer at any rate.
LOL - you're right, I'm not. Not even a hobbyist programmer by any stretch. But then, *I* don't go around posting about how developing for linux sucks. 

> **Simian Man said:**
>  Compare [this]("http://library.gnome.org/devel/gtk/stable/") to ... 
Cool - I believe that someone was trying to make the point that this sort of documentation is lacking for Linux ... Nice of you to provide a counter example :)

> **Simian Man said:**
> 
There are ways around the issue as people pointed out, but modern Linux is built on package management which *is* a pain to deal with.  Look at most non-free Linux apps like Skype, VirtualBox etc.  They provide a dozen different downloads for each distribution because that's how you make a polished Linux app, but it is a pain.

Yes, but that's a packaging issue. and packaging, in so far that it deals with where files should go in the directory three and such, is more of a sysadmin issue than a programming issue.

There are workarounds (like : drop everything in /opt), but basically, and correct me if I'm wrong, the context here is that on an open source platform, so the underlying idea is that you can compile from source for any distro. Therefore,  the *developer* doesn't really need to worry about this (although library versions may be something to look out for). It's only the binary-only programs that need to deal with this by offering all those different installers/packages



> **Simian Man said:**
> 
LOL Objective C is not the same thing as C (which is what Gnome is mostly written in). 

Hm, I seem to remember reading a FAQ or a discussion on gnome.org about the use of Objective-C, but I can't find it right now. 
Anyway, still, the post I replied to claimed there's no support for Objective-C on Linux, which is obviously wrong. 
And I know enough about C to know that it isn't OO, so it must be different from Objective-C ...

---
Other than that, I found your post interesting.

---

### Post by Simian Man on 2009-09-25
[QUOTE=koenn]
Cool - I believe that someone was trying to make the point that this sort of documentation is lacking for Linux ... Nice of you to provide a counter example :)[/quote]
Yeah, the GTK+ documentation is awesome.  If only all libraries had that level of rigor.  I am actually impressed with the overall quality of documentation on Linux given that it is people donating their time for it - and that I personally hate writing docs myself :).


[QUOTE=koenn]Yes, but that's a packaging issue. and packaging, in so far that it deals with where files should go in the directory three and such, is more of a sysadmin issue than a programming issue.

There are workarounds (like : drop everything in /opt), but basically, and correct me if I'm wrong, the context here is that on an open source platform, so the underlying idea is that you can compile from source for any distro. Therefore,  the *developer* doesn't really need to worry about this (although library versions may be something to look out for). It's only the binary-only programs that need to deal with this by offering all those different installers/packages[/quote]
You are right to a certain extent.  For most open-source developers, they can just focus on development and let the distributors package up their releases and take into account any details specific to their distro.

For either non-opensource projects or small developers that want to distribute programs themselves it doesn't work quite so well.  You can either build a static build of your project (which violates the LGPL unless you are writing OSS, so you would be *very* limited when choosing libs), ask the user to build it themselves (which works really well but can be a burden for users), or try to make packages for some subset of the distros out there.

So it can be quite a burden for independent software vendors.


[QUOTE=koenn]Hm, I seem to remember reading a FAQ or a discussion on gnome.org about the use of Objective-C, but I can't find it right now. 
Anyway, still, the post I replied to claimed there's no support for Objective-C on Linux, which is obviously wrong. 
And I know enough about C to know that it isn't OO, so it must be different from Objective-C ...[/QUOTE]

Well Gnome is a big project and includes programs written in several languages, but it is mostly C with a bit of Python and C# (mono).  They are actually moving away from C and investigating using Vala (a new language based on Gobject) and javascript I believe.

There is an Objective-C implementation for Linux called GNUStep, but it's basically a dead project now.


BTW sorry, as I reread my post, I realized I came across a bit rudely :(.

---

### Post by hessiess on 2009-09-25
> 
Hm, I seem to remember reading a FAQ or a discussion on gnome.org about the use of Objective-C, but I can't find it right now.
Anyway, still, the post I replied to claimed there's no support for Objective-C on Linux, which is obviously wrong.
And I know enough about C to know that it isn't OO, so it must be different from Objective-C ...


Gnome Is written in plain C, Object orientation is just a paradigm, it can be applied to any language, though the syntax may be cleaner in a languag directly designed to support object orented programming. Take a look at [http://en.wikipedia.org/wiki/GObject](http://en.wikipedia.org/wiki/GObject).

---

### Post by koenn on 2009-09-25
> **Simian Man said:**
> 
BTW sorry, as I reread my post, I realized I came across a bit rudely :(.
Don't worry about it, I'm not that fragile :)
Besides, I probably come across as rude most of the time myself ...

---

### Post by koenn on 2009-09-25
> **hessiess said:**
> Gnome Is written in plain C, Object orientation is just a paradigm, it can be applied to any language, though the syntax may be cleaner in a languag directly designed to support object orented programming. Take a look at [http://en.wikipedia.org/wiki/GObject](http://en.wikipedia.org/wiki/GObject).
GObject, maybe that's what I was thinking of in stead of Objective-C in regards to Gnome - they both sound like "C with an OO overlay" to me. 

Although I can see that OO is primarily a paradigm, I pretty much doubt you can just apply it to *any* languague. According to the wikipedia article you refer to GObject heavily relies on pointers and macros to pull this of - it leaves me wondering how languages without support for pointers or macros would be able to handle this.
Also, as that articla states,  "programmers with experience in high-level object-oriented languages are likely to find it very tedious to work with GObject in C. For example, creating a non-trivial subclass can require writing and/or copying hundreds of lines of code."

So even if you could write OO in a non-OO language, you probably wouldn't want to.

It all sounds a a lot like  using GOTO to try and emulate functions in a language that doesn't know the concept of functions.

---

### Post by 1clue on 2009-09-25
The best code documentation an application can possibly have is the code itself.

Good code is self-documenting.  The need for a comment to tell you what is going to happen is an indication that there is something smelly going on.  Every modern language supports variables which can be used to describe what that variable is for.  Documentation for parameters and return values is fine, and maybe an overall strategy for the class, but traditional code comments are rarely correct and often totally irrelevant to the actual code being executed.

One exception is a marker for something that needs to change.  We use FIXME and TODO all over, for something we don't have time to fix now but which needs attention later.  Once the task is complete, you get rid of the comment.

Documentation of code is something which needs to be maintained separately.  By definition, it can't be kept in sync with the code without huge expense, and chances are the person doing the documentation won't fully understand what the programmer intended.

Code comments also can be incredibly misleading, the code maintainer reads that and chances are the code has changed 6 times since that comment was written.  The code being referenced might be moved elsewhere or no longer exist at all.

Instead, code should be written such that the entire function/procedure/method can be fit onto a single page of easily readable code.

On top of that, good testing can help document code too.  A unit test can tell you how the snippet was intended to work, and can detect when it no longer works that way.  Integration tests can test whole chunks of the application, in situ.

One thing that the rest of the programming world could learn from Java is documentation through javadocs.  Another thing is the testing strategies developed recently, although I'm not sure Java was the first in that respect. A third thing is the concept of deprecation of code, which was a huge problem with c and c++ last time I looked.

---

### Post by doas777 on 2009-09-25
> **1clue said:**
> The best code documentation an application can possibly have is the code itself.


and the worst is a tie between the RKR C reference, and the official IBM COBOL85 reference.

but I did have a really bad one for DOS\VSE CICS once. that was painful as well.

---

### Post by RiceMonster on 2009-09-25
> **doas777 said:**
> and the worst is a tie between the RKR C reference, and the official IBM COBOL85 reference.

but I did have a really bad one for DOS\VSE CICS once. that was painful as well.

IBM documentation generally sucks. I think I read some of their JCL and Z/OS documentation and it wasn't even slightly helpful.

---

### Post by zipperback on 2009-09-25
> **haemulon said:**
> Linux is just not coming together on the desktop, and for desktop applications.

What the Linux community still doesn't understand is that it's all about the applications. 


The community in general does understand its about applications, however not everyone in the community is a developer, a vast number of Linux users are END USERS that just want their computer to work properly.

A quick check in Synaptic shows there are 26784 packages listed. Thats a huge number of packages available for install.



> **haemulon said:**
> 
All too often one is yet again reminded that linux is a kernel, not an operating system.
What does Linux offer developers really anyway? Not much at all.


Numerous programming languages which are cross platform compatible.
C, C++, Mono, Gambas, Perl, PHP, Python, Ruby, and numerous others.
All available for free.

Non restrictive licenses and available source code.

The list could go on and on.


> **haemulon said:**
> 
All the different distros with different libraries and in different directories, with different versions, even with different names. So if you are working on a Suse computer one day and try to test on a Ubuntu or Slackware computer the next, nothing will work.
It really is a big mess.


Each distribution in general has chosen a package management system which they believe best fits their own needs.

Debian and distributions based upon Debian use .deb packages, which are generally installed with apt-get, synaptic, and aptitude.

Red Hat uses .rpm packages.

It is up to each distribution to decide how they want to handle their package management.

Compiling from source however, providing of course you have the required dependencies installed is generally the same on all distributions.

./configure
make
sudo make install



> **haemulon said:**
> 
You write an application on Windows and it just works on ALL versions of Windows, and your software is available to a HUGE number of users with the possibility to even make a few dollars from the work.


Incorrect. 
Windows 2000 applications won't run on Windows 3.1.
Applications built for Windows XP will not run on Windows 95.

I could go on, but the point is that you are providing information which is not backed up by any factual information.


> **haemulon said:**
> 
Maybe a better alternative to Windows will come around, Linux is a big disappointment on the desktop, as it's quite difficult to develop applications that aren't tied to specific distributions.
Linux really should just be for business computing projects (in house development projects).
On the desktop leave to hobbyists and those with lots of free time.

You've failed to provide any information other than just a rant about "it's too hard..."

If you don't like Linux, the answer is simple for you then.
Don't develop on it. Stick with using your Windows system.
We aren't stopping you. By all means, please use what works best for you.
But at the same time, show the same respect and let others use what works best for them.

- zipperback

---

### Post by 1clue on 2009-09-25
> **zipperback said:**
> 
...
Non restrictive licenses and available source code.
...
- zipperback

While I agree with most of your post, I disagree with this part.  The GPL is every bit as restrictive as anything Microsoft or Oracle has ever put out, just in a different way.

Try releasing commercial software sometime and bundling a GPL library with it.  You can't, and stay legal.  You have to have them get "some implementation of this API" and let them handle it.

Other OS licenses (including LGPL) are much less restrictive and still protect the code from abuse.

---

### Post by koenn on 2009-09-25
> **1clue said:**
> The GPL is every bit as restrictive as anything Microsoft or Oracle has ever put out, just in a different way.
I suggest you go read a Windows EULA, or an MS Shared Code License or something similar, and enumerate what it leaves you with that is actually allowed. Then do the same with GPL, ....

---

### Post by credobyte on 2009-09-25
> **1clue said:**
> While I agree with most of your post, I disagree with this part.  The GPL is every bit as restrictive as anything Microsoft or Oracle has ever put out, just in a different way.

Try releasing commercial software sometime and bundling a GPL library with it.  You can't, and stay legal.  You have to have them get "some implementation of this API" and let them handle it.

Other OS licenses (including LGPL) are much less restrictive and still protect the code from abuse.

> Selling a copy of a free program is legitimate, and we encourage it.

:-k

---

### Post by Mateo on 2009-09-25
> **Simian Man said:**
> I agree with your other points, but not this one.  Mono is quite mature and is a really good C# implementation which integrates nicely into Gnome.  There is also my favorite language, Objective Caml, which is awesome but maybe a little too obscure for you.

I disagree about Mono.  Didn't it just recently get support for .NET 2.0?  Last time I used MonoDevelop, the debugger was broken and not working (i don't say that as an anecdote, it said on the official site that it didn't work).  I don't consider that to be mature.

Objective Caml might be great, but I'm not a fan of functional languages due to not being able to reassign variables.

---

### Post by mehaga on 2009-09-25
To "Linux desktop development rox0rz!" guys...

Compared to Windows, Linux desktop development sucks. If it was the other way around, it would be Windows fighting to gain 5% usage share. "Having many libraries available..." boosts your productivity? If you're writing the next greatest media player I believe you. For anything else... "Best documentation is the code itself..." and "Try getting hold of Windows library developer..." are equally amusing. Documentation - we're not talking about Javadoc kind of documentation here. You need tutorials, books that explain how to achieve some complex task asap. Reading through code would take far more time than you have. Availability of OSS Developers - I tried. Again, a quick how-to is far more accessible. Deadlines, deadlines...

And let's not forget the fact that most stuff you're talking about is also available on Windows. QT is great! It is, but it also works on Windows. Java is awesome! OpenGL rox! SDL ftw! All available on Windows, plus many Windows-only goodies. 

I love Linux as much as you do, but in this area,  unfortunately, it lags far behind the competition. Let's try to change this with some constructive criticism. Please :)

---

### Post by Simian Man on 2009-09-25
> **Mateo said:**
> Objective Caml might be great, but I'm not a fan of functional languages due to not being able to reassign variables.

Ocaml supports functional and imperative programming.  You can certainly reassign variables :)

---

### Post by zipperback on 2009-09-25
> **1clue said:**
> While I agree with most of your post, I disagree with this part.  The GPL is every bit as restrictive as anything Microsoft or Oracle has ever put out, just in a different way.

Try releasing commercial software sometime and bundling a GPL library with it.  You can't, and stay legal.  You have to have them get "some implementation of this API" and let them handle it.

Other OS licenses (including LGPL) are much less restrictive and still protect the code from abuse.


I never said GPL in my original post.
 

> **zipperback said:**
> 
Non restrictive licenses and available source code.


I said "Non restrictive and available source code". 

Here is a link to my original post.
[http://ubuntuforums.org/showpost.php?p=8006864&postcount=37](http://ubuntuforums.org/showpost.php?p=8006864&postcount=37)

If you develop an original application, as the creator of that original application, you have the right to determine what kind of license you will market your software under. 

If you want to develop and market software for commercial purposes, then use a license which you feel best suits your needs.

GPL isn't the only license. Check the following page for several more.
[http://www.gnu.org/philosophy/license-list.html](http://www.gnu.org/philosophy/license-list.html)


- zipperback
:popcorn:

---

### Post by doas777 on 2009-09-25
> **vekaz said:**
> To "Linux desktop development rox0rz!" guys...

Compared to Windows, Linux desktop development sucks. If it was the other way around, it would be Windows fighting to gain 5% usage share. "Having many libraries available..." boosts your productivity? If you're writing the next greatest media player I believe you. For anything else... "Best documentation is the code itself..." and "Try getting hold of Windows library developer..." are equally amusing. Documentation - we're not talking about Javadoc kind of documentation here. You need tutorials, books that explain how to achieve some complex task asap. Reading through code would take far more time than you have. Availability of OSS Developers - I tried. Again, a quick how-to is far more accessible. Deadlines, deadlines...

And let's not forget the fact that most stuff you're talking about is also available on Windows. QT is great! It is, but it also works on Windows. Java is awesome! OpenGL rox! SDL ftw! All available on Windows, plus many Windows-only goodies. 

I love Linux as much as you do, but in this area,  unfortunately, it lags far behind the competition. Let's try to change this with some constructive criticism. Please :)

you've exposed an interesting schism in the computing industry at large; the key differance between IS and IT. I (and from the earmarks, you) are in IT; we write programs for business users that care not a whit for anything but having it work, done ontime, and with a positive cost-benifit-analysis. 

IS guys are usually on a differant end of the spectrum. they are the guys that write the libraries that we consume, develop new protocols and methodologies, and their customers are... well... us.

Windows is great for IT development, but it is terrible for IS dev, because no one can get far enough into it to do what they need to, unless they are a large ISV and can work directly with MS.

Linux is great for IS development because you can customize it to a far greater extent, and really bend it to your will. it can become completely transparent if needed.

so, I guess the quandry is where are you and where do you wanna go? I see myself moving slowly from IT to IS. hopefully someday I'll be there. 

cheers

---

### Post by phrostbyte on 2009-09-25
> **Mateo said:**
> I disagree about Mono.  Didn't it just recently get support for .NET 2.0?  Last time I used MonoDevelop, the debugger was broken and not working (i don't say that as an anecdote, it said on the official site that it didn't work).  I don't consider that to be mature.

Objective Caml might be great, but I'm not a fan of functional languages due to not being able to reassign variables.

Mono trunk supports things all the way to .NET 4.0 (which isn't even released yet!). There are some notable things missing like WPF/WWF, but that's mostly because of lack of demand.

On top of this, there is a whole slew of things Mono can do that .NET can not do. Miguel did a talk on this ironically at a Microsoft convention. I will try to find the video. :)

---

### Post by phrostbyte on 2009-09-25
> **vekaz said:**
> To "Linux desktop development rox0rz!" guys...

Compared to Windows, Linux desktop development sucks. If it was the other way around, it would be Windows fighting to gain 5% usage share. "Having many libraries available..." boosts your productivity? If you're writing the next greatest media player I believe you. For anything else... "Best documentation is the code itself..." and "Try getting hold of Windows library developer..." are equally amusing. Documentation - we're not talking about Javadoc kind of documentation here. You need tutorials, books that explain how to achieve some complex task asap. Reading through code would take far more time than you have. Availability of OSS Developers - I tried. Again, a quick how-to is far more accessible. Deadlines, deadlines...

And let's not forget the fact that most stuff you're talking about is also available on Windows. QT is great! It is, but it also works on Windows. Java is awesome! OpenGL rox! SDL ftw! All available on Windows, plus many Windows-only goodies. 

I love Linux as much as you do, but in this area,  unfortunately, it lags far behind the competition. Let's try to change this with some constructive criticism. Please :)

I don't know if you mean "developing Linux desktop apps" or "developing on the Linux desktop". I will assume the first, correct me if I am wrong.

I suggest you look at [Ruby on Rails]("http://rubyonrails.org/") or [Django]("http://www.djangoproject.com/"). These are RAD web frameworks with no peer. Microsoft is actually playing catch up with them through their "ASP.NET MVC" product. 

Here on Linux these frameworks are IMO more pleasant to work with then it would be on Windows. This is because of the package manager. If I need a set of libraries for development, I simply apt-get them, and use them directly. With Windows I'd have to hunt them down on the 'net, and usually mess with PATH variables.

---

### Post by Mateo on 2009-09-25
> **phrostbyte said:**
> I don't know if you mean "developing Linux desktop apps" or "developing on the Linux desktop". I will assume the first, correct me if I am wrong.

I suggest you look at [Ruby on Rails]("http://rubyonrails.org/") or [Django]("http://www.djangoproject.com/"). These are RAD web frameworks with no peer. Microsoft is actually playing catch up with them through their "ASP.NET MVC" product. 

Here on Linux these frameworks are IMO more pleasant to work with then it would be on Windows. This is because of the package manager. If I need a set of libraries for development, I simply apt-get them, and use them directly. With Windows I'd have to hunt them down on the 'net, and usually mess with PATH variables.

RoR has its own package manager.

---

### Post by 1clue on 2009-09-26
> **koenn said:**
> I suggest you go read a Windows EULA, or an MS Shared Code License or something similar, and enumerate what it leaves you with that is actually allowed. Then do the same with GPL, ....

> **credobyte said:**
> :-k


Go here:
[http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

And scroll all the way to the last paragraph:
> **_*The GNU General Public License does not permit incorporating your program into proprietary programs.*_** If your program is a subroutine library, you may consider it more useful to permit linking proprietary applications with the library. If this is what you want to do, use the GNU Lesser General Public License instead of this License. But first, please read <http://www.gnu.org/philosophy/why-not-lgpl.html>.

The end.  There is no negotiation there.  If a commercial software vendor wants to incorporate GPL'd software then that vendor must negotiate a different license agreement with the owners of the GPL'd software.  The stock GPL does not have a clause in it which allows that to happen.  Some corporate vendors who have GPL'd their software have extra clauses to say that they can release the software under some other license, but stock GPL does not.

Further, if you read the whole license, you'll discover that by trying to incorporate such GPL software, the only way you can really do that is to GPL your software.

So, one thing that you absolutely cannot do with GPL is incorporate it into your code and maintain proprietary control of your portion of the software.  The only way it can be done is if you use an API which some GPL'd software implements, and then the customer can hook the GPL code into it.  For example, an ODBC driver for MySQL is under some sort of OS license, but not all ODBC drivers are GPL or even OS.  So you can have an app which hooks up to ODBC, and somebody can use a MySql driver on it, and you don't lose proprietary license on your software.  You simply have no control over them hooking it up to GPL software in that case.

---

### Post by 1clue on 2009-09-26
> **zipperback said:**
> I never said GPL in my original post.
 
I said "Non restrictive and available source code". 

[/url]


- zipperback
:popcorn:

Zipperback,

You are correct, you didn't say GPL'd software, you said non-restrictive and available source code.  However, every Linux distribution I know of has a whole lot of GPL'd software in it.  GPL is not even sort of a little bit non-restrictive if you are a commercial software vendor with a closed-source, proprietary license.

Most other (non-GPL) OS licenses allow some sort of commercial application.  Apache and FreeBSD licenses come to mind.  Many OS licenses simply make sure that the commercial interests can't claim ownership, although some allow you to incorporate the OS software into a commercial product.  I am under the impression that Microsoft replaced their entire network stack a while back, and used OS to do it.

---

### Post by koenn on 2009-09-26
> **1clue said:**
> 
Further, if you read the whole license, you'll discover that by trying to incorporate such GPL software, the only way you can really do that is to GPL your software.
well, duh ...
That's common knowledge - the GPL does not permit to make GPL software proprietary. If that is a problem for you, don't use GPL'd libraries. 
The reason behind this is that the FSF / the GNU project want to further their cause : They want more Free Software, so they're not very likely to help you do something that goes against their goals : develop proprietary software.
You find that strange ? 


But your point was GPL is more restrictive than "_anything_ MS or Oracle ever came up with", such as 
- licenses that require you accept a  Non Disclosure Agreement
- licenses that do not allow any form of commercial use / distribution
- licenses that don't allow you to distribute your programs other than for in-house use
- licenses that are limited to use on the Windows platform only


sources:
[http://www.microsoft.com/resources/sharedsource/referencesourcelicense.mspx](http://www.microsoft.com/resources/sharedsource/referencesourcelicense.mspx)
[http://www.microsoft.com/resources/sharedsource/productsourcelicensing.mspx](http://www.microsoft.com/resources/sharedsource/productsourcelicensing.mspx)
[http://www.microsoft.com/resources/sharedsource/referencesourcelicense.mspx](http://www.microsoft.com/resources/sharedsource/referencesourcelicense.mspx)
[http://www.microsoft.com/resources/sharedsource/referencesourcelicensing.mspx](http://www.microsoft.com/resources/sharedsource/referencesourcelicensing.mspx)

---

### Post by mehaga on 2009-09-26
> **phrostbyte said:**
> I don't know if you mean "developing Linux desktop apps" or "developing on the Linux desktop". I will assume the first, correct me if I am wrong. 


You assumed correctly, but then you named two web frameworks :) We're talking about desktop apps.

> so, I guess the quandry is where are you and where do you wanna go?
Everything you said makes sense, but...

The question is, where does Linux want to go? If it wants more users, it will need more developers and hence go both ways. Obviously, the direction you call IT (and I have no idea what your acronyms stand for, had to guess from the context :)) needs more work. 

If I understood IT/IS correctly, IS guys could make Linux better for IT development. I'll try to come up with few examples... They can develop a framework similar to Swing Application Framework, but more usable, or DevExpress XAF, but free :). They would love to develop language/toolkit agnostic, declarative UI tools, or tools more suitable for Polyglot programming... IMHO, that would help Linux developer base use it's greatest asset - diversity. My choice of examples may be poor, but that's not the point.

The point is that companies like Canonical keep investing money to decrease boot time by few seconds, and not a dime to make development easier. Microsoft, OTOH... Well, you get the point.

---

### Post by purgatori on 2009-09-26
> So if you are working on a Suse computer one day and try to test on a Ubuntu or Slackware computer the next, nothing will work.

It really is a big mess.

You write an application on Windows and it just works on ALL versions of Windows, and your software is available to a HUGE number of users with the possibility to even make a few dollars from the work.

Two false statements don't make a right.

---

### Post by 1clue on 2009-09-26
> **koenn said:**
> well, duh ...
That's common knowledge - the GPL does not permit to make GPL software proprietary. If that is a problem for you, don't use GPL'd libraries. 
The reason behind this is that the FSF / the GNU project want to further their cause : They want more Free Software, so they're not very likely to help you do something that goes against their goals : develop proprietary software.
You find that strange ? 


But your point was GPL is more restrictive than "_anything_ MS or Oracle ever came up with", such as 
- licenses that require you accept a  Non Disclosure Agreement
- licenses that do not allow any form of commercial use / distribution
- licenses that don't allow you to distribute your programs other than for in-house use
- licenses that are limited to use on the Windows platform only


sources:
[http://www.microsoft.com/resources/sharedsource/referencesourcelicense.mspx](http://www.microsoft.com/resources/sharedsource/referencesourcelicense.mspx)
[http://www.microsoft.com/resources/sharedsource/productsourcelicensing.mspx](http://www.microsoft.com/resources/sharedsource/productsourcelicensing.mspx)
[http://www.microsoft.com/resources/sharedsource/referencesourcelicense.mspx](http://www.microsoft.com/resources/sharedsource/referencesourcelicense.mspx)
[http://www.microsoft.com/resources/sharedsource/referencesourcelicensing.mspx](http://www.microsoft.com/resources/sharedsource/referencesourcelicensing.mspx)

Commercial software and Open Source software can coexist very happily.  I think they SHOULD coexist.  The GPL scares the crap out of just about every large corporation's lawyers.  Apache gets along fine with corporate people.  Apache has all sorts of commercial software that works extremely well with it, and many OS nuts buy commercial software which is completely non-free without thinking twice about it and hook it into apache.  In some cases, the commercial option is the best option.  If you need the best option, that's what you should be able to get.

No matter what commercial vendor licenses say, you can always approach them and say, "I want to do this..." and have them come up with a price.  Then you either pay it or not.  Microsoft DOES have their licensing terms, but they are willing and able to make special terms for a value added reseller.

GNU does not let you do that, ever, for any reason whatsoever--unless there is a specific clause for the project in question which allows other licenses.  If you need a tool that is GPL, then you just as well ignore it and write your own.

It seems that a lot of people don't see a problem here, that there is no conflict of interest.  However, a lot of OS software could be generated from the "price" of using the free software under a slightly different license.  Either by creating/releasing a much-needed tool under an OS license, or by funding OS development of a project in return for being allowed to bend the normal contract in some limited way.

---

### Post by koenn on 2009-09-26
> **1clue said:**
> 
No matter what commercial vendor licenses say, you can always approach them and say, "I want to do this..." and have them come up with a price
You can also approach the copyright owner of the code and see if he's willing to license it to you on different terms ... 

I have no problem understanding that Commercial software and Open Source software can coexis. I run Oracle on RedHat. So what. 

What you want is to use GPL libraries for proprietary programs, and are frustrated that they won't let you. OK, then write your own or get your libraries somewhere else. What's the problem ?

---

### Post by directhex on 2009-09-26
> **Mateo said:**
> I disagree about Mono.  Didn't it just recently get support for .NET 2.0?  Last time I used MonoDevelop, the debugger was broken and not working (i don't say that as an anecdote, it said on the official site that it didn't work).  I don't consider that to be mature.

Objective Caml might be great, but I'm not a fan of functional languages due to not being able to reassign variables.

.NET 2.0 support appeared in Mono 1.1.13, at the start of 2006. How recent is your definition of "recent"?

And MonoDevelop's debugger support was broken by the introduction of a kernel bug in recent kernels preventing proper tracking of PIDs of child processes - it was later worked around.

---

### Post by Twitch6000 on 2009-09-26
> **haemulon said:**
> Linux is just not coming together on the desktop, and for desktop applications.

What the Linux community still doesn't understand is that it's all about the applications. 

All too often one is yet again reminded that linux is a kernel, not an operating system.

What does Linux offer developers really anyway?

Not much at all.


All the different distros with different libraries and in different directories, with different versions, even with different names.

So if you are working on a Suse computer one day and try to test on a Ubuntu or Slackware computer the next, nothing will work.

It really is a big mess.

You write an application on Windows and it just works on ALL versions of Windows, and your software is available to a HUGE number of users with the possibility to even make a few dollars from the work.

Maybe a better alternative to Windows will come around, Linux is a big disappointment on the desktop, as it's quite difficult to develop applications that aren't tied to specific distributions.

Linux really should just be for business computing projects (in house development projects).

On the desktop leave to hobbyists and those with lots of free time.
Do you even know what you are talking about?


> Linux is just not coming together on the desktop, and for desktop applications.

Huh? In the past few years this has been worked on alot. So i see it coming together quite nicely :).

> What the Linux community still doesn't understand is that it's all about the applications. 


uhmm huh I think anyone knows this.

> 
All too often one is yet again reminded that linux is a kernel, not an operating system.


True very true,but when combined with gnu and all the tools it becomes an os :).

> What does Linux offer developers really anyway?

Not much at all./quote]

I disagree,most distros come with basic programming tools. Not to mention qt and gtk ;).

[quote]All the different distros with different libraries and in different directories, with different versions, even with different names.


True to a point,the libary part is wrong. Due to every distro with lets say gnome needs the gnome libs.

> So if you are working on a Suse computer one day and try to test on a Ubuntu or Slackware computer the next, nothing will work.

It really is a big mess.

Incorrect,look at how firefox is made for linux. It works on any distro.
 There is also alien and package kit. 

> 
You write an application on Windows and it just works on ALL versions of Windows, and your software is available to a HUGE number of users with the possibility to even make a few dollars from the work.

HAHAHAH that was funny. You know windows has troubles with dll's on each version right? So yeah that is just a lie.

---

### Post by rucadulu on 2009-09-26
This statement "You write an application on Windows and it just works on ALL versions of Windows" is the biggest misconception in the computer world today. 

Lets see I have apps for Windows 3.1, 95, 98, ME that will not work on Windows NT, 2000, XP, Vista or 7.  

Oh and I have apps for Windows XP that won't work on Vista and 7 as well. 

This is not to mention that now days we have several different sub-versions of the same release Professional, Home, Business edition, etc.  And there are apps that will work one sub-version but not the others. 

Wow kind sounds like Linux and Windows have the issue, all-be damn.  

If you would like a list of the apps that don't work from one Windows version to the next I will be happy to give you a list of the ones that I know of.  

But in the mean time I would love to see you geat MechWarrior2 from Activision working on in Windows NT, 2000, XP, Vista, or 7 If you figure that one out let me know, I won't have to run it in a Windows 98 VM session anymore.

---

### Post by directhex on 2009-09-26
> **Twitch6000 said:**
> HAHAHAH that was funny. You know windows has troubles with dll's on each version right? So yeah that is just a lie.

Take a peek in c:\windows\winsxs on a Vista machine.

That folder contains 14 gig (!) of libraries - essentially bundling the same library loads of times, for every time a library might have broken behaviour, so a particular app can use a particular version with particular breakage - e.g. six versions of System.Workflow.Runtime.dll per architecture

That's the attempted workaround for the breakage in Windows between every update (let alone every version) - 14 gig of old libraries.

---

### Post by 1clue on 2009-09-27
> **koenn said:**
> You can also approach the copyright owner of the code and see if he's willing to license it to you on different terms ... 


That's pretty much what I've been saying.  Oh, you mean the GPL code?  In some cases that's not even possible given the distributed nature of OS software.  Some projects have very few contributors though, in which case it would be pretty easy to do.  With a commercial license, there is specific ownership at all times, and a contract/license can always be negotiated.

> 
I have no problem understanding that Commercial software and Open Source software can coexis. I run Oracle on RedHat. So what. 

What you want is to use GPL libraries for proprietary programs, and are frustrated that they won't let you. OK, then write your own or get your libraries somewhere else. What's the problem ?

I think most people who run Linux use commercial software without thinking twice about it.  It's completely natural and IMO the only system which even remotely makes sense.  Neither the all-commercial guys make sense, nor do the all-OS guys.  You use the tools you need to get the job done.

The only frustration I'm experiencing right now is that people don't get my point.  Oh, and I'm also trying unsuccessfully to install RAID+LVM on an i7 right now, but that's beside the point.

I've been writing commercial software for a decade and a half now.  I've read the OS licensing of several projects, and I don't particularly want to use GPL software, at least not bare-stock GPL.  I use Sun's Java, so I am in fact using a modified GPL.  In that case, the license specifically allows using it to make commercial software.

My only point, which is now beaten into an unrecognizable pulp, is that just because software is open source, it does not mean it is unrestricted.  I can't even remember who posted the comment that set me off on this tangent, but some OS licenses are extremely restrictive in some respects.  GPL being first and foremost of the ones I know of.  Another one is the license for webmin, which can't even remotely be described as "open" even though it's a very small, simple license that lets pretty much anyone use it.  That by the way is why Debian won't include webmin in the package tree.

I used the GPL and commercial integration as an example of how some OS licenses are not unrestrictive.  That's all.  I'm not trying to use GPL software in a way that is not allowed, nor am I frustrated by the situation.  We use plenty of OS libraries, but always within their license terms.  Some licenses work extremely well with commercial software, as I mentioned before.

I think we've pretty much chewed all the flavor out of this subject, and it's not really on topic for the thread anyway, at least not anymore.

---

