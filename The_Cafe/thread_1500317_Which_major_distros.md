---
title: "Which major distros?"
date: 2010-06-03
forum: The Cafe
---

### Post by uRock on 2010-06-03
Which major distros do not use Plymouth? Or would it be easier to ask which ones do, then avoid them?

Why do I ask this? I am not trolling. I am looking for an OS that isn't using Plymouth.

Thanks,
Ronnie

---

### Post by BoneKracker on 2010-06-03
Gentoo doesn't use it, for one.

I have no idea, but I would suspect that Fedora (and all the Fedora ducklings), and Ubuntu (and all the Ubuntu ducklings) may be the only ones using it.

---

### Post by 2cute4u on 2010-06-03
Another option, would be to just ubinstall it.

---

### Post by Spr0k3t on 2010-06-03
It's not as easy as you might think.

> **philinux said:**
> Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.

---

### Post by NightwishFan on 2010-06-03
Fedora and Ubuntu use Plymouth, and Debian has it in Unstable/Experimental, but it is not default installed. (Frankly it doesnt work yet anyway).

---

### Post by uRock on 2010-06-03
> **amr.2047 said:**
> [COLOR=#000000][FONT=Times New Roman][FONT=arial]I do not think so

[RIGHT]:(
[/RIGHT]
[/FONT][/FONT][/COLOR]

?

> **NightwishFan said:**
> Fedora and Ubuntu use Plymouth, and Debian has it in Unstable/Experimental, but it is not default installed. (Frankly it doesnt work yet anyway).
Agreed. My system was running great for weeks, then out of the blue it started trying to boot into safe graphics mode with every boot. I have been forced to either run Windows or Peppermint until I get a replacement installed. I have been thinking about Arch, but I am not sure it is right for me.

---

### Post by BoneKracker on 2010-06-03
> **Spr0k3t said:**
> It's not as easy as you might think.

That's ridiculous.  No package manager should rip packages out unless there is nothing left on the system that depends upon them.  Maybe he means "mountall has a hard dependency on plymouth"?

I don't use Ubuntu, but unless I am misunderstanding this, I'd bet this is either mis-stated or easily worked around with a simple apt command that causes the otherwise orphaned package to be considered user-selected.

---

### Post by tjwoosta on 2010-06-03
> **uRock said:**
> Which major distros do not use Plymouth? Or would it be easier to ask which ones do, then avoid them?

Why do I ask this? I am not trolling. I am looking for an OS that isn't using Plymouth.

Thanks,
Ronnie

Well.. Arch, Gentoo, Slackware, Crux, Sorcerer, and LFS to name a few. Any do it yourself distro obviously. Probably many others that aren't do it yourself.

---

### Post by TironN on 2010-06-03
Arch? I'm not sure though.

---

### Post by Spr0k3t on 2010-06-03
> **BoneKracker said:**
> That's ridiculous.  No package manager should rip packages out unless there is nothing left on the system that depends upon them.  Maybe he means "mountall has a hard dependency on plymouth"?

I don't use Ubuntu, but unless I am misunderstanding this, I'd bet this is either mis-stated or easily worked around with a simple apt command that causes the otherwise orphaned package to be considered user-selected.

That's what I was thinking as well.  When I get some free time, I'm going to dupe one of my VMs and test it.

---

### Post by NightwishFan on 2010-06-03
Plymouth is good because it supports kms, which most major drivers will soon rely on.

---

### Post by BoneKracker on 2010-06-03
> **Spr0k3t said:**
> That's what I was thinking as well.  When I get some free time, I'm going to dupe one of my VMs and test it.

Well, if he meant it the other way around (mountall has a hard dependency on plymouth), then the statement makes sense.  I don't know if such a dependency is likely, since I don't have mountall.

By the way, now that I look it up, that seems like a bad idea to me -- just defaulting to mounting local filesystems willie-nillie because they don't happen to be listed in the fstab?  Is this a good idea?  Maybe it makes it easier for newly-converted Windows users who are dual-booting to get at their Windows files, but this strikes me as not only an inconvenience over the long haul but a potential security problem.  It's like "opt out" mounting of everything.  Maybe I don't understand.

---

### Post by mkvnmtr on 2010-06-03
I have a Debian install that does not use plymouth. It is xfce4 but just like the same install on Ubuntu. The difference is it uses about a third of the resources.

---

### Post by wojox on 2010-06-03
openSUSE is real good if you like KDE.

---

### Post by 98cwitr on 2010-06-03
yeah i accidentally my machine by uninstalling plymouth...gives you a cool warning beforehand though :)

---

### Post by BoneKracker on 2010-06-03
Personally, I prefer to see what's going on as I boot, so I don't like boot splash screens -- they just prevent you from seeing what's happening.

---

### Post by RedSquirrel on 2010-06-03
> **BoneKracker said:**
> Well, if he meant it the other way around (mountall has a hard dependency on plymouth), then the statement makes sense. 

[mountall]("http://packages.ubuntu.com/lucid/mountall") does indeed have a hard dependency on plymouth.

[Remove plymouth destroying system]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531331")

This [post]("http://ubuntuforums.org/showpost.php?p=9142673&postcount=10") from [RAOF]("http://ubuntuforums.org/member.php?u=31330") (Ubuntu dev) is interesting as well:

> Plymouth is not just the splash; it's also the way that the initscripts  interact with the user (such as cryptsetup needing you to enter a  passphrase, or fsck asking what to do), and sets up other things.

It's not just the splash.In summary, plymouth cannot be removed. :)

---

### Post by BoneKracker on 2010-06-03
Okay, then what we have here is a package management system that behaves very badly.  I'm far from being an expert on package management systems, but this behavior seems grossly inefficient to me.  I will just assume that the apt developers are smarter than I, and that I don't fully understand the situation.

More importantly, I think this is questionable architecture.  This shows a lack of modularity.  One should be able to remove ones boot splash (which performs one function) without destroying the system.  This is supposed to be Linux, not Windows.

---

### Post by NightwishFan on 2010-06-03
This is just the way it was packaged. I am willing to bet it could be done differently. I know of no such issues on Debian where dpkg/apt originated.

---

### Post by SunnyRabbiera on 2010-06-03
openSUSE, PClinux and Mepis might be good options.

---

### Post by kevin01123 on 2010-06-03
> **BoneKracker said:**
> Okay, then what we have here is a package management system that behaves very badly.  I'm far from being an expert on package management systems, but this behavior seems grossly inefficient to me.  I will just assume that the apt developers are smarter than I, and that I don't fully understand the situation.

More importantly, I think this is questionable architecture.  This shows a lack of modularity.  One should be able to remove ones boot splash (which performs one function) without destroying the system.  This is supposed to be Linux, not Windows.

The Ubuntu devs hard coded Plymouth that way. Try Debian if you want the apt system without these types of problems.

---

