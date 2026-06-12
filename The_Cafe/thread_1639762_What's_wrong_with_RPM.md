---
title: "What's wrong with RPM?"
date: 2010-12-07
forum: The Cafe
---

### Post by Spice Weasel on 2010-12-07
On these forums I've seen quite a lot of hatred towards RPM (the RPM Package Manager), whether these are misconceptions or just FUD I have no idea.

Also, I feel sorry for [Fuduntu.]("http://ubuntuforums.org/showthread.php?t=1637104")

So, I ask you today: What is wrong with RPM, and why is Dpkg (.deb) superior?

Let's clear up some misconceptions.

**.deb is used more than .rpm**

CentOS is the most used GNU/Linux distribution on servers, and uses RPM as its default package manager.

Fedora is apparently the second most used, according to DistroWatch, and Mandriva the 9th most used.

RPM is also part of the Linux Standard Base, which makes it the standard package manager for GNU/Linux. The Debian Project programmed Dpkg way before the LSB came in to existence.

**Yum is slow/terrible**

Well, that's okay then! :D

Alternative frontends for RPM:

APT (yes, [APT]("http://en.wikipedia.org/wiki/APT-RPM").)
Synaptic
urpmi
Rpmdrake
up2date
Zypper
SPM

**Aptitude is superior to all of the above.**

I agree. Hopefully, it will be ported soon. :)

But face it, the majority of Debian and Ubuntu users use APT, not Aptitude.

**I can't install .debs on a RPM system, but I can install .rpms on a Dpkg system.**

Dpkg is available in the Fedora repository, and probably in other RPM distributions repositories too.

It's okay if you prefer .deb, and I have no problem with that. The free software world is all about choice. It's just that you shouldn't flame RPM without backing it up. ;)

---

### Post by NightwishFan on 2010-12-07
I have no problem with RPM, also you can convert RPM packages to Debian ones using alien. :)

---

### Post by HermanAB on 2010-12-07
FUD.

RPM and Deb have similar features.

---

### Post by I'mGeorge on 2010-12-07
> **NightwishFan said:**
> I have no problem with RPM, also you can convert RPM packages to Debian ones using alien. :)

I've did that quite a lot actually. Some needed packages I only found on [http://rpm.pbone.net/](http://rpm.pbone.net/)

---

### Post by 3Miro on 2010-12-07
I have never seen anyone complain about RPMs on this forum. There is virtually no significant difference in technology between the two, so I don't think there can be a problem.

---

### Post by matthewbpt on 2010-12-07
I can think of one significant difference: rpm supports delta packages, deb doesn't (AFAIK). This is quite important for people with bandwidth limits/slow connections, hopefully we'll see it implemented soon!

---

### Post by Paqman on 2010-12-07
PCLOS had a nice implementation of Synaptic with RPMs. You'd never know the difference.

For 99.9% of people i'm sure it doesn't matter at all.

---

### Post by jrusso2 on 2010-12-07
At this point it is a matter of preference.  A long time ago their was some issues with RPM and it fell out of favor for a while but I think its equal to dpkg now.

---

### Post by RiceMonster on 2010-12-07
> **Spice Weasel said:**
> **Aptitude is superior to all of the above.**

I strongly disagree (mostly in terms of yum). I think apt is a mess. Just look at the output of aptitude - It's laughable.

---

### Post by MooPi on 2010-12-07
Back when I fiddled with Fedora and RPM, i can't say I had considerable issues. Fedora at the time had dependency problems but I don't think you could pin that on RPM. Aptitude is not in my opinion superior to vanilla apt. Apt for me gets the job done simple and neatly. I never have issue with apt.

---

### Post by juancarlospaco on 2010-12-07
FYI Canonical has developed a package manager that can handle both transparently, named smartpm, on repos.

---

### Post by wojox on 2010-12-07
Depends on your hardware and network. I use *yum-plugin-fastestmirror* and never had a problem. ;)

---

### Post by CharlesA on 2010-12-07
I think I know which post sparked this thread.

Anyway, rpm and debs are about equal, use whatever one you prefer.

I haven't run into any problems with yum or apt-get, myself.

---

### Post by fuduntu on 2010-12-07
> **Spice Weasel said:**
> On these forums I've seen quite a lot of hatred towards RPM (the RPM Package Manager), whether these are misconceptions or just FUD I have no idea.

Also, I feel sorry for [Fuduntu.]("http://ubuntuforums.org/showthread.php?t=1637104")

So, I ask you today: What is wrong with RPM, and why is Dpkg (.deb) superior?

Let's clear up some misconceptions.

**.deb is used more than .rpm**

CentOS is the most used GNU/Linux distribution on servers, and uses RPM as its default package manager.

Fedora is apparently the second most used, according to DistroWatch, and Mandriva the 9th most used.

RPM is also part of the Linux Standard Base, which makes it the standard package manager for GNU/Linux. The Debian Project programmed Dpkg way before the LSB came in to existence.

**Yum is slow/terrible**

Well, that's okay then! :D

Alternative frontends for RPM:

APT (yes, [APT]("http://en.wikipedia.org/wiki/APT-RPM").)
Synaptic
urpmi
Rpmdrake
up2date
Zypper
SPM

**Aptitude is superior to all of the above.**

I agree. Hopefully, it will be ported soon. :)

But face it, the majority of Debian and Ubuntu users use APT, not Aptitude.

**I can't install .debs on a RPM system, but I can install .rpms on a Dpkg system.**

Dpkg is available in the Fedora repository, and probably in other RPM distributions repositories too.

It's okay if you prefer .deb, and I have no problem with that. The free software world is all about choice. It's just that you shouldn't flame RPM without backing it up. ;)

RPM is easier to build and manage than DEB.  It is also easier to deploy to a repository.  RPM also supports verification which makes it simple to validate a system based only on the installed packages.

RPM is superior to DEB, but to the Linux *user*, there is no real difference that has any merit.

---

### Post by madjr on 2010-12-07
here is an overview of the limitations of APT (and probably also rpm based).

[http://zero-install.sourceforge.net/matrix.html](http://zero-install.sourceforge.net/matrix.html)

basically they're missing a ton of stuff and kinda suck

---

### Post by Spice Weasel on 2010-12-07
Fedora having repository mirrors enabled by default is great tbh. I haven't seen many distributions do this.

> **CharlesA said:**
> I think I know which post sparked this thread.

I also started a Fedora 14 thread on here a while ago and people were whining about RPM. Most of it is, well, just FUD.

---

### Post by Lucradia on 2010-12-07
> **NightwishFan said:**
> I have no problem with RPM, also you can convert RPM packages to Debian ones using alien. :)

You can't with some RPMs, especially when converting ALL to x64, when that ALL should've been x86 (inviso-architectures on dependencies are worse.)

Also, converting an RPM to debian, when your distro's PPAs have none of some of the required dependencies, is also bad.

Take ayttm for example.

---

### Post by NightwishFan on 2010-12-07
I know it has limitations. Every instance I have done on it has worked. I would never replace something that would tangle with the core system, or have missing libraries.

---

### Post by mips on 2010-12-07
Some of us have history with RPM and it tends to linger in my case.

---

### Post by Simian Man on 2010-12-07
The reason is historical.  Back when Red Hat, Mandrake and Suse were the top dogs in the Linux world, independent software vendors distributed software for Linux with rpm, but they weren't very good at it.  Also there were differences between Red Hat, Mandrake and Suse that made packages for one not work on the other.  So many of the packages had broken dependency requirements which people blamed on rpm itself.  Even back then rpm wasn't bad, it can't do anything if the packages you're installing are broken.

At that time, nobody made Debian packages but the Debian project and there were no distros but Debian, and near perfect clones like Mepis, so the packages were very uniform.  This gave the dpkg tool a reputation for being better than rpm, when in reality it was the packages.

Now of course, both rpm and deb distros provide a ton of well-tested packages in repos, so both tools work very well, so it comes down to personal preference.  I like the relative simplicity of rpm - for example I've never had rpm uninstall packages because they "conflict" which is something dpkg is "apt" to do.  I also **much** prefer the yum interface.

Unfortunately, some people who haven't used rpm since the early days are still under the impression that "RPM Hell" exists.  Worse, many Debian/Ubuntu fanboys parrot this belief despite never even having tried it.  I suspect that is more often the case here.

> **mips said:**
> Some of us have history with RPM and it tends to linger in my case.
I tried Ubuntu 4.10 and it's version of Gnome is way behind Fedora 14's.  Should I tell everyone that Ubuntu comes with a crappy version of Gnome?

> **juancarlospaco said:**
> FYI Canonical has developed a package manager that can handle both transparently, named smartpm, on repos.
Canonical didn't develop that.

---

### Post by NightwishFan on 2010-12-07
> **Simian Man said:**
> 
I tried Ubuntu 4.10 and it's version of Gnome is way behind Fedora 14's.  Should I tell everyone that Ubuntu comes with a crappy version of Gnome?

:popcorn:

---

### Post by cariboo on 2010-12-07
+1 to what Simian Man said, I used RedHat and Mandrake back in the day when there were dependency problems. I swore off rpm based distributions, until I tried PCLOS. Now I really don't see much difference, whether a distro uses rpms or debs. they both work equally well for me.

I think a lot of it is more due unfamiliarity than actually problems with either.

---

### Post by mips on 2010-12-07
> **Simian Man said:**
> 
I tried Ubuntu 4.10 and it's version of Gnome is way behind Fedora 14's.  Should I tell everyone that Ubuntu comes with a crappy version of Gnome?

Why be a troll and compare something from 1994 to 2010?

If you know the history of RPM dependency hell back in the day then you would know where I'm coming from. Now go tease some kids. Honestly, some times I wonder what the hell is wrong with people and forums just seem to bring out the worst.

---

### Post by NightwishFan on 2010-12-07
He was just making a joke, he meant the exact same thing as you. "Why compare something so old". :D

---

### Post by mips on 2010-12-07
> **NightwishFan said:**
> He was just making a joke, he meant the exact same thing as you. "Why compare something so old". :D

I read it differently.

---

### Post by madjr on 2010-12-07
> **mips said:**
> Honestly, some times I wonder **what the hell is wrong with people** and forums just seem to bring out the worst.

um, i think you just did, what you said #-o

---

### Post by ilovelinux33467 on 2010-12-07
Nothing wrong with RPM. In fact running openSUSE as my main distro for over 6 months now has taught me how to use RPM really well. And to those who thought that YUM was slow that should try Zypper which is a very nice front end to RPM which is extremely fast (Uses SAT solver to solve dependencies)

---

### Post by Khakilang on 2010-12-07
As a noob I don't see any difference between the 2. I had PCLinuxOS on an older computer. No problem installing any software.

---

### Post by kaldor on 2010-12-07
> **ilovelinux33467 said:**
> Nothing wrong with RPM. In fact running openSUSE as my main distro for over 6 months now has taught me how to use RPM really well. And to those who thought that YUM was slow that should try Zypper which is a very nice front end to RPM which is extremely fast (Uses SAT solver to solve dependencies)

Zypper is why I had to give up on openSUSE. I couldn't get stability for the life of me.

---

### Post by ilovelinux33467 on 2010-12-08
> **kaldor said:**
> Zypper is why I had to give up on openSUSE. I couldn't get stability for the life of me.

zypper has been extremely stable for me. What kind of problems did you have with zypper and what version of openSUSE?

---

### Post by toupeiro on 2010-12-08
Subjective to opinion, Nothings wrong with RPM.  And it wasn't that RPM's had dependency problems anymore than DEB's did as package files.  DEB's (more particularly, debian based Linux) had aptitude and the repo system down way before yum (and yum is still not there comparatively.)  as a packaging system, RPM is fine, no better or worse than deb at this point, I am simply more familiar with rpm due to the amount of years I've been using them.

---

### Post by Spice Weasel on 2010-12-08
> **toupeiro said:**
> DEB's (more particularly, debian based Linux) had aptitude and the repo system down way before yum (and yum is still not there comparatively.)  as a packaging system,

You can use APT with RPM.

---

### Post by handy on 2010-12-08
To the OP, nothing is wrong with RPM. It had problems in the past, they no longer exist.

The BIG problem is that we have two major branches - .rpm & .deb - supplying most of the Linux distros.

When the day finally comes that we can combine these two into one, we will have taken Linux a HUGE step forward. As we won't be wasting the time of so many smart people - dev's & package-managers.

---

### Post by mcduck on 2010-12-08
> **Spice Weasel said:**
> You can use APT with RPM.

The point probably wasn't what you can do these days, more that you *couldn't* do that *in the past*.

That goes for me as well, last time I used an RPM-based distro was in the times when Debian had apt but RPM-based distros had nothing equivalent. Pretty horrible experience, bad enough to keep me a safe distance away from RPM even if it might these days have usable package management tools.

---

### Post by nlsthzn on 2010-12-08
> **3Miro said:**
> I have never seen anyone complain about RPMs on this forum. There is virtually no significant difference in technology between the two, so I don't think there can be a problem.

Oh, I have found this to be true on the forum and on Ubuntu channels on IRC...

> **matthewbpt said:**
> I can think of one significant difference: rpm supports delta packages, deb doesn't (AFAIK). This is quite important for people with bandwidth limits/slow connections, hopefully we'll see it implemented soon!

One of the first differences I noticed when I switched to openSUSE and updated my system, +1 for just getting what you need :)

> **mips said:**
> Some of us have history with RPM and it tends to linger in my case.

... yet not everyone with issues decide to take them to the Internet with them :/

> **ilovelinux33467 said:**
> Nothing wrong with RPM. In fact running openSUSE as my main distro for over 6 months now has taught me how to use RPM really well. And to those who thought that YUM was slow that should try Zypper which is a very nice front end to RPM which is extremely fast (Uses SAT solver to solve dependencies)

Zypper is very feature rich, I like it a lot... (but it still doesn't have Super Cow Powers :D)

@OP, thanks for the thread, I shared your frustration... down with FUD!

---

### Post by ronnielsen1 on 2010-12-08
> Some of us have history with RPM and it tends to linger in my case.

> ... yet not everyone with issues decide to take them to the Internet with them :/

Still it's hard to let it go. I remember waiting and waiting for rpm's package manager whether it be smart package manager (which didn't seem too smart) or yum or. . . 

Seems like anytime I try a rpm based distro. . .

Something either upsets me sending me back to debian land and I can never find xmille and alot of the people on the forums have RTFM  on speed dial

---

### Post by bonixavier on 2010-12-08
Handling dependencies is a job for a human. Pkgtool all the way.

---

### Post by NCLI on 2010-12-08
> **bonixavier said:**
> Handling dependencies is a job for a human. Pkgtool all the way.
...why?

---

### Post by ilovelinux33467 on 2010-12-08
> **nlsthzn said:**
> Oh, I have found this to be true on the forum and on Ubuntu channels on IRC...



One of the first differences I noticed when I switched to openSUSE and updated my system, +1 for just getting what you need :)



... yet not everyone with issues decide to take them to the Internet with them :/



Zypper is very feature rich, I like it a lot... (but it still doesn't have Super Cow Powers :D)

@OP, thanks for the thread, I shared your frustration... down with FUD!

Hello fellow openSUSE user! I am known as ah7013 on the openSUSE forums! :)

zypper has something else (don't know what it is):
```

andrew@andrew-desktop:~> zypper moo
   \\\\\
  \\\\\\\__o
__\\\\\\\'/_

```

---

### Post by nlsthzn on 2010-12-08
> **bonixavier said:**
> Handling dependencies is a job for a human. Pkgtool all the way.

Got Slack? :D

---

### Post by mcduck on 2010-12-08
> **ilovelinux33467 said:**
> 
zypper has something else (don't know what it is):
```

andrew@andrew-desktop:~> zypper moo
   \\\\\
  \\\\\\\__o
__\\\\\\\'/_

```
A hedgehog, perhaps? They don't say "moo", though. :D

---

### Post by ilovelinux33467 on 2010-12-08
> **mcduck said:**
> A hedgehog, perhaps? They don't say "moo", though. :D

yes is could be a hedgehog :D - Imagine that - a hedgehog mooing :p

---

### Post by RiceMonster on 2010-12-08
> **NCLI said:**
> ...why?

Because some people have too much time on their hands.

---

### Post by Spice Weasel on 2010-12-08
> **nlsthzn said:**
> @OP, thanks for the thread, I shared your frustration... down with FUD!

No problem, it seems that people still haven't read it before posting though.

---

### Post by llawwehttam on 2010-12-08
Deb's and RPM's both suck!!!!!

Building from source using the ABS FTW!!!!!


It's down to personal preference in the end.

This is a forum for a deb based OS with a load of fanboys. I'm sure its just the same over at the fedora forums with RPM's.

---

### Post by KdotJ on 2010-12-08
Personally I prefer dpkg. However, and this is just a minor thing, I do think that yum's output is far superior to apt's. It is nicely formatted and has the progress bars in the terminal and not just loads of lines quickly zooming past your eyes like what you get with apt. My same opinion also applies to pacman over apt, but that's another story for another day. I know that it's a minor "look and feel" preference, but looks are important in my opinion.

---

### Post by ilovelinux33467 on 2010-12-08
I do think that it would be nice to get delta debs like how rpm has it

---

### Post by NightwishFan on 2010-12-08
.deb package fanboys. :) Most of the posters here I am sure either do not care or like both. I am the latter.

---

