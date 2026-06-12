---
title: "apt-get question"
date: 2005-04-15
forum: Repositories &amp; Backports
---

### Post by lmellen on 2005-04-15
:? If I use apt-get to install realplayer, does apt-get install the files to the proper directories?
Right now the system is running very nicely and I'm quite capable of screwing everything up!
                                                               Thanks -- Larry :) 

( I'm using Kubuntu)

---

### Post by mendicant on 2005-04-15
Yes, that's the whole idea behind using a package management system.  To see what a .deb will install to, download it, then do:

% dpkg --contents my_downloaded.deb

It is also free to run pre and post installation scripts, but you typically don't have to worry about those.  With realplayer, if you're using the ubuntu package in multiverse, it actually downloads the rpm (or requires you to do so) and turns it into a .deb (probably), which it installs.  Since the package does exist, it will probably do the right thing on your system.

PS: I've mentioned it before, and I'll mention it again: you should use aptitude in preference to apt-get.

---

### Post by lmellen on 2005-04-15
mendicant-- What do you mean by aptitude? -- sudo aptitude install Package,or sudo aptitude-get install Package or what? I'll do as you suggest
     Thanks for the reply -- Larry :)

---

### Post by mendicant on 2005-04-15
aptitude replaces apt-get, so:
% sudo aptitude install packagename
for instance

aptitude is better because:
[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

I like it mainly because it keeps track of automatically installed dependencies, and gets rid of them when I uninstall something (if there's nothing else also depending on it).  Reduces clutter.

Typical command line usage is exactly the same as apt-get (like install, remove, update, upgrade, dist-upgrade, clean, autoclean).  It even has some additional ones, like purge, reinstall, show, changelog, download.  It is only missing the 'source' based stuff (source and build-dep) and check.

---

### Post by Leigh on 2005-04-16
If aptitude is so good, why then does apt-get exist?

I'm not being faceious, I'd really like to know!

---

### Post by mendicant on 2005-04-16
apt-get was made before aptitude.  You could ask the same question of dselect.  dselect was made before aptitude, as well, but if you've ever used aptitude and dselect, you'd come to realize that aptitude is a much better interface.

Fortunately for us, user interfaces evolve over time, sometimes for the better.  aptitude is one example of this.  It was made to address some shortcomings in apt-get.

---

### Post by az on 2005-04-17
[QUOTE=Leigh]If aptitude is so good, why then does apt-get exist?

I'm not being faceious, I'd really like to know![/QUOTE]


aptitude, as does synaptic use apt-get.

It is a frontend-backend thing.

To touch on your original concern, it is just as easy to remove a package as it is to install it.  Do not worry.

---

### Post by mendicant on 2005-04-17
[QUOTE=azz]aptitude, as does synaptic use apt-get.

It is a frontend-backend thing.
[/QUOTE]

Not exactly.  They both do similar things in some cases, and aptitude has reused (or been influenced by) some of the apt-get code, and they are both frontends for the package management system, and they both use libapt-pkg.  aptitude doesn't use apt-get though.  From the man page for apt-get:
       Several  "front-end"  interfaces  exist,  such as dselect(8), aptitude,
       synaptic, gnome-apt and wajig.

---

### Post by vlakov on 2005-04-17
Hi, first i need to know what is a universal repository, i have installed Ubuntu 5.04 on a machine withouth internet connection, what can i do ??, can i download packages withouth that??


(Sorry about my english... I speak spanish).


Vlakov

---

### Post by mendicant on 2005-04-17
You can download on a separate machine and transfer the files somehow.  The only updates are language packs and artwork.  Security updates will eventually come.  If they do, and you don't have an internet connection, it's unclear if these will be important to you--if you completely trust your local users, you don't need to worry.  Otherwise, you will need to do a download of the affected files, copy them over to your Ubuntu machine, then install them (using dpkg, for instance).

One minor point:  you should really be starting a new thread instead of using this one, so as not to confuse people who are reading this thread.

Not sure what you want to know about the universe repositories.  They contain other packages that are not officially supported by the project in the way of security updates.  You may or may not see security updates for packages in universe.

---

