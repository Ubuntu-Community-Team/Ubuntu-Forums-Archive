---
title: "rpms and managers"
date: 2010-10-05
forum: The Cafe
---

### Post by YoshiroShin on 2010-10-05
So me and a friend of mine start discussing rpms and debs after I tell him that I've been testing openSUSE and Fedora (I'm not thinking of switching away from Ubuntu, just testing :P). I'm posting it here cause you guys will obviously have deb but hopefully maybe also rpm experience on the side also. It goes like this:
---
Him:
I *hate* rpm! I won't use a distro that uses it. I used Mandriva for a while before I found Ubuntu and I was always getting headaches because of the package manager.

Me: 
from what I understand the package manager's faults would be those of itself rather those of the rpm format. There are multiple managers for rpm like Zypper (for SUSE), Synaptic (PCLinuxOS), etc than just Urpmi.

Him:
it was a massive bitch to install anything that wasn't in the repos.
Comparatively, I can throw apt a deb and it'll install the deps for me before installing the deb. It won't make it halfway through and then [bug] off telling me to "choose a pkg". It chooses the most compatible pkg.
I have to get [humped] by rpm before anything can get done and even then the pkg won't necessarily get installed.
It almost seems like rpm's pkg resolution isn't recursive or it just gives up really easily.
I find that as soon as rpm has a choice of pkgs to provide a req, it [bug]s off faster than superman on ritalin. When you finally choose a pkg, it will turn out to be incompatible with another dep of the original pkg. *Then* you're really [messed] and it'll be easier to survive a zombie invasion rather than figuring out which of the 5 choices *is* compatible.
Makes no difference because the problem is inherent to rpm, not the mgr.

Me:
hmm.. So you had this experience with Mandriva only? Are you sure you're not confusing Urpmi with rpm? How were you able to determine that it was the package format and not the manager that was messed up?

Also some rpms are made for different distros so they might have different nomentclature and assumptions of what's already installed (i.e. a Fedora rpm vs a openSUSE one).

Still I think you might try to give SUSE or Fed or even P.L.O. a shot. It wouldn't hurt to attempt to broaden your horizons a bit. This could just be Mandriva's problem. You might even like the others even if you ultimately choose to stick with Ubuntu anyway.

It wouldn't hurt, especially if you have a test machine.

Him: 
tl;dr rpm allows reqs specified as pkgs or provides (a capability, file, etc) whereas deb only allows pkgs.

I think the times I tried to install an rpm were with a one-off rpm (not from a repo) built for that distro.
I'm not confusing urpmi with rpm. rpm pkgs specify general reqs (eg requires usb-hotplug). This req may be satisfied by more than one pkg in which case the manager will prompt the user to choose an option. AFAIK, most managers don't check the user's choice against the rest of the deps, direct or not. They blindly install the choice and then continue. All goes well with *this* install. Now suppose the user goes to install another pkg that deps on usb-hotplug but alsp deps on usb-somethingelse. usb-somethingelse is only available in one package and that one package also provides usb-hotplug. The manager won't let 2 usb-hotplug pkgs be installed so it [bug]s off and leaves the user to sort it out. This phenomenon is colloquially known as rpm dependency hell. This is possible because rpm allows both deps on specific pkgs *and* provides whereas deb only allows pkgs.
I'm not saying it's not possible to get into a deb dependency hell, it's just a bit harder. This is all coming from 5 year old memory though.
---

So what do you think? Do these issues he's describing still persist? Is it an rpm design issue or was it just a package manager issue? 

P.S. I hope this was the right section to post this under. If not I apologize.

---

### Post by NightwishFan on 2010-10-05
Rpm is usually fairly ok. OpenSUSE specifically has always been ok to manage packages with, much faster in newer releases. Certainly easier to have external sources (opensuse build service).

---

### Post by YoshiroShin on 2010-10-05
Wow. Sorry about the profanity - I thought it was alright if it was censored - I posted this on Fedora forums and they locked it instantly even though they were censored out.

Once more I apologize guys.

---

### Post by YoshiroShin on 2010-10-05
(double post)

---

### Post by BuffaloX on 2010-10-05
There used to be a lot of complaints about RPM.
It sucked at handling dependencies, but AFAIK it should be much better now.

Sometimes debs made for Debian or another version of Ubuntu don't work either.

I don't think your friends arguments are valid, but they may have been a few years back.

---

### Post by NMFTM on 2010-10-05
I've had the same problems with RPM distros. I tried OpenSuse last Christmas and although I liked it better than Ubuntu, I didn't like the hassle of getting software installed. So I switched back.

Why is it that RPM distros like Ubuntu and Debian tend to have really big repos while RPM distros don't? Theirs really no reason why Fedora or OpenSuse couldn't also have repos so gigantic that you'd almost never have to manually install packages.

---

### Post by NightwishFan on 2010-10-05
I am not sure originally why however I know it has to do with Debian itself why it has so many packages. Just a flurry of maintainers perhaps.

---

### Post by RiceMonster on 2010-10-05
yum/rpm is my preferred option for packages. I have never experienced dependency hell. I've found them very easy to create and manage, plus, they've got deltas, which is very nice. Yum is also very clean and very well thought out.

---

### Post by szymon_g on 2010-10-05
personally- i find rpm's easier to create (than debs), easier to manipulate and easier to work with (checking database, validating etc)- about capabilities- they are great, much more 'natural' than pkg-only requirements (like: i install xorg, and it requires a window_manager capability provided by, let say, openbox, icewm etc etc)

@nmftm
the main reason why debian (and its forks, like ubuntu) has so big repository, is fact, debian's developpers have to follow strict rules about packaging- this is the most important part- and it's irrelative to pros/cons of debs (compared to rpm's)- and please do not forget that debian is around for many years, while some rpm's-based distros are relatively new- and that have to have impact on number of packages

---

### Post by YoshiroShin on 2010-10-06
By the way I've got this topic on openSUSE forums and Fedora forums also to generate more input although I'm not that up to replying on the Fedora one cause their forum just doesn't seem as welcoming... Anyway here's his reply:
--
Him:
let them know that A) I *was* using a pkg mgr when I experienced my  problems, B) it was some time ago so these issues have probably been  resolved, and C) I *do* know what I'm talking about.  I've used Mandriva  (just after the rebranding) for >6 months and I've used Ubuntu for  >1 year. [In other words], I'm not a newbie.
It's the ability for RPM to specify capabilities that screws you.  (contrived) scenario:
Pkg  A(not installed) provides cap_1, cap_2.  Pkg B(not installed) provides  cap_1, cap_2, cap_3.  You install Pkg C which requires cap_1+cap_2 and  conflicts with cap_3.  To satisfy the dependency, you choose Pkg A.  All  goes well.  Later, you choose to install Pkg D which requires  cap_1+cap_2+cap_3.  Now you're [in a not too good position] if you need both C and D  installed as they're mutually exclusive.       
--
More thoughts? I'm only doing this as it's a learning experience for me and he might find this conversation constructively stimulating.

---

### Post by YoshiroShin on 2010-10-06
Oh yeah you may read these also:

[http://forums.opensuse.org/english/community/general-chit-chat/447646-rpms-managers.html](http://forums.opensuse.org/english/community/general-chit-chat/447646-rpms-managers.html)
[http://forums.fedoraforum.org/showthread.php?t=252488](http://forums.fedoraforum.org/showthread.php?t=252488)

---

### Post by koenn on 2010-10-06
> **szymon_g said:**
>  ... they are great, much more 'natural' than pkg-only requirements (like: i install xorg, and it requires a window_manager capability provided by, let say, openbox, icewm etc etc)

debs do that to. You can have any nimber of packages with "Provides:windowmanage", and if a package "Depends:windowmanager", any of those packages will satisfy the dependency. 
It all depends on how the packages are configured, then, not on whether they're rpm or deb. 



> **szymon_g said:**
> 
@nmftm
the main reason why debian (and its forks, like ubuntu) has so big repository, is fact, debian's developpers have to follow strict rules about packaging- this is the most important part- and it's irrelative to pros/cons of debs (compared to rpm's)- and please do not forget that debian is around for many years, while some rpm's-based distros are relatively new- and that have to have impact on number of packages

I don't quite see how maintainers having to follow struct rules would explain a larger repository. 

Also, Redhat, the mother of rpm, has been around about the same time Debian has. So why would that explain Redhat and its forks havung smaller numbers of packages (if that indeed is the case) ?

---

### Post by Spice Weasel on 2010-10-06
apt-get remove gnome-desktop

Removing xorg, bash, grub, x11-apps... please wait...

yum remove gnome-desktop

Removing gnome-desktop, gnome-apps... please wait...

Given, that was an exaggeration... but it's still fairly accurate.

---

### Post by koenn on 2010-10-06
> **Spice Weasel said:**
> apt-get remove gnome-desktop

Removing xorg, bash, grub, x11-apps... please wait...

yum remove gnome-desktop

Removing gnome-desktop, gnome-apps... please wait...

Given, that was an exaggeration... but it's still fairly accurate.

Not exaactly sure what you're trying to say here, but
dependencies are a property of a specific .deb file, configured by the packager of that package. So if removing gnome desktop triggers the removal of xorg (and, cascading, the removal of bash, grub, etc), it's because a human decided that it should happen that way (and got away with it). If those dependencies are not arbitrary decisions but reflect actual technical requirements (as in bash can't run on a system without xorg, so removing xorg makes bash useless, so it can be removed as well), that goes to the design or the implementation of the packaged program.

it says absolutely nothing about the quality (or lack thereof) of the package management software  or the package file format/ structure/ ...

---

### Post by Spice Weasel on 2010-10-07
> **koenn said:**
> Not exaactly sure what you're trying to say here, but
dependencies are a property of a specific .deb file, configured by the packager of that package. So if removing gnome desktop triggers the removal of xorg (and, cascading, the removal of bash, grub, etc), it's because a human decided that it should happen that way (and got away with it). If those dependencies are not arbitrary decisions but reflect actual technical requirements (as in bash can't run on a system without xorg, so removing xorg makes bash useless, so it can be removed as well), that goes to the design or the implementation of the packaged program.

it says absolutely nothing about the quality (or lack thereof) of the package management software  or the package file format/ structure/ ...

I'm trying to say that rpm distributions generally handle removal of packages and dependencies much better than dpkg systems. If you remove an included package (for example, Evolution mail) on a system like Ubuntu you'll probably end up with a massive list of packages that will also be removed, but you don't generally see this on rpm systems.

---

### Post by koenn on 2010-10-07
> **Spice Weasel said:**
> I'm trying to say that rpm distributions generally handle removal of packages and dependencies much better than dpkg systems. If you remove an included package (for example, Evolution mail) on a system like Ubuntu you'll probably end up with a massive list of packages that will also be removed, but you don't generally see this on rpm systems.
I'll take your word for it, its been a while since i've used rpm-based systems (although I do still vividly remember trouble with circular dependencies and such in Suse, some 10 years ago)

but again, the trouble you describe is the result of policy set by or decisions made by humans, it's not inherent to .deb files or dpkg. 
In the case of Ubuntu, the excessive use of metapackages (packages that exist only to trigger the installation of their dependencies) in combination with auto-remove, can trigger a cascade of removals. But that's a side-effect of a policy decision, not a flaw in dpkg.

---

