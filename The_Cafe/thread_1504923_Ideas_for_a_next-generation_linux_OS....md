---
title: "Ideas for a next-generation linux OS..."
date: 2010-06-08
forum: The Cafe
---

### Post by Sporkman on 2010-06-08
Just thinking out loud here...

If I were were to bring linux into the 21st century from the ground up, I'd do two things:

A. Restructure the filesystem
B. Make executable access control policies mandatory

Re A: The current system is archaic & inconsistent (etc, var, home, etc.). I'd redo it as follows, for example:

config
   config/<categories, apps, not sure>
bin
   bin/base (system execs)
   bin/apps (installed apps, perhaps?)
log
locks
tmp
sys (stuff from proc & dev, for example)
users
public (stuff avaliable to the network unsecured)

...etc. Or, perhaps we could turn it on its head & do the top level on an app basis, with bin, config, etc in each app directory.

What are your thoughts on how we could modernize the filesystem?

Re B: Think Apparmor-style permissions. Kernel level. To make a file executable, you need to register an access control profile (as root). If you do not have root privileges, then you can create an executable in "probationary mode", which would have a standard profile assigned to it which would be very restrictive.

This would apply to all executable on the system, including the system ones like ls, chmod, bash, etc.

Anybody else want to chime in on how you'd design things if you could start "from the ground up" so to speak?

---

### Post by LowSky on 2010-06-08
So you want a file system and access control which is basically based on Microsoft Windows Server?

---

### Post by Sporkman on 2010-06-08
> **LowSky said:**
> So you want a file system and access control which is basically based on Microsoft Windows Server?

Eh?

I've never looked at MS Server.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2010-06-08
Is that possible?

---

### Post by Revolutionary101 on 2010-06-08
A. I don't understand the purpose of changing the organization of the files. By changing the places the files are, we would need to do a ton of reworking of the kernel. What advantage do you see by doing a complete rework of the kernel file system organization?

B. I understand what you are saying for this part of the rework. Although, I don't understand how it would benefit us. It may benefit us a little, but is it worth the time and effort of people to do this complete rework?

---

### Post by BrokenKingpin on 2010-06-08
> **LowSky said:**
> So you want a file system and access control which is basically based on Microsoft Windows Server?
Sure, if the layout is better.

---

### Post by Sporkman on 2010-06-08
> **Revolutionary101 said:**
> A. I don't understand the purpose of changing the organization of the files. By changing the places the files are, we would need to do a ton of reworking of the kernel. What advantage do you see by doing a complete rework of the kernel file system organization?

B. I understand what you are saying for this part of the rework. Although, I don't understand how it would benefit us. It may benefit us a little, but is it worth the time and effort of people to do this complete rework?

Re (A) - it would make future work/design more rationally structured & easier to maintain. It would also help security in that defining profiles in (B) would be easier. It might also improve partition-ability, so to speak.

Re (B) - it would make the system much more secure, wouldn't it?

---

### Post by koenn on 2010-06-08
> **Sporkman said:**
> Re (A) - it would make future work/design more rationally structured & easier to maintain. It would also help security in that defining profiles in (B) would be easier. It might also improve partition-ability, so to speak.


The current directory hierarchy also takes into account things like
- stuff that can be mounted off a NFS server vs stuff that *needs* to be local (files/commands/... the system needs before network is up) vs stuff you'd *prefer* to be local (eg sysadmin tools for fixing a near unbootable system)

- stuff that can be mounted read-only vs stuff that needs to be read-write

- root & system vs plain users (eg /sbin vs /bin)

- ...

Any proposal to "improve" the directory hierarchy should at least cover those areas as well. I  don't see them in the OP's suggestion.

---

### Post by Sporkman on 2010-06-08
File permissions could be enforced based on the directory context as well. For example, a file residing in /config could not be made executable, and a file residing in /bin could not be made writeable...

---

### Post by harlan on 2010-06-08
[GoboLinux]("http://www.gobolinux.org/?page=at_a_glance") is developing a new file hierarchy system. Maybe you'll find it interesting.

---

### Post by Sporkman on 2010-06-08
> **koenn said:**
> 
Any proposal to "improve" the directory hierarchy should at least cover those areas as well. I  don't see them in the OP's suggestion.

My proposal is not that specific structure, rather that the filesystem could be revamped to be more consistent. For example, re sbin vs bin we could have under /bin:

/bin/sys
/bin/usr (or "installed" or "apps")...

See where I'm going with this..?

---

### Post by Sporkman on 2010-06-08
> **harlan said:**
> [GoboLinux]("http://www.gobolinux.org/?page=at_a_glance") is developing a new file hierarchy system. Maybe you'll find it interesting.

Thanks- yes, it look like they have the same idea, except they do it the easy way via symbolic links:

> The GoboLinux system layout seems to be a major departure from the Unix tradition. Does this mean all programs need to adjusted so that they work with the new layout? Fortunately, the answer is no. Through a mapping of traditional paths into their GoboLinux counterparts, we transparently retain compatibility with the Unix legacy.

~] ls -l /dev/null | cut -b 45-
/dev/null

~] ls -l /bin/sh | cut -b 45-
sh -> /Programs/Bash/3.0/bin/bash

~] ls -l /usr/include/stdio.h | cut -b 45-
stdio.h -> /Programs/Glibc/2.3.6/include/stdio.h

There is no rocket science to this: /bin is a link to /System/Links/Executables. And as a matter of fact, so is /usr/bin. And /usr/sbin... all "binaries" directories map to the same place. Amusingly, this makes us even more compatible than some more standard-looking distributions. In GoboLinux, all standard paths work for all files, while other distros may struggle with incompatibilites such as scripts breaking when they refer to /usr/bin/foo when the file is actually in /usr/local/bin/foo.

You may have noticed that the Unix paths did not show up in the system root listing in the very first example. They are actually there, but they are concealed from view using the GoboHide kernel extension. This is for aesthetic purposes only and purely optional, though: GoboLinux does not require modifications in the kernel or any other system components. But our users seem to like it a lot. :-)


---

### Post by juancarlospaco on 2010-06-08
The FileSystem becomes replaced by the FailSystem:
/users/
/p0rn/
/ThingsIdontUnderstandBecauseImAnoob/
/ThingsIdontUnderstandBecauseImAnoob/system/
/ThingsIdontUnderstandBecauseImAnoob/system/C/

---

### Post by koenn on 2010-06-08
> **Sporkman said:**
> My proposal is not that specific structure, rather that the filesystem could be revamped to be more consistent. For example, re sbin vs bin we could have under /bin:

/bin/sys
/bin/usr (or "installed" or "apps")...

See where I'm going with this..?

in the wrong direction ?

in the current FHS, 
/bin  ->  binaries you want/need locally, eg to boot, setup network, troubleshoot  ->  mount from a local partition

/usr/bin -> binaries/executables for end users / applications -> could be mounted from NFS, eg to provide the same set of apps to multiple machines

by mixing them, you'd gave up that advantage.

---

### Post by Sporkman on 2010-06-08
> **koenn said:**
> in the wrong direction ?

in the current FHS, 
/bin  ->  binaries you want/need locally, eg to boot, setup network, troubleshoot  ->  mount from a local partition

/usr/bin -> binaries/executables for end users / applications -> could be mounted from NFS, eg to provide the same set of apps to multiple machines

by mixing them, you'd gave up that advantage.

You could still mount them as such via the bin/sys and bin/usr scheme.

...but if you think it's more rational to put the usage context layer on top, then we could go with:

sys
sys/bin
sys/config
usr
usr/bin
usr/config

...etc.

With the filesystem structure better defined, the system could enforce appropriate file permissions and access control.

---

### Post by koenn on 2010-06-08
> **Sporkman said:**
> You could still mount them as such via the bin/sys and bin/usr scheme.

but it would require a lot more separate exports and an equal lot of separate mounts, no ? 

> **Sporkman said:**
> 
...but if you think it's more rational to put the usage context layer on top, ...

With the filesystem structure better defined, the system could enforce appropriate file permissions and access control.

I haven't given it much thought, really, so i don't have a solid opinion in this. The current layout never bothered me from a sysadmin point of view, and as an end user, /home/me is all you need to know.

All I'm saying is, there's quite a bit of rationale behind the current FSH, and people suggesting improvements should at least be aware of it.

---

### Post by beren.olvar on 2010-06-08
The fact you don't like the hierarchy doesn't mean it is not well defined.

An improvement I think will come soon is the database-like file systems. I think Haiku project is using something like that, and I love the idea.

---

### Post by aysiu on 2010-06-08
Why does the end user need to see the filesystem hierarchy?

Rather than rearranging the hierarchy, which functions just fine as it is, why not just eliminate the need for non-programmers to see the hierarchy?

This is what Apple does with Mac OS X. OS X still has /bin and /lib and /usr, but 99% of Mac users either never see those directories or don't have to see them unless they want to. The end users basically sees their username (/Users/*username*) with all their files and such, mounted volumes (/Volumes/*mount name*), and applications (/Applications/*program name*).

There's no good reason a Linux distro couldn't have some sensible names and just hide the current hierarchy from the end user. GoBo does something like this, except GoBo is **not** designed for novices.

---

### Post by Sporkman on 2010-06-08
> **beren.olvar said:**
> The fact you don't like the hierarchy doesn't mean it is not well defined.


Maybe it's well defined, but it seems rather haphazard. A lot of config stuff goes in /etc, but the system init scripts also go in /etc. /var contains /var/log, /var/lock, and /var/cache, but it also contains /var/games (game data files?), /var/lib, /var/run (which looks like stuff that should go in /proc), and /var/www (!).

The stuff under /proc seems closely related to /dev, and likewise the contents of /sys. /usr contains a directory called "games"...

---

### Post by Penguin Guy on 2010-06-08
Such a change is impossible without badly breaking compatibility - it would require lots of work and make porting of programs much harder. I don't think a change like this is worth it, although I would like to see a non-hierarchical file system that supports tags and more advanced metadata.

On a related subject - does anyone else not see the sense in using '.' to mark a hidden file??

---

### Post by Sporkman on 2010-06-08
> **aysiu said:**
> Why does the end user need to see the filesystem hierarchy?

Rather than rearranging the hierarchy, which functions just fine as it is, why not just eliminate the need for non-programmers to see the hierarchy?

I'm talking about from a system design point of view. I would think you'd want a rational and consistent hierarchical layout. It would simplify system maintenance and facilitate better security.

---

### Post by Sporkman on 2010-06-08
BTW I'm not trying to bad-mouth the way things are now nor criticize anybody involved in any decision making. I'm just trying to strike up a conversation about what decisions could be made if a complete re-design occurred (not likely of course :) ).

---

### Post by sisco311 on 2010-06-08
> **Sporkman said:**
> 
The stuff under /proc seems closely related to /dev, and likewise the contents of /sys. /usr contains a directory called "games"...

:)

---

### Post by koenn on 2010-06-08
> **Sporkman said:**
> Maybe it's well defined, but it seems rather haphazard. A lot of config stuff goes in /etc, but the system init scripts also go in /etc. /var contains /var/log, /var/lock, and /var/cache, but it also contains /var/games (game data files?), /var/lib, /var/run (which looks like stuff that should go in /proc), and /var/www (!).

The stuff under /proc seems closely related to /dev, and likewise the contents of /sys. /usr contains a directory called "games"...

/proc, /dev, /sys, ... don't contain real files, they are a file-like representation of other system components (eg /proc is +/- a representation of kernel processes in RAM). you can't 'put' things there they way you do in '/var/run'

/var is 'variable' data, so it's one of those partitions that always need to be mounted read/write. It contains mainly system housekeeping data (lock files, caches, pid files, ...) and some other stuf than needs to be writeable.

I agree /var/www and the likes is a bit weird - there's a new trend to put those under /srv ( ~ "data served by this system") 

having init scripts in /etc may be an arbitrary decision, or you could see them as configuration files to the startup procedure.

---

### Post by Sporkman on 2010-06-08
> **koenn said:**
> /proc, /dev, /sys, ... don't contain real files, they are a file-like representation of other system components (eg /proc is +/- a representation of kernel processes in RAM). you can't 'put' things there they way you do in '/var/run'


Agreed - I'd propose they be put under the same directory, for example under "everythingsafileinunix" (ha ha). Then we could have:

everythingsafileinunix/proc (minus the hardware description files)
everythingsafileinunix/dev
everythingsafileinunix/<something> (the hardware description files in /proc)

---

### Post by sisco311 on 2010-06-08
> **Sporkman said:**
> Agreed - I'd propose they be put under the same directory, for example under "everythingsafileinunix" (ha ha). Then we could have:

everythingsafileinunix/proc (minus the hardware description files)
everythingsafileinunix/dev
everythingsafileinunix/<something> (the hardware description files in /proc)

what's your point?

---

### Post by Sporkman on 2010-06-08
> **sisco311 said:**
> what's your point?

Consistent hierarchical organization, where the top layer is defined based on a particular attribute (either file type, usage context, ownership, whatever), then the next layer is organized base on a different attribute, but one that is more applicable to its parent category.

Let me put it another way: If you could do it all over again, would you choose the exact same layout?

Obviously this scheme grew incrementally over a long period, during which things have changed a lot.

---

### Post by sisco311 on 2010-06-08
> **Sporkman said:**
> 
Consistent hierarchical organization, where the top layer is defined based on a particular attribute (either file type, usage context, ownership, whatever), then the next layer is organized base on a different attribute, but one that is more applicable to its parent category.


We do have a consistent hierarchical organization.

> **Sporkman said:**
> 
Obviously this scheme grew incrementally over a long period, during which things have changed a lot.

point taken! please feel free to (re)implement it in a better way!!

---

### Post by mmix on 2010-06-08
any linux distro which support fbui, i will use it only.
Framebuffer UI (fbui) in-kernel Linux windowing system
[http://home.comcast.net/~fbui/](http://home.comcast.net/~fbui/)

---

### Post by DoubleClicker on 2010-06-08
One thing I notice, whenever threads like this come up, is that there is a lot of "legacy thinking".    People automatically start thinking in terms of what they already use.   

What is a much more interesting discussion would be:

If the only file system ever existed was everything is in the root and with no access restrictions;  what would be the structure of the file system you would create, to totally replace it, without trying to be compatible with any existing software.

---

### Post by szymon_g on 2010-06-08
> **Sporkman said:**
> Re A: The current system is archaic & inconsistent (etc, var, home, etc.). I'd redo it as follows, for example:

config
   config/<categories, apps, not sure>
bin
   bin/base (system execs)
   bin/apps (installed apps, perhaps?)
log
locks
tmp
sys (stuff from proc & dev, for example)
users
public (stuff avaliable to the network unsecured)

where would go programs necessary for booting and mounting partitions (i.e. /bin, /sbin) :?


> **Sporkman said:**
> 
Re B: Think Apparmor-style permissions. Kernel level. To make a file executable, you need to register an access control profile (as root). If you do not have root privileges, then you can create an executable in "probationary mode", which would have a standard profile assigned to it which would be very restrictive.

Apparmor is dead. get over it; although, tomoyo is in mainline from few versions now. how many distributions are using it (apart from Mandriva2010)?

---

### Post by Sporkman on 2010-06-08
[QUOTE=szymon_g;9432048]

Apparmor is dead. get over it; 
[quote]

It is?? Is the concept of kernel-enforced access controls dead too?

---

### Post by szymon_g on 2010-06-08
> **Sporkman said:**
> It is?? Is the concept of kernel-enforced access controls dead too?

you mean Mandatory Access Control? hell, no!

---

### Post by juancarlospaco on 2010-06-08
**LSGB**:

Linux Standard Gaming Base.

As equal to LSB but for Gaming Industry, 
OpenGL 3.x is perfect, but we have some problems on Sound area and such...

Just an Open Standard declaration,
that all mayor distros will have *(it not means used by default)*,
X, Y , Z Software Library/SoundSystem/WhatEverNeededForGames.

And an Effort to make a simple GUI*(GTK/QT/WX/Tk)*
and NCurses*(with script-friendly in mind)* 
to EASY configure input definitions_ for Gaming Mouses_.
*(Since all GUI actually uses HAL, HAL is removed now)*

A GUI Application to test the PC's 3D OpenGL capability,
better than *"run glxgears, if run its ok"*,
something descriptive but user friendly, like:
Shaders: yes!
Anisotropic: no!
blahblah: no!


*Steam is coming, lets stay prepared for these...*

---

### Post by Austin25 on 2010-06-08
Many, Many drivers.
Very easy to install.
Mainstream.
Abandon the Desk metaphor for a video game like gui.
Portable to video game systems.

---

### Post by koenn on 2010-06-09
> **DoubleClicker said:**
> One thing I notice, whenever threads like this come up, is that there is a lot of "legacy thinking".    People automatically start thinking in terms of what they already use.   

What is a much more interesting discussion would be:

If the only file system ever existed was everything is in the root and with no access restrictions;  what would be the structure of the file system you would create, to totally replace it, without trying to be compatible with any existing software.

talking on behave of the 'legacy thinking' :) :
you could also see that as a learning process: analyse what's been done before, see the rationale behind the design decisions and implementation, and learn from it improve your own designs and implementations.

Or, as someone wrote: 
"Those who don't understand UNIX are condemned to reinvent it, poorly."

---

### Post by murderslastcrow on 2010-06-09
Haha, those two changes sound extremely underwhelming considering your opening statement("bring Linux into the 21st century").

SELinux and AppArmor are being worked on and integrated as time goes on- we're preparing for issues far before they're likely to happen. The most innate security possible will continually be reworked as necessary.

And changing the file system layout? Most users don't even come in contact with these files, so this would be focusing on developers, and so far as I see it, the organization isn't really so painful at the moment. It allows for more versatility, and compatbility.

---

