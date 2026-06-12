---
title: "That's what I'm talking about! Nixstaller."
date: 2007-10-21
forum: The Cafe
---

### Post by Wiebelhaus on 2007-10-21
I hope this becomes THE standard.

[http://nixstaller.berlios.de/news.php](http://nixstaller.berlios.de/news.php)

you should [digg]("http://digg.com/linux_unix/Universal_Installer_For_Linux_Coming_Soon") it.

Thanks -Rick- , I believe this is going to be huge.

---

### Post by BWF89 on 2007-10-21
It would be cool if there was one standard. But I doubt it's ever going to happen. *nix has been around since 1969 and if there was going to be a single standard it would have been implemented years (or decades) ago before it got forked into hundreds of active distributions.

---

### Post by Ireclan on 2007-10-21
How is this any more efficient than what we have now (DEBs)?

---

### Post by Wiebelhaus on 2007-10-21
> **Ireclan said:**
> How is this any more efficient than what we have now (DEBs)?

Deb's are fantastic , but this applies to a larger scale , like linux.com could add a monster applications list to the website and no matter the distro you could download and install using this tech and ports could use this tech instead of creating multiple ports for YUM,RPM,DEB,Tar.gz etc etc.




psss kinda like .exe , yea! DON'T TASE ME BRO!

---

### Post by FranMichaels on 2007-10-21
> **sx66gns said:**
> Deb's are fantastic , but this applies to a larger scale , like linux.com could add a monster applications list to the website and no matter the distro you could download and install using this tech and ports could use this tech instead of creating multiple ports for YUM,RPM,DEB,Tar.gz etc etc.




psss kinda like .exe , yea! DON'T TASE ME BRO!

Every distro should use .deb! ;) Ahem... 

Well, regardless, as long as this allows some form of package management and repositories, I say go for it. Having to install packages manually like in the Windows world would be a step backward. 

I know gdebi allows this, but it works from commandline too, and the option is great. As long as the choice is there, choice is good. :popcorn:

---

### Post by Depressed Man on 2007-10-21
I couldn't care about what the end result for installing is, as long as it acts like .debs where it can self install the dependencies.

I've had to install programs in Windows..which install fine. But try to run it "sorry you need to get this driver, or get whatever microsoft's net code thing is".

Argh!

---

### Post by Ireclan on 2007-10-21
[quote=sx66gns]Deb's are fantastic , but this applies to a larger scale , like linux.com could add a monster applications list to the website and no matter the distro you could download and install using this tech and ports could use this tech instead of creating multiple ports for YUM,RPM,DEB,Tar.gz etc etc.




psss kinda like .exe , yea! DON'T TASE ME BRO![/quote]

Oh. Well, I am of the opinion that bringing yet ANOTHER way to package things into the Linux world isn't going to solve anything. I'd rather just wait for DEB and RPM to fight it out. My money's on DEB. Don't get me wrong, it's admirable what this guy's trying to do, I just don't think it'll be adopted.

---

### Post by LanDan on 2007-10-21
in fact its already possible and i use it all the time

when installing xen vm's you can use debootstrap or rpmstrap.
BSD and Solaris don't use the same packages either, so it can never take lang to have debootstrap and rpmstrap integrated inti the same installer as an option

---

### Post by LanDan on 2007-10-21
ps.

.deb is nice, but its nothing compared to what bsd has (never tried solaris tough)

---

### Post by happysmileman on 2007-10-21
As a gentoo user I'm wondering what will happen for those who wish to compile if "every distribution" starts using this?

---

### Post by LanDan on 2007-10-21
if the distribution uses it, it doesn't mean you have to

---

### Post by happysmileman on 2007-10-21
> **LanDan said:**
> if the distribution uses it, it doesn't mean you have to

I meant that Gentoo compiles everything, that IS it's package manager, just a very simplified way of compiling, and one that resolves dependencies... If it uses this as a package manager then compiling would have to be done by hand, dependencies wouldn't be resolved and updates would be a bitch and break your system pretty much every time (instead of about a modest 20-30% of important updates right now )

---

### Post by LanDan on 2007-10-21
> **happysmileman said:**
> I meant that Gentoo compiles everything, that IS it's package manager, just a very simplified way of compiling, and one that resolves dependencies... If it uses this as a package manager then compiling would have to be done by hand, dependencies wouldn't be resolved and updates would be a bitch and break your system pretty much every time (instead of about a modest 20-30% of important updates right now )

i never tried gentoo, but i am fairly well known with bsd and fairly at home when it comes to the port system, not that i ever user packages in bsd but it is certainly verry well possible including taking care of dependencies same as that i never use synaptic either

i would be surpised if gentoo is like slackware when it comes to pre-compiled packages, but i'm not sure, is it?

---

### Post by Polygon on 2007-10-21
i heard from another ubuntuforums member, i think az, that even if there was one standard for packaging, there would still have to be different packages for each distro because of the differences between them

---

### Post by LanDan on 2007-10-21
> **Polygon said:**
> i heard from another ubuntuforums member, i think az, that even if there was one standard for packaging, there would still have to be different packages for each distro because of the differences between them

true, but you can also make the installer able to handle different packages, it is still basically a front end for the real command line installer.

nevertheless it would not be a bad thing if redhat and debian sat around the table to introduce a new standard that both can get away with, if only they weren't so damn stubborn

---

### Post by salsafyren on 2007-10-21
This project doesn't mean a damn thing.

There are already projects for installers. We need binary compatibility but the distros won't do that. That's why users are having a hard time.

Klik2 is much more promising since it includes all dependencies as one file and klik2 packages do not touch the base system.

---

### Post by napsilan on 2007-10-21
from my experience, uninstalling things can be harder than installing them.  When I do compile stuff from scratch and forget to use checkinstall, it's nearly impossible to cleanly remove the program unless I keep the source files and pay very close attention to where I store them.

---

### Post by hanzomon4 on 2007-10-21
I don't see what this solves, folks would still bitch about having to package them. How would this be any different then making debs the standard?

---

### Post by bobbocanfly on 2007-10-21
> **hanzomon4 said:**
> I don't see what this solves, folks would still bitch about having to package them. How would this be any different then making debs the standard?

As far as i can see .debs are much harder to make than a nixstaller. With deb's you have to go through a massive process for each package while with Nixstaller you just edit a small script. If debs were that easy to make, everyone would probably be using them...

---

### Post by FranMichaels on 2007-10-21
> **bobbocanfly said:**
> As far as i can see .debs are much harder to make than a nixstaller. With deb's you have to go through a massive process for each package while with Nixstaller you just edit a small script. If debs were that easy to make, everyone would probably be using them...

It is not hard to make debs, if you use checkinstall. 

It is more complicated to do it the proper way, with dpkg-build and such... There is a reason why they are so robust. 

Either method can be automated with script and template... It's not particularly massive. 

Considering that the 23,000+ packages provided by Ubuntu are all debs... I'd say it's doable :)

---

### Post by happysmileman on 2007-10-21
> **LanDan said:**
> i never tried gentoo, but i am fairly well known with bsd and fairly at home when it comes to the port system, not that i ever user packages in bsd but it is certainly verry well possible including taking care of dependencies same as that i never use synaptic either

i would be surpised if gentoo is like slackware when it comes to pre-compiled packages, but i'm not sure, is it?

Not really sur what slackware's like, but Gentoo generally won't use pre-compiled packages...

For example "emerge opera" will give a pre-compiled package only because there's no source available.
But "emerge amarok" will compile Amarok from source, and most things will get compiled, all dependencies will be retrieved and compiled for any package (whether or not it's binary).
There aren't actually "packages" technically, each program has a script that will install it, it generally just contains the commands to download, extract and compile source.

So with Nixstaller you'd have to used pre-compiled binaries for everything, whereas I want to compile all I can to salvage the last years of my slowly degrading PC

---

### Post by proalan on 2007-10-21
I read this on digg this morning. All in all i think its a neat idea to have some kind of a cross linux standard. 

I hope that this will not kill off existing package managers. Instead only serve as an extra option along side debs, source code, etc...

The danger is that some users will treat it as window users treat .exe and won't check what they are actually installing. It could be a gateway to installing malicious scripts perhaps?

---

### Post by triptoe on 2007-10-21
what about smart package? [http://labix.org/smart](http://labix.org/smart)

---

### Post by bobbocanfly on 2007-10-22
rofl. This is popping up all over the place now, even on Puppy Linux Forums etc. Almost as many downloads as 0.2.2 got in a couple of months in the last 3 days. properly good :D

---

### Post by SomethinSnappy on 2007-10-22
> **proalan said:**
> I read this on digg this morning. All in all i think its a neat idea to have some kind of a cross linux standard. 

I hope that this will not kill off existing package managers. Instead only serve as an extra option along side debs, source code, etc...

The danger is that some users will treat it as window users treat .exe and won't check what they are actually installing. It could be a gateway to installing malicious scripts perhaps?

How is that different than installing a third party Synaptic package?

---

### Post by -Rick- on 2007-10-22
Thanks for all the support everyone :KS

> **bobbocanfly said:**
> rofl. This is popping up all over the place now, even on Puppy Linux Forums etc. Almost as many downloads as 0.2.2 got in a couple of months in the last 3 days. properly good :D
Yeah, Digging it sure made it more popular :)

I'm looking in to more 'serious issues' right now, such as generating system native packages (deb) and what to do about dependencies. Creating basic deb or rpm files isn't very hard and will hopefully featured in the next release. Handling dependencies will be more interesting...some thoughts I had:

[LIST]
[*]When a package is created, fill in dependencies aswell and try to install them. This would be the most ideal option, but is most lickely way too much work and not very robust (over time dependencies may be renamed, removed from the system's repos etc.).
[*]Don't handle dependencies at all, just notify the user for any missing dependencies and wait for them to be installed. Pros: Fairly easy to develop, fairly robust. Cons: Less easy for the end user.
[*]Create 'package containers'. Similar to what PC-BSD does; the package itself will contain every required library, icons etc. Pros: When done right, package should work and keep working on many different systems. When installed in a seperate directory it doesn't interfere other packages. Cons: Package size will grow (a simple GTK2 app might be over 20mb unpacked), however this doesn't have to be a big issue assuming the user won't install many different Nixstaller packages.
[/LIST]

Ofcourse suggestions are welcome.

---

### Post by igknighted on 2007-10-22
LOL!

This thread cracks me up.  Look, the reason you can't convert .rpm to .deb and back via alien is not because the package types... but because different distro's name folders differently and put folders in different places.  If every dependency has the same name and the folders are in the right places, then it works fine.  I am oversimplifying of course, but the organization of the distros is a much larger hurdle than the package type to making packages cross-compatible.  Also different versions of libraries and what not... these are the real troubles.  Not the extension (rpm vs. deb).

Another common misconception here is what a deb or rpm is.  It is not a .exe equivalent.  A .bin or other executable file is a .exe equivalent.  The closest thing I can think of in windows is a .msi file (microsoft installer).  This is a file (not a program) that is opened by a program (dpkg/rpm, or microsoft installer for .msi).  A .exe in windows (and it appears the same is true of the nixstaller), is an executable program that does an install.  It may call the installer to actually do the install, but the file itself is a program.

Which then leads me to what I consider the most elegant solution (although I like the coding ability to create it... right now).  Imagine a generic binary of the application ready to be installed.  Now imagine the "nixstaller" or other install program is called to query the system for its distribution type.  All the major ones would be covered, and since it would be open source any distribution could write code to include theirs.  Once the distribution is obtained, one of two things could happen.  Either it builds the application into the proper package (.deb/.rpm/etc) and calls the package manager (yum/apt/urpmi) to find the dependencies, or all the dependencies could be included and built into rpms or debs and installed via dpkg or rpm (after querying to make sure nothing was duplicated).  As an alternative, the application and dependencies could be self-contained (all in one folder in /opt for example), but this is not the linux way and so not really preferable.

I realize that this has many challenges, but unless the LSB is re-written to include packaging standards, this seems the best solution to me.

---

### Post by cookies on 2007-10-22
How is this different from:
[http://www.autopackage.org/](http://www.autopackage.org/)
?

---

