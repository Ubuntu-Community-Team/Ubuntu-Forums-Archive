---
title: "Where is this impossible-to-install software?"
date: 2006-08-16
forum: The Cafe
---

### Post by Iandefor on 2006-08-16
I've recently seen some debates over package management and seen the argument that because* some* software isn't in the repos, isn't in a third-party repo, hasn't been packaged for your distro, nor will the software compile because of library version mismatches, in terms of software installation, Linux is inferior to Windows. I have *never* encountered a piece of software I couldn't get up and running because of the above problems. What software is out there that:[LIST=1]
[*]Isn't in the Ubuntu repo's
[*]Isn't in a third-party repo that works for Ubuntu
[*]Hasn't been packaged for Dapper, nor does a package exist that will work on Ubuntu
[*]Suffers from unresolvable dependency mismatches with Ubuntu[/LIST]I'm really quite interested in hearing about it, because, well, I've heard this above argument used too much and now I want some concrete evidence for it.

For any newcomers to the thread, the list is currently composed of:
[INDENT][URL="http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake"]DiskDrake
[/URL][/INDENT]There used to be three other items on that list, such as LSongs, FIleZilla, and Songbird. However, that was last updated on 16 August 2006. Now all three have an installation path on Ubuntu and the only remaining software whose installability status is "impossible" is DiskDrake.

---

### Post by bluntu on 2006-08-16
For a moment I though you mean "Where is this impossible-to-install software? Tell me and I will make it work!" LOL

I'm bookmarking this thread and will let you know when I find one since I look for softwares on my spare time.

---

### Post by aysiu on 2006-08-16
Songbird and FileZilla...? I guess those aren't even in alpha testing yet, so they don't count...?

LSongs?

---

### Post by ahaslam on 2006-08-16
I believe that it's nonexistent.
There is only different levels of difficulty, some seem to confuse 'hard' with 'impossible' though. I find that a lack documentation often makes things seem impossible, which is often the case for many obscure/uncommon/cutting edge apps.

Tony.

.. Oh, I got it.. some windows apps are impossible to install/run without some core MS components ;)

---

### Post by aysiu on 2006-08-16
> **Anthony Haslam said:**
> I believe that it's nonexistent.
There is only different levels of difficulty, some seem to confuse 'hard' with 'impossible' though. I find that a lack documentation often makes things seem impossible, which is often the case for many obscure/uncommon/cutting edge apps.

Tony.
Can anyone show us with terminal output evidence of LSongs being "not impossible" to install on Ubuntu?

[http://lsongs.com/?page=downloads](http://lsongs.com/?page=downloads)

---

### Post by 23meg on 2006-08-16
> **aysiu said:**
> Can anyone show us with terminal output evidence of LSongs being "not impossible" to install on Ubuntu?

[http://lsongs.com/?page=downloads](http://lsongs.com/?page=downloads)
Does the RPM not work when converted via Alien? [quote=Iandefor]3. Hasn't been packaged for Dapper, nor does a package exist that will work on Dapper[/quote]

---

### Post by aysiu on 2006-08-16
> **23meg said:**
> Does the RPM not work when converted via Alien?
Nope. Believe me--I've tried. I've also searched the Ubuntu forums and haven't found anyone able to successfully install it.

Now, don't get me wrong. Even though I think there does exist "impossible" to install software, I agree with the general sentiment of Iandefor's post: I have yet to find software I've truly needed in Ubuntu that I couldn't find either in the repositories or as a precompiled .deb.

I didn't really need LSongs, but I remember on a couple of occasions trying to help someone on these forums install LSongs and to no avail.

**Edit**: Here are two threads as examples that I was able to dig up through a Google search:
[http://ubuntuforums.org/showthread.php?t=51844](http://ubuntuforums.org/showthread.php?t=51844)
[http://ubuntuforums.org/showthread.php?t=22056](http://ubuntuforums.org/showthread.php?t=22056)

---

### Post by magnoliablossom on 2006-08-16
I've only had one that I couldn't get installed which was Winamp...And I know it works on Linux/Ubuntu.  It was the Linux version.  When I installed it, it just sat there.  But I really didn't put forth much of an effort because Totem works fine for me.

---

### Post by 23meg on 2006-08-16
[QUOTE=aysiu]
Now, don't get me wrong. Even though I think there does exist "impossible" to install software, I agree with the general sentiment of Iandefor's post
[/QUOTE]I did expect that you'd agree. 

For what I observed, most of the flak we take about things being "impossible to install" is based on drivers for specific hardware being "impossible" to compile, and when a user can't get their hardware working, they tend to be very upset.

Other than that, people usually don't complain about things being "impossible" to install, but rather "too hard" to install, which  in most cases translates as "I'm reluctant to leave my understanding that to install something means double click next I agree next next finish".

---

### Post by ahaslam on 2006-08-16
Pyxine (a dependency of Lsongs):
"This code is in it's very infancy"
"I've also updated the (still incomplete) README"

Alpha with incomplete documentation :-k no wonder it's hard to install.

Tony ;)

---

### Post by aysiu on 2006-08-16
But LSongs itself isn't alpha software, only the pyxine package.

---

### Post by ahaslam on 2006-08-16
> **23meg said:**
> For what I observed, most of the flak we take about things being "impossible to install" is based on drivers for specific hardware being "impossible" to compile, and when a user can't get their hardware working, they tend to be very upset.

Other than that, people usually don't complain about things being "impossible" to install, but rather "too hard" to install, which  in most cases translates as "I'm reluctant to leave my understanding that to install something means double click next I agree next next finish".
I couldn't agree more.

Tony ;)

---

### Post by ahaslam on 2006-08-16
> **aysiu said:**
> But LSongs itself isn't alpha software, only the pyxine package.

But it's a package that's essential for it to work. If it doesn't work properly, I wouldn't expect Lsongs to.

Tony.

---

### Post by aysiu on 2006-08-16
Anyone want to tack on to [this survey](http://www.ubuntuforums.org/showthread.php?t=116365)?

---

### Post by ahaslam on 2006-08-16
> **aysiu said:**
> Anyone want to tack on to [this survey](http://www.ubuntuforums.org/showthread.php?t=116365)?

*I need a few programs that aren't conveniently packaged, but I don't mind installing from source.* - That's  me ;)

---

### Post by Iandefor on 2006-08-16
So, LSongs, which depends on a project that's been dead for three years and is written in python anyways. FileZilla and Songbird, neither of which have even hit alpha yet. We have three projects, all of which have extremely important caveats.

Any more?

---

### Post by aysiu on 2006-08-16
DiskDrake?

---

### Post by Iandefor on 2006-08-16
> **aysiu said:**
> DiskDrake? Good, good, let's keep going... so, four pieces of software, 3 of which have important caveats and one of which I know almost nothing about.

Let's keep the ball rolling!

Oh, and by the way, if anyone wants to try and subject themselves to fixing pyxine to get LSongs going on Dapper, the build failed, but I have build output in the attached document.

---

### Post by aysiu on 2006-08-16
If you don't want to click the attachment, here it is inline: ```
running build
running build_py
running build_ext
building 'pxlibc' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c pxlib/Geometry.cc -o build/temp.linux-i686-2.4/pxlib/Geometry.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from /usr/include/python2.4/Python.h:8,
                 from pxlib/Traits.h:31,
                 from pxlib/Geometry.cc:28:
/usr/include/python2.4/pyconfig.h:835:1: warning: "_POSIX_C_SOURCE" redefined
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/i486-linux-gnu/bits/os_defines.h:39,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/i486-linux-gnu/bits/c++config.h:35,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/iostream:43,
                 from pxlib/pxlib.h:26,
                 from pxlib/Geometry.h:28,
                 from pxlib/Geometry.cc:24:
/usr/include/features.h:150:1: warning: this is the location of the previous definition
pxlib/Geometry.cc:34: error: explicit specialization of â&#8364;&#732;pyxine::VideoGeometry pyxine::Traits<pyxine::VideoGeometry>::unpack_tuple(PyObject*)â&#8364;&#8482; must be introduced by â&#8364;&#732;template <>â&#8364;&#8482;
pxlib/Geometry.cc:34: error: template-id â&#8364;&#732;unpack_tuple<>â&#8364;&#8482; for â&#8364;&#732;pyxine::VideoGeometry pyxine::Traits<pyxine::VideoGeometry>::unpack_tuple(PyObject*)â&#8364;&#8482; does not match any template declaration
pxlib/Geometry.cc:34: error: invalid function declaration
pxlib/Geometry.cc:45: error: explicit specialization of â&#8364;&#732;PyObject* pyxine::Traits<pyxine::VideoGeometry>::pack_tuple(const pyxine::VideoGeometry&)â&#8364;&#8482; must be introduced by â&#8364;&#732;template <>â&#8364;&#8482;
pxlib/Geometry.cc:45: error: template-id â&#8364;&#732;pack_tuple<>â&#8364;&#8482; for â&#8364;&#732;PyObject* pyxine::Traits<pyxine::VideoGeometry>::pack_tuple(const pyxine::VideoGeometry&)â&#8364;&#8482; does not match any template declaration
pxlib/Geometry.cc:45: error: invalid function declaration
pxlib/Geometry.cc:57: error: explicit specialization of â&#8364;&#732;pyxine::VideoOutputGeometry pyxine::Traits<pyxine::VideoOutputGeometry>::unpack_tuple(PyObject*)â&#8364;&#8482; must be introduced by â&#8364;&#732;template <>â&#8364;&#8482;
pxlib/Geometry.cc:57: error: template-id â&#8364;&#732;unpack_tuple<>â&#8364;&#8482; for â&#8364;&#732;pyxine::VideoOutputGeometry pyxine::Traits<pyxine::VideoOutputGeometry>::unpack_tuple(PyObject*)â&#8364;&#8482; does not match any template declaration
pxlib/Geometry.cc:57: error: invalid function declaration
pxlib/Geometry.cc:72: error: explicit specialization of â&#8364;&#732;PyObject* pyxine::Traits<pyxine::WindowGeometry>::pack_tuple(const pyxine::WindowGeometry&)â&#8364;&#8482; must be introduced by â&#8364;&#732;template <>â&#8364;&#8482;
pxlib/Geometry.cc:72: error: template-id â&#8364;&#732;pack_tuple<>â&#8364;&#8482; for â&#8364;&#732;PyObject* pyxine::Traits<pyxine::WindowGeometry>::pack_tuple(const pyxine::WindowGeometry&)â&#8364;&#8482; does not match any template declaration
pxlib/Geometry.cc:72: error: invalid function declaration
pxlib/Geometry.cc:83: error: explicit specialization of â&#8364;&#732;std::string pyxine::Traits<pyxine::WindowGeometry>::to_string(const pyxine::WindowGeometry&)â&#8364;&#8482; must be introduced by â&#8364;&#732;template <>â&#8364;&#8482;
pxlib/Geometry.cc:83: error: template-id â&#8364;&#732;to_string<>â&#8364;&#8482; for â&#8364;&#732;std::string pyxine::Traits<pyxine::WindowGeometry>::to_string(const pyxine::WindowGeometry&)â&#8364;&#8482; does not match any template declaration
pxlib/Geometry.cc:83: error: invalid function declaration
error: command 'gcc' failed with exit status 1

```

---

### Post by DoktorSeven on 2006-08-16
n/m

---

### Post by Iandefor on 2006-08-16
> **aysiu said:**
> If you don't want to click the attachment, here it is inline: ```
running build
running build_py
running build_ext
building 'pxlibc' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c pxlib/Geometry.cc -o build/temp.linux-i686-2.4/pxlib/Geometry.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from /usr/include/python2.4/Python.h:8,
                 from pxlib/Traits.h:31,
                 from pxlib/Geometry.cc:28:
/usr/include/python2.4/pyconfig.h:835:1: warning: "_POSIX_C_SOURCE" redefined
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/i486-linux-gnu/bits/os_defines.h:39,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/i486-linux-gnu/bits/c++config.h:35,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/iostream:43,
                 from pxlib/pxlib.h:26,
                 from pxlib/Geometry.h:28,
                 from pxlib/Geometry.cc:24:
/usr/include/features.h:150:1: warning: this is the location of the previous definition
pxlib/Geometry.cc:34: error: explicit specialization of â€˜pyxine::VideoGeometry pyxine::Traits<pyxine::VideoGeometry>::unpack_tuple(PyObject*)â€™ must be introduced by â€˜template <>â€™
pxlib/Geometry.cc:34: error: template-id â€˜unpack_tuple<>â€™ for â€˜pyxine::VideoGeometry pyxine::Traits<pyxine::VideoGeometry>::unpack_tuple(PyObject*)â€™ does not match any template declaration
pxlib/Geometry.cc:34: error: invalid function declaration
pxlib/Geometry.cc:45: error: explicit specialization of â€˜PyObject* pyxine::Traits<pyxine::VideoGeometry>::pack_tuple(const pyxine::VideoGeometry&)â€™ must be introduced by â€˜template <>â€™
pxlib/Geometry.cc:45: error: template-id â€˜pack_tuple<>â€™ for â€˜PyObject* pyxine::Traits<pyxine::VideoGeometry>::pack_tuple(const pyxine::VideoGeometry&)â€™ does not match any template declaration
pxlib/Geometry.cc:45: error: invalid function declaration
pxlib/Geometry.cc:57: error: explicit specialization of â€˜pyxine::VideoOutputGeometry pyxine::Traits<pyxine::VideoOutputGeometry>::unpack_tuple(PyObject*)â€™ must be introduced by â€˜template <>â€™
pxlib/Geometry.cc:57: error: template-id â€˜unpack_tuple<>â€™ for â€˜pyxine::VideoOutputGeometry pyxine::Traits<pyxine::VideoOutputGeometry>::unpack_tuple(PyObject*)â€™ does not match any template declaration
pxlib/Geometry.cc:57: error: invalid function declaration
pxlib/Geometry.cc:72: error: explicit specialization of â€˜PyObject* pyxine::Traits<pyxine::WindowGeometry>::pack_tuple(const pyxine::WindowGeometry&)â€™ must be introduced by â€˜template <>â€™
pxlib/Geometry.cc:72: error: template-id â€˜pack_tuple<>â€™ for â€˜PyObject* pyxine::Traits<pyxine::WindowGeometry>::pack_tuple(const pyxine::WindowGeometry&)â€™ does not match any template declaration
pxlib/Geometry.cc:72: error: invalid function declaration
pxlib/Geometry.cc:83: error: explicit specialization of â€˜std::string pyxine::Traits<pyxine::WindowGeometry>::to_string(const pyxine::WindowGeometry&)â€™ must be introduced by â€˜template <>â€™
pxlib/Geometry.cc:83: error: template-id â€˜to_string<>â€™ for â€˜std::string pyxine::Traits<pyxine::WindowGeometry>::to_string(const pyxine::WindowGeometry&)â€™ does not match any template declaration
pxlib/Geometry.cc:83: error: invalid function declaration
error: command 'gcc' failed with exit status 1

``` It renders some of the characters rather funkily. I wonder why?

---

### Post by aysiu on 2006-08-16
> **Iandefor said:**
> It renders some of the characters rather funkily. I wonder why?
I was using Windows at the time. How's this? ```
running build
running build_py
running build_ext
building 'pxlibc' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c pxlib/Geometry.cc -o build/temp.linux-i686-2.4/pxlib/Geometry.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from /usr/include/python2.4/Python.h:8,
                 from pxlib/Traits.h:31,
                 from pxlib/Geometry.cc:28:
/usr/include/python2.4/pyconfig.h:835:1: warning: "_POSIX_C_SOURCE" redefined
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/i486-linux-gnu/bits/os_defines.h:39,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/i486-linux-gnu/bits/c++config.h:35,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/iostream:43,
                 from pxlib/pxlib.h:26,
                 from pxlib/Geometry.h:28,
                 from pxlib/Geometry.cc:24:
/usr/include/features.h:150:1: warning: this is the location of the previous definition
pxlib/Geometry.cc:34: error: explicit specialization of ‘pyxine::VideoGeometry pyxine::Traits<pyxine::VideoGeometry>::unpack_tuple(PyObject*)’ must be introduced by ‘template <>’
pxlib/Geometry.cc:34: error: template-id ‘unpack_tuple<>’ for ‘pyxine::VideoGeometry pyxine::Traits<pyxine::VideoGeometry>::unpack_tuple(PyObject*)’ does not match any template declaration
pxlib/Geometry.cc:34: error: invalid function declaration
pxlib/Geometry.cc:45: error: explicit specialization of ‘PyObject* pyxine::Traits<pyxine::VideoGeometry>::pack_tuple(const pyxine::VideoGeometry&)’ must be introduced by ‘template <>’
pxlib/Geometry.cc:45: error: template-id ‘pack_tuple<>’ for ‘PyObject* pyxine::Traits<pyxine::VideoGeometry>::pack_tuple(const pyxine::VideoGeometry&)’ does not match any template declaration
pxlib/Geometry.cc:45: error: invalid function declaration
pxlib/Geometry.cc:57: error: explicit specialization of ‘pyxine::VideoOutputGeometry pyxine::Traits<pyxine::VideoOutputGeometry>::unpack_tuple(PyObject*)’ must be introduced by ‘template <>’
pxlib/Geometry.cc:57: error: template-id ‘unpack_tuple<>’ for ‘pyxine::VideoOutputGeometry pyxine::Traits<pyxine::VideoOutputGeometry>::unpack_tuple(PyObject*)’ does not match any template declaration
pxlib/Geometry.cc:57: error: invalid function declaration
pxlib/Geometry.cc:72: error: explicit specialization of ‘PyObject* pyxine::Traits<pyxine::WindowGeometry>::pack_tuple(const pyxine::WindowGeometry&)’ must be introduced by ‘template <>’
pxlib/Geometry.cc:72: error: template-id ‘pack_tuple<>’ for ‘PyObject* pyxine::Traits<pyxine::WindowGeometry>::pack_tuple(const pyxine::WindowGeometry&)’ does not match any template declaration
pxlib/Geometry.cc:72: error: invalid function declaration
pxlib/Geometry.cc:83: error: explicit specialization of ‘std::string pyxine::Traits<pyxine::WindowGeometry>::to_string(const pyxine::WindowGeometry&)’ must be introduced by ‘template <>’
pxlib/Geometry.cc:83: error: template-id ‘to_string<>’ for ‘std::string pyxine::Traits<pyxine::WindowGeometry>::to_string(const pyxine::WindowGeometry&)’ does not match any template declaration
pxlib/Geometry.cc:83: error: invalid function declaration
error: command 'gcc' failed with exit status 1
```

---

### Post by Iandefor on 2006-08-16
Not so funky :-D.

---

### Post by welsh_spud on 2006-08-17
A *LOT* of the stuff in [KDE-Apps]("http://www.kde-apps.org/") doesn't have an Ubuntu package, and are pretty awkward to install.

---

### Post by slimdog360 on 2006-08-17
loki installer

---

### Post by 3rdalbum on 2006-08-17
I couldn't get EnemyLines 3 (version 1.2) to compile the first time I did it, but just now when I tried to compile again (to get an error message) it worked.

Songbird compiled for me without a problem, but that was a while ago so their later nightly builds might be more difficult.

---

### Post by prizrak on 2006-08-17
For some reason Winamp and iLife just don't install on Ubuntu. I dunno I mean I've tried everything. Oh wait they are for a different OS never mind ;) I have not been able to find any software actually made for Linux that wouldn't install. It might be a huge pain in the butt and you might run into dependancy hell (I have) but eventually you will get it working. Hell I even manage to install from CVS when the need arises and those things are barely in alpha.

---

### Post by Iandefor on 2006-08-17
> **welsh_spud said:**
> A *LOT* of the stuff in [KDE-Apps]("http://www.kde-apps.org/") doesn't have an Ubuntu package, and are pretty awkward to install. But you can get them to compile?> **3rdalbum said:**
> I couldn't get EnemyLines 3 (version 1.2) to compile the first time I did it, but just now when I tried to compile again (to get an error message) it worked.

Songbird compiled for me without a problem, but that was a while ago so their later nightly builds might be more difficult. Well, then one more **not** going on the list :).

Songbird also worked for me, but that was a while ago, too.

---

### Post by Iandefor on 2006-08-17
> **prizrak said:**
> For some reason Winamp and iLife just don't install on Ubuntu. I dunno I mean I've tried everything. Oh wait they are for a different OS never mind ;) I have not been able to find any software actually made for Linux that wouldn't install. It might be a huge pain in the butt and you might run into dependancy hell (I have) but eventually you will get it working. Hell I even manage to install from CVS when the need arises and those things are barely in alpha. iLife won't install?! Oh noes!

---

### Post by aysiu on 2006-10-17
I've got a couple more to add to the list. Not impossible, but difficult:

F4L
Jedit

---

### Post by Randal Leavitt on 2006-10-17
OK - I have hit a brick wall with Codeweaver's "Crossover Office".  The installation script seems to run without errors, but the application will not install any Windows applications for me.  This is critical in my case since I have to have Quicken 2000 running if I want to use Ubuntu as my primary machine (a requirement that is out of my control).

I think the Codeweavers and the Ubuntu people need to talk.  I don't have the resources to make this happen.  I have listed this problem as a ticket item at Codeweavers, and as a forum entry on Ubuntu.

---

### Post by Iandefor on 2006-10-17
> **aysiu said:**
> I've got a couple more to add to the list. Not impossible, but difficult:

F4L
Jedit No problems here installing Jedit. There's a Debian repository that works with Dapper on the Jedit website. Just check the [download page]("http://www.jedit.org/index.php?page=download").

I'll look into F4L.

Thanks!

---

### Post by aysiu on 2006-10-17
I did.

The repository never resolved itself.

[If you do a search for threads involving *jedit* in the title, you'll see almost all of them have to do with how to install it, and almost all of them have no solution given on how to install it.](http://ubuntuforums.org/search.php?searchid=8904466)

I just tried to install it myself in the hopes of helping a new user install it. No luck, even with Sun's Java.

---

### Post by 3rdalbum on 2006-10-17
I second F4L. I couldn't get it to compile either.

Also, Gnomad 2.8.6 wouldn't compile for me, and I couldn't figure it out.

---

### Post by Bloch on 2006-10-17
I was able to install gnomad 2.8.8 by following this thread:
[http://ubuntuforums.org/showthread.php?t=199250&highlight=creative+V+zen](http://ubuntuforums.org/showthread.php?t=199250&highlight=creative+V+zen)

The original instructions had become faulty (maybe they have been updated again) and I had to do some extra messing creating a symlink as one poster mentioned. But most people on the thread couldn't ionstall it.
I installed it by the shel;l script which installs executables as I always do that before attempting to compile.

The software works great - it's a pity the creators' don't make the extra effort to make it easily available.

---

### Post by FISHERMAN on 2006-10-17
I find Gens (Sega Genesis/MegaDrive emulator) hard to compile and I havn't been able to find a deb.

---

### Post by zugu on 2006-10-17
I wish there was a .deb for XMMS-projectM - a Linux port of the popular Winamp visualisation plug-in, Milkdrop. I tried to compile libprojectm by myself (the first requirement of projectm), but got stuck.

LinuxDC++/Valknut/Wulfor - these are DC++ clients that need precompiled debs. Many of them are in alpha/beta, but there are unofficial packages arount the forum. They should also be in the repos - it's better than nothing.

There are many applications that have not reached their 1.0 version. Does this mean they shouldn't be in the repos? Look at GStreamer, or VLC, or Wine or whatever; they are not "finished" and "polished", yet they are in the repos. What if the Ubuntu devs would have chosen to wait for these projects to mature, before adding them in the distribution? I think this debunks the "if it's alpha/beta then it's not gonna make it in the repos" kind of excuse.

---

### Post by Iandefor on 2007-05-16
It's been a good few months, plenty of new faces. Anybody else run across software that they just could not get to install on Ubuntu? Since there've been a few releases since I last updated this, specifying the release you tried it on would be neat. As well as the particular version of the software you tried to install.

---

### Post by strixy on 2007-05-16
Good thread! 

If you're accepting software running under Wine as not too much of a caveat  then I would add Corel Draw (without crossover). It's been a year since I last tried and I don't really care to try again any time soon. Of course, with the state of native SVG packages coming along quite nicely... I figure I'll just wait.

---

### Post by Iandefor on 2007-05-16
> **strixy said:**
> Good thread! 

If you're accepting software running under Wine as not too much of a caveat  then I would add Corel Draw (without crossover). It's been a year since I last tried and I don't really care to try again any time soon. Of course, with the state of native SVG packages coming along quite nicely... I figure I'll just wait.I'm hesitant to include Windows software under WINE, because Windows software running under WINE isn't proper Linux software and isn't liable to be packaged for a particular distro (Ignoring cases like PC-BSD for the moment).

To recap, we left off with:[INDENT]LSongs
DiskDrake
FileZilla
Songbird
[/INDENT]Let's cross Songbird off the list, because it will now build under Linux, as well as FileZilla, because, as its [documentation states]("http://filezilla.sourceforge.net/documentation/"),> FileZilla is a powerful FTP-client for Windows NT4,  2000 and XP. It has  been designed for ease of use and with support for as many features as possible,  while still being fast and reliable.Which means it isn't *Linux* software.

---

### Post by aysiu on 2007-05-16
Well, Songbird has an installation script, which makes it pretty easy to install.
Filezilla is now in the repositories.
I think I saw a recent thread about successfully installing LSongs (I'll have to dig up the thread).

That leaves... DiskDrake.

**Edit**: Here we go:
[LSongs for Kubuntu/Ubuntu 6.10 (Edgy)](http://thoc.blogspot.com/search/label/lsongs)

---

### Post by Iandefor on 2007-05-17
> **aysiu said:**
> Well, Songbird has an installation script, which makes it pretty easy to install.
Filezilla is now in the repositories.
I think I saw a recent thread about successfully installing LSongs (I'll have to dig up the thread).

That leaves... DiskDrake.

**Edit**: Here we go:
[LSongs for Kubuntu/Ubuntu 6.10 (Edgy)]("http://thoc.blogspot.com/search/label/lsongs") A list of 1 so far?

I'm impressed.

---

### Post by pmj on 2007-05-17
As long as you can exclude beta software, any other versions of software as long as one version is packaged, and anything that isn't completely IMPOSSIBLE to install, you're bound to be left with a very short list. Longer than one, mind you, since we're just a few people on a forum and not an entity with perfect knowledge of all Linux software in existence.

You also completely ignore that many people DO want newer software than is packaged, DO want new software on their one year old installation, and DON'T want to compile it on their own, and they want it EASY. That is NOT available for us today. It just isn't.

This thread proves nothing except the unwillingness of some people to have an honest debate. But I guess it's easy to declare yourself the winner of this game if you get to decide the rules, huh?

---

### Post by JNowka on 2007-05-17
I have to admit that I was able to install LSongs on Feisty.  Most of the needed files are found in the repos.  

The only files needed for download was the id3lib, and the pyid3lib.  
Oh and you need to type in after the install of id3lib "sudo cp /usr/local/lib/libid3-3.8.so.3 /usr/lib"

*EDIT* 
I forgot to include the fact that you have to comment out "import ipod" in the PodLibrary.py and PodPlaylist.py that is found in the folder "/usr/lib/python2.5/site-packages/Lsongs"
*END EDIT*

after that everything should work just fine.

good luck

---

### Post by jariku on 2007-05-17
> **JNowka said:**
> Oh and you need to type in after the install of id3lib "sudo cp /usr/local/lib/libid3-3.8.so.3 /usr/lib"
Would a soft link do? That is, after all, "the UNIX way". :)

---

### Post by ReiKn on 2007-05-17
> **aysiu said:**
> Well, Songbird has an installation script, which makes it pretty easy to install.
Filezilla is now in the repositories.
I think I saw a recent thread about successfully installing LSongs (I'll have to dig up the thread).

That leaves... DiskDrake.

**Edit**: Here we go:
[LSongs for Kubuntu/Ubuntu 6.10 (Edgy)](http://thoc.blogspot.com/search/label/lsongs)

[http://www.getdeb.net/search.php?keywords=songbird](http://www.getdeb.net/search.php?keywords=songbird) <- for songbird there's even a .deb.

---

### Post by salsafyren on 2007-05-17
> **pmj said:**
> 
You also completely ignore that many people DO want newer software than is packaged, DO want new software on their one year old installation, and DON'T want to compile it on their own, and they want it EASY. That is NOT available for us today. It just isn't.

This thread proves nothing except the unwillingness of some people to have an honest debate. But I guess it's easy to declare yourself the winner of this game if you get to decide the rules, huh?

I completely agree. This thread is a waste of time and actually proves you (the one who opened this thread) think users are stupid because they want something that is not in the repositories.

"I am right, there is only 1 package not in the repositories. Ubuntu is so great!".

The level of discussion in this forum is getting lower all the time because you are NOT acknowledging the weaknesses but instead cover your eyes and ears. At least, that's how it looks from the outside.

---

### Post by zugu on 2007-05-17
I can't find newer versions for nearly all the software in the Ubuntu Dapper repositories. Could it be because Ubuntu is using a time-based release model, forcing me to update every six months? I guess not. Anyway, please update the list for me, OP.

---

### Post by Bou on 2007-05-17
> **Iandefor said:**
> 
[*]Isn't in the Ubuntu repo's
[*]Isn't in a third-party repo that works for Ubuntu
[*]Hasn't been packaged for Dapper, nor does a package exist that will work on Ubuntu
[*]Suffers from unresolvable dependency mismatches with Ubuntu[/LIST]I'm really quite interested in hearing about it, because, well, I've heard this above argument used too much and now I want some concrete evidence for it.

Well, I've found some packages in the past that I couldn't install but of course it could just be that I didn't know what to do or where to look, rather than it was actually impossible to install. But it's true that software that:

> [*]Isn't in the Ubuntu repo's

Is harder than it ideally should. In my -possibly unfounded- opinion, there should be a standard installation package format that would work for ANY distro and would include the package itself AND all of its dependencies, except really big ones that any system with Linux should have installed or available like the GTK libraries, for example.

This kind of package should be in each program's webpage and installed through some kind of gdebi-like software that would, prior to installing the downloaded package, look for it in the repos and install it from there in case it be found.

Think of it as the equivalent of Windows' .exes, but improved.

---

### Post by salsafyren on 2007-05-17
> **Bou said:**
> 
Is harder than it ideally should. In my -possibly unfounded- opinion, there should be a standard installation package format that would work for ANY distro and would include the package itself AND all of its dependencies, except really big ones that any system with Linux should have installed or available like the GTK libraries, for example.

This kind of package should be in each program's webpage and installed through some kind of gdebi-like software that would, prior to installing the downloaded package, look for it in the repos and install it from there in case it be found.

Think of it as the equivalent of Windows' .exes, but improved.

zeroinstall, [http://0install.net/](http://0install.net/) does this.

It would be nice to make an automated solution, that downloaded a source package and its dependencies and made a zeroinstall feed for it. Then ALL distros would benefit from it.

---

### Post by Bou on 2007-05-17
> **salsafyren said:**
> zeroinstall, [http://0install.net/](http://0install.net/) does this.

Didn't even know somethink like that actually existed, but it seems great. But, I just downloaded a package and Ubuntu doesn't install it or anything, how's it supposed to work?

---

### Post by JNowka on 2007-05-17
> **jariku said:**
> Would a soft link do? That is, after all, "the UNIX way". :)

The file is a soft link.  What I did was copy a soft link to another place.  I didn't see the need to make a soft link to a soft link.

---

### Post by Iandefor on 2007-05-17
> **pmj said:**
> As long as you can exclude beta software, any other versions of software as long as one version is packaged, and anything that isn't completely IMPOSSIBLE to install, you're bound to be left with a very short list. Longer than one, mind you, since we're just a few people on a forum and not an entity with perfect knowledge of all Linux software in existence. A couple of things:

1. Did I say that beta/newer versions were discounted? SongBird and FileZilla did indeed have the caveat that they hadn't even hit alpha yet they went on the list. I never said I would discount newer versions of software, but newer versions are more of a moving target. Anywho, the amount of software that has been submitted is rather low and there haven't been any instances of "version *x* works but not *y*" yet.

2. The context in which I made the thread was that there was a lot of discussion on the Forums about whether or not proper package management was really a viable option for a desktop distribution ("In Windows I download the .exe, double-click, and it goes! In Linux I have to look at a terminal, maybe?!") and even whether or not it was viable to get a wide base of software working across a large number of related operating systems. My point in making the thread was that there most certainly *are* installation paths (not that difficult, either) for about 98+% of all software and that arguments for abandoning proper package management or giving up on Linux in frustration because there are large numbers of software that just will *not* work are usually specious.

>  You also completely ignore that many people DO want newer software than is packaged, DO want new software on their one year old installation, and DON'T want to compile it on their own, and they want it EASY. That is NOT available for us today. It just isn't. There is a difference between "ignoring" and "not addressing" I am fully aware of all of those facts, but the reality is that if a person absolutely cannot upgrade their installation or download the updated source and compile/install it (which consists of ./configure && make && sudo make install and grabbing build dependencies *in the repository and nicely named for your convenience* for the vast majority of software), or track down an updated .deb (usually a matter of Google), then I have to wonder if they're not looking so much for *easy* as they are for *something so mind-numbingly simple a chimpanzee could do it*. 

> **salsafyren said:**
> I completely agree. This thread is a waste of time and actually proves you (the one who opened this thread) think users are stupid because they want something that is not in the repositories.If you think it's a waste of time then you are free to not participate.

 I have to admit, I find it hard to respect the technical prowess of a user so afraid of their computer they're not willing to interact with it on anything other than a wizardly basis, but to assume I "think users are stupid because software isn't in the repositories" because I don't think it's unreasonable to expect someone who wants unpackaged software to *get it without recourse to a package* is somewhat of a leap.> The level of discussion in this forum is getting lower all the time because you are NOT acknowledging the weaknesses but instead cover your eyes and ears. At least, that's how it looks from the outside.It seems the level of discussion in this forum is getting lower all the time because some people aren't willing to acknowledge that what they want is not, in fact, Linux, but a free copy of Windows that doesn't get viruses, that they aren't actually interested in learning how their computer *works* but would rather someone know all that *for* them, make it work, and give away software that makes it work for free. Ubuntu is not that. If you want a drop-in replacement for Windows that doesn't get viruses, take a look at PC-BSD.

---

### Post by samjh on 2007-05-17
Anjuta 2.1.x

Not in Ubuntu repos.
Not in third-party repos (as far as I've searched, roughly several minutes on Google).
No pre-packaged .deb file (again, with several minutes of Google searching).
Cannot compile without excess effort because dependencies do not exist in Ubuntu repos (can be done by compiling dependencies by hand, but result is hugely variable from non-functional to somewhat unstable, and takes more time than expected of the averge non-advanced user).

That is only one example from recent personal experience.

Linux needs to improve.  It won't improve if one simply dismisses, belittles, or otherwise downplays any comparisons to dominant operating systems like Windows.  The sooner that the Linux community at large accept the fact that software packaging in Linux suffers from weaknesses, the sooner this area will improve.  What's wrong with Linux becoming "a free copy of Windows that doesn't get viruses"?  As long as it remains Linux in spirit, I see nothing wrong with that, personally.

---

### Post by aysiu on 2007-05-17
I think United Nations should bring about world peace, an end to hunger and homelessness, and a balanced budget for every nation.

I don't want to contribute in any way for this to happen, though. They should just do it.

Isn't my idea great?

All kidding aside, that's what a lot of posts in here sound like. "Oh, I don't want to *do* anything. I just want to demand that others do things the way I want instead of the way they want."

Well, I'm sorry, but no one has to listen to your ideas. Your ideas are not better than my ideas or Mark Shuttleworth's ideas or Bill Gates' ideas or Kevin Carmony's ideas. Everyone has ideas. Everyone thinks "If only they'd listen to me..."

Developers are motivated by two things mainly:
1. Personal interest/motivation
2. Money

If a developer wants to do something because she finds it interesting or somehow personally fulfilling, she'll do it for free. And if you want a developer to do something she's not interested in, you generally have to pay her to do it.

Announcing in a forum, "Ubuntu should do this! Ubuntu should do that!" doesn't make it so.

The only difference between Ubuntu and Windows/Mac OS X is that in Ubuntu you can put up bounties for certain features (pay money), use another Linux distro that's closer to your vision of how things should be, or fork it yourself if you don't like the way things are going. If you don't like the way Windows or Mac OS X are going... tough luck. You can't pay Windows developers bounties to implement features you like. You can't fork Windows legally. You can't even use a Windows-like "distro"--the closest there is is ReactOS. Same deal with Mac OS X.

---

### Post by Iandefor on 2007-05-17
> **samjh said:**
> Anjuta 2.1.x

Not in Ubuntu repos.
Not in third-party repos (as far as I've searched, roughly several minutes on Google).
No pre-packaged .deb file (again, with several minutes of Google searching).
Cannot compile without excess effort because dependencies do not exist in Ubuntu repos (can be done by compiling dependencies by hand, but result is hugely variable from non-functional to somewhat unstable, and takes more time than expected of the averge non-advanced user).

That is only one example from recent personal experience.

Linux needs to improve.  It won't improve if one simply dismisses, belittles, or otherwise downplays any comparisons to dominant operating systems like Windows.  The sooner that the Linux community at large accept the fact that software packaging in Linux suffers from weaknesses, the sooner this area will improve.  What's wrong with Linux becoming "a free copy of Windows that doesn't get viruses"?  As long as it remains Linux in spirit, I see nothing wrong with that, personally. What do you mean by Linux? Ubuntu, Fedora, Slackware? The kernel? The kernel and the GNU implementations of UNIX utilities?

---

### Post by Adamant1988 on 2007-05-17
mugshot packages don't exist for 32-bit feisty at the moment, and Flock packages don't exist for feisty AFAIK.  Several games including planeshift, etc.

---

### Post by Iandefor on 2007-05-17
> **Adamant1988 said:**
> mugshot packages don't exist for 32-bit feisty at the moment, and Flock packages don't exist for feisty AFAIK.  Several games including planeshift, etc. Mugshot has been packaged for a great number of distributions, such as RHEL, Debian, OpenSUSE, FreeBSD, and [the last three releases of Ubuntu]("http://developer.mugshot.org/wiki/Downloads#Ubuntu").

Flock is most certainly installable since it follows the Firefox tradition of leaving everything in one folder. Extract it into /opt, add a menu entry with Alacarte, and you're done. In fact, you don't even need to do that. I'm running it out of a folder on my desktop right now.

So it's not prepackaged but it's certainly installable.

---

### Post by pmj on 2007-05-18
> **Iandefor said:**
> A couple of things:

1. Did I say that beta/newer versions were discounted? SongBird and FileZilla did indeed have the caveat that they hadn't even hit alpha yet they went on the list. I never said I would discount newer versions of software, but newer versions are more of a moving target. Anywho, the amount of software that has been submitted is rather low and there haven't been any instances of "version *x* works but not *y*" yet.
Pretty much all of Gnome. Pretty much all of KDE. Want that new media player with bug fixes and new features? You gotta upgrade your whole distribution, unless you are *really* skilled. There, you can now add a ton of software to your list.


> **Iandefor said:**
> There is a difference between "ignoring" and "not addressing" I am fully aware of all of those facts, but the reality is that if a person absolutely cannot upgrade their installation or download the updated source and compile/install it (which consists of ./configure && make && sudo make install and grabbing build dependencies *in the repository and nicely named for your convenience* for the vast majority of software), or track down an updated .deb (usually a matter of Google), then I have to wonder if they're not looking so much for *easy* as they are for *something so mind-numbingly simple a chimpanzee could do it*. 
In other words, Linux is more difficult and that's the way you like it, and if you don't you're an idiot.


> **Iandefor said:**
>  I have to admit, I find it hard to respect the technical prowess of a user so afraid of their computer they're not willing to interact with it on anything other than a wizardly basis
Your (false) assumptions about the people you're talking to here says a lot about you.

> **Iandefor said:**
> some people aren't willing to acknowledge that what they want is not, in fact, Linux, but a free copy of Windows that doesn't get viruses, that they aren't actually interested in learning how their computer *works* but would rather someone know all that *for* them, make it work, and give away software that makes it work for free. Ubuntu is not that. If you want a drop-in replacement for Windows that doesn't get viruses, take a look at PC-BSD.
Again, nothing but assumptions and thinly veiled insults.

---

### Post by pmj on 2007-05-18
> **aysiu said:**
> I think United Nations should bring about world peace, an end to hunger and homelessness, and a balanced budget for every nation.

I don't want to contribute in any way for this to happen, though. They should just do it.

Isn't my idea great?

All kidding aside, that's what a lot of posts in here sound like. "Oh, I don't want to *do* anything. I just want to demand that others do things the way I want instead of the way they want."

Well, I'm sorry, but no one has to listen to your ideas. Your ideas are not better than my ideas or Mark Shuttleworth's ideas or Bill Gates' ideas or Kevin Carmony's ideas. Everyone has ideas. Everyone thinks "If only they'd listen to me..."

Developers are motivated by two things mainly:
1. Personal interest/motivation
2. Money

If a developer wants to do something because she finds it interesting or somehow personally fulfilling, she'll do it for free. And if you want a developer to do something she's not interested in, you generally have to pay her to do it.

Announcing in a forum, "Ubuntu should do this! Ubuntu should do that!" doesn't make it so.

The only difference between Ubuntu and Windows/Mac OS X is that in Ubuntu you can put up bounties for certain features (pay money), use another Linux distro that's closer to your vision of how things should be, or fork it yourself if you don't like the way things are going. If you don't like the way Windows or Mac OS X are going... tough luck. You can't pay Windows developers bounties to implement features you like. You can't fork Windows legally. You can't even use a Windows-like "distro"--the closest there is is ReactOS. Same deal with Mac OS X.
You are absolutely right. You should probably go tell yourself this in all of your IDEA threads. And every other time you ever suggested or discussed something. "Shut up". Words to live by. Unless you pay of course.

---

### Post by aysiu on 2007-05-18
> **pmj said:**
> You are absolutely right. You should probably go tell yourself this in all of your IDEA threads. And every other time you ever suggested or discussed something. "Shut up". Words to live by. Unless you pay of course.
There's a big difference between proposing an idea and demanding something be done, especially if it's something that can't be done by Ubuntu developers. There are also proper channels for proposing ideas. And if ideas get rejected, don't make it sound as if the sky is falling. As a matter of fact--looking through your posts in this thread--I haven't seen you propose a single feasible idea... not even one the Ubuntu developers could implement, not even one all the Linux developers cooperating together could implement. So why are you bagging on ideas? You haven't even proposed one. An idea is something that can be implemented. Just bagging on how Ubuntu doesn't suit your software needs is pointless.

You're also missing the point of Iandefor's thread, which is not to say that the package management will solve every user's software installation problems. The point is that declarations that there is a lot of software out there that's impossible to install are exaggerated. Yes, there is *some* software that's "impossible" or extremely difficult to install. The vast majority of software is not, however. That's the only point of the thread.

If you asked Iandefor, "Could software installation be improved in Ubuntu?" or "Would you like to see more packages available in the Universe and Multiverse repositories?" do you think the response would be "Ubuntu is perfect right now" or "Of course!"? It seems to me you just came in here wanting to pick a fight... and not really proposing any practical solutions. If you have one, create an [IDEA] thread and draw up a blueprint or specification.

---

### Post by pmj on 2007-05-18
> **aysiu said:**
> There's a big difference between proposing an idea and demanding something be done, especially if it's something that can't be done by Ubuntu developers.
I'm arguing with people who claim that the problem with software installation either doesn't exist, or doesn't need fixing. I'm not demanding anything of anyone. There is also no requirement of providing an argument of your own in order to poke holes in someone else's.

> **aysiu said:**
> You're also missing the point of Iandefor's thread, which is not to say that the package management will solve every user's software installation problems. The point is that declarations that there is a lot of software out there that's impossible to install are exaggerated. Yes, there is some software that's "impossible" or extremely difficult to install. The vast majority of software is not, however. That's the only point of the thread.
If you read the thread, you will notice that Iandefor is strongly against any new system to install software. This thread is used an argument in the ongoing software installation debate. That is the point of this thread.

---

### Post by Iandefor on 2007-05-18
> **pmj said:**
> Pretty much all of Gnome. Pretty much all of KDE. Want that new media player with bug fixes and new features? You gotta upgrade your whole distribution, unless you are *really* skilled. There, you can now add a ton of software to your list. I doubt it would take a full distribution upgrade. Probably a rebuild of your current DE if the new package is *that* different, but I really haven't had any experiences grabbing software from a late-in-development branch/new release and compiling it on the (old) stable except for recompiling the metacity in GNOME 2.15.90something on GNOME 2.14. The worst I needed to do was an apt-get build-dep metacity. I'll concede the point about DE's for the moment.
> In other words, Linux is more difficult and that's the way you like it, and if you don't you're an idiot. You must have misread. I merely contested the idea that compiling software is generally difficult. I'm also interested in knowing how the act of typing 35 or so characters (./configure && make && make install) is now considered "difficult"?> 
Your (false) assumptions about the people you're talking to here says a lot about you. Did I say I was referencing someone to whom I was talking?> Again, nothing but assumptions and thinly veiled insults. Your ability to conjure hidden meanings and hostilities where none were before is positively a*mazing*. How *do* you do it? 

The level of ease people demand from Ubuntu *is* quite extraordinary and the vagueness of the demands is nothing less than shocking. "Make it better!" "How?" "Make it better!" 

When people *do* finally conjure an idea up about how they want it to become better it almost always makes reference to Windows and it almost always is along the lines of standardized base/buildsystem/package management system/packagesets/default spins, Windows-like package management, or something like that. 

I speak from long experience in discussions with users on how to make Ubuntu "better". People do *not*, in general, actually *want* a Linux kernel with GNU utilities and a centralized package management system for their distribution or a SysV-style init system, a GPL'ed kernel, human-readable config files, dpkg-based package-management systems, string-manipulation tools and pipes or the ability to compile their very own system from the ground up. I know *I* didn't have any of that in mind when I first installed a LInux. I thought "OpenOffice and Firefox on the install disk and no licensing fee? Sweet!" and it's that kind of thing that usually gets people to at least try it. 

My experience has overwhelmingly been that end-users who switch aren't usually interested in the fact that they now have a UNIX-like GNU/Linux operating system and aren't interested in learning what that means and how it impacts the way they use it. They *do* care, however, when they go looking for the control panel and can't find it and find out that for some things, a CLI just makes more sense. In fact, they get *quite* upset. What they want is Windows, not Linux.

Just because I think that some people aren't aware of exactly what they want does not mean that I'm insulting them.
> If you read the thread, you will notice that Iandefor is strongly against any new system to install software. This thread is used an argument in the ongoing software installation debate. That is the point of this thread. I'm strongly against reinventing the wheel, that is true. Linux software is developed for Linux and so it is generally installable on Linux. *That* is my point.

> I'm arguing with people who claim that the problem with software installation either doesn't exist, or doesn't need fixing. I'm not demanding anything of anyone. There is also no requirement of providing an argument of your own in order to poke holes in someone else's. Actually, I rather think that if you want to take a negative statement and oppose it with a positive statement, you need some kind of line of reasoning.

---

### Post by pmj on 2007-05-18
> **Iandefor said:**
> I have to admit, I find it hard to respect the technical prowess of a user so afraid of their computer they're not willing to interact with it on anything other than a wizardly basis
> **Iandefor said:**
> Did I say I was referencing someone to whom I was talking?
You said this in response to "think users are stupid because they want something that is not in the repositories". I belong to the group that wants things not in repositories (I have 73(!) subfolders in my CVS/SVN folder), the group you admitted you had no respect for. Or did that change since I now revealed that I am, in fact, capable of compiling software?

> **Iandefor said:**
> Your ability to conjure hidden meanings and hostilities where none were before is positively a*mazing*. How *do* you do it? .
Yes, how *do* I do it? I could go and quote every derogatory statement towards new users you've made in this thread, but it would be pointless. You, me and any onlooking "chimpanzee" knows what you have said.

I'm afraid this will have to be the last post I make in this thread. You simply write too little with too many words, Iandefor, and I'm finding it very tiresome to go through.

---

### Post by Iandefor on 2007-05-18
> **pmj said:**
> You said this in response to "think users are stupid because they want something that is not in the repositories". I belong to the group that wants things not in repositories (I have 73(!) subfolders in my CVS/SVN folder), the group you admitted you had no respect for. Or did that change since I now revealed that I am, in fact, capable of compiling software? No, I admitted I had *difficulty* respecting the *technical prowess* of users who were too afraid to touch anything not resembling a wizard. There is a difference between respecting someone's ability at something and respecting them themselves. Also, look at the statement to which I was responding. I was *refuting* the statement that I thought users who wanted software outside the repositories to be stupid. Must I quote myself? I think I quite clearly said the opposite- a user *not willing to go outside of the repositories to get software they want is liable to be lacking in technical skill:* > I find it hard to respect the technical prowess of a user so afraid of their computer they're not willing to interact with it on anything other than a wizardly basis, but to assume I "think users are stupid because software isn't in the repositories" because **I don't think it's unreasonable to expect someone who wants unpackaged software to *get it without recourse to a package* is somewhat of a leap.*** By your own admission* you *cannot* belong to this group because you keep CVS/SVN checkouts (unless you keep them for some reason other than compiling/hacking that I cannot fathom), by the way.> Yes, how *do* I do it? I could go and quote every derogatory statement towards new users you've made in this thread, but it would be pointless. You, me and any onlooking "chimpanzee" knows what you have said. Since when have any chimpanzees been onlooking? Perhaps you reference this? > I have to wonder if they're not looking so much for *easy* as they are for *something so mind-numbingly simple a chimpanzee could do it*. 
 The wonderful thing about that sentence is that it does not actually *liken* anyone to a chimpanzee and there is no actual* implication *of likening, either. At worst, it could be said to be a tastelessly extreme exaggeration of the efforts to simplify UI's on the part of some people.
> I'm afraid this will have to be the last post I make in this thread. You simply write too little with too many words, Iandefor, and I'm finding it very tiresome to go through. I would be lying if I were to say that I were sorry to see you leave the thread.

---

### Post by awakatanka on 2007-05-18
If it is not in the repo you can mostly install it with ./configure etc. But if you have to do that to much because you want bleeding edge you better move to Gentoo. Sometimes someone made a deb and a repo line to get it, but how can new people trust it when the first thing they here don't trust software outside the repo's. Everything outside the repo's can bring you system to risk. Contradicting messages for new starting users.

---

### Post by ReiKn on 2007-05-18
> **Adamant1988 said:**
> mugshot packages don't exist for 32-bit feisty at the moment, and Flock packages don't exist for feisty AFAIK.  Several games including planeshift, etc.

[http://www.getdeb.net/release.php?id=891](http://www.getdeb.net/release.php?id=891) <- getdeb.net has also flock packages for feisty.

---

### Post by pmj on 2007-05-18
> **Iandefor said:**
> I think I quite clearly said the opposite- a user *not willing to go outside of the repositories to get software they want is liable to be lacking in technical skill:* * By your own admission* you *cannot* belong to this group because you keep CVS/SVN checkouts (unless you keep them for some reason other than compiling/hacking that I cannot fathom), by the way.
I do this because I must, not because I enjoy it, and I would stop the second I didn't have to do it anymore. Thus I belong to the group you insulted. Still, whether I belong to it or not is irrelevant; you had no way of knowing at the time you made that statement.

Talking about compiling software, you greatly exaggerate how easy it is. I find it is very rarely as easy as "./configure && make && make install". And as someone who has spent several hours trying to help a newbie to compile a piece of software he relied on, and ultimately failing, I *know* it isn't easy for everyone. Even newbies deserve a usable computer. What they do not deserve is being told to go back to Windows when they point out a problem they're having.

> **Iandefor said:**
>  The wonderful thing about that sentence is that it does not actually *liken* anyone to a chimpanzee and there is no actual* implication *of likening, either. At worst, it could be said to be a tastelessly extreme exaggeration of the efforts to simplify UI's on the part of some people.
Like I said, thinly veiled. And you do it a lot. I'm glad you agree.

> **Iandefor said:**
>  I would be lying if I were to say that I were sorry to see you leave the thread.
At least you didn't spend two long paragraphs saying absolutely nothing this time. I'd like it if you were to cut out all the italics as well, but I guess you can't get everything.

---

### Post by zugu on 2007-05-18
> **ReiKn said:**
> [http://www.getdeb.net/release.php?id=891](http://www.getdeb.net/release.php?id=891) <- getdeb.net has also flock packages for feisty.

When user A is complaining about the sad state of backports, user B is pointing user A to Getdeb. When user A still can't find what he/she needs on Getdeb, user B replies "oh, I never ran into that specific problem" or "I don't know about you, but Ubuntu is the perfect OS for me, never had any problems with it" or "but why do you need that specific application? If I can live without it, you should, too", or "did you try *insert inferior equivalent* ?".

This attitude can be seen throughout all these forums, in topics concerning all kinds of technical issues, not only repositories or backports availability.

And it saddens me greatly. I think it's time we acknowledge the real problems Ubuntu has. It's time some of us stop pretending they can't see them.

---

### Post by ReiKn on 2007-05-18
> **zugu said:**
> When user A is complaining about the sad state of backports, user B is pointing user A to Getdeb. When user A still can't find what he/she needs on Getdeb, user B replies "oh, I never ran into that specific problem" or "I don't know about you, but Ubuntu is the perfect OS for me, never had any problems with it" or "but why do you need that specific application? If I can live without it, you should, too", or "did you try *insert inferior equivalent* ?".

This attitude can be seen throughout all these forums, in topics concerning all kinds of technical issues, not only repositories or backports availability.

And it saddens me greatly. I think it's time we acknowledge the real problems Ubuntu has. It's time some of us stop pretending they can't see them.

I for myself am not saying that there aren't any problems with the software installation system. I just wish the examples posted in this thread would be checked from at least the most obvious sources. Instead of "as far as I know" "as far as I checked" should be used. 

The positive thing I've been noticing lately about deb packages is that more and more software makers have started to package for ubuntu themselves.

I agree with your criticism although in my opinion you were barking up the wrong tree here. It's indeed annoying to see answers like "why do you need that specific application?" instead of helping the poster with his problem or just shutting up.

But then again.. for how many alternative programs for approximately the same task the packages should be officially made, provided, supported and distributed by ubuntu? Why shouldn't it be also the software maintainers concern to provide an ubuntu package if he/she wants the software to gain any popularity among the ever-growing ubuntu users crowd?

---

### Post by saulgoode on 2007-05-18
Like Pmj, I have several dozen programs that I build from source. In fact, for most of them I have created packages rather than use "sudo make install" (this is so I can keep track of what packages I have installed and more easily remove/upgrade them). 

I do not contribute my packages to a repository because that software is still in development. If I were to publish a package for a development version of a program it would be with the understanding that any problems encountered with executing the program should have to be reported to me. It is unfair to the project developers to expect them to investigate bugs that might very well have been introduced by my packaging.

Anyone who is using a development version of a program should either have the capacity to compile it himself or be working with such people (which is basically the role of the distribution package maintainers). If there is nobody willing to maintain a package and be a focal point for bug reporting, it is a disservice to the project's developers to produce that package.

In short, not all software should be available in packaged form. This is not elitism or an insult to non-technical persons, it is simply the way most Free Software is developed.

---

### Post by samjh on 2007-05-18
> **Iandefor said:**
> What do you mean by Linux? Ubuntu, Fedora, Slackware? The kernel? The kernel and the GNU implementations of UNIX utilities?

Just what the average computer-literate user thinks when referring to Linux.  In case this cannot be comprehended by context of my post - it means well known Linux distributions.

---

### Post by 3rdalbum on 2007-05-18
What about non-x86 architectures that are supported by Ubuntu?

I don't believe anyone has managed to compile Songbird on PowerPC.

---

### Post by ReiKn on 2007-05-18
> **3rdalbum said:**
> What about non-x86 architectures that are supported by Ubuntu?

I don't believe anyone has managed to compile Songbird on PowerPC.

I think the key words here are "supported by Ubuntu". The non-x86 architectures that are supported by ubuntu have their supported repositories full of software which is supported by ubuntu. Software outside these isn't supported. Should it be songbird maintainers responsibility to provide that package or ubuntus? What's your opinion on this? Should ubuntu provide photoshop for ubuntu or adobe?

Songbird is one of those programs I'd like to see officially supported bu ubuntu.. but clearly all emerging software can't be. Some kind of a common package management system between distros would of course be cool and is something worth hoping for. Like that software maintainers wouldn't have to worry about different distros and such.

---

### Post by strixy on 2007-05-20
I have found three software packages maintained in the repo's by the Ubuntu community that don't work.

The default torrent clients in 7.04 don't work by default, straight out of the repositories, on the AMD64 arch w/ Feisty.

For example, Azureus requires Sun Java 1.6. The default with 7.04 is 1.5. If you install Azureus out of the repositories it doesn't install Java 1.6.

Anyone care to tackle that one? Or maybe Ktorrent which has a crashing problem (overrun?) that has since been fixed with the new release. The new release, however, isn't in the repos yet.

Deluge doesn't work, but I haven't researched the problem with that one yet.

Any of them you can get working, but not "out of the box" - as it were.

Anyway, there are my three examples.

It's nice to see wine for AMD64 now coming online.

---

### Post by Haegin on 2007-06-01
Firstly this thread made me think. Here are the results: [http://ubuntuforums.org/showthread.php?p=2761208#post2761208](http://ubuntuforums.org/showthread.php?p=2761208#post2761208)

> **zugu said:**
> When user A is complaining about the sad state of backports, user B is pointing user A to Getdeb. When user A still can't find what he/she needs on Getdeb, user B replies "oh, I never ran into that specific problem" or "I don't know about you, but Ubuntu is the perfect OS for me, never had any problems with it" or "but why do you need that specific application? If I can live without it, you should, too", or "did you try *insert inferior equivalent* ?".

This attitude can be seen throughout all these forums, in topics concerning all kinds of technical issues, not only repositories or backports availability.

And it saddens me greatly. I think it's time we acknowledge the real problems Ubuntu has. It's time some of us stop pretending they can't see them.

I am sorry this saddens you but often user B doesn't know any better and simply wishes to help user A in whichever way (s)he can. If user A wanted a bit torrent program to download one ISO (for example) and cant find deluge in the repositories and user B recommends the official bit torrent client this will probably satisfy user A's immediate need. If user A needs a better program or particularly wanted to use deluge they are welcome to carry on asking questions (either to user B or to user C, D and E as they wish).

[QUOTE=pmj]
Yes, how do I do it? I could go and quote every derogatory statement towards new users you've made in this thread, but it would be pointless. You, me and any onlooking "chimpanzee" knows what you have said.
[/QUOTE]

I don't think he was getting at new users, just users who demand packaged programs and ignore people who try and help them learn how to compile, point them to an alternative or help them in any other way.

---

### Post by Bou on 2007-06-01
As far as I know, [gendesign]("http://ubuntuforums.org/showthread.php?t=459995") is impossible to install correctly in Ubuntu. I would love someone to prove me wrong, though.

---

