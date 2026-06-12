---
title: "From Win2k3 to Ubuntu Server (via SLES ... briefly)"
date: 2008-03-05
forum: Testimonials &amp; Experiences
---

### Post by waveform on 2008-03-05
**Background:**
The project I'm working on uses two Win2k3 servers, primarily for a medium sized data warehouse (~100Gb), web serving (BI apps), and development. After a couple of years I had grown fed up of dealing with Windows' various quirks. An opportunity arose for the project to obtain a couple of (much bigger) new servers, on which I was determined to install Linux and migrate most of the applications (for certain legacy reasons one application will have to remain on Windows for now, but that's not a major concern).


**First Attempt (SLES):**
Our company has various internal security policies for servers, and provides pre-built configurations for a couple of distros (RHEL and SLES) which should make compliance easy. I decided to opt for SLES 10 (having had some bad experiences with older versions of RHEL), after checking it supported all the various components we required. The installation went fairly smoothly, except to discover that configuring EVMS on it was next to impossible. Still, minor quibbles aside, after getting the base system (OS and database server) done, I figured I could do the rest remotely over SSH and headed home.

Over the next few days I discovered several rather disturbing things - the most important of which was that SLES 10's software repository was _incredibly_ out of date in several areas, and completely lacking in others. For example, Subversion 1.3, Python 2.4, mod_python 3.1 (we're using Subversion 1.4 and mod_python 3.3 on our Win2k3 boxes). For console web browsers (the server is a headless, no-X setup, and a console browser was required for certain bits of setup), there was one choice: w3m. Nothing else.

Now, I could migrate our Subversion repository from 1.4 to 1.3 without any loss of required functionality, although performance might suffer a little. Unfortunately we couldn't live with an older mod_python version (we rely on certain functions only available in 3.3, which isn't exactly a "recent" release: Feb 2007!). Lesson learned: don't just check which components are available, check the versions too, even if it seems ridiculous that they would be out of date.

I could've chosen to manually install the later versions, but then maintenance becomes difficult; I'm the only one on the project with experience administering a Linux server and was really hoping for a setup that, for the most part, could be administered by people without a great deal of Linux experience (until they can be bought up to speed). Hence, the more that could be maintained by the OS' package manager, the better (this also explains why I wanted EVMS - primarily for a nice simple GUI that could be used to easily expand the database file-system should it become necessary).

After another couple of days getting more and more frustrated with SLES' behaviour (I won't go into detail on all the other annoyances here, as this isn't the appropriate place) I decided to try something else...


**The Alternatives:**
At home I use Gentoo on a server, and my main work machine has a dual-boot XP and Gentoo setup. I think Gentoo's an excellent distro - especially for software developers. However, I'm under no illusions that it's an easy distro to maintain, or that it'd be ideal for our production servers with only one experienced Linux maintainer. So, Gentoo was out.

I could've opted for the other "blessed" distro of the company: RHEL. But I wasn't in a rush to spend yet more money on an "enterprise" distro unless I was sure it was going to work out. So, why Ubuntu? I'd done an Ubuntu server setup for a friend on an old box, and had been impressed by the ease of the LAMP stack install. The maintenance had looked tolerably simple (via aptitude), and a quick check of the Ubuntu packages site showed Gutsy had all the necessary versions of all the packages we required. Strangely, there doesn't appear to be a public package search for SLES or RHEL ... or not that I could find anyway.

Our company doesn't provide a pre-built security config for Ubuntu, but a check of the policy documents showed it probably wouldn't be difficult to comply with manually (password minimum lengths, maximum age, permissions on certain files, etc. etc. - mostly stuff that required a one-time setup). So, Ubuntu looked likely to succeed at providing the required environment with a sufficiently simple maintenance procedure. Furthermore, I knew it would be quick to install and evaluate, so if it didn't work out I'd have enough time left over for a third option.


**Second Attempt (Ubuntu):**
Given that I live 200+ miles away from the location housing the server, and didn't fancy another trip just to do the base install, I walked a colleague (who had no Linux experience) through the install over the phone. Everything went quickly and smoothly (including the manual LVM setup). Needless to say, I am *very* impressed with the Ubuntu installation environment.

Next I remotely connected to the server (SSH) and finished the application setup and policy compliance steps. No major surprises or problems here, just some minor notes:

[LIST]
[*]I was surprised (and disappointed) to see EVMS support had been removed, but a quick search turned up the reasons why and I can't say I disagree with them. That said, I'm now searching for a decent console partition manager which can handle LVM (the YaST tool on SLES provided an easy alternative for managing LVM - unfortunately I haven't discovered an alternative on Ubuntu yet).
[*]Another surprise was that the rather ancient [FONT=Courier]sysklogd[/FONT] was the default logging service. I replaced it with [FONT=Courier]syslog-ng[/FONT] partly because I'm more familiar with it, and partly because it makes complying with our security policy much easier. The replacement procedure was impressively smooth, but I was slightly concerned to see [FONT=Courier]ubuntu-minimal[/FONT] get removed (given that the description seems to indicate it's necessary for certain distro-related upgrade procedures). Hopefully this won't cause much pain down the road, but for now everything seems fine.
[*]I encountered one strange problem after an [FONT=Courier]apt-get upgrade[/FONT] on one of the servers immediately following the initial installation. Somehow, [FONT=Courier]libcrypto[/FONT] got trashed by the upgrade (something failed in the ldconfig step which I hadn't noticed), which prevented me from logging in via SSH after a reboot. A simple [FONT=Courier]apt-get --reinstall[/FONT] fixed it, but obviously I had to get my colleague onsite to perform the procedure (being unable to reach the server myself anymore).
[*]Incidentally, I found the Ubuntu docs _excellent_. I only needed to refer to them a couple of times (to brush up on [FONT=Courier]aptitude[/FONT] and [FONT=Courier]dpkg[/FONT]), but they proved easy to locate and navigate. They also have a rather different "feel" to the Gentoo docs that I'm used to: informative without including extraneous technical material (I think I prefer the Gentoo style, but I wouldn't suggest changing the Ubuntu docs; they're just right given the focus of the distro on simplicity and ease-of-use).
[/LIST]

I've encountered no real issues in the migration of various applications from Windows - but this isn't too surprising given we deliberately chose many of those applications with a view to a Linux migration at some point (Apache, Subversion, Python, PostgreSQL, Trac, OpenLDAP, etc.).


**Conclusion:**
The migration isn't yet fully complete (I've still got to transfer the full data warehouse content which, for reasons unrelated to Ubuntu, is going to be slightly complex). However, my experience thus far is that Ubuntu has met every requirement (either out of the box, or with a minimal amount of effort).

There are some rough edges; it would be nice to see a polished console administration tool like SLES' YaST at some point (which includes things like LVM configuration). But overall such things aren't absolute "requirements", so much as things it would be "nice to have". More important that the distribution contains the right packages with the right versions, and a simple interface for maintaining them. Here, Ubuntu has excelled.


Anyway, that's quite enough waffling ... many thanks for an excellent distribution!

---

### Post by wPwLUi3N on 2008-03-28
That is a lot of effort you put in there!!! 

Hard work and persistence always pays.

I am pretty sure you will be successful in the end.

---

