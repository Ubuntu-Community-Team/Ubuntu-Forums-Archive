---
title: "Freedroid RPG"
date: 2005-06-01
forum: Ubuntu Backports
---

### Post by ChamPro on 2005-06-01
The Freedroid Classic game is already in the repositories, but the much newer and more graphically pleasing [Freedroid RPG](http://freedroid.sourceforge.net/)  would be nice to add.

Since there's doesn't exist any packages already for this game, we don't have to worry about previous versions. And there doesn't even seem to be DEBs for the newest version of the game that's been released.

Since the game is OpenGL based, there are a number of pre-reqs.

On a different note, I've been playing the Windows version. I'm hooked. Kinda Diablo-like with niftier graphics. Not remembering to save often is troublesome and not having more than one save slot per game is a little annoying. But I guess it does add a challenge.

---

### Post by Dokramu on 2005-11-19
how can I play it? I have the game in my computer, but dunno how 2 run it

---

### Post by Cameron on 2006-04-17
I am trying to get Freedroid RPG to run on Linux.

I'm using the current **developent version rc3 (from August 2005)** When I ran the game it said it had a couple of dependices.

OK I got the first two but It currently says it needs *libopengl32*. 

I cannot find this amongst the repositories.  I would really like to get Freedroid RPG running without having to download another version of the game. 

Cameron 8)

---

### Post by FictionPimp on 2006-08-01
Did anyone ever get a deb of this made?

---

### Post by samichx on 2007-08-03
Freedroidrpg will be in the repos as of gutsy, If you are slightly impatient you can grab the deb at [http://packages.ubuntu.com/gutsy/games/freedroidrpg](http://packages.ubuntu.com/gutsy/games/freedroidrpg) and don't forget the data deb and any extra addons that you want.

---

### Post by stedevil on 2007-11-19
Im trying to compile the 0.10.3 release in Ubuntu Gutsy 7.10, but I run into problems with the ./configure script. It fails to detect that I have OpenGL properly installed (at least according to this website I have everything required [http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development) )

But yet I get the following message during the config
```

checking for OpenGL library... no
checking for openGL libraries... no
configure: WARNING:  openGL libs not found!
----------------------------------------------------------------------
WARNING: openGL libraries/headers could not be found.
==> Therefore we are building freedroid only with SDL-graphics support.
    No 3D acceleration will be available.
    It is recommended to install openGL.

(if compiling on Darwin, try './configure --with-apple-opengl-framework')
----------------------------------------------------------------------

```

Anybody know how to fix this?

BTW For anybody else interested in compiling from source (to not be annoyed at old bugs since long fixed) you will need to also install these libs (and possibly some more if this is your first compile).

Required: libsdl-image1.2-dev libsdl-net1.2-dev libsdl-mixer1.2-dev
Optional: libgtk1.2-dev 
OpenGL: The correct dev package for your GLX driver (In my case nvidia-glx-new-dev but your card and driver determines what you need)

---

### Post by stedevil on 2007-11-21
Got ahold of the developers on IRC and we managed to track this problem down to being a bad symlink (some package bug for the nvidia-glx-new-dev where a symling remained pointing at an old binary).

Procedure to fix if the same happens to you

1) Find any broken symlinks

ls -l /usr/lib/libGL*

...
lrwxrwxrwx 1 root root       18 2007-08-23 10:26 /usr/lib/libGL.so -> libGL.so.100.14.11
lrwxrwxrwx 1 root root       18 2007-11-02 10:34 /usr/lib/libGL.so.1 -> libGL.so.100.14.19
-rw-r--r-- 1 root root   605788 2007-11-02 02:22 /usr/lib/libGL.so.100.14.19
...

In my case the one ending with .11 was broken (since the actual installed driver was .19 like in the second line)

so the fix in my case was

sudo rm /usr/lib/libGL.so
sudo ln -s /usr/lib/libGL.so.100.14.19  /usr/lib/libGL.so

---

### Post by stedevil on 2007-11-22
BTW FreedroidRPG 0.10.3 exsists as a debian package
[http://packages.debian.org/unstable/games/freedroidrpg](http://packages.debian.org/unstable/games/freedroidrpg)

It is an alternative for people who want to play an up to date version of the game without compiling it them selves. However I do recommend compiling from source though because the Debian package (and thus likely the Ubuntu package that comes from it) is a modified one and has it's own quirks and bugs not present in the original sources. It also means that any bugs and problems you run into should be reported to the debian package maintainer, not the creators of freedroidRPG unless you verify that the problem also exists when you compile from source.

---

### Post by stedevil on 2007-11-29
CVS has apparently been quite flaky lately on SF so FreedroidRPG was just moved over to SVN instead. sudo apt-get install subversion and 

svn co [https://freedroid.svn.sourceforge.net/svnroot/freedroid](https://freedroid.svn.sourceforge.net/svnroot/freedroid) freedroid

Then "sudo apt-get install automake" if you dont have it already and  cd to the freedroid dir and do
./autogen.sh
./configure
make

Then either just make install or cd to the src/ dir and ./freedroidRPG to run the latest and greatest version. Usually it wont explode in your face ;)

---

### Post by stedevil on 2009-01-10
For up to date instructions for how to get the latest release or developer version of this game running under Ubuntu, check out this post. :)

[http://ubuntuforums.org/showthread.php?p=6127097#post6127097](http://ubuntuforums.org/showthread.php?p=6127097#post6127097)

---

### Post by anfractuosities on 2009-01-24
> **stedevil said:**
> For up to date instructions for how to get the latest release or developer version of this game running under Ubuntu, check out this post. :)

[http://ubuntuforums.org/showthread.php?p=6127097#post6127097](http://ubuntuforums.org/showthread.php?p=6127097#post6127097)

Will installing the new version overwrite my saved game?

---

### Post by KIAaze on 2009-01-24
The Freedroid developers will probably be the most qualified to answer this question. Try to look for a mailing list, e-mail address or IRC channel on their website.

Why not just back up the saved games (probably in ~/.freedroid or something like that) and see for yourself?

edit: I think it's unlikely that installing from source will overwrite your existing saved games.
However, it's quite possible that you won't be able to load them due to changed saved game formats.

---

### Post by stedevil on 2009-02-14
> **anfractuosities said:**
> Will installing the new version overwrite my saved game?

No, it will not overwrite your savegame. However we dont have savegame compability between versions yet. Too much is changing between versions yet. :)

---

### Post by stinkyfishheadisred on 2009-08-25
The most up-to-date way to install this game is to click on: [SIZE=3][COLOR=Teal][apt:freedroidrpg](apt:freedroidrpg)[/COLOR][/SIZE] .  If you are running Ubuntu this ought to bring up the menu to install the software directly through subversion.

---

### Post by stedevil on 2009-08-29
Well, some people are more interested in getting an up to date PACKAGE of a software not an up to date way of getting an outdated version of that package. ;)

---

### Post by KIAaze on 2009-08-31
Well, it sure sounded like a way to get the latest package:
> If you are running Ubuntu this ought to bring up the menu to install the software directly through subversion.
But I haven't heard of apt-get having gotten such a powerful new feature yet. :)

---

