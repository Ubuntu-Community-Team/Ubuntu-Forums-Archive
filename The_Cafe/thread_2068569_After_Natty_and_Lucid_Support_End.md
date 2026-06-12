---
title: "After Natty and Lucid Support End"
date: 2012-10-09
forum: The Cafe
---

### Post by Futurian on 2012-10-09
I have three of my six Linux installations running 12.04.1; two others run Natty (11.04), and one runs Lucid (10.04.4). Support for Natty is supposed to end this month. I am still trying to figure out what to do with those installations.

I've found much to like about Precise, but am still spending too much time trying to figure out how to tweak it. Both the printer and users-and-groups issues have bitten me. I'm also unhappy with some of the colors on my current desktop and in some windows, but have already spent too many hours and tried too many attempted fixes to feel that I can spend any more time on this issue.

What is everyone else going to do when Natty support ends this month? When Lucid support ends next Spring?

The last Ubuntu upgrade that I was really pleased with, and that did not disrupt my work, was from Lucid to Maverick. At times, I'm tempted to reinstall (unsupported) Maverick. People say it would be subject to security issues that have been fixed in later releases, but how serious are the security threats to Linux anyway?
Futurian is online now Report Post   	Edit/Delete Message

---

### Post by mamamia88 on 2012-10-09
> **Futurian said:**
> I have three of my six Linux installations running 12.04.1; two others run Natty (11.04), and one runs Lucid (10.04.4). Support for Natty is supposed to end this month. I am still trying to figure out what to do with those installations.

I've found much to like about Precise, but am still spending too much time trying to figure out how to tweak it. Both the printer and users-and-groups issues have bitten me. I'm also unhappy with some of the colors on my current desktop and in some windows, but have already spent too many hours and tried too many attempted fixes to feel that I can spend any more time on this issue.

What is everyone else going to do when Natty support ends this month? When Lucid support ends next Spring?

The last Ubuntu upgrade that I was really pleased with, and that did not disrupt my work, was from Lucid to Maverick. At times, I'm tempted to reinstall (unsupported) Maverick. People say it would be subject to security issues that have been fixed in later releases, but how serious are the security threats to Linux anyway?
Futurian is online now Report Post   	Edit/Delete MessagePure Debian?   Slackware?  Freebsd?  CentOS? Sounds like you are looking for something tried and true with long support

---

### Post by blackbird34 on 2012-10-09
Upgrade to Precise, i think, then no need to worry for a full five years...

Otherwise isn't Debian 6 pretty close to Lucid?

---

### Post by mamamia88 on 2012-10-09
> **blackbird34 said:**
> Upgrade to Precise, i think, then no need to worry for a full five years...

Otherwise isn't Debian 6 pretty close to Lucid?

i'd say that ubuntu and debian are 95% the same so you'd feel pretty much at home on debian. software is slightly older though.

---

### Post by jerrrys on 2012-10-09
For 10o4 desktop I have an untried tentative plan to install the server kernel (hoping this will give me kernel updates for a few more years) and open up the backports before EOL.  And this is if I still feel the need to keep 10o4 at all.  For me 12o4 isn't in bad shape, just not as customized as 10o4, which is perfect  :)

---

### Post by snowpine on 2012-10-09
when a release reaches "end of life" all official support from Canonical terminates, and the unofficial support on these forums slows to a trickle.

That being said, an advanced user could theoretically keep an end-of-life release running indefinitely by compiling their own kernels, installing the latest applications from upstream sources, and troubleshooting problems themselves (since there is no support any more). 

I quit using Ubuntu in 2009 but I still use Linux as my primary OS. There are lots of distributions or "distros" and I'm sure you can find one that works for you. In my experience on these forums, the two distros where I have seen the greatest number of former Ubuntu users find their home are Arch (for people who like the latest & greatest unstable software) and Debian (for people who like old, tested, very stable software).

---

### Post by wheeze on 2012-10-09
How long are the repos kept online after support ends for a release? I'm wondering in particular about Natty.

I install custom systems starting from a mini.iso CLI install. I can't get anything newer than Natty to pass network autoconfig, so I install using the Natty mini.iso then change sources and dist-upgrade to Precise. How long can I keep doing that?

---

### Post by snowpine on 2012-10-09
> **wheeze said:**
> How long are the repos kept online after support ends for a release? I'm wondering in particular about Natty.

I install custom systems starting from a mini.iso CLI install. I can't get anything newer than Natty to pass network autoconfig, so I install using the Natty mini.iso then change sources and dist-upgrade to Precise. How long can I keep doing that?

When a release hits "end of life" its repos are moved to: [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

I know of some users who have edited their /etc/apt/sources.list to point at old-releases; doing so would allow you to install the (old and unsupported) apps from the end-of-life repo.

---

### Post by wheeze on 2012-10-09
> **snowpine said:**
> When a release hits "end of life" its repos are moved to: [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

I know of some users who have edited their /etc/apt/sources.list to point at old-releases; doing so would allow you to install the (old and unsupported) apps from the end-of-life repo.

Thanks for that info. I imagine that's going to break the Natty mini.iso though. Aren't the installation sources hard-coded into the mini images? It won't know to go to old-releases.ubuntu.com to pull its files for installation. I don't need the repos for the old apps, I need them for the initial install. After that I change sources and use the new repos to upgrade the base install, add a DE, install apps, etc.

I guess I'll finally have to knuckle down and figure out why the network autoconfig fails on this machine with the newer mini.isos :P

---

### Post by snowpine on 2012-10-09
> **wheeze said:**
> Thanks for that info. I imagine that's going to break the Natty mini.iso though. Aren't the installation sources hard-coded into the mini images? It won't know to go to old-releases.ubuntu.com to pull its files for installation. I don't need the repos for the old apps, I need them for the initial install. After that I change sources and use the new repos to upgrade the base install, add a DE, install apps, etc.

I guess I'll finally have to knuckle down and figure out why the network autoconfig fails on this machine with the newer mini.isos :P

Ubuntu is "open source" so theoretically you could modify the installer to your exact needs.

---

### Post by Futurian on 2012-10-09
Thanks, using the old releases could be an option.

Or maybe 12.04 will mature sufficiently.

Or maybe one of the other distros ....

---

