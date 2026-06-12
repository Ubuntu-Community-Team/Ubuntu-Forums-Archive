---
title: "Possible answers to Installation Complexities"
date: 2005-12-07
forum: The Cafe
---

### Post by matthewstory on 2005-12-07
Alot of the insults directed at Linux by Windows users switching to their first linux distribution is at how much of a pain it is to install things in Linux.  I, and I'm sure most of you, don't agree with this claim, but i think there are several ways in which it could be made less complex (and by that i mean easier for the average windows convert).

My roomate and i were discussing this the other day and we each came up with one solution that we think might make linux installs easier on the average ex-windows user.

Solution 1:

Make it like mac OS X, and make the install the combination of downloading an image and then dragging it into an application program.  This option is being looked into by GOBO linux ([http://www.gobolinux.org/)](http://www.gobolinux.org/)).

Their whole catch is to rewrite the file system heirarchy in linux so that when you install an application all of the files for that application go into the application folder along with the application itself.  This solution would stop all the threads popping up on here that go something like this "I installed a bunch of programs but where are they?"  And if one needed to edit a file they wouldn't have to search around /etc and /usr/local/lib etc.

Solution 2:

Make all installations Jam installations.  Jam is a installation tool like make, except all you have to do to jam install is be in the right directory and then simply run jam.  Jam then downloads and compiles all the dependancies and then compiles and installs the desired program as well.  If a simple GUI were written for jam, that allowed you to use a file browser to surf to the proper directory and then you pushed a button to 'jam' the file, this would make installs akin to a wizard instillation.

Anyway those were our ideas.

regards,
matt

---

### Post by aysiu on 2005-12-07
Ideally, I'd like to see solution #3--add more packages to the repositories. There's nothing I've found easier than apt-get/Synaptic.

Fortunately, for me, almost everything I ever want to install is in the repositories.

Unfortunately, for other people, the repositories are limited, and they find themselves having to manually (alien) install .rpm files or extracting and compiling .tar.gz files from source.

There used to be an add-on repositories CD floating around, too, for those without an internet connection. I don't know what happened to that...

---

### Post by matthewstory on 2005-12-07
I use several other repositories to get all the programs i need through apt-get, but not all of them are there.  I have no problem installing from the source, i actually enjoy it (and after a few goes it's a relatively easy and painless process).  Specific to Ubuntu is the problem that debian-sarge packages don't always work for Ubuntu anymore, i read an article the other week about how Ubuntu has surpassed and is no longer Debian at all, but is now a completely seperate distro.  
The first time I used Jam was to install handbrake, which has a debian repository, but unfortuanately uses some more current packages than are in the global ubuntu repositories.  So i downloaded the source and ran jam, and voila, i run one program with one command and all my dependancies are downloaded and compiled and now i can run handbrake (alot like apt-get actually, except it works from the source, and doesn't require debian packages).
But yea, if there were more packages then there would be no need for these solutions, now if only there were a way to force people to build packages . . . hmmmm (include evillaugh.h) hahahahahahaha.

regards,
matt

---

