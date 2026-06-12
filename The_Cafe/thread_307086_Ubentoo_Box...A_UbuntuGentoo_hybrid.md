---
title: "Ubentoo Box...A Ubuntu/Gentoo hybrid"
date: 2006-11-26
forum: The Cafe
---

### Post by RAV TUX on 2006-11-26
EDITED:


I have seen how you can use KNOPPIX to install Gentoo(which also installs Debian),...also I have seen Gentoo and Debian create Gentoo/BSD, and Debian/BSD hybrids...

I have also seen how SabayonLinux has made the use of Gentoo easy.

Here is the concept a Ubuntu/Gentoo hybrid:

Ubentoo


Imagine first of all Ubuntu with Emerge...Image the ease of installation of Gentoo as found in Ubuntu..

It would require (I think) making Gentoo the foundation of Ubuntu as opposed to Debian. (or making the foundation a combination of Debian and Gentoo....utilize the best from both)

The current Debian based Ubuntu would and should continue to exist but if there are any developers, idealist, dreamers who think this would be a great idea...lets here from you...

**Ubentoo....A Ubuntu/Gentoo hybrid**

This is purely conceptual and I would like to hear opinions or even give birth to a new concept

---

### Post by RAV TUX on 2006-11-26
> **RAV TUX said:**
> EDITED:


I have seen how you can use KNOPPIX to install Gentoo(which also installs Debian),...also I have seen Gentoo and Debian create Gentoo/BSD, and Debian/BSD hybrids...

I have also seen how SabayonLinux has made the use of Gentoo easy.

Here is the concept a Ubuntu/Gentoo hybrid:

Ubentoo


Imagine first of all Ubuntu with Emerge...Image the ease of installation of Gentoo as found in Ubuntu..

It would require (I think) making Gentoo the foundation of Ubuntu as opposed to Debian. (or making the foundation a combination of Debian and Gentoo....utilize the best from both)

The current Debian based Ubuntu would and should continue to exist but if there are any developers, idealist, dreamers who think this would be a great idea...lets here from you...

**Ubentoo....A Ubuntu/Gentoo hybrid**

This is purely conceptual and I would like to hear opinions or even give birth to a new concept


Interesting enough Gentoo appears to be a breed of Penguin...
[URL="http://img228.imageshack.us/img228/6585/acpengnest1bun9.jpg"]
[/URL]

---

### Post by RAV TUX on 2006-11-26
Ubentoo screenshot
[[IMG]http://img154.imageshack.us/img154/5260/gentuja1.th.png[/IMG]]("http://img154.imageshack.us/img154/5260/gentuja1.png")
(actually KNOPPIX 5.0.1 with the Gentoo Penguin nest wallpaper);)

---

### Post by shining on 2006-11-26
> **RAV TUX said:**
> I have seen how you can use KNOPPIX to install Gentoo(which also installs Debian),...also I have seen Gentoo and Debian create Gentoo/BSD, and Debian/BSD hybrids...


Yes, you can install Gentoo from any Linux distrib, just like you can install Debian or Ubuntu from any Linux distrib with debootstrap. This can be useful for doing some specific install, or if you've troubles with Gentoo, Debian or Ubuntu installer (livecd).

I don't see the link with Gentoo/BSD, and Debian/BSD hybrids, which is a total different concept. It's about keeping the GNU part of GNU/Linux, and replacing the Linux part (the kernel) with BSD. I don't really like it, but at least I can see some reasons. Here are a few:
[http://www.debian.org/ports/netbsd/why.en.html](http://www.debian.org/ports/netbsd/why.en.html)

I'm curious to learn the reasons behind your project idea, besides the "Because we can."

---

### Post by RAV TUX on 2006-11-26
> **shining said:**
> Yes, you can install Gentoo from any Linux distrib, just like you can install Debian or Ubuntu from any Linux distrib with debootstrap. This can be useful for doing some specific install, or if you've troubles with Gentoo, Debian or Ubuntu installer (livecd).

I don't see the link with Gentoo/BSD, and Debian/BSD hybrids, which is a total different concept. It's about keeping the GNU part of GNU/Linux, and replacing the Linux part (the kernel) with BSD. I don't really like it, but at least I can see some reasons. Here are a few:
[http://www.debian.org/ports/netbsd/why.en.html](http://www.debian.org/ports/netbsd/why.en.html)

I'm curious to learn the reasons behind your project idea, besides the "Because we can."
  
using Emerge with Ubuntu would be reason enough, but honestly it is just an idea.

---

### Post by NiklasV on 2006-11-26
Interesting idea...
I would love to be able to compile packages effortlessly with emerge at the same time as I would have access to the huge repository of binary debian packages.
Maybe a modification of emerge could be made, so it would compile debian packages and then call on dpkg to install the package.
The dependencies of emerge would have to somehow be satisifed by debian packages as well.

---

### Post by zgornel on 2006-11-26
I'd just settle for a synaptic with a 'compile and optimize from source' option :D

---

### Post by Dual Cortex on 2006-11-26
> **RAV TUX said:**
> Interesting enough Gentu appears to be a breed of Penguin, here is a picture of a Gentu Penguin nest...

[[IMG]http://img228.imageshack.us/img228/6585/acpengnest1bun9.th.jpg[/IMG]]("http://img228.imageshack.us/img228/6585/acpengnest1bun9.jpg")



Gentoo *IS* a type of penguins... Gentu isn't.

---

### Post by jc87 on 2006-11-26
Would´t be easier to create an Ubuntu version tweaked to use **apt-build** (sudo apt-get install apt-build if you dont know what i mean) instead of regular **apt-get**?

Since apt-build builds the software from source would be "almost" the same than using portage? (and much easier to implement)

---

### Post by RAV TUX on 2006-11-26
> **Dual Cortex said:**
> Gentoo *IS* a type of penguins... Gentu isn't.

you are correct...and there is a spelling error of Gentoo online
[http://mstecker.com/pages/antpengnest.htm](http://mstecker.com/pages/antpengnest.htm)
(unless there is more then one way to spell Gentoo/Gentu?)

particulary the picture I posted...

also I have found an old, questionable active distro by the name of Gentus
[http://home.c2i.net/espensh/#](http://home.c2i.net/espensh/#)

so it appears a new new name for this concept has to be given:

Ubentoo ?

or something completely different?

---

### Post by Old Pink on 2006-11-26
> **Dual Cortex said:**
> Gentoo *IS* a type of penguins... Gentu isn't.

[http://en.wikipedia.org/wiki/Gentoo_penguin](http://en.wikipedia.org/wiki/Gentoo_penguin)

[URL="http://en.wikipedia.org/wiki/Gentoo_Linux"]http://en.wikipedia.org/wiki/Gentoo_Linux
[/URL]

---

### Post by RAV TUX on 2006-11-26
> **jc87 said:**
> Would´t be easier to create an Ubuntu version tweaked to use **apt-build** (sudo apt-get install apt-build if you dont know what i mean) instead of regular **apt-get**?

Since apt-build builds the software from source would be "almost" the same than using portage? (and much easier to implement)
  The key program I would like to see is Emerge....on Ubuntu....

but you have a good idea...

I would like to see a Ubuntu version built on Gentoo instead of Debian,....

nothing against Debian, I love Debian.

It would be just another version of Ubuntu

Instead of a seperate release based on the Desktop: Ubuntu/Kubuntu/Xubuntu, etc

it would be a seperate release based on the core build:

Ubentoo

---

### Post by RAV TUX on 2006-11-26
> **Old Pink said:**
> [http://en.wikipedia.org/wiki/Gentoo_penguin](http://en.wikipedia.org/wiki/Gentoo_penguin)

[URL="http://en.wikipedia.org/wiki/Gentoo_Linux"]http://en.wikipedia.org/wiki/Gentoo_Linux
[/URL]
  Thank you and this error has been acknowledged...

hence the change in name of the concept to:

Ubentoo

but it ultimately could be called anything.

Please note: that all titles to post have been changed to reflect the new Title of the thread...

and thanks to all who contributed to this correction early on.

---

### Post by RAV TUX on 2006-11-26
> **NiklasV said:**
> Interesting idea...
I would love to be able to compile packages effortlessly with emerge at the same time as I would have access to the huge repository of binary debian packages.
Maybe a modification of emerge could be made, so it would compile debian packages and then call on dpkg to install the package.
The dependencies of emerge would have to somehow be satisifed by debian packages as well.
  This I 100% agree with....a hybrid of Deb packages and Emerge.

---

### Post by FyreBrand on 2006-11-26
> **RAV TUX said:**
> EDITED:


I have seen how you can use KNOPPIX to install Gentoo(which also installs Debian),...also I have seen Gentoo and Debian create Gentoo/BSD, and Debian/BSD hybrids...

I have also seen how SabayonLinux has made the use of Gentoo easy.

Here is the concept a Ubuntu/Gentoo hybrid:

Ubentoo


Imagine first of all Ubuntu with Emerge...Image the ease of installation of Gentoo as found in Ubuntu..

It would require (I think) making Gentoo the foundation of Ubuntu as opposed to Debian. (or making the foundation a combination of Debian and Gentoo....utilize the best from both)

The current Debian based Ubuntu would and should continue to exist but if there are any developers, idealist, dreamers who think this would be a great idea...lets here from you...

**Ubentoo....A Ubuntu/Gentoo hybrid**

This is purely conceptual and I would like to hear opinions or even give birth to a new conceptI think this is a really great idea.  One reason Gentoo is appealing to so many people is it let's you create the Linux you want.  The hard thing is the initial learning curve.  I have a friend who is a diehard Gentoo user and he talks about the greatness of emerge.

There are other things about Gentoo that are intriguing along with emerge.  I think if Ubuntu/Kubuntu could learn from and integrate some of Gentoo's qualities it would greatly improve the OS.

---

### Post by fuscia on 2006-11-26
in my one weekend with sabayon installed, i found emerge to be somewhat of a nightmare (i am, after all, just a humble end user). i could use synaptic back when i knew even less. so, what would be the advantage of emerge over synaptic and would it be an advantage to the majority of users?

---

### Post by RAV TUX on 2006-11-26
> **FyreBrand said:**
> I think this is a really great idea.  One reason Gentoo is appealing to so many people is it let's you create the Linux you want.  The hard thing is the initial learning curve.  I have a friend who is a diehard Gentoo user and he talks about the greatness of emerge.

There are other things about Gentoo that are intriguing along with emerge.  I think if Ubuntu/Kubuntu could learn from and integrate some of Gentoo's qualities it would greatly improve the OS.

I am glad you like the idea...

I honestly would like to pursue this further if others are interested. Again this would not counter the current lineup of Ubuntu flavors but add to them and hopefully spawn other builds

starting with Ubentoo (Ubutnu/Gentoo hybrid)

others may start 

UbunSLAX (Ubuntu/SLAX hybrid)

XubunPUP (Xubuntu/Puppy hybrid)

etc...

(please note I have edited your qoute to reflect the edit to my opening post)

---

### Post by RAV TUX on 2006-11-26
> **fuscia said:**
> in my one weekend with sabayon installed, i found emerge to be somewhat of a nightmare (i am, after all, just a humble end user). i could use synaptic back when i knew even less. so, what would be the advantage of emerge over synaptic and would it be an advantage to the majority of users?
  not over but integrated...

I found Emerge to be easy and a dream when I used Sabayon for about a month.

Again this project would not be counter to the main Ubuntu line-ups but added to it

think of Ubentoo a flavor for more advanced Linux users to use....

I picked up Emerge in about 5 minutes, and I would love to learn more about Gentoo in general

Ubentoo would be a great integration for users to transcend to if they so choose...

---

### Post by FyreBrand on 2006-11-26
Have you outlined a plan yet?  I'm curious how you envision the approach to it.  I would definitely be interested in helping to test it out.  I would love the opportunity to learn more along the way.  There is a lot I don't know about standard Linux functionality.

---

### Post by RAV TUX on 2006-11-26
> **FyreBrand said:**
> Have you outlined a plan yet?  I'm curious how you envision the approach to it.  I would definitely be interested in helping to test it out.  I would love the opportunity to learn more along the way.  There is a lot I don't know about standard Linux functionality.

I haven't outlined a roadmap, yet...but would love to do it now. This started as a concept that I immediately posted here...

If anybody would like to work on this together please PM me directly...

here is a little info about Emerge for those unfimiliar with it:

> **emerge** is the definitive command-line interface to the Portage system.  It is primarily used for installing packages, and **emerge** can automatically handle any dependencies that the desired package has. **emerge** can also update the **portage tree**, making new and updated packages available.  **emerge** gracefully handles updating installed packages to newer releases as well. It handles both source and binary packages, and it can be used to create binary packages for distribution. [http://gentoo-wiki.com/MAN_emerge_1](http://gentoo-wiki.com/MAN_emerge_1)

---

### Post by RAV TUX on 2006-11-26
> **fuscia said:**
> in my one weekend with sabayon installed, i found emerge to be somewhat of a nightmare (i am, after all, just a humble end user). i could use synaptic back when i knew even less. so, what would be the advantage of emerge over synaptic and would it be an advantage to the majority of users?  Also keep in mind fuscia ideally both the Synaptic Package Manager and Emerge would be enabled....

so you could use both or either one of your choice...

if you are not confident with Emerge you could use the Synaptic Package Manager for those of us like myself who prefer Emerge this would be great for us to have this available in our own version of Ubunto/Gentoo....Ubentoo

---

### Post by po0f on 2006-11-26
RAV TUX,

Nice idea, but how are you going to keep apt and portage from stepping on each other's feet?

---

### Post by RAV TUX on 2006-11-26
> **po0f said:**
> RAV TUX,

Nice idea, but how are you going to keep apt and portage from stepping on each other's feet?

I honestly don't know this is purely a concept right now.

The beauty is being flexible and being able to edit and customize along the way......

Such things would be overcome or reckoned with when we get into building such a project...

Again this is only a conceptual idea,,,,and it would need developers from Gentoo, Sabayon, Ubuntu, and Debian I suspect...

An idea without developers to actualize the project is simply that a great idea...and posting this an endusers forum may or may not attract developers but it doesn't hurt to dream and see if others share in this dream...

For specific objections I would not know if they can be overcome...

But thanks for posting this...I am sure we will collect many objections but there are no problems only solutions...

I know Puppy Linux was able to use Pup-Get and deb files while overcoming any problems...

I am sure Emerge and Deb files can live together...

---

### Post by darkhatter on 2006-11-26
Having ubuntu spend 26 hours compiling my system so I can get a .0025 second speed up, I'm all for it :-D . I'd love to see what Emerge is and why everyone is so happy about it.

---

### Post by RAV TUX on 2006-11-26
> **darkhatter said:**
> Having ubuntu spend 26 hours compiling my system so I can get a .0025 second speed up, I'm all for it :-D . I'd love to see what Emerge is and why everyone is so happy about it.

The best introduction is by trying SabayonLinux,
[http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

If you are unfimilar with Gentoo...

Most Ubuntu users I have spoken with who have used Gentoo miss Emerge over anything else in a Debian based Ubuntu.

This is why I feel a new Gentoo flavor of Ubuntu would be nice.

What better way to bring all of Linux together then under Ubuntu.

---

### Post by RAV TUX on 2006-11-26
> **RAV TUX said:**
> The best introduction is by trying SabayonLinux,
[http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

If you are unfimilar with Gentoo...

Most Ubuntu users I have spoken with who have used Gentoo miss Emerge over anything else in a Debian based Ubuntu.

This is why I feel a new Gentoo flavor of Ubuntu would be nice.

What better way to bring all of Linux together then under Ubuntu.

I would like to see Ubuntu eventually released in every possible flavor of Linux and BSD...

eventually you would have a one stop shop for all derivatives here under Ubuntu...

Starting with Ubentoo.

---

### Post by FyreBrand on 2006-11-26
> **RAV TUX said:**
> I honestly don't know this is purely a concept right now.

The beauty is being flexible and being able to edit and customize along the way......

Such things would be overcome or reckoned with when we get into building such a project...

Again this is only a conceptual idea,,,,and it would need developers from Gentoo, Sabayon, Ubuntu, and Debian I suspect...

An idea without developers to actualize the project is simply that a great idea...and posting this an endusers forum may or may not attract developers but it doesn't hurt to dream and see if others share in this dream...

For specific objections I would not know if they can be overcome...

But thanks for posting this...I am sure we will collect many objections but there are no problems only solutions...

I know Puppy Linux was able to use Pup-Get and deb files while overcoming any problems...

I am sure Emerge and Deb files can live together...I think the concept of dealing with package and format unification is really important.  Mark wrote an interesting article in his blog ([**Mark Shuttleworth Blog Archive #12 - Consistent Packaging**]("http://www.markshuttleworth.com/archives/66")) about packages and unification.  Even if this idea doesn't solve that problem (right away) the consideration of apt and emerge co-existing is a move in the right direction.

I also like the vision of different engines driving Ubuntu.  Going back to what intrigues me most about Gentoo is it's freedom of customization.  I think this idea in Ubuntu will draw in more community than eye candy (or lack of) or a specific software philosophy ever will.  I like the idea of an Ubuntu exactly how you want it.

---

### Post by RAV TUX on 2006-11-26
> **FyreBrand said:**
> I think the concept of dealing with package and format unification is really important.  Mark wrote an interesting article in his blog ([**Mark Shuttleworth Blog Archive #12 - Consistent Packaging**]("http://www.markshuttleworth.com/archives/66")) about packages and unification.  Even if this idea doesn't solve that problem (right away) the consideration of apt and emerge co-existing is a move in the right direction.

I also like the vision of different engines driving Ubuntu.  Going back to what intrigues me most about Gentoo is it's freedom of customization.  I think this idea in Ubuntu will draw in more community than eye candy (or lack of) or a specific software philosophy ever will.  I like the idea of an Ubuntu exactly how you want it.

Exactely, this is transcending into a wonderful Ubuntu project.

---

### Post by justin whitaker on 2006-11-26
> **RAV TUX said:**
> starting with Ubentoo (Ubutnu/Gentoo hybrid)

An interesting idea Rav....I have to say, though, I really do not see how Emerge is really all that different from APT, other than being gentoo source and debian package formats. 

Bear with me a sec: if I apt-get dist-update, or emerge world (not sure of the sytax), then you end up in the same place, more or less. The Gentoo system is more optimized, being compiled at install, but can't you do the same thing by resetting your Compiler flags and using apt-build? 

[http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

> others may start 

UbunSLAX (Ubuntu/SLAX hybrid)

You can use Thomas' kernel and patches on any distribution, althogugh I believe something in the Linux-Live script does not play all that well with debian packages. Some .ko file I believe. 

> XubunPUP (Xubuntu/Puppy hybrid)

I don't know about this one. Puppy is moving away from debian, so there could be a need for something like this, but only "because we can".

Keep in mind, "because we can" is a perfectly fine reason for me, I just wonder if time wouldn't be better spent making an existing ubuntu subproject roxxorz.

---

### Post by RAV TUX on 2006-11-26
> **justin whitaker said:**
> An interesting idea Rav....I have to say, though, I really do not see how Emerge is really all that different from APT, other than being gentoo source and debian package formats. 

Bear with me a sec: if I apt-get dist-update, or emerge world (not sure of the sytax), then you end up in the same place, more or less. The Gentoo system is more optimized, being compiled at install, but can't you do the same thing by resetting your Compiler flags and using apt-build? 

[http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)



You can use Thomas' kernel and patches on any distribution, althogugh I believe something in the Linux-Live script does not play all that well with debian packages. Some .ko file I believe. 



I don't know about this one. Puppy is moving away from debian, so there could be a need for something like this, but only "because we can".

Keep in mind, "because we can" is a perfectly fine reason for me, I just wonder if time wouldn't be better spent making an existing ubuntu subproject roxxorz.

Keep in mind that Puppy and SLAX were only given as random examples of potential future builds.

I would like to focus on discussing the viability of a Gentoo based Ubuntu...Ubentoo so users if they choose to could build a **Ubentoo Box**.;)

as far as emege goes here is a complete list of commands that can be used:
> 
  emerge - Command-line interface to the Portage system   **SYNOPSIS**

  **emerge**   [*options*] [*action*] [*ebuild* | *tbz2file* | *set* | *dependency*] ... **emerge**   **--sync** | **--info** | **--version** **emerge**   **--search** *somestring* **emerge**   **--help** [**system** | **config** | **sync**]    **DESCRIPTION**

  **emerge** is the definitive command-line interface to the Portage system.  It is primarily used for installing packages, and **emerge** can automatically handle any dependencies that the desired package has. **emerge** can also update the **portage tree**, making new and updated packages available.  **emerge** gracefully handles updating installed packages to newer releases as well. It handles both source and binary packages, and it can be used to create binary packages for distribution.   **EBUILDS, TBZ2S, SETS AND DEPENDENCIES**

  **emerge** primarily installs packages.  You can specify packages to install in one of four main ways: an *ebuild*, a *tbz2file*, a *set*, or a *dependency*.   
**ebuild**   An *ebuild* must be, at a minimum, a valid Portage package directory name without a version or category, such as **portage** or **python**. Both categories and version numbers may be used in addition, such as **sys-apps/portage** or **=python-2.2.1-r2**. **emerge** ignores a trailing slash so that filename completion can be used. The *ebuild* may also be an actual filename, such as **/usr/portage/app-admin/python/python-2.2.1-r2.ebuild**. WARNING: The implementation of **emerge /path/to/ebuild** is broken and so this syntax shouldn't be used. **tbz2file**   A *tbz2file* must be a valid .tbz2 created with **ebuild <package>-<version>.ebuild package** or **emerge --buildpkg [category/]<package>** or **quickpkg /var/db/pkg/<category>/<package>**. **set**   A *set* is a convenient shorthand for a large group of packages.  Two sets are currently supported: **system** and **world**.  **system** refers to a set of packages deemed necessary for your system to run properly.  **world** contains all the packages in **system**, plus any other packages listed in **/var/lib/portage/world**.  [See **FILES** below for more information.]  Note that a *set* is generally used in conjunction with **--update**. **dependency**   A *dependency* describes bounds on a package that you wish to install. *See [portage]("http://gentoo-wiki.com/MAN_portage_5")(5) for the details on these 'atoms'.*  For example, **>=dev-lang/python-2.2.1-r2** matches the latest available version of Python greater than or equal to 2.2.1-r2.  Similarly, **<dev-lang/python-2.0** matches the latest available version of Python before 2.0. Note that in many shells you will need to escape characters such as '<' and '='; use single- or double-quotes around the *dependency* to get around escaping problems.    **ACTIONS**

  **No action**   If no action is specified, the action is to merge in the specified packages, satisfying any dependencies that they may have. The arguments can be *ebuilds*, *tbz2s*, *sets*, or *dependencies*.  **Note that you need to use the --usepkg option if you want to install a tbz2**.  The packages are added to the **world** file at the end, so that they are considered for later updating. **--clean **(**-c**)   Cleans the system by removing packages that will not affect the functionality of the system.  The arguments can be *ebuilds*, *sets*, or *dependencies*.  For example, **emerge clean binutils** cleans out old versions of binutils; **emerge --clean net-www/mozilla-0.9.9-r2** cleans out that specific version of Mozilla.  This is generally safe to use. **Note that** --clean **does not remove unslotted packages.** **--config **   Run package specific actions needed to be executed after the emerge process has completed. This usually entails configuration file setup or other similar setups that the user may wish to run. **--depclean**   Determines all packages installed on the system that have no explicit reason for being there.  **emerge** generates a list of packages which it expects to be installed by checking the **system** package list and the **world** file. It then compares that list to the list of packages which are actually installed; the differences are listed as unnecessary packages and then unmerged after a short timeout. **WARNING: Removing some packages may cause packages which link to the removed package to stop working and complain about missing libraries.** Re-emerge the complaining package to fix this issue. **Note that changes in USE flags can drastically affect the output of --depclean.** **--help **(**-h**)   Displays help information for emerge. Adding one of the additional arguments listed above will give you more specific help information on that subject. The internal **emerge** help documentation is updated more frequently than this man page; check it out if you are having problems that this man page does not help resolve. **--info**   Produces a list of information to include in bug reports which aids the developers when fixing the reported problem.  **Please include this information when submitting a bug report.**  Expanded output can be obtained with the *--verbose* option. **--metadata**   Causes portage to process all the metacache files as is normally done on the tail end of an rsync update using **emerge --sync**.  The processing creates the cache database that portage uses for pre-parsed lookups of package data. **--prune **(**-P**)   **WARNING: This action can remove important packages!** Tries to remove all but the last version installed. Since the command currently does not handle multiple versions of the same package properly, beware! This does not check dependencies, so it may also remove packages necessary for the proper operation of your system. **Use** --clean **instead unless you really know what you're doing**.  Its arguments can be *ebuilds*, *sets*, or *dependencies* -- see **--clean** above for examples.  You have been warned! **--regen**   Causes portage to check and update the dependency cache of all ebuilds in the portage tree. The cache is used to speed up searches and the building of dependency trees. This command is not recommended for rsync users as rsync updates the cache using server-side caches. If you do not know the differences between a 'rsync user' and some other user, then you are a 'rsync user' :). Rsync users should simply run **emerge --sync** to regenerate the cache.  After a portage update, rsync users may find it convenient to run **emerge --metadata** to rebuild the cache as portage does at the end of a sync operation. **--resume**   Resumes the last merge operation. Please note that this operation will only return an error on failure. If there is nothing for portage to do, then portage will exit with a message and a success condition. **--search **(**-s**)   Searches for matches of the supplied string in the portage tree. The --search string is a regular expression.  For example, **emerge --search "^kde"** searches for any package that starts with "kde"; **emerge --search "gcc$"** searches for any package that ends with "gcc"; **emerge --search "office"** searches for any package that contains the word "office".  If you want to search the package descriptions as well, use the **--searchdesc** action. **--searchdesc **(**-S**)   Matches the search string against the description field as well as the package name.  **Take caution** as the descriptions are also matched as regular expressions. **--sync**   Initiates a portage tree update with one of the rsync.gentoo.org mirrors.  **Note that any changes you have made to the portage tree will be erased**.  Except for special circumstances, this uses **rsync** to do the update.  See **[make.conf]("http://gentoo-wiki.com/MAN_make.conf_5")**(5)'s description of PORTDIR_OVERLAY for a method to avoid deletions. **--unmerge **(**-C**)   **WARNING: This action can remove important packages!** Removes all matching packages. This does no checking of dependencies, so it may remove packages necessary for the proper operation of your system. Its arguments can be *ebuilds*, *sets*, or *dependencies* -- see **--clean** above for examples. **--update **(**-u**)   Updates packages to the best version available, which may not always be the highest version number due to masking for testing and development. This will also update direct dependencies which may not be what you want. In general, use this option only in combination with the world or system target. **--version **(**-V**)   Displays the version number of **emerge**.    **OPTIONS**

  **--alphabetical **   When displaying USE and other flag output, combines the enabled and disabled lists into one list and sorts the whole list alphabetically. **--ask **(**-a**)   Before performing the merge, display what ebuilds and tbz2s will be installed, in the same format as when using **--pretend**; then ask whether to continue with the merge or abort.  Using **--ask** is more efficient than using **--pretend** and then executing the same command without **--pretend**, as dependencies will only need to be calculated once. **WARNING: If the "Enter" key is pressed at the prompt (with no other input), it is interpreted as acceptance of the first choice. Note that the input buffer is not cleared prior to the prompt, so an accidental press of the "Enter" key at any time prior to the prompt will be interpreted as a choice!** **--buildpkg **(**-b**)   Tells emerge to build binary packages for all ebuilds processed in addition to actually merging the packages. Useful for maintainers or if you administrate multiple Gentoo Linux systems (build once, emerge tbz2s everywhere). The package will be created in the *${PKGDIR}/All* directory.  An alternative for already-merged packages is to use **quickpkg** which creates a tbz2 from the live filesystem. **--buildpkgonly **(**-B**)   Creates binary packages for all ebuilds processed without actually merging the packages. This comes with the caveat that all build-time dependencies must already be emerged on the system. **--changelog **(**-l**)   Use this in conjunction with the **--pretend** option.  This will show the ChangeLog entries for all the packages that will be upgraded. **--columns**   Used alongside **--pretend** to cause the package name, new version, and old version to be displayed in an aligned format for easy cut-n-paste. **--debug **(**-d**)   Tells emerge to run the emerge command in **--debug** mode. In this mode the bash build environment will run with the -x option, causing it to output verbose debugging information to stdout. **--debug** is great for finding bash syntax errors. **--deep **(**-D**)   When used in conjunction with **--update**, this flag forces **emerge** to consider the entire dependency tree of packages, instead of checking only the immediate dependencies of the packages. As an example, this catches updates in libraries that are not directly listed in the dependencies of a package. **--emptytree **(**-e**)   Reinstalls all world packages and their dependencies to the current USE specifications while differing from the installed set of packages as little as possible. You should run with **--pretend** first to make sure the result is what you expect. **--fetchonly **(**-f**)   Instead of doing any package building, just perform fetches for all packages (the main package as well as all dependencies). **--fetch-all-uri **(**-F**)   Instead of doing any package building, just perform fetches for all packages (the main package as well as all dependencies), grabbing all potential files. **--getbinpkg **(**-g**)   Using the server and location defined in *PORTAGE_BINHOST* (see **[make.conf]("http://gentoo-wiki.com/MAN_make.conf_5")**(5)), portage will download the information from each binary package found and it will use that information to help build the dependency list. This option implies **-k**.  (Use **-gK** for binary-only merging.) **--getbinpkgonly **(**-G**)   This option is identical to **-g**, as above, except it will not use ANY information from the local machine. All binaries will be downloaded from the remote server without consulting packages existing in the local packages directory. **--ignore-default-opts**   Causes *EMERGE_DEFAULT_OPTS* (see **[make.conf]("http://gentoo-wiki.com/MAN_make.conf_5")**(5)) to be ignored. **--newuse **(**-N**)   Tells emerge to include installed packages where USE flags have changed since compilation. An asterisk marks when a USE flag has changed since the package was compiled. **--nocolor **   Suppresses all coloring of portage's output. **--noconfmem**   Causes portage to disregard merge records indicating that a config file inside of a **CONFIG_PROTECT** directory has been merged already. Portage will normally merge those files only once to prevent the user from dealing with the same config multiple times. This flag will cause the file to always be merged. **--nodeps **(**-O**)   Merges specified packages without merging any dependencies. Note that the build may fail if the dependencies aren't satisfied. **--noreplace **(**-n**)   Skips the packages specified on the command-line that have already been installed. Without this option, any packages, ebuilds, or deps you specify on the command-line *will* cause Portage to remerge the package, even if it is already installed. Note that Portage will not remerge dependencies by default. **--nospinner**   Disables the spinner for the session. The spinner is active when the terminal device is determined to be a TTY. This flag disables it regardless. **--oneshot **(**-1**)   Emerge as normal, but do not add the packages to the world profile for later updating. **--onlydeps **(**-o**)   Only merge (or pretend to merge) the dependencies of the packages specified, not the packages themselves. **--pretend **(**-p**)   Instead of actually performing the merge, simply display what *would* have been installed if **--pretend** weren't used.  Using **--pretend** is strongly recommended before installing an unfamiliar package.  In the printout: 
  
  
  *N* = new (not yet installed) 
  *S* = new SLOT installation (side-by-side versions) 
  *U* = updating (to another version) 
  *D* = downgrading (best version seems lower) 
  *R* = replacing (remerging same version)) 
  *F* = fetch restricted (must be manually downloaded) 
  *f* = fetch restricted (already downloaded) 
  *B* = blocked by an already installed package **--quiet **(**-q**)   Results may vary, but the general outcome is a reduced or condensed output from portage's displays. **--skipfirst**   This option is only valid when used with **--resume**. It removes the first package in the resume list so that a merge may continue in the presence of an uncorrectable or inconsequential error. This should only be used in cases where skipping the package will not result in failed dependencies. **--tree **(**-t**)   Shows the dependency tree for the given target by indenting dependencies. This is only really useful in combination with **--emptytree** or **--update** and **--deep**. **--usepkg **(**-k**)   Tells emerge to use binary packages (from $PKGDIR) if they are available, thus possibly avoiding some time-consuming compiles. This option is useful for CD installs; you can export PKGDIR=/mnt/cdrom/packages and then use this option to have emerge "pull" binary packages from the CD in order to satisfy dependencies. **--usepkgonly **(**-K**)   Tells emerge to only use binary packages (from $PKGDIR). All the binary packages must be available at the time of dependency calculation or emerge will simply abort. Portage does not use $PORTDIR when calculating dependency information so all masking information is ignored. **--verbose **(**-v**)   Tell emerge to run in verbose mode. Currently this flag causes emerge to print out GNU info errors, if any, and to show the USE flags that will be used for each package when pretending.    **ENVIRONMENT OPTIONS**

  **ROOT** = *[path]* Use **ROOT** to specify the target root filesystem to be used for merging packages or ebuilds. 
  Defaults to /. **PORTAGE_CONFIGROOT** = *[path]* Use **PORTAGE_CONFIGROOT** to specify the location for various portage configuration files (see **FILES** for a detailed list). 
  Defaults to /.    **OUTPUT**

  When utilizing **emerge** with the **--pretend** and **--verbose** flags, the output may be a little hard to understand at first.  This section explains the abbreviations. **[blocks B     ] app-text/dos2unix (from pkg app-text/hd2u-0.8.0)**   Dos2unix is Blocking hd2u from being emerged. Blockers are defined when two packages will clobber each others files, or otherwise cause some form of breakage in your system. However, blockers usually do not need to be simultaneously emerged because they usually provide the same functionality. **[ebuild  N    ] app-games/qstat-25c**   Qstat is New to your system, and will be emerged for the first time. **[ebuild  NS   ] dev-libs/glib-2.4.7**   You already have a version of glib installed, but a 'new' version in a different SLOT is available. **[ebuild   R   ] sys-apps/sed-4.0.5**   Sed 4.0.5 has already been emerged, but if you run the command, then portage will Re-emerge the specified package (sed in this case). **[ebuild    F  ] media-video/realplayer-8-r6**   The realplayer package requires that you Fetch the sources manually. When you attempt to emerge the package, if the sources are not found, then portage will halt and you will be provided with instructions on how to download the required files. **[ebuild    f  ] media-video/realplayer-8-r6**   The realplayer package's files are already downloaded. **[ebuild     U ] net-fs/samba-2.2.8_pre1 [2.2.7a]**   Samba 2.2.7a has already been emerged and can be Updated to version 2.2.8_pre1. **[ebuild     UD] media-libs/libgd-1.8.4 [2.0.11]**   Libgd 2.0.11 is already emerged, but if you run the command, then portage will Downgrade to version 1.8.4 for you. 
This may occur if a newer version of a package has been masked because it is broken or it creates a security risk on your system and a fix has not been released yet. 
 Another reason this may occur is if a package you are trying to emerge requires an older version of a package in order to emerge successfully. In this case, libgd 2.x is incompatible with libgd 1.x. This means that packages that were created with libgd 1.x will not compile with 2.x and must downgrade libgd first before they can emerge. **[ebuild     U ] sys-devel/distcc-2.16 [2.13-r1] USE=ipv6* -gtk -qt%**   Here we see that the make.conf variable **USE** affects how this package is built. In this example, ipv6 optional support is enabled and both gtk and qt support are disabled. The asterisk following ipv6 indicates that ipv6 support was disabled the last time this packages was installed. The percent sign following qt indicates that the qt option has been added to the package since it was last installed. 
  ***Note:** Flags that haven't changed since the last install are only displayed when you use the **--pretend** and **--verbose** options. Using the **--quiet** option will prevent all information from being displayed.[http://gentoo-wiki.com/MAN_emerge_1](http://gentoo-wiki.com/MAN_emerge_1)

---

### Post by RAV TUX on 2006-11-26
keep in mind that there are other benefits that would come from a Gentoo based Ubuntu.

beyond simply using Emerge.

I would like to discover all of those benefits,...

---

### Post by rattlerviper on 2006-11-26
Are you just looking to create a easier and Debian based Gentoo?  I've read through the thread and I'm still not sure. Or are you wishing to create a self compiled Ubuntu like distro that has emerge and synaptic?  Who is the perspective user base?  That's a very important question to answer before attempting to decide how to build, unless your perspective user base is yourself and perhaps a few friends.

---

### Post by RAV TUX on 2006-11-26
> **rattlerviper said:**
> Are you just looking to create a easier and Debian based Gentoo?  I've read through the thread and I'm still not sure. Or are you wishing to create a self compiled Ubuntu like distro that has emerge and synaptic?  Who is the perspective user base?  That's a very important question to answer before attempting to decide how to build, unless your perspective user base is yourself and perhaps a few friends.

The concept simply is a Gentoo based Ubuntu. (Not much unlike a Debian based Ubuntu, simply a different core foundation)

Which utilizes Emerge and possibly deb files, in theory but nothing is difinite. 

The perspective user base is anyone who shows interest in such a build, This perspective user base has already been established by those who have posted interest here. Of which we have been making plans, of course this will not happen instaneous so don't expect immediate results overnight in this thread.

For such a new concept this has shown more interest then not. I expect the nay sayers will come but perhaps not.

Ubentoo Box (Ubuntu/Gentoo hybrid)

No need to pigeon hole a user base for something that has not yet been built. Yet I envision a Sabayon-like version of Ubuntu but it could be more pure Gentoo based for advanced Linux users or it could be both. 

We are only speaking in conceptual terms here so there are no definitives or absolutes...

The beauty of a symbiotic idea like this is that it can be altered as needed.

I have put in a request for a Incubator forum or Sandbox Forum here at UbuntuForums for just such ideas,....ideas too new for a third party forum but that can develope into a third party development with nurturing...

This concept of an Ubuntu Incubator could help grow concepts like this into viable working modules that the whole community could benefit from, from the developers to the end users,....a Ubuntu developers community based Think Tank if you will.

This is a concept that would help the Ubuntu community as a whole, and could be a working model for other communities to replicate.

There could be such models already in place elsewhere and that would be great to show that it is a viable idea that can work.

---

### Post by rattlerviper on 2006-11-26
By user base I simply meant what level of experience do you think the average user would need for the concept that you have?  Then build to that rather than just build and see who it is aimed at.  Naysayers will indeed come as with every project, but who cares?  Clearly they are just disinterested parties rather than anyone with a valid input.  Honestly I was just attempting to figure out whether this was to be a attempt to make a easy Gentoo or to make a complicated Ubuntu (both have good possibilities).  

As for a developmental community here I have no feelings about that either way, as I am sure there would be positives and negatives associated with it.

---

### Post by RAV TUX on 2006-11-26
> **rattlerviper said:**
> By user base I simply meant what level of experience do you think the average user would need for the concept that you have?  Then build to that rather than just build and see who it is aimed at.  Naysayers will indeed come as with every project, but who cares?  Clearly they are just disinterested parties rather than anyone with a valid input.  Honestly I was just attempting to figure out whether this was to be a attempt to make a easy Gentoo or to make a complicated Ubuntu (both have good possibilities).  

As for a developmental community here I have no feelings about that either way, as I am sure there would be positives and negatives associated with it.
  ahhh...I see it would be geared towards intermediate to advanced Linux users,...not just Ubuntu users....It would be an excellent way to attract non-Debian based developers to the Ubuntu fold.

---

### Post by rattlerviper on 2006-11-26
> **RAV TUX said:**
> ahhh...I see it would be geared towards intermediate to advanced Linux users,...not just Ubuntu users....It would be an excellent way to attract non-Debian based developers to the Ubuntu fold.
Then a excellent idea!  I was hoping that it would not be geared toward beginning users.  Linux for new people seems to be the most common distros around now. Not that that's a bad thing(it's good in some circumstances where it should just work), but I find myself really wanting a intermediate distro that needs some work done to it!  Not sure if you understand what I mean...A distro that requires something of it's users, and returns more to those willing to invest the time and knowledge.

---

### Post by RAV TUX on 2006-11-26
> **rattlerviper said:**
> Then a excellent idea!  I was hoping that it would not be geared toward beginning users.  Linux for new people seems to be the most common distros around now. Not that that's a bad thing(it's good in some circumstances where it should just work), but I find myself really wanting a intermediate distro that needs some work done to it!  Not sure if you understand what I mean...A distro that requires something of it's users, and returns more to those willing to invest the time and knowledge.

Exactly once your skill level moves beyond the beginning Linux mode, people tend to get bored and want something more challenging and more customizable...otherwise we would have stuck with Apple or Windows.

Too many Linux Distros are geared towards the Beginner and ignore that every beginner progresses beyond this stage to the intermediate and the advanced level. There should be something here at Ubuntu to keep all users interested at all levels.

Gentoo has always been seen as the "Creme de la Creme" for advanced Linux users...even intermediate users looking to be challenged...

There is no reason that we can't focus on this as a users base and build:

Ubentoo Box

with that said there is no reason there should not be an Easy  Gentoo based version also like SabayonLinux....

Ubayon ? Sabuntu ?

Who knows....but I have laid out the concept and put the idea out in the universe, Wether I  help or not I would love to see it in action.

---

### Post by rattlerviper on 2006-11-26
I agree 100%.  Sometimes I think the whole reason I distro test is out of boredom with using 1 distro all the time that requires little of the user.  Sometimes I want something that just works...but other times I really want to get my hands dirty.  Not necessarily filthy, but dirty.
At least I now know I am not the only person who feels this way.

---

### Post by RAV TUX on 2006-11-26
> **rattlerviper said:**
> I agree 100%.  Sometimes I think the whole reason I distro test is out of boredom with using 1 distro all the time that requires little of the user.  Sometimes I want something that just works...but other times I really want to get my hands dirty.  Not necessarily filthy, but dirty.
At least I now know I am not the only person who feels this way.

Don't get wrong rattlerviper...I feel that a distro as a base line should always "just work".

If I get under the hood of a distro it should only be my chioce not because I am forced to

But there is no need for Ubuntu to be harnessed to Debian,...not that there any thing wrong with Debian. I just feel that if different versions of Ubuntu are to be offered why just limit it to the desktop used (Gnome/KDE/XFCE/Fluxbox/etc)...why not base it on other OS's not even just different Linux OS's.

One way to unite Linux developers is to unite them under Ubuntu....

If we could say attract one or two first class Gentoo developers to work on the Ubentoo Box project it would make the effort worth while.

But it would have to "Just Work" as a baseline but be more fully customizable as Gentoo is.

---

### Post by rattlerviper on 2006-11-26
> **RAV TUX said:**
> Don't get wrong rattlerviper...I feel that a distro as a base line should always "just work".

If I get under the hood of a distro it should only be my chioce not because I am forced to

But there is no need for Ubuntu to be harnessed to Debian,...not that there any thing wrong with Debian. I just feel that if different versions of Ubuntu are to be offered why just limit it to the desktop used (Gnome/KDE/XFCE/Fluxbox/etc)...why not base it on other OS's not even just different Linux OS's.

One way to unite Linux developers is to unite them under Ubuntu....

If we could say attract one or two first class Gentoo developers to work on the Ubentoo Box project it would make the effort worth while.

But it would have to "Just Work" as a baseline but be more fully customizable as Gentoo is.

There comes the problem ;) getting something to just work and have it as customizable as Gentoo or Arch.  Honestly I don't even care if a distro has a livecd or not when I am looking for a distro.  So often distros seem to run differently when installed than when run live.  Sometimes the installer really sucks and ruins what could be a really good experience.

---

### Post by RAV TUX on 2006-11-26
> **rattlerviper said:**
> There comes the problem ;) getting something to just work and have it as customizable as Gentoo or Arch.  Honestly I don't even care if a distro has a livecd or not when I am looking for a distro.  So often distros seem to run differently when installed than when run live.  Sometimes the installer really sucks and ruins what could be a really good experience.
  Here we can agree I often look for install DVD's over LiveCD's. 

I think getting Gentoo to just work is completely reliant upon the user and not the software...

Thus the research and foreknowledge will determine the amount of success....If Gentoo had the same great user community found here at UbuntuForums more new users would have much more success...

Thus the key to Ubuntu's success is revealed...the key is UbuntuForums.

---

### Post by rattlerviper on 2006-11-26
> **RAV TUX said:**
> Here we can agree I often look for install DVD's over LiveCD's. 

I think getting Gentoo to just work is completely reliant upon the user and not the software...

Thus the research and foreknowledge will determine the amount of success....If Gentoo had the same great user community found here at UbuntuForums more new users would have much more success...

Thus the key to Ubuntu's success is revealed...the key is UbuntuForums.
99% true...Ubuntu has also done one heck of a good job developing the distro in a short amount of time and spreading the word.  But without the forums Ubuntu would certainly be no where near as popular.
I agree that Gentoo is complety reliant (or nearly so) on the user doing the install and not the software.  Gentoo can be a real bear to install if someone comes along (like I did once) downloads the iso and proceeds to try to install without any research.  I had no idea what I was in for, with some research it  turns out to be doable...I still won't call it easy;) ...and a great deal of fun.
One thing that really upsets me is when installing a livecd...half way through the install...you find out you can not repartition your hard drive without starting over because they failed to include a partitioner on the live cd.  It upsets me even more if they include a partitioner during the install that doesn't work and tells you that you need to reboot for the changes to take effect and upon reboot you are still faced with your original partitions.  I usually attempt to use the partitioner of the distro I am testing since presumably that is how many people will repartition their drives when installing.

---

### Post by adam.tropics on 2006-11-26
Interesting, deja vu here! Have a read through [this one....]("http://www.ubuntuforums.org/showthread.php?t=208595&highlight=genbuntoo")it kind of died I think, from over complicating itself, but it is a neat idea.

---

### Post by RAV TUX on 2006-11-26
> **adam.tropics said:**
> Interesting, deja vu here! Have a read through [this one....]("http://www.ubuntuforums.org/showthread.php?t=208595&highlight=genbuntoo")it kind of died I think, from over complicating itself, but it is a neat idea.

WOW...thinks for the link that is a bit complicated...reminds me of one of those inventions where a ball rolls though everything and with the help of a thousand mice on wheels a guy flips his egg or something like that.

Simplicity is obviously Key here...so I think the focus should always be simplicity....like with Sabayon where everything under the sun already works...

The simple goal should be kept then

Ubentoo Box should be an easy Gentoo much like SabayonLinux...the difference is that both Emerge and deb files could be used...Emerge and the Synaptic Package Manager would be enabled and the end user could choose to use one or the other or both(but not sure this is possibly)

Thanks for the link...

Honestly Gentoo is one of the most beautiful distros I have seen or used I commend the Sabayon Devs on a job well done on simplifing it for the not-so-technically enhanced user....

I still think a Gentoo based Ubuntu would be great, a wonderful alternative flavor of Ubuntu...

Ubentoo Box

---

### Post by drummer4lifex on 2006-12-10
Okay, first of all, I would like to start off saying that I'm a relatively new Linux user (<1 year experience), however I've learned A LOT in the past year about Linux. I've tried MANY distros, mainly for two reasons, 1) I had NO idea how to troubleshoot hardware when I first started, and 2) I was trying to find something fast enough to run on my OLD 600 MHz Coppermine Laptop.

Well, things have changed, and I've been a long-time Ubuntu user, with my few escapades on Gentoo, or Gentoo-based Linux. After spending this weekend trying to troubleshoot portage, I think I have a decently knowledgeable position on this concept.

In my opinion, creating an Ubuntu with portage is basically cloning Sabayon, which I'm not against, but I don't see it as that creative. I understand that people would like to combine dpkg & apt-get with portage, which I'm also not opposed to, I think it's a good idea, but it will require a lot of work... And it might just be easier expanding on apt-build (which you can optimize towards microarchitecture, just not USE Flags, etc).

Here's my idea--

It's both very possible to optimize by compiling on your own system (using portage), and it's very fast and efficient to install through apt-get, why not something in between? I don't think combining portage and apt-get dpkg is the answer.

I think it would be interesting to release precompiled "flavors" of Ubuntu (Or Debian) that are made according to one's marchitecture. I'm not just talking apps, I'm talking the whole Desktop Environment... The whole thing (Even optimizations in the  Kernel) on each of their own CD (i.e. Ubuntu-P3M for Pentium 3-M, Ubuntu-AXP for Athlon XP's). But that's just the start--

Each architecture would have it's own repositories with binaries specifically compiled to that marchitechture so ALL of the packages are optimized for the system (at least the most significant optimizations) and the speed is that of installing a binary package.

Think Swiftfox, but across the entire board! 

What do you think of that? 

*Also I wanted to add, if you think about it, the total compile time of all development would ultimately be much less than that of the users, especially if we use a beefy workstation*

DISCLAIMER: I have no idea if this post makes sense or not, but I've been up all night trying to study for my finals - so please ask questions if I was unclear at any point. Also, please disregard any grammatical or stylistic errors :mrgreen:

---

### Post by mips on 2006-12-10
> **RAV TUX said:**
> using Emerge with Ubuntu would be reason enough, but honestly it is just an idea.

I would say you need a proper broadband connection for emerge. I do not have the time to sit and wait for things :(

---

### Post by drummer4lifex on 2006-12-10
If you employ ccache your internet usage becomes more efficient... most of the time you're waiting is for the system to compile the package.

---

### Post by RAV TUX on 2006-12-10
> **mips said:**
> I would say you need a proper broadband connection for emerge. I do not have the time to sit and wait for things :(
I have found emerge is faster and more efficient then Synaptic Package manager or apt-get.

---

### Post by RAV TUX on 2006-12-10
Perhaps this is not such a good idea overall?

---

### Post by mips on 2006-12-10
> **RAV TUX said:**
> I have found emerge is faster and more efficient then Synaptic Package manager or apt-get.

The last time I tried to do a emerge sync it took ages, so long in fact that i canceled it. And just for the record I tried a few times on different days.

---

### Post by RAV TUX on 2006-12-10
> **mips said:**
> The last time I tried to do a emerge sync it took ages, so long in fact that i canceled it. And just for the record I tried a few times on different days.

the time depends on the ebuild what were you trying to emerge?

---

### Post by mikerduffy on 2006-12-11
What about focusing on Gentoo, as an intermediate-advanced (fun) distro, and integrating access to .debs and to the Debian/Ubuntu repositories?  This would give you the best of both worlds, since (IMO) access to packages is the real meat that a hybrid *buntu would provide.  As was said before, if you want something that's just easy to use, *buntu and Saboyan are already doing that.

Still, Ubuntu and Gentoo are rich enough that there's more than one way to go...

---

### Post by yabbadabbadont on 2006-12-11
If you talk with long time users of Gentoo (like myself), you will find that most of us will tell you that the optimization is pretty much a trivial side effect of building the system from source.  The thing that most of us liked about Gentoo, was the ability to decide which optional features a package should have when installed on our systems.  My pet peeve with binary based distributions is that I don't like packages that pull in a dozen others just to provide support for hardware that doesn't exist on my system.  In Gentoo, I would configure the USE flags and a few other settings in make.conf and only the bare minimum of software would be pulled in.  I realize that there isn't any way for me to easily have that kind of configurability in a binary package based system.  (at least not when you only get binaries from trusted sources)  If you can work out a way to have several alternate versions of each binary package, each one with a different combination of optional features, and manage to have a package manager that can keep the system in a stable state, then I would be all for it.  However, that would be a logistical nightmare, to say the least.  (which pretty much describes maintaining the current Gentoo portage tree...)

---

### Post by drummer4lifex on 2006-12-11
But short of being a control freak, what do USE Flags ultimately accomplish? Performance optimizations. There is no way to avoid the dependencies and support for all hardware with out installing it by default, obviously - but moreover, sometimes I feel that some binary packages are just generally poorly compiled (desklets, for instance). It is possible to install portage on  other distros,  although I have no idea how effective or how well it works.  apt-build is very similar, yet cleaner than a dual build of portage and apt-get/dpkg - yet you cannot use USE Flags (but you can use CFlags). Why not just continue the development of that? I've already installed it and it seems to work well, but right now I'm doing an apt-build-world so I will see how well things work after that. Now that I think of it, there probably was no reason to do it, but other than just to do it. The place where I see apt-build being very effective is rebuilding slow or poorly compiled binaries such as superkaramba, and maybe OpenOffice. But then leave everything else that is working fine alone... Although, integrating portage, apt-build, and apt-get/dpkg does sound more-doable. I honestly think that a few years in the future, it will be integrated into one package management system.

In response to the march-specific builds, I disagree that it would be a logistical nightmare. Just imagine repositories multiplied by 12 or something compiled march-specific. The only issue would be assigning the right repository to the right system (which with 12 different CDs wouldn't be an issue if they were default). It's not a nightmare, just a lot of work, but would it be worth it? I think so. It wouldn't be all that hard either.

---

### Post by avc302000 on 2006-12-11
Hi!
I think that in terms of a hybrid Ubuntu/Gentoo, besides the optimization provided by emerge, the install of the OS is a fundamental thing to users, such as me, who are newbies.
I've once tried Gentoo because i've read in foruns that installation of ndiswrapper (i have a broadcom wifi) was simply and in most cases works as a charm.
As a newbie I was unable to complete the instalation process because of the complexity of gentoo at the time (2004).](*,) 
I've switched to Ubuntu at that time and the ease of use was the victory key against Gentoo.
For me Ubuntu rules and as a newbie I am, i try to install  everything through command-line and read a lot to se if I can aspire to be a more reliable linux user.

That is my opinion, and I think that a "fusion" between Ubuntu/Gentoo technologies are great!

Best regards

---

### Post by technodigifreak on 2006-12-12
Now, before everyone reads my comments, please understand that this is honest questioning.  I really like the idea of melding FLOSS projects and 'Nix distros, but there are some times when a fork should stay forked.

> **shining said:**
> I'm curious to learn the reasons behind your project idea, besides the "Because we can."

Not to steal the fire of this thread, but that seems to be the jist of it.

> **zgornel said:**
> I'd just settle for a synaptic with a 'compile and optimize from source' option :D

Excellent idea! I completely agree.

> **RAV TUX said:**
> XubunPUP (Xubuntu/Puppy hybrid)

There may be some merit to that one, and it should be a much more simple blending.  Ubuntu Core would be more difficult, but more inline with a corporation's needs.  We (the FLOSS community) have to consider the needs of the business world.  There are plenty of "intermediate" and advanced distro's out there, few are simple enough that "Sally, the Administrative Assistant" could use.

<sarcasm>Maybe an Ubuntu from Scratch?  (You'd be compiling for 3 weeks, well, ok, maybe 6 months)</sarcasm>

> **rattlerviper said:**
> ...but I find myself really wanting a intermediate distro that needs some work done to it!  Not sure if you understand what I mean...A distro that requires something of it's users, and returns more to those willing to invest the time and knowledge.

Linux from Scratch.  Learn the structure and then you can contribute to any Linux distro.  The real innovation on linux systems is on the minimal install side and on the desktop side.  It's the middle ground that's being left behind.  That's because custom compiled systems work great on embedded and low overhead systems.  But it is just not practical to have to hand compile every package in a modern desktop.  Compiling a full desktop with all of the modern productivity software on it would take an inordinate amount of time.  If you want to compile it yourself, then you can, the sources are out there. There is no way I'm going make a user wait weeks when I can use a different system and have them up and running in a matter of minutes.  *This is Ubuntu's strength, quick setup with reasonable defaults.  Help build on this strength by integrating simple tools that anyone can use (but have very advanced features tucked away for the power users).*

---

### Post by jonqrandom on 2006-12-13
just found this thread, i'm installing ubuntu for a friend at the moment, used to use it myself for a good year or so before switching to gentoo a couple of months ago.  anyway, there's a few points i'd like to chuck into the mix:

gentoo's "steep learning curve"... as far as i can tell, that's code for "you have to type stuff".  well, yeah, but if you read the install guide it tells you pretty much *exactly* what to type, and more importantly *why*.  so it slowly but surely builds your understanding of the system you're building, right from the get-go.  it's not suitable for absolute noobs, sure, but once you've got some friendly linux experience under your belt, it's not that hard.

a version of ubuntu based on portage... sure. no probs (just some time). create an ebuild depending on all the ebuilds that install the ubuntu core software (and a graphical front-end to emerge/portage - see below).  once you have your gentoo base system going, then bang out "emerge ubuntu".  of course, you'd have to enjoy editing ebuilds, really ;)

a version of ubuntu that you compile yourself... uhhh - beg the [synaptic]("http://www.nongnu.org/synaptic/") coders to support apt-build?  course, you could use it yourself, from the command line, but then, well... wouldn't it be more like gentoo? ;-p

the "gentoo speed advantage" myth/debate...  i have no idea.  my gentoo install is tons faster than my ubuntu install was, but then i use [evilwm]("http://www.6809.org.uk/evilwm/") instead of gnome, so it's /going/ to be loads quicker :)  as a poster pointed out earlier, the funky thing about compiling for yourself is being able to throw dependencies and features in and out of the mix, to get software that does exactly what you want it to.

-emerge/portage guis:
[portagemaster]("http://portagemaster.sourceforge.net/")
[kentoo]("http://www.ralfhoelzer.com/kentoo.html")
[porthole]("http://porthole.sourceforge.net/")
[kuroo]("http://kuroo.org/")

---

### Post by mips on 2006-12-13
> **jonqrandom said:**
> 

gentoo's "steep learning curve"... as far as i can tell, that's code for "you have to type stuff".  

Something like Sabayon makes it easier to get into Gentoo.

---

### Post by maddog39 on 2006-12-24
I love this idea! I was thinking of something similar myself. It would be wicked sick to be able to compile ubuntu from source. It would be soo freakin' fast!

---

### Post by RAV TUX on 2006-12-24
> **mips said:**
> Something like Sabayon makes it easier to get into Gentoo.

This is more what I was thinking of, the ease and sophistication of Sabayon...

then incorporate this idea:

> **jonqrandom said:**
> 
a version of ubuntu based on portage... sure. no probs (just some time). create an ebuild depending on all the ebuilds that install the ubuntu core software (and a graphical front-end to emerge/portage - see below). once you have your gentoo base system going, then bang out "emerge ubuntu". of course, you'd have to enjoy editing ebuilds, really ;)



A Portage based Ubuntu that you could easily "emerge ubuntu" either in Sabayon or Gentoo...

So we could all the benefits of using Ubuntu on Sabayon/Gentoo.

perhaps a way to unite Sabayon/Gentoo & Ubuntu/Debian developers and end users.

---

### Post by RAV TUX on 2007-01-20
> **maddog39 said:**
> I love this idea! I was thinking of something similar myself. It would be wicked sick to be able to compile ubuntu from source. It would be soo freakin' fast!I am glad someone can appreciate a good idea :guitar:

---

### Post by runningwithscissors on 2007-01-20
It isn't difficult at all to make a Gentoo/Ubuntu hybrid.

Just start with a Gentoo install (no, it doesn't have to be all compiled from source), install GNOME, tweak fonts and other stuff,  add the brown Ubuntu theme and slap random Ubuntu logos everywhere.

The init system may be the only major difference after that, which can be replaced of course.

---

### Post by maddog39 on 2007-01-22
Well that seams a bit sloppy and a rather bad way to go about it. Another problem would be apt, how to get that on there. Also a thing about ubuntu is ease of use, and currently Gentoo can only be installed by 'computer nerds'. I even find their installation system a bit cryptic sometimes and I compile things from source all the time and I develop software in linux, etc. and use it everyday.

---

### Post by runningwithscissors on 2007-01-23
> **maddog39 said:**
> Well that seams a bit sloppy and a rather bad way to go about it. Another problem would be apt, how to get that on there.
Not really. A consistent GNOME theme from bootsplash to the desktop would do the trick. 

Also, apt is more Debian than Ubuntu. 
If you want something faster than Portage, there is a capable option, with a few additional features, even. But it is somewhat newbie-unfriendly and is officially unsupported.
```

# emerge --search paludis

*  sys-apps/paludis [ Masked ]
      Latest version available: 0.14.3
      Latest version installed: [ Not Installed ]
      Size of files: 1,225 kB
      Homepage:      http://paludis.pioto.org/
      Description:   paludis, the other package mangler
      License:       GPL-2

```
:wink:

> Also a thing about ubuntu is ease of use, and currently Gentoo can only be installed by 'computer nerds'.
It is not easy to use by default because it is minimalistic.
It can't make too many choices for you because that is it's selling point. It gives you the opportunity to make the choices.
One of the choices is, that you can turn it into a kind of Ubuntu, if you like :wink:

If you want hardware detection to include extensive support for all kinds of devices, you can simply compile your kernel with Ubuntu's kernel config.

I am not sure there are too many other things that Ubuntu does that makes it friendlier. (Yes, this is not a flame attacking Ubuntu's user-friendliness, but a defence against the sentiment that Gentoo is difficult to use).

> I even find their installation system a bit cryptic sometimes and I compile things from source all the time and I develop software in linux, etc. and use it everyday.
Portage is actually quite friendly. The options you can issue it with are surprisingly few. It cannot be made any simpler than, say,
# emerge <packagename>

---

### Post by runningwithscissors on 2007-01-23
Double post. Sorry.

---

### Post by Insomniac20k on 2007-01-23
We need to create an Ubuntu that will support RPMs as well as building from source too. How hard would it be to make apt-get install RPMs? Ubuntu should break away from debian's apt-get and work on it's own super installer that would support .deb, rpms, and building from source.

I can see integrating emerge into this and all, but what's the point of using the rest of Gentoo? Ubuntu works fine the way it is. All we want to change is the installer, right?

---

### Post by RAV TUX on 2007-01-23
> **Insomniac20k said:**
> We need to create an Ubuntu that will support RPMs as well as building from source too. How hard would it be to make apt-get install RPMs? Ubuntu should break away from debian's apt-get and work on it's own super installer that would support .deb, rpms, and building from source.

I can see integrating emerge into this and all, but what's the point of using the rest of Gentoo? Ubuntu works fine the way it is. All we want to change is the installer, right?

Ebuilds, and emerge would be nice in Ubuntu....I also would like to use pup-get....Puppy linux has enabled deb-files.....we should be able to use Pup-get also

---

### Post by dolny on 2007-01-23
I would love to see this concept becoming reality.

[i]Between ideas and reality,
Between conception and creation...[/i]

---

### Post by Sunnz on 2007-02-06
Maybe we can make something like portage-deb...

Which builds a deb file from sources...

Then uses aptitude to install it.

---

### Post by runningwithscissors on 2007-02-06
> **Sunnz said:**
> Maybe we can make something like portage-deb...

Which builds a deb file from sources...

Then uses aptitude to install it.

Heh.
If you're compiling from source, creating a deb package is pointless. Direct deployment of the binaries is the obvious choice. :)

---

### Post by usernamebob on 2007-02-06
> **runningwithscissors said:**
> Heh.
If you're compiling from source, creating a deb package is pointless. Direct deployment of the binaries is the obvious choice. :)

not realy.. you'd have the advatage of it intergrating better with the current packaging system.. if you could do it with use flags it'd be nice.

personaly I just want a gentoo stable branch.. would be great for servers. Course I could just use bsd.. but then there'd be a learning curve :p

---

### Post by runningwithscissors on 2007-02-06
> **usernamebob said:**
> not realy.. you'd have the advatage of it intergrating better with the current packaging system.. if you could do it with use flags it'd be nice.
The USE flags only matter during compilation. After you've compiled the source, it certainly makes more sense to copy the binaries directly to their respective locations rather than stuffing them into an archive and then unpacking them again immediately for deployment. ;)

> **usernamebob said:**
> personaly I just want a gentoo stable branch.. would be great for servers. Course I could just use bsd.. but then there'd be a learning curve :p
They're a bit shorthanded on the development team. Maintenance of a seperate stable branch would be difficult. I don't see why the keyword system can't serve as a distinction between stable and testing packages.

---

### Post by Sunnz on 2007-02-06
I can think of a few advantage of portage-deb.

You have one database of installed software.

If portage and apt co-exists it means they can for example both install firefox, possibly overwrite each other. Then if you unmerge it apt still has firefox in its database.

There could be a way to integrate both database together, but consider the sheer size of the databases, it would be far easier to just use one database.

It would be cumbersome having to emerge -s gnat && aptitude show gnat just to find out which has installed with what and where.

Building deb with portage also means you can distribute them over your own network or some distcc things.

EDIT: unless you tell me there is a way to deploy binaries in portage such that it adds an entry in apt-get which then knows how to uninstall/unmerge it.

---

### Post by LSparky on 2007-02-22
Ok, Now this idea that you people have that emerge and the gentoo package management system should be integrated with ubuntu is never gonna happen, now that Ubuntu has merged with Linspire to implement CNR and Linspires package management system into Ubuntu. I am also one to believe that emerge should be added to Ubuntu, but i honestly believe it will never happen now that Ubuntu is modifying there package system for Linspire.

---

### Post by igknighted on 2007-02-22
From an installation perspective, I think that this is where Ubuntu can really put its fingerprint on a Gentoo based system.  What if the installer could (in a graphical setting):
1) Allow you to plan out the system in a comfortable setting beforehand
2) recommend compiler flags
3) map your devices and perhaps build your fstab and other config files for you (letting you view to approve of course)
4) Selecting packages beyond the base install to compile (ie X-server, DE of choice, apps, etc)
5) After collecting all this information, you can walk away and let it compile merrily away

I think this is the idea behind the Gentoo live installer, but I don't really trust the Gentoo devs to really see this through to completion, and it's a perfect spot for Ubuntu to make "Gentoo for Humans".  Ubuntu could even add their source repo's as an overlay, perhaps allowing Ubuntu art to be the default.  Heck, if you used the source repo's as the main source for portage then it would save any worries about breakages via updates, and you could keep up with security updates much more safely (or stay cutting edge using Gentoo's files).  It would be an incredibly diverse system, able to go from custom compiled Ubuntu to pure Gentoo.  I think its very promising.  I don't have the coding ability to help, but any development releases sign me up!

---

### Post by FyreBrand on 2007-02-22
> **igknighted said:**
> From an installation perspective, I think that this is where Ubuntu can really put its fingerprint on a Gentoo based system.  What if the installer could (in a graphical setting):
1) Allow you to plan out the system in a comfortable setting beforehand
2) recommend compiler flags
3) map your devices and perhaps build your fstab and other config files for you (letting you view to approve of course)
4) Selecting packages beyond the base install to compile (ie X-server, DE of choice, apps, etc)
5) After collecting all this information, you can walk away and let it compile merrily away

I think this is the idea behind the Gentoo live installer, but I don't really trust the Gentoo devs to really see this through to completion, and it's a perfect spot for Ubuntu to make "Gentoo for Humans".  Ubuntu could even add their source repo's as an overlay, perhaps allowing Ubuntu art to be the default.  Heck, if you used the source repo's as the main source for portage then it would save any worries about breakages via updates, and you could keep up with security updates much more safely (or stay cutting edge using Gentoo's files).  It would be an incredibly diverse system, able to go from custom compiled Ubuntu to pure Gentoo.  I think its very promising.  I don't have the coding ability to help, but any development releases sign me up!I've been testing out Sabayon for a little bit now at home.  There are some really interesting possibilities there I think.  If there were a way to merge the functionality of dkpg and portage it would be great.  Apt at the command line with switches isn't so very different and to extend portage-like functionality would be powerful.

It would be so nice to choose what to compile and what to install as binaries while still having package management track versioning.  I like the stability Kubuntu has to offer, but the performance of Sabayon, even with multiple DE's and tons of apps installed, is quite remarkable.  There is a lot each community would have to offer each other if they could work together.

---

### Post by RAV TUX on 2007-04-07
this all still sounds interesting...how about an emerge/conary/deb hybrid system?

---

### Post by igknighted on 2007-04-07
> **RAV TUX said:**
> this all still sounds interesting...how about an emerge/conary/deb hybrid system?

It would be nice to have more binaries to suplement the source than Gentoo adds.  There are some apps that just aren't worth compiling.  If I had a choice, that would be tremendous.  But overall, I think such a distro should stay primarily source based.  We have lots of binary Ubuntus, so a source one would be a nice touch.

---

### Post by RAV TUX on 2007-04-07
> **igknighted said:**
> It would be nice to have more binaries to suplement the source than Gentoo adds.  There are some apps that just aren't worth compiling.  If I had a choice, that would be tremendous.  But overall, I think such a distro should stay primarily source based.  We have lots of binary Ubuntus, so a source one would be a nice touch.

It would be nice to port all debs and portages to conary

[img]http://skins.hotbar.com/skins/mailskins/em/google_emoticons/emoti_121.gif[/img]

---

### Post by igknighted on 2007-04-07
> **RAV TUX said:**
> It would be nice to port all debs and portages to conary

[img]http://skins.hotbar.com/skins/mailskins/em/google_emoticons/emoti_121.gif[/img]

I've gotta try to get into conary... I've heard so many great things, I just never took the time to see what its all about.  The whole web browser thing threw me off.  Is there a site I can read up on it?  Including command line commands for installing stuff?

---

### Post by RAV TUX on 2007-04-07
> **igknighted said:**
> I've gotta try to get into conary... I've heard so many great things, I just never took the time to see what its all about.  The whole web browser thing threw me off.  Is there a site I can read up on it?  Including command line commands for installing stuff?

[Conary:Install_or_Update_Software_HOWTO]("http://cafelinux.org/forum/index.php/topic,182.0.html")
[http://wiki.rpath.com/wiki/Conary:Install_or_Update_Software_HOWTO](http://wiki.rpath.com/wiki/Conary:Install_or_Update_Software_HOWTO)

[Conary:Packager]("http://cafelinux.org/forum/index.php/topic,180.0.html")
[http://wiki.rpath.com/wiki/Conary:Packager](http://wiki.rpath.com/wiki/Conary:Packager)

[Conary:conaryrc]("http://cafelinux.org/forum/index.php/topic,181.0.html")
[http://wiki.rpath.com/wiki/Conary:conaryrc](http://wiki.rpath.com/wiki/Conary:conaryrc)

[Conary:Concepts]("http://cafelinux.org/forum/index.php/topic,179.0.html")
[http://wiki.rpath.com/wiki/Conary:Concepts](http://wiki.rpath.com/wiki/Conary:Concepts)

[Conary:Recipe]("http://cafelinux.org/forum/index.php/topic,178.0.html")
[http://wiki.rpath.com/wiki/Conary:Recipe](http://wiki.rpath.com/wiki/Conary:Recipe)


also read up on:

[rPathApplianceAgent:Forums]("http://cafelinux.org/forum/index.php/topic,183.0.html")
[http://wiki.rpath.com/wiki/rPathApplianceAgent:Forums](http://wiki.rpath.com/wiki/rPathApplianceAgent:Forums)

....and you can test it all out in **[[COLOR=Purple]Oz[/COLOR]]("http://www.rpath.org/rbuilder/project/oz/")**

[IMG]http://skins.hotbar.com/skins/mailskins/em/google_emoticons/emoti_443.gif[/IMG]

---

### Post by %hMa@?b&lt;C on 2007-04-07
I personally feel that the two distros come from total opposites.  Ubuntu for total package management, gentoo for a totally compiled on your box, customized approach.  Adding package management like dpkgs and rpms would ruin the idea of Gentoo.  Dont let me stop you though!

---

### Post by forrestcupp on 2007-04-07
I used Sabayon for a while, and I didn't really like portage.  The concept is great, but it took forever to install things.  It has to download, configure, build, then install and if you're doing very much, it takes a very long time.  So I tried to convince myself that the speed increase in the running of the programs would be worth the wait of installing.  But I actually think things are slightly faster or at least the same when I install binaries from apt-get.  So I don't really see any worthwhile advantages to portage except that there were some things available in the portage tree that aren't available in Ubuntu repos (like cinelerra).  But there are a lot of things missing from portage, too, though.

Anyway, Sabayon just started testing a binary repo that runs parallel with the portage tree.  It looks promising, but it's far from complete.  But I think I'll stick with Ubuntu.

---

### Post by Sunnz on 2007-04-07
> **jeffc313 said:**
> Ubuntu for total package management, gentoo for a totally compiled on your box, customized approach. What's a "total package management"?

Anyway I think people often wish for the best of both worlds. Install apps as quickly as possible so you can use it, but want to customise more when they want more.

---

### Post by TravisNewman on 2007-04-07
jdong, back in late 2004 or early 2005, managed to get emerge/portage installed on Ubuntu, and it did actually work.

One gentoo install I did once, I just installed the base of required packages then compiled apt to install from Debian repositories. That way I had the INCREDIBLE hardware detection of Gentoo and apt to install stuff.

I ended up having to manually edit some dependencies in some debs for them to install properly but I eventually got a functioning system... but not one that you could do much with. Everything that I wanted to install had issues, as you could imagine with two separate package managers competing for the system.

If one were to do this, a new repo and portage tree would need to be made. Either have an ubuntu based repository for system components or applications, and a portage tree for the other one. I think it could be done, but not with the default repositories.

---

### Post by aeto on 2007-04-07
> Anyway, Sabayon just started testing a binary repo that runs parallel with the portage tree.  It looks promising, but it's far from complete.  But I think I'll stick with Ubuntu.

That's right. This project is called "Entropy". It is VERY new. Fabio (lxnay) is having good progress so far, and things definitely are looking better. This basically will integrate binary- AND source-based package management seamlessly. It is one of, if not the first of its kind (CRUX & Slackware derivatives tried somewhat similar routes). Portage, well, given its power, it has its ups and downs. One thing that Entropy will rectify is dependency. Right on, so from there, you can pretty much modify the mechanism.

Gentoo has BINHOST, where you specify a binary pool (its very nice because there are arch-optimized pools) and get your packages. Revolving around that system, you can use the Ubuntu repos and DEB-based binaries. With Entropy, the fluctuation and conflict between source and binary will no longer be a cause for concern.

[http://planet.sabayonlinux.org](http://planet.sabayonlinux.org) - read about it here
[www.wikipedia.ork/wiki/SabayonLinux](www.wikipedia.ork/wiki/SabayonLinux) - updated info

---

### Post by RAV TUX on 2007-04-07
> **Sunnz said:**
> What's a "total package management"?

Anyway I think people often wish for the best of both worlds. Install apps as quickly as possible so you can use it, but want to customise more when they want more.

> **panickedthumb said:**
> jdong, back in late 2004 or early 2005, managed to get emerge/portage installed on Ubuntu, and it did actually work.

One gentoo install I did once, I just installed the base of required packages then compiled apt to install from Debian repositories. That way I had the INCREDIBLE hardware detection of Gentoo and apt to install stuff.

I ended up having to manually edit some dependencies in some debs for them to install properly but I eventually got a functioning system... but not one that you could do much with. Everything that I wanted to install had issues, as you could imagine with two separate package managers competing for the system.

If one were to do this, a new repo and portage tree would need to be made. Either have an ubuntu based repository for system components or applications, and a portage tree for the other one. I think it could be done, but not with the default repositories.

This is why I find there is more potential in a conary based OS like that found in [SIZE=4][COLOR=Purple]**Oz[COLOR=Gray],[/COLOR] **[SIZE=2][COLOR=Gray]also
the ease of use in updates utilizing the [/COLOR][/SIZE][/COLOR][/SIZE][rAA]("http://cafelinux.org/forum/index.php/topic,183.0.html") is simply awesome.

---

### Post by Ateo on 2007-04-18
would be a good idea. However, compiling from source is retarded, for the average user who just needs to work. Compiling from source is for the geeks with nothing better to do than to watch compile code fly by.

Ubuntu is fine just the way it is....

---

### Post by igknighted on 2007-04-18
> **Ateo said:**
> would be a good idea. However, compiling from source is retarded, for the average user who just needs to work. Compiling from source is for the geeks with nothing better to do than to watch compile code fly by.

Ubuntu is fine just the way it is....

Did you read the thread?  You missed the point entirely.  The point is that this ISNT for the average user, but rather an attempt to take a great idea like Gentoo, and put a Ubuntu twist on it (IE, make it more user friendly).  There are lots of more advanced linux users who would use Ubuntu if it had anything to offer them, and part of making linux for everyone (in my mind) means some for new users, and some for advanced users.  Take a look at PC-BSD or DesktopBSD, or even Sabayon.  All these integrate the source and binary repos to make an environment where users can have immense control over their software.  This is what the Ubentoo idea is about.

---

### Post by RAV TUX on 2007-04-18
> **igknighted said:**
> Did you read the thread?  You missed the point entirely.  The point is that this ISNT for the average user, but rather an attempt to take a great idea like Gentoo, and put a Ubuntu twist on it (IE, make it more user friendly).  There are lots of more advanced linux users who would use Ubuntu if it had anything to offer them, and part of making linux for everyone (in my mind) means some for new users, and some for advanced users.  Take a look at PC-BSD or DesktopBSD, or even Sabayon.  All these integrate the source and binary repos to make an environment where users can have immense control over their software.  This is what the Ubentoo idea is about.

Thank You igknighted for your understanding and clarification:)

---

### Post by Sunnz on 2007-04-19
> **Ateo said:**
> would be a good idea. However, compiling from source is retarded, for the average user who just needs to work. Compiling from source is for the geeks with nothing better to do than to watch compile code fly by.

Ubuntu is fine just the way it is....
If people can just read about things themselves before post this nonsense the world would be a much much better place.

---

### Post by salsafyren on 2007-05-19
So are there anybody working on this?

Maybe you could integrate gobolinux's ([http://www.gobolinux.org/](http://www.gobolinux.org/)) tools into this?

They have some really simple "recipes" to build packages.

---

### Post by dan171717 on 2007-06-09
so this is saying that you can run ubuntu with the bsd kernel insted of linux

---

### Post by mips on 2007-06-09
> **Sunnz said:**
> If people can just read about things themselves before post this nonsense the world would be a much much better place.

Agreed. Then you get those that argue it takes to long and they want it installed NOW.

---

### Post by helliewm on 2007-06-09
This is very interesting I am devoted to Ubuntu and single boot Ubuntu on my laptop and desktop but my second choice would be Sabayon.

Yes this would be a good project.

Helen

---

