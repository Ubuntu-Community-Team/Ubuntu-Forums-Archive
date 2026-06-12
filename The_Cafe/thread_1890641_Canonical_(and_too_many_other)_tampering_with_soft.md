---
title: "Canonical (and too many other) tampering with software unneccessarily"
date: 2011-12-03
forum: The Cafe
---

### Post by Kolusion on 2011-12-03
When I go through whats available in the Ubuntu 10.04 repository, I am seeing the "Ubuntu" versions for just about everything.  Is there any critical reason why Canonical has to tamper with everything? I think most of it was perfectly working and that it wasn't neccessary to tamper with them.  Allot of people talk about 'freedom', but what tampering with perfectly working software does is just create fragmentation in the Linux world, and drive people towards distro's rather Linux as a whole.

---

### Post by cariboo on 2011-12-04
Can you show what you mean by **tampering**? Can you give us some examples, most of what you are seeing is branding, all distributions do it.

---

### Post by jjex22 on 2011-12-04
Try to see 'branding' as a distro - for example Ubuntu and mint - let's not start that one again, but basically how the gui looks is the difference between the two. Try to remember that linux is actually GNU/Linux, as in the GNU tools and packages built around the Linux kernel - this is all every distro is - in theory, choose a kernel then the basic tools, then a package management system, then add the packages you want - TA DA! linux. In reality this is a PITA and everyone would be going round and round in cricles, with massive delays in releases, so in the interest of advancement linux code is shared - Ubuntu takes Debian and builds on it - mint takes Ubuntu and builds on it - debian takes their ideas that it liked (and were stable) and the process repeats - but across all distros.

Here's the thing - Ubuntu don't care if you systematically remove all 'branding' elements from their system, but do they care about brand identity? of course they do! they're the biggest name in linux, funded by Canonical who have shareholders, but as long as they remain part of GNU/linux, who cares? They've grown linux faster than any other distro, and ceated so many more *buntu based distros out there now that I think it's a good thing.

Ubuntu make it pretty clear their intention is to grow as an OS and to 'tweak' linux to be more noob friendly...I'm not sure how the fact that they change things from distro to distro is surprising so many people - it's always been like this. There are a hell of a lot of distros with different mission statements?

(If anyone's thinking about mentioning a certain Shell interface for Gnome 3 ... put a tenner in the Unity box and change your DE)

---

### Post by tartalo on 2011-12-04
I suspect that the OP is not talking here about branding, but about modifications to the software.

Debian has often been criticized for patching the programs when packaging them, and this lead to the well known OpenSSH fiasco. It's also the reason why Mozilla products go unbranded in Debian.

Ubuntu does modifications too.

I guess it's a problem when the patches stay in the distribution and are not sent to the original authors.

---

### Post by Copper Bezel on 2011-12-04
Upstream doesn't always want them. Or there's political crap, like the bizarre recent issues re: Ubuntu's overlay scrollbars, which Gnome wants but doesn't want to give Ubuntu the satisfaction of seeing Gnome accept into upstream.

---

### Post by beew on 2011-12-04
Branding is rather trivial, but what I don't like is that they have features disabled or crippled for a variety of reasons. For examples ffmpeg doesn't support x264, k3b doesn't rip dvd  because it is not compiled with libdvdread (installing the package doesn't help as it needed to be compiled with it), the reason is rather lame,--that libdvdread is in multiverse while k3b is in universe.. there are other examples too. If they can't provide a fully functional version because of legitimate reasons,--such as licensing issues,--  I would rather them not offer it at all, but  make the full version available in places such as medibuntu instead of putting crippled wares in the repo. Fedora doesn't offer many software with non free contents but you can get the non crippled versions from rpmfusion.

That's why it would be a bad idea to make vlc the default media player, if it does I am sure that it wouldn't be a fully working version.

---

### Post by 3Miro on 2011-12-04
Every major distribution "tampers" with software. From what I have seen, the amount of "tampering" depends only on the size of the community and the amount of resources available. As the largest distro, Ubuntu probably tampers more than others.

The whole point of GPL and Freedom Philosophy is to allow for people to tamper.

---

### Post by KiwiNZ on 2011-12-04
> **3Miro said:**
> Every major distribution "tampers" with software. From what I have seen, the amount of "tampering" depends only on the size of the community and the amount of resources available. As the largest distro, Ubuntu probably tampers more than others.

The whole point of GPL and Freedom Philosophy is to allow for people to tamper.

No the GPL is there to allow "tampering" that is approved by a small group. It has nothing to do with freedom.;)

---

### Post by Copper Bezel on 2011-12-04
It obviously has a very great deal to do with what that small group considers freedom, or they wouldn't brand it so. There's no commonsense definition of freedom to fall back on in this context, so you'd need to define your own use.

---

### Post by screaminj3sus on 2011-12-04
> **cariboo907 said:**
> Can you show what you mean by **tampering**? Can you give us some examples, most of what you are seeing is branding, all distributions do it.

Not sure if this is the type of thing the OP is talking about, but I've seen on a few occasions where ubuntu or debian patches break functionality that works fine in the upstream versions of packages. (for example on my laptop 3 finger tap to middle click works fine on pretty much any distro thats not ubuntu/ubuntu based. But ubuntu's patched synaptics input package totally breaks it)

---

### Post by Copper Bezel on 2011-12-04
Often that's the result of a bug fix for another configuration. In the case you're referring to (my netbook suffers from this as well) it's a result of tweaks relating to full-multitouch devices (which the affected touchpads are not) and there's an active bug relating to efforts to fix the new problem created for semi-multitouch devices.

---

### Post by grahammechanical on 2011-12-04
Well I never. There packages in the Ubuntu repositories that have Ubuntu in the package name. Fancy that. What is the world coming to?

There is a sensible reason for this:

> Notice that the version has a -0ubuntu1 appended to it, this is the distro revision, used so that the packaging can be updated (to fix bugs for example) with new uploads within the same source release version.

Ubuntu and Debian have slightly different package versioning schemes to avoid conflicting packages with the same source version. If a Debian package has been changed in Ubuntu, it has ubuntuX (where X is the Ubuntu revision number) appended to the end of the Debian version. So if the Debian hello 2.6-1 package was changed by Ubuntu, the version string would be 2.6-1ubuntu1. If a package for the application does not exist in Debian, then the Debian revision is 0 (e.g., 2.6-0ubuntu1).

See link to the Packaging Guide. The rules to follow for anyone interested in becoming a package maintainer.

[https://wiki.ubuntu.com/PackagingGuide/Complete]("https://wiki.ubuntu.com/PackagingGuide/Complete")

Yes, there is a very critical reason. It is a mark of professionalism.

Regards.

---

### Post by PuddingKnife on 2011-12-04
> **grahammechanical said:**
> Well I never. There packages in the Ubuntu repositories that have Ubuntu in the package name. Fancy that. What is the world coming to?

There is a sensible reason for this:



See link to the Packaging Guide. The rules to follow for anyone interested in becoming a package maintainer.

[https://wiki.ubuntu.com/PackagingGuide/Complete]("https://wiki.ubuntu.com/PackagingGuide/Complete")

Yes, there is a very critical reason. It is a mark of professionalism.

Regards.


/thread

---

### Post by Khakilang on 2011-12-05
Does it mean when Canonical modified the software to fit into Unity desktop environment?

---

### Post by Bachstelze on 2011-12-05
> **Khakilang said:**
> Does it mean when Canonical modified the software to fit into Unity desktop environment?

There are a ton of possible reasons why a package can be modified in Ubuntu. If you want to know why a specific package was modified, look at the changelog in /usr/share/doc/*package*.

*EDIT:* Also the vast majority of packages are not modified by Canonical but by the community.

---

