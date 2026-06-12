---
title: "Can i get a .deb to include all dependencies like a .pib?"
date: 2008-05-29
forum: The Cafe
---

### Post by madjr on 2008-05-29
i would like my .debs to include all the dependencies 

"***create once run anywhere .deb***"

i would like it to work in any version of ubuntu (from 5.04 to 20.10+)

sort off like .pibs in PC-BSD:

> 
PC-BSD uses files with the **.pbi** (Push Button Installer or PC-BSD Installer) filename extension.

PC-BSD's own package management system resolves the issue of **library dependency problems that often occur on Linux based systems**. This is the feature that sets PC-BSD apart from most free open source systems that are available. It's easy, simple and straightforward.A PBI installs all software packages and libraries in their own self-contained directories in /Programs, decreasing confusion about where the binary programs reside and reducing the possibility of breaking a package if system libraries are upgraded or changed. The PC-BSD package manager also takes care of creating links in the KDE menu and on the KDE desktop.

[http://docs.pcbsd.org/guide/chap1.1.html#17PackageManagement](http://docs.pcbsd.org/guide/chap1.1.html#17PackageManagement)


why i need this?

because in my country **80% of the population does not have internet**. Most can't even afford dial-up.

In fact many have trouble just getting an old used sub $100 pc or even food.

i need **portable apps** for the population that work in either ubuntu 5.04 or 9.10 regardless.

---

### Post by geoken on 2008-05-29
It basically sounds like a portable-type app. A lot of Mozilla apps seem to be similar to this. Basically you extract and archive and can just run the app because all dependencies are inside that archive.

I think it sounds like a great idea. I couldn't care less if an app's size grew from 3mb to 20mb due to redundant libraries being included in the package.

This whole issue just makes me think of the post the other day where someone was talking about how the Windows port of KDE4 was easier to install than the Linux version. This too is related to the fact that Windows apps have all their libraries bundled in. This is mostly due to the fact that Windows lacks a package manager which it would use to get dependencies so apart from making users hunt the libraries down on the internet, bundling them into the installer is the only option. Of course this has the side effect of making apps whose dependencies are hard to find infinately easier to install on Windows.

---

### Post by az on 2008-05-29
Gnu/Linux applications are compatible on the source level, not the binary level.

The disadvantages of binary-compatibility by far outweigh the small convenience.

The disadvantages of binary-compatibility are (but not limited to):
- increased complexity and difficulty to develop
- decreased performance
- increased opportunities for security exploits
- limits choice for the development and user since certain things must be "set in stone".
- etc...

---

### Post by geoken on 2008-05-29
> **az said:**
> Gnu/Linux applications are compatible on the source level, not the binary level.

The disadvantages of binary-compatibility by far outweigh the small convenience.

The disadvantages of binary-compatibility are (but not limited to):
- increased complexity and difficulty to develop
- decreased performance
- increased opportunities for security exploits
- limits choice for the development and user since certain things must be "set in stone".
- etc...

An archived application with a self contained 'libraries' folder which the app pulls it's libs from (rather than looking for these libraries in the default system paths) does not have to be a binary file. Songbird can run out of it's own directory immidiately after being un-packed, does this mean songbird is a big binary blob and I am not able to browse it's self contained libraries?

---

### Post by SunnyRabbiera on 2008-05-29
well personally resolving dependencies in a debian system is better then that in a rpm system in my mind...
The thing is that if there is a big giant package with all the dependencies included it could be more of a pitfall then a improvement.

---

### Post by FuturePilot on 2008-05-29
Sounds kind of like the way Windows works. Most all libraries are included with an installer.

---

### Post by geoken on 2008-05-29
> **SunnyRabbiera said:**
> 
The thing is that if there is a big giant package with all the dependencies included it could be more of a pitfall then a improvement.

Do you mean from a 'large filesize' point of view?

---

### Post by loell on 2008-05-29
> **geoken said:**
> An archived application with a self contained 'libraries' folder which the app pulls it's libs from (rather than looking for these libraries in the default system paths) does not have to be a binary file. Songbird can run out of it's own directory immidiately after being un-packed, does this mean songbird is a big binary blob and I am not able to browse it's self contained libraries?

a compiled application like songbird, do pull binary libraries from its base directory and subdirectory.

---

### Post by geoken on 2008-05-29
> **loell said:**
> a compiled application like songbird, do pull binary libraries from its base directory and subdirectory.

My point was that songbird has self contained libraries (inside it's folder structure, not compiled into the application itself) without the app itself being a large binary blob. The libraries may be binary (because the app runs without being compiled) but they are still there in a self contaiend folder structure. 

All I'm saying is that an app can be packaged with it's libraries without needing to have those libraries contained inside the main application as a binary.

---

### Post by loell on 2008-05-29
> **geoken said:**
> My point was that songbird has self contained libraries (inside it's folder structure, not compiled into the application itself) without the app itself being a large binary blob. The libraries may be binary (because the app runs without being compiled) but they are still there in a self contaiend folder structure. 

you meant not statically linked.

> **geoken said:**
> 
All I'm saying is that an app can be packaged with it's libraries without needing to have those libraries contained inside the main application as a binary.

yes, its all about redundancy vs dependency. imagine having to download the same libraries 100 times for those 100 apps, not only does it take a very huge space storage wise, it will also eat a lot of bandwidth from where it came from.

---

### Post by geoken on 2008-05-29
> **loell said:**
> 
yes, its all about redundancy vs dependency. imagine having to download the same libraries 100 times for those 100 apps, not only does it take a very huge space storage wise, it will also eat a lot of bandwidth from where it came from.

You're right. But sometimes it's worth the extra space/bandwidth. For example, I had to compile buzztard (a music creation app) the other day. It required the compilation of a couple libraries, and there were a few more optional libraries to get full functionality from the app. IIRC, the libraries were less than 100kb. In situations like that I don't think it would be a big deal to include them in a package considering their minimal size.

---

### Post by d.kusummmanth@gmail.com on 2008-05-29
> **madjr said:**
> i would like my .debs to include all the dependencies 

"***create once run anywhere .deb***"

i would like it to work in any version of ubuntu (from 5.04 to 20.10+)

sort off like .pibs in PC-BSD:
well first of all, its an interesting idea. But, u need to be clear about why u want all the dependencies to be bundled inside a .deb?

If u hv a strong enough reason, u can definitely tweak a linux OS to include ur own customised package manager, which has all th repositories incl. in the installation file for the software.

---

### Post by ssam on 2008-05-29
it would be handy if gdebi would accept a tar.gz that contained several deb files. one would be the master package, and the other would only be installed if needed.

---

### Post by madjr on 2008-05-29
> **loell said:**
> you meant not statically linked.



yes, its all about redundancy vs dependency. **imagine having to download the same libraries 100 times for those 100 apps**, not only does it take a very huge space storage wise, it will also eat a lot of bandwidth from where it came from.


-1

sorry but you're just over speculating with your imagination.

That never happened to me in my 10 years of using windows.

Mac uses this method too.

i have not seen anyone complain.

Usually Linux-only users (or linux purists) with a good internet connection seem to be the only ones over exaggerating how "things work" in other OSs.

anyway, a packagemanager is great but is useless without an internet connection.

imagine those OLPC kids trying to install programs in ubuntu (or other packagemanager centric distro) without internet... (and as you all know, where those kids live there's no internet, in fact they barely eat)

hmm, now i see why some governments were pushing for windows in the OLPCs. At least the apps are portable in windows

---

### Post by qazwsx on 2008-05-29
> **madjr said:**
> -1
imagine those OLPC kids trying to install programs in ubuntu (or other packagemanager centric distro) without internet... (and as you all know, where those kids live there's no internet, in fact they barely eat)

Debian releases huge bunch of CD images for offline purposes. Ubuntu should too do that for LTS releases. Works pretty well. Have you tried?

---

### Post by madjr on 2008-05-29
> **qazwsx said:**
> Debian releases huge bunch of CD images for offline purposes. Ubuntu should too do that for LTS releases. Works pretty well. Have you tried?

OLPC does not have a CD-rom

those kids will have **loads** of fun...

but am not just speaking of the ones in the repos, but all in general.

i.e. i want to give my friend XXXX apps in an usb stick, would he have to carry arround the **21 repo CD's** with him?

he has no internet and no cd-rom, but on windows this aint a problem for him.

is absurd to carry around 21 repo CDs just to install dependencies for 1 or 2 apps.

also a waste of time trying to download dependency after dependency of a dependency of a dependency (aka **dependency hell**, something common in linux if u have no internet)

apps in linux are just not portable. But no one care about the poor.

linux users just assume that everyone has an ADSL connection

---

### Post by bobbocanfly on 2008-05-29
One (annoying and clunky) way you could do it is to include pre-compiled binaries in the debian packaging and use a pre-inst script to install them via dpkg. It would work and be fairly simple to setup but if you are depending on a lot of libraries the resulting binary is going to be huge.

---

### Post by qazwsx on 2008-05-29
> **madjr said:**
> 
i.e. i want to give my friend XXXX apps in an usb stick, would he have to carry arround the **21 repo CD's** with him?

is absurd to carry around 21 repo CDs just to install dependencies for 1 or 2 apps.

LOL. When we are talking about DVDs it sounds much more reasonable. Or just one BluRay disk ;) (not for poors currently :(). And besides there is so called popularity contest in Debian so it is very unlikely you are going to need all of those CDs.

I don't think this is huge issue in OLPC. They have packaged an customized the best combination of software for target audience.

---

### Post by geoken on 2008-05-29
> **qazwsx said:**
> Debian releases huge bunch of CD images for offline purposes. Ubuntu should too do that for LTS releases. Works pretty well. Have you tried?


In my experience, the issues aren't even related to an internet connection or lack there of. It's more an issue of a dependency not being in the repo's at all. 

It usually seems to happen with less popular apps that are using an even less popular library for some core functionality. In many cases the author's themselves know that the dependency is un-popular and instruct users where to find it and how to compile it because it's almost certain it wont be in their repositories. In these situations it would be a lot easier for the library in question to be bundled in the deb.

I guess the best current solution is to set up a repository and host that uncommon dependency (which is usually what happens) but it would be cool if a standalone deb could do the same.

---

### Post by loell on 2008-05-29
> **madjr said:**
> -1

sorry but you're just over speculating with your imagination.

That never happened to me in my 10 years of using windows. 

not exagerating at all, if you are a software junky then you'd know.. 


> **madjr said:**
> 
Mac uses this method too.

i have not seen anyone complain.


that doesn't mean a problem doesn't exist in their package management style. and tell me, how many desktop environment macs have? and how many variants do they have?   yes exactly, they only have one, which makes dependencies a bit predictable.

> **madjr said:**
> 
Usually Linux-only users (or linux purists) with a good internet connection seem to be the only ones over exaggerating how "things work" in other OSs.

depends, on who you ask, but true purist would know the downside and the upside on package/software management on any OS,  usually the once exaggerating are those pundits.


> **madjr said:**
> 
anyway, a packagemanager is great but is useless without an internet 
connection. 

imagine those OLPC kids trying to install programs in ubuntu (or other packagemanager centric distro) without internet... (and as you all know, where those kids live there's no internet, in fact they barely eat)
  

like others have said you can put the entire repo to a DVD, so that's not true.

> **madjr said:**
> 
hmm, now i see why some governments were pushing for windows in the OLPCs. At least the apps are portable in windows

i'm not sure if you're really following the OLPC saga, but portability is not the reason.

---

### Post by smartboyathome on 2008-05-29
One way to do this is to set up a repo on that USB drive and then you can add programs to the repo. When you plug it in to a friend's machine, just use the repo on your usb drive (/media/whatever) as a repo in synaptic.

---

### Post by loell on 2008-05-29
the original question wasn't address yet, because of opposing views ;)


the answer is

Yes, you can build a deb package with all included dependencies, very doable but not recommended. that is if you know very well on where/what environment it is specifically deployed.

---

### Post by SunnyRabbiera on 2008-05-29
> **geoken said:**
> Do you mean from a 'large filesize' point of view?

yes, as with the current system if you have a slower connection you can download the packages separate if needed.
What there needs to be though is a middle ground between something like a windows executable and a debian installer file.
A installer that works simular to windows .exe in the manner of selecting what comes with the installation (a good example is how microsoft office or seamonkey is set up on windows, you can pick and choose what is installed with the application or not... a basic install, a full install and a custom install, thus lowering the size of the package.
But it also needs the ease of update that a debian system does, something that updates when the repositories are updated thus eliminating the need to manually update each package... something I always liked in debian.

---

### Post by qazwsx on 2008-05-29
> **SunnyRabbiera said:**
> 
What there needs to be though is a middle ground between something like a windows executable and a debian installer file.

Autopackage.

[http://autopackage.org/](http://autopackage.org/)

Autpackage seems to be dead. I think it just showed us that there is not really need to use it.

Also there are even open soure games that uses .run/.bin way of static installation and usually comes with simple GUI. Usually those packages just work and even asks where to extract the components (I recommend home folder and hidden directory to be safe side).

---

### Post by geoken on 2008-05-29
> **smartboyathome said:**
> One way to do this is to set up a repo on that USB drive and then you can add programs to the repo. When you plug it in to a friend's machine, just use the repo on your usb drive (/media/whatever) as a repo in synaptic.

It would be cool if there was a way this process could become single click. Like packing the whole repository into a single package, then having gdebi recognize the nature of that archive and having it realize that it should treat it as a repository and attempt to look for dependencies inside it (if they aren't already installed or available through the normal software channels).

---

### Post by Polygon on 2008-05-29
isnt there an option to make like a repo on a cd? you can also mirror the ubuntu repos if you really want to and have a offline repo for yourself.

---

### Post by madjr on 2008-05-29
> **loell said:**
> > 
sorry but you're just over speculating with your imagination.

That never happened to me in my 10 years of using windows.

not exagerating at all, if you are a software junky then you'd know.. 

hmm i was a software junkie in windows. In fact i reviewed and tested tons of software back then for local use.

still didn't really had a problem.

anyway, this is what i love about package-managers in linux. 

This problem would not happen if i use .debs, because if i install a dependency once it will use it for other programs and not make copies of it.

but i don't know if it supports having different versions of the same dependencie i.e. v1.9 and v2.3 of X dependency/library.

> **loell said:**
> 
like others have said you can put the entire repo to a DVD, so that's not true.


in reality is like 4 or 5 DVDs for the repos

but my friend has an old lap with no DVD/CD player.

he only has a 256mb usb stick... (that's what he can afford)

portable linux apps is a project so linux can get adopted in developing nations.

We're striving to get some **government officials** interested in linux **instead of windows**, but Linux is **too internet dependable**.


> **loell said:**
> 
i'm not sure if you're really following the OLPC saga, but portability is not the reason.


**portability of apps is a big concern** over here.

In fact linux hasn't been mass deployed in this country thanks to this. Since windows still shines in that area.

internet is scarce in a 3rd world country. Even slow winmodem dial-up

**is like linux was made for medium and high class societies.**

---

### Post by Lostincyberspace on 2008-05-29
you could use Apt-OnCd install what you need for the other computers then run AptOnCD it is in the repositories and will make a copy of all you none original programs (+dependencies) in a apt cd so you can place it in and ubuntu will recognise it and you can use it to install from instead of internet or what ever else.

---

### Post by geoken on 2008-05-29
> **Polygon said:**
> isnt there an option to make like a repo on a cd? you can also mirror the ubuntu repos if you really want to and have a offline repo for yourself.

Is there currently a way to use this as elegently as a .deb? A deb is a quick, on click proccess. 

To the best of my knowledge the repo on a medium solution requires adding the repo, then searching it. It's still pretty simple, but it's not on the same level as .deb installs.

---

### Post by Lostincyberspace on 2008-05-30
the debs are contained on the disk if you want you could just take the debs? But the disk is easier.

---

### Post by madjr on 2008-05-30
> **Lostincyberspace said:**
> you could use Apt-OnCd install what you need for the other computers then run AptOnCD it is in the repositories and will make a copy of all you none original programs (+dependencies) in a apt cd so you can place it in and ubuntu will recognise it and you can use it to install from instead of internet or what ever else.

am aware of aptoncd, but is only good for moving updates around. It can be a bit complicated and lengthy (we already tried it and use it only for updates). 


the government officials want portable apps.

1 click install apps without depending on internet access.

**big .debs with all dependencies** would do the job, but i don't know how to get all the dependencies inside it.

also, most of the ubuntu PCs may not be upgraded. So the .debs need to work in any version of ubuntu (present 8.04 and future 8.10, 9.04, etc. )

---

### Post by geoken on 2008-05-30
> **Lostincyberspace said:**
> the debs are contained on the disk if you want you could just take the debs? But the disk is easier.

But the point is that the debs on the disk require more than a simple double click if you want to use that disk to satisfy dependencies. If you just click a deb on the disk, gdebi is going to run the deb then complain about missing dependencies (unless you edited your sources list to include the disk). What I'm saying is that there should be a archive, similar to a .deb, which contains all the dependencies in it. The archive could let gdebi know which deb is the main app, and gdebi will know that when it's dealing with that filetype it should look inside the archive for .deb's of the dependencies.

---

### Post by loell on 2008-05-30
> **madjr said:**
> 
portable linux apps is a project so linux can get adopted in developing nations.

We're striving to get some **government officials** interested in linux **instead of windows**, but Linux is **too internet dependable**.


**portability of apps is a big concern** over here.

In fact linux hasn't been mass deployed in this country thanks to this. Since windows still shines in that area.

internet is scarce in a 3rd world country. Even slow winmodem dial-up

**is like linux was made for medium and high class societies.**


guess what, over here we adopted debian to lower much the cost of our weather forecasting system, and because i'm still in a third world too as i can still remember we have the same problem as yours. public schools are using edubuntu even with slow internet connection.

so I guess it will just depend on those people in our respective government then,  one must be alarmed if a government official says we want portability and yet doesn't know what that word means. portability has nothing to do with package management.

---

### Post by madjr on 2008-05-30
> **loell said:**
> guess what, over here we adopted debian to lower much the cost of our weather forecasting system, and because i'm still in a third world too as i can still remember we have the same problem as yours. public schools are using edubuntu even with slow internet connection.

so I guess it will just depend on those people in our respective government then,  one must be alarmed if a government official says we want portability and yet doesn't know what that word means. portability has nothing to do with package management.

yea we're trying to push it in schools and public institutions. Most have internet access, so is not too trivial (if it gets accepted).

but our main goal is to get many local vendors to pre-install ubuntu.

but most don't want, thanks to the problems of portability the low internet access to the main public. Essential to install drivers and apps from the repos.

Some have tried, even included the DVD packs, but has not worked out well. Swapping dvds is what confuses them. Also, the discs get damaged very easily. 

once we resolved these issues we'll have another shot at getting it mass accepted.

still we don't want to wait for the debian guys to fix this problem any time soon. Since **they don't consider it a priority**.

We'll be re-packaging the .debs ourselves to get all dependencies in 1 tar file (if we can).

If everything goes well we might even publish it on the internet for everyone to benefit.

but still we don't have much info at doing this.

---

### Post by az on 2008-05-30
> **madjr said:**
> 

internet is scarce in a 3rd world country. Even slow winmodem dial-up

**is like linux was made for medium and high class societies.**

It's cheaper to provide broadband internet access than to provide optical media and optical readers to all the hardware.  DVDS are a thing of high class societies.  

> **qazwsx said:**
> Autopackage.

[http://autopackage.org/](http://autopackage.org/)

Autpackage seems to be dead. I think it just showed us that there is not really need to use it.


I think autopackage showed that you can't impose one way of doing things upon the whole free-libre open source community.  Autopackage requires all of upstream to use its libraries.

---

### Post by loell on 2008-05-30
> **madjr said:**
> 
We'll be re-packaging the .debs ourselves to get all dependencies in 1 tar file (if we can).

If everything goes well we might even publish it on the internet for everyone to benefit.

but still we don't have much info at doing this.



nteresting!! :)

yes, you most certainly can do it like that..

it would be easier if its just selected apps, one for each purpose.  

doing this would be tedious unfortunately, but nevertheless doable.

you can have an installed vanilla debian , download an application, then get those cached debs and pack it as tar. that should get all the dependencies thats needed for a certain application.

---

### Post by InfinityCircuit on 2008-05-30
The answer to this question is of course.  It's trivial to do this.  If you want an idea how to structure the debian/rules file a good example is the package dwm-tools.  There is no need to make a .tar.gz of all the debs.  You can very specifically state the order of installation for each binary in order to avoid dependency problems.

---

### Post by madjr on 2008-05-30
ok, thanks guys for the good ideas

i think pretty soon we'll have a good way at doing this. Fast, easy and probably automated.

We don't want to reinvent the wheel, so we're going to use what's already available. 

i already have a few people willing to help with all the work. It will take a long time, but the sooner the better
 
keep those ideas rolling in :)

---

### Post by hammer v2 on 2008-06-01
Yo DUDE!!

I'm so with you on this. I've almost got a solution for you too. I've been working a a bash script that creates install files for ubuntu. I've just about finished it. Please PM me!!! 

I had the same problem when trying to introduce Ubuntu to Laos.

H.

---

### Post by mohanohi on 2009-06-18
hey hammer.. i am interested..

---

### Post by Sublime Porte on 2009-06-19
The best way would be to distribute the debs of the dependancies along with your program. dpkg will look in the same folder for dependancies, so does Gdebi I think. This is actually not all that different to how a lot of programs are installed in Windows. They contain a lot of other files along with the installer, and the installer installs them all.

Another option is to create a composite deb, which basically means when you create your deb, you can also package in the contents of the other debs, but this messess up the packaging system a bit.

Or the third option, compile it statically, so it doesn't need extra libraries.

---

### Post by VincenzoDentamaro on 2009-06-23
Hello to all.
I am promoting my idea (SFS Technology) to resolve this problem.
The idea is explained here:
[[IMG]http://brainstorm.ubuntu.com/idea/20108/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20108/)

If you agree vote it!

---

