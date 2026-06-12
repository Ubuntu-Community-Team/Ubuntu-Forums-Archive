---
title: "repository list"
date: 2005-09-17
forum: Repositories &amp; Backports
---

### Post by Brad wilkinson on 2005-09-17
does anyone know where there is a list of repositories?

I'm looking for something closer to home (australia) to point at. anyone know of any mirrors down under?

---

### Post by XDevHald on 2005-09-18
[QUOTE=Brad wilkinson]does anyone know where there is a list of repositories?

I'm looking for something closer to home (australia) to point at. anyone know of any mirrors down under?[/QUOTE]
 No problem, if I am correct au for australia? :)

 >  ## Uncomment the following two lines to fetch updated software from the network
deb [http://au.archive.ubuntu.com/ubuntu]("http://au.archive.ubuntu.com/ubuntu") hoary main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu]("http://au.archive.ubuntu.com/ubuntu") hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://au.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu]("http://au.archive.ubuntu.com/ubuntu") hoary universe
deb-src [http://au.archive.ubuntu.com/ubuntu]("http://au.archive.ubuntu.com/ubuntu") hoary universe

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe

deb [http://au.archive.ubuntu.com/ubuntu]("http://au.archive.ubuntu.com/ubuntu") hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse 

---

### Post by casper_2095 on 2005-10-01
What's the difference between all these repositories listed in Synaptic by default?
I.e.
*CD Ubuntu 5.04 "Hoary Hedgehog" (binary) [Officially supported Restricted Copyright]*
This is obviously the install CD and is the definitive Hoary release.

*Ubuntu 5.04 "Hoary Hedgehog" (binary) [Officially supported Restricted Copyright]*
I guess this is as above but seems to include a few extra packages not included on the official CD.

*Ubuntu 5.04 "Hoary Hedgehog" (source) [Officially supported Restricted Copyright]*
As above but contains all the source code required to do a build.

*Ubuntu 5.04 Updates (binary) [Officially supported Restricted Copyright]*
???  Updates which are improved versions released after Hoary was, and not in direct response to security flaws.
[I]
Ubuntu 5.04 Security Updates (binary) [Officially supported Restricted Copyright][/I]
??? Critical updates which patch security flaws exposed since Hoary's release.
[I]
Ubuntu 5.04 "Hoary Hedgehog" (binary) [Community maintained Universe][/I]
??? The universe of packages contributed by the general public which do not bear, and probably don't need, Ubuntu's official blessing.
[I]
Ubuntu 5.04 Security Updates (binary) [Community maintained (Universe)][/I]
??? Criticial updates to the community universe, which patch flaws but don't necessarily include new features?

Is this close?

---

