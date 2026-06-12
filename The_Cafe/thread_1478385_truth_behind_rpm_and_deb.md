---
title: "truth behind rpm and deb?"
date: 2010-05-09
forum: The Cafe
---

### Post by keljaden on 2010-05-09
Is there a real downside to using a distro (such as openSUSE) that uses rpms as opposed to debs?

Like what is the real difference between the two?

I don't want this thread to turn into a DEB VS RPM showdown; however, I would like to see the actual difference between the two posted so I can see what I would be getting myself into if I choose to use something like OpenSUSE.

(I did google this and got really convoluted and hoped you guys here could help clear it up for me.)

---

### Post by -humanaut- on 2010-05-09
I don't really think theres a clear cut winner.
.deb packages to me are easier to handle but I've spent a great deal of time learning it I'm sure I could adapt to RPM files fairly quickly but my familiarity with dpkg vs rpm I would say .deb but that is just an opinion.

---

### Post by nothingspecial on 2010-05-09
You are worrying about nothing.

.debs run on debian based systems and .rpms run on redhat based systems.

The difference is the package manager.

You can compile the source code on either system.

You can even make an rpm into a deb using alien.....
....... if you want.

---

### Post by keljaden on 2010-05-09
I plan on tripple boot win7 (cause my mic isn't working with skype in linux, yet my webcam does...sigh), OpenSUSE, and Linux Mint on my laptop.  

I should be fine then?

---

### Post by Iowan on 2010-05-09
Moved to Community Cafe.

---

### Post by descendent87 on 2010-05-09
Most people  wouldnt notice a difference between rpm and deb. For example if you try kubuntu (deb) and fedora kde (rpm) version (both use kpackagekit) then you won't notice any differences

---

### Post by keljaden on 2010-05-09
From what I read, the difference lies in the package manager.  (also, I heard fedora neglects KDE....which is sad).  That is why I was hoping to give OpenSUSE a go.  I did not ask on their forums as I felt it would be to biased towords yast.

The the package does not make a really big difference, it is the package manager and how dependencies are dealt with?

---

### Post by Xbehave on 2010-05-09
To the end user there is almost no difference.

---

### Post by nothingspecial on 2010-05-09
> **keljaden said:**
> Is there a real downside to using a distro (such as openSUSE) that uses rpms as opposed to debs?


Simple answer?

No.

---

### Post by NMFTM on 2010-05-09
> **nothingspecial said:**
> You can even make an rpm into a deb using  alien.....
....... if you want.
I've heard that using Alien is never a good idea unless it's absolutely the only way. Such, as an application that doesn't have source code available and was only released in binary format as an RPM.
> **keljaden said:**
> (also, I heard fedora neglects KDE....which is sad).
Based on what I've heard, Kubuntu is possibly the worst implementation of KDE out all the major distros. Suse is supposed to be a much better implementation.
> **keljaden said:**
> The the package does not make a really big difference, it is the package manager and how dependencies are dealt with?
I've heard that RPM's are superior to Deb's as far as how the package managers handle dependencies. Yum will only get the dependencies which are strictly necessary while Apt-get will go crazy. The same (only opposite) with removing packages.

One of the reasons that many people (myself included) like to use Debian based distros is because they (for some reason) have a tendency of having much larger first party software repositories. Which means that the end user doesn't need to install as many third party repos or individual packages which might cause dependency hell. But that's doesn't have anything to do with the actual formats the packages are released as.

---

### Post by srs5694 on 2010-05-09
> **keljaden said:**
> The the package does not make a really big difference, it is the package manager and how dependencies are dealt with?

Dependencies are spelled out in the package; the package manager is just the software that verifies that the dependencies are met and then does something with the package (installs it, uninstalls it, etc.). The dependencies can vary from one package to another, even one RPM package to another RPM package or one Debian package to another Debian package, depending on things like compiler options and what versions of necessary support libraries were installed on the system that was used to compile the software. For this reason, it's often impossible to install a binary package for a later version of a distribution on an earlier version (for instance, an Ubuntu 10.04 package on an Ubuntu 8.10 system).

---

### Post by OrbJinzo on 2010-05-09
Back in the day rpm's had really bad dependency recognition.. Even as late as 2005ish Go download a copy of the last Red Hat Linux and take a try at it. deb's however have had the lucky benefit of being developed earlier and being intergrated alot easier into the OS then rpm's did. However all those problems are a thing of the past and i would use either or.

---

### Post by themarker0 on 2010-05-09
Imho autoinstallers are just as bad as .EXE's someone is gonna get smart one of these days and gonna exploit them!

---

### Post by cariboo on 2010-05-09
> **themarker0 said:**
> Imho autoinstallers are just as bad as .EXE's someone is gonna get smart one of these days and gonna exploit them!

Somebody already has, do a search in recurring for gnome-look+deb. Which only proves that you shouldn't download .debs from an untrusted source.

---

### Post by stmiller on 2010-05-09
[http://en.wikipedia.org/wiki/RPM_Package_Manager](http://en.wikipedia.org/wiki/RPM_Package_Manager)

[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

[http://en.wikipedia.org/wiki/Deb_(file_format](http://en.wikipedia.org/wiki/Deb_(file_format))

It's just how software for a particular distro is packaged. Each package contains metadata such as: version of software in the package, other dependent packages, arch, and such. 

Redhat created rpm years ago; Debian created .deb years ago.

:P

Most Ubuntu/Debian folks will say that apt is superior to yum or any other package management software other distros currently use. 

But yum in fedora does something I wish debian/ubuntu would do:

Yum now only downloads the small incremental changes needed for updates instead of downloading the whole sha-bang.

---

### Post by keljaden on 2010-05-09
Thanks for the info.  I do not mind adding third party repos as I have to do that with ubuntu anyways.  I finally figured out how to get codecs install in openSUSE so when 11.3 comes out I will give it a go.. Is there a fedora release with KDE as the main DE, or will I have to install it from the repos myself?


Also, I have this in another post and no one has seemed to answer it;
What is so special about the netbook remixes.  Is UNR still using gnome? and KNR using KDE?  Like is it just a different menu?

---

### Post by speedwell68 on 2010-05-09
> **cariboo907 said:**
> Somebody already has, do a search in recurring for gnome-look+deb. Which only proves that you shouldn't download .debs from an untrusted source.

Quite right.  I used to download debs at will, I reckon it was a hangover from all my years of Windows use, just download the exe and run it with a devil may care attitude.  These days I will only install a deb if I really can't find a repository for the program I want.

---

