---
title: "Your opinion on APT"
date: 2010-01-21
forum: The Cafe
---

### Post by k64 on 2010-01-21
What is you guys's opinion on APT? Do you say it is better than YUM, or are they the same? Or, is APT worse than YUM?

---

### Post by 5dolla on 2010-01-21
I think apt is way better than yum.:D

---

### Post by Frak on 2010-01-21
Yum > Apt

---

### Post by RaZe42 on 2010-01-21
I haven't used yum, but I really like pacman more than apt.

---

### Post by Icehuck on 2010-01-21
> **Frak said:**
> Yum > Apt

Yes

---

### Post by doorknob60 on 2010-01-21
I like APT better than YUM. Haven't used YUM much, but the times that I have I wasn't really a fan of it. I like pacman best though, simply for its speed and top notch dependency handling, as well as the fact that it's easy to make packages (still haven't managed to make a DEB package right...), but yeah APT is pretty good :)

---

### Post by MaxIBoy on 2010-01-21
Having not used YUM extensively, I can't give an honest answer. However, I do like APT a lot. YUM would need to be pretty amazing in order to top it.

---

### Post by gnomeuser on 2010-01-21
Apt's commandline interface is arcanic and not very userfriendly. The underlying packaging format I haven't worked a lot with but it seems very hard to work with.

Yum has a very nice commandline interface, it displays information in a useful manner and it's tools are very well designed. Sadly the underlying RPM packaging format is anything if not verbose to the point of absurdity.

Of the two I like Yum the best, I also like the yum/rpm works very well with PackageKit whereas apt/dpkg does not.

The best tool as a packager isn't yum or apt though, it's Conary and it really does pretty much everything right from a packaging point of view, it is easy to work with. As a user though it is fairly slow but worst is that it doesn't correctly handle situation where you want to uninstall A which B depends on. Instead of offering to uninstall both it will refuse to do anything which isn't very helpful. Conary does have a lot of nice features though, it downloads deltas instead of full packages, it offers unlimited rollbacks and it works very well with PackageKit.

---

### Post by xuCGC002 on 2010-01-21
Voted for all of them.

---

### Post by Techsnap on 2010-01-21
APT whines more than YUM especially when you start force installing packages, it's certainly slower than YUM too and also the ncurses aptitude interface is awful.

---

### Post by szymon_g on 2010-01-21
well... apt-get sucks a bit, aptitude is much better solution.
Yum works slowly, but it supports Delta-rpms, apt and aptitude- not.
Zypper is fast, configurable and supports Deltarpms... Zypper FTW!

---

### Post by Mornedhel on 2010-01-21
> **gnomeuser said:**
> The best tool as a packager isn't yum or apt though, it's Conary and it really does pretty much everything right from a packaging point of view, it is easy to work with. As a user though it is fairly slow but worst is that it doesn't correctly handle situation where you want to uninstall A which B depends on. Instead of offering to uninstall both it will refuse to do anything which isn't very helpful. Conary does have a lot of nice features though, it downloads deltas instead of full packages, it offers unlimited rollbacks and it works very well with PackageKit.

You wouldn't be running Foresight, would you ? That's about the only distribution I know of that uses Conary. Plus, well, you're gnomeuser.

I've been toying with the idea to switch to it but am pretty busy at the moment, so can't do that on a whim. How is the distribution ?

---

### Post by YeOK on 2010-01-21
Apt is great until you get an error, then you get a screen full of useless information. I'd have to say yum makes life a lot easier.

---

### Post by gnomeuser on 2010-01-21
> **Mornedhel said:**
> You wouldn't be running Foresight, would you ? That's about the only distribution I know of that uses Conary. Plus, well, you're gnomeuser.

I've been toying with the idea to switch to it but am pretty busy at the moment, so can't do that on a whim. How is the distribution ?

Foresight is great, however it tends towards the same installing everything under the sun crap that openSUSE is so beloved for doing. Another problem being based on rPath's distro the toolchain is outdated, this problem is being worked but Foresight is severely starved of developers meaning progress is slow.

I would currently not recommend switching unless you are willing to deal with issues and engage yourself actively to get problems resolved. With one notable exception, the Foresight developer community is very nice and helpful, they can generally be found on #foresight-devel on freenode.

---

### Post by infestor on 2010-01-21
apt...the one and only :)

---

### Post by Hetor on 2010-01-21
I think APT is pretty cool guy. Eh, manages my packages and doesn't afraid of anything.

---

### Post by Xbehave on 2010-01-21
> **Techsnap said:**
> APT whines more than YUM especially when you start force installing packages, it's certainly slower than YUM too and also the ncurses aptitude interface is awful.
You can use aptitude directly without ncurses, it is slower than apt (about the same as yum), but if you've managed to beak anything (i.e you need to be forcing apt) aptitude is the easiest way to fix problems.

apt is definitely a powerful tool and contrary to popular beleif can be used for source management too (not as powerful as portage/emerge obviously) but can handle downloading source+deps and building it.

For people wanting delta-debs, try using debdelta (i'm not sure if repos offer deltas though), however IMHO for most people the bandwidth saved isn't worth the time spent rebuilding the rpms, so unless you have a powerful CPU/slow internet connection it actually slows things down.

---

### Post by Queue29 on 2010-01-21
Does apt even support binary diffs yet? Yum has had that for a while.

---

### Post by Techsnap on 2010-01-21
> You can use aptitude directly without ncurses, it is slower than apt

I know. I'm not stupid. How the heck can aptitude be slower than apt because it's a just a frontend to apt its self. I think you mean apt-get.

---

### Post by RiceMonster on 2010-01-21
Yum is great. It feels really clean and well thought out.

> **Frak said:**
> Yum > Apt

Agreed.

> **RaZe42 said:**
> I haven't used yum, but I really like pacman more than apt.

Cool story bro.

---

### Post by slakkie on 2010-01-21
The only thing I disliked with yum was the speed. It does some things under the hood which explains the waiting period, but I should be able to tell yum not to do all that. 

I voted for the both of them.

---

### Post by Mornedhel on 2010-01-21
> **RiceMonster said:**
> Cool story bro.

OK, I thought I'd understood this meme, but either I didn't or you misused it (or its meaning has shifted).

Could you please enlighten me, RiceMonster, as to what you meant here ? Your wisdom will be much appreciated.

---

### Post by xuCGC002 on 2010-01-21
> **Mornedhel said:**
> OK, I thought I'd understood this meme, but either I didn't or you misused it (or its meaning has shifted).

Could you please enlighten me, RiceMonster, as to what you meant here ? Your wisdom will be much appreciated.

Riveting tale, chap.

---

### Post by Xbehave on 2010-01-21
> **slakkie said:**
> The only thing I disliked with yum was the speed. It does some things under the hood which explains the waiting period, but I should be able to tell yum not to do all that. 
-C (work from cache) helps a bit, but i agree my main beef with yum was speed (even in fedora 11, which is apparently much better than yum used to be)

> **Queue29 said:**
> Does apt even support binary diffs yet? Yum has had that for a while.
yes, read my previous post deltadebs are supported, but i don't know if the repos support deltas yet and deltarpms arn't as impressive in practice as they sound.

> I know. I'm not stupid. How the heck can aptitude be slower than apt because it's a just a frontend to apt its self. I think you mean apt-get.
yes, i meant the apt-* utils (get/cache/mark/etc), all the added functionality of aptitude definitely makes it slower than apt-*.

---

### Post by k64 on 2010-01-21
I say APT, because YUM is a proprietary package manager by Red Hat.

That said, APT has a much cleaner interface than YUM. However, if I used Conary, I probably would like it. I'm thinking of downloading Foresight right now. However, I want to boot Foresight Live first to see if it recognizes my hardware and if it can install from a Live environment, not to mention if it includes Usplash.

How many packages does Conary support?

---

### Post by Xbehave on 2010-01-21
> **k64 said:**
> I say APT, because YUM is a proprietary package manager by Red Hat.
YUM is open source (GPL 2+), and is originally from Yellow-dog linux not red hat.

> How many packages does Conary support?
That question doesn't make sense, it depends how many have been packaged in that format the format itself supports any package (just like rpm/deb/tgz)

---

### Post by Mornedhel on 2010-01-21
> **k64 said:**
> I say APT, because YUM is a proprietary package manager by Red Hat.

Yum is a proprietary package manager by Red Hat just as much as Apt is a proprietary package manager by Debian. Both are GPL and other distributions use them.

---

### Post by patrickaupperle on 2010-01-21
I'm going to have to agree with a lot of the posts I have read (the first page):

pacman > apt >>> yum

In my (limited) experience, yum works extremely slowly. pacman seems the fastest. pacman also has the best dependency management, followed by apt. In pacman, dependencies are automatically removed when I remove the package. A command in apt does the same thing, but I have had some problems with it in the past. I consider pacman the best, and that is why I use Arch.

---

### Post by k64 on 2010-01-21
> **Mornedhel said:**
> Yum is a proprietary package manager by Red Hat just as much as Apt is a proprietary package manager by Debian. Both are GPL and other distributions use them.

Sorry for jumping to conclusions there. However, Debian is a real community, whereas Red Hat is a corporation like Xandros that makes you pay for a stable distro.

---

### Post by Luke has no name on 2010-01-21
> **k64 said:**
> That said, APT has a much cleaner interface than YUM.

See, I haven't had much experience with Yum in detail; I don't know if its dependency handling / atomicity / etc. are on par with apt; but the few times I've used yum on Fedora. I thought its interface was much cleaner and informative than apt-get. it's also nicer to type 'yum' than 'apt-get'.

---

### Post by Frak on 2010-01-21
> **k64 said:**
> Sorry for jumping to conclusions there. However, Debian is a real community, whereas Red Hat is a corporation like Xandros that makes you pay for a stable distro.
Oh, boy. Here we go again.

RedHat is 100% Open Source, has commited to being that, and has a community of **corporations and users** through **RedHat and Fedora**. I bet you that RedHat is used far more extensively than Debian is. Debian is great, but RedHat is just a great consumer choice.

> **k64 said:**
> That said, APT has a much cleaner interface than YUM.

You've never used Yum, and here's how I know. NOBODY who's used Yum would EVER say that Yum has a dirty interface. Yum's interface blows Apt's interface out of the water, waits for the scattered bits to settle, and then blows it out of the water again.

---

### Post by Techsnap on 2010-01-21
Since others are doing this:

pkgtool > zypper > yum > urpmi  > APT > pacman

I haven't used any others.

---

### Post by Xbehave on 2010-01-21
> **Frak said:**
> OYou've never used Yum, and here's how I know. NOBODY who's used Yum would EVER say that Yum has a dirty interface. Yum's interface blows Apt's interface out of the water, waits for the scattered bits to settle, and then blows it out of the water again.
I wouldn't say YUM's interface is dirty, but there is certainly too much going on for my liking, I've used YUM and apt and definitely prefer apt's interface.

(just for clarity when i say apt i mean  apt-*)

---

### Post by Grifulkin on 2010-01-21
> **k64 said:**
> Sorry for jumping to conclusions there. However, Debian is a real community, whereas Red Hat is a corporation like Xandros that makes you pay for a stable distro.

For support, you aren't buying the distro, you are buying the support.  If you just want the distro you could us CentOS.

---

### Post by Grifulkin on 2010-01-21
> **Techsnap said:**
> Since others are doing this:

pkgtool > zypper > yum > urpmi  > APT > pacman

I haven't used any others.

Techsnap, I am curious as to why you think Pacman is the worst?  Just asking.

---

### Post by RiceMonster on 2010-01-21
> **k64 said:**
> Sorry for jumping to conclusions there. However, Debian is a real community, whereas Red Hat is a corporation like Xandros that makes you pay for a stable distro.

So what? Red Hat releases all their source offers a free distro (Fedora), and contributes more to Linux related upstream projects than any other company. If Red Hat were to disappear, Debian would be hit hard.

Charging for their stable distro shouldn't matter to you, because it's not targeted at home users.

---

### Post by Daisuke_Aramaki on 2010-01-21
> **Techsnap said:**
> APT whines more than YUM especially when you start force installing packages, it's certainly slower than YUM too and also the ncurses aptitude interface is awful.

Love the signature Vince. 

I like yum better than apt.

---

### Post by Daisuke_Aramaki on 2010-01-21
> **k64 said:**
> Sorry for jumping to conclusions there. However, Debian is a real community, whereas Red Hat is a corporation like Xandros that makes you pay for a stable distro.

Lol. You've gotta be kidding me.

---

### Post by llawwehttam on 2010-01-21
> **Frak said:**
> Oh, boy. Here we go again.

RedHat is 100% Open Source, has commited to being that, and has a community of **corporations and users** through **RedHat and Fedora**. I bet you that RedHat is used far more extensively than Debian is. Debian is great, but RedHat is just a great consumer choice.



You've never used Yum, and here's how I know. NOBODY who's used Yum would EVER say that Yum has a dirty interface. Yum's interface blows Apt's interface out of the water, waits for the scattered bits to settle, and then blows it out of the water again.

I agree with everything said here. Not just Red Hat use yum either. Fedora and CentOS use it and with plugins like fastest repo it is very fast. Its great for updates and yumex works like a dream.  Apt is nice too but it just doesn't do it for me. I'm starting to go down the pacman route.

---

### Post by liamnixon on 2010-01-21
I'm gonna jump on the bandwagon!

pkgtools > yum >>>>>>>>>>>>>>>>>>>>>>> apt

---

### Post by Zoot7 on 2010-01-21
In my experience yum is the better package manager. It's definitely faster (hugely so, thanks to the delta rpms). The only reason I don't use it (or Fedora) is that I'm not a fan of the bleeding edge breakage that Fedora often introduces.

Apt is a lot slower and sometimes the dependency handling is a disaster. That said, I have apt kept on a leach so its shortcomings and disadvantages don't concern me too much.

---

### Post by ratcheer on 2010-01-21
I don't know what YUM is, but I no longer use apt. I use ***aptitude***, instead.

Tim

---

### Post by Frak on 2010-01-21
> **ratcheer said:**
> I don't know what YUM is, but I no longer use apt. I use ***aptitude***, instead.

Tim
Aptitude is just a wrapper around apt.

---

### Post by Simian Man on 2010-01-21
Yum's interface is sooo much nicer than apt's.  First off, the commands themselves are much clearer.  "yum remove" has the equivalent of "apt-get remove".  Why are you getting it if you're removing it?  "yum search" translates to "apt-cache search".  Why not "apt-get search"?  Also this command needs root privelges for some bizarre reason.  Then there's the fact that you can also use aptitude, and I've never really understand why both exist.

The biggest reason, though, is that yum's output is clear and organized while apt pretty much blows chow all over your terminal.

> **Xbehave said:**
> For people wanting delta-debs, try using debdelta (i'm not sure if repos offer deltas though), however IMHO for most people the bandwidth saved isn't worth the time spent rebuilding the rpms, so unless you have a powerful CPU/slow internet connection it actually slows things down.
I have a very fast internet connection, and a relatively fast processor, but yum with the presto plugin still saves time.  Especially for large packages, your savings ratio can be huge.

Not to mention that some people have very slow connections and/or have monthly transfer limits.

---

### Post by Xbehave on 2010-01-21
> **Zoot7 said:**
> In my experience yum is the better package manager. It's definitely faster (hugely so, thanks to the delta rpms).
What are the specs on your machine/internet? here delta rpms slowed everything down because generating the package was slower than just downloading the whole thing (10Mbps connection & ~2Ghz laptop, not great spec but not terrible either), I got the impression that this was pretty much the norm and that's why deltaRPMs aren't used by default.

---

### Post by KiwiNZ on 2010-01-21
> **k64 said:**
> Sorry for jumping to conclusions there. However, Debian is a real community, whereas Red Hat is a corporation like Xandros that makes you pay for a stable distro.

K64 Stop jumping on other open source communities. Its wrong and disrespectful. Their contribution to the overall Open Source community is the same.

You need to research before making many of your statements .

---

### Post by Zoot7 on 2010-01-21
> **Xbehave said:**
> What are the specs on your machine/internet? here delta rpms slowed everything down because generating the package was slower than just downloading the whole thing (10Mbps connection & ~2Ghz laptop, not great spec but not terrible either), I got the impression that this was pretty much the norm and that's why deltaRPMs aren't used by default.
I've a 20Mb symmetrical connection and my desktop has a 3.2GHz Phenom II.

---

### Post by Xbehave on 2010-01-21
> **Simian Man said:**
> Yum's interface is sooo much nicer than apt's.  First off, the commands themselves are much clearer.  "yum remove" has the equivalent of "apt-get remove".
zomg! an extra 3 characters, if it bothers you that much 
```
echo 'alias apt-rm="apt-get remove"' >> .bashrc
echo 'alias apt-remove="apt-get remove"' >> .bashrc
```

> Also this command needs root privelges for some bizarre reason.No it doesn't, that's why there is apt-cache/get, for clear separation of privileged and unprivileged operations, apt-cache is also read only so you can launch it while apt-get/cache is already running and it will still work.

> Then there's the fact that you can also use aptitude, and I've never really understand why both exist.
apt is lightweight and small
aptitude is powerful and big
There is no point in bloating apt, with features many don't want/need, but those that do can use aptitude which is pretty full featured, you can reformat the output too. (the only thing it's missing is a local install method)

> The biggest reason, though, is that yum's output is clear and organized while apt pretty much blows chow all over your terminal.
I find it to be the otherway round there is less info when you do something specific with apt-cache search <package name> gives you a simple list, yum search adds install status, version info,arch info, etc.

edit:
> **Zoot7 said:**
> I've a 20Mb symmetrical connection and my desktop has a 3.2GHz Phenom II.
Maybe my machine is older than most, I suppose as deltaing can be threaded easily your machine is probably fast enough to see a benefit then.

---

### Post by Techsnap on 2010-01-21
> Techsnap, I am curious as to why you think Pacman is the worst?  Just asking.

Because whenever I use it, it pulls in more crap than other package manager does. I've gathered it's a flaw of dependency handling package managers but pacman pulls in so many useless dependencies on so many apps I've used.

---

### Post by Xbehave on 2010-01-21
> **Techsnap said:**
> Because whenever I use it, it pulls in more crap than other package manager does. I've gathered it's a flaw of dependency handling package managers but pacman pulls in so many useless dependencies on so many apps I've used.
Sounds like bad packaging, not a mistake of the package manager itself (the only possible mistake is that it pulls in recommends by default, which used to happen in aptitude too)

---

### Post by lisati on 2010-01-21
Having only used apt based managers, 

YAY APT!

---

### Post by Techsnap on 2010-01-21
It might not be a mistake of the package manager, but that's my experience with it anyways.

---

### Post by Grifulkin on 2010-01-21
> **Techsnap said:**
> Because whenever I use it, it pulls in more crap than other package manager does. I've gathered it's a flaw of dependency handling package managers but pacman pulls in so many useless dependencies on so many apps I've used.

I noticed this the other day when I went to update VLC and it wanted to download smbclient.  I really need to switch to Slackware on this laptop, I don't need the extra dependencies on it, my desktop I don't really mind.

---

### Post by Mornedhel on 2010-01-21
> **Xbehave said:**
> zomg! an extra 3 characters, if it bothers you that much 
```
echo 'alias apt-rm="apt-get remove"' >> .bashrc
echo 'alias apt-remove="apt-get remove"' >> .bashrc
```

Have you actually tried it ? Yeah, that won't work.

```
$ ls
[output]
$ sudo ls
[same output without color -- first hint]
$ alias foo=ls
$ foo
[output]
$ sudo foo
sudo: foo: command not found
```

There are workarounds but they're all ugly.

(Still, a few extra characters is not that expensive.)

---

### Post by Icehuck on 2010-01-21
> **Simian Man said:**
> 

The biggest reason, though, is that yum's output is clear and organized while apt pretty much blows chow all over your terminal.


I have to agree that YUM makes it easier for the user to follow what's going on.

---

### Post by lykwydchykyn on 2010-01-21
> **Simian Man said:**
> Yum's interface is sooo much nicer than apt's.  First off, the commands themselves are much clearer.  "yum remove" has the equivalent of "apt-get remove".  Why are you getting it if you're removing it?  "yum search" translates to "apt-cache search".  Why not "apt-get search"?  Also this command needs root privelges for some bizarre reason.  Then there's the fact that you can also use aptitude, and I've never really understand why both exist.

I have no opinion on yum vs. apt, but as for aptitude it is considered the recommended package manager for Debian and has more or less superseded apt-get/apt-cache/etc.  (See the release notes for etch or lenny if you think I'm making that up).

In the Ubuntu world people persist in using apt-get for some reason.

Apart from being a few more characters, aptitude has pretty sane syntax IMHO.

---

### Post by RiceMonster on 2010-01-21
> **lykwydchykyn said:**
> Apart from being a few more characters, aptitude has pretty sane syntax IMHO.

Last time I used it though, the output was horrendous. I don't know if it's improved since then.

---

### Post by Techsnap on 2010-01-21
> Last time I used it though, the output was horrendous. I don't know if it's improved since then.

Nope it's still messy compared to YUM.

---

### Post by Simian Man on 2010-01-21
> **Xbehave said:**
> zomg! an extra 3 characters, if it bothers you that much 
```
echo 'alias apt-rm="apt-get remove"' >> .bashrc
echo 'alias apt-remove="apt-get remove"' >> .bashrc
```
I don't care about typing characters, I was pointing out that "apt-get remove" sounds stupid (to me) because it contains get and remove which are opposites.  Why not call the commands "apt install" and "apt remove" or something that makes more sense?


> **Xbehave said:**
> No it doesn't, that's why there is apt-cache/get, for clear separation of privileged and unprivileged operations
Huh.  I could have *sworn* that apt-cache search needed root privileges.  Is this a recent change?


> **Xbehave said:**
> I find it to be the otherway round there is less info when you do something specific with apt-cache search <package name> gives you a simple list, yum search adds install status, version info,arch info, etc.

No it doesn't:
```
yum search asteroids
Loaded plugins: presto, refresh-packagekit
============================== Matched: asteroids ==============================
Maelstrom.i686 : Space combat game
kdegames3.i686 : K Desktop Environment 3 - Games not ported to KDE 4
orsa.i686 : Orbit Reconstruction, Simulation and Analysis
overgod.i686 : Another arcade-style shoot-em-up
qstars.i686 : A screensaver simulating planets and asteroids in space
qstars-kde.i686 : KDE screensaver support for qstars
qstars-xscreensaver.i686 : XScreenSaver support for qstars
skychart.i586 : Planetarium software for the advanced amateur astronomer
smashteroid.i686 : Astrosmash Remake
solarwolf.noarch : A Python port of SolarFox
zasx.i686 : Asteroid like game with powerups

```

It gives you the info you mentioned if you do "yum info <pkg>", but then you'd *want* info wouldn't you.  Where apt's output is really awful is when it's updating or installing stuff though.

---

### Post by del_diablo on 2010-01-21
It works something like this after my experience

Yum:
-Slow
-Download less, get more
-Nice CLI
-The manual is incomplete
-Troublesome lack of unsigned packages and similar, and the man is quite troublesome!
-I have yet to se a properly working frontend :(

Apt:
-Fast
-Terrible CLI
-Got quite a few nice frontends
-Got some weird supply of fresh packages

---

### Post by Techsnap on 2010-01-21
APT is not fast that's for sure.

---

### Post by dragos240 on 2010-01-21
Yum < APT < pacman = emerge.

---

### Post by Icehuck on 2010-01-21
> **dragos240 said:**
> Yum < APT < pacman = emerge.

not even close

---

### Post by Gallahhad on 2010-01-21
If the package manager resolves dependencies, then it's doing its job correctly in my opinion. Use what works for you, if Yum seems better, they Yum it is, if RPM works for you use RPM, if Apt works for you use it, etc., etc., etc.

Usually the "best one" is the one *you* use.

---

### Post by Techsnap on 2010-01-21
> If the package manager resolves dependencies, then it's doing its job correctly in my opinion.

That's not true. Sometimes it will pull in dependencies of no relevance.

---

### Post by dragos240 on 2010-01-21
> **Icehuck said:**
> not even close

Well that's my opinion.

---

### Post by lykwydchykyn on 2010-01-21
> **Techsnap said:**
> That's not true. Sometimes it will pull in dependencies of no relevance.

That would be a packaging problem then.  Packages store info about dependencies, not package managers.  The package manager's job is to read the dependency list and make sure all dependencies are installed.

I'm pretty sure no package manager randomly installs needless crap that no package depends on.

---

### Post by Grifulkin on 2010-01-21
> **Techsnap said:**
> That's not true. Sometimes it will pull in dependencies of no relevance.

Which brings me to a question, is there a package manager that doesn't pull in any unneeded dependencies short of doing it all yourself.  Because it seems like a package manager, like that, would be easier to configure.  Just saying.

---

### Post by Skripka on 2010-01-21
> **lykwydchykyn said:**
> That would be a packaging problem then.  Packages store info about dependencies, not package managers.  The package manager's job is to read the dependency list and make sure all dependencies are installed.

I'm pretty sure no package manager randomly installs needless crap that no package depends on.

What do you mean by "depends" is the crux of the problem.

There are actual depends that software will not run without, there are optional dependencies for non-essential features to name a few.  Some packagers treat anything that might be useful once in a 1000 years as a dependency.

---

### Post by Techsnap on 2010-01-21
> Which brings me to a question, is there a package manager that doesn't pull in any unneeded dependencies short of doing it all yourself. Because it seems like a package manager, like that, would be easier to configure. Just saying.

Yes pkgtools on Slackware which has never screwed up for me. The most superior dependency handling package manager is when you use YaST in OpenSUSE because it allows you to choose to ignore dependencies and will even make suggestions if you choose to, of course if you click ignore it won't break anything, it will just continue working like you told it to.

---

### Post by lykwydchykyn on 2010-01-21
> **RiceMonster said:**
> Last time I used it though, the output was horrendous. I don't know if it's improved since then.

It's not something I'd print out and tack to my corkboard, but it does the job I guess.  What's yum's output look like?

My only point was that people complaining about apt's syntax are largely referring to the apt-get/apt-cache/apt-foo mess.  That aspect is addressed by aptitude, but people choose not to use it for some reason.

---

### Post by Gallahhad on 2010-01-21
> **Techsnap said:**
> That's not true. Sometimes it will pull in dependencies of no relevance.
I'll admit I am barely a novice on this subject; so correct me if I'm wrong so I can learn, but I was under the understanding that the dependency list was up to the package creator/maintainer to take care of, and that a package manager read the .deb or .yum or .rpm or whatever and then went out to the repositories and pulled down the packages the package maintainer listed?

If that is the case, then it would seem logical that "un-needed" packages/dependencies are the fault of the package maintainer and not the package manager?

If that is not the case, then I will need to start reading up to better understand the a.i. involved in a package manager that lets it determine what additional dependencies/packages are grabbed in order to make the selected software work. Suggested reading would be appreciated if you have time to link me up.

---

### Post by Techsnap on 2010-01-21
You're misunderstanding what I'm saying. The only dependency handling package manager which gives you even close to picking and choosing dependencies is using YaST to manage packages in OpenSUSE.

My gripe is, the others really don't give you many options and in fact with APT it's quite possible to totally break the package management by force installing things.

---

### Post by lykwydchykyn on 2010-01-21
> **Skripka said:**
> What do you mean by "depends" is the crux of the problem.

There are actual depends that software will not run without, there are optional dependencies for non-essential features to name a few.  Some packagers treat anything that might be useful once in a 1000 years as a dependency.

Either way it's a packaging issue.  If I install a program and the .deb or .rpm or whatever specifies libfoo1.x as a dependency, the package manager is going to install it whether or not the binary actually requires it.  If it's truly not needed, that's a problem with the package in question.

Would you rather a package manager second-guess the dependencies specified by the package? :confused:

---

### Post by Mornedhel on 2010-01-21
> **Gallahhad said:**
> I'll admit I am barely a novice on this subject; so correct me if I'm wrong so I can learn, but I was under the understanding that the dependency list was up to the package creator/maintainer to take care of, and that a package manager read the .deb or .yum or .rpm or whatever and then went out to the repositories and pulled down the packages the package maintainer listed?

If that is the case, then it would seem logical that "un-needed" packages/dependencies are the fault of the package maintainer and not the package manager?

If that is not the case, then I will need to start reading up to better understand the a.i. involved in a package manager that lets it determine what additional dependencies/packages are grabbed in order to make the selected software work. Suggested reading would be appreciated if you have time to link me up.

Nope, you're correct.

The only thing is that APT is configured to pull in recommended packages by default. You can configure it so that it only pulls dependencies, in /etc/apt/apt.conf:

```
APT::Install-Recommends "false";
APT::Install-Suggests "false";
```

Any superfluous package installed is then the fault of the package maintainer.

---

### Post by RiceMonster on 2010-01-21
> **lykwydchykyn said:**
> What's yum's output look like?

```
root@fedora:~# yum install xterm
Loaded plugins: presto, refresh-packagekit
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package xterm.i686 0:253-1.fc12 set to be updated
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package         Arch           Version                 Repository         Size
================================================================================
Installing:
 xterm           i686           253-1.fc12              updates           352 k

Transaction Summary
================================================================================
Install       1 Package(s)
Upgrade       0 Package(s)

Total download size: 352 k
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
updates/prestodelta                                      | 435 kB     00:01     
Processing delta metadata
Package(s) data still to download: 352 k
xterm-253-1.fc12.i686.rpm                                | 352 kB     00:00     
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing     : xterm-253-1.fc12.i686                                    1/1 

Installed:
  xterm.i686 0:253-1.fc12                                                       

Complete!
```

---

### Post by Techsnap on 2010-01-21
Yes I know it's the package maintainers, but what I'm trying to say is none of them really give you many suitable options for ignoring dependencies. OpenSUSE with YaST will let you choose to ignore the dependencies if you really want to and that you know what you're doing. 

I've forced installed things on APT and it has forbidden the install of other packages until I remove the "broken" package when it's not broken at all. This is what I'm saying here, it's how they handle the user telling them otherwise.

---

### Post by lykwydchykyn on 2010-01-21
> **RiceMonster said:**
> ```
root@fedora:~# yum install xterm
Loaded plugins: presto, refresh-packagekit
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package xterm.i686 0:253-1.fc12 set to be updated
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package         Arch           Version                 Repository         Size
================================================================================
Installing:
 xterm           i686           253-1.fc12              updates           352 k

Transaction Summary
================================================================================
Install       1 Package(s)
Upgrade       0 Package(s)

Total download size: 352 k
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
updates/prestodelta                                      | 435 kB     00:01     
Processing delta metadata
Package(s) data still to download: 352 k
xterm-253-1.fc12.i686.rpm                                | 352 kB     00:00     
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing     : xterm-253-1.fc12.i686                                    1/1 

Installed:
  xterm.i686 0:253-1.fc12                                                       

Complete!
```
That is pretty nice.  Do you mind if I print it and tack it to my corkboard?

---

### Post by Xbehave on 2010-01-21
> **Techsnap said:**
> That's not true. Sometimes it will pull in dependencies of no relevance.
I realise as a slackware user packagemanagers are not your area of expertise :P, but it's definitely the packager/ditro's fault, yum and apt (and i'd be 99% sure pacman and emerge) support recommendations and and/or logic so can be fine grained enough to only pull the minimum dependancies. If more than the essential dependencies HAVE to be pulled it's the packagers fault, not the programs.

> I don't care about typing characters, I was pointing out that "apt-get remove" sounds stupid (to me) because it contains get and remove which are opposites. Why not call the commands "apt install" and "apt remove" or something that makes more sense?Because as Techsnap correct me earlier, apt is the framework, apt-get is a frontend (a frontend that gets stuff, and even when you are removing packages it may need to get get files to fill dependencies). Why have multiple small programs instead of one do everything program? Do you really need to ask that on a unix-like OS? IIRC yum locks the database when it is running so if you are installing lots of packages you can't search. it's also good from a sandboxing perspective, apt-get needs network access, apt-cdrom needs cd access, apt-cache only needs to be able to read var, etc.

---

### Post by Simian Man on 2010-01-21
> **lykwydchykyn said:**
> That is pretty nice.  Do you mind if I print it and tack it to my corkboard?

Ricemonster's post doesn't even quite do it justice because, while it is installing or updating, it has a nice little text progress bar along with the percentage, download speed and ETA.

---

### Post by Techsnap on 2010-01-21
I just proved my point with APT:

```
aptitude install scrot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Reading task descriptions... Done  
The following NEW packages will be installed:
  giblib1{a} libgif4{a} libimlib2{a} scrot 
The following packages will be REMOVED:
  desktop-base{u} desktop-file-utils{u} fortune-mod{u} fortunes-min{u} 
  gtk2-engines-xfce{u} libfont-afm-perl{u} libfs6{u} libhtml-format-perl{u} 
  libhtml-parser-perl{u} libhtml-tagset-perl{u} libhtml-tree-perl{u} 
  libjpeg-progs{u} libjpeg7{u} libmailtools-perl{u} librecode0{u} 
  librsvg2-common{u} libthunar-vfs-1-2{u} libtimedate-perl{u} 
  libwnck-common{u} libwnck22{u} libwww-perl{u} libxfce4menu-0.1-0{u} 
  libxfcegui4-4{u} libxfconf-0-2{u} libxklavier15{u} libxml-parser-perl{u} 
  libxres1{u} libxvmc1{u} libxxf86misc1{u} orage{u} tango-icon-theme{u} 
  thunar{u} thunar-data{u} thunar-volman{u} x11-apps{u} 
  x11-session-utils{u} x11-xfs-utils{u} xdg-user-dirs{u} 
  xfce-keyboard-shortcuts{u} xfce4-appfinder{u} xfce4-mixer{u} 
  xfce4-panel{u} xfce4-session{u} xfce4-settings{u} xfce4-utils{u} 
  xfconf{u} xfdesktop4{u} xfdesktop4-data{u} xfonts-100dpi{u} 
  xfonts-75dpi{u} xfonts-base{u} xfonts-scalable{u} xfwm4{u} 
  xfwm4-themes{u} xinit{u} xinput{u} xli{u} xscreensaver{u} 
  xscreensaver-data{u} 
0 packages upgraded, 4 newly installed, 59 to remove and 0 not upgraded.
Need to get 304kB of archives. After unpacking 118MB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Get:1 http://ftp.uk.debian.org squeeze/main libgif4 4.1.6-8 [41.0kB]
Get:2 http://ftp.uk.debian.org squeeze/main libimlib2 1.4.2-5 [222kB]
Get:3 http://ftp.uk.debian.org squeeze/main giblib1 1.2.4-5 [22.3kB]
Get:4 http://ftp.uk.debian.org squeeze/main scrot 0.8-11 [19.0kB]
Fetched 304kB in 1s (293kB/s)   
(Reading database ... 60548 files and directories currently installed.)
Removing desktop-base ...
update-alternatives: using /usr/share/images/desktop-base/moreblue-orbit-wallpaper-widescreen.svg to provide /usr/share/images/desktop-base/desktop-background (desktop-background) in auto mode.
update-alternatives: using /usr/share/images/desktop-base/nightly-wallpaper.png to provide /usr/share/images/desktop-base/desktop-background (desktop-background) in auto mode.
update-alternatives: using /usr/share/images/desktop-base/debian-blueish-wallpaper.svg to provide /usr/share/images/desktop-base/desktop-background (desktop-background) in auto mode.
update-alternatives: using /usr/share/images/desktop-base/gnome-splash-curves.png to provide /usr/share/images/desktop-base/desktop-splash (desktop-splash) in auto mode.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.30-2-amd64
Found initrd image: /boot/initrd.img-2.6.30-2-amd64
done
Removing thunar-volman ...
Removing thunar ...
Removing desktop-file-utils ...
Removing xfce4-session ...
Removing fortune-mod ...
Removing fortunes-min ...
Removing gtk2-engines-xfce ...
Removing libhtml-format-perl ...
Removing libfont-afm-perl ...
Removing x11-xfs-utils ...
Removing libfs6 ...
Removing xfce4-utils ...
Removing libxml-parser-perl ...
Removing libwww-perl ...
Removing libhtml-tree-perl ...
Removing libhtml-parser-perl ...
Removing libhtml-tagset-perl ...
Removing libjpeg-progs ...
Removing libjpeg7 ...
Removing libmailtools-perl ...
Removing librecode0 ...
Removing librsvg2-common ...
Removing xfdesktop4 ...
Removing xfce4-appfinder ...
Removing libthunar-vfs-1-2 ...
Removing libtimedate-perl ...
Removing xfwm4-themes ...
Removing xfwm4 ...
Removing xfce4-settings ...
Removing xfce4-mixer ...
Removing orage ...
Removing xfce4-panel ...
Removing libwnck22 ...
Removing libwnck-common ...
Removing libxfce4menu-0.1-0 ...
Removing libxfcegui4-4 ...
Removing libxfconf-0-2 ...
Removing libxklavier15 ...
Removing libxres1 ...
Removing libxvmc1 ...
Removing xscreensaver ...
Removing libxxf86misc1 ...
Removing tango-icon-theme ...
Removing thunar-data ...
Removing x11-apps ...
Removing x11-session-utils ...
Removing xdg-user-dirs ...
Removing xfce-keyboard-shortcuts ...
Removing xfconf ...
Removing xfdesktop4-data ...
Removing xfonts-100dpi ...
Removing xfonts-75dpi ...
Removing xfonts-base ...
Removing xfonts-scalable ...
Removing xinit ...
Removing xinput ...
Removing xli ...
Removing xscreensaver-data ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Processing triggers for fontconfig ...
Selecting previously deselected package libgif4.
(Reading database ... 46469 files and directories currently installed.)
Unpacking libgif4 (from .../libgif4_4.1.6-8_amd64.deb) ...
Selecting previously deselected package libimlib2.
Unpacking libimlib2 (from .../libimlib2_1.4.2-5_amd64.deb) ...
Selecting previously deselected package giblib1.
Unpacking giblib1 (from .../giblib1_1.2.4-5_amd64.deb) ...
Selecting previously deselected package scrot.
Unpacking scrot (from .../scrot_0.8-11_amd64.deb) ...
Setting up libgif4 (4.1.6-8) ...
Setting up libimlib2 (1.4.2-5) ...
Setting up giblib1 (1.2.4-5) ...
Setting up scrot (0.8-11) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Reading task descriptions... Done
```Thanks a lot APT.

**Yes I know it gave me the option, so don't bother pointing that out. I'm wiping this tomorrow anyway. **

---

### Post by Zoot7 on 2010-01-21
> **Techsnap said:**
> Thanks a lot APT.

**Yes I know it gave me the option, so don't bother pointing that out. I'm wiping this tomorrow anyway. **
I'd a similar problem with LMMS in Debian, apt wanted to remove the whole gnome desktop to install it. WTF?
Solution - fetch the source, compile it and package it myself. Sort of defeats the purpose of a package manager in the first place. :rolleyes:

---

### Post by Techsnap on 2010-01-21
> Solution - fetch the source, compile it and package it myself. Sort of defeats the purpose of a package manager in the first place. :rolleyes:

Yes, that and what I think is, what about those users who don't know much about these things. They'll probably just let it run anyway because they'll think that it's removing stuff because they're replacing it with newer versions if you get me. 

Anyways I'm gonna replace this install with OpenSUSE in a minute, Slackware & OpenSUSE are the only distros which haven't let me down on the desktop.

---

### Post by YeOK on 2010-01-21
> **Techsnap said:**
> **Yes I know it's the package maintainers, but what I'm trying to say is none of them really give you many suitable options for ignoring dependencies.** OpenSUSE with YaST will let you choose to ignore the dependencies if you really want to and that you know what you're doing. 

I've forced installed things on APT and it has forbidden the install of other packages until I remove the "broken" package when it's not broken at all. This is what I'm saying here, it's how they handle the user telling them otherwise.

Yum's sole purpose in life is to manage your selected packages and its dependencies. If you really wanted to install an RPM without its dependencies, you could just use RPM.

```

# rpm -ivh --nodeeps package.rpm

```

---

### Post by Xbehave on 2010-01-21
> **Techsnap said:**
> Yes, that and what I think is, what about those users who don't know much about these things. They'll probably just let it run anyway because they'll think that it's removing stuff because they're replacing it with newer versions if you get me. 

Anyways I'm gonna replace this install with OpenSUSE in a minute, Slackware & OpenSUSE are the only distros which haven't let me down on the desktop.It removed packages that had been pulled in by other packages you installed but where no longer needed, it's removing unneeded dependencies and you are complaining, what do you want it to do? If you wanted to keep any of those packages just reinstall them a package manager isn't a replacement for reading. If aptitude is going to upgrade a package it will tell you, it will not tell you it's going to remove them.

---

### Post by Techsnap on 2010-01-21
I forgot about the --nodeps option.

> t removed packages that had been pulled in by other packages you installed but where no longer needed, it's removing unneeded dependencies and you are complaining, what do you want it to do? If you wanted to keep any of those packages just reinstall them a package manager isn't a replacement for reading. If aptitude is going to upgrade a package it will tell you, it will not tell you it's going to remove them.Yep I installed scrot so thunar and stuff is no longer needed nice. You must be one of the package maintainers.

---

### Post by Zoot7 on 2010-01-21
> **Techsnap said:**
> Yes, that and what I think is, what about those users who don't know much about these things. They'll probably just let it run anyway because they'll think that it's removing stuff because they're replacing it with newer versions if you get me. 
Yes exactly. I can understand wanting to pull in and install dependencies, even if some of them aren't required. I can't understand it wanting to remove stuff willie-nillie like it does at times.
How in the world can installing an Audio editor conflict with the entire gnome desktop to the degree that the latter has to be removed?

---

### Post by Xbehave on 2010-01-21
> **YeOK said:**
> Yum's sole purpose in life is to manage your selected packages and its dependencies. If you really wanted to install an RPM without its dependencies, you could just use RPM.

```

# rpm -ivh --nodeeps package.rpm

```
I think the same thing is doable with dpkg --force-depends

---

### Post by phrostbyte on 2010-01-21
> **gnomeuser said:**
> Apt's commandline interface is arcanic and not very userfriendly. The underlying packaging format I haven't worked a lot with but it seems very hard to work with.

Yum has a very nice commandline interface, it displays information in a useful manner and it's tools are very well designed. Sadly the underlying RPM packaging format is anything if not verbose to the point of absurdity.

Of the two I like Yum the best, I also like the yum/rpm works very well with PackageKit whereas apt/dpkg does not.

The best tool as a packager isn't yum or apt though, it's Conary and it really does pretty much everything right from a packaging point of view, it is easy to work with. As a user though it is fairly slow but worst is that it doesn't correctly handle situation where you want to uninstall A which B depends on. Instead of offering to uninstall both it will refuse to do anything which isn't very helpful. Conary does have a lot of nice features though, it downloads deltas instead of full packages, it offers unlimited rollbacks and it works very well with PackageKit.

++

Conary is probably the most revolutionary package manager ever.

---

### Post by Xbehave on 2010-01-21
> **Zoot7 said:**
> I can't understand it wanting to remove stuff willie-nillie like it does at times.
If you install A, it might pull in libA progB progC
Then when you remove A (with apt-get), libA progB progC will be left on your disk until you either run apt-get autoremove or aptitute. If you explicitly install libA and progB then they will be kept around.

---

### Post by Zoot7 on 2010-01-21
> **Xbehave said:**
> If you install A, it might pull in libA progB progC
Then when you remove A (with apt-get), libA progB progC will be left on your disk until you either run apt-get autoremove or aptitute. If you explicitly install libA and progB then they will be kept around.
I probably should have said when it removes stuff willie-nillie when you install something else. I can't see the reasoning behind removing the gnome desktop to install LMMS.
Don't get me wrong, I use Debian all the time and it is indeed my distro of choice, but apt is a downright disaster at times.

---

### Post by phrostbyte on 2010-01-21
> **Zoot7 said:**
> I probably should have said when it removes stuff willie-nillie when you install something else. I can't see the reasoning behind removing the gnome desktop to install LMMS.
Don't get me wrong, I use Debian all the time and it is indeed my distro of choice, but apt is a downright disaster at times.

The Debian package format has a conflicts property such that

Conflicts: ubuntu-desktop

Would make installing a package with ubuntu-desktop not permitted, and possibly remove packages related to ubuntu-desktop when installed.

---

### Post by Xbehave on 2010-01-21
> **Zoot7 said:**
> I probably should have said when it removes stuff willie-nillie when you install something else. I can't see the reasoning behind removing the gnome desktop to install LMMS.
Don't get me wrong, I use Debian all the time and it is indeed my distro of choice, but apt is a downright disaster at times.
It did it because techsnap had removed programs with apt-get which doesn't remove unneeded programs by default, then later he installed a program with aptitude which does. The only times I have seen apt do anything stupid it has been either user error or packager error (these are usually easy to fix, so are worth filing bug reports about)

---

### Post by k64 on 2010-01-21
I didn't expect this thread to become a 10-page debate. Linux is Linux, and anything on top of it really doesn't matter too much to me.

FOSS = Okay, no matter what! Proprietary Software = Bad.

---

### Post by lykwydchykyn on 2010-01-21
> **Techsnap said:**
> I forgot about the --nodeps option.

Yep I installed scrot so thunar and stuff is no longer needed nice. You must be one of the package maintainers.

I wouldn't suggest that the situation you showed isn't a problem; it's that it's not a package manager problem.  It's a packaging problem.  Something depended on or conflicted with something it shouldn't have.

Package maintainers in debian and Ubuntu are known to make mistakes specifying dependencies or conflicts.  My guess is that since other distributions are also packaged by human beings, these mistakes happen there as well.  

I suppose you could criticize aptitude (or apt in general) for being very strict about enforcing conflicts and dependencies, but that kind of thing is a double-edged sword.  If there were easy ways of overriding dependency handling and force-installing or uninstalling things despite dependencies or conflicts, we'd have a whole lot of people breaking their systems this way because they took dependency handling into their own hands.

As it is you can still do this, but don't expect your package manager to be happy about it.

Out of curiosity, was that scrot/thunar problem something that happened with default repositories on a stable release?

---

### Post by Xbehave on 2010-01-21
> **k64 said:**
> FOSS = Okay, no matter what! Proprietary Software = Bad.
1) That's not true
2) How is that at all relevant, all package managers are OSS and all handle both open and closed source packages.

> **lykwydchykyn said:**
> Out of curiosity, was that scrot/thunar problem something that happened with default repositories on a stable release?
read my explanation above, this isn't a package conflict, this is a user error (the user didn't understand that aptitude removes unneeded dependencies by default)

---

### Post by Icehuck on 2010-01-21
> **Xbehave said:**
> It did it because techsnap had removed programs with apt-get which doesn't remove unneeded programs by default, then later he installed a program with aptitude which does. The only times I have seen apt do anything stupid it has been either user error or packager error (these are usually easy to fix, so are worth filing bug reports about)

That doesn't even remotely fit the problem. If you use nothing but aptitude, and use aptitude to install scrot. Then why does it uninstall xfce? Please try to tell me that autoremove some how wanted to get rid of xfce because he might have removed something like open office.

---

### Post by k64 on 2010-01-21
> **Xbehave said:**
> 1) That's not true
2) How is that at all relevant, all package managers are OSS and all handle both open and closed source packages.


read my explanation above, this isn't a package conflict, this is a user error (the user didn't understand that aptitude removes unneeded dependencies by default)

Did you even look at my first sentence? I really don't care what is on Linux as long as it is open source. I only care about the source model, and copyleft (not copyright) model.

YUM, APT, KDE, GNOME, all that doesn't matter to me.

---

### Post by Xbehave on 2010-01-21
> **Icehuck said:**
> If you use nothing but aptitude, and use aptitude to install scrot. Then why does it uninstall xfce?
It does not.
to reproduce what happened
1) apt/aptitude install xfce4
2) use apt-get to remove a package in xfce4 and accept that it removes xfce4 (notice how xfce4 was not removed when he install scrot but all the dependencies where)
3) do anything else with apt then some time latter...
4) use aptitude to do anything (such as install scrot)

there is no magic in apt/aptitude

---

### Post by Mornedhel on 2010-01-21
> **Xbehave said:**
> read my explanation above, this isn't a package conflict, this is a user error (the user didn't understand that aptitude removes unneeded dependencies by default)

No no no, this actually happens when no packages are markable for autoremove, then you install foo that requires libfoo2, and libfoo2 conflicts with libfoo1, and baz-tiger depends on libfoo1.

It happens from time to time on Ubuntu as well as Debian, it happened to me, and it's definitely a packager error (for instance libfoo2 should not conflict with libfoo1), but everybody already agrees on that. What Techsnap says is that sometimes you need to be able to override depends and conflicts.

---

### Post by Daisuke_Aramaki on 2010-01-21
@k64

You are better off opening Miley Cyrus type of threads.

---

### Post by Name change on 2010-01-21
It's long time since I've used apt and I never used yum(even though I did install OpenSuSE which uses it).
And I more or less don't care as long as it installs what it has to install nad deosn't have any problems.
But I do agre with some that pacman is getting quite bad.
It want's to install lirc with vlc WTF???

But there's still "source" compilation where you can build your own package and choose your own dependancies. (but I'm to lazy to do it... :D)

---

### Post by Xbehave on 2010-01-21
> **Mornedhel said:**
> No no no, this actually happens when no packages are markable for autoremove, then you install foo that requires libfoo2, and libfoo2 conflicts with libfoo1, and baz-tiger depends on libfoo1.

It happens from time to time on Ubuntu as well as Debian, it happened to me, and it's definitely a packager error (for instance libfoo2 should not conflict with libfoo1), but everybody already agrees on that. What Techsnap says is that sometimes you need to be able to override depends and conflicts.
The example Techsnap gives clearly looks like a case of user error, it's removing the dependencies of xfce4 but not xfce4, scrott has no conflicts. As for real packaging conflicts they are not apt/yum/any package managers fault, they are the maintainers. If libfoo1 provides /usr/lib/libfoo.so and libfoo2 provides /usr/lib/libfoo.so, how can they not conflict.

---

### Post by x3roconf on 2010-01-21
APT is a lot of better.

---

### Post by Simian Man on 2010-01-21
> **Xbehave said:**
> The example Techsnap gives clearly looks like a case of user error, it's removing the dependencies of xfce4 but not xfce4, scrott has no conflicts. As for real packaging conflicts they are not apt/yum/any package managers fault, they are the maintainers. If libfoo1 provides /usr/lib/libfoo.so and libfoo2 provides /usr/lib/libfoo.so, how can they not conflict.
OK then how about we say that Debian and its derivatives have a lot more broken packages than other distributions.  Would that make you happy?

---

### Post by Zoot7 on 2010-01-21
> **k64 said:**
> FOSS = Okay, no matter what! Proprietary Software = Bad.
Wow now that's logic. How about the situations where the proprietary software part is clearly superior to the open source alternative? 
I'll give you an example, in my line of work and studies one particular app I'm required to use on a daily basis is MATLAB. It's a programming language in its own right, that allows simulation of an absolutely hugely wide range of Engineering areas. The open source alternative is GNU Octave which has some nice libraries but is nowhere near as powerful as MATLAB.
I can't exactly say to my employer or academic supervisor "Hey lets use Octave because MATLAB is EVIL proprietary software".

> **Xbehave said:**
> The example Techsnap gives clearly looks like a case of user error, it's removing the dependencies of xfce4 but not xfce4, scrott has no conflicts. As for real packaging conflicts they are not apt/yum/any package managers fault, they are the maintainers. If libfoo1 provides /usr/lib/libfoo.so and libfoo2 provides /usr/lib/libfoo.so, how can they not conflict.
I've been using Debian for years now, and there always seems to be an isolated case whereby APT wants to remove a large portion of completely unrelated packages to install a single package.

---

### Post by Xbehave on 2010-01-21
> **Simian Man said:**
> OK then how about we say that Debian and its derivatives have a lot more broken packages than other distributions.  Would that make you happy?Well atleast were starting to blame the right people. However
1) the assumption that libfoo1 and libfoo2 will not conflict is wrong (you'd have to be using something like gobolinux or be very specific when compiling packages that depend on libfoo to make sure you link to libfoo.so.x never libfoo.so)
2) I don't think your assumption is true, I would like to see some data because I've rarely run into unneeded dependencies/conflicts whereas many claim to have problems with arch installing everything under the sun.

---

### Post by Mornedhel on 2010-01-21
> **Xbehave said:**
> The example Techsnap gives clearly looks like a case of user error, it's removing the dependencies of xfce4 but not xfce4, scrott has no conflicts. As for real packaging conflicts they are not apt/yum/any package managers fault, they are the maintainers. If libfoo1 provides /usr/lib/libfoo.so and libfoo2 provides /usr/lib/libfoo.so, how can they not conflict.

*Everybody* here has agreed that it's the package maintainers' fault.

It's very possible to have two versions of a library installed side by side, by the way. You can install several versions of Berkeley's libdb. I have 4.6 and 4.7 installed side by side. Important packages depend on both (not at the same time), for reasons unknown and probably valid. There are a lot more examples.

---

### Post by Techsnap on 2010-01-21
> It did it because techsnap had removed programs with apt-get which doesn't remove unneeded programs by default, then later he installed a program with aptitude which does. The only times I have seen apt do anything stupid it has been either user error or packager error (these are usually easy to fix, so are worth filing bug reports about)

Stop making assumptions I NEVER use apt-get EVER. It didn't have ANY unneeded packages to remove because there simply weren't any.

---

### Post by Twitch6000 on 2010-01-21
I prefer anything over apt-get tbh... I find apt-get the slowest out of them all.. Not to mention it doesn't give to much detail when upgrading or install things..

---

### Post by Twitch6000 on 2010-01-21
> **Primož Papi&#269 said:**
> It's long time since I've used apt and I never used yum(even though I did install OpenSuSE which uses it).
And I more or less don't care as long as it installs what it has to install nad deosn't have any problems.
But I do agre with some that pacman is getting quite bad.
It want's to install lirc with vlc WTF???

But there's still "source" compilation where you can build your own package and choose your own dependancies. (but I'm to lazy to do it... :D)Open Suse uses zypper for its cli tool. Yast for the gui. Fedora is the only one I know of that uses yum.

---

### Post by k64 on 2010-01-21
Actually, Moblin and Linpus also use YUM.

---

### Post by xuCGC002 on 2010-01-21
I loved yum when I used Fedora. Ah, if only there were a yum-based distro with easy to install media codecs, KDE 4.3, and good Nvidia support.

---

### Post by Techsnap on 2010-01-21
Fedora, 12 has KDE 4.3 and you can just enable RPM Fusion at install time to get your codecs and nvidia drivers.

---

### Post by juancarlospaco on 2010-01-21
Ubuntu *(not by default)* theorically supports RPM since its LSB

---

### Post by xuCGC002 on 2010-01-21
> **Techsnap said:**
> Fedora, 12 has KDE 4.3 and you can just enable RPM Fusion at install time to get your codecs and nvidia drivers.

Really? What's RPM Fusion?

---

### Post by Techsnap on 2010-01-21
[http://rpmfusion.org/](http://rpmfusion.org/) Have Fun :)

---

### Post by xuCGC002 on 2010-01-21
> **Techsnap said:**
> [http://rpmfusion.org/](http://rpmfusion.org/) Have Fun :)

Guess who might be moving to Fedora?

---

### Post by Techsnap on 2010-01-21
If you download the DVD or the net install you can add those repos during install time so you can choose to install your codecs and drivers by selecting custom on anaconda. Just add these:

RPM Fusion - Free
```
http://mirrrors.rpmfusion.org/free/fedora/12/i386
```

RPM Fusion - Free - Updates
```
http://mirrrors.rpmfusion.org/free/fedora/updates/12/i386
```

RPM Fusion - Nonfree
```
http://mirrrors.rpmfusion.org/nonfree/fedora/12/i386
```

RPM Fusion - Nonfree - Updates
```
http://mirrrors.rpmfusion.org/nonfree/fedora/updates/12/i386
```

Change i386 for x86_64 if you're running 64-bit.

---

### Post by RiceMonster on 2010-01-21
> **xuCGC002 said:**
> Guess who might be moving to Fedora?

Good choice :).

---

### Post by Xbehave on 2010-01-21
> It's very possible to have two versions of a library installed side by side, by the way. You can install several versions of Berkeley's libdb. I have 4.6 and 4.7 installed side by side. Important packages depend on both (not at the same time), for reasons unknown and probably valid. There are a lot more examples.It depends on the package itself.

> **Techsnap said:**
> Stop making assumptions I NEVER use apt-get EVER. It didn't have ANY unneeded packages to remove because there simply weren't any.
Well i don't know exactly how you did it but scrot has no conflicts (the following is from ubuntu but debian's scrot packages will likely be the same)
```
apt-cache depends scrot giblib1 libc6 libimlib2  libx11-6 | grep Conflicts
Conflicts: <xlibs-data>         #old unavalible
Conflicts: <belocs-locales-bin> #old unavalible
Conflicts: tzdata               #conflicts old version
Conflicts: <tzdata-etch>        #old unavalible
```
so while i don't know exactly what you did, the packages that were removed look a lot like what would be removed if xubuntu-desktop (or debians equivalent package) had been removed and it's dependencies were catching up. Its a lot more likely that you did something wrong than you have discovered a packaging conflict that not one of the over a thousand debian scrot users came across.

---

### Post by Kenny_Strawn on 2010-02-07
YUM Bug 1: There is a limited number of packages available for YUM

YUM Bug 2: You cannot perform a distribution upgrade from the YUM command line

Gee, what now?

Note: I am just the OP under a different username, not to mention that the OP account has been deactivated and this new account is what I go by now

---

### Post by RiceMonster on 2010-02-07
> **Kenny_Strawn said:**
> YUM Bug 1: There is a limited number of packages available for YUM

That's not a "bug", and has proves nothing about whether yum is good or not. That's a problem specifically with the Fedora repos.

> **Kenny_Strawn said:**
> YUM Bug 2: You cannot perform a distribution upgrade from the YUM command line

True, you have to manually switch repos, but most people tell you to do a clean install of ubuntu on distro upgrade anyway.

> **Kenny_Strawn said:**
> Gee, what now?

You proved one thing apt can do. Would you like a cookie, kelly?

---

### Post by xuCGC002 on 2010-02-08
> **Kenny_Strawn said:**
> YUM Bug 1: There is a limited number of packages available for YUM


So how many packages a certain distro provides is the fault of YUM? Many different distros with different packages available use YUM. I don't think that counts as a bug.

> **Kenny_Strawn said:**
> 
YUM Bug 2: You cannot perform a distribution upgrade from the YUM command line


You do have a valid point there. Just one setback, though.

> **Kenny_Strawn said:**
> 
Gee, what now?


I don't know, I think I might kill myself. I have no reason to live anymore.


> **Kenny_Strawn said:**
> 
I am just the OP under a different username, not to mention that the OP account has been deactivated and this new account is what I go by now

Thanks for the info, Penelope.

---

### Post by The Toxic Mite on 2010-02-08
> **Frak said:**
> Yum < Apt

fixed it for ya ;)

---

### Post by schauerlich on 2010-02-08
> **xuCGC002 said:**
> Thanks for the info, Penelope.

It's BENNY

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2010-02-08
pacman=apt>rpm/yum

---

### Post by Frak on 2010-02-08
> **The Toxic Mite said:**
> fixed it for ya ;)
Looks like you broke it beyond repair. You are know a certified Linux Technician.

---

### Post by RichardLinx on 2010-02-09
> **frak said:**
> yum > apt

 qft!

---

### Post by Kenny_Strawn on 2010-02-09
> **schauerlich said:**
> It's BENNY

I already PMed the Mods about this name crap, and it's only going to get worse from here. From now on, that spitework will be taken as a PERSONAL ATTACK against me.

---

### Post by RichardLinx on 2010-02-09
> **Kenny_Strawn said:**
> I already PMed the Mods about this name crap, and it's only going to get worse from here. From now on, that spitework will be taken as a PERSONAL ATTACK against me.

Oh Shirley, lighten up a bit.

---

### Post by Kenny_Strawn on 2010-02-09
> **RichardLinx said:**
> Oh Shirley, lighten up a bit.

Report sent

---

### Post by RichardLinx on 2010-02-09
> **Kenny_Strawn said:**
> Report sent

I'm sorry, but who are you?

---

### Post by mushwars on 2010-02-09
> **question said:**
> **Is APT better or worse than YUM?**
**emerge is better than both** *(your vote)*

^ that is my opinion of apt, though if I had to choose between the 2 I would choose aptitude.

( don't worry I used ubuntu when I was younger for [s]many months[/s]about a year before upgrading to bsd )

---

### Post by schauerlich on 2010-02-09
> **Kenny_Strawn said:**
> name crap

How did that get through the word filter? Bad Kenny.

---

### Post by mushwars on 2010-02-09
oh and, I forgot to mention how nice emerge is when you can mask the version that you dont want so you get the newest version or the use of the ~x86 to make your system unstable and on the bleeding edge.


Then you have --depclean inplace of autoremove which the name its self sounds a whole lot cooler.

then you have something that apt doesnt have that makes it SO much better.
```
revdep-rebuild
```
if you get a broken library this will check dependencies and repair them for you ^^

Not to mention when you install stuff, you make sure you like it first so you dont install crap on your drive. 

I like that it actually feels like its doing something, when it takes 5 minutes to install ubuntu-desktop when it takes 14 hours to install the same thing on gentoo.

But here is the thing, it you took my server harddrive or my laptop harddrive and put it in your box, it wouldnt work, you wouldnt even get past 
```
[    0.000000] KERNEL supported cpus:
```

;)

---

### Post by khelben1979 on 2010-02-11
APT always works okay with Debian Lenny, so I think it's okay!

---

