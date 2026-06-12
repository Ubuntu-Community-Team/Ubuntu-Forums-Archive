---
title: "Mozilla Firefox 1.0 ?"
date: 2004-12-03
forum: Repositories &amp; Backports
---

### Post by deception on 2004-12-03
How comes Synaptic doesn't show 1.0 as an available package?  :| 

Thanks,
deception

---

### Post by ubuntu_demon on 2004-12-03
maybe you are using warty ? firefox 1.0 is only avaiilable in hoary

You can get firefox 1.0 from the hoary repositoriy  by :

-change warty to hoary in yor sources.list 

sudo apt-get update
sudo apt-get install mozilla-firefox

-change your sources.list back

Check the how-to section for more on this. (things like apt-pinning)

---

### Post by jdong on 2004-12-03
Warty has and forever will have Firefox 0.9.3... Once a stable version of Ubuntu is released, packages in that version will only receive security updates -- no feature/program updates. If you think about guaranteeing stability or making tech support's job easier, you'll see why!


Hoary is stable enough for use, and it'll have the latest everything!

---

### Post by deception on 2004-12-03
Thank you for the replies! Well I have only just set up Warty.. and customised it to how I like it, so I don't know if I'm willing to upgrade just now. I'll stick with 0.9.3. 


Many thanks!

---

### Post by ubuntu_demon on 2004-12-03
staying with warty is the safest choice :-D

---

### Post by M@t on 2004-12-03
Updating to hoary won't destroy your customisations, but there are risks to have broken softwares during a few days.

If you don't have a very good reason to update firefox and you don't want to loose the stability of warty, don't change anything.

There are means to have a mix of warty and hoary, but that is tricky.

---

### Post by ubuntu_demon on 2004-12-03
[QUOTE=M@t]Updating to hoary won't destroy your customisations, but there are risks to have broken softwares during a few days.

If you don't have a very good reason to update firefox and you don't want to loose the stability of warty, don't change anything.

There are means to have a mix of warty and hoary, but that is tricky.[/QUOTE]
 newbies should stick with warty
anyone who would want to run a server should stick with warty
hoary is for everyone who likes a bit of risk and likes to have the bleeding-edge stuff
hoary is a nice desktop environment for nerds

---

### Post by astoltz on 2004-12-03
I agree that mixing a few Hoary packages with a base Warty install is not the best idea.  However, I really missed FireFox1.0 after installing Warty so I had to try and upgrade.  Ubgrading from Hoary was NOT fun.  In fact, I never did get it to work.  What did work was downloading FireFox from mozilla.org, installing it manually and then changing  /usr/bin/mozilla-firefox to be a link to the new FF1.0.  I didn't touch the 0.93 version but it never gets started because of the change to /usr/bin/mozilla-firefox.

---

### Post by brainchill on 2004-12-03
I don't know that applying patches constantly is a good way to make sure that the system stays stable ... in fact I Think it's kind of stupid.

A good example is apache for instance. If the version of apache that shipped had a security problem and a new release was put out by the apache developers. often times more than just a single bug is fixed in the new release. If all you do is backport the security fix to the older version and release that it could still be vulnerable to problems that exist in the old version that may have been fixed in the new but were not considered security but reliability fixes.

Redhat is forever plagued by this ..... they are constantly backporting fixes to older software and this same problem gets them every time. That's why they have historically had 4-8 times the patches then say slackware who .... when the developer releases a new version to address security/reliability concerns just puts out a package of the version that is reccomended by the developer of the software.
This includes the kernel.

And for the love of god don't try and tell me that slackware is unstable. It's one of the only amazingly stable distros left.

I'm not saying that ubuntu isn't .... I have to say that in general it has been the most stable desktop distro using software with this level of newness .... amazingly stable ... I'm just argueing with the mindset.

I think it's thoroughly outdated and poorly thought through so far as reality is concerned

---

### Post by castrojo on 2004-12-03
I've been using the firefox 1.0 backport listed on [http://www.ubuntulinux.org/wiki/BreakMyUbuntu](http://www.ubuntulinux.org/wiki/BreakMyUbuntu) and it's been good to me so far.

---

### Post by brainchill on 2004-12-03
that's kind of my point .... but that term "backport" in this instance is very deceptive .... I'm talking about backporting patches from newer versions of a piece of software to older version .... in the sense that you're talking about a "backport" it is really not at all .... you are talking about using a current stable release of a piece of software with a distro that didn't originally come with it .... in many ways you are actually proving my point.

---

### Post by castrojo on 2004-12-03
Heh I'm just trying to help the original poster.

IMO it's easier to plop in a deb line for the one or two packages that I need updated than mess with an installer that totally skips the package manager or installing it in my home directory.

---

### Post by jdong on 2004-12-03
[QUOTE=brainchill]I don't know that applying patches constantly is a good way to make sure that the system stays stable ... in fact I Think it's kind of stupid.

A good example is apache for instance. If the version of apache that shipped had a security problem and a new release was put out by the apache developers. often times more than just a single bug is fixed in the new release. If all you do is backport the security fix to the older version and release that it could still be vulnerable to problems that exist in the old version that may have been fixed in the new but were not considered security but reliability fixes.

Redhat is forever plagued by this ..... they are constantly backporting fixes to older software and this same problem gets them every time. That's why they have historically had 4-8 times the patches then say slackware who .... when the developer releases a new version to address security/reliability concerns just puts out a package of the version that is reccomended by the developer of the software.
This includes the kernel.

And for the love of god don't try and tell me that slackware is unstable. It's one of the only amazingly stable distros left.

I'm not saying that ubuntu isn't .... I have to say that in general it has been the most stable desktop distro using software with this level of newness .... amazingly stable ... I'm just argueing with the mindset.

I think it's thoroughly outdated and poorly thought through so far as reality is concerned[/QUOTE]

I won't dispute Slack's stability. LOL, I fully respect it :)

For Apache, it's nice that the developers differentiate already between security updates and feature updates. So do many other packages.

However, other packages like Firefox also add new *features* and changes existing settings in addition to providing security updates. It's these changes that drive me nuts! Let's save all the debug-a-huge-.conf-file-because-it-won't-work fun for version updates, please?


Maybe redhat sucked at getting updates right, but IMO Debian does a good job of backporting bugfixes to stable branch. Let's hope Ubuntu follows Debian closer than RedHat! LOL



P.S. I don't think there's anything wrong with backports.org-like updates for a few specific packages in Warty. Desktop users would especially like to see updates for Firefox and certain packages in Universe!

---

### Post by brainchill on 2004-12-03
Point taken .... and LOL at the sig quote.

---

### Post by anklator on 2004-12-07
i am using  the default firefox installer, i just downloaded it installed and now its running, no repository changes, no compilation \\:D/

---

### Post by luiska on 2004-12-08
Ok, I am trying the breakmyubuntu thing now. Apt doesnt seem to mind. Only problem is that I am sitting at school and ssh into my machine. Will not be able to see the result until tonight :)

---

### Post by jdong on 2004-12-08
Check out the new section about Warty Backports. That's gonna be the BEST way to get new versions of Firefox and GAIM (no, I'm not biased -- I SWEAR!!!)

---

