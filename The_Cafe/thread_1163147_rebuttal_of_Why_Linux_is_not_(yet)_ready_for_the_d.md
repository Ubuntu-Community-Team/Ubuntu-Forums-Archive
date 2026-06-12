---
title: "rebuttal of: Why Linux is not (yet) ready for the desktop"
date: 2009-05-18
forum: The Cafe
---

### Post by gnomeuser on 2009-05-18
[This atrocity of lies and half truths](http://linuxfonts.narod.ru/why.linux.is.not.ready.for.the.desktop.html) hit slashdot earlier.

0. Let's grant this premise even if it's both bleak and unlikely for software patents. Additionally it is forgotten that one can be commercial and Open Source, many companies do this.

1.  Learn to love Pulseaudio, while not yet perfect it is paving the way towards that solution. Not labeling this as in progress is extremely dishonest.

1.1 See 1., once PA is in place we have a very sane set of volume controls available to us.

1.2 See 1. and 1.1

1.3 See 1. - 1.2, also file bugs

2. supposed X problems

2.1 An outright lie, GTK has been API stable for years and the new plan for GTK3 and beyond still sets API stability as an important goal.

2.2 Not citing measurements and methodology is dishonest

2.3 Pass (I don't know enough about the internals of toolkits to give a full and accurate answer for this)

2.4 fontconfig bitching

2.4.1 funny when I change the hinting defaults in GNOMe they are applied instantly. I'll call bogus or at least demand additional data here.

2.4.2 Only works in every modern toolkit yes, but applications written using those make up every preinstalled application on most distros (not citing data here, I welcome people to poke holes in this assumption).

2.4.3 Ugly is subjective.

2.4.3.1 I assume he means disabling subpixel hinting by default and not shipping the patented parts of freetype/cairo enabled. The first one is untrue for Ubuntu (Fedora ships with sph disabled though) the second one is grounded in legal reasons.

2.5 Pass (I don't know enough about the internals of toolkits to give a full and accurate answer for this)

3. The downfall through prolification fallacy

3.1 See [Augeas](http://augeas.net/). Not labeling this as in progress is also dishonest. Aside that for most users no configuration is needed, where we can we autodetect correct settings or pick sane defaults.

3.2 Meet [PackageKit](http://packagekit.org/) works on all major distros and is getting very mature. This is solely about installation and package management. 

3.3 Packaging itself is another problem however that can be left up to distributions who have shown themselves quite capable of packaging pretty much everything. Smaller distros will not have the manpower to package everything but most distros today based themselves on distros with a large package base. openSUSE, Fedora and Ubuntu all have tens of thousands of packages as well as an eager community to do this work for you. More unification would be nice though but not likely for the near future.

3.4  If you absolutely must, the LSB defines a set of standards you can rely on for this development. As does FreeDesktop.org for higher level desktop tasks. I agree more standardization is good however I do not believe that a 100% frozen API for all time is a good idea.

4. I'll grant him this with the modification that most things today can be set without opening a terminal for many users. Work is in progress, there is also long standing tools like YaST to fill this hole.

5. Whining over marketshare and misunderstandings of FLOSS.

5.1 For highly specialized applications this is true but for a surprising amount of common real world tasks it is not only false but you are offered choice between a range of applications. This will always be the case but as more long tail software gets written using .NET porting will be a minimal effort (Novell e.g. does good business helping vendors move to Linux this way).

5.1.1 I believe this to be a minor subset of users compared to mom and pops who do wordprocessing, browsing, photo editing, chatting and email. I believe this group to make up a larger part than the group mentioned in this item by the author. As these guys move over a larger market is created for vendors to port this applications. For 3D animation e.g. it is also untrue, while 3D studio max might not be here, major hollywood companies do all their work on Linux desktops (Madagascar e.g. was done entirely in a GNOME environment running on Linux using specialized applications).

5.2 There are lots of games for Linux, sure we might not have World of Warcraft but we have many games and the selection of titles is growing. Steam is even said to be ported to Linux soon giving us a deployment channel for both major players and indie game producers.

5.3 Drivers are a problem, but out of the box no OS supports more hardware than Linux. We are closing the gap for video drivers and plugging holes in ALSA as I type this. Not labeling this in progress is utterly dishonest.

5.3.1 Pass (Every printer I have owned worked under Linux, but I don't feel confident enough to give an answer on this one).

5.3.2 True, but with hefty modifications. Recently the uvcvideo driver set was merged into Linux and this brought with it a lot of support. We are expanding every day plus the Linux Driver Project will happily write the driver for vendors for free, under NDA. All we need is specifications. In progress, not labeling it as such is also dishonest.

5.4 True, but ffmpeg amongst other projects have pledged to add blu-ray support. I doubt this one will stand for long.

5.5 Total bogus (with reserve). The legal status is not questionable for codecs, they are illegal to install where software patents exist due to license violations. However more and more vendors move towards open standards and till then you can buy supported, legal codecs from companies like [Fluendo](http://www.fluendo.com).

6. Regression testing is performed with every kernel, distros like ubuntu have automated crash reporting as well as hardware testing. There are tools to test suspend and resume. We can do better but regression testing on a scale as massive as every hardware configuration out there will be lacking regardless of how much effort you put into it. We are getting better, the tools are there and distros do consider it a priority. Tools are also present today such as Smolt to show us which setups are the most used to help us target regression testing. True but the goal is unrealistically set.

7. We have bugs, all software has bugs. There will be a few that never get worked on unfortunately but of those filed a decade ago how many are still valid or relevant given the pace of development I wonder. True, but the goal is set unrealistic, no project will ever realistically reach zero bugs.

8. Examples?

9. True, performance testing for desktop use could definitely improve. However using OpenOffice as the example is picking the worst possible case as it uses a non native toolkit, reinvents a lot of wheels and so on. Still it has gotten better over time, Michael Meeks e.g. has done some amazing optimizations. I will grant that we should if possible focus more on getting proper tracing and a performance regression testing done. Tracing is in progress and many projects have regression testing now e.g. Banshee and when major problems occure users tend to complain followed by fixes being commited.

9.1 Lacks data, also [largely solved](http://google-opensource.blogspot.com/2008/04/gold-google-releases-new-and-improved.html) - I assume he means a gcc linker but we have many linkers mono has a linker as well e.g. which performs quite nicely as I understand. The problem is poorly defined.

9.2 Parallel boot has not been shown to decrease boot time, e.g. Moblin' impressive 5 sec boot from bootloader to usable gui was specifically done without parallization for performance reasons. Aside that most major distros today ship a parallel capable bootsystem (upstart e.g. is parallel capable and deployed in Ubuntu as well as Fedora just to mention two major distros). Untrue and a false assumption.

9.3 Lacks data but tends to be true in my experience. Work to be done. As suspend becomes more reliable one could question if shutdown will be as large as problem space as it is now though. Still worth fixing and being worked on (Fedora e.g. has work ongoing to fix this).

10. It depends, you really don't want users to see all manners of errors. Varnish has a good approach where it just displays "guru meditation error" with an error code admins can look up in their logs. An error message needs to be translated and it might not always make sense to users. Instead we could do better capture tools to report bugs. I am unconvinced that heaping on more and more error dialogs will be the best way to solve this.

11. True, at least for many projects. This is a good entry point for users to get involved though. The Fedora documentation project has good experiences with this. I believe such effort could do with more PR at least and yes we could do with better documentation at all levels. True but also true for most non-Linux deployments.

12. SELinux protects against many attack vectors. As does AppArmor and every one of the 3 major distros deploys one of these solutions by default. Linux has a very strong security framework along with proactive security enhancements. I feel unqualified to speak to specific threats but in general we have very strong security available to us along with a much better patch rate and a shorter patch cycle than Windows([Mark Cox' blog is good reference for this data](http://www.awe.com/mark/blog/)).

13 API/ABI complaints

13.1 GNOME 2.x has been API compatible since June 2002 till now and we are only just breaking API. There are good reasons to not keep certain APIs stable such as in-kernel APIs but aside that the major desktop environments have strict API stability requirements for the duration of each major cycle. There are reasons why we change APIs and it is not done lightly, there are also many projects where keeping the APIs stable is a primary concern to say that as a whole Linux doesn't care about these things or engineering solutions that are forward looking is false.

13.2 True, see 13.1. Not all APIs will or should remain stable at all times aside that compatibility libraries are options, as is static compilation. I assume we are talking about situations where source is not available in which case static compilation is the safest option (if licenses are a problem for this solution, often asking politely for an exception or a license change very often works).

13.3 Companies like the one referenced are most welcome to file bugs. I don't see the blog referencing any of the bugs they hit, I am sure they are there - no software is flawless. I am unsure what the actual complaint is here, that libraries are software and thus have bugs?
(please note we are at item 13.3, near the end and this is the first reference given in the entire article)

14. Enterprise woes

14.1 Unsure what he even means with this. Companies like Red Hat specifically offer products with strong API/ABI policies with up up to a decade of support. The complain needs to be specified with an example.

14.2 Every enterprise distro has it's distribution channel, Red Hat network, Novell has it's thing and Canonical has Landscape. If you want to deploy a single application often the best option that is the least support burden for you is a software appliance. It depends on your needs if this is a problem. Yes it would be nice if we have the one true distribution method, and in part we do, source code but work is being done on such management (see [Spacewalk](http://www.redhat.com/spacewalk/) - there is no reason why this could be extended to support multiple distributions). If the complaint is that everyone uses their own packaging format and package manager then yes, it is a problem but often the solution is as simple as asking someone to do the hard work of packaging it and accepting bugs, trusting them to do good work and accepting bugs. The way into RHEL e.g. goes through Fedora.

---

### Post by Regenweald on 2009-05-18
That you read all of that then put in the time and effort to offer a rebuttal based on fact......you have my kudos.

---

### Post by gnomeuser on 2009-05-18
> **Regenweald said:**
> That you read all of that then put in the time and effort to offer a rebuttal based on fact......you have my kudos.

Some valid points but on the whole it annoyed me to read his list so I decided to spend a couple of hours putting up a rebuttal. I figured someone was bound to post the original one so it is nice to have preemptive addressed most of the points.

Btw. if I am wrong I will be happy to stand corrected or debate my answer. 

I know that the references can be clearer, I will expand them as I go along. There is additionally some research I need to do on the toolkit questions were I admit I don't know enough to make a definitive reply.

---

### Post by Tipped OuT on 2009-05-18
Nice post, although it's too much for me to read at the moment, just woke up. :|

---

### Post by BuffaloX on 2009-05-18
©2009 Artem S. Tashkinov - All rights reserved. No reproduction of any kind is allowed without express permission by the author. [Yandex counter]

Yeah thats the spirit. :p

---

### Post by Corelogik on 2009-05-18
Sounds to me like someone whining mostly about Linux's lack of Windows features,... go figure.

I almost spewed the morning coffee all over the monitor when I read that Linux isn't secure,...

---

### Post by days_of_ruin on 2009-05-18
> **BuffaloX said:**
> ©2009 Artem S. Tashkinov - All rights reserved. No reproduction of any kind is allowed without express permission by the author. [Yandex counter]

Yeah thats the spirit. :p

Makes it look like he is just an anti-FOSS troll. Which he probably is.

---

### Post by Wiebelhaus on 2009-05-18
Wow man , the haters are having fits and the more this thing gains in popularity the more angry they are going to become , I've said this many times , Pay them no mind.

---

### Post by swoll1980 on 2009-05-18
A bunch of your rebuttals refered to things that are not finished, PA, package kit. Wouldn't the fact that these solutions are not yet ready yet, only further prove the point that Linux isn't ready?

---

### Post by Screwdriver0815 on 2009-05-18
the only anti-Linux stuff which is worth reading is [http://linuxhaters.blogspot.com/](http://linuxhaters.blogspot.com/)

because this guy is swearing around like nothing else and this is funny.

But the guy who delivers the topic for this thread... even when he was right: so what? Who cares whether Linux is ready for the desktop? Nobody except maybe some companies who want to sell Linux to huge numbers of people.

But even the companies like Red Hat or Novel don't care because they make the money with enterprise solutions. As canonical tries too. 

I personally don't care anymore if there are new users coming from the windows-side. Sure, when they ask for support, I help where I can. I also contribute to the translations. But mostly only because its fun and a good thing to know that I have contributed to something useful.

So why should anyone care about FUD coming from someone who does not have a clue what he is talking about?

---

### Post by gnomeuser on 2009-05-18
> **swoll1980 said:**
> A bunch of your rebuttals refered to things that are not finished, PA, package kit. Wouldn't the fact that these solutions are not yet ready yet, only further prove the point that Linux isn't ready?

I don't disagree with him as such that we aren't ready, but I doubt any OS really is ready on all points. I think we have reached a point where most users can comfortably listen to music, play videos, browse the web and so on (ordinary tasks). There is a group of people we will never be ready for for various reasons but I believe the majority of all people would be fine on a Linux desktop.

Also being in progress doesn't mean it's hopelessly broken now, just that in some cases a few corners need to be polished. I am hestitant to call any bit of FLOSS totally finished. I would consider PackageKit and Pulseaudio pretty solid, there are problems with the backends, ALSA e.g. needs some fixing but for most setups now both are very nice. so his whole point of saying this is a mess is wrong, which is what I aimed to counter, we are aware that it's problematic, we have solutions and they are ready for deployment.

---

### Post by aysiu on 2009-05-18
I actually don't have beef with any of the original points. I just don't see how that necessarily leads to a conclusion of "Linux isn't ready for the desktop," especially when no one has put forth an agreed-upon definition of what "ready for the desktop" actually means.

Instead of using absolutely terms like "ready for the desktop" or "not ready for the desktop," I prefer to just know all the pros and cons of Windows, Mac OS X, and Linux and then recommend the most appropriate OS depending on the individual user's needs. Someone may need an SUV, and I may need a compact car... or I may not need a car at all.

Some people prefer Mac OS X. Some prefer or depend on Windows. Others prefer Linux. To each her own. Why make sweeping statements about what is absolutely ready or absolutely not ready?

---

### Post by swoll1980 on 2009-05-18
> **gnomeuser said:**
> I don't disagree with him as such that we aren't ready, but I doubt any OS really is ready on all points. I think we have reached a point where most users can comfortably listen to music, play videos, browse the web and so on (ordinary tasks). There is a group of people we will never be ready for for various reasons but I believe the majority of all people would be fine on a Linux desktop.

Also being in progress doesn't mean it's hopelessly broken now, just that in some cases a few corners need to be polished. I am hestitant to call any bit of FLOSS totally finished. I would consider PackageKit and Pulseaudio pretty solid, there are problems with the backends, ALSA e.g. needs some fixing but for most setups now both are very nice. so his whole point of saying this is a mess is wrong, which is what I aimed to counter, we are aware that it's problematic, we have solutions and they are ready for deployment.

That sums it up pretty nicely. I myself Have never had a problem with PA, but for some people it seems to be an absolute nightmare. Are these people exaggerating? Are these, so called nightmares, nothing more than maybe one program needed a setting changed for audio to work?

---

### Post by nitehawk777 on 2009-05-18
@aysiu....
> especially when no one has put forth an agreed-upon definition of what "ready for the desktop" actually means.

Excellent point!
 ...What do they actually mean when they say that, anyhow?  Is Windows all that "ready for the desktop"?   Oh well,..Linux is perfectly ready for MY desktop.

---

### Post by directhex on 2009-05-18
2001 is TOTALLY gonna be the year of the Linux desktop.

---

### Post by drawkcab on 2009-05-18
Ya, linux is ready for my desktop.

---

### Post by Bölvaður on 2009-05-18
omg omg omg I don't care.

omg omg omg):P

---

### Post by Arup on 2009-05-18
One thing is very clear, even with little penetration by Ubuntu and Linux in general in the desktop world has got the the rabid MS fanbois frothing and foaming in their mouth, imagine when the number would reach close to 30%. I guess we will see them doing all kinds of extreme acts against Linux users.

Linux has been on my desktop since last ten years, been dual booting but ended my Windows install last year and have never looked back. Never felt the need. I have installed Ubuntu on many ex Win users and not because I evangelize it, it was their voluntary request and guess what, every single one of them is happy with it and they have never looked back. Most of these persons have suffered virus attacks with their Win installs. Also they all were tired of seeing their Windows install come to a crawl after a year or so, desktop icons disappearing, programs just stop working and of course, the fiasco that comes with every service pack in Windows. So if Ubuntu is not desktop ready for myself or the others I install, I guess for some Windows worshippers, it never will be. Desktop ready to me means getting up, turning my PC on and doing what I intend to do instead of worrying about hacks, HIPS, AVs etc. Most security apps bring even top of the line Win systems to a crawl thereby negating any advanatage of using new hardware.

---

### Post by aysiu on 2009-05-18
> **nitehawk777 said:**
> @aysiu....


Excellent point!
 ...What do they actually mean when they say that, anyhow?  Is Windows all that "ready for the desktop"?   Oh well,..Linux is perfectly ready for MY desktop.
I created a little poll, and [as you can see the results are all over the place.](http://ubuntuforums.org/showthread.php?t=450676)

---

### Post by Saint Angeles on 2009-05-18
what did he mean by "very slow GUI except when being run with a compositing..."

what a minute! my gui is much more responsive when compiz is OFF! given the difference is negligible, the fact is that he really doesn't know what he's talking about.

"no standard way of software distribution"

WHAT?! ubuntu has synaptic and apt-get. wtf does windows have?! they have nothing.

(4) i've stated this on the forums many times, but i converted my sister and my mom to ubuntu and they know nothing about CLI but they are able to customize their own computers above and beyond anything they've ever done on windows!

and look at (3.2). he mentions deb, rpm, portage, tarballs, source... well windows has exe, msi, zip, and source as well..

ARGH

---

### Post by perce on 2009-05-18
I've been using Linux as my only operating system since 1996, why should I care about people telling me I have been wrong for almost 15 years?

---

### Post by monsterstack on 2009-05-18
> **perce said:**
> I've been using Linux as my only operating system since 1996, why should I care about people telling me I have been wrong for almost 15 years?

My brother delights in forwarding me links to news articles that predict doom and gloom for Linux adoption. I always tell him, "Yes, that's great. But why should I care? The number of Linux users has never dropped, and there are already enough of us to make sure it's a decent OS for me."

---

### Post by aysiu on 2009-05-18
It takes a great deal of naivete to believe that marketshare is directly correlated to usability.

If that were really the case *and* if Linux were truly "not ready for the desktop," then Microsoft would have no problem with OEMs selling Linux preinstalled with "[Our company] recommends Linux for home computing" at the top of every page of the website, leaving potential Windows users with only the ability to buy a Windows license individually and install and configure Windows themselves. And neither Apple nor Microsoft would see a point in creating advertisements bashing each other.

We know this isn't the case, though. We know people use what's familiar to them, what they've been told "everyone else" is using, what they see in stores for sale, what they've seen advertised. That's even a big reason why many Windows users have stuck with XP instead of upgrading to Vista--the fear of change, the fear of the unknown, the comfort of the familiar.

---

### Post by nolliecrooked on 2009-05-18
The default Sans font IS ugly without sub-pixel rendering. But then again most fonts look like crap without it. Just look at Verderna in IE6/7/8. 

It would also be nice if a distro/DTE could at least have a nice, professional looking default theme. KDE4 pulls this off pretty well.
One thing that has always bothered me slightly with linux icons is why things like my music dont have a default music icon? I know you can add one yourself if the icon set you have supports that, but even then GNOME wont show it in the tree view or the Places dropdown menu.

---

### Post by mysoogal on 2009-05-20
Linux Operating system is not ready for a normal User

1. firstly a Linux System such as Ubuntu or another Linux OS is depended on Open source software that is the main issue here Which i believe, in my opinion this creates unstable software releases as developers get bored, fed up or simply move on. When i say unstable do not misunderstand i mean this, new software developments that are being released for the Linux communicability are sometimes are incomplete and not released in a good way. something like that. 

2. is the normal user knowledge we can say that 90 % of the world have no experience with Linux operating system only that 10 % left presents the whole world wide users who are Linux experienced and have moved from Windows to Linux or started to use Linux directly. the issue here is also that most users are born into a windows operating system and will most probably stay their for whatever reason. i can name few such as windows provides much more open source projects and has a good installation environment, most users do not want for example " sudo apt-get install ffmpeg etc in the Terminal I'm sure most new users are not sure what and where the Terminal is. now on Windows this is completely different as a user just needs to download to desktop and double clicks, magically software package is installed." Linux can have the same thing if all software packages are released as debs. the other problem i believe creates much more issues are the Linux Users them self. they do not provide a easy way of understanding how a problem should be fixed, a good example could be found for the vlc which dims screen ! i have yet to follow a good tutorial which tells me how to fix this problem. some users post bad tutorials which can and possibly disable your screen or remove ubuntu-desktop altogether, which happens to me. all from some users on the forums. Linux does not have a wiki of fix this problem the Simple way ! you know with a screen dump step by step and explaining maybe other issue which could encounter during the fix.

3. have to say again that, there simply is to much Sudo commanding to get things running.

new users will most probably have problems with these soon as they installed a Linux system ubuntu 8.10 or 9.04 etc

flash player 10, video codecs, restricted drivers. etc and file permission most undoubtedly will be the main issue throughout their experience

4. the good thing about Linux, Ubuntu, its totally meant for a development and security usage. 

for me i could say its kinda same as a graphical telnet problem in windows lolz :KS


5. you can always teach a new user how things run in Linux. thats the last thing i wanted to say. I'm teaching my mother which uses ubuntu 8.10 on Eee PC. She knows pretty much what a normal user would want to do, Go visit you-tube, download clips. check email. connect laptop to HD TV through VGA, press super + 2 to zoom in-case something is blurry. 


....good luck, but please remember to not use taskile command it removed my ubuntu-desktop trying to uninstall Lamp-server :o

thats my experience, don't forget i started to use Linux for the first time just few months ago, so far i have about 12 % complete understanding how to fully use the operating system.

---

### Post by Buovjaga on 2012-04-05
2012 edition anyone?

[Why Linux is not (yet) Ready for the Desktop aka Linux problems, 2012 edition]("http://linuxfonts.narod.ru/why.linux.is.not.ready.for.the.desktop.current.html")
[Ingo Molnar: What ails the Linux desktop? Part I]("https://plus.google.com/109922199462633401279/posts/HgdeFDfRzNe")
[Ingo Molnar: What ails the Linux desktop? Part II]("https://plus.google.com/109922199462633401279/posts/VSdDJnscewS")

What was the name of that GNOME co-founder (?) who said breaking backwards compatibility is the reason Linux has been unsuccessful on the desktop?

Yeah.. I think the OP rebuttal is a bit silly. "This atrocity of lies and half truths" - a bit of a cultish reaction. Furthermore, Artem is not  an anti-FOSS troll, but a valuable asset to the Linux community and his observations should be seen as contributions and not bashing. He has been Linux-only since 1999, about the time I myself **stopped** using Linux.

[QUOTE="gnomeuser"]I think we have reached a point where most users can comfortably listen  to music, play videos, browse the web and so on (ordinary tasks). There  is a group of people we will never be ready for for various reasons but I  believe the majority of all people would be fine on a Linux desktop.[/QUOTE]
And now in 2012 we have reached a point where a desktop is not even needed for these tasks and tablets and smartphones have taken over the market for consuming-oriented behavior. So it's time to concentrate on the people doing actual work with their computers.
Fragmentation of systems and no backwards compatibility means companies don't want to invest in Linux versions of professional software. Open source equivalents of specific creative apps need to take their funding and marketing strategies to another level. Novacut video editor is a shining example (it's Linux-first, but many Mac users are desperately waiting for it).

---

### Post by MisterGaribaldi on 2012-04-05
Yawn. Embedded Linux and Linux-on-the-server are awesome. Come back to me when Linux is a drop-in replacement for Mac OS X or Windows desktops and then we'll talk.

Otherwise, and this is directed at the original discussion that the OP cited and not the OP himself, this is an old horse long since beaten to death.

---

### Post by nothingspecial on 2012-04-05
Old Thread.

Closed.

---

