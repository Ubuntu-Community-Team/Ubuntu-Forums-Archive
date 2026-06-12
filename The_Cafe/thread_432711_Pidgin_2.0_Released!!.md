---
title: "Pidgin 2.0 Released!!"
date: 2007-05-04
forum: The Cafe
---

### Post by Kunstar on 2007-05-04
Its finally out!

[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234&release_id=505814](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234&release_id=505814)

---

### Post by EdThaSlayer on 2007-05-04
Can't wait to see this. GAIM beta [6?] crashes way too often for me when logging in via multiple accounts. I did see some previews where its GUI looked sexier than the GAIM GUI.

---

### Post by WishMaster on 2007-05-04
someone has a feisty .deb ?

---

### Post by cookieofdoom on 2007-05-04
There's an i386 over in this thread. [http://ubuntuforums.org/showthread.php?t=429255&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=429255&highlight=pidgin)

If I can find a good tutorial I'll see if I can make a 64-bit debian.

---

### Post by Boreras on 2007-05-04
compiling it right now, but it won't be much use sharing it. This is a breezy badger upgraded box, which also has had a lot of non official repos, and upgraded while development was in alpha state two times.
Hope someone does have the right box to make a good .deb.

---

### Post by hanzomon4 on 2007-05-04
So whats different?

---

### Post by bvanaerde on 2007-05-04
Won't this be included into the Feisty updates?

---

### Post by cookieofdoom on 2007-05-04
> **hanzomon4 said:**
> So whats different?

Well, for starters it's a release version. What we have in the feisty repos now is a beta. I tried to make a debian and managed to mess up at every turn possible. :confused:

If anyone does manage to make a debian I'd be happy to host it. Although I'm hoping it'll just be an update that gets released soon.

---

### Post by Mr. Picklesworth on 2007-05-04
Argh!
They cut back on package formats :(
I guess I'll wait for a deb or an autopackage. Hopefully they'll come. (They have at least Autopackage for 1.5, so I would hope they keep it up for 2.0!).

As for an update to Feisty, let's hope! It is in Main, and the current version in the repos is a beta, so I think an update is necessary. (You can't use an old *beta* of something that has a perfectly good stable release and call it OK, 6-month release schedule or not).
It's quite bothersome to remove gaim since it also removes the ubuntu-desktop metapackage, which is a pain.

---

### Post by hyperair on 2007-05-04
Ok, so I'm a bit blur, but is this the final or the beta7? I certainly don't see any post of pidgin 2.0.0 final anywhere, but the archives there don't have the word beta in it.

---

### Post by hype on 2007-05-04
Well, it's released at sourceforge, so just wait a bit for other sites to updates the info. :)

I'm just compiling it; i tested beta 7 which was stable; i dint see anychanges, exept icons.

Edit; ok, just compiled: tray icon looks better, but i still find the contacts icons to big. :p
Anyway still a great IM client! :D

---

### Post by Kristopher on 2007-05-04
Will this just remove Gaim and install that if its done via Ubuntu updates? or will you need to remove gaim first?

---

### Post by AaronMT on 2007-05-04
How do I get a menu launcher for it under Internet in Applications?

---

### Post by bobpaul on 2007-05-04
> **bvanaerde said:**
> Won't this be included into the Feisty updates?

I don't think so. Ubuntu's policy is to only provide security and stability updates after the feature freeze--and certainly after the official release. A good example is Firefox. We had to wait till the next release for both 1.5 and 2.0 unless you installed the newer versions manually or with automatix or something.

That said, this case is a little blurry in that it's transitioning from beta to final. There might be an argument to be made with regards to providing the update before the new Ubuntu. If not, this will surely be available from Automatix rather shortly.

---

### Post by hyperair on 2007-05-04
Before you run the last command (sudo make install), run ```
gedit pidgin.desktop
``` and at the line where it says ```
Icon=pidgin
``` change it to ```
Icon=pidgin.svg
```

Then run ```
sudo make install
```

---

### Post by AaronMT on 2007-05-04
```
aaron@aaron-laptop:~/Desktop/pidgin-2.0.0$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

?

---

### Post by darweth on 2007-05-04
> **hype said:**
> Well, it's released at sourceforge, so just wait a bit for other sites to updates the info. :)

I'm just compiling it; i tested beta 7 which was stable; i dint see anychanges, exept icons.

Edit; ok, just compiled: tray icon looks better, but i still find the contacts icons to big. :p
Anyway still a great IM client! :D

The tray icon has changed since Pidgin Beta 7?  Screenshots!

---

### Post by tehkain on 2007-05-04
> **bobpaul said:**
> I don't think so. Ubuntu's policy is to only provide security and stability updates after the feature freeze--and certainly after the official release. A good example is Firefox. We had to wait till the next release for both 1.5 and 2.0 unless you installed the newer versions manually or with automatix or something.

That said, this case is a little blurry in that it's transitioning from beta to final. There might be an argument to be made with regards to providing the update before the new Ubuntu. If not, this will surely be available from Automatix rather shortly.

Didn't edgy ship with a firefox 2.0 release candidate? Then they updated to final about a 2 weeks after release?

---

### Post by motang on 2007-05-04
Yeah finally.  It much better pleasing icons the tired old ones.  Can't for the update to come through.

---

### Post by AaronMT on 2007-05-04
```
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure.

```

?

---

### Post by Megatog615 on 2007-05-04
Any chance of a .deb of the final version soon?

---

### Post by amphet on 2007-05-04
Just compiled it from source without issues, it even created a *.desktop for me.

---

### Post by MRiGnS on 2007-05-04
EDIT&#65306;got it working

---

### Post by Rattle on 2007-05-04
> **AaronMT said:**
> ```
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure.

```

?
sudo apt-get build-dep gaim && sudo apt-get install doxygen

then
./configure && make && make install


buld-dep to let apt-get take care of the dependencies for compiling Gaim and install doxygen to make MSN work. Can't remember exactly what the package did or why you need it, but you need it.

---

### Post by amphet on 2007-05-04
> **Rattle said:**
> sudo apt-get build-dep gaim && sudo apt-get install doxygen

then
./configure && make && make install


buld-dep to let apt-get take care of the dependencies for compiling Gaim and install doxygen to make MSN work. Can't remember exactly what the package did or why you need it, but you need it.

I don't have doxygen installed and I'm using msn as we speak so I don't think you really need that.

---

### Post by Rattle on 2007-05-04
OK, I needed that for Gaim 2.0 beta 2 or something and haven't compiled Gaim/Pidgin without installing doxygen since then. If your MSN works without doxygen, I guess you don't need it anymore then. :)

---

### Post by Gilgad Drumheller on 2007-05-04
For AaronMT's problem,
```
sudo apt-get install libgtk2.0-dev
```
should do the trick.  You can also search for it through synaptic/adept/whatever

---

### Post by amphet on 2007-05-04
> **Rattle said:**
> OK, I needed that for Gaim 2.0 beta 2 or something and haven't compiled Gaim/Pidgin without installing doxygen since then. If your MSN works without doxygen, I guess you don't need it anymore then. :)

probably, I never used the betas.

---

### Post by mech7 on 2007-05-04
Can anybody post the debs for the final ?:)

---

### Post by MRiGnS on 2007-05-04
i tried to make debs but i fails everytime because it wants to overwrite a gcc file :(

make install works fine though

---

### Post by DoktorSeven on 2007-05-04
For anyone trying to compile from source and get an error that they don't have something installed -- remember that to compile from source you need the **-dev** version of the package from the repos.  For example, for the GTK error **AaronMT** is getting, one needs **libgtk2.0-dev**.

Compiling from there should be as easy as ./configure, make, sudo make install.

---

### Post by Quillz on 2007-05-04
> **Kunstar said:**
> Its finally out!

[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234&release_id=505814](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234&release_id=505814)
Went ahead and upgraded, thanks for the news!

---

### Post by Rattle on 2007-05-04
> **DoktorSeven said:**
> For anyone trying to compile from source and get an error that they don't have something installed -- remember that to compile from source you need the **-dev** version of the package from the repos.  For example, for the GTK error **AaronMT** is getting, one needs **libgtk2.0-dev**.

Compiling from there should be as easy as ./configure, make, sudo make install.
'apt-get build-dep gaim' takes care of all that.

---

### Post by zerwas on 2007-05-04
No DEB for Ubuntu 7.04 so far? I will try.

---

### Post by MRiGnS on 2007-05-04
Building it from source doesn't cause any issues just building a deb file with checkinstall does not work.

If have enough time i will build them manually tomorrow. x86 x86-dbg

---

### Post by nexx on 2007-05-04
Just installed using ./configure, make and make install. It works but is not in the menu, have to start it using F2 start application. It does not appears in synaptics either. I am just wondering if it is safe to dump (uninstall) gaim at this point. Also how can you uninstall a program that does not appears in synaptic, it look weird to me.

---

### Post by mech7 on 2007-05-04
I get this,.. ./configure seems to work but then..

> chris@chris-laptop:~/Desktop/pidgin-2.0.0$ make
make: *** No targets specified and no makefile found.  Stop.
chris@chris-laptop:~/Desktop/pidgin-2.0.0$ make install
make: *** No rule to make target `install'.  Stop.
chris@chris-laptop:~/Desktop/pidgin-2.0.0$ ./configure ,make
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: ,make
checking build system type... Invalid configuration `,make': machine `,make' not recognized
configure: error: /bin/bash ./config.sub ,make failed


> chris@chris-laptop:~/Desktop/pidgin-2.0.0$ ./configure ,make
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: ,make
checking build system type... Invalid configuration `,make': machine `,make' not recognized
configure: error: /bin/bash ./config.sub ,make failed
chris@chris-laptop:~/Desktop/pidgin-2.0.0$ 


or all commands at once..

> chris@chris-laptop:~/Desktop/pidgin-2.0.0$ ./configure, make, sudo make install.bash: ./configure,: No such file or directo
How does this work :mad:

---

### Post by Rattle on 2007-05-04
*Sigh*

I have mentioned it twice in this thread.

---

### Post by mailbox on 2007-05-04
Just got done compiling it... so, uh, how do I run it? 'pidgin' in term does nothing, and i can't find it under networking.

---

### Post by happy-and-lost on 2007-05-04
Looks very nice, but it won't connect to MSN without a certain SSL... any clue as to what to install?

---

### Post by brunomiguel on 2007-05-04
Was anyone able to compile pidgin with gstreamer enabled? Every time I try to compile it with Gstreamer, it disables it... Already tried --enable-gstreamer, but no success...

---

### Post by zerwas on 2007-05-04
> **MRiGnS said:**
> Building it from source doesn't cause any issues just building a deb file with checkinstall does not work.

If have enough time i will build them manually tomorrow. x86 x86-dbg

No i will publish a DEB for feisty, built with dh_make, dpkg-buildpackage and pbuilder. :-)
I will finish it this night. Hopefully with GStreamer-support (and SSL for sure)

---

### Post by brunomiguel on 2007-05-04
My bad... I didn't had gstreamer dev installed.

---

### Post by Mateo on 2007-05-04
so how long until it's in the repos?  will it upgrade from gaim, or do you have to uninstall gaim and install this instead?

---

### Post by mailbox on 2007-05-04
what's the command to run it?
anyone?

---

### Post by brunomiguel on 2007-05-04
open the terminal and type [COLOR=Black]_**pidgin**_[/COLOR]

---

### Post by Hubris2 on 2007-05-04
I compiled from source, as per this thread.  First time I ran it, it had my full contact list, as organized in Gaim beta 6.  Doesn't look like an upgrade is required.

---

### Post by MRiGnS on 2007-05-04
> **zerwas said:**
> No i will publish a DEB for feisty, built with dh_make, dpkg-buildpackage and pbuilder. :-)
I will finish it this night. Hopefully with GStreamer-support (and SSL for sure)

ok, then i will build my own deb with blackjack and h**kers ;P

---

### Post by Aranel on 2007-05-04
> **happy-and-lost said:**
> Looks very nice, but it won't connect to MSN without a certain SSL... any clue as to what to install?

*sudo apt-get install libgnutls-dev* should take care of it.

---

### Post by mailbox on 2007-05-04
> **brunomiguel said:**
> open the terminal and type [COLOR=Black]_**pidgin**_[/COLOR]

"command not found"

---

### Post by Aranel on 2007-05-04
> **mailbox said:**
> "command not found"

I believe it installs in /usr/local/bin instead of /usr/bin. I can't know for sure myself (mine's still compiling :p ), but this might work:

```
sudo ln -s /usr/local/pidgin /usr/bin/
```

---

### Post by mailbox on 2007-05-04
Nope, that didn't work either.

---

### Post by Aranel on 2007-05-04
> **mailbox said:**
> Nope, that didn't work either.

Er, that's because I messed it up. Whoops. :mad:

Try this:

```
sudo ln -s /usr/local/bin/pidgin /usr/bin/
```

---

### Post by rolando2424 on 2007-05-04
Too bad I can't seem to make the bipping sound the default one (that existed in Gaim). I only got the bip console... :(

---

### Post by mailbox on 2007-05-04
still no.
i'll try recompiling.

---

### Post by MRiGnS on 2007-05-04
> **rolando2424 said:**
> Too bad I can't seem to make the bipping sound the default one (that existed in Gaim). I only got the bip console... :(

you probably ompiled it without gstreamer support

---

### Post by b1g4L on 2007-05-04
Here is a review of Pidgin for those wondering whether or not to install....

[http://arstechnica.com/reviews/apps/pidgin-2-0.ars](http://arstechnica.com/reviews/apps/pidgin-2-0.ars)

---

### Post by Polygon on 2007-05-04
i tried compiling and i needed to install

libglib-dev
libgtk2-dev
libxml2-dev

now lets see if i can figure out the arguments...

arg i cant figure out which ones to put

i want:

dbus support
ssl support
gstreamer support
gtkspell support

and what does build with network manager mean?

if anyone could help me out that would be cool

---

### Post by mustang on 2007-05-04
Thanks for letting us know. Here's what I did to get it going:

```

sudo apt-get build-dep gaim
./configure
make
sudo make install

```

Thanks you Rattle for that time-saving build-dep command.

---

### Post by zerwas on 2007-05-04
I made a DEB (for Feisty users)

Grab it while it's hot: [http://rapidshare.com/files/29533296/pidgin_2.0.0-1_i386.deb.html](http://rapidshare.com/files/29533296/pidgin_2.0.0-1_i386.deb.html)

And thanks for feedback :-)

---

### Post by Sef on 2007-05-04
> Won't this be included into the Feisty updates?


Yes, probably will show up in about a week.

---

### Post by Mateo on 2007-05-04
Why does it take so long?  Some people try to say that repositories is a plus for ubuntu, but having to wait forever after new software is released is not a plus.  It's a minus.

---

### Post by zerwas on 2007-05-04
> **Mateo said:**
> having to wait forever

Come on, a week. That's pretty fast. If you can't wait, build it from source or try my DEB so long.

---

### Post by Polygon on 2007-05-04
its because they check the software out, test it, make sure malicious code hasnt been added, and make sure that all the dependencies and build options are set up correctly

and if its going to be included in the repos as an update (from gaim 2.0 beta 6 to pidgin 2.0) then ill just wait for the update to come through.

---

### Post by MRiGnS on 2007-05-04
> **Mateo said:**
> Why does it take so long?  Some people try to say that repositories is a plus for ubuntu, but having to wait forever after new software is released is not a plus.  It's a minus.

lol, waiting forever. try debian stable if you want to wait forever. software for the repositories must be tested and approved. you can't just add something because of security issues.

---

### Post by Mateo on 2007-05-04
> **zerwas said:**
> Come on, a week. That's pretty fast. If you can't wait, build it from source or try my DEB so long.

No it's not.  You made a deb in less than a day.  So if you can do it, why does it take canonical a week?

---

### Post by Mateo on 2007-05-04
> **MRiGnS said:**
> lol, waiting forever. try debian stable if you want to wait forever. software for the repositories must be tested and approved. you can't just add something because of security issues.

tested specifically for what, and why does this testing take a week?

---

### Post by MRiGnS on 2007-05-04
at first they got the source. they must check the sourcecode for eventual added malware etc.

then they build the debs for several architectures, add all the deps, they need to test the debs if they really work on every machine and not just on their ownv test if there are memory or security holes. ok now you got the debs. these debs must be put on all the repo servers.

now they have to check all the md5 checksums of every single package on every single server.

if all went well it's in the list of the software you can download.

---

### Post by compwiz18 on 2007-05-04
one amd64 deb of pidgin 2.0.0 final: [http://compwiz18.ig3.net/linux/pidgin/pidgin_2.0.0-1_amd64.deb](http://compwiz18.ig3.net/linux/pidgin/pidgin_2.0.0-1_amd64.deb)

---

### Post by Polygon on 2007-05-05
> **zerwas said:**
> I made a DEB (for Feisty users)

Grab it while it's hot: [http://rapidshare.com/files/29533296/pidgin_2.0.0-1_i386.deb.html](http://rapidshare.com/files/29533296/pidgin_2.0.0-1_i386.deb.html)

And thanks for feedback :-)

btw, thank you so much for the deb.

---

### Post by kaede on 2007-05-05
another link for i386

[http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb)

:D

---

### Post by kpolice on 2007-05-05
> **Mateo said:**
> Why does it take so long?  Some people try to say that repositories is a plus for ubuntu, but having to wait forever after new software is released is not a plus.  It's a minus.

It's one of the reasons I don't use Ubuntu anymore although I try to help in the forums everyday.

---

### Post by Quillz on 2007-05-05
> **Mateo said:**
> so how long until it's in the repos?  will it upgrade from gaim, or do you have to uninstall gaim and install this instead?
I installed a .deb package of Beta 7 outside of Synaptic, and later found out that Synaptic somehow picked it up and is now managing it for me. So it's in the repos, but Beta 7, not the final release yet.

And since Pidgin is just the new name for Gaim, yes, it keeps all your settings and profiles just the way they were.

---

### Post by Quillz on 2007-05-05
> **Mateo said:**
> Why does it take so long?  Some people try to say that repositories is a plus for ubuntu, but having to wait forever after new software is released is not a plus.  It's a minus.
The final release only came out today. And there's always a chance it could be buggy. Just give it a few days, I'm sure it won't be long before the final release is in there. And if you absolutely can't wait, just compile an independent build yourself and place it in /opt or some other place that it won't get touched by Synaptic.

---

### Post by NeoChaosX on 2007-05-05
> **Quillz said:**
> I installed a .deb package of Beta 7 outside of Synaptic, and later found out that Synaptic somehow picked it up and is now managing it for me. So it's in the repos, but Beta 7, not the final release yet.

Actually, no, it's not in the repos yet. Synaptic manages all debs installed, regardless if the package is in the preset repos or not.

If you want a Ubuntu-built Pidgin 2.0, you have to wait until Gutsy for it.

---

### Post by zerwas on 2007-05-05
A good build (i hope)
[Pidgin]("http://www.getdeb.net/app.php?name=Pidgin")

---

### Post by Polygon on 2007-05-05
> **NeoChaosX said:**
> Actually, no, it's not in the repos yet. Synaptic manages all debs installed, regardless if the package is in the preset repos or not.

If you want a Ubuntu-built Pidgin 2.0, you have to wait until Gutsy for it.

one of the forum mods said that it would be in the repos within a week. And it makes sense, as ubuntu's policy is not to include new major versions of software, but updates of the same version (aka beta 7 to final 2.0) are included.

---

### Post by rolando2424 on 2007-05-05
To bad my Guifications don't seem to work in Pidgin...

---

### Post by plb on 2007-05-05
It's not hard to build it from source, it took me all of 10 minutes to get all the deps than build it :confused:

---

### Post by haggard1 on 2007-05-05
Hi fellas.

I tried to compile latest final Pidgin from source, when all was going well, I faced with these:

> make[2]: Leaving directory `/home/alperen/geik/pidgin-2.0.0/m4macros'
Making all in po
make[2]: Entering directory `/home/alperen/geik/pidgin-2.0.0/po'
file=`echo af | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file af.po
/bin/sh: line 1: -o: command not found
make[2]: *** [af.gmo] Error 127
make[2]: Leaving directory `/home/alperen/geik/pidgin-2.0.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alperen/geik/pidgin-2.0.0'
make: *** [all] Error 2
iskenderun:/home/alperen/geik/pidgin-2.0.0#

What can it be now? I'm a Debian user by the way.

---

### Post by plb on 2007-05-05
> **haggard1 said:**
> Hi fellas.

I tried to compile latest final Pidgin from source, when all was going well, I faced with these:



What can it be now? I'm a Debian user by the way.

I compiled on debian as well with no issues whatsoever. I already had many *-dev packages installed so the only 2 I had to get was libxml2 and perl xml parser package. I imagine you would also need gtk2 dev and maybe some xorg ones. I'm on sid btw.

---

### Post by Quillz on 2007-05-05
> **Polygon said:**
> one of the forum mods said that it would be in the repos within a week. And it makes sense, as ubuntu's policy is not to include new major versions of software, but updates of the same version (aka beta 7 to final 2.0) are included.
So by this policy, I take it we won't see Thunderbird 2 until 7.10?

---

### Post by Polygon on 2007-05-06
> **Quillz said:**
> So by this policy, I take it we won't see Thunderbird 2 until 7.10?

yes. They do it cause major version upgrades (like 1.5.0.11 or w/e to 2.0) are...major... they want to make sure that it plays nicely with the rest of the programs and the operating system. Usually minor upgrades are bug fixes, not additional features.

so if you have been waiting for thunderbird 2 to hit the repos, i would go ahead and find a deb of it somewhere and install it, as its not coming out until gutsy ;)

---

### Post by quantumcheese on 2007-05-06
I had no trouble compiling beta 6 under Dapper, and then I didn't need to once I switched to Edgy; but for beta 7 and now the final realease under Feisty, I can compile, and it seems to work, but when I launch pidgin, it doesn't have any protocols installed; all my accounts show up as "unknown".
All I can think is that I'm missing some package, but I thought   sudo apt-get build-dep gaim  would get all that I needed. 

Any thoughts/suggestions?  Thank you.

---

### Post by OffHand on 2007-05-06
I wonder why their fonts still suck. It's just plain ugly.

---

### Post by joeblow1102 on 2007-05-06
> **rolando2424 said:**
> To bad my Guifications don't seem to work in Pidgin...

have you compiled the most recent version of guifications?  pidgin.guifications.org

i was surprised that pidgin kept my plugins when i updated from beta7 to final.

---

### Post by DoktorSeven on 2007-05-06
> **haggard1 said:**
> Hi fellas.
I tried to compile latest final Pidgin from source, when all was going well, I faced with these:
What can it be now? I'm a Debian user by the way.

Do you have **gettext** installed?  Looks like it didn't find/know about the **msgfmt** binary.

---

### Post by rolando2424 on 2007-05-06
> **joeblow1102 said:**
> have you compiled the most recent version of guifications?  pidgin.guifications.org

i was surprised that pidgin kept my plugins when i updated from beta7 to final.

Thank you, it worked :D

---

### Post by DocHoliday52090 on 2007-05-06
I jumped the gun and compiled beta7. 

Is there any way I can 'update' the install rather than uninstalling it and replacing it? 

On that note, 'sudo apt-get remove pidgin' doesn't work either. Can't find the package.

---

### Post by ZeroXR on 2007-05-06
Anyone have any idea how to get the gFire plug-in working with Pidgin? That's the only thing I need at the moment...

---

### Post by gradedcheese on 2007-05-06
Hey, I am not sure if this has been mentioned, but the amsn people registered "pigdin.im" ...dorks.

DocHoliday52090 -- apt doesn't manage software you build from source, it manages .deb packages.  So you can't remove it that way and no to upgrade you build it again and install.  Look at the install log files (in the source directory) to see where things got placed.

---

### Post by hanzomon4 on 2007-05-06
> **DocHoliday52090 said:**
> I jumped the gun and compiled beta7. 

Is there any way I can 'update' the install rather than uninstalling it and replacing it? 

On that note, 'sudo apt-get remove pidgin' doesn't work either. Can't find the package.

Go to the directory you compiled the program in and run "sudo make uninstall"

---

### Post by Yggdrasill on 2007-05-06
Where is Pidgin 2.0 installed?  I tried looking in /usr/share/pixmap but only find a GAIM folder.  I need to copy [this](http://www.deviantart.com/deviation/29142704/?q=tango+GAIM&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5&offset=40) theme into Pidgin.

---

### Post by chrishaney on 2007-05-06
[http://www.freshnet.org/wordpress/2007/05/05/pidgin-200-for-ubuntu-feisty/](http://www.freshnet.org/wordpress/2007/05/05/pidgin-200-for-ubuntu-feisty/)

---

### Post by Wiebelhaus on 2007-05-06
the icon is just....bad.

---

### Post by Quillz on 2007-05-07
> **OffHand said:**
> I wonder why their fonts still suck. It's just plain ugly.
Looks fine to me on a stock 7.04...

---

### Post by Footissimo on 2007-05-07
> **Yggdrasill said:**
> Where is Pidgin 2.0 installed?  I tried looking in /usr/share/pixmap but only find a GAIM folder.  I need to copy [this](http://www.deviantart.com/deviation/29142704/?q=tango+GAIM&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5&offset=40) theme into Pidgin.

You can try and replace the pidgin icon folder in /usr/share/pixmaps, but it doesn't work - I believe Pidgin gets rid of all the old icons that symbolised different protocols - so the icons used in this lovely Tango theme are fairly useless =(

---

### Post by Polygon on 2007-05-07
> **gradedcheese said:**
> Hey, I am not sure if this has been mentioned, but the amsn people registered "pigdin.im" ...dorks.


thats really low of the amsn devs.

---

### Post by graabein on 2007-05-07
> **sx66gns said:**
> the icon is just....bad.

I have not seen it in reviews or the Pidgin website. Can you post a screenshot please?

---

### Post by philldo on 2007-05-07
yea, its not the best of icons... but its unmistakable i guess ;-)

---

### Post by bvanaerde on 2007-05-07
> **philldo said:**
> yea, its not the best of icons... but its unmistakable i guess ;-)
I do like the icon, but the full image looks a bit childish.

---

### Post by meborc on 2007-05-07
hmm... reminds me of a thunderbird... or should i say thunderpidgin :D

installed the final from scource... the make took ages... but it's up and running :P

---

### Post by graabein on 2007-05-07
Okay, it's a purple bird :) Fine by me I guess... I was thinking of the tray/notification icon though. 

I downloaded and installed the windows version (at work) and I like it. A green circle means *available* and a blue clock is *away*.


I can't connect with my MSN account though. I get **Writing error**. Anyone know what that means? I use the same proxy settings as I had in my previous IM client.

---

### Post by jeduan on 2007-05-07
> **graabein said:**
> Okay, it's a purple bird :) Fine by me I guess... I was thinking of the tray/notification icon though. 

I downloaded and installed the windows version (at work) and I like it. A green circle means *available* and a blue clock is *away*.


I can't connect with my MSN account though. I get **Writing error**. Anyone know what that means? I use the same proxy settings as I had in my previous IM client.
Have you tried the "Use HTTP method checkbox" in Edit account->Advanced?

---

### Post by bvanaerde on 2007-05-07
> **graabein said:**
> I was thinking of the tray/notification icon though.
I like it simple, so the tray icon is good enough for me :)

---

### Post by graabein on 2007-05-07
> **jeduan said:**
> Have you tried the "Use HTTP method checkbox" in Edit account->Advanced?

Yeah I think so. I'll double check at work tomorrow.

---

### Post by gummygod on 2007-05-07
there isnt a .deb for dapper (6.06)  32 bit somewhere is there? (for the final 2.0.0 version)
i looked everywhere. when i try to compile source i get this annoying "checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool" error.  
apparently this: [http://www.karakas-online.de/forum/viewtopic.php?t=3915](http://www.karakas-online.de/forum/viewtopic.php?t=3915) should help but i cant get that to work either.  
any1 kno of this .deb? or kno what the problem is?

---

### Post by phinn on 2007-05-07
So uhhh is Ubuntu going to update their repositories for the most popular instant messaging client in existence or we going to sit around waiting forever?????

:( 

My friends with Windows boxes all have it and I don't wanna have to download 100mbs in compiling crap to get it running.

---

### Post by phinn on 2007-05-07
Ah ok, although ubuntu doesn't have it on the repos these guys have it

[http://www.freshnet.org/wordpress/2007/05/05/pidgin-200-for-ubuntu-feisty/]("http://www.freshnet.org/wordpress/2007/05/05/pidgin-200-for-ubuntu-feisty/")
and
[http://www.getdeb.net/app.php?name=Pidgin]("http://www.getdeb.net/app.php?name=Pidgin")


I just hope it doesn't mess anything up when Ubuntu finally does add it.
Why the hell they had to go with that UGLY purple design is beyond me.

EDIT:  None of these packages work for me. They all have a bunch of dependencies I can't seem to download... Sure wish Ubuntu would update their ****

---

### Post by bionnaki on 2007-05-07
upgraded and it's ok. same thing as the latest gaim, seems like. real ugly icons and artwork. I really wish gaim/pidgin moves in the direction of or can compete with the beauty of iChat.

---

### Post by graabein on 2007-05-08
> **jeduan said:**
> Have you tried the "Use HTTP method checkbox" in Edit account->Advanced?

I have the following settings:

**MSN Options**
[INDENT]Server: gateway.messenger.hotmail.com
Port: 80
Use HTTP Method: Yes
Show custom smileys: Yes[/INDENT]

**Proxy Options**
[INDENT]Proxy type: HTTP
Host: <proxy address>
Port: 8080
Username: <blank>
Password: <blank>[/INDENT]

And I get this error message:

**<mail address> disconnected**
Connection error from Notification server:
Writing error

---

### Post by misfitpierce on 2007-05-08
I myself have tried out pidgin... It is alright I prefer gaim atm myself tho

---

### Post by plb on 2007-05-08
Pidgin is in debian unstable...perhaps you can snag it from their repos and "hope" it works for ubuntu :)

---

### Post by Polygon on 2007-05-08
i really like pidgin 2.0, stable and it looks better then gaim. Good job to the devs :D

---

### Post by GumbyX on 2007-05-09
Hey all. I am liking Pidgin, but I am having problems with sound. I can only choose console beeps or commands (no automatic like in GAIM) under sound method. Anyone else having this problem or know of a fix for it?

Thanks ahead of time.

PS I have found people saying that Pidgin is not debain stable yet, though I compiled it fine and made a deb out of it.

---

### Post by b1g4L on 2007-05-09
> **GumbyX said:**
> Hey all. I am liking Pidgin, but I am having problems with sound. I can only choose console beeps or commands (no automatic like in GAIM) under sound method. Anyone else having this problem or know of a fix for it?

Thanks ahead of time.

PS I have found people saying that Pidgin is not debain stable yet, though I compiled it fine and made a deb out of it.

I am having the same issue with sound. Sound worked fine with GAIM, but in Pidgin, I can only get console beeps.

---

### Post by mech7 on 2007-05-09
Yeah pidgin 2 is great.. i hope they will make a search form like in live messenger though it is pretty usefull for findinf contacts in large lists :)

---

### Post by jack1254 on 2007-05-09
Hey, this got rid of the XML::Parser error for me:

```
sudo apt-get install libxml-perl libxml-parser
```

(If the package names are slightly off, sorry this is from memory. Easily found in a package manager.

---

### Post by Madmoose on 2007-05-09
Hey all, 

Thanks for the debs! Have you submitted them to [http://www.getdeb.net/](http://www.getdeb.net/) yet?

If you haven't... can you? :) Please.

Thanks!

Moose

---

### Post by Barrakketh on 2007-05-13
> **b1g4L said:**
> I am having the same issue with sound. Sound worked fine with GAIM, but in Pidgin, I can only get console beeps.

Sound works for me, but I'm using a package I created that is based off of the Ubuntu Gaim 2.0beta6 package.

---

### Post by bvanaerde on 2007-05-14
> **Madmoose said:**
> Thanks for the debs! Have you submitted them to [http://www.getdeb.net/](http://www.getdeb.net/) yet?
It looks like [somebody else already did this]("http://www.getdeb.net/app.php?name=Pidgin").
In [this thread]("http://ubuntuforums.org/showthread.php?t=441363"), you'll find a deb for feisty, along with a plugin pack.

---

### Post by Znupi on 2007-05-14
So uhm... why is pidgin better than gaim?! I'm a Yahoo! Messenger user, and, pidgin is worse than gaim for me.

1) There are no more Yahoo! emoticons. (WHY??)
2) I still can't have an avatar on Yahoo!
3) I still can't receive files on Yahoo!
4) I still can't chat with my MSN-user friends...

Will there ever be a pidgin version that will correctly work on Yahoo!, too?

I actually went back to gaim :|.

---

### Post by misfitpierce on 2007-05-14
I didnt bother to check while I had pidgin but can pidgin use the gaim festival plugin?

---

### Post by CowPizza on 2007-05-14
Any one else notice this when compiling from the source?

```
checking for me pot o' gold... no
```

---

### Post by Ghostlove on 2007-05-16
Is anyone else finding they have no menu bar? I downloaded it from getdeb.net and it's fine, except a lot of the features are unavailable to me because there's no menu! :/

---

