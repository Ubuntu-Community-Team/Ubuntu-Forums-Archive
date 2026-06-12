---
title: "GiftWrap 0.1 release"
date: 2009-05-28
forum: The Cafe
---

### Post by Vadi on 2009-05-28
[CENTER][SIZE="4"][Video]("http://www.youtube.com/watch?v=JEb95mG36UU") | [Download]("http://giftwrap.tuxfamily.org/index.php?pages/download") [/SIZE][/CENTER]

[SIZE="3"]What is GiftWrap?[/SIZE]

GiftWrap is a **hassle-free way to create Ubuntu packages**. It is designed for anyone who deals with distributing software - be it theme artists, software developers, or anyone else. In the future, it will support updating of existing packages, uploading to PPA's split packages and more.

It stems from the (now dead) Deb Creator project, with a complete rewrite planned in the near future.

[SIZE="3"]What is planned?[/SIZE]

A lot of things, including a redesign of the interface and a host of improved functionality. See the [roadmap]("http://giftwrap.wikia.com/wiki/Roadmap") a more detailed view, or just subscribe to the news feed to stay updated.

[SIZE="3"]How can I help?[/SIZE]

See the [contribute]("http://giftwrap.tuxfamily.org/index.php?pages/contribute") page. Any help is welcome, thanks!
[SIZE="3"]
[Digg it]("http://digg.com/linux_unix/GiftWrap_helps_you_create_debs")![/SIZE]

---

### Post by ghindo on 2009-05-28
Very, very interesting.  I may have to give this a whirl and package Rubyripper.

Thanks for posting this!

---

### Post by Vadi on 2009-05-28
Yep. Give it a go.

---

### Post by pelle.k on 2009-05-29
I didn't see you add the build-dep in giftwrapper (youtube demonstration). Also, i build my packages in a chroot (pbuilder) as to not forget any build-deps already installed on my system.
So it worries me a little of what people may put on their PPA. But that goes for everyone not packaging in a chroot such as pbuilder, not just giftwrapper.
Other than that - great initiative.

---

### Post by Vadi on 2009-05-29
Yes, I skipped adding the missing library in the youtube vid - thinking now maybe I should've done it, but I was aiming for a quick overview.

It doesn't do chroots yet, but that is obviously planned as I'm aiming here to make a high-quality program, not a graphical checkinstall.

---

### Post by Bou on 2009-05-29
Hi Vadi,

I learnt about Giftwrap this morning and have been thinking about it. I love the idea and would like to propose a simpler interface, since wizard types were never my thing:

[IMG]http://imgur.com/8gFXp.png[/IMG]

What do you think? Clicking on the "source button" would trigger a typical open dialogue, where you could select archives or folders. It would also allow us to use "open with giftwrap" with archives.

All the "next-next-next" steps shouldn't be necessary either; once you've entered all necessary data, the "generate" button should become active and not require any further action.

---

### Post by Bou on 2009-05-29
Once you click "generate", there could be a progress dialogue:

[IMG]http://img216.imageshack.us/img216/3736/pantallazo1i.png[/IMG]

In case of missing a dependency, giftwrap would ask for permission to install it (i.e. no hunting packages down the web):

[IMG]http://img216.imageshack.us/img216/672/pantallazo2v.png[/IMG]

Once the package is created, giftwrap (through gdebi integration) would offer you to install it:

[IMG]http://img36.imageshack.us/img36/7449/pantallazo3.png[/IMG]

---

### Post by Bou on 2009-05-29
Other random ideas would be:

-Search gnomefiles in order to fill necessary data automatically.
-Uninstall installed dependencies automatically once the package is created, to keep the system clean.
-File-roller integration: If file-roller detects certain characteristics in a compressed file, it could trigger a dialogue: "it seems this file contains softare. Do you want to create an installable package from it?"

That would make installing apps as easy as double-clicking a file and following the instructions.

---

### Post by Vadi on 2009-05-29
Yes, wizards aren't my thing too (interface redesign is being worked on next).

I love your proposal here, but it needs more thought about the more general stuff - come by on the [IRC]("http://giftwrap.tuxfamily.org/index.php?contact").

There is also a wiki available: [http://giftwrap.wikia.com](http://giftwrap.wikia.com)

---

### Post by Vadi on 2009-05-29
0.11 is in the PPA: fixed a missing dependency on dh-make and an icon from the Applications menu.

---

### Post by Tibuda on 2009-05-29
This is interesting. I tried to create a deb once, and it was a pain. It is not hard, but you have to figure out many things. I'll keep an eye on this.

I also agree wizards are annoying.

---

### Post by pt123 on 2009-05-29
> **Bou said:**
> Once you click "generate", there could be a progress dialogue:

[IMG]http://img216.imageshack.us/img216/3736/pantallazo1i.png[/IMG]


Would possible have a deb file for this program Paperbox, have been looking for one.
Thanks

---

### Post by ghindo on 2009-05-29
> **pt123 said:**
> Would possible have a deb file for this program Paperbox, have been looking for one.
ThanksNow you can just use GiftWrap to make one :)

---

### Post by hero1900 on 2009-05-30
thank you very much for this info
:popcorn:

---

### Post by Technophobia on 2009-06-10
Thank you Vadi for this great software, I can't wait to use it.

---

### Post by Vadi on 2009-06-17
Just to note - [https://launchpad.net/~giftwrap-users](https://launchpad.net/~giftwrap-users) team has been opened, and *giftwrap-users@lists.launchpad.net* is the mailing list to use for any support / discussion and etc. :)

---

### Post by Ubuntiac on 2009-07-25
Hey Vadi,

This has to be THE idea, who's time has come for Ubuntu. The number of times that I've heard that the main thing holding Ubuntu back is the speed of which we can package new software for testing.

Can this be used to package a straight binary (ie without any compiling). I'm making a game in Blender, which precompiles a binary straight from the app. I just want something that lets me browse for the binary, put in the name, dependencies, license etc and click generate.

Would this be possible with GiftWrap? Every packaging guide I ever see assumes I want to learn all about make files, source packages and worse. I just want to share a binary with dependencies, a menu entry and a description!


EDIT: Well, I tried it... saved my binary in a folder in the format packagename-version and .tar.gz compressed it for giftwrap. Unfortunately I got:

dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package mr-cubie
dpkg-buildpackage: source version 0.1-1
dpkg-buildpackage: source changed by Ubuntiac <please@dontspamme.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/user/.giftwrap/mr-cubie/mr-cubie-0.1'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/user/.giftwrap/mr-cubie/mr-cubie-0.1'
make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2


Any way around this?

---

### Post by xuCGC002 on 2009-07-25
Why didn't anyone else make it this easy to package .DEBs?

Amazing, I'll try it out tomorrow morning.

---

### Post by Ubuntiac on 2009-07-25
> **xuCGC002 said:**
> Why didn't anyone else make it this easy to package .DEBs?

Better yet: Why hasn't everyone heard of this, despitew the fact its been out (nearly) 2 months? Deb-a-day? Planet Gnome? Plaet KDE? Phoronix? All of the Ubuntu / Debian podcasts?

This really should be on them all.

Well, if it works the way *I* want, anyway! ;)

---

### Post by xuCGC002 on 2009-07-25
I tried compiling DOOM Legacy 1.42, but it keeps saying:
> Unable to detect the top source folder in the archive. This should be something like <name>-<version>.

I'm not sure what to do.

EDIT: The top source folder is doomlegacy_142_src.

---

### Post by Ubuntiac on 2009-07-25
Maybe try changing the folder name to: DoomLegacy-1.42

Just a guess...

---

### Post by 569874123 on 2009-08-08
Very nice project. Is it still being developed?

---

### Post by Vadi on 2009-08-08
Yep.

---

### Post by Ubuntiac on 2009-08-09
So uh,

Can GiftWrap be used to package a straight binary?

---

### Post by Vadi on 2009-08-10
Not yet.

---

### Post by Ubuntiac on 2009-09-03
Can Giftwrap do packages that normally compile with:

a) cmake (eg koffice apps)
b) Scons (eg Blender)

? Appologies for if this is obvious. Whats attractive about giftwrap is that it's usable by someone who doesn't know how to compile. ;) Thanks again for an awesome utility that *everyone* should know about!

---

### Post by Locke_99GS on 2009-10-11
> **Ubuntiac said:**
> So uh,

Can GiftWrap be used to package a straight binary?

Use *epm* for that.

---

### Post by hoppipolla on 2009-10-11
> **Vadi said:**
> [CENTER][SIZE="4"][Video]("http://www.youtube.com/watch?v=JEb95mG36UU") | [Download]("http://giftwrap.tuxfamily.org/index.php?pages/download") [/SIZE][/CENTER]

[SIZE="3"]What is GiftWrap?[/SIZE]

GiftWrap is a **hassle-free way to create Ubuntu packages**. It is designed for anyone who deals with distributing software - be it theme artists, software developers, or anyone else. In the future, it will support updating of existing packages, uploading to PPA's split packages and more.

It stems from the (now dead) Deb Creator project, with a complete rewrite planned in the near future.

[SIZE="3"]What is planned?[/SIZE]

A lot of things, including a redesign of the interface and a host of improved functionality. See the [roadmap]("http://giftwrap.wikia.com/wiki/Roadmap") a more detailed view, or just subscribe to the news feed to stay updated.

[SIZE="3"]How can I help?[/SIZE]

See the [contribute]("http://giftwrap.tuxfamily.org/index.php?pages/contribute") page. Any help is welcome, thanks!
[SIZE="3"]
[Digg it]("http://digg.com/linux_unix/GiftWrap_helps_you_create_debs")![/SIZE]

oo that's clever! Someone's been using the ol' noggin ^_^

---

### Post by Ubuntiac on 2009-10-11
> **Locke_99GS said:**
> Use *epm* for that.

Interesting. Thanks! I'll look into that...

---

### Post by Gyrotwister on 2009-10-17
I just managed to package and install Crrcsim from a .tar.gz without touching the terminal.  I've never packaged an app before.  The only thing is, I didn't get an icon installed in the Applications menu.  I had to do that manually after the .deb was installed.  

Is there something I can do during packaging to make it so the Crrcsim launch icon gets added to the games menu when installed?

---

### Post by Vadi on 2009-10-18
Not at the moment

---

### Post by titopagan on 2009-11-12
> **xuCGC002 said:**
> I tried compiling DOOM Legacy 1.42, but it keeps saying:


I'm not sure what to do.

EDIT: The top source folder is doomlegacy_142_src.


> **Ubuntiac said:**
> Maybe try changing the folder name to: DoomLegacy-1.42

Just a guess...

@xuCGC002-- did the above sugestion work for you?

---

### Post by MrQuincle on 2009-11-20
Dear all,

It was hard for me to find a tutorial for GiftWrap. So, I am gonna add some additional information regarding a C program in the CDT environment in Eclipse. Say I am gonna create the package "linda"...

**Example: linda package**
*Title*: The Linda engine is a threadpool for TCP/IP
*Description*: The Linda engine is a threadpool for TCP/IP powered by an abbey. Part of the CHAP software platform.
*Section*: Libraries

**Add Makefile to Eclipse**
Regretfully Eclipse has such a Makefile management system that it is almost impossible to get it running. :(

You have to add your own custom Makefile in the root of the project directory. Make sure you are in a real directory, not one soft linked from somewhere else! (GiftWrap can't cope with that yet.) The following is the content of the Makefile I created. Like you see it just evokes the makefile in the Debug directory. And it adds an install section. Add echo statements over there if you want to communicate during the installation process with the person installing your stuff.

```

all:
    (cd Debug; make $@)

clean:
    (cd Debug; make $@)

install:
    sudo cp Debug/liblinda.so /usr/lib
    sudo mkdir -p /usr/include/linda
    sudo cp inc/*.h /usr/include/linda
```
It is very convenient to run giftwrap from the **command line**. For instance, on deleting a *previously made* package, it needs confirmation to delete the .svn directories from the command line (the developer didn't use the flag -rf for removal). The symlink error is communicated by the cryptic message: "can't cd to /home/anne/.giftwrap/linda/linda-0.0.20091120". (When I did ls -latr, I saw that it was referring to the wrong directory.)

---

### Post by john4 on 2010-05-14
> **Ubuntiac said:**
> Hey Vadi,

This has to be THE idea, who's time has come for Ubuntu. The number of times that I've heard that the main thing holding Ubuntu back is the speed of which we can package new software for testing.

Can this be used to package a straight binary (ie without any compiling). I'm making a game in Blender, which precompiles a binary straight from the app. I just want something that lets me browse for the binary, put in the name, dependencies, license etc and click generate.

Would this be possible with GiftWrap? Every packaging guide I ever see assumes I want to learn all about make files, source packages and worse. I just want to share a binary with dependencies, a menu entry and a description!


EDIT: Well, I tried it... saved my binary in a folder in the format packagename-version and .tar.gz compressed it for giftwrap. Unfortunately I got:

dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package mr-cubie
dpkg-buildpackage: source version 0.1-1
dpkg-buildpackage: source changed by Ubuntiac <please@dontspamme.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/user/.giftwrap/mr-cubie/mr-cubie-0.1'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/user/.giftwrap/mr-cubie/mr-cubie-0.1'
make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2


Any way around this?

Has any one solved this.  I'm trying to create a PPA for our FOSS project (java web app) and I'm getting the same error.

Thank you,

John

---

### Post by Ubuntiac on 2010-05-14
Nope, sorry. I never did manage to find an easy way to package a single binary.

If you find a way, I'd love to hear it!

---

