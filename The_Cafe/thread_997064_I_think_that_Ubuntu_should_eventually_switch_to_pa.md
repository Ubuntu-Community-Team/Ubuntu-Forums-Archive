---
title: "I think that Ubuntu should eventually switch to pacman instead of apt."
date: 2008-11-29
forum: The Cafe
---

### Post by smartboyathome on 2008-11-29
Before I get started, let me state that I know Ubuntu probably never will switch due to the shear number of packages it has made into debs, but I thought I would post it anyway since its been going through my head a lot recently. Also, let me tell you this is **not** about Ubuntu becoming rolling release or being based on Arch or anything like that. Its just about the package manager Arch uses, and is just my personal opinion.

I have used Ubuntu since March of last year. I have tried several times to make packages, but its all in vain. Debian packaging is very complicated, and each time I try I have something to wrong somewhere. I have learned to get by through hoping others would make packages for me since it was very hard to make my own.

I have been using Arch for a few months now, and have come to appreciate how easy it is to build packages. I can make my own PKGBUILDs using a simple template and my knowlege of how to compile programs, then install them from the .pkg.tar.gz which is generated. In Debian packaging, I would have to deal with complicated stuff such as fakeroot and such, and trying to get it to compile how debian wanted it was a hassle. The debs that were generated were also painless to install though.

The power of pacman comes from how easy everything is though. There are tons of unsupported packages for Arch in AUR (I can say if you include these packages the amount of programs packaged for Arch rivals that of Ubuntu), and it is easy to install these using yaourt, which automates everything for you. The AUR is kind of like Ubuntu's universe and multiverse repository, where the majority of Ubuntu's packages are.

You can even easily create an Arch Linux repository, using the well documented page on the wiki. I have used Larch's (the livecd arch linux builder) Gen_repo script for this, which works very well and painlessly.

I can say that overall from my experience, Arch's package manager rivals that of Ubuntu's, and surpasses it in ease of use. Its easier to create packages for, and could possibly have just as many programs as Ubuntu does packaged for it if you include AUR. Its even easy to create a repository for Arch Linux.

Again, though, these are my opinions, taken from my experiences thus far, and should be taken with a grain of salt.

---

### Post by mentallaxative on 2008-11-29
If Ubuntu should ever be blessed (or cursed) with a new package manager in the future, I think it should be Conary. It tracks dependencies down to individual files, installs only what is needed, and keeps a history of package installation similar to how a version control system functions, allowing you to revert changes. See Foresight Linux if you want to see Conary in action.

Of course, Pacman is great too. It's simple done well.

---

### Post by SunnyRabbiera on 2008-11-29
Yes but the library of packages for arch is minuscule compared to debian.

Arch:
4859

Debian:
25457

Plus I never had problems creating .deb, also good luck converting non native .rpm files too, there are many packages out there that people may find useful that are RPM only so its easier to convert rpms to deb then it is to create arch packages.

---

### Post by sub2007 on 2008-11-29
I think the suggestion of an improved build system for Ubuntu, like Gentoo/Slackware/Arch has, is excellent. But pacman is just a package manager and doesn't necessarily work better than apt (it does in Arch but not sure on other distros) - I don't know of any implementations that can install .deb and so don't know how well it would work. Pacman is hard coded for Arch format packages (Judd Vinot wrote both format and pacman together) and as I see it as highly unfeasable that Ubuntu would drop .deb totally (being that it's based on Debian and people are used to it) then it would need a complete pacman rewrite, which would be essentially a new package manager (which people will probably complain doesn't work as well as apt).

[quote=SunnyRabbiera]Yes but the library of packages for arch is minuscule compared to debian.

Arch:
4859

Debian:
25457[/quote]

Yes but Debian breaks packages up more than Arch. Lots of them have -dev packages as well as the main package (which adds to the count) which Arch doesn't have. In Ubuntu, Beagle comes in about 15 packages whereas in Arch it comes as two. With that factored in as well as AUR (AUR hosts 10,529) the number of packages is not as bad as you make out.

---

### Post by SunnyRabbiera on 2008-11-29
> **sub2007 said:**
> I think the suggestion of an improved build system for Ubuntu, like Gentoo/Slackware/Arch has, is excellent. But pacman is just a package manager and doesn't necessarily work better than apt (it does in Arch but not sure on other distros) - I don't know of any implementations that can install .deb and so don't know how well it would work. Pacman is hard coded for Arch format packages (Judd Vinot wrote both format and pacman together) and as I see it as highly unfeasable that Ubuntu would drop .deb totally (being that it's based on Debian and people are used to it) then it would need a complete pacman rewrite, which would be essentially a new package manager (which people will probably complain doesn't work as well as apt).

that too, why mess with something when there are already many .debs out there to convert.
Debian has the most diverse amount of packages out there so why cut it out for something with so few packages?
Plus you would have to make sure those packages are compiled on your own, not ideal for new users.
But in the future I feel debian will get better with its packages, so what is the point?

---

### Post by smartboyathome on 2008-11-29
Like I said, I know that it would probably never happen, its just something I was stating.

And about deb packages: I can install them on Arch easily by using this code:
```
deb2targz <nameofdeb>.deb
tar -xcf <nameofdeb>.tar.gz
```
That code turns the deb into a tar.gz file, and then you can extract the tar.gz file into the pkg directory, where makepkg makes it into a pkg.tar.gz.

Also, pacman has a lot more packages than it looks, and its easier for people to make .pkg.tar.gz packages than in Ubuntu. I would be interested to see Conary, though. What distros use it?

---

### Post by SunnyRabbiera on 2008-11-29
But people would still have to compile and that is where you have to make the deal breaker.
Debian just has too many packages to go to something with so few packages out by default.
You might as well say Ubuntu should use RPM's next

---

### Post by smartboyathome on 2008-11-29
> **SunnyRabbiera said:**
> But people would still have to compile and that is where you have to make the deal breaker.
Debian just has too many packages to go to something with so few packages out by default.
You might as well say Ubuntu should use RPM's next

Actually, as stated above, Arch has more packages than it looks. Also, people wouldn't *have* to compile if they wanted to stay with the packages in the repos (which there are quite a few). Its basically the same as Ubuntu, compile if you want to or if there is no package available. Since Arch has AUR, there would be less compiling due to more packages being available due to easier package creation.

---

### Post by sub2007 on 2008-11-29
I think what the OP is getting at is that Arch has a better build system for creating it's package format than Ubuntu has for creating it's package format. I found creating .debs so labourious that I stopped doing it. On Arch creating a package is a piece of cake (it's a matter of just changing the pkgbuild file, often just updating the version number and running makepkg).

So it seems that it's not about adopting pacman or Arch's package format, more about creating or incorporating something like ABS that would make .deb creation easier, because it is undeniably easier on Arch than on Ubuntu.

---

### Post by Newuser1111 on 2008-11-29
> I think that Ubuntu should eventually switch to pacman instead of apt.  I don't. 
If you don't like apt then go to a different one that has what you want.

---

### Post by SunnyRabbiera on 2008-11-29
the thing is that I never really liked pacman, apt seems so easy and painless compared to most other package managers out there.

---

### Post by smartboyathome on 2008-11-29
> **sub2007 said:**
> I think what the OP is getting at is that Arch has a better build system for creating it's package format than Ubuntu has for creating it's package format. I found creating .debs so labourious that I stopped doing it. On Arch creating a package is a piece of cake (it's a matter of just changing the pkgbuild file, often just updating the version number and running makepkg).

So it seems that it's not about adopting pacman or Arch's package format, more about creating or incorporating something like ABS that would make .deb creation easier, because it is undeniably easier on Arch than on Ubuntu.

Thats exactly what I mean. I like Ubuntu and all, but its just a PITA to maintain packages for.

> **Newuser1111 said:**
> I don't. 
If you don't like apt then go to a different one that has what you want.

I do, I use Arch. The problem is though that sometimes I want a quick, painless install (Arch installs are mostly painless, but definately not quick). With Ubuntu adopting something like Pacman I might go back.

> **SunnyRabbiera said:**
> the thing is that I never really liked pacman, apt seems so easy and painless compared to most other package managers out there.

Whats so hard about pacman? Hardest thing I've seen is the syntax for the pacman command, which I use aliases for anyway on both Ubuntu and Arch.

---

### Post by -grubby on 2008-11-29
I love Pacman, and building packages is easy, but I don't think Pacman is stable enough to include in Ubuntu. I only had it break on me once, but once is too many times. Strangely I had to fix it by reinstalling Pacman with Pacman..

---

### Post by smartboyathome on 2008-11-29
> **nathangrubb said:**
> I love Pacman, and building packages is easy, but I don't think Pacman is stable enough to include in Ubuntu. I only had it break on me once, but once is too many times. Strangely I had to fix it by reinstalling Pacman with Pacman..

I have only had one break, but that was solved quickly. I have had apt-get break more when something doesn't install completely. I think its much more stable than apt, but thats imo of course.

---

### Post by mentallaxative on 2008-11-29
> **smartboyathome said:**
> 
I do, I use Arch. The problem is though that sometimes I want a quick, painless install (Arch installs are mostly painless, but definately not quick). With Ubuntu adopting something like Pacman I might go back.


I think coming up with a quickie Arch install with some default GUI apps like Ubuntu is a better fix than contemplating an angry mob of Ubuntu users demanding their apt back. :)

---

### Post by -grubby on 2008-11-29
> **smartboyathome said:**
> I have only had one break, but that was solved quickly. I have had apt-get break more when something doesn't install completely. I think its much more stable than apt, but thats imo of course.

Come to think of it.. apt has broken alot more for me, also.

---

### Post by smartboyathome on 2008-11-29
> **mentallaxative said:**
> I think coming up with a quickie Arch install with some default GUI apps like Ubuntu is a better fix than contemplating an angry mob of Ubuntu users demanding their apt back. :)

I know, unfortunately that doesn't follow the Arch way though, and most of the distros based on it are either not what I want, or not active anymore. I am trying to work on one as part of Maryan Linux, but unfortunately I can't get it to work that well yet. :(

---

### Post by Mr. Picklesworth on 2008-11-29
What we need is a friendly development environment that isn't an IDE (eg: doesn't try to do anything other than organizing Debian packaging projects with well designed templates specific to the platform). Maybe some file manager extensions, a "create project" tool / autoconf setup wizard...
No need to switch packaging formats; they're all somewhat odd to develop for.

---

### Post by doorknob60 on 2008-11-29
> **SunnyRabbiera said:**
> Yes but the library of packages for arch is minuscule compared to debian.

Arch:
4859

Debian:
25457

Plus I never had problems creating .deb, also good luck converting non native .rpm files too, there are many packages out there that people may find useful that are RPM only so its easier to convert rpms to deb then it is to create arch packages.

In Arch, so far I've never had to manually install or compile anything, it's always wither in the regular repositories, or it's in AUR, easily accessible with yaourt. Also, creating PKGBUILDS is extremely easy, and honestly even after lots of googling I never really figured out how to make debs. Also pacman is faster IMO too :-) But I think Ubuntu should stick with apt since that's what Debian uses, it makes sense. People that want pacman should come over to the Arch side :-D

---

### Post by Dr Small on 2008-11-29
> **nathangrubb said:**
> I love Pacman, and building packages is easy, but I don't think Pacman is stable enough to include in Ubuntu. I only had it break on me once, but once is too many times. Strangely I had to fix it by reinstalling Pacman with Pacman..
I have had apt break on me numerous times between my server, my sisters computer and the laptop. I can't think of one event that Pacman has ever failed on me.

Having Pacman in Ubuntu would be nice, easier and more efficient, but I still wouldn't come back to Ubuntu for my favorite package manager. Arch is just too cozy for me to return to bloat world.

---

### Post by andras artois on 2008-11-29
It wouldn't be very based off debian if it switched....

---

### Post by smartboyathome on 2008-11-29
> **andras artois said:**
> It wouldn't be very based off debian if it switched....

Its only half based off of debian now, since Ubuntu uses a lot of its own package names or tools.

---

### Post by sub2007 on 2008-11-29
> **smartboyathome said:**
> Its only half based off of debian now, since Ubuntu uses a lot of its own package names or tools.

Ubuntu is a lot more than half based on Debian. Ubuntu takes a freeze of Debian Sid every 6 months and then works with that to stabilise what they have, with some renamed packages and a lot of patches. At it's core, it's still Debian.

---

### Post by smartboyathome on 2008-11-29
> **sub2007 said:**
> Ubuntu is a lot more than half based on Debian. Ubuntu takes a freeze of Debian Sid every 6 months and then works with that to stabilise what they have, with some renamed packages and a lot of patches. At it's core, it's still Debian.

*At its core*, but its only to a point. To prove this, try taking many debian packages and using them on Ubuntu. A lot of them might not work without tweaks. I digress, though, as it would get this thread no where and makes it go off topic.

---

### Post by handy on 2008-11-29
> **SunnyRabbiera said:**
> 
Plus I never had problems creating .deb, also good luck converting non native .rpm files too, there are many packages out there that people may find useful that are RPM only so its easier to convert rpms to deb then it is to create arch packages.

I use NeroLinux on Arch, it is an RPM, which was converted & installed on my system initially & whenever there has been an upgrade since.

Arch has no problem with RPM's.

---

### Post by InfinityCircuit on 2008-11-29
Does pacman support building packages in clean chroots?

Where does Arch host the source of its packages?  

Does pacman actually make it easier to maintain a complex package like glibc or the kernel or kde that requires large patch systems?  

How does arch handle package uploads?  Does it use a buildd?

What kind of support does pacman have for cross compiling? 

Any comparison of dpkg v pacman would require a comparison of the wanna-build infrastructure in comparison to whatever Arch uses.  In other words: It's probably much easier for the average user to create an Arch package than a Debian package.  But if the development system of Debian is superior for the experienced user that is probably a reason to stay with dpkg.

I'm not trying to be confrontational, but I'm trying to understand how it works.  In any case, Debian will never abandon IWJ code. :)

---

### Post by Luke has no name on 2008-11-29
Ubuntu should be based on FreeBSD, not Debian.

---

### Post by smartboyathome on 2008-11-29
> **InfinityCircuit said:**
> Does pacman support building packages in clean chroots?

Yes, just build the PKGBUILD in a chroot.

> **InfinityCircuit said:**
> Where does Arch host the source of its packages?  

I don't know, actually. Never thought about it.

> **InfinityCircuit said:**
> Does pacman actually make it easier to maintain a complex package like glibc or the kernel or kde that requires large patch systems?  

I wouldn't know that either, as I don't try to do that.

> **InfinityCircuit said:**
> How does arch handle package uploads?  Does it use a buildd?

It handles them using AUR, if thats what you mean.

> **InfinityCircuit said:**
> What kind of support does pacman have for cross compiling? 

Packages which are used in pacman can be cross compiled using the pkgbuilds.

> **InfinityCircuit said:**
> Any comparison of dpkg v pacman would require a comparison of the wanna-build infrastructure in comparison to whatever Arch uses.  In other words: It's probably much easier for the average user to create an Arch package than a Debian package.  But if the development system of Debian is superior for the experienced user that is probably a reason to stay with dpkg.

I haven't seen any reason TO stay with debs besides the fact that theres so many of them.

> **InfinityCircuit said:**
> I'm not trying to be confrontational, but I'm trying to understand how it works.  In any case, Debian will never abandon IWJ code. :)

I know it won't, and I respect that. Just stating what I wish would happen to Ubuntu.

---

### Post by InfinityCircuit on 2008-11-29
> **smartboyathome said:**
> I haven't seen any reason TO stay with debs besides the fact that theres so many of them.

Debian packages have:

1) support for 3-tier system to communicate information about package upgrades to the user. (debian/changelog, debian/NEWS, debconf postinst reminders)

2) lots of supporting infrastructure that already exists (wanna-build, sbuild/pbuilder, lintian, vcs-controlled packaging - git-buildpackage, svn-buildpackage, hg-buildpackage, cvs-buildpackage, arch-buildpackage. etc)

3) extensive support for patching (simple-patchsys, quilt, dpatch, dbs)

4) lots of new features coming post-Lenny (lzma compression = smaller downloads, dpkg-source v3 will support 100% vcs-managed packaging)

5) A very simple way to build packages in debhelper 7.  A basic package basically just needs a skeletal debian/control, debian/copyright, and debian/rules containing only these lines:

```
#!/usr/bin/make -f

%:
    dh $@
```

That seems pretty accessible to the average user.  Launchpad already exists to help distribute unofficial packages.

I don't know the pacman equivalents of this system but I feel that they would be deficient.  Ultimately, it comes down to what I said earlier--Arch packages probably are easier for the average user.  But for the advanced developer Debian probably offers far far more flexibility.  And which one of those two people do you want creating your kernel and glibc?  :popcorn:

---

### Post by HoppingWombat on 2008-11-29
No, RPMs. And users should have to use source RPMs, too, for all of the packages with over 50 downloads. :lolflag:

---

### Post by Changturkey on 2008-11-29
> **Luke has no name said:**
> Ubuntu should be based on FreeBSD, not Debian.

:)

---

### Post by smartboyathome on 2008-11-29
> **InfinityCircuit said:**
> Debian packages have:

1) support for 3-tier system to communicate information about package upgrades to the user. (debian/changelog, debian/NEWS, debconf postinst reminders)

2) lots of supporting infrastructure that already exists (wanna-build, sbuild/pbuilder, lintian, vcs-controlled packaging - git-buildpackage, svn-buildpackage, hg-buildpackage, cvs-buildpackage, arch-buildpackage. etc)

3) extensive support for patching (simple-patchsys, quilt, dpatch, dbs)

4) lots of new features coming post-Lenny (lzma compression = smaller downloads, dpkg-source v3 will support 100% vcs-managed packaging)

5) A very simple way to build packages in debhelper 7.  A basic package basically just needs a skeletal debian/control, debian/copyright, and debian/rules containing only these lines:

```
#!/usr/bin/make -f

%:
    dh $@
```

That seems pretty accessible to the average user.  Launchpad already exists to help distribute unofficial packages.

I don't know the pacman equivalents of this system but I feel that they would be deficient.  Ultimately, it comes down to what I said earlier--Arch packages probably are easier for the average user.  But for the advanced developer Debian probably offers far far more flexibility.  And which one of those two people do you want creating your kernel and glibc?  :popcorn:

1) is a good reason, one I didn't know about
2) isn't imo, as there wouldn't be that many if there was a default, good way to make packages.
3) So these patches get applied to the *already installed* packages, or are they just ways to apply patches to programs before the packages are made?
4) I am not a developer, so I don't know what the advantages of VCS are, but I know that the pacman devs have been looking into implimenting lzma instead of gz since last April.
5) So what if the package is more complicated than a basic ./configure, make, make install, will this work then?

As for Arch devs vs Debian devs, Arch devs are pretty smart as well, since the Arch Way naturally makes them smarter than the average joe. I don't think we will see people trying to create you a default glibc or kernel with this.

---

### Post by bruce89 on 2008-11-29
I'm sure everyone knows this is impossible. If you like pacman, use a distro that uses it and stop preaching to others.

---

### Post by smartboyathome on 2008-11-29
> **bruce89 said:**
> I'm sure everyone knows this is impossible. If you like pacman, use a distro that uses it and stop preaching to others.

I wasn't really trying to preach, just stating I wished that debian had an easier build system. I think I mistitled the thread (oops :(). I basically meant what this post says:

> **sub2007 said:**
> I think what the OP is getting at is that Arch has a better build system for creating it's package format than Ubuntu has for creating it's package format. I found creating .debs so labourious that I stopped doing it. On Arch creating a package is a piece of cake (it's a matter of just changing the pkgbuild file, often just updating the version number and running makepkg).

So it seems that it's not about adopting pacman or Arch's package format, more about creating or incorporating something like ABS that would make .deb creation easier, because it is undeniably easier on Arch than on Ubuntu.

---

### Post by bruce89 on 2008-11-29
> **smartboyathome said:**
> I wasn't really trying to preach, just stating I wished that debian had an easier build system. I think I mistitled the thread (oops :(). I basically meant what this post says:

Ah, fair enough. The Debian system is complex, but it probably as it is quite old.

---

### Post by smartboyathome on 2008-11-29
> **bruce89 said:**
> Ah, fair enough. The Debian system is complex, but it probably as it is quite old.

Probably. Personally, though, I wish that the debian developers would rewrite the package system so that it could support some newer features and much easier packaging.

---

### Post by bruce89 on 2008-11-29
> **smartboyathome said:**
> Probably. Personally, though, I wish that the debian developers would rewrite the package system so that it could support some newer features and much easier packaging.

It's rather tricky without breaking the 20,000 packages all at once.

---

### Post by smartboyathome on 2008-11-29
> **bruce89 said:**
> It's rather tricky without breaking the 20,000 packages all at once.

Yeah, thats the hard part. Oh well though, perhaps like Linux is starting to overcome Windows, some other package format will overcome debian when the time is right. :)

---

### Post by bruce89 on 2008-11-29
> **smartboyathome said:**
> Yeah, thats the hard part. Oh well though, perhaps like Linux is starting to overcome Windows, some other package format will overcome debian when the time is right. :)

You'd have thought the same about autotools, but alas, it's not the case.

---

### Post by Luke has no name on 2008-11-29
I tried to understand how to package very simply using Daniel Holbach's video tutorial, but it just seems like there are too many steps and tools. I wouldn't mind seeing a better system, and I've heard good things about Conary as it relates to how it manages partial installation, dependencies, etc.

---

### Post by smartboyathome on 2008-11-29
> **Luke has no name said:**
> I tried to understand how to package very simply using Daniel Holbach's video tutorial, but it just seems like there are too many steps and tools. I wouldn't mind seeing a better system, and I've heard good things about Conary as it relates to how it manages partial installation, dependencies, etc.

What distros use Conary? I would be interested in seeing it. :)

---

### Post by ibutho on 2008-11-29
> **smartboyathome said:**
> What distros use Conary? I would be interested in seeing it. :)

Rpath and Foresight Linux use Conary.

---

### Post by smartboyathome on 2008-11-29
> **ibutho said:**
> Rpath and Foresight Linux use Conary.

Cool, thanks. I will be checking it out. :)

---

### Post by eldragon on 2008-11-30
> **InfinityCircuit said:**
> 
Does pacman actually make it easier to maintain a complex package like glibc or the kernel or kde that requires large patch systems?  

i dont know about glibc, but making a package for the kernel is much more simpler to maintain, everything resides in the PKGBUILD file. you just update the version number there, and it will download the source and apply your patches, or do whatever you wish to do.

> 
How does arch handle package uploads?  Does it use a buildd?

as far as ive seen, packages are all grabbed from upstream, and patches are supplied through the AUR database (where you get the initial PKGBUILD, produced by a submitter). this is how i got to build the kernel. got the 2.6.27 from kernel.org, the arch patchset from archlinux.org, and i edited the PKGBUILD to include my patches (only 1).


> 
What kind of support does pacman have for cross compiling? 

havent done any, but it supports it from what ive seen.

now. what the OP mixed is the pacman software with the way to create custom packages in arch.
pacman just solves dependencies and upgrades the system. thats it. you can specify manual packages youve created from AUR or yourself. if you ve configured your PKGBUILD file correctly (or someone did), pacman will solve dependencies.

IMO, apt-get and pacman are too different. i think pacman wouldnt work well on a user friendly distro like ubuntu, where users expect initial configuration to be done for them. pacman does NOT do that, (and as ive read in the arch wiki or forum, its a feature).

i found the build system quite powerful in arch, while i cannot say the same of debian's or ubuntu's for that matter. i think what ubuntu should integrate into their resources, is the makepkg filosofy and use the PKGBUILD scripting thingie. but make it make debs instead of tar.gz

---

### Post by SomeGuyDude on 2008-11-30
Arch vs Ubuntu in terms of packages. I'll say this:

I have had to add lots and lots of repos in Ubuntu to get the things I wanted. I have never had to add anything to Arch, just seach the AUR.

---

### Post by Dharmachakra on 2008-11-30
> **SomeGuyDude said:**
> Arch vs Ubuntu in terms of packages. I'll say this:

I have had to add lots and lots of repos in Ubuntu to get the things I wanted. I have never had to add anything to Arch, just seach the AUR.

Wanna upgrade your video driver? Hop over to ABS. :)

Of course, non-savvy users wouldn't wanna mess around with config files. But honestly, they'll find every package they want in Arch. 

I'm biased towards Arch though...

---

### Post by eldragon on 2008-11-30
> **Dharmachakra said:**
> Wanna upgrade your video driver? Hop over to ABS. :)

Of course, non-savvy users wouldn't wanna mess around with config files. But honestly, they'll find every package they want in Arch. 

I'm biased towards Arch though...

your avatar kind of gives you away :D

they are so different, they are not worth comparing. im still sad intrepid was such a fluke on my hardware. but it made me try arch. which im actually loving atm, so, there's that :D

---

### Post by kk0sse54 on 2008-11-30
pacman is good but yaourt is even better, of course I also liked the FreeBSD ports system but that's just me :D

---

### Post by Polygon on 2008-11-30
if it aint broke, dont fix it.

---

### Post by tiachopvutru on 2008-11-30
> **Polygon said:**
> if it aint broke, dont fix it.

I read somewhere about a response to that phrase being "if it can be improve, then isn't it slightly broken?"

---

### Post by kevdog on 2008-12-01
I really got to try Arch --- Ive been saying this for a while now!!

I know I'm getting flamed for asking, however can you use gnome from within Arch?

---

### Post by RiceMonster on 2008-12-01
> **kevdog said:**
> I really got to try Arch --- Ive been saying this for a while now!!

I know I'm getting flamed for asking, however can you use gnome from within Arch?

yeah you can. You just have to install it after an initial install. It's not hard though. All you have to do is:

```
pacman -S gnome
```

here's some [more info](http://wiki.archlinux.org/index.php/Gnome).

---

### Post by cardinals_fan on 2008-12-01
> **smartboyathome said:**
> What distros use Conary? I would be interested in seeing it. :)
Conary is okay, but the PackageKit frontend in Foresight is appalling.

I **despise** APT.  I actually refuse to even try Debian-based systems now.  Building Debian packages is a horrible process, much harder than on Slackware (I've built a **lot** of Slack packages :)).  SliTaz has a very nice system with tazpkg and tazwok - you might want to check it out.  Read [this]("http://www.slitaz.org/en/doc/manuals/tazwok.en.html") and then download SliTaz to give it a shot.  Or ignore me and continue as you were :)

---

### Post by deepclutch on 2008-12-01
rolling release distros with sympathetic package managers like conary,pacman is proven to be not safe for mission-critical applications.just my 2 paise.

---

### Post by cardinals_fan on 2008-12-01
> **deepclutch said:**
> rolling release distros with sympathetic package managers like conary,pacman is proven to be not safe for mission-critical applications.just my 2 paise.
The package managers have nothing to do with the rollingness of the distro...

---

### Post by mentallaxative on 2008-12-01
> **deepclutch said:**
> rolling release distros with sympathetic package managers like conary,pacman is proven to be not safe for mission-critical applications.just my 2 paise.

Sympathetic? Proven? Please explain further. :)

---

### Post by Luke has no name on 2008-12-01
There really has to be a better way to create and track packages than apt. Ubuntu shouldn't stick with an inferior PM just because its base distro does. Hell, if you made the packaging and patching system easier, more powerful, and quicker, we wouldn't need to use Debian to get a lot of heavy lifting out of the way.

---

### Post by smartboyathome on 2008-12-01
> **cardinals_fan said:**
> Conary is okay, but the PackageKit frontend in Foresight is appalling.

I **despise** APT.  I actually refuse to even try Debian-based systems now.  Building Debian packages is a horrible process, much harder than on Slackware (I've built a **lot** of Slack packages :)).  SliTaz has a very nice system with tazpkg and tazwok - you might want to check it out.  Read [this]("http://www.slitaz.org/en/doc/manuals/tazwok.en.html") and then download SliTaz to give it a shot.  Or ignore me and continue as you were :)

Cool, even better! Slitaz has been on my list for a while, and since it is so small and my 10 year old laptop is in need of an OS, I will give it a try. :)

---

### Post by jimi_hendrix on 2008-12-01
+1 for pacman
+.5 for apt
+10 for getting something like AUR

---

### Post by Dr Small on 2008-12-01
> **kevdog said:**
> I really got to try Arch --- Ive been saying this for a while now!!

I know I'm getting flamed for asking, however can you use gnome from within Arch?
Of course you can. You can run anything on Arch. 
You can even build Arch up to look like Ubuntu (minus the bloat). It's your choice ;)

---

### Post by Polygon on 2008-12-01
> **Luke has no name said:**
> There really has to be a better way to create and track packages than apt. Ubuntu shouldn't stick with an inferior PM just because its base distro does. Hell, if you made the packaging and patching system easier, more powerful, and quicker, we wouldn't need to use Debian to get a lot of heavy lifting out of the way.

we sync with debian every 6 months. if we used a different package manager, we would have to rebuild ALL of the packages in the repos...which would be an insane process to do as there are 1000's of packages.

what exactly are the problems with debs? ive heard that they are harder to build...but what else is  wrong with them?

---

### Post by cardinals_fan on 2008-12-01
> **Polygon said:**
> we sync with debian every 6 months. if we used a different package manager, we would have to rebuild ALL of the packages in the repos...which would be an insane process to do as there are 1000's of packages.

what exactly are the problems with debs? ive heard that they are harder to build...but what else is  wrong with them?
I don't like some of the philosophies employed by Debian regarding packaging.  I'm rather strongly opposed to distro specific modifications or adulterations.  Leave it vanilla!

---

### Post by eldragon on 2008-12-01
> **cardinals_fan said:**
> I don't like some of the philosophies employed by Debian regarding packaging.  I'm rather strongly opposed to distro specific modifications or adulterations.  Leave it vanilla!

thats exactly what surprised me about arch, everything comes from upstream. something that should be taken for granted, under ubuntu it was a pain to get stuff that wasnt in the repos installed

---

### Post by InfinityCircuit on 2008-12-02
> **cardinals_fan said:**
> I don't like some of the philosophies employed by Debian regarding packaging.  I'm rather strongly opposed to distro specific modifications or adulterations.  Leave it vanilla!

What do you mean?  What modifications by Debian do you object to?

Debian has extra themes and wallpaper that you can install but it's not forced.  This also has nothing to do with Debian Policy.

---

### Post by cardinals_fan on 2008-12-02
> **InfinityCircuit said:**
> What do you mean?  What modifications by Debian do you object to?

Debian has extra themes and wallpaper that you can install but it's not forced.  This also has nothing to do with Debian Policy.
A quote from [http://www.debian.org/doc/maint-guide/index.en.html#contents:](http://www.debian.org/doc/maint-guide/index.en.html#contents:)
> 9.1 New Debian revision

Let's say that a bug report was filed against your package, #54321, and it describes a problem that you can solve. To create a new Debian revision of the package, you need to:

    * Correct the problem in the package source, of course.

    * Add a new revision at the top of the Debian changelog file, for example with `dch -i`, or explicitly with `dch -v <version>-<revision>' and then insert the comments using your preferred editor.

      Tip: how to easily get the date in required format? Use `822-date', or `date -R'.

    * Include a short description of the bug and the solution in the changelog entry, followed by this: "Closes: #54321". That way, the bug report will be automagically closed by the archive maintenance software the moment your package gets accepted in the Debian archive.

    * Repeat what you did in Complete rebuild, Section 6.1, Checking the package for errors, Chapter 7, and Uploading the package, Chapter 8. The difference is that this time, the original source archive won't be included, as it hasn't been changed and it already exists in the Debian archive.

In accordance with this, Debian packages are often non-vanilla and include Debian-specific patches.  One well-known example of this going wrong was the [OpenSSL fiasco]("http://www.debian.org/security/2008/dsa-1571") last year.  A quote (emphasis mine):
>     Luciano Bello discovered that the random number generator in Debian's openssl package is predictable. This is **caused by an incorrect Debian-specific change** to the openssl package (CVE-2008-0166). As a result, cryptographic key material may be guessable.

---

### Post by InfinityCircuit on 2008-12-02
Would you prefer that bug reports go unfixed?  Upstream can be very very slow.  Some upstreams are dead.

How do you approach upstream projects that no longer support older versions?  Do you just never change the package and let it rot in the archive?  

Obviously the OpenSSL fiasco was a disaster but the number of disasters that have been averted by quick patching of upstream sources are probably worth the risk.  And the OpenSSL fiasco at best proves that some Debian developers aren't very skilled, which doesn't necessarily imply that patching is bad.

---

### Post by cardinals_fan on 2008-12-02
> **InfinityCircuit said:**
> Would you prefer that bug reports go unfixed?  Upstream can be very very slow.  Some upstreams are dead.

How do you approach upstream projects that no longer support older versions?  Do you just never change the package and let it rot in the archive?  

Obviously the OpenSSL fiasco was a disaster but the number of disasters that have been averted by quick patching of upstream sources are probably worth the risk.  And the OpenSSL fiasco at best proves that some Debian developers aren't very skilled, which doesn't necessarily imply that patching is bad.
I expect my distro to provide me with a set of apps chosen to go well together.  I want the software itself to be exactly as it was made to be.  When I install Ruby, it should be plain old Ruby, not Debian-Ruby (just an arbitrary example; I don't know if Ruby is adulterated).  If they didn't write the program, how can they judge what should or should not be done to it?

Obviously there are cases where patching might be better for most people, even if I don't like it.  However, it should only be applied carefully and in desperate circumstances, not cavalierly according to a developer's whims.

---

### Post by Luke has no name on 2008-12-02
*Full disclosure:* I am not an expert. I am a hobbyist who knows a bit about the system.

**I don't like Apt's output.** 
Yum has a better way of printing information to console. Apt-get is ugly. Perhaps I could patch it(just add some line breaks, jeez.)

**Package creation is ridiculous.**
I'm no expert on packaging, compiling, etc., but I know the concepts. There must be a more intuitive, easy flowing way of creating packages than the current bombardment of deb tools.

**I don't like having 30 packages for a package.** 
openoffice.org-cores-docs-beta-3.0.0 is an annoying site to see. I'm looking for openoffice.org! Packages should have a hierarchy of importance: 

---Primary (entire packages that people would actually use, like openoffice.org), 
---Secondary (major components of packages, perhaps self-sufficient, like openoffice.org-calc) and 
---Tertiary(docs, modules, libraries, etc. that usually aren't installed by themselves).

Users could intelligently sort and search packages based on what TYPE of package they are looking for, maybe? I know having a lot of packages makes patching and maintaining easier, but it's hell to look at in a search. This particular point is something I'm not quite sure of, but it sounds good.

**A very powerful package tracker needs to be employed.**
For every package "P" in the system, the system should know every other package in the system that is possibly associated with "P", when it was downloaded, what referred its download, etc.

**Installation tracking needs to be present.**
If an installation is interrupted, the system should know and ask what to do. Retry installation, revert system, etc. Not just "leave the packages that were installed on the system" (I don't know if apt does this).

Kind of related:
[http://www.informationweek.com/news/software/linux/showArticle.jhtml?articleID=212100714](http://www.informationweek.com/news/software/linux/showArticle.jhtml?articleID=212100714)

One of the main things mentioned that Linux needs is a standard packaging system. This would be very beneficial. And if a single packaging mechanism were to be deployed throughout all major distros, it better be the best, not just "good enough". Apt can improve, or be replaced.

---

### Post by billgoldberg on 2008-12-02
For me as a user apt works great.

---

### Post by smartboyathome on 2008-12-02
> **Polygon said:**
> we sync with debian every 6 months. if we used a different package manager, we would have to rebuild ALL of the packages in the repos...which would be an insane process to do as there are 1000's of packages.

what exactly are the problems with debs? ive heard that they are harder to build...but what else is  wrong with them?

What else is wrong with debs besides how to build them? Not much, but if they are a PITA to build for devs, isn't that reason enough for a change to be needed to happen?

> **Luke has no name said:**
> One of the main things mentioned that Linux needs is a standard packaging system. This would be very beneficial. And if a single packaging mechanism were to be deployed throughout all major distros, it better be the best, not just "good enough". Apt can improve, or be replaced.

It can be beneficial in one sense, and bad in another. I see where you are coming from, that the developers wouldn't have to worry about what package format, but in another sense it is bad because it hinders competition between package formats and thus hinders the development of new features for the package formats. Thats the only thing I'm concerned about when it comes to having one package format.

---

### Post by InfinityCircuit on 2008-12-02
> **smartboyathome said:**
> What else is wrong with debs besides how to build them? Not much, but if they are a PITA to build for devs, isn't that reason enough for a change to be needed to happen?

The trouble is that debs are in no way a PITA to build for devs.  If you ask vorlon or manoj if they want to switch to pacman they will look at you with an incredulous stare.  I don't find it troubling at all to build for Debian because of the sheer resources that debhelper provides for a variety of obscure packaging tools.  Devs need to be able to build udebs, broken out packages, etc.  The same is not true for the average user.

---

### Post by Mr. Picklesworth on 2008-12-02
> **cardinals_fan said:**
> I expect my distro to provide me with a set of apps chosen to go well together.  I want the software itself to be exactly as it was made to be.  When I install Ruby, it should be plain old Ruby, not Debian-Ruby (just an arbitrary example; I don't know if Ruby is adulterated).  If they didn't write the program, how can they judge what should or should not be done to it?

Obviously there are cases where patching might be better for most people, even if I don't like it.  However, it should only be applied carefully and in desperate circumstances, not cavalierly according to a developer's whims.

It should also be noted that downstream patching is one of the reasons why Debian is such a beast to comprehend. For dead projects, it would be completely justified to create a branch in bzr and say "this is the active branch of the project!"
No reason whatsoever to drop all the wonderful organization presented by distributed source code management in favour of a brain-damaged patching system.

It is never a good sign that there seem to be a lot of Debian maintainers who not only don't understand the software they are maintainning, but also don't understand Debian. I just noticed that installing Konqueror (as a web browser) arbitrarily pulls in Dolphin via a long chain of Dependencies, where removing Dolphin also removes Konqueror. Considering that Debian favours a system of completely fragmented packages, where everything is in bite-sized pieces, it shouldn't be much to expect that this Not Happen.

This is why we also need good tools that check for these things passively before releasing. A heap of shell scripts does not cut it for all purposes.

---

### Post by -grubby on 2008-12-02
> **InfinityCircuit said:**
> The trouble is that debs are in no way a PITA to build for devs.  If you ask vorlon or manoj if they want to switch to pacman they will look at you with an incredulous stare.  I don't find it troubling at all to build for Debian because of the sheer resources that debhelper provides for a variety of obscure packaging tools.  Devs need to be able to build udebs, broken out packages, etc.  The same is not true for the average user.

More packages can be created if the package creation method takes less time.

---

### Post by Dr Small on 2008-12-02
> **nathangrubb said:**
> more packages can be created if the package creation method takes less time.
+1

---

### Post by Mr. Picklesworth on 2008-12-02
More packages can be created if it happens upstream, too. Thus, what really must be asked is a lot simpler: Why don't they make packages for us upstream?

I have one very likely guess: Because they don't *want* to deal with the complexity. Now, how is it that they are content packaging their source code snapshots in different archive formats and installer binaries for Windows and MacOS, both 64 and 32 bit with auto update services? It's an especially important question when we consider that those technologies for MacOS and Windows are far less powerful and potentially a great deal more complicated since they lack established centralized systems to be maintained by.

The same question must be asked for every other packaging format the free software community produces.

---

### Post by SomeGuyDude on 2008-12-02
Anyone ever watched a discussion like this and been absolutely amazed that you used to have a computer where nothing was tracked by the system?

It just baffles me that in my Windows days it never struck me as an issue that none of my software was considered "official" by MS and updating was pretty much my own responsibility.

---

