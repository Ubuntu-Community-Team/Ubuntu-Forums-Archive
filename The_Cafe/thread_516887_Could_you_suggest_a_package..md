---
title: "Could you suggest a package."
date: 2007-08-03
forum: The Cafe
---

### Post by Frak on 2007-08-03
I'm bored and I would like to create some .deb's for the great people of UbuntuForums.org. I know how to package, and I would like to help the community in that way. Just list below a package you would like to have compiled into a .deb and I will try my hand at making a .deb with it.

Thanx

Only simple packages only, no complicated packages such as DE's.
Open source only also.

---

### Post by bread eyes on 2007-08-03
[http://haskell.org/haskellwiki/Yi](http://haskell.org/haskellwiki/Yi)

---

### Post by init1 on 2007-08-03
[http://www.piettes.com/fallingsandgame/](http://www.piettes.com/fallingsandgame/)

---

### Post by user1397 on 2007-08-03
Please make ubuntu debs for tovid: [http://tovid.org]("http://tovid.org/")
 They need them pretty bad, as they&#8217;ve never got them to work right.
 I&#8217;ve got admin rights to upload the package to the official website, so if you decide to do it, just upload it as an attachment on the ubuntuforums thread, so that I can in turn download and upload it to the site.
 Thank you very much.



btw: this is the same message I put on your blog.

---

### Post by Frak on 2007-08-03
Lets continue this on my Blog, its in my signature. I could help you all faster that way. Plus I am working with Cutler Software to host the files there. And possibly make a repo in the process. Sorta like the Serveas repo.

Thanks

EDIT
This is not spam, I just decided I'd rather do this there instead. As I can post back with a new topics.

---

### Post by Frak on 2007-08-04
> **init1 said:**
> [http://www.piettes.com/fallingsandgame/](http://www.piettes.com/fallingsandgame/)
download the fsg-4.4 binary and run
```
sudo apt-get install libpng3
```
then cd to the directory with the fsg-4.4 binary and run
```
chmod +x fsg-4.4
```
then either run ./fsg-4.4 in the directory where it is kept, or double click on its icon.

---

### Post by init1 on 2007-08-04
> **Frak said:**
> download the fsg-4.4 binary and run
```
sudo apt-get install libpng3
```
then cd to the directory with the fsg-4.4 binary and run
```
chmod +x fsg-4.4
```
then either run ./fsg-4.4 in the directory where it is kept, or double click on its icon.
:confused:
I'm aware of that. I just thought it was a nice game that deserved a deb package.

---

### Post by Frak on 2007-08-04
> **init1 said:**
> :confused:
I'm aware of that. I just thought it was a nice game that deserved a deb package.
OK
Compiling it is being a living hell though, it doesn't recognize wxWidgets being installed.

---

### Post by user1397 on 2007-08-04
I replied to your blog, just so you know :)

---

### Post by Frak on 2007-08-04
Thanx, I'll check up on that.

---

### Post by Frak on 2007-08-04
> **ubuntuman001 said:**
> Please make ubuntu debs for tovid: [http://tovid.org]("http://tovid.org/")
 They need them pretty bad, as they&#8217;ve never got them to work right.
 I&#8217;ve got admin rights to upload the package to the official website, so if you decide to do it, just upload it as an attachment on the ubuntuforums thread, so that I can in turn download and upload it to the site.
 Thank you very much.



btw: this is the same message I put on your blog.

Here's the file.
Note, you can create a symbolic link to a menu (or create a custom launcher) , or run tovidgui from the terminal, but I can't get it to populate the menu.

---

### Post by happy-and-lost on 2007-08-04
A patched SVN of AWN for Gutsy would be nice... I'm not sure how much longer I can live without it!

---

### Post by Macintosh Sauce on 2007-08-04
[COLOR="Navy"]I would suggest making a package of the free REALbasic 2007 Release 3 program for Linux at [http://www.realbasic.com/download/](http://www.realbasic.com/download/).[/COLOR]

---

### Post by user1397 on 2007-08-04
> **Frak said:**
> Here's the file.
Note, you can create a symbolic link to a menu (or create a custom launcher) , or run tovidgui from the terminal, but I can't get it to populate the menu.Alright man, thanks so much!  I'll let the tovid devs know.

---

### Post by Frak on 2007-08-04
> **Macintosh Sauce said:**
> [COLOR="Navy"]I would suggest making a package of the free REALbasic 2007 Release 3 program for Linux at [http://www.realbasic.com/download/](http://www.realbasic.com/download/).[/COLOR]
I should have stated this at the beginning, If it doesn't have a makefile, I can't compile it, if I can't compile it, I can't make a binary. And I can't use precompiled binaries, as I don't know how to package them.
Just run REALbasic from your home folder and it should work fine.

---

### Post by Frak on 2007-08-04
> **ubuntuman001 said:**
> Alright man, thanks so much!  I'll let the tovid devs know.
It did populate the menu's after I restarted X, and I haven't had any trouble with it, so it should be just fine.

---

### Post by M$LOL on 2007-08-04
I'd like to see a Skype deb for 64-bit Ubuntu that just *works*, with the existing one you have to manually satisfy two dependencies and then use getlibs to fix the missing libraries.

IDK if you can or not, just a thought.

---

### Post by Frak on 2007-08-04
> **M$LOL said:**
> I'd like to see a Skype deb for 64-bit Ubuntu that just *works*, with the existing one you have to manually satisfy two dependencies and then use getlibs to fix the missing libraries.

IDK if you can or not, just a thought.
Sorry M$LOL, I don't have a 64-bit processor. If I did I definately would, because I use skype alot. I'm planning to get a core 2 duo later, but for now I can't. Sorry.

---

### Post by Spr0k3t on 2007-08-04
Hey Frak, can you by chance mentor a project on this?  I'd like to build weechat into a deb and have it submitted to the official repos.

---

### Post by Frak on 2007-08-04
Well its pretty simple, all you need is checkinstall or [autodeb]("https://wiki.ubuntu.com/AutoDeb"), and alien is also a good program to have just in case your very lazy (as I am)
Basically:
```
sudo aptitude install build-essential checkinstall alien
```
Now some other stuff may have to be done for it to work right, as not all programs were made to work right with Ubuntu/Debian.
But you get the source code and make sure it either contains an install.sh or makefile.
```
cd /path/to/containing/directory/
./configure (sometimes ./config)
make
sudo checkinstall -D --install=no
```
or you could use autodeb
```
sudo ./autodeb.sh --gnome
```
or if you use KDE
```
sudo ./autodeb.sh --kde
```
Autodeb will attempt to download all of the needed dependencies, append them to the depends requirement, and make sure that false dependencies aren't downloaded.
See, I'm just doing the job others wouldn't want to do, because I like to make things easier for other people.

To be honest though, the only difficult parts are the dependencies. Back in the first page I got the request for Falling Sands Game, from which I couldn't build because I just kept getting wxWidgets problems.
Other than that, its pretty simple.
Hope that helps.
Oh and make sure to note where it dropped the file after it completed. You'll need it, as checkinstall usually places it in the directory where it built the package, yet autodeb puts it in the /tmp directory.

Good luck :guitar:

EDIT
Oh and Alien can usually change RPM's into DEB's
but its recommended to build it into the deb as then it is correctly made, but
```
sudo alien -D /patch/to/rpm/
```

---

### Post by M$LOL on 2007-08-04
> **Frak said:**
> Sorry M$LOL, I don't have a 64-bit processor. If I did I definately would, because I use skype alot. I'm planning to get a core 2 duo later, but for now I can't. Sorry.

No problem, just a thought :)

---

### Post by Sammi on 2007-08-04
You should work with [www.getdeb.net](www.getdeb.net)

They are really the best website for Ubuntu debs. Seems like they are open for contribution.

---

### Post by Frak on 2007-08-04
> **Sammi said:**
> You should work with [www.getdeb.net](www.getdeb.net)

They are really the best website for Ubuntu debs. Seems like they are open for contribution.
Forgot about them, sure, I'll help.

---

### Post by Sammi on 2007-08-04
I just realized that I've been downloading quite a lot of debs from getdeb, so I just donated 20 euro to them. This is actually the first donation I've made to any open source project, but it sure won't be the last :KS

Oh and you could make a deb for mpd .13 [http://www.musicpd.org/](http://www.musicpd.org/)
That would be great :D

---

### Post by user1397 on 2007-08-04
> **Frak said:**
> It did populate the menu's after I restarted X, and I haven't had any trouble with it, so it should be just fine.Okay, awesome.  One question though: did you make it with checkinstall or with autodeb?  I'm just wondering because I could never get checkinstall to work (for older versions though)

---

### Post by Frak on 2007-08-04
I just always done
```
./configure
make
sudo checkinstall -D install=no
```
and it usually just works, but
if you don't have the correct dependencies, it won't build, if it doesn't build, a .deb can't be created.

---

### Post by user1397 on 2007-08-05
> **Frak said:**
> I just always done
```
./configure
make
sudo checkinstall -D install=no
```and it usually just works, but
if you don't have the correct dependencies, it won't build, if it doesn't build, a .deb can't be created.Ah; so you installed all the dependencies listed on the tovid site before building this deb?  Or does the deb include all the dependencies?

---

### Post by Frak on 2007-08-05
Installed all of the dependencies. Thats how package management works in Ubuntu. Its incredibly wasteful if you install the same dependency 10x over. Only PC-BSD includes all of its dependencies.
But, the installer will install the needed dependencies.

---

### Post by UbuWu on 2007-08-05
> **Sammi said:**
> You should work with [www.getdeb.net](www.getdeb.net)


Even better would be working the Ubuntu MOTU team to get more packages in the official repositories. Although this is a little bit more complicated than just running autodeb or checkinstall.

[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by Frak on 2007-08-05
I was thinking about it, I just hate the thought of working in CHROOT enviroments, don't know why. :confused:

---

### Post by UbuWu on 2007-08-05
> **Frak said:**
> I was thinking about it, I just hate the thought of working in CHROOT enviroments, don't know why. :confused:

Pbuilder, the program used to build the binary package, should take care of that. You don't have to do anything inside a chroot yourself.

---

### Post by user1397 on 2007-08-05
Now if you could get tovid into the *official repos*, that would be great!

---

### Post by Frak on 2007-08-05
Yeah, let me rebuild tovid so it works better and I'll mention it to the MOTU.

---

### Post by user1397 on 2007-08-05
> **Frak said:**
> Yeah, let me rebuild tovid so it works better and I'll mention it to the MOTU.Thanks man!  This is great news for tovid, will let the devs know immediately.

---

### Post by Frak on 2007-08-06
> **ubuntuman001 said:**
> Thanks man!  This is great news for tovid, will let the devs know immediately.

Here's the package, and I'll mention it to the men higher up.
P.S. It is now configured to auto install all dependencies.

---

### Post by user1397 on 2007-08-06
> **Frak said:**
> Here's the package, and I'll mention it to the men higher up.
P.S. It is now configured to auto install all dependencies.So this is a true deb package or was it made with autodeb or checkinstall? (Thanks either way, you've been a big help!)

---

### Post by user1397 on 2007-08-06
All I've got to say is...WOW...the new package installed perfectly, with all needed dependencies; I didn't even need to refresh the gnome-panel or X, the menu entries were there already!

Thanks a bunch again, I'll contact the devs immediately.

---

### Post by Frak on 2007-08-06
This is the true package created in a CHROOT cleanroom environment.

---

### Post by user1397 on 2007-08-06
> **Frak said:**
> This is the true package created in a CHROOT cleanroom environment.Awesome!  Where did you learn how to package debs? (Just wondering, been wanting to learn for a while, but haven't found much time...)

---

### Post by Frak on 2007-08-06
[http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)
I used a combination of pbuilder, dpkg-buildpackage, and dh_make.

---

### Post by user1397 on 2007-08-06
> **Frak said:**
> [http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)
I used a combination of pbuilder, dpkg-buildpackage, and dh_make.Alright, I guess I'll start reading.

---

### Post by Frak on 2007-08-06
Seriously, if you're only building a .deb from source, there really is no need to go past page 4, and even then there's alot of stuff that can be skipped.

---

### Post by user1397 on 2007-08-06
> **Frak said:**
> Seriously, if you're only building a .deb from source, there really is no need to go past page 4, and even then there's alot of stuff that can be skipped.okay, thanks for the tips.

---

### Post by user1397 on 2007-08-06
One more question Frak: why does it say "i386" in the package name of the new deb?  As far as I know, tovid is architecture independent as it is written in bash and python.

---

### Post by Frak on 2007-08-06
in the control or .dsc file, change the arch to all, and it should be fine. Right now though, it has been compiled for your system and it automatically assumes i386.

---

### Post by user1397 on 2007-08-06
> **Frak said:**
> in the control or .dsc file, change the arch to all, and it should be fine. Right now though, it has been compiled for your system and it automatically assumes i386.ah ok, thanks.

---

### Post by UbuWu on 2007-08-06
> **ubuntuman001 said:**
>  Where did you learn how to package debs?

The official [Ubuntu packaging guide]("http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html") would be a good start.

---

### Post by UbuWu on 2007-08-06
Frak, you should really consider joining the MOTU team, there are [so many programs]("https://launchpad.net/ubuntu/+bugs?field.searchtext=&orderby=-importance&field.status%3Alist=New&field.status%3Alist=Incomplete&field.status%3Alist=Confirmed&field.status%3Alist=Triaged&field.status%3Alist=In+Progress&field.status%3Alist=Fix+Committed&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_contact=&field.component-empty-marker=1&field.status_upstream-empty-marker=1&field.omit_dupes.used=&field.omit_dupes=on&field.has_patch.used=&field.tag=needs-packaging&field.has_cve.used=&field.has_no_package.used=&search=Search") that are not in the ubuntu repo's yet!

My personal list of wanted packages:
Kdenlive
Bibus
Songbird
Virtualbox
Handbrake

I have those installed, but it would be great if they were available from the repositories.

---

### Post by Frak on 2007-08-06
I'll try, but it won't be immediate. I was planning to make some contributions first, it gives me a better chance of being accepted, as thats something else they review. They want to make sure that MOTU's aren't braindead, and I respect that.

---

### Post by user1397 on 2007-08-09
yo frak, I've tested the deb myself (I have an i386 processor) and it worked flawlessly.  Then I asked a guy to try it on his AMD64 machine and he said that it did not work at all.

I thought this weird myself, because even though "i386" is in the package name, tovid is arch independent.

Your thoughts?

Also, is there a page that lists all the current MOTU package considerations? (Just curious)

Note: I tried to do the instructions you gave me about changing the control file in the deb, but then I realized that I still don't know how to re-package it into a deb.  So if changing the arch in that file to "all" is all it needs to work on any arch, then if you please could do it just tell me.

---

### Post by Frak on 2007-08-09
Well to create the package,** it had to be created for my arch**. So in all actuallity, I doubt it would be able to work with anything else. Usually when the script creates it rulings for arch's, they should be followed.
If you have ever seen packages that are made for all arch's, that means it is a **Multiple Binary** with multiple packages contained with in its orig.tar.gz.
I, myself, use dh_make and dpkg-buildpackage -rfakeroot within a Feisty CHROOT environment.

---

### Post by user1397 on 2007-08-09
> **Frak said:**
> Well to create the package,** it had to be created for my arch**. So in all actuallity, I doubt it would be able to work with anything else. Usually when the script creates it rulings for arch's, they should be followed.
If you have ever seen packages that are made for all arch's, that means it is a **Multiple Binary** with multiple packages contained with in its orig.tar.gz.
I, myself, use dh_make and dpkg-buildpackage -rfakeroot within a Feisty CHROOT environment.Ah, ok.

Also, apparently there is such a site, I've found it, but it is currently down. [http://revu.tauware.de/](http://revu.tauware.de/)

---

### Post by Frak on 2007-08-09
such what of a site?

---

### Post by user1397 on 2007-08-09
> **Frak said:**
> such what of a site?it's the site that lists all the MOTU hopeful packages (or packages requesting to be made into ubuntu debs)

I was asking you if there was such a site like 2 posts back, 
but I found it quickly after.

---

### Post by Frak on 2007-08-09
I think there is also [wiki.ubuntu.com/MOTU]("https://wiki.ubuntu.com/MOTU") which has the same thing.
And then there is [launchpad]("http://launchpad.net/~motu"), from which I posted a bug report requesting Torvid to be added to the Universe.

---

### Post by user1397 on 2007-08-24
frak, this link now works ([http://revu.tauware.de/](http://revu.tauware.de/)) but I do not see tovid listed

I thought I saw it listed there before, but for some reason someone took it off or they have since cleared the list and started a new one.

btw, tovid has come out with a new version, 0.31

...so...wanna make another deb for it?!

---

### Post by Frak on 2007-08-24
I'm really up to my neck in work ATM. I am only running Vista and XP for business reasons and the school I work for is having us "Terror-proof" the servers so they can't get "Hijacked".

Ubuntu will be back on my machine, but it'll be awhile.

As for the tovid package, its still waiting approval from the MOTU.

---

### Post by user1397 on 2007-08-24
> **Frak said:**
> I'm really up to my neck in work ATM. I am only running Vista and XP for business reasons and the school I work for is having us "Terror-proof" the servers so they can't get "Hijacked".

Ubuntu will be back on my machine, but it'll be awhile.

As for the tovid package, its still waiting approval from the MOTU.ah, ok, no problem man.

---

### Post by Fbot1 on 2007-08-24
That second post looks interesting.

---

### Post by user1397 on 2007-08-28
by the way, thanks so much for all your help, frak, I think I forgot to mention it :)

---

### Post by Frak on 2007-08-28
np, glad to help

---

### Post by user1397 on 2007-10-30
hey frak, so I randomly decided to build a tovid deb again, but with checkinstall (never got around to learning how to make a proper deb...:( ) and I figured out that even with checkinstall, you can still make a package that installs all dependencies for you.  I just tried it, and it worked...check it out: [http://tovid.sourceforge.net/download/ubuntu/tovid_0.31_i386.deb](http://tovid.sourceforge.net/download/ubuntu/tovid_0.31_i386.deb)

I just did ```
sudo checkinstall -D --install=no --requires=[all dependencies listed here]
```

---

### Post by ice60 on 2007-10-30
what about gnome-launch-box? it's in the repos, but it seems lots of people get seg. faults when they try and run it. it's quite difficult to install by hand too. i installed it on my suse, but it took a bit of time getting all the deps.
[http://developer.imendio.com/projects/gnome-launch-box](http://developer.imendio.com/projects/gnome-launch-box)

is there any chance making a new package will make it work better?

---

### Post by Frak on 2007-10-30
> **ice60 said:**
> what about gnome-launch-box? it's in the repos, but it seems lots of people get seg. faults when they try and run it. it's quite difficult to install by hand too. i installed it on my suse, but it took a bit of time getting all the deps.
[http://developer.imendio.com/projects/gnome-launch-box](http://developer.imendio.com/projects/gnome-launch-box)

is there any chance making a new package will make it work better?
It's very difficult to package in such a way that it will harm the resulting package, so I'll tinker with this, but I'm probably not going to delve into it.

Also, you could file a bug in launchpad, they can fix it much easier and faster than I could dream of doing.

---

### Post by master_kernel on 2007-10-30
Good work with your packaging! I started up a project like this a long while ago, (I think my freewebs site is still up: [http://www.freewebs.com/linuxnewbie946/](http://www.freewebs.com/linuxnewbie946/)), but I abandoned it after getting complaints for using checkinstall instead of the "official Debian way". I eventually found a howto for the official Debian way, but by then I had lost interest in the project. Anyway, thanks again for helping the community!

master_kernel

---

### Post by ice60 on 2007-10-30
> **Frak said:**
> It's very difficult to package in such a way that it will harm the resulting package, so I'll tinker with this, but I'm probably not going to delve into it.

Also, you could file a bug in launchpad, they can fix it much easier and faster than I could dream of doing.OK, it's not a big deal, it's just something i noticed when i started a thread about it, everyone seems to have problems with it! -
[http://ubuntuforums.org/showthread.php?t=596174](http://ubuntuforums.org/showthread.php?t=596174)

searching through the forums looks like most people have trouble getting it installed and/or working, it installed fine for me lol :)

OT. i had to use google to search the forum for it because the forum search doesn't understand the - inbetween the words!

---

### Post by Frak on 2007-10-30
> **master_kernel said:**
> Good work with your packaging! I started up a project like this a long while ago, (I think my freewebs site is still up: [http://www.freewebs.com/linuxnewbie946/](http://www.freewebs.com/linuxnewbie946/)), but I abandoned it after getting complaints for using checkinstall instead of the "official Debian way". I eventually found a howto for the official Debian way, but by then I had lost interest in the project. Anyway, thanks again for helping the community!

master_kernel
I'm going on a Hiatus for some time until I regain interest (MOTU are my heroes now ;), talk about being persistent)

Also, thanks for helping the Community master_kernel with your kernel scripts :)

---

### Post by Frak on 2007-10-30
> **ice60 said:**
> OK, it's not a big deal, it's just something i noticed when i started a thread about it, everyone seems to have problems with it! -
[http://ubuntuforums.org/showthread.php?t=596174](http://ubuntuforums.org/showthread.php?t=596174)

searching through the forums looks like most people have trouble getting it installed and/or working, it installed fine for me lol :)

OT. i had to use google to search the forum for it because the forum search doesn't understand the - inbetween the words!
No search engine is perfect, but I wished Google would open up about their algorithm.

---

### Post by ice60 on 2007-10-30
> **Frak said:**
> No search engine is perfect, but I wished Google would open up about their algorithm.i heard you can learn quite a lot looking through the patent claim they made for it. i think it was the patent i'm thinking about. i think the most important part of google's quick search is the hardware...

---

