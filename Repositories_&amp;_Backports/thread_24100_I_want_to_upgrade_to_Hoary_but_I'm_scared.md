---
title: "I want to upgrade to Hoary but I'm scared"
date: 2005-04-05
forum: Repositories &amp; Backports
---

### Post by Campitor on 2005-04-05
Hello Everyone:

  I really want to upgrade to Hoary, but I'm a bit scared.  I've installed a bunch of packages, some of which I think came from the backports (e.g. acrobat7.0, some python extensions, gdesklets, wine).  I read this thread:

[HTML]http://www.ubuntuforums.org/showthread.php?t=12174&page=3&pp=10[/HTML]

and don't know if I'm gonna run into problems.  At the end of the thread, a Moderator says that leaving backports shouldn't be a problem.  I've also read threads on the wiki pages, about what to do...:

[HTML]http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes[/HTML]

[HTML]http://www.ubuntulinux.org/wiki/GuideToHoary[/HTML]


but still I'm afraid that I'll break the system.

So here's my question:

  IS it better to download the CD iso of Hoary and upgrade from CD than using apt-get dist-upgrade (removing warty and back-ports from the source.list file)?

  Should I just wait a bit, until Hoary's bugs have been resolved and the back-port issue is no longer a problem?

  Should I just back-up my data and give it a try...No guts no glory, style?  Do the following:
1. change all references from Warty to Hoary in source.list
sudo apt-get update
sudo apt-get install ubuntu-base ubuntu-desktop -f
sudo apt-get dist-upgrade
sudo dpkg-reconfigure locales

Any suggestion would be highly appreciate it

Campitor

---

### Post by kiddo on 2005-04-05
That's what I did. I had everything backuped regularly already, and I absolutely wanted amaroK, so I dist-upgraded (removing the backports and everything). I messed up my Xorg I think, anyways the nvidia drivers make wonders.. And I had a friend to help me (via MSN on a laptop besides me).

So I'd say, yeah why not, if you got everything under backup, then you got nothing really to loose? If your installation is really too messed up, then pop out that ubuntu hoary preview or candidate release (that you burned before dist-upgrading heheh) and do a fresh install.

The only drawbacks I've found to dist-upgrading is that


[list]
[*]  you don't always know what new packages come standart with the new release ;) such as the update-manager
[/list]
[list]
[*] this maybe my imagination, but my fresh-hoary-installed laptop boots faster than my dist-upgraded hoary desktop (wich is 4 times more powerful).
[/list]Besides, while I think of it.. as for the "deadly bugs", there shouldn't be anymore... Hoary is out tomorrow ;)

---

### Post by Campitor on 2005-04-05
Thanks for the quick reply...

  So you did remove the packages from back-ports?  I was hoping I didn't need to...

I forgot that Hoary's final release is tomorrow...I might just wait and try to download the CD (I imagine a lot of people will try the same thins... bandwidth will be an issue), tomorrow.

I still want to give the dist-upgrade a try...It would be so nice to have a linux distro that you can upgrade to the next level, by just upgrading over the net.  I think you can do it easily if you didn't screw around to much with the back-ports...but I really wanted some of the newest software.

We'll see...
camp

---

### Post by Leif on 2005-04-05
Reading through that thread, it seems that the problems were ironed out. I upgraded with 0 problems.

---

### Post by kiddo on 2005-04-05
>    So you did remove the packages from back-ports?  I was hoping I didn't need to... 

Well I did it because I was as paranoid as you, and that's what I read in a forum thread. And, I just realized we are Tuesday the 5th, the release is on Friday the 8th. Sorry >_< I should look at my gnome clock instead of my watch. XD

---

### Post by kiddo on 2005-04-05
Urgh, stupid DSL disconecting me just when I'm about to reply :) 

So to say, I removed the backports only because that was suggested. And, sorry, I'm mistaken, the release is not tomorrow, but Friday (I got to learn to read Tue and Thu without messing up... XD)

//EDIT: urgh! please remove this post, mods!

---

### Post by poofyhairguy on 2005-04-05
Well. You can upgrade a not pure Warty install. I did it painlessly. But it bugged me that I did it. So I wipped it and put on a clean install. Everything seems to run nicer now. No hard evidence on that one (might just be how a claen car feels faster or whatever).

---

### Post by Campitor on 2005-04-06
[QUOTE=poofyhairguy]You can upgrade a not pure Warty install. I did it painlessly. [/QUOTE]
When you say "not pure Warty" did you mean that you also had Back-ports and Hoary software installed?  I 've actually gone and done really bad things with my Ubuntu, like changing the repositories to hoary to install a package (i.e. Acrobat7) and get rid of dependency problems and then changing them back to warty  ;-) ... so that freaks me out a bit, that when I do a full dist-upgrade, those indiscretions are gonna come back and bite me in the a$$.

Did you do a dist-upgrade without removing the back-ports or Hoary software?  Did you encounter any problems?

camp

---

### Post by Campitor on 2005-04-14
[QUOTE=Campitor]When you say "not pure Warty" did you mean that you also had Back-ports and Hoary software installed?  I 've actually gone and done really bad things with my Ubuntu, like changing the repositories to hoary to install a package (i.e. Acrobat7) and get rid of dependency problems and then changing them back to warty  ;-) ... so that freaks me out a bit, that when I do a full dist-upgrade, those indiscretions are gonna come back and bite me in the a$$.

Did you do a dist-upgrade without removing the back-ports or Hoary software?  Did you encounter any problems?

camp[/QUOTE]
 Well....sorry for not replying sooner, but had a lot of actual work to do.

A couple of days ago I upgraded to Hoary with apt-get dist upgrade...and all went perfectly fine. 

I did have to install ubuntu-desktop and ubuntu-base (which made a real dent on my HD space, for I only have 5 GB), but everything went fine.  I didn't remove any packages, nor any from the backports.  I did not include the backport repositories until after Hoary was updated.

I'm happy.  Now I probably will get a bigger HD and reinstall fresh, which is a little disapointing because I have my box tweaked to how I wanted.  All that installing and modifying I'm not looking forward to, but hopefully I wont have to do it for a long time

Camp

---

### Post by mark on 2005-04-14
I've been running Hoary in most of its pre-release incarnations & through consistent updating, I'm now running my own "tweaked" version of the official 5.04 release.  Having said that...

I do plan on doing a *careful* backup and a "fresh" install of 5.04.  To paraphrase poofyhairguy - it may only be psychological, but a "clean" install just seems to run better, somehow...

(Besides which, I've done so many "clean" installs that most of the tweaking I want is stuff I could pretty much do in my sleep!)

---

### Post by beerorkid on 2005-04-15
well I am in the same boat as a lot of ya it seems.  I have done fresh installs of 5.04 on both my home PC's, yet my work one is a heavily updated and modified warty.

I have a bunch of special stuff on here for work, sure I could do a clean one, yet the tinkerer in me screams do an upgrade some how.

At home I would put in the newly burned 5.04 and a screen would pop up that asked me if I wanted to upgrade.  Although they were hoary RC not warty, it was really cool.

I have done the apt-get dist-upgrade and yet it cannot upgrade 49 packages. Is there a way to force it?  I put a -f yet nothing.  Is there a way to make it do it off the CD?  if not I love reinstalling any way.

Oh yeah ubuntu rocks my world.

---

