---
title: "Unified Package Manager (Autopackage and other ideas)"
date: 2005-07-17
forum: The Cafe
---

### Post by NoTiG on 2005-07-17
Just wondering if in the future it will be possible for them to work together? I mean, i like the idea of having a central repository for some things ... because it makes it really easy to install and maintain things.. and also because it limits spyware / adware since it comes from a central verifiable source ...but it does have some caveats.. namely :

In the future if linux does become more widespread... there is no way that ALL programs will be able to become distributed through the repositories, especially commercial applications.  Secondly, sometimes the programs that are in the repositories arent updated fast enough... for bleeding edge stuff you need an installer.

So will auto package be able to work with synaptic ever? will they be able to exist in harmony and not crap the system? [I saw the vision for the future of autopackage and it looks really nice](http://autopackage.org/ui-vision.html) 

>  A fundamental assumption of this article is that the concept of installers have flawed usability. Firstly, their usefulness is limited: you typically download them or get them on CD, use them, then throw them away. If you don't throw them away you now have two representations of the application on your system: the installer icon, and the launcher for the app itself. It is a user error to click the installer icon at this point, but that's perhaps not obvious to somebody who doesn't really understand what's going on behind the scenes 

>  So, what would our ideal software installation UI look like? Something similar to the appfolders approach, but with an implementation that lets us take it further would be good. For instance, we should be able to launch software directly from an icon embedded in a web page, decide we like the program and drag it to a panel and send it to a friend by dropping it into an email or IM conversation. This should all transfer the minimum amount of data required, deal with dependencies, and the icon name and appearance should be themable and localised into the users language. 

>  You may be thinking that being able to install and run software direct from a web page is rather bad security, but really it's little different to the user downloading and running a .package, RPM or Windows installer normally. Once the user has chosen to give some software access to their system, we should be making it as easy as possible for them to act upon their decisions. Security therefore becomes a matter of how to aid the user in making the correct decisions rather than making their lives inconvenient.

---

### Post by UbuWu on 2005-07-17
[QUOTE=NoTiG]
So will auto package be able to work with synaptic ever? [/QUOTE]

It will when they stick to their plans:

# 1.4 New features for end users:

    * Basic native package manager integration framework: register installed autopackages with RPM and DPKG, uninstall software if it's already installed via the native package manager

# 1.6 Platform management:

    * Add support for using apt-get/yum/etc to resolve missing dependencies if the distro provides them, but they aren't installed

More important: when will this happen?

---

### Post by NoTiG on 2005-07-17
Good question. MOst of the major problems with linux... arent linux's fault... and we dont have much control over them. for instance:

software that is developed with proprietary apis which makes unportable code (VB, Directx etc....)

codecs (mp3, dvix etc.. that cant be legally included)

Drivers for peripherals like scanners, pdas etc....

But the one major problem that linux has control over is the installation of software. And repositories are nice... but they cannot be solely relied on for the distribution of software.

It would have been nice if the google summer of code thing would have sponsored the autopackage dev team. How come there isnt a wider base behind this issue??

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=NoTiG]How come there isnt a wider base behind this issue??[/QUOTE]

Because most Linux Distro developers all prefer their way of installing software. To give an priority to autopackage would require givening up some control over their version of Linux.

I personally agree with you that it would be a good idea. I've always thought Linux needed this, or- even better- something like this that would install the program from source on your computer (using a GUI) and resolve dependancies. The second way would get rid of any binary imcopatibility problems. Basically a tar file with an installer....a kind of portable portage.

I hop to see it. I hate configure make make install and find you own dependancies for new or fringe software.

Hopefully autopackage wil grow, and Linux will be better because of it.

---

### Post by UbuWu on 2005-07-17
[QUOTE=poofyhairguy] I've always thought Linux needed this, or- even better- something like this that would install the program from source on your computer (using a GUI) and resolve dependancies. The second way would get rid of any binary imcopatibility problems. Basically a tar file with an installer....a kind of portable portage.

I hop to see it. I hate configure make make install and find you own dependancies for new or fringe software.
[/QUOTE]

Wow... wouldn't want that as the only option... imagine compiling openoffice for instance. Sounds like what gentoo does. Anyway, autopackage is a great program, but its usefullnes will be mostly in making it possible for commercial programs to be easily installed on any linux system and it would be great for programs that are not yet in the repositories.

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=UbuWu]Wow... wouldn't want that as the only option... imagine compiling openoffice for instance. [/QUOTE]

Ok. It would take a while...but it would be new openoffice without relying on the backport team. Better than make make installing the newest openoffice.

---

### Post by papangul on 2005-07-17
Does autopackage allow installation of precompiled bin packages? I feel the necessity of having the choice to install both from-source and binary versions.

---

### Post by Burgundavia on 2005-07-18
There are a few issues with autopackage. However, it has already (at the current time) rejected by the Ubuntu developers. If it does integrate with dpkg, then the issue might be revisted.

See:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8308](https://bugzilla.ubuntu.com/show_bug.cgi?id=8308)

Corey

---

### Post by duffman25 on 2005-07-20
[QUOTE=Burgundavia]There are a few issues with autopackage. However, it has already (at the current time) rejected by the Ubuntu developers. If it does integrate with dpkg, then the issue might be revisted.

See:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8308](https://bugzilla.ubuntu.com/show_bug.cgi?id=8308)

Corey[/QUOTE]

I've just tried to install alltray with autopackage and it didn't work as intended. Autopackage installed correctly, because it wasn't in my system already, BUT when it tried to install alltray, and asked me for root password, it didn't work (I imagine because root password is disabled in ubuntu) so it didn't work well. I know that running the .package with sudo would probably do the trick, but that's another thing they will need to polish.

On another note, I've tried to uninstall autopackage with it's gtk app manager, and I have to say that it didn't uninstall correctly!  :-x 
I had to workout myself what did it install and delete everything myself. One of my reasons for moving to linux was that using sw as apt you can safely remove sw with all it's dependencies & config. files... 

autopackage still needs work. Maybe they should offer the main autopackage as a deb so you can uninstall it with apt/dpkg. The idea is good, but it needs more work.

---

### Post by NoTiG on 2005-07-20
from therealmike: Right now there's really only 3 of us working on the code. It'll be a long time before all that's done (assuming we carry on working on it!). We need to find more and recruit more developers.

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=Burgundavia] If it does integrate with dpkg, then the issue might be revisted.[/QUOTE]

Forget dpkg, I want it to work with aptitude.

---

### Post by jdong on 2005-07-21
[QUOTE=poofyhairguy]Forget dpkg, I want it to work with aptitude.[/QUOTE]

It sorta has to work on the dpkg level first ;)

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=jdong]It sorta has to work on the dpkg level first ;)[/QUOTE]

Hell....I wish dpkg worked with aptitiude. It sucks when you install deb pacakges by hand that dependancies aren't resolved.

---

### Post by benplaut on 2005-07-22
[QUOTE=jdong]It sorta has to work on the dpkg level first ;)[/QUOTE]

aye... but isn't it better for it to work, after dpkg is accomplished, directly, with apt, instead of one specific program?  :wink:

---

### Post by sapo on 2005-07-22
[QUOTE=poofyhairguy]Hell....I wish dpkg worked with aptitiude. It sucks when you install deb pacakges by hand that dependancies aren't resolved.[/QUOTE]

yep.. i have to install wxpython everytime i want to use it..

when i install it gives me a dependencie error.. but the program works without propblems.. but the next apt-get that i use remove the package  ](*,)

---

### Post by poofyhairguy on 2005-08-03
This often comes up in the Linux community: "why can't they (as in developers) find a way to make files that can install programs on all versions of Linux?"

Window converts especially wonder "why do I have to mess with package managers and tar files? Why can't Linux have an exe?"

I wondered that for a while. Even thought that Linux was inferior at first because it lacks it. Then I discovered the answer. The answer made me respect the Gnu OS a little more, and be suprised at what actually works:

Today I wrote out that answer for everyone to see. I will link it here because I think some people might disagree with my assessment and I want to know where I am wrong. The forum its in now has less people reading it.

The assessment is my opinion, and like most things is not absolute truth. OSS is such a big thing that almost anything is possible, so many disagree with my assessment. Either way , this issue is very relevent to the future of the GNU OS, where it stands and where it is going. I hope the thread is enlightening.

[http://www.ubuntuforums.org/showthread.php?p=285685#post285685](http://www.ubuntuforums.org/showthread.php?p=285685#post285685)

---

### Post by Omnios on 2005-08-03
Sounds pretty good so far. When I first started Linux I had similar questions about exe etc and why source at first I thought it was the way they came. Then I began to understand the cross distro issues etc as Poofyhairguy explains in the link. Now things make total sense and the best part about it is its not that hard and it works. Another thing is Ubuntu even has an amazing synaptic app thats like having tucows come with your OS. 

 One thing the other day I thought what if I had to compile a source in WIndows? I was stumped.

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Omnios]Sounds pretty good so far. When I first started Linux I had similar questions about exe etc and why source at first I thought it was the way they came. Then I began to understand the cross distro issues etc as Poofyhairguy explains in the link. Now things make total sense and the best part about it is its not that hard and it works. Another thing is Ubuntu even has an amazing synaptic app thats like having tucows come with your OS. 

 One thing the other day I thought what if I had to compile a source in WIndows? I was stumped.[/QUOTE]

Linux can't have exes. Windows can't have large repositories of free software to fit many needs. 

Use what fits you best.

---

### Post by N'Jal on 2005-08-04
I like and often use auto package

---

### Post by NoTiG on 2005-08-04
I have a lack of understanding about this. What i dont understand, is that i thought a binary file, was compiled for a cpu architecture, not a distribution. I thought that linux tries to re-use as many library files as possible so it uses shared libraries, which don't get compiled into the actual program. So i thought the difference between an RPM, and a .deb for instance, wasn't the actuall binary file , but it was the way dependencies were handled, and the way the "package" gets unpacked and sent to different directories in the file structure. 

Are the actual binary files incompatible???

---

### Post by kanem on 2005-08-04
[QUOTE=NoTiG]I have a lack of understanding about this. What i dont understand, is that i thought a binary file, was compiled for a cpu architecture, not a distribution. I thought that linux tries to re-use as many library files as possible so it uses shared libraries, which don't get compiled into the actual program. So i thought the difference between an RPM, and a .deb for instance, wasn't the actuall binary file , but it was the way dependencies were handled, and the way the "package" gets unpacked and sent to different directories in the file structure. 

Are the actual binary files incompatible???[/QUOTE]It's just like what you said. The 'incompatability' comes from libraries being in different places in the filesytem, or having a different name, or the kernel being vastly different. Also the actual package putting stuff in different places for different distros. 

But the binaries aren't inherently incompatible. You just have to make sure the two systems are similar enough. Sometimes I've had trouble getting an app to compile in Ubuntu (even though I had all dependencies) and just emerged it in Gentoo and used the binaries it generated. I wouldn't expect this to always work, but it has so far.

Things like [Alien](http://www.kitenet.net/programs/alien/) depend on there being some compatibility. If you used Alien to try to install many rpm's I'd imagine (based on the failure rate) it would give a sense of just how compatible an rpm distro is with Debian based ones. Probably somewhat, but not 100%

---

### Post by kanem on 2005-08-04
What does the exe extension have to do with how you install stuff? Installers in Windows having exe extensions just reflects the fact that the installer itself is an executable. The actual programs, the binaries themselves that are put in Program Files that you double click to run also have exe extensions.

Same as the executables that are put in our /usr/bin. We even have some .exe stuff thanks to Mono.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=NoTiG]
Are the actual binary files incompatible???[/QUOTE]

Kinda. They expect libs to be in different places. The only way around that is to make special packages for each....doh....you saw where I was going.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=kanem]What does the exe extension have to do with how you install stuff? Installers in Windows having exe extensions just reflects the fact that the installer itself is an executable.[/QUOTE]

I was just using that as a term to mean installer. There are so many Windows installers, it would be stupid to pick one and say that.

---

### Post by UbuWu on 2005-08-04
[QUOTE=poofyhairguy]Linux can't have exes. Windows can't have large repositories of free software to fit many needs. 
[/QUOTE]

Of course windows can have a large repository of free software if someone decides to make it... Most of the best open source programs can also be used on windows (firefox, openoffice, inkscape, etc.), putting them together on one server isn't difficult at all.

---

### Post by UbuWu on 2005-08-04
[QUOTE=poofyhairguy]Kinda. They expect libs to be in different places. The only way around that is to make special packages for each....doh....you saw where I was going.[/QUOTE]

A statically linked program will work on just about any linux distro. Just installed inkscape .42 that way on hoary. It needs libs that aren't on hoary, but that's no problem. It is just that a dynamically linked program has a lot of other advantages.

---

### Post by Knome_fan on 2005-08-04
Though I see where you are coming from, I think it's actually a lot more complicated. I just read the other thread you mentioned and let's just say, Mike Hearn really begs to differ:
[http://www.ubuntuforums.org/showpost.php?p=286197&postcount=184](http://www.ubuntuforums.org/showpost.php?p=286197&postcount=184)

---

### Post by charlieg on 2005-08-04
**poofyhairguy:** It looks like somebody, who knows a thing or two about a thing or two, vehemently disagrees with you:
[http://www.ubuntuforums.org/showpost.php?p=286197&postcount=184](http://www.ubuntuforums.org/showpost.php?p=286197&postcount=184)

EDIT: ***looks up*** Ah, I'm not the only one reading that thread.  :smile:

---

### Post by macgyver2 on 2005-08-04
Just a general observation...IMHO saying things like "it's an impossible dream" or that it "won't come" is, well, wrong.  Were everyone on the forums were to list everything we could think of that at one time someone said was "an impossible dream", we would be posting for the next...who knows how long.  At one point in history, were I to have told someone that I could communicate instantaneously with someone a thousand miles away, I would have been derided with calls of "that's impossible" (or maybe I would have been burned as a warlock for possessing some form of "magic").  Yet I'm doing it right now on IM.

"Magic" does exist in the real world...it's just that once something "magical" happens, we realize it wasn't really ever magic at all.

I realize we are each entitled to his or her own opinion...but when you state an opinion, please make sure everyone reading it knows it's your opinion.  I think the post you link to reads too much as fact when it's really just your opinion.

---

### Post by qalimas on 2005-08-04
[QUOTE=poofyhairguy]This often comes up in the Linux community: "why can't they (as in developers) find a way to make files that can install programs on all versions of Linux?"

Window converts especially wonder "why do I have to mess with package managers and tar files? Why can't Linux have an exe?"

I wondered that for a while. Even thought that Linux was inferior at first because it lacks it. Then I discovered the answer. The answer made me respect the Gnu OS a little more, and be suprised at what actually works:

Today I wrote out that answer for everyone to see. I will link it here because I think some people might disagree with my assessment and I want to know where I am wrong. The forum its in now has less people reading it.

[http://www.ubuntuforums.org/showthread.php?p=285685#post285685](http://www.ubuntuforums.org/showthread.php?p=285685#post285685)[/QUOTE]

Very well said! :D

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=charlieg]**poofyhairguy:** It looks like somebody, who knows a thing or two about a thing or two, vehemently disagrees with you:
[http://www.ubuntuforums.org/showpost.php?p=286197&postcount=184](http://www.ubuntuforums.org/showpost.php?p=286197&postcount=184)
[/QUOTE]

Good. I posted all of that (and posted the link here) to give audiance to dissidence.

I wanted to hear more sides. My point still stands -getting to where Windows is seems impossible- but I won't say that nothing can be done.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=macgyver2]
I realize we are each entitled to his or her own opinion...but when you state an opinion, please make sure everyone reading it knows it's your opinion.  I think the 
post you link to reads too much as fact when it's really just your opinion.[/QUOTE]

Well.....I used to write editorials as an occupation. I tried to structure that like an editorial. I left no sources besides me, and I used the same writing style I used in the past.

But you are correct....I guess if I think about it magic happens everyday when you aren't noticing.

I just have really high expectations.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=UbuWu]A statically linked program will work on just about any linux distro. Just installed inkscape .42 that way on hoary. It needs libs that aren't on hoary, but that's no problem. It is just that a dynamically linked program has a lot of other advantages.[/QUOTE]

I'm hoping that work to integrate with a native package manger will fix those problems. Yet autopackage doing that is still not the "Windows way"....I would love to see it work.

Tar files do need replacing.

---

### Post by BWF89 on 2005-08-04
[QUOTE=Poofyhairguy from the other thread this one links to]hey only way something will work on all of them is the most primative of all software packages (the tar file) because by compiling it on your system you are making it compatible with the OS you have. Thats how even BSDs can install Linux tar files.[/QUOTE]
Then why don't we all just use tar files? When I was duel booting with Fedora Core 2 and WinXP last Christmas before I had to reload Windows and thus delete FC2 I installed Firefox was a tar file off of Mozilla.org. And it was incredibally easy. If I remember all you had to do was unzip the file in your home folder, find out the name of the install file, and go into terminal and type in something like:

```
Type in the path to home
-Type in the name of the foulder off of Mozilla.org
-Type in the name of the file that had the word install on it

Then some text flashed across terminal and the FF graphical installer came up.
```

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]Good. I posted all of that (and posted the link here) to give audiance to dissidence.

I wanted to hear more sides. My point still stands -getting to where Windows is seems impossible- but I won't say that nothing can be done.[/QUOTE]

Well, as your point was that binary compatability doesn't exist and won't come and Mike Hearn emphatically disagreed with this assessment from a technical point of view (which is far over my head, I freely admit this), I don't see how you can really claim that your point still stands.

At least I did find nothing in your answer to Mike Hearn in the unfortunately now closed thread that even addresses the technical points he brought up:
> So listen to me - when we tell you that binary compatibility on Linux exists, and is real, you had better pay attention.

Do you understand dynamic linking? Have you read the ELF specifications? The source code to the Linux dynamic linker? What about how dynamic linking works on MacOS X or Windows?

Do you understand DSO versioning, symbol versioning? Do you understand the difference between an API break, an ABI break and a semantic interface break? Do you understand how it's possible to break source code such that it will no longer compile yet the binaries produced on another machine will work perfectly? Do you understand that this is not just theoretical but happens all the time?

Do you know what weak linking is?

---

### Post by Knome_fan on 2005-08-04
[QUOTE=BWF89]Then why don't we all just use tar files? When I was duel booting with Fedora Core 2 and WinXP last Christmas before I had to reload Windows and thus delete FC2 I installed Firefox was a tar file off of Mozilla.org. And it was incredibally easy. If I remember all you had to do was unzip the file in your home folder, find out the name of the install file, and go into terminal and type in something like:

```
-Home
-Firefox foulder
-Firefox install file
```[/QUOTE]

I think he means tar files in the sense of having a source archive you'll still have to compile to get the app to work. But you are right, there are of course other things besides source archives that come as tar files.

---

### Post by Brunellus on 2005-08-04
[QUOTE=Knome_fan]I think he means tar files in the sense of having a source archive you'll still have to compile to get the app to work. But you are right, there are of course other things besides source archives that come as tar files.[/QUOTE]
 ...isn't that portage?

---

### Post by Knome_fan on 2005-08-04
[QUOTE=Brunellus]...isn't that portage?[/QUOTE]
Yes and no.
You are right that most of the time people on gentoo are installing source archives via portage.

Portage is a (great imho) tool that helps you compile the stuff you want from source.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]Well, as your point was that binary compatability doesn't exist and won't come and Mike Hearn emphatically disagreed with this assessment from a technical point of view (which is far over my head, I freely admit this), I don't see how you can really claim that your point still stands.

At least I did find nothing in your answer to Mike Hearn in the unfortunately now closed thread that even addresses the technical points he brought up:[/QUOTE]

Then I'll do it right here Gnome fan. I'll use an example.

Lets say I'm using....Warty. I want to install the newest GIMP using autopackage. Unfortunately lets say the newest GIMP relies on newer versions of important base libraries. How does autopackage get around that? The only way my package manager has those is if I upgrade. Does autopackage install the newest version of libs (aka bringing all the libs with it in one big file), despite the problems they might cause with my old programs that depend on the old libs?

[http://www.iecc.com/linker/linker10.html](http://www.iecc.com/linker/linker10.html)
> 
Beyond issues of call compatibility, a chronic source of problems is changes in library semantics. Since dynamic shared libraries are so easy to update compared to unshared or static shared libraries, it's easy to change libraries that are in use by existing programs, which means that the behavior of those programs changes even though "nothing has changed". This is a frequent source of problems on Microsoft Windows, where programs use a lot of shared libraries, libraries go through a lot of versions, and library version control is not very sophisticated. Most programs ship with copies of all of the libraries they use, and installers often will inadvertently install an older version of a shared library on top of a newer one, breaking programs that are expecting features found in the newer one. Well-behaved applications pop up a warning before installing an older library over a newer one, but even so, programs that depend on semantics of older libraries have been known to break when newer versions replace the older ones.
Mike's answer did not give me the answer to that problem: the biggest problem concerning binary compatibility.

---

### Post by macgyver2 on 2005-08-04
[QUOTE=poofyhairguy]Well.....I used to write editorials as an occupation. I tried to structure that like an editorial. I left no sources besides me, and I used the same writing style I used in the past.[/QUOTE]

That doesn't surprise me...the post was very well written in terms of organization and continuity and readability...  But in terms of content...I suppose I have the same reaction as I did to your post when I read the newspaper and see the articles in the op/ed section reading like fact (and on the other hand the articles in the news sections reading like opinion).

[QUOTE=poofyhairguy]I just have really high expectations.[/QUOTE]

Nothing wrong with that!  Isn't that why, after all, 1) most of us on these forums prefer Linux, and 2) we decided to try Ubuntu? ;-)

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]Then I'll do it right here Gnome fan. I'll use an example.

Lets say I'm using....Warty. I want to install the newest GIMP using autopackage. Unfortunately lets say the newest GIMP relies on newer versions of important base libraries. How does autopackage get around that? The only way my package manager has those is if I upgrade. Does autopackage install the newest version of libs (aka bringing all the libs with it in one big file), despite the problems they might cause with my old programs that depend on the old libs?

[http://www.iecc.com/linker/linker10.html](http://www.iecc.com/linker/linker10.html)

Mike's answer did not give me the answer to that problem: the biggest problem concerning binary compatibility.[/QUOTE]

Oh, on the contrary I think it did, though again, I'm really in over my head when it comes to this. But he pointed out that the story about shared libraries isn't as simplistic is you seem to believe. At least that's what I discern from my minimal knowlegde about DOS and symbol versioning he mentiones. 

And he further claimed that autopackage addresses these points. Now again, I don't have any intimate knowledge of how autopackage works and I don't have the necessary knowledge to really understand it anyway, so I can't really say if and how autopackage addresses them. However as autopackage is free software and as he specifically posted two progams (or rather, their code), anyone with more knowledge than I have on this matter should be able to see if and how theses things are addressed.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=macgyver2]That doesn't surprise me...the post was very well written in terms of organization and continuity and readability...  But in terms of content...I suppose I have the same reaction as I did to your post when I read the newspaper and see the articles in the op/ed section reading like fact (and on the other hand the articles in the news sections reading like opinion).[/QUOTE]

Just so you know: A rule in editorial writing is that you present your opinion as fact. You never say "this is my opinion," you force the reader to chose what information to acccept as fact.

Its probably not the most moral way to do it (even though it might be...hmm....elitist...I did worry when I wrote professionally that some people might have problems seperating the two), but its how I was trained.

The biggest mistake I made was making that point on that thread. As a moderator I should have known that that is not the place for such things- it sucks someone had to point that out for me.

My bad.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]Oh, on the contrary I think it did, though again, I'm really in over my head when it comes to this. But he pointed out that the story about shared libraries isn't as simplistic is you seem to believe. At least that's what I discern from my minimal knowlegde about DOS and symbol versioning he mentiones. 

And he further claimed that autopackage addresses these points. Now again, I don't have any intimate knowledge of how autopackage works and I don't have the necessary knowledge to really understand it anyway, so I can't really say if and how autopackage addresses them. However as autopackage is free software and as he specifically posted two progams (or rather, their code), anyone with more knowledge than I have on this matter should be able to see if and how theses things are addressed.[/QUOTE]

From what I understand, he addressed the point "Distros having libs in all different places named different things." And he discussed ways to get around basic lib problems. I also understand that he showed how a Distro with newer libs than those needed can be used. I figured that was the weaker problem anyway (early on I suggested that I could imagine a system to get around it...he pointed out the system that can).


How do you get around the problem of needing newer libs than the system has? What if these libs have a feature the programs needs? In Windowsland, the installer just copies the newest libs over the old ones (after asking many times). Can you do this in Linux without undermining the package manager, or compromising the structure of the distro? Can it be done?

I don't know. If there is a way, please educate me. My main point revolves around that- that is the primary difference between the GNU OS and others. If I can be shown a solution to that problem (that is elegant) then I will admit I'm 100% wrong and that perfect binary compatiblity is more than possible.

There is a reason the backport project won't touch major libs.

If I am ignorant about this, then please enlighten me. Don't get mad, get teh truth out.

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]
How do you get around the problem of needing newer libs than the system has? What if these libs have a feature the programs needs? In Windowsland, the installer just copies the newest libs over the old ones (after asking many times). Can you do this in Linux without undermining the package manager, or compromising the structure of the distro? Can it be done?
[/QUOTE]

So all you said boils down to:
If an app needs a newer lib, the newer lib has to be installed?
And doesn't autopackage try to exactly do that?

---

### Post by Amaranth on 2005-08-04
Some libraries can be replaced without issue, others do stupid things and can't be so they are given a new SONAME (libfoo.so.X.Y.Z). I don't understand what the problem is here.

However a general rule seems to be that if you want to distribute a binary program it should be built against glibc 2.2, GTK+ 2.2, GNOME 2.4, and it should statically link everything else.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]So all you said boils down to:
If an app needs a newer lib, the newer lib has to be installed?
And doesn't autopackage try to exactly do that?[/QUOTE]

Autopackage is about installing programs. From what I've seen it one day expects to use native package managers to resolve dependancy problems (such as libs). So when you install a program with autopackage in the future, it will work with apt-get to get whatever that package needs.

What I am asking is what happens when the package manager lacks the newer lib that is needed? Does the autopackage include all the libs it needs? Does it copy over my older libs with the newer ones to get the new program to run? Doesn't that compromise the entire make-up of a person's distro? Won't that create problems with previously installed programs that rely on those old libs? Won't that really change the distro? How could you get the package manager to recognize these newer libs? As it is now, everything in the official repository works with the libs at the levels I have them, so it isn't a problem. How does autopackage solve this problem?

How do you get around these problems? I really want to know. I'd rather be wrong about it all and someone tells me a solution to that problem today. I really don't mind being wrong. Doesn't bug me as long as I learn something in the process.

I think that neither you nor I are actually qualified to discuss such things knome fan. But If I stopped myself from posting everytime I wasn't qualified to post, I would have 1/100th the post count I do (I know you might see that as a good thing).

---

### Post by godsunderstudy on 2005-08-04
[QUOTE=poofyhairguy]
Lets say I'm using....Warty. I want to install the newest GIMP using autopackage. Unfortunately lets say the newest GIMP relies on newer versions of important base libraries. How does autopackage get around that? The only way my package manager has those is if I upgrade. Does autopackage install the newest version of libs (aka bringing all the libs with it in one big file), despite the problems they might cause with my old programs that depend on the old libs?
[/QUOTE]

Lets say I'm using... Windows 95. I have a program that needs Windows XP. Why O why can't I install it?

---

### Post by lithorus on 2005-08-04
[QUOTE=Amaranth]Some libraries can be replaced without issue, others do stupid things and can't be so they are given a new SONAME (libfoo.so.X.Y.Z). I don't understand what the problem is here.[/QUOTE]
Imagine that autopackage upgraded xxxlib 1.0.1 without notifying dpkg with a newer version 1.0.2 because there is needed the xxx feature in that lib. Then a few days later there is a security fix for xxxlib in apt/dpkg(which does get released without the need to distro-upgrade). This will then overwrite xxxlib 1.0.2 with 1.0.1ubuntu1. What you have now is breakage...

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]
What I am asking is what happens when the package manager lacks the newer lib that is needed? Does the autopackage include all the libs it needs?
[/quote]
As I said, I really am no expert on autopackage, but from what I gathered so far, it simply installs the new lib.

[QUOTE=poofyhairguy]
Does it copy over my older libs with the newer ones to get the new program to run?
[/quote]
No, and as has been repeatedly explained alread it doesn't have to.

[QUOTE=poofyhairguy]
Doesn't that compromise the entire make-up of a person's distro?
[/quote]
No, why should it. But it will certainly a cleaner solution once it gets integrated into the package manager and notifies your distribution, so to speak.

[QUOTE=poofyhairguy]
Won't that create problems with previously installed programs that rely on those old libs?
[/quote]
As again, the old libs are still present, nope.

[QUOTE=poofyhairguy]
Won't that really change the distro?
[/quote]
How would it?

[QUOTE=poofyhairguy]
How could you get the package manager to recognize these newer libs?
[/quote]
Well, again I'm no expert, but apt certainly stores in some way what libs are installed, so merely getting it to recognice it should be rather trivial I guess.

[QUOTE=poofyhairguy]
As it is now, everything in the official repository works with the libs at the levels I have them, so it isn't a problem. How does autopackage solve this problem?
[/quote]
Again, what problem.

[QUOTE=poofyhairguy]
How do you get around these problems? I really want to know.
[/quote]
Well, they are no problems.

[QUOTE=poofyhairguy]
(I know you might see that as a good thing).[/QUOTE]
Not really. I enjoy your posts, though I don't necessarily agree with all of them.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=godsunderstudy]Lets say I'm using... Windows 95. I have a program that needs Windows XP. Why O why can't I install it?[/QUOTE]

You are joking but you help prove my point. How do you get around this problem? In Windowsland releases are so few and far between that this problem doesn't rear it ugly head that much. But what do you do when some libs are upgraded every year, or twice a year? What do you do when when the stable releases of your distro doesn't come around that much (such as Debian stable)? 

You point is that "Windows doesn't even do this. In Windows you need the newest version or it doesn't work." Well....Windows doesn't crank out (stable) versions of major libs as much as the GNU OS does. Thats the WHOLE problem. All the distros are too different: one has newer libs than another, one completely lacks this or that lib, etc.

In Windows, most software made for XP can run on 2000. That means that new software will work on an OS that is over five years old. Will autopackage work easily on a five year old install of Linux? Can it do that without making lib problems? You make fun of me for saying Warty, but Warty is less than a year old. How can a system claim to be "the answer to the problem of binary incompatibilities in Linux" when it can't install software on a distro that is less than one year old without changing large parts of it? Noe the package managers don 't even try to beat this, and that leads to one of the biggest gripes about current methods of installation in Linux.

Will autopackage (in those cases) require everyone who uses it to have the newest release? To have stuff that your own distro only has in its "cooker" or "unstable" development version?

If this is the case I am correct. My point is proven. I unfortunately win this stupid debate. I don't want to win, someone please show me the light.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]As I said, I really am no expert on autopackage, but from what I gathered so far, it simply installs the new lib.[/QUOTE]

If anything about that was simple Gnome Fan someone would have done this years ago.


> No, and as has been repeatedly explained alread it doesn't have to.

No, why should it. But it will certainly a cleaner solution once it gets integrated into the package manager and notifies your distribution, so to speak.

Ok...so it doesn't copy over the old lib. Fine. It installs the new lib along side the old lib. How can you get the package managers deal with that? They aren't built to have more than one version of a lib at one time. but you need them to resolve dependancies.

When you upgrade you distro with the package manager, does it install over the libs you added with autopackage? Each package manager uses a different system to know if one package is newer than another, how can you make it so that EVERY TIME you add a lib, the package manager knows to replace it with the newer official version when you upgrade?

In Windows you simply copy over the old lib. Thats a way to solve the problem. that way won't work in Linux because each distro has its own way of dealing with libs. The Ubuntu developers spend a lot of time stabilizing and working of the base libs for the next release. When the release comes, the libs are set up how they want to make the OS work well together. If you start to mess with those libs, you compromise their work and essentially change the distro (which will force autopackage to be exactly what I said in the last thread it would start out as: an inferior way to install packages when the package manager can't instead of a wonderful bold new and better way to install packages).

I know autopackage is not meant to replace package managers....but it can't ignore them and their ways. 

I have too many questions.

> 
Not really. I enjoy your posts, though I don't necessarily agree with all of them.

Well...Knome fan you keep me on my toes. I must thank you for that.

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]If anything about that was simple Gnome Fan someone would have done this years ago.
[/quote]
Well, as several versions of one lib are routinly installed on every linux system I ever used it has been done for years already.

[QUOTE=poofyhairguy]
Ok...so it doesn't copy over the old lib. Fine. It installs the new lib along side the old lib. How can you get the package managers deal with that? They aren't built to have more than one version of a lib at one time. but you need them to resolve dependancies.
[/quote]
You underestimate the power of current package managers. They handle different versions of one lib just fine.

[QUOTE=poofyhairguy]
When you upgrade you distro with the package manager, does it install over the libs you added with autopackage? 
[/quote]
As autopackage currently does not integrate with the package manager I'm sure it won't. If autopackage in the future integrates with the package manager it will if possible and needed and it will not if it's not possible and not needed, at least I guess that that's what it will do.

[QUOTE=poofyhairguy]
Each package manager uses a different system to know if one package is newer than another, how can you make it so that EVERY TIME you add a lib, the package manager knows to replace it with the newer official version when you upgrade?
[/quote]
I don't really understand your question here, but when autopackage integrates with the package manager in the future it has to use the versioning system of the package manager, otherwise it couldn't integrate, could it? So I don't really see a problem here.

[QUOTE=poofyhairguy]
Well...Knome fan you keep me on my toes. I must thank you for that.[/QUOTE]
All my pleasure. *evilgrin* (Just joking  ;-) )

---

### Post by poofyhairguy on 2005-08-04
This is fun knome fan, you are doing a good job to answer my questions.

[QUOTE=Knome_fan]
You underestimate the power of current package managers. They handle different versions of one lib just fine.[/QUOTE]

Ok. I know that apt-get does handle multiple versions of some libs often (as they are packaged differently). But what I don't know is how apt-get could take account of libs that aren't in its repos. I bet the rest of your post answers that.

> 
As autopackage currently does not integrate with the package manager I'm sure it won't. If autopackage in the future integrates with the package manager it will if possible and needed and it will not if it's not possible and not needed, at least I guess that that's what it will do.

That confused me. Doesn't autopackage plan to work with the package managers? Or does it have its own method of resolving dependancies?

> 
I don't really understand your question here, but when autopackage integrates with the package manager in the future it has to use the versioning system of the package manager, otherwise it couldn't integrate, could it? So I don't really see a problem here.

I see your point. You are saying that part of getting the system working with the package manager would fix this problem. Is that the biggest problem? Is that why this hasn't been done before? Because its hard to work with all the different package managers?

Since at some level autopackage would resolve its own dependancies (aka for libs where the version needed is not in the package manager) will this be dealt with by adding every needed dependancy to the autopackage, or will it have a seperate dependancy resolution system?

Would a program installed by autopackage show up in synaptic as if you installed it from a deb file? Will the package managers take care of removing autopackage software that you don't want or that is made obsolete by an release upgrade? 
[B]
How can autopackage deal with systems that lack huge dependancies? For example, a program that needs the newest KDE libs (pretty big stuff) when your distro lacks them in the central repository? It seems like that could get messy. What if a program needs the newest KDE, the newest Xorg, and a newer kernel version that the distro its being installed on? Will the autopackages just have huge install files to include EVERY possible dependancy?[/B]

Will autopackage start to have its own central repo to hold dependancies needed?

EDIT: I bolded my most important question.

---

### Post by Knome_fan on 2005-08-04
> **poofyhairguy]This is fun knome fan, you are doing a good job to answer my questions.
[/quote]
Thanks. I'm trying my best, so a lot of what I say will probably cause those who really know this stuff cry out in pain.   said:**
> 
Ok. I know that apt-get does handle multiple versions of some libs often (as they are packaged differently). But what I don't know is how apt-get could take account of libs that aren't in its repos. I bet the rest of your post answers that.

I don't think it's really a question of being in the repos, but off being installed. So if autopackage installes a lib it can simply notify the package manager that it did, so that the package manager knows it's there.

[QUOTE=poofyhairguy]
That confused me. Doesn't autopackage plan to work with the package managers? Or does it have its own method of resolving dependancies?
[/quote]
Right now it doesn't integrate, so the package manager does not interfere so to say with the stuff installed with autopackage. And yes, I think it has its own method of resolving dependencies right now as far as I know.

[QUOTE=poofyhairguy]
I see your point. You are saying that part of getting the system working with the package manager would fix this problem. Is that the biggest problem? Is that why this hasn't been done before? Because its hard to work with all the different package managers?
[/quote]
I'm only guessing here, but I think that this probably one of the problems the autopackage devs are facing.

[QUOTE=poofyhairguy]
Since at some level autopackage would resolve its own dependancies (aka for libs where the version needed is not in the package manager) will this be dealt with by adding every needed dependancy to the autopackage, or will it have a seperate dependancy resolution system?
[/quote]
I'm not really sure how they do it actually, but I guess they add a lot to the actual package, though I think they also have some dependency resolution implementd.

[QUOTE=poofyhairguy]
Would a program installed by autopackage show up in synaptic as if you installed it from a deb file? Will the package managers take care of removing autopackage software that you don't want or that is made obsolete by an release upgrade? 
[/quote]
AFAIK autopackage right now comes with its own management tool for the packages you installed via autopackage, how they plan to do it in the future, I don't know, but I'd guess that a package would automatically show up in synaptic if autopackage integrates with the package manager.

[QUOTE=poofyhairguy]
How can autopackage deal with systems that lack huge dependancies? For example, a program that needs the newest KDE libs (pretty big stuff) when your distro lacks them in the central repository? It seems like that could get messy. What if a program needs the newest KDE, the newest Xorg, and a newer kernel version that the distro its being installed on? Will the autopackages just have huge install files to include EVERY possible dependancy?
[/quote]
I honestly don't know how and if they address a situation like this. (Well, I guess if a new kernel is needed, an autopackage is simply out of the question) It's probably best to take a look at the autopackage site, they have a lot of documentation about what they are actually doing, or ask Mike Hearn directly. After all he is a member of this forum.

[QUOTE=poofyhairguy]
Will autopackage start to have its own central repo to hold dependancies needed?[/QUOTE]
As they want to get rid of central repositories for normal apps, I don't think that's the plan.

Edit:
I just had an idea. As this has largely become a discussion about autopackage and we both don't really know the ins and outs of it (to put it mildly) and as autopackage seems to be a hot topic for many people here, how about you as a mod ask Mike Hearn if he would be willing to post something here in this forum explaining autopackage. How it works, what they are trying to achieve, how they are trying to achieve it, what the biggest problems are, what their future plans are for autopackage. I think a lot of people would be interested in this and I hope he would be interested in answering some questions and clear up some misunderstandings about autopackage.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]
I honestly don't know how and if they address a situation like this. (Well, I guess if a new kernel is needed, an autopackage is simply out of the question) It's probably best to take a look at the autopackage site, they have a lot of documentation about what they are actually doing, or ask Mike Hearn directly. After all he is a member of this forum.
[/QUOTE]

Thanks for your answers Knome Fan I guess I hit the wall with how much you and I know... I would just PM Mike about my bolded question but I don't want it to come off as an attack. 

I really like the idea of autopackage. I'm not some Linux elitist that hates the Window way of doing things just because its the Windows way.

Good idea on looking to the site. I got a few questions answered:

How will it handle dependancies?

> 
 If a dependency is missing, it can be installed automatically from another autopackage (which ideally is maintained by the dependency maintainers themselves).

How will programs uninstall?

>  Because the launchers on the users desktop (and in their menu) now contains the package name you can trigger an uninstall by dragging the app to the trash can. One alternative is to garbage collect desktop packages: this would be an opt in system whereby any packages that were marked as collectable were tracked for reachability in a similar manner to how objects are garbage collected in a managed runtime such as Java. When no more desktop entries are reachable from any users account, the software is safe to delete.


Will it work with package manager?

> 
For these reasons, we plan to add native package manager integration as a high priority feature in the next major development cycle after 1.0.

unfortunately, I didn't get my bold questioned answered. This is as close as it came:

> 
Well, you could try and convince the library maintainers to produce their own autopackages, you could produce your own (make sure upstream know you're doing this!), or you could statically link the library. Long term the solution to this problem is the development of a desktop Linux platform, so it's possible to predict with certainty what will be available on your users systems.

So basically autopackage doesn't have the answer to my bolded question. There is its weak point. The creator of the documentation is saying "that will be fixed when Linux has common standards."

Damn. Well, no one can call me a complete idiot...I was kinda right. The lack of standards and consistancy won't be magically solved by autopackage. I've found that anything that plans to rely on agreed upon standards in the Linux community (such as the Linux Standards Base) is almost asking for failure.

That means (unfortunately) at some level I was correct. It is near impossible for binary compatiblity to exist at the same level it does on Windows. There can't be a solution that works 99.999% of the time (yet).

Here is the long term solution the autopackage site suggests:

> 
 A desktop Linux platform would help, because instead of enumerating the dependencies of an app each time (dependencies that may be missing on the users system), application authors can simply say that their program requires "Desktop Linux v1.0" - a distribution that provides platform v1.3 is guaranteed to satisfy that. Support for a given platform version implies that a large number of libraries are installed.

The platform would update every year, meaning that for applications that were Desktop Linux compatible (or whatever branding was used), there would be a worst-case upgrade lifespan of 12 months.

A platform is more than just providing a bunch of packages. It implies a commitment to stability - that's why it's called a platform. Would you want to build your house on sand? No? Neither do application developers, and this is why a platform is so important.

In the other thread I said that getting a binary to work on all of the Linuxs would be harder than using magic. But then I admitted that in a general sense miracles happen and magic (in a perspective) does exist.

Asking for a "desktop linux platform" is WAY harder than getting magic to work. That is on the level of World Peace, flying to the nearest star, or making objects out of thin air. Star Trek stuff.

The ONLY way I ever see that happening is if one Distro "wins." One becomes "the desktop distro" above all others. Then in that case whatever pacakge that distro used (if it was ubuntu it would be .deb) would be the standard package format.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]
I just had an idea. As this has largely become a discussion about autopackage and we both don't really know the ins and outs of it (to put it mildly) and as autopackage seems to be a hot topic for many people here, how about you as a mod ask Mike Hearn if he would be willing to post something here in this forum explaining autopackage. How it works, what they are trying to achieve, how they are trying to achieve it, what the biggest problems are, what their future plans are for autopackage. I think a lot of people would be interested in this and I hope he would be interested in answering some questions and clear up some misunderstandings about autopackage.[/QUOTE]

Actually, the site does a good job of presenting autopackage. A lot is there. 

Plus....if you didn't notice...he is not to happy with me.

---

### Post by Amaranth on 2005-08-04
[QUOTE=poofyhairguy]You are joking but you help prove my point. How do you get around this problem? In Windowsland releases are so few and far between that this problem doesn't rear it ugly head that much. But what do you do when some libs are upgraded every year, or twice a year? What do you do when when the stable releases of your distro doesn't come around that much (such as Debian stable)? 

You point is that "Windows doesn't even do this. In Windows you need the newest version or it doesn't work." Well....Windows doesn't crank out (stable) versions of major libs as much as the GNU OS does. Thats the WHOLE problem. All the distros are too different: one has newer libs than another, one completely lacks this or that lib, etc.

In Windows, most software made for XP can run on 2000. That means that new software will work on an OS that is over five years old. Will autopackage work easily on a five year old install of Linux? Can it do that without making lib problems? You make fun of me for saying Warty, but Warty is less than a year old. How can a system claim to be "the answer to the problem of binary incompatibilities in Linux" when it can't install software on a distro that is less than one year old without changing large parts of it? Noe the package managers don 't even try to beat this, and that leads to one of the biggest gripes about current methods of installation in Linux.

Will autopackage (in those cases) require everyone who uses it to have the newest release? To have stuff that your own distro only has in its "cooker" or "unstable" development version?

If this is the case I am correct. My point is proven. I unfortunately win this stupid debate. I don't want to win, someone please show me the light.[/QUOTE]
 These apps only work on Windows 2000 because they don't use things that are only in Windows XP. So, the answer on linux is the same as windows. Target older versions of the main libraries and bring everything else you need with you.

---

### Post by Knome_fan on 2005-08-04
[QUOTE=poofyhairguy]
unfortunately, I didn't get my bold questioned answered. This is as close as it came:

So basically autopackage doesn't have the answer to my bolded question. There is its weak point. The creator of the documentation is saying "that will be fixed when Linux has common standards."
[/quote]
While I agree that this is a problem, I don't really think it's fair to point to autopackage in this instance. It is intended for normal applications (not for core system stuff). If it really achieves that people are simply able to install gnome or kde apps with it and the only thing that's needed for this is that they either already have gnome or kde installed, or it is installable on their distro (which should be the case on almost any distro), it's still a major achievement, isn't it?

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Amaranth] Target older versions of the main libraries and bring everything else you need with you.[/QUOTE]

How old though? And what if you need features only the new libs have?

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Knome_fan]If it really achieves that people are simply able to install gnome or kde apps with it and the only thing that's needed for this is that they either already have gnome or kde installed, or it is installable on their distro (which should be the case on almost any distro), it's still a major achievement, isn't it?[/QUOTE]

It is. As I said, the idea has many merits, and might become "the official way" to install closed source applications and drivers in Linux.

Its a great thing. I will use it to install stuff I don't want to bug jdong about (to backport).

But...my premise is correct. Since I don't believe standards can work, and any universal install system in Linux would rely on standards to create universal binaries that work on all Linux systems (or at least the rate that Windows or OSX binaries do), then universal binaries that work 99.9999% of the time aren't going to be here any time soon. 

So the person that asks "why can't Linux have an install system like Windows?" gets their answer.

Autopackage at its best will replace the tar file, but it will not replace apt-get. Thats a truth that I am sad to report and discover...but its a fact of life.

---

### Post by Amaranth on 2005-08-04
[QUOTE=poofyhairguy]How old though? And what if you need features only the new libs have?[/QUOTE]
 What if you need features only available on Windows XP SP2 with .NET Framework 1.1 and GTK# installed? You hope users go along with you and live with the consequences or you relax the dependencies and live without things.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Amaranth]What if you need features only available on Windows XP SP2 with .NET Framework 1.1 and GTK# installed? You hope users go along with you and live with the consequences or you relax the dependencies and live without things.[/QUOTE]

Well....in Windowsland backward compatibility is the biggest goal and problem. The GNU OS is less focused on that..

---

### Post by Amaranth on 2005-08-04
[QUOTE=poofyhairguy]Well....in Windowsland backward compatibility is the biggest goal and problem. The GNU OS is less focused on that..[/QUOTE]
 That doesn't help the poor users without SP 2, .NET 1.1, and GTK# installed. Windows has the same issues as Linux but the developers have **experience** working with them. Linux developers mostly just toss code out there and let the users/packagers figure out what to do.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Amaranth]That doesn't help the poor users without SP 2, .NET 1.1, and GTK# installed. Windows has the same issues as Linux but the developers have **experience** working with them. Linux developers mostly just toss code out there and let the users/packagers figure out what to do.[/QUOTE]


Good point. The releases are less too. SP2 was the first big upgrade to Windows since XP was released. So.....three years with no new release. Debian stable timeline there.

---

### Post by Amaranth on 2005-08-04
The releases happen less often but linux users also upgrade faster. A good portion of windows users will have Windows 98.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Amaranth]The releases happen less often but linux users also upgrade faster. A good portion of windows users will have Windows 98.[/QUOTE]

True. Its pretty different worlds really.

---

### Post by r_a_trip on 2005-08-04
***I wanted to hear more sides. My point still stands -getting to where Windows is seems impossible- but I won't say that nothing can be done.***

Poofyhairguy, you are absolutely spot on. Getting all GNU/Linux distributions to become 100% binary compatible is a pipe-dream. Not because it is a technical matter, but a philosophical one.

What all the "proprietary OS refugees" seem to forget is that the OS they came from was manufactured by a sole entity. The basic decisions of what the OS is, lay in the hands of one sole "dictator". This way you can make sure that binaries install on every copy out there.

Microsoft is the entity that has vigorously promoted the idea that Windows = Windows = Windows = Windows. MS went out of their way (spending billions) to make it seem that all disparate versions of Windows operate as one single system. (Apple has caused some more breakage, but could sell it in the name of innovation.)

When we want to translate this to the GNU/Linux eco-system, we get into trouble. We don't have (nor want, for that matter) GNU/Linux = GNU/Linux = GNU/Linux = GNU/Linux. Every distribution has its own design team calling the shots. As a consequence, all GNU/Linux distributions are in effect different Operating Systems. (Just like all cars are basically equal, but not identical)

Is it tecnically impossible to make all GNU/Linux systems the same? No. Just kill all distributions except one. Then all copies of GNU/Linux are binary compatible across the board. The only problem with this solution is that it imposes the same failing "one size fits all" philosophy on to GNU/Linux that plagues that other commercial system.

The price for 100% binary compatibility is the sacrifice of choice, innovation and low barrier to entry. If we were to make all distributions the same, there would be no wiggle room, no way of trying unproven ways of making something new. GNU/Linux would become a bureaucracy that forbade projects like Symphony OS, BeaTrix, Blue Eyed OS, Famelix and many others, current and future ones.

An ".exe" is very well possible on GNU/Linux. Autopackage is an implementation of that solution. Although the project members describe it as the second coming, I agree with Poofyhairguy that it has to prove itself some more.

I've fiddled with it and it seems to do what it says it does. Yet Autopackage has the same shortcoming as any other package format on GNU/Linux. Packages still need to be made by people who know how to package them properly. End users are not automagically liberated from waiting for the software.

Plus in it's current incarnation, Autopackage jams itself into the system without registering itself with the native dependancy management system. This is bound to give some nasty borked installations in the future. (Right now Autopackage is a small blip on the radar, so its impact on system stability will be minimal).  I wonder who will get the blame for this... Will the Autopackage project suck up and say, "yeah, we made a boo boo" or will they just shove the blame towards the "evil distributions, who won't support us"?

The silly thing is that all the hubbub is about the perception that software is not available fast enough. If it takes two or four weeks to get Firefox version 1.0.x in the (backports) repository it is the end of the world. I still wonder why the world hasn't eviscerated Microsoft for not developing IE for three years plus.

***Tar files do need replacing.***

Do they? Shouldn't the OS know what to do with a source tar file and offer the user to do the "./configure && make && make install dance" automatically (on the CLI and in the GUI)? Preferably registering it with the systems standard package manager? No need for Windows-style, inaccesible binary blobs.

---

### Post by poofyhairguy on 2005-08-04
> **r_a_trip]
I've fiddled with it and it seems to do what it says it does. Yet Autopackage has the same shortcoming as any other package format on GNU/Linux. Packages still need to be made by people who know how to package them properly. End users are not automagically liberated from waiting for the software.[/QUOTE]

Very true!! Sometimes it might be better to leave the packaging to the packagers. 

> 
The silly thing is that all the hubbub is about the perception that software is not available fast enough. If it takes two or four weeks to get Firefox version 1.0.x in the (backports) repository it is the end of the world. I still wonder why the world hasn't eviscerated Microsoft for not developing IE for three years plus.

SOOOO true. When Ubuntu first came out, people were mad that no new apps came in between releases said:**
> 
Do they? Shouldn't the OS know what to do with a source tar file and offer the user to do the "./configure && make && make install dance" automatically (on the CLI and in the GUI)? Preferably registering it with the systems standard package manager? No need for Windows-style, inaccesible binary blobs.

Whatever can do that effectively replaces the tar file.

What I don't get is why is binary a big deal? Why can't we just make a nice GUI installer for tar files like XFCE has done? By compiling the app on the system you get rid of so many problems. Systems are powerful enough now to compile (especially smaller) apps like no problem. Whats the deal with binaries?

---

### Post by kanem on 2005-08-05
Aren't all these possible problems of libraries being overwritten or erased (which, I agree, are serious problems) precluded by just not letting Autopackage install system wide? Just don't give it a root password and it has to install into your local directory. No chance of overwriting anything important, no confusing Apt. The only thing that can become broken is the app it'self that you were trying to install.

BTW poofyhairyguy, I didn't think you were the one that needed to apologize in that other thread. Speaking of threads getting testy, theres some good argumentation on this over at the [Gentoo forums](http://forums.gentoo.org/viewtopic-t-315009-start-0-postdays-0-postorder-asc-highlight-autopackage.html)

---

### Post by subterrific on 2005-08-05
[QUOTE=poofyhairguy]Kinda. They expect libs to be in different places. The only way around that is to make special packages for each....doh....you saw where I was going.[/QUOTE]

LD_LIBRARY_PATH can easily be used to tell the dynamic loader where to find libraries. The bigger issues are ABI/API compatibility and library availability. You also completely ignore the possibility of static linking, which many vendors are already using to create universal binaries (Oracle, ID software, Philips, TeamSpeak, Rainbow Technologies just to name a few off the top of my head).

[QUOTE=poofyhairguy]Linux can't have exes. Windows can't have large repositories of free software to fit many needs.[/QUOTE]

Neither of these goals are out of reach. Nothing is technically preventing portage, rpm, or dpkg/apt from working on Windows. There is already lots of free software that has been ported to Windows. As far as Linux having "exes" :roll: lots of people who understand this topic better than you are working towards making software distribution more distributed on Linux, as it is on Windows and Mac.

Since you cannot claim to be an expert in software development, perhaps you should not speak in absolutes about topics you don't fully understand. You're spreading FUD, not helping. If you want to help, describe why Linux isn't there today (which you almost successfully did) and then describe what needs to happen before it gets there, and how they are being worked on, and the amazing progress being made. This is a very exciting time for Linux IMHO.

[list]
[*]major libraries like GTK+, GStreamer stabilizing
[*]freedesktop.org/LSB desktop API standard and adoption by distros
[*]developers coding to standard
[*]gcc ABI stabilizing (lets hope 4.0 is it)
[*]more developers using byte-code compiled languages like python
[*]autopackage maturing
[/list]

You could also describe the advantages of a centralized package management system over what exists in the Windows and Mac world. Mainly that you have an automated way of updating your entire system, not to mention automated notification of security patches. If you're running gaim, x-chat, apache, <insert closed source 3rd -party windows app here> on Windows there is no unified automated notification about security patch upgrades. Lots of Mac applications include libraries inside their bundles. For example, you might end up with 5 copies of libsqlite in 5 different app bundles. Lets say a security hole or data corruption bug is found in libsqlite. You're now depending on the providers of those 5 applications to release new versions and now you've got to *somehow* find out about these new versions and upgrade. On Ubuntu you get a notification that libsqlite needs to be upgraded, you click update, all apps using libsqlite are now fixed. Centralized package management also makes it a pleasure to deploy software for Linux. I don't have to worry about users having library xyz because every distro packages libxzy and when they package my app, libxyz will be installed automatically.

If you're going to be voicing your uninformed opinion, at least have the decency to label it prominently as such in your first post (perhaps in the topic?) instead of calling it "the answer". Being a moderator, I'd hope you'd know better. If you really want to learn about a topic, alienating yourself from the experts, by ignoring and denouncing their work just because you don't understand it, probably isn't the best idea (and I'm not just talking about Mike Hearn here, I'm also talking about the hundreds of developers working on LSB compliance, drafting new standards, freedesktop.org, package maintainers, etc). It is, however, a good way to bring out a bunch of trolls, which you've done a fantastic job of.

---

### Post by jwenting on 2005-08-05
The lack of compatibility (mainly binary but ever more often at source level as well) between distributions could well be a main reason slowing adoption of the platform.
Another of course is the religious zeal with which the main players in the large projects (kernel, X, Gnome and KDE for example) reject any good idea that ever came out of any corporation (and especially Microsoft, who have some pretty good ideas for making operating systems and applications work intuitively and have seemless integration).

Effectively Linux is now where the computer world as a whole was in the late 1970s and early 1980s.
Companies who wanted to have any market share at all of the whole market needed to release their product on a dozen or more platforms, with not just testing but customisation of the code required for each one.
As the market as a whole was small (just as the Linux market today, and the desktop Linux market especially, is small) that often wasn't economically feasible so many application developers choose to create only for a few platforms.

That all changed when Microsoft and IBM released the IBM PC with its DOS operating system.
The OS was capable of working on many different hardware combinations as long as it had an Intel CPU, and the hardware was capable of being configured in those many configurations to suit the need of many different target audiences.
Suddenly here was a platform that anyone could find something of value in and it took off like a rocket (completely surprising IBM who'd designed it like they had mainly to decrease manufacturing cost).
That architecture was so flexible it's still in use 20 years later (albeit with just about every part of it replaced with higher performance versions and alternatives as time went by).

While Linux doesn't have the problem of many different hardware architectures (there are of course some exceptions to that) it does have the problem of having many different non-compatible versions and that's hurting adoption.

While it may mean more "freedom" of choice, it also means a less lucrative market and one must remember that the computer industry has always been market driven.
If there's no money in it, it will end sooner or later.

---

### Post by Knome_fan on 2005-08-05
[QUOTE=jwenting]The lack of compatibility (mainly binary but ever more often at source level as well) between distributions could well be a main reason slowing adoption of the platform.
[/quote]
Lack of compatability on the source level? Even worse than on the binary level? Dude, what are you smoking?

[QUOTE=jwenting]
Another of course is the religious zeal with which the main players in the large projects (kernel, X, Gnome and KDE for example) reject any good idea that ever came out of any corporation (and especially Microsoft, who have some pretty good ideas for making operating systems and applications work intuitively and have seemless integration).
[/quote]
Yes, senseless insults and namecalling really speaks for the absence of religious zeal...
Impressive.
Btw., ever hear of freedesktop.org? Ever wondered why we now have things like udev and hal?

[QUOTE=jwenting]
Effectively Linux is now where the computer world as a whole was in the late 1970s and early 1980s.
Companies who wanted to have any market share at all of the whole market needed to release their product on a dozen or more platforms, with not just testing but customisation of the code required for each one.
As the market as a whole was small (just as the Linux market today, and the desktop Linux market especially, is small) that often wasn't economically feasible so many application developers choose to create only for a few platforms.
[/quote]
Excuse me?
What are you talking about?
This is simply untrue, to put it mildly.

[QUOTE=jwenting]
That all changed when Microsoft and IBM released the IBM PC with its DOS operating system.
The OS was capable of working on many different hardware combinations as long as it had an Intel CPU, and the hardware was capable of being configured in those many configurations to suit the need of many different target audiences.
Suddenly here was a platform that anyone could find something of value in and it took off like a rocket (completely surprising IBM who'd designed it like they had mainly to decrease manufacturing cost).
That architecture was so flexible it's still in use 20 years later (albeit with just about every part of it replaced with higher performance versions and alternatives as time went by).
[/quote]
And your point was?

[QUOTE=jwenting]
While Linux doesn't have the problem of many different hardware architectures (there are of course some exceptions to that) it does have the problem of having many different non-compatible versions and that's hurting adoption.
[/quote]
Is it? Who says so? 

[QUOTE=jwenting]
While it may mean more "freedom" of choice, it also means a less lucrative market and one must remember that the computer industry has always been market driven.
If there's no money in it, it will end sooner or later.[/QUOTE]
Yep, that's got to be the reason why Linux is the fastest growing OS on the market and why market researchers predict it will stay this way.

---

### Post by super on 2005-08-05
hmm,  :-k  this is a very interesting thread.

imo ubuntu/debian/redhat/mandrivia/gentoo and other distros with huge software repo and existing package managers and a relatively large number of developers do not **need** exes, **but** linux in general should probably have some sort of framework for smaller distros without a large amount of resources to easily install software.

autopackage is making large strides in doing this and according to the autopackage developers both in this thread and the one over at gentoo, they are in the process of fixing the problems that exist with autopackage. (of course, i take their words with a grain of salt)

as it stands i find that apt\synaptic works well for me, tho it could use some cosmetic improvements. (things like screenshots, links to homepage of the software developers, descriptions and icons for all available software, looking like [this!](http://www.rcdrummond.net/articles/images/2iris.png) )

i **do** use autopackage for some third party stand-alone applications like games, opera, acrobat etc.. and it works (tho this does not mean it's perfect)

for system libraries and internal apps its apt\synaptic all the way.

---

### Post by NoTiG on 2005-08-05
Well.. I see in the future that a graphical .deb installer will be in place, and when that happens, then installing a .deb will be just as easy as installing an autopackage. So to an ubuntu user, .deb would be just as good, except for the fact that the developer might find it inconvenient to package more than just one package (rpm, .deb) .

So my questions are :

How hard is it to make a .deb? If it was easy then it really shouldn't be an issue. Is the problem that you have to compile it from source when you make the package and developers don't have the time or just dont have the motive to do this? Is it possible for developers to compile once, and then package for RPM, and .deb with the same compiled binary? 

Is it possible that .deb might become the universal package? Is it possible to install .debs on an RPM distro? I was reading through the alien man page, and it looks like you can convert deb to rpm and vice versa. Perhaps there will be a graphical install tool for .deb, that also uses alien to install rpm? 

Is alien an ugly hack? What are the disadvantages to using it ?

Does installing .deb s play well with apt-get ? I mean... if you install a .deb, does it share the libraries with packages installed through synaptic/apt-get ? Yet when you apt-get upgrade, it doesnt maintain your .debs that were installed manually correct?

Is it possible to have a clientside respoitory, so for instance, i could have a line in my /etc/apt/sources.list and have it point to a file on my own system where I could then place a .deb i got manually into it ? Is that convenient? is it even necessary?

edit: Super read this: [http://udu.wiki.ubuntu.com/FindingPackages?highlight=%28DistroSpec%29](http://udu.wiki.ubuntu.com/FindingPackages?highlight=%28DistroSpec%29)
its high priority

Perhaps with a graphical .deb installation tool, that incorporates alien, and continued development of alien, autopackage will be unnecessary?

---

### Post by Knome_fan on 2005-08-05
@NoTiG:
> dpkg is the base of the Debian package management system. It was created by Ian Jackson in 1993. dpkg is similar to RPM, as it is used to install, remove, and provide information about .deb packages. In fact, RPM is based heavily on dpkg's idea of package dependencies, although simplified.

dpkg itself is a low level tool; additional higher level front ends are required to fetch packages from remote locations or resolve complex conflicts in the package dependencies. Debian provides APT for this purpose. 
[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

> deb is the extension of the Debian software package format and the most often used name for such binary packages.
...
The canonical program for handling these packages is dpkg, most commonly via apt.

deb packages can be converted into other packages using Alien.
 
[http://en.wikipedia.org/wiki/Deb_%28file_format%29](http://en.wikipedia.org/wiki/Deb_%28file_format%29)
Hope this clears things up a bit.

On other note:
You seem to think that just because something ends with .deb, it is compatible with every distro that uses debs. This is not the case. For example, try to install a deb from sid at the moment in hoary and you will most likely run into a problem.

---

### Post by Lambert on 2005-08-05
I'm a noob to linux. Add on programs and how they work in linux does baffle me. I've played with various distros from suse, to slackware, to a deb system. I'm working on trying a gentoo base with their portage. What baffles me is I can't just find an app I want to use, I have to find it in the right format and make sure all dependencies are accurate. The best way seems to be stay in the distros stable repository. 

Interesting on all the variations between the distros.

This thread has been enlightening and I'm gaing knowledge on linux from it. Thanks for everyone who participated.

I will keep reading and going to other various sites on this such as autopackage but I'm curious on other projects outside of autopackage that have tried this? CAn anyone elaborate on projects that are active or that are inactive and either failed or just didn't have the resource to continue? I read and heard a little about conary ( [http://www.rpath.com/technology/conary.html](http://www.rpath.com/technology/conary.html)) which sounds similar to autopackge in it's overall goal.

Being an average desktop user migrating from Win, I see a gap here. And that is in the installation of add on apps. Work is being done and I'm sure there is much progress being accomplished daily but with the infrastucture of linux distros as a whole there seem to be large obstacles to overcome to simplify the installer and create a package system for all linux distros.

It would be nice to see something like snapfiles or tucows for linux where you don't worry about what distro you have installed, if you have linux, you go to that area, find the app you're looking for, download and install not worrying about what distro you have. You would just have Linux. Maybe that will never be the linux way though. I believe someone else said this earlier, if you want that then you can just pick windows.

---

### Post by NoTiG on 2005-08-05
[QUOTE=Knome_fan]@NoTiG:
 
[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

 
[http://en.wikipedia.org/wiki/Deb_%28file_format%29](http://en.wikipedia.org/wiki/Deb_%28file_format%29)
Hope this clears things up a bit.

[/QUOTE]

Yes, I knew all of that 

> 

On other note:
You seem to think that just because something ends with .deb, it is compatible with every distro that uses debs. This is not the case. For example, try to install a deb from sid at the moment in hoary and you will most likely run into a problem.

I was under the impression that this was more of a problem with RPM (that could be corrected with LSB produced rpm's), and that it was an ubnutu package which might not be compatible with debian rather than the other way around.

---

### Post by poofyhairguy on 2005-08-05
[QUOTE=subterrific]
If you're going to be voicing your uninformed opinion, at least have the decency to label it prominently as such in your first post (perhaps in the topic?) instead of calling it "the answer". Being a moderator, I'd hope you'd know better. If you really want to learn about a topic, alienating yourself from the experts, by ignoring and denouncing their work just because you don't understand it, probably isn't the best idea (and I'm not just talking about Mike Hearn here, I'm also talking about the hundreds of developers working on LSB compliance, drafting new standards, freedesktop.org, package maintainers, etc). It is, however, a good way to bring out a bunch of trolls, which you've done a fantastic job of.[/QUOTE]

Actually, I admitted in this thread I wasn't qualified. But yet this thread still has much of the answer, from people like yourself that are more qualified.

Someone once told me that the best way to get info out of the GNU community is to challenge them in stubborn ways. If I would have said "I have my kinda thought idea about why this maybe is like it is." you and many other people might never have posted in this thread. It wouldn't have been very insightful, it wouldn't have been a learning experiance as it has.

I've learned about neat things like powerful forms of linking, discovered the biggest benefit of package managers, and all kinds of other neat stuff.

I titled the thread:

"If you have ever wondered why Linux lacks something like an exe"

My point was to get some answers. I'm getting them, and many others are learning important facts as well. Humility might have been more polite, but taking a hard (and flawed) line on the issue was more effective.

You say "If you really want to learn about a topic, alienating yourself from the experts, by ignoring and denouncing their work just because you don't understand it, probably isn't the best idea." Maybe not. But when I did that this time the "experts" were jumping out of the woodwork to prove me wrong with more information that I can consume. Sounds like an efficient way to learn about it to me.

I must admit that I did try to learn about this more myself using Google, and using academic resources, and poking through what documentation I could find. Problem is, that at first I didn't know enough to learn anything. I didn't know enough at the time to even put the right keywords in a search engine. But I gathered the best information I could find, created the opposing position and increased my knowledge exponentially.

Thank you and everyone else that has posted in this thread.

---

### Post by poofyhairguy on 2005-08-05
[QUOTE=Lambert]
This thread has been enlightening and I'm gaing knowledge on linux from it. Thanks for everyone who participated.
[/QUOTE]

Me 2.

---

### Post by super on 2005-08-05
In actuality i would presume to say that for someone who is not used to installing or has never installed software in windows, apt/synaptic really is the easier way of installing software (more intuitive, less mouse clicks, less user involvement, etc..)

but those migrating from windows would miss the installers. and as has been mentioned it would be easier for developers to produce one package that would work on all distros.

i think if autopackage can eventually do all the things it is touted to do i think it would be an excellent tool.

@ NoTiG
> super read this: [http://udu.wiki.ubuntu.com/FindingP...28DistroSpec%29](http://udu.wiki.ubuntu.com/FindingP...28DistroSpec%29)
its high priority 
Thanks for the link, i had not heard about this. got some reading to do  :)

---

### Post by subterrific on 2005-08-05
[QUOTE=poofyhairguy]I must admit that I did try to learn about this more myself using Google, and using academic resources, and poking through what documentation I could find. Problem is, that at first I didn't know enough to learn anything. I didn't know enough at the time to even put the right keywords in a search engine. But I gathered the best information I could find, created the opposing position and increased my knowledge exponentially.[/QUOTE]

The best places I've found are mailing lists and irc. Don't ask questions, just read the archives or chat history. This is how most free software developers communicate with each other (some have blogs). You'll find their ideas for future development and discussions on a technical level.

My point about labeling your assessment as opinion was just that you're doing a diservice to people who might not take the time to read 7 pages into this thread. They might just read your comment and go away thinking Linux will never change and no one is even trying. That would be a shame.

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=subterrific]
My point about labeling your assessment as opinion was just that you're doing a diservice to people who might not take the time to read 7 pages into this thread. They might just read your comment and go away thinking Linux will never change and no one is even trying. That would be a shame.[/QUOTE]

I edited the first post. I made it clear its my opinion. And I made it clear that some people disagree.

---

### Post by Knome_fan on 2005-08-06
[QUOTE=poofyhairguy]
My point was to get some answers. I'm getting them, and many others are learning important facts as well. Humility might have been more polite, but taking a hard (and flawed) line on the issue was more effective.
[/QUOTE]

Poofy, really, that's quite silly. Reading this thread and the other one that got closed it's quite obvious that you simply didn't know all too much about what you were talking about, yet were convinced that you did. To try to weasel out of this now claiming that you just wanted to provoke people into giving you answers is just silly.

> There will never be a way to compile an app on your development box and package it so that each distro works perfectly with it. Can't happen. I'm not trying to be mean, I don't hate binary compatibility. Just stating the truth (which some people refuse to accept). 
[http://www.ubuntuforums.org/showpost.php?p=285655&postcount=178](http://www.ubuntuforums.org/showpost.php?p=285655&postcount=178)

Further, now declaring that it was only your opinion doesn't make it any better really, as a lot of things you said were simply factually incorrect. Facts, at least in my book, are not a matter of opinion.

Finally, in the process of telling everyone what you perceived to be the truth, you managed to get a discussion closed in which a lot of people were participating (that's a really bad thing if a moderator is responsible for derailing a thread, though I acknowledge you appologized) and what's far worse, you deeply insulted someone by putting down the software he puts a lot of work into:

> Autopackage is not the answer. Its a kludge. There is only a few installers that truely work across all Linuxs (XFCE , Nvidia's) and all of those compile the app or module needed on the users computer. If you are not a developer, either deal with it (I have) or buy Windows or buy a Mac. There isn't another option. 
[http://www.ubuntuforums.org/showpost.php?p=285685&postcount=180](http://www.ubuntuforums.org/showpost.php?p=285685&postcount=180)

Needless to say that your assessement of autopackage didn't spring from any deeper knowledge about the underlying problems or about the way autopackage works, as became really evident in further discussions, where you freely admitted that you didn't know anything about autopackage and the way it works.
Frankly, I don't think putting the work of other people down without even trying to educate yourself about this work before and then claiming you just wanted to provoke answers isn't the way we should interact with each other on this forum.

Finally, I hope you don't take this post the wrong way. As I already said, I enjoy your posts in general and I certainly enjoy discussing stuff with you, I just felt that in this instance it was better to voice my critizism than to simply get anry or not say anything.

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=Knome_fan]P To try to weasel out of this now claiming that you just wanted to provoke people into giving you answers is just silly.[/QUOTE]

Let me just get one thing clear- I am not trying to weasel out of what I said. I DID try my best to present a side, and I WAS doing it the entire time for the sake of knowledge, not to insult or to throw dirt in the faces of those that care.

I didn't know more than I claimed to know, to manipulate peoples answers. I didn't just ask questions to type more for fun. 

When someone puts forth their option, and asks tons of questions (many of my posts have been full of questions) they are hoping for answers. Simply stating an opinion or asking a question provokes a response in its mear nature. 

I must admit that I didn't handle myself very well in that other thread. I apologized for it. I felt bad about it. I'm also sorry if the title of the thread is misleading to some. I didn't see it that way, but if someone suggested a better title I might change it to it.

And sure, a few times I have been wrong. Really wrong. About factual stuff. Like every person is at one point in their lives. Doesn't dull my curiosity. Doesn't make what I've learned from this experiance any less valuable.

If you want to consider this a debate I lose. But I see it more as a dialoge, and in that case you only lose if you had nothing to say.

So we beat on, boats against the current, borne back ceaselessly into the past.

---

### Post by mhearn on 2005-08-06
Wow, there's a lot of discussion here about what autopackage does, and what it can or cannot do. Let's clear a few things up.

Firstly, poofy, sorry I flipped out at you. You mean well, and that's what counts. As others have said, perhaps in future you'd do better to present such editorials as opinion rather than fact, unless you know what you say is technically verifiable.

OK so firstly, **what does autopackage do if the library is too old**?

There are a few techniques to deal with this. Contrary to popular opinion, autopackage does **not** silently upgrade libraries! If your system does not meet the minimum requirements of the package you're installing, it will stop with a message like this:

> "The 'GTK+ User Interface Toolkit' is installed but is of the wrong version, and the right version could not be located. [IV 2.4 for @gtk.org/gtk]"

The last bit identifies what *interface* version of the library was requested, and is useful for developers to debug what went wrong. In future it's likely that autopackage will report anonymous statistics to a central statistics service so we can get a better idea of what libraries most frequently cause installs to fail.

Autopackage **can** install missing libraries if they aren't there and somebody has produced an autopackage of that library. Right now the internal depsolver is limited to installing other autopackages : in future, somebody may teach it how to use apt-get and similar tools on other distributions and it'll then be able to use the distributions repositories to install missing dependencies. 

A more likely approach is the desktop Linux platform, which is touched on briefly in the FAQ. Briefly, this means joining dependencies together into one "mega dependency" that can be trivially installed either by end users or by autopackage itself (teaching it to use apt once is far easier than teaching it to use it generically). Essentially the "platform" is a series of packages that are common dependencies of programs. Developers are encouraged to target only what's available in the platform and use weak linking if they want extra features. The platform would rev about once a year but preserve backwards compatibility.

Autopackage does not solve dependency hell. It was not designed to - as has been said before, autopackage is only one component of a wider plan. Other elements of that plan deal with dependency hell. If a program has ridiculous dependencies, it'll be hard to install, end of story. Developers who care about the number of users they have will ensure their software can run on older systems by **relaxing dependencies**.

A common technique to relax dependencies (ie reduce minimum system requirements) is "weak linking". This means the program loads up pieces of code at runtime instead of at startup, and if the code it asks for is missing it can do any arbitrary action. The default approach is that any functions a program use are "hard/strong linked" and that means the operating system will abort startup and print an error if the necessary library or function cannot be found.

The standard interface to do this on Linux is called "dlopen", and it's a standard C interface. The dlopen function returns a handle you can use with dlsym to get a pointer to the code if it exists, or NULL otherwise. You then have to cast the result to a function pointer to use it. If you don't know what that means, don't worry, it can be summed up quite simply: *it's a pain in the ass to use *.

Unsurprisingly, not many developers bother with dlopen/dlsym, instead preferring to take the much simpler route of compile time conditionals. Because it's simpler to disable a feature if it's missing at compile time rather than runtime, you can find that a binary won't install because it has a dependency on something but if you compile from source it magically works. This is one of the causes of the "Linux is not binary compatible" meme that's going around - this simple observation that binaries often have tighter dependencies than source code does.

In fact this isn't some fundamental law of the universe, it's simply because it's easier to switch off features at compile time rather than runtime. The solution is easy enough: make it trivial for developers to enable/disable features at runtime as well. If the *gtkspell* library is missing, the program should still start up and just run without spell checking instead of refusing to install.

This is what **relaytool** does. It makes it as easy to enable/disable features at runtime according to what you have installed as autoconf makes it to do the same at compile time. I wrote relaytool to solve this very problem and give developers the tools they needed to make autopackages install on more systems, so reaching more users.

For the technical types reading this thread, relaytool builds small assembly-language jump blocks with the same name as the target symbol in the real library (say, gtkspell). The linker binds the undefined symbols in the main program to these generated jump blocks that are linked into the binary. Relaytool also injects an ELF constructor function into the program that builds an indexed table of each function that is to be weak linked, and fills in the entry either with the address of the real function or NULL if it's missing. At runtime, any usage of the gtkspell functions will be routed via the relaytool generated jump blocks which look up the address in the table and pass control directly to the target function. We have to use assembly here to avoid disrupting the stack layout (the jump blocks operate entirely using the scratch registers). 
For variables, the constructor function rewires the internal ELF global offset table.

Relaytool also exports a couple of extra functions you can use to find out what the system has available at runtime. If a piece of code looks like:

```

#include <config.h>

...

#ifdef HAVE_GTKSPELL
    gtkspell_attach(....)
#endif

```

the developer changes it to look like this:

```

#include <config.h>

....

RELAYTOOL_GTKSPELL;

#ifdef HAVE_GTKSPELL
    if (libgtkspell_is_present) gtkspell_attach( .... )
#endif

```

Basically, relaytool works in the same way as regular dynamic linking, except because we control the process we can extend it to provide the features developers need. The upshot is that where traditionally you'd have had to rewrite all the code specifically to use dlopen, avoid the standard headers etc - make the code very ugly, in other words - you can use relaytool to make features optional in only a few minutes.

There is more documentation on how to use relaytool on our website.

Autopackage has built in support for this in its dependency checker, you can mark dependencies either as "required" which means the install will abort if the library is missing, or "recommended" which means autopackage will try and ensure it's available but if it's missing and can't be resolved, the install will continue. At the end you get a little list of things you could install to get extra functionality.

We also provide support for **static linking**, where the contents of a library is sucked into the main binary itself so it doesn't have to be on the system at runtime, and **bundle linking**, where an actual .so file is placed in a private directory relative to the main binary and it will override the systems copy. If you already have it on your system, you can delete the private copy and the systems copy will be used.

This allows developers to include rare, unstable or very new libraries with their application, further reducing their dependencies.

For the technical types, here are some extra details:
[list]
[*] The apbuild tool makes static linking far easier than it'd normally be. We pass in some extra options to GCC not many people know about that can reduce the overhead involved in static linking significantly: by default the GNU toolchain does not do full function-granularity dead code elimination, but only does it at the file level. By passing **-ffunction-sections -fdata-sections -Wl,--gc-sections** much more code can be dropped leading to smaller binaries and less memory usage.
[*] Bundle linking relies on the ELF ${ORIGIN} DT_RUNPATH feature. It's similar to using LD_LIBRARY_PATH except there is no need for wrapper scripts. All apbuild compiled binaries (ie most autopackages) use both lib/my-program and lib/autopackage as private directories. In the rare case that autopackage does need to override libraries, in future it'll be putting them in these private directories so they don't interfere with the main system.
[*] Static linking can actually increase performance in some cases.
[/list]

OK, what else?

Oh yes. **"Distros have different libs in different places so they are not binary compatible" - wrong**. Binaries identify the libraries they need via what's called a *soname*. This is basically the filename of the library minus some version data, for "libfoobar.so.1.2.3" the soname would be "libfoobar.so.1". When loading a library, the linker looks in a variety of directories controlled by the /etc/ld.so.conf configuration file, the LD_LIBRARY_PATH environment variable, and any DT_RPATH/DT_RUNPATH headers in the binary itself. As long as your distribution is set up correctly, it doesn't matter where the libraries are put as long as the linker can find them. If the linker can't find them, then no binaries will be able to load them, so it's not a binary portability issue.

Actually, this is a minor problem on Debian/Ubuntu because IIRC by default the linker does not look in /usr/local/lib, so any libraries you install from source won't be located unless you compile other binaries yourseolf and they are built using libtool. Complicated!

One last question - this post is too long already: **Will autopackage work easily on a five year old install of Linux?**

Quick answer: no
Long answer: no. Linux has a very fast release cycle, most distros release new versions every 6 months (instead of every 3-4 years like Windows) and each revision brings interesting new features developers want to use. MacOS X has the same problem - try installing a modern MacOS X app on anything less than 10.2 and you'll hit difficulties. This has the advantage that we can quickly catch up with Windows/MacOS functionality-wise (important because for non-commercial software we usually have less manpower than for the commercial equivalents) but unfortunately places users on a vicious upgrade treadmill. Currently there's no easy way to avoid that, except by encouraging developers to not instantly upgrade their dependencies when new libraries come out.

---

### Post by TravisNewman on 2005-08-06
thanks mhearn. That makes me feel more confident in autopackage. I already was pretty confident, but most of my questions have been answered. The only problem I see now is developers not going along with your requests on how to incorporate their dependencies.

---

### Post by mhearn on 2005-08-06
[QUOTE=panickedthumb]thanks mhearn. That makes me feel more confident in autopackage. I already was pretty confident, but most of my questions have been answered. The only problem I see now is developers not going along with your requests on how to incorporate their dependencies.[/QUOTE]

Yes. We can lead people to water but can't make them drink, as it were. If a developer ignores our advice or doesn't use our tools, he can make an autopackage that is very hard to install. Such is life. If you can't get an app installed, try finding an alternative that's easier to use - that's the free market at work.

---

### Post by poofyhairguy on 2005-08-06
Sorry again. I'll do better in the future to show that something is my opinion. I really like your project, and I felt really bad that I made you so mad. Your long post is more than I could have asked for, thanks for answering many of my questions.

[QUOTE=mhearn]
Actually, this is a minor problem on Debian/Ubuntu because IIRC by default the linker does not look in /usr/local/lib, so any libraries you install from source won't be located unless you compile other binaries yourseolf and they are built using libtool. Complicated!
[/QUOTE]

Smacks forehead!!

> 
Long answer: no. Linux has a very fast release cycle, most distros release new versions every 6 months (instead of every 3-4 years like Windows) and each revision brings interesting new features developers want to use. MacOS X has the same problem - try installing a modern MacOS X app on anything less than 10.2 and you'll hit difficulties. This has the advantage that we can quickly catch up with Windows/MacOS functionality-wise (important because for non-commercial software we usually have less manpower than for the commercial equivalents) but unfortunately places users on a vicious upgrade treadmill. Currently there's no easy way to avoid that, except by encouraging developers to not instantly upgrade their dependencies when new libraries come out.

I might be wrong, be isn't this one of the reasons things like apt-get were invented in the first place? Is the modern package manager the only elegant solution to deal with constant upgrading? What package manager will autopackage support first?

---

### Post by Knome_fan on 2005-08-07
Just wanted to thank mhearn for the writeup.
The more I read about autopackage, the more interesting it starts to look.

---

### Post by mhearn on 2005-08-07
[QUOTE=poofyhairguy] I might be wrong, be isn't this one of the reasons things like apt-get were invented in the first place? Is the modern package manager the only elegant solution to deal with constant upgrading? What package manager will autopackage support first?[/QUOTE]

Well, package managers were invented because there was no concerted organisation or effort around the userland Linux OS in the very early days. Package managers evolved to cope with unorganized complexity by providing some safeties - they didn't solve the underlying complexity but attacked the symptoms (remove one package, ten others broke, add one package, have to find 10 more etc).

The approach we're advocating is to solve the underlying complexity by having a managed platform. It wasn't until the formation of KDE and GNOME that serious desktop platforms emerged. GNOME, KDE and the LSB - these are all desktop platforms, but unfortunately none are tuned to the exact purpose of reducing dependency hell. That's why we keep saying we need a new desktop platform.

In general, MacOS X users can upgrade their OS just fine with no package manager. They can do this because MacOS X is a (relatively) stable and large desktop platform and dependencies are bundled in with apps. That's not the only way to handle packages, but it definitely works.

On most Linux distros today you still need tools like apt-get to do upgrades because whilst upstream projects like GNOME, KDE and the kernel often care about backwards compatibility the distribution developers themselves usually do not, so libraries come and go depending on whether the apps they ship in the base set need them or not.

A classic example of this is Kubuntu, which does not install GTK+ or libglade, libraries that are guaranteed to be present on practically every other distro.

---

### Post by lithorus on 2005-08-09
Thanks to mhearn for clearing out a few things.

But just a few more questions.

You mention that autopackage could use apt-get for installing dependencies(should be easy enough with apt-file). Is there any timeline for such things?

Will there be a .deb package of autopackage anytime soon? (there's already an .rpm).

---

### Post by mhearn on 2005-08-10
[QUOTE=lithorus] You mention that autopackage could use apt-get for installing dependencies(should be easy enough with apt-file). Is there any timeline for such things? [/QUOTE]

Actually, autopackage doesn't use file dependencies (although it could be adapted to do so in future). 

There is no timeline for this feature. If somebody motivated enough writes a good patch we'll accept it. Until then we're more likely to spend our time on the desktop platform - this is the only way to be sufficiently robust and reliable for non-technical end users.

> Will there be a .deb package of autopackage anytime soon? (there's already an .rpm).

If somebody makes one then yes. There's no fundamental reason why there's an RPM and not a .deb, it's just that somebody contributed an RPM specfile. I don't know anybody who is intending to make a .deb anytime soon though.

---

### Post by jobezone on 2005-08-19
[QUOTE=poofyhairguy]Hell....I wish dpkg worked with aptitiude. It sucks when you install deb pacakges by hand that dependancies aren't resolved.[/QUOTE]

Perhaps this is late in the discussion, but I noticed this thing the other day.

I downloaded Gxmame's .DEB the other day from its website, as the one in Debian unstable was a few versions behind.

When I went to install it using ```
dpkg -i gxmame-blah.deb
```, it did the expected thing, complained about dependencies :)
Before I went to take care of installing them using apt-get (actually, I use aptitude), I went ahead and commanded aptitude to install some other package. To my amazement, a few extra packages were going to be installed as well: gxmame (version I got) and its dependencies (from Debian's repositories).

Later I found that, this automatic solving of depencies of individual .DEB packages we are trying to install, can simply be done by first trying to install the package with dpkg, like:```
dpkg -i <package.deb>
``` and then tell apt-get to **f**ix it, like: ```
apt-get -f install
```
.
Although I'm using Debian now, I'm really looking forward to see the gnome-install app in Breezy, and how it works, makes it easier for users.

---

### Post by poofyhairguy on 2005-08-19
[QUOTE=jobezone]Perhaps this is late in the discussion, but I noticed this thing the other day.

I downloaded Gxmame's .DEB the other day from its website, as the one in Debian unstable was a few versions behind.

When I went to install it using ```
dpkg -i gxmame-blah.deb
```, it did the expected thing, complained about dependencies :)
Before I went to take care of installing them using apt-get (actually, I use aptitude), I went ahead and commanded aptitude to install some other package. To my amazement, a few extra packages were going to be installed as well: gxmame (version I got) and its dependencies (from Debian's repositories).

Later I found that, this automatic solving of depencies of individual .DEB packages we are trying to install, can simply be done by first trying to install the package with dpkg, like:```
dpkg -i <package.deb>
``` and then tell apt-get to **f**ix it, like: ```
apt-get -f install
```
.
Although I'm using Debian now, I'm really looking forward to see the gnome-install app in Breezy, and how it works, makes it easier for users.[/QUOTE]


Sounds like a good wiki page to me!

---

### Post by jobezone on 2005-08-20
[QUOTE=poofyhairguy]Sounds like a good wiki page to me![/QUOTE]
 Sorry, but what do you mean? Making a wiki page about "apt-get -f install" or about gnome-app-install ?

---

### Post by poofyhairguy on 2005-08-20
[QUOTE=jobezone]Sorry, but what do you mean? Making a wiki page about "apt-get -f install" or about gnome-app-install ?[/QUOTE]

"How to Download Packages From the Internet and Resolve Dependacnies Automatically."

---

### Post by jobezone on 2005-08-21
commented on the wrong thread..

---

### Post by jonathanb on 2005-08-30
This thread started off with the following sentences :

"If you have ever wondered why Linux lacks something like an exe
This often comes up in the Linux community: "why can't they (as in developers) find a way to make files that can install programs on all versions of Linux?"

Window converts especially wonder "why do I have to mess with package managers and tar files? Why can't Linux have an exe?""

before it lost me totally as I am pretty new to Linux  :???: .

I also used to wonder this until I stopped thinking in terms of windows, linux, unix and mac and started thinking in terms of operating systems. Not all windows packages will work on all win versions and you need to check that you get a version of the software that will run on your version of win just as not all linux apps will work on all linux dists. If you think in terms of os's then it is easy to understand.

I run ubuntu so I need an accounting package for Ubuntu or I run Red Hat so I need an accounting package for Red Hat or I run windows so I need an accounting package for windows. (ok you also have to check the versions for them all just to complicate things)
The fact that the package might run on diffferent types of OS's is just a bonus then.

---

### Post by Lord Illidan on 2005-08-30
I haven't read all the thread but here are my 2 cents. Sorry if I repeated what someone else said..

Back in the days when I used Fedora Core 1, I remember being totally stumped about how to install a program. 

Ok, it is easy to say to someone, "./configure; make; make install", but when you have just started Linux, after a lifetime using Windows, where installing an app is as easy as clicking "Setup.exe", one starts getting extremely frustrated. 
Then, when I got used to doing it, I always got configure errors. It always wanted a specific library which I hadn't got. So I used to trawl the internet even more, trying to install a dependency which led to another dependency, and so on..

Then I got around to installing .rpms... 
So... App A needs Dep. X which needs Dep. Y, which needs Dep. Z, but Dep. Z can't be found anywhere. Or it tells you to include something in the $PATH...

Ubuntu's synaptic is a breath of fresh air. However, not everything is included, (no fault to the hardworking volunteers), and there some people may get frustrated, especially new users. Also, apt-get can be tricky to use, and it often gives cryptic messages, for example.. The application could not be found but was referenced by another application. Gibberish to me, especially when it installs quite well with Synaptic.

I have to say that a common .exe like format for Linux would be extremely welcome, and if autopackage can do it, I say go ahead!

---

### Post by weasel fierce on 2005-08-30
I havent had any dependency issues with Ubuntu..

---

### Post by earobinson on 2005-08-30
mhearn and the rest of the autopakage team keep up the good work. Im sure your goal is possiable and as autopakage becomes bigger and bigger distros will probaly want to help out more (the soultion may require some evoultion on the distro side also) but change is good and and an autopakage world would be great and is very important to the success of linux.

---

### Post by neighborlee on 2005-08-30
[QUOTE=earobinson]mhearn and the rest of the autopakage team keep up the good work. Im sure your goal is possiable and as autopakage becomes bigger and bigger distros will probaly want to help out more (the soultion may require some evoultion on the distro side also) but change is good and and an autopakage world would be great and is very important to the success of linux.[/QUOTE]


definitely..we can have as many distros as they come out but as long as something installs as easily on one as the other, then we're set and can  expect big things from outside sources, which means M$ monopoly is toast as long as of course things like useability are maintained ;-)

The  autopackage uses each systems  native package manager to deal with things, but I really like idea of a browser installable ( try first) system , which as I understand it  is a possible goal as things mature ?

cheers
nl

---

### Post by DancingSun on 2005-08-30
You know, it's ironic (moronic, even) that the open source movement into the commercial sector touts that open source software are open and standards compliant, while Linux distros don't want to comply to a standard for such a fundamental and important part of an OS.  If all binary Linux distros use ONE package management system and have some standard build configuration for building software, it would save so many user's hair pulling, head banging, and word abusing.  And developers will probably have a much easier time convincing the managment to port games, software, all the cool stuff to Linux as well.

While apt with dpkg is good, I think a better system would be something similar to [RubyGems](http://docs.rubygems.org/).  Linux distros *really* need to collaborate on this.

But before this kind of collaboration can get through the politics, ignorance, and arrogance to come to fruition, autopackage has my support, as they are at least doing something about the problem.  It's not a solution that can solved the root cause of the problem, but so is taking pain relievers when you are having a cold.  If it makes it less painful for me to get the latest software, hey, I'm all for it.

---

### Post by Brunellus on 2005-08-30
[QUOTE=DancingSun]You know, it's ironic (moronic, even) that the open source movement into the commercial sector touts that open source software are open and standards compliant, while Linux distros don't want to comply to a standard for such a fundamental and important part of an OS.  If all binary Linux distros use ONE package management system and have some standard build configuration for building software, it would save so many user's hair pulling, head banging, and word abusing.  And developers will probably have a much easier time convincing the managment to port games, software, all the cool stuff to Linux as well.

While apt with dpkg is good, I think a better system would be something similar to [RubyGems](http://docs.rubygems.org/).  Linux distros *really* need to collaborate on this.

But before this kind of collaboration can get through the politics, ignorance, and arrogance to come to fruition, autopackage has my support, as they are at least doing something about the problem.  It's not a solution that can solved the root cause of the problem, but so is taking pain relievers when you are having a cold.  If it makes it less painful for me to get the latest software, hey, I'm all for it.[/QUOTE]
 the same hand that gives you standards compliance and openness also opens the door to autarky and bloody-mindedness.  

You can't have one without the other.

---

### Post by poofyhairguy on 2005-08-30
(this whole thing is my opinion)

> Linux distros *really* need to collaborate on this.

You have to answer one question first :Why? 

Your arguements why:


[QUOTE=DancingSun]If all binary Linux distros use ONE package management system and have some standard build configuration for building software, it would save so many user's hair pulling, head banging, and word abusing. [/QUOTE]

But would make life harder for developers. Who would maintain this repo for these pacakges? That matters way more than a tool. RPM and debs are nearly the same, the differences are what dependancies are needed, what's on the repo you connect to, where packages drop its files and expect the files to be. Who would controlt he repo? Linus? He can barely control just the kernel. A company like Redhat? Other companies would hate it an fork to make money, and non profits like Debian would fork to remove commercialness. A non-profit like Debian? The corporations would hate it (they would lose decision power) and resources would be hard to manage. 

The truth is.......Linux is just a kernel. The whole OS is NOT "Linux." Its GNU if anything. We are lucky there is only one kernel honestly. 

The OSes all look the same because they use the same software.....but in many ways they are different. There is no unity, no force to tie them together besides the kernel. And that is not enough.

>  And developers will probably have a much easier time convincing the managment to port games, software, all the cool stuff to Linux as well.

Many (if not most) Gnu developers couldn't give a rats about companies releasing closed source programs for their OS or closed drivers. This is the truth. If it wasn't the case, the kernel would be friendlier to closed drivers and the kernel releases would focus on backwards compatability. It might make a new user sad....but its the truth. They care about free software over popularity, since they do the work I can't blame them.

The license of GNU stuff (and BSD stuff) makes it easy to fork. So in Gnu land the landscape is covered with forks. Some important people might not agree, but I think that Ubuntu is a good fork of Debian. Forking helps Linux grow...if forking did not happen things like Ubuntu and Xorg could never come along and set the world on fire. Its a good thing, but it leads to fragmentation. 

I believe that autopacakge will grow to meet a certain need" a good way to install newer programs when you distro has not packaged them yet. One it resolves dependancies it can work more than half the time...that will be great.

But if there will ever be ONE package format that all the major distro makers use for their own projects, I think it will be because one distro gets so popular that it forces everyone else to comply or risk being minimalized....like Redhat almost did.

---

### Post by DancingSun on 2005-08-30
[QUOTE=poofyhairguy]But would make life harder for developers. Who would maintain this repo for these pacakges?[/QUOTE]
You're jumping ahead of yourself here.  I did not explicitly state that the "package managment system" would be repository based.  It could, but it doesn't have to be.  Or it could be a system that allows a combination of repository based installation and local installations.  And besides I did suggest that you should have ONE repository.  No, not one repository but ONE system.  The word system here is quite vague, and purposely so.  It's the concept, not the implementation.  In short, you could call it an open standard or interface for package management.

> Many (if not most) Gnu developers couldn't give a rats about companies releasing closed source programs for their OS or closed drivers. This is the truth. If it wasn't the case, the kernel would be friendlier to closed drivers and the kernel releases would focus on backwards compatability. It might make a new user sad....but its the truth. They care about free software over popularity, since they do the work I can't blame them.
Err...right, and most users don't give a rats about open source programs as long as the programs and drivers work.  Sadly GNU/Linux will remain a toy for enthusiasts or a tool for professionals if this mentality rings true for the majority of the GNU/Linux developers.  I must agree that I believe GNU/Linux started out with this mentality, but with the recent wave of OSS movements into the commercial sector I see this mentality changing.  Companies like Canonical, are trying to build a business model around OSS, even if Ubuntu is to remain free, Cananical still need to make money to pay for the developers of Ubuntu, so that they can work full time to produce quality software...sad to some, but true.

If GNU/Linux cannot attract commercial developers to port or develop programs for GNU/Linux, "mainstream" is probably going to be much harder to acheive.  When commercial developers develop for GNU/Linux, it's likely they'll need support, which in Ubuntu's case, Canonical can provide with a small fee.  If there's many commercial developers needing Canonical's service, Canonical can then make more money and expand its Linux operation with better developers and marketing campaigns.  Things would blossom for Ubuntu and the community that has gathered around it.  This might conflict with some Open Source philosophies, but we live in the "real" world, and in reality, practicality usualy prevails.  Or else communism wouldn't have morphed into something that resembles more like dictatorship than an utopia.

---

### Post by poofyhairguy on 2005-08-30
[QUOTE=DancingSun]You're jumping ahead of yourself here.  I did not explicitly state that the "package managment system" would be repository based.  It could, but it doesn't have to be.  Or it could be a system that allows a combination of repository based installation and local installations.  And besides I did suggest that you should have ONE repository.  No, not one repository but ONE system.  The word system here is quite vague, and purposely so.  It's the concept, not the implementation.  In short, you could call it an open standard or interface for package management.[/QUOTE]

The problem is less the details, and more the fact that the major players all have different interests so cooperation is limited and forking is expected.

> 
Err...right, and most users don't give a rats about open source programs as long as the programs and drivers work.  Sadly GNU/Linux will remain a toy for enthusiasts or a tool for professionals if this mentality rings true for the majority of the GNU/Linux developers.  I must agree that I believe GNU/Linux started out with this mentality, but with the recent wave of OSS movements into the commercial sector I see this mentality changing.

Sure. You have Linspire, Professional SUSE, Redhat and its many "official" RPMs. Some in the community will work for this. Its in their interest. But not everyone will. And with people on so many different pages, its hard to make standards.

> 
  Companies like Canonical, are trying to build a business model around OSS, even if Ubuntu is to remain free, Cananical still need to make money to pay for the developers of Ubuntu, so that they can work full time to produce quality software...sad to some, but true.

And the Ubuntu model is to release free software. Its amazing what Ubuntu can do out of the box without a single closed thing.

> 
If GNU/Linux cannot attract commercial developers to port or develop programs for GNU/Linux, "mainstream" is probably going to be much harder to acheive.  

False. All it means is that Linux won't rule the desktop....which will probably be the case anyway (big chicken and egg situation on that one).but Linux will sneak into people's lives: through their cell phones, wireless routers, TiVos, car computers, etc. if they like it or not. Linux is mainstream today- everyone I know has a TiVo (cept me). It just might not be the major desktop OS. Oh well, its better at other things. 

> 
When commercial developers develop for GNU/Linux, it's likely they'll need support, which in Ubuntu's case, Canonical can provide with a small fee.  If there's many commercial developers needing Canonical's service, Canonical can then make more money and expand its Linux operation with better developers and marketing campaigns.  Things would blossom for Ubuntu and the community that has gathered around it.  This might conflict with some Open Source philosophies, but we live in the "real" world, and in reality, practicality usualy prevails.

None of that is against the Gnu philosophy. Richard Stallman does not mind if someone makes money off of Linux, sell support for GNU software. Hell...he doesn't care if you sell GNU software. As it is, the GNU system is the rawest form of capitalism you can encounter in the computer world- it encourages competition and commerce.

What is against the philosophy is playing to nice with closed drivers, find ways to illegal distribute closed media codecs, or encouraging software with a closed source code. If that is what separates Linux from success then one would think that BSD (with its less restrictions, its platform stability , and its compatibility with closed drivers) would be on top.....but currently Linux is bigger. For a reason.

---

### Post by woedend on 2005-08-31
im not a linux programmer, or a programmer at all so will not argue with anyone on technical points but pose an objective view.  What would, per se, the problem be with installing two or more versions of the same library.  That is to say, if a program needs a newer version of the one that's installed, rather than replace it, just add a .1 to the end and have the code reference that one(as it would cycle, if the base file wasnt correct, try .1 if it exists.  if it does not exist, create and use it. if it does and is not correct, try .2).   Or is that completely unrealistic?  Not being sarcastic, I really just don't know all that much about it.

---

### Post by DancingSun on 2005-08-31
[QUOTE=poofyhairguy]False. All it means is that Linux won't rule the desktop....which will probably be the case anyway (big chicken and egg situation on that one).but Linux will sneak into people's lives: through their cell phones, wireless routers, TiVos, car computers, etc. if they like it or not. Linux is mainstream today- everyone I know has a TiVo (cept me). It just might not be the major desktop OS. Oh well, its better at other things.[/QUOTE]
True, False, or Both?  You probably noticed my quotes around "mainstream".  Although, I was aiming for more of a high profile notion of mainstream, but even with your definition of "mainstream" it still means that commercial developers *have* to develop for the GNU/Linux platform.  Which means, you really meant "True".  BTW, I don't own a TiVO, too, so you're not alone. :neutral: 

> As it is, the GNU system is the rawest form of capitalism you can encounter in the computer world- it encourages competition and commerce.
Not quite.  Secrecy can be a huge part of commercial success.  Which is why patents are invented in the first place.  In essense, the longer you can preserve your relative advantage over the competition, the better it is for your business and the more money you can make.  Monetary incentive, now that's raw capitalism.  The GNU system is too open, too transparent.  What the GNU system is good at promoting is, from my understanding, academic competition, not commercial competition.  The open nature of the GNU system prohibits anyone from locking into a superior technology long enough to reap a significant amout of profits from it.  However, it does work wonders for someone interested in how things work.  A person extremely interested in the technology behind a piece of software can freely and legally look at how it is implemented.  He/she can even re-implement it with a better approach.  Here, you have academic competition.

But I think the biggest limiting factor is that many OSS software are free (monetarily).  Like you pointed out, they don't have to be, but a lot of them sure are.  If Ubuntu wasn't free, I probably would actually go *buy* a copy of Linspire.  But no, I'm too cheap.  :-P  That's discouraging for Linspire, and hurts their ability to compete, but that's what I decided, and I'm part of the market force.  And lets not forget, the various incompatible package management systems sure doesn't help Linspire compete with the MS camp here.

I think GNU/Linux's technical achievements are proven by it's academic and professional use.  And it would be such a waste to have GNU/Linux limiting itself to only specialized commercial applications.  From an ideal, technical, and academic point of view, I think the Open Source development model is the best way to develop software.  It's about technical achievement, about having fun, about experimentation, about collaboration, about many many things BUT money.  

Ironically, as I see it now, the Open Source movement is popular precisely because it involves money.  Perhaps an open source vendor doesn't make as much money as the proprietary vendor, but the buyer of the software certainly is benefiting from the cheaper cost.  The in-house IT departments certainly are benefiting from being able to read and change the source code to tailor to their corporate needs.  So in the end, I think if the Open Source movement is to increase its foothold, it has to play nice with key proprietary technologies.

Now, while you say BSD plays nice with proprietary drivers, that's certainly news to me, since I usually don't read much news about BSD at all.  Perhaps that has something to due with BSD's relatively quiet existence in the consumer arena.  Much of Linux's success is due to the "buzz" that's being generated around the various consumer desktop distributions.  While there have been many attempts to get Linux on the desktop, I've never heard of any attempts of BSD getting onto the desktop scene.  Whatever proprietary drivers BSD supports probably aren't the ones that I'll be using.

Now, I'd very much like to see Ubuntu and other Linux distributions succeed in gaining a large market share of the consumer OS market.  That's because I really like some of the designs of the operating system.  However, it's really a thorn in the side when I realize that my proprietary hardware doesn't work correctly on Ubuntu.  If we have open source hardware, then we wouldn't have this clash of philosphies, right? Then maybe we won't have this kind of problem! But hey...that doesn't sound right.  Yes, you *cannot* have open source hardware on a large scale, the thing not only costs money to develop, but it also costs money to build and distribute!  

I think the GNU/Linux developers should really focus on being pragmatic rather than idealistic.  If working with proprietary drivers is too extreme, then maybe they should try working *with* themselves.  A standard package management system  will go a long way to helping Linux adoption in the consumer OS arena, and in my opinion, make building businesses, or making a living, depending on your goal, around GNU/Linux a lot easier; all the while keeping a healthy selection of Linux distros.

Even just for convenience's sake, I'd love to not having to wait for a package to be included into Ubuntu's repositories before I can install it (while I technically could install it manually, I certainly don't want to go through the hassle).  If I were to develop for GNU/Linux, I would love to not deal with all these varying package managers that are not compatible with each other.  And I think this is already evident enough, as most developers don't release packages for ALL package managers.  From where I'm looking at, I definitely see this as a problem that the distro developers need to solve.

---

### Post by DancingSun on 2005-08-31
[QUOTE=woedend]im not a linux programmer, or a programmer at all so will not argue with anyone on technical points but pose an objective view.  What would, per se, the problem be with installing two or more versions of the same library.  That is to say, if a program needs a newer version of the one that's installed, rather than replace it, just add a .1 to the end and have the code reference that one(as it would cycle, if the base file wasnt correct, try .1 if it exists.  if it does not exist, create and use it. if it does and is not correct, try .2).   Or is that completely unrealistic?  Not being sarcastic, I really just don't know all that much about it.[/QUOTE]

It's not unrealistic, in fact a package management system like that already exists!  Haha, now that I got you excited, too bad it's not for any of the Linux distros (that I know of).  The package management system I'm talking about is called [RubyGems](http://http://docs.rubygems.org/) and is the package manager for the Ruby platform.  RubyGems not only manages install/uninstall/upgrade, it also allows different versions of the same package to be installed.  However, for this to work correctly, the software requiring the library must indicate compatible versions of that library, or else it'll just use the newest one and might cause some problems.

---

### Post by rolfotto on 2005-08-31
[QUOTE=DancingSun]Not quite.  Secrecy can be a huge part of commercial success.  Which is why patents are invented in the first place.  In essense, the longer you can preserve your relative advantage over the competition, the better it is for your business and the more money you can make.[/QUOTE]

Actually Patents are quite the opposite - open.  Because they have to be, otherwise others can't know if they are infringed if patents were closed.

Though the relative advantage part is true, patents are temporary monopolies on an invention all to encourage initial invenstment/innovation  in areas that had slim chance of reward.

These days though, seeing what gets patents...... it seems the system is broken.

---

### Post by poofyhairguy on 2005-08-31
> **DancingSun]
Not quite.  Secrecy can be a huge part of commercial success.  Which is why patents are invented in the first place.  In essense, the longer you can preserve your relative advantage over the competition, the better it is for your business and the more money you can make.  Monetary incentive, now that's raw capitalism.  The GNU system is too open, too transparent.[/QUOTE]

Allowing for perfect competition, a nice thing in a free market.

> 
  What the GNU system is good at promoting is, from my understanding, academic competition, not commercial competition.  The open nature of the GNU system prohibits anyone from locking into a superior technology long enough to reap a significant amout of profits from it.

You need to put the word "software" in there somewhere. The GNU is great for hardware. You "lock" you competitors out by having the underneith stuff be great and patented, and lower development costs by using Linux (and not have to start from scratch with an OS). All you have to do is give the source code away, and that can only run on your hardware (so bonus if someone buys your product to get the source code to work). Now software is a different story.

> However, it does work wonders for someone interested in how things work.  A person extremely interested in the technology behind a piece of software can freely and legally look at how it is implemented.  He/she can even re-implement it with a better approach.  Here, you have academic competition.

And if you sell it (Linspire, Mandriva, SUSE, Xandros, Slackware, Red Hat, etc.) you get economic competition.

> 
But I think the biggest limiting factor is that many OSS software are free (monetarily).  Like you pointed out, they don't have to be, but a lot of them sure are.  If Ubuntu wasn't free, I probably would actually go *buy* a copy of Linspire.  But no, I'm too cheap.  :-P  

But some people think that "anything that costs nothing must be useless." Thats why a Linspire exists. That and legal codecs and click and run.

> 
That's discouraging for Linspire, and hurts their ability to compete, but that's what I decided, and I'm part of the market force. 

Linspire stays afloat, as they are shipped on many PCs by default. And you (or me) don't matter. If you are willing to pay nothing, then you are small fish. Linspire wants a school district or a company to switch to them, not a single user.

> 
 And lets not forget, the various incompatible package management systems sure doesn't help Linspire compete with the MS camp here.

Actually they do help Linxpire. Linspire's biggest profit comes from selling click-and-run, their way of installing software. Easiest in Linuxland (easier than Windows, maybe easiest in the world), but you have to pay every month.  So another compatible binary format might hurt this revenue. They give their OS away for free sometimes. Its just blades to them, they want to sell razors (click-and run).

> 
I think GNU/Linux's technical achievements are proven by it's academic and professional use.  And it would be such a waste to have GNU/Linux limiting itself to only specialized commercial applications.  From an ideal, technical, and academic point of view, I think the Open Source development model is the best way to develop software.  It's about technical achievement, about having fun, about experimentation, about collaboration, about many many things BUT money.

Tell that to Google, Pixar, Amazon, DaimlerChrysler, AutoZone, IBM, and many others if Linux is not always about saving money or other resources (that can be traded for money). They love their Linux.

> 
Ironically, as I see it now, the Open Source movement is popular precisely because it involves money.  Perhaps an open source vendor doesn't make as much money as the proprietary vendor, but the buyer of the software certainly is benefiting from the cheaper cost.  The in-house IT departments certainly are benefiting from being able to read and change the source code to tailor to their corporate needs.  So in the end, I think if the Open Source movement is to increase its foothold, it has to play nice with key proprietary technologies.

Maybe. I mean, I can see your point. Developers can too. Thats why Linux can read NTFS, or open Word docs (despite NO MS help). But....not everyone in the community agrees. No one can make them agree. So, some of the Gnu world might still buck "the man." Better than them not doing anything.

> 
Now, while you say BSD plays nice with proprietary drivers, that's certainly news to me, since I usually don't read much news about BSD at all.  Perhaps that has something to due with BSD's relatively quiet existence in the consumer arena.  Much of Linux's success is due to the "buzz" that's being generated around the various consumer desktop distributions.  While there have been many attempts to get Linux on the desktop, I've never heard of any attempts of BSD getting onto the desktop scene.  Whatever proprietary drivers BSD supports probably aren't the ones that I'll be using.

BSD has a very loose license...so it can be used for whatever. And there is a new wave of desktop bsds:

[http://www.pcbsd.org/](http://www.pcbsd.org/)

> 
Now, I'd very much like to see Ubuntu and other Linux distributions succeed in gaining a large market share of the consumer OS market.  That's because I really like some of the designs of the operating system.  However, it's really a thorn in the side when I realize that my proprietary hardware doesn't work correctly on Ubuntu.

Me to. My answer? I sell the stuff or throw it away and replace it with Linux compatible stuff. I call it "true cost of Linux." I like Linux better so it is worth it for me. If it is not worth it for others, well...thats their choice.

> 
  If we have open source hardware, then we wouldn't have this clash of philosphies, right? Then maybe we won't have this kind of problem! But hey...that doesn't sound right.  Yes, you *cannot* have open source hardware on a large scale, the thing not only costs money to develop, but it also costs money to build and distribute!  

Open hardware does exist. Many Serial ATA cards, wireless cards, vga cards, ethernet cards, etc. have their specs released. Open hardware does not mean free hardware. Computer hardware competes on price point. By giving the design documents away (like Realtek or ATI did) you allow someone else to make your drivers....much cheaper.

> 
I think the GNU/Linux developers should really focus on being pragmatic rather than idealistic.  

Some are. Some aren't. Can't make them all be. That takes away the free. Linus is a very pratical man.

> 
If working with proprietary drivers is too extreme, then maybe they should try working *with* themselves.  A standard package management system  will go a long way to helping Linux adoption in the consumer OS arena, and in my opinion, make building businesses, or making a living, depending on your goal, around GNU/Linux a lot easier said:**
> 

Sure. I'll admit it would. Heck, I'll say it would. If we had magical binary compatibility then many things would be easier. Its true. 

The problem is the implementation. This thread and the one before it and the autopackage website lay out the problems. They are many. I think most are doable (the stuff that doesn't require standards) in the near future and that autopackage will be a success. But I don't think it will ever be 100%. The only way I see standards is if one distro finally "wins" for a long while, which might never happen.

I like Utopia too. The Gnu community is not this. Its divided. Package managers were created to bridge those gaps. And they do. Sure we don't know what each package means, but the software works. The chaos is tamed. Is there other, better ways for other better systems? Sure. Is there a better way to bring together a community that can not be united, for almost any reason? I don't think so. I could be very wrong. Would be happy to be wrong.

[QUOTE]
Even just for convenience's sake, I'd love to not having to wait for a package to be included into Ubuntu's repositories before I can install it (while I technically could install it manually, I certainly don't want to go through the hassle).

Well. here is the deal. Those deb pacakges are just more than gift wrapped tar files. The packagers also fix bugs, work the thing into the dependancy system and get it to work 99% of the time. That takes time. That takes work. You do it yourself with a tar file. Even autopackage must be good packages. Those take time. 

The problem is that nothing is easier than throwing out a tar file (well...maybe "just compile from CVS" is easier). As it is there is no quick way just to make a package. Hopefully distros will make it easier to make packages for each of their OSes, but it even harder to make a package that will work on all.

 Its a bunch of technical problems. Pilled on each other. And you don't get to change the rules. The licences can not change. The "not invented here" syndrome will not go away. You can't change the community. You just have to find some magic way to make it all work. Mike is trying to do that. I wish him luck. I hope he can. From what he told me, its possible....but hard.

If you really need new packages as they are released, use Gentoo. As if to prove my theory, Ebuilds are the easiest Linux "package" to make, and Gentoo always has the newest stuff. 

[QUOTE]
  If I were to develop for GNU/Linux, I would love to not deal with all these varying package managers that are not compatible with each other.  And I think this is already evident enough, as most developers don't release packages for ALL package managers.  From where I'm looking at, I definitely see this as a problem that the distro developers need to solve.

how can the distro developers solve it? How can one (or even a group) force the others to play along? How can they tame the chaos? Not everyone will agree. People have tried to make standards and so far have failed (in my opinion). What can developers do? 

Only one way I can see developers doing something about that. Each distro team can just try to make the best Linux they can....one soo much better than the rest it is "THE" desktop Linux...and then everyone will have to copy them. So many are trying for something like that. What else can they do?

---

### Post by doclivingston on 2005-08-31
[QUOTE=woedend]im not a linux programmer, or a programmer at all so will not argue with anyone on technical points but pose an objective view.  What would, per se, the problem be with installing two or more versions of the same library.  That is to say, if a program needs a newer version of the one that's installed, rather than replace it, just add a .1 to the end and have the code reference that one(as it would cycle, if the base file wasnt correct, try .1 if it exists.  if it does not exist, create and use it. if it does and is not correct, try .2).   Or is that completely unrealistic?  Not being sarcastic, I really just don't know all that much about it.[/QUOTE]

Shared libraries already do this - they have a three part version number, which indicates which versions are compatible with each other. The real problem is with everything else: data files, utilities and the like.

---

### Post by DancingSun on 2005-08-31
[QUOTE=rolfotto]Actually Patents are quite the opposite - open.  Because they have to be, otherwise others can't know if they are infringed if patents were closed.

Though the relative advantage part is true, patents are temporary monopolies on an invention all to encourage initial invenstment/innovation  in areas that had slim chance of reward.

These days though, seeing what gets patents...... it seems the system is broken.[/QUOTE]
Sorry, I wasn't clear enough on this.  I didn't mean to associate patent with secrecy, but with the relative advantage that it can give, similar to business secrets.

---

### Post by DancingSun on 2005-08-31
[QUOTE=poofyhairguy]Only one way I can see developers doing something about that. Each distro team can just try to make the best Linux they can....one soo much better than the rest it is "THE" desktop Linux...and then everyone will have to copy them. So many are trying for something like that. What else can they do?[/QUOTE]
What else? There are many solutions to one problem.  If there's "open" hardware, the conform to standards, why can't there be Linux that conform to standards? There's already a bunch of open source software that conform to standards, why not Linux?  Why not throw away that ego, and collaborate.  Don't know how? Vote on it!  If you try to forever satisfy every single person in the group, the group will remain fragmented.  I'm not trying to suggest that it's a easy undertaking, but with determination, it can happen.  What changes the community?  I believe it starts with individuals.

Not having standards works against economies of scale, and while can spawn many branches, it impedes the kind of progress that might have happened if all resources are funneled into one stream.  While Linspire's click 'n run is great, it does not solve the problem that developers don't release software in the click 'n run format (well, as far as I know, not in a wide scale at least).  I'm sure many user buy into it, then to find out that some software that they want was not in the click 'n run repository and they'd have to wait.

BTW, perfect competition is a killer for the economy.  Why?  Because you will not be able to make ANY profit.  If you could copy what your competitors are doing, then the market will lack product differentiation, in the end you can not charge more than what your competitors charge.  And under free market conditions (no trust, price fixing), a price war is likely to start until the profit margin reaches zero.  You could probably still keep the business running, but you will not be able to take a profit.   It's good for consumers in the short run, but this also stifles the economy and will come around and hit the consumers eventually.  It is the imperfect competition that allows room for profit taking, and a healthy economy.

---

### Post by doclivingston on 2005-08-31
> **DancingSun]Not quite.  Secrecy can be a huge part of commercial success.  Which is why patents are invented in the first place.  In essense, the longer you can preserve your relative advantage over the competition, the better it is for your business and the more money you can make.  Monetary incentive, now that's raw capitalism.[/quote]

Secrecy is important for a product-based economy. Making software freely available changes the economy from being product-based to being service-based - because companies no longer sell the software, they sell training and support.

[QUOTE=DancingSun]The GNU system is too open, too transparent.  What the GNU system is good at promoting is, from my understanding, academic competition, not commercial competition.  The open nature of the GNU system prohibits anyone from locking into a superior technology long enough to reap a significant amout of profits from it.  However, it does work wonders for someone interested in how things work.  A person extremely interested in the technology behind a piece of software can freely and legally look at how it is implemented.  He/she can even re-implement it with a better approach.  Here, you have academic competition.[/quote]

By not locking people into one technology, you are in fact encouraging the free market by removing artificial restrictions. There is still commercial competition, although it isn't the same as before.

[QUOTE=DancingSun]But I think the biggest limiting factor is that many OSS software are free (monetarily).  Like you pointed out, they don't have to be, but a lot of them sure are.  If Ubuntu wasn't free, I probably would actually go *buy* a copy of Linspire.  But no, I'm too cheap.  :-P  That's discouraging for Linspire, and hurts their ability to compete, but that's what I decided, and I'm part of the market force.  And lets not forget, the various incompatible package management systems sure doesn't help Linspire compete with the MS camp here.[/quote]

Isn't hurting someones ability to compete, by being able to sell something cheaper than them (giving something away is just selling it for no money), one of the core ideas of the free market?

There is nothing stopping you from selling Free (libre) software, but someone can always sell it cheaper then you.


[QUOTE=DancingSun]Ironically, as I see it now, the Open Source movement is popular precisely because it involves money.  Perhaps an open source vendor doesn't make as much money as the proprietary vendor, but the buyer of the software certainly is benefiting from the cheaper cost.  The in-house IT departments certainly are benefiting from being able to read and change the source code to tailor to their corporate needs.  So in the end, I think if the Open Source movement is to increase its foothold, it has to play nice with key proprietary technologies.[/quote]


[QUOTE=DancingSun]I think the GNU/Linux developers should really focus on being pragmatic rather than idealistic.[/quote]

Developers all have different reasons for working on Open-Source Software, some get paid to do it, some want to improve the software they use, and it is the idealistic goals. Many developers are pragmatic about it, but not all are, and that isn't going to change.

[QUOTE=DancingSun]If working with proprietary drivers is too extreme, then maybe they should try working *with* themselves.  A standard package management system  will go a long way to helping Linux adoption in the consumer OS arena, and in my opinion, make building businesses, or making a living, depending on your goal, around GNU/Linux a lot easier said:**
> 

The reason for the different package management systems is that they have different goals, and priorities - some of which conflict with others. There isn't a standard installation system on WIndows either; some products use MSI, some use InstallShield, others come in zip files and so on.


[QUOTE=DancingSun]Even just for convenience's sake, I'd love to not having to wait for a package to be included into Ubuntu's repositories before I can install it (while I technically could install it manually, I certainly don't want to go through the hassle).  If I were to develop for GNU/Linux, I would love to not deal with all these varying package managers that are not compatible with each other.  And I think this is already evident enough, as most developers don't release packages for ALL package managers.  From where I'm looking at, I definitely see this as a problem that the distro developers need to solve.

Whatever happens, *someone* is going to have to package it (even if it is the product's developers).

As I pointed out above the reasons for having different (and incompatible) package management systems if that they have different goals. Take one of the differences between RPMs and DEBs: file dependencies - some people think these are vital, and some think they are one of the stupidest things about RPM. If you want to have one package system that everyone uses, you are going to have to appease everyones own goals - which may be impossible.


As an analogy consider main power, and the fact that it isn't the same in different countries. The US uses 110V 60hz with a certain plug shape, Australia uses 240V 50 with a different plug shape, other countries have other different systems. Sure this causes some problems for manufacturers of electrical and electronic good some problems - but they deal with it, because they know that there isn't going to be one standard that everyone agrees upon.

---

### Post by doclivingston on 2005-08-31
> **DancingSun]What else? There are many solutions to one problem.  If there's "open" hardware, the conform to standards, why can't there be Linux that conform to standards? There's already a bunch of open source software that conform to standards, why not Linux?  Why not throw away that ego, and collaborate.  Don't know how? Vote on it!  If you try to forever satisfy every single person in the group, the group will remain fragmented.  I'm not trying to suggest that it's a easy undertaking, but with determination, it can happen.  What changes the community?  I believe it starts with individuals.[/quote]

The best thing about standards, is that there are so many to choose from.

As you said, you can't satisfy every person in a group. What happens if you make a "standard" that satisfies 80% of the people in a group, but then the other 20% get together and make their own "standard"? You then have two standards which people don't agree on said:**
> BTW, perfect competition is a killer for the economy.  Why?  Because you will not be able to make ANY profit.  If you could copy what your competitors are doing, then the market will lack product differentiation, in the end you can not charge more than what your competitors charge.  And under free market conditions (no trust, price fixing), a price war is likely to start until the profit margin reaches zero.  You could probably still keep the business running, but you will not be able to take a profit.   It's good for consumers in the short run, but this also stifles the economy and will come around and hit the consumers eventually.  It is the imperfect competition that allows room for profit taking, and a healthy economy.

Which is your aim a) what is best for companies, b) what is best for consumers, c) what is best for developers, d) what is best for the "the ecomony" (all of those in both short-term and long-term versions)? All of those are different, and require different approaches.

Perfect competition and free-market conditions cause convergence to an equilibrium - whether that is a good equilibruim is something that you're not going to be able to tell until afterwards.


Of course, all this assumes that everyone involved has capitalistic (profit making) goals. Some people contribute because they find it interesting (academic interest) or because they want to give something to the world, or they are bored. All the other reasons cause this to be not entirely a economic issue, which makes it *much* more complicated.

(edited to fix a quoting issue)

---

### Post by poofyhairguy on 2005-08-31
[QUOTE=DancingSun] If you try to forever satisfy every single person in the group, the group will remain fragmented. [/QUOTE]

True. A jack of all trades does no one thing well. But in reality there is only one thing holding this together- a licence. Thats the big difference. Its not the idea, but its how it coexists in a world with law.

If you modify the licence to force unity, then the old code will not be under the new licence. People will fork and go on their merry way.

The cat is out of the bag. Linux has to legally try to satisfy every person if they want. Everyone gets a shot legally. 

Gnu is a meritocracy. Rank is determined by quality and dedication. A program or format or whatever in "Linux" only becomes the "only" one if it is super superior to all others. Thats not the case with distros now. It is the case for the kernel and Xorg (kinda).

 > 
While Linspire's click 'n run is great, it does not solve the problem that developers don't release software in the click 'n run format (well, as far as I know, not in a wide scale at least).  I'm sure many user buy into it, then to find out that some software that they want was not in the click 'n run repository and they'd have to wait.


Its like anything else for the average user then. Then new version is released when its on their OS. In Click-and-run. I don't like it either.

---

### Post by Buffalo Soldier on 2005-08-31
that's why we have open standards. I don't belief in 1 standard... one fix'em all solution.

That's why we have many different standards... and that should not pose much problem IF they are all open.

Variation is always good... even variation in species... it keeps from one virus wiping out us human.

---

### Post by DancingSun on 2005-08-31
I guess I should say "industry" standard.  If you have too many standards for the same purpose, it's the same as having no standard.  If all the web browsers were to support their own set up HTML extensions and Javascripts then it would be a mess for both web developers and web surfers.  If ATI and nVidia don't adhere to the PCI-express standard then it would create a mess for the motherboard manufacturers and consumers (and I wouldn't be building my own computers).  If there's isn't SAT, it would make getting into college much more complicated in the U.S.  If we all didn't know English (not saying it's a "standard", but a standard creates common ground, which is what we have here by knowing the English language), we wouldn't be having this conversation.

I can tell you that "perfect" competition is bad for a capitalistic free market economy, which is becoming even more dominant in this world (I have studied this subject before).  This is why you see such a clash between the idealism introduced by some open source licenses and philosophies with business goals.  Whist open source is getting more and more attention, it's also making people rethink ways to integrate the open source "advantage" with traditional business models.  It is true much of the open source business models revolves around providing service and support.  But this is not new.  Companies selling proprietary software have been doing so for a long time.  But instead of making money from the software product as well, you're only making money from service and support.  From a pure business standpoint this makes surviving in the market harder, since you can monetize fewer aspects of your business.  You *probably* can't hire as much employees because of the revenue restrictions, and that *could* translate into a less than robust labor market, which would impact you and I.  As technical developing a software may be, the current open source model is accelerating the comoditization of software products and services.  Good for consumers in the short-run, but not for existing professionals in the industry.

Moreover, relying heavily on support and services highlights an ethical/moral conflict that might cross with the personal interests of some.  If you use the "best" software, the most stable software for your customers, it might mean they will need less support and services from you.  But now that you're not selling the software, all your revenue can only come from providing service and support.  If you are ethical, you will strive to gain more customers and hope that the increased amount of customers will give you more opportunity to provide support and services.  But this means you'll need to do more work to make the same amount of money.  Similar ethical conflicts as this has long existed in other job professions, so perhaps this one will sort it self out in time.

I'm going to make a claim. The open source movement, if continued at it's current pace, will eventually catapult our society into new grounds and into a new economic system (and I may have to re-learn economics all over!) .  Hmm...the claim is off topic though... :-P

---

### Post by Wolki on 2005-08-31
[QUOTE=poofyhairguy]If you really need new packages as they are released, use Gentoo. As if to prove my theory, Ebuilds are the easiest Linux "package" to make, and Gentoo always has the newest stuff. [/QUOTE]

Stable Gentoo ebuils are quite similar to packages made by other (fast) distros. You can select to install unstable packages too, which are more up to date; but then your system is likely to break, and often. And even then you're not going to have the newest versions of everything.

These are my experiences fom running gentoo around 9 months ago. I can remember one case where i had a newer version of rox in Mandrake (using a cooker package) than the latest Gentoo one. 

This is of course not an attack on Gentoo, while it's not really the distro for me it is loved by many. But even there ebuilds have to be written and tested, updated, bugs have to be fixed etc. Packaging doesn't do itself alone and takes time, that's true for any flavor of linux.

---

### Post by neighborlee on 2005-08-31
[QUOTE=r_a_trip]***I wanted to hear more sides. My point still stands -getting to where Windows is seems impossible- but I won't say that nothing can be done.***

The price for 100% binary compatibility is the sacrifice of choice, innovation and low barrier to entry. If we were to make all distributions the same, there would be no wiggle room, no way of trying unproven ways of making something new. GNU/Linux would become a bureaucracy that forbade projects like Symphony OS, BeaTrix, Blue Eyed OS, Famelix and many others, current and future ones.[/quote]

choice is nice but how many windows/mac users do you see yelling about how horrible it is they are stuck without it. Millions of people use it everyday ( minus growing threat of virus's and spam of course) and dont have issues.

> 
***Tar files do need replacing.***

Do they? Shouldn't the OS know what to do with a source tar file and offer the user to do the "./configure && make && make install dance" automatically (on the CLI and in the GUI)? Preferably registering it with the systems standard package manager? No need for Windows-style, inaccesible binary blobs.

yeah but then we're back to gentoo, and if polled,  how many ( old timers sure but what about windows converts hoping to get good experience with an alternaive OS ) would be willing to deal with the hastle ?

Would one distro for GNU be so horrid ?,,course that would mean deliberation and agreeing on one.  The government can't even handle that so what fate would that leave for poor GNU  ;-)

Im not the enemy here as I already USE linux..and love ubuntu even though I question some design decisions....but I clamour for a time when we are as one united front,  and when such issues are mocked as wth ???. ;-)

cheers
nl

---

### Post by neighborlee on 2005-08-31
[QUOTE=kanem]Aren't all these possible problems of libraries being overwritten or erased (which, I agree, are serious problems) precluded by just not letting Autopackage install system wide? Just don't give it a root password and it has to install into your local directory. No chance of overwriting anything important, no confusing Apt. The only thing that can become broken is the app it'self that you were trying to install.

BTW poofyhairyguy, I didn't think you were the one that needed to apologize in that other thread. Speaking of threads getting testy, theres some good argumentation on this over at the [Gentoo forums](http://forums.gentoo.org/viewtopic-t-315009-start-0-postdays-0-postorder-asc-highlight-autopackage.html)[/QUOTE]

thx for url there..very interesting ;-)

cheers
nl

---

### Post by poofyhairguy on 2005-08-31
[QUOTE=DancingSun] As technical developing a software may be, the current open source model is accelerating the comoditization of software products and services.  Good for consumers in the short-run, but not for existing professionals in the industry.[/QUOTE]

Open source does not do more damage to the overall wages of software developers than the craze to outsource the jobs to whatever place has the lowest cost of living has. In fact, OSS is a way for local (U.S.) developers to stay relevent, to be paid (if only for support) when no company will hire them.

---

### Post by neighborlee on 2005-08-31
[QUOTE=super]In actuality i would presume to say that for someone who is not used to installing or has never installed software in windows, apt/synaptic really is the easier way of installing software (more intuitive, less mouse clicks, less user involvement, etc..)

but those migrating from windows would miss the installers. and as has been mentioned it would be easier for developers to produce one package that would work on all distros.

i think if autopackage can eventually do all the things it is touted to do i think it would be an excellent tool.

@ NoTiG
 
Thanks for the link, i had not heard about this. got some reading to do  :)[/QUOTE]


yes indeed..I was espeically interested to hear that autopackage supports static linking although I suppose if taken to an extreme is going to cause bloat of new libs and prob wont make everyone happy as sharelibs is the linux way >>.

however yes synaptic is very kewl..I think adding pictures and better descripts in some areas ( and url to homepage ? ) would be a very kewl addition to an otherwise excellent product. I"d be willing to help with that.

cheers
nl

---

### Post by Amaranth on 2005-09-01
[QUOTE=neighborlee]yes indeed..I was espeically interested to hear that autopackage supports static linking although I suppose if taken to an extreme is going to cause bloat of new libs and prob wont make everyone happy as sharelibs is the linux way >>.

however yes synaptic is very kewl..I think adding pictures and better descripts in some areas ( and url to homepage ? ) would be a very kewl addition to an otherwise excellent product. I"d be willing to help with that.

cheers
nl[/QUOTE]
 You might be interested in [https://wiki.ubuntu.com/FindingPackages](https://wiki.ubuntu.com/FindingPackages) then.

---

### Post by poofyhairguy on 2005-09-01
[QUOTE=neighborlee]
Would one distro for GNU be so horrid ?[/QUOTE]

Not horrid. The word you are looking for in impossible.

---

### Post by aysiu on 2005-09-01
[QUOTE=poofyhairguy]Not horrid. The word you are looking for in impossible.[/QUOTE] Actually, it would be both horrid *and* impossible. I don't think we need hundreds of distributions, but having at least five is a good thing.

I'm of the opinion that there are at least five Debian-based distros that would suit just about anyone's needs: Linspire, Mepis, Ubuntu, Debian, and Damn Small Linux.

For me info, go [here](http://www.psychocats.net/essays/whichdistro.php)

---

### Post by neighborlee on 2005-09-01
[QUOTE=Amaranth]You might be interested in [https://wiki.ubuntu.com/FindingPackages](https://wiki.ubuntu.com/FindingPackages) then.[/QUOTE]

nice thx mucho for url

cheers
nl

---

### Post by Deanodriver on 2005-09-02
[QUOTE=UbuWu]Of course windows can have a large repository of free software if someone decides to make it... Most of the best open source programs can also be used on windows (firefox, openoffice, inkscape, etc.), putting them together on one server isn't difficult at all.[/QUOTE]

What would be really useful in getting open source out to more people is a Synaptic-style program for Windows. That way, they could select from the vast array of quality open source software available, right at their fingertips (although they'd have to use the installers associated with each program), just like we can with Ubuntu, rather than looking around the Internet for each individual app.

Whilst it may not convert lots of people over to switching completely, at least it'll get more people using open-source software, and more people aware of what open source applications are available.

However, does such a program already exist? :)

---

### Post by doclivingston on 2005-09-02
[QUOTE=Deanodriver]What would be really useful in getting open source out to more people is a Synaptic-style program for Windows. That way, they could select from the vast array of quality open source software available, right at their fingertips (although they'd have to use the installers associated with each program), just like we can with Ubuntu, rather than looking around the Internet for each individual app.[/QUOTE]

[WinLibre](http://www.winlibre.com/en/index.php) is probably the kind of thing you're looking for.

---

### Post by Deanodriver on 2005-09-02
[QUOTE=doclivingston][WinLibre](http://www.winlibre.com/en/index.php) is probably the kind of thing you're looking for.[/QUOTE]

cool, I thought there'd already be such an app out there, thanks :)

---

### Post by bryan986 on 2005-09-20
Why not have a a copy of all versions of a library on a system?

So a program would be directly linked to a certain version of a library, so then it wont get broken when the library updates, or even better, a nice interface to choose which versions of a library each program uses

Sure it would use more space, but it would save a lot of headache

---

### Post by regeya on 2005-09-20
[QUOTE=N'Jal]I like and often use auto package[/QUOTE]

As do I, and I wonder why some people see it as a bad thing. *shrug*  I see nothing wrong with trying to do things the Windows way.

See, IMNSHO part of the reason you see distributions with sophisticated release cycles, dev teams devoted to keeping everything compatible just on their own distribution, etc. is because the typical Linux system is more primitive by design than Windows on exactly one front:  dynamically linked code.  How many different versions of basic MS libs do you have on one typical WinXP installation?  Depending on how much software you have installed, probably several.  It's just handled.  A lot of people deride Windows for "DLL hell" but they have a hell (pardon) of an advantage on their own system.

Personally I think it's time to rethink the idea of "distribution."  Why should I worry about what Distribution X has done to, say, KDE?  My distribution should be nothing more than the base system, IMO.  I should be able to grab, I don't know, an autopackage of KDE and be done with it.  Why not?  I already have simple programs like Lincity-NG installed and, somewhat embarrassingly NVU, via their own Autopackages and that was good enough.

---

### Post by xy77 on 2005-09-20
[QUOTE=poofyhairguy]What you want is the Windows model in Linux. We don't not want it because Windows does it or something- its just that Linux lacks major qualities of Windows. On Windows EVERYONE uses the same kernel. EVERYONE has IE (in some form). EVERYONE has _____ .dlls in the system folder by default. Same thing applies for OSX. This does not apply to Linux. That is why the ways both OSes install apps won't work in Linux.
[/QUOTE]
direct quote from [http://www.ubuntuforums.org/showthread.php?p=285685#post285685](http://www.ubuntuforums.org/showthread.php?p=285685#post285685)

Hi poofyhairguy,

I'm not completely sure, but I don't think every Windows user uses the same kernel, there are surely different for the various windows versions (9x/SE,ME,2k,xp), and I guess the kernel.exe(?) can get patched by updates or security patches (correct my if wrong). Then, there are a lot of different versions of .dll files. I used to do end-user support for an payroll accounting software. We found out you even have to check dll-versions in order to find out what's going wrong.

Just my 2ct.

- David (xy77)

---

### Post by poofyhairguy on 2005-09-20
[QUOTE=xy77]
I'm not completely sure, but I don't think every Windows user uses the same kernel, there are surely different for the various windows versions (9x/SE,ME,2k,xp), and I guess the kernel.exe(?) can get patched by updates or security patches (correct my if wrong). [/QUOTE]

What I meant was that within a version (say XP) its the same kernel. But I guess many of the problems with SP2 shows that the kernel is changed over the life of OS.

---

### Post by Stormy Eyes on 2005-09-20
No, I haven't. If it did, I would have been surprised, since Unix is not Windows.

---

### Post by doclivingston on 2005-09-20
[QUOTE=regeya]See, IMNSHO part of the reason you see distributions with sophisticated release cycles, dev teams devoted to keeping everything compatible just on their own distribution, etc. is because the typical Linux system is more primitive by design than Windows on exactly one front:  dynamically linked code.  How many different versions of basic MS libs do you have on one typical WinXP installation?  Depending on how much software you have installed, probably several.  It's just handled.  A lot of people deride Windows for "DLL hell" but they have a hell (pardon) of an advantage on their own system.[/quote]

While that kind of works, there are some problems with it:

* As there is only one version, you can upgrade by changing the one library. This is important if the upgrade fixes security problems, when you don't want to have to update several copies (and in some cases you might not know there are extra copies).

* There are libraries when you _cannot_ have multiple versions of the library being uded. As an acute example, consider mdns & dns-sd libraries, such Apple's Rendevous/Bonjour, Howl or Avahi. You CANNOT run more than one mdns stack at once - so as well as not using multiple versions of such a library, you cannot run two different ones either. If you want to run one program that is compiled to use Avahi, and one that is compiled to use Howl, you're out of luck.

---

### Post by jfdill_2 on 2005-10-20
This is too funny.  Long before Windows I was working primarily on MicroVax then SGI Unix systems.  When Windows came out, my question was, **Why doesn't Windows have a decent package manager?**  Windows really annoys me that when you uninstall stuff, it always leaves junk in the registry, and you can forget about anything like real "software dependencies."  From my perspective, I couldn't figure out why people think it's a "good thing" the way that Windows handles software install and uninstall, it's incredibly sloppy.

---

### Post by igor4u on 2005-12-01
I think Autopackage must be in Dapper! 

[http://www.linux.com/article.pl?sid=05/11/22/2021228]("http://www.linux.com/article.pl?sid=05/11/22/2021228")

---

### Post by Halvorsen on 2005-12-01
Can you tell me more about this?

As a newbie to Linux I find synaptic extreemly bad. It seems smooth enough, but is often sending me into terminal commandos or even config-files, witch seems to produce more errors than solutions.

A really working automated installer would be my first yippi! in Ubuntu.

---

### Post by lithorus on 2005-12-01
Not again.....*sigh* #-o
Old thread in Breezy : [http://ubuntuforums.org/showthread.php?t=51434](http://ubuntuforums.org/showthread.php?t=51434)

Edit:
To summarize the whole issue. Autopackage is another packagemanager which aims to be cross-distro, however it does not work together with the existing package system in the distro, this can result in a whole bunch of compliations if both gets used extensively. If it's only a few packages, it should work fine. Another thing is that it undermines the efforts done in the add/remove applications which works with synaptics which doesn't work with autopackage.

IMHO, until autopackage can talk with apt/dpkg it should not be installed per default.

---

### Post by az on 2005-12-01
[QUOTE=igor4u]I think Autopackage must be in Dapper! 
[/QUOTE]

Actually, autopackage is the tool for creating autopackage files.  I beleive that the autopackge files are self-extracting, no?

There is some great stuff there in terms of upstream developers using tools which allow for an elimination of binary-interface incompatibilities to a certain extent.  The original program developer must use those tools, though, so it is a chicken-and-egg problem.

A lot of developers think that it is easier to maintain compatibility between applications at the source level, instead of making life difficult and trying to get things working together at the binary level.

Time will tell.  Right now, it is frightening to think of the security implications this could have on the open source landscape.  That and the struggle between autopackage and native package management (apt) makes autopackage less appealing to me.  

It's your choice.

---

### Post by jounihat on 2005-12-01
I think Klik ( [http://klik.atekon.de](http://klik.atekon.de) ) has a lot more potential than Autopackage.

---

### Post by poofyhairguy on 2005-12-01
Autopackage is cool, but it works well without the blessing of the distromaker. Thats its whole point actually. good read though.

---

### Post by Anthem on 2005-12-01
[QUOTE=jounihat]I think Klik ( [http://klik.atekon.de](http://klik.atekon.de) ) has a lot more potential than Autopackage.[/QUOTE]
Glad you brought that up... I was going to if you didn't.

---

### Post by lean on 2005-12-02
Security, security, safety and security.
This is the most important aspect of software installation!

You alternatives _sucks_ to say it mildly? How are you going to know they came from a trusted source? How are you going to remove the package again? How are you going to see what resources the program will use? How are you going to limit the resources? How are you going to see excactly what the package has changed? 

Also other things - how is it going to integrate into the menu? What if Redhat has a different menu than Ubuntu?

To solve these problem a much more general package system is needed. Java webstart is actually not that bad! 
But it can get much better.

---

### Post by Halvorsen on 2005-12-02
My main reason for leaving Microsoft is hackers, spam and viruses. Otherwise I think Windows (XP) is a well working os, with third party programs like Nero, Photoshop, Open Office, Thunderbird, Firefox and so on. And it gives a warning when not sertified programs are being installed. Just as the rpm-installers.

Is this a security hazard? Will Windows and Redhat move toward Debian, where Synaptic almost decides what to install and what to leave behind (unless you are a terminalator)?

A look at [klik]("http://klik.atekon.de/") tells me that Firefox 1.5 is ready for installation. The RC2 I'm using has a lot of bugs. Is it a hazard to use klik to update Firefox?

---

### Post by teaker1s on 2005-12-02
in synaptic preferences mark recommended packages as dependencies- you will have a lot more install success

---

### Post by az on 2005-12-02
[QUOTE=Halvorsen] where Synaptic almost decides what to install and what to leave behind ?[/QUOTE]

Synaptic does not decide.  The fact is that these packages have dependancies.  Whether you play around with the ABI to resolve the dependancies or you do it at the source level, the result is the same.

It all boils down to the package maintainer.  The packaging policies are pretty strict and the bar is set high to be a debian package maintainer.  This is why debian is a quality distro.  Everything works.

---

### Post by Halvorsen on 2005-12-03
Everything didn't work in Breezy. I had to use a third party installer, Automatix, to do an automated installing of Skype. I could not install my Logitech quickcam (it frooze the hole system), and anyway there were no programs in Synaptic to use it. (Since I know the developement policy I cannot say anything about Dapper untill it's final release).

An OS is not the whole thing. We all want different things from our computers. I want a multitrack recorder working out of the box, you want something else. I'm not (yet) a terminal-user, but I want to be able to install rpm-files as well as the experts.

In the end I want Ubuntu to be so big that I can seek and give help from my friends.

---

### Post by lean on 2005-12-03
> A look at [klik]("http://klik.atekon.de/") tells me that Firefox 1.5 is ready for installation. The RC2 I'm using has a lot of bugs. Is it a hazard to use klik to update Firefox?
So you are using a release candidate of some software? That would mean you are either a developer or a software tester. Yes, maybe klik is for software testers, but not for users.
You also went to a website to update software?? And then an application that comes default with your distribution. It doesn't seem very easy from a user point of view. It should just be there, always updated always working.

And how are you sure that your software actually is well integrated with your distro? Does Firefox  from klik install in a new place? Maybe it is using an icon of a fox around a globe? WTF does that mean? I am just a user wanting to surf the web, what has a red fox to do with that???
Also, firefox goes to the page google.com per default! The Ubuntu version does not. Why should google know every time I open my browser - thats a security breach?

And then the final reason why klik is such a bad Idea - it is just the same as the apt sources! Except the programs in e.g Ubuntu apt is well tested. I would as a user, always expect my software to be well tested before I use it. How can I trust that klik applications is that (Well, Ubuntu software isn't well tested either, but you just have to use the best you can get)?

---

### Post by melalcoolique on 2005-12-03
And what about [Smart]("http://labix.org/smart") ?

This package manager is sponsorised by Canonical and is available in Dapper (smartpm).

---

### Post by jecos on 2005-12-03
Theres nothing wrong with debians apt/dpkg!  The only people that think we need another package manager are the people that have the least experience with linux..

If you can't use command line then I don't think you should be suggesting anything but asking for help instead...

---

### Post by arnieboy on 2005-12-03
[QUOTE=Halvorsen]Everything didn't work in Breezy. I had to use a third party installer, Automatix, to do an automated installing of Skype. I could not install my Logitech quickcam (it frooze the hole system), [/QUOTE]
the following is a howto which will fix the "system freezing" problem when u try to turn on ur webcam on breezy:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

### Post by lithorus on 2005-12-03
[QUOTE=jecos]Theres nothing wrong with debians apt/dpkg!  The only people that think we need another package manager are the people that have the least experience with linux..

If you can't use command line then I don't think you should be suggesting anything but asking for help instead...[/QUOTE]
Actually with gdebi the need for command line should be non-existing. Either way gdebi will give a Ubuntu alot of new possibilities in terms of integration with things like synaptic and apt.

---

### Post by Halvorsen on 2005-12-03
[QUOTE=jecos]Theres nothing wrong with debians apt/dpkg!  The only people that think we need another package manager are the people that have the least experience with linux..

If you can't use command line then I don't think you should be suggesting anything but asking for help instead...[/QUOTE]

Did jecos tell the thruth, or am I right? Am I right being a regular Ubuntu 6.04 user, to tell about my experiences with Ubuntu, or should I leave it all to the Experts? Do you want regular users in here, or not?

---

### Post by rattaro on 2005-12-04
[QUOTE=jounihat]I think Klik ( [http://klik.atekon.de](http://klik.atekon.de) ) has a lot more potential than Autopackage.[/QUOTE]

None of these package management systems are mutually exclusive of each other.  In fact, Autopackage has a completely different target user and developer population than most other systems, including Klik.  I like, Klik, and I really like Autopackage.  We can also have both, depending on what we need.

---

### Post by mhancoc7 on 2005-12-04
I started using Linux with Ubuntu. As a noobie I always found synaptic extremely easy to use and very intuitive. 

I still use it for most of my installation purposes. However I find my self using apt-get more and more. I think that between the gui approach (synaptic) and the command line approach (apt-get) it is very easy for noobies and advanced users to install/uninstall software to Ubuntu.

Edit: I forgot to mention the Add/Remove Application feature. That is a really benfit to new users since it is so very easy to use. It lets a new user install and uninstall programs with ease. Once a new user gets more comfortable with Linux or Ubuntu they can venture into the world of synaptic or apt-get.

But that is just my opinion.

God Bless, Jereme

---

### Post by LinuxWiz83 on 2005-12-04
[QUOTE=Halvorsen]Can you tell me more about this?

As a newbie to Linux I find synaptic extreemly bad. It seems smooth enough, but is often sending me into terminal commandos or even config-files, witch seems to produce more errors than solutions.

A really working automated installer would be my first yippi! in Ubuntu.[/QUOTE]

I have friends i converter to the linux desktop and they do not say this at all because they have used it through shell and now Synaptic finds the dependence for the package you want. There is no config questions except for java, tv viewers but there only preference questions really and they are not hard.

---

### Post by LinuxWiz83 on 2005-12-04
[QUOTE=Halvorsen]My main reason for leaving Microsoft is hackers, spam and viruses. Otherwise I think Windows (XP) is a well working os, with third party programs like Nero, Photoshop, Open Office, Thunderbird, Firefox and so on. And it gives a warning when not sertified programs are being installed. Just as the rpm-installers.

Is this a security hazard? Will Windows and Redhat move toward Debian, where Synaptic almost decides what to install and what to leave behind (unless you are a terminalator)?

A look at [klik]("http://klik.atekon.de/") tells me that Firefox 1.5 is ready for installation. The RC2 I'm using has a lot of bugs. Is it a hazard to use klik to update Firefox?[/QUOTE]

Well 90% of the people you think are hackers on windows are not they are script kiddies and the percentage could be higher than that. I don't call use a trojan to gain remote access to someones computer hacking or dos attacking them.

---

### Post by leech on 2005-12-04
[QUOTE=Halvorsen]My main reason for leaving Microsoft is hackers, spam and viruses. Otherwise I think Windows (XP) is a well working os, with third party programs like Nero, Photoshop, Open Office, Thunderbird, Firefox and so on. And it gives a warning when not sertified programs are being installed. Just as the rpm-installers.

Is this a security hazard? Will Windows and Redhat move toward Debian, where Synaptic almost decides what to install and what to leave behind (unless you are a terminalator)?

A look at [klik]("http://klik.atekon.de/") tells me that Firefox 1.5 is ready for installation. The RC2 I'm using has a lot of bugs. Is it a hazard to use klik to update Firefox?[/QUOTE]

Did no one else find it funny that with the exception of Photoshop, all the applications Halvorsen named run natively under linux?

Leech

---

### Post by leech on 2005-12-04
[QUOTE=Halvorsen]Did jecos tell the thruth, or am I right? Am I right being a regular Ubuntu 6.04 user, to tell about my experiences with Ubuntu, or should I leave it all to the Experts? Do you want regular users in here, or not?[/QUOTE]

Regular Ubuntu 6.04 user doesn't really fit..... since 6.04 is a development release.  Which should just be called development branch, not release.  In essence you are beta testing it.  I wouldn't say that you should have to be an Expert to do some of the testing, but it doesn't hurt.  At least if you know what you're doing and somethig breaks horribly, you can fix it.  Dapper is not intended for 'regular users' per se, but it is advantageous to the project for a 'regular user' to play with the development versions to point out what new features they would like, more than the actual trouble shooting.  Or perhaps just trouble shooting the new features that are being added, and to give advice on how it could be changed to make things easier for newer users.

Hope that all makes sense.

Leech

---

### Post by Halvorsen on 2005-12-06
First I wish to thank Arnieboy for a helping hand, and espesially for Automatix - a find for a newbie to Ubuntu.

If Automatix is looked upon as a security threat, I'd rather hear what is the problem than a general disbelief in everything else than apt-get or Synaptic.

Bruce Byfield from [Autopackage]("http://www.linux.com/article.pl?sid=05/11/22/2021228") is writing:
> Besides these technical problems, the Autopackage team believes that managing system and desktop software together is a mistake. It requires developers to pay attention to desktop applications that are of secondary importance to them, and confuses end users with problems about dependencies and upgrades. Moreover, Hearn maintains, separating the two types of packages from each other potentially makes security easier. "If you can distinguish between third-party software and operating software," he says, "then you can apply different levels of security privilege to those packages. A kernel package clearly needs full access to the system, whereas installing a chat program clearly doesn't."

Allowing ordinary users to install software is a new concept for GNU/Linux, but it's one that the Autopackage team thinks is overdue. Hearn notes that the arrangement gives users some power over what they install without doing any harm to the system. With security precautions, administrators and developers can also use local installations as a sandbox for testing programs.

"If you're a geek like me, then having two systems feels inelegant or dirty," Hearn concedes. "That's a natural feeling. But you have to stay focused on the end user. "We really do need to dump this one-size-fits-all approach to operating system design. It was a nice idea, it was tried, and it turned out to work well for servers and not so well for desktops."

Mostly I agree with Byfield, but with the security issues, I don't know who's right, Byfield or the critics.

I am looking for a way to install the windows program of my canoscan4200F, and as I see it, a desktop program that doesn't need the Linux-drivers to work, would be the best solution. (In the Wiki I was told to write my own drivers).

So I give my credit to everyone working for a better Linux.

I tried to install Skype from [klik]("http://klik.atekon.de/"), and it workes just like the Skype I installed with Automatix (takes 30 sec to load). But it lies like a green footprint on my desktop, and that isn't nice.

---

### Post by Halvorsen on 2005-12-09
Won't give up on this one. I don't want to have Ubuntu to decide what to install, upgrade or whatever.

I've tried klik, and didn't like it.

Autoconfig isn't very much updated.

---

### Post by Lovechild on 2005-12-09
Honestly I think a solution like rPath's Conary is much more suited as a replacement for our current package management systems. RBuilder makes it easy to derive a distro from the vanilla core, now imagine that all application authors out there by default checked their program updates into conary, then Ubuntu simply pulls the rPath changes, merge their patches (you always want some kind of branding patch, feature tie in, sudo patches or something like that). Build a iso and voila. Now Kubuntu could derive from rPath and Ubuntu's branch, merging their own patches.

For the user all this would be transparent, you pull binary updates but you can also rebuild from source (e.g. for debugging purposes). 

Autopackage has always seemed like an easy way to introduce insecurity and breakage on my system, having two package management systems dealing with sometimes the same code is dangerous - say I have gtk+ installed using debs, however to install package X using autopackage I need some other version of GTK+ (it might need a patched in feature, e.g.), autopackage overwrites my gtk which dpkg is tracking, this is probably no problem but the next time apt-get updates gtk+ and the patched in feature goes away.. well then the autopackage is sorta screwed right?

Having one clear way to install software is by far the best, now autopackage might be suitable as an all in all replacement for rpm/deb/portage/etc. even when they say that's not the goal but having two package managers shouldn't be the goal either.

Of course this is given my very limited understanding of how Autopackage works, I could be wrong - I honestly haven't bothered with it as I find it at a glance arcanic compared to solutions like Conary, it doesn't really introduce anything really new to the handling.

---

### Post by jdong on 2005-12-09
The idea of including Autopackage has been discussed a few times here and on the Ubuntu developer's list. The truth is that Autopackage has numerous technical and design flaws that makes it unreliable and at times even dangerous to a Linux system. As a result, there is no plan of using Autopackage.


I agree that a Coronary system would be nice to play with, especially if APT can be adapted to it.

---

### Post by Lovechild on 2005-12-09
[QUOTE=jdong]The idea of including Autopackage has been discussed a few times here and on the Ubuntu developer's list. The truth is that Autopackage has numerous technical and design flaws that makes it unreliable and at times even dangerous to a Linux system. As a result, there is no plan of using Autopackage.


I agree that a Coronary system would be nice to play with, especially if APT can be adapted to it.[/QUOTE]

As I understand it the conary console tools and the Concerto gui frontend would completely replace dpkg/apt-get/synaptics. But the transition should be very smooth once one learns conary. A bonus is that is Conary is all written in python and the recipe format even uses some of this syntax, it is extremely well designed and the format remains just as readable as say Portage' ebuilds. But I assume one could write a wrapper to have an apt-get like frontend with conary doing the magic behind the scene instead of dpkg.

I'm wondering how one could merge the launchpad platform with conary in interesting ways. The first step to try this out would of course be to split all the ubuntu patches out, branch rPath and apply them to get a conary'ified Ubuntu to work with. 

The absolutely best selling point with Conary is that is moves the distributed revision control idea that Mark likes so much directly into the package management system, deriving, sharing patches and such tasks are trivial. And all developers could have their own label developing an aspect of the system with full transparency and have conary help merge the changes back into mainline. The cost of carrying a delta is suddenly trivially low as merging back is easy.

---

### Post by Breepee on 2005-12-09
[QUOTE=Lovechild]Honestly I think a solution like rPath's Conary is much more suited as a replacement for our current package management systems. [/QUOTE]
You are looking at it from the wrong viewpoint. Autopackage is *by no means* meant as a replacement for any package system. It's meant as a *supplement* to and existing package system.

What's the use of maintaining 2 of those systems? Autopackage just something like Mozilla Thunderbird: You just include it (or not) with the distro and people can use it (or not). You don't have to use it yourself, but of course you could.

Autopackage is meant as a means to install software on any Linux system by bypassing whatever software is managing that system. Why is that a good thing? Not everything can be in the repositories, not everyone what's everything in the repositories and I really can't see why all software I should ever need has to be contained in a repositorie. I don't see the point in forcing everyone to rely on these specific repositories. Windows users just grab their software from anywhere on the web, double click and have in installed. Of course the repositories have some conveniance to it, put the point is some people don't like a) distribution specific repo's/package managers b) distributing source.

Take commercial software for example. Nowadays they all rely on custom .sh to install their bunch. Source can't be made available for obvious reasons and providing both .deb and .rpm and whatever eats too much diskspace and providing only one of these rules a big bunch of people out.

Autopackage is *the* answer. Anyone (big software companies, game companies, shareware writers, freeware writers, hell, even OSS writers) can use the system to distribute software directly. The distro does not need to make use of it itself, just provide a way with which to install software, of which I suspect could be (much needed) commercial software.

A few billion people are used to this system of distribution, almost every commercial software writer is, I can't see why filling up this gap meets resistance.

To add another comparison with our big friends from Redmond: WIndows sports Windows update and Windows Installer. Windows update provides a similar (not quite equal) functionality as apt and Windows Installer (better knows as MSI, or .msi) correlates to Autopackage. The problem with Windows is the late inception of these methods and thus many vendors already use proprietary solutions such as Installshield or NSIS, but that of course shouldn't mean that we allow the same clutter of non-centralized (de)installers.

Say no to .sh and yes to Autopackage.

---

### Post by jdong on 2005-12-09
please try to find some of the Ubuntu developers' comments about Autopackage. They've pointed out **specific flaws** in Autopackage that can result in system breakage.

---

### Post by Halvorsen on 2005-12-09
Wel, jdong, what cannot?

---

### Post by jdong on 2005-12-09
Ubuntu repository packages.

---

### Post by Lovechild on 2005-12-09
I assume this is the same problem we are seeing when installing something then having the package manager also messing with that set of file.

You can really break your system if you let anyone else, be that yourself or autopackage install stuff mess with it. As Autopackage gets more and more package especially ones replacing system packages (like gtk+), this will happen on a more regular basis because users wants the newest version of say abiword uses the autopackage because the package is still not in backports.. this is just bound to go boom.

Commercial software isn't a concern here, many projects of this kind offer debs, rpms as well as tar.gz files, and they aren't likely to overwrite system files.

Widespread advocacy of running two package managers at once is just a bad idea. It was either completely replace the current system or not even try - anything else is heresy.

---

### Post by xombie on 2005-12-09
What Breepee said and a summary.

Autopackage is targeted at closed sourced programs that need to install on a broad base of linux distributions. They auto detect where the distro puts certain files, detects missing files and installs them, and installs the application and configures it. For those of you that remember windows, it performs the same function of install shield.

Autopackage is not a distribution package management solution and never claimed to be one. It is filling the perceived need of closed source developers to distribute their wares to linux platforms.

If these developers had a clue there would not be a need for Autopackage.

---

### Post by jdong on 2005-12-09
[http://www.netsplit.com/blog/tech/autopackage_II.html](http://www.netsplit.com/blog/tech/autopackage_II.html)

Here's one particularly strong look at Autopackage from a developer.

My main concerns are that:

(1) Autopackage packages still conflict system packages by intercepting binary locations.

(2) Why the heck is it fetching executable code when run as root, and worse, not doing md5sums on fetched code?

(3) The "super smart depedency resolution" system that Autopackage uses sucks. It's incapable of detecting differences in ABI, not differentiating between libraries compiled with incompatible compilers or silent ABI breakages.


In other words, if Alien wouldn't work on the package, nor would Autopackage. It has **NO SPECIAL ABILITIES** whatsoever and will lead to more trouble than good.

---

### Post by poofyhairguy on 2005-12-09
[QUOTE=Breepee]Windows users just grab their software from anywhere on the web, double click and have in installed. Of course the repositories have some conveniance to it, put the point is some people don't like a) distribution specific repo's/package managers b) distributing source..[/QUOTE]

I don't want to criticize Autopackage, but I will say this is a false analogy. Windows does not alter versions very often- only one major upgrade since 2001! Therefore its easier to develop and release software for the more stable (library wise) Windows platform. The Linux Desktop on the other hand moves very fast. Jdong had trouble backporting an application as simple as Firefox because so many libraries it depends on have changed just since the Breezy release. Autopackage is great for software that is meant to run on your system (aka uses same libraries) or software that needs no dependancies besides itself. But I think even the Autopackage creators wouldn't say its useful in situations where you need a new kernel (like Beagle at one point) or something major like that.

Eventually one just has to deal with the fact that the software realities in the Windowsworld do not often apply to Desktop Linux. Thats why so many find it frustrating- you not only have to learn a new system with new GUIs but you have to learn the pluses and minuses of a new development philosophy that has weaknesses and strengths far differents from MS's flagship product or OSX.

---

### Post by poofyhairguy on 2005-12-09
[QUOTE=Halvorsen]Won't give up on this one. I don't want to have Ubuntu to decide what to install, upgrade or whatever.
[/QUOTE]

Well good, because for most software (aka the Universe) the decisions is Debian Sid's.

---

### Post by Breepee on 2005-12-10
[QUOTE=jdong][http://www.netsplit.com/blog/tech/autopackage_II.html](http://www.netsplit.com/blog/tech/autopackage_II.html)
In other words, if Alien wouldn't work on the package, nor would Autopackage. It has **NO SPECIAL ABILITIES** whatsoever and will lead to more trouble than good.[/QUOTE]
The point is that THERE ARE NO PACKAGES of the software targeted by Autopackage. Say Adobe would release Photoshop as .rpm. You can't expect them to rely on their customers computer-IQ to even concieve there's such a thing as Alien and then letting them convert the 600MB package (What would you think of 4GB games).

All in all, a gap that Autopackage can fit perfectly.
[QUOTE=poofyhairguy]I don't want to criticize Autopackage, but I will say this is a false analogy. Windows does not alter versions very often- only one major upgrade since 2001! Therefore its easier to develop and release software for the more stable (library wise) Windows platform. The Linux Desktop on the other hand moves very fast. Jdong had trouble backporting an application as simple as Firefox because so many libraries it depends on have changed just since the Breezy release. Autopackage is great for software that is meant to run on your system (aka uses same libraries) or software that needs no dependancies besides itself.[/QUOTE]
Windows changes too I might add, a lot of incompatibilities exist between XP and 9X. SP2 changed a few things too. On the whole you're right; Linux is on the move (therefore a difficult target for many people!).

On Windows sharing libraries (dlls) is indeed much more uncommon then on Linux. Most software is distributed with all dependancies included. It's another way of doing thing, I'm not going to favor one over the other (Linux's way is more efficient and easier to maintain I think, but the Windows-way lets the dev have more control).

Autopackage's primairy focus isn't the 'common' Linux software. Most distro's will be continuing to maintain their own repo's and such, no problem. But, nothing about Linux's dev pace is forbidding Mozilla to create a firefox.autopackage with pretty much most dependancies included (like the Windows Firefox). OK, little more clutter, but most people with their 200GB won't mind a few GB's more or less. And with Windows the space is lost anyhow, so no loss compared to Windows.

But the in the end (I personally think) autopackage will deliver commercial software to Linux. It'll function as a magnet, aiding the dev's in deploying their software across Linux-space, unlimited by distro's or dependancies.

Autopackage does have *special potential*, and I vote to grab it.

---

### Post by jdong on 2005-12-10
[QUOTE=Breepee]
Autopackage's primairy focus isn't the 'common' Linux software. Most distro's will be continuing to maintain their own repo's and such, no problem. But, nothing about Linux's dev pace is forbidding Mozilla to create a firefox.autopackage with pretty much most dependancies included (like the Windows Firefox). OK, little more clutter, but most people with their 200GB won't mind a few GB's more or less. And with Windows the space is lost anyhow, so no loss compared to Windows.

But the in the end (I personally think) autopackage will deliver commercial software to Linux. It'll function as a magnet, aiding the dev's in deploying their software across Linux-space, unlimited by distro's or dependancies.

Autopackage does have *special potential*, and I vote to grab it.[/QUOTE]

So what does that Firefox autopackage do with dumping binaries? Where are the binaries placed? What about .desktop files and menu entries? How won't those conflict the distro's built-in equivalents? What about any .so's? They'll have to be placed on the path. Will they cause conflicts with system packages?

What about system essentials needed by Firefox autopackages? I suppose it's not going to be bundling glibc, xlibs, and an entire Linux distro around it. If so, then never mind. Does Autopackage check for system dependencies, sort of. What happens if the Mozilla Autopackage is compiled with GCC 3.3 but Ubuntu's base libs are compiled with GCC 4.0? The autopackage will crash on startup.


This sounds like a GREAT idea!

---

### Post by Breepee on 2005-12-10
[QUOTE=jdong]What happens if the Mozilla Autopackage is compiled with GCC 3.3 but Ubuntu's base libs are compiled with GCC 4.0? The autopackage will crash on startup.[/QUOTE]
And why on earth would that be? Last time I checked Quake 4 ran on both GCC3 and GCC4 compiled Linuxes.

I think you understand me. Take Photshop for example on Windows (or pretty much any software on Windows)? Do I know what it install's, where it install's and how it is compiled? No. Do I need to know? No. Do I want to know? No. Does Microsoft need to know? NO!

Same with most of the software likely to use autopackage.

---

### Post by Lovechild on 2005-12-10
Quake is likely to be statically compiled to ensure the availablity of the libraries in question, no?

And autopackage wouldn't be, thus if the compatability packages aren't installed they refuse to start - just try installing the skype deb package on Breezy/Dapper and see this problem in real life.

---

### Post by jobezone on 2005-12-10
[QUOTE=xombie]What Breepee said and a summary.

Autopackage is targeted at closed sourced programs that need to install on a broad base of linux distributions. They auto detect where the distro puts certain files, detects missing files and installs them, and installs the application and configures it. For those of you that remember windows, it performs the same function of install shield.
[/QUOTE]
This is true. A few quotes from a NOTES file on autopackage's website [http://www.autopackage.org/NOTES](http://www.autopackage.org/NOTES):

"To compete
  with Windows for mindshare and acceptance we must be a platform."


"- Potential solution? A mostly informal, flexible base set
          maintained by a standard heirarchical team rather than a
          committee who are willing to patch upstream binaries in
          order to maintain compatibility with pre-existing code: the
          Microsoft approach

            - Not as extreme, majority of software on free desktop
              free software, can be upgraded for zero dollars
              (automatically?) even if it's a pain for the user, so
              affects breaking change cost/benefit analysis

            - However, basic theory is the same: don't break
              compatibility, this is more than ABI/API stability and
              includes things like buggy behaviour apps depend on.

            - We want to support games, these are almost always
              proprietary and worse they have a max shelflife of a few
              months: vendors often not interested in fixing bugs after
              this date, even if people are still playing years after
              release

        - Advantage: can be fast moving, can do things a formal
          organization would frown upon, can JUST DO IT

        - Disadvantage: lacks legitimacy
"

"- If versioning policy is moved upstream, and packaging
          decentralised WHAT IS A DISTRIBUTION?
"

Mostly, this seems to be a move supported by **proprietary** ISV's (ISV=Independent Software Developers, most of the cases this means Software Corporations) which want to get into the free software world, and since they are in a disadvantageous position with free software, because of apt-like characteristics of distributions and the nature of free software itself, are hoping to level the playing field by taking away the relevance of distributions.

---

### Post by Breepee on 2005-12-10
[QUOTE=jobezone]
Mostly, this seems to be a move supported by **proprietary** ISV's (ISV=Independent Software Developers, most of the cases this means Software Corporations) which want to get into the free software world, and since they are in a disadvantageous position with free software, because of apt-like characteristics of distributions and the nature of free software itself, are hoping to level the playing field by taking away the relevance of distributions.[/QUOTE]
Exactly.

Of course taking away the 'relevance' or difference in distributions is from developer, and ultimately the common user's (as in Windows/Office/web/theSims), point of view.

'relevance' could be taken negatively, but it's meant in a positive way. The Linux world is very fragmented and diverse and while that can be a good thing, it apparantly makes in not-so interesting for some developers.

---

### Post by Burgundavia on 2005-12-10
Autopackages is never going to happen for Dapper and I seriously doubt that it will ever happen for Ubuntu. 

Autopackage might be a nice IDEA but the implementation sucks. Every single package is an executable shell script you must run to install the package. That is completely insane.

Corey

---

### Post by Lovechild on 2005-12-10
[QUOTE=Burgundavia]Autopackages is never going to happen for Dapper and I seriously doubt that it will ever happen for Ubuntu. 

Autopackage might be a nice IDEA but the implementation sucks. Every single package is an executable shell script you must run to install the package. That is completely insane.

Corey[/QUOTE]

You speak the truth sir!

---

### Post by poofyhairguy on 2005-12-10
[QUOTE=Burgundavia]Autopackages is never going to happen for Dapper and I seriously doubt that it will ever happen for Ubuntu. 
[/QUOTE]

If Autopackage is a wild success its because it works in a way that does not need the support of each distro. Or at least thats why I got from its website.


But you are right- I remember reading that Mark is commited finacially to the Smart package manager instead.

---

### Post by asimon on 2005-12-11
[QUOTE=Burgundavia]Every single package is an executable shell script you must run to install the package. That is completely insane.
[/QUOTE]
Actually you even have to run the scripts to just see what files get installed where. There is no way to statically analyze a package to see what gets installed before actuall installation without running these scripts, i.e. something simple like dpkg-deb -c foo.deb is not possible with Autopackage. And these times you better inspect a package from a random site before you install it. Insane^2.

---

### Post by jdong on 2005-12-11
When installing an Autopackage, the executable is a stub. The rest is fetched over the network. That's right -- a root mode installer is fetching data over the network in cleartext and not checksumming it after fetching.

Insane^3.

---

### Post by neighborlee on 2005-12-11
[QUOTE=jounihat]I think Klik ( [http://klik.atekon.de](http://klik.atekon.de) ) has a lot more potential than Autopackage.[/QUOTE]

I think so too...mainly for like trying out cvs v ersions without installing anything.  I also would point people to the fact that there are tons of klik apps and  how many autopackage ?

I dont know the ins andouts of klik /autopackge but atm on the surface things would seem to point to working on more klik integration ?

i also think uninstalling via the commandline (autopackage current implementation) is rather anti-noob whereas klik uninstall is braindead easy as i recall (  just del DIR ?? )

cheers
nl

---

### Post by jdong on 2005-12-11
I think the Klik folks had been targeting Ubuntu a while back.

---

### Post by Halvorsen on 2005-12-12
[QUOTE=Burgundavia]Autopackages is never going to happen for Dapper and I seriously doubt that it will ever happen for Ubuntu. 

Autopackage might be a nice IDEA but the implementation sucks. Every single package is an executable shell script you must run to install the package. That is completely insane.

Corey[/QUOTE]

Isn't it happening in Ubuntu? Since I'm concerned with the security-issues I've not tried Autopackage, but I've seen other using it.

My point of view is more philosophcal than practical. When jdong says that Ubuntu repository packages wont result in system breakage, it isn't true. The Ubuntu Breezy forum is filled with problems. It is not a good idea to tell a lie, and then compare other systems with the new (un)truth.

A computer is not a product, like a car. It is more like a puzzle, where the issue is to fill in what's missing. From the first click we are all developing the computer-systems. And of course, we don't want to sit here as trouble-shooters for people making programs - we also want to use the machine for our purposes. I think Ubuntu has to realize this or loose popularity (myself I'm thinking about moving to a rpm-based system, where a newbie can manage to install from the desktop).

Autopackage, smart, automatix, easy-ubuntu, klik, etc. The names means nothing to me. I want a program that is easy to install, use and working. And I don't want ten different programs to do almost the same (like in the past of Linux). I installed Skype with klik. It is working and I need it. Ubuntu without Skype is no Ubuntu for me. Hopefully the Ubuntu team needs me too.

---

### Post by poofyhairguy on 2005-12-12
[QUOTE=Halvorsen] And of course, we don't want to sit here as trouble-shooters for people making programs - we also want to use the machine for our purposes. I think Ubuntu has to realize this or loose popularity (myself I'm thinking about moving to a rpm-based system, where a newbie can manage to install from the desktop).[/QUOTE]

Well, a GUI way to install debs is being made I think. And things Autopackage and klik do work on an Ubuntu system without Ubuntu support. What it comes down to is if it gets "Ubuntu's blessing" and it doesn't make sense for Ubuntu (with limited resoure for support) to give its blessing to non Debian ways of installing packages.

---

### Post by aysiu on 2005-12-12
[QUOTE=poofyhairguy]Well, a GUI way to install debs is being made I think.[/QUOTE] Isn't it called KPackage?

---

### Post by RAOF on 2005-12-12
[QUOTE=aysiu]Isn't it called KPackage?[/QUOTE]
For KDE perhaps.  I think the new gnome one is called gdebi.  Let's see if I can russtle up a link... [here]("http://lists.ubuntu.com/archives/ubuntu-devel/2005-November/013048.html")

---

### Post by leech on 2005-12-13
Yeah, in fact gdebi is already in dapper, [http://packages.ubuntu.com/dapper/admin/gdebi](http://packages.ubuntu.com/dapper/admin/gdebi) 

As far as running rpm based distros, I have used plenty of different distributions, and whenever I run a rpm based distribution it requires so many third party rpms that it ends up breaking or becoming unstable easily.  For example, with Fedora Core 4, there are several different yum repositories which have the same package, but just slightly different versions and they conflict, or sometimes when you try to do an upgrade, the mirrors are just simply down.  I haven't ever had that problem with Ubuntu (except possibly when there is a new release and they suffer the /. effect.)

Leech

---

### Post by melalcoolique on 2005-12-13
Kpackage is similar to Synaptic but "deprecated" and replaced by Adept at this time.

---

### Post by Jengu on 2005-12-13
[QUOTE=jdong]please try to find some of the Ubuntu developers' comments about Autopackage. They've pointed out **specific flaws** in Autopackage that can result in system breakage.[/QUOTE]

That's nice but the fact is their claims are going to become more and more obsolete. Autopackage is in development -- it is a moving target. For example, among the Ubuntu developer's complaints is that it doesn't have C++ support. This won't be true with the next stable release.

As long as they're saying autopackage is inadequate, they should be putting an alternative forward. The current system of dpkg/apt-get is not an attractive platform for 3rd party development. Making a package that's only going to work on one distribution is stupid, because it splits an already small market (Linux desktops). Distributing source is not an option for many companies, and honestly having to compile a package can be a major PITA anyway. gdeb isn't going to change that if I'm Joe Blow Company X, and I want to make software that runs on linux, statically linking everything is my best chance at cross-distro compatibility.

The real reason everyone hates autopackage is it reveals a nasty little secret -- the differences between many distributions are insignificant save one major detail: their packaging system. If there were an easy, consistent way of installing and removing software across distros the number of distros would shrink dramatically.


[QUOTE=jdong](3) The "super smart depedency resolution" system that Autopackage uses sucks. It's incapable of detecting differences in ABI, not differentiating between libraries compiled with incompatible compilers or silent ABI breakages.[/QUOTE]

You must be using some other software. The whole point of using autopackage is that it hides ABI differences. There's reams of documentation on their site about this.

[QUOTE=jdong]So what does that Firefox autopackage do with dumping binaries? Where are the binaries placed? What about .desktop files and menu entries? How won't those conflict the distro's built-in equivalents? What about any .so's? They'll have to be placed on the path. Will they cause conflicts with system packages?
[/quote]

[Perhaps you should read the documentation and find out]("http://www.autopackage.org").

> What happens if the Mozilla Autopackage is compiled with GCC 3.3 but Ubuntu's base libs are compiled with GCC 4.0? The autopackage will crash on startup.

Wrong. The whole point of autopackage is that it can compensate for those differences in ABI.

> This sounds like a GREAT idea!

It probably would if you had read their site before spouting off.

[QUOTE=Burgundavia]Autopackage might be a nice IDEA but the implementation sucks. Every single package is an executable shell script you must run to install the package. That is completely insane.[/QUOTE]

That would be a great argument if autopackage was meant to replace the core system package management. But it's not. The real alternative you should be comparing autopackage to is install.sh. Now all of a sudden autopackage sounds a lot more appealing...

If you actually listen to the autopackage authors, they're painting a world where there is a distinction between core OS software and desktop software. Core OS stuff is still updated in big release style increments, is handled by a standard package manager like dpkg, comes from trusted repositories, etc. Autopackage targets the desktop software like Gaim.

[QUOTE=jdong]When installing an Autopackage, the executable is a stub. The rest is fetched over the network. That's right -- a root mode installer is fetching data over the network in cleartext and not checksumming it after fetching.[/quote]

That's interesting, [because the first step in this diagram]("http://autopackage.org/docs/package-run-overview.jpg") is "Check Checksum."

But let's say for a moment that you were right. Is that a good reason to bash autopackage into oblivion? To never consider its use? Working with its developers to fix its problems seems a lot more constructive.

I think Linux distribution developers need to fess up:

1. If you want 3rd party development, a massive centralized repository for all types of packages is not a scalable system. A centralized respository for maintaining updates to *core system packages* is lean enough to be maintainable, but trying to include all linux software is not.

2. If you want to migrate desktop users from Mac OS X and Windows where they can just download the latest software on a whim, no matter of explaining dependency and ABI issues is going to satiate them. They're just going to go back to their old OS.

3. No Linux desktop OS will ever become popular unless it it's an easy target for closed source development.

Maybe autopackage isn't the answer. But the way we're doing things now sure as hell isn't either.

---

### Post by Breepee on 2005-12-13
Jengu, you got it.

---

### Post by poptones on 2005-12-13
*If you actually listen to the autopackage authors, they're painting a world where there is a distinction between core OS software and desktop software. Core OS stuff is still updated in big release style increments, is handled by a standard package manager like dpkg, comes from trusted repositories, etc. Autopackage targets the desktop software like Gaim.*

All the more reason to not listen to them. There IS no distinction between these - that's the fatal mistake made in windows: those browser-centric "activex controls" weren't supposed to be able to root a system, but in fact that's exactly what many of them do... just as GAIM, Evolution or even a simple panel applet can root a system. 

Further stirring the pot by making a "distribution agnostic rootkit" is just one more step on the road to making linux an even bigger security nightmare than windows. 

*If you want to migrate desktop users from Mac OS X and Windows where they can just download the latest software on a whim, no matter of explaining dependency and ABI issues is going to satiate them. They're just going to go back to their old OS.*

Good. If they are too unmotivated to learn something new, who needs them? We do not need ten million know-nothing users further polluting the network by installing one-click rootkits on their boxes. We should be *encouraging* these folks to stay the hell away from "desktop linux." Let them run x-boxes and tivos where the administration and support fees are built into the product.

---

### Post by asimon on 2005-12-13
[QUOTE=Jengu]That's nice but the fact is their claims are going to become more and more obsolete. Autopackage is in development -- it is a moving target. For example, among the Ubuntu developer's complaints is that it doesn't have C++ support. This won't be true with the next stable release.
[/quote]
That doesn't change that it is broken in it's fundamental design. See above posts.

[QUOTE=Jengu]The current system of dpkg/apt-get is not an attractive platform for 3rd party development. Making a package that's only going to work on one distribution is stupid, because it splits an already small market (Linux desktops). Distributing source is not an option for many companies, and honestly having to compile a package can be a major PITA anyway. gdeb isn't going to change that if I'm Joe Blow Company X, and I want to make software that runs on linux, statically linking everything is my best chance at cross-distro compatibility.
[/quote]
A per distribution package is the only way to get world-class integration into the distribution and good QA. If someone releases a general package it's usually only tested for one or two platfroms, it can break on many others, or doesn't integrate good.
And honestly why should the problems of companies who want to release propritary stuff concern us? "Ubuntu is entirely committed to the principles of free software development". Free Software! Why should a distribution which is entirely commited to the principles to free software become attractive to propritary vendors? We want to get out of those chains. Propritary software vendoes already have a good attractive platform for their stuff. We want people to use Free Software.

[QUOTE=Jengu]
The real reason everyone hates autopackage is it reveals a nasty little secret[/quote]
No, the real reason is that it is technically inferior.

[QUOTE=Jengu]
If you actually listen to the autopackage authors, they're painting a world where there is a distinction between core OS software and desktop software.
[/quote]
I would have loved if the autopackage authors would have listened to apt/dpkg/rpm/yum authors with many years of expierience. Some of them already made nice (or not if you happen to be a autopackage author) technical rants about it.

[QUOTE=Jengu]
But let's say for a moment that you were right. Is that a good reason to bash autopackage into oblivion? To never consider its use? Working with its developers to fix its problems seems a lot more constructive.
[/quote]
It's not easily fixed by a patch here and there. It's a fundamental design which is (in the eyes of many) totaly wrong.

[QUOTE=Jengu]
3. No Linux desktop OS will ever become popular unless it it's an easy target for closed source development.
[/quote]
I don't want to become Linux a good platfrom for closed source development. Use Windows. I want Linux to be the best platfrom for free software development, a priciple Ubuntu is entirely commited to.

---

### Post by Jengu on 2005-12-13
> 
A per distribution package is the only way to get world-class integration into the distribution and good QA. If someone releases a general package it's usually only tested for one or two platfroms, it can break on many others, or doesn't integrate good.


Not really. By 'breaking' you really just mean 'entering into dependency hell.' By integrating you mean 'was compiled with the same ABI.' Autopackage is here to help solve those.

> 
And honestly why should the problems of companies who want to release propritary stuff concern us? "Ubuntu is entirely committed to the principles of free software development". Free Software! Why should a distribution which is entirely commited to the principles to free software become attractive to propritary vendors? We want to get out of those chains. Propritary software vendoes already have a good attractive platform for their stuff. We want people to use Free Software.


Because the idea that free software is going to go the whole way all by itself is naive. If the free software movement will ever catch on en masse, it will begin by people becoming exposed to mixed systems of closed and open source software. Look at the number of windows users running Firefox.

> 
I would have loved if the autopackage authors would have listened to apt/dpkg/rpm/yum authors with many years of expierience. Some of them already made nice (or not if you happen to be a autopackage author) technical rants about it.


I've seen a few. The ones that I have seen are usually written by developers who don't understand the idea of a desktop platform. They're still locked in the server mindset. One technical aspect they perceive to be wrong and they immediately become prejudice against the whole project. If you want to link to some enlightened rants that don't argue points argued in the autopackage.org FAQ, I'd love URLs.


> I don't want to become Linux a good platfrom for closed source development. Use Windows. I want Linux to be the best platfrom for free software development, a priciple Ubuntu is entirely commited to.

**Windows is a better platform for open source development from a desktop user's persepective**. Yeah, I said it. I want OO2? I just go to openoffice.org and download it. I don't 'nano' my 'sources.list'. I don't wait for a backport. I don't 'compile' anything from 'source.' Firefox 1.5? Same deal.

P.S. Will people arguing this please go to [www.autopackage.org](www.autopackage.org) and read the FAQ. All the comparisons to ActiveX show some people clearly don't know what they're talking about.

---

### Post by Lovechild on 2005-12-13
Ah so now we are operating with the idea that the debian/ubuntu cabal is preventing this great new technology from entering the arena.. maybe you people should try reading the technical reasons why this is a bad idea before putting on the tinfoil hat.

It's executables that run as root
It ventures into the package managers domain, thus increasing the chance of system break.. mostly untraceable breakage.

If for some reason a program is missing from the repos, instead of reinventing the wheel, add them to Universe.

---

### Post by charlieg on 2005-12-13
[QUOTE=poptones]We do not need ten million know-nothing users further polluting the network by installing one-click rootkits on their boxes. We should be *encouraging* these folks to stay the hell away from "desktop linux." Let them run x-boxes and tivos where the administration and support fees are built into the product.[/QUOTE]

That is such a retarded outlook.  By that token, let's just forget making Desktop Linux for anybody other that developers who understand how to lock down their machines.  Let's send the rest packing back to Windows.  Really, that's undermining the whole reason behind Ubuntu and all the other projects striving to make software better for everybody.

Not all 3rd party software is malicious.  If you woke up and smelt the coffee, you'd realise the **entire purpose** of this thread is to say, "Let's coordinate efforts on some level, thereby creating a significant pool of applications that users can install without absorbing humoungous amounts of Ubuntu Foundation resources."

Why should I not be able to just grab the latest version of Inkscape.  Why do I need to wait for it to be integrated into Ubuntu?  Answer, I don't, I just use the autopackage.  Now I happen to trust Inkscape, but it would be great if this could be officially acknowledged by Ubuntu.

Nobody is asking Ubuntu to redesign itself around autopackage.  Just, why employ another person to look after another suite of desktop applications when the applications can support themselves.  When you multiply this effort by the number of Linux distributions, think about the amount of duplicated work.  It's one of many things slowing down the "Free Software Revolution" when it should be at full steam ahead by now.

---

### Post by asimon on 2005-12-13
[QUOTE=Jengu]Not really. By 'breaking' you really just mean 'entering into dependency hell.' By integrating you mean 'was compiled with the same ABI.' Autopackage is here to help solve those.[/quote]
Broken dependencies are not the only reason why a package is broken. There are many more. And integration has nothing do to with ABI. I mean stuff like using the distros menu system, using the distros init scripts system, following the distros filesystem layout, following package guidelines of the distro, integrate into things like Yast, Guidance, system tools, etc. There is much more work to get a good package done than building the binaries and place them somewhere. And I have seen specs for rpms which are meant to build on different versions of SUSE, Mandrake, and Red Hat all together. They are not very maintainable because they are full of conditionals to handle the various distro (versions) indiocyncracies.


[QUOTE=Jengu]
If you want to link to some enlightened rants that don't argue points argued in the autopackage.org FAQ, I'd love URLs.
[/quote]
The usual blogs and packager's list are all full of discussions. Easy to google. Evidently the FAQ's answer are not enough for many people.

[QUOTE=Jengu]
**Windows is a better platform for open source development from a desktop user's persepective**. Yeah, I said it. I want OO2? I just go to openoffice.org and download it. I don't 'nano' my 'sources.list'. I don't wait for a backport. I don't 'compile' anything from 'source.' Firefox 1.5? Same deal.[/quote]
There is only one Windows. In the free software world it's possible for me to change stuff and release a new version (Like Ubuntu did with Debian). And this is good. Because I may not like what there is already. The situation is different. If I were able to fork Windows and make changes to the system, openoffice.org wouldn't be able to have one binary for all those possible versions out there.


Ubuntu users can download autopackge and install stuff with it already, can't they? I am against putting it into main. Maybe universe. But the main developers should rather spend their time on better things.

---

### Post by jdong on 2005-12-13
Aren't autopackages already installable if a user decides he wants to use them? What exactly needs to be done on the Ubuntu side? It's not very "distro neutral" if distros have to implement it in some way, right? ;)

And no, their FAQ does not answer all the concerns addressed here. If it ain't gonna alien, it ain't gonna autopackage well either.

---

### Post by charlieg on 2005-12-13
[QUOTE=jdong]Aren't autopackages already installable if a user decides he wants to use them? What exactly needs to be done on the Ubuntu side? It's not very "distro neutral" if distros have to implement it in some way, right? ;)

And no, their FAQ does not answer all the concerns addressed here. If it ain't gonna alien, it ain't gonna autopackage well either.[/QUOTE]
It's not a matter of distributions implementing autopackage-specific stuff (although doing things to keep up compatability is nice), but a matter of distributions acknowledging and encouraging the installation of autopackages.

Sadly I just don't see that happening.

---

### Post by asimon on 2005-12-13
> **jdong]Aren't autopackages already installable if a user decides he wants to use them? What exactly needs to be done on the Ubuntu side? It's not very "distro neutral" if distros have to implement it in some way, right?  said:**
> 
Maybe one thing distributions should support for such packaging initiatives is a location which is correctly included in all the various paths where one can install third party packages. Currently autopacakge uses /usr to install it's stuff, which IMO is a no-go as it interferes too much with system packages. They tried first /usr/local but too many distros don't have it in their PATH,  ld.so.conf, KDEDIRS, the various XDG_ paths, etc.

[QUOTE=jdong]
If it ain't gonna alien, it ain't gonna autopackage well either.

A [quote from Joey Hess](http://kitenet.net/~joey/blog/entry/autopackage_designed_by_monkeys-2005-03-28-14-20.html), the alien maintainer:
```
In summary, autopackage is not a real package format,
it's a bunch of shell scripts that depend on other shell scripts
in the autopackage program to work, and Alien will never,
ever support autopackage unless at least this last bit is
changed.
```

---

### Post by Breepee on 2005-12-13
[QUOTE=asimon]If I were able to fork Windows and make changes to the system, openoffice.org wouldn't be able to have one binary for all those possible versions out there.[/QUOTE]
Why? Just make sure to include all dependancies (like the Win versions do). Sure, maybe it'll result in a number of redundant files, so what?

Aside from that, OOo works on 98, ME, 2000, XP and maybe even NT4, but I'm not sure about that one. All in all a bunch of not so similar OS's.

---

### Post by jdong on 2005-12-13
I'm pretty sure if I change the GDI32 API, Openoffice would need to start bundling its own version of Windows ;)

---

### Post by Halvorsen on 2005-12-13
[QUOTE=poptones]Good. If they are too unmotivated to learn something new, who needs them? We do not need ten million know-nothing users further polluting the network by installing one-click rootkits on their boxes. We should be *encouraging* these folks to stay the hell away from "desktop linux." Let them run x-boxes and tivos where the administration and support fees are built into the product.[/QUOTE]

Who are 'they' and who are 'we'? Am I amongst the ten million 'them' that 'we' don't need? Do I need myself?

My Canoscan4200F is not working in Ubuntu. The ideal solution would be to add firmware that allows my scanner to boot up a PC or even opens in a window. HD-recorders, DVD-players or even my adsl-modem has such firmware. Well, this my be the future, but not for my scanner.

So I have three possibilities. One is to have drivers and software made for Debian Ubuntu Dapper Drake. Two is to have Windows as my second distro (I am 100% Linux, but must crawl to my daugthers Windows-laptop when I need the scanner. I don't like it, and don't have enough money to feed the wealthiest man in the world). Three is to fool my scanner to think it is in a Windows-distro.

I have the Windows-drivers. I have the Windows-software. All I need is a program that will put my software on the desktop (wine doesn't install drivers). For me, this is what it is all about. And this must be the future for 3rd party programs. But do people make programs that we don't want to use? Of course not. So we must use 3rd party programs in order to develope them.

You might say I'm amogst the ten million not-human-beings that bougt a Windows-only-scanner, and of course we don't need me. I don't think that's the policy of Bill Gates.

---

### Post by leech on 2005-12-13
> My Canoscan4200F is not working in Ubuntu.

It's not so much that Ubuntu doesn't support it, but that the sane project doesn't support it.  I would suggest looking on [www.sane-project.com](www.sane-project.com) and look at what scanners work.  Or just get one of the HP scanners.  They work pretty well with linux.  I myself have a HP PSC 1315v, and it works great for both printing and scanning and cost less than $100 USD.

Back on topic....

Why Autopackage?  There is always the Loki installer, which games have been using for years.  Not to mention that Autopackage SHOULD just use /usr/local for it's software, and NEVER /usr.  They said that some distributions don't have /usr/local in their paths... that's not a problem, use SYMLINKS, it's not that hard to figure out.

I'm on the side that is against things like autopackage.  You should not HAVE TO or WANT TO go anywhere else for your software except for inside synaptic if it is free software.  For commercial products, what is wrong with the loki installer?  I personally think that Autopackage is just trying to create a 'windows like' installer, which I think stinks.  If it would for example create a .deb or .rpm or .tgz or whatever and work WITH the distribution's package manager, it would be MUCH better (in fact when I first heard of the idea, that's what I thought it was supposed to do.)  But then, that's basically what alien is for, right?  

That couldn't be all that hard, could it?  For example, you could have a set of files that is the program, then a package container that just lists these files, and tells the package manager what these files are, that way it can be removed through the package manager.  Otherwise you get a huge mess.  

Autopackage is a bad idea, plain and simple.

The only reason Autopackage came up in the first place is for those people who just don't understand what a package manager is good for.  Those people who are used to the 'windows way' of just finding software on the web, downloading it, installing it, then wondering why suddenly they have all this adware infested crap on their system.  It's a bad idea.

I really see no advantage to Autopackage over the Loki installer.  With the loki installer, it gives the choice of where you want the package, you can install it without root to the user's home directory, and it just plain works.  

If I were to create a commercial product for linux, that's what I would use.  Just distribute it as executable, maybe even customize it to ask "Do you want to install this for all users?  If so, please enter your admin password" (or maybe even put in code that checks if it's Ubuntu and then ask for the sudo password).  Then all someone would have to do is double click on the file in Nautilus (sound familiar?)  

Of course what could help as well is if the Loki installer was modified to create a listing in the package manager as well, for an easy uninstall.

The fact is, the package manager is there for a reason.  To centralize software, to let users know that it can be trusted software.  All third party apps should be installed to /usr/local.  Or perhaps /opt.  But NEVER /usr.

Ok, maybe that's enough ranting, someone has probably posted another to this thread anyhow, I just thought I'd throw in some input, since no one else seems to have mentioned the loki installer, which really should be what is used for this sort of thing.  

And for people who want to just go searching around the web, and download some weird piece of software, that is why there are sections clearly marked in Synaptic.  You want a game?  Just click Sections, Games and Amusements (there are three categories here, I think this is a usability issue, but I know why it's there (to split up free/non-free/contrib stuff) but most users aren't going to care about that, as long as the package specifies it's a demo, or whatever is fine.)

Leech

---

### Post by Breepee on 2005-12-13
[QUOTE=leech]
Why Autopackage?  There is always the Loki installer, which games have been using for years.

For commercial products, what is wrong with the loki installer?  I personally think that Autopackage is just trying to create a 'windows like' installer, which I think stinks.[/QUOTE]
Loki has been out of business for like 5 years... That's no solution.

While you may think 'windows like' installers stink, it's *the* way that 99.999% software in the world is installed, so something has to be user friendly about it. And that's what we're after, userfriendlieness. Not satisfying packagemanager-fanboys.

[QUOTE=leech]
The only reason Autopackage came up in the first place is for those people who just don't understand what a package manager is good for.  Those people who are used to the 'windows way' of just finding software on the web, downloading it, installing it, then wondering why suddenly they have all this adware infested crap on their system.  It's a bad idea.
[/QUOTE]
Again, how I'm I supposed to get some software (be it a game or photoshop for linux or something) from the store or the web and install it on every distro? .autopackage is an answer.
[QUOTE=leech]
You want a game?  Just click Sections, Games and Amusements [/QUOTE]Generally, that type of games in not why NVidia has realeased it's Geforce FX/6/7 or Ati it's 9x00/Xx00/X1x00. People want to pick up the latest and the greatest (eg Battlefield 2, King Kong, The Sims 2: exp. pack 231) from the store, and not play snake or some other have-played-that-in-DOS-20-years-ago game.

---

### Post by Lovechild on 2005-12-13
When it comes to games, the number of commercial games supported under Linux has been steadly increasing over the years, I don't see that changing anytime soon- ID Software continues to give us their brilliant engines under the GPL so if anyone is aspiring to build an FPS game the foundation is there.

I think the main problem is that curently Linux just isn't attracting the kind of people who sit down and write games for the hell of it. Gaming as a market seems to be moving towards consoles for pure profit reasons, the platform is entirely known, making development easier and the revenue stream is even for an unsuccesful game much higher than compared to even the most succesful Linux game of all time.

Not that Linux but all standards would make a great gaming OS, I used to think it would but looking at it now I see that we do lack some key things and sadly development of things like SDL completely halted - so we aren't improving much on the situation.

on the other hand, there are projects out there to provide handheld gaming consoles running Linux, etc. maybe we will see this happen within a few years - who knows.. all it takes is one guy with skills and faith in the platform really.

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=Jengu]
I think Linux distribution developers need to fess up:

1. If you want 3rd party development, a massive centralized repository for all types of packages is not a scalable system. A centralized respository for maintaining updates to *core system packages* is lean enough to be maintainable, but trying to include all linux software is not.[/QUOTE]

Tell that to Gentoo.

> 
2. If you want to migrate desktop users from Mac OS X and Windows where they can just download the latest software on a whim, no matter of explaining dependency and ABI issues is going to satiate them. They're just going to go back to their old OS.

I didn't. My friends don't. False premise.

> 
3. No Linux desktop OS will ever become popular unless it it's an easy target for closed source development.

Popular for developers. For users, no Linux Desktop will be popular till one company spends like two billion marketing it like MS does with XP. Then when it gets popular, what package manager it uses does not matter.

> 
Maybe autopackage isn't the answer. But the way we're doing things now sure as hell isn't either.

From a Windows user perspective, no.  But there is a reason that NO ONE has made a magical bridge between the distros- some thing are just too hard to do.

That said I support Autopackage for what its meant to do- be a GUI installer for certain third party apps. Is it "needed"? No, but its cool its there.

---

### Post by leech on 2005-12-13
[QUOTE=Breepee]Loki has been out of business for like 5 years... That's no solution.

While you may think 'windows like' installers stink, it's *the* way that 99.999% software in the world is installed, so something has to be user friendly about it. And that's what we're after, userfriendlieness. Not satisfying packagemanager-fanboys.[/QUOTE]

That's the beauty of open source, Loki may be out of business for 5 years, but they have opened up the source for the installer.  
[http://www.lokigames.com/development/setup.php3](http://www.lokigames.com/development/setup.php3)

Well, I wouldn't go so far as to say 99.999% of software.  Probably more like 85%, and if you look at [http://thefnords.org/windowsturd.html](http://thefnords.org/windowsturd.html) you'll see why the 'Windows Way' sucks.  By the way, that's an article that I wrote, and I made sure to try not to use any comparisons to any linux.  I still need of course to do some things with that article before I post it up on other sites...

Sorry, but the package manager (especially the add/remove programs application that Ubuntu has) is WAY easier to install things with than to go to the store and buy something that could very well not even work on your PC.  

> Again, how I'm I supposed to get some software (be it a game or photoshop for linux or something) from the store or the web and install it on every distro? .autopackage is an answer.

Just because it's AN answer, doesn't mean it's THE answer.  There is a reason for package managers.  If you read the article I write about windows, you'll see that not all programs for windows adds an entry to the Add/Remove control panel.  There is also the programs who don't put Uninstall in their menu entry.

There needs to be a STANDARD way to install packages.  Plain and simple.  Otherwise your system gets messy, and quite possibly unstable.  Debian/Ubuntu has methods already in place to convert most any package out there to a .deb, I've used it on many occasions and very rarely have I had an issue with it.  Ultimately it would be great to have .debs made by the distributor of the software, much like RPMs are made.  In fact there ARE some that do it this way.  Simple fact is, I've seen quite a few commercial programs for linux and NONE of them use Autopackage.  Doom 3 uses it's own ncurses installer, Pagestream for linux (I've just tried the demo) executes from it's own directory, UT2004 uses the Loki installer.  What I mean by standard is one that will add it to whatever package manager the distribution uses, for easy removal.  Otherwise we'll get the same thing that we do with Windows where a user has to track down how to remove a program from their system, and even if they manage to uninstall it, there still is all the crap left over in the registry.  You wouldn't want something like that would you?  

Just because linux uses a different method of installation and keeping track of what's installed than windows does, does NOT MEAN THAT IT IS WRONG.

> Generally, that type of games in not why NVidia has realeased it's Geforce FX/6/7 or Ati it's 9x00/Xx00/X1x00. People want to pick up the latest and the greatest (eg Battlefield 2, King Kong, The Sims 2: exp. pack 231) from the store, and not play snake or some other have-played-that-in-DOS-20-years-ago game.

You completely missed my point on that one.  I used the game section just as an example.  Besides games, etc, the most common software that people download off of the net are shareware programs, maybe picture viewers or sound editors, mp3 players, etc.  You can easily get all of these through synaptic.  

The ONLY problem with the package manager philosophy is support.  I know some commercial 3D software say it will only work on a certain distribution (If I recall correctly, Oracle was only recently said to officially work on Debian, even though it's been working on it forever, it was just harder to install on Debian than Red Hat.)  

Let's say sometime in the future, Photoshop comes out for linux.  You buy it from the store, come home, pop it into you rmachine.  The Loki installer pops up, asks if you want to install it as your user or as root, and if root asks for a password.  If you choose root, it installs under /usr/local/adobe/photoshop/ and then creates a symlink /usr/bin/photoshop and creates a menu entry under Applications -> Graphics -> Adobe Photoshop.  This will also put a menu entry for Loki_Uninstall.  When you open that up, it gives you a list of everything that is installed with the loki installer.  Of course if you installed the program as root, you'll need to put in the root password to uninstall it.  But the point is, this method works, it's already out there (except the part about asking for passwords, which couldn't be that hard to put in).  Why develop Autopackage?  It's like trying to re-invent the wheel.

Maybe the other improvement we could do with the Loki installer is to talk to apt/yum/<other package manager>.  

Loki may be out of business, but the installer is out there (I think even America's Army uses it as well).  This is pretty much a no brainer considering a lot of the windows installers require the developers to pay a licensing fee, and the loki installer is FREE.

Leech

---

### Post by leech on 2005-12-13
> For users, no Linux Desktop will be popular till one company spends like two billion marketing it like MS does with XP.

Actually two things must happen for Linux to really take off on the desktop.  The first one, you named.  Though IBM has been marketing it, just as a server OS though.

The Second thing would be to have OEMs sell linux computers.  If Dell and HP suddenly started shipping 1/10 of their PCs with linux pre-installed, I bet it would take off like wildfire.  I bet if a person could walk into their local CompUSA and see up on the shelf a computer with Windows XP next to one with Ubuntu and then Kubuntu and then a Mac, there would be a LOT more Linux users.  Once that happens then more and more companies will start creating software for the platform.  The Linspire computers that Walmart sells would have done a whole lot better if Walmart had carried them inside the stores themselves.  At least that way some shoppers could see it in action.  KDE and Gnome can look very pretty, and functional (granted, if you're a 5 year old that's heavily into Fisher Price you may choose Windows XP over either of them) so I think they would sell on that alone.  And add in the marketing, "Virus and spyware free, plus less expensive than the competition!"  Just advertise all the 'bundled' software, like a full office suite, photo image manipulation software, games (even old Dos games and ones like Mahjongg are great for Mom), video editing, etc.  

Once that happens, and sales start to go up on them, more companies will start making their software for linux.  I really don't think it has much to do with package managers or the fact that there are a million distributions.  All a company has to do is say "This requires Fedora Core 4" or something like that, and I can pretty much gaurantee that someone out on the Internet would find a way to install it on Ubuntu or Gentoo.  They could even just have data files seperate, and make a simple package for each major distribution.  A good example of this is Cedega.  It now has an engine package and .deb, .rpm, .tgz (maybe more, can't recall).  

This is the day I'm looking forward too.  I really wish I could get a SBA loan, 'cause then I would start my own store selling computers with pre-installed linux.  But that's for another discussion... :D

Leech

---

### Post by aysiu on 2005-12-13
[QUOTE=leech]The Linspire computers that Walmart sells would have done a whole lot better if Walmart had carried them inside the stores themselves.  At least that way some shoppers could see it in action.[/QUOTE] It would have helped, too, if the computers had reasonable specifications (RAM of at least 256 MB) and looked better.

---

### Post by earobinson on 2005-12-13
I would be nice!

---

### Post by poptones on 2005-12-13
> So I have three possibilities. One is to have drivers and software made for Debian Ubuntu Dapper Drake. Two is to have Windows as my second distro (I am 100% Linux, but must crawl to my daugthers Windows-laptop when I need the scanner. I don't like it, and don't have enough money to feed the wealthiest man in the world). Three is to fool my scanner to think it is in a Windows-distro.

Wrong. You have more possibilities than this - the most obvious being "live without a scanner" and the second most obvious being "stop buying hardware that is windows specific and not supportable in the operating system you have chosen." You do not go toi the Apple store and plunk down $2000 on a new system then expect it to run all your windows software and to work with all your windows hardware... how is it reasonable to expect this of linux? 

It isn't - because a computer is not just a box of parts. It's a system of hardware and software and those parts must work together. The fact you complain about this as a liability only shows how little you know about these systems and how much "the windows way" is taken for granted as "the only way." The solution is not to make everything more like windows, the solution is to explain why the old way isn't as good as the new way. The solution is education, not emulation.

> I have the Windows-drivers. I have the Windows-software.

Then, if it so important to you to have this exact scanner and software, you should run windows. 

You don't go to the Chevy dealership and demand they sell you a new Corvette painted Mustang Rallye Red - if you simply MUST have a Corvette painted Mustang Rallye Red you buy the Corvette then pay someone to fix it up for you - this is what *distributions* are for. 

If the people at Photoshop want their product deployed across "every linux desktop" then they should be striking up deals with the major distributions t support their product; license them object modules and sufficient source code the distributions can package Photoshop for their desktop with enough customization and branding to differentiate Red Hat's Photoshop from Suse's Photoshop, then let the markets decide. Adobe gets Photoshop on linux without having to actually SUPPORT Photoshop on linux, which works better for them anyway. The sooner the software OEMs learn this lesson the better off the "free software" community will be - those of us who value the *freedom* of a linux desktop can continue unabated and the people who are trying to actually earn a living by providing support on this *free* platform will be able to work with the old school publishers to bring well known "brands" to this ecosystem.

---

### Post by Breepee on 2005-12-13
[QUOTE=Lovechild]When it comes to games, the number of commercial games supported under Linux has been steadly increasing over the years, I don't see that changing anytime soon- ID Software continues to give us their brilliant engines under the GPL so if anyone is aspiring to build an FPS game the foundation is there.
[/QUOTE]
I havn't seen any increase lately. Even worse, I think the high time was a few years ago. Doom3 and Quake4 have been pretty mych the only ones the last year and that's because they're ID games and they give a shit.

Sadly, ID doesn't make diverse enough games to appease all, me included.

[QUOTE=Lovechild]
Not that Linux but all standards would make a great gaming OS, I used to think it would but looking at it now I see that we do lack some key things and sadly development of things like SDL completely halted - so we aren't improving much on the situation.[/QUOTE]
That is indeed very sad. A competitor for DirectX (like SDL, only better) is what we need.

[QUOTE=poofyhairguy]
Popular for developers. For users, no Linux Desktop will be popular till one company spends like two billion marketing it like MS does with XP. Then when it gets popular, what package manager it uses does not matter.
[/QUOTE]
No no no no NO!!!

3rd party developers have made Windows a succes. They made Windows big and had people swarm to PC's. Windows wasn't the reason they wanted a PC, it was usefull software (and perhaps games).

Buying software in a *real life store* and installing in pretty much all distro's is a requirement for real succes for Linux I think.

Your situation might work, for a single distro so that package manager indeed doesn't matter. But a single distro kicking serious MS butt, that's not going to happen.

[QUOTE=leech]
Sorry, but the package manager (especially the add/remove programs application that Ubuntu has) is WAY easier to install things with than to go to the store and buy something that could very well not even work on your PC.  
[/quote]
That may be (please let the user decide and not you!), but commercial software isn't in the store and given that fact that there are (plenty) stores that sell software and that most people want something material when the buy and are used to going to town to get stuff, installing a bought CD/DVD with software just has to be possible.
[QUOTE=leech]
Just because it's AN answer, doesn't mean it's THE answer.[/quote]
True, but it's (one of) the best right now, and we're not living in the future...
[QUOTE=leech]
There is a reason for package managers. [/quote]
Yep, and for some reason commercial software developers pretty much all ignore it.
[QUOTE=leech] If you read the article I write about windows, you'll see that not all programs for windows adds an entry to the Add/Remove control panel.  There is also the programs who don't put Uninstall in their menu entry.
[/quote]
I've developed software (and used installer software like opensource NSIS that is more powerful or at least as powerful as commercial installer software) myself in Windows, so yeah, I'm quite aware of the ad-hoc software management in Windows. I totally agree that apt is a perfect wat to maintain a distro and the software (and updates for that software) that's in the distro, but it just is not suitable (because of the fragmentation in packetmanagers) for software obtained from outside the repo's... You gotta see that.

Unless every distro has the same package manager,

---

### Post by leech on 2005-12-13
[QUOTE=Breepee]I havn't seen any increase lately. Even worse, I think the high time was a few years ago. Doom3 and Quake4 have been pretty mych the only ones the last year and that's because they're ID games and they give a shit.

Sadly, ID doesn't make diverse enough games to appease all, me included.[/QUOTE]

Hopefully Cold War will be released for Linux (it's already made, last I heard LGP may publish it, they were working on a deal with Dreamcatcher.  I think the real problem here is with Copy Protection.  Windows games have many different commercial copy protection schemes that they can license, whereas Linux really has none (at least that I'm aware of)).  Other than that, there are a few other games for it, I just can't think of any right now :D


> That is indeed very sad. A competitor for DirectX (like SDL, only better) is what we need.

Uhm, isn't OpenGL a standard.... even before DirectX was a standard?  At least for doing 3D graphics, SDL is good for the DirectDraw stuff and OpenAL for 3D sound (UT200x uses OpenAL as do several other commercial games)

> No no no no NO!!!

Yes yes yes yes YES!!!  (sorry, just had to be argumentative, since you are :D)

> 3rd party developers have made Windows a succes. They made Windows big and had people swarm to PC's. Windows wasn't the reason they wanted a PC, it was usefull software (and perhaps games).

Buying software in a *real life store* and installing in pretty much all distro's is a requirement for real succes for Linux I think.

It's the Chicken/Egg syndrome.  We need more commercial apps (including mostly games, as far as high-end professional apps, we have most of what we need for linux).  Problem is, until there is a bigger MEDIA market for it, the developers are not going to be able to talk their bosses (idiots who only see the $$$) into letting them port their programs.  By bigger media market, I mean what some refer to as Mindshare.  Personally when people say that only 3% or whatever of people in the world have linux installed on their computers, I think they are nuts.  There is no real way as of yet to determine how many linux users there are.  You can't really count it by how many people have downloaded ISOs for example, because some people (like me) download multiple distributions and try them all out.  Now do I count as 1 person, or do I count as 65 (for all the distros I've tried, well, that's a guess...) or do I count as four because I have four computers that have linux installed?  Plus even if a website puts up a poll, there are always going to be skewed numbers because of course if Ubuntu puts up a poll, of course there is going to be a lot of linux users, if you put up a poll on Microsoft.com, same thing, though maybe you'll get tons of linux users just to skew the results on that (would be rather funny).  Fact of the matter is, if anyone could walk into a store, pick up a computer with linux on it, and then that person could say "I got this great new computer, I don't have any viruses on it, and everything just works great, you should go get one." to their friends, parents, siblings etc then it would spread a lot faster than it already is.  But the fact that linux is as popular as it already is has me thinking that there is just something inherently wrong with the way things have been done before.

I know some people (my brother in law included) just don't 'get it' that you don't have to go to the store to 'buy' linux software.  Hell, anymore you don't even have to do that for windows software.  A lot of games now you can just pay over the internet and download it there.  This of course isn't feasible for dial-up users, but this is the way the future is going.  

> Your situation might work, for a single distro so that package manager indeed doesn't matter. But a single distro kicking serious MS butt, that's not going to happen.

That may be (please let the user decide and not you!), but commercial software isn't in the store and given that fact that there are (plenty) stores that sell software and that most people want something material when the buy and are used to going to town to get stuff, installing a bought CD/DVD with software just has to be possible.

I can only think of TWO stores in the Salt Lake City valley that even sells software for the PC anymore.  CompUSA and Best Buy.  All of the Software Etc stores went away.

> True, but it's (one of) the best right now, and we're not living in the future...

If it were one of the best right now, I don't think we'd be having this discussion and commercial vendors would have been using it already.  But it's still in development?  Well, until then, the Loki installer would work just fine for 3rd party commercial applications, but some are saying that they shoud be able to just go to mozilla.org, and download the newest version of Firefox.  Open source apps should always be integrated into the repositories (unless they have a weird license that says they can't be)

> Yep, and for some reason commercial software developers pretty much all ignore it.

Not all of them ignore package managers.  Cedega is one that does not.  Actually come to think of it, most of the commercial applications (non games) have used RPMs or have .debs.  RealPlayer, Maya, etc.  Granted they're mostly RPMs, but still, they don't just ignore package managers.

I've developed software (and used installer software like opensource NSIS that is more powerful or at least as powerful as commercial installer software) myself in Windows, so yeah, I'm quite aware of the ad-hoc software management in Windows. I totally agree that apt is a perfect wat to maintain a distro and the software (and updates for that software) that's in the distro, but it just is not suitable (because of the fragmentation in packetmanagers) for software obtained from outside the repo's... You gotta see that.

Unless every distro has the same package manager,[/QUOTE]

It's not that hard....  Company A makes Application B.  Application B has data files and an executable.  So Company A decides to make this available for linux.  They have several choices.  Use an open sourced installer like the Loki installer, or Autopackage or whatever.  Loki installer at least has a wide userbase already, is quite well tested.  Has an update mechanism built into it, along with an uninstall mechanism.  Loki installer works univserally on all distributions, is graphical and copies everything into a 'safe' directory /usr/local (or in /home/$user).  Autopackage is still in development, everyone in the linux community is up in arms about it for whatever reason.

Or they could do it the Cedega 5.x way.  Have a .pkg that is the engine (data) and then distribute several packages that have executable.  Build the executable for each system they want to support (let's say it's a desktop app, so they'll want to support the leading desktop distributions, which are probably Ubuntu, SuSE, Fedora and Mandriva).  So they would have to create a .deb and three .rpms.  Unfortunately for them, not all rpm based distros are compatible (same with .deb distributions, but even more so).  This actually wouldn't be much of a problem though, since for the most part they are compatible with each other.  And really, they could statically link their libraries that are required (copy them all into /usr/local/ and just use those as well) and not even have to have ANY dependencies.  In essence, distribute a .deb and a .rpm (.tgz if they want to support slackware and for some reason Gentoo users would want to be able to optimize it for that 0.1% of speed boost they may or may not get.... :D)

Autopackage to me is just another attempt at something that has already been accomplished.  A universal installer.  Why not just port the Loki installer to GTK2/QT and be done with it?  And then maybe have Loki automagically integrate with whatever package manager the distribution uses.  Hell, if I could program worth a damn, I would do it myself!

Leech

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=Breepee]
No no no no NO!!!

3rd party developers have made Windows a succes. They made Windows big and had people swarm to PC's. Windows wasn't the reason they wanted a PC, it was usefull software (and perhaps games).

Buying software in a *real life store* and installing in pretty much all distro's is a requirement for real succes for Linux I think.

Your situation might work, for a single distro so that package manager indeed doesn't matter. But a single distro kicking serious MS butt, that's not going to happen.[/QUOTE]

This is a very well worn debate. But in the end I truely think that without the dinero for marketing you will not get more developers and users on board- autopackage or not.

Don't get me wrong. I like Autopackage. A lot. I will like when it works with apt-get so I can install Linux programs the day they are released like Windows users do. I like that idea a "next, next, next" installer exists so that when the 1,000,000th Windows convert complains about Linux's software system we can say "they is another way" even if some of us think its a technical nightmare (not me).

But I don't think that even in a great form (say it works 80% of time or more) it will attract too much more Linux development. The people that do develop for Linux might use it, but I don't see Autopackage or anything like it bringing forth Photoshop for Linux or new games for Linux. I could be really wrong, but I could be very right.

Until developers are sold on Linux they won't develop for it at all. They won't be sold without influence and mass user demand. Both of those things are created by money and marketing. If such a huge influx of money entered the Desktop Linux scene (where money is scare compared to say MS or IBM) it would come through a distro. It does not matter if that distro uses Autopackage, RPM, Debs, etc. because all the new developers that came to the platform will want to develop for the "it" distro- supporting the other Desktop Linuxs that will increasingly take up a smaller part of the Linux Desktop market compared to this "it" distro would be an unneeded bonus. The other distros will have to be compatible or miss out (like Alien and Redhat stuff now).

Of course you probably disagree. I see Desktop Linux as a future market- at some point a REALLY big compay will want to play. Till then, third partydevelopment will increase at a slow pace- even with a klik or Autopackage.

---

### Post by zootreeves on 2005-12-13
Whats the advantage of auto package over just a gui installer for .deb files? (e.g. double click on the deb file to install)

---

### Post by jdong on 2005-12-13
Some would argue the lack of availability of debs that are always bleeding edge and such? "Distro neutrality"?

---

### Post by leech on 2005-12-13
Bleeding Edge is not always good.  

I don't know about everyone else's experience, but let's look at this from an entirely different point of view.

We're all linux users and/or high-powered windows users.  We have/want the latest software out there.  

Now, let's look at the average, or maybe slightly above average windows user.  For a real world person, I'll choose a friend of mine, we'll call him Fred.  Fred is a Windows user.  He is the type of person who thinks he knows a lot about computers.  I've told him a lot about computers and how to do certain things, but unless he actually does these things on a regular basis, he forgets how to do them.  So I tend to have to explain things to him over and over.

Fred uses Firefox.  He uses Firefox 1.0.4.  Why?  He's in Windows?  He can install the newest version anytime he wants to, right?  Well, yes he can.  But does he?  Nope, he waits until I come over and use his PC for something or other and then I notice he's using an old as hell version and so I update it for him.  

This is the same thing with most of the Windows users that I know.  The only time they update is when someone else does it for them.  Hell, the company that I used to work at had a CEO that would always skip Norton Anti-virus's update because "it was always coming up at the wrong time" so his virus protection was probably 6 months old.  This is the CEO of a computer based company!  Not to mention this is an AUTO updater that has enough user input just to cancel it or to do a manual upgrade.

Windows users do NOT live on the bleeding edge.  And neither do normal users that a GUI driven installer would be good for.  The only people that I know of that always want/require the newest version of any piece of software are the geeks.  Even a different friend of mine that is a network administrator and all that stuff usually waits until I go over to his house to have any of his software updated!

The point is, we really don't need autopackage.  We need a gui for commercial software, which is already available (Loki-setup, or in fact I think there are a few other free ones too).  But people keep bringing up "This needs a universal package manager!"  I don't think Autopackage is meant to be a package manager in the first place, am I right?  It's more of just a packaging mechanism.  Synaptic is a package manager, Yum is a package manager, urpmi is a package manager.  Autopackage sounds more like dpkg or rpm or .ebuild or whatever.  Something similar to the way the Loki-setup program works is perfect.  We get a way to uninstall/update the software, and we get an easy seperation from commercial and non-commercial applications.  

Why the loki-setup program hasn't been updated to do this job is beyond me.  Looks like the latest changes to it were made about 3 months ago, but those were minor.  I found the new page for the project over at icculus.org (that man is a freaking genius by the way, All Praise Ryan Gordon, the porting God.)

For the record, I think all windows users go through the phase of downloading all sorts of shareware, freeware, public domain crap and then end up removing 90% of it (I know, I did the same thing) But when it comes down to it, it's just so much easier to have all those little programs of that quality inside the package manager.  Any professional grade applications would be best off either making compatible packages for the major distributions (like I said before, there are four of them) or using something similar to Loki setup (which some would argue Autopackage is like that).  It's also another possibilty for application developers could simply post up a job opportunity to package their software for particular distributions.  Have NDAs or whatever signed, have someone who does packaging for Debian, Fedora, etc and have them create the package that just installs the software from the CD.  

Oh, and by the way, Crossover Office also uses the Loki-Setup program, for anyone who has ever used that.

Autopackage is literally trying to re-invent something that has been around for 5~ years.

Leech

P.S.  I don't mean this an attack on Jdong in any way, you brought up the bleeding edge thing, and I had to tell the funny story of people just not updating at all, even when there is an update notification (Firefox has one)

---

### Post by jdong on 2005-12-13
[QUOTE=leech]
P.S.  I don't mean this an attack on Jdong in any way, you brought up the bleeding edge thing, and I had to tell the funny story of people just not updating at all, even when there is an update notification (Firefox has one)[/QUOTE]

No problem -- if you read through the thread, I've been on the not-so-liking-autopackage side.

Bleeding edge -- people only care if it's the programs they care about. Sounds circular, but true. I've made enough bleeding edge comments for now: [http://distrowatch.com/weekly.php?issue=20051212#3](http://distrowatch.com/weekly.php?issue=20051212#3) <--- that nicely sums up my views about bleeding edge software. Fairly reasonable IMO.

---

### Post by Halvorsen on 2005-12-13
[QUOTE=poptones]Wrong. You have more possibilities than this - the most obvious being "live without a scanner" and the second most obvious being "stop buying hardware that is windows specific and not supportable in the operating system you have chosen." You do not go toi the Apple store and plunk down $2000 on a new system then expect it to run all your windows software and to work with all your windows hardware... how is it reasonable to expect this of linux? 

Then, if it so important to you to have this exact scanner and software, you should run windows. [/QUOTE]

Is this an argument? When I first tried Debian I couldn't get the integrated soundcard in my P4 mainboard to work. What is the answer to this? Buy another mainboard? I see people having trouble with their SATA HD. Don't buy SATA hard drives?

What you are telling me, is that Ubuntu is a commercial product far more expensive than other distros, not only telling me whitch programs to install, but also what hardware to buy. And for all I know, Ubuntu may be some korrupt distro getting money from selected harware producers. Hopefully someone can tell me it isn't so.

Since testing Dapper already is the biggest hazard since the invention of poker, I have decided to try the 3rd party programs. **Smart** seems to be just another kind of Synaptic. **Klik** has a lot of programs. Skype works as it did in Breezy, but of course I want to try out the windows betaversion with webcam. **Autoconfig** has few programs, and they are all in Synaptic, so I don't see the point of using it. I installed Stellarium with autoconfig. Everything went well, and the program is working fine. Synaptic tells me Stellarium is not installed, so autoconfig and Synaptic is not working together.

Let me try to look at the discussion from another point of view. Someone said Firefox is natively Linux (I thought Mozilla came from Netscape, who turned into open source and went into Linux). v1.0.7 is the latest (norwegian) version of Firefox. In windows it was faster than in Breezy. And it didn't wait for some Ubuntu-team to upgrade.

Let's say the users are 1000 to 1 with Windows vs Ubuntu. Who would the Mozilla team care most about? The 1000 Windows users, or me? Open office was Linux. The Gimp was Linux. Do we see programmers moving to areas where the people are? Will they loose interrest in developing Linux? Is poptones just telling me the same as Thunderbird, Firefox, Open office, The Gimp - go back to windows!

---

### Post by jdong on 2005-12-13
[QUOTE=Halvorsen]Is this an argument? When I first tried Debian I couldn't get the integrated soundcard in my P4 mainboard to work. What is the answer to this? Buy another mainboard? I see people having trouble with their SATA HD. Don't buy SATA hard drives?
[/quote]
Don't generalize. Have a SATA problem, apply latest BIOS patches and also hop over to #ubuntu or bugzilla.ubuntu.com to enlist developer attention to the issue. Help us identify the problem and permanently fix it.

> Let me try to look at the discussion from another point of view. Someone said Firefox is natively Linux (I thought Mozilla came from Netscape, who turned into open source and went into Linux). v1.0.7 is the latest (norwegian) version of Firefox. In windows it was faster than in Breezy. And it didn't wait for some Ubuntu-team to upgrade.

Breezy's Firefox 1.0.7 was a very unfortunate release -- patched with 10000+ lines of custom code pulled from here and there. It slowed down considerably in the process, and trust me -- I've been one of the proponents in the complaint about Breezy Firefox slowness.

You can always take mozilla.com tar.gz Firefox releases and unpack them to a folder and run it from there -- that is a pure GUI solution that works quite well.

---

### Post by leech on 2005-12-13
I completely agree with the backporting stuff.  You do a fine job at that.  One program that almost necessitates being the bleeding edge version is xmame (since every release that comes out fxes bugs and adds tons of new games to support, and very rarely has show stopping bugs), I recall reading at one point though that there was a problem with compiling it under Ubuntu, so I just grab the packages from Debian Sid and they work without problems :D

Backporting smallish programs isn't too terrible, it's when you're trying something like Firefox that it bites you in the nah nahs.  

And I think maybe you need to just work on your telepathic skills :D  

I've tried backporting a few things, and while some were successful, others were not.  Mainly I think I was trying to get a newer asterisk on Debian Sarge, and that was a headache and a half.  

Since Ubuntu has a 6 month release cycle anyhow, it's got to be hard to decide which programs should be backported and which ones could just wait until the next release.  Granted if you have support contracts and the one paying for it wants something backported, that's just what you have to do.

Maybe I should break down and try to backport xmame to Breezy myself :D

Leech

---

### Post by RAOF on 2005-12-13
[QUOTE=Halvorsen]Is this an argument? When I first tried Debian I couldn't get the integrated soundcard in my P4 mainboard to work. What is the answer to this? Buy another mainboard? I see people having trouble with their SATA HD. Don't buy SATA hard drives?...[/QUOTE]
Just to bring this vaguely back on topic, how would autopackage or other 3rd party install-type-program help here?  The problem is not (only) that they'd be perfectly happy to write a linux driver if only there was some way to install it.  
There are all sorts of reasons why companies don't produce linux drivers, and I suspect that the lack of a generalised installer barely rates on their list.

---

### Post by jdong on 2005-12-13
The backports that are officially packaged tend to be more for the "general user", excuse me for generalizing in the heat of this and the Linus GNOME debate ;)

However, power/enthusiast users tend to like to roll their own Backports to track Dapper changes more aggressively than would be sane to do officially! I tend to be one of those :)

---

### Post by leech on 2005-12-13
[QUOTE=Halvorsen]Is this an argument? When I first tried Debian I couldn't get the integrated soundcard in my P4 mainboard to work. What is the answer to this? Buy another mainboard? I see people having trouble with their SATA HD. Don't buy SATA hard drives?[/QUOTE]

Unfortunately for some hardware, you have to tweak it.  Usually this is because the hardware manufacturer does not support linux in any way, and it's just the good folks that develop the different parts of the operating system that work on it.  In some cases you're lucky if it's just a generic motherboard that the sound works at all, since they could be some unknown sound chip, though most of those anymore are still compatible with ac97.  Forums are good for that.

> What you are telling me, is that Ubuntu is a commercial product far more expensive than other distros, not only telling me whitch programs to install, but also what hardware to buy. And for all I know, Ubuntu may be some korrupt distro getting money from selected harware producers. Hopefully someone can tell me it isn't so.

That's not Ubuntu, that's Apple :D  The only reason Ubuntu would not work with a particular piece of hardware is because that piece of hardware is NOT working in linux at all.  If you had checked the sane-project page as I suggested, you would see that the Canon is NOT SUPPORTED.  That isn't the fault of either Ubuntu or the Sane project.  It's the fault of Canon for using a proprietary language for the scanner and not opening it up for anyone to create a driver.

> Since testing Dapper already is the biggest hazard since the invention of poker, I have decided to try the 3rd party programs. **Smart** seems to be just another kind of Synaptic. **Klik** has a lot of programs. Skype works as it did in Breezy, but of course I want to try out the windows betaversion with webcam. **Autoconfig** has few programs, and they are all in Synaptic, so I don't see the point of using it. I installed Stellarium with autoconfig. Everything went well, and the program is working fine. Synaptic tells me Stellarium is not installed, so autoconfig and Synaptic is not working together.[/QUTOE]

Sounds to me like you should be one of the people that either waits for Dapper to come out, and just use the backports or simply wait until a month before Dapper (when they do the feature freeze and are just doing bug fixes).  I didn't know the new version of Skype is going to have webcam support, that's sweet.  I just hope they put all features of the windows version into the linux version, or I'm going to be pissed.  The only webcam program I know of in linux is Gnomemeeting, which on the windows side only works with Netmeeting, which MS hid from everyone's view in XP (I think they did it on purpose...)

[QUOTE]Let me try to look at the discussion from another point of view. Someone said Firefox is natively Linux (I thought Mozilla came from Netscape, who turned into open source and went into Linux). v1.0.7 is the latest (norwegian) version of Firefox. In windows it was faster than in Breezy. And it didn't wait for some Ubuntu-team to upgrade.

Firefox is a native linux application...  not quite sure what you mean by that, but even Netscape (before t became Mozilla) had a native linux version.  I haven't noticed that Firefox is slow in Breezy, probably because I haven't booted into windows for weeks (not to mention I haven't rebooted my desktp in 12 days).  There is a reason why Ubuntu doesn't just upgrade it whenever a new version comes out.  It's called Stability and Support base.  Can you imagine the nightmare of trying to support a client that has all these different programs from all sorts of different places and applications that are continuously being updated?  

> Let's say the users are 1000 to 1 with Windows vs Ubuntu. Who would the Mozilla team care most about? The 1000 Windows users, or me? Open office was Linux. The Gimp was Linux. Do we see programmers moving to areas where the people are? Will they loose interrest in developing Linux? Is poptones just telling me the same as Thunderbird, Firefox, Open office, The Gimp - go back to windows!

The beauty of cross-platform applications is all in the name.....They are cross-platform, so it isn't a "we pay more attention to the windows version" For example, the Gaim.  While it is a Native linux app, it does have a port for windows, and works the same way that the same version works for Linux.  Some distributions have to patch things to make them work better with their chosen environment (for example, OpenOffice to make it look better and more integrated with Gnome).  Usually if the application is built cross-platform from the ground up, there isn't much more attention that needs to be spent on different OSs.

Leech

---

### Post by leech on 2005-12-13
[QUOTE=RAOF]Just to bring this vaguely back on topic, how would autopackage or other 3rd party install-type-program help here?  The problem is not (only) that they'd be perfectly happy to write a linux driver if only there was some way to install it.  
There are all sorts of reasons why companies don't produce linux drivers, and I suspect that the lack of a generalised installer barely rates on their list.[/QUOTE]

I agree, something like Autopackage would be pointless for a driver.  A driver should be included in the kernel if it's something like SATA, because how else are you even going to install the OS?  I prefer all the drivers I can get in the kernel (though certain types of drivers like external peripherals (mostly scanners and printers) should not be in the kernel).

Autopackage is just a bad idea, mostly because of NEW users.  To specify, NEW users meaning ones who have never used a computer before, or ones that have only barely used Windows.  In fact I think Ubuntu (and linux in general) are PERFECT for people like this.  One of the biggest problems I've personally had with telling people about linux is explaining to them that they have a repository of software to just download and use for free.  They somehow don't understand that bit of information.  "Well, can I just go out and buy a label maker for my printer?"  "No, just open up synaptic and do a search for 'label' and you'll most likely find several different programs you can install.  I would suggest glabel"  "How much does it cost?"  "Nothing, it's completely free.  Well, unles you count the time to download it, and the time for me to explain it all to you...."  

Windows users are USED to just paying for all their software.  Whether it's a label maker, or a simple frozen bubble style game.  They expect to have to pay for it.  I'm not above buying software, but I want the OS and anything that makes the OS useful to be free.  And since the various linux versions work so hard to have everything integrated well together, the package manager is never going to go away.  Which means unless there is a distribution created completely around Autopackage (like Debian and Ubuntu is around apt/dpkg and Fedora is around yum/rpm) then Autopackage is not going to go anywhere.  I know it tries to be a universal package manager, but until it can actually integrate with the existing ones, it's not going anywhere.

Leech

---

### Post by leech on 2005-12-13
[QUOTE=jdong]The backports that are officially packaged tend to be more for the "general user", excuse me for generalizing in the heat of this and the Linus GNOME debate ;)

However, power/enthusiast users tend to like to roll their own Backports to track Dapper changes more aggressively than would be sane to do officially! I tend to be one of those :)[/QUOTE]

A friend of mine showed that to me earlier today (the Linus Gnome debate).  Linus may be a great guy and gave us the Linux kernel, but that doesn't mean he is an expert on GUIs :D  Then again, I would almost tend to think the opposite, that by the very nature of him being a code hacker that he wouldn't know anything about GUIs.  I just liked some of the quotes "Interface Nazis" and "Feature Sluts"  Ah, the war rages on....

Oh, and to be on topic.  Autopackage sucks :D

Leech

---

### Post by jdong on 2005-12-13
I'm not in a diss linus mood today, just happy that Linux gives me the choice to choose :)

Though at times I migrate between KDE and GNOME, for the most part I find myself a happy GNOME user... and I consider myself no idiot by any measure :)

---

### Post by leech on 2005-12-13
[QUOTE=jdong]I'm not in a diss linus mood today, just happy that Linux gives me the choice to choose :)

Though at times I migrate between KDE and GNOME, for the most part I find myself a happy GNOME user... and I consider myself no idiot by any measure :)[/QUOTE]

I TRY to like KDE.... I really do.  But everytime I use it (which is pretty much about every new release of it) something starts to bug me to no end, so I end up going back to Gnome.  When I first started using Linux, it was really Enlightenment that made me think "I want to run that, it is cool!"  That was in the days of DR13.  Then on and off of linux for awhile after that, until KDE 1.0 came out.  For me it was too much like windows....  So I thought I may as well go back to windows, same crappy interface but has more games/apps.  Well, then Gnome came out and I loved it... even using the pre-1.0 on Debian was fun.  I've stuck with Gnome since then, but as I said, every new release of KDE I try it out, hoping it's gotten better.

When 3.5.0 came out I installed it through the KDE Breezy repositories at ftp.kde.org and it works pretty well, and I'll probably logout and play around with it some more later.  But there was still something that bugged me about it... can't place my finger on it now, but I'll list some past annoyances....

1) Sounds.  The sounds in KDE are SO obtrusive and annoying, come on, who wants to hear a sound everytime a window is opened, closed, minimized, maximized etc.  I'm suprised they didn't have a sound for when you MOVED the window.  And it's not terribly obvious how to turn these sounds off.  

2) The Keramik theme.  That has got to be the ugliest them ever made.  Even Windows XP's luna theme didn't look so hideous.  Thank god for Plastik

3) The Clock.  How on earth can they think that hiding the option to switch between 12h and 24h time is a good thing?  I was playing around with the RR4 Gentoo Linux LiveDVD and spent probably 30 minutes trying to find it.  Finally gave up in a cloud of curses.

Anyhow enough of the DE rant.  Linus is a good guy, I just find it funny that he calls Gnome users idiots, just because he's a power user.  I usually am a power user too, but KDE just isn't lain out very well.  

Maybe I should start a new topic on this somewhere else, since ths is going way off of talking about Autopackage....  

Leech

---

### Post by Breepee on 2005-12-14
[QUOTE=leech]Other than that, there are a few other games for it, I just can't think of any right now :D
[/quote]
That's the problem isn't it :rolleyes: No one can.
[QUOTE=leech]

Uhm, isn't OpenGL a standard.... even before DirectX was a standard?  At least for doing 3D graphics, SDL is good for the DirectDraw stuff and OpenAL for 3D sound (UT200x uses OpenAL as do several other commercial games)
[/quote]
Well, Direct3D is the equivalent of OpenGL, DirectX is a whole lot more and the very reason Direct3D is used. SDL tries to be a similar framework as DirectX.

But please, read up a little on the possibilities of DirectX.
[QUOTE=leech]
It's the Chicken/Egg syndrome.
[/quote]
And all we can do is make sure everything is OK from our side. Autopackage is an effort.
[QUOTE=leech]
I know some people (my brother in law included) just don't 'get it' that you don't have to go to the store to 'buy' linux software.  Hell, anymore you don't even have to do that for windows software.  A lot of games now you can just pay over the internet and download it there.  This of course isn't feasible for dial-up users, but this is the way the future is going.  
[/quote]
Because 90% of the people do not buy online... This percentage is dropping, but still, people will always want to go to the mall, for other reason than aquiring things (have you ever shopped with a woman, you'll know what I mean).
[QUOTE=leech]
I can only think of TWO stores in the Salt Lake City valley that even sells software for the PC anymore.  CompUSA and Best Buy.  All of the Software Etc stores went away.
[/quote]
I can think of litteraly hundreds right here in Amsterdam, with dozens of *specialized* computergames shops.
[QUOTE=leech]Open source apps should always be integrated into the repositories
[/quote]
Why? Please let people decide that for themselves? Why are you thying to make choices for others which you shouldn't make?
[QUOTE=leech]


Not all of them ignore package managers.  Cedega is one that does not.  Actually come to think of it, most of the commercial applications (non games) have used RPMs or have .debs.  RealPlayer, Maya, etc.  Granted they're mostly RPMs, but still, they don't just ignore package managers.
[/quote]
It's a very limited number of products and a limited amount of format's. And generally limited in digital size so that Alien-ing those packages to deb won't take so long.

If I buy, say Splinter Cell Chaos Theory, and it comes as an rpm, I'd have to Alien 4GB in into a deb. And they're not going to supply a deb disc and a rpm disc.

It's just no solution.

[QUOTE=leech]
I've developed software (and used installer software like opensource NSIS that is more powerful or at least as powerful as commercial installer software) myself in Windows, so yeah, I'm quite aware of the ad-hoc software management in Windows. I totally agree that apt is a perfect wat to maintain a distro and the software (and updates for that software) that's in the distro, but it just is not suitable (because of the fragmentation in packetmanagers) for software obtained from outside the repo's... You gotta see that.

Unless every distro has the same package manager,[/QUOTE]

It's not that hard....  Company A makes Application B.  Application B has data files and an executable.  So Company A decides to make this available for linux.  They have several choices.  Use an open sourced installer like the Loki installer, or Autopackage or whatever.  Loki installer at least has a wide userbase already, is quite well tested.  Has an update mechanism built into it, along with an uninstall mechanism.  Loki installer works univserally on all distributions, is graphical and copies everything into a 'safe' directory /usr/local (or in /home/$user).  Autopackage is still in development, everyone in the linux community is up in arms about it for whatever reason.

Or they could do it the Cedega 5.x way.  Have a .pkg that is the engine (data) and then distribute several packages that have executable.  Build the executable for each system they want to support (let's say it's a desktop app, so they'll want to support the leading desktop distributions, which are probably Ubuntu, SuSE, Fedora and Mandriva).  So they would have to create a .deb and three .rpms.  Unfortunately for them, not all rpm based distros are compatible (same with .deb distributions, but even more so).  This actually wouldn't be much of a problem though, since for the most part they are compatible with each other.  And really, they could statically link their libraries that are required (copy them all into /usr/local/ and just use those as well) and not even have to have ANY dependencies.  In essence, distribute a .deb and a .rpm (.tgz if they want to support slackware and for some reason Gentoo users would want to be able to optimize it for that 0.1% of speed boost they may or may not get.... :D)
[/quote]
In other words, there are no readily available tools that a studio can purchase and just use and have support for if it doesn't work in 10 minutes.

These companies don't have the time nor the whishes to fiddle around for days just to sell a 100 copies more.
[QUOTE=leech]Why not just port the Loki installer to GTK2/QT and be done with it?  And then maybe have Loki automagically integrate with whatever package manager the distribution uses.[/QUOTE]
Then do it or stop arguing and admit that commercial software developers have nowhere to turn to except maybe some geeks in basements...


The point is: there has to be readily available, activily developed software that comes with some form of support.

---

### Post by Halvorsen on 2005-12-14
> **Halvorsen]Since testing Dapper already is the biggest hazard since the invention of poker, I have decided to try the 3rd party programs. **Smart** seems to be just another kind of Synaptic. **Klik** has a lot of programs. Skype works as it did in Breezy, but of course I want to try out the windows betaversion with webcam. **Autoconfig** has few programs, and they are all in Synaptic, so I don't see the point of using it. I installed Stellarium with autoconfig. Everything went well, and the program is working fine. Synaptic tells me Stellarium is not installed, so autoconfig and Synaptic is not working together.[/QUOTE]

In klik I found mldonkey. Well, thats a nice one! It's kinda slow, but a search on Bob Dylan gives more than 6000 hits. So I klik on the klmdonkey gui. Now it wasn't that easy. It doesn't come with the mldonkey-server. (Don't ask me why. I guess someone just want to have a not-working gui). So it's back to the apt-get, wget, untar, install, and the nervous tapping on the table while messages are running thru the terminal with the speed of light said:**
> gdebi[/URL]. (Is in Synaptic). A desktop installer for .deb files. So I'm back to the mldonkey sites. But where is the .deb file? There is a load of information telling me less than nothing. I'm sure the .deb file is there, but I can't find it.

In Mandriva I've been into rpm-search, and that's fun and easy. Sometimes it works, sometimes not, but it tries and is getting better day by day.

In Wiki I read:

[QUOTE=MichaelVogt]The problem
Currently, there's no easy way to install packages that have been downloaded from the web. The only way to install no-repository packages is dpkg -i with manual dependency resolution. This is not very userfriendly and does not encourage 3rd party development for Ubuntu.

The Solution
Michael Vogt has hacked together a prototype called Gdebi. The source is available via bazaar-ng (bzr) at [WWW] [http://people.ubuntu.com/~mvo/bzr/gdebi--main](http://people.ubuntu.com/~mvo/bzr/gdebi--main). Debs are available at [WWW] [http://people.ubuntu.com/~mvo/gdebi](http://people.ubuntu.com/~mvo/gdebi).

My idea would be to inspect the deb file and extract the control information and parse the Depends/PreDepends/Conflicts line. Now use libapt to figure if these dependencies can be satified and if so, install them. Then dpkg -i is called. This way it will never produce a broken cache but still make install local debs easy and painless (with information how many additonal packages needs to be installed). And no need to modify apt/synaptic/sources.list. [..]

Well, the .deb-files must be out there somewhere...

In Breezy the mldonkey-core didn't work when installing from Synaptic, so I had to do it the hard way. Then starting mlnet (mldonkey-core) from root, and then, when using Sancho as gui, I just had to download and run the Sancho-ikon to install the gui. Confusing? Not at all. You just have to see that there is no need for a universal package manager in Ubuntu. It's better to know a lot about ten installers than to have one working piece of art to use.

---

### Post by paddy2706 on 2005-12-14
[QUOTE=Halvorsen][...] So I klik on the klmdonkey gui. Now it wasn't that easy. It doesn't come with the mldonkey-server. (Don't ask me why. I guess someone just want to have a not-working gui). [...][/QUOTE]

you could use the gui with an external server, so its not neccessary to have the server installed. i guess thats y :)

---

### Post by Halvorsen on 2005-12-15
[QUOTE=leech]A friend of mine showed that to me earlier today (the Linus Gnome debate).  Linus may be a great guy and gave us the Linux kernel, but that doesn't mean he is an expert on GUIs :D  Then again, I would almost tend to think the opposite, that by the very nature of him being a code hacker that he wouldn't know anything about GUIs.  I just liked some of the quotes "Interface Nazis" and "Feature Sluts"  Ah, the war rages on....[/QUOTE]

So Thorwald Linus, the man who made all this possible, don't know Linux? I'm amazed. (And to jdong - Linus didn't call you an idiot, but said that the Gnome-people treated you like you were an idiot).

__________

I think this is about autopackage. But Linux is so filled with unfinished solutions that you have to compare them to each other. Maybe autoconfig is the right one, maybe klik, loki or gdebi (gdebi - oh, I see - that must mean gnome debian installer. Or maybe girl debi - an udressing game for mail pigs? It's not easy, but some day, who knows, we don't have to guess what a program do).

I've tried out gdebi, a desktop installer for .deb files. I found the files at the [debian packages site]("http://www.debian.org/distrib/packages").

I downloaded the Thunderbird mailclient. It was already installed on my PC, but I couln't open or copy link location in it, so it was worth a try. I right clicked on the Thunderbird .deb file an choose install. After the installation I got an error telling me to 'run apt-get install -f' to correct a depency problem, and so I did.  (I still could not open a link in Thunderbird, but I could copy it).

So you see. gdebi isn't a desktop-installer, but it's a beginning. Just like autoconfig.

The next try was mldonkey-server. gdebi told me that mldonkey was a newer version than in the repositories, and adwised me to use the old one, but this was exactly what I was looking for. I choose to install. The installation went one for some minutes, but nothing happend. Then I saw this litle arrow where I could open the terminal, and had to choose to start mldonkey at startup or not. The installation went fine, and everything is working.

(Mldonkey is a p2p program who downloades from torrent, kazaa, amule and so on at the same time. Mldonkey need a gui to work, and I think Sancho is the best one. When Sancho is dl and extracted, you just dobbelclick on the icon to install it. But before you can run it you must open mldonkey in a terminal by writing 'sudo mlnet'. It is possible for Sancho to start and kill the mldonkey-server, but Ubuntu don't give permission to let Sancho do this. Maybe someone can tell what to do to put Sancho into the gnomepanel and to start mldonkey without a terminal.

Thats that. Next stop is Loki.

---

### Post by jdong on 2005-12-15
[QUOTE=Halvorsen](And to jdong - Linus didn't call you an idiot, but said that the Gnome-people treated you like you were an idiot).
[/QUOTE]


What I was trying to say is that in the current situation, we need to be cautious when trying to talk on behalf of "THE AVERAGE USER" or "THE TYPICAL USER" or "THE NORMAL USER".

---

### Post by leech on 2005-12-15
[QUOTE=jdong]What I was trying to say is that in the current situation, we need to be cautious when trying to talk on behalf of "THE AVERAGE USER" or "THE TYPICAL USER" or "THE NORMAL USER".[/QUOTE]

Exactly!  I personally find the definition of NORMAL (about anything) is completely relative to the people you hang out with.  Normal in the case of Gnome would be the people they are targetting, mainly corporate desktops.  But they also target those who just like to USE their computers and don't need to tweak every bit of their OS.  Gnome is about good defaults and KDE is about every setting possible.  

Choice as always is good.  I just think it's funny that Linus tells people to switch to KDE.  He's a programmer, which of course means he wants all the configuration options that he can get.  People like my Mom who would never need to change settings on her clock, or never needs to move where the close/minimize/maximise buttons are.... Gnome is for those people.  KDE is for those who want to be able to customize their desktop to whatever they'd like it to be.  

I find it even more hilarious that one of the goals for KDE 4 is to simplify the dialogs and make it more gnome-like.  While at the same time the Gnome developers are trying to make theirs have more options (tucked away in Gconf) and more features.  I think somewhere in between is the happy medium, but the DEs should have a good default desktop (which Kubuntu I would say does, but it's always crashing on me (especially when I log out)).  Super Karamba does look very nice, but why on earth would they remove the option to uninstall a widget?  That sounds even worse than anything I've ever heard of gnome removing!

The theory of Autopackage is good, but doesn't work for several reasons and in general is only a good idea for COMMERCIAL packages.  Any Open Sourced ones should be handled by the package manager, period.  Just because some people don't like package managers for whatever reason, does not mean that they aren't a good idea.

They keep the system clean, though if it's like Fedora Core, it still gets messy, because you have to have so many different repositories just to get mp3 capability and nvidia drivers...  but that's for another rant.

Leech

---

### Post by rykel on 2005-12-15
[QUOTE=lithorus]Not again.....*sigh* #-o[/QUOTE]

pal... the reason why autopackage keeps coming up is simply because, like it or not, it's **popular**... it's useful, it's easy and it's visually appealing. it's also FREE ($$$) (code) software.

> 
To summarize the whole issue. Autopackage is another packagemanager which aims to be cross-distro, however it does not work together with the existing package system in the distro, this can result in a whole bunch of compliations if both gets used extensively. If it's only a few packages, it should work fine. Another thing is that it undermines the efforts done in the add/remove applications which works with synaptics which doesn't work with autopackage.

IMHO, until autopackage can talk with apt/dpkg it should not be installed per default.

synaptic should devote itself to core system files, and let autopackage take care of all the rest - ie. the applications, such as openoffice, firefox, thunderbird, amarok, totem, xine, xsane etc.

and no, autopackage is not "another" package manager which aims to be cross-distro... it is currently, imho, ***THE* installer which runs on all distros** ~ whether ubuntu, suse, fedora, mandriva, mepis, RPM or DEB-based.

i don't mean to sound anything more than just stating my two cents here (so no offenses! pls don't debate!), and please understand that i am simply an **autopackage user and advocate**!

i love you all!!

---

### Post by jdong on 2005-12-15
The only thing is, Autopackage currently is not technologically powerful enough to handle universal installation of half or more of the software you listed. Especially those with strings and strings of system level dependencies (i.e. Amarok). It will lead to a less unified distribution, which is the opposite of what we want.


We hear your requests for easier to install, wider selection of, and more up to date packages. We are trying hard to address all of these concerns in technically sound manners -- trust us. Just give us a chance. Abandoning our efforts and delegating responsibility to Autopackage, in many ways, is a step back for Dapper.

---

### Post by rykel on 2005-12-15
guys, i believe i am quite right when i say tat in the world of open source, if u feel tat some software is inadequate in meeting your needs, you are at liberty to contribute patches and changes to it.

so, instead of going into two camps regarding autopackage, the "autopackage-does-not-work-with-my-rpm-or-deb-repositories-so-i-won't-use-it" and the "i love autopackage!" types, why don't u take the effort to help out the autopackage project ~ if u feel tat autopackage is not up to par?

after all, if YOU can write a patch to make autopackage synchronise with the native package manager or do watever u feel it should do before installing the latest and greatest program, why not?

it will both improve autopackage AND satisfy the discomfort of those who are against autopackage. lets put some action and work together rather than NATO all day. (no action talk only)

the spirit of open source and free (code) software! yeah!   =)

---

### Post by RAOF on 2005-12-15
[QUOTE=rykel]...
after all, if YOU can write a patch to make autopackage synchronise with the native package manager or do watever u feel it should do before installing the latest and greatest program, why not?
...[/QUOTE]
One problem is time.  There are many, many solutions to this problem of installing stuff.  It is impossible to work on all of them, so devs prioritise.  Since autopackage does not appear to them to be a technically sound solution, they won't want to spend the time working on it.  You are, of course, welcome to work on it yourself ;)

Another problem I've already touched upon:  maybe autopackage's design makes it fundamentally difficult to make it acceptable to the devs.  They certainly seem to think so.

Finally, the Ubuntu devs need do nothing to support autopackage.  That is, after all, its main selling point - it needs no distro support.  You can use autopackages all you like.  We won't stop you :)

---

### Post by rykel on 2005-12-15
[QUOTE=jdong]The only thing is, Autopackage currently is not technologically powerful enough to handle universal installation of half or more of the software you listed. Especially those with strings and strings of system level dependencies (i.e. Amarok). It will lead to a less unified distribution, which is the opposite of what we want.


We hear your requests for easier to install, wider selection of, and more up to date packages. We are trying hard to address all of these concerns in technically sound manners -- trust us. Just give us a chance. Abandoning our efforts and delegating responsibility to Autopackage, in many ways, is a step back for Dapper.[/QUOTE]

thanks brother!! i will check with the autopackage team abt the ability of autopackage to actually handle complex software ~ i believe things are being hammered out to make autopackage better ~ and yes, thank u for giving little users like me a chance to feedback... i know tat ***both ubuntu and autopackage are efforts to improve the linux experience!***

until a better alternative appears (or mabbe autopackage gets the worldwide developers' contribution - and thus gets modified until it is able to handle difficult programs AND synchronise with the native rpm/deb database), i am afraid it is the best solution tat end users across all distros have right now to get the latest and greatest software.

running firefox 1.5 already!! thanks autopackage.

---

### Post by -DarkMind- on 2005-12-15
autopackage is great!

---

### Post by poptones on 2005-12-15
> so, instead of going into two camps regarding autopackage, the "autopackage-does-not-work-with-my-rpm-or-deb-repositories-so-i-won't-use-it" and the "i love autopackage!" types, why don't u take the effort to help out the autopackage project ~ if u feel tat autopackage is not up to par?

If you feel my six wheel bicycle isn't up to par then stop complaining about why it won't work and help me build it! The world needs a six wheel bicycle!

---

### Post by poptones on 2005-12-15
By the way.... it is this sort of attitude:

> Then do it or stop arguing and admit that commercial software developers have nowhere to turn to except maybe some geeks in basements...

That demanding, ungrateful, "the market demands it" attitude provokes me and many others to say "piss off, linux works for me and "we" do not need you." **Linux is not a corporation. Linux does not owe you anything and does not need "the market" in order to survive.**

If adopting "autopackage" were the only thing standing between wankers like you using this OS and not using it I would make it my personal mission to kill the project dead, dead, dead.

Go back to Windows, you effin ingrate. It was those "geeks in basements" that created this fucking operating system, that support it, and that will keep it going long after you've gone back to Mild Bill's teat.

---

### Post by Jengu on 2005-12-16
> **Lovechild]Ah so now we are operating with the idea that the debian/ubuntu cabal is preventing this great new technology from entering the arena..[/quote]

Who said that?

[QUOTE=asimon]
There is only one Windows. In the free software world it's possible for me to change stuff and release a new version (Like Ubuntu did with Debian). And this is good. Because I may not like what there is already. The situation is different. If I were able to fork Windows and make changes to the system, openoffice.org wouldn't be able to have one binary for all those possible versions out there.[/QUOTE]

That's funny, the one OO2 binary seems to run on Windows98, Windows ME, Windows 2000, Windows XP...

The point is -- for most linux distro differences -- desktop users just don't give a damn. Having a slightly different naming scheme for the file layout for example, doesn't justify a new distro. That just leads to stupid duplication of work. No one **cares** if fonts are in /usr/fonts or /usr/share/fonts, so long as the location is consistent. But a lot of the differences between distros is dumb stuff like that still.

[QUOTE=jdong]And no, their FAQ does not answer all the concerns addressed here. If it ain't gonna alien, it ain't gonna autopackage well either.[/QUOTE]

Wrong. Alien converts *already compiled* packages to different formats. It's an attempt to make them usable across different distros *with no intervention from the developer*. Autopackage, however, requires developers' intervention in order to work. A few source changes, and autopackage takes care of ABI issues for you. Alien doesn't do that at all. Go look at the reams of documentation on binary compatibility they have on their site. Hell, just look at the frontpage, that brags that 1.0 can handle mplayer. Tried running alien on mplayer? I did -- segfaults and makes my terminal unresponsive everytime a video ends.

[QUOTE=jdong]Aren't autopackages already installable if a user decides he wants to use them? What exactly needs to be done on the Ubuntu side? It's not very "distro neutral" if distros have to implement it in some way, right?  said:**
> 

Well, as long as distributions spend tons and tons of time packaging desktop software independently, time that could be spent hacking on something useful, encouraging distros to take a closer look at autopackage makes sense. And a lot of free software authors are also the packagers of their software for their favorite distro, so trying to get at them this way makes sense. 

[QUOTE=jdong]I'm pretty sure if I change the GDI32 API, Openoffice would need to start bundling its own version of Windows ;)

What exactly is the linux corallary here? gtk and gtk2 can coexist on the same system.

[QUOTE=leech]
Why Autopackage?  There is always the Loki installer, which games have been using for years.
[/quote]

You're kidding, right? The loki installer isn't much more than an xdialog for copying files.

> 
The only reason Autopackage came up in the first place is for those people who just don't understand what a package manager is good for.  Those people who are used to the 'windows way' of just finding software on the web, downloading it, installing it, then wondering why suddenly they have all this adware infested crap on their system.  It's a bad idea.


Please stop making stuff up. The autopackage developers didn't make autopackage because they "didn't understand what a package manger is good for."

> 
I really see no advantage to Autopackage over the Loki installer.  With the loki installer, it gives the choice of where you want the package, you can install it without root to the user's home directory, and it just plain works.  

...

The fact is, the package manager is there for a reason.  To centralize software, to let users know that it can be trusted software.  All third party apps should be installed to /usr/local.  Or perhaps /opt.  But NEVER /usr.


And now for those that can't read:

> 
The Autopackage FAQ

# Why do packages install to /usr by default?

We used to use /usr/local however there are too many distros that do not set up all the paths for this correctly, so **various things broke badly**. In particular, *desktop integration like menu items and file associations tend not to work*.

Installing to /usr fixed all these issues and gives the user a much more reliable experience. **If you dislike it you can alter the default install prefix in the /etc/autopackage/config file, or use the --prefix switch.**

**Alternatively, report bugs against your distribution to get /usr/local (or /opt, or wherever) supported as a first class citizen and we will whitelist the distribution upstream so autopackages automatically install to wherever your distribution prefers**. We won't do this unless installing to the chosen prefix is as functional as installing to /usr however.


[QUOTE=poofyhairguy]Tell that to Gentoo.[/quote]

That's funny, I used gentoo for over a year and found software that wasn't in portage all the time. Did I mention they're about 4 versions behind stable wine? That QT4 is just making it in now? That they didn't update Python for **ages**?

> I didn't. My friends don't. False premise.

Do you really think that as someone willing to install a desktop linux distro in its current state, post on that linux distributions forum, and argue over linux packaging mechanisms that you and your friends somehow represent the average user? We're all geeks here :cool: 

> 
Popular for developers. For users, no Linux Desktop will be popular till one company spends like two billion marketing it like MS does with XP. Then when it gets popular, what package manager it uses does not matter.

People will switch over the right applications. Think about how many computers Apple has sold because of the iPod/iTunes.

All that said, do I think autopackage is the bees knees? No. But is it incredibly clear that half the people here are against it because they either don't know what they're talking about, haven't read the FAQ, are prejudiced because ubuntu doesn't follow the autopackage way, or are snotty geeks who think that only they and their equally full of free time brethren should be able to use computers? Yes.

Cmon. When the real whiz bang solution does come around, at this rate, no one is going to recognize it. Instead we'll all throw stones at it because it's new.

---

### Post by Breepee on 2005-12-16
[QUOTE=poptones]By the way.... it is this sort of attitude:



That demanding, ungrateful, "the market demands it" attitude provokes me and many others to say "piss off, linux works for me and "we" do not need you." **Linux is not a corporation. Linux does not owe you anything and does not need "the market" in order to survive.**

If adopting "autopackage" were the only thing standing between wankers like you using this OS and not using it I would make it my personal mission to kill the project dead, dead, dead.

Go back to Windows, you effin ingrate. It was those "geeks in basements" that created this fucking operating system, that support it, and that will keep it going long after you've gone back to Mild Bill's teat.[/QUOTE]
You sum up precisly the type I mean. It's a very small group, but it's there. A bunch of Mr. Knowitall's who undermine everything that people like the Ubuntu folk try to do: get Linux to the masses. 

People like you do not understand that there are people other than themselves and respond like you do, harsh words and little meaning. This is a forum and people can say what they would like to see happing. If you can't live with that, crawl back into your basement please (I permit myself this small form of retaliation in order to get the point across like I did before. You just try to be mean for no reason).

---

### Post by leech on 2005-12-16
Originally Posted by leech
Why Autopackage? There is always the Loki installer, which games have been using for years.

[QUOTE=Jengu]You're kidding, right? The loki installer isn't much more than an xdialog for copying files.[/QUOTE]

Well, uhm, that's the point isn't it?  Really, that's all a package manager does, it copies files into a location, and then keeps track of what files those are via the management tools.  

My entire point is that Autopackage should be for software that cannot be put into a repository.  For Commercial or non-open sourced licensed software.  But if it is going to become mainstream at all, it should try to work WITH the current package managers, not separately from it.

One of the other reasons that people think this is good is due to "wanting the latest software" as I said in an earlier post, most people don't update their software that often, unless there is a flashing thing telling them to update, or there are automatic updates.  Since the distributions are the ones that cover the security updates, then the users don't have to really worry about it, not to mention that Ubuntu in specific comes out every 6 months, so more than likely when a new version comes out of a piece of software it'll be in Ubuntu soon enough, and probably into backports even before that.

You say that Package managers should be in charge of 'CORE' software and Autopackage should be in charge of 'DESKTOP' software.  Well, in case you weren't aware, Ubuntu/Debian and most other distributions do have a Main section, and just because Firefox is a desktop applicaton, doesn't mean that it's not part of the Core desktop.  I know most peope consider it a requirement on most desktops.

Leech

---

### Post by jobezone on 2005-12-16
Autopackage people should just **Do IT Themselves** and prove all the rest of us wrong, by creating a distro which puts in pratice what they propose. Or not, and keep hoping that everybody else sees "the light", and do it for them.

---

### Post by jobezone on 2005-12-16
Your best bet is too look into the README.Debian text file in /usr/share/doc/mldonkey (or simillar).
EDIT: in response to using mldonkey a few posts back

---

### Post by Halvorsen on 2005-12-16
Thanks to jobzone. I'll look into mldonkey when I need to challenge my hangover tomorrow.
____________

I'm not a geek, and is often told where to be or not to be. But I'm here and hope to be useful. It's not only about programming, but also internet. If you look at the pages of [klik]("http://klik.atekon.de/"), [autopackage]("http://autopackage.org/") and [loki]("http://icculus.org/loki_faq/"), with klik you are there from the beginning. You need to run a command, but it's the first thing you see. You're into it before getting confused (klik is designed for Breezy, so I dont want to make complains about it in Dapper. If it works like expected it is a must for Linux). Autopackage has a lot of philosophie. It's interesting, but after the reading you start looking for a way to install autopackage. You cant find it, and after a while you stop reading and just start looking at the pages whitout knowing what you're looking for. The loki-sites really scares the shit out of me.

Maybe you dont see this, but I do. And maybe you can learn something by looking at the pages instead of on your own skills. It's not about 'us' and 'them'. A mom can get more out of her pictures than a professional photographer.

I'm not my mom. There are moms using the same Windows-PC for ten years. They never update. They never defragment. And they never have any problems. They use word, exel, play some music and go on internet no and then. If their kids have a schoolplay recorded on a CD, they need some help installing new codecs and so on. I think it's unfair to compare me (as a more demanding user) to this moms (and I'm sure Linus think the same way).

So far, except from klik which is not yet in Dapper, I think autopackage is the best solution. Someone mentioned Skype, but it isn't in Autopackage. If I could give an adwise to Autopackage, it would be to make a package for Skype. That would really change the point of view.

---

### Post by jdong on 2005-12-16
People interested in the autopackage concept (Windows-like software), the PQI format used by PC-BSD is a very similar concept.

Only time will tell how this'll play out, but it's nontheless interesting.

---

### Post by Halvorsen on 2005-12-16
[QUOTE=jdong]People interested in the autopackage concept (Windows-like software), the PQI format used by PC-BSD is a very similar concept.[/QUOTE]

I'm interrested. Can you be more spesific. Doing a google-search on 'PQI' isn't the easyest thing to do.

---

### Post by lithorus on 2005-12-16
Think he means PBI
[http://en.wikipedia.org/wiki/PC-BSD](http://en.wikipedia.org/wiki/PC-BSD)

---

### Post by jdong on 2005-12-16
yeah, PBI, sorry.

---

### Post by Halvorsen on 2005-12-16
Excuse me for being off topic. I use Mandriva as my second OS. All my work is copied into its home directory, in case of a serious crash with Dapper. Can I replace Mandriva with [PBI]("http://en.wikipedia.org/wiki/PC-BSD")?

---

### Post by jdong on 2005-12-16
Mandrake is a Linux distribution, while PC-BSD is a **BSD** UNIX distribution. Though very similar in the end user software choices, fundamentally they are completely different core OSes.

The same /home partition cannot be directly transplanted to a BSD system like PC-BSD, though I am willing to bet that if you tar/untar (transfer) the files over after installing PC-BSD, everything would work.


Again, understand that you will be using the FreeBSD operating system instead of Linux in PC-BSD -- a very powerful OS, but with subtle differences compared to Linux especially significant if you work below the GUI.

---

### Post by Halvorsen on 2005-12-16
Thanks for the quick reply. I'm doing my work in Dapper, and it's going well. Only once I had to move over to Mandriva. Getting information on how to copy work from Mandriva to Ubuntu wasn't as easy as the opposite. So I'll try...

---

### Post by Halvorsen on 2005-12-16
Sorry for the quick reply. The url is[ here]("http://www.pcbsd.org/")

---

### Post by poptones on 2005-12-16
*People like you do not understand that there are people other than themselves...*

Look, you... I suggest you read some of my posts here before you go casting about shit you have made up as if it were true. You know nothing of me (obviously). You know nothing of the countless posts I have made *in assistance of others who know less than me*. Not just here but at Ars and other sites and in newsgroups and mailing lists and even various support wikis. I have **trained** tech support jockeys and I run a tight ship so don't you **dare** try to pretend I do not care about others.

*A bunch of Mr. Knowitall's who undermine everything that people like the Ubuntu folk try to do: get Linux to the masses.*

It is "Mr. Knowitalls" who provide *support* for these products. Without those "mr knowitalls" taking time out of their day *writing code* to tell "people like you" for the fiftieth time how to edit their /etc/fstab file, "people like you" would not even be here because you could never have even gotten past the first geek-lingo installer screen.

I suggest you read again the "mission of ubuntu." It is **not** to provide "people like you" a free ride from windowsland. it is to provide a *completely Free solution*. That does not, in any way, mean a *sort of free solution that embraces proprietary and commercial interests*. Any considerations made in that direction are only as an aid to ease your *transition* from the land of not -  the mission is NOT to provide tools and a desktop that will **attract more proprietary software developers**. That, in fact, is 100% **against the stated mission of ubuntu**. 

Look it up.

Linux is not here to cater to a sense of *entitlement* from "people like you," who know **nothing** of the real world needs of support personnel, who insist verything in linux has to ape the most primitive, LCD desktop in the commercial marketpace simply because it somehow "needs" those users. The "open source ethos" is about *education* not pacification.

Get this through that pointy skull of yours: **linux is not a company. Linux does not need you**. If redhat wants your money then it is up to redhat to make an ass ugly, low security desktop that will appeal to your latent fanboi desires. Go run Linspire or something where the default desktop is "root" and they give you a nice and easy way to *pay for your Free software*... something that feels "home" to you.

Supporting software across multiple operating systems is a gigantic pain in the ass. Not Gateway, not dell, not even effin *Microsoft* have a single support structure for multiple versions of their own OS - if you are a corporate customer running windows 2000 you do not talk to the same people that consumers running XP home or even windows 98 are running - those calls all are directed to people with different levels and specialties of training because *the operating systems are different*. 

The world does not need a "run on any platform" packaging system because what breaks Photoshop 2010 running on Debian is not likely to be the same thing that breaks Photoshop 2010 running on Redhat or Photoshop 2010 on Mandriva.  Those support issues have to be dealt with by people who are familiar with *the operating system in use* and the best ones to do that are those who produce it.

Open source software was meant to provide an ecosystem of ideas and of tools. It was to povide those with the *talent and desire to create* a means of pooling work and sharing ideas. **Open source was never meant to provide frustrated windows users a free ride**. Developers have to earn a living and providing support is the way "we" do it. If it is up to Adobe to "publish" a version of Photoshop that runs on every mainstream distribution **and** provide support on thos distributions when something goes pop it ain't ever gonna happen because the people at Adobe don't **need** that small share of potential revenues. Redhat or Mandriva or Linspire, on the other hand, *can* provide this service because **that is their market**. If redhat or Linspire think they can attract more marketshare by providing recognized, non free, branded software on their desktops, linux provides the toolkit for them to do exactly this - it is up to them to hammer out a licensing deal with those non-free OEMs that will attract more *people like you* on their desktops. Just be aware this does not mean because Linspire may provide you with Photoshop that you somehow then have the "right" to run Photoshop on your copy of Ubuntu - if you want **non-free and proprietary** you accept the baggage it brings. 

If you want to be able to run Photoshop on Ubuntu, start a thread about it. Write Mark Shuttleworth - believe it or not he will respond (I know because he has done so with me).  Write the folks at Linspire and urge them to license the code from Adobe so they can provide you with a software brand you recognize. Linspire already has many **non free, commercial** packages in their "click and run" repository, there's no reason any other distribution (even Canonical) cannot do the same.

---

### Post by Halvorsen on 2005-12-16
Well, whois the one and only to get a free ride - you?

---

### Post by poofyhairguy on 2005-12-16
[QUOTE=Jengu]
That's funny, the one OO2 binary seems to run on Windows98, Windows ME, Windows 2000, Windows XP...[/QUOTE]


Apples and Oranges.

> 
The point is -- for most linux distro differences -- desktop users just don't give a damn.

And most Linux distros are not for desktop users.

> 
 Having a slightly different naming scheme for the file layout for example, doesn't justify a new distro. That just leads to stupid duplication of work. No one **cares** if fonts are in /usr/fonts or /usr/share/fonts, so long as the location is consistent. But a lot of the differences between distros is dumb stuff like that still.

Maybe, but nothing can prevent people from forking the distros in that way, so its a moot point. Back to autopackage.

> 
Wrong. Alien converts *already compiled* packages to different formats. It's an attempt to make them usable across different distros *with no intervention from the developer*. Autopackage, however, requires developers' intervention in order to work. A few source changes, and autopackage takes care of ABI issues for you. Alien doesn't do that at all. Go look at the reams of documentation on binary compatibility they have on their site. Hell, just look at the frontpage, that brags that 1.0 can handle mplayer. Tried running alien on mplayer? I did -- segfaults and makes my terminal unresponsive everytime a video ends.

The fun with Alien is trying every RPM of that program you can get your hands on (Fedora, Mandrake, SUSE) till one magically works. I get your point- Autopackage does try to do more.

> 
Well, as long as distributions spend tons and tons of time packaging desktop software independently, time that could be spent hacking on something useful, encouraging distros to take a closer look at autopackage makes sense. 

Then it should also make sense when they say no because "it does not work well enough for us."  And its not time "wasted" packaging- who knows if that time would go to something "useful." Thats a logical fallacy.

If Autopackage is soooooo great for all desktop apps, then where is the magical page that has more Autopackages than debian files in the Ubuntu universe? No where? Thats what I thought. And don't say "it wouldn't be that way if all the distros would support it." It must prove its worth first and do what everyone asks- work with the native package managers. It will someday, and maybe THEN some distro can consider using it "officially" (but probably never Ubuntu as it is died to the Debian way, sink or swim).

> 
That's funny, I used gentoo for over a year and found software that wasn't in portage all the time. Did I mention they're about 4 versions behind stable wine? That QT4 is just making it in now? That they didn't update Python for **ages**?

Fine, then run Debian experimental. Or Arch. 

Not good enough? Then compile your own programs. Not good enough? Then install an Autopackage for you program. Autopackage doesn't exist? Then I guess its no better than Gentoo or Ubuntu for getting out new software.

You are pretending that it can change the Linux Desktop landscape, but unless you haven't noticed it can't yet (not developed enough- does not work with native package manager) and even if it could it would lack the support of big players for political reasons (aka Red Hat would hate 3rd party Autopackages because now people are forced to use the enterprise version of their software in order to have support for many high end pieces of closed software- Oracle for one).

> 
Do you really think that as someone willing to install a desktop linux distro in its current state, post on that linux distributions forum, and argue over linux packaging mechanisms that you and your friends somehow represent the average user? We're all geeks here :cool: 

Later today I plan to give an Ubuntu CD to a friend of mine that is an "average user." With my help he bought a new computer that is 100% Linux compatible and he will install it for the first time himself. He does not care about new software (the every six months upgrade are a little much for him), he does not care about going on the internet and installing new programs he finds. He wants a stable, easy to use system. And he has what he wants.

Only geeks go on the internet to find new software and download it. My mom has been using the old version of Windows' Firefox for months. Why? Cause I'm not there to upgrade it. But its so easy to do, with the little icon to help her! Sure, but she does not care. Normal users do not care about new software- they care that the software they have works. Thats it. Firefox 1.02 works for her, so leave it at that she says.

Only geeks care about having the newest software within six months of it coming out. Those geeks come in two categories- middle road users and hard cores. The hardcore can compile their own programs- they prefer to. The middle of the road geeks are the ones you hear complaining about the lack of a universal GUI installer for Linux because unlike the supergeeks (who know that its partially a pipe dream) and the normal users (who don't care about having the newest software) they are duped into believing Desktop Linux is one thing. Its not- each distro is its own OS that might as well be a bunch of BSDs or BeOses for how different there are. If a magical bridge connects the big five distros on the desktop, then the sacrifices it must make will make it less suitable as each distros main program package manager so none will support it. I hate to sound like a negative person but thats the way it is. No middle of the road geeks who can't code demanding that Desktop Linux change to be like the Windows they know well is going to change that.

Autopackage works best as an installer for third party software made by those who don't want others packaging their software. And for that it does the job better than anything before it. But its not a magic bullet- a bridge between all distros. If what you demand from Desktop Linux is a cross distro installer or else, then have fun with your Intel Mac next year.

> 
People will switch over the right applications. Think about how many computers Apple has sold because of the iPod/iTunes.

Ipods-yes! iTunes- no! The only people I know that go on and on about iTunes is Apple fans. The rest of us steal all the music we want and use iTunes as the bridge between Kazaa and our shiny iPods. GTKPod does the same job, as does Ephpod.

> 
All that said, do I think autopackage is the bees knees? No. But is it incredibly clear that half the people here are against it because they either don't know what they're talking about, haven't read the FAQ, are prejudiced because ubuntu doesn't follow the autopackage way, or are snotty geeks who think that only they and their equally full of free time brethren should be able to use computers? Yes.

Using a computer is far different from being able to upgrade the software for any part of a computer on a whim. I can't do that with my cell phone (upgrade, say, its web browser) without trouble so why should I expect more from a PC? Before you say they are different, to many (most) they are both just tools. Same rules apply for everyone not a geek.

> 
Cmon. When the real whiz bang solution does come around, at this rate, no one is going to recognize it. Instead we'll all throw stones at it because it's new.

It will deserve every stone thrown. A solution is not a solution till it can take the worst of the communities insults and move forward.

---

### Post by poptones on 2005-12-16
*Well, whois the one and only to get a free ride - you?*

You have 32 posts here: how many people have you helped? How many docs have you contributed to? How many patches have you submitted? How many projects have you worked on? How many hours have you spent *learning* to do these things?

Now, *who's* getting the free ride here?

---

### Post by aysiu on 2005-12-16
[QUOTE=poofyhairguy]
Only geeks go on the internet to find new software and download it. My mom has been using the old version of Windows' Firefox for months. Why? Cause I'm not there to upgrade it. But its so easy to do, with the little icon to help her! Sure, but she does not care. Normal users do not care about new software- they care that the software they have works. Thats it. Firefox 1.02 works for her, so leave it at that she says.

Only geeks care about having the newest software within six months of it coming out. Those geeks come in two categories- middle road users and hard cores. The hardcore can compile their own programs- they prefer to. The middle of the road geeks are the ones you hear complaining about the lack of a universal GUI installer for Linux because unlike the supergeeks (who know that its partially a pipe dream) and the normal users (who don't care about having the newest software) they are duped into believing Desktop Linux is one thing.[/quote] Bravo, Poofyhairguy! I'm glad someone else noticed this, too. All these supposed middle users trying to speak on behalf of the "average" user when the average user almost never updates software or installs software. I installed Firefox on more than half of the computers in my office over the past year, and each and every one of them is on the same version I installed in the first place (be it 0.9 or 1.0.2 or 1.0.4 or 1.0.6).

People just don't bother to tweak. Real ordinary users don't. They don't install programs. They don't update programs. Hell, they don't even read. I've seen people get annoyed at Clippy and not even bother to check the "hide assistant" button or to look for that option. They just make a face.

Maybe not having easier ways to install up-to-date versions of applications is a valid complaint, but no one should pretend it's the complaint of "average" users. It's middle users all the way--Windows-savvy users but not computer experts.

> 
Ipods-yes! iTunes- no! The only people I know that go on and on about iTunes is Apple fans. The rest of us steal all the music we want and use iTunes as the bridge between Kazaa and our shiny iPods. GTKPod does the same job, as does Ephpod. I happen to like iTunes not for the music store but for its organization and interface. Maybe I'm alone in that. I don't know.

---

### Post by poofyhairguy on 2005-12-16
[QUOTE=aysiu]
 I happen to like iTunes not for the music store but for its organization and interface. Maybe I'm alone in that. I don't know.[/QUOTE]

You are not. I was purposefully overgeneralizing. My mom likes the iTunes store as well. My point (not well made obviously) is that the style of the iPods and the fact that they do well at playing normal MP3s is what has lead to their popularity. Not to offend you, but I bet if you did a poll of those who actually buy songs from iTunes the average age would be in the 30's. People my age (who have iPods comming out the wazoo) use them as devices to play back stolen songs. My market is what originally drove the iPods popularity to the point that people like my mom heard of it and wanted one which has driven Apple's name to a popular standpoint where their computers are relevent again.

And just to slam home another point- yes my mom uses iTunes, but she does not have the newest version of that either!

---

### Post by aysiu on 2005-12-16
I updated my wife's iTunes to the latest version, and she hates it! The new interface has some bad visual transitions between iTunes window components. Oh, well.

---

### Post by Knomefan on 2005-12-16
Ahhhhhhhhhh
/me sits back and enjoys the popcorn

What would the ubuntuforums be without the usual autopackage flamefest?
After all, we always learn interesting things here, don't we?

For example I'm always amazed to learn what Linux and Open Source are _really_ all about. One of my favorites.

Another classic is people knowing for _certain_ that it is their pet peeve, and their pet peeve alone that is responsible for Linux not being a success on the desktop. (And I'm also always amazed to learn that it isn't a success, but then again, what do I know)

Throw in the usual "how many post do you have sir and how can you dare to critisize me???1111!!!1" and we sure are in for a wild ride. Simply great!

Anyway, to get away from the general observations and back on topic, I think autopackage and klik address a real need. I don't think it is the need most people mention here, that is being able to easily install newer software, I think they address a problem facing many open source devs: How to provide a package for as many people as possible? 

I think this is a real problem, especially if you want people to be able to test your app in order to improve it and at least klik was specifically developed to address this very issue.

Now, if autopackage or klik are the right answer to this problem, I honestly don't know. Personally, I find the klik solution much more endearing as it is a lot less intrusive on the system than autopackage is and though I know the reason for doing it, I really don't like a system that installs stuff in /usr.

---

### Post by poofyhairguy on 2005-12-16
[QUOTE=Knomefan]Ahhhhhhhhhh
/me sits back and enjoys the popcorn

What would the ubuntuforums be without the usual autopackage flamefest?
After all, we always learn interesting things here, don't we?
[/QUOTE]

That is true. Last time I learned about hard links for packages. Oh, and I learned why Kubuntu is different from every KDE distro out there almost. Mr. Hearn is a wealth of knowledge.

---

### Post by Halvorsen on 2005-12-16
[QUOTE=poptones]*Well, whois the one and only to get a free ride - you?*

You have 32 posts here: how many people have you helped? How many docs have you contributed to? How many patches have you submitted? How many projects have you worked on? How many hours have you spent *learning* to do these things?

Now, *who's* getting the free ride here?[/QUOTE]

As I've been told, a millionaire from South Africa is supporting Ubuntu. Where did he get the money from? From poor people?

 Think about this: There was an old dad. He lost his wife. He got lonesome and needed a hobby. He bougth a camera and a PC and a scanner. He used the PC to have contact with his children and grandchildren. One day he got to know the program 'photomagic' and the universe of computing was opened up for him.

To place myself on the map, altough I'm not running Windows anymore, I'm helping out a lot of Windows-people, on all levels. It might be an argument in exel or a simpel question. And I cannot tell the person calling every other day, that "you're an idiot, I've told you this ten or more times before, and now you should sell your PC." I dont have a license to drive. That dont mean I should walk. 

popotones, you dont place yourself in this community, but above it.

---

### Post by poptones on 2005-12-16
*How to provide a package for as many people as possible? *

Make a piece of software that is robust; reliable; not brittle; trustworthy; user and support friendly - or at least one that is sort of these things and that fulfills a need. And make it open source.

if you do that then "the community" will do the rest for you. And yes, *that is what Free software is about.*

---

### Post by leech on 2005-12-16
[QUOTE=Knomefan]Ahhhhhhhhhh
/me sits back and enjoys the popcorn

What would the ubuntuforums be without the usual autopackage flamefest?
After all, we always learn interesting things here, don't we?

For example I'm always amazed to learn what Linux and Open Source are _really_ all about. One of my favorites.

Another classic is people knowing for _certain_ that it is their pet peeve, and their pet peeve alone that is responsible for Linux not being a success on the desktop. (And I'm also always amazed to learn that it isn't a success, but then again, what do I know)

Throw in the usual "how many post do you have sir and how can you dare to critisize me???1111!!!1" and we sure are in for a wild ride. Simply great!

Anyway, to get away from the general observations and back on topic, I think autopackage and klik address a real need. I don't think it is the need most people mention here, that is being able to easily install newer software, I think they address a problem facing many open source devs: How to provide a package for as many people as possible? 

I think this is a real problem, especially if you want people to be able to test your app in order to improve it and at least klik was specifically developed to address this very issue.

Now, if autopackage or klik are the right answer to this problem, I honestly don't know. Personally, I find the klik solution much more endearing as it is a lot less intrusive on the system than autopackage is and though I know the reason for doing it, I really don't like a system that installs stuff in /usr.[/QUOTE]

I have to agree with every single point here :D  It's been pointed out twice that I should read the faq about why they put the software in /usr and I even once said why it's a bad idea.  The fact is that ALL distributions I have ever used (and that is a LOT) put any program that is compiled by the local admin into /usr/local.  Hell, anyone who has ever used OpenBSD knows that the package manager that it uses puts everything in /usr/local as well.  For those that haven't ever used OpenBSD, their secret to having the most secure operating system?  NO SOFTWARE is installed by default.  I've used Debian for years, and it's less sparse than an install of OpenBSD.  

Autopackage says that they had issues with just using /usr/local.... well, that's what symlinks are for.  

Someone above mentioned PC-BSD, I played around with it a little bit, and the so called package management of it tries to be much like Mac OS X (just extracts the tarball into the users home directory and runs it from there).  Nice idea if you're the only one who uses the computer, but if there are multiple users, you're going to have multiple copies of the same software.  Other than that, it is a pretty nice system.

As I've said before in this thread, Autopackage should be for commercial packages.  It isn't a waste of time for people to package the software they like for their distribution, because a lot of packagers aren't the developers themselves, not to mention it doesn't require programming to be able to make a package.  Pretty much anyone, if they want to help a project, can volunteer to make packages for their favorite distributions.  For the most part, it's a pretty automated process, once the initial work is done.  You may have to tweak dependencies occasionally, but that's about it.

Leech

---

### Post by leech on 2005-12-16
[QUOTE=poptones]*How to provide a package for as many people as possible? *

Make a piece of software that is robust; reliable; not brittle; trustworthy; user and support friendly - or at least one that is sort of these things and that fulfills a need. And make it open source.

if you do that then "the community" will do the rest for you. And yes, *that is what Free software is about.*[/QUOTE]

How odd, you posted this right at the same time I was writing basically the same thing :D  And it's true, as long as it's open source, and worthwhile, someone in the community will package it.  How else is there 15,000+ packages in Debian/Ubuntu.  Especially considering Debian is a completely volunteer project.

Leech

---

### Post by poptones on 2005-12-16
> As I've been told, a millionaire from South Africa is supporting Ubuntu. 

Shuttleworth has put a lot into ubuntu, but where did ubuntu come from? And who answers the support questions? I wonder how many people in this support forum have ever picked up the phone and *paid Canonical for an answer to a problem*.

Unless you do that, where do you get your help?

From "geeks in basements." 

It is this slap in the face of *the community* that pisses me off. Why the hell should I (or you) help a person who looks down their nose at the people they are asking for help?

*popotones, you dont place yourself in this community, but above it.*

Again, you make up "facts." I suggest (again) you actually do some reading before claiming to "know" the first thing about me.

---

### Post by Knomefan on 2005-12-16
> **poptones]
Make a piece of software that is robust said:**
> 
Hm, isn't it one advantage of free software that people are able to freely use your program and find bugs, etc., so that the program becomes more robust and reliable, etc. in the process of people using it?

[QUOTE=poptones]
if you do that then "the community" will do the rest for you. And yes, *that is what Free software is about.*
What is? Making robust and reliable software?
The community?
Having the community do the rest for you?
Honestly, while free software might be mainly about freedom, open source on the other hand is about a lot of things, not just one thing. How about it is [ just for fun? ]("http://www.amazon.com/gp/product/0066620732/qid=1134768338/sr=8-1/ref=sr_8_xs_ap_i1_xgl14/002-0143382-5348021?n=507846&s=books&v=glance")

---

### Post by scaine on 2005-12-16
Heheh.  Knomefan sums it up perfectly, I reckon.  You gotta love these threads.

Poptones - I like you.  You cut through the crap (usually),  but your posts over the last few days (in varoius threads) have been breathtakingly superior.  You obviously know what you're talking about but your tone is so condecending at times that nobody wants to *be* helped by you.  I wish you'd drop the "you only have xx posts" arguments too - take a wee peek at tomwell's profile to see how relevant that argument is.  Sorry to have a pop (poor choice of words maybe) at you, but I wish you'd chill a bit.

To get back on topic - I don't enough about autopackage to comment on its merits directly, but I do think that Ubuntu needs someway of installing packages easily that aren't in the repos.  It's very annoying when you find something on gnomefiles that you'd like to try and there's just this tar.gz file staring at you once you've downloaded.  I've got a background in programming and decades of experience in computers but I've rarely had success installing anything when it needs compiled.

Maybe this front end for dpkg that I've been hearing about (can't remember what's called - something like g-dpkg?) will help out some, but unless people start offering deb files for install (which is rare - it's usually rpms you get offered), then there will a few disappointed Ubuntu noobs.

And although you might ask if that's too big a deal, if Shuttleworth thinks that Ubuntu is going to give Vista (or Mac come to that) a scare, then there needs to be some way of standardising this stuff.

Of course, my biggest worry if it *is* standardised would be that LInux would become a haven for spyware in the same way that Windows has become.

---

### Post by leech on 2005-12-16
[QUOTE=Knomefan]Hm, isn't it one advantage of free software that people are able to freely use your program and find bugs, etc., so that the program becomes more robust and reliable, etc. in the process of people using it?[/quote]

The double-edged sword, your program has to at least be initially useful, then people will start using it, and reporting bugs and requesting features, which you add, then test (and have the people who are crazy enough to try the cvs stuff) then release, process continues on and on.  So otherwise, yes. :D

> What is? Making robust and reliable software?
The community?
Having the community do the rest for you?
Honestly, while free software might be mainly about freedom, open source on the other hand is about a lot of things, not just one thing. How about it is [ just for fun? ]("http://www.amazon.com/gp/product/0066620732/qid=1134768338/sr=8-1/ref=sr_8_xs_ap_i1_xgl14/002-0143382-5348021?n=507846&s=books&v=glance")

I think he specifically was talking about the community creating a package out of the program.  So otherwise Developer creates the program, then someone who enjoys the program creates the package for it, then either uploads it to the forum, hosts it on their personal site, or tries to get it into the distribution they use.

Leech

---

### Post by poptones on 2005-12-16
*I wish you'd drop the "you only have xx posts" arguments too*

Why? it is not a pissing contest. It is about someone claiming another to have "a free ride" when they know **nothing at all** about that person. If my comments along this line were ironic that only **better makes the goddamned point**. 

"Free software" is **not** a free ride unless your only measure of merit is economic. And if **that** is your standard of measure then why are you even here? Why the hell aren't you using the clearly "superior" WINDOWS?

---

### Post by Halvorsen on 2005-12-16
[QUOTE=Halvorsen]As I've been told, a millionaire from South Africa is supporting Ubuntu. Where did he get the money from? From poor people?[/QUOTE]

This is a question no one want to answer. Is the money for you geeks, or us, including the poor people, who never touched a PC?

popone removed the question, but it is there. Isn't it?

---

### Post by scaine on 2005-12-16
There are two reasons I'm here :

1.  Microsoft launched the "Genuine Advantage" program and claimed that I couldn't use the XP license code from a Dell PC that we bought at work, even though we bought those PCs with XP on them for convenience and actually re-image them with Windows 2000 which we also had to purchase from Microsoft.  That annoyed me, because we're basically paying two licenses and unless we dropped Dell, that would remain the case.  When they enforced the license through the  "Geniune Advantage", I decided I'd had enough and started playing about with various distros.

2.  Windows bores me now.  I'm forced to use it at work and the standardised desktops we enforce don't allow much customisation.  When I saw that the linux desktop wasn't actually all that far behind Windows, I decided to give it a whirl.

I genuinely believe that the linux desktop will surpass Windows in a couple of years.  Not market share (obviously), but in terms of features and applications.  And when it does, the snowball will have started rolling.  And that will mean more linux and therefore Ubuntu users.  And one of the first things they'll say is, "So how do I install this Skype thing on linux".

Or whatever.  But we'll need some way of letting these total amateurs install proprietary software.

Hell, if it wasn't for Automatix, I'd still be having headaches over Java 1.5...

---

### Post by Knomefan on 2005-12-16
[QUOTE=Halvorsen]This is a question no one want to answer. Is it for you geeks, or us, including the poor people, who never touched a PC?
[/QUOTE]
Though I really fail to see what the purpose of this question is and I have a really hard time to see the relation with autopackage and its merits or problems:

> Mark Shuttleworth (born 18 September 1973 in Welkom, Free State) is a South African entrepreneur. As an early space tourist, he was the first African [1] in space.

After going to school at Diocesan College, Shuttleworth obtained a Business Science degree in Finance and Information Systems at the University of Cape Town.

In 1995, he founded Thawte, which specialised in digital certificates and internet security. He sold Thawte in December 1999 to VeriSign, and subsequently formed HBD Venture Capital, a business incubator and venture capital provider, and the Shuttleworth Foundation, a non-profit organisation dedicated to social innovation which also funds educational and open source projects in South Africa, such as The Freedom Toaster.

Shuttleworth gained worldwide fame on 25 April 2002 as a civilian cosmonaut aboard the Russian Soyuz TM-34 mission, paying approximately US$ 20 million. Two days later, the Soyuz spacecraft arrived at the International Space Station, where he spent eight days, participating in experiments related to AIDS and genome research. On 5 May, he returned to Earth. In order to participate on the flight, Shuttleworth had to undergo one year of training and preparation, including seven months which he spent in Star City, Moscow.

He participated as a Debian developer since the early 1990s, and in 2004 he returned to the Linux world by funding the development of Ubuntu Linux, a user-friendly version of Linux, through his company Canonical Ltd. In 2005 he founded the Ubuntu Foundation and made an initial investment of 10 million dollars. The foundation is used to pay Ubuntu contributors. In September of 2005, he purchased a 65% stake of ImpiLinux. [2]

Mark Shuttleworth currently lives in London.
[http://en.wikipedia.org/wiki/Mark_Shuttleworth](http://en.wikipedia.org/wiki/Mark_Shuttleworth)

---

### Post by leech on 2005-12-16
[QUOTE=scaine]To get back on topic - I don't enough about autopackage to comment on its merits directly, but I do think that Ubuntu needs someway of installing packages easily that aren't in the repos.  It's very annoying when you find something on gnomefiles that you'd like to try and there's just this tar.gz file staring at you once you've downloaded.  I've got a background in programming and decades of experience in computers but I've rarely had success installing anything when it needs compiled.

Maybe this front end for dpkg that I've been hearing about (can't remember what's called - something like g-dpkg?) will help out some, but unless people start offering deb files for install (which is rare - it's usually rpms you get offered), then there will a few disappointed Ubuntu noobs.

And although you might ask if that's too big a deal, if Shuttleworth thinks that Ubuntu is going to give Vista (or Mac come to that) a scare, then there needs to be some way of standardising this stuff.

Of course, my biggest worry if it *is* standardised would be that LInux would become a haven for spyware in the same way that Windows has become.[/QUOTE]

Actually this gives me an idea, though I'm not sure if this is already included in the feature list, but the program you're talking about is gdebi, and I was thinking that maybe if gdebi included a frontend to alien to convert packages, that would make at least some people happy.  The problem I have with all of this is that people will start doing things the 'Windows way' and installing all sorts of stuff that is already packaged for Ubuntu.

The thing about Autopackage if you really think about it... it's a support nightmare!  Just as Windows is.  For example, if you install something from Autopackage that is already packaged inside of Ubuntu, and you have to ask for support from whoever you get support from.  The person you ask will not know what package you have installed, or what version you are running.

At least if someone says "I'm running Ubuntu Breezy, and I'm having this problem with <insert program here>" you'll know to ask if they've installed all updates, and if they have, you'll know exactly what version that is installed, you'd be able to look at the bugzilla for it and see if the bug is already in there, and if not you can have the person having the problem submit a bug, or get the information from them to submit it yourself.  

Here is a good example of why Autopackage would be bad.  Let's say the subject is running Breezy, someone else on his computer installs firefox via autopackage.  Suddenly he's having a problem with it.  He doesn't know about the autopackage program, so the person helping him asks if he has done the updates, he says yes, so support guru looks at that version, and tries out the same thing the user having the problem is reporting.  Hmm, no problem there.  So he tells this user to do a 'dpkg -l firefox' and he tells him the version he has is 1.0.7-0ubuntu20.  At this point the only way to tell what version is installed is by clicking the help -> about in Firefox itself.  But of course if Firefox isn't loading, then the only way to even test this would be to wipe out the users .mozilla directory (making a backup of the bookmarks first of course) then trying to see if Firefox will load.  If it does, it could have been a user installed extension, in which case the user will have to re-install all those extensions.

This is pretty much a support nightmare.  Now on the otherhand, I think Autopackage is good for commercial apps that will never be packaged anyhow, as long as it keeps track of what it has installed, (for easy removal) and it does it unobtrusively (uses ld_preload or in generall does not break the libraries that are already installed)

Leech

---

### Post by scaine on 2005-12-16
[QUOTE=leech]
This is pretty much a support nightmare.  Now on the otherhand, I think Autopackage is good for commercial apps that will never be packaged anyhow, as long as it keeps track of what it has installed, (for easy removal) and it does it unobtrusively (uses ld_preload or in generall does not break the libraries that are already installed)
Leech[/QUOTE]

Exactly - you've nailed it.  This *must* be a program that only handles packages that will *never* be in the repos.  Possibly due to their license, for example.

There is a ton of files on gnomefiles that I just won't go near because I hit massive (and to me very confusing) compile errors.  Been a while since I tried one to be honest, but I'm lazy that way - I'm just not inclined to learn more and find out how to compile... it's been far, far too long since I did any programming.

I know that sounds lame, considering that most compile instructions are just like "configure, make and make install", but I'm telling you - I've *never* had a program to compile on my system.  There's always some kind of error.

You might be onto something with the alien inclusion on the gdebi tool though.

---

### Post by Halvorsen on 2005-12-16
"He participated as a Debian developer since the early 1990s, and in 2004 he returned to the Linux world by funding the development of Ubuntu Linux, a user-friendly version of Linux"

Not the ten million I guess, but the geek solution?

---

### Post by Breepee on 2005-12-16
[QUOTE=poptones]*I wish you'd drop the "you only have xx posts" arguments too*

Why? it is not a pissing contest. It is about someone claiming another to have "a free ride" when they know **nothing at all** about that person. If my comments along this line were ironic that only **better makes the goddamned point**. 

"Free software" is **not** a free ride unless your only measure of merit is economic. And if **that** is your standard of measure then why are you even here? Why the hell aren't you using the clearly "superior" WINDOWS?[/QUOTE]
I see that discussing with you in a civilized manner without using bad language  is just not possible. Perhaps you're trying to make up for a lack of meaning? I almost can't read beyond your little insults and annoyances. Don't you have other hobbies besides cluttering up webforums?
 
There's a difference in being a helpdesk/creating software solutions and being a dictator. I argue that some people (you included) are trying to be the last, but say they are the first.

Make no mistake, I'm happy with every bit of support for Linux, and that includes geeks in basements, but some just lost it and think they need to dictate what and how people should do (with their computers). I say that's stupid, pointless and totally besides idea behind Ubuntu.

By the way, this thread was about autopackage. I hope this useless flame can stop.

I totally agree with scaine. He's stated (besides commerical software) a possible target for autopackage.

---

### Post by scaine on 2005-12-16
[QUOTE=Breepee]
By the way, this thread was about autopackage. I hope this useless flame can stop.
[/QUOTE]

Heheh.  We were back on topic for a while there too... ;) 

Rise above it Poptones - you have nothing to prove.  Be the bigger person here.

Seriously, I'm unsubscribing from this thread.  I think everything's been said that needs to as far as autopackage is concerned.  I'm looking forward to how gdebi sizes up against autopackage and klik.

Me?  I'll stick with the repos.  I trust them for now and despite all my whining about the gnomefiles stuff and my total inability to compile even the simplest programs, I have no real complaints.  The backport team do a fantasic job at getting the good stuff out on time (thanks jdong and the rest) and that's good enough for me.

---

### Post by poptones on 2005-12-16
> **Breepee]I see that discussing with you in a civilized manner without using bad language  is just not possible.[/quote]

"Bad language?" Would you prefer Russian? Farsi? French? I am using **fine** language said:**
> There's a difference in being a helpdesk/creating software solutions and being a dictator.

No, there isn't. When a client ("like you") calls on the phone and then tries to tell *the technician they are asking for help* how things work, **you have to be a dictator**. If you do not take charge of the conversation - even if that means slapping the person in the face by reminding them, in no uncertain terms, they are the one **asking for help**, then you accomplish nothing but wasting a bunch of time on a call that ends with no resolution.

If you are not a "dictator" regarding *allowable support options* you can never accomplish anything - and the merest act of "trying" to help that person can end up in **the person in charge** causing the person asking for help to obliterate irreplaceable data or even physically damage their machine. You may have no objection to destroying your machine, but you have no right to obligate others to you in that very stupid quest.

> ...some just lost it and think they need to dictate what and how people should do (with their computers). I say that's stupid, pointless and totally besides idea behind Ubuntu.

I am not telling you what you *may* do with your computer - no one can. If you want to run the very latest software **learn to drive a fucking compiler**. That, my friend, is freedom. What you are advocating is not *freedom* at all, but *entitlement*: You have the "right" to do absolutely anything you want with your computer but absoltely no obligation to *actually contribute to that end*. 

Look at this forum itself: do you see the *separate sections* for Warty, Breezy, Dapper, Hoary? Have you ever considered, for even a second, that is because *these are all different operating systems, each with their own support needs?* It is naive to argue "a distribution agnostic installer will be good for everyone"  - and it is *stupidity* to keep arguing that when it has been shown, by *many who know more than you*, why that argument is utterly false. 

If you have a python application, it is going to have dependancies. If you have a mono application, it will have dependancies. If you have a GTK application, it will have dependancies. Resolving these dependancies among - literally - *hundreds* of unique configurations is a support nightmare. This is *why you choose a distribution*. If your distribution is not meeting your needs, choose another - or better still, form your own. Then YOU can be the person everyone screams at when your installer chews through their existing partitions and obliterates their baby pictures and their porn collection; YOU can be the person who has to figure out why the latest CVS of Mozilla keeps crashing your defaul install and causing your "customers" to fill your support forum with flames.

You want freedom? Learn to do this stuff yourself. Ironically, if you succeed in that you will come to realize *"they" were right all along*.

---

### Post by Jengu on 2005-12-16
> **poptones]
I suggest you read again the "mission of ubuntu." It is **not** to provide "people like you" a free ride from windowsland. it is to provide a *completely Free solution*. That does not, in any way, mean a *sort of free solution that embraces proprietary and commercial interests*. Any considerations made in that direction are only as an aid to ease your *transition* from the land of not -  the mission is NOT to provide tools and a desktop that will **attract more proprietary software developers**. That, in fact, is 100% **against the stated mission of ubuntu**. 
[/quote]

Hopefully part of the ultimate mission of the free software movement in general as well as Ubuntu is to convert them if possible. Which means reeling them in.

> 
Linux is not here to cater to a sense of *entitlement* from "people like you," who know **nothing** of the real world needs of support personnel, who insist verything in linux has to ape the most primitive, LCD desktop in the commercial marketpace simply because it somehow "needs" those users. The "open source ethos" is about *education* not pacification.


Yes but 99% of the time this "education" is learning how to edit a dozen types of config files because they're not formatted consistently. Sure, I'm being "educated" by doing this in the sense that I now know how to edit /etc/fstab, /etc/X11/xorg.conf, etc. but have I really **learned** anything? No. I've learned a few ridiculously specialized skills, probably time better spent thinking about real problems.

> Get this through that pointy skull of yours: **linux is not a company. Linux does not need you**. If redhat wants your money then it is up to redhat to make an ass ugly, low security desktop that will appeal to your latent fanboi desires. Go run Linspire or something where the default desktop is "root" and they give you a nice and easy way to *pay for your Free software*... something that feels "home" to you.

It doesn't "need" mass users perhaps, but it really is **in my self interest**, and probably good for the **linux community as a whole** for it to get mass users. Because if it gets mass users than maybe driver developers will get onboard. Because then maybe distro maintainers will be able to afford to hire more people to add polish. Because then maybe Linux will rock just that much more.

> The world does not need a "run on any platform" packaging system because what breaks Photoshop 2010 running on Debian is not likely to be the same thing that breaks Photoshop 2010 running on Redhat or Photoshop 2010 on Mandriva.

But the issue here is that Mandriva and Debian and Redhat are not really that significantly different a platform. What I look forward to is the day that if Photoshop 2010 breaks on Redhat, that *it is considered a Redhat bug* because they've deviated from something like the LSB somewhere. Nowdays open source project changelogs have stuff all the time like "Bug fix to make work on Debian," "configure hack to compile on Fedora," etc.

> 
Open source software was meant to provide an ecosystem of ideas and of tools. It was to povide those with the *talent and desire to create* a means of pooling work and sharing ideas. **Open source was never meant to provide frustrated windows users a free ride**. Developers have to earn a living and providing support is the way "we" do it. If it is up to Adobe to "publish" a version of Photoshop that runs on every mainstream distribution **and** provide support on thos distributions when something goes pop it ain't ever gonna happen because the people at Adobe don't **need** that small share of potential revenues. Redhat or Mandriva or Linspire, on the other hand, *can* provide this service because **that is their market**. If redhat or Linspire think they can attract more marketshare by providing recognized, non free, branded software on their desktops, linux provides the toolkit for them to do exactly this - it is up to them to hammer out a licensing deal with those non-free OEMs that will attract more *people like you* on their desktops. Just be aware this does not mean because Linspire may provide you with Photoshop that you somehow then have the "right" to run Photoshop on your copy of Ubuntu - if you want **non-free and proprietary** you accept the baggage it brings.


I'm not sure if you're trying to argue against autopackage here or more generally against my claim that we *need*, or at least, *should want* closed source developers. As an argument against autopackage it doesn't make any sense because autopackage is equally useful for packaging closed source software. The closed source point I think I answered above.

[QUOTE=poofyhairguy]
And most Linux distros are not for desktop users.
[/quote]

Perhaps you would like to reread the title of the thread...

> 
Maybe, but nothing can prevent people from forking the distros in that way, so its a moot point. Back to autopackage.


Actually they can. Literally they can't sure, they can't pass an amendment to the GPL or something, but for all practical purposes they can. When the major distros (Redhat, SuSE, Mandrake, Ubuntu) agree and conform to something, other distros will follow out of **self interest**. Why put fonts in a different place when it's going to make converting packages harder?

> 
And its not time "wasted" packaging- who knows if that time would go to something "useful." Thats a logical fallacy.


Well, time or money. Maybe I just have more faith in Mark's ability to find worthwhile projects for Canonical's surplus dollars  said:**
> 
Fine, then run Debian experimental. Or Arch. 


Debian experimental isn't whole inclusive either. And Arch has a really poor package selection. The point is -- repositories can never include all software and be simultaneously up to date. Out of the 7 or 8 distros I've tried, gentoo was best about Selection*Recentness, and that's probably in part due to them not having to compile packages before uploading them ;P

> 
Only geeks go on the internet to find new software and download it. My mom has been using the old version of Windows' Firefox for months. Why? Cause I'm not there to upgrade it. But its so easy to do, with the little icon to help her! Sure, but she does not care. Normal users do not care about new software- they care that the software they have works. Thats it. Firefox 1.02 works for her, so leave it at that she says.


Eh, that's not quite true. I've seen quite a few people download and install aim or itunes. "Geekiness" is a gradient. Your mom is probably at the other extreme.

> 
No middle of the road geeks who can't code demanding that Desktop Linux change to be like the Windows they know well is going to change that.


Yeah, I must be one of those middle of the road ones. My post count on gentoo.org is nothing to sneer at. My job is to code a crossplatform project in C++. I read the wine-devel, python, and kde usability (!!) mailing lists. I'm writing this under X.org 6.9 RC1. In my spare time I'm reverse engineering the level format for an old game so I can reimplement it in python so it'll be crossplatform but still compatible with the old levels. I read the kernel changelogs.

I understand the mentality that different distros are totally different OSs. But I think that's a bad perception to work under, at least for the desktop. I think it makes sense for their to be different distros aimed at different purposes. A distro aimed at servers wouldn't put the preemption patches in their kernel for example. Distros may also come with a different set of default software installed. Different architectures maybe targeted.

BUT -- desktops are only going to have one architecture: x86 (Apple is converting, so PPC will soon die off desktop wise). None of the distros are going to rip out Xorg and put in their own alternative. All of them are going to include the kernel, glibc, libstdc++, etc. I view different desktop distros as something less than an entirely different OS. Even whether or not certain libs is included out of the box isn't a good separator, because any distro worth it's salt is going to provide a way to get libs that weren't included on install (apt, yum, emerge, whatever).


> It will deserve every stone thrown. A solution is not a solution till it can take the worst of the communities insults and move forward.

Probably true :P

---

### Post by poptones on 2005-12-16
> desktops are only going to have one architecture: x86 (Apple is converting, so PPC will soon die off desktop wise). None of the distros are going to rip out Xorg and put in their own alternative.

They don't all use Xorg NOW. 

CPU architecture means something only in terms of third party (ie illegal) "driver" and codec support (ie making WMV play on linux when Microsoft doesn't want it to) and unit cost. There are already far more "linux systems" deployed around the world on *appliances* that are not, in any way, "pc compatible" than are. Just the number of *linux cellphones in asia* likely outnumbers all the desktop linux installations in the world. Then let's add in all those "hardware firewall" appliances, tivos, car stereos, portable media players...

> All of them are going to include the kernel, glibc, libstdc++, etc. I view different desktop distros as something less than an entirely different OS.

Then your view is poorly informed indeed. Let's see you boot ubuntu on your cellphone.

---

### Post by Halvorsen on 2005-12-16
Your talking shit. The loosing one is the deb-packages. YOU cannot even do a debsearch. See the truth or leave.

---

### Post by jdong on 2005-12-16
packages.ubuntu.com? packages.debian.org?

apt-get.org?

---

### Post by poptones on 2005-12-16
See the truth or leave?

I guess "the truth" is that having the ability to run *the latest software* means running an OS that has been hammered out in comittee, dictated by a standards body, and therefore uses modules that are at least six months out of date - in other words, an "open source" Windows.

Oh, the irony...

---

### Post by Jengu on 2005-12-17
[QUOTE=poptones]They don't all use Xorg NOW.[/quote]

What desktop distro, and by desktop distro I mean installs a WM at least by default, isn't running Xorg? I'm not talking about embedded devices like cell phones. Are you trying to be a stickler and point to some distros still using XFree, which for all practical purposes is just an older version of Xorg?

> Then your view is poorly informed indeed. Let's see you boot ubuntu on your cellphone.

The hell? I'm talking about *desktop linux*. There's a reason in my previous post I made sure to separate linux as a whole from desktop linux. A cell phone is not a desktop computer. People aren't going to expect their PC apps to run on cell phones.

[QUOTE=poptones]See the truth or leave?

I guess "the truth" is that having the ability to run *the latest software* means running an OS that has been hammered out in comittee, dictated by a standards body, and therefore uses modules that are at least six months out of date - in other words, an "open source" Windows.

Oh, the irony...[/QUOTE]

In a word: no. The distinction here is "hammering out" those parts of the OS that nobody cares are different so developers can concentrate on diversity that *is useful*. Different paths to fonts is not useful.

---

### Post by leech on 2005-12-17
[QUOTE=Halvorsen]Your talking shit. The loosing one is the deb-packages. YOU cannot even do a debsearch. See the truth or leave.[/QUOTE]

With that statement all I can ask is... why are you using a debian based distribution if you think that?  Why not go with Gentoo, or Sorceror or another source based distribution?  Generally I'm not the type of person to say go back to windows, but I'll make an exception in your case.  If you think that the package manager way of doing things is so wrong, then obviously you are just that much of a troll.  How about you just go make our own distribution?  How can you not do any sort of debian search?  how about this, make  distribution based around Autopackage?

Leech

---

### Post by poptones on 2005-12-17
*The hell? I'm talking about desktop linux. There's a reason in my previous post I made sure to separate linux as a whole from desktop linux. A cell phone is not a desktop computer. People aren't going to expect their PC apps to run on cell phones.*

You said you consider all *desktop linux distributions* roughly the same OS and then went on to point outhow they are al going to use these libraries, a kernel, etc...

Well then, why not on a cellphone? 

XP and Windows 2000 both use an "NT kernel." They are not, in any way, the same OS. Not even XP Pro and XP Home are considered the same OS - because they aren't. Yes, you can kludge one into the other but they do not come OOTB with the same libraries installed - some features on one are "missing" on the other.

The fact a distribution uses "glib, a kernel, and gtk" doesn't mean a damn thing. Even the difference between imagemagick 6.0 and 6.02 can make the difference between fuinctionality that works and crap that doesn't - so how on earth can you equate one OS with another? Microsoft doesn't even do this among their own operating systems and there is far less diversity there than even between Ubuntu Warty and Ubuntu Breezy. The fact they have the same label on the cd sleeve and look similar when you open the desktop doesn't have a thing to do with what's under the hood - the desktop is nothing but *branding*. 

This...

*But the issue here is that Mandriva and Debian and Redhat are not really that significantly different a platform. What I look forward to is the day that if Photoshop 2010 breaks on Redhat, that it is considered a Redhat bug because they've deviated from something like the LSB somewhere.*

Makes the point completely: they **are** "substantially different." they don't use the same compilers, the same libraries, or even entirely the same directory structure. That's because *they're not the same operating systems*. They were compiled from a common pool of **tools** - that doesn't make them *the same operating system*, "essentially" or otherwise. Two men working with hammers will not necessarily build the same house.

What you seem to be longing for is a linux that is no longer diverse; a linux designed by comittee. If that's your goal then I wish you good luck with that, but I'll again point out to you that even if Redhat and Mandriva and ubuntu were all to sign onto this project *the latest software* still would not be "an easy one click installation" - because *you wouldn't be using the latest software*. You'd be using this "standard" kernel and this "standard" glib and this "standard" structure that was all hammered out in comittee last year. And if this makes it easy for those "middle of the road" sorta-geeks to install the latest cvs of gimp all you're doing is setting them up for havoc when that cvs breaks something that those "middle of the road geeks" do not have the skills to correct.

The people who are ranting about the frustrations of "not being able to run the latest software" are **not** "the average user" nor are they even advocating **freedom**. They are confusing *openness in development* with *software releases* - they see a decimal point "upgrade" in the toolkit and then assume that means it should be just a mouse click away from being able to install on their machine because, after all, they're already using "the last version." Never mind that decimal point upgrade can bring with it dependancies on, say, a whole new glib, new kernel, new compiler... all things that must be tested and made to work together. If these "middle of the road geeks" do not have the talents to contribute to that effort you are not doing **anyone** a favor by making it easier for them to completely trash their computer. They cannot even offer reliable bug reports because, as the state of their system was indeterminate at the time of the incident, you have no reliable means of establishing *why* a given event was triggered. 

What is "the latest version" of a piece of software? It is whatever version is packaged *for your distribution*. If the community supporting your chosen distribution cannot meet your needs then you choose (or create) another - that's how you incent competition in the marketplace and, thereby, "grow linux."

---

### Post by jobezone on 2005-12-17
"Users may not fully appreciate another role filled by Linux distributors, however: they serve as middlemen between the producers and consumers of free software. This work goes beyond packaging programs and feeding back bug reports; Linux distributors also serve as crucial advocates for their users. When developers fail to act in the interest of the people using their software, the distributors can come in with their advocacy and patching skills to improve the situation." This is the exact reason distributions should not become irrelevant. Because they've stopped being mere distributors of bits & bytes a long time ago, especially ever since the first open and fully democratic project, Debian, first was formed in the 90's. I've never seen proprietary (or any kind of) ISV's agree between themselves on a Social Contract to their users... Full article, with an interesting history lesson about the misgivings of the creator of cdrecord, and Debian developers action on it, at: [http://lwn.net/Articles/97469/](http://lwn.net/Articles/97469/)

EDIT:Actually this article doesn't mention Debian, but Fedora, and at least all the major distributions helped in fixing the "bug" the upstream developer didn't want to fix (meaning, having dvd recording support).

---

### Post by Breepee on 2005-12-17
[QUOTE=poptones]"Bad language?" Would you prefer Russian? Farsi? French? I am using **fine** language; I am not the one belittling the people of this forum (those "basement dwellers") who take time out of their day to help ingrates like you. I am not the one making ridiculous arguments based on a complete *ignorance* to the realities of "the way things work."[/QUOTE]
I can see it right there. All you do is insulting other people and keep bragging about why you are so good.

This is a forum and I'm saying what I think and you can't handle that. That's all there is to it. You even admit you're a (wannabe) dictator.

Your other points are in part not thure and totally besides the point, but I really don't feel like explaining that to you now. My guess is you'll keep on scolding instead of contributing to the discussion or explaining what I purportedly don't understand.

---

### Post by Halvorsen on 2005-12-17
It's a cool day and I'm back from the heat of the night. Maybe my cpu got a bit overheated, but no hard feelings.

You see, poptones, that when you do a quote, you do it like this  [QUOTE=halvorsen]. With it you adress the quote to a person instead of just arguing against words.

Don't thank me. I'm just happy to be helpful.

---

### Post by jdong on 2005-12-17
[QUOTE=Jengu]What desktop distro, and by desktop distro I mean installs a WM at least by default, isn't running Xorg? I'm not talking about embedded devices like cell phones. Are you trying to be a stickler and point to some distros still using XFree, which for all practical purposes is just an older version of Xorg?[/QUOTE]

Sarge for one.

---

### Post by leech on 2005-12-17
[quote=poptones]What is "the latest version" of a piece of software? It is whatever version is packaged for your distribution. If the community supporting your chosen distribution cannot meet your needs then you choose (or create) another - that's how you incent competition in the marketplace and, thereby, "grow linux."[/quote]

BINGO!  We have a winner!  I completely agree with this.  If someone wants a newer version from upstream, either ask the current package maintainer nicely if they'll update, or help him/her with it yourself, so that everyone else in the community will benefit.  Or as Poptones said, find another distribution or make your own.

A good example of this, Xmame for Ubuntu is old as sin, so I kept going back to Debian Sid so that I could use the latest Xmame, and for some other packages as well, that just hadn't been updated in a long time under Ubuntu.  But then Gnome hasn't been updated in Debian Sid forever (Gnome 2.12 is mostly there, though I think a lot of the packages are still in experimental), and yet Ubuntu has had it for a few months now and are on their way to 2.14 in Dapper.  So that's what I'm using now.

Maybe for some of those that like to have the bleeding edge software should try out Foresight Linux.  It uses conary and has updates all the time for it to the latest/greatest/brokenest (yeah, I know the last one isn't an actual word...) software you can download.

Autopackage will not help any of this, because you would still either have to have a developer 'waste his time' (since apparently makng any packages is a waste of time, at least someone on this thread said this) to package it as an autopackage.  What Open Source projects could do is just have developers, and package maintainers.  Then anytime a new release is out, a new version will appear, at least in backports.  You don't want to have to continuously upgrade the main repositories, since they are supposed to be a set list of packages for SUPPORT reasons.

Leech

---

### Post by leech on 2005-12-17
[QUOTE=Jengu]What desktop distro, and by desktop distro I mean installs a WM at least by default, isn't running Xorg? I'm not talking about embedded devices like cell phones. Are you trying to be a stickler and point to some distros still using XFree, which for all practical purposes is just an older version of Xorg?> 

[QUOTE=jdong]Sarge for one.

I wouldn't really consider Sarge as a desktop distro.  Mainly because it doesn't actually install anything by default (it's very much equivalent to using 'server' when installing Ubuntu).  Though of course the choice to install the window managers is there during the initial setup... so it could be argued either way.  I think I would describe Sarge as the ultimate OS in choice, since it's just as easy to build a server as a desktop from it.  Tasksel needs a bit of improvement though (like splitting the option for KDE/Gnome/other WM.  Since as it is right now, if you're doing a net install and tell it to install Desktop Environment, it installs both KDE and Gnome.)

Leech

---

### Post by Jengu on 2005-12-17
[QUOTE=poptones]You said you consider all *desktop linux distributions* roughly the same OS and then went on to point outhow they are al going to use these libraries, a kernel, etc...

Well then, why not on a cellphone? 
[/quote]

Sorry, that still sounds like a nonsequiter to me. You're going to have to expand that a little more for me to get your point.

To answer the rest of your post:

You're trying to factually state that distros are totally different operating systems. I'm saying we *choose* to look at it that way. And I don't think it's healthy.

And you continue to claim that I year for linux by committee. I don't. I yearn for agreement and standardization of those things that **serve no useful purpose being different**. The fonts example continues. I think we can both agree that we love the diversity of open source software and of linux distributions. But I think we can also agree that some of the differences are stupid and serve no purpose other than making life harder for packagers.

[QUOTE=jdong]Sarge for one.[/QUOTE]

Did you read the last sentence in the snippet you quoted? ;) XFree86 4.3 is for all practical purposes an older version of Xorg. It's a name change. It's still the same X protocol. It's still xlib. The extensions Xorg have added are on top of what was already there, not in place of. My point is still the same -- nobody is going and using something radically different.

---

### Post by poptones on 2005-12-17
> You're trying to factually state that distros are totally different operating systems. I'm saying we choose to look at it that way. And I don't think it's healthy.

and you haven't so much as *tried* to explain the logic (or lack of it) for your "feelings." I have explained why your "feelings" are illogical - do you have an argument to make or are you just going to keep making this unfounded assertion again and again until you convince someone to take your word for it?

> The fonts example continues.

The fonts example is trivial and stupid; my fonts live in ~/.fonts and work just fine - just as they did when I used Mandrake and Suse. I personally find it more of a nuisance to keep track of where *icons* go - there's about three different folders and no rhyme or reason to which app uses which pixmaps...oops, wait, that's not a problem with the distributions, it's a problem with *gnome*.

> XFree86 4.3 is for all practical purposes an older version of Xorg. It's a name change. It's still the same X protocol. It's still xlib.

Uh huh. *Which* xlib? *Which* "older version?" You think ubuntu's gnome would "just deal with it" if you were to strip out xorg and just drop in xfree from debian?

Linux already has a "standard base." No one cares. 

There is no reason to have "write once run on them all" binaries. Just look at the interviews with fearless (ubuntu) leader on the reasons for diverging from debian: one of the main reasons cited was that everything is hammered out to work together while providing a reasonably up to date OS - every deb is recompiled and repackaged, in part, for QC. 

Linux is not a company and it's not an operating system - linux is a kernel inside a big ol' wad of software and that software all has to work together in order for the desktop to function. Someone has to take the time and trouble to do that, and that "someone" is the community of distribution houses. I guess to you OS X is just BSD, huh? Hell, for that matter let's call Windows BSD too - after all, it has code lifted from there.

Come to think of it just about every *nix like OS AND windows all share a common link in the tools originally used to produce them. So I guess we should just be compiling everything to stick the libraries in /Windows/System32 and the user shares in /Documents; after all, that's the way the other guys do it...

---

### Post by jobezone on 2005-12-17
[QUOTE=leech] Tasksel needs a bit of improvement though (like splitting the option for KDE/Gnome/other WM.  Since as it is right now, if you're doing a net install and tell it to install Desktop Environment, it installs both KDE and Gnome.)[/QUOTE]
I installed Etch (from a etch netinstall CD), and now Desktop Environment only installs Gnome. It's an improvement, but why debian people chose Gnome as _the_ desktop environment beats me.

---

### Post by jdong on 2005-12-17
[QUOTE=Jengu]Did you read the last sentence in the snippet you quoted? ;) XFree86 4.3 is for all practical purposes an older version of Xorg. It's a name change. It's still the same X protocol. It's still xlib. The extensions Xorg have added are on top of what was already there, not in place of. My point is still the same -- nobody is going and using something radically different.[/QUOTE]

Umm, if you think XFree86 4.3's xlib is binary compatible with Ubuntu, you're sadly mistaken.

---

### Post by poofyhairguy on 2005-12-18
> **Jengu]Hopefully part of the ultimate mission of the free software movement in general as well as Ubuntu is to convert them if possible. Which means reeling them in.[/QUOTE]

I think an eventual goal for many projects IS to increase their userbase, but no way thats the ultimate motive for EVERY project.

> 
But the issue here is that Mandriva and Debian and Redhat are not really that significantly different a platform.

They are two totally different OSes. Hundreds of small differences(decisions) seperate them. It might be confusing because they run different versions of the same software, but they are WAY different platforms.

> 
 What I look forward to is the day that if Photoshop 2010 breaks on Redhat, that *it is considered a Redhat bug* because they've deviated from something like the LSB somewhere. Nowdays open source project changelogs have stuff all the time like "Bug fix to make work on Debian," "configure hack to compile on Fedora," etc.

So you dream for a day where the Linux Desktop is not chaos? This is not on topic, but I will say that he only reason you even have a want like that is because of a market mindset created by MS and Windows (unity is best thing, only one can rule, etc.) and that its a pipe dream. Red Hat will be a server OS, Ubuntu will be a libre desktop OS, Linspire will be an OEM OS, Knoppix will be a Live CD OS and no magic fairy powder is going to convince all these seperate groups with different goals for Linux to work together.

 At best something like the LSB can make an Autopackage work 80% of the time but no magic will make Linux a single "platform" to develop for.

But this is off topic as this is not the point of Autopackage.

> 
Perhaps you would like to reread the title of the thread...

Why? It does not change the fact that the Linux Desktop is a side effect of the Linux server (and its resources) and is destined to stay a hobbiest side of Linux till some REAL money enters the market.

> 
Actually they can. Literally they can't sure, they can't pass an amendment to the GPL or something, but for all practical purposes they can. 

You and I have different definitions of "practical." To you it must mean that it is physically possible. To me it means that it COULD happen. In this case with the first definition you are right, and for the second I am right I think.

> 
When the major distros (Redhat, SuSE, Mandrake, Ubuntu) agree and conform to something, other distros will follow out of **self interest**. 

And an example of this happening is? To dream that the major distros will all work together on ANYTHING thats not code or something like that is setting yourself up for dissapointment.

There is a reason Mark went on a rant about why binary compatibility is a pipe dream and its source compatibility that matters. He knows the truth- all the major Desktop Distro will work together for binary compatibility the day MS releases its Office product under the GPL.

And again its all off topic. The point of Autopackage is not to bring the distros together. Its a realistic attempt to deal with the fact that such won't happen.

> 

Why put fonts in a different place when it's going to make converting packages harder?

Because you make the packages and that the way you prefer it? If you dislike these small decisions, there is always Gentoo or LFS.

> 

Well, time or money. Maybe I just have more faith in Mark's ability to find worthwhile projects for Canonical's surplus dollars  said:**
> 

Ubuntu is a rare case. For all non distro supported (aka important) packages Debian Sid maintains them. For all important packages Ubuntu packages them- and this would be the same in the best case scenario spelled on the Autopackae site. So no time is wasted. 

[QUOTE]
Debian experimental isn't whole inclusive either. And Arch has a really poor package selection. The point is -- repositories can never include all software and be simultaneously up to date. Out of the 7 or 8 distros I've tried, gentoo was best about Selection*Recentness, and that's probably in part due to them not having to compile packages before uploading them ;P

Autopackage's list is not huge at the moment either. If the developers are still going to release tarbars, there is little the community can do besides continuing to package the software for themselves and their distro. Now maybe if the Autopacakge "repo" ever gets bigger than the Ubuntu one a distro can use it exclusively.

[QUOTE]
Eh, that's not quite true. I've seen quite a few people download and install aim or itunes. "Geekiness" is a gradient. Your mom is probably at the other extreme.

My mom is the majority as far as anyone can tell. Are geeks, hardcore gamers or computer hobbiests the majority? No. People that think that knowing your way around the Windows Control Panel is knowing "how to use a computer", "which is something I don't know" are the majority.

Just because people install new software once does not mean that they sift throught nerd news sites waiting for releases- only geeks want the newest programs THE DAY they come out. For the rest there is backports and distros that constantly update.

> 
Yeah, I must be one of those middle of the road ones. My post count on gentoo.org is nothing to sneer at. My job is to code a crossplatform project in C++. I read the wine-devel, python, and kde usability (!!) mailing lists. I'm writing this under X.org 6.9 RC1. In my spare time I'm reverse engineering the level format for an old game so I can reimplement it in python so it'll be crossplatform but still compatible with the old levels. I read the kernel changelogs.

Not to insult you, but compared to the main kernel hackers or the people developing QT or GTK that is middle of the road.

And that was not my point. Nor is either on topic- Autopackage says its for beginning users. It will be good for closed projects for such users.

> 
I understand the mentality that different distros are totally different OSs. But I think that's a bad perception to work under, at least for the desktop.

Its the only perception that keeps you from be disappointed again and again when the leaders of Desktop Linux reject one chance after another to work together more.

 > 
I think it makes sense for their to be different distros aimed at different purposes. A distro aimed at servers wouldn't put the preemption patches in their kernel for example. Distros may also come with a different set of default software installed. Different architectures maybe targeted.

BUT -- desktops are only going to have one architecture: x86 (Apple is converting, so PPC will soon die off desktop wise).

Actually, many believe that a part of future Desktop growth for Linux will come from supporting the PPC machines Apple is leaving behind at some point. 

> 
 None of the distros are going to rip out Xorg and put in their own alternative.

No, but some can stand to have a newer version of it than others (see Mandrake releasing final release recently with Xorg beta included).

> 
 All of them are going to include the kernel, glibc, libstdc++, etc.

But what version depends on what the goal of the distro is.

> 
 I view different desktop distros as something less than an entirely different OS.

Its easy to see why, but the truth is that they are.

On topic, Autopackage trys to find a way to work these different OSes into one platform. Because of that it makes technical sacrifices that many distros don't like and therefore will never support. But Autopackage knows this and part of its intention is to not need the support of distros. Thats why it will be good software and the end, but asking for distro support at this point is pointless.

---

### Post by Knomefan on 2005-12-18
[QUOTE=poofyhairguy]
They are two totally different OSes. Hundreds of small differences(decisions) seperate them. It might be confusing because they run different versions of the same software, but they are WAY different platforms.
[/quote]
No, they aren't.
That's why it is generally possible to compile the same source code on all of them and why it is possible to create one binary that run on all of them (e.g. firefox, acrobat reader, etc.)

[QUOTE=poofyhairguy]
So you dream for a day where the Linux Desktop is not chaos?
[/quote]
Yes, as is the dream of the KDE and Gnome and freedsktop.org guys:
[http://www.desktoplinux.com/news/NS2649626642.html](http://www.desktoplinux.com/news/NS2649626642.html)

[QUOTE=poofyhairguy]
But this is off topic as this is not the point of Autopackage.
[/quote]
If you read the autopackage faq, that's exactly the point of autopackage.

[QUOTE=poofyhairguy]
Why? It does not change the fact that the Linux Desktop is a side effect of the Linux server (and its resources) and is destined to stay a hobbiest side of Linux till some REAL money enters the market.
[/quote]
Is that a fact? Who would have thought.
And of course it is factually incorrect.
[http://2005.guadec.org/schedule/speakers.html#speaker-nathan-wilson](http://2005.guadec.org/schedule/speakers.html#speaker-nathan-wilson)

[QUOTE=poofyhairguy]
Not to insult you, but compared to the main kernel hackers or the people developing QT or GTK that is middle of the road.
[/quote]
Well, if you don't want to insult him, then simply don't.

---

### Post by poofyhairguy on 2005-12-18
[QUOTE=Knomefan]No, they aren't.
That's why it is generally possible to compile the same source code on all of them and why it is possible to create one binary that run on all of them (e.g. firefox, acrobat reader, etc.)[/QUOTE]

My DVD Shrink binary works on Ubuntu using WINE and XP. Does that make then the same OS too? No. The truth is that the lines are political ones- its hard to tell exactly where they are drawn. I can say they are different OSes and be correct.

> 
Yes, as is the dream of the KDE and Gnome and freedsktop.org guys:
[http://www.desktoplinux.com/news/NS2649626642.html](http://www.desktoplinux.com/news/NS2649626642.html)

Not all of them (well....maybe all of thefreedesktop.org people).

> 
If you read the autopackage faq, that's exactly the point of autopackage.

The point is to be a bridge for somethings, not a platform:
> 
What RPM is not good at is non-core packages, ie programs available from the net, from commercial vendors, magazine coverdisks and so on. This is the area that autopackage tackles. Although in theory it'd be possible to build a distro based around it, in reality such a solution would be very suboptimal as we sacrifice speed for flexibility and distro neutrality

> 
Is that a fact? Who would have thought.

How funny. Of course its not a fact.

> 
And of course it is factually incorrect.
[http://2005.guadec.org/schedule/speakers.html#speaker-nathan-wilson](http://2005.guadec.org/schedule/speakers.html#speaker-nathan-wilson)


And that link says so...how? How does that not prove that current interest in the Linux Desktop use resources and frameworks intended for server use? Oh well, its off topic.

> 
Well, if you don't want to insult him, then simply don't.

For most people pointing out that they are not at the top of the mountain is not an insult- its reality unless they truely are (aka just won Olympic gold metal).

---

### Post by poofyhairguy on 2005-12-18
Let me say before we get any further off the point that I think that Autopackage is a really neat piece of software. Its cool for a GUI installer to try to focus on less technical users. 

Its cool software for what it does I say. But the end result is that until itworks with the native package managers more it might have support problems.] with distros.

---

### Post by Knomefan on 2005-12-18
[QUOTE=poofyhairguy]My DVD Shrink binary works on Ubuntu using WINE and XP. Does that make then the same OS too? No. The truth is that the lines are political ones- its hard to tell exactly where they are drawn. I can say they are different OSes and be correct.[/quote]
What kind of example is that? DVD Shrink is running on wine, which is a compatibility layer for Windows, so this has nothing at all to do with what I said. If anything your example would be wine == Windows, though wine of course isn't an OS in itself.

[QUOTE=poofyhairguy]
Not all of them (well....maybe all of thefreedesktop.org people).
[/quote]
So?

[QUOTE=poofyhairguy]
The point is to be a bridge for somethings, not a platform:
[/quote]
Yes and it's part of a greater effort to create a platform:
[http://autopackage.org/faq.html#5_1](http://autopackage.org/faq.html#5_1)
[http://autopackage.org/NOTES](http://autopackage.org/NOTES)

[QUOTE=poofyhairguy]
How funny. Of course its not a fact.
[/quote]
Yes, it's hilarious, isn't it?

[QUOTE=poofyhairguy]
And that link says so...how? How does that not prove that current interest in the Linux Desktop use resources and frameworks intended for server use? Oh well, its off topic.
[/quote]
That link simple says that claiming Linux on the desktop "is destined to stay a hobbiest side of Linux" is simply wrong. 

[QUOTE=poofyhairguy]
For most people pointing out that they are not at the top of the mountain is not an insult- its reality unless they truely are (aka just won Olympic gold metal).[/QUOTE]
Well, belittling someone elses efforts and achievements is very easily taken as an insult and thus should be avoided, imho.

---

### Post by poofyhairguy on 2005-12-18
[QUOTE=Knomefan]
That link simple says that claiming Linux on the desktop "is destined to stay a hobbiest side of Linux" is simply wrong. [/QUOTE]

Links don't prove that to be wrong. Market penetration does that. Its an opinion. 

> 
Well, belittling someone elses efforts and achievements is very easily taken as an insult and thus should be avoided, imho.

Thats not my intention. Just in case I openly apologize for any insults.

---

### Post by Knomefan on 2005-12-18
[QUOTE=poofyhairguy]Links don't prove that to be wrong. Market penetration does that. Its an opinion. [/quote]
Ok, to be precise, the content of the web page that the link leads to proves you wrong.

Oh, and btw., according to IDC linux already has a bigger market share on the deskotp than Apple.

---

### Post by poptones on 2005-12-18
> No, they aren't (different OS's).
That's why it is generally possible to compile the same source code on all of them and why it is possible to create one binary that run on all of them (e.g. firefox, acrobat reader, etc.)

Firefox and OOo, even in Ubuntu where they have been "tweaked" to better fit in the desktop, still do not fit seamlessly. In OOo some themes make parts of dialogs downright unreadable. This alone shows they are not "the same OS."

You can also get toolkits that allow you to write c applications that can be compiled for linux, mac and windows. They don't install with a common installer but they all are "source code compatible" so long as the build machine has the proper libs installed. This is exactly what separates many linux systems from one another - just a difference in installed libraries and build gcc. Again, it would seem linux and windows really are just the same OS.

Well, after all, they're both POSIX compliant...

---

### Post by Knomefan on 2005-12-18
[QUOTE=poptones]Firefox and OOo, even in Ubuntu where they have been "tweaked" to better fit in the desktop, still do not fit seamlessly. In OOo some themes make parts of dialogs downright unreadable. This alone shows they are not "the same OS."
[/quote]
No, it shows the integration into Gnome and KDE is not perfect.

[QUOTE=poptones]
You can also get toolkits that allow you to write c applications that can be compiled for linux, mac and windows. They don't install with a common installer but they all are "source code compatible" so long as the build machine has the proper libs installed. This is exactly what separates many linux systems from one another - just a difference in installed libraries and build gcc. Again, it would seem linux and windows really are just the same OS.
[/quote]
Again, you are confusing having a compatability layer with beinge the same OS.

[QUOTE=poptones]
Well, after all, they're both POSIX compliant...[/QUOTE]
Windows isn't, not anymore anyway.

---

### Post by poptones on 2005-12-18
*Again, you are confusing having a compatability layer with beinge the same OS.*

Uhhh.. you are making the argument two operating systems built from a common toolkkit are "the same OS." How is that different? What is a "compatability layer" anyway? Windows itself has many of these because it has to remain somewhat backward compatible - yet each OS *is* different. This is not just my opinion; it is a fact borne out by Microsoft itself on virtually every level of support. Strip certain libraries out of XP, toss in a few more and now you've got Server 2003... that makes XP and 2003 the same OS? No way.

*...it shows the integration into Gnome and KDE is not perfect.*

Why not? They are made to run on *the same operating system*, after all.

---

### Post by poofyhairguy on 2005-12-18
[QUOTE=Knomefan]Ok, to be precise, the content of the web page that the link leads to proves you wrong.[/QUOTE]

How? Because it shows that a few people with serious careers are tied to Gnome? Gnome is not Desktop Linux- it can be used on many things like FreeBSD or Solaris so its status tells nothing about Desktop Linux alone. Plus plenty of serious people are part of hobbiest projects (John Carmack and rockets anyone?) but that does not make the genre a non hobbiest area.

Since my denotation is probably different than yours, its a harder thing to prove.

> 
Oh, and btw., according to IDC linux already has a bigger market share on the deskotp than Apple.

So? OSX still has only hobbiest numbers as well. Not being hobbiest to me means:

1. Widespread use by at least 10% of largest organizations.

or 

2. Its used by 20% of the the marketshare for that market.

Or both.

So until I hear a reference to Desktop Linux on primetime T.V., read about it in Newsweek or hear that a BIG computer maker (like HP or Dell or someone of that size) ships it by default on a decent percentage of their Desktop line its still hobbiest to me. Sure many businesses probably use it as a Desktop- but until the Desktop side is as popular or more than the server side of Linux(or heck even close) then I consider it to be hobbiest based. Not a bad thing really.

Of course, this is not about Autopackage at all so I will drop it.

---

### Post by Knomefan on 2005-12-18
[QUOTE=poptones]
Uhhh.. you are making the argument two operating systems built from a common toolkkit are "the same OS." How is that different? What is a "compatability layer" anyway? 
[/quote]
Ok, let me give you an example.
Take some java app, say azureus. Now this app runs on Windows, Mac, Linux, etc..
However, in fact it doesn't run on these OSes at all, but on Java and Java is running on these OSes.
Now, head over to sun and look for the java versions you will get. You'll get one for OSX, one for Windows and, gosh, one for Linux (which means essentially all linux distributions).

[QUOTE=poptones]
*...it shows the integration into Gnome and KDE is not perfect.*

Why not? They are made to run on *the same operating system*, after all.[/QUOTE]
Integration into a desktop environment has absolutely nothing to do with which OS something runs on, so what's your point?

---

### Post by poptones on 2005-12-18
So now you are comparing a managed code interpreter to a system API?

Linux with wine will run many windows apps - just like windows. This is not managed code nor is it emulation - it is a library just like glib and gtk and that other stuff you are arguing makes all distributions "the same os." If that be so then linux is windows because linux with wine installed can run at least as many contemporary applications as could windows 95.

You seem to draw the line at "compatability layer" at whatever arbritrary point best suits your argument of the minute.

---

### Post by Knomefan on 2005-12-18
> Wine is an Open Source implementation of the Windows API on top of X and Unix.

Think of Wine as a compatibility layer for running Windows programs.
[http://www.winehq.com/](http://www.winehq.com/)

---

### Post by poptones on 2005-12-18
Thanks for helping prove my point. You do realize logic dictates one does not say "think of this as" when they mean "this is?" 

Wine is just a library of system calls running on a kernel... *exactly* like system32 on windows. 

Ubuntu is not debian is not mandrake is not redhat is not windows 95 is not windows 2000 is not windows xp.

---

### Post by jdong on 2005-12-18
Wow.... I think this thread has really exposed that many of us do not truly understand the technical issue that the Ubuntu devs and others are concerned about with Autopackage.

---

### Post by awakatanka on 2005-12-18
> Oh, and btw., according to IDC linux already has a bigger market share on the deskotp than Apple.
1 of the reasons apple still get targetted by closed source programs is the easly installing and there for can reach all of the users.

The 1 reason that closed source almost not writting anything for linux is no easly installing and there for can not reach all linux Desktop users.

Autopackage is a effort to fill a gap but the distro's are atm not happy with it for alot of reasons and there for they need to prove them wrong. I'm more a fan of klik because it doesn't change anything of my installation.

But if there isn't going to be a easly install for programs that are not in the distro's repositories for what ever reason then the normal none nerd/geek will be scared away from linux desktop. The normal user simply want a simple click and install and don't wan't to ./configure ,make & make install our search for hours to find a dep ,rpm and hope its for the distro the use.

---

### Post by neighborlee on 2005-12-18
[QUOTE=awakatanka]1 of the reasons apple still get targetted by closed source programs is the easly installing and there for can reach all of the users.

The 1 reason that closed source almost not writting anything for linux is no easly installing and there for can not reach all linux Desktop users.

Autopackage is a effort to fill a gap but the distro's are atm not happy with it for alot of reasons and there for they need to prove them wrong. I'm more a fan of klik because it doesn't change anything of my installation.

But if there isn't going to be a easly install for programs that are not in the distro's repositories for what ever reason then the normal none nerd/geek will be scared away from linux desktop. The normal user simply want a simple click and install and don't wan't to ./configure ,make & make install our search for hours to find a dep ,rpm and hope its for the distro the use.[/QUOTE]


I couldn't agree more.

If anyone doubts that  then they only have to look at  market share Windows represents and our flimsy what 3% or whatever it is now, and the fact that most vendors still wont adopt us and that game developers are still shying away ( latest nasty in that war is fact that NWN2 wont be for us out of the box )

I MUCH prefer KLIK as well because its great for testing apps for example,  and I really like the non-intrusive way of running apps.  I feel that dependency resolution IS a major stumbling block for linux and that is another reasoN ( okay  yes sure, at expensive of a few extra used HD space ) to adopt KLIK.  I wish it had broader adoption that just SLICK,kannotix and whatever else. o_0

The linux world needs something like download.com where ANY distro  using it will be able to install ANYTHING from there.  I figure KLIK has the best chance of obtaining that goal in a reasonable amount of time, but  it could use  a enhanced UI ( not unlike CNR IMO ).

cheers
nl

---

### Post by Leif on 2005-12-18
[QUOTE=neighborlee]
I MUCH prefer KLIK as well because its great for testing apps for example,  and I really like the non-intrusive way of running apps.  I feel that dependency resolution IS a major stumbling block for linux and that is another reasoN ( okay  yes sure, at expensive of a few extra used HD space ) to adopt KLIK.  I wish it had broader adoption that just SLICK,kannotix and whatever else. o_0

The linux world needs something like download.com where ANY distro  using it will be able to install ANYTHING from there.  I figure KLIK has the best chance of obtaining that goal in a reasonable amount of time, but  it could use  a enhanced UI ( not unlike CNR IMO ).
[/QUOTE]

I think that Klik is fundamentally a better idea as well, but I've never used it, so it's a pretty theoretical view. I'm not sure what you mean by "broader adoption", but if you mean that it doesn't work with more distros, I'll point out that it does actually work with breezy, and a few more distros too.

---

### Post by aysiu on 2005-12-18
[QUOTE=awakatanka]
But if there isn't going to be a easly install for programs that are not in the distro's repositories for what ever reason then the normal none nerd/geek will be scared away from linux desktop. The normal user simply want a simple click and install and don't wan't to ./configure ,make & make install our search for hours to find a dep ,rpm and hope its for the distro the use.[/QUOTE] Haven't we been through this before? **Normal people do not install software**, and if they get someone else to do it for them, they rarely update that software.

People who install a lot of software (especially stuff outside of the repositories) are **not** "normal people." They are, in fact, intermediate nerds/geeks instead of advanced nerds/geeks.

You will find yourself running into problems if you have high needs and low means. Them's the breaks.

Low needs and low means are happy in Linux (me).
High needs and high means are also happy (some other users here).

---

### Post by awakatanka on 2005-12-18
[QUOTE=aysiu]Haven't we been through this before? **Normal people do not install software**, and if they get someone else to do it for them, they rarely update that software.

People who install a lot of software (especially stuff outside of the repositories) are **not** "normal people." They are, in fact, intermediate nerds/geeks instead of advanced nerds/geeks.

You will find yourself running into problems if you have high needs and low means. Them's the breaks.

Low needs and low means are happy in Linux (me).
High needs and high means are also happy (some other users here).[/QUOTE]
Well i think you very wrong. I'm working in it doing support and repairs. And lots of people install, heck how do you think lots of people have problems with spyware and other prg's, because they hear from friends he mate thats a cool prg you have to try that, so don't say normal people don't install because you realy don't know what the normal desktop people do. What people don't do is when its getting to difficult then they ask people to help. And what is difficult? yep the uninstall of those spyware shit and thats where i get my earnings from. 

(k)ububtu is targeting the desktop users so they have to make it user friendly and easly to install also for prgs outside the repository.

---

### Post by aysiu on 2005-12-18
[QUOTE=awakatanka]And lots of people install, heck how do you think lots of people have problems with spyware and other prg's, because they hear from friends he mate thats a cool prg you have to try that, so don't say normal people don't install because you realy don't know what the normal desktop people do.[/QUOTE] First of all, you don't have to actively try to install anything to get spyware. Most people get it just by using Internet Explorer and visiting shady websites. Good try, though. Secondly, most of the types of programs ordinary users try to install (email clients, chat programs, etc.) are available via Synaptic.

Whenever someone posts here saying, "Yeah, how do I install such-and-such a program. I can't find it in Synaptic anywhere," my reactions are always:

1. How the hell did this person even know about that program? I've never heard of it.
2. I'm so glad I don't need programs like that. All my needs are met by programs in Synaptic.

I happen to know a lot of normal people, because on a day-to-day basis they come to me with their Windows problems. And almost no one in my office knows how to install programs. Hell, I have to even install iTunes for them--double-click, click, click, click. I deal with ordinary users every day.

---

### Post by awakatanka on 2005-12-18
[QUOTE=aysiu]First of all, you don't have to actively try to install anything to get spyware. Most people get it just by using Internet Explorer and visiting shady websites. Good try, though. Secondly, most of the types of programs ordinary users try to install (email clients, chat programs, etc.) are available via Synaptic.

Whenever someone posts here saying, "Yeah, how do I install such-and-such a program. I can't find it in Synaptic anywhere," my reactions are always:

1. How the hell did this person even know about that program? I've never heard of it.
2. I'm so glad I don't need programs like that. All my needs are met by programs in Synaptic.

I happen to know a lot of normal people, because on a day-to-day basis they come to me with their Windows problems. And almost no one in my office knows how to install programs. Hell, I have to even install iTunes for them--double-click, click, click, click. I deal with ordinary users every day.[/QUOTE]
They people that you know and i know have to be very different then.  I have a very good earning because people do everything with there computers. And installing prgs is also a thing they do. You make it look like that all users are playstation people " cd in and play " Then i'm living in a other world then you.

Why you think a site as download.com would be if a normal user doesn't install. You have degrees of people , New people that don't know much and ask a lot and ask for installs, Normal users that try a lot of things with there pc, and tweaker nerds geeks pro's that think they know all and know what is good for the other degrees. And if a  windows nerd can't even easly install a linux appz outside a repository then there is something wrong with the user friendlyness.

---

### Post by poptones on 2005-12-18
Download.com is the number one repository of **shit** on the internet. The last thing **the world** needs (linux or otherwise) is more of these bastions of exploit. It sounds more like you are arguing in defense of your ability to make money off poor saps who bork their computer by whoring it out to every "freeware" developer that lures them in with a deceptive sales pitch.

I support "normal users" evey day. Just the other day I was working on a four year old Compaq that still has those stupid feature stickers on the front of the case. "Normal users" don't even remove the adverts from their computer before setting it up in their bedroom or living room - much less visit download.com. "Normal users" spend their time shopping ebay and amazon, not cnet and tucows.

If you want that stuff, install cedega and knock yourself out. Or better still, just use windows.

---

### Post by awakatanka on 2005-12-18
[QUOTE=poptones]If you want that stuff, install cedega and knock yourself out. Or better still, just use windows.[/QUOTE]

a atitude like that will attrackt of people to (k)ubuntu. 

It just was a example that people do install stuff. But there is no point in arguing   with people like you that think they know whats the best for others.

I thought the main goal is to make a distro atractive to as much of people as possible. And 1 thing that it needs then is a easy install for things outside repository for what ever reason. And attrackt closed sources writer to make appz to for a desktop linux, because not everything has a counterpart in opensource.

And i'm not a fan of autopackege to, even if it means i can probably money with it because its not secure enough. And what is secure a computer is as secure as the people behind it.

---

### Post by aysiu on 2005-12-18
[QUOTE=awakatanka]They people that you know and i know have to be very different then.[/QUOTE] Agreed. I'm not saying a significant portion of the Windows population doesn't visit Download.com and download and install whatever, but I do believe a significant portion also does not download or install anything explicitly, and when they do install stuff, they need help from someone like me, and then they never update it.

Now how common these two populations are, I don't know. However, you can't imagine that the people I describe are only a fringe population. Just about all of my relatives and my wife's relatives also do not install anything (except my sister-in-law who likes spyware-infesting file sharing programs).

---

### Post by awakatanka on 2005-12-18
[QUOTE=aysiu]Agreed. I'm not saying a significant portion of the Windows population doesn't visit Download.com and download and install whatever, but I do believe a significant portion also does not download or install anything explicitly, and when they do install stuff, they need help from someone like me, and then they never update it.

Now how common these two populations are, I don't know. However, you can't imagine that the people I describe are only a fringe population. Just about all of my relatives and my wife's relatives also do not install anything (except my sister-in-law who likes spyware-infesting file sharing programs).[/QUOTE]
The forums of distro's are filled with windows nerds that wanna try linux desktop because they heard about the freedom and tweaking possibility's but after a few try's with compiling a source our finding debs for prgs that are not in repository they leave and go back to there (illigale)windows because its a simple click work for them.  You can simply say they are to lazy to stick and learn our you can make it actractive for them and they will stay. 

A good distro will have the best of both worlds easy for the people not willing to learn much and hardcore for the geeks that know what they do. 

But enough now for me. my wife is almost exploding she thinks i'm married to my pc.

---

### Post by scaine on 2005-12-18
Jaaaaysus!  I deliberately unsubscribed for this thread for about a week.  Serves me right for reading up on it again.

My main argument, that both Aysiu and Poptones seem to be overlooking (perhaps deliberately) is games.  And possibly drivers.  But mainly games.

I know of tens of people (not directly, but friends of friends) who are exactly as Poptones and Aysiu describe - they just do not install software.  But they *do* install games.  For no other reason, we need a Klick or an Autopackage.

Simple as that.

For no other reason, you ***MUST*** have an easy way of installing a "linux" game on any distro.  Because otherwise, can you honestly see games developers listing : requirements - Windows 95, 95, 2000, XP, Ubuntu (Warty, Hoary, Breezy), Redhat (8, 9, 10), Fedora (2, 3), Mandriva (whatever-the-f*ck), blah blah, blah), DirectX, OpenGL, etc, etc.

No.  It'll just be "linux".  And people will expect it to run.  Like the Loki installers did (if you did any reseach on it of course).  And waaaaaaaaaaaay back in this thread someone compared Autopackage to Loki - well done.  You'd nailed it, but it took (what feels like) several hundred posts to get to the crux of the situation.

Although even now, I'm sure someone will pick holes in my argument.

---

### Post by poptones on 2005-12-18
Scaine, I personally do not think this is appropriate *even for games*. Complex games with demanding graphics need a *game platform*. That's even a worthy project for the linux folks to tackle and, honestly, I hope someone does go there in *a meaningful way* that garners some real support. Evolving a "standard" gaming platform that doesn't change every other week would, I think, go a long way toward attracting more serious game developers - not that I think, in any way, that the world needs even more developers of *proprietary, closed source gaming technology*. I personally find fps games boring but I would love to participate in an *open and evolving* world like Myst. 

That doesn't mean any of this has any part in *desktop linux*. With the virtualization techniques available even today there is no reason someone who wants to run games could not take advantage of a completely separate *operating system* dedicated to that task. 

And **still** none of that would benefit from a "compile once and run (sort of, kinda, in uniformly crippled fashion) on every distribution" installer like autopackage. If someone evolves a sophisticated and dedicated gaming platform those "write once installers" wouldn't be able to ttake advantage of any of those features to the end of providing more compelling game play because it would have to be crippled so as to work with the low end, stripped down desktops where it can also be "eaily installed." 

> But there is no point in arguing with people like you that think they know whats the best for others.

How utterly ironic you are trying to point that finger at **me** when it is **you** who is arguing *exactly this*. I am not telling what you may or may not do *at all*. I am not telling you what I think is "best for you" - **that is, however, what those folks you are defending do**. "They" don't "release" software to the world until "they" have tested it and packaged it and made it brain dead easy "for people like you" to install and (more often than not) *break* your computer.

Don't you get it? Proprietary software is **released**. That means it's out there in the world and people are using it, playing with it, creating it... but it is walled off from you; you are not "allowed to see it" until **they say so**.

Linux evolves in the open. It is a "community project." It is there for everyone to see and to "use" **even when it isn't done**. This confuses windows users because they think, since the software is there on this website and other "regular people" have acces to it then they have the "right to it" as well. 

You see someone building a swimming pool in your neighborhood and, rather than picking up a shovel and helping get it done, you're standing there in your swimsuit insisting we're all oppressing you by not letting you jump in the muddy hole in the ground where everyone's still working. No one is saying you cannot go swim *over there* in the pool we made * last year* - we're telling you that if you want to jump in *this hole* then you are going to have to pick up a damn shovel and do some work. That's not being mean, that's just how things get done.

---

### Post by Jormundgand on 2005-12-18
That post got to the point where I have absolutely no idea what the argument even IS anymore.

I vote this topic be closed as too god-damned confusing.

I will say this - using **lots of bold** must obviously make you **really cool**, else why **would** poptones be using **them** such **a** lot?

---

### Post by poptones on 2005-12-18
I do it just to confuse "people like you."

Seems to be working...

---

### Post by r4ik on 2005-12-18
Honestly Poptones however there is some truth in your arguments there is no reason to tell somebody he is braindead.

---

### Post by poptones on 2005-12-18
Where did I do that?

Somewhere around here there is even a thread about BDI - the "brand dead installer."

Some of you take too much of what I say way too seriously. I'm not Rush Limbaugh; I'm more like a belligerent Bill Murray.

---

### Post by newbie2 on 2005-12-18
stupid question maybe , but what if there was one universal package manager 'baked' into the linux kernel(if this was possible to do) ? :p

---

### Post by jdong on 2005-12-18
That does not technically make sense.

---

### Post by newbie2 on 2005-12-18
[QUOTE=jdong]That does not technically make sense.[/QUOTE]
why not?

---

### Post by jdong on 2005-12-18
(1) Package managers cannot be embedded into kernels for feasibility reasons (there are pretty extreme limitations on the flexibility of the C code inside the kernel)

(2) Security: Package manager vulnerabilities would result in full kernel compromise

(3) It would actually reduce flexibility, because package manager modifications mean recompiling a kernel.

(4) Not even the kernel is immune from ABI changes. It will not solve the problem.

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=awakatanka]Well i think you very wrong. I'm working in it doing support and repairs. And lots of people install, heck how do you think lots of people have problems with spyware and other prg's, because they hear from friends he mate thats a cool prg you have to try that, so don't say normal people don't install because you realy don't know what the normal desktop people do.[/QUOTE]

Thanks for giving the non-techinical reason why many resist something like Autopackage.

I'm not going to say this is my own opinion (or anyone here), but maybe instead of "most users do not install software" some in the community believe it should be "most users should not install software not from some trusted source (aka a repo) because most users have no idea what they are doing with computers."

> 
(k)ububtu is targeting the desktop users so they have to make it user friendly and easly to install also for prgs outside the repository.

I don't see how those go together.

Let me put it this way:

THINGS NOT IN THE REPO ARE NOT RELEASED FOR YOUR OS YET! YOUR OS IS UBUNTU! TILL AN UBUNTU PACKAGE IS MADE IT IS NOT RELEASED FOR UBUNTU- JUST LIKE WHEN NO EXE IS MADE A PROGRAM IS NOT RELEASED FOR WINDOWS. YOU ARE USING A LESS POPULAR OS, SO THERE ARE LESS PEOPLE PACKAGING THINGS. YOU EITHER HAVE TO DEAL WITH THAT FACT, MESS WITH UNSUPPORTED STUFF LIKE AUTOPACKAGE, OR GO BACK TO ANOTHER OS THAT IS MORE POPULAR (aka packages first day).

It seems to me the essential problem is that no distro is big enough to warrent the effort of making a package the first day like Windows and OSX. So some want some magic bridge to tie the Linux Desktops together so that they can get the userbase needed to get packages the day of first release.

I think in the end this will be actually solved when one distro gets so big on the Linux desktop that it warrents packages the first day of release from major projects. But I am probably very wrong.

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=poofyhairguy]Thanks for giving the non-techinical reason why many resist something like Autopackage.

I'm not going to say this is my own opinion (or anyone here), but maybe instead of "most users do not install software" some in the community believe it should be "most users should not install software not from some trusted source (aka a repo) because most users have no idea what they are doing with computers."



I don't see how those go together.

Let me put it this way:

THINGS NOT IN THE REPO ARE NOT RELEASED FOR YOUR OS YET! YOUR OS IS UBUNTU! TILL AN UBUNTU PACKAGE IS MADE IT IS NOT RELEASED FOR UBUNTU- JUST LIKE WHEN NO EXE IS MADE A PROGRAM IS NOT RELEASED FOR WINDOWS. YOU ARE USING A LESS POPULAR OS, SO THERE ARE LESS PEOPLE PACKAGING THINGS. YOU EITHER HAVE TO DEAL WITH THAT FACT, MESS WITH UNSUPPORTED STUFF LIKE AUTOPACKAGE, OR GO BACK TO ANOTHER OS THAT IS MORE POPULAR (aka packages first day).

It seems to me the essential problem is that no distro is big enough to warrent the effort of making a package the first day like Windows and OSX. So some want some magic bridge to tie the Linux Desktops together so that they can get the userbase needed to get packages the day of first release.

I think in the end this will be actually solved when one distro gets so big on the Linux desktop that it warrents packages the first day of release from major projects. But I am probably very wrong.[/QUOTE]


Ooops. Caps lock.

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=aysiu]
Whenever someone posts here saying, "Yeah, how do I install such-and-such a program. I can't find it in Synaptic anywhere," my reactions are always:

1. How the hell did this person even know about that program? I've never heard of it.
2. I'm so glad I don't need programs like that. All my needs are met by programs in Synaptic.
[/QUOTE]

It happens to me a lot. No big deal- thats what Alien is for!

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=awakatanka]The forums of distro's are filled with windows nerds that wanna try linux desktop because they heard about the freedom and tweaking possibility's but after a few try's with compiling a source our finding debs for prgs that are not in repository they leave and go back to there (illigale)windows because its a simple click work for them.  You can simply say they are to lazy to stick and learn our you can make it actractive for them and they will stay. 
[/QUOTE]

Until they try to run the newest stolen Windows program or game and it does not work then its "back to Windows!" (tm).

---

### Post by awakatanka on 2005-12-19
[QUOTE=poofyhairguy]
Let me put it this way:

THINGS NOT IN THE REPO ARE NOT RELEASED FOR YOUR OS YET! YOUR OS IS UBUNTU! TILL AN UBUNTU PACKAGE IS MADE IT IS NOT RELEASED FOR UBUNTU- JUST LIKE WHEN NO EXE IS MADE A PROGRAM IS NOT RELEASED FOR WINDOWS. YOU ARE USING A LESS POPULAR OS, SO THERE ARE LESS PEOPLE PACKAGING THINGS. YOU EITHER HAVE TO DEAL WITH THAT FACT, MESS WITH UNSUPPORTED STUFF LIKE AUTOPACKAGE, OR GO BACK TO ANOTHER OS THAT IS MORE POPULAR (aka packages first day).

[/QUOTE]
Atleast i can simply click setup.exe if i find a cool new app. :P

But bottemline you right ;) we have to depend on ubuntu to get it in.

Peace and love.

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=awakatanka]
Peace and love.[/QUOTE]

Ditto.

---

### Post by r4ik on 2005-12-19
[QUOTE=poptones]Where did I do that?

Somewhere around here there is even a thread about BDI - the "brand dead installer."

Some of you take too much of what I say way too seriously. I'm not Rush Limbaugh; I'm more like a belligerent Bill Murray.[/QUOTE]

Oke get the piont let's forget about it.

---

### Post by neighborlee on 2005-12-19
[QUOTE=poofyhairguy]Thanks for giving the non-techinical reason why many resist something like Autopackage.

I'm not going to say this is my own opinion (or anyone here), but maybe instead of "most users do not install software" some in the community believe it should be "most users should not install software not from some trusted source (aka a repo) because most users have no idea what they are doing with computers."



I don't see how those go together.

Let me put it this way:

THINGS NOT IN THE REPO ARE NOT RELEASED FOR YOUR OS YET! YOUR OS IS UBUNTU! TILL AN UBUNTU PACKAGE IS MADE IT IS NOT RELEASED FOR UBUNTU- JUST LIKE WHEN NO EXE IS MADE A PROGRAM IS NOT RELEASED FOR WINDOWS. YOU ARE USING A LESS POPULAR OS, SO THERE ARE LESS PEOPLE PACKAGING THINGS. YOU EITHER HAVE TO DEAL WITH THAT FACT, MESS WITH UNSUPPORTED STUFF LIKE AUTOPACKAGE, OR GO BACK TO ANOTHER OS THAT IS MORE POPULAR (aka packages first day).
[/QUOTE]

yea lets stick our heads in the sand and be anal about it cause that is the linux way isn't it..most distros have had various features for sometime yet debian ( or their dervitatives) plunder along without them cause well we all know it aint important cause if debian says so it must be true ( or fedora or whomever adheres to policies that makes OS's 'hard' to use or 'un-windows like : read> ease-of-use ). Mandrake ( do not read into this Im advocating using mandriva ) has ( so has suse ) had ability to install stuff from internet for quite sometime and they even handle dependencies in the process unlike fedora.

You helped make some points ...vendors/developers are agas at making things work everywhere because of the nightmare that represents in doing so, which makes things like klik < my preferred method, - or smartrpm or whatever all the more important.  I wont try to argue that windows is a safe environment and all that..there are apps that 'spy' or 'infect' of course...but windows users typically ( and fairly so based on download stats ) take that chance cause there is a wealth of 'safe' apps out there, and well there are other 'apps' that protect from those that otherwise aren't safe ;-).  In linux we have something called the 'root' account . ( which is entirey safe long as you use something sane for your password )

Its foolhardy to have a discussion around the merits  of not using something like gdebi or klik ..people have the right to download something ( need we talk about CNR ?..no I didn't think so > ) and install it with a simple click or two ( we want to attraCt the windows crowd that prefers ease of use dont we ? 

I am a little weary of reading posts from actual community members that seem to not want to make things easier for people.  Take your CLI and go do something.  I am  even more weary of reading posts from people that seem to indicate its "okay' to act like an arse and still have linux be considered a  decent alternative from some other OS. There should be a law against it. If you can't 'behave' yourself ( you know who you are ) then by all means,- avoid forums and IRC, cause no one wants to listen to your diatribe ramblings of childishness. 

I dont, windows converts surely dont and its just bad PR and plain unfeeling.
( so if you dont feel liike being a 'feeling' person then maybe you should not post until you've had some milk and cookies or something )

Using linux does not give you a license to be petty and mean.

...and we wonder why our market share is still in single digits.


cheers
nl

---

### Post by leech on 2005-12-19
Here's an idea, instead of whining about Autopackage, why don't we just create a web page in the same style as download.com or whatever other place that windows users generally get their shareware software from, and then start putting in entries for free software that is available through the repositories (sort of a freshmeat.net, but for Ubuntu) and have it then integrate with Synaptic or add/remove programs.  This will be similar to Xandros Networks and the Click N Run from Linspire, except through a web interface.  We could have screenshots and feature lists on the page.  

That would replace the "Well, I can't just go to a page and download software for Ubuntu"  Then we could put the web page into a bookmarks package so that it'll pop up on Firefox/Konqueror/Epiphany etc.  Just have it called [www.ubuntusoftware.com](www.ubuntusoftware.com) or whatever.  

I am considering developing this.  Anyone know how to get a job working for Canonical?  :D

Leech

---

### Post by Knomefan on 2005-12-19
First off, calm down. This is just a stupid forum discussion.

> **neighborlee]yea lets stick our heads in the sand and be anal about it cause that is the linux way isn't it
[/quote]
No, it isn't. In fact there is no linux way and claiming that the things you don't like are the linux way is very unfriendly towards the people who try to make Gnu/Linux more userfriendly and actually don't stick their heads in the sand when it come to problems.

[QUOTE=neighborlee]
..most distros have had various features for sometime yet debian ( or their dervitatives) plunder along without them cause well we all know it aint important cause if debian says so it must be true ( or fedora or whomever adheres to policies that makes OS's 'hard' to use or 'un-windows like : read> ease-of-use ).
[/quote] You complain about diatribe ramblings of others and yet you write something like this? Seriously, there are probably a lot of things that could be better in debian and fedora, but accusing them of intentionally making things hard to use in order to be un-windows like is just childish.

[QUOTE=neighborlee]
Mandrake ( do not read into this Im advocating using mandriva ) has ( so has suse ) had ability to install stuff from internet for quite sometime and they even handle dependencies in the process unlike fedora.
[/quote]
There's nothing wrong with advocating mandriva. It's a great distro in my experience. And there have been programs for debian systems that do exactly what you describe for quite some time. But you'll be happy to learn that gdebi, a tool that will allow you to install debs downloaded from the net will be in dapper.

[QUOTE=neighborlee]
You helped make some points ...vendors/developers are agas at making things work everywhere because of the nightmare that represents in doing so, which makes things like klik < my preferred method, - or smartrpm or whatever all the more important.
[/quote]
Where did you get this idea?

[QUOTE=neighborlee]
I wont try to argue that windows is a safe environment and all that..there are apps that 'spy' or 'infect' of course...but windows users typically ( and fairly so based on download stats ) take that chance cause there is a wealth of 'safe' apps out there, and well there are other 'apps' that protect from those that otherwise aren't safe  said:**
> 
Huh? How does having a root account help if you install stuff as root? Root also doesn't prevent something that you install as a user messing up your home directory.
And I seriously doubt that the concept of having apps that protect you from other apps is a good one, judging from the virus and spyware infected monsters I regularly see.

[QUOTE=neighborlee]
Its foolhardy to have a discussion around the merits  of not using something like gdebi or klik ..people have the right to download something ( need we talk about CNR ?..no I didn't think so > ) and install it with a simple click or two ( we want to attraCt the windows crowd that prefers ease of use dont we ? 

So you know about gdebi? Hm, now I have an even harder time understanding the stuff you wrote earlier.
And I don't think the issue is wether people have a right to install stuff with a simple click, the issue is making installing software as easy, convenient and safe as possible and though it has it's limitations, apt with a nice frontend like CNR, or gnome-app-install is pretty good when it comes to this imho.

> **neighborlee]
I am a little weary of reading posts from actual community members that seem to not want to make things easier for people.  Take your CLI and go do something.  
[/quote]
I agree with you, yet I do get the impression that you might also put people who simply disagree with you about how to make thing easier into this category and that wouldn't be fair.

[QUOTE=neighborlee]
If you can't 'behave' yourself ( you know who you are ) then by all means,- avoid forums and IRC, cause no one wants to listen to your diatribe ramblings of childishness. 
[/quote]
Hm, judging from my experience, forums and IRC seem to be exactly the place for people who can't behave themselves.  said:**
> 
Using linux does not give you a license to be petty and mean.

It doesn't? Sh***
Do I have to run BSD then? :D
Seriously, relax, there are idiots within every community, the community of people using linux is not an exception.

[QUOTE=neighborlee]
...and we wonder why our market share is still in single digits.
[/QUOTE]
I'm sure there are a lot of reasons, I doubt though that stupid posts in some linux forum feature very prominently among them.

---

### Post by neighborlee on 2005-12-19
> **Knomefan]First off, calm down. This is just a stupid forum discussion.

yeah your right its a bit stupid...

> 
No, it isn't. In fact there is no linux way and claiming that the things you don't like are the linux way is very unfriendly towards the people who try to make Gnu/Linux more userfriendly and actually don't stick their heads in the sand when it come to problems.
==============
the linux way can be unruly aS we all know..linspire is a good example of something that is easy to use albeit not free and clealry not for everyone, but clearly they have a good model.

> You complain about diatribe ramblings of others and yet you write something like this? Seriously, there are probably a lot of things that could be better in debian and fedora, but accusing them of intentionally making things hard to use in order to be un-windows like is just childish.

you dont think its intentional to avoid supermount-ng type behavior when clearly most 'all' the other distros have had this for like ages ? ..this doesn't seem rather odd to you ? ( but I guess    certain developers know better than others dont they )

> 
There's nothing wrong with advocating mandriva. It's a great distro in my experience. And there have been programs for debian systems that do exactly what you describe for quite some time. But you'll be happy to learn that gdebi, a tool that will allow you to install debs downloaded from the net will be in dapper.

I see , well thats certainly a good step in the right direction and Im glad to hear it.

> 
And I don't think the issue is wether people have a right to install stuff with a simple click, the issue is making installing software as easy, convenient and safe as possible and though it has it's limitations, apt with a nice frontend like CNR, or gnome-app-install is pretty good when it comes to this imho.

I never said synaptic wasnt kewl or useful  (although I know its being enhanced to be more CNR like ? ) , just that alternatives are necessary to accomodate end users needs  said:**
> 
I agree with you, yet I do get the impression that you might also put people who simply disagree with you about how to make thing easier into this category and that wouldn't be fair.

nope I dont, I just advocate decisions based on making linux compete broadly.

> 
Hm, judging from my experience, forums and IRC seem to be exactly the place for people who can't behave themselves. ;)
In other words, it's sometimes a good idea not to take some people too seriously.

I dont see where friendly comes into play there , but then clearly YMMV I guess.

LInus hit the nail on the proverbial head with his gnome comments, and if something doesn't change I can see a dead project in the works .  Cooporate america doesn't exist to tell users what is best for them because the two dont necessarily mix.

Im glad someone finally spoke up, and that it was Linus is all the more telling.

cheers
nl

---

### Post by neighborlee on 2005-12-19
[QUOTE=leech]Here's an idea, instead of whining about Autopackage, why don't we just create a web page in the same style as download.com or whatever other place that windows users generally get their shareware software from, and then start putting in entries for free software that is available through the repositories (sort of a freshmeat.net, but for Ubuntu) and have it then integrate with Synaptic or add/remove programs.  This will be similar to Xandros Networks and the Click N Run from Linspire, except through a web interface.  We could have screenshots and feature lists on the page.  

That would replace the "Well, I can't just go to a page and download software for Ubuntu"  Then we could put the web page into a bookmarks package so that it'll pop up on Firefox/Konqueror/Epiphany etc.  Just have it called [www.ubuntusoftware.com](www.ubuntusoftware.com) or whatever.  

I am considering developing this.  Anyone know how to get a job working for Canonical?  :D

Leech[/QUOTE]


That would be a nice addition to any distro ;-)

Klik already does most of this and frankly I love the underlying structure.  I dont want to discourage you from doing something good for the community, but I think linux as a whole needs something all distros can use, thereby giving linux standardization along with LSB.

My suggestion ( along with your ubuntu software idea ) is to help KLIK make the UI provide more visual information ;-) ( I think CNR is wonderful myself but the pricing structure does leave some out of the loop ).

cheers
nl

---

### Post by leech on 2005-12-19
> **neighborlee]you dont think its intentional to avoid supermount-ng type behavior when clearly most 'all' the other distros have had this for like ages ? ..this doesn't seem rather odd to you ? ( but I guess    certain developers know better than others dont they )[quote]

Supermount, last I checked, was quite broken.  Most of the time while I was using Mandrake, I was lucky of mounting worked at all.  Supermount is a hack, a bad one at that.  Besides, with hal/dbus/gnome-volume-manager mounting CD/DVDs and external storage works quite nicely.  They weren't intentionally making things unfriendly.  They were working on a better solution to the problem.


[quote=neighborlee]I never said synaptic wasnt kewl or useful  (although I know its being enhanced to be more CNR like ? ) , just that alternatives are necessary to accomodate end users needs  said:**
> 

Where did you hear that?  It doesn't really need to, Ubuntu already has their add applications program, and people who use standard Debian can use Synaptic anyhow.  I like that Synaptic shows everything.

[quote=neighborlee]LInus hit the nail on the proverbial head with his gnome comments, and if something doesn't change I can see a dead project in the works .  Cooporate america doesn't exist to tell users what is best for them because the two dont necessarily mix.

Im glad someone finally spoke up, and that it was Linus is all the more telling.

cheers
nl

Except that Linus is a tweaker by nature.  I've been trying to like KDE for the past few days (and I try it everytime there is a new release) but it's just not friendly at all.  It's usable only if you accept defaults and never change the layout of anything.  But then that's what Gnome excels in.  They have a good default, whereas KDE has a Windows-Like default (which in my mind makes it bad).  I downloaded and installed kwin-baghira (ok, the package's dependencies are broken in Dapper, so I had to 'apt-get source -b kwin-baghira' and it worked), and it literally took me hours to get the theme working with brushed metal working.  Between having different dialogs for Window Decorations and style, then also having two different places for the shading effects....  KDE's dialogs are bloated and very unorganized.  In Gnome I could make it have the Brushed theme in about 5 minutes (counting time to download the themes)

KDE 4 is working more towards the goal of having simplified dialogs.  Personally I think the best course for both Gnome and KDE to do would be to have a Advanced, Intermediate and Beginner level.  At least that way you can have it tweakable, or not so much, or have it much like Gnome is now.  KDE already has a first-time wizard, as does Fedora Core 4 for it's Gnome.  

Leech

---

### Post by leech on 2005-12-19
[QUOTE=neighborlee]That would be a nice addition to any distro ;-)

Klik already does most of this and frankly I love the underlying structure.  I dont want to discourage you from doing something good for the community, but I think linux as a whole needs something all distros can use, thereby giving linux standardization along with LSB.

My suggestion ( along with your ubuntu software idea ) is to help KLIK make the UI provide more visual information ;-) ( I think CNR is wonderful myself but the pricing structure does leave some out of the loop ).

cheers
nl[/QUOTE]

It actually wouldn't be all that hard to include support for other distros.  Just include along with the package description include links to the packages.  

I'm thinking something along the lines of a wiki, where people can submit their own programs and/or packages as well.  There are several websites out there already for rpms, etc.  But none that really put everything in one place.  For example, rpm.net will show the various rpms, and has a brief description of the program, but it doesn't include screenshots or a features list.

Leech

---

### Post by scaine on 2005-12-19
So lets just recap, will we?

1.  We (mostly) don't like Autopackage.
2.  We (mostly) don't like klik.
3.  Synaptic will only allow installation of software in the repos, which is far from a complete list, but at least ensures compatibility with your distro.  Of course, there's very little third-party, pay-for-it software in there.
4.  Gdebi is on the way which is a in-between app which will allow a GUI install of a deb file from the internet.  Who knows?  This might enourage those third parties to offer deb files the way (nearly) everyone offers rpms.
5.  Many, many people think that having *any* form of nice GUI front end for non-repo software is a terrible idea.  That this will fundamentally increase support and quite possibly lead to a horrible, spyware infested, windows-like world.

Have I missed any options there?  I suppose there's one worth mentioning - someone did indeed shoot down in flames my suggestion that a simple linux installer must exist if only for games.  The reason?  We should not be playing games in Ubuntu - games should have their own platform.  Sadly, I already have that platform - it's called Windows.

Just to sum up my own view - despite the various problems it certainly represents, I doubt that Ubuntu (or any linux distro) will be anything more than a niche O/S on the desktop without a simple to use installer.

Just to clarify that : "On the desktop" for me, includes household use.  For others, perhaps it's just desktop use in the corporate (which might explain the above "gaming-platform" comment).

So, for the second time in over 200 posts, I'm ducking out of this discussion.  I have no hope left alive from reading all this that we'll see an easy way to install non-repo linux software.  None at all - this thread has surely crushed it completely.  Here's hoping GDebi lights the way.

---

### Post by leech on 2005-12-19
[QUOTE=scaine]So lets just recap, will we?

1.  We (mostly) don't like Autopackage.
2.  We (mostly) don't like klik.
3.  Synaptic will only allow installation of software in the repos, which is far from a complete list, but at least ensures compatibility with your distro.  Of course, there's very little third-party, pay-for-it software in there.
4.  Gdebi is on the way which is a in-between app which will allow a GUI install of a deb file from the internet.  Who knows?  This might enourage those third parties to offer deb files the way (nearly) everyone offers rpms.
5.  Many, many people think that having *any* form of nice GUI front end for non-repo software is a terrible idea.  That this will fundamentally increase support and quite possibly lead to a horrible, spyware infested, windows-like world.

Have I missed any options there?  I suppose there's one worth mentioning - someone did indeed shoot down in flames my suggestion that a simple linux installer must exist if only for games.  The reason?  We should not be playing games in Ubuntu - games should have their own platform.  Sadly, I already have that platform - it's called Windows.

Just to sum up my own view - despite the various problems it certainly represents, I doubt that Ubuntu (or any linux distro) will be anything more than a niche O/S on the desktop without a simple to use installer.

Just to clarify that : "On the desktop" for me, includes household use.  For others, perhaps it's just desktop use in the corporate (which might explain the above "gaming-platform" comment).

So, for the second time in over 200 posts, I'm ducking out of this discussion.  I have no hope left alive from reading all this that we'll see an easy way to install non-repo linux software.  None at all - this thread has surely crushed it completely.  Here's hoping GDebi lights the way.[/QUOTE]

The Loki installer works fine for games, if that's all you want an installer for, and is pretty much universally used for all the commercial linux games.

Leech

---

### Post by lithorus on 2005-12-19
The idea to make a ubuntusoftware.com is really good and constructive. Ubuntu/Debian could really use a "packages.ubuntu.com" for regular people, with screenshots, comments. Sorta like gnomefiles.org. About 75%(just a wild guess) of the repo packages are libraries which most people couldn't care less about(and shouldn't, since they are installed automatically when needed).

---

### Post by poptones on 2005-12-19
> Cooporate america doesn't exist to tell users what is best for them because the two dont necessarily mix.

I assume you mean "corporate" and you're completely wrong. "Corporate america" exists **completely** on "telling people what is best for them." it's called advertising and it's not just those toothpaste and butt cream sales pitches you see in between *the other ads* that tell people what's best for them - adverts like "Survivor" and "CSI" and "Law and Order" and "West Wing" and "Shrub's State of the Union" and "The Nine O'clock News."

> We should not be playing games in Ubuntu - games should have their own platform. Sadly, I already have that platform - it's called Windows.

Then don't you already have a "platform" for everything else calle windows? advocating a platform doesn't mean that platform should not be open source. How about if you want a "platform" to run your CNC machine? Windows doesn't have one (unless you pay some manufacturer a butt load of money for add-ons) but there is a free and open "platform" in linux that will dedicate any pc to the task of running a multi axis milling machine. There are also several "platforms" (distributions) dedicated to media - to video and to sound. There's also "platforms" dedicated to providing administrators a bootable diagnostic and recovery tool.

These all exist because they are all specialized tasks - milling machines and audio/video apps require low latency, highly "interactive" i/o. Bootable cds require very good platform detection and conservative driver setups so as to work with as much hardware as possible. 

And *videogames* are every bit as demanding as audio, video, and milling machines - but even more because they have to calculate and render complex calculations. How does it make sense to load up a desktop machine with all the overhead requirements of a proper game machine? It doesn't - especially when there are multiple ways to run more than one operating system on a machine.

"Write once run everywhere" is for managed code. If this is what you want start shopping for java and mono apps (and don't complain when they are bogged down in uniformly ugly, lowest common denominator interfaces and sluggish behavior). In another few years even that won't matter since the cpus will support virtualization at the core level and you'll be able to run five operating systems all at once on the same machine anyway - install redhat, suse and ubuntu and install whatever you want.

Oh, but I forgot: most of you are so paranoid about that you'll never buy such machines... never mind those very popular game machines everyone loves are already full of that perceived "big brother" technology.

Some of you really need to get over this "linux way." The whole point is *there is no linux way* because "linux" isn't owned by any individual. Linux is just a toolkit that many different entities employ in the creation of *their own tools*. There are a thousand differnt kinds of hammers and you cannot use them all interchangeably; despite the fact a "hammer" amount to nothing more than a stick attached to a heavy weight, and despiote the fact you can go to the hardware store and buy a new "stick" and the wedge to attach it that will work with **some** hammerheads,  you will never be able to swap parts between all of them. Expecting even that level of interchangeability between tools that are infinitely more complex is absurd.

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=scaine]So lets just recap, will we?

1.  We (mostly) don't like Autopackage.
2.  We (mostly) don't like klik.
3.  Synaptic will only allow installation of software in the repos, which is far from a complete list, but at least ensures compatibility with your distro.  Of course, there's very little third-party, pay-for-it software in there.
4.  Gdebi is on the way which is a in-between app which will allow a GUI install of a deb file from the internet.  Who knows?  This might enourage those third parties to offer deb files the way (nearly) everyone offers rpms.
5.  Many, many people think that having *any* form of nice GUI front end for non-repo software is a terrible idea.  That this will fundamentally increase support and quite possibly lead to a horrible, spyware infested, windows-like world.

Have I missed any options there? [/QUOTE]

6. Some people think that Autopackage is great for limited use (aka me). Its a good idea for closed thrid party stuff- the Loki Installer is quite old.

> 
I suppose there's one worth mentioning - someone did indeed shoot down in flames my suggestion that a simple linux installer must exist if only for games.  The reason?  We should not be playing games in Ubuntu - games should have their own platform.  Sadly, I already have that platform - it's called Windows.

Or a console.

> 
Just to sum up my own view - despite the various problems it certainly represents, I doubt that Ubuntu (or any linux distro) will be anything more than a niche O/S on the desktop without a simple to use installer.

Does gdebi do the job for you? Or do you think desktop Linux needs the multi-distro bridge to compete?

> 
So, for the second time in over 200 posts, I'm ducking out of this discussion.  I have no hope left alive from reading all this that we'll see an easy way to install non-repo linux software.  None at all - this thread has surely crushed it completely.  Here's hoping GDebi lights the way.

I use both Klik and Autopackage for fun. For some things they work ok. In fact, Klik is a brilliant idea.

---

### Post by leech on 2005-12-19
[quote=poptones]Oh, but I forgot: most of you are so paranoid about that you'll never buy such machines... never mind those very popular game machines everyone loves are already full of that perceived "big brother" technology.[/quote]

I agree with everything you said but this, there is a difference with having that crap in your computers where your data is.  On the one hand someone could find out how much porn your downloading and from where, on the other hand, what are they going to get off of your game console, your high score in Pac Man?

All that DRM, Trusted Computing crap is like hardware level spyware, no thank you.  I'm not really all that worried about it myself, since anyone with a brain the size of a pea will know that it'll be hacked within a week at most.

Leech

---

### Post by poptones on 2005-12-19
*I agree with everything you said but this, there is a difference with having that crap in your computers where your data is. On the one hand someone could find out how much porn your downloading and from where, on the other hand, what are they going to get off of your game console, your high score in Pac Man?*

So use encryption **yourself**. I do. You can run vmware or wine, stick windows in its own encrypted partition, filter it through whatever iptables firewalls you want and the linux host will remain pretty much completely secure no matter how infested "windows" becomes. When the new virtualization tech gets here it will be even more transparent and apis will most certainly be constructed to allow dbus-type connectivity between multiple os hosts running on the same machine (or distributed over local encrypted nets). 

Look, that's really a (slightly) different discussion and perhaps I should not have mentioned it. I was just making a point that there is no "linux way" of doing things - tcpa is very controversial and even stallman speaks out the party line rhetoric about "freedom," yet there are those of us who are not so knee jerk and realize there are legitimate uses for this technology in the context of **preserving liberty** - in fact this technology, properly applied, can do more to that end than any technology of the last century because it would allow collectives to communicate, on a large scale, with relative security. 

"The linux way" (at least the "mainstream linux way") is to smash this new technology without even bothering to learn how to apply it - yet there are **Free software advocates** who also realize you *can* develop free software in a "trusted" context; so long as the "key" is attached to the hardware (and, for example, the user has the ability to "reset" the hardware by making it create new keys even though the user himself cannot access those keys) *Free software* can exist because you and I, for example, can both compile the same code, using the same settings, and thereby verify one another's work.

---

### Post by poofyhairguy on 2005-12-19
> **neighborlee]yea lets stick our heads in the sand and be anal about it cause that is the linux way isn't it..most distros have had various features for sometime yet debian ( or their dervitatives) plunder along without them cause well we all know it aint important cause if debian says so it must be true ( or fedora or whomever adheres to policies that makes OS's 'hard' to use or 'un-windows like : read> ease-of-use ). Mandrake ( do not read into this Im advocating using mandriva ) has ( so has suse ) had ability to install stuff from internet for quite sometime and they even handle dependencies in the process unlike fedora.[/QUOTE]

Gdebi is made to solve this problem. Sounds good to me- I like Gnome GUIs.

>  I wont try to argue that windows is a safe environment and all that..there are apps that 'spy' or 'infect' of course...but windows users typically ( and fairly so based on download stats ) take that chance cause there is a wealth of 'safe' apps out there, and well there are other 'apps' that protect from those that otherwise aren't safe  said:**
> 

Fun part about Ubuntu- I no longer have to worry "whats the motive of the new free app I just found." If its in Synaptic, it has no spyware and no problems for me! 

[QUOTE]
Its foolhardy to have a discussion around the merits  of not using something like gdebi or klik ..people have the right to download something ( need we talk about CNR ?..no I didn't think so > ) and install it with a simple click or two

You have a right to do it if you can. You have no right to demand that someone else makes this solution for you, or that a Linux distro that you do not fund primarily uses it! 


[QUOTE]( we want to attraCt the windows crowd that prefers ease of use dont we ? 

Not at all costs, no.

> 
I am a little weary of reading posts from actual community members that seem to not want to make things easier for people.  Take your CLI and go do something.  

Actually, I am a VERY pro GUI person. Making things easier for people is all fine and good, but there are a least a thousand ways Ubuntu can improve on the topic of ease of use and I think it only makes sense to support the ways that work well with the system!

> 
I am  even more weary of reading posts from people that seem to indicate its "okay' to act like an arse and still have linux be considered a  decent alternative from some other OS. 

We do not represent Linux. Linus himself and his views do not represent Linux. Linux is bigger than we all are. To quote my sig:

"Because Linux is more than just an os.Without overstating it, Linux, and the beliefs behind it, helps us, (in small or large part) define who we are, as individuals, and as a community."

And every community has a few jerks, a few fights and a few black eyes. ITs part of life.

> 
There should be a law against it.  

By whose authority?

> 
If you can't 'behave' yourself ( you know who you are ) then by all means,- avoid forums and IRC, cause no one wants to listen to your diatribe ramblings of childishness.  

If you see clear violations of the Code of Conduct point them out.

> 
I dont, windows converts surely dont and its just bad PR and plain unfeeling.
 

If you don't want to read the rants of others then don't. No one makes you. This is a community of ideas and people- we are not going to cut things out that are "bad for PR."

> 
Using linux does not give you a license to be petty and mean. 

Nor does it give anyone the right to demand more from the Linux community than the community freely gives.

 > 
...and we wonder why our market share is still in single digits.

Considering that no single major computer vendor ships a Linux based Desktop syste, I sure know why the marketshare is what it is.

---

### Post by xombie on 2005-12-19
The future is in the conary type system (wiki.conary.com). They have tools for building a projects files and resolving the dependancy. Essentially they design a python recipe for every projects' tarball. The more sane the projects tarball is the simpler the recipe is. They use path rather than version or epoch as version avoiding all the old package headaches.

I love the system I currently use but the future has potential.

---

### Post by leech on 2005-12-20
[QUOTE=xombie]The future is in the conary type system (wiki.conary.com). They have tools for building a projects files and resolving the dependancy. Essentially they design a python recipe for every projects' tarball. The more sane the projects tarball is the simpler the recipe is. They use path rather than version or epoch as version avoiding all the old package headaches.

I love the system I currently use but the future has potential.[/QUOTE]

The conary system is pretty cool, though right off the bat I noticed one downfall of it.  It's SLOW.  Just like RPM/YUM it's slower than sin to download and install things with.  

Sadly, I was going to try out the new Foresight Linux recently because I like the idea of it.  Unfortunately after the install in VMware, it just choked, as if it didn't install a bootloader, which it should have installed Grub.  Oh well, guess I'll wait for a new release or something.

Leech

---

### Post by awakatanka on 2005-12-20
> **poofyhairguy]Gdebi is made to solve this problem. Sounds good to me- I like Gnome GUIs.
[/QUOTE]
Will there be something like that for kubuntu to? The dapper section is nice to have but most posts i see is for ubuntu there is little info to find for kubuntu. I don't like the gnome os and want my kde klean of gnome appz  said:**
> 
You have a right to do it if you can. You have no right to demand that someone else makes this solution for you, or that a Linux distro that you do not fund primarily uses it!  What the users try is suggest a thing so it makes live easier, and if you look how many times the same topics are reposted there is probably a need for it. But you are right we can never demand but we may try to suggest.


[QUOTE=poofyhairguy]
I suppose there's one worth mentioning - someone did indeed shoot down in flames my suggestion that a simple linux installer must exist if only for games. The reason? We should not be playing games in Ubuntu - games should have their own platform. Sadly, I already have that platform - it's called Windows.

Or a console.[/QUOTE]

I bought a powerfull Computer to do all kind of things, why would i buy a consule to play games that i can play better and easier (MMORPG's )on my computer. Why i need different OS to things on? I would like to have 1 OS that can do all. I would like it if it would be a free OS and not a MS OS that dictate me what kind of appz i need. Real freedom is i can choose what i want to do on my Computer. 

I'm not demanding but hope linux will be that powerfull OS that can do all things i like.


Klik love and peace. 

Btw why there is a seprate kubuntu forum isn't it better to have all forums at the same spot? Now kubuntu users are divided at 2 spots.

---

### Post by asimon on 2005-12-20
> **awakatanka]Will there be something like that for kubuntu to? The dapper section is nice to have but most posts i see is for ubuntu there is little info to find for kubuntu. I don't like the gnome os and want my kde klean of gnome appz  said:**
> 
From [Kubuntu Dapper Package Manager](https://wiki.ubuntu.com/KubuntuDapperPackageManager): "Time permitting we will create a program to install individual .deb files. This would have to check if the dependencies could be resolved and install those or if they are not available install nothing."

So the only thing which is holding this back for Kubuntu is limited resources, i.e. developer time which currently doesn't look as spendid as it does for Ubuntu.

[QUOTE=awakatanka]
Btw why there is a seprate kubuntu forum isn't it better to have all forums at the same spot? Now kubuntu users are divided at 2 spots.
Absolutely, I too would prefer one forum to rule them all, Ubuntu, Kubuntu, Edubuntu, Xubuntu, etc. But anyone can open a new forum and if people flock there there is nothing you really can do.

---

### Post by poofyhairguy on 2005-12-20
> **awakatanka]Will there be something like that for kubuntu to? The dapper section is nice to have but most posts i see is for ubuntu there is little info to find for kubuntu. I don't like the gnome os and want my kde klean of gnome appz  said:**
> 

I bet one day. Mepis has it, so......KDE can do it now.

> 
 What the users try is suggest a thing so it makes live easier, and if you look how many times the same topics are reposted there is probably a need for it. But you are right we can never demand but we may try to suggest.

The problem is:

A. The developers almost never read these forums (too busy for forums) so the crys fall on the ears of those that do nothing.

B. If you read the forums a lot, you notice that there is no one single thing Ubuntu can do to make things easier- almost everyone has their own idea. Almost everyone is shocked that the simple problem they can see that is "holding back Ubuntu" is not solved or fixed. Its 100's of problems when you put them all together.

But you know who usually gets what they want around here? Not those people that make the demands, but the people that do. Many people complained about the lack of menu editing. Nothing happened till someone made SMEG. Many complained about the lack of new apps. Nothing happened till someone made backports. Many are complaining that Ubuntu can't install things from outside the repos with a GUI. Nothing will happen till someone finishes gdebi. There are WAY less Ubunbut developers than everyone thinks and they have their hands tied just trying to put together the best of the free software world (and make it better little by little). Demands made on the forums are worse than silence because all it does is stir up people that understand the true nature of the community.

Like it or not, Linux and the groups behind it are part of a meritocracy- not a business. To get what you want you MUST show you idea has merit (even it it means doing it yourself) before it will be accepted. This is unlike a business that tries to make "the customer" happy. Unless someone on here has paid for support there are no customers on this forum- only users. And users have two options- show the merit behind what they want (and thats not a rant on the forum) or just accept that they will get that when someone else does it or Mark decides one day its worth his money.

Its hard to accept this for many when their whole lives they have been software customers. Thats why so many people who makes demands talk about things like competing with Windows- they are stuck in a mindset where Ubuntu is a business that is trying to compete for usershare at Windows' expense. Its not- Mark has basically said that Ubuntu is at worst a donation to the community and at best maybe a place that will break even (like a non-profit). He cares about competing at some level, but only by making usuable software (and he defines that).

If Ubuntu was a business in the mold of MS, all these demands would make sense. But Ubuntu is a "community based distro"- to get what you want you have to SHOW the community!

And for the record, everything we have talked about in this thread someone IS working on. Autopackage. Klik. Everything. So someone IS out to prove the merit of ideas. So then you have a situation where those making demands are just acting impatient- nothing good can come of that (unless it pushes them so far to help Autopackage or whatever).

[QUOTE]
I bought a powerfull Computer to do all kind of things, why would i buy a consule to play games that i can play better and easier (MMORPG's )on my computer. 

Because you don't use Windows?

> 
Why i need different OS to things on? 

Why can't you play Gamecube games on an Xbox? Same answer- it was not designed for your platform.

> 
I would like to have 1 OS that can do all.

I hate to tell you it, but it exists almost. Its called Windows.

> 
 I would like it if it would be a free OS and not a MS OS that dictate me what kind of appz i need.

The thing is that MS's whole philosophy (right down to the dictatorshipness) is part of the reason it puts a higher emphasis on third party support! 

> 
 Real freedom is i can choose what i want to do on my Computer. 

I say real freedom is being able to sacrifice in order to have choice. Freedom never involves making demands of others.

> 
I'm not demanding but hope linux will be that powerfull OS that can do all things i like.

If you can then jump in and help. Or at least spend some money and buy the games Linux does have to show that people want that. Thats how true change comes.

> 
Klik love and peace. 

Ditto.

> 
Btw why there is a seprate kubuntu forum isn't it better to have all forums at the same spot? Now kubuntu users are divided at 2 spots.

I am not qualified to answer that one.

---

### Post by leech on 2005-12-20
I have put forth some ideas for making a Web based frontend so to speak of repositories for newbies.  [http://www.ubuntuforums.org/showthread.php?t=106360](http://www.ubuntuforums.org/showthread.php?t=106360) go ahead and give it a look over and see if this would help with the "I want to be able to download something off of the web to install on my linux." thought process.  

Leech

---

### Post by poptones on 2005-12-20
> Real freedom is i can choose what i want to do on my Computer. 

Actually, no. Real freedom is **doing** what you want with your computer. That means accepting the responsibility of *learning to do what you want to do* even if it means learning to do for yourself.

"Real freedom" is not demanding (or even needing) others do those things for you.

---

### Post by awakatanka on 2005-12-20
> **poofyhairguy]
Because you don't use Windows?[/QUOTE] I have windows and legal, because my wife does video editing and i like to play some mmorpg. I don't like it when people use copy's because it more or less stealing ( btw i still steal mp3's :P but if i like the album i buy it  said:**
> 
I hate to tell you it, but it exists almost. Its called Windows. You right but i still will dream that linux will be that one day.  


> **poofyhairguy]
I say real freedom is being able to sacrifice in order to have choice. Freedom never involves making demands of others.[/quote] I will never demand, but discusse something can bring sometimes goodthings.



[QUOTE=poofyhairguy]
If you can then jump in and help. Or at least spend some money and buy the games Linux does have to show that people want that. Thats how true change comes.[/quote] If i could program i would surly help, but all that i can is solve other peoples window mess  said:**
> 
I am not qualified to answer that one.Hehe can understand but may be you can give them a hint. Think its better to have a close community then a devided one on seprate boards.

Btw it's one of the best community's i have seen in linux land, on some other communtity you see alot of RTFM answers.

---

### Post by awakatanka on 2005-12-20
[QUOTE=poptones]Actually, no. Real freedom is **doing** what you want with your computer. That means accepting the responsibility of *learning to do what you want to do* even if it means learning to do for yourself.

"Real freedom" is not demanding (or even needing) others do those things for you.[/QUOTE]
Learning i do, but i can see why some people try and leave after a couple of hard times with compiling a sources. Not everyone has the power to do that. And from what i read we will have a good prg with that gdebi. Hope the 3th party Programmers will put (k)ubuntu debs also on there site then. And hopping people will stick a bit longer on (k)ubuntu and give it a change, because its a good distro that deserve more users.
[QUOTE=leech]I have put forth some ideas for making a Web based frontend so to speak of repositories for newbies.  [http://www.ubuntuforums.org/showthread.php?t=106360](http://www.ubuntuforums.org/showthread.php?t=106360) go ahead and give it a look over and see if this would help with the "I want to be able to download something off of the web to install on my linux." thought process.  

Leech[/QUOTE]
Hope there will be more people like you. Great idea

---

### Post by leech on 2005-12-20
[QUOTE=awakatanka]Hope there will be more people like you. Great idea[/QUOTE]

Thanks.  I think I pretty much covered all the bases.  But of course I believe in the by the People, for the People....so any help on this would be appreciated.  I think it could go a long way towards helping make linux more friendly.

Leech

---

### Post by poofyhairguy on 2005-12-20
> **awakatanka]
 You right but i still will dream that linux will be that one day.  [/QUOTE]

Nothing wrong with a dream.

> 
 I will never demand, but discusse something can bring sometimes goodthings.


My rant was not direct at you on that point. Discussion can be helpful, but not if it raises expectations needlessly.

[QUOTE]
 If i could program i would surly help, but all that i can is solve other peoples window mess  said:**
> 

And file bug reports. That really how a normal user can help.

[QUOTE]
Hehe can understand but may be you can give them a hint. Think its better to have a close community then a devided one on seprate boards.

I can't even do that much. I am the staff member that tries to keep the communication ties open and some words might endanger that.

---

### Post by poptones on 2005-12-21
*Nothing wrong with a dream.*

A dream of linux becoming windows?

I disagree utterly.

---

### Post by leech on 2005-12-21
[QUOTE=poptones]*Nothing wrong with a dream.*

A dream of linux becoming windows?

I disagree utterly.[/QUOTE]

I think he meant that it was a dream for linux to have as much commercial (i.e. games) support as windows.  If linux ever became like windows, I think I'd have to sell my computer and go back to using an Atari ST :D  Or maybe just get one of those new Amigas (if they ever come out).  

I just don't see that happening since Linux is all about choice, and it's the choice of most people who use linux not to use windows for one reason or another....

Leech

---

### Post by Burning Bronx on 2005-12-21
I remember when I read the first Autopackage topic for Breezy development branch. The answer was a hard and conclusive "No". The way Autopackage works is not suitable. It's something just as bad as those exe files that keep screwing up the PCs of innocent Windows user downloading random software. *shrugs* Or even worse cause it "could" (not quite correct - eventually it will) mess dependencies

---

### Post by leech on 2005-12-21
[QUOTE=Burning Bronx]I remember when I read the first Autopackage topic for Breezy development branch. The answer was a hard and conclusive "No". The way Autopackage works is not suitable. It's something just as bad as those exe files that keep screwing up the PCs of innocent Windows user downloading random software. *shrugs* Or even worse cause it "could" (not quite correct - eventually it will) mess dependencies[/QUOTE]

Exactly!  Which is why I'm proposing something that up front looks like a typical website for windows software, except that it works with gdebi/synaptic/apt as a backend.

By the way, I think your sig is a little off, gdebi doesn't own over dpkg, it's just a frontend for it and apt.  It uses apt for dependency resolution and of course apt is just a program that uses dpkg to install it.  But I do get your meaning that gdebi is much easier to use to install things than opening a terminal and typing 'sudo dpkg -i <package name>' then having to work out dependencies on your own.

Leech

---

### Post by Burning Bronx on 2005-12-21
/* offtopic Actually I like dpkg more than gdebi. The only reason I am using it is cause I am too lazy to fix my dependencies ;P I was using this sig to encourage gdebi testing and just modified it when it went to Universe... I think I will remove it these days ;) */

 As for your idea about a web based repo... well unless you suggest it to devs and they embrace it (hard stuff) it will remain only an idea.

---

### Post by leech on 2005-12-21
The beauty of it is that the devs would never have to embrace it.  And I don't intend for it to be just for Ubuntu, though I think with Ubuntu's tools, it'd be easiest to get it working right.  Initially that's where it's going to be though.  At the core of it, it's just a prettier and easier to use frontend to packages.ubuntu.com

Leech

---

### Post by Burning Bronx on 2005-12-21
So if the devs don't have to embrace it who's gonna do it? You? And who's gonna maintain the package database? Hmmm... no offence but that sounded weird.

---

### Post by codejunkie on 2005-12-21
i may be butting in on this conversation, but leech are you talking about maybe writing something like a firefox extension that would send the command to apt when you click the html link and apt would install the software from the repos?

---

### Post by Jengu on 2005-12-21
Most of my points have gone unanswered so I won't reiterate them.

But for those of you most worried that it will muck with the native packaging system, the autopackage team has begun integration work. I think the core developer, Mike Hearn, actually runs Ubuntu, so I'd expect dpkg to be one of the first supported. Also, autopackage already backs up any files it's going to overwrite so you can restore them if it messes up your packager.

Finally -- Inkscape 0.43 and Firefox 1.5 installed with autopackage work perfectly for me. The obstinate among you can stay happy with the buggier Inkscape 0.42 and the slower Firefox 1.0.6, or waste your own time compiling them from source. I had previously followed the Firefox 1.5 Howto in the tips and tricks forum -- which broke flash. The autopackage did not. Still waiting to see some manifestation of the dependency hell that's supposed to ensue by me typing this from the latest version.

[Click here for Inkscape 0.43](http://inkscape.modevia.com/ap/inkscape-0.43.x86.package)
[Click here for Firefox 1.5](http://www.wildgardenseed.com/Taj/autopackage/firefox-1.5.x86.package)

P.S. You know those things called rpms? They allow arbitrary code execution too.

---

### Post by codejunkie on 2005-12-21
[QUOTE=Jengu]Most of my points have gone unanswered so I won't reiterate them.

But for those of you most worried that it will muck with the native packaging system, the autopackage team has begun integration work. I think the core developer, Mike Hearn, actually runs Ubuntu, so I'd expect dpkg to be one of the first supported. Also, autopackage already backs up any files it's going to overwrite so you can restore them if it messes up your packager.

Finally -- Inkscape 0.43 and Firefox 1.5 installed with autopackage work perfectly for me. The obstinate among you can stay happy with the buggier Inkscape 0.42 and the slower Firefox 1.0.6, or waste your own time compiling them from source. I had previously followed the Firefox 1.5 Howto in the tips and tricks forum -- which broke flash. The autopackage did not. Still waiting to see some manifestation of the dependency hell that's supposed to ensue by me typing this from the latest version.[/QUOTE]
i've used autopackage and it work's great for some things, and it's good for a few newer applications that have'nt made it in the repos. but there is no way it is sutable as the main package management system as some people have stated. it would be worse the the old rpm hell days tracking down packages with lots of dependencies and installing 50 packages in order to make one app work.

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=Burning Bronx]So if the devs don't have to embrace it who's gonna do it? You? And who's gonna maintain the package database? Hmmm... no offence but that sounded weird.[/QUOTE]

Thats how backports started. And the packages.ubuntu.com. This is a community distro.

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=Jengu]
Finally -- Inkscape 0.43 and Firefox 1.5 installed with autopackage work perfectly for me. The obstinate among you can stay happy with the buggier Inkscape 0.42 and the slower Firefox 1.0.6, or waste your own time compiling them from source. I had previously followed the Firefox 1.5 Howto in the tips and tricks forum -- which broke flash. The autopackage did not. Still waiting to see some manifestation of the dependency hell that's supposed to ensue by me typing this from the latest version.
.[/QUOTE]

Sounds great. Where is the Autopackage for the 64 bit version of Firefox?

---

### Post by poofyhairguy on 2005-12-22
Last go round for those interested (Mr. Hearn makes me look like the idiot I am):

[http://ubuntuforums.org/showthread.php?t=54227&highlight=effect](http://ubuntuforums.org/showthread.php?t=54227&highlight=effect)

---

### Post by awakatanka on 2005-12-22
[QUOTE=jfdill_2]This is too funny.  Long before Windows I was working primarily on MicroVax then SGI Unix systems.  When Windows came out, my question was, **Why doesn't Windows have a decent package manager?**  Windows really annoys me that when you uninstall stuff, it always leaves junk in the registry, and you can forget about anything like real "software dependencies."  From my perspective, I couldn't figure out why people think it's a "good thing" the way that Windows handles software install and uninstall, it's incredibly sloppy.[/QUOTE]
If i install kubuntu desktop on ubuntu it installs also lots of extra programs, but if i uninstall it it doesn't uninstall all the programs that where in the original install. This is with more programs.

It realy annoys me when it does that. It leaves junk i didn't want anymore. I can't figure out why some people only see disadvantce from a windows way and don't see the disadvantce of linux. 

;) peace and happy hollidays.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-22
> If i install kubuntu desktop on ubuntu it installs also lots of extra programs, but if i uninstall it it doesn't uninstall all the programs that where in the original install. 

It does if you select "completely remove."

---

### Post by awakatanka on 2005-12-22
> **&#1055 said:**
> It does if you select "completely remove."
Hmm most be a difference in kubuntu ( using adept) and ubuntu (synaptic), our i'm the one that doeing something wrong what is possible as a newbee user ;)

---

### Post by Amaranth on 2005-12-22
sudo aptitude remove kubuntu-desktop

Removes the metapackage and any packages that the metapackage depends on (they aren't still needed for something else).

---

### Post by Sheinar on 2005-12-22
[QUOTE=Amaranth]sudo aptitude remove kubuntu-desktop

Removes the metapackage and any packages that the metapackage depends on (they aren't still needed for something else).[/QUOTE]
I thought that only worked if you installed it with aptitude in the first place.

---

### Post by prizrak on 2005-12-22
I didn't read the entire thread, so I might be repeating. But I always thought that .bin files were universal installers for Linux systems.

---

### Post by scaine on 2005-12-22
Well - thanks very much PoofyHairGuy.  You've taken one very frustrating thread : [http://www.ubuntuforums.org/showthread.php?t=97504&page=13](http://www.ubuntuforums.org/showthread.php?t=97504&page=13)

... and turned it into three equally frustrating threads.  ;) 

One of the frustrating things about this is that even the faintest whiff of a suggestion that distros must come together and do something across all of linuxland (for the good of the end user) and suddenly, we go massively off topic and into the politics of free, libre, open, unlicensed, yadadada, whatever dude  Stay on topic ffs...  Thank god Poptones hasn't had a whiff of this thread yet.  Yikes!  :rolleyes: 

The other frustrating thing (and I had to restrain myself on the "quote" and "reply" buttons as I was reading PoofyHair's latest venture near the boundaries of "How Windows Does Things"), is that everyone gets confused (rightly) about the repositories as opposed to the ability to easily install a piece of non-repo software.

We've had arguements, like 
*  If it's not in the repos, then it's not supported on your "O/S".
*  And yes, Ubuntu *is* a seperate O/S from (eg) Mandriva.  As is Warty from Breezy.
*  Third party software shouldn't be installed easily, cos doing so is too dangerous (or endangers the "openness" of your O/S).

My argument, as always, is this : I *love* the repos.  But they don't do the whole job and I *need*... okay then *would really like* an easy way to install third party software.  Just check out the UbuntuGuide.com - filled with stuff that you can't do from the repos.  Just can't - for legal reasons :

*  Java
*  Flash
*  Real Player
*  Codecs

In addition to this, I'd add the following software :

*  Third party Games
 - this is the "killer app" for me.  Games publishers will forever steer cleer of Linux as a whole until there's an easy way to install games, regardless of the Linux in question.  Obviously, there's more to it (and is off-topic to discuss it - in case you're reading this, Poptones), but it's a hurdle.
*  Cedega (which is games related).
 - look at their support forum when they brought out the latest version.  No-one knew how to uninstall it, but the new version wouldn't install until the last one was uninstalled.  Classic.  You had people writing in saying - just use apt-get uninstall xxxxx, but of course, loadsa customers used the tarball.  What a mess.
*  Any other piece of software that's licensed to use (even shareware), like Crossover Office.  Again, shareware writers aren't going to want to support Linux unless they have a single, easy way to distribute their app to every linux distro.  Otherwise, they have to learn several - sheesh, too much effort, stay with Windows.

The main reason I keep going on about games and third-party software is that you won't get the source to these things.  Just won't, because it's intellectual property or somesuch and the license forbids it.  I expect.

Look, there are plenty of holes with this, I'm sure.  But I know, fundamentally, that linux needs a way to do this to flourish.  Why? Well, I've used Ubuntu for 8 months now, my first proper experience with Linux after aborted attempts with Mepis, Linspire, Mandriva, PCLinuxOS and a few others.  And without fail in that 8 months, I haven't managed to compile anything successfully.  I haven't managed to get Java installed (thanks to Automatix for that btw).  I haven't gotten movies to stream *to my satisfaction* inside Firefox (some sites work, others don't).  I haven't bothered re-installing RealPlayer, and jeez - the realplayer plug-in for firefox... that requires some link command to get it going.  First time I did that, I linked it into Mozilla instead.  I think.  Who knows?  Why isn't this stuff easier to install?  ;) 

The bottom line is that as a user, I think this is needed.  It may be niave.  It may even be, as some suggest, nigh on impossible.  But that's my opinion.

Here's hoping that opinion isn't shredded off-topic.  Despite unsubscribing twice from Poofy's first valiant attempt at addressing this issue, I got drawn back in again.

Right, I'm off to visit the Autopackage home page and see how big a job they have on their hands.  Then I'll have a look at klik.  Poofy's brought my attention to GDebi - sounds good, if developers/publisher will support the deb format (they all seem to support rpm install though).  I've already got RubyGems open from a previous post (out of curiosity).  Then I'll sit down and ask myself whether my assertion that I'll not see a universal *installer* (not package manager necessarily) in linux in my lifetime was premature.

Apologies for that last sentence.  Re-read it a few times.  It does makes sense eventually.  :???:

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=scaine]Well - thanks very much PoofyHairGuy.  You've taken one very frustrating thread : [http://www.ubuntuforums.org/showthread.php?t=97504&page=13](http://www.ubuntuforums.org/showthread.php?t=97504&page=13)

... and turned it into three equally frustrating threads.  ;) [/QUOTE]

I didn't plan to bring this thread back to life, its just that I was searching yesterday for something else and I found this thread and I thought "I bet some people that are just learning about this stuff in the Dapper section might like to know what a real Autopackage developer (Mr. Hearn is in this and the other thread a lot) thinks."

Honestly, he ate my lunch last time- this thread is not a source of pride for me! But I learned, others learned and we move on.

Ok....I'll be a good boy and butt out for now.

---

### Post by Malphas on 2005-12-22
[QUOTE=poofyhairguy]Windows can't have large repositories of free software to fit many needs.[/QUOTE]
It probably can to be honest, although it depends on your definition of free to some extent.  Also, I think the notion that there can never be an executable-like feature, common to many distributions to be pure speculation and - to be frank - nonsense.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-22
And it would work just as well...

Go visit your favorite windows software forum and look at the help requests from people who do not have the proper libraries installed. There was a thread right here with someone complaining they couldn't install a video driver without the .net framework installed - and that's software from ONE company. Now multiply that times the number of linux distributions.

Linux is a toolkit; a kernel... it's not a product. 

> ...without fail in that 8 months, I haven't managed to compile anything successfully. I haven't managed to get Java installed (thanks to Automatix for that btw). I haven't gotten movies to stream to my satisfaction inside Firefox (some sites work, others don't). I haven't bothered re-installing RealPlayer, and jeez - the realplayer plug-in for firefox... that requires some link command to get it going. First time I did that, I linked it into Mozilla instead. I think. Who knows? Why isn't this stuff easier to install?

Because none of that stuff is *free*. Ubuntu comes with the *free* stuff installed. If you want an easy, shrink wrapped solution then you need to be running a *non free* distribution like mandriva or linspire. Any centralized service making that stuff you're complaining about *free for all* would be shut down and, quite possibly, the site owner imprisoned.

If you want freedom then you're going to have to take some steps to secure that freedom: you're going to have to *learn to do for yourself*.

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=Malphas] Also, I think the notion that there can never be an executable-like feature, common to many distributions to be pure speculation and - to be frank - nonsense.[/QUOTE]

Yeah...through the course of the thread Mr. Hearn hammered that into my feeble mind.

---

### Post by scaine on 2005-12-23
> **&#1055 said:**
> 
Go visit your favorite windows software forum and look at the help requests from people who do not have the proper libraries installed.


I never said this would be easy.  Ask Mr Hearne - it's obviously not.  I said it was needed (by me).  It was also raised a while back that such an installer would bring about a huge support burden - joe average installed this or that, and now something is broken.  Fair point, but there's already a massive support element along the lines of "I can't compile this/that", so I don't think that "better the devil you know" is a great attitude here.  Joe average needs an easy way to install this software, simply because - one way or another - it will get installed.  Probably poorly unless there's a good, easy, hopefully universal, installer to get the job done properly.

> **&#1055 said:**
> 
Linux is a toolkit; a kernel... it's not a product. 


Nope, and that's the political engine rumbling up there briefly.  No, Linux isn't a product, per se.  But Ubuntu is.  Many distrobutions are.  And in my opinion, a failing of these products is an easy way to install non-free software.  There's an all too common misuse of the word "Linux" in threads like this - we should be talking mostly about Ubuntu.  "Linux" is too politically charged.

Saying "I want an easy installer for Linux" isn't really saying the same thing as "I want an easy installer for Ubuntu".

> **&#1055 said:**
> 
Because none of that stuff is *free*. Ubuntu comes with the *free* stuff installed. If you want an easy, shrink wrapped solution then you need to be running a *non free* distribution like mandriva or linspire. Any centralized service making that stuff you're complaining about *free for all* would be shut down and, quite possibly, the site owner imprisoned.


Hmmm - I think you've missed my point here.  I don't want these tools installed with my O/S.  I want to buy them online (or otherwise), then have an easy way to install them onto my Ubuntu box.  Even better, *any* distibution, but lets keep it on Ubuntu.

That "easy way" doesn't exist yet.  But I'm extremely glad that the AutoPackage, Klik and GDebi teams agree with me on at least a basic level and have decided to try to address this fundamental lack.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
> Hmmm - I think you've missed my point here. I don't want these tools installed with my O/S. I want to buy them online (or otherwise), then have an easy way to install them onto my Ubuntu box.

Then you will have a very long wait. You **can** buy that stuff but not from ubuntu. take a look at the mission statement and you'll see this is one of the very main points - *there will never be a separate "non free" version of ubuntu*. If you want easy and paid for there are a few pretty good linux distributions willing to take your money. Suse has a gorgeous default desktop and Mandriva does multimedia OOTB better than any I have seen. I personally don't care for them, but they do offer what you are asking for, just not the ubuntu brand. Maybe if ubuntu keeps picking up steam and offering good base features those french folks will drop the redhat fork and pick up ubuntu. That seems to be the planned direction.

But even if that happens it has nothing to do with "autopackage" type stuff because it's still not needed. If mandriva were to offer a non-free ubuntu based distribution there's still no good reason for it to support such tools ootb - and plenty of good reasons for it not to, since non-free distributions have to be supported by non-free support personnel.

---

### Post by scaine on 2005-12-23
We're still talking about something very different here.  I don't want Out of the Box third party software!  I thought I'd made that clear in my previous post.

I want to install Ubuntu - it's a magic distibution and after a couple of hours personalising it, there's not much more I need from it.

Except... I want to install RealPlayer, Java, Unreal Tournament, etc.

I've paid good money for this stuff (not Ubuntu of course), now I want an easy, preferably universal, way of installing them.

I hopefully won't have that long a wait on my hands, thanks to the efforts of the various installer teams previously mentioned.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
OK, here's the question: why does it matter to you if the installation is or is not "universal?" You have stated your preference for ubuntu, so what relevance is it to you whether the same installer works on mandriva or linspire? 

If I am installing a game in windows and I use XP I do not care if it works on windows 98, so how is it reasonable to expect things work differently in whatever linux distribution you are using?

Unix (and this battle) is far older than linux; in the 1980's workstation manufacturers were having this exact same battle with proprietary software makers and it was never resolved - in fact, as PCs gained the needed power many of those software makers moved their support to windows so they would only have to support one "flavor" of their software.

If your aim is to wipe out a monopoly you don't do that by creating another. The more alike the various versions of linux are the less reason there is to choose. If your goal is to have a diverse ecosystem of talented and *employed* people supporting the world's IT infrastructure you need tools that will sustain diversity and encourage competition. Making every linux bow to some universal packager (at the native level) isn't going to accomplish that. I don't think the world will ever see another Microsoft (they were able to become what they were because there was no IT infrastructure on teh scale we needed - now we probably have as many unemployed IT workers as unemployed UAW workers), but you don't encourage innovation by bogging everyone down with binary compatability. Soon OS X will be running on x86 - so would it then be logical to insist Apple applications run in Windows and vice-versa? 

Virtualization will soon make it all moot, anyway. If you can run mandrake and ubuntu on the same machine and you can cut and paste between apps seamlessly on those machines, what difference does it make? When you buy a PVR appliance do you care what kernel it's using? If your OS supports native virtualization, I can make my video player with whatever features I need using whatever tools I want, and you can "plug it in" on your machine no matter the core OS you use on your desktop, then what does any of the rest matter?

---

### Post by scaine on 2005-12-23
> **&#1055 said:**
> OK, here's the question: why does it matter to you if the installation is or is not "universal?" You have stated your preference for ubuntu, so what relevance is it to you whether the same installer works on mandriva or linspire? 


Well, it's so that if I end up not liking something about Ubuntu, I can ditch it, move to another (hopefully equally free) O/S and have no issues re-installing all my paid-for software.

> **&#1055 said:**
> 
If I am installing a game in windows and I use XP I do not care if it works on windows 98, so how is it reasonable to expect things work differently in whatever linux distribution you are using?


Well, it's usually unreasonable to compare Windows to any linux distro - I usually get told of for trying that, but... here's my take anyway :

It's reasonable on the level that if you don't have an easy way to install software on an O/S, it will attract little more than a niche user base.  If that's all you want, fair enough.  I believe (my opinion) that Shuttleworth wants more for Ubuntu.  And so far, I've liked what I've seen of Ubuntu - *so I* want more for it.  I believe (my opinion again) that Ubuntu won't get more unless there's an easy way to install non-repo software.

Here's a funny example, slightly off-topic.  In the Fridge, they have a video helper to show you how to install software (excellent idea) - one video for repo, one for compile from source.  The reason it's funny (or sad) though is that the page has Macromedia flash on it, which isn't OOTB on Ubuntu and I couldn't be bothered to get working - it was a tar ball and that usually means pissing about with the command line.  If only there was an easy way to install Flash after I install Ubuntu...

> **&#1055 said:**
> 
If your aim is to wipe out a monopoly you don't do that by creating another. 


Heh. :) I can see why Mr Hearn ducked out of the first thread on this subject.  Why is there such negativity around a simple installer?  It isn't a monopoly!  It's a nice, easy way to install third party software.  Monopoly?  Holy cow.

Okay, if it was cross-distro, it *might* be considered a monopoly.  Let's see... is X.org a monopoly?  Is using a mouse to interact with your desktop?  

Ach - poor examples, but I'm sure there's a ton of software like that which nearly every linux distro will use and no one bats an eyelid.

I mean, how the hell did Synaptic make it into any linux distribution?  It must surely have gone through the same bad press... 

> **&#1055 said:**
> 
Soon OS X will be running on x86 - so would it then be logical to insist Apple applications run in Windows and vice-versa? 


I assume this is a good joke on your part, so I won't take it seriously.  Cos if I did, it would be highly insulting to my intelligence.  It really amazes me the resistance an easy-to-use installer garners.  And the extreme, ridiculous examples it elicits to prove it's evil nature.  Just read the 250-odd posts on this in the other thread :
[http://www.ubuntuforums.org/showthread.php?t=97504](http://www.ubuntuforums.org/showthread.php?t=97504)

> **&#1055 said:**
> 
Virtualization will soon make it all moot, anyway. If you can run mandrake and ubuntu on the same machine and you can cut and paste between apps seamlessly on those machines, what difference does it make?


Cos I don't want to run two O/S's, I want to run Ubuntu and only Ubuntu.  Virtualisation has it's place in the corporate, but I doubt it will affect me much.  You know why, right?  Cos I won't be able to install it unless it's in the repos... ;)

Seriously - I don't see a connection between virtualisation and easy-to-use installers.  Sorry if I missed your point there.


> **&#1055 said:**
> 
When you buy a PVR appliance do you care what kernel it's using? If your OS supports native virtualization, I can make my video player with whatever features I need using whatever tools I want, and you can "plug it in" on your machine no matter the core OS you use on your desktop, then what does any of the rest matter?

I have no idea why you're suddenly talking about kernels and PVRs here.  Again- I apologise if I'm missing something obvious.
What I'm asking is really simple, but seemingly, very very difficult.  Give me an easy way to install commercial, paid-for software on Ubuntu.  If it works on others distros - bonus.  But let's keep it to Ubuntu.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
*Why is there such negativity around a simple installer? It isn't a monopoly!*

I didn't say that was a monopoly. I said you do not wipe one out while fostering an environment that facilitates the creation of another. "One linux" is just as bad as "one windows."

*is X.org a monopoly?*

Of course not. I can compile the source code using whatever tools I want. But in order to support a *binary compatible installer* you cannot do that. 

Try installing mandrake rpms in redhat. They're both RPMs and mandrake is spawned (initially) from redhat. So why don't they work? Should mandrake have to compile everything for 386 systems (as redhat does) rather than provide an OS that supports more reasonably modern processor extensions?

*Give me an easy way to install commercial, paid-for software on Ubuntu.*

What software are you talking about? The only ones stopping Adobe and oracle from setting up respositories that would facilitate "one click installation" of their software on ubuntu are Adobe and Oracle. But when they start linking their stuff into some GPL tools what happens? Linus says he has no problem facilitating binary only kernel modules, but not everyone is so pragmatic. What happens if Adobe links to libmagick rather than their own graphic modules? Non-programmers don't realize how many "tools" are included in windows that get used over and over. If you have to include all those in your own software then the file size can grow considerably, and there is still no real precedent on linkng Free modules with non-Free. That is why virtualization is important - because systems will be able to link non-free and free without these legal concerns. Software can be made to support specific featuresets (like ubuntu desktop) or it can be packaged as a complete machine that communicates only through standard virtual i/o channels. So when you open Photoshop 2010 on your linux desktop it is sending your image through a black box connection into adobe's virtual machine. It draws on your screen through standard system calls, but it's not linked to any of the core modules of your desktop. Software can be packaged in black boxes like home appliances. That way "non free" and "Free" can coexist and compete on their own terms.

*I don't want to run two O/S's, I want to run Ubuntu and only Ubuntu.*

Then you are already screwed, cos your machine wouldn't even boot without "another OS." It lives on your motherboard and it is the middleman between your OS and your hardware. Modern systems force it out of the way as much as possible but they can never completely overcome it. Set your bios to "alarm on boot secotr changes," for example, and then modify your boot sector. On any machine I have done this I still heard those alarms. Thus, the machine is already virtualized at some level - the OS communicates through the hardware, but the bios is still there. 

* Virtualisation has it's place in the corporate, but I doubt it will affect me much.*

But you're the one who cannot understand why it's so hard to make a "one size fits all" installer. You're making a statement of opinion here and trying to defend it on technical grounds. That ain't gonna fly, especially when one need only visit th websites of intel and amd to see that greater virtualization is coming to a desktop near you. The only way to avoid it is to stick with aging equipment. 

*You know why, right? Cos I won't be able to install it unless it's in the repos... *

Virtualization will be in the hardware itself. Any operating system that refuses to support it will be left without hardware to run on, or will be relegated to being a sub-process on that virtual host (ie "ubuntu for windows")

---

### Post by DancingSun on 2005-12-23
&#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046;, could you explain, in your understanding, what virtualization is?  And how it leads to one software running on OS A, linking a library in OS B (like your Adobe example)?  It is my understanding that the virtualization technology that AMD and Intel has for us in the future allows multiple OS to run concurrently in *isolatation*.

BTW, BIOS is not the full blown Operating-System-that-can-manage-many-software-programs that scaine is referring to.  Lets not try to pick bones out of eggs shall we?  Obviously he's fine running the BIOS and his Ubuntu together, I mean, Ubuntu won't even load without the BIOS!
[http://en.wikipedia.org/wiki/Bios](http://en.wikipedia.org/wiki/Bios)

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-23
> And how it leads to one software running on OS A, linking a library in OS B (like your Adobe example)?

I didn't say that. I said this was a *problem* with (in my example) Adobe linking their proprietary product to GPL libraries on a system.

Virtualization (and a standard means of communicating information like clipboard data) is how you allow multiple virtualized systems to communicate. 

> BTW, BIOS is not the full blown pperating-System-that-can-manage-many-software-programs that scaine is referring to.

Neither is DOS. It's irrelevant because, if you can run multiple virtualized systems, you don't need all that anyway. How does linux do what it does? How does Windows? It creates multiple virtualized *processes* that are tightly linked. Moving the virtualization closer to the hardware allows greater robustness *and* allows those processes to do things their own way. If you have a single user licensed copy of Photoshop running on a system then all Adobe has to do is make an "operating system" to contain it that connects via the industry standard i/o (for example, dbus). It doesn't have to worry about conflicting libraries or how their libraries interact with other tools (try running Photoshop and Dscaler, for example, on windows 2000. Clue: you can't cuz it'll bsod).

> It is my understanding that the virtualization technology that AMD and Intel has for us in the future allows multiple OS to run concurrently in isolatation.

That's the point. But when you have onboard encryption to enforce containment policies you can move data between those processes via secure socket connections. It doesn't even make any difference whether those processes are running on the same CPU or not - you could have every machine linked together in your home and automatically distribute work among them.

No, I don't work for Sun. 

But I am looking forward to working with more virtualized, more secure processors. And I'm looking forward to doing this with open source tools.

---

### Post by DancingSun on 2005-12-24
Running many OSes, micro-OSes, virtual machines, whatever you call it, is very resource intensive.  The more guest OSes there is, the more resource is required to juggle between them.  Each of them is their own software platform.  Each platform will have to manage the memory of the software programs that run on them.  You'll get lots of code duplication that provides the same basic function for each platform/VM/OS.  Also, the vendors will not only have to be application vendors, they'll also need to become platform vendors.  Plus, there's no guarantee that these different vendors will comply to industry standards to have their applications communicate with those from the other vendors, similar to there's no standard way to install an application on Linux distributions.

There's also the concern that it's unlikely that any of the existing software will be able to work in a virtualized environment the way you described.  Current software just doesn't work that way.  So what you described doesn't solve the problem at hand.

Now, if running software/software packages as VMs becomes a reality, there still is the question of how easy is installing these separate OSes/VMs?

---

### Post by Amaranth on 2005-12-24
Can't this thread just die already? :(

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-24
> There's also the concern that it's unlikely that any of the existing software will be able to work in a virtualized environment the way you described.

When the virtualization is in the hardware the software only needs to support the virtualized machine. Putting linux (or any other os) on that hardware is a standard process of writing the needed drivers.

> Current software just doesn't work that way.

It doesn't work that way because vmware doesn't have the hardware needed to support a fully virtualized system (accelerated graphic card, sound i/o etc).

I honestly don't understand this resistance to the idea. It's coming, and it's not far off either. Fully virtualized machines will get here long before there becomes a ubiquitous  "one size fits all" package manager for linux (which is to say never, since the VM system will render such necessity moot).

---

### Post by scaine on 2005-12-24
> **&#1055 said:**
> 
It doesn't work that way because vmware doesn't have the hardware needed to support a fully virtualized system (accelerated graphic card, sound i/o etc).

I honestly don't understand this resistance to the idea.

You honestly don't see the irony of that statement?  Funny.  You've just spent the last several posting resisting a far simpler concept.

What your basically saying then is that Autopackage are wasting their time with an easy-to-use installer because... what?  In a few years time we'll all have virtualisation-supporting hardware, the linux kernel will support it and we'll never have to install software ever again?

You were wrong earlier.  I'm not trying to force my opinion on you by backing it up with technical detail.  I'm stating my opinion and explaining that enough people agree with me (actually, I agree with them) that they're *actually doing something about it*.  And more power to them.  You're an excellent example of what they're up against just to make things easier for the rest of us.

> **&#1055 said:**
> 
*I don't want to run two O/S's, I want to run Ubuntu and only Ubuntu.*

Then you are already screwed, cos your machine wouldn't even boot without "another OS." It lives on your motherboard and it is the middleman between your OS and your hardware.


And please stop with the extreme counter examples when arguing against.

Here's the link for you again - visit the site.  Install an auto-package.  Experiment, then come back with *real* reasons why this is a bad thing.
[http://autopackage.org/](http://autopackage.org/)

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-24
> Experiment, then come back with real reasons why this is a bad thing.

For the bazillionth time: I didn't simply say "this is a bad thing." That is a subjective matter of opinion. What I said was it is an *impractical thing* and, due to the great number of technical **and** political barriers it is about as likely as Windows going GPL. The reasons I presented were objective observations based onyears of experience. It really doesn't matter whether you *like* hearing these things, time will prove me right. And, if you doubt that, I suggest you consult the last three decades of *nix history. As I said, this is not at all a new "battle."

> And please stop with the extreme counter examples when arguing against.

Sorry, you can keep asserting it until your lungs explode, but there is nothing at all "extreme" about calling a motherboard bios a "primitive" OS - and it will be considerably less primitive as virtualization moves into the cpu and support circuitry and most of the peripheral i/o is handled via highly abstract data packets traversing high speed serial connections on the motherboard.

> You're an excellent example of what they're up against just to make things easier for the rest of us.

Again with the personal insults? You know nothing of me. I have spent more time on making stuff "easier for the rest of you" than you will ever know. But since you asked, I will take a minute to "reply" to their faq...

*Packaging as separate from development tends to introduce obscure bugs caused by packagers not always fully understanding what it is they're packaging.*

Do the developers of program x know everything about every library they link to? Very unlikely. Nevertheless it is up to the publishers of a given distribution to provide a quality product: if it is built by a bunch of know-nothing idiots it won't last. Their "customers" will find a better distribution and that will be that.

*It makes no more sense than UI design or artwork being done by the distribution.*

Do you see? these folks don't even think it's a good idea for different distributions to *look different* or have extra features. There are plenty of people working their butts off to add features to ubuntu that are missing or poorly implimented on other distributions. These folks want nothing of that; "linux is linux" to them, not a toolkit upon which further innovation and competition can occur in a *Free and diverse* marketplace. 

*Distro developers end up duplicating effort on a massive scale. 20 distros == the same software packaged 20 times == 20 times the chance a user will receive a buggy package.*

This is provably false "logic." It doesn't matter if there are ten thousand distributions out there unless I am running ten thousand distributions. But building a "package" that ignores distribution specific features is a very good way to ensure the program *will* at least appear to be "broken" when user X goes to operate within the application in a manner she has come to expect and the black and white "generic" application wasn't built to support that user's desktop.

*apt et al require extremely well controlled repos*

Irrelevant. If an idiot builds an "autopackage" it will also break a user's system. There are no magic bullets.

*...they can get confused and ask users to provide solutions manually*

As opposed to just ignoring and completely not supporting features that do not fit within the generic "one size fits all" desktop.

[i]Very hard to avoid the "shopping mall" type user interface, at which point choice 
becomes unmanagably large: see Synaptic for a pathological example of this.[/i]

You don't need to tear down the house just because the roof is leaky.

*Long term the solution to this problem is the development of **a** desktop Linux platform, so it's possible to predict with certainty what will be available on your users systems.*

Again.. this system ultimately depends upon a reduction of diversity. Make "a linux to compete with windows" - *make a linux windows*.

There's nothing wrong with wanting to make an open source windows. There's nothing wrong with wanting to make a "linux windows" - the whole point of the open source and Free toolkit is we can all build whatever floats our boat and compete with one another for a slice of the pie. But *if* that happens and someone "invents" a windows-linux it will still just be a grandfather of a "platform" like debian with its ubuntu/Linspire descendants and RedHat with its family of Mandrake/Suse/whatever.

---

### Post by KiwiNZ on 2005-12-24
Please keep discussion to the points and not divert into personal insults and attacks.

Thankyou folks

---

### Post by raynevandunem on 2006-01-06
Hello, seeing that this forum hasn't been closed as of yet, I'll just add my two cents, or at least divy them up as much as I can among the many valid arguments which have been posted so far (I'm not usually one to diss opinions except in the exacting of retribution, so I'll try to stay as positive as I can):

1. As mentioned by poofyhairguy, [http://www.ubuntuforums.org/showthread.php?p=285685#post285685](http://www.ubuntuforums.org/showthread.php?p=285685#post285685), there isn't any universal package management solution for most Linux users due to the simple fact that new distros (and their derivatives) are being made by the day (hmm, seems more like rabbits than penguins to me...). Hell, even [http://distrowatch.com](http://distrowatch.com) can't keep an exact count.

My suggestion for those who seek the goal that is (at least seemingly) being reached by such efforts as autopackage, klik, and smartpm is something that will involve the efforts of three parties in question: distributors (of the OS), makers (of the third-party software), and the users (of both).

**Makers** will have to make the tars available to the public, be the ware open-source or not (that is, if they want an audience beyond just the Windows majority and Mac leading minority), which I sincerely doubt most of them will do since Windows serves as the potential cash cow for most of their products.

**Users** will have to compile the sources into binaries for their respective systems, and then send copies of the resultant binaries back to the maker so that others who would want the latest version for, and compatible with, their own OS will be able to DL and install the binary off the bat. Again, I doubt that the majority of makers will want to host the hundreds, maybe thousands of binaries sent back in on their own servers, since they will have to repeat this cycle over and over again with every update.

**Distros** will (I agree) be able to focus on further core development as a result, rather than have, hold, and sometimes firmly grip numerous binaries in potentially humongous backports.

If followed, would such a trend give end users a free hand to go to every possible third-party maker with a demand for a Linux porting of a program that is geared primarily toward the Windows majority? I doubt it, but it would give them a somewhat freer hand as far as updates to that same third-party software (say, Firefox 1.5, which, last time I used Ubuntu, was not updated in the backports department; same with MPlayer for some other reason) is concerned.

Plus, such a gradualized processing of sources into binaries would possibly give the third-parties the impression that there actually IS a market with Linux (although, again, I do emphasize that I prefer open to closed-source, which would pretty much rule out people like Adobe, who now owns the former Macromedia) and thus allow for more of them to provide Linux tar portings of originally-made-for-Windows software (and, with Linux crossing over with other *nixes, this would also bode well for Darwin/Mac, *BSD, Solaris, and others as well).

The developers, be they in the basement, dorm room, lab, or cubicle, will, in the meantime, continue to improve upon the Linux platform, the several 2nd-generation platforms based on Linux (Debian, Gentoo, RedHat/Fedora, SuSe, etc.), the 3rd-generation platforms built upon those (Ubuntu, Arch, Knoppix, VidaLinux, etc.), and so on. They will continue to make sure that functionality, usability, and fundamental ethics will all be payed attention to as far as the OS is concerned. Now, with the third-parties, that may be harder, and with the end users, the hardest.

A fundamental truth can be applied here, as it can be applied to open-source and life in general: there is no true "alpha" release. There will always be bugs, annoyances, and compatibility issues. As soon as this issue is eventually resolved and put to rest (and never truly, completely so), there will be others to address. No one will ever be truly and completely satisfied with the state of Linux, Debian-Linux, or Ubuntu-Debian-Linux, be they distributor, developer, or end user (and all three will have some high horses to sit on, which is never good).

Which is why we must always develop something better, or at least bring it up in discussion.

btw, instead of a universal solution like autopackage, I'd opt for what I just offered above, as well as for a further simplification, further streamlining, further debugging, and further foolproofing of the present dpkg/APT (on the part of the distributors). Among countless others, I wholeheartedly ***refute and reject*** the belief that its perfect in its present form, based upon the "fundamental" premise presented above.

Oh, and for some particular others in this and a few other threads on this same matter: "reinvention of the wheel" = "improvement". GNU/Linux itself is  the same, so-called "reinvention of the wheel", as is every distro based upon it.

Such is the inherent nature of Linux, Open Source, and life itself.

---

### Post by warpforge on 2006-01-07
I've only read this thread until about page 12, so maybe I'm repeating something here. The current system of backports and repositories doesn't do the job. I, too, want to run Firefox 1.5 without dist-upgrading to a beta OS.

There are two solutions I see:
1. I really like the Klik system, as it seems to function much like the OS X .app packages. Downsides: Duplication of dependancies and multiple library versions possibly opening security issues. Also, some libraries HAVE to run at the system level and can't just get rolled up into a Klik package.
2. A one-click link on pages to add the right mini-repository for my distribution, apt-get update, and apt-get install a specific package. Yes, this is a Debian-centric solution, but I think it would be a good first step. Downsides: Upgrading things like Firefox can pull the rug out from under other applications. The repository might upgrade other libraries that break other applications. This is basically an auto-upgrading version of the "just distribute .debs and have a GUI installer for .debs" idea.

I don't see a simple answer to this problem, but we need something better than the current system.

---

### Post by MadMan2k on 2006-01-07
you cant compare linux with windows or osx, since linux is much more modulized.
In linux you will get only the app, where in osx it also brings all its dependancies along.

thats the reason you cant update to firefox 1.5 yet - other applications depend on firefox 1.0.x.
You simply dont have that circumstance in windows or osx...

the main problem that the firefox release cyles are out of sync with GNOME/ Ubuntu.

---

### Post by r_a_trip on 2006-01-07
*the main problem that the firefox release cyles are out of sync with GNOME/ Ubuntu.*

No, the main problem is that most newcomers to GNU/Linux have no respect for the  unwritten rules of the community around this OS. They assume that everything they learned on either Windows or Mac OS can be grafted without complications on to GNU/Linux.

The problem with this is that it flies against 20 years of acquired good practises in the Free Software community. There is a very good reason why you can't go plonking any old piece of software with a higher version number in a particular distro, it wreaks havoc with the interdependacies of several packages on that distro.

Most Windows or Mac OS users who switch don't take the time to get to know what they use. They don't realize that they were never part of a community where it is possible to use unfinished software, software that has been freshly released but not yet packaged or software that comes out of the box. It is a choice offered that hinges on the ability and willingness to gain the necessary skills to use those options.

Sadly, the ones that are damaged by using proprietary software too long, have this misguided sense that they are entitled to go through every stage of FOSS development and have this experience be handheld and spoonfed. They never realize that they got very old and very tested software out of the box in the proprietary world.

That is why it worked so easily on their Mac and Windows distributions. That brandspanking new package they bought was already stale and the new version halfway done. But since it all happened behind closed doors, the old "new" package had a false sense of immediacy at the time of purchase.

I wish more people were like me. When I came to GNU/Linux I didn't come with a sense of entitlement nor was I making feature requests that were founded upon a misunderstanding of the OS and the community around it. I gave myself the time to get acquainted with this wonderful work that was offered Free (and even gratis). In the end every weird thing I encountered in the beginning had a very good reason for being so.

Too bad most people have turned into bored consumers these days, unwilling to spend more than ten seconds on every item that is presented in their lives.

---

### Post by leech on 2006-01-07
Bingo, right on the nose!  Thank you, r_a_trip you pretty much took the words right out of my mouth!

Leech

---

### Post by r_a_trip on 2006-01-07
* Thank you, r_a_trip you pretty much took the words right out of my mouth!*

You're welcome! It's difficult being a "veteran" GNU/Linux user. We have a staggering influx of new users and sadly they are, for the most part, not in it for a love of the new, but out of a loathing of the old.

As an "oldtimer" I know the true joys of GNU/Linux and its strengths, I also know the jarring annoyances it has. I also have come to know the power of its community to continually make things better.

The new comers don't take the time to discover the amazing properties this OS has nor do they particularly care for the community aspect of it, because they aren't raised to value it.

I have had days in which I thought about excluding these new users, but that is not what I really want. I want to be able to welcome all, it's just that I fear that they might succeed in killing the goose with the golden eggs if they keep demanding a cheap Windows clone and nothing more. 

If computing is brought down to that level, I don't think Free Software will survive. It is restrictive and kills the drive for new and better ways. Too bad that the current crop of newcomers is so damn selfabsorbed and unwilling to explore anything new. It seems that they aren't even interested in selfempowerment anymore.

---

### Post by leech on 2006-01-07
Yeah, you sum it quite well.  I try to welcome all the people over that I can, but some of them just don't 'get it'.  They want to be able to go into CompUSA and buy a label maker (or whatever) and they don't understand when I say that that stuff can be downloaded for free for linux.  

Or of course the big problem as this thread states, people want to be able to just download the newest software and install it right away.  Well that breaks the whole distribution aspect of things.  Maybe that is the direction we should take the argument.  Same as with why I haven't installed the new nVidia drivers, since I'm testing Dapper, I want any problems to crop up to be Dapper's, not because of something weird I did.  Makes bug reporting and support much easier.

A Distribution of Linux is exactly that, a Distribution of a set of software that will be under support for contracts or whatever.  It makes support a nightmare if people are downloading this and that from all sorts of other places.

Leech

---

### Post by r_a_trip on 2006-01-07
Being on the cutting edge requires one to be very computer savvy. Everybody screaming for no-brainer ways to install software that is cutting edge and has the potential of rendering your system useless, haven't gotten a clue about what software really is. (Do they even know what they really want and need?)

GNU/Linux doesn't stop you from doing just that though, but then you need to aquaint yourself with CVS, compiling from source, risking extreme trouble with your system if you use "unsanctioned" third party software and you have to know how to configure yourself out of the maze if your setup goes South.

Ubuntu is not about cutting edge software in the hands of newbies (Gentoo fits that description better). Ubuntu is about maintanable and functional software for all of us, with at least the guarantee that that software is supported for its core.

If a newbie wants to go poweruser and use the really latest and greatest (mind you newbies, on Windows or Mac OS you never did! Always old sanctioned for sale packages), then you need to become a GNU/Linux Guru or hire one to work for you.

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=warpforge]I've only read this thread until about page 12, so maybe I'm repeating something here. The current system of backports and repositories doesn't do the job. I, too, want to run Firefox 1.5 without dist-upgrading to a beta OS.

I don't see a simple answer to this problem, but we need something better than the current system.[/QUOTE]

You want to run Firefox 1.5? Then do it! Go to the Mozilla site and download it. Unzip the folder and click on the Firefox excutable. It WILL work. I promise. Just like many Windows programs that come in zip files.

A universal installer is sitting there on the official site for the exact program you want and you can't see it for some reason. Why? Its there. Waiting for you.

The system does not need to be changed because because a few people can't see the problem is fixed...

Heck, use Automatix. That installs Firefox 1.5 in a way for you FAR better than most Windows installers. Its SOOO easy to get the new Firefox. So just do it already....

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=r_a_trip]
Sadly, the ones that are damaged by using proprietary software too long, have this misguided sense that they are entitled to go through every stage of FOSS development and have this experience be handheld and spoonfed. They never realize that they got very old and very tested software out of the box in the proprietary world.

That is why it worked so easily on their Mac and Windows distributions. That brandspanking new package they bought was already stale and the new version halfway done. But since it all happened behind closed doors, the old "new" package had a false sense of immediacy at the time of purchase.
[/QUOTE]

In all the Autopackage threads on the forum, this post is by far the most awesome one.

THAT is the problem. You nailed it. You freaking nailed it.

---

### Post by MadMan2k on 2006-01-07
[QUOTE=r_a_trip]
That is why it worked so easily on their Mac and Windows distributions. That brandspanking new package they bought was already stale and the new version halfway done. But since it all happened behind closed doors, the old "new" package had a false sense of immediacy at the time of purchase.[/QUOTE]
thats only true for commercial CS software, but there are olso OSS project for Windows.
Firefox ist the beste example; while the Ubuntu have still to wait, the Windows users already can use it.
The advantage of Windows is, that it has stable ABI and developers can thereby easily package their software.
You cant deny that linux has a problem with the developer <> distribution delta.
Autopackage is one approach to solve this - I dont think it is the right one, but denying the problem is absolutley wrong.

---

### Post by warpforge on 2006-01-07
[QUOTE=r_a_trip]No, the main problem is that most newcomers to GNU/Linux have no respect for the  unwritten rules of the community around this OS. They assume that everything they learned on either Windows or Mac OS can be grafted without complications on to GNU/Linux.

The problem with this is that it flies against 20 years of acquired good practises in the Free Software community. There is a very good reason why you can't go plonking any old piece of software with a higher version number in a particular distro, it wreaks havoc with the interdependacies of several packages on that distro.[/quote]
You're confusing *what is* with *what has to be*. The reason you can install stuff quickly and easily on Mac and Windows is because they remove most desktop applications out of the dependency tree. Maybe Ubuntu keeps Firefox 1.0.7 in the dependencies tree but allows me to install Firefox 1.5 in a purely application mode. Such a separation creates a stable foundation for application development without impairing a user's ability to run new software.

When I bought my new video iPod, I needed software to run it. I had to find some .debs of a CVS version of gtkpod and a supporting library. A new stable version of gtkpod is out that supports my iPod, but I can't find it in the repositories, so I either have to settle with an unpackaged install, a third-party packaged install, or an old version.

I'm tired of having 15 repositories installed so I can use my iPod or have the current stable OO.org.

> 
I wish more people were like me. When I came to GNU/Linux I didn't come with a sense of entitlement nor was I making feature requests that were founded upon a misunderstanding of the OS and the community around it. I gave myself the time to get acquainted with this wonderful work that was offered Free (and even gratis). In the end every weird thing I encountered in the beginning had a very good reason for being so.

Too bad most people have turned into bored consumers these days, unwilling to spend more than ten seconds on every item that is presented in their lives.
I'm *so* sorry I had my 4G iPod stolen so I had to buy a new one and expected to find the stable version of gtkpod that supports my 5G iPod in the Ubuntu repositories.

I invite you to find a different distro if you think flexible software management that makes sense to users is built out of some consumerist sense of entitlement because I don't want Ubuntu to be "Ivory Tower Linux."

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=MadMan2k]thats only true for commercial CS software, but there are olso OSS project for Windows.
Firefox ist the beste example; while the Ubuntu have still to wait, the Windows users already can use it.
The advantage of Windows is, that it has stable ABI and developers can thereby easily package their software.[/QUOTE]

Firefox is the worst example of this problem. You go to the Mozilla site in Linux and they will give you a magical binary that runs on every Linux install I have tried it on.

Where is the problem? Thats how I get Firefox in Windows too- go to Mozilla site and download it!

In fact, with the proven existance of that and things like Autopackage it points to the real problem- OSS software makers do not always want to spend the time to package their software. Releasing a tar file is easier. In Windows they HAVE to release a binary (aka the hard way) because there is no other option. In Linux there is MANY options for packaging and a few a near universal (Klik, Autopackage, Loki, whatever Firefox's thing is) yet most software developers pick the easiest route- the tar file. 

The only solution to that problem is to take away the tar file from developers. Then they would be FORCED onto a harder route like Autopackage. Of course this goes against everything Linux is, so don't expect it to happen any time soon.

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=warpforge]You're confusing *what is* with *what has to be*. The reason you can install stuff quickly and easily on Mac and Windows is because they remove most desktop applications out of the dependency tree. Maybe Ubuntu keeps Firefox 1.0.7 in the dependencies tree but allows me to install Firefox 1.5 in a purely application mode. Such a separation creates a stable foundation for application development without impairing a user's ability to run new software.[/QUOTE]

Thats EXACTLY how it is. Thats how I have Firefox 1.5 installed right now on my computer.

> 
When I bought my new video iPod, I needed software to run it. I had to find some .debs of a CVS version of gtkpod and a supporting library. A new stable version of gtkpod is out that supports my iPod, but I can't find it in the repositories, so I either have to settle with an unpackaged install, a third-party packaged install, or an old version.

I'm tired of having 15 repositories installed so I can use my iPod or have the current stable OO.org.

Then don't use Ubuntu. Ubuntu clearly says what it is "a stable release every six months with bug fixes inbetween." Its not a distro where applications are upgrading as they are released. Its a distro where applications are all upgraded every six months. The reason so many Linux Distros exist is because they each scratch an itch. This is Ubuntu's itch.

And it works for many people. Like who? Non nerds. Such as my friends that are using the exact version of Firefox I originally installed on their Windows machine a year ago. Or my mom, who would think that two upgrades a year is a little much.

If you are tired of Ubuntu's approach pick the distro that fits you. Gentoo and Debian Sid and Arch Linux all have rolling releases- as software comes out they are packaged and you get them. If that is what you need, why not use one of those distros? No single Linux is going to make everyone happy. Pick what fits you.

Mark (they guy who pays for Ubuntu) has said more than once that he does not believe in binary compatibility. That means that Mark would never officially support something like Autopackage- he does not like that solution. If this is unacceptable to you then vote with your feet. Use another distro. Or fork Ubuntu and make a version that is in flux. Or help with backports. Or don't use Linux at all. Its your choice. Thats what the freedom is free software is about- being able to pick what option fits you best.

Ubuntu never claimed to be the best Linux distro or the one that lacked focus. It has a clear focus that might not be right for you. 

> 
I'm *so* sorry I had my 4G iPod stolen so I had to buy a new one and expected to find the stable version of gtkpod that supports my 5G iPod in the Ubuntu repositories.

Don't try to play the victum role. No matter what happened to your first MP3 player, you replaced it with one that has no official Linux support. Apple has never released a version of iTunes for linux. 

Nothing prevented you from getting a player that actually works with Ubuntu. I have a MP3 player that I plug in and it shows up on the desktop and I use nautilus to put on MP3s. I REPLACED my iPod with this player because the iPod has no official Linux support!

You are even lucky that a project like GTKPod exists. How did you even know that it supported your iPod? Was it in the changelog? How did you know it supported it well? I used GTKPod for many moons and it claimed to support things that it barely did. Thats not the developer's fault- its my fault on having to rely on the GTKPod developer. So I fixed it by buying a compatible player.

No one forced that new iPod on you. You knew it had no official support in Linux.....you made your choice. This is the price you pay!

Why did you "expect" that Ubuntu would fix this problem for you? The concept that you "expected" Ubuntu to magically have the software needed for your new non-Linux compatible device blows my mind!

> 
I invite you to find a different distro if you think flexible software management that makes sense to users is built out of some consumerist sense of entitlement because I don't want Ubuntu to be "Ivory Tower Linux."

Ubuntu ships its version all over the world for free. It can never be the elitist distro because its offered to everyone.

The maker of Ubuntu makes his opinion clear when it comes to binary compatibility:

[https://wiki.ubuntu.com/MarkShuttleworth](https://wiki.ubuntu.com/MarkShuttleworth)
> 
Just to be clear, I'll say it again, for the record. We don't aim for "binary compatibility" with any other distribution. Why?

In short, because we believe in Free Software as a collaborative process focused on SOURCE CODE, and consider it superior to the proprietary process which is focused on specific applications and binary bits. We choose to devote the large majority of our energy to the improvement of the source code that is widely and freely available, rather than trying to work on binary bits that cannot be shared as widely. When we spend hours of time on a feature, we want that work to be usable by as many other distributions as possible, so we publish the source code in "real time" as we publish new versions of the packages. We go to great lengths to make those patches widely available, in an easy to find format, so that they will be useful to upstreams, and other distributions. That benefits Debian, but it also benefits Suse and Redhat, if any of them are willing to take the time to study and apply the patches.

We synchronise our development with upstream, and with Debian, and with other distributions such as Suse and Gentoo and Mandrake and Red Hat, on a regular basis. We draw code from the latest upstream projects (which might not even be in Debian, or in Red Hat, or addressed in the LSB). We try to merge with Debian Unstable (a.k.a. Sid) every six months. We have no control over the release processes of other distributions, nor of upstream, so it would be impossible for us to define in advance an API or ABI for each release. We are in the hands of hundreds of other developers every time we freeze Ubuntu in preparation for a new version. Even though the Ubuntu community is substantial and growing rapidly, it is still tiny compared to the total number of developers working on all the free software applications that make up the distribution itself. Our job is to package what is there, efficiently and cohesively, not to try to massage it to some pre-defined state of compatibility. We focus on delivering the newest-but-stabilised-and-polished versions of the best open source applications for your server or desktop. If we were to set binary compatibility (at any level) as a top priority, it would massively diminish our ability to deliver either newer software, or better integration and polish. And we think our users care most about the fact that they are getting the best, and most integrated, apps on the CD.

---

### Post by leech on 2006-01-07
My thinking has always been like this, a project starts, gets developed, then the developers get to a point they release it.  Then if it's developed by someone who uses debian, then there will probably be a debian package, if they use redhat rpm, etc.  If the package is POPULAR enough, then the maintainers of the different distributions will put that package in their repositories.  

Newer versions are of course dependent on the package maintainter, but most of them are pretty good.  I really don't see the problem with waiting 6 months for the new version of anything, unless of course it is due to a serious bug fix or a security issue.

Leech

---

### Post by MadMan2k on 2006-01-07
> **poofyhairguy]Firefox is the worst example of this problem. You go to the Mozilla site in Linux and they will give you a magical binary that runs on every Linux install I have tried it on.[/QUOTE]
i dont have libstdc++5 installed, since I dont need it in dapper anymore and thus it wont run.  said:**
>  In Windows they HAVE to release a binary (aka the hard way) because there is no other option.
they have to compile it anyway too see if it runs - and if it does all they have to do on windows is to zip it.
This will not work on linux due to the mentioned problems.

but I think we can find a solution except of enforced stable ABI (thats what autopackae finally is)

---

### Post by r_a_trip on 2006-01-07
*I invite you to find a different distro if you think flexible software management that makes sense to users is built out of some consumerist sense of entitlement because I don't want Ubuntu to be "Ivory Tower Linux."*

No, you just want every need of yours catered to irrespective of the history, philosophy and essence of what is GNU/Linux. You don't care what eventually happens to it, as long as it serves you now. The moment you find something that is "better" you'll discard GNU/Linux, as to you it is just another OS.

I know GNU/Linux isn't perfect, but I know that in the long run it'll be the software that respects me as a user the most and I am willing to give up some amenities for that.

There is a lot I want too, but I don't expect others to fly for me and present that on a silver plate to me. At least I took the time to learn the very easy steps of **./configure && make && make install** if I really desperately *need* some sofware now instead of over a period of less than six months.

I don't fear a change in software installation. If applictions can be made more independant from the core OS, yes, do so. Just don't do it with quick and dirty hacks, just so you can say I'm running Firefox version plus 1, because it is a must have. Let the developers have the time to "fix" this issue in a sane and constructive manner.

You might scoff at _"Ivory Tower Linux"_, but it was the principals of the Free Software movement that made this alternative a reality more than anything else. If RMS hadn't been unbending in his ways, you'd not be using GNU/Linux at all right now.

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=r_a_trip]*I invite you to find a different distro if you think flexible software management that makes sense to users is built out of some consumerist sense of entitlement because I don't want Ubuntu to be "Ivory Tower Linux."*

No, you just want every need of yours catered to irrespective of the history, philosophy and essence of what is GNU/Linux. You don't care what eventually happens to it, as long as it serves you now. The moment you find something that is "better" you'll discard GNU/Linux, as to you it is just another OS.

I know GNU/Linux isn't perfect, but I know that in the long run it'll be the software that respects me as a user the most and I am willing to give up some amenities for that.

There is a lot I want too, but I don't expect others to fly for me and present that on a silver plate to me. At least I took the time to learn the very easy steps of **./configure && make && make install** if I really desperately *need* some sofware now instead of over a period of less than six months.

I don't fear a change in software installation. If applictions can be made more independant from the core OS, yes, do so. Just don't do it with quick and dirty hacks, just so you can say I'm running Firefox version plus 1, because it is a must have. Let the developers have the time to "fix" this issue in a sane and constructive manner.

You might scoff at _"Ivory Tower Linux"_, but it was the principals of the Free Software movement that made this alternative a reality more than anything else. If RMS hadn't been unbending in his ways, you'd not be using GNU/Linux at all right now.[/QUOTE]

I have a new hero.

---

### Post by raynevandunem on 2006-01-07
Zubuntu ("Z" as in "zoom!")

An Ubuntu derivative that will be geared toward power users (many of whom are Windows converts like myself).

It will combine the rock-hard stability of Debian and the userfriendliness of Ubuntu with the needs of high-powered users who want the most up-to-date (read also: "third-party") software without having to run into compatibility or dependency problems for the majority of the time (that is, until the easily-pitied fool decides to "play God" with the engine that drives the **basic** system. At that point, you're on your own, bub).

What will be introduced for this Ubuntu derivative is a, at this point, hypothetical new package management system that will make it easier and more understandable for people to DL and compile third-party sources into binaries. It may be slower than the current dpkg/APT, but it will make it even easier to comprehend for the average user, if not totally foolproofing it until further down the road of development.

Furthermore, a clear, easily-discernable distinction will be made between the engine (which will remain within the jurisdiction of the distributor, so a "no touchee" policy as far as end users are concerned will be applied) and the drivers seat (think Gentoo to an extent). Users will not (so easily, as they do with Gentoo) possess the privilege of upsetting the balance that keeps the ZUbuntu system alive and breathing, but the compilation, resolution, and installation of sources-cum-binaries will, with the improvements that will be made with APT, indeed, to slightly quote the fellow who started [this other thread]("http://ubuntuforums.org/showthread.php?t=51434") satisfy the so-called "n00b" in all of us.

Example: say that I want to install the latest, greatest Firefox (1.5 at the time of writing) and, simultaneously, get rid of the previous version as promptly as possible. So I click on the source package download link at Mozilla.com; it will immediately say "You have chosen to open Firefox-1.5.tar.gz which is a: gzip. What should Firefox do with this file?" However, instead of opening it with a file manager, it will open with.....um....what should I call it......ahh! "GComp"!

GComp will then open up as soon as the source package finishes downloading. It will ask "Into what do you want to compile this source?", to which you'll answer ".deb" (a drop-down scroll will allow you to select between different binary formats, which will probably lead to a porting of this to other Linux OSes if all goes well). It will then set forth to the compilation stage, which will, in the process, make sure that all dependencies are already resolved either prior to or during compilation. Then, when the compilation is done, the resulting binary will be installed using Synaptic (which will be opened upon GComp closing), for which you will have to enter your password in the standard fashion. The binary will then be installed in your own personal, computer-based library of binaries known as "Galaxy" (in the style of backports for Ubuntu and other OSes being named "Universe", "Multiverse", and so on). Galaxy will also handle all other binaries of similar/same origin. Also, if you have an eariler version of that same software, GComp will immediately uninstall it for you, again using Synaptic (if you sudo or root allow it, of course).

Such a situation as this will not only make Zubuntu an ideal OS for users who want more out of their system than can be, or is currently being, offered at current by the distributor, but will also possibly make it an ideal platform for Linux-centric software development. Not that Ubuntu kicks major ass already (its my own first love, first taste of the Linux operating platform), but Zubuntu could probably up it up a notch, not only for power users, but also for the most rabid of former-Windows converts among us (me included).

Thoughts?

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=raynevandunem]Zubuntu ("Z" as in "zoom!")

An Ubuntu derivative that will be geared toward power users (many of whom are Windows converts like myself).

It will combine the rock-hard stability of Debian and the userfriendliness of Ubuntu with the needs of high-powered users who want the most up-to-date (read also: "third-party") software without having to run into compatibility or dependency problems for the majority of the time (that is, until the easily-pitied fool decides to "play God" with the engine that drives the **basic** system. At that point, you're on your own, bub).

What will be introduced for this Ubuntu derivative is a, at this point, hypothetical new package management system that will make it easier and more understandable for people to DL and compile third-party sources into binaries. It may be slower than the current dpkg/APT, but it will make it even easier to comprehend for the average user, if not totally foolproofing it until further down the road of development.

Furthermore, a clear, easily-discernable distinction will be made between the engine (which will remain within the jurisdiction of the distributor, so a "no touchee" policy as far as end users are concerned will be applied) and the drivers seat (think Gentoo to an extent). Users will not (so easily, as they do with Gentoo) possess the privilege of upsetting the balance that keeps the ZUbuntu system alive and breathing, but the compilation, resolution, and installation of sources-cum-binaries will, with the improvements that will be made with APT, indeed, to slightly quote the fellow who started [this other thread]("http://ubuntuforums.org/showthread.php?t=51434") satisfy the so-called "n00b" in all of us.

Example: say that I want to install the latest, greatest Firefox (1.5 at the time of writing) and, simultaneously, get rid of the previous version as promptly as possible. So I click on the source package download link at Mozilla.com; it will immediately say "You have chosen to open Firefox-1.5.tar.gz which is a: gzip. What should Firefox do with this file?" However, instead of opening it with a file manager, it will open with.....um....what should I call it......ahh! "GComp"!

GComp will then open up as soon as the source package finishes downloading. It will ask "Into what do you want to compile this source?", to which you'll answer ".deb" (a drop-down scroll will allow you to select between different binary formats, which will probably lead to a porting of this to other Linux OSes if all goes well). It will then set forth to the compilation stage, which will, in the process, make sure that all dependencies are already resolved either prior to or during compilation. Then, when the compilation is done, the resulting binary will be installed using Synaptic (which will be opened upon GComp closing), for which you will have to enter your password in the standard fashion. The binary will then be installed in your own personal, computer-based library of binaries known as "Galaxy" (in the style of backports for Ubuntu and other OSes being named "Universe", "Multiverse", and so on). Galaxy will also handle all other binaries of similar/same origin. Also, if you have an eariler version of that same software, GComp will immediately uninstall it for you, again using Synaptic (if you sudo or root allow it, of course).

Such a situation as this will not only make Zubuntu an ideal OS for users who want more out of their system than can be, or is currently being, offered at current by the distributor, but will also possibly make it an ideal platform for Linux-centric software development. Not that Ubuntu kicks major ass already (its my own first love, first taste of the Linux operating platform), but Zubuntu could probably up it up a notch, not only for power users, but also for the most rabid of former-Windows converts among us (me included).

Thoughts?[/QUOTE]

So an Ubuntu with a GUI for Checkinstall?  Sounds good. That thing needs a GUI.

---

### Post by raynevandunem on 2006-01-08
[QUOTE=poofyhairguy]So an Ubuntu with a GUI for Checkinstall?  Sounds good. That thing needs a GUI.[/QUOTE]

Hell yeah! There will be a (furtherly comprehendible) GUI for every step of the way, from start to finish, thus further reducing the need for the power users among us to whip out (reluctantly, I'm afraid to say on my part) the command terminal.

Furthermore, it will make the end users somewhat less dependent upon backports (or the inclusion of further repositories which have been partially locked up save for the usage of a certain set of terminal commands which will release those BACK-backports to the user....frankly, this shouldn't be the case, or at least not necessary for even the average power user, since the distributors have found good reason for locking those specific repositories up in the first place). Of course, this will lead to a dying down of the endless package-management clamor which is heard in such threads as this.

On the other hand, what I'm expecting from the creation of this distribution is a greater demand by these particular users for more third-party (and hopefully open-source) software. This time, however, the calls will be aimed in the direction of the makers themselves (rather than the distros), and more directly so than ever before in the history of the Linux platform.

Is it OK to repost this idea to the front? and if so, which one?

---

### Post by doclivingston on 2006-01-08
[QUOTE=poofyhairguy]In fact, with the proven existance of that and things like Autopackage it points to the real problem- OSS software makers do not always want to spend the time to package their software. Releasing a tar file is easier. In Windows they HAVE to release a binary (aka the hard way) because there is no other option. In Linux there is MANY options for packaging and a few a near universal (Klik, Autopackage, Loki, whatever Firefox's thing is) yet most software developers pick the easiest route- the tar file. 

The only solution to that problem is to take away the tar file from developers. Then they would be FORCED onto a harder route like Autopackage. Of course this goes against everything Linux is, so don't expect it to happen any time soon.[/QUOTE]

Which would be better:

1) The developers concentrated on developing the program and making it better, and people who know lots about packaging make pakages, or
2) The developers, who probably don't know much about making .deb packages, .rpms and autopackages, quickly whip something together that has packaging issues.


By forcing developers to release the packages, you're forcing them to either learn all the intricacies of packaging (probably for several different packaging systems), or create crappy packages.

I, for one, would much prefer the developers concentrate on making the software better, and leave packaging up to the packaging experts.

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=doclivingston]Which would be better:

1) The developers concentrated on developing the program and making it better, and people who know lots about packaging make pakages, or
2) The developers, who probably don't know much about making .deb packages, .rpms and autopackages, quickly whip something together that has packaging issues.


By forcing developers to release the packages, you're forcing them to either learn all the intricacies of packaging (probably for several different packaging systems), or create crappy packages.

I, for one, would much prefer the developers concentrate on making the software better, and leave packaging up to the packaging experts.[/QUOTE]

Me too. Don't get me wrong Doc....I 100% agree with you. My comments on the matter were just to explain why tar files rule the day. I was not trying to imply that developers were lazy!


I don't care that they rule the day- I've learned how to use checkinstall. I can make my own packages.

---

### Post by MadMan2k on 2006-01-08
so might I sum up, that the only problem we have with ubuntu is, taht is has no rolling (development) release which could bring us ff1.5 + recompiled dependancies?

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=MadMan2k]so might I sum up, that the only problem we have with ubuntu is, taht is has no rolling (development) release which could bring us ff1.5 + recompiled dependancies?[/QUOTE]


Is that what Dapper is?

I thought the essential problem is there is not a magically easy way to install things that are not from the repos.....

---

### Post by MadMan2k on 2006-01-08
[QUOTE=poofyhairguy]Is that what Dapper is?[/QUOTE]
dapper will be released some time, so it is not rolling and new software wont be incorporated in the stabilizing phase.

[QUOTE=poofyhairguy]
I thought the essential problem is there is not a magically easy way to install things that are not from the repos.....[/QUOTE]
this is because you should not install things which are not from the repros.
But since the repros will never contain everything, it should be easier to package/ submit packages to universe, so that in the best case theat software will have to be compiled only once for ubuntu.

---

### Post by BoyOfDestiny on 2006-01-08
[QUOTE=MadMan2k]dapper will be released some time, so it is not rolling and new software wont be incorporated in the stabilizing phase.


this is because you should not install things which are not from the repros.
But since the repros will never contain everything, it should be easier to package/ submit packages to universe, so that in the best case theat software will have to be compiled only once for ubuntu.[/QUOTE]

Hmm.../me Checks OS... yep it's Dapper. Typing this in Firefox 1.5 64... 
Anyway, I do agree about the universe part. There are several GPL apps I'd like to see in Universe. Although checkinstall is a good tool in the mean time.

---

### Post by scaine on 2006-01-08
[QUOTE=r_a_trip]Sadly, the ones that are damaged by using proprietary software too long, have this misguided sense that they are entitled to go through every stage of FOSS development and have this experience be handheld and spoonfed. They never realize that they got very old and very tested software out of the box in the proprietary world.

That is why it worked so easily on their Mac and Windows distributions. That brandspanking new package they bought was already stale and the new version halfway done. But since it all happened behind closed doors, the old "new" package had a false sense of immediacy at the time of purchase.[/QUOTE]

God, this thread is so used up I don't know why I'm even responding.  But this is an intereseting and (for once) new issue.

But I find it only addresses one aspect of Autopackage, and the least important one at that : keeping up to date with new revisions of software.

I'm not concerned by that.  The reason I want autopackage (or an equivalent - raynevandunem's idea has merit, if it can work, although it's source only) is to make installing *new* programs easier.

You later go on in another post about taking the time to learn make/make install/blah blah blah, but that won't wash with many closed source programs.  Besides, why should a user have to take that time?  It's simple on other O/Ss - it should be made to be simple on Linux.  No, I didn't say it was simple.  I said it should be made to be simple.  Somehow.  I don't have the answer sadly, but I acknowledge the need.

What I find incredible is the resistance to an idea like this - make installations easy.  Only in Linux-land is such resistance apparent.  I think maybe there's a fear that simple installations will lead linux to the kind of spyware/virusware/adware mess that Windows is in.  Who knows?  But is that any reason to make software a nightmare to install?

Leech agrees with you, I see - but I know Leech is pretty competent around a LInux box.  I'm not so fortunate at the moment - I'm still learning.  I see your post as nothing more than a veiled attack on the "noob" linux user, of which I admit there are many.  They can be frustrating (I know I am), but in this, I think I have a point.

[QUOTE=r_a_trip]
I wish more people were like me. When I came to GNU/Linux I didn't come with a sense of entitlement nor was I making feature requests that were founded upon a misunderstanding of the OS and the community around it. I gave myself the time to get acquainted with this wonderful work that was offered Free (and even gratis). In the end every weird thing I encountered in the beginning had a very good reason for being so.[/QUOTE]

Sheesh - it's difficult to respond to comments like that without turning it into a personal attack...  let me just say that I'm very pleased that there are diverse people in this world and many of them are trying to make Ubuntu a better distro.  I just argue about it, but I'm pleased that guys like Mike Hearn are creating Autopackage, Leech is working on a web-based front end to Synaptic and so on.

[QUOTE=r_a_trip]
Too bad most people have turned into bored consumers these days, unwilling to spend more than ten seconds on every item that is presented in their lives.[/QUOTE]

That's a bit cynical.  It's taken me 10 months to get the point where I can compile the really simple apps, but I still get problems trying to install an Nvidia driver, for example.

My respect goes out to JDong and all the other packagers out there, but the point is that even though they cover a huge amount of work, there are always the Javas, the Flash players and the wma media files in this world that will never hit the repositories and desperately need an easier way to install themselves than having to apt-get build-essentials, ./configure, make, make install and so on.  Or run a .bin file from the terminal.  Or whatever.  It may be difficult, but surely we can all accept it would be a useful result if it can be achieved?

---

### Post by leech on 2006-01-08
[quote=scaine]Sheesh - it's difficult to respond to comments like that without turning it into a personal attack... let me just say that I'm very pleased that there are diverse people in this world and many of them are trying to make Ubuntu a better distro. I just argue about it, but I'm pleased that guys like Mike Hearn are creating Autopackage, Leech is working on a web-based front end to Synaptic and so on.[/quote]

Autopackage has good ideas, but bad implementation.  Nothing should be installed in the /usr unless it's part of the repositories, why else do you think that all the source compiled stuff goes into /usr/local?  There basically is a reason for the way things are.  It's not a case of trying to make it harder for people to install things.

I had hoped to have a lot more of the web based repository done by now, but have ran into a few snags...  mainly that e107 trashed itself after a security update, and now I'm trying out the cvs version of the .7 release and it's not quite done yet....  In the mean time I've been needing to find a job, you know that evil thing called money is kind of required :-({|= 

Leech

---

### Post by leech on 2006-01-08
[QUOTE=MadMan2k]so might I sum up, that the only problem we have with ubuntu is, taht is has no rolling (development) release which could bring us ff1.5 + recompiled dependancies?[/QUOTE]

It's called Debian Sid :D  It is a rolling distribution, and you can always volunteer to help package more things.  That's just the way things are right now.  Ubuntu doesn't have an unstable branch, it just has release and development.

There are really only a few differences with Debian and Ubuntu at the moment.  Mainly that Ubuntu generally has newer Gnome and X packages.  But a few small things like the Update-notification, and the add/remove applications.

But the gdm in Debian has a randomizer by default, and also has splashy, which actually will show an image when you're shutting down.

Debian also has a tendency to have newer versions of software than Ubuntu has in the Universe/Multiverse section.  

The cool thing about the way Debian's distribution is set up, you have stable, testing and unstable (with some stuff in experimental).  The way it is, you can either use these names as the distribution, or you can use the actual names (currently Sarge, Etch and Sid respectively), Sid is always a rolling distribution, like you said.  Etch is currently the same as testing, but if you want, you can leave your apt to point to 'testing' instead of Etch and you will always be getting whatever is in the testing branch, even after Etch releases.  The main difference between testing and unstable is that after a package goes into unstable, it is tested for conflicts with other packages and show-stopping bugs, and if there aren't any found for ten days, then it goes into 'testing'  So testing will always be pretty stable, if a little dated some times.  

The biggest thing I miss going from Ubuntu to Debian is the community forums, Debian has mailing lists, but they're just not as friendly.  

Leech

---

### Post by Bandit on 2006-01-08
[QUOTE=jecos]Theres nothing wrong with debians apt/dpkg!  The only people that think we need another package manager are the people that have the least experience with linux..

If you can't use command line then I don't think you should be suggesting anything but asking for help instead...[/QUOTE]
You nailed it right on the head ;)

---

### Post by Spark* on 2006-01-08
If things don't work when you put them into /usr/local, then this is not a good argument. If they work, then it shouldn't be too difficult to modify the installer to default to /usr/local. And of course there's always the option to install the application anywhere, thanks to the binary relocation stuff.

I don't see how it's possible to be upset about autopackage when you just consider it a more convenient alternative to tarballs (binary or source). It should only be used when appropriate and ideally only where it won't be able to break your system. Personally I see autopackage as most appropriate for slightly advanced users, who can take the responsibility for their actions (in other words, the kind of user who would have no problem formatting his Windows partition when something goes wrong). I don't need it, but if it can save me a few moments and the installation of unnecessary development packages, then I will use it. And I hope that Ubuntu will not condemn it, even they put a big "at your own risk" disclaimer on it. It has the potential to be good for everyone, even if it's not a new world order of package management.

---

### Post by MadMan2k on 2006-01-08
[QUOTE=leech]It's called Debian Sid :D  It is a rolling distribution, and you can always volunteer to help package more things.  That's just the way things are right now.  Ubuntu doesn't have an unstable branch, it just has release and development.[/QUOTE]
I know, I'm coming from sid - I changed, because I like Ubuntus desktop orientation.
It was the time when everyoby else was playing with Xorgs Composite, while debian still sticked with Xfree.

my dream would be a desktop orientated online distribution. (i.e. one with rolling releases)
Thats what Arch Linux basically is, but it lacks of maintainers and therefore you have to compile half of your packages yourself...

---

### Post by MadMan2k on 2006-01-08
[QUOTE=Spark*]
I don't see how it's possible to be upset about autopackage when you just consider it a more convenient alternative to tarballs (binary or source).[/QUOTE]
the point is that autopackae cant be convinient at all, since its basically just another distribution.
If somoene needs more recent packages, I would rather suggest him to take the stuff from debian unstable, since it will work better with ubuntu. (packagemanager integration is the most obviuos thing)

The problem with autopackage or any other binary distribution method ist that it relies on ABI, which has too many draw offs IMHO.

---

### Post by Spark* on 2006-01-08
Of course it can be more convenient, because it is. :P The ABI compatibility problem is getting a little overblown IMO. For some kind of applications it just isn't a big deal. Take Firefox, OpenOffice.org or most commercial games. They all provide binary installers which don't always work, but most of the time they do. Whether you provide a tarball, your own custom installer or an autopackage, the only difference is that autopackage is much cuter than the alternatives.

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=MadMan2k]
this is because you should not install things which are not from the repros.
But since the repros will never contain everything, it should be easier to package/ submit packages to universe, so that in the best case theat software will have to be compiled only once for ubuntu.[/QUOTE]

The MOTU is kinda strict about what goes in the Universe for a reason.

What I think would be more practical is just some random third party repo where you can submit debs. A "use at your own risk" type thing. The Universe has high standards.

I have been thinking this has been needed ever since the Backports went official. It would be cool to have a backports where the hands are not tied as much.

> 
my dream would be a desktop orientated online distribution. (i.e. one with rolling releases)
Thats what Arch Linux basically is, but it lacks of maintainers and therefore you have to compile half of your packages yourself...

It exists. Its called Gentoo. 

Basically the problem is that its hard to package things. Ubuntu and Sid do the best jobs in the Linux world, but for some its still not enough. No distro will ever have enough resources to package every single application possible. The only way to get that is with a Gentoo....Gentoo packages are easy to make.

I personally believe that the whole problem of "I can't find this package" will be solved one day with a portable portage. One day I dream that portage will be made more indepent of Gentoo and the faster computers of the world at the time will just be able to compile easily any package that has no deb.

Yeah, I know we are back to compiling. But just like Mark I do not think any other answer is really pratical...

---

### Post by r_a_trip on 2006-01-08
*Leech agrees with you, I see - but I know Leech is pretty competent around a LInux box. I'm not so fortunate at the moment - I'm still learning. I see your post as nothing more than a veiled attack on the "noob" linux user, of which I admit there are many. They can be frustrating (I know I am), but in this, I think I have a point.*

You are forgetting one thing. The one thing being, that I started out a complete GNU/Linux noob myself (started out as an Amiga GUI clicker, then DOS, then Windows) and I took the time to learn the stuff and get skills that reward me with an OS that obeys me. Or did you really think I was born a Unix guru?

I'm not attacking a lack of knowledge, I attack the unwillingness to gain knowledge at every turn. The world doesn't need another clickdrone which has to be handheld till the day he or she dies. As a beginner you can't have it all within ten minutes. There is stuff that needs knowledge. If you really want a spoonfed system, go out and get a for pay system which is designed to get you hooked from cradle to grave on non-skill computing.

If you are in it for the long haul, gaining skills will only serve you. If you are just using GNU/Linux to weather over the tides before jumping ship to a closed source system that isn't overrun by malware, I don't think the community should spend much time making you comfortable. GNU/Linux is not just an OS, it is also a commitment to protect personal and societal Freedom in the information age. A typical GNU/Linux user is not only a user but also an activist of sorts.

*But is that any reason to make software a nightmare to install?*

Software install on GNU/Linux isn't harder than on Windows, if you use sanctioned packages. The problem is that many try to use unsanctioned packages. These unsanctioned packages don't fit the system, they have to be made to fit and not every new user can be assigned a personal packager. That is where the user comes in him- or herself. If a new user perseveres and learns how to be rewarded with difficult to obtain software by increasing their own skill level, then not only the user grows, but the community also. There is no taking without giving back, we are all in it with eachother. There is no big Linux Inc. we can call for support and fixes, there is only the community.

It is just that noobs see all the different distributions as one thing and that is Linux. This is a falsehood altogether. Fedora is a different OS than SUSE or Ubuntu, but yet you want universal software between them. Just use software certified for your Distribution or learn how to roll your own (skills that enable you). Why all the different GNU/Linux-based OSes need to be binary compatible and Windows and Mac OS X don't is quite a puzzle to me.

*That's a bit cynical. It's taken me 10 months to get the point where I can compile the really simple apps, but I still get problems trying to install an Nvidia driver, for example.*

Yes, and I have spend 5 years on GNU/Linux and have acquired an arsenal of knowledge that will serve me the rest of my Unix lifetime. Don't forget, you have to unlearn Windows, which takes over two years (at least it did in my case). At the same time you need to learn Unix which takes about three years (ditto: my case) and then it is maintenance and discovering even more possibilities. Not everything will be put in a GUI upon release. 

If your response is that that is a waste of time, you will never be satisfied with GNU/Linux. GNU/Linux is an enabler for those willing to learn how to work with it. It is a base of knowledge, made for everybody willing to invest in it with time, effort and some money.

*My respect goes out to JDong and all the other packagers out there, but the point is that even though they cover a huge amount of work, there are always the Javas, the Flash players and the wma media files in this world that will never hit the repositories and desperately need an easier way to install themselves than having to apt-get build-essentials, ./configure, make, make install and so on. Or run a .bin file from the terminal. Or whatever. It may be difficult, but surely we can all accept it would be a useful result if it can be achieved?*

Not to deliberately smash your hope, but all the software you mention here is made by proprietary companies which have no commitment with FOSS. The chances that they will release easily GNU/Linux usable packages is pretty dim in itself. When it comes to WMA and WMV, these are the property of an openly GNU/Linux hostile company, which has stated before that GNU/Linux is like packman, infecting everything it touches, is like a cancer and un-American. Do you really think the chances of superb MS format support is great?

We can only get good media support if we increase the usage of our own formats like Ogg Vorbis, Ogg Theora, Open Document Format. Flash and Java are being reimplemented in FOSS versions, so that they can be easily integrated and shipped without problems.

GNU/Linux doesn't exist to be a drop in replacement for Windows, it doesn't exist to make life of newcomers harder either. It exists to create a base of computer software that can be used by anyone willing to use it, protected against coercive conditions through its licensing and supported by peers like you and me (well, once you get in tune with the community spirit that is).

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=scaine]
You later go on in another post about taking the time to learn make/make install/blah blah blah, but that won't wash with many closed source programs.  Besides, why should a user have to take that time?[/QUOTE]

There is the first problem- fear of a learning curve.

Why should users take the time to learn any parts of a new OS? Why not just make a Windows clone if the point is to shorten the learning curve as much as possible?

Users should have to take the time because thats a part of Linux and they want something from that part- new applications.

> It's simple on other O/Ss - it should be made to be simple on Linux. 

There is the second problem- a level of expectations that is unreasonable.

Linux is a kernel. There is no single "Linux." It can't be made simple on "Linux." Autopackage (which again I say I support) will try to make it easier of Ubuntu and Mandriva and SUSE and Knoppix, but not "Linux." I don't expect it to work on my sister's TiVo or her cell phone. Its great for third party binaries though- it was needed for that. But its not a total solution to the entire problem.

"Linux" is not a desktop OS. Heck, its not an OS at all. Its part of an OS. Everyone calls all of these distros "Linux" because we are lazy and because the word has some mindshare. Its easier than "Ubuntu, a Linux/Debian/Xorg/Gnome/GNU based distro." But thats what it really is.

> 
 No, I didn't say it was simple.  I said it should be made to be simple.  Somehow.  I don't have the answer sadly, but I acknowledge the need.

Third problem- demands from users but no solutions. If people like Mark don't see a solution...

Ok. Let me admit the Mr. Hearn has done more than I expected at first. Autopackage is almost "there." But even at its peak Autopackage is not a magic solution. Why?

Because if Autopackage does not have what you want packaged then you are in the same boat as if the repos do not have it. So again you are limited by the amount of Autopackages. And in Linuxland the best packagers are inside each of the distros making distro specific packages- no group is paid to put together Autopackages like a group is paid to put together distro packages. So its "repo" might always be behind the Sid repo....so even a magical new package format does not solve the problem that there are not enough packages.

Fourth problem- that its hard to make packages. I know- I have tried many times. I have never had success without checkinstall because making debs the real way is hard. I'm sure its not cake walk making RPMs or Kliks either.

If it was easy to make packages- if you could just send tar files into some magic packaging program and it always pops out perfect debs then the problem would be solved. Each developer's site would release tar files and debs because that would be almost just as easy. But that program will never get made because its not that easy. A GUI to checkinstall if the best we could get.

The reason OSX and Windows lacks these problems is that developers are FORCED to make packages. Unlike GNU/OSS developers which have the luxery to skip that step on the Linux platform, they HAVE to go through the pains of making OSX and Windows packages or those users would never use them. Neither OS has an easy to install compiler ready to put together the tar files. You either package it or no one uses it. It would be impossible (and a waste I say) to force Linux developers to have the same philosophy. They would rather leave packaging to the packagers.

> 
What I find incredible is the resistance to an idea like this - make installations easy.  Only in Linux-land is such resistance apparent. 

As I went through your initial points I pointed out one at a time each of the main problems to illustrate where a "resistance" comes from. Even listed them. So now you know. Well I did leave one problem out.

> 
 I think maybe there's a fear that simple installations will lead linux to the kind of spyware/virusware/adware mess that Windows is in.  Who knows?  But is that any reason to make software a nightmare to install?

Final problem- its far harder than any user who demands these things wants to admit.

Sure I admit some people would prefer to see it harder install third party programs because of security problems, but I promise they are in the minority.

There is not some group of long bearded Gnu-nerds who block the progress of a universal installer at every turn. There is not a real resistance to making software easier to install for users- otherwise apt-get and rpms and portage would have never been built.

The reason a universal installer does not exist is because its too hard to make it happen. It just is. Its not to be mean to new users, or to make life hard for those wanting new Firefox. Its because its just too hard.

The only way a universal installer would work 100% of the time like in Windowland (and only a truly universal installer could get the support needed to get rid of the "I can't find that deb" problem) is if the distros got together and made some Desktop Linux platform. Some distros actually like this idea- I think Mandriva does. But one or two is not enough. ALL would have to go along with it. And all won't. 

Why? Because they hate new users? No...because it would compromise the goals of that distro. 

Lets say some magic platform was made. Fedora, SUSE , Ubuntu, and Mandriva got together and said "for one year each distro with have the exact same libs with the exact same versions (and whatever else is needed to make universal binaries work)." Lets say that happened.

Lets just look at the sacrifices just Ubuntu would have to make: First of all the two releases a year would go out the window. And Ubuntu would have to spend its (very limited) resources making sure that one release a year fits all of these criteria. Then Ubuntu would have to spend time hammering out this new standard each year, making sure the parts it wants the most (say...mono) got included in the commitee. And if those parts did not get included, Ubuntu could not develop in that direction for a whole year (in case next year such was not accepted either).

Development of Ubuntu (which is at break neck speeds now) would slow to a crawl. And thats just Ubuntu. Each distro would have to make the same sacrifices. Thats why Mark throws out the idea of binary compatibility time and time again. Its not him being mean, its him not wanting to be held back. And because the licenses let him, he does not have to be held back. So why volunteer to do it? 

So a "Linux Desktop Platform" is a pipe dream. The best that can happen is an Autopackage (aka a third party using tricks to tie the distros together) and even thats only works in limited cases. The only way I ever see a platform existing is if one distro gets so much more popular than the rest that the rest have to remain compatible or be ignored. Say if Ubuntu became the most popular Desktop Linux by far, SUSE would have to be able to install Ubuntu debs or it would never compete. But there has not been an "IT" Desktop Linux yet, and there does not appear to be one in the near future.

So THATS why the resistance exists. Its not to torture new users. 

Heck, even the heart of Linux is against such things. Linus refuses to add a stable way too get closed binary drivers to work with the Linux kernel. He thinks (rightfully) that if he was forced into making a stable platform for that it would hinder Linux kernel development.

So there you go. From the bottom (Linus) to the top (Mark) the entire process is one that is not compatible with a "Linux .exe." Its part of the essential nature of Desktop Linux- one of the things you choose to accept if you walk down this path.

Some would say the real problem is not the system (which manages to push out two Ubuntus and many kernel versions a year) but instead that new users do not know what they are getting themselves into.

I love this topic because its more than "why is it hard to install things in Linux." Its a real example of what differences Linux based distros have compared to OSX and Windows.

I embrace the differences. You might not. Each to their own. Thats what true freedom is.

---

### Post by r_a_trip on 2006-01-08
Poofyhairguy, you've said I was your new hero, but you flatter me too much. It is you who is much more of a hero than me.

My general reaction to "stupid" newbie questions is **"get with the program"**. You on the otherhand, you are open and warmhearted. You take the time to respond to newbies very kindly and you explain it to a much better degree than I do.

Keep it up. You are one heck of an ambasador for Ubuntu and GNU/Linux in general.

---

### Post by MadMan2k on 2006-01-08
[QUOTE=poofyhairguy]The MOTU is kinda strict about what goes in the Universe for a reason.

What I think would be more practical is just some random third party repo where you can submit debs. A "use at your own risk" type thing. The Universe has high standards.

I have been thinking this has been needed ever since the Backports went official. It would be cool to have a backports where the hands are not tied as much.[/QUOTE]
Arch Linux hast that - its called Trusted User Repositories, where selected Users are hosted by the arch project.

[QUOTE=poofyhairguy]
It exists. Its called Gentoo. [/QUOTE]
oh, I forgot to add that I want a binary distribution - I also used Gentoo until I relised that compiling myself is plain useless in most of the cases.

[QUOTE=poofyhairguy]
I personally believe that the whole problem of "I can't find this package" will be solved one day with a portable portage.[/QUOTE]
it already exists in freeBSD an is called Ports - thats what Portagegot its name and "inspiration" from.
Arch Linux also offers something similar for the binary Linux world.

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=r_a_trip]Poofyhairguy, you've said I was your new hero, but you flatter me too much. It is you who is much more of a hero than me.

My general reaction to "stupid" newbie questions is **"get with the program"**. You on the otherhand, you are open and warmhearted. You take the time to respond to newbies very kindly and you explain it to a much better degree than I do.

Keep it up. You are one heck of an ambasador for Ubuntu and GNU/Linux in general.[/QUOTE]

Thanks. I blush.

---

### Post by Spark* on 2006-01-08
Well, there is [Conary](http://wiki.conary.com) of course which makes packaging a snap (they are "cooked" from simple recipes which are similar to ebuilds) and the features for distributed repositories are interesting as well. I'm still keeping an eye on [Foresight](http://foresightlinux.com).

(I just realized this reads like an advertisement ;-))

---

### Post by scaine on 2006-01-08
Well - that's one hell of a post, Poofyhair.  I reckon that post (#291) should be given a medal!  It's a beaut.

I'll be very brief (because - a. surely nearly everything has been said now and - b. the new 8178 Nvidia drivers have just finished updating on my system and I'm gagging to try them with gcompmgr).

[QUOTE=poofyhairguy]There is the first problem- fear of a learning curve.
[/QUOTE]

Well - I'll stop you there.  I agree with you, but my Mum doesn't.  I'd like to give her Ubuntu, then for example, talk her (over the phone, since she'd 80 miles away) through downloading and installing Skype.  Ain't gonna happen on Ubuntu, sadly.

[QUOTE=poofyhairguy]There is the second problem- a level of expectations that is unreasonable.
[/QUOTE]

It's a problem, again I agree.  But unreasonable expectations got us Linux in the first place.  You could even argue it got Mark into space.  Let's not build up the problem cos it's diffuclt.  A great Dan Brown quote is "Everything is possible - the impossible just takes longer".

Also, you latched on the fact that I used the word "Linux", when I instead meant "Ubuntu".  I've already made the point (about 200 posts ago) that these terms are used too interchangeably...

[QUOTE=poofyhairguy]
Third problem- demands from users but no solutions. If people like Mark don't see a solution...
[/QUOTE]

We agree that at least some people are giving it their best shot.  Hats off to them.

[QUOTE=poofyhairguy]
Final problem- its far harder than any user who demands these things wants to admit.

<snip>

The only way a universal installer would work 100% of the time like in Windowland (and only a truly universal installer could get the support needed to get rid of the "I can't find that deb" problem) is if the distros got together and made some Desktop Linux platform. Some distros actually like this idea- I think Mandriva does. But one or two is not enough. ALL would have to go along with it. And all won't. 
[/QUOTE]

A couple of quick points here.  First off, I don't think they *all* have to go along with it, just most.  Then the rest are more likely to follow.  Maybe.  Also, let's not go down the binary compatibility route as a given either, which you explain in great detail would hurt various distros plans for Linux.  All I'm hoping for is a unified experience for installing non-repo software.  Maybe it'll compile silently in the background, maybe it'll run a .bin file, maybe it's detected that the binary in it's package is compatible with my Ubuntu system.  Whatever, but hide it and make the front end understandable.

Second - the Gnome 10x10 project would appear to have a bearing on the "Desktop Linux platform" idea.  Personally, the way Gnome's going, I think it's losing ground to KDE, but I'm ignorant of take up in the corporate (which is where it matters most), so maybe I'm wrong.  But if Gnome 10x10 takes off, perhaps there's hope that an underlying unification of installation can happen too.  Who knows?

[QUOTE=poofyhairguy]
I love this topic because its more than "why is it hard to install things in Linux." Its a real example of what differences Linux based distros have compared to OSX and Windows.
[/QUOTE]

Me too.  Because I think that ease-of-installation is at the core of Linux (and I do mean Linux this time) take up in the home.  I work in a systems department of 60 staff.  Of those, I run Ubuntu.  That's it.

Every single person (around 15) that I've given a live CD to, claimed that it was too difficult to get stuff to work that they'd downloaded from the Net.  Some of this stuff was obviously just negativity on their part, some was ignorance of the repos.  But most of us like our BitTorrent at work and getting Java to work was a shocker for most of them.  Or their Nvidia acceleration.  Or Skype.  Or something else they just "expect" to work (back to Poofyhair's "expectation" line again).

But the point is that I don't think it's unreasonable to expect things like that to work.  Seriously, if Gnome 10x10 takes off, maybe Sun will have to provide an easier way to make this happen.  But that's just one example.

[QUOTE=poofyhairguy]I embrace the differences. You might not. Each to their own. Thats what true freedom is.[/QUOTE]

That old biblical quote comes to mind : "Have the courage to change what you can, and the wisdom to know what you cannot".  However, in this case, there are a few guys who either have more courage, or less wisdom that you and me.  They're working on Autopackage.  Good luck to them.

---

### Post by aysiu on 2006-01-08
[QUOTE=scaine]
Every single person (around 15) that I've given a live CD to, claimed that it was too difficult to get stuff to work that they'd downloaded from the Net.  Some of this stuff was obviously just negativity on their part, some was ignorance of the repos.  But most of us like our BitTorrent at work and getting Java to work was a shocker for most of them.  Or their Nvidia acceleration.  Or Skype.  Or something else they just "expect" to work (back to Poofyhair's "expectation" line again).[/QUOTE] I wouldn't give people like this a Ubuntu live CD. I'd give them Mepis, Knoppix, or PCLinuxOS.

---

### Post by r_a_trip on 2006-01-08
*But the point is that I don't think it's unreasonable to expect things like that to work.*

In a world where everything was alright, yes, it would be so. But I have given up hope on decent proprietary support from big name firms. Most companies work against FOSS. Even Sun does it with their not quite FOSS OpenSolaris.

Java, Skype, MS fileformats, Flash, they all will be nails in the coffin of FOSS, unless we rip them out of the equasion and replace them with FOSS software, where the community calls the shots and has the Freedom to develop and ship it.

A peaceful cohabitation of closed source and FOSS is ultimately a pipe dream. The core essence and goals of the two systems are mutually exclusive. They might be aggregated right now, but they can't integrate with eachother. Like mayonaise, it is a mixture that is only artificially held together. If the heat turns up they will fall apart, just like mayonaise.

I am just looking at the long run. The schism between closed source and FOSS might fall in my lifetime and then I want to be on the side that respects my needs the most, hence FOSS and hence my zeal to keep it sane and sound.

---

### Post by ZephyrXero on 2006-01-08
I know I'm coming in kind of late to the discussion...so if I repeat something already said, forgive me and just let me know ;)

Out of the few pages on this thread I've thumbed through, there's alot of talk about how cross-distro "binary compatability isn't possible." Hell, even Shuttleworth said it recently when he shot down the debian consortium idea again...

Sadly the solution is quite simple, and many don't see it staring them in the face. Staticly linked libraries... Numerous open source apps are released as static binaries that you simply unzip to a folder of your choice and run. And a fairly complex program like Firefox or Blender runs just as well in this form as one that has been placed on your system by way of package manager and repository.

The only real problem with this solution is it will take up far more disk space. This is pretty much the whole reason dynamicly linked libraries were invented. But with today's modern systems it's not really an issue anymore. You can buy a 200GB harddrive for less than $100 now and even the cheapest prebuilt systems come with at very least a 40gig.

Now just grabbing tar/zips/whatever and dropping them all in your home directory isn't exactly the best way to manage your system, so some sort of simple management is still needed even for this solution.

Luckily the autopackage devs already realize this. If you look at their faqs they pretty much tell developers flat out to staticly link all the libraries and such they will need unless it's an extremely common/large one like glibc or gtk.

So following this train of thought, to have cross-distro binary compatability, only a very small portion of programs and libraries would have to be standardized.

Now one other issue that arises is legacy/backwards compatability. For a truely smooth, compatable system you would probably need multiple versions of the same libraries. This is one reason I'm getting very interested in GoboLinux's alternative file structure, and I wish more distros would follow their lead. But this is a completely different discussion to be had, so I won't go into that any further...

I also am of the opinion that there will need to be one dominant distro (at least for a little while) before we really see much progress in standardization. And just as others have said I would never wish this upon all distros, just the most common desktop distros. Open source development is very much like evolution, so luckily at some point a clear "fittest" distro is going to come out on top while the "less fit" slowly die out...yet there will always be new interesting alternatives created too.

I don't know if Autopackage is the perfect solution to any of these problems, but they are certainly making a giant stab in the right direction. I think the real issue we need to look at here is whether or not distro developers work with them or against them. If autopackages and the native package managers could co-exist peacefully I think it could mean great things for all Linux adoption by casual/average users.

---

### Post by leech on 2006-01-08
[quote=scaine]Every single person (around 15) that I've given a live CD to, claimed that it was too difficult to get stuff to work that they'd downloaded from the Net. Some of this stuff was obviously just negativity on their part, some was ignorance of the repos. But most of us like our BitTorrent at work and getting Java to work was a shocker for most of them. Or their Nvidia acceleration. Or Skype. Or something else they just "expect" to work (back to Poofyhair's "expectation" line again).[/quote]

Well, not to beat a dead horse, but none of this stuff works out of the box for windows either.  Drivers have to be downloaded or skype or even Java.  

So instead of going to seperate sites for all of these for Ubuntu, generally you can go to one site (this forum) and find links to everything so you can just run a few command lines and they're working.

Let's do a quick comparison between Windows and Ubuntu.  Right after installation of Windows XP (I'm not talking a slipstreamed one, 'cause most of them are not.  Even a lot of the Dell XP CDs don't have all the drivers they should) you still have to install all your drivers (Video, chipset, network, sound) Under linux, you install... video drivers.  In most cases, all the other drivers will be installed by default.

Next, under XP.  Java, Flash, Skype, Office, Firefox (sorry, this is required :D).  Anti-virus, firewall.  

Under Ubuntu.  Java, Flash, Skype.  

Really Ubuntu is just better out of the box.  It's certainly more usable.  

I think what perhaps would be good for Dapper is instead of a little webpage that kind of tells what Kubuntu/Ubuntu is, we should have a quick how to on finding and installing new software and talk about how certain things will need to be configured by the user for full enjoyment.  I think this would go a very long way on improving the user experience.

Leech

---

### Post by ZephyrXero on 2006-01-08
[QUOTE=r_a_trip]A peaceful cohabitation of closed source and FOSS is ultimately a pipe dream. The core essence and goals of the two systems are mutually exclusive. They might be aggregated right now, but they can't integrate with eachother. Like mayonaise, it is a mixture that is only artificially held together. If the heat turns up they will fall apart, just like mayonaise.[/QUOTE]

I think this is a pretty negavite, close-minded and FUD-like way to look at the world. People are always going to need money to live while developing software, and just charging for support or bounties aren't always gonna cut it. I like to look at the balance between open source and closed source stuff in a fairly utilitarian way. The more common/useful/necessary a piece of software is the more there will be a need for it to be free (libre) software. The less common, less needed and more specialized something is the more likely it is something appropriate to be at least partially proprietary.

Let me give some examples... of course something like your operating system and drivers should always be 100% open sourced, as they are the most necessary and common components of your system. Yet something like specialized accounting software or a video game may not be appropriate to make fully open. In the case of a video game, developers would be better off using open source development tools, libraries, and possibly even engines...yet if they release their games completely free of charge and free to redistribute, no one will ever feel a need to pay for it. Who's gonna need to get tech support on the phone while their trying to play some Mario? Now perhaps something like a MMORPG could be succesful with the tech support model, but generally a piece of software that's intended simply for entertainment purposes isn't going to be very feasable with the traditional open source models we've seen so far.

So once again, in case my point was lost amongst my little rant there...if it's something like a driver, file format, browser or operating system... sure, it should always be open sourced, but if it's software that only benefits a select few or is purely for entertainment purposes it isn't really feasable...money wise.

Now as I agree people like Sun are doing a real halfass job of being true to open source as they claim...not everyone's like that. It will probably take many years if not decades for the average person to see the benefits of open source and collaboration as opposed to the old proprietary ways. But in the end, as long as some sort of rediculous software patent laws don't get passed, I think open source and it's odd relationship with proprietary software will be here to stay.

PS. Sorry for getting off the main topic, but as AP is much more feasable for proprietary apps I figure this is still relevant to the tread ;)

---

### Post by doclivingston on 2006-01-08
[QUOTE=ZephyrXero]Sadly the solution is quite simple, and many don't see it staring them in the face. Staticly linked libraries... Numerous open source apps are released as static binaries that you simply unzip to a folder of your choice and run. And a fairly complex program like Firefox or Blender runs just as well in this form as one that has been placed on your system by way of package manager and repository.

The only real problem with this solution is it will take up far more disk space. This is pretty much the whole reason dynamicly linked libraries were invented. But with today's modern systems it's not really an issue anymore. You can buy a 200GB harddrive for less than $100 now and even the cheapest prebuilt systems come with at very least a 40gig.[/QUOTE]

That is not the only disadvantage of statically linking aganist libraries. Two more that spring to mind are:


1) Updating libraries. If you statically link against a library, you need to rebuild the application when a newer version of the library comes out. This is a particular problem if the new version is to fix a security flaw or critical bug.

With the zlib security flaw that came out a while back, most linux distros just had to update the system installed one, and that was it. Fixing it on Windows (where applications statically linked to it, or had their own dll) required updating *every* application that used zlib to fix the problem.


2) Conflicting libraries. There are some libraries for which it is impossible to run multiple versions at one. Not moderately difficult, or really hard, *impossible*.

For example, you can't run multiple mDNS stacks on one machine[0]. So if you are running Avahi, and the program statically links to Howl or another copy of Avahi, then you're out of luck. Forcing two mdns stacks to run will probably lead to a cascade of looping response packets - which is effectively performing a DoS attack on your own machine.


[0] technically you can, but they MUST be bound to different network interfaces, which makes it not applicable to most peoples machines.

---

### Post by ZephyrXero on 2006-01-08
As while I see your point with number 1, number 2 is not impossible. This is particularly why I made mention of [Gobo]("http://www.gobolinux.org/"). With the way their system is setup, you can have a practically unlimited number of versions for the same library as you so choose. Of course in a system like Ubuntu, the distro devs would make those decisions...but no, it's not impossible.

Now, back to point #1. I'm still not sure this is that huge a deal. Programs such as Firefox, can patch themselves now without need for a full reinstall, and hopefully more will follow in the future. Also, a library as common as zlib is NOT what I was talking about ;)

---

### Post by Aphorism on 2006-01-08
Grr...

> Orignal quote from ZephyrZero:
I think this is a pretty negavite, close-minded and FUD-like way to look at the world. People are always going to need money to live while developing software, and just charging for support or bounties aren't always gonna cut it. I like to look at the balance between open source and closed source stuff in a fairly utilitarian way. The more common/useful/necessary a piece of software is the more there will be a need for it to be free (libre) software. The less common, less needed and more specialized something is the more likely it is something appropriate to be at least partially proprietary.


What has that got to do with open source?  Free speech has nothing to do with charging for vocals.  Free software has nothing to do with free beer.  Get with the program and deal with it.  It is sickly and ill-informed statements such as this that confuse exactly what the goals of free software and open source are trying to achieve.  It is in the founding documenations from Richard Stallman.  Perhaps you need to educate yourself on exactly what the implications of free software are:

[http://www.fsf.org/](http://www.fsf.org/)

Read the top bold thing.

---

### Post by ZephyrXero on 2006-01-08
No, even Stallman has said that things such as video games may not be feasable as free software. I know plenty about what I'm talking about buddy, these concepts aren't exactly new to me... Some extremists like RMS may not completely agree with all that I said/think...but you need to look into the real world implications beyond just the ideals.

Give me a few minutes and I'll post a link...

Update: Well, I couldn't find the interview/article I was thinking of, but I did find [this]("http://www.gnu.org/licenses/licenses.html#OtherWorks"). "We don't take the position that artistic or entertainment works must be free..."

This doesn't completely cover what I was talking about...but it's a portion. When someone pays money for free/open source software they are either paying for a physical copy, tech support, a specific bountie or just making a donation. This unfortunately isn't applicable for all types of software (my original point).

But this has gotten way further off topic than I intended so please PM me or start a new thread if this is going to continue...

---

### Post by Buffalo Soldier on 2006-01-09
Wow... I wonder how could I have missed this thread... can't believe it's been going on for 3 weeks. I can't even think where/how to give a reply.

One think for sure... I stand with the current way/method of repository in Ubuntu and Debian and the reasons have been all laid out through out this thread.

But guys... especially the ones who joined this forum from the very beginning... late 2004... doesn't this thread ring a bell? When I read the post by [Breepee](http://ubuntuforums.org/member.php?u=14107), [Halvorsen](http://ubuntuforums.org/member.php?u=53607) and [Jengu](http://ubuntuforums.org/member.php?u=25331) ... they remind me of a couple of forum members from a time long long ago.

Any of you guys still remembers [wowbuntu](http://ubuntuforums.org/member.php?u=21225), [Sushi](http://ubuntuforums.org/member.php?u=31905), [its_jon](http://ubuntuforums.org/member.php?u=33970), [MaZiNgA](http://ubuntuforums.org/member.php?u=1777) and [sisya](http://ubuntuforums.org/member.php?u=6519)?

Maybe these threads can bring back some old good "sweet" memories ;) :[list][*] [open source community?? huh!](http://ubuntuforums.org/showthread.php?t=12976)
[*] [Linux needs to be more Stylish](http://ubuntuforums.org/showthread.php?t=11722)
[*] [Dissapointed in Linux yet again](http://ubuntuforums.org/showthread.php?t=57706)
[*] [A call to arms: Linux needs to "just work"!](http://ubuntuforums.org/showthread.php?t=64760)
[*] [Why I hate Ubuntu](http://ubuntuforums.org/showthread.php?t=41612)[/list]

I guess every once in a while... this kinda members and threads will exist in here :p

---

### Post by doclivingston on 2006-01-09
[QUOTE=ZephyrXero]As while I see your point with number 1, number 2 is not impossible. This is particularly why I made mention of [Gobo]("http://www.gobolinux.org/"). With the way their system is setup, you can have a practically unlimited number of versions for the same library as you so choose. Of course in a system like Ubuntu, the distro devs would make those decisions...but no, it's not impossible.[/quote]

For most libraries, I agree with you, and it ranges from easy to do to hard. But there are some (although not very many) libraries where it is impossible to run multiple versions at one - the mDNS example I gave is one.

[http://avahi.org/wiki/Avah4users](http://avahi.org/wiki/Avah4users) gives a very short explanation, but there are features of mDNS that **will** cause problems if you run more than one implementation on the same machine.


> Now, back to point #1. I'm still not sure this is that huge a deal. Programs such as Firefox, can patch themselves now without need for a full reinstall, and hopefully more will follow in the future. Also, a library as common as zlib is NOT what I was talking about ;)

While that's great for bigger projects, but supporting that kind of thing would be a *lot* of work for smaller projects. One of the reasons for using AutoPackage, is that it lets you use software not in the distro repositories - and the software not in there, tends to be the smaller/less well known things.

---

### Post by macleod199 on 2006-01-09
[QUOTE=MadMan2k]
they have to compile it anyway too see if it runs - and if it does all they have to do on windows is to zip it.
This will not work on linux due to the mentioned problems.
[/QUOTE]

Have you ever developed any software? This is *not* how it works on Windows. If you use visual studio you often have to make sure your users have (or distribute) the VS runtimes. If you use GCC your users have to have cygwin or mingw32 dlls which you have to figure out how to package/distribute. Why do you think there's so many Windows installer products (e.g. InstallShield, the Nullsoft installer, Windows MSI.....)

There is dll hell just like there is rpm hell and dependency hell.

---

### Post by Spark* on 2006-01-09
[QUOTE=ZephyrXero]I think this is a pretty negavite, close-minded and FUD-like way to look at the world. People are always going to need money to live while developing software, and just charging for support or bounties aren't always gonna cut it. [/QUOTE]

*People* don't get money for proprietary software. *Companies* do. People get money for doing contract work, whether the result is open source or proprietary doesn't really matter. It is probably more common for software developers to be hired for in-house development anyway, or to do customizations for a client. As long as people need software, other people will be paid to work on it. So the whole idea that we need proprietary software because people need to eat is completely flawed. What is usually meant by that is that we need proprietary software because a select few people want to drive Porsches.

In case of videogames I do indeed agree that the opensource model only makes limited sense, but it would make sense do develop the game engine as opensource and only keep the actual content proprietary. If you think about it, there are only a select few companies who develop their own high-end game engines anyway, while most others license it from them. So using opensource engines could at some point be economically very reasonable for many companies _and_ lead to better games, since they could spend more ressources on the content (which to me is what games are all about) and polishing the gameplay.

---

### Post by r_a_trip on 2006-01-09
*Luckily the autopackage devs already realize this. If you look at their faqs they pretty much tell developers flat out to staticly link all the libraries and such they will need unless it's an extremely common/large one like glibc or gtk.*

In which case Autopackage itself becomes unnecessary. A big statically linked app could be made into a pretty dumb selfextracting tar.gz, which just dumps the content in /opt/appname. Oh wait a minute, that is roughly what Autopackage is :), but dumping instead in /home/user or /usr. So the magic behind Autopackage is just duplicating the Oses libs for each and every application. Innovation Redmond style.

*I think this is a pretty negavite, close-minded and FUD-like way to look at the world.*

No, it is a valid way for some to look at the world. Just because you don't agree with that view, doesn't make it negative, close-minded or FUD.  Free Software is only Free Software if it is unencumbered. As soon as you put one piece of non-redistributable proprietary software on a disc with 99.9 %  Free Software, you have removed one of the four Freedoms attached to Free Software on that disc.

I can't give you a copy of Commercial (mixed source) SUSE as I would breach copyright in doing so and I would burdon you with illegal software possession. I would have to say no to you, if you needed my help to get software and I don't have the money to buy you another copy. So ethically the disc has become difficult to accept. As  Free Software without the four Freedoms isn't  Free Software at all, the inclusion of proprietary software on a  Free Software disc makes that disc non-Free in real life. You either go  Free Software, or you go proprietary. An aggregate mixture becomes proprietary by default. A statically or dynamically linked mixture becomes non-redistributable all together (yep, I prefer GPL and LGPL). In the case of BSD or MIT, it just defaults to proprietary again.

*Yet something like specialized accounting software or a video game may not be appropriate to make fully open. In the case of a video game, developers would be better off using open source development tools, libraries, and possibly even engines...yet if they release their games completely free of charge and free to redistribute, no one will ever feel a need to pay for it.*

It doesn't matter if the accounting software is open or closed when it comes to highly specialized software. As it is highly specialized, it's users will always need support to keep it functioning, to get training and updates and bugfixes, because only a few can actually develop that program. So in this case it wouldn't matter if it was Open Source, since there aren't any massive numbers of competitors to cannibalize your market.

Your gaming argument has one big flaw. Artwork and storyline are not software. A game is a piece of art powered by software, but the software alone isn't the game, now is it. So your argument doesn't hold any water. You even said that the engine (the software part) could be Open Sourced, but not the artwork, so you unconsciously already separated the art from the software. So Open Source game-engine software is very viable, but gratis artwork and storyline are not.

---

### Post by MadMan2k on 2006-01-09
[QUOTE=macleod199]Have you ever developed any software?[/QUOTE]
nothing which had to be compiled... :p

but I already ran into the "dll hell" which it actually is not - most of the windows software simply brings its dependancies along.
I even have a game which has its own local JRE...

But it has also a huge drawoff, namely that you cant share ressources that way.

and this doesnt change the fact that you can rely on core components in windows, while you cant in linux.

---

### Post by Jengu on 2006-01-09
[QUOTE=Buffalo Soldier]
But guys... especially the ones who joined this forum from the very beginning... late 2004... doesn't this thread ring a bell? When I read the post by [Breepee](http://ubuntuforums.org/member.php?u=14107), [Halvorsen](http://ubuntuforums.org/member.php?u=53607) and [Jengu](http://ubuntuforums.org/member.php?u=25331) ... they remind me of a couple of forum members from a time long long ago.
[/QUOTE]

I don't think the threads you posted are the same other than that they've gotten rather long and flamey ;)

My purpose in my responses here was to get people thinking about autopackage, because I think most people dismiss it out of hand without really understanding what it does. The overwhelming number of responses in this thread making attacks on it that are answered in the autopackage FAQ demonstrates this is the case.

A lot of people are under the **incorrect** impression that if you can't alien something you can't autopackage it. A lot of people **wrongly** think rpms and debs are more secure, because they don't let you execute "arbitrary" code (they do, preinstall and postinstall scripts). A lot of people still think of Linux as a **server** OS, so the idea of packaging software for download from arbitrary sites is unthinkable.

Repositories aren't scaleable. The first otherwise decent distro that comes along that gets packaging right will squash the others.

---

### Post by leech on 2006-01-09
[QUOTE=Jengu]I don't think the threads you posted are the same other than that they've gotten rather long and flamey ;)

My purpose in my responses here was to get people thinking about autopackage, because I think most people dismiss it out of hand without really understanding what it does. The overwhelming number of responses in this thread making attacks on it that are answered in the autopackage FAQ demonstrates this is the case.

A lot of people are under the **incorrect** impression that if you can't alien something you can't autopackage it. A lot of people **wrongly** think rpms and debs are more secure, because they don't let you execute "arbitrary" code (they do, preinstall and postinstall scripts). A lot of people still think of Linux as a **server** OS, so the idea of packaging software for download from arbitrary sites is unthinkable.

Repositories aren't scaleable. The first otherwise decent distro that comes along that gets packaging right will squash the others.[/QUOTE]

There is a definite problem with your argument.  The reason that people (correctly) assume that RPMs and Debs are secure is that they are in a repository of software that is checked and checked again by all that use it.  That's why repositories are good, it is one of their strengths.  A package doesn't just get thrown into a main repository without being looked into.  

Certainly if you install any old .deb or .rpm from some random place on the internet there is the potential for software to be placed in it that is bad, but of course people are generally aware of this risk.

Repositories are scalable, since there are constantly new packages being released into them.  That's part of the community itself, some one sees a program that they'd like packaged and either package it themselves, or request that it's packaged.  Then through several different levels of peer review, that program can be put into a distributions repositories.

The only thing that Autopackage (and it's similar software) are things that cannot for legal or distribution reasons can't be put into repositories (commercial packages such as Pagestream, Maya, Softimage, etc).  There really isn't a need for gaim or firefox or whatever to be distributed with autopackage because they are already in all the distributions.  

Leech

---

### Post by r_a_trip on 2006-01-09
*The first otherwise decent distro that comes along that gets packaging right will squash the others.*

Wrong. This is proprietary, competitive for profit thinking. GNU/Linux can foster commercial efforts, but by and large it is a cooperational endeavor with friendly coopetition.

There will never be one distro to rule them all, because the Freedom embedded in the license makes sure that no project can be killed as long as even one person has an interest in it. There will always be projects that will reject "easy" solutions and there will be projects that embraces them.

Truth is that Autopackage doesn't need the Distributions to propel them into the limelight. Autopackage is Distro independant (so they say) and as such they should be able to achieve a majority stake in package usage through their sheer claimed superiority.

They just need to walk the talk and get outside developers to massively adopt Autopackage as their distribution format. It is not the job of the Distributions to make Autopackages, because distributions already have their own working packaging systems.

---

### Post by poofyhairguy on 2006-01-09
> **ZephyrXero]I know I'm coming in kind of late to the discussion...so if I repeat something already said, forgive me and just let me know  said:**
> 

Problem is that even this is not magic bullet. What happens when the application was compiled with a GCC that is not compatible with the distro?

[QUOTE]
I also am of the opinion that there will need to be one dominant distro (at least for a little while) before we really see much progress in standardization. And just as others have said I would never wish this upon all distros, just the most common desktop distros. Open source development is very much like evolution, so luckily at some point a clear "fittest" distro is going to come out on top while the "less fit" slowly die out...yet there will always be new interesting alternatives created too.
.

Exactly.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=Jengu]The first otherwise decent distro that comes along that gets packaging right will squash the others.[/QUOTE]

I have read this many times and each time it amazes me.

If thats all it takes- for some distro to "get it right"- then why does no distro do that? 

Every week a new distro comes out, yet none "get it right" it seems.

Heck, Mark with his millions can "get it right."

If this was even remotely possible, why doesn't someone just do it already? Why are we waiting?

Oh yeah. Because distros already "get" packaging. They just don't get it in a way that every user finds acceptable.

I mean....its really simple guys. Linux is not an OS. Ubuntu is an OS. Until that new Firefox or Openoffice or whatever is sitting in the repos than its not released for your OS. I don't care if a tar file exists- until its sitting in some sort of deb in some repo it has not been released for your OS.

Does it kinda suck that Windows users and OSX users and Gentoo users get Firefox or whatever the first day of the week while we (at most) have to wait six months? Sure it does. But that is how Ubuntu is.

If you need that Firefox/Abiword/whateverapp the first day than either use a distro or OS that gives you that (Windows, OSX, Gentoo, etc) or find some other way to get it. Other ways include:

1. Use Autopackage if you can find one for that app. Most big apps have Autopackages now. I fit works, problem solved.

2. YOU be the one to "release" that app for Ubuntu. Thats means compiling it yourself- hopefully with checkinstall. Sure new users can't do this, but new users can't make exe's either.

3. Alien some other distro's RPM package of it. If I try enough RPMs of the same program, eventually one works ALL the time.

4. Ask for a backport. If it is possible you will get one.

5. Use a community repository or tool to get it (Automatix). 

There is your solutions. Sure its not as easy as "go to a site, download exe and click next a billion times" (unless there is an Autopackage for your application) but thats the sacrifice you pay for using Linux. 

Some might say "well if you can't give a solution better than the five mentioned above, forget competing with Windows."

Fine. Its forgotten. I have ranted on this forum more than once that Ubuntu and Windows don't compete anyway.

It seems people are looking for a magical perfect OS. "The freeness of Linux, combined with the expandability (aka ease of installing programs) of Windows, combined with the community of OSX."

Well.....no perfect solution exists in the OS world. Sorry. Thats life- everything has flaws. 

If you keep waiting around for this "perfect distro" to emerge then you will spend your entire life waiting. There is no "one size fits all" distro and there can never be- thats why we have like 200 of them.

If you need a good, stable Linux with fairly new applications and reliable releases every six months than Ubuntu is for you. If you need new applications the day they come out over all else, then Gentoo or VLOS is for you (based on Gentoo). VLOS is free and not that bad. Sure you still have to compile apps but portage makes it simple and thats as good as we will ever get in the Linux world. 

Pick the shoe that fits you best. 

I picked Ubuntu because I hated having to find RPMs all over the web (and their dependencies) in order to get my box set up like I want. I picked Ubuntu because of its large Universe and Community. I personally like new apps too, but I only need the big ones soon after then come out (say Firefox and OpenOffice) and the community has a way to provide those for me (Automatix) so I am happy.

If you are not happy then please become happy. Life is to short to waste time trying to turn Ubuntu or whatever distro into a perfect OS. Its just not going to happen.

Push comes to shove- there is always Windows. Its not that bad with some free Anti-virus and Anti-spyware programs. Just like Ubuntu you have to sacrifice a few things to use it though. Thats life.

I mean...Mark is a smart boy. He MUST know that many users would not like his "no new software till six months are up" plan. But he just figured those users needs are better met elsewhere.

And he was right.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=MadMan2k]
and this doesnt change the fact that you can rely on core components in windows, while you cant in Ubuntu.[/QUOTE]

(by the way I changed "Linux" to "Ubuntu" in that quote of yours so that I don't have to nit pick over that)

And the reason is obvious. The Windows platform updates like every two or so years.  The Ubuntu platform updates every six months.

I happily trade new whole releases every six months for the ability to easily install new versions of software soon after they are "released."

But if thats not cool than use the distro that does NOT change its platform so often- Debian. 

Debian's backport site has most of the new best software (even some stuff our backports do not have) and its free as well. Its there- new Firefox and everything.

[http://backports.org/](http://backports.org/)

Use what works best for you.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=Buffalo Soldier]
I guess every once in a while... this kinda members and threads will exist in here :p[/QUOTE]

Its all in good fun.

---

### Post by leech on 2006-01-09
One thing to add to that, Poofyhairguy, is that if someone wants their "Perfect OS" why don't they make it themselves?

There is always the Linux from scratch, or you could even do what Ubuntu did and build off of Debian, or whatever.  Yes there are many distributions out there, and that's for a reason, because everyone has different needs.  If you want you could probably even just use Debian as a core and then autopackage all the rest of your stuff as some other people have suggested Ubuntu should do.

Ubuntu strives for a good desktop out of the box and provides support for that desktop system as a whole, which is exactly why Autopackage whill never become supported on it.  Autopackage is a support nightmare, as is Windows.  Anyone who has ever had to try to trouble shoot windows over the phone knows how much a pain in the butt it can be.  Supporting Linux is far easier, if you know what distribution it is, then you'll know automatically what software is out there for it.  

Leech

---

### Post by scaine on 2006-01-09
Remember what this thread was about?  It's about the question of whether or not the Autopackage support libraries can be included with Ubuntu.

What's was the verdict on that again?  Oh yeah, everyone was too busy shooting a good idea down in flames to decide.  I suppose that's a no then.

Shame.  A simple solution to make (some) installations easier for users.  End of story.  Instead we debate for 3 weeks on whether Autopackage should exist, how it should develop, whether it should be embraced, the cliffs it has to scale, the security implications, why it's impossible, why it'll never be embraced, why Linux-noobs just "don't get Linux", why it isn't in the spirit of FOSS, the support ramifications... I suppose you get the idea.

But hardly a single post said, "Yeah - why not?".

Exactly, what harm can it do to include this?  And that's a rhetorical question.  Please don't answer it... again.  (Check Lean's post on the first page of this excruitiating thread).

Buffalo Soldiers post sums it up for me :
> I guess every once in a while... this kinda members and threads will exist in here 
... yeah - but then they become so disheartened by some of the attitudes to anything that might make Ubuntu slightly more like Windows.

There's plenty of things not-to-like about Windows.  But easy installations isn't one of them.

Yours, spirit broken,
Scaine.

---

### Post by leech on 2006-01-09
It's been shot down for many reasons.  I think one of the problems with this thread is the topic's name.  "Autopackage: Toward a universal package manager for the desktop" But it's not a package manager.  Or at least one that is friendly with any of the other package managers.  I think if they could make it co-exist with the package manager that is already in the distributions, I'd accept it with open arms.

For it to be a universal package manager, it'd have to first be used by every distribution out there.  Right now we basically have RPM, DEB, tar.gz and the newest, ebuild.  There are of course others like conary, but it's only used by two distributions at the moment, and it is a good idea.

I would even say Autopackage would be a good idea to support in Ubuntu if it were only for packages that could not duplicate what is in the repositories, especially commercial packages.  I've always said that.  I think it's just a bad idea for it to conflict or copy over things that are in the repositories (such as firefox).

Leech

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=scaine]Well - that's one hell of a post, Poofyhair.  I reckon that post (#291) should be given a medal!  It's a beaut.[/QUOTE]

Thanks for the award. And thanks for your replys- otherwise no more ranting from me. As you can tell I really like this subject.

Thats because recently I "got" it. I was once in the same boat as everyone else. I wanted it all- the packages in the repos and a release every six months and new applications when they come out. When I was new I too thought "man, Linux needs an EXE!" I too have wanted the same thing everyone else here wants, I have made the same demands.

Then one day I got it. Hit me like a ton of bricks. It all came together for me.

I knew suddenly why I (and everyone else here) could not get what I want- my expectations were too high. I didn't want Ubuntu for what it was. I wanted a better Windows than Windows that did not lose the ease of install that Windows had.

And I can have that. But its not Ubuntu (in the Linux world its Gentoo or linux from scratch). Ubuntu is what it is, its made for a certain type of people.

Who? Easy. Every person I have ever met and installed Firefox for on Windows that has not updated it since I was there (even though it is easy to do on Windows). Every person that uses really old versions of applications and doesn't care. So bascially normal people.

The biggest shame about Linux Desktop adoption is those that have the ability to switch are the ones that are helped by it the least.

Of those that can get through the installer- the hardcore gamers, the Windows power users, and Unixy types- many are not benefitted greatly by Ubuntu and Desktop Linux.

Gamers lose their games. Windows Power Users often don't have seucrity problems (a HUGE advantage of Ubuntu) and don't get to have applications the day they are released (which sucks because only Windows Power Users care to have applications the day they are released).

Those who would be really helped by Ubuntu- those who just want to do some web browsing, play some puzzle games, or do some basic chat and Office (doc) work- usually don't have the knowledge to get through partitioning and finding Automatix and all that crap (well...unless they are willing to nuke the XP install they have and never go back).

The biggest success I have had with spreading Ubuntu is not to fellow geeks, but to normal users. I set it all up for them and many times its been a success. THAT is Ubuntu's target market.....yet that market will only come really when machine are shipped with Ubuntu preinstalled. Sigh.

> 
Well - I'll stop you there.  I agree with you, but my Mum doesn't.  I'd like to give her Ubuntu, then for example, talk her (over the phone, since she'd 80 miles away) through downloading and installing Skype.  Ain't gonna happen on Ubuntu, sadly.

A. Its a *nix! YOU set it up for you mom over SSH! No need to walk her over the phone.

B. I bet she could get Automatix to work.

> 
It's a problem, again I agree.  But unreasonable expectations got us Linux in the first place.  You could even argue it got Mark into space.  Let's not build up the problem cos it's diffuclt.  A great Dan Brown quote is "Everything is possible - the impossible just takes longer".

Expectations are fine if people are willing to sacrifice and work to overcome them. They are not fine when you expect someone else to sacrifice and overcome them for you.

> 
A couple of quick points here.  First off, I don't think they *all* have to go along with it, just most.  Then the rest are more likely to follow.  Maybe.  Also, let's not go down the binary compatibility route as a given either, which you explain in great detail would hurt various distros plans for Linux.  All I'm hoping for is a unified experience for installing non-repo software.  Maybe it'll compile silently in the background, maybe it'll run a .bin file, maybe it's detected that the binary in it's package is compatible with my Ubuntu system.  Whatever, but hide it and make the front end understandable.

Second - the Gnome 10x10 project would appear to have a bearing on the "Desktop Linux platform" idea.  Personally, the way Gnome's going, I think it's losing ground to KDE, but I'm ignorant of take up in the corporate (which is where it matters most), so maybe I'm wrong.  But if Gnome 10x10 takes off, perhaps there's hope that an underlying unification of installation can happen too.  Who knows?

Thats the one place where me and Mr. Hearn differ in opinion. I think that a unified Linux Desktop Platform (aka one where the distros work together) is a pipe dream. I think the fact that some huge players like Mark and Red Hat openly reject it mean that such a plan is doomed (just like Mark ignoring the DCCA pretty much killed it).

The only distro I have seen support the idea is Mandriva and in the last year or so that distro has become was less relevent.

The only chance I see is if some company with more money than God comes into the scene and makes a distro that has so many resources poured into it (aka it is so much better than the rest) that all the others have to adapt to survive. 

Gnuland is a meritocracy, for better or for worse.

> 
Me too.  Because I think that ease-of-installation is at the core of Linux (and I do mean Linux this time) take up in the home.  I work in a systems department of 60 staff.  Of those, I run Ubuntu.  That's it.

Every single person (around 15) that I've given a live CD to, claimed that it was too difficult to get stuff to work that they'd downloaded from the Net.  Some of this stuff was obviously just negativity on their part, some was ignorance of the repos.  But most of us like our BitTorrent at work and getting Java to work was a shocker for most of them.  Or their Nvidia acceleration.  Or Skype.  Or something else they just "expect" to work (back to Poofyhair's "expectation" line again).

Its not bad to expect such things. Its bad to expect such things to be delievered in the exact way Windows does (aka go to site and download and next, next, next).

There is obviously a need for such things to be installed. And a need for that process to be made easy. Thats why Automatix was made. For everything you just mentioned Automatix does it. We have a solution ready and waiting. People just have to break old habbits (I MUST be able to download software from the internet and install it with double clicking) and embrace it.

> 
That old biblical quote comes to mind : "Have the courage to change what you can, and the wisdom to know what you cannot".  However, in this case, there are a few guys who either have more courage, or less wisdom that you and me.  They're working on Autopackage.  Good luck to them.

Yeah....good luck to Autopackage. It has a role. I see that. It has a role. We need some sort of third party installer (if only for closed applications and such) and Mr. Hearn is making it.

More power to him. Lets just not break his back with the same thing that has killed many a dream of Ubuntu- too high of expectations.

---

### Post by aysiu on 2006-01-09
[QUOTE=poofyhairguy]
The biggest shame about Linux Desktop adoption is those that have the ability to switch are the ones that are helped by it the least.[/QUOTE] Don't forget that the ones who'd be best helped by Linux desktop adoption A) have not even *heard* of Linux B) are scared of change and C) don't like their computer nerd friends installing stuff on their computers for fear of "breaking" things.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=scaine]Remember what this thread was about?  It's about the question of whether or not the Autopackage support libraries can be included with Ubuntu.

What's was the verdict on that again?  Oh yeah, everyone was too busy shooting a good idea down in flames to decide.  I suppose that's a no then.[/QUOTE]

No. The verdict is that:

1. If something like Autopackage needs distro support than it is a failure for what it is trying to do. And its not a failure (I use it in Ubuntu easily) so it does not need distro support to work well.

2. Ubuntu MIGHT play nicer with it by default if it worked with apt-get. Mr. Hearn says one day it will work with apt-get. This is an example of something not being ready yet. Its day will come...

> 
Shame.  A simple solution to make (some) installations easier for users.  End of story.  Instead we debate for 3 weeks on whether Autopackage should exist, how it should develop, whether it should be embraced, the cliffs it has to scale, the security implications, why it's impossible, why it'll never be embraced, why Linux-noobs just "don't get Linux", why it isn't in the spirit of FOSS, the support ramifications... I suppose you get the idea.

I do- its been a fun ride. Heck, I was going on about Autopackage in the forums LONG before this thread started.

> 
But hardly a single post said, "Yeah - why not?".

Which is a good thing. Package management in Ubuntu is not a simple problem with simple answers. Sorry if that depresses you or whatever.

> 
... yeah - but then they become so disheartened by some of the attitudes to anything that might make Ubuntu slightly more like Windows.

There's plenty of things not-to-like about Windows.  But easy installations isn't one of them.

I PROMISE that the resistance is not all about "we do not want to have easy to install packages like Windows." Its more like "Desktop Linux has many challenges and attributes that make it so that the Windows model does not fit it well, despite many people wishing that was not the truth."

> 
Yours, spirit broken,
Scaine.

If it makes you feel any better repeat to yourself "no one in this thread is a developer, so their opinions concerning the direction of Ubuntu does not matter."

I say that to myself a lot on the forums.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=aysiu]Don't forget that the ones who'd be best helped by Linux desktop adoption A) have not even *heard* of Linux B) are scared of change and C) don't like their computer nerd friends installing stuff on their computers for fear of "breaking" things.[/QUOTE]

Amen aysiu. I could give examples of each one of those things in my own life if I wanted to.

Thats why, yet again, until Ubuntu is sold on PCs the same issues will keep popping up.

On a side note I'm glad to see you are reading this aysiu. As I have been typing some of this stuff I thought "man, this is aysiu's favorite Linux subjects!"

---

### Post by scaine on 2006-01-09
[QUOTE=poofyhairguy]No. The verdict is that:

1. If something like Autopackage needs distro support than it is a failure for what it is trying to do. And its not a failure (I use it in Ubuntu easily) so it does not need distro support to work well.[/QUOTE]

It doesn't need support, PoofyHair - it just makes it *simpler*, in fact no - just a better experience for the user, if the support libraries are pre-installed.  Unlike many contributors to this thread, you've actually used AutoPackage.  You know what I mean.  The first time you run a .package file, you're run through a tiny little install script - which you have to run from a terminal.

Wouldn't be easier, slicker, and more user-friendly if those libraries were already in place?  Then you'd just download the .package file and double click on it.

[QUOTE=poofyhairguy]
2. Ubuntu MIGHT play nicer with it by default if it worked with apt-get. Mr. Hearn says one day it will work with apt-get. This is an example of something not being ready yet. Its day will come...[/QUOTE]

Yep.  Or an autopackage competitor.  I don't have a preference one way or another - I'm just looking for a solution to a problem.

[QUOTE=poofyhairguy]I PROMISE that the resistance is not all about "we do not want to have easy to install packages like Windows." Its more like "Desktop Linux has many challenges and attributes that make it so that the Windows model does not fit it well, despite many people wishing that was not the truth."[/QUOTE]

But that shouldn't be a reason for resistance.  Let the autopackage guys worry about how hard it is.  We should simply support them, by installing those support libraries if possible.  Job done.  That's all.

[QUOTE=poofyhairguy]If it makes you feel any better repeat to yourself "no one in this thread is a developer, so their opinions concerning the direction of Ubuntu does not matter."

I say that to myself a lot on the forums.[/QUOTE]

:) I've been saying that a lot recently.  I reckon more than a few people have been saying that about me.

---

### Post by aysiu on 2006-01-09
[QUOTE=poofyhairguy]
On a side note I'm glad to see you are reading this aysiu. As I have been typing some of this stuff I thought "man, this is aysiu's favorite Linux subjects!"[/QUOTE] You betcha. I read everything except the mailing lists, pretty much. Even if autopackage or something like it is a worthy goal in some sense, novices (those best served by Linux desktop adoption) will still never install Linux themselves.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=scaine]It doesn't need support, PoofyHair - it just makes it *simpler*, in fact no - just a better experience for the user, if the support libraries are pre-installed.  Unlike many contributors to this thread, you've actually used AutoPackage.  You know what I mean.  The first time you run a .package file, you're run through a tiny little install script - which you have to run from a terminal.[/QUOTE]

I of course get your point. It WOULD be easier if the libraries come by default.

And I think that after it works with apt-get and major closed applications like Crossover or Cedega use it then the libraries should be included with Ubuntu. I will help pitch a fit to get that done when its time.

But honesly until it sees the Ubuntu package manager the developers are not going to consider it....so lets save our one good shot (hissy fit) for when the opportunity is best.

> 
Yep.  Or an autopackage competitor.  I don't have a preference one way or another - I'm just looking for a solution to a problem.

I know you are. And thats a noble goal. But in order to find a solution to the problem you first have to discover what the real problem is (not the superficial "I can't install the new Firefox" kind of problem, but the root cause). Thats what this thread has been about.

> 
But that shouldn't be a reason for resistance.  Let the autopackage guys worry about how hard it is.  We should simply support them, by installing those support libraries if possible.  Job done.  That's all.

Hmm...that would be nice but in Gnuland things don't work that way. When you prove yourself worthy as an application or platform is when you get put into major distros, not the other way around (aka putting programs in major distros to prove that they are worthy).

Plus personally its not enough to say "that's all" because the problem is just not that we lack the Autopackage libraries. There is a root problem that even Autopackage won't solve

What people really want is an easy way to install stuff not from the repos. Many see Autopackage as a magic bullet for that but its not- there are far less Autopackages than Debian packages and so if you can't find what you want you are still screwed.

No....we can't get leave it alone. Because then when Autopackage fails these people like apt-get did before they will just want to hop to the next ship without ever realizing that the problem might be themselves and their expectations.

THAT is worth discussing!

> 
:) I've been saying that a lot recently.  I reckon more than a few people have been saying that about me.

If it makes you feel any better, Mark hired the guy who is working on the Smart Package manager. So Mark sees the problem, and he has his own solution.

So its not all grim.

---

### Post by scaine on 2006-01-09
Nope, not all grim I suppose at all.  Smart looks good.  I like this :

> I have a package on my disk. Can I use Smart to install it?

Yes. Use:

# smart install foo-1.1-1.i386.rpm

Smart will even download dependencies from remote channels if necessary, which is nifty.

The filename must end with a well-known package extension for this to work. 

But sadly, Smart is similar to Gdebi from what I gather on the FAQ page.  It doesn't allow RPMs to install on a Debian based system, which means that we'll still need .deb files for whatever we want to install.

I'll keep my eye on Autopackage and cross my fingers I think.  Let's face it, Ubuntu support for Autopackage doesn't matter to me anymore anyway - I've already used it once.  I'd just like to see more AutoPackages out there now.  Particularly for the commercial games I play such as Quake 4 and so on.

Time will tell.  (How often have I said that in this thread...)

---

### Post by leech on 2006-01-09
That's what I've been saying the whole time, Autopackage would be good for Commercial stuff, but not for things like firefox, unless of course the whole distro is based on Autopackage... which would be interesting, even if that's not the intention of the project.

Leech

---

### Post by Spark* on 2006-01-09
[QUOTE=leech]unless of course the whole distro is based on Autopackage... which would be interesting, even if that's not the intention of the project.[/QUOTE]
Or more realistically, a distribution that uses another package management only for system libraries and autopackage for all optional applications (those which cannot hose your system when they break).

I think Firefox is a bad example, since it double-serves as a library to some other applications, which doesn't really make it suitable for autopackage yet. If Gecko and frontends would already be properly separated, then no harm could be done from installing Firefox (but not Gecko) via autopackage. Especially if the installer would be modified to default to /usr/local.

---

### Post by mhearn on 2006-01-10
Wow. Hard to believe this thread is still ongoing. Anyway, I did a blog post lately about autopackage/apt-get and security:

   [http://plan99.net/~mike/blog/?p=10](http://plan99.net/~mike/blog/?p=10)

Hopefully that should present the reasoning behind some of the things we've said w.r.t security. There are other blog posts about different ways to deal with spyware there. We are not approaching this blindly.

---

### Post by MadMan2k on 2006-01-10
[QUOTE=mhearn]Wow. Hard to believe this thread is still ongoing. Anyway, I did a blog post lately about autopackage/apt-get and security:

   [http://plan99.net/~mike/blog/?p=10](http://plan99.net/~mike/blog/?p=10)[/QUOTE]
you have not considered the possibilities OSS offers not well enough.

1) adverts in OSS application cant only be removed, but made optional. For example by a *advertised* repository where you got the unmodified applications.

2) you wouldnt trust a centralised repository run by microsft not because its microsoft, but because its not OSS and you therefore cant see what they are doing

but I generally agree with you that the software distribution has be to be less centralized. my solution would be third-party repositories, like they are already possible today and representing applications with metapackes wich would only contain the necessary repository information for the appropriate distribution.

The reason you cant do that today, is that mass of different packaging formats you have today which are generally doing all the same.
But if Ubuntu keeps growing at that speed, deb could become the dominant format, so that it would be enough to set up a deb repository with different branches to statisfy most of the people.

---

### Post by aysiu on 2006-01-10
[QUOTE=MadMan2k]
But if Ubuntu keeps growing at that speed, deb could become the dominant format, so that it would be enough to set up a deb repository with different branches to statisfy most of the people.[/QUOTE] Unfortunately, even now, people advise Ubuntu users to add Debian repositories only temporarily so as not to bork their Ubuntu installations.

Regular Debian repositories, as far as I know, can already be used and shared among Xandros, Mepis, Debian proper, and Libranet.

---

### Post by MadMan2k on 2006-01-10
[QUOTE=aysiu]Unfortunately, even now, people advise Ubuntu users to add Debian repositories only temporarily so as not to bork their Ubuntu installations.

Regular Debian repositories, as far as I know, can already be used and shared among Xandros, Mepis, Debian proper, and Libranet.[/QUOTE]
thats why I added different branches ;)

it could look something like this in the end:
[http://people.debian.org/~dexter/dists/php5.1/](http://people.debian.org/~dexter/dists/php5.1/)

/edit:
I want to have my coffee cups back too :(

---

### Post by ZephyrXero on 2006-01-12
I think the number one issue that makes Autopackage (and any other 3rd party/decentralized/whatever you want to call it packages/installers) a better system than the repository system is that the math does not add up. As a distro's repository grows larger and larger it will be harder and harder for the community to maintain. As while the number of new packages released grows expotentially every day, the number of maintainers grows at a much smaller rate.

For a good example, just look at Gentoo. Anyone who's been watching/using it for the last couple years can see it's falling apart because there's so many directions it's trying to go at once. I've heard some people claim that Gentoo's the distro to go with if you want bleeding edge software, but frickin' Gnome is still only at version 2.10.2 (stable). I remember back when NVU was at around version 0.6 it took months for them to add it to the repositories, and then many months before they updated it either. This kind of thing happens all the time, and if you start mixing in masked apps/libs (unstable) things can start going nuts if your not extremely careful.

If Ubuntu had as many different programs available for it as Windows (I don't say just XP either b/c it's fairly backwards compatable most of the time), there's no way anyone could keep it all even remotely up to date.

The idea of a 3rd party repository is nice, but not really feasable as different distros will always use different package managers. [I had an idea](http://autopackage.org/forums/viewtopic.php?t=176) a couple months ago about a gnome-files.org/download.com site for autopackages that might work...but when it comes down to it, all these other issues that keep getting brought up are not nearly as powerful as the main one I've just said. Forget who a specific distro is aimed at and all of that...it just doesn't make sense to continue using centralized repositories as they will eventually grow to an unmanagable size no matter how popular you distro is.

However, another seperate point I'd like to talk about is the fact that distro developers/maintainers don't really matter towards the success of Autopackage. Really the application developers that release their software in this format and the people who use it will be the deciding factor, so it really doesn't matter if the Ubuntu devs read this thread or not ;)

---

### Post by doclivingston on 2006-01-12
[QUOTE=ZephyrXero]The idea of a 3rd party repository is nice, but not really feasable as different distros will always use different package managers. [I had an idea](http://autopackage.org/forums/viewtopic.php?t=176) a couple months ago about a gnome-files.org/download.com site for autopackages that might work...but when it comes down to it, all these other issues that keep getting brought up are not nearly as powerful as the main one I've just said. Forget who a specific distro is aimed at and all of that...it just doesn't make sense to continue using centralized repositories as they will eventually grow to an unmanagable size no matter how popular you distro is.[/QUOTE]

If the distro-repositories won't scale, couldn't the same argument be applied to say that large third-party repositories won't scale either? The only way I can think of them scaling better (as in order-of-magnitude better, not just a multiple) if if the number of repositories grows large - at which point it isn't much better than downloading of random websites.


If you expect that developers will make packages for their own software, then either they will have to learn (which a lot may not want to take the time to do), or they'll make crappy packages. If you expect that there will be a group of people that go around packaging everything, then this isn't really different to the MOTUs.

---

### Post by r_a_trip on 2006-01-12
Actually, we shouldn't keep people from potentially shooting themselves in the foot. If there is a demand for Autopackage, support infrastructure should be included in Universe. (Although Autopackage is selfcontained). Just add the statement that it is at your own risk and using it voids any support contract that you have with canonical.

If Autopackage is really the kickass installer format it is claimed to be, nothing will go wrong. If it does bork up an install, because of some obscure unforeseen reason, you had the disclaimer in place.

Kids learn to pick up their feet by falling down and hurting their knees. New users learn how to compute by screwing up their computers. If they can install Ubuntu for themselves, they can learn how to fix problems as well.

---

### Post by Jengu on 2006-01-12
[QUOTE=doclivingston]If the distro-repositories won't scale, couldn't the same argument be applied to say that large third-party repositories won't scale either? The only way I can think of them scaling better (as in order-of-magnitude better, not just a multiple) if if the number of repositories grows large - at which point it isn't much better than downloading of random websites.[/quote]

Autopackage isn't advocating third-party repositories.


> 
If you expect that developers will make packages for their own software, then either they will have to learn (which a lot may not want to take the time to do), or they'll make crappy packages. If you expect that there will be a group of people that go around packaging everything, then this isn't really different to the MOTUs.


I think developers would like the idea of making 1 autopackage instead of three different kinds of rpms, a deb, a tar.gz...

---

### Post by leech on 2006-01-12
[QUOTE=r_a_trip]Actually, we shouldn't keep people from potentially shooting themselves in the foot. If there is a demand for Autopackage, support infrastructure should be included in Universe. (Although Autopackage is selfcontained). Just add the statement that it is at your own risk and using it voids any support contract that you have with canonical.

If Autopackage is really the kickass installer format it is claimed to be, nothing will go wrong. If it does bork up an install, because of some obscure unforeseen reason, you had the disclaimer in place.

Kids learn to pick up their feet by falling down and hurting their knees. New users learn how to compute by screwing up their computers. If they can install Ubuntu for themselves, they can learn how to fix problems as well.[/QUOTE]

That doesn't quite apply to computer users, because most of them don't know why their Outlook isn't working and have to call the tech guy, who just tells them to click that little thing in the lower right hand corner that says they're working offline.  Then two weeks later the same person has the same problem and has to call the tech guy again.  

You have to realize that most people want to just use their computer for the task that was given them and don't want to (or can't) learn how it actually works.

Autopackage would only be good for those that already know what they're doing, plain and simple.  That's why a distribution of software won't try to work with autopackage, after all, if you had spent so many years perfecting your package manager, would you want some other program coming along and decimating your perfected system?  

Leech

---

### Post by zootreeves on 2006-01-12
I mentioned this in another thread. But if your talking about web based repositories  have you looked at apt-plus. I think it would be much easier if the ubuntu repos just had the core programs (main) and the universe should be replaced with a web based repository, like apt-plus.com.

btw take a look at Symphony OS, looks like it has great potential.

---

### Post by leech on 2006-01-12
I had never heard of apt-plus!  This is exactly what I was looking for!  Very cool.  We could just use this, or make a different one for Ubuntu.  SymphonyOS is a very cool idea, I remember seeing stuff on it a long time ago, when it was just a mockup.  This is very cool.  I'm looking into it now.

Leech

Edit:  I was going to download apt-plus, but unfortunately the link on the apt-plus.com website is not working, and there aren't any other versions of apt-plus on the site that it gives.  But this is pretty much exactly what I was talking about.

---

### Post by r_a_trip on 2006-01-13
*You have to realize that most people want to just use their computer for the task that was given them and don't want to (or can't) learn how it actually works.*

If this is true, then no normal person is using Ubuntu right now. If this truly is the case, we either have to restrict Ubuntu to the point of being equiped with only three buttons or admit to ourselves that GNU/Linux is still above and beyond any ordinary user, in which case it doesn't matter if it is in Universe or not because a normal person wouldn't know how to activate Universe anyways.

*Autopackage would only be good for those that already know what they're doing, plain and simple.*

Which would be almost all the people using Ubuntu right now, they managed to do the non-trivial (initial) install themselves (that or Mark S. has a secret army running around which stealthilly installs Ubuntu on every noobsystem, negating the requirement to know how to install it).

If you can install Ubuntu from disc, you can understand the risks of a third party package too. If all the previous stuff is chinese to non-chinese speaking people, they won't know how to install software anyways, so what is the harm of including support for a packagemanager they can't use and thus is unable to wreak havoc on their systems?

Innitially I was against inclusion, but I've thought it over. To resist this is infantile. Since when does the exclusion of an option help anybody? Those that don't know what Autopackage is won't use it, those that do will probably use it anyways. 

When it is universe, at least the basic infrastructure can be made to fit Ubuntu, if necessary. On the other hand... Mike Hearn had the foresight to make AP selfcontained and able to get its own support files from the net, so AP is only inconvenienced in a minor way by not having Universe support.

---

### Post by aysiu on 2006-01-13
[QUOTE=r_a_trip]*You have to realize that most people want to just use their computer for the task that was given them and don't want to (or can't) learn how it actually works.*

If this is true, then no normal person is using Ubuntu right now. If this truly is the case, we either have to restrict Ubuntu to the point of being equiped with only three buttons or admit to ourselves that GNU/Linux is still above and beyond any ordinary user, in which case it doesn't matter if it is in Universe or not because a normal person wouldn't know how to activate Universe anyways.[/QUOTE] Not necessarily. It means most people don't use Ubuntu, and the people who fit into the "most people" category who *do* use Ubuntu had Ubuntu installed and configured *for* them by someone else.

---

### Post by leech on 2006-01-13
Thank you Ayisu for saying exactly what I was going to.

If a corporation (in which case it would be the IT guys who do the installing) have Ubuntu on their computers, the users that use only the applications would only worry about using the applications.  That was my point.  

Don't forget also that there are some companies that are starting to have Linux pre-installed on their systems.  Someone mentioned HP was somewhere.  

Besides, r_a_trip, have you ever actually installed a fresh, non-slipstreamed version of Windows XP?  With perhaps the one exception of the partitioning part, Ubuntu is far easier to set up and to have an actual worthwhile system.  You can install Ubuntu and they can load up OpenOffice and get right to work.  Maybe they would need a little bit of retraining to the differences between Word/Excel/Powerpoint, etc and how OO.o does things, but that's it.  They really wouldn't need to know how or even what a package manager is.

This is of course in the corporate world, where computers are just tools to get the job done.  Usually home users of Linux either know what they are doing, or know someone who knows what they are doing.  At least this is the state of things right now.

If Ubuntu (or Linux distributions in general) take off in the corporate world, I can gaurantee that they will take off in the home world even more so.  

That's how the IBM PC Compatibles took off in the first place.  The Amiga, Atari ST and Macs were all far beyond any of the capabilities of the IBM compatibles during the mid-late 80s, and yet they all failed because all the business users used the IBMs, and people needed/wanted to be able to do some of their work at home.

Leech

---

### Post by aysiu on 2006-01-13
[QUOTE=leech]
Besides, r_a_trip, have you ever actually installed a fresh, non-slipstreamed version of Windows XP?  With perhaps the one exception of the partitioning part, Ubuntu is far easier to set up and to have an actual worthwhile system.[/quote] This has been my experience as well, especially when you need to track down drivers--makes you wish you could just copy and paste a few commands or add a line or two to your /etc/X11/xorg.conf to fix things.  

> You can install Ubuntu and they can load up OpenOffice and get right to work.  Maybe they would need a little bit of retraining to the differences between Word/Excel/Powerpoint, etc and how OO.o does things, but that's it.  They really wouldn't need to know how or even what a package manager is. It depends, of course, on the corporate needs, but I know in my office everyone uses Thunderbird, Firefox, Word, and Excel... and that's it. And they don't use complicated Macros and such in Word--they just type things, bold them, do bullet points, and such.

In fact, sometimes the transition from Microsoft Office to OpenOffice is easier than the transition from one version of Microsoft Office to another. I got totally thrown off when we upgraded our Office at work!

---

### Post by leech on 2006-01-13
Exactly!  Sounds like your office could change over to Ubuntu and not even notice all that much.

The place where I used to work couldn't quite switch yet, due to Evolution being buggy (they used Outlook for calendaring, and an Exchange server for doing meetings, etc.  I tried talking them into dumping Exchange... but was laid off before anything could happen.) and a few apps that wouldn't quite work in Wine at the time.  

Leech

---

### Post by aysiu on 2006-01-13
[QUOTE=leech]Exactly!  Sounds like your office could change over to Ubuntu and not even notice all that much.[/QUOTE] They'd notice, but I think the change would be about the same as the one they made from Windows 2000 to Windows XP.

---

### Post by ZephyrXero on 2006-01-20
This is why I think Vista's going to be the perfect time for people to start trying Ubuntu (and other Linux distros). All these companies are going to say, well, Windows XP has now been obsoleted, so do we install this new version or try something different... That and hopefully Dapper will add that extra polish to really get things running smoothly.

---

### Post by rykel on 2006-03-27
hi pals,

i know i am late for this thread, but hey, my nifty little toshiba is under servicing, so rite now i am writing from somebody else's notebook... i am sure my point below would have been mentioned by someone earlier in this thread...


anywae, here's something i have said b4 about autopackage, and tat is, let apt-get/synaptic and autopackage co-exist!

let the core system files be upgradable and installed silently by synaptic while let  the other group of ubuntu developers create a website like Download.com where there are tons of autopackages for users to go download, instead of making debs.

tis way, u satisfy both the apt-get users, and the autopackage lovers.

tis way, u contribute to even more widespread adoption of linux.

tis way, our wonderful ubuntu devs can help to troubleshoot and hack autopackage.

and of course, one day autopackage will play with apt-get too... may tat day come soon!   :KS

---

### Post by burzum on 2006-07-05
One of the problems why linux cant touch the massmarket is in my opinion that theres no standard for binary and source packages. For example, there different rpm packages for Suse, Redhat and other. Even ubuntus packages are not 100%  the same as debians and i think you cant use easy them with other distributions.

My suggestion is to create a containerformat that can include one of both or both, binary and source of a package. It should also include information about the package and the content. It would be nice to use XML for this purpose. I think this solution would be ok for every buildsystem. A sub-optimal solution would be to include a lot of different installinstructions for different distributions in the package. This would also solve the mainproblem that you have to use different packages for different distributions.

Dependencys suck, in my opinion. Why doesnt everyone compile their programms static (dont know if this is the right term) that they include the necessary code instead of accessing everytime another bunch of libraries or different versions of a library? This is also a problem because it causes dependencyproblems and this problems make different packages for different distributions necessary.

I hope somebody with more technical knowledge will understand what i try to say and can tell me if this is a good idea or not and can provide more ideas or suggestions.

---

### Post by CoolGoose on 2006-07-05
Static compiling sucks .. i don't want to have 10 gb of space ocupied when i can have 2 :).

---

### Post by burzum on 2006-07-05
I dont think so. Space is cheap today and its not THAT much more.

---

### Post by nlogax on 2006-07-05
[QUOTE=burzum]My suggestion is to create a containerformat that can include one of both or both, binary and source of a package. It should also include information about the package and the content. It would be nice to use XML for this purpose. I think this solution would be ok for every buildsystem.[/quote]

Interesting suggestion.  There are also many alternatives proposed, such as autopackage and other package management systems like Conary (RPath Linux) and even meta package managers, which is similar to what you seem to be proposing.

> Dependencys suck, in my opinion. Why doesnt everyone compile their programms static (dont know if this is the right term) that they include the necessary code instead of accessing everytime another bunch of libraries or different versions of a library? This is also a problem because it causes dependencyproblems and this problems make different packages for different distributions necessary.

Statically-compiled binaries don't only consume more disk, they also consume more RAM when running.  If every package running on your system used its own copy of the libraries your memory usage would increase enormously and performance would suffer.  In practise, with a decent package manager like APT, dynamically-compiled programs don't create 'dependency problems' as they are compiled against a specific version of a library.

---

### Post by samir85 on 2006-07-05
concerning static/dynamic compiled programs:

does windows use static compiled programs ? (because there're no dependencies ...)

---

### Post by apoclypse on 2006-07-05
I don't think so they just include all neccessary dll in the package (except base ones which all windows installs should have). Thats why packages in linux are surprisingly small because usuallu all deps are handled seperately from the package you are trying to install and chances are that another app is already using that dep for something so apt or yum don't have to install anything. It surprises me somtimes how small packages are in apt as opposed to windows.

---

### Post by Adamant1988 on 2006-07-05
Why not give the user a choice? Is there anyway to package it so that the user can be told "Sorry this has dependency problems, but the package can install them for you" Including them in the package in such a way that they're only used if needed seems like a good "grey" area... I don't know if it's EASILY possible, but I  would think it would be possible to do...

---

### Post by nlogax on 2006-07-05
[QUOTE=Adamant1988]Why not give the user a choice?[/QUOTE]

This is what alternatives like AutoPackage are for.

We seem to be confusing the role of the APT package manager and the repositories in Ubuntu/Debian with the installation methods for 3rd party software that is not in the repos.

With a given RELEASE of Ubuntu/Debian, all versions of all applications in the repos will work with the versions of said libraries in the repos.

With 3rd party software that has not been added to the repos, the vendor presumably needs a way of making it installable by people on any distro for a given architecture (such as i386).  They can't count on any Ubuntu/Debian packages and/or libraries being installed.  For these folks, yes statically linking might be worthwhile.  If you're really interested, it's probably worth reading about the following alternatives for installing 3rd party apps:

- Klik
- ZeroInstall
- Autopackage

and others.

---

### Post by m94mni on 2006-07-05
You are also forgetting the security aspects. Remember when recently Windows was hit by a zlib vulnerability? More or less *all* apps using zlib needed to be updated separately. For quite a number of libs, the number of packages can be huge (think libc).

Currently on Linux you install an updated zlib and *all* apps are fixed, just like that. This of course also applies to regular bugfixing...

---

### Post by jan on 2006-07-08
Well autopackage is definitely a good project idea. I think it has beter chance to survive than maybe Automatix.

---

### Post by jimmygoon on 2006-08-05
Whats up with this?
[http://autopackage.org/index.html](http://autopackage.org/index.html)

---

### Post by ciscosurfer on 2006-08-05
I downloaded a .package to see what it was all about (you don't need to download Autopackage at first to get your .package to work -- you will be prompted to download Autopackage once you click on your .package...did that make sense?)  Anyway, I've installed inkscape and abiword using autopackage and everthing seams quite seemless.  I'm very impressed =D> I wonder if it'll take off...

---

### Post by jimmygoon on 2006-08-06
I find "deb"s to be easy... but who knows, maybe this will be more cross platform... That and just thinking about it... It kinda destroys the idea of having automatic updates and what not through the apt-get system...

---

### Post by 23meg on 2006-08-06
[http://www.ubuntuforums.org/showthread.php?t=97504](http://www.ubuntuforums.org/showthread.php?t=97504)

---

### Post by ciscosurfer on 2006-08-06
Everything old is new again :D

---

### Post by mattisking on 2006-08-06
It's my understanding that the plan was/is to go with "smart": [http://labix.org/smart]("http://labix.org/smart")

---

### Post by Amaranth on 2006-08-06
SMART is just a tool like apt that works on top of dpkg. It does not allow you to mix RPM and DEB in the same system, for example.

---

### Post by Iandefor on 2006-08-06
> **Amaranth said:**
> SMART is just a tool like apt that works on top of dpkg. It does not allow you to mix RPM and DEB in the same system, for example. No, it's pm-agnostic. You can use it as a frontend for rpm *and* dpkg, and it supports slackware packages. Also, it *does* allow for mixing rpm and deb packages- it's just that a package in one format won't be listed as installed in the others' lists of installed packages, and it's usually a dumb idea anyways.

---

### Post by Amaranth on 2006-08-06
I never said it couldn't support RPMs and etc, I just said it was like apt. Even if it lets you actually install RPMs and DEBs it doesn't let you mix them properly (dependencies and such).

---

### Post by ZephyrXero on 2006-08-10
Once again here we go...

Autopackage ***IS NOT INTENDED TO REPLACE YOUR NATIVE PACKAGE MANAGER***. It is ***ONLY** INTENDED* for _3rd party_ applications that are either not included or out of date in your local repository.

For example, Ubuntu has Inkscape 0.43 in Dapper's repository. Inkscape 0.44 is out and it has not been backported yet, so if you just were dying to have the latest copy of Inkscape, you would need to uninstall it via apt/synaptic and then install the .package for 0.44, and yes, any updates/upgrades would have to be done manually for your .packages.

Autopackage does not conflict with your local/native package manager as it should only install the app and no libraries. As long as you do not have a copy of the app installed via both, you should be fine. Also, if there are libraries included with a .package they are supposed to be statically linked, so once again no way to conflict with your natively installed ones. However, it is possible, in theory (as I've never seen it happen yet), that a poor developer could screw up and include something improperly, but it's highly unlikely 99.9% of the time.
[B][I]
Use Autopackage at your own risk [/I][/B];)

And yes, it's always worked great for me too :D

---

### Post by he_man on 2006-11-08
Hello. I read somewhere (I can't remember now) that autopackage will be available by default in ubuntu 7.04. This is great!! A good improvement, but...

Reading about zero install and autopackage, I think zero install has some additional features that should be desirable.

I think that signed software is one of those things that should be available (think of virus and microsoft...) and multiple versions of a program or libraries and so on would have to coexist because sometimes you'll need different versions of a library for two different pieces of software.
Zero install seems to be conflict-free also. 
I think this is the most important thing that the installing tool has to solve.
Why autopackage was chosen over zero install?
You've got the comparison here:

[http://zero-install.sourceforge.net/matrix.html](http://zero-install.sourceforge.net/matrix.html)

---

### Post by lithorus on 2006-11-08
Here we go again.....

There should be a general thread called "Will auto-package be installed by default in `cat /etc/issue`+1?"

---

### Post by lithorus on 2006-11-08
To comment about zero-install it does look alot better than autopackage and doesn't have the some of the same issues that autopackages have. In one of the comparisons it says that autopackage (together with zero-install) cannot mess up base-system, which is quite untrue.

However zero-install still have the issue that you cannot have general system wide libraries. Zero-install looks much like a Windows approach to me and it can quickly end up in the same dll-hell that Windows has/had. Eg. one application needs a specific version of a library and it'll need to bundle it for it to work together correctly. A good example of this is vmware which broke because it depended on a specific version of libhal and when the versions got mixed it wouldn't start.

Not using the system-wide libraries also have the effect that if you have a bug in eg. libpng you'll have to patch every single application which uses this library and is installed using zero-install and not using the system-wide libraries.

I haven't seen any confirmation that autopackage would ever be integrated into Ubuntu. But IF it can be combined with apt/dpkg it would be a little bit better than zero-install.

Zero-install is nice but not something which seems to be able to be integrated into apt/dpkg.

---

### Post by RAOF on 2006-11-08
Also, the statement "autopackage available by default" doesn't actually make sense.  The entire (somewhat flawed) idea of autopackage is that it doesn't want, or need, the support of the distribution.  You just run the autopackage and it does the rest.

---

### Post by Burgundavia on 2006-11-09
Even if autopackages issue with the "lets run random bits of code as root" didn't exist, it still doesn't integrate with apt/dpkg. So no, not going to happen. Period. I really do mean that. Trust me.

Corey

---

### Post by he_man on 2006-11-09
I think it would be really a great idea to have autopackage. What autopackage is trying to do now is integrating it with repositories systems as apt, yum and rpm. Once this is done, it would be very useful to install applications that aren't in the repository itself or the latest version of a package without worrying about dependencies. You can install it in your user's directory without any worry.

---

### Post by temcat on 2006-11-12
There are zero reasons to not include Autopackage runtime. Contrary to what many believe, it doesn't really *need* to integrate with apt/dpkg: 

- The proper way - let Autopackage install stuff systemwide to /usr/local. This requires trivial fixes that should be there *anyway, regardless of Autopackage as such*- because it concerns all software installed to /usr/local (for example, from sources). The relevant information can be found here:

[http://plan99.net/autopackage/What_can_distributions_do_to_fix_broken/usr/local_support](http://plan99.net/autopackage/What_can_distributions_do_to_fix_broken/usr/local_support)

- The minimal way - set the default target for Autopackage install to user's home directory. This prevents systemwide installs, but gives user at least something instead of nothing if the software (version) s/he wants to get is not in the repository.

---

### Post by amiga_os on 2006-11-14
There's already been a discussion about the Gobo Linux file structure... which stores files categorised by package and version rather than the standard Unix file system structure (/etc /usr /var...)

A phantom Unix file system structure is made up of symlinks to the latest versions of the relevant packages.  This also gives Gobo the ability to be backwardly compatible on a phenomenal scale.  It was met with scorn and derision by some, and hailed as Messianic by others - which screams innovation to me.

I've been following this discussion... and I've been really excited about it.  It relates to something that Mark Shuttleworth said in his blog, that there should be a standardised Linux package management system across the distros.  And this is why I'm starting a new thread.

Here's an idea for Feisty(+1): **Make the Smart package manager the default package manager for Ubuntu**.

EDIT:
The issue I wanted to raise with this thread was using the Smart package manager.  I just mentioned the discussion about Gobo because that thread showed me that there are clearly people interested in the area of package/software management.  Sorry for being unclear
/EDIT

Mark's Blog entry is here:

[http://www.markshuttleworth.com/archives/66]("http://www.markshuttleworth.com/archives/66")

The Gobo Linux thread is here:

[http://www.ubuntuforums.org/showthread.php?t=297429]("http://www.ubuntuforums.org/showthread.php?t=297429")

The Gobo Linux site here:

[http://gobolinux.org/?page=at_a_glance]("http://gobolinux.org/?page=at_a_glance")

---

### Post by frodon on 2006-11-14
I don't like the idea, i like the standard Unix structure which i find easy, it's just a matter of taking the time to understand.

You're already able to see what is installed thanks to synaptic so i don't get the point. If your going to modify some config files directly then your enough skilled to know where they are, so no interest in such structure. 
Devs should spend more times working on smooth interfaces to handle software installation like synaptic (which is awesome) rather than such details IMO.

So i would say that i'm against this for any ubuntu release, it's just useless IMO.

---

### Post by fog on 2006-11-14
I don't like the idea too. I like the structure of the my system and my package manager.-

---

### Post by dinxter on 2006-11-14
seems to be on the cards [https://features.launchpad.net/distros/ubuntu/+spec/smartpm](https://features.launchpad.net/distros/ubuntu/+spec/smartpm)

as far as reshaping the filesystem goes i have to say i'm not convinced yet. but having said that, if there was someway to build in a method of having verified debs installed as root and all others installed as a lesser user into perhaps a diferent part of the filesystem so that they can do no harm, i'd be all for a change. 
i tend to have to compile from source to ease my paranoia but many new users seem happy to throw in a source.lst entry for apt which could easily destroy the root system if it wanted too. it seems to me to be a seriously dangerous and increasingly common practice as far as i can tell so even a radical change in the filesystem arrangement might be ok if it could address the issue. or perhaps some sort of usermode apt setup could handle this, or smartpm, but im in the dark there

---

### Post by amiga_os on 2006-11-14
Thanks dinxter... looks like it's on the agenda at least...

---

### Post by leech on 2006-11-14
Well on the one hand, last I used SmartPM it wasn't very feature filled, and didn't work very well, and was simply unstable.

On the other hand, it is still in development and is actually made by the developer of Synaptic!

My problem with the Universal Package Support is that there is no such thing as a Universal Package.  Let's take for instance the many RPM distributions.  A Suse RPM will not work properly on a Mandriva Distro, or a Fedora Core one won't work on Suse, etc.  Even sometimes they are broken between ones that are "Based on XXXX"  For example, Debian .deb packages don't always install cleanly on Ubuntu.

The main reason for this is the way the different packages handle dependencies.  From what I recall of RPMs (which I have always hated, though they do have some benefits) is that they can depend on either Package name, or Library version or even both.  So their dependency structure is something like; foobar depends on libfoo, libbar, libfoo.so.2, libbar.so.5.

With something like that, you can actually have the source code of libfoo installed rather than the package with that name, and the package will still install.

Debian packages are a bit more limited in that they only have a Depends, Conflicts, Recommends and Suggested field.  So it would only depend on libfoo and libbar.  Then we have the problems of the debian version of foobar2 is dependent upon libfoo2 and libbar2, but the Ubuntu version is dependent upon libfoo2.1 and libbar2.3.  So the Ubuntu one won't install on Debian or the other way around.  

Now if we start mixing all that together, we're going to get a nasty broken mess.  Think of all the different cool things you can do with debconf, then think of all the packages that are RPM that won't have that.

Another downside is that (at least in my experience, up to and including FC5) that RPMs are SLOW.  It takes at least 5 times as much time to install RPMs through Yum than it does a .deb package through apt-get.  At least this has been what I've experienced here.  Sometimes Yum just freaks out and can't even find the mirror one minute, then it'll be there the next.

The way package managing is so far, it's a downright mess.

The other problem for this "universal package support" is that of security.  Let's face it, the only reason you'd need the package manager to handle all package formats is if you're going to install software from random places, in which case this is one of the things that screws up Windows Installs.

Just some thoughts to take into account.

Leech

---

### Post by leech on 2006-11-14
Now I'll make it a separate post for the Filesystem.  I would say it's a bad idea unless somehow they make it so they're just symbolic links.  For example, Applications folder would really point to /usr/bin.  Games would be /usr/games.  It's be pretty simple, but really unnecessary.  Think about Windows XP.  They basically hid the filesystem from the users anyhow, granted you can just click on Show Folder, but by default, it's hidden.  Why?  Because most of the Billy Ray Wallace type people from Arkansas won't need to go into the filesystem and are happy accessing their porn collection within My Documents.

The same could be said for Ubuntu, really do we need to know where any files are, besides our personal ones?  I mean when the Menu itself will have most of our programs that are GUI driven in them, and even if they don't, you can bring up a terminal (and use auto-complete) or alt+F2 (which also supports auto-complete, though I wish it'd show a drop down menu for it, I'm going to request that for the next Gnome)

Leech

---

### Post by frodon on 2006-11-14
Nice posts leech !

I wouldn't have better explained the question, i fully agree with both posts you made.

Thanks the insight brought

---

### Post by amiga_os on 2006-11-14
After some thinking, and reading leech's post, I don't think I'm a fan of the Gobo filesystem... if only because - why should the filesystem be easy for 1st time users to understand?  They'll only try and fiddle with it then, and probably break something.

However.  My big issue is, say, starfighter - that I can only find on RPM.  Or if I try and code a little program, and want to make it easily available.

In an ideal world, we'd all use .lsp, Linux Standard Packages.  But since they don't exist yet, using a package manager that can install every type of package is the next best thing.  And having that the default package manager in Ubuntu would be awesome.

---

### Post by leech on 2006-11-14
No problem, glad to help.  It just seems that every time it's "Ok, throw in your thoughts on what should be in the next Ubuntu release" that these two subjects come up.  Gobo Linux has been around for quite some time, and no one has adopted it for a reason.  It's not really all that innovative, and innovative doesn't always mean good.  Ubuntu uses the standard filesystem because it IS a standard!  It's pretty much that way on all variations of Unix, perhaps with some slight differences.

Leech

---

### Post by KingArthur10 on 2006-11-14
All I care about is Synaptic.  I chose Ubuntu based on the package manager (the others from SuSE and RedHat just didn't seem intuitive to me).  I love apt and synaptic and would probably consider switching if the whole package managing system was to change.  For all I know, a smart package manager would be used with Synaptic, but if not, I would be very annoyed.

---

### Post by plb on 2006-11-14
There will never be a universal package installer....this is Linux not Windows..people are free to do what they like.....well almost :)

---

### Post by garba on 2006-11-14
> **amiga_os said:**
> 

Here's an idea for Feisty(+1): **Make the Smart package manager the default package manager for Ubuntu**.


Sometimes i wonder how you guys could ever come up with ideas like these: you are "suggesting" that in five months time ubuntu should DEFAULT to a new package format and trash the debian package format. Do you have ad idea of the efforts that went into this deb thing you are suggesting to ditch?

---

### Post by garba on 2006-11-14
> **leech said:**
> They basically hid the filesystem from the users anyhow, granted you can just click on Show Folder, but by default, it's hidden.  Why?  Because most of the Billy Ray Wallace type people from Arkansas won't need to go into the filesystem and are happy accessing their porn collection within My Documents.


i propose /porn to be taken into consideration in the next draft of the linux file system hierarchy, this is on par with proposing smart as the default package manager for a debian based distro :p

---

### Post by scaine on 2006-11-14
Wow - standard package management just keeps cropping up, doesn't it?  :) 

[http://www.ubuntuforums.org/showthread.php?t=295588](http://www.ubuntuforums.org/showthread.php?t=295588) (talks about autopackage for Feisty)
and
[http://www.ubuntuforums.org/showthread.php?t=97504](http://www.ubuntuforums.org/showthread.php?t=97504) (first autopackage discussion I was involved in.  Amusingly, lithorus then links to ANOTHER autopackage discussion back in Breezy).

The only thing I'll say this time round, since it's all been said before, is that it's great news that Mark Shuttleworth is tentatively putting forward the notion.  Perhaps something will come of it this time round.  Not in Feisty, probably not even in Feisty+1, but maybe, eventually, we'll see the first steps towards the day when you can visit [http://www.gnomefiles.org/](http://www.gnomefiles.org/) and actually install something that you think might be useful, without taking a crash course in programming.

As for the filesystem, I'd like to see change there too.  It might be a standard filesystem, but even after nearly two years of using it, I still think it sucks - simply because no one can agree what standard IS the standard.  So you get some files in /usr/lib that should be in /usr/local/lib, or wait a minute, shouldn't that be /lib... no, maybe it's in /var/lib.  I've given up by then.

Hang on, shouldn't my mount points be inside /mnt?  What the hell??? ](*,)

;)

---

### Post by scaine on 2006-11-14
> **garba said:**
> Sometimes i wonder how you guys could ever come up with ideas like this: you are "suggesting" that in five months time ubuntu should DEFAULT to a new package format and trash the debian package format.

Garba - I don't think amiga_os is necessarily suggesting that.  Mark Shuttleworth is.  But you're right - 5 months is crazy talk.  But maybe the snowball will start rolling...

---

### Post by garba on 2006-11-14
Perhaps it's just me who's narrowminded, but i really can't understand all this hype about these "package systems", or whatever they aim at accomplishing. My point is, the open source environment is an heterogenous one, we have different build systems, different release schedules, code forks, you name it. Hence the need for those projects we refer to as "distros": their purpose is (should?) assuring all pieces fit in together nicely. Now, deploying a distro takes hundreds of developers, mantainers, well i guess you have the picture.

Then some dude who has just taken a course in c at the local LUG comes along and comes up with the soopa-automatic-package-creator... :mrgreen:

The problem doesn't lie with the package manager, the problem lies with the way open source software is developed I fear.

---

### Post by Hobbes on 2006-11-14
I think some of you are misunderstanding what the SMART package manager is.  It is not a replacement for apt-style or .deb files.  Nor is it a way to install rpms or some universal packages on ubuntu.

The benefits of SMART are that it claims to be a better solution than say Synaptic+apt back-end, and the reason that it is universal is that while ubuntu could have SMART downloading, managing, and installing .deb files from different apt repositories, etc... Redhat, Suse, Fedora Core, etc. users can also use SMART to download, manage, and install rpms on their systems.  Therefore, without abandoning either parties' packaging system, there would be a usability gain because if anyone ever switched distrobutions they would still be using the familiar SMART package manager. An added bonus of course is that development could be more focused on this system.

Answers to more questions about SMART here: [http://labix.org/smart/faq](http://labix.org/smart/faq)

---

### Post by garba on 2006-11-14
taken from smart's website:

---
What is Smart?
Smart is a meta-package manager in the spirit of APT, YUM, URPMI and others. It can manage RPM, DEB and Slackware packages and provides a clean architecture to add new package and repository formats (called channels in Smart). 
What sets Smart apart is a dependency-solving algorithm that outperforms other package managers, a clean architecture, wide support for package and repository formats, and great mirror-management. Check the  features page for more information.
---

yeah sure, i loved the better dependency-solving algorithm part, you know what? this reminds me of the tango project, same approach: lemme show you how this should be done kind of thing

---

### Post by amiga_os on 2006-11-14
Garba - I think you're right, it would be crazy to ditch the deb system in 6 months.  However, at the moment, when I want to download something from another website, I have to:

1 - wait for them to produce some Ubuntu debs
2 - compile it myself
3 - install a deb intended for another version of Ubuntu
4 - install a deb intended for Debian
5 - use alien and convert an rpm package

Sometimes I can't find Ubuntu debs for something I want to download... sometimes I can't find it packaged as a deb at all.

Another issue is how hard developers have to work, simply to get through the 'distro barrier' so that an end user can have a working copy of their software:

I use Cinelerra.  Specifically I use the cvs.cinelerra packages (this is *not* a development version from cvs, this is actually - ironically - a *more* stable version upstream from the heroine cinelerra code).  Those guys package cinelerra in rpm, slack and deb... and they have to do different rpms and debs for Suse, Fedora, Ubuntu and Debian.

I think - in the long term - I'd love to see a standard linux package system, that basically works as well as apt, but better.  Smart has algorithms because it works out which package would be best for your system... and that may not necessarily be the most up to date package.  In other words, it tries to deal with some of the myriad of issues thrown up by the fact that you can install packages from anywhere in any format.

I'd like to see my package manager handle the Ubuntu repos very carefully, keeping track of my system, keeping everything compatible and up to date - just like it does now.  But I'd also like to see my package manager intelligently handle software that I've been forced to download that is packaged for a different distro or version.

Whether that package manager is called Synaptic or Smart... I don't really care.

There is one thing that's cropped up a bit in this thread so far... the fact that this has been mentioned "over and over again".  I think there's a really good reason this has been mentioned over and over again... because going to a website and downloading a 1 meg Tetris clone seems - at least to me - insanely complex with the current situation.

I would like to see Feisty+1 at least be able to have a good go at installing an rpm, or checking if it conflicts with any other installed software, when I double click it on my desktop...

---

### Post by amiga_os on 2006-11-14
I've just realised that the guy behind smart, Gustavo Niemeyer, is a maintainer for Synaptic:

[http://www.nongnu.org/synaptic/contribute.html]("http://www.nongnu.org/synaptic/contribute.html")
[http://labix.org/smart]("http://labix.org/smart")

If someone's already mentioned that in this thread, then I'm sorry - it's late... I think I remember reading it.  But it does lend some credibility to smart, the guy behind it has a good track record with these kind of systems :D

I've also just realised that Canonical are funding the development of Smart.  So maybe some people have been planning to make it the package manager in Ubuntu for a long time?

---

### Post by scokar on 2006-11-15
> **amiga_os said:**
> ...why should the filesystem be easy for 1st time users to understand? ...

yeah! and why should Linux be easy to understand for the 1st time user? Ubuntu? oh wait...

---

### Post by amiga_os on 2006-11-15
> **scokar said:**
> yeah! and why should Linux be easy to understand for the 1st time user? Ubuntu? oh wait...

The filesystem shouldn't be easy to understand for the 1st time user.  That's why you need root access to change anything below your own home directory.  Messing around can damage your system... and if the file system was so intuitive to the newbie that they felt they could poke around, they're just going to get themselves into a pointless pickle - trust me, I'm a newbie, and that's exactly what I try to do.

The filesystem structure - as it is - is actually very intuitive for the people who know what to do with it.  Programs are categorised according to function, rather than package, which means you can partition your drive to keep similar areas of the system together... even though the average user probably doesn't do that now.

I do it to a certain extent.  I have a separate /boot partition, as I dual boot 4 os's (Ubuntu, Fedora, PCLinuxOS and Debian - though the last three are just to play with, and get changed frequently)... having a separate /boot partition allows me to keep all the boot files I need in one place.

The Ubuntu GUIs (such as Gnome and the package manager) then make everything I need to see in the filesystem obvious and simple, while keeping the more complex and advanced stuff hidden.

Anyway... I have now been accused of being too pro the Gobo filesystem and being too anti the idea all in the same thread...

---

### Post by leech on 2006-11-15
> **garba said:**
> i propose /porn to be taken into consideration in the next draft of the linux file system hierarchy, this is on par with proposing smart as the default package manager for a debian based distro :p

I say forget all this and let's get down to what computers and the internet are really used for: PORN!  

Let's dump Synaptic and apt-get and have porn-get as our default package manager!

By the way, there really is a 'porn-get'

[http://www.lesbian.mine.nu/](http://www.lesbian.mine.nu/)

Now THAT is what I call a package manager!

Leech

---

### Post by leech on 2006-11-15
> **scaine said:**
> 
As for the filesystem, I'd like to see change there too.  It might be a standard filesystem, but even after nearly two years of using it, I still think it sucks - simply because no one can agree what standard IS the standard.  So you get some files in /usr/lib that should be in /usr/local/lib, or wait a minute, shouldn't that be /lib... no, maybe it's in /var/lib.  I've given up by then.

Hang on, shouldn't my mount points be inside /mnt?  What the hell??? ](*,)

;)

Ok, let me preface this with "RTFM"  I usually don't say that, but honestly, anyone who wants to say that the file system is not standard as to where things go is simply ignorant of the way it works.

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

That shall enlighten you all to the Standard FHS.

Leech

---

### Post by leech on 2006-11-15
> **amiga_os said:**
> I've just realised that the guy behind smart, Gustavo Niemeyer, is a maintainer for Synaptic:

[http://www.nongnu.org/synaptic/contribute.html]("http://www.nongnu.org/synaptic/contribute.html")
[http://labix.org/smart]("http://labix.org/smart")

If someone's already mentioned that in this thread, then I'm sorry - it's late... I think I remember reading it.  But it does lend some credibility to smart, the guy behind it has a good track record with these kind of systems :D

I've also just realised that Canonical are funding the development of Smart.  So maybe some people have been planning to make it the package manager in Ubuntu for a long time?

Yeah, I pointed out that, though I wasn't aware that Canonical are funding the development.

Please note that I know Smart is not replacing .deb.  It's an entirely different thing.  .deb is the package format, apt-get is the package manager (cli) Synaptic sits on top of apt-get and Smart sits on top of apt-get, but also supports rpm, dpkg, pkg-add, etc...  well, can't remember if the last one is what slackware uses, but you get the idea.  It's more of a universal package manager front-end.

Leech

---

### Post by scaine on 2006-11-15
> **leech said:**
> Ok, let me preface this with "RTFM"  I usually don't say that, but honestly, anyone who wants to say that the file system is not standard as to where things go is simply ignorant of the way it works.

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

That shall enlighten you all to the Standard FHS.

Leech

Whoah, there Leech.  If Distro developers and Package maintainers won't "RTFM", then why the hell should I?  :rolleyes: 

I'm not saying that the Linux file system doesn't have standards and protocols, but since they're not enforced, and since everyone interprets them differently, it's a mess.

It's a minor point really.  The only time it really annoys me is if I install a new app and want that app to launch from firefox, for example.  It asks me where the program I want to launch is, and I'm like, "Dunno, mate - let me open a terminal and use the 'whereis' command".

Like I say - minor.  But annoying.  Every time I have to open a terminal, Ubuntu has lost a tiny, tiny bit of respect.  Sure terminal is awesome and powerful - but if I don't chose to open, I shouldn't have to.

It'll happen one day though.  That's why I'm still here, 2 years on.

---

### Post by scaine on 2006-11-15
> **leech said:**
> Ok, let me preface this with "RTFM"  I usually don't say that, but honestly, anyone who wants to say that the file system is not standard as to where things go is simply ignorant of the way it works.

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

That shall enlighten you all to the Standard FHS.

Leech

Sorry, Leech - I gotta quote you again.  This link is awesome.  But look at this - it's the first one I clicked on, since it's to do with my earlier example :

> /usr/local/share

The requirements for the contents of this directory are the same as /usr/share. The only additional constraint is that /usr/local/share/man and /usr/local/man directories must be synonomous (usually this means that one of them must be a symbolic link). [28]

So, basically, you can use either/or.  This is the reason it's such a mess.  Even the official specification can't make up its mind on the best place to put stuff.

At least, that's how it reads to me, so I guess a few other, more important, folk have come to the same conclusion (ie package creators).

Good link though, interesting - thanks.

---

### Post by Wolki on 2006-11-15
> **scaine]It's a minor point really. The only time it really annoys me is if I install a new app and want that app to launch from firefox, for example. It asks me where the program I want to launch is, and I'm like, "Dunno, mate - let me open a terminal and use the 'whereis' command".[/QUOTE]

So the open with dialog in Firefox sucks. I fully agree. That's a fault in an application, not in the standard. Even if all applications were installed into the same directory, it would suck that you a) have to know what that directory is called b) have to know what the executable is called c) have to navigate there and browse through thousands of files that have nothing to do with what you're trying to do.


[QUOTE=scaine said:**
> 
So, basically, you can use either/or.  This is the reason it's such a mess.  Even the official specification can't make up its mind on the best place to put stuff.

At least, that's how it reads to me, so I guess a few other, more important, folk have come to the same conclusion (ie package creators).

Well, I guess they expect you to read the whole thing, as often with such specifications (makes them shorter). See here:
> 
/usr/local : Local hierarchy
Purpose

The /usr/local hierarchy is for use by the system administrator when installing software locally. It needs to be safe from being overwritten when the system software is updated. It may be used for programs and data that are shareable amongst a group of hosts, but not found in /usr.

So the purpose of /usr/share and /usr/share/local is actually quite clear. One is for stuff from packages (i.e. will be updatd by the packaging system), the other is for locally installed (and usually compiled) stuff. But they are similar in that the stuff that would go into /usr/share when installed from a package needs to go into /usr/local/share when installed manually.

This does not mean that there aren't packagers who do not pay attention to this and package things into /usr/local. Often this is a hint that they don't know much about packaging, and that the packages might be of low quality, Ubuntu packages are checked for such things (among others) before they go in.

---

### Post by leech on 2006-11-15
Wolki said it perfectly.

It's a matter of where the package creator decides to put it, which means that it's their fault if it's in the wrong place, not the file system itself.

It's really not that hard to see why it is the way it is.  Most people have a hard time accepting the fact that Unix style file systems don't use drive letters for different partitions.  If you really think about it, if you have /boot on /dev/hda1, / on /dev/hda2 and /home on /dev/hdb1 with swap on /dev/hda4 should it really be that apparent to the end users?  

The real beauty of the way it works is in that if you do have different directories mounted on different partitions or physical hard drives this way is that it works automatically for when you install things.  Unlike Windows where if you are picky where things are installed and want your games in C:\Games, then you have to change the installation path on EVERY game you install.  It's a complete mess there.

By the way, as far as 'I have to go to the terminal'....  So?  Quite frankly there are a lot of times I have to open a command prompt inside of Windows.  It's not that the terminal is some evil thing that is unusable.  I try to write all my guides so that you don't have to open the Terminal, but that's just because most people have gotten so used to just pointing and clicking that it's absurd, and not all people of course actually are interested in actually LEARNING about their computer, they just want to be able to browse the net and do their email, etc.  In which case you wouldn't ever have to open a terminal for in ubuntu anyhow.

I could say the same thing about windows, "Every time I have to run a virus scan or a spyware scan, Windows loses a tiny bit of respect from me."  Well, I wouldn't say tiny, I get pissed when I have to scan for such things, and that's just from going to my regular sites.  Cookies are pretty much everywhere on the net.

Leech

---

### Post by fox_xyzzy on 2006-12-05
> **lithorus said:**
> To comment about zero-install it does look alot better than autopackage and doesn't have the some of the same issues that autopackages have. In one of the comparisons it says that autopackage (together with zero-install) cannot mess up base-system, which is quite untrue.

Well, since you never install as root, it's hard to see how it would mess up the base system (at least, without the base system being buggy already).

> 
However zero-install still have the issue that you cannot have general system wide libraries. Zero-install looks much like a Windows approach to me and it can quickly end up in the same dll-hell that Windows has/had. Eg. one application needs a specific version of a library and it'll need to bundle it for it to work together correctly. A good example of this is vmware which broke because it depended on a specific version of libhal and when the versions got mixed it wouldn't start.

I don't see where it says this on the site. All I see is ([http://0install.net/matrix.html):](http://0install.net/matrix.html):)

Libraries shared between programs 	Yes

In fact, it removes the possibility of DLL-hell, because libraries are shared automatically *only if compatible*. E.g.:

Two programs need GTK => they share GTK 2.8.6.

One program needs GTK < 2.1.0, one needs GTK > 2.8.0 => two copies of GTK are downloaded. Each program runs with the version it needs.

> 
Not using the system-wide libraries also have the effect that if you have a bug in eg. libpng you'll have to patch every single application which uses this library and is installed using zero-install and not using the system-wide libraries.


True, although a new libpng available through Zero Install would affect all Zero Install applications.

---

### Post by fox_xyzzy on 2006-12-06
Note that there is a Zero Install .deb waiting for comments in the REVU queue here:

[http://revu.tauware.de/details.py?upid=3360](http://revu.tauware.de/details.py?upid=3360)

---

### Post by ma1kel on 2006-12-13
Autopackage is a new project, with the goal of making a GUI based "click and finish" installer for Linux. The idea of it is to be easy and cross platform(distributions). You don't need to download a special "package manager" as it comes with one, if you don't have the "package manager" installed when you click the .package file, it will ask you if you want to install it.

Gaim and Inkscape as two high-profile programs have an Autopackage installer, so you can try them out.

Now, should Ubuntu support it through including the Autopackage "package manager" by default in Feisty and recommending developers/users to use it by including .package files of software in the repos?

---

### Post by lwr on 2006-12-13
I've heard about this from [LugRadio]("http://www.lugradio.org/"). I think it would be a good idea to support it, as you say, to help new users, until they discover the joys of apt. I'm all for making things easy; it's the only way we're going to grow the Linux market share. I'm not sure I'd go so far as to recommend that that developers/users use it. It's up to them, and I think most people would prefer the current way of doing things the majority of the time.

---

### Post by fuscia on 2006-12-13
sure, adds another choice. you can still do it the 'handful of leaves' way, if you wish. btw, how can you have zero beans?

---

### Post by lwr on 2006-12-13
> **fuscia said:**
> sure, adds another choice. you can still do it the 'handful of leaves' way, if you wish. btw, how can you have zero beans?

It appears that beans aren't being added on for posts at the moment. I was on 195 about 5 posts ago.

---

### Post by hanzomon4 on 2006-12-13
Seems nice, however I would like something smilar to the OSX or rox's app-dirs.

---

### Post by sweemeng on 2006-12-13
is it really that necessary

i install amsn using using autopackage. no problem here. and it even have manage third party software option in kubuntu menu. 

on the other hand, you will need tcl, thats all

---

### Post by finferflu on 2006-12-13
I voted yes only because in that way the switch from Windows is easier, even though I wouldn't like Linux to be compared to Windows. People should get used to the difference as well, I think. Difference is good!

---

### Post by dorcssa on 2006-12-13
Well, I don't know what to do with an autopackage. The new amsn only have autopakcage, and no deb file, so I dowloadid it. I followed the instuctions, and all that happened, that it created a library in my /home/user folder with the name autopackage. There was no launcher, or anything else, so I removed it, and installed back the one what is in the repos.

---

### Post by public_void on 2006-12-13
I'm not really in favour, I prefer .debs and wished aMSN did a .deb, and others, not just an autopackage.

---

### Post by earobinson on 2006-12-13
I don't think Autopackage is new i just think it hasn't caught on but it "kicks the lamas a**" i'm all for ubuntu using it.

---

### Post by maniacmusician on 2006-12-14
It sounds alright, I don't see why not. Is there really any "support" involved?

I'm more interested, however, in a GUI-based program that helps a user easily compile programs from source. That'd be an interesting experiment, I think, because it would keep the ease of Ubuntu while picking up the optimization of source-based distros. 

However, I still love the current way of doing things, it's nice and fast and easy to do.

---

### Post by DC@DR on 2006-12-14
I guess it will help to convert more Windows users to Ubuntu...:-)

---

### Post by MetalMusicAddict on 2006-12-14
I think the GNU/Linux community just needs to agree in a standard package. Shuttleworth has even called for [THIS]("http://www.markshuttleworth.com/archives/66").

---

### Post by housam on 2006-12-14
I think it is a good goal for feisty. I've posted a [similar thread ]("http://www.ubuntuforums.org/search.php?searchid=11193276")day's ago.

---

### Post by mcduck on 2006-12-14
New project? Should Ubuntu support it?

Come on. It's been around for ages and works just fine with Ubuntu.

First time you download something packaged with Autopackage you run the binary file from terminal with simple './appname.package', and it'll install Autopackage GUI for you, add configuration tools to your menu (to add & remove software packaged with Autopackage), configure icons for .package files and then install the app you wanted. After that .package files are automatically handled correctly.

I've used it since Hoary Hedgehog for couple of apps that aren't available as .debs :)

Anyway, I'd rather see debian packages, so I could handle all my software with one single tool, and also get automatic updates for them.

---

### Post by dorcssa on 2006-12-14
> **dorcssa said:**
> Well, I don't know what to do with an autopackage. The new amsn only have autopakcage, and no deb file, so I dowloadid it. I followed the instuctions, and all that happened, that it created a library in my /home/user folder with the name autopackage. There was no launcher, or anything else, so I removed it, and installed back the one what is in the repos.

Nobody can tell what I do wrong?

---

### Post by Lord Illidan on 2006-12-14
Autopackage has been out for quite some time. I like it, but at the same time, I prefer .deb and synaptic..

---

### Post by gorilla on 2006-12-14
Autopackage surely is not meant to replace a system's package manager.

It would be great if more developer supported this, but I don't see a point in a OS supporting it?

btw, autopackage is better than .debs because AFAIK it installs also dependencies.

---

### Post by Lord Illidan on 2006-12-14
> **gorilla said:**
> Autopackage surely is not meant to replace a system's package manager.

It would be great if more developer supported this, but I don't see a point in a OS supporting it?

btw, autopackage is better than .debs because AFAIK it installs also dependencies.

Um, not always. Some libraries might have to be provided by the distro. And anyway, if you are downloading an app from the repo, dependencies are always handled for you.

If you are talking about .debs and .package files on the internet, well then, yes, the autopackage tends to be better.

---

### Post by Polygon on 2006-12-14
a packaging standard is what linux really needs. Then all you have to do is double click it and enter your root password and it installs, on ANY distrubution. Whether it is this autopackage, deb, rpm, or whatever, a standard would make it easier for everyone.

---

### Post by maagimies on 2006-12-14
I just tried out Autopackage for the first time; I installed the game Tome and InkScape. Both went on greatly.
If not otherwise supported, I think Ubuntu should ship with the Gtk installer part so the first install won't go trough in text.

---

### Post by awakatanka on 2006-12-14
There where some heated discusson a year back on this forum about it. Even the dev from autopackage posted some info about it and tryed to defend his few and the fud that was spread about it.

---

### Post by qamelian on 2006-12-14
> **awakatanka said:**
> There where some heated discusson a year back on this forum about it. Even the dev from autopackage posted some info about it and tryed to defend his few and the fud that was spread about it.
Unfortunately, it wasn't all FUD. Although autopackages generally work well, I've had a couple of bad experiences them causing breakage on my system. They also bring back the "bad old days" of upgrading a single app at a time. Autopakage is a good way to occassionally get a newer version of a package or one that doesn't exist for your distro, but they can still be a gamble.

---

### Post by Ptero-4 on 2006-12-14
We should support klik more. It's better and promises what OSX gives, packages that are easy to install and easy to move around after installation.

---

### Post by darkhatter on 2006-12-14
its the rpm the "standard" on L.S.B. atleast, you can still use apt with rpms so people wouldn't even notice if Ubuntu switched to rpm

---

### Post by rlozano on 2006-12-14
it's not that it will exactly be alot easier to a new user, but more thatn that, Ubuntu will become attractive to big software companies if an Autopackage will be included. i think that is where the beauty of autopackage will come in.

---

### Post by darkhatter on 2006-12-14
> **rlozano said:**
> it's not that it will exactly be alot easier to a new user, but more thatn that, Ubuntu will become attractive to big software companies if an Autopackage will be included. i think that is where the beauty of autopackage will come in.

I don't think package format was ever a problem they just support Red Hat and leave everyone else to figure out their own way.

---

### Post by rlozano on 2006-12-14
then you can do the marketing tango, darkhatter. :-)

---

### Post by aysiu on 2006-12-14
You'd be amazed how many threads there are about AutoPackage. Well, now they're all in one place. Have fun discussing it.

By the way, as far as I can tell, based on [AutoPackage's home page](http://autopackage.org/), there's nothing Ubuntu needs to do to "support" AutoPackage. The whole point of AutoPackage is that it works a lot like a setup.exe in Windows and doesn't need integration with the distro. It's up to the software developers to create .packages for AutoPackage.

It has a notice for developers "Learn how to create packages." It's not a notice to developers "How to integrate AutoPackage into your distro."

Am I reading that wrong? What does Ubuntu have to do to "include" AutoPackage exactly?

---

### Post by hanzomon4 on 2006-12-15
I just read the article on page 1 and it seems that autopackage will use some form of application directories

---

### Post by temcat on 2006-12-15
> **aysiu said:**
> What does Ubuntu have to do to "include" AutoPackage exactly?

Strictly speaking, you don't have to do anything specific, but the actions outlined below will improve user experience.

1. Install Autopackage runtime by default.

2. Set it up:

2a. The proper way: make the trivial fixes needed for /usr/local support (this is useful not only for autopackage, but for source installs, too) and set /usr/local as the default install prefix. The necessary fixes are listed here: [http://plan99.net/autopackage/What_can_distributions_do_to_fix_broken/usr/local_support](http://plan99.net/autopackage/What_can_distributions_do_to_fix_broken/usr/local_support)

2b. The minimal way: set /home as the default install prefix. In this case the users won't be able to install software systemwide, but will at least have something if the needed software is not in the repositories. And again, autopackage won't intefere with system files in any way.

---

### Post by NoTiG on 2006-12-15
I think smartpackage is the future ........

---

### Post by MadMan2k on 2006-12-15
believe it or not but package managment is the only area where linux is ahaead of osx & windows. autopackage is a step back.

---

### Post by aamukahvi on 2006-12-15
> **MadMan2k said:**
> believe it or not but package managment is the only area where linux is ahaead of osx & windows. autopackage is a step back.
If only it was unified.

---

### Post by aysiu on 2006-12-15
> **aamukahvi said:**
> If only it was unified.
Or if only there were more packages available in the repositories.

---

### Post by dorcssa on 2006-12-16
> **MadMan2k said:**
> believe it or not but package managment is the only area where linux is ahaead of osx & windows. autopackage is a step back.

A totally agree with that.

---

### Post by Burgundavia on 2006-12-16
I just wanted to make clear that this is not going to happen for Feisty. Please see page one of this thread for a link to the bug report in which autopackage was rejected by Matt Zimmerman, the lead distro dev and Canonicals CTO.

Corey

---

### Post by temcat on 2006-12-16
> **Burgundavia said:**
> I just wanted to make clear that this is not going to happen for Feisty. Please see page one of this thread for a link to the bug report in which autopackage was rejected by Matt Zimmerman, the lead distro dev and Canonicals CTO.

Corey

This was expected. However, the reasons he cited were hardly valid. Improving Ubuntu packaging system is good, but it's inherently unable to help solve the problem of third party packaging when you realise that Ubuntu is not the only distro in the world and ISV do not want to have different packages even for all major distros out there. Now, the REAL reason might be that Matt has a vision for Ubuntu as THE Linux distro. But in this case, why not say openly "No, we are NOT interested in cross-distro packaging and want ISV to package for Ubuntu exclusively"?

Ultimately, I don't care if it's Autopackage, ZeroInstall, LSB-on-steroids or something else. What I care about is having a working solution for easy to install cross-distro 3rd party packages. Autopackage is closest to this goal. All it esentially takes to implement it is a tiniest bit of standardization (mostly redarding menu creation and MIME types) and fixing /usr/local support issues, which will make native package manager integration unnecessary.

---

### Post by samjh on 2006-12-24
I have been annually installing linux on my Windows PC for the past 3 years.  This is my third year trying linux, and my second year trying Ubuntu (my first trial was Red Hat).

IMHO, the one thing which really sets linux back from Windows in being accepted by non-technical people, is that there is no universal, easy-to-use software packaging and distribution system.

For Windows, you download a setup packages, and run it (usually named setup.exe, install.exe, or something to that effect).  Dependencies are usually fulfilled without a fuss.  Uninstallation is usually very clean these days.  Very easy and simple stuff.  Old software is very easy to update, and updates can be applied as soon as they are released.

But for linux, there are rpm, deb, tgz, and other packaging formats.  Updates are tied to the individual linux distro, and configuring repositories are a serious pain in the *** for those who don't know much about computers.  Then there is "dependency hell", which these days are even worse than Windows "DLL hell".

Should the linux community work toward a single, universal packaging format?  In this way, linux users can download updates directly from the publisher, without depending on repositories to update - a process that often takes months.  Like Windows, users merely download the setup file and run it to install.  If any needed files are missing, it can inform the user to install them, or even install them itself (users may even get an option to choose where the files are installed).  Like Windows, there would also be a universal package management software (eg. Add/Remove Packages), that can be used to perform a clean uninstall of the package, with the option to remove any unneeded dependencies.

I understand that because of the many distros that are available, along with the accompanying niggles of each one, the creation of a universal packaging format would be problematic.  But surely if the major distros like Ubuntu, SUSE, Fedora, and Debian, all combined their expertise, a universal packaging format could be created that will allow packages to be installed reliably on the vast majority of linux machines?

What does everyone think of this?

---

### Post by cilynx on 2006-12-24
Yes - it will be difficult but should be attempted

Being a Debian Junky for the last 10 years or so, I have to tout the wonders of the deb dependency resolution system.  It is in my opinion far and away better than any other package manager in existance.  Again in my opinion, rpm is a dying breed.  It does what it needs to, but not much else.  It pretty much stays around because there is a large userbase around it, not because of good tech.  Slackware never really claimed that tgz was a package format.  All it is is a tarball.  A zip file for you non-'nix folks out there.

As for your comparisons to the Windows world, I have to provide contest.  The reason that "dependencies are usually fulfilled without a fuss" on Windows is that there are practically no shared libraries.  Every program is an island and doesn't rely on any other work.  This may make for a nice isolated installation, but it becomes highly inefficient if you have multiple similar applications running on the machine.

Finally, why stop with a unified package manager?  I remember a while back, a dispute about whether applications should be spread across the filesystem or each have their own directory such as operations under /opt.  It would be kinda neat to be able to wholy and completely remove an application with a simple 'rm  -rf /opt/badapp/'.  Unfortunately, this once again leads to difficulties with shared libraries.  If two apps share some code, where does that go?

---

### Post by Henry Rayker on 2006-12-24
I guess it could be done, but I don't think it should be. At the same time, it could be nice as well. The repos are very nice in that they allow for trusted locations to update your applications essentially automagically. By simplifying to one type of installation, though, I think viruses and the like would have a better chance of propagating. I've only had a couple problems with dependencies (usually because I didn't read the documentation, though ](*,)  ) I don't think a "sudo ./configure" and "sudo make install" is terribly rough, in terms of installation.

I guess I just don't really have too much of an opinion because I can't really weigh the possible security problems against the ease of use (given that I think security is best left to an educated user and the fact that I don't think the current methods are too rough)

---

### Post by cilynx on 2006-12-24
Personally, I think having an LSB certification on applications proving that they have a working 'make uninstall' would be a nice thing.

---

### Post by kripkenstein on 2006-12-25
Actually, this problem is in the process of being fixed, and fixed well I think. Look at [Autopackage]("http://autopackage.org/") ([good summary on Wikipedia]("http://en.wikipedia.org/wiki/Autopackage"))

It is already being used for some projects, and interest in it is rising. What is nice is that it not only works well, it has a very clean GUI, even nicer than the Windows installer.

Expect a few bugs though, at this stage. But the project looks extremely promising.

---

### Post by rykel on 2006-12-25
To all fans, critics and watchers of autopackage,

Let me set the record straight:

[INDENT]1.   Ubuntu does NOT need to "support" autopackage per se, although it would be a nice gesture to include the autopackage support code in the default installation. It would be even nicer to set those PATHS correctly as defined in the Linux Standard Base? (?) or whatever the paths were that was mentioned by temcat. (thanks, aysius!)

2.   Autopackage is easy to install - as easy as Synaptic/gDebi, if not easier. Period.

3.   Autopackage can be installed as USER, rather than Root, which means my younger brother can install all the Linux programs he likes in his User account and not mess around with my System Password or files.

4.   Autopackage (One-Installer-Does-It-All) means that every program written for Linux will only have one installer, versus a page full of downloads for different distros. If software creators "love" making a whole list of binaries to keep up with all the distros on Distrowatch.com, fine. Otherwise, autopackage certainly makes it easier for developers as much as for their users.

5.   Autopackage puts the power back into the hands of the program developers. If all Linux programs come as autopackages, we will then go to the respective websites and download the latest and fastest versions of whatever software we need, rather than wait for days (or months) on end for the distro to make it available in the repositories.

6.   Last but not least, unless the distro can do the following two things, or else do not try to LOCK users into its package manager:

[INDENT]a.   Include EVERY SINGLE Linux program out there in the repositories;

b.   Keep them all UP-TO-DATE.[/INDENT]
[/INDENT]
Hope that clears the light. Correct me if I am wrong in any of the points. Come on!   : )

---

### Post by temcat on 2006-12-25
As an update on the topic, it seems that recently the situation with /usr/local support on Ubuntu has improved significantly. While there are some things left that don't work, it shows a movement in the right direction. Keep on the good work!

Link: [http://article.gmane.org/gmane.comp.autopackage.devel/5856](http://article.gmane.org/gmane.comp.autopackage.devel/5856)

---

### Post by qamelian on 2006-12-25
> **rykel said:**
> To all fans, critics and watchers of autopackage,

Let me set the record straight:[INDENT]1.   Ubuntu does NOT need to "support" autopackage per se, although it would be a nice gesture to include the autopackage support code in the default installation. It would be even nicer to set those PATHS correctly as defined in the Linux Standard Base? (?) or whatever the paths were that was mentioned by temcat. (thanks, aysius!)[/INDENT][INDENT]Okay, I'll give you this one.

> 2.   Autopackage is easy to install - as easy as Synaptic/gDebi, if not easier. Period.For the most part, this is correct. However, I have had some autopackages fail miserably while trying to install extra stuff that a package needs to work.[/quote]

> 3.   Autopackage can be installed as USER, rather than Root, which means my younger brother can install all the Linux programs he likes in his User account and not mess around with my System Password or files.This is news to me. Every autopackage I have ever tested required admin rights to install. I have never seen one yet that did not prompt for a password or fail when no password was provided.[/quote]

> 4.   Autopackage (One-Installer-Does-It-All) means that every program written for Linux will only have one installer, versus a page full of downloads for different distros. If software creators "love" making a whole list of binaries to keep up with all the distros on Distrowatch.com, fine. Otherwise, autopackage certainly makes it easier for developers as much as for their users.The autopackage concept is nice, but it's not ideal. Several times I've used autopackages which failed to detect existing libraries on my system and proceeded to download what it "needed" to complete an install. In some cases, this has resulted in other applications being broken.
> 5.   Autopackage puts the power back into the hands of the program developers. If all Linux programs come as autopackages, we will then go to the respective websites and download the latest and fastest versions of whatever software we need, rather than wait for days (or months) on end for the distro to make it available in the repositories.Again, nice idea but it doesn't always work out that way. Installing an application from autopackage is now guarantee that it will install and work properly on any given distro.

> 6.   Last but not least, unless the distro can do the following two things, or else do not try to LOCK users into its package manager:[INDENT]a.   Include EVERY SINGLE Linux program out there in the repositories;

b.   Keep them all UP-TO-DATE.[/INDENT][/INDENT]Users are never "locked into" a given package manager. There are always multiple ways to install a given piece of software. Some just require more effort than others.
> Hope that clears the light. Correct me if I am wrong in any of the points. Come on!   : )I'm all for the Autopackage concept, but only when it really is the panacea that some folks make it out to be already. I've had some autopackages install completely trouble-free. I've had others that have left me with a badly broken system. That said, it is improving all the time.

---

### Post by msak007 on 2006-12-25
This has always been one of the sticking points for Linux detractors. They always argue that Windows is simpler to install apps in and that Linux will never gain the market share because too many distros all have their own packaging systems and they're incompatible. And to a certain extent I agree, but I'm not saying I agree with a need or wish for a unified packaging system. Let me explain why (this is a specific reference to Autopackage which kripkenstein mentioned).

I just recently installed a demo for a commercial Linux game, and the installer was made using Autopackage. This was my first encounter with it, and upon making the installer executable and double-clicking it, I was prompted with a terminal asking me if I want to download Autopackage. After it did download, I was then prompted with a box for the root password (twice - one for installing Autopackage and then once for installing the game). I admit that the interface was nice, it offered an explanation for why a password was needed, and had a box for "No password" to install as the user instead of system-wide. Good security precautions, just like installing a downloaded .deb asks for a password.

This all sounds nice for the average user who wants to install apps and games, but I have to agree with Henry Rayker about the security aspect. A unified packaging system will also make it easier for someone who desires to write a virus to do so. What's to stop someone from making a package that will install a Linux virus (if a credible and damaging one existed) using Autopackage and then emailing it or posting it on the web? With the recent rise in popularity of Ubuntu (and Linux in general), there are many more casual computer users who used to use Windows now using Linux. They are the ones that desire and are used to the "Next, Next, Next, Finish" style of installing apps. User discretion about security can no longer be taken for granted when you no longer have only security-conscious computer savvy users using Linux. Many of those same ex-Windows users are doing the OS installs themselves and have access to the root password because it's theirs, so it's just as easy for them to say "Hey what's this new game i just got in the email" and install it using Autopackage or the likes. 

I guess my point is that yes having a unified package system *can* be beneficial to Linux. But even if it ever is achieved, nobody can say for sure what kind of Pandora's box it'll open up in terms of security risks. Personally, I see nothing wrong with the way we install apps and I've never had problems with dependencies when using the repositories. Use apt / repositories whenever possible, compile from source as a 2nd alternative, or use a 3rd party installer if the first 2 options aren't possible (for example commercial apps or demos).

P.S. **cilynx** - I also prefer Debian's package management (one of a few reasons I won't use Fedora or SuSE), but RPM is not a dying breed. It is still alive and well, and recent efforts are under way to make it a unified RPM so that Red Hat, SuSE, and all their derivatives can use the same packages. Read it [here]("http://linuxhelp.blogspot.com/2006/12/rpm-to-be-revitalized-courtesy-of.html"). The article also mentions a desire for a unified packaging system, and makes a valid point that work is being repeated to package the same apps for every single distro.

---

### Post by hanzomon4 on 2006-12-26
When it comes to package management I prefer the Appdir approach of Mac OS and Rox. Basically AppDirs allow you to install and uninstall apps by just dragging a folder to your desktop or dragging them them to the trash. 

The autopackage maker has some good ideas on improving the Appdir approach and he makes a good case that improvement is needed. One goal is to make Appdirs installable over chats or the Internet by drag and drop. He gives more under the hood suggestions that I can't really explain with any intelligence, so I'll try and find the link to his page.  I like apt/synaptic but I don't think it helps desktop linux  when devs have to make 10 different linux packages for one app. Package management in linux is one of it's strong suits, but 10 ways to do the same thing in ways that make one way incompatible with the other 9 is very serious issue that must be addressed sooner or later

---

### Post by BoyOfDestiny on 2006-12-26
OK here is my reasoning.

I can install 40+ apps/packages + dependencies (automatically) on a whim in synaptic. When do I do this? Usually after a fresh install. They get updates and fixes automatically. If I upgrade the distro, ALL these apps are updated.

For things like wine and audacious, they offer debs for Ubuntu. Or you can add their 3rd party repo (System->Administration->Software Sources I find the most straight forward), and get them updated and installed automatically.

It's either through the update manager, synaptic, or a command or 2. Not everyone wants to go through the GUI (commandline is easier to automate-- works without needing X or a mouse), but the choice is good.

No manually visiting the page, no click next, click next, click next, click next unless you want it. Not to mention having to "guess" when your app is updated...

Downside?

If it's not the repos and there is no .deb for your distribution on the site, prepare to have to jump through hoops. 

So would I trade the convenience of keeping all these apps easily installed, reinstalled, removed, and updated (including security updates) hmm... Nope... 

Would things be easier if everyone used deb (IMHO) and same versions of particular distros and the same architecture... Yeah, but not likely... 

So one really great flexible package manager that is either compatible or incorporates all these features would do the trick... So yes, I think a unified package manager (smart? that someone mentioned) would be grand.

Do I think going to a page, picking and app, running an install that requires a GUI... Or to add and remove things manually via drag and drop... No thanks. The option is good, but to make it a "standard" I'll pass...

---

### Post by kripkenstein on 2006-12-26
msak007, I agree that there is a security issue here, and a serious one. Still, I think some method of 'easy-installation' is needed, because people really want it, they are used to it.

Autopackage is basically in the right direction - most programs, and nearly all shared libraries, are still managed by the distro's package management system; but Autopackage allows another option for things like game demos, frequently-updated software, etc. Now, if you set Autopackage up so that it installs those things only under user permissions, then some of the security issue is solved - I would like Autopackage to allow that as an option (i.e. that a system administrator sets up Autopackage so that it can't be used to install things on a system level).

Yes, it isn't a perfect solution, it's a compromise, but that is what I think is needed in this case. Ubuntu does release every 6 months, so packages are generally up-to-date; but sometimes people need even quicker updates - say, when gaim finally supports voice and video, I'll want to install it the same day ;) - and they shouldn't have to compile from the command line to get that, in my opinion.

---

### Post by hanzomon4 on 2006-12-26
What BoyOfDestiny posted is basically why I think the package management system is such an advantage over the Windows way. Having a single app that upgrades apps, applies security updates, and upgrades the whole OS takes the work out of keeping your system up-to-date. I just wish packages where compatible across distros, is that a goal of the LSB? If a dev just had to make one package  that was compatible with every linux distro I think we could get more folks porting apps to linux

---

### Post by ComplexNumber on 2006-12-26
[quote=cilynx]Being a Debian Junky for the last 10 years or so, I have to tout the wonders of the deb dependency resolution system. It is in my opinion far and away better than any other package manager in existance. Again in my opinion, rpm is a dying breed.[/quote] you couldn't be more wrong. deb(dpkg) doesn't have any dependency resolution, and neither does rpm. DEPENDENCY RESOLUTION IS HANDLED AT THE FRONT END (ie apt, urpmi, yum, smart).
you also got it wrong about rpm being "a dying breed". rpm is very much alive, and is almost certainly and inevitably the future of linux. conversely,  the only thing keeeping deb alive is ubuntu....and thats a fact.

i voted for "*Yes - it can be done and should be done"*

---

### Post by cilynx on 2006-12-27
ok, ok.  First let me clarify.  When I say .deb, I mean the entire Debian package management system.  When I say .rpm, I mean the entire RedHat package management system.  I am well aware that both .deb and .rpm files are just glorified tarballs with some metadata and that the various frontends do the resolution.  I feel that the Debian package management system is much more usable and powerful than any other.  This is only my opinion.

As for my opinion on rpm, it is my opinion.  I cannot be wrong about that.  Anyone can disagree with it, but it is still my opinion.

And I could be more wrong.  I could say that up is down and right is left.  That would be more wrong.  Feel free to disagree with me, but kindly don't attack my statements.  This elitest atitude from the community is one of the big things "normal" people have against the open source movement.

As for "the only thing keeping Debian alive", you can fight that on both sides.  If you look at the recent history of Debian, development dwindled when Ubuntu really took off.  Debian was founded on a theory of ethics.  Ubuntu is founded on a capitalist business model.  If you're a Debian developer, what drive do you have anymore when you know that your product is going to be reworked into something that no longer follows your philisophy and then the mangler is going to get all the credit?  My opinion is that Ubuntu has killed Debian.  It's not a fact.  It's my opinion.

EDIT: 

I think you were talking about the ".deb" format as opposed to Debian.  Sorry for the misunderstanding.  As for the .deb format, Debian is keeping the format going.  Ubuntu could easily change to anything else and repack all of the Debian packages that they steal.  Debian would still use .deb and Debian would still be used for serious systems.  All of that is pretty well water under the bridge however as there isn't any proof for any of your arguments or mine.  In my personal opinion, the Debian package management system is better than the RedHat package management system.  That's all I really have to say about that.  Feel free to disagree with me.

---

### Post by macogw on 2006-12-27
I'm not going to worry about the rest of the stuff since I think the repo system is easy (and if you look in Synaptic, adding repos is really simple), but regarding uninstall, Windows is terrible at that.  That's why there are Registry Cleaners.  Every app leaves behind some .dll's.  They are rarely cleaned up completely, and tend to leave lots of leftover crap.  That's why Windows chokes itself after a while.  All those apps you delete believing they are going all the way away, are still sort of there.  They clog it up and take up hdd space even after deleted.  At least with the apt-get way, pieces are only left behind if they are libraries being used by another program.

I'm not sure I'd call tarballs packages either.  They're just the source, they're not binaries.  I do think it'd be nice for there to be an alternate binary format that works for ALL of Linux.  There can be debs for us and rpms for RH users, but if there was a .lin that both could share, that'd be nice for people who don't want to have to build and package on both and for people who don't want to bother with alien.

---

### Post by highneko on 2006-12-27
> **samjh said:**
> I have been annually installing linux on my Windows PC for the past 3 years.  This is my third year trying linux, and my second year trying Ubuntu (my first trial was Red Hat).

IMHO, the one thing which really sets linux back from Windows in being accepted by non-technical people, is that there is no universal, easy-to-use software packaging and distribution system.

For Windows, you download a setup packages, and run it (usually named setup.exe, install.exe, or something to that effect).  Dependencies are usually fulfilled without a fuss.  Uninstallation is usually very clean these days.  Very easy and simple stuff.  Old software is very easy to update, and updates can be applied as soon as they are released.

But for linux, there are rpm, deb, tgz, and other packaging formats.  Updates are tied to the individual linux distro, and configuring repositories are a serious pain in the *** for those who don't know much about computers.  Then there is "dependency hell", which these days are even worse than Windows "DLL hell".

Should the linux community work toward a single, universal packaging format?  In this way, linux users can download updates directly from the publisher, without depending on repositories to update - a process that often takes months.  Like Windows, users merely download the setup file and run it to install.  If any needed files are missing, it can inform the user to install them, or even install them itself (users may even get an option to choose where the files are installed).  Like Windows, there would also be a universal package management software (eg. Add/Remove Packages), that can be used to perform a clean uninstall of the package, with the option to remove any unneeded dependencies.

I understand that because of the many distros that are available, along with the accompanying niggles of each one, the creation of a universal packaging format would be problematic.  But surely if the major distros like Ubuntu, SUSE, Fedora, and Debian, all combined their expertise, a universal packaging format could be created that will allow packages to be installed reliably on the vast majority of linux machines?

What does everyone think of this?

I hate downloading those annoying programs where they're trial software or something. One time I downloaded something to make a gif animation, and just as I closed it there was a very loud voice asking for money. Software is in many cases packaged with adware or maybe spyware. Even popular programs like winrar and deamon tools are having adware these days i think.

How is uninstalling easy in windows? You have to find your control panel link, find the uninstall programs thing, scroll around to find the program you wanna uninstall, and it's done, but in ubuntu it can be as simple as an apt-get remove program, or apt-get install program without all the spyware, serial number, trial, or registration stuff.

Windows does install things without a problem, but it's all crap programs. :3

Free software will rarely if ever give you a popup asking for money. I personally like everything about the debian packages.

---

### Post by 3rdalbum on 2006-12-27
Even though programmers can obviously compile their programs, they don't always feel like making binary packages. Check Sourceforge some time if you don't believe me. Having a unified package format would not change that. Plus, universally-binary packages are useless if you don't run 32-bit x86.

What we need is this: A graphical frontend for ./configure && make && sudo make install.  Has anyone else used the XFCE 4.2 graphical installer? It's got a GUI that looks a lot like one of those Windows-based installers, but it compiles everything from source code. If we had a generic source installer like that, which had links to the package management systems to allow for dependency resolution and the creation of Debian packages using Checkinstall, that would be brilliant. It would be as easy to use as a binary Windows installer or a Debian package, but it would work over multiple arches and have the flexibility of a normal package.

---

### Post by Extreme Coder on 2006-12-31
What Autopackage should aim to be is the 'bridge' between software installation and linux distributions. It would be much easier and better if Autopackage implements installation support for current Linux distibutions (like package integration, menu and dependency checking stuff...) and then the software provider would just provide one .autopackage. I'm all for the autopackage idea, as long as it is implemented correctly.

Come to think of it, I think the whole Linux software installation problem is caused by RPM. I mean, you have to provide different RPM packages for different RPM distributions? That's just... bad. I hope the same thing doesn't happen with Debian and Ubuntu as they grow... Ubuntu gets most of its packages from Debian, doesn't it?

---

### Post by Sef on 2006-12-31
> Ubuntu gets most of its packages from Debian, doesn't it?

Yes, it does.

---

### Post by Choad on 2007-03-19
the unified linux thread is massive and there are many good reasons for not having 1 single linux distro, but i cant think of a reason why we shouldnt all use the same package manager

who cares if its .deb or .rpm or anything else or an entirely new one, there is just no need whatsoever to have a half dozen package managers as far as i can see.

obviously, this is never going to happen, due to peoples pride in their distribution of choice.

it would make distributing apps so much easier if there was a reliable way of packaging up your app, including dependencies and whatnot. i dont think .deb is that good to be honest, at least not the ubuntu way. i mean often people have to release a different .deb for dapper, feisty, edgy as well as a different one for debian it's self. so that is a bit completely crap really.

opinions?

---

### Post by Crashmaxx on 2007-03-19
Its not that simple, .deb's are just binaries of the package compiled for specific settings. They may only work for a specific environment that is the same as the one they are made in. Different apps have different dependencies and options so some make more portable .deb's then others. So that is why even .deb's aren't universal.

Many distros don't use binaries. Every user just gets the source and compiles it themselves for their specific system and options. Some of these have their own package managers, and some still just leave it all for the user to figure out. So no one using a source based distro would ever even consider using a .deb or anything similar.

And .rpm's are their own beast that I've never dealt with. I don't know much about them, but for a time they were the closest thing to a unified package you could ask for.

In the end though, anything that is open source is pretty much universal. Its just a matter if anyone has compiled a .deb for you are not. But if you are willing to compile it yourself, then there is very little that you can't use. And you can even make your own .deb's using check install, which does make them easier to manage.

So I hope you understand now that it is not a matter of pride. It is just a choice we are all free to make, and packages for linux are source compatible and not binary compatible like windows.

---

### Post by DoctorMO on 2007-03-19
Package managers are not the same as packagers.

---

### Post by Choad on 2007-03-19
> 
Its not that simple, .deb's are just binaries of the package compiled for specific settings. They may only work for a specific environment that is the same as the one they are made in. Different apps have different dependencies and options so some make more portable .deb's then others. So that is why even .deb's aren't universal.

specific settings? i am not sure what you mean here. i understand that one compiled for 686 will not work with a 386 processor (and obviously x86/x86_64/ppc are all different), but that doesnt mean you cant simply release it for the lowest common denominator. it works for windows, does it not?

other than that i can see no reason why one package should not in theory be able to work on any linux operating system, so long as it's dependencies are met.

the fact is that (for example) deluge is packaged in half a dozen different ways, which is a lot of work for the devs, and *STILL* it only is available for a handful of distros. this is completely insane. it is not beyond the ingenuity of man to create a single package management system that can be implemented in all OS's

as for all the distros that dont use binary, well they are hardly relevant. its not like the source code would suddenly disappear is it?

as for rpm's being "their own beast" well that is entirely my point. i have used them, and they do the same job as .debs. they install binary packages in to the system and try (badly) to make sure dependencies are met. it does nothing that deb doesnt do (apart from work reliably), and visa versa. 

if it's not a matter of pride, then what is it? what valid technical reason is there for suse and redhat to keep using rpm when deb is more reliable? 

i would love to see the freedesktop.org people invent a package standard that could replace everything else.

---

### Post by SishGupta on 2007-03-19
There is already a type of unified package.
[http://www.autopackage.org/](http://www.autopackage.org/)

---

### Post by Choad on 2007-03-19
i suppose that is kinda in the right direction, but i dont think it is sophisticated enough to maintain an entire distribution, and it installs things in wierd directories/menus

---

### Post by DoctorMO on 2007-03-19
> it works for windows, does it not?

Hahahahaha! yes and then again no, the more generic the package the slower it'll run, it'll also stop you from using different compiled libs which is prevent in distro's.

Please empty your head of windows world quo's because they don't work in a community driven and open source world.

---

### Post by Adamant1988 on 2007-03-19
I see no reason to unify package management.   Different distributions will use different approaches to package management, they'll use what works best for the niche they fill.  A perfect example of this is CNR (which will be available for Ubuntu soon as I understand it), it fills a very specific niche for the new user.   Now, I do agree that standards need to be made (to an extent) but let distributions use the appropriate tool for the job without harassing them about it.

Also, I haven't seen any hard conclusive evidence to say that .rpm/.deb is more reliable than the other, besides personal preference.   It's my understanding that a lot of the hard feelings between the package managers comes from times past and aren't really relevant today.

---

### Post by Choad on 2007-03-19
> **Adamant1988 said:**
> I see no reason to unify package management.   Different distributions will use different approaches to package management, they'll use what works best for the niche they fill.  A perfect example of this is CNR (which will be available for Ubuntu soon as I understand it), it fills a very specific niche for the new user.   Now, I do agree that standards need to be made (to an extent) but let distributions use the appropriate tool for the job without harassing them about it.

Also, I haven't seen any hard conclusive evidence to say that .rpm/.deb is more reliable than the other, besides personal preference.   It's my understanding that a lot of the hard feelings between the package managers comes from times past and aren't really relevant today.
ok heres 1 reason

suppose macradobe wanted to release dreamweaver for linux. are they expected to package 25 different versions of it? because that isnt going to happen in this life time. or are they expected to release the source? because thats not going to happen either?

the only thing they can do at the moment is make some hackish blob that breaks the dependencies used in the system.

your example of CNR is just another example of why we need a unified package manager. we certainly dont want CNR, a technology owned by a single company to become a standard. ok, its nice to use for the newbies (maybe?) but its hardly a viable long term solution is it?

different distributions use different approaches to package management? really? coz i thought they all did the same thing: install binary apps and make sure dependencies are met.

im not trying to stip up hard feelings at all, im just interested in this debate... i have yet to hear any real reason why not to unify the packaging  of linux binaries.

---

### Post by Choad on 2007-03-19
> **DoctorMO said:**
> Hahahahaha! yes and then again no, the more generic the package the slower it'll run, it'll also stop you from using different compiled libs which is prevent in distro's.

Please empty your head of windows world quo's because they don't work in a community driven and open source world.
ok so lets suggest that program y distributes various x86 versions to compensate for this

as it stands they need to release y * x * z different versions, where y is the program, x is the architecture and z is all the package types used in all the distros

z is probably at least 10 as it stands. it should, imo, be 1

---

### Post by aysiu on 2007-03-19
Turns out there were a whole bunch of threads on this topic, so to give some continuity to the discussion, I've merged them. I've attached screenshots of the old polls.

---

### Post by Adamant1988 on 2007-03-19
> **Choad said:**
> ok heres 1 reason

suppose macradobe wanted to release dreamweaver for linux. are they expected to package 25 different versions of it? because that isnt going to happen in this life time. or are they expected to release the source? because thats not going to happen either?

the only thing they can do at the moment is make some hackish blob that breaks the dependencies used in the system.

your example of CNR is just another example of why we need a unified package manager. we certainly dont want CNR, a technology owned by a single company to become a standard. ok, its nice to use for the newbies (maybe?) but its hardly a viable long term solution is it?

different distributions use different approaches to package management? really? coz i thought they all did the same thing: install binary apps and make sure dependencies are met.

im not trying to stip up hard feelings at all, im just interested in this debate... i have yet to hear any real reason why not to unify the packaging  of linux binaries.

I expect that the distributions will make it worth the ISV's time to support their distribution.

---

### Post by prizrak on 2007-03-19
I just installed NetBeans from the official website. It was a .bin file that had to be chmoded to +x and then run with sudo to install. I even got a menu entry. I did the same thing with RealPlayer about a week earlier. Yes it would be nice to have a universal packager but not as critical as you might think. Also LSB .rpm's don't seem to have any problem being alien'ed into Ubuntu. Maybe a little redesign fo gdebi that would allow double clicking them to install is all it would take. Better yet a Synaptic redesign that would allow it to double click install local files and search for dependancies in repos.

---

### Post by Choad on 2007-03-19
@adamant 

...ooookay

and how exactly does one go about doing that? commercial companies listen to 1 thing: money.

put yourself in macradobe's shoes... or any generic game studio... what advantages are there in releasing their software for linux? a comparitively small userbase (read: not much money) and an absolute nightmare to support (read: lots of money). having a standard packaging solution, with a standard method of determining dependencies will cut out a *very* large portion of the hassle. not to mention it would make free software easier to install as well.

---

### Post by Choad on 2007-03-19
> **prizrak said:**
> I just installed NetBeans from the official website. It was a .bin file that had to be chmoded to +x and then run with sudo to install. I even got a menu entry. I did the same thing with RealPlayer about a week earlier. Yes it would be nice to have a universal packager but not as critical as you might think. Also LSB .rpm's don't seem to have any problem being alien'ed into Ubuntu. Maybe a little redesign fo gdebi that would allow double clicking them to install is all it would take. Better yet a Synaptic redesign that would allow it to double click install local files and search for dependancies in repos.
with your installing of a .bin file you have now broken apt-get. ideal? methinks not

if you now installed netbeans from synaptic, it would install over the old things with no regard and you'd probably end up with a dozen conflicts causing instability.

---

### Post by Adamant1988 on 2007-03-19
> **Choad said:**
> @adamant 

...ooookay

and how exactly does one go about doing that? commercial companies listen to 1 thing: money.

put yourself in macradobe's shoes... or any generic game studio... what advantages are there in releasing their software for linux? a comparitively small userbase (read: not much money) and an absolute nightmare to support (read: lots of money). having a standard packaging solution, with a standard method of determining dependencies will cut out a *very* large portion of the hassle. not to mention it would make free software easier to install as well.

The way things are going, some companies will support "Red Hat", other companies will support "SuSE" and other companies will support "Ubuntu".   They'll limit what they support, if money is the issue then obviously making it worth their time to support Xdistribution involves showing that it will be profitable for them.

---

### Post by Choad on 2007-03-19
> **Adamant1988 said:**
> The way things are going, some companies will support "Red Hat", other companies will support "SuSE" and other companies will support "Ubuntu".   They'll limit what they support, if money is the issue then obviously making it worth their time to support Xdistribution involves showing that it will be profitable for them.
and how is that in any way a good thing? is this not something that should be avoided at all costs?

ever heard the phrase "united we stand, devided we fall"?

---

### Post by Adamant1988 on 2007-03-19
> **Choad said:**
> and how is that in any way a good thing? is this not something that should be avoided at all costs?

ever heard the phrase "united we stand, devided we fall"?

No, it's not something that should be avoided, necessarily.  If a package is optimized for a system it's going to work better on it, right? Now, let's say that XYZ company releases software that's really only relevant to the server market, each distribution is different meaning it's going to run differently on each distro.  You tell me how XYZcompany is supposed to support that many distributions? supporting single distributions with their software means that they can actually manage to support it.

---

### Post by Choad on 2007-03-19
> **Adamant1988 said:**
> No, it's not something that should be avoided, necessarily.  If a package is optimized for a system it's going to work better on it, right? Now, let's say that XYZ company releases software that's really only relevant to the server market, each distribution is different meaning it's going to run differently on each distro.  You tell me how XYZcompany is supposed to support that many distributions? supporting single distributions with their software means that they can actually manage to support it.

so if "3rd part server prog a" chooses to back redhat, and "3rd party server prog b" chooses to back debian, how is this advantageous to the linux community? its would just end up in a horrible mess, or alternatively a homogenous environment which is something we do not want. the flexibility of linux should be made to be an advantage, not a disadvantage.

> each distribution is different meaning it's going to run differently on each distro. You tell me how XYZcompany is supposed to support that many distributions?

isnt that the whole point of this debate? this is me (us) saying *this* is how we make it possible for a company to support linux generically, instead of a single distribution. each distribution has differences, but they have more similarities than differences. they all run the same kernel, same libraries, just different versions and combinations of the kernel and libraries. thats the only difference. if distribution x chooses to use a non-standard kernel or library then it is legitimately the distributions fault for breaking the compatibility. but assuming the distribution uses a standard build of version x kernel and version y library, then a program that depends on version_a > kernel > version_b and version_c > library > version_d *will* work so long as the program is installed correctly and linked to the libraries it needs. this is where the package manager comes in.

but i digress

i have still yet to hear a single disadvantage to a unified packaging system.

---

### Post by Adamant1988 on 2007-03-19
> **Choad said:**
> isnt that the whole point of this debate? this is me (us) saying *this* is how we make it possible for a company to support linux generically, instead of a single distribution. each distribution has differences, but they have more similarities than differences. they all run the same kernel, same libraries, just different versions and combinations of the kernel and libraries. thats the only difference. if distribution x chooses to use a non-standard kernel or library then it is legitimately the distributions fault for breaking the compatibility. but assuming the distribution uses a standard build of version x kernel and version y library, then a program that depends on version_a > kernel > version_b and version_c > library > version_d *will* work so long as the program is installed correctly and linked to the libraries it needs. this is where the package manager comes in.

but i digress

i have still yet to hear a single disadvantage to a unified packaging system.

They do NOT run the same kernel.  Does Ubuntu not hack their kernels?  Does Fedora not hack their kernels? How many distributions can you name that actually don't touch their kernels before release? 

You say you want a disadvantage to a unified package management system with forced standards... Well, let's start at how much trouble it would be to actually make that happen.  First you have to come to an agreement within a majority of distributions, and then they ALL have to implement the new package manager.  That's a lot of unnecessary work to fix a problem that really isn't *that* big of a deal.  Support would still be a nightmare even with a unified package manager.  What you're wanting is a unified distribution. 

So what you're saying is that ISV's just need to force a standard on the Linux community, awesome.  There does *not* need to be a unified package management scheme, it's just a hope..  Even so RPMs for SuSE are different than RPMs for Fedora, so different versions of the packages would have to be made anyway.

---

### Post by Choad on 2007-03-19
> **Adamant1988 said:**
> They do NOT run the same kernel.  Does Ubuntu not hack their kernels?  Does Fedora not hack their kernels? How many distributions can you name that actually don't touch their kernels before release? 

You say you want a disadvantage to a unified package management system with forced standards... Well, let's start at how much trouble it would be to actually make that happen.  First you have to come to an agreement within a majority of distributions, and then they ALL have to implement the new package manager.  That's a lot of unnecessary work to fix a problem that really isn't *that* big of a deal.  Support would still be a nightmare even with a unified package manager.  What you're wanting is a unified distribution. 

So what you're saying is that ISV's just need to force a standard on the Linux community, awesome.  There does *not* need to be a unified package management scheme, it's just a hope..  Even so RPMs for SuSE are different than RPMs for Fedora, so different versions of the packages would have to be made anyway.
well maybe that's something that needs to be worked out then. maybe it would force the distro's to merge upstream or choose not to mod the kernel.

also, theres nothing to say it couldnt have an advanced verisoning system. for example version 2.x.x+nvidia+random_hack 

and even so, its still not a disadvantage to a unified packaging system. its a hurdle to overcome for closed source vendors, but it would no doubt be made easier by having a unified packaging system

and where on earth did i say that isv's are forcing the standard. it should be a freedesktop/lsb standard.

and nowhere did i say i wanted a unified distribution. in fact i said the exact opposite in my last post.

and coming to an agreement with all the distros... it would be an effort yes, but the end result would be technologically superior. isnt that what the whole freedesktop.org/lsb thing is all about? and they dont ALL have to do ANYTHING. only if they want to be standards compliant. it would be a gradual shift most likely, but it would be a shift in the right direction. and as it gains momentum we would see the benifits emerge

---

### Post by Adamant1988 on 2007-03-19
> **Choad said:**
> well maybe that's something that needs to be worked out then. maybe it would force the distro's to merge upstream or choose not to mod the kernel.

also, theres nothing to say it couldnt have an advanced verisoning system. for example version 2.x.x+nvidia+random_hack 

and even so, its still not a disadvantage to a unified packaging system. its a hurdle to overcome for closed source vendors, but it would no doubt be made easier by having a unified packaging system

and where on earth did i say that isv's are forcing the standard. it should be a freedesktop standard.

Those kernel mods are how you get a lot of great stuff in the kernel, they get sent back upstream to be included in later versions.   The major disadvantage to your unified package manager (UPM for short) is that it would be a complete waste of time to implement, tons of work for minimal gain.  

You want Linux to be treated as a single platform, understandable, but not really going to happen.. the diversity is what allows it to grow so fast., don't try to kill that with your UPM. 
I saw first hand the AMAZING leaps forward that Linux had made when I left for 4 years or so and then came back to Linux, it's developing so quickly that it's scary and that's because of the diversity.  Just let ISV's support whatever distro is targeting the same market as them...


What you're pushing is a unified distribution, the differences between distros will boil down to a choice in desktop environment.  Just leave it be.

I'm not going to argue this anymore.  This whole argument reminds me of my sister's current relationship.  She's completely blind to this guy's flaws and refuses to acknowledge that they exist, she's love-blind.  Well, you're about the same way with this idea, give it time, you'll come to your senses.

---

### Post by Choad on 2007-03-19
> **Adamant1988 said:**
> Those kernel mods are how you get a lot of great stuff in the kernel, they get sent back upstream to be included in later versions.   The major disadvantage to your unified package manager (UPM for short) is that it would be a complete waste of time to implement, tons of work for minimal gain.  

You want Linux to be treated as a single platform, understandable, but not really going to happen.. the diversity is what allows it to grow so fast., don't try to kill that with your UPM. 
I saw first hand the AMAZING leaps forward that Linux had made when I left for 4 years or so and then came back to Linux, it's developing so quickly that it's scary and that's because of the diversity.  Just let ISV's support whatever distro is targeting the same market as them...


What you're pushing is a unified distribution, the differences between distros will boil down to a choice in desktop environment.  Just leave it be.

I'm not going to argue this anymore.  This whole argument reminds me of my sister's current relationship.  She's completely blind to this guy's flaws and refuses to acknowledge that they exist, she's love-blind.  Well, you're about the same way with this idea, give it time, you'll come to your senses.
ok i edited that last post about 6 times u might wanna read again.

i dont want linux to be treated as a single platform. what i want (now listen carefully) is a universal *package* manager. 

im sorry if i come off as patronising, but its not that hard to grasp. it is also not that hard to implement. all that is needed is a standard to be written. then its just a matter of writing the packaging tools, creating a gtk/qt/cli frontend, and waiting for the distro's to start accepting it.

which leads me back to my very first post "of course this will never happen because of people being proud of their distro". whether it's pride or whether its "cant be bothered because my one works as it is" is basically irrelevant. the end result would be a system as good, if not better for what we do now with our separate package managers, except packages would not have to be bundled separately for each distro, and there would be a much greater chance of getting 3rd party support for 3rd party programs.

now i hate to sound like a broken record, but where is the disadvantage of a UPM? other than the 1 time effort of converting in the first place which is short term and shouldnt really be taken in to the equation.

> This whole argument reminds me of my sister's current relationship.  She's completely blind to this guy's flaws and refuses to acknowledge that they exist, she's love-blind. well thanks for that wonderfully patronising analogy, but you have presented no flaws for me to be blind to. other than what i have written above re the one time effort.

---

### Post by Adamant1988 on 2007-03-19
> **Choad said:**
> ok i edited that last post about 6 times u might wanna read again.

i dont want linux to be treated as a single platform. what i want (now listen carefully) is a universal *package* manager. 

im sorry if i come off as patronising, but its not that hard to grasp. it is also not that hard to implement. all that is needed is a standard to be written. then its just a matter of writing the packaging tools, creating a gtk/qt/cli frontend, and waiting for the distro's to start accepting it.

which leads me back to my very first post "of course this will never happen because of people being proud of their distro". whether it's pride or whether its "cant be bothered because my one works as it is" is basically irrelevant. the end result would be a system as good, if not better for what we do now with our separate package managers, except packages would not have to be bundled separately for each distro, and there would be a much greater chance of getting 3rd party support for programs.

now i hate to sound like a broken record, but where is the disadvantage of a UPM? other than the 1 time effort of converting in the first place which is short term and shouldnt really be taken in to the equation.

Ok, let me spell this out. 

You want 1 package manager, right?  1 format, that's it? 

Ok, so this means ISV's would have to produce 1 single package for Linux in general, right? 
Does this not effectively turn Linux into one platform instead of a lot of smaller ones?  Also, the process of changing the package manager in every single distribution would probably be a lot more extensive than you think , and hardly short term. 

It has nothing to do with pride friend, it's "Why should I?"  Why should Red Hat conform to your single package manager? It doesn't benefit them at all, you would be putting a lot of unneeded strain on them and in the end they would refuse to use it.   That's the point, it *won't* happen.

Different distributions meet different needs, and XYZcompany is going after the same market as Xdistribution, why waste time supporting the other 150+ distributions when that one distribution will give you the exposure you need?

---

### Post by Choad on 2007-03-19
> **Adamant1988 said:**
> Ok, let me spell this out. 

You want 1 package manager, right?  1 format, that's it? 

Ok, so this means ISV's would have to produce 1 single package for Linux in general, right?  not just isv's but the whole open source world

> Does this not effectively turn Linux into one platform instead of a lot of smaller ones?
](*,)  no no no no no no no no no no no no no no no and no

>  Also, the process of changing the package manager in every single distribution would probably be a lot more extensive than you think , and hardly short term. im not denying that it would be hard, but it is short term. as in, you do it once.

> It has nothing to do with pride friend, it's "Why should I?"  Why should Red Hat conform to your single package manager? It doesn't benefit them at all, again, exactly what i am trying to say here. it would benefit them if 3rd parties started distributing through this UPM, and more importantly it wouldnt DISADVANTAGE them in any way  > you would be putting a lot of unneeded strain on them and in the end they would refuse to use it. what? where? what strain? after the initial overhaul it would be as easy, if not easier (due to the package manager being written from scratch with all the lessons learned from current package managers) than what they use at the moment


> Different distributions meet different needs, and XYZcompany is going after the same market as Xdistribution, why waste time supporting the other 150+ distributions when that one distribution will give you the exposure you need?
what about games? im sure there are well over 100 desktop oriented linux distros.


and remember, its not neccessarily just about the ISV's its about having interoperability between linux OS's generally. i love the repositories, its great, but it only works for so many things. they cant go on hosting every program forever. its not sustainable. especially if ubuntu/linux got the kind of popularity of windows. we'd have to move to a windows-esque "go to the product's site and download an installer" type scenario. as it stands, joe user cant do this. if he's lucky there will be a version for his build of his distro (if its opensource) but more likely he will be left stuck.

---

### Post by saulgoode on 2007-03-19
> **Choad said:**
> im sorry if i come off as patronising, but its not that hard to grasp. it is also not that hard to implement. all that is needed is a standard to be written. then its just a matter of writing the packaging tools, creating a gtk/qt/cli frontend, and waiting for the distro's to start accepting it.

So it is your belief that it would be "not that hard to implement" a package manager that would be cognizant of all the variations of the different distributions and be capable of installing a single binary that functions regardless of which kernel version, device implementation, glib version, X11 version, and sound system is installed? [1]

How do you expect for a package manager to account for such differences? Unless you can solve this, what you are talking about is only feasible within the context of a unified Linux; they are one and the same.


[1] Not too mention other dependencies such as graphics toolkits, font rendering, compositing engines, printing system, database handling, network interfacing, interprocess communication, et alia.

---

### Post by Choad on 2007-03-19
> **saulgoode said:**
> So it is your belief that it would be "not that hard to implement" a package manager that would be cognizant of all the variations of the different distributions and be capable of installing a single binary that functions regardless of which kernel version, device implementation, glib version, X11 version, and sound system is installed? [1]

How do you expect for a package manager to account for such differences? Unless you can solve this, what you are talking about is only feasible within the context of a unified Linux; they are one and the same.


[1] Not too mention other dependencies such as graphics toolkits, font rendering, compositing engines, printing system, database handling, network interfacing, interprocess communication, et alia.
isnt that exactly what .deb does atm?

if the package manager registers which version of what is used... its just a giant mySQL database.

---

### Post by smbm on 2007-03-19
> **Choad said:**
> isnt that exactly what .deb does atm?

My knowledge on the matter is pretty limited but it occurs to me that this isn't what .debs do at the moment. You have different .debs for Dapper, Edgy, Feisty etc.

---

### Post by Choad on 2007-03-19
> **smbm said:**
> My knowledge on the matter is pretty limited but it occurs to me that this isn't what .debs do at the moment. You have different .debs for Dapper, Edgy, Feisty etc.
well ok, isnt this what debs are *supposed* to do :p:

iirc ubuntu got a bit of flack from debian for breaking compatibility with debs.

and oh look! another reason for an improved package manager :rolleyes:

---

### Post by 23meg on 2007-03-19
Anyone heard of Smart?

[http://labix.org/smart](http://labix.org/smart)

---

### Post by smbm on 2007-03-19
> **Choad said:**
> well ok, isnt this what debs are *supposed* to do :p:

iirc ubuntu got a bit of flack from debian for breaking compatibility with debs.

and oh look! another reason for an improved package manager :rolleyes:

Perhaps they are supposed to. I've never had too many problems though. You can always compile/checkinstall etc if you don't want to break apt. 

Perhaps (and I say this respectfully and without being sarcastic or condescending in any way) you should start learning to code and write the aforementioned software/standard and lobby all the distros yourself. Get the ball rolling. That's the beauty of open source I guess.

---

### Post by aysiu on 2007-03-19
> **23meg said:**
> Anyone heard of Smart?

[http://labix.org/smart](http://labix.org/smart)
There's a brief discussion about Smart around [post #530 of this thread](http://ubuntuforums.org/showthread.php?p=1344294#post1344294).

---

### Post by saulgoode on 2007-03-19
> **Choad said:**
> well ok, isnt this what debs are *supposed* to do :p:


So Macrodobia doesn't need to worry about whether the system its Flash player is being installed on is using i386/x86_64/PowerPC/ARM, OSS/ALSA/Arts, or GTK/QT/FLTK, V4L./V4L2, SSL/TLS, GStreamer/Arts/ESD, SCIM/XIM/UIM ?  All that is necessary is to put their player in a .deb and everything will work just fine? 

Package management doesn't make any of the above decisions and if it were to attempt to do so, the result would still be that Macrodobia would need to generate binary packages supporting the different alternatives. Unless you restrict the options offered (i.e., a unified Linux), unified package management produces no benefit. (And restricting options for improved interoperability is the point of distributions.)

---

### Post by Choad on 2007-03-19
> **smbm said:**
> Perhaps they are supposed to. I've never had too many problems though. You can always compile/checkinstall etc if you don't want to break apt. 

Perhaps (and I say this respectfully and without being sarcastic or condescending in any way) you should start learning to code and write the aforementioned software/standard and lobby all the distros yourself. Get the ball rolling. That's the beauty of open source I guess.
indeed i would, and i will should i get the skills, but i think something this fundamental needs the collaboration of the greatest linux minds, not some newb hacker on a one man mission.

as far as i can see... it would involve a specification for a mySQL database, a specification for how programs (as in programs that help install and uninstall things) should interact with the database, and a specification for the packages themselves and how they should list their dependencies. the packages could probably consist of an xml file detailing what things are required and what things conflict with it, and also detailing where the files should be installed, along with the actual files of the program, and the whole thing wrapped in a container format.

the actual programs that install things could be written by whoever using whatever gui so long as they adhere to the specification. in fact, it could even be possible to extend the functionality of apt-get to handle files in said specification. (tho perhaps not ideal, it would ease the transition)

---

### Post by Choad on 2007-03-19
> **saulgoode said:**
> So Macrodobia doesn't need to worry about whether the system its Flash player is being installed on is using i386/x86_64/PowerPC/ARM, OSS/ALSA/Arts, or GTK/QT/FLTK, V4L./V4L2, SSL/TLS, GStreamer/Arts/ESD, SCIM/XIM/UIM ?  All that is necessary is to put their player in a .deb and everything will work just fine? 

Package management doesn't make any of the above decisions and if it were to attempt to do so, the result would still be that Macrodobia would need to generate binary packages supporting the different alternatives. Unless you restrict the options offered (i.e., a unified Linux), unified package management produces no benefit. (And restricting options for improved interoperability is the point of distributions.)

i386 x86_64 PowerPC ARM  - all of these are issues as it stands, even on windows. obviously they would have to release a different version for a different architecture.

 OSS/ALSA/Arts, or GTK/QT/FLTK, V4L./V4L2, SSL/TLS, GStreamer/Arts/ESD, SCIM/XIM/UIM - every single one of these are programs, and as such would be registered in the package manager as installed or not installed, and as such it would install/not install depending on whether the dependencies are met or not. so in effect, yes, macradobe doesnt have to worry about that.

---

### Post by smbm on 2007-03-19
> OSS/ALSA/Arts, or GTK/QT/FLTK, V4L./V4L2, SSL/TLS, GStreamer/Arts/ESD, SCIM/XIM/UIM

Again I'm no expert but adapting to all this would probably require recompilation. Am I wrong?

---

### Post by Choad on 2007-03-19
> **smbm said:**
> Again I'm no expert but adapting to all this would probably require recompilation. Am I wrong?
well not really no

they'd choose to go (say) the gnome route, and use gtk, gstreamer (which in turn uses alsa i believe) and so on, and then if the end user tried to install it on a kde system it would say "im sorry, cant install it on this system"

it would then depend on how advanced the package manager is as to whether it would offer to install the dependencies for the user. but that is relatively unimportant. its the underlying framework for handling packages and their dependencies that i believe should be unified

---

### Post by smbm on 2007-03-19
> **Choad said:**
> well not really no

they'd choose to go (say) the gnome route, and use gtk, gstreamer (which in turn uses alsa i believe) and so on, and then if the end user tried to install it on a kde system it would say "im sorry, cant install it on this system"

it would then depend on how advanced the package manager is as to whether it would offer to install the dependencies for the user.

It may be my short sightedness but I can't understand how that would be an improvement (at least from my own computing perspective).

Surely Synaptic does this. Also double clicking on a .deb opens gdebi which seems to always install dependencies correctly for me. 

Are you suggesting that other distros adopt .deb?

---

### Post by Choad on 2007-03-19
> **smbm said:**
> It may be my short sightedness but I can't understand how that would be an improvement (at least from my own computing perspective).

Surely Synaptic does this. Also double clicking on a .deb opens gdebi which seems to always install dependencies correctly for me. 

Are you suggesting that other distros adopt .deb?
synaptic does do this, you're right, and having all distro's move to .deb *would* be an improvement. 

but i cant see that happening somehow. to much pride. 

it would be little extra effort to create a new format (even one heavily influenced by current formats) that way nobody feels they're conceding to another distro. as long as it is accepted by the lsb/freedesktop.org, it really doesnt matter. 

and dont get me wrong, it would be very possible to make it just as easy as clicking a (correct) .deb is in ubuntu. it wouldnt have to be that easy tho... if you get me. there could be a half dozen front ends that handle varying amounts of auto-fetching application dependencies for you. ubuntu, being user friendly, would roll out a front end that tries its best to do everything for you.

---

### Post by hanzomon4 on 2007-03-19
Dude you're looking for a solution to a problem faced by closed source developers and trying to remedy this problem on the linux/distro side. 

That's unnecessary in my view. Don't change the packages favored by xyz distro... just develop a package closed source developers can use for their releases. I would suggest they use appdirs such as [klik]("http://klik.atekon.de/") or rox-style application directories. 

Why? 

Because there is no way to standardize the libs, and versions of those libs, used by the various distros. Appdirs, or bundles, include all of the dependences  in the applications directory. This would suck as a format to build or maintain a distro with but for the closed apps(adobe photoshop?) such a format would prove useful.

Klik's main issue is that the .cmg file is loop-mounted as a disk image. This limits the amount of kliks apps that can run at the same time to 8. However the klik team is working with fuse to do away with this limit. 

.cmg is like .app on Macs and don't interfere with a distros base system. uninstalling .cmg's is simple, just delete it. 

Again the package management of linux is a strength, i.e. don't screw with a good thing.  Giving a platform independent way to packaging the odd app is cool, just don't push this job on the backs of the distros.

---

### Post by saulgoode on 2007-03-19
> **Choad said:**
> OSS/ALSA/Arts, or GTK/QT/FLTK, V4L./V4L2, SSL/TLS, GStreamer/Arts/ESD, SCIM/XIM/UIM - every single one of these are programs, and as such would be registered in the package manager as installed or not installed, and as such it would install/not install depending on whether the dependencies are met or not. so in effect, yes, macradobe doesnt have to worry about that.

Actually, those are all libraries and provide alternatives for a program to access system resources. Adobe could not produce a Linux program without deciding which combination of those alternatives they wish to use.

A universal package manager not only must handle which libraries are present, but would also have to be aware of variations in architectures, versions, and compile-time options of those different libraries. 

> **Choad said:**
> they'd choose to go (say) the gnome route, and use gtk, gstreamer (which in turn uses alsa i believe) and so on, and then if the end user tried to install it on a kde system it would say "im sorry, cant install it on this system"

Let's say that the serendipitous event occurs that my system currently satisfies all of the requirements of Adobe's Flash program. Now let's say my distribution decides the next release should update GTK+ from version 2.4 to 2.10. Guess what? Flash will not work because the two versions are not binary compatible. Of course, the Open Source programs have no problem because GTK+ 2.4 and 2.10 ARE source compatible and my distro's developers would be recompiling the programs anyway. (This is an example, I have not installed Flash and do not know how they handle GTK+ dependencies; that is their problem, not mine.)

Even if you solve the problem of support for a third party binary *today*, your solution will only work tomorrow if the ABIs are not permitted to change. By the time of your distro's next release, your unified package system will most likely be generating "im sorry" messages for every third party binary that does not release an update and all of your efforts will have been for naught.

> **Choad said:**
> synaptic does do this, you're right, and having all distro's move to .deb *would* be an improvement. 

but i cant see that happening somehow. to much pride.

I don't see where there would be an improvement. The fact that a project is packaged as a .deb doesn't mean it will work in Ubuntu. It only means it is in a .deb package. The underlying issues of installation baselines still exists (and based on the fact that Synaptic will install Debian packages on Ubuntu -- yet they don't work -- would indicate quite clearly that dependency verification is a lot harder than you suggest).

---

### Post by prizrak on 2007-03-19
> **Choad said:**
> with your installing of a .bin file you have now broken apt-get. ideal? methinks not

if you now installed netbeans from synaptic, it would install over the old things with no regard and you'd probably end up with a dozen conflicts causing instability.

Mmm.... no actually I do not. The software is installed in /opt. It has an unistaller included with it. If it somehow becomes available in the repos for one I don't see it overwriting any of my settings (no software I have seen so far in the repos does) for two it's easy enough to run an unistaller. Adobe distributes Flash to all distro's, some even package it themselves (Ubuntu for instance). nVidia distributes a unified driver for all distros. Point is that while it would be very nice to have a universal package installer it isn't nearly as much of a problem as you think it is.

---

### Post by Choad on 2007-03-19
> **saulgoode said:**
> Actually, those are all libraries and provide alternatives for a program to access system resources. Adobe could not produce a Linux program without deciding which combination of those alternatives they wish to use.

A universal package manager not only must handle which libraries are present, but would also have to be aware of variations in architectures, versions, and compile-time options of those different libraries. 



Let's say that the serendipitous event occurs that my system currently satisfies all of the requirements of Adobe's Flash program. Now let's say my distribution decides the next release should update GTK+ from version 2.4 to 2.10. Guess what? Flash will not work because the two versions are not binary compatible. Of course, the Open Source programs have no problem because GTK+ 2.4 and 2.10 ARE source compatible and my distro's developers would be recompiling the programs anyway. (This is an example, I have not installed Flash and do not know how they handle GTK+ dependencies; that is their problem, not mine.)

Even if you solve the problem of support for a third party binary *today*, your solution will only work tomorrow if the ABIs are not permitted to change. By the time of your distro's next release, your unified package system will most likely be generating "im sorry" messages for every third party binary that does not release an update and all of your efforts will have been for naught.



I don't see where there would be an improvement. The fact that a project is packaged as a .deb doesn't mean it will work in Ubuntu. It only means it is in a .deb package. The underlying issues of installation baselines still exists (and based on the fact that Synaptic will install Debian packages on Ubuntu -- yet they don't work -- would indicate quite clearly that dependency verification is a lot harder than you suggest).
that middle section interests me

i seem to remember talking to you re: the binary driver plugins too. it seems the ever changing ABI layer of the open source world is an oft overlooked disadvantage. 

are you sure that they are binary incompatible? it seems... to be frank... completely ****. if this is indeed the case and that newer binaries are not backwards compatible, it would appear that we will simply never get 3rd party closed source apps. but yet we do... quake, flash and opera are all closed source, yet they manage to cope with the ever changing linux world 

so i think there is more to it perhaps than just "broken ABI's everywhere"

and even *if* 3rd party support was completely impossible, i still maintain that a UPM would make open source app distribution alot easier.

---

### Post by saulgoode on 2007-03-19
> **Choad said:**
> i seem to remember talking to you re: the binary driver plugins too. it seems the ever changing ABI layer of the open source world is an oft overlooked disadvantage. 

It is only a disadvantage to the closed source world. In the OS world, maintaining only API compatibility results in such advantages as optimization for a specific system, rapid implementation of innovations, and less bloat. 

Consider the case of USB drivers over that past five years: Windows has in its kernel three different ABI interfaces to access the USB port (perhaps four in Vista?). This is done to maintain backwards compatibility as the specification changed and yet if a (outdated) program uses the earliest USB ABI then it locks out other programs during this time. If it uses the second version of the USB ABI, other programs can share the port to communicate with other devices. If the latest ABI is used, other programs can share the port and communicate with the same device. Linux only needs one USB API to gain the latest functionality of USB and older programs do not lock out everything else because they are API compatible. 

Now one might say: no big deal, just keep the old ABIs around. Well, multiply that USB ABI by about 1000 times and one begins to understand how Windows is fast becoming a crippled dinosaur. 

> **Choad said:**
> are you sure that they are binary incompatible? it seems... to be frank... completely ****. if this is indeed the case and that newer binaries are not backwards compatible, it would appear that we will simply never get 3rd party closed source apps. but yet we do... quake, flash and opera are all closed source, yet they manage to cope with the ever changing linux world 

Yes, I am sure that [ they are binary incompatible](http://wiki.debian.org/Gtk210Transition) (not completely, mind; but then nor is a 2.6 kernel completely incompatible with a 2.4 series).

I imagine in some cases the installers for Quake, Flash, and Opera have to examine the runtime environment and determine what resources are available and adjust the installation appropriately (in which case, perhaps you could convince them to share their code :) ). More often than not, an extra compatibility layer is introduced into their program which adapts their system calls to the ones present. 
 
> **Choad said:**
> so i think there is more to it perhaps than just "broken ABI's everywhere"

and even *if* 3rd party support was completely impossible, i still maintain that a UPM would make open source app distribution alot easier.

I am a firm believer in people working on whatever project they wish. If you wish to develop a universal package manager, I wish you well. I just wanted to share some of my thoughts on the pitfalls inherent in such an endeavor.

---

### Post by prizrak on 2007-03-19
Choad,

Don't take it the wrong way, your hear is in the right place but you don't seem to understand the technical issues.

Every program is compiled with certain dependancies. For instance a Feisty .deb won't work on Edgy because it's expecting a different version of the library. There kernels are different, the front ends are different. So on and so forth. When it comes to just about every program you see in the repos they are recompiled against the new libraries and then sent down to your system. Feisty being beta is getting alot of updates and once a week or so I get a new version of Xorg and the kernel with that I get a new version of nvidia-glx. Now the actual official driver is still the same all I get is a version that was compiled (nvidia driver actually compiles on install) against the new kernel and xorg. 

The only way for a UPM to happen is that it would pull down all dependancies. This basically would mean that each and every distro will have to have the same software installed. Basically we are talking a hugely overbloated unified Linux distro. They will look different sure but underneath it all they will contain the same things. Now certain things can be backwards compatible, others cannot. 

If ISV's want to provide software for Linux they can do the same thing they already do on Windows - roll all of the necessary files into the application. This way they don't have to worry about any kind of dependancy issues or package management.

---

### Post by Mr. Picklesworth on 2007-03-21
My vision for how this can work is software packages (be they Autopackage or just .debs) being able to add their own standardized package repository to one's sources.list.

This will need one of these many formats to win, of course, so only time will let it happen. Some day...

The idea then is that the centralized updates would happen; removing the package via apt could of course happen (assuming it was installed nicely, through apt); and since there isn't a reason to purge this futuristic sources.list of unused repositories, it could be again reinstalled at any time.

This needs lots of cooperation. For example Autopackage needs to talk to Apt to have packages installed via it working in a centralized manner with the rest of my desktop, and to erase the sad need for that "Manage 3rd Party Software" tool.

This way a company like Adobe could have its own online package repository. When someone buys a CD with an Adobe product and installs it, that Adobe repository would be added to sources.list.
Now that Adobe product can be added or removed cleanly, or someone can browse other Adobe software for which they own licenses and which is hosted on the repository. Finally, updates to Adobe software /without/ Adobe Updater.
In the package manager of the future, the fact that one already owns a CD with the same futuristic Linux version of Photoshop could be detected so that nobody goes around downloading full computer programs that they can just get from disks.

Err... I'm rambling.
Long story short: Why doesn't everyone just get along?

---

### Post by prizrak on 2007-03-22
> **Mr. Picklesworth said:**
> My vision for how this can work is software packages (be they Autopackage or just .debs) being able to add their own standardized package repository to one's sources.list.

This will need one of these many formats to win, of course, so only time will let it happen. Some day...

The idea then is that the centralized updates would happen; removing the package via apt could of course happen (assuming it was installed nicely, through apt); and since there isn't a reason to purge this futuristic sources.list of unused repositories, it could be again reinstalled at any time.

This needs lots of cooperation. For example Autopackage needs to talk to Apt to have packages installed via it working in a centralized manner with the rest of my desktop, and to erase the sad need for that "Manage 3rd Party Software" tool.

This way a company like Adobe could have its own online package repository. When someone buys a CD with an Adobe product and installs it, that Adobe repository would be added to sources.list.
Now that Adobe product can be added or removed cleanly, or someone can browse other Adobe software for which they own licenses and which is hosted on the repository. Finally, updates to Adobe software /without/ Adobe Updater.
In the package manager of the future, the fact that one already owns a CD with the same futuristic Linux version of Photoshop could be detected so that nobody goes around downloading full computer programs that they can just get from disks.

Err... I'm rambling.
Long story short: Why doesn't everyone just get along?

So CnR then?

---

### Post by Mateo on 2007-04-06
i just ran across this and was wondering what everyone thought about it. I think it's quite nice, i hope it becomes more commonplace.

---

### Post by aysiu on 2007-04-07
There's been a lot of discussion about AutoPackage (and other options like CNR). I've merged you in with those discussions. Happy reading!

---

