---
title: "The quest for new package versions"
date: 2005-11-20
forum: Repositories &amp; Backports
---

### Post by Erwin Van de Velde on 2005-11-20
Dear all,

First of all, I'm new to the Ubuntu community, leaving the Mandriva Cooker community due to some annoying issues (not in the least broken repositories and some weird package choices). I was attracted by some reviews and the very lively community.

I'd like to have a system that has new software (hence the former use of Cooker), but in combination with a working system: e.g. the new KDE 3.5 would be nice when it is officially released as KDE is most of the time really stable on official release but the new Xorg 6.9 before it has been declared stable by the Xorg people (as Cooker and even Mandriva 2006 did) can (and in fact did) break working systems... and even on a shiny new system I still have some work to do too you know :) 

So I'd like to know something more about the Ubuntu update policy and all I found was fragmented and confusing.
I found about the Ubuntu update policy that a released distribution like Breezy only gets security updates and really zero feature updates, is this correct?
What about the backports? What is backported, when (no Breezy backports yet), etc?
How stable is Dapper? Is it really bleeding edge like in beta software or is it bleeding edge as in the newest releases?

Last question:
Is it easy to maintain a mixed system (e.g. Breezy-Dapper)? Howto's? And is this recommendable for my needs? This of course only in the case that Dapper is to unstable and Breezy+backports to old for an adventurous guy like me ;)

Thanks a lot!
Erwin

---

### Post by SSTwinrova on 2005-11-21
[QUOTE=Erwin Van de Velde]So I'd like to know something more about the Ubuntu update policy and all I found was fragmented and confusing.
I found about the Ubuntu update policy that a released distribution like Breezy only gets security updates and really zero feature updates, is this correct?
What about the backports? What is backported, when (no Breezy backports yet), etc?
How stable is Dapper? Is it really bleeding edge like in beta software or is it bleeding edge as in the newest releases?

Last question:
Is it easy to maintain a mixed system (e.g. Breezy-Dapper)? Howto's? And is this recommendable for my needs? This of course only in the case that Dapper is to unstable and Breezy+backports to old for an adventurous guy like me ;)[/QUOTE]

1. Correct, after a version is released, it will *only* get security updates.

2. Backports started out as a project by (I believe) jdong here on the forums and ballooned into an official project. Users can request backports in the corresponding forum here, and assuming that the program compiles against the stable version (and won't affect other programs/the stability of the system), it will be added into the backports repo. This is the first release that had seen backports as an official project, so there's not much to go on for giving a solid time frame. However, I was under the impression that Brezzy backports were already open. If they aren't, it shouldn't be too much longer since Dapper's repos (where the backported programs are taken from) are open.

3. Dapper (and all development versions) will go through periods of relative stability, massive unstability, and then back to being fairly stable as the release approaches. Unless you can deal with fixing issues on your own, it's generally recommended to stay away from using devel versions as your primary OS on a primary computer. So it is "bleeding edge" much more in the sense of "beta" than just "newest".

4. If you read up on apt pinning and know what you're doing, I don't think managing a mixed system would be **too** hard, but most people seem fine with backports for an up-to-date source of programs.

---

### Post by jdong on 2005-11-21
Breezy Backports is indeed open though it went off to a slow start due to the busy UBZ conference!

However, the first source packages are already trickling into Backports and it's just gonna be a matter of hours before the binaries finish building and appear in the repositories...

As far as what goes into backports, it's purely community-driven -- whatever you request.

Mixing packages, either the fancy APT pinning way, or use packages.ubuntu.com to hand-pick .debs to install.

---

