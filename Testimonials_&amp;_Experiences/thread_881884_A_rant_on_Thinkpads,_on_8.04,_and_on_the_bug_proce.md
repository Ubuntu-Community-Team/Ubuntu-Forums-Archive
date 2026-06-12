---
title: "A rant on Thinkpads, on 8.04, and on the bug process."
date: 2008-08-06
forum: Testimonials &amp; Experiences
---

### Post by grendel_khan on 2008-08-06
It's traditional to vent about this sort of thing in the bug report, but I reckon it's more polite to do so here.

I normally wait for at least a few weeks after the release date to upgrade my copy of Ubuntu. Thus it was that I didn't update until just recently; I'd been happily running Gutsy, though there were a few kernel bugs fixed in newer releases I wanted to take advantage of, along with tickless support to drop my power consumption.

I ran into two major problems, one of which was known several weeks ago, and one of which was known since *March*.

The first was [the localedef hang on upgrade (LP #249340)]("https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340"); apparently a recent kernel doesn't play nicely with the upgrade process. There was a workaround that involved sticking my hands into the upgrade mechanism, and eventually realizing that I should renice the unkillable spinning localedef process if I wanted the rest of the upgrade to get any CPU time whatsoever.

Booting into the new kernel (2.6.24-19.36) caused several problems. There was an inexplicable five-minute pause early in the boot process. Sound and wireless didn't work. Wondering if I'd done something wrong, I hopped to another machine in the apartment and found [IBM T40 breaks under Hardy with 2.6.24 kernel (LP #209342)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209342"). I have a Thinkpad T40p, and the symptoms I saw were identical to those reported by other users. Several solutions were proposed, including delving into the use of "git bisect" to find the commit between 2.6.24 and 2.6.25 which eventually fixed it. (As the broken and fixed versions were in different git trees, I have no idea how this would work.) A copy of the newer kernel, built for Hardy, was posted; the bug reporters used it, and the issue was apparently abandoned. The custom kernel is no longer in the PPA, so the problem is exactly as unfixed as it was before it was put up.

I fetched the source packages for "linux-ports" in Intrepid (apparently the kernel build infrastructure has changed this from "linux-meta", which it was in Hardy), and it was time to party like it was 1994, by building my own kernel. dpkg-buildpackage simply hung, so I ran "AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-386" as suggested on [Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile#Build%20the%20kernel%20(when%20source%20is%20from%20git%20repository,%20or%20from%20apt-get%20source)"). After realizing that building the kernel requires more than 1.5GB of free space, and that my disk was in its steady state, I gave up on this tack, and elected to simply install the kernel packages built for Intrepid. Because I couldn't find the Intrepid equivalent of my linux-restricted-modules-386 package, and because my wireless requires a driver in -restricted, I downloaded what looked like the right packages from packages.ubuntu.com and installed them with dpkg -i.

This, surprisingly, *did* end up working, and I'm enjoying a roughly one-third reduction in power usage at idle; apart from the occasional burst of static (happened at startup and again at login; hoping that's the last of it), the sound works, and the wireless works as well. pulseaudio works, and while I haven't gotten a chance to poke at the other things I upgraded for, I have no doubt they'll work fine.

I'm more than a little put off by the handling of this issue. A long term support release appears to be seriously broken across a wide range of relatively popular hardware, going on four months after the initial release, after the first update. A special-case workaround was provided to the first person to report the bug, while the real issue remains unfixed. Apart from running a now-ancient kernel, my only option was to muddle through the process of installing a bleeding-edge kernel, which I'll have to apply unstable updates to manually if I want to keep it secure.

The bug-handling system appears to have failed here, and failed hard.

---

