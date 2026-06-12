---
title: "AutoPackage?"
date: 2005-03-27
forum: The Cafe
---

### Post by Rotarychainsaw on 2005-03-27
Looks cool. What do yous guys think?

---

### Post by UbuWu on 2005-03-27
Looks to me as it is a very easy way to get loats of crap running on your pc. The ideal way to get spyware/adware/viruses to the linux masses. There are some comments on the homepage on this.

Something I couldn't fi
Got security questions or concerns about any Ubuntu releases?nd: how will updating programs you installed using this work?

Nice to see that they are working to integrate it with the distro specifig package systems.

Apart from that I think it is a very easy way of installing software not in the repositories. But for now you can easily run into trouble if you accidentily install something twice, using autopackage and apt-getting it.

Here is a link to the homepage:
[http://bylands.dur.ac.uk/~mh/autopackage.org/](http://bylands.dur.ac.uk/~mh/autopackage.org/)

---

### Post by UbuWu on 2005-03-27
hmmm... think I was wrong and that was just a mirror with the original site located at:

[http://www.wildgardenseed.com/apkg/](http://www.wildgardenseed.com/apkg/)

---

### Post by jdong on 2005-03-27
Autopackage is quite interesting -- I've tried using it to install Inkscape and Gaim. However, I still want my packages through my distro -- Autopackage'd Firefox confuses the heck out of debconf, and so on... It's not the best solution in the world!

---

### Post by bored2k on 2005-03-27
I installed latest gaim with it, and I must say install was a breeze, but I am really not impressed at all by it. When you attempt to install it, it downloads the autopackage files, so it is not really like its installing on top of anything. And like UbuWu said, this can might as well used as a crapware petretation for Linux.

Again, nothing that apt-get install, urpmi, yum can't do .

---

### Post by tim1 on 2005-03-27
> Looks to me as it is a very easy way to get loats of crap running on your pc. The ideal way to get spyware/adware/viruses to the linux masses.

That's a rather bad argument. Everything that works good will also work good to do bad things. If you don't want spyware, don't install spyware. Autopackage is not a higher security threat than anything else that gets executed on your pc.


[QUOTE=bored2k]Again, nothing that apt-get install, urpmi, yum can't do .[/QUOTE]

So you can create a package one time and then install it on any distro which uses one of the above? I don't think so. And that is exactly the point of autopackage.


I think atopackage is a good thing, but 1.0 is only the beginning. When autopackage someone works together with dpkg/rpm/... it will be a great tool for third party developers who don't want to mess around with every unix package format just to spread some binaries.

greets, tim

---

### Post by bored2k on 2005-03-27
[QUOTE=tim1]That's a rather bad argument. Everything that works good will also work good to do bad things. If you don't want spyware, don't install spyware. Autopackage is not a higher security threat than anything else that gets executed on your pc.




So you can create a package one time and then install it on any distro which uses one of the above? I don't think so. And that is exactly the point of autopackage.


I think atopackage is a good thing, but 1.0 is only the beginning. When autopackage someone works together with dpkg/rpm/... it will be a great tool for third party developers who don't want to mess around with every unix package format just to spread some binaries.

greets, tim[/QUOTE]
 That was me being and Debian b1@7# ;) .

---

### Post by poofyhairguy on 2005-03-28
[QUOTE=Rotarychainsaw]Looks cool. What do yous guys think?[/QUOTE]

Its a GREAT idea. I mean, installing programs with apt, emerge or yum is fine as long as ITS ACTUALLY IN THE REPOS! When its not, you have to compile it and its dependancies from source which is only slightly better than being kicked in the balls.

I can't wait till the day when I can go to a random sourceforge page (for an obscure thing I need but apt-get doesn't have) and see a tarball AND a universe package. The other alternative for me is digging through Google till I find someone else that packaged it.

I HATE installing programs from source in an unautomated way. If the slackware way was the only way to use Linux, I wouldn't....

---

### Post by dolson on 2005-03-28
[QUOTE=poofyhairguy]Its a GREAT idea. I mean, installing programs with apt, emerge or yum is fine as long as ITS ACTUALLY IN THE REPOS! When its not, you have to compile it and its dependancies from source which is only slightly better than being kicked in the balls.

I can't wait till the day when I can go to a random sourceforge page (for an obscure thing I need but apt-get doesn't have) and see a tarball AND a universe package. The other alternative for me is digging through Google till I find someone else that packaged it.

I HATE installing programs from source in an unautomated way. If the slackware way was the only way to use Linux, I wouldn't....[/QUOTE]
 I'm undecided at this point. I think it's cool, but I can't see it working out very well on a larger scale. At least not at 1.0, as said earlier, it's just the beginning. Time will tell.

---

### Post by UbuWu on 2005-03-28
[QUOTE=tim1]That's a rather bad argument. Everything that works good will also work good to do bad things. If you don't want spyware, don't install spyware. Autopackage is not a higher security threat than anything else that gets executed on your pc.
[/QUOTE]

The security threat from installing software from the official ubuntu repositories is lower. You probably will never install spyware on your system, but a lot of people will yet noone means to do so. Have you ever asked a windows user if he installed that spyware on his pc himself? He will say no, but if you ask him if he installed that fancy all new screensaver, you get a different anwer. The point is, at this moment I get my software for ubuntu from a source I trust. While at first it seems nice to be able to install software from any source, I do think it will be a security threat.

---

### Post by daniels on 2005-03-28
[http://kitenet.net/~joey/blog/entry/autopackage_designed_by_monkeys-2005-03-28-14-20.html](http://kitenet.net/~joey/blog/entry/autopackage_designed_by_monkeys-2005-03-28-14-20.html)

---

### Post by jdong on 2005-03-28
[QUOTE=tim1]
So you can create a package one time and then install it on any distro which uses one of the above? I don't think so. And that is exactly the point of autopackage.[/QUOTE]

NO, autopackaged software does **NOT** mean distro-neutrality... The package FORMAT is distro-neutral, NOT THE PACKAGE CONTENTS!!!

If you tell me that I can compile K3b, package it with Autopackage, and then install it on Debian Woody (KDE 2.x.x) or Kubunu (KDE 3.4.x), then you should seriously consider joining the GCC team.... You'd be a very useful asset!


We already **HAVE** distro-neutral packager formats -- binary tarballs work just as well as any autopackager format! Plus, alien facilitates converting from packager format to packager format perfectly, so I honestly don't see the big deal with Autopackage.

---

### Post by poofyhairguy on 2005-03-28
[QUOTE=jdong]
Plus, alien facilitates converting from packager format to packager format perfectly,...[/QUOTE]

Not quite. I've done everything I can to convert Mandrake's beagle RPMs to no avail...

---

### Post by Glanz on 2005-03-28
[QUOTE=daniels][http://kitenet.net/~joey/blog/entry/autopackage_designed_by_monkeys-2005-03-28-14-20.html]("http://kitenet.net/%7Ejoey/blog/entry/autopackage_designed_by_monkeys-2005-03-28-14-20.html")[/QUOTE]
Yes! I read that too. Joey asks if Autopackage wasn't designed by monkeys. That's a nice way of saying that it is crapola. I personally believe it was designed by a Micro$oft developer or a company wanting to peddle antivirus software for Linux.:twisted:

---

### Post by bobmitch on 2005-03-28
Autopackage could be the best thing to happen for linux in a long time.

That is, of course, if your definition of "best" includes things like "ease of use for end user", "minimal development effort resulting in maximum possible target audience", and "increase in potential migration to linux from other OS's."

I personally believe that package management tools such as apt, rpm and emerge are great for distro-specific system, security and application updates/installs.

I also believe that Autopackage (or another tool with the same ideals/methods) is, or at least, could be the best way for distributing applications/drivers which are not intended to be, or are targeted toward a specific distro.

All of the benefits of the native package management system, without any of the distribution (in the delivery sense) problems inherent with linux software.

What's not to like?

---

### Post by Glanz on 2005-03-28
The idea behind it is of course, good. As long as this doesn't get as insecure as the method used by MS with it's ".exe" installations. Then the point that third party shell scripts to install software on the user level without system-specific verification is a very bad idea is well taken. Linux distros are not monoliths like Windows into which hidden code installs hidden code. This will surely lead to the proliferation of spyware, the violation of root, the dumbing down of secure verification methods and the further Windows emulation of Linux to appease the credulous for whom security means hiding the screen when the wife enters the room.

---

### Post by bobmitch on 2005-03-29
It has to be said that the majority of windows spyware, and, broadly speaking, harmful or privacy infringing,  is actually gained through insecure activex and maliciously coded web pages.  This hidden injection of code is not trivial to achieve on linux.

The more mundane 'spyware' which users install knowingly, such as weather docklets, password reminders and so on, are only spyware insofar as the end user is unaware that the software is performing task(s) other than the primary task they assumed.  These applications, in most cases, actually state their secondary tasks within the installation procedure, normally via a EULA.  

Idiots will find a way of installing these kind of applications regardless of installation simplicity.  Ease of installation is such a non-argument in terms of system security.  It`s up there with security-by-obscurity.  Hiding a problem does not make it go away.

---

### Post by Slapdash on 2005-03-29
I love the idea although its not 100% at the moment.

Linux needs an EXE type installation system for people coming from Windows. Also If I downloaded a Open Source app and want to give it to someone else ( Regardless of Distro on their PC ) I can easily just give them a Autopackage.
GREAT for newbies.
I installed Ubuntu for 5 people now on their PC's 3 of whom dont have a regular internet connection. believe it or not THEY DONT WANT TO APT-GET on a 56K modem.
Needless to say 4 of the 5 is back to Windows. I quote 1 of them. "This Linux is Sh*t!, I cant get any of the thoudands of software you say to work! I need to be connected to the internet all the time. Thats so bullsh*t." If I can give these people a CD with a "EXE type" installer they would switch to linux and maore importantly stay with it.

it's not to say that an "EXE type" installer should be as crappy / unsecure as MS's .exe files.

Question though... Does the Autopackage solve the dependency problem issue?
i.e if I use a .DEB file on some PC's there is always some sort of dependency that I dont have.
Obviously its solved if i'm on the net but one thing Linux desperatly needs is a way to distribute the software easily and install it even easier, WITHOUT having to have access to the net.

For me personnaly Apt-Get works even greater than the best EXE's but what about it if i dont have a net connection or a slow modem. There Linux looses TONS of ground for new adopters, and I have first hand experience of this.

---

### Post by bobmitch on 2005-03-29
[QUOTE=Slapdash]I love the idea although its not 100% at the moment.


Question though... Does the Autopackage solve the dependency problem issue?
i.e if I use a .DEB file on some PC's there is always some sort of dependency that I dont have.
Obviously its solved if i'm on the net but one thing Linux desperatly needs is a way to distribute the software easily and install it even easier, WITHOUT having to have access to the net.
[/QUOTE]

Autopackage checks for dependencies by looking directly at the filesystem, rather than using a bespoke database such as apt.  They plan on integrating with apt (and rpm if that is your bag) in future.

At the moment, this is only really problematic for libraries and core system files.  Applications are largle unaffected.

See [here](http://autopackage.org/faq.html)

---

### Post by CowPie on 2005-03-30
[QUOTE=UbuWu]The security threat from installing software from the official ubuntu repositories is lower. You probably will never install spyware on your system, but a lot of people will yet noone means to do so. Have you ever asked a windows user if he installed that spyware on his pc himself? He will say no, but if you ask him if he installed that fancy all new screensaver, you get a different anwer. The point is, at this moment I get my software for ubuntu from a source I trust. While at first it seems nice to be able to install software from any source, I do think it will be a security threat.[/QUOTE]

how about mac users?

---

### Post by DJ_Max on 2005-03-30
Most people who download spyware, are people who downloaded no-name applications from "shady" sites in the first place. Know where to download programs (simple), and you will have no problem(in Unix). Of course NT users face another problem in it's own.

---

### Post by zenwhen on 2005-03-30
I used it to install Inkscape. It works pretty well.

---

### Post by Randabis on 2005-03-30
[QUOTE=Slapdash]I love the idea although its not 100% at the moment.

Linux needs an EXE type installation system for people coming from Windows. Also If I downloaded a Open Source app and want to give it to someone else ( Regardless of Distro on their PC ) I can easily just give them a Autopackage.
GREAT for newbies.
I installed Ubuntu for 5 people now on their PC's 3 of whom dont have a regular internet connection. believe it or not THEY DONT WANT TO APT-GET on a 56K modem.
Needless to say 4 of the 5 is back to Windows. I quote 1 of them. "This Linux is Sh*t!, I cant get any of the thoudands of software you say to work! I need to be connected to the internet all the time. Thats so bullsh*t." If I can give these people a CD with a "EXE type" installer they would switch to linux and maore importantly stay with it.

it's not to say that an "EXE type" installer should be as crappy / unsecure as MS's .exe files.

Question though... Does the Autopackage solve the dependency problem issue?
i.e if I use a .DEB file on some PC's there is always some sort of dependency that I dont have.
Obviously its solved if i'm on the net but one thing Linux desperatly needs is a way to distribute the software easily and install it even easier, WITHOUT having to have access to the net.

For me personnaly Apt-Get works even greater than the best EXE's but what about it if i dont have a net connection or a slow modem. There Linux looses TONS of ground for new adopters, and I have first hand experience of this.[/QUOTE]
 You should have made them package CDs. :p

---

### Post by Slapdash on 2005-03-31
Yeah and while i'm at at it build them a new house! ;) 
Nah, I get what you are saying but why not try make it easier. We need all the help we can get to take down the M$ money making machine :)


I found this on the TO DO: List of the Autopackage.

Deal with ubuntu sudo vs su

So it means 2 things. Ubuntu is becoming mainstream and that autopackage is really working hard to become better.

it gets my vote for sure.

---

### Post by FooBarWidget on 2005-04-12
Hi guys.

In the weekends I installed Ubuntu. Sudo support is now 95% complete. It didn't make it into autopackage 1.0.1, but expect full Ubuntu/sudo support for 1.0.2.

This thread is 3 pages but I'll try to keep my reply short. A lot of the criticism boils down to:
1. Installing to /usr = evil
Many say that we're supposed to install to /usr/local. But we install to /usr in order to make sure everything works. Distributions don't treat /usr/local as a first-class citizen. Which means that, for example, if you install menu items to /usr/local, they won't show up in the menu. Some distributions don't even have /usr/local/bin in $PATH!
The solution is to fix the distribution and treat /usr/local as a first-class citizen. At the mimimum, menu items must show up, /usr/local/bin must be in $PATH, /usr/local/lib must be in the default library search path, and a few other things I forgot about (you may want to ask the mailing list; Mike probably knows more). If Ubuntu treats /usr/local with respect, then we will add Ubuntu to the whitelist, and install to /usr/local in Ubuntu by default. Same goes for all other distributions: if they treat /usr/local well, we'll add them to the whitelist.

2. No native package manager integration
This is planned for post-1.0. It's definitely something that we will work on in the future. This means that autopackages will register themselves in the RPM/dpkg database, and will try to use apt-get/yum to resolve dependancies. Originally this was plannend for 1.0, but many people were interested in autopackage even without native PM integration, so we changed the schedule.

3. Central repository > random packages on the Internet
Well, yeah, but only if there's only one central repository for everything. In reality, we have many distributions, and that is not going to change any time soon. Because the application has to be re-packaged for every distribution repository, it wastes a lot of manpower. Mathematically, this cannot scale.
Furthermore, packagers do not always do a good job. Mike has had a lot of experience with broken third-party Wine packages. We believe that packages should be maintained upstream, and packagers should work together with upstream developers, not independend of them.
And small, relatively unknown applications won't make it to repositories. Just browse SourceForge. A lot of applications are not in the repositories, or the repository packages are out of date. I don't think it's friendly to tell users to compile those apps. Even those applications should be easy to install.
Finally, there's the fear that a decentralized model might stimulate trojans and spyware. Well... I can't really comment on this, but I don't think central repositories can stop trojans and spyware. Trojans and spyware mostly rely on social engineering. Nothing stops an evil person from sending an email to your mom in which he instructs her to download [http://www.evil.com/trojan.deb](http://www.evil.com/trojan.deb) and run it.

Mike could probably comment on all this in more details, but I think he's kinda tired of replying to 3000 forum threads about autopackage. ;) Everybody pretty much ask about the same things over and over.

---

### Post by FooBarWidget on 2005-04-12
Stupid me, I should have read the entire thread. There seems to be a lot of misunderstanding. I'll address them.

> [http://kitenet.net/~joey/blog/entry...3-28-14-20.html](http://kitenet.net/~joey/blog/entry...3-28-14-20.html)

Sigh, I really wish Joey's blog allows comments. I have to duplicate this post in 3000 different forums.
Autopackage is, by design, very different from RPM/DEB. Because of this different design, it cannot be reliably converted to RPM/DEB. Think changing a boat into a car: both machines are meant for transport, but they are designed in an entirely different way.
Basically, Joey finds out that he cannot make Alien convert autopackage to RPM/DEB, and concludes that autopackage must suck.
Besides, converting an RPM to DEB and vice-versa doesn't always work. Heck, installing an RPM on a different RPM-based distribution doesn't even always work! That's caused by things like different naming policies for dependancies. On RedHat, the dependancy is called gnome-vfs. On Debian/Ubuntu, it's called libgnomevfs or something. On Mandrake it's called libgnomevfs-2 or something. How can Alien deal with that?

You guys may also want to read the Lugradio interview with Mike Hearn. It explains a lot about autopackage and should clear up a lot of misunderstanding: [http://www.lugradio.org/files/25/ogg-high/](http://www.lugradio.org/files/25/ogg-high/)
This is episode 25 of lugradio.

> NO, autopackaged software does NOT mean distro-neutrality... The package FORMAT is distro-neutral, NOT THE PACKAGE CONTENTS!!!

This is not entirely true. Our project is more than just creating a packaging format. From the beginning, we were aware of problems like binary incompatibility, library versioning, etc etc. And we have developed tools to fight those problems. Visit autopackage.org and take a look at apbuild, relaytool, binreloc, etc. We have written tons of documentation, in order to educate developers about the importance of compatibility and how you can improve it.

Of course, "distribution-neutrality" does not mean *perfect* neutrality. We're not magicians. So yes, a KDE 3 app will not work on a distro that only has KDE 2. But autopackage is meant for third party desktop applications. If you have a reasonably modern desktop Linux distribution, then autopackage should work, provided of course that you have the correct versions of libraries. Autopackage supports dependancy handling, but it does not try resolve distribution core packages. It's not a distribution upgrade tool.
But really, nearly all desktop distributions these days come with KDE 3, GNOME 2, etc. You have a much greater chance in successfully installing an autopackage than a random RPM.

> We already HAVE distro-neutral packager formats -- binary tarballs work just as well as any autopackager format!

Binary tarballs don't integrate with your desktop. Autopackage does. And plain binary tarballs don't deal with binary compatibility issues like glibc symbol versioning, relocation, etc. Autopackage does. Binary tarballs don't resolve dependancies. Autopackage does.


> I personally believe that package management tools such as apt, rpm and emerge are great for distro-specific system, security and application updates/installs.

So do we. Autopackage is *not* intended to be a full replacement for RPM/DEB/apt/yum. It's a complement, only meant for third party desktop applications. For distribution core packages, DEB and RPM and better.


> Then the point that third party shell scripts to install software on the user level without system-specific verification is a very bad idea is well taken.

RPM and DEB have a script section. So autopackage is not really more insecure than RPM or DEB. And if you want to inspect the code, you can! Open a .package in 'less'. The stub is a shell script, which you can inspect for malicious code. Once you're sure that the stub doesn't contain malicious code, you can run ./foo.package -d, which extracts the content of the package to disk. You can then further inspect the content of the other scripts for malicious code.


Finally: what is the point of autopackage if you're happy with apt/yum? Well, for YOU, there is no point because you're already happy with what you've got. But there are many people who aren't so happy. They can't apt-get everything. They don't want out-of-date repository packages. They don't want to compile from source. Or they're not using Debian/Ubuntu/Gentoo. Autopackage is for them.

---

### Post by Farina on 2005-04-14
I personally think the autopackage paradigm is the way to go for userland software.  There is no reason for the people working on Ubuntu to waste time packaging the world.  Look what has happened to Debian's sarge: there is no reason that kind of cruft can't happen to Ubuntu.  Furthermore, maintaining and submitting a given piece of software to N different repositories is simply not a sustainable way to deal with an exploding population of software.  

I, like everyone else who has dealt with good-old-days *NIX, get a warm fuzzy feeling when I can just say "apt-get install $SOFTWARE" and have it be in my $PATH in seconds, so don't get me wrong--but it is simply not sustainable if more software gets written for *NIX.  I don't think autopackage will ever replace (nor do I think it is its intention to) critical parts of a distribution such as the windowing system or desktop environment, as well as extremely popular software such as OpenOffice and Gaim that absolutely _MUST_ work to attract users, but for Joe Programmer's nifty niche application it will be a great boon should autopackage become a de-facto standard.

---

### Post by rykel on 2005-05-12
I am 100% behind Autopackage.

And I hope that developers will kindly release all their software as autopackages.

A GnomeBaker developer was very kind, and he created an autopackage for me, but as he went along, despite the initial learning curve in creating autopackages, he said that Autopackage is just great!

Simple, learn once, use for all distros.

I hope that Ubuntu developers and the guys at Debian will free themselves from creating Gaim, Inkscape, AbiWord and any other debs that already have autopackages, and concentrate on developing the core operating system that cannot be "autopackaged".

OR, ideally, when Autopackage 2.0 integrates with the native package manager, then this whole thing about Autopackage vs. Apt-Get will all become moot.

In the meantime, just take it as two parallel package manager databases running on your system. Simply make sure that you apt-get remove whatever programs that you want to install with their respective autopackages.

eg. I have uninstalled GIMP, Inkscape and Abiword. I even removed my ubuntu-desktop - because it insisted on installing Gaim, which I do NOT want to install - since I have already set up the latest version with Gaim Autopackage. So, ubuntu-desktop has to go, for now... in some cases, you can simply install your Autopackage over your Ubuntu default program, which cannot be removed because Ubuntu depends so badly on it. Example: Firefox.)

Another angle to look at it: Windows and Photoshop... Microsoft will concentrate on the operating system, while the vendors will concentrate on Photoshop.EXE, nVidia.EXE or whatever .EXEs there need to be.

Of course, Microsoft itself also has applications, such as Windows Media Player and Microsoft Office - which ALSO comes as .EXE.

So I do not see any reason why, with the 101 distributions of Linux out there, we should have to download Fedora RPMs, Mandriva RPMs, SuSE RPMs, Debian DEBs, TGZ etc. for a single program when we can have ONE-AUTOPACKAGE-DOES-IT-ALL. ("10 different RPMs/DEBs with 100 dependency files and a broadband internet connection" for ONE program vs. "Just download and install THE autopackage")

Sooner or later, the majority of Linux users, ie. people who migrate from Windows, will insist on autopackages instead of RPMs and DEBs for their programs.

That way, we can all share our favourite programs, AND still keep our favourite distributions. For me, of course, it is Ubuntu.    O:)

---

