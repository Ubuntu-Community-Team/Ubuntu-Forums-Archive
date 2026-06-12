---
title: "Is Ubuntu suited as a server distro?"
date: 2005-03-23
forum: The Cafe
---

### Post by TjaBBe on 2005-03-23
Is Ubuntu suited as a pure-server distro? Do you think the main goal of Ubuntu is delivering a nice and friendly desktop alternative or is Ubuntu also well-suited for a high-end web/file server or a router distro?

I don't mean running a webserver on your desktop for development means, or running a fileserver to share your music to the network. Offcourse Ubuntu is well-suited to do these tasks. 

It may also be that some people think Ubuntu should, in the future, bring a seperate server compilation in the way the difference between gnome and kde is made in hoary.

I personally think Ubuntu's main focus is, and should be, delivering a nice and friendly desktop distribution to the public. For example, a pure-server doesn't need an X userinterface, but Ubuntu integrates one as default.

---

### Post by Slapdash on 2005-03-23
I dont think the default Ubuntu is suited for a server but one can easily make it play VERY nicely as a server. esp. because of it's lean'ness.

Maybe a UBUNTU Server repository should be created to cater for just this need?

---

### Post by TjaBBe on 2005-03-23
This is stupid, I see I have spelled Ubuntu as Ubunto in the last answer, I am deeply ashamed.  :-# (Hope some mod or something could fix it)

I partly agree with Slapdash, I think it would be nice to have a seperate server repository. But I also think Ubuntu's main goal and focus should be bringing linux to the desktop...

---

### Post by defkewl on 2005-03-23
No. I don't quite agree. I think Ubuntu should always focus on desktop OS. There's already FreeBSD and OpenBSD that is more well suited as server OS.

---

### Post by jdong on 2005-03-23
Ubuntu is the most suited server distro of them all...

First of all, it's always up-to-date. Latest software means best support through HOWTO's and vendors (open-source or otherwise).

Second of all, updates are stable and reliable. With Ubuntu, you can feel comfortable with an auto-upgrade script, because you know Ubuntu updates are only for security purposes, and that those updates won't break your system.

---

### Post by TjaBBe on 2005-03-23
[QUOTE=defkewl]No. I don't quite agree. I think Ubuntu should always focus on desktop OS. There's already FreeBSD and OpenBSD that is more well suited as server OS.[/QUOTE]

That is more or less my opinion (add debian to the server OS list). But on the other hand it would be nice to have a lean server repository (which leaves all desktop utillities from the list) of Ubuntu for reasons as described by jdong.

---

### Post by Buffalo Soldier on 2005-03-23
I think by trying to please too many crowd a distro will lose it's focus.

---

### Post by az on 2005-03-23
[QUOTE=Buffalo Soldier]I think by trying to please too many crowd a distro will lose it's focus.[/QUOTE]

If you do one thing well and others build on it, that is really healthy.

Kubuntu is an example of the comunity building on the Ubuntu base.  This makes ubuntu better.  Maybe the server side of Ubuntu will be kept lean with the rest of the packages being supported by the ocmmunity...

---

### Post by MDJ2000 on 2005-03-23
I'm only on my second day using Ubuntu, I've been using debian for years and the reason I choose to try ubuntu was for a quick, clean desktop that works well, and I'm impressed thus far. 

For my servers, I install a minimal debian, and tweak it just the way I want/need, nothing more, nothing less. I don't see how or why I would change that.

---

### Post by jdong on 2005-03-23
Umm, If I set up a PHP 3.x.x server (Debian Woody) for a customer, I think I'd be burned at the stake...... ;) THAT's what's wrong with Debian.

---

### Post by TjaBBe on 2005-03-23
[QUOTE=jdong]Umm, If I set up a PHP 3.x.x server (Debian Woody) for a customer, I think I'd be burned at the stake...... ;) THAT's what's wrong with Debian.[/QUOTE]

Debian woody includes php4... So thats not entirily true ;).

---

### Post by MDJ2000 on 2005-03-23
[QUOTE=jdong]Umm, If I set up a PHP 3.x.x server (Debian Woody) for a customer, I think I'd be burned at the stake...... ;) THAT's what's wrong with Debian.[/QUOTE]Stability is what I want in a server. I use Arch Linux when I'm testing bleeding edge stuff. Woody has php 4.1.2 by the way, no need to use php 3, and you could backport whatever else.

---

### Post by TjaBBe on 2005-03-23
[QUOTE=MDJ2000]Stability is what I want in a server. I use Arch Linux when I'm testing bleeding edge stuff. Woody has php 4.1.2 by the way, no need to use php 3, and you could backport whatever else.[/QUOTE]

That's what I said ;). There also always appear people who seem to think that with woody you're stuck on kernel 2.2.x while debian woody also includes 2.4.x. You just have to specifically install it.

---

### Post by garyng on 2005-03-23
I am doing almost a parallel install of both sarge and hoary(to test things out), for SMB servers. Many of the server packages(or should I say non-UI oriented packages) are newer in sarge than hoary.

At the moment, I would say that if one is a hardcore command shell server admin, sarge has an advantage over hoary but for a more "Window" oriented admin, hoary with its GNOME admin tools are more appealing(like managing shares, user and groups etc.) . May be the same tools are also available in sarge(or are they new in 2.6.10?).

What I am not feeling comfortable with ubuntu is that many packages are in "universe" which are termed as "not necessary supported" but in sarge, they are supposed to be fully supported once turn stable.

---

### Post by jdodson on 2005-03-23
ubuntu would work as a great server.  here are some reasons.

apt - if you don't realize why this would benifit you as an admin, i really don't think you understand apt.

1 cd - most servers don't need 5 cds full of GUI apps.  

18 mo release cycle - this seems to be a pretty generic release cycle.  suse operates on this 18 month cycle.  if you need more support time go RHES, they have 5 years :-o 

timely security patches - the ubuntu folk are great at keeping things secure.

free - the only thing you have to pay for is support.

stable - ubuntu seems to be very stable.  if you need a more stable system see debian stable.

---

### Post by jdodson on 2005-03-23
[QUOTE=TjaBBe]That's what I said ;). There also always appear people who seem to think that with woody you're stuck on kernel 2.2.x while debian woody also includes 2.4.x. You just have to specifically install it.[/QUOTE]

if 2.2.x is the default kernel, then does that not imply they would rather you use 2.2.x?  is not the point of debian stable to be in fact "stable."  why would you deviate from the defaults to get less recommended stability?  if 2.4.x is stable then why make 2.2.x the default?  personally it seems that if you want a "more stable" system they suggest 2.2.x.

realize i am not saying 2.4.x is not stable, however it seems if you want the "most stable" recommended system, which is the point of debian stable in the first place, then 2.2.x is your kernel.

---

### Post by MDJ2000 on 2005-03-23
[QUOTE=jdodson]if 2.2.x is the default kernel, then does that not imply they would rather you use 2.2.x?  is not the point of debian stable to be in fact "stable."  why would you deviate from the defaults to get less recommended stability?  if 2.4.x is stable then why make 2.2.x the default?  personally it seems that if you want a "more stable" system they suggest 2.2.x.

realize i am not saying 2.4.x is not stable, however it seems if you want the "most stable" recommended system, which is the point of debian stable in the first place, then 2.2.x is your kernel.[/QUOTE]I'd venture a guess that "they" couldn't care less what you use, in my opinion "they" are providing a base system that will operate on as much hardware as possible.

It's a moot point anyways, TjaBBe never implied that, he simply said people complain of being stuck with 2.2 when there's no need to, and this is way too silly and OT to waste time on.

---

### Post by jdodson on 2005-03-23
[QUOTE=MDJ2000]
It's a moot point anyways, TjaBBe never implied that, he simply said people complain of being stuck with 2.2 when there's no need to, and this is way too silly and OT to waste time on.[/QUOTE]

i don't think its moot at all, thats why i commented on it.  because you don't agree and think it is "silly" does not in fact make it so.

defaults are not accidents.

the fact that debian stable uses 2.2.x as a "default" kernel is a big deal.  the reasons i gave are a good reason why ubuntu is a better alternative as a server.   because you can actually get a kernel that can scale to todays hardware and conditions.

---

### Post by TjaBBe on 2005-03-23
[QUOTE=jdodson]if 2.2.x is the default kernel, then does that not imply they would rather you use 2.2.x?  is not the point of debian stable to be in fact "stable."  why would you deviate from the defaults to get less recommended stability?  if 2.4.x is stable then why make 2.2.x the default?  personally it seems that if you want a "more stable" system they suggest 2.2.x.

realize i am not saying 2.4.x is not stable, however it seems if you want the "most stable" recommended system, which is the point of debian stable in the first place, then 2.2.x is your kernel.[/QUOTE]

That may be true. But if it wasn't recommended at all, wich does not take too much by debian stable standards, they would not put it in the repository at all. 

Anyway I am absolutely not trying to make this a debian vs. Ubuntu topic, I use and like them both very much. But both for different purposes...

---

### Post by jdodson on 2005-03-23
[QUOTE=TjaBBe]That may be true. But if it wasn't recommended at all, wich does not take too much by debian stable standards, they would not put it in the repository at all.[/quote]

good point. 

[QUOTE=TjaBBe]Anyway I am absolutely not trying to make this a debian vs. Ubuntu topic, I use and like them both very much. But both for different purposes...[/QUOTE]

i agree.

---

### Post by scarecrow on 2005-03-23
Ubuntu is nice as a desktop, but I'd rather use something else for server usage... Slackware and Crux are the obvious and 100% working choices.
A server needs stable, proven packages, and not X and up-to-date packages. Doing a "slapt-get update" once every XX days on Slack should be more than enough.
Even Mandrake (cough... cough...) is a better choice with the included web UI for the firewall and basic administration tasks. Of course there's always webmin and/or ssh, but lets put the facts straight.

---

### Post by MDJ2000 on 2005-03-23
[QUOTE=jdodson]i don't think its moot at all, thats why i commented on it.  because you don't agree and think it is "silly" does not in fact make it so.

defaults are not accidents.

the fact that debian stable uses 2.2.x as a "default" kernel is a big deal.  the reasons i gave are a good reason why ubuntu is a better alternative as a server.   because you can actually get a kernel that can scale to todays hardware and conditions.[/QUOTE]lol, the arguing is silly and OT, not the point, however, it's still moot ;)

---

### Post by nocturn on 2005-03-24
[QUOTE=MDJ2000]I'm only on my second day using Ubuntu, I've been using debian for years and the reason I choose to try ubuntu was for a quick, clean desktop that works well, and I'm impressed thus far. 

For my servers, I install a minimal debian, and tweak it just the way I want/need, nothing more, nothing less. I don't see how or why I would change that.[/QUOTE]

I run an public webserver at work (on SuSE currently)
My webapps require PHP4, Apache2, Tomcat5 and MySQL4, these are not available on Debian (stable).  
Debian has an ancient version of SNORT that does not pick up newer attacks.

Debian unstable does not have security tracking, thus making it not an option for a server (for my requirements).

Ubuntu has all the advantages of Debian, but adds security tracking to the up-to-dateness of Debian unstable.

---

### Post by nocturn on 2005-03-24
[QUOTE=MDJ2000]... you could backport whatever else.[/QUOTE]

Yes, but the backports or not tested equally well and they are also not security tracked.  So again, a no-no for a secure server.

---

### Post by ubuntu_demon on 2005-03-24
I voted :
"Yes, Ubuntu is meant to serve!"

If I were a server admin I think I would choose Ubuntu, doing daily security upgrades (if they are available) and keeping the same release until it isn't supported anymore or if I need some new features (like php 5 in the future) .... then I would dist-upgrade it to the newest release that has all my demands. I wouldn't compile or backport anything because that would decrease stability and security.

Is it possible to dist-upgrade for example from warty to bendy ? I think such things matter for server-admins.

---

### Post by TjaBBe on 2005-03-24
[QUOTE=demon666_nl]I voted :
"Yes, Ubuntu is meant to serve!"

If I were a server admin I think I would choose Ubuntu, doing daily security upgrades (if they are available) and keeping the same release until it isn't supported anymore or if I need some new features (like php 5 in the future) .... then I would dist-upgrade it to the newest release that has all my demands. I wouldn't compile or backport anything because that would decrease stability and security.

Is it possible to dist-upgrade for example from warty to bendy ? I think such things matter for server-admins.[/QUOTE]

I think that should be possible, you would just be able to add the bendy repositories to your sources.lst and off you go.

---

### Post by ubuntu_demon on 2005-03-24
(edited)

from : [http://www.ubuntulinux.org/ubuntu/releases/](http://www.ubuntulinux.org/ubuntu/releases/) :
> 

Upgrades are supported from each release to the next. If you wish to skip a release, and then update to the latest one, then it is necessary to update the system from your existing release through each intermediate release to get to the release you wish to run.

Enterprise releases

In addition to the regular six-monthly releases, the Ubuntu team may make an Enterprise Release (based on an existing time-based release) that has received additional stabilisation, polish and translation work. These Enterprise Releases will be supported for a longer period than the standard 18 month support of the time based releases. Upgrades will be supported from enteprise release to enterprise release.


sounds good :)

---

### Post by dusu on 2005-03-24
I really hope Ubuntu can be used for a server !
That's what the administrator in the lab where I work has decided to use !
And in some months all our Desktops will also be Ubuntu powered :-D

---

### Post by garyng on 2005-03-24
I haven't seen the "enterprise" release yet.

After a short period of having ubuntu and sarge side by side, I would go back to sarge as my main purpose is for server installation and found that there are lots of glitches in ubuntu(hoary). 

Beside, I like the long release schedule(of debian) for server. 2 - 4 years IMO is a very reasonable time frame between major release. Ubuntu has just moved too fast as a server platform.

---

### Post by poofyhairguy on 2005-03-24
[QUOTE=dusu]I really hope Ubuntu can be used for a server !
That's what the administrator in the lab where I work has decided to use !
And in some months all our Desktops will also be Ubuntu powered :-D[/QUOTE]

Clap, clap, clap, clap.....

Sounds like a dream...

---

### Post by jdonnell on 2005-03-24
[QUOTE=demon666_nl]In addition to the regular six-monthly releases, the Ubuntu team may make an Enterprise Release [/QUOTE]

I really hope this happens! I'm currently using ubuntu as a subversion server to see how well it works out. It's not that big of a deal if our subversion server goes down so it's a safe test. 

We have 4 redhat 9 production servers and I am not satisfied with them. There is not a well established/documented upgrade path. I was really disappointed with the way rh handled this. Currently I'm trying to find a suitable distro for our servers and I have three main requirements. A clean upgrade path, good package management, and semi recent packages. There are a lot of important new features in the newer versions of python and mysql which is what we use the most. An enterprise version of Ubuntu sounds like a perfect fit.

---

### Post by BWF89 on 2005-03-24
If it runs Apache HTTP Server it's a server distro.

---

### Post by jdonnell on 2005-03-24
[QUOTE=BWF89]If it runs Apache HTTP Server it's a server distro.[/QUOTE]

Then windows and linux from scratch are server distro's, but I'd never use one of them by choice on my servers :)

---

### Post by defkewl on 2005-03-24
[QUOTE=jdong]Ubuntu is the most suited server distro of them all...
[/QUOTE]
It might be suited but it's not the main purpose. It's like saying: I could chop a carrot with a chainsaw but it's not the main purpose of it.

---

### Post by TravisNewman on 2005-03-24
[QUOTE=garyng]...and found that there are lots of glitches in ubuntu(hoary).[/QUOTE]

You do know that it's still in development right?

Now, if it includes an http server is it a server distro? No, not really.
Like has been said, Windows XP pro is not a server OS, and it includes a webserver, ftp server, etc. You can MAKE ANYTHING a server, but is it a server OS? Is it tweaked and geared toward servers? Maybe, but a blanket statement like "if it has Apache it's a server distro" is false. I could make a distro that included the 2.7 kernel, Gnome 2.10, about a thousand games, no system logger, no ftp, 20 thousand themes for gtk, metacity, etc, and apache. I'd call it "why-would-you-ever-want-to-install-this Linux." And I'm SURE nobody would call it a server distribution.

---

### Post by ember on 2005-03-24
[QUOTE=defkewl]It might be suited but it's not the main purpose. It's like saying: I could chop a carrot with a chainsaw but it's not the main purpose of it.[/QUOTE]

Well, that's more or less what describes my attitude towards ubuntu as a server. Of course Ubuntu really is ready for a neat little home php+sql+ftp+apache-server, but that is, to my mind, more because it's a really useful distribution for software devolopers (e.g. like me ;)). 

Yet I always felt, Ubuntu isn't really aimed at the server market and it's quite good that way.

---

### Post by TravisNewman on 2005-03-24
Actually, after my rant about how just because it'll run Apache doesn't make it a Server OS, I WOULD like to say that the configurability of it is well suited for servers, and, after installing just what you need, and if you have the patience, installing a hardened kernel and SELinux, I think it'd be quite ready for just about any server task.

---

### Post by jdonnell on 2005-03-25
I was just searching for a debian vds, didn't think I could find an ubuntu one, and I came across this site.
[http://www.linode.com/](http://www.linode.com/)
They have ubuntu as an option for their vds's :) :) :)
Not sure if I'm comfortable enough to get it over debian.

---

### Post by defkewl on 2005-03-25
I think Ubuntu has already done a perfect job by focusing on making desktop linux with Gnome as a default window manager. It's much much better rather than having a swiss army knife distro.

---

### Post by j-georg on 2005-03-27
If you install desktop environment, you have a desktop. If you install server software, you have a server. And if you install both, you have both :)

I do not quite agree, that server does not need newest software. For example - my client requires webmin-shorewall which does not exist in Debian (event not in testing). And there are many other packages still missing in "non-unstable" Debian.

Today's server platform, being stable, must constantly evolve - be able to provide latest technological possibilites, so their users can stay in competition.

---

### Post by jdonnell on 2005-03-27
[QUOTE=j-georg]
I do not quite agree, that server does not need newest software.
[/QUOTE]

This is exactly why I started using ubuntu. I wanted good package management with recent versionf of the software I use. Specifically server software, (apache, php, mysql, python, etc)

---

### Post by garyng on 2005-03-28
[QUOTE=panickedthumb]You do know that it's still in development right?

.[/QUOTE]

Yup, and I see that sarge changes more often than hoary for those server packages I used(both are not freezed yet). So it has nothing to do with whether it is still in development, IMO. More to do with user base, stanard debian(sid/sarge) has a much larger server package user base than ubuntu, the reverse is true for desktop.

In fact, ubuntu desktop(both KDE and GNOME) are much more polished than sarge.

---

### Post by ubuntu_demon on 2005-03-28
[QUOTE=garyng]Yup, and I see that sarge changes more often than hoary for those server packages I used(both are not freezed yet). So it has nothing to do with whether it is still in development, IMO. More to do with user base, stanard debian(sid/sarge) has a much larger server package user base than ubuntu, the reverse is true for desktop.

In fact, ubuntu desktop(both KDE and GNOME) are much more polished than sarge.[/QUOTE]
 sarge has been testing for a very long time so off course it's pretty stable. Ubuntu offers security support and sarge doesn't.

---

### Post by garyng on 2005-03-28
[QUOTE=demon666_nl]sarge has been testing for a very long time so off course it's pretty stable. Ubuntu offers security support and sarge doesn't.[/QUOTE]

both hoary and sarge are not released yet so both don't officially offer security support. When they are both released(seems to be RSN), sarge willl have an advantage that it has security support for the whole repository which I find many of the packages I used is under 'universe' in hoary that gives me the impression that they are not fully supported.

hoary as far as I know took a snapshot of sarge(around Jan?) so it is not really that much far behind but still,  sarge has more recent packages(and fixes) for most non-UI based packages.

---

### Post by ubuntu_demon on 2005-03-28
[QUOTE=garyng]both hoary and sarge are not released yet so both don't officially offer security support. When they are both released(seems to be RSN), sarge willl have an advantage that it has security support for the whole repository which I find many of the packages I used is under 'universe' in hoary that gives me the impression that they are not fully supported.

hoary as far as I know took a snapshot of sarge(around Jan?) so it is not really that much far behind but still,  sarge has more recent packages(and fixes) for most non-UI based packages.[/QUOTE]
 hoary is not a snapshot of sarge. Ubuntu is based on debian unstable(sid). Ubuntu improves on debian's strong points and also gives back to debian. here's a nice slide show about these sorts of stuff(I got the link from [http://planet.ubuntulinux.org](http://planet.ubuntulinux.org)) :

[http://mako.yukidoke.org/talks/20050317-ubuntu_and_debian/ubuntu_debian_slides-HTML/img0.html](http://mako.yukidoke.org/talks/20050317-ubuntu_and_debian/ubuntu_debian_slides-HTML/img0.html)

hoary gets released in a couple of days .. aprox april 6. Sarge's releasedate is still unknown.

all basic server stuff is in main including the popular weblanguages as far as I know. So they are fully supported with security fixes.

---

### Post by garyng on 2005-03-28
[QUOTE=demon666_nl]hoary is not a snapshot of sarge. Ubuntu is based on debian unstable(sid). Ubuntu improves on debian's strong points and also gives back to debian. here's a nice slide show about these sorts of stuff(I got the link from [http://planet.ubuntulinux.org](http://planet.ubuntulinux.org)) :

[http://mako.yukidoke.org/talks/20050317-ubuntu_and_debian/ubuntu_debian_slides-HTML/img0.html](http://mako.yukidoke.org/talks/20050317-ubuntu_and_debian/ubuntu_debian_slides-HTML/img0.html)

hoary gets released in a couple of days .. aprox april 6. Sarge's releasedate is still unknown.

all basic server stuff is in main including the popular weblanguages as far as I know. So they are fully supported with security fixes.[/QUOTE]

based on sid/sarge doen't really matter as sid would migrate to sarge if things go well. The fact remind that it is taken from some snapshot and some later change in debian sid would be ignored(which is understandable and desirable too). I just want to point out that ubuntu doesn't automatically be "more recent" than debian sarge. The desktop packages are, not many non UI packages. I use SVN for example which is 1.1.3 on sarge, and 1.1.1 on hoary. Does it matter ? Not really for me, but may be for others.

As for security updates, it depends on individual needs. I have a colinux(or similar headless server setup). In order to have X on it(for better admin experience), I need to install VNC 4 server which is under universe, not main in hoary.

This is not a trash talk about ubuntu, just my experience with it which may serve as a FYI.

---

### Post by ubuntu_demon on 2005-03-28
[QUOTE=garyng]based on sid/sarge doen't really matter as sid would migrate to sarge if things go well. The fact remind that it is taken from some snapshot and some later change in debian sid would be ignored(which is understandable and desirable too). I just want to point out that ubuntu doesn't automatically be "more recent" than debian sarge. The desktop packages are, not many non UI packages. I use SVN for example which is 1.1.3 on sarge, and 1.1.1 on hoary. Does it matter ? Not really for me, but may be for others.

As for security updates, it depends on individual needs. I have a colinux(or similar headless server setup). In order to have X on it(for better admin experience), I need to install VNC 4 server which is under universe, not main in hoary.

This is not a trash talk about ubuntu, just my experience with it which may serve as a FYI.[/QUOTE]
 ubuntu gets released every 6 months so on average ubuntu is newer than stable debian

system->preferences->remote desktop ... I haven't tried this

---

### Post by garyng on 2005-03-28
[QUOTE=demon666_nl]ubuntu gets released every 6 months so on average ubuntu is newer than stable debian

system->preferences->remote desktop ... I haven't tried this[/QUOTE]

Ah, you misunderstood me, I want to run X on a headless(or graphic card less) server(for remote admin). This can only be done by running some "pseudo' X server like VNC but VNC server is in universe, not main.

As for release schedule, you are right but I am talking about sarge/hoary in particular. For those who need a tight update schedule, ubuntu will be a better choice in the future but sarge as of now contains almost all the latest server(or non-UI) packages which is on its way to release soon(I tracked it pretty closely). 

For me, I don't need the server package to change that often, 24-36 months is good enough, so long the security update is there. changes every 6 months is too much for my taste, as server.

---

### Post by ubuntu_demon on 2005-03-28
[QUOTE=garyng]Ah, you misunderstood me, I want to run X on a headless(or graphic card less) server(for remote admin). This can only be done by running some "pseudo' X server like VNC but VNC server is in universe, not main.

As for release schedule, you are right but I am talking about sarge/hoary in particular. For those who need a tight update schedule, ubuntu will be a better choice in the future but sarge as of now contains almost all the latest server(or non-UI) packages which is on its way to release soon(I tracked it pretty closely). 

For me, I don't need the server package to change that often, 24-36 months is good enough, so long the security update is there. changes every 6 months is too much for my taste, as server.[/QUOTE]
 I also use vncserver on an internet gateway of mine. It would be nice if vncserver would be in main.

as for release schedule ... then you can go for the ubuntu enterprise releases. as they probably come more often than stable debian releases. :)

---

