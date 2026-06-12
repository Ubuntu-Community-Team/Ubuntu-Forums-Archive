---
title: "what's slackware like for the minimalist?"
date: 2008-11-03
forum: Slackware and derivatives
---

### Post by chucky chuckaluck on 2008-11-03
i guess i'm an odd combination of an end user and someone who doesn't like any unnecessary crap on his computer. i'm enjoying using arch, but i like to mix things up occassionally. how does slackware compare to arch in the areas of ease of installment, package managment and day to day use?



edit: *crickets*

---

### Post by factotum218 on 2008-11-03
> **chucky chuckaluck said:**
> i guess i'm an odd combination of an end user and someone who doesn't like any unnecessary crap on his computer. i'm enjoying using arch, but i like to mix things up occassionally. how does slackware compare to arch in the areas of ease of installment, package managment and day to day use?



edit: *crickets*


Read the [Slackbook]("http://www.slackbook.org/"). If that doesn't help answer your questions then move along.

---

### Post by kk0sse54 on 2008-11-03
Go with a minimal install and just build from there, like Arch once you get it set up it's very easy to take care of, if you need to install software you can use the package manager to install vanilla packages from the slackware repo although they are quite limited and any further software needs can be usually handled through slackbuild.com which is very similiar to the Arch Aur repository. Often the biggest drawback seen with the slackware package manager is that there's no dependency handling (which can be a good thing for those who don't like dependency hell) otherwise you can also install other tools such as slackpkg and slapt-get that you can install.

---

### Post by chucky chuckaluck on 2008-11-03
> **C!oud said:**
> Often the biggest drawback seen with the slackware package manager is that there's no dependency handling (which can be a good thing for those who don't like dependency hell) otherwise you can also install other tools such as slackpkg and slapt-get that you can install.

i don't know if 'depedency hell' is not having them supplied, or having them supplied. as with reading the slackbook, i guess it's hard to get a frame of reference about it all. i didn't really have an idea about using linux until i actually used it, and switching to arch until i actually did switch, so i guess if i want to find out about slackware, i have to just actually install it.

---

### Post by kk0sse54 on 2008-11-03
> **chucky chuckaluck said:**
> i don't know if 'depedency hell' is not having them supplied, or having them supplied. as with reading the slackbook, i guess it's hard to get a frame of reference about it all. i didn't really have an idea about using linux until i actually used it, and switching to arch until i actually did switch, so i guess if i want to find out about slackware, i have to just actually install it.

Dependency hell is when the package manager or the user screws up an installation or uninstallation of a program and all of the sudden you get all kinds of broken packages, missing depencies etc etc. I've gotten it once in Ubuntu and it was my fault and I wouldn't say is as applicable so much today as a reason to switch to slackware.

---

### Post by Sorivenul on 2008-11-03
I like Arch.  But  I like Slack more.  Give it a try, it is the best way to do it.  For what I call an "assisted" setup with Slack, I suggest Absolute.  While not as barebones as Slack, it is far from bloated, and is the best current Slackware derivative, IMO.

---

### Post by cardinals_fan on 2008-11-03
If you're in the mood for a thrill, a fast (but rather dodgy) way of installing Slack is available.  Download SLAX and install it:[QUOTE=markds on the slax forums][http://backtrack.serveftp.com/backtrack/misctools/slax6-install.kmdr]("http://backtrack.serveftp.com/backtrack/misctools/slax6-install.kmdr")

Its a kmdr script, so download it to where you want, say /usr/share/slax/, then run it using the following :

/usr/bin/kmdr-executor /usr/share/slax/slax6-install.kmdr
Ignore the portion on the "live" version install, use the "real" version install.[/QUOTE]Then install slapt-get (although slackpkg seems better, I haven't tried it with this, so do it at your own risk), sync with the Slackware repos, and upgrade.  There will be some packages to reinstall using slapt-get (or maybe slackpkg), make sure you get everything on SLAX reinstalled.

This is a rather nasty way of installing Slackware, and you should definitely do things normally to get a real taste, but I like this method because it's fast and doesn't require too much downloading.

EDIT: A quick warning (I'm really enthusiastic about this, aren't I?): this isn't conventional, and you're on your own if you try it.  I make no guarantees, and most Slack experts will just flame you for being dumb enough to try this.

---

### Post by chucky chuckaluck on 2008-11-04
> **cardinals_fan said:**
> If you're in the mood for a thrill, a fast (but rather dodgy) way of installing Slack is available.  Download SLAX and install it:Then install slapt-get (although slackpkg seems better, I haven't tried it with this, so do it at your own risk), sync with the Slackware repos, and upgrade.  There will be some packages to reinstall using slapt-get (or maybe slackpkg), make sure you get everything on SLAX reinstalled.

This is a rather nasty way of installing Slackware, and you should definitely do things normally to get a real taste, but I like this method because it's fast and doesn't require too much downloading.

EDIT: A quick warning (I'm really enthusiastic about this, aren't I?): this isn't conventional, and you're on your own if you try it.  I make no guarantees, and most Slack experts will just flame you for being dumb enough to try this.

uh-oh, i'm just retarded enough to do it, too. i love slax. running it in ram is wicked fast and was what got me curious about slackware (i also love the name). tempting as that is, i'm more likely to go for the most minimal installation from the start. (actually, i should probably just stick to arch. i do love it. i just get bored occassionally.)

---

### Post by Sorivenul on 2008-11-04
> **chucky chuckaluck said:**
> (actually, i should probably just stick to arch. i do love it. i just get bored occassionally.)
I find both Slack and Arch to be far from boring.

---

### Post by SomeGuyDude on 2008-11-06
> **C!oud said:**
> Go with a minimal install and just build from there, like Arch once you get it set up it's very easy to take care of, if you need to install software you can use the package manager to install vanilla packages from the slackware repo although they are quite limited and any further software needs can be usually handled through slackbuild.com which is very similiar to the Arch Aur repository. Often the biggest drawback seen with the slackware package manager is that there's no dependency handling (which can be a good thing for those who don't like dependency hell) otherwise you can also install other tools such as slackpkg and slapt-get that you can install.

The dependency thing is what bothers me. Does that mean before I install anything the onus is on me to see if it has any dependencies? Granted, I don't install tons of software on a daily basis, but sometimes things have a boatload of dependencies and the idea of rooting for each one and installing them individually, only to find out I forgot one, just doesn't sound fun.

---

### Post by kk0sse54 on 2008-11-06
> **SomeGuyDude said:**
> The dependency thing is what bothers me. Does that mean before I install anything the onus is on me to see if it has any dependencies? Granted, I don't install tons of software on a daily basis, but sometimes things have a boatload of dependencies and the idea of rooting for each one and installing them individually, only to find out I forgot one, just doesn't sound fun.

If you use slackbuilds you shouldn't have to worry about it.

---

### Post by cardinals_fan on 2008-11-06
> **SomeGuyDude said:**
> The dependency thing is what bothers me. Does that mean before I install anything the onus is on me to see if it has any dependencies? Granted, I don't install tons of software on a daily basis, but sometimes things have a boatload of dependencies and the idea of rooting for each one and installing them individually, only to find out I forgot one, just doesn't sound fun.
Out of the box, yes.  However, slackpkg and slapt-get both resolve deps and are easily installed.

---

### Post by saulgoode on 2008-11-06
> **SomeGuyDude said:**
> The dependency thing is what bothers me. Does that mean before I install anything the onus is on me to see if it has any dependencies?
Yes. It is the responsibility of the person installing a package to assure that dependencies are met. Of course, Slackware provides all the dependencies for software included in the installation; so the main concern is when installing "third-party" packages.

The site from which you obtain your third-party package should list the dependencies for you. As an example, [vobcopy]("http://www.slacky.eu/index.php?option=com_content&task=view&id=8789&Itemid=65") specifies that you will also need 'libdvdread' and 'libdvdcss' (the latter is actually only needed for encrypted DVDs). The same site will typically provide the dependency packages as well (I have never encountered otherwise), but the onus is on the user to download and install them.

> **SomeGuyDude said:**
> Granted, I don't install tons of software on a daily basis, but sometimes things have a boatload of dependencies and the idea of rooting for each one and installing them individually, only to find out I forgot one, just doesn't sound fun.

With Slackware, you WILL have to "root for" and install dependencies manually (unless you use one of the add-ons such as 'slapt-get' or 'slackpkg'), however, one shouldn't assume that Slackware installation entails "boatloads of dependencies" just because the corresponding installation in Debian or Ubuntu does.

Slackware packages are, with very few exceptions, unmodified versions of the software as provided by the upstream projects; and upstream projects generally try to minimize the number of their dependencies. This is a different from the Debian philosophy of splitting projects into multiple packages in order to provide better granularity. 

One area this granularity is exhibited in the fact that SW packages always include the documentation and development files as provided by the upstream project. There is never a need to install a separate "-dev" or "-doc" package (or any "build-essentials" either). 

More importantly, the Debian philosophy seems to encourage a proliferation of packages (and thus dependencies). Whereas Slackware (packaging the software as provided by an upstream project) requires 3 packages for an OpenOffice install, Debian has separate 145 packages. Slackware requires 3 packages for ALSA, Debian has 41. Slackware requires installation of a single Apache package, whereas Debian provides 146. Slackware has three kernel module packages, whereas Debian breaks them down into 250 different packages. 

This is not to disparage Debian's approach to packaging, just pointing out the differences. Slackware's approach is definitely more wasteful of harddrive space -- I would estimate that about 20% of the data in a full Slackware install is never used (dev files, documentation, unused drivers/libs, etc) -- and the statistics I provided are for the most extreme cases (more typically, a single Slackware package is equivalent to about four or five Debian packages). Nonetheless, it should be noted that a "boatload" of Debian dependencies does not correlate to a "boatload" of Slackware dependencies. 

Manually fulfilling dependencies can indeed be troublesome at times. This is especially true for installation of GNOME-based software (as SW does not officially support GNOME). Installing AbiWord, for example, requires that seven other packages be installed. If you're intent on running GNOME, Slackware may not be the best choice of distro for you. 

Another area where you may find yourself needing to fulfill a large number of dependencies is with multimedia programs (for example, the Kino video editor has about a half dozen dependencies which need to be met). The caveat to this is that, as you fulfill the dozen or so basic dependencies supporting multimedia, installing additional MM packages requires less effort. Personally, multimedia is one of my main reasons for preferring Slackware; I have to install about two dozen packages of applications, libraries, and codecs but I end up with the latest versions and I'm quite knowledgeable about what my system is capable of. 

Also, since I often choose to compile and build these multimedia packages myself, I know what the configuration of programs such as FFMPEG, MPlayer, or VideoLan is. This can be important because such "applications" are often employed as "libraries" by other MM applications. It can be extremely frustrating trying to figure out that an application is not working owing to inappropriate configuration switches having been used in creating a dependency's package. This problem is not addressed by APT and RPM package managers and error messages generated are rarely instructive to the user. (Neither does Slackware resolve this problem, however, having created the packages myself, I am able to avoid it or at least recognize it.)

Other than GNOME apps and multimedia, Slackware provides a fairly complete set of programs and their associated dependencies. Since your Slackware system is basically configured exactly the same as the developer's (as opposed to Ubuntu where the typical user installation does not include all the software employed by its developers), updating versions of pre-installed programs/libraries becomes trivial; especially so since you can rely on the vanilla source code from the upstream project not conflicting with other packages. 

With Slackware, you can rely on the fact that practically no errors will have been introduced by the distro packager* and that system error messages will accurately report the true nature of the problem. Of course, this is the ideal sought by all distributions, but using a dependency resolving package management system involves a lot more people, a more complex approach, and a much greater chance of errors being introduced by the process. 



* I recall once about 8 years ago that Patrick had the permissions set wrong on a file in a package. That is the only "Slackware" bug I have personally ever encountered (though I imagine others have occurred).

---

### Post by cardinals_fan on 2008-11-06
@saulgoode: brilliant post

---

### Post by factotum218 on 2008-11-06
> **saulgoode said:**
> 
Whereas Slackware (packaging the software as provided by an upstream project) requires 3 packages for an OpenOffice install, Debian has separate 145 packages. Slackware requires 3 packages for ALSA, Debian has 41. Slackware requires installation of a single Apache package, whereas Debian provides 146. Slackware has three kernel module packages, whereas Debian breaks them down into 250 different packages. 

This is not to disparage Debian's approach to packaging, just pointing out the differences.

:)

---

### Post by Sorivenul on 2008-11-06
@saulgood:
Great post.

---

### Post by Antman on 2008-11-07
> **cardinals_fan said:**
> @saulgoode: brilliant post
+9Billion
:guitar:

---

### Post by SomeGuyDude on 2008-11-07
> **saulgoode said:**
> With Slackware, you WILL have to "root for" and install dependencies manually (unless you use one of the add-ons such as 'slapt-get' or 'slackpkg'), however, one shouldn't assume that Slackware installation entails "boatloads of dependencies" just because the corresponding installation in Debian or Ubuntu does.

Slackware packages are, with very few exceptions, unmodified versions of the software as provided by the upstream projects; and upstream projects generally try to minimize the number of their dependencies. This is a different from the Debian philosophy of splitting projects into multiple packages in order to provide better granularity. 

One area this granularity is exhibited in the fact that SW packages always include the documentation and development files as provided by the upstream project. There is never a need to install a separate "-dev" or "-doc" package (or any "build-essentials" either). 

More importantly, the Debian philosophy seems to encourage a proliferation of packages (and thus dependencies). Whereas Slackware (packaging the software as provided by an upstream project) requires 3 packages for an OpenOffice install, Debian has separate 145 packages. Slackware requires 3 packages for ALSA, Debian has 41. Slackware requires installation of a single Apache package, whereas Debian provides 146. Slackware has three kernel module packages, whereas Debian breaks them down into 250 different packages.

Interesting. VERY interesting. I've said elsewhere that I'm going to be "inheriting" an older machine and it's either getting Slack or Gentoo. I haven't decided yet.

---

### Post by chucky chuckaluck on 2008-11-08
thanks for that response, saulgoode. that was pretty interesting. i always wondered wtf was up with all the *dev* packages, when i still used ubuntu.

---

### Post by cardinals_fan on 2008-11-08
> **SomeGuyDude said:**
> Interesting. VERY interesting. I've said elsewhere that I'm going to be "inheriting" an older machine and it's either getting Slack or Gentoo. I haven't decided yet.
I wouldn't recommend source-based unless you have lots of patience.

---

### Post by SomeGuyDude on 2008-11-08
> **cardinals_fan said:**
> I wouldn't recommend source-based unless you have lots of patience.

It's a spare, really. My goal is to use it for my "distro-hopping" desires without messing with my main production machine. So ideally I'll try out just about EVERYTHING with it, and then find that "perfect" distro for me and put it on the main.

At the moment I'm aiming for control, speed, and minimalism. I know I could go DSL or Puppy but I want minimalism in that as little is on my machine as possible while still keeping everything I want/need.

Arch so far seems about right, but it feels like I'm just at a midpoint between the "full featured" distros and the "control-oriented" ones. Gentoo seems like the ultimate in control and personalization, but Slack still has some odd allure to it I can't put my finger on.

---

### Post by chucky chuckaluck on 2008-11-08
> **cardinals_fan said:**
> I wouldn't recommend source-based unless you have lots of patience.

i couldn't stand evolve, emerge (or whatever the asterisks it's called) when i briefly used sabayon (thus, eliminating gentoo). does that also eliminate slackware?

---

### Post by cardinals_fan on 2008-11-08
> **chucky chuckaluck said:**
> does that also eliminate slackware?
No.  Slack uses binary packages.

---

### Post by MisfitI38 on 2008-11-08
> **cardinals_fan said:**
> No.  Slack uses binary packages.

Hehe..until you want to install multimedia players and codecs; off to compile the Slackbuilds. ;)

I like Slack. How could you not? It's the downright coolest distribution around, by a large margin. Pat is, well, he's the Benevolent Dictator for life, I mean come on! Slack is stable, because releases are slow, and it remains largely unchanged for about a year at a time, typically.

Having said that, actually using Slack as my main system would be too much work for me. Slapt-get is a neat idea, but it is not a true package management solution for me. (True Slackers usually agree). The Slack repos are tiny, and the adjustment to looking here there and everywhere for sources and build scripts always got old for me. pkgtool, installpkg, removepkg and upgradepkg are just too crude for me; I feel package management, and especially software installation, should be more of a 'no-brainer'.
One last annoyance for me; I was uncomfortable with the percentage of what, in my experience, seemed to be fanboys among Slack users on the linuxquestions.org forums.

I like the Slack system itself (simple, clean, BSD-init, fast) except for these issues, which Arch happens to solve for me.
If there were no Arch, I would use Slack.

---

### Post by chucky chuckaluck on 2008-11-09
thank you all for convincing me not to mess up my arch installation.

---

