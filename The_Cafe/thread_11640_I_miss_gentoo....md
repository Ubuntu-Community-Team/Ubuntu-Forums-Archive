---
title: "I miss gentoo..."
date: 2005-01-18
forum: The Cafe
---

### Post by jdong on 2005-01-18
I'm really missing the good old days of Gentoo... I restored my last image of Gentoo onto a 15GB partition, and I spent a few days in it over the long weekend. It emerge -uDav'ed perfectly to the latest stable-marked packages...

Now, I'm considering swapping Gentoo and Ubuntu, with Gentoo being primary and Ubuntu secondary. This will seem to be a permanent switch, unlike the Fedora, Suse, and FreeBSD ordeal!


I'm not going to stop contributing on this forum -- I'll be just as involved as before. I'll also continue backports. Why? 

1. Not everyone has a mighty Athlon64 to compile stuff with :). I'm fortunate to barely notice the compile times of Gentoo.

2. Not everyone likes the Gentoo experience. The install is too complicated and too long. Ubuntu's great -- in 30 minutes, I can get a system just the way I want it.

3. I have three workstations at school that run Ubuntu ONLY, and I still need backports for using those computers.


My switch to Gentoo again has been influenced by the following reasons. I feel quite a few can be addressed by the Ubuntu team.

1. Great support community. Just like this one. I won't compare the two -- I'm not saying one is superior to the other. It's just that whenever I need a question answered, the community has it!

2. Up-to-date software. Sure, I've improved the situation with Backports, but Gentoo is still farther ahead as to getting latest software out there.

3. Prompt security updates for ALL ebuilds. I have an Apache/PHP/Subversion server running, and a few components have to be pulled from Universe. I really wish for some security backing. With Gentoo, just keep an eye on a security site, then file a bugreport for anything found -- within hours, there will be a Gentoo patch. It takes little effort on the developers' side to get such fixes out. With Ubuntu, even when a Universe fix is easy, there's no place I'm allowed to even file a bug report. There's certain packages in universe that have blatant security issues, but no resolution.

4. Bigger variety of ebuilds, no need for 3rd parties. Primarily thanks to the ebuild mechanism, users fetch their own sources. Ebuilds are available for everything from sun java to Win32codecs and UT2004 and VMWare. Stuff like the marillat repository is in the past!

5. Programmer's hacking appeal. I'm a tweaker. I can't say otherwise. Gentoo ebuilds are simple to write and extremely convenient. I virtually write a shell script to unpack and copy files all over the / tree, while Gentoo **keeps track** of everything! With deb's, sure there's checkinstall, but it's not as flexible as ebuilds.

---

### Post by jdodson on 2005-01-18
[QUOTE=jdong]I'm really missing the good old days of Gentoo... I restored my last image of Gentoo onto a 15GB partition, and I spent a few days in it over the long weekend. It emerge -uDav'ed perfectly to the latest stable-marked packages...

Now, I'm considering swapping Gentoo and Ubuntu, with Gentoo being primary and Ubuntu secondary. This will seem to be a permanent switch, unlike the Fedora, Suse, and FreeBSD ordeal!


I'm not going to stop contributing on this forum -- I'll be just as involved as before. I'll also continue backports. Why? 

1. Not everyone has a mighty Athlon64 to compile stuff with :). I'm fortunate to barely notice the compile times of Gentoo.

2. Not everyone likes the Gentoo experience. The install is too complicated and too long. Ubuntu's great -- in 30 minutes, I can get a system just the way I want it.

3. I have three workstations at school that run Ubuntu ONLY, and I still need backports for using those computers.


My switch to Gentoo again has been influenced by the following reasons. I feel quite a few can be addressed by the Ubuntu team.

1. Great support community. Just like this one. I won't compare the two -- I'm not saying one is superior to the other. It's just that whenever I need a question answered, the community has it!

2. Up-to-date software. Sure, I've improved the situation with Backports, but Gentoo is still farther ahead as to getting latest software out there.

3. Prompt security updates for ALL ebuilds. I have an Apache/PHP/Subversion server running, and a few components have to be pulled from Universe. I really wish for some security backing. With Gentoo, just keep an eye on a security site, then file a bugreport for anything found -- within hours, there will be a Gentoo patch. It takes little effort on the developers' side to get such fixes out. With Ubuntu, even when a Universe fix is easy, there's no place I'm allowed to even file a bug report. There's certain packages in universe that have blatant security issues, but no resolution.

4. Bigger variety of ebuilds, no need for 3rd parties. Primarily thanks to the ebuild mechanism, users fetch their own sources. Ebuilds are available for everything from sun java to Win32codecs and UT2004 and VMWare. Stuff like the marillat repository is in the past!

5. Programmer's hacking appeal. I'm a tweaker. I can't say otherwise. Gentoo ebuilds are simple to write and extremely convenient. I virtually write a shell script to unpack and copy files all over the / tree, while Gentoo **keeps track** of everything! With deb's, sure there's checkinstall, but it's not as flexible as ebuilds.[/QUOTE]


[http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

could this ease your gentoo addiction :mrgreen:

---

### Post by jdong on 2005-01-18
cool & all, but definitely doesn't solve all of my addiction :)

---

### Post by poofyhairguy on 2005-01-18
[QUOTE=jdong]I'm really missing the good old days of Gentoo... I restored my last image of Gentoo onto a 15GB partition, and I spent a few days in it over the long weekend. It emerge -uDav'ed perfectly to the latest stable-marked packages...

Now, I'm considering swapping Gentoo and Ubuntu, with Gentoo being primary and Ubuntu secondary. This will seem to be a permanent switch, unlike the Fedora, Suse, and FreeBSD ordeal!


I'm not going to stop contributing on this forum -- I'll be just as involved as before. I'll also continue backports. Why? 

1. Not everyone has a mighty Athlon64 to compile stuff with :). I'm fortunate to barely notice the compile times of Gentoo.

2. Not everyone likes the Gentoo experience. The install is too complicated and too long. Ubuntu's great -- in 30 minutes, I can get a system just the way I want it.

3. I have three workstations at school that run Ubuntu ONLY, and I still need backports for using those computers.


My switch to Gentoo again has been influenced by the following reasons. I feel quite a few can be addressed by the Ubuntu team.

1. Great support community. Just like this one. I won't compare the two -- I'm not saying one is superior to the other. It's just that whenever I need a question answered, the community has it!

2. Up-to-date software. Sure, I've improved the situation with Backports, but Gentoo is still farther ahead as to getting latest software out there.

3. Prompt security updates for ALL ebuilds. I have an Apache/PHP/Subversion server running, and a few components have to be pulled from Universe. I really wish for some security backing. With Gentoo, just keep an eye on a security site, then file a bugreport for anything found -- within hours, there will be a Gentoo patch. It takes little effort on the developers' side to get such fixes out. With Ubuntu, even when a Universe fix is easy, there's no place I'm allowed to even file a bug report. There's certain packages in universe that have blatant security issues, but no resolution.

4. Bigger variety of ebuilds, no need for 3rd parties. Primarily thanks to the ebuild mechanism, users fetch their own sources. Ebuilds are available for everything from sun java to Win32codecs and UT2004 and VMWare. Stuff like the marillat repository is in the past!

5. Programmer's hacking appeal. I'm a tweaker. I can't say otherwise. Gentoo ebuilds are simple to write and extremely convenient. I virtually write a shell script to unpack and copy files all over the / tree, while Gentoo **keeps track** of everything! With deb's, sure there's checkinstall, but it's not as flexible as ebuilds.[/QUOTE]

Hey, thats fine. If Gentoo fits you best, then have at it! Just expect to still be bugged about backports! (especially when Hoary releases).

---

### Post by jdong on 2005-01-18
I feel like being lazy right now. I'll make the switch when I have plenty of free time. :)

---

### Post by poofyhairguy on 2005-01-18
[QUOTE=jdong]I feel like being lazy right now. I'll make the switch when I have plenty of free time. :)[/QUOTE]

Thats the whole thing with Gentoo. Its as good as the amount of free time you have!

---

### Post by jdong on 2005-01-18
Ok, I'm running Gentoo right now, keyword x86 except for selective ebuilds (much more conservative than I was running prior to Ubuntu). Ubuntu made me value stability a lot more.


Building bluefish backports too, lol.... Who wants to help me with magnetic flux??  :mrgreen:

---

### Post by Xian on 2005-01-18
I've run Gentoo before, and have nothing to say against it at all. It is a superb distro. 
But...it has a very certain way of swallowing you.

Alas, I've crawled out of the mouth and I won't go back there again. :)

---

### Post by nocturn on 2005-01-19
[QUOTE=Xian]I've run Gentoo before, and have nothing to say against it at all. It is a superb distro. 
But...it has a very certain way of swallowing you.

Alas, I've crawled out of the mouth and I won't go back there again. :)[/QUOTE]

I liked Gentoo too.  Although I must admid that in the last month I saw more breakage then is good for me (hotplug/coldplug, cyrus imap, ...).

Apart from the compile times (which became unacceptable for my desktops - KDE, OpenOffice, ... -  but are OK on my X-less server), the amount of fixing after emerge world was getting to high.

Ubuntu is very nearly ready for the server, but it needs all packages one needs for that server to be in main (security).

For me that is not the case now (I use Kerberos and libpam-krb5).

---

### Post by shmonkey on 2005-01-19
IMHO Gentoo as gone a bit down hill Quality wise since about 6 months ago. I am talking about running stable too ! recently a GCC update cuased a lot of problems. I was finding that more anf more apps were failing to compile (QT included) even though I was using very conservative CFLAGS. 
I borked my system with "emerge depclean" (my fault, I should have checked more carefully). That said, because I try a lot of apps out, I need a reliable method of uninstalling orphaned libraries and I'm afraid "emerge depclean" is too unreliable.
I have found deborphan to be a very reliable wat of uninstalling orphaned libraries.

So I did not want to compile another system so I switched to Ubuntu, things are working out good so far  8-) 

I hope Gentoo does improve again as I really enjoyed using this distro.

I do miss Gentoo's init system and excellent tools though.

---

### Post by Daniel G. Taylor on 2005-01-19
[QUOTE=shmonkey]IMHO Gentoo as gone a bit down hill Quality wise since about 6 months ago. I am talking about running stable too ! recently a GCC update cuased a lot of problems. I was finding that more anf more apps were failing to compile (QT included) even though I was using very conservative CFLAGS. 
I borked my system with "emerge depclean" (my fault, I should have checked more carefully). That said, because I try a lot of apps out, I need a reliable method of uninstalling orphaned libraries and I'm afraid "emerge depclean" is too unreliable.
I have found deborphan to be a very reliable wat of uninstalling orphaned libraries.

So I did not want to compile another system so I switched to Ubuntu, things are working out good so far  8-) 

I hope Gentoo does improve again as I really enjoyed using this distro.

I do miss Gentoo's init system and excellent tools though.[/QUOTE]
 That's funny because I switched from Gentoo to Ubuntu about six months ago and haven't looked back once (though I still help out with [Porthole](http://porthole.sf.net) occaisionally).

The distribution is fine but when I left Portage was... interesting (talking as a developer who worked with a lot of low-level Portage internal stuff). jstubbs, carpaski, and a few others have done a lot of good work since then, though.

The main reason I left was that I am spending less time on the computer and more time working on finishing my degree and doing "family" things. I bought an iBook and now run OSX on it with Ubuntu on my desktop, and need to use both to get things done. With Gentoo, I also got things done, but it took longer, and to be honest I've got reiser4, Xorg (with fixes/damage/compositing), GNOME 2.9.4, udev+hal+dbus+g-v-m, and other goodies right here with Ubuntu. It takes me minutes rather than hours to update (try emerge updating GNOME and Xorg in Gentoo). It Just Works for me.

Now, to be fair I don't yet know enough about Debian's package manager and tools. Hopefully I'll really get into it at some point.

---

### Post by jdong on 2005-01-19
Screw this... I'm reverting back.

Two days, already they broke a stable MySQL. This ain't reliable.


With Hoary, I'll try harder with Universe security backports.


I'll be back in Ubuntu by the end of the week.

---

### Post by poofyhairguy on 2005-01-19
[QUOTE=jdong]Screw this... I'm reverting back.

Two days, already they broke a stable MySQL. This ain't reliable.


With Hoary, I'll try harder with Universe security backports.


I'll be back in Ubuntu by the end of the week.[/QUOTE]


Yea! I knew you couldn't stay on the other side, when Hoary is so close to release!


After you see how Ubuntu "just works," its hard to do it the other way!

---

### Post by poofyhairguy on 2005-01-19
[QUOTE=Daniel G. Taylor]. With Gentoo, I also got things done, but it took longer, and to be honest I've got reiser4, Xorg (with fixes/damage/compositing), GNOME 2.9.4, udev+hal+dbus+g-v-m, and other goodies right here with Ubuntu. [/QUOTE]

Hmmm. This reiser4 sounds cool....I'm making a new install soon, I want to try it!

---

### Post by TravisNewman on 2005-01-19
You can do reiser4 in Ubuntu, though it's not as easy.

Seriously jdong, you should just accept the fact that you'll never be happy with another distro since you've used Ubuntu ;)

---

### Post by jdong on 2005-01-19
[QUOTE=panickedthumb]You can do reiser4 in Ubuntu, though it's not as easy.[/QUOTE]


If you could set up Gentoo, you can compile a reiser4 kernel and copy a filesystem. Hint: LiveCD, then rsync -av --progress /mnt/old_fs/./ /mnt/reiser4_fs/./

---

### Post by davro on 2005-01-21
Hi all,

About a year ago i installed gentoo.
Started tweaking the system, gentoo is really a work of art, in every sence.
I have used many different distros kernels and all sorts of optimization, im the time i have been using 'Linux' from Tinfoil to distributed linux terminal servers Ltsp and personally i belive the most important factors are '' 'Humane Interfaces' marked or motivated by concern with the alleviation of suffering.
The Gentoo Emerge is a very powerful command, but i know i would have real trouble getting some Linux 'USERS' to 'emerge' to the idea of running the gentoo way.

Davro

---

### Post by poofyhairguy on 2005-01-21
[QUOTE=davro]Hi all,

About a year ago i installed gentoo.
Started tweaking the system, gentoo is really a work of art, in every sence.
I have used many different distros kernels and all sorts of optimization, im the time i have been using 'Linux' from Tinfoil to distributed linux terminal servers Ltsp and personally i belive the most important factors are '' 'Humane Interfaces' marked or motivated by concern with the alleviation of suffering.
The Gentoo Emerge is a very powerful command, but i know i would have real trouble getting some Linux 'USERS' to 'emerge' to the idea of running the gentoo way.

Davro[/QUOTE]


Quick question for Gentooers (or ex-gentooers). I always hear how great emerge is as a command. But for me the apt-get command isn't what kicks ass about Debian, its Synaptic. The thousands of packages confuse me if there is no good GUI way to get to them.

Does Gentoo have a rival to synaptic? If so, why isn't it ever mentioned?

---

### Post by Daniel G. Taylor on 2005-01-21
[QUOTE=poofyhairguy]Does Gentoo have a rival to synaptic? If so, why isn't it ever mentioned?[/QUOTE]

[Porthole](http://porthole.sf.net) is one such program, though there are others (I think there are at least two for KDE, one using kioslaves). 8-) 

The problem with Portage is that it was never made to allow GUIs to be built on top of it, whereas apt was made in such a way that it is not only possible, but also not that difficult. A lot of Portage stuff is done in a somewhat strange way (like output and spawning children processes) that makes it very hard to catch and work with. Fredrik, Brian and Bill did some amazing work with this on Porthole, where we actually import Portage as a Python library for our information, but have to call 'emerge ...' to actually do anything because of how Portage is built (much of the functionality is in the emerge script instead of the Python library, for instance)

So, when building a Portage GUI you basically have two options, do everything by calling 'emerge ...' and [try] to catch the output, then process the output (which I believe the KDE programs do) or use Python and do a mix of importing the library and calling external programs (which is what we do). All in all it was a big pain in the ass, to be honest. And don't get me started on documentation and the dependency code in Portage.

That said Jason Stubbs showed me a library he had built atop of a modified Portage that incorporated some of our PortageLib (the library we wrote to interface with the Portage library) functionality, and he was able to completely re-make the emerge script using this library. It was pretty clean and well documented. To be honest I'm not quite sure what happened to that.

Also, this allows up to date seaching and browsing -> [http://gentoo-portage.com/Browse](http://gentoo-portage.com/Browse)

---

### Post by poofyhairguy on 2005-01-21
[QUOTE=Daniel G. Taylor][Porthole](http://porthole.sf.net) is one such program, though there are others (I think there are at least two for KDE, one using kioslaves). 8-) 

The problem with Portage is that it was never made to allow GUIs to be built on top of it, whereas apt was made in such a way that it is not only possible, but also not that difficult. A lot of Portage stuff is done in a somewhat strange way (like output and spawning children processes) that makes it very hard to catch and work with. Fredrik, Brian and Bill did some amazing work with this on Porthole, where we actually import Portage as a Python library for our information, but have to call 'emerge ...' to actually do anything because of how Portage is built (much of the functionality is in the emerge script instead of the Python library, for instance)

So, when building a Portage GUI you basically have two options, do everything by calling 'emerge ...' and [try] to catch the output, then process the output (which I believe the KDE programs do) or use Python and do a mix of importing the library and calling external programs (which is what we do). All in all it was a big pain in the ass, to be honest. And don't get me started on documentation and the dependency code in Portage.

That said Jason Stubbs showed me a library he had built atop of a modified Portage that incorporated some of our PortageLib (the library we wrote to interface with the Portage library) functionality, and he was able to completely re-make the emerge script using this library. It was pretty clean and well documented. To be honest I'm not quite sure what happened to that.

Also, this allows up to date seaching and browsing -> [http://gentoo-portage.com/Browse](http://gentoo-portage.com/Browse)[/QUOTE]


Thats a good answer. Thanks!

---

### Post by Magneto on 2005-01-21
I was a ubuntu fanatic but then I woke up :(

I use Ubuntu on a server at home but it is too hamstrung by packages. 

I went back to gentoo on my main system a few months ago because portage outclasses everything else for me.

If Im forced to compile software it defeats the advantages of Ubuntu for me. Also I seriously hate the debian kernel method.

I like the Ubuntu community and mission but it can't replace functionality.

Gentoo works. Thats the number one problem I have with all Linux distros- Does it work?  Slackware was cool but I have to compile too much myself.  Rpm distros etc buggy apps and poor quality releases, dumbed down distros etc- no thanks

The main problem I had was that I no longer had Ubuntu, I had Ubuntu plus i dont know how many packages from Debian at different release levels all in an effort to bypass compilation. So people try to get me to build from source in Ubuntu- WHY ? I can do that in Gentoo and with less worry.  Gnome would crash when I'd change themes etc in Ubuntu alot of other issues too- in Gentoo compiled with my own flags for my own system with my own kernel  its perfect.

I just couldnt take it. I love ubuntu but if I can't do what I need to easily it defeats the purpose.

The time I lose with the initial install in Gentoo is easily regained by not having to hunt for sources of packages that arent included in the Ubuntu repos, not having to compile software and organizing it myself, by not having to troubleshoot buggy apps due to software not being built for my specific system.

For me its worth it. For other users it probabaly is fine.

Now I search for apps that will do what I need done and I don't search for packages. 

Emerge

---

### Post by Magneto on 2005-01-21
[QUOTE=jdong]Screw this... I'm reverting back.

Two days, already they broke a stable MySQL. This ain't reliable.


With Hoary, I'll try harder with Universe security backports.


I'll be back in Ubuntu by the end of the week.[/QUOTE]

Exactly ! when they did that with Gnome a few months ago I jumped ship. Warty is too old and Hoary is tooooo bleeding edge.

---

### Post by poofyhairguy on 2005-01-21
[QUOTE=Magneto]I was a ubuntu fanatic but then I woke up :(

I use Ubuntu on a server at home but it is too hamstrung by packages. 

I went back to gentoo on my main system a few months ago because portage outclasses everything else for me.

If Im forced to compile software it defeats the advantages of Ubuntu for me. Also I seriously hate the debian kernel method.

I like the Ubuntu community and mission but it can't replace functionality.

Gentoo works. Thats the number one problem I have with all Linux distros- Does it work?  Slackware was cool but I have to compile too much myself.  Rpm distros etc buggy apps and poor quality releases, dumbed down distros etc- no thanks

The main problem I had was that I no longer had Ubuntu, I had Ubuntu plus i dont know how many packages from Debian at different release levels all in an effort to bypass compilation. So people try to get me to build from source in Ubuntu- WHY ? I can do that in Gentoo and with less worry.  Gnome would crash when I'd change themes etc in Ubuntu alot of other issues too- in Gentoo compiled with my own flags for my own system with my own kernel  its perfect.

I just couldnt take it. I love ubuntu but if I can't do what I need to easily it defeats the purpose.

The time I lose with the initial install in Gentoo is easily regained by not having to hunt for sources of packages that arent included in the Ubuntu repos, not having to compile software and organizing it myself, by not having to troubleshoot buggy apps due to software not being built for my specific system.

For me its worth it. For other users it probabaly is fine.

Now I search for apps that will do what I need done and I don't search for packages. 

Emerge[/QUOTE]


Thats cool. Use what works...for you. I hate compile times, so I will stick with Ubuntu myself.

But use Gentoo if you like emerge more.

---

### Post by Magneto on 2005-01-22
[QUOTE=poofyhairguy]Thats cool. Use what works...for you. I hate compile times, so I will stick with Ubuntu myself.

But use Gentoo if you like emerge more.[/QUOTE]
 I really want to keep Ubuntu Poofyhairguy - it just pissed me off that on my server-different issue here- I had to search high and low for the right dvdauthor and transcode etc packages so I could do what I needed with DVDs. Then after all that the packages were compiled on the wrong architecture and labeled wrong- I was pissed. lol 


I just read that apt-build page and I will try it out   the author's non-command of english is amusing lol

---

### Post by poofyhairguy on 2005-01-22
[QUOTE=Magneto]I really want to keep Ubuntu Poofyhairguy - it just pissed me off that on my server-different issue here- I had to search high and low for the right dvdauthor and transcode etc packages so I could do what I needed with DVDs. Then after all that the packages were compiled on the wrong architecture and labeled wrong- I was pissed. lol 


I just read that apt-build page and I will try it out   the author's non-command of english is amusing lol[/QUOTE]

Thats cool. I left Fedora (for something based on Debian- eventually Ubuntu) when I couldn't find a Bit Tornado rpm. Turned out to be a good thing for me. Maybe Hoary will convince you to look the other way when its released!

---

### Post by jdong on 2005-01-22
[QUOTE=poofyhairguy]Maybe Hoary will convince you to look the other way when its released![/QUOTE]

I was looking at Universe and all in Hoary, and it seems much better integrated.

---

### Post by dritan on 2007-08-09
This thread looks pretty old but couldn't help to voice my 2 cents here =) 

I've been using gentoo for almost 3 years now, and it has given me my fair share of headache. But of course it's been a great pleasure! The way I see it's like driving, some people like the manual stick shift (gentoo slackware,LFS), while other just care about getting there no matter how (most other distros). Although I don't use ubuntu but I come here often for help (the forum is not bad!!) and the fact that so many windows converts are using ubuntu shows that it really get things done much easier! That said, I don't see myself moving away from gentoo anytime soon.

---

### Post by stmiller on 2007-08-09
EDIT: wow 2005 thread, woops

---------------

> **poofyhairguy said:**
> 
Does Gentoo have a rival to synaptic? If so, why isn't it ever mentioned?

[Kuroo]("http://kuroo.org/") is excellent. 

[IMG]http://kuroo.org/images/shots/08/08main.png[/IMG]

---

