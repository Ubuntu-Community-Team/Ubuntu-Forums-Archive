---
title: "Request: aMule 2.0.0"
date: 2005-05-03
forum: Ubuntu Backports
---

### Post by bassMonkey on 2005-05-03
aMule 2.0.0 has finally been released. YEAH! =)

Are we going to see it in backports anytime soon?

[aMule 2.0.0 Released!](http://www.amule.org/amule/thread.php?threadid=5981&sid=638a2f1006635fdc8629613693790a62)

---

### Post by gbil on 2005-05-03
The debian packages from the amule site work fine with ubuntu so there is no need for a backport.

---

### Post by rpgcyco on 2005-05-03
Hey jdong,

If you do backport aMule 2.0.0, is there some way you can also backport libwxgtk2.6.0? I don't know if it's in breezy, but if possible it would be good because aMule can now use it. :)

- Rpg Cyco

---

### Post by ow50 on 2005-05-03
I'm sure we'll see a debian source for 2.0.0 to build from soon, because aMule has had daily debian packages made from cvs. It's just a matter of tagging some day's package as 2.0.0.

---

### Post by RastaMahata on 2005-05-05
aww, no gtk2?

---

### Post by jeremy on 2005-05-05
The debian file at amule.org is only for rc8 as far as I can see.

---

### Post by ow50 on 2005-05-05
The latest cvs debian sources are at
[http://www.vollstreckernet.de/debian/dists/testing/amule/source/](http://www.vollstreckernet.de/debian/dists/testing/amule/source/)

I'm guessing 20050503 is about the same as 2.0.0. I built a deb package from that myself and it works fine. I don't know what's the hold up with the getting a 2.0.0 deb package to the download list.

---

### Post by RastaMahata on 2005-05-05
[QUOTE=rpgcyco]Hey jdong,

If you do backport aMule 2.0.0, is there some way you can also backport libwxgtk2.6.0? I don't know if it's in breezy, but if possible it would be good because aMule can now use it. :)

- Rpg Cyco[/QUOTE]
 If this means "better looking amule", then I give it my vote :)

---

### Post by XDevHald on 2005-05-05
[QUOTE=RastaMahata]If this means "better looking amule", then I give it my vote :)[/QUOTE]
 I don't see why this would be a problem to backport the 2.0.0 version, and yes it is quite easy to download it from the site, but in convenience to newbies and others it probably would be nice to have this as an auto get thing :)

---

### Post by bored2k on 2005-05-05
[QUOTE=BB]I don't see why this would be a problem to backport the 2.0.0 version, and yes it is quite easy to download it from the site, but in convenience to newbies and others it probably would be nice to have this as an auto get thing :)[/QUOTE]
 It's even harder for a newbie to dist-upgrade to the next release after using the backports (--downgrading things). Funny :-P ..

I think I'll wait a little bit more. Last time i gave rc8 a shot it devoured my RAM like [Morgan Spurlock](http://www.imdb.com/title/tt0390521/) at a Subway..

---

### Post by jdong on 2005-05-06
I'd _REALLY_ like to see this imported into Sid or Breezy before backporting it.

That was the original intention of Backports -- to bring the stable release up-to-date with the development release.

---

### Post by Dax0r on 2005-05-07
Someone try this repository for debian?

deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule

---

### Post by bored2k on 2005-05-07
[QUOTE=Dax0r]Someone try this repository for debian?

deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule[/QUOTE]
 Isn't it the same thing.. we all should avoid using debian repositories, wich is why jdong's waiting for a sid release to backport.

---

### Post by Poul on 2005-05-07
Hmm I've got a dilema . i decided to use mldonkey because of more candylooking gui but if new version is gonna support gnome looks then I am going to try it . I hope  that ubuntu package will show up by tommorow - otherwise I'll have to be bothered to compile it.

---

### Post by jdong on 2005-05-07
If one of you want to drop a POLITE "what's up" e-mail to the Debian amule maintainer, that'd be great.

I've sent too many of these to be effective anymore ;)

---

### Post by rpgcyco on 2005-05-13
Hey jdong,

I've enabled the breezy repositries on my sister's computer (hahaha), and noticed that aMule 2.0.0 is there, but for some unknown reason, it's still being compiled against wxgtk2.4.2 and GTK1. GTK1 apps are very ugly in Ubuntu unfortunately, so if it's possible can you please compile aMule 2.0.0 against wxgtk2.5.3 with GTK2 enabled?

**EDIT:** aMule 2.0.0 is now in Debian Unstable.

[http://packages.debian.org/unstable/x11/amule](http://packages.debian.org/unstable/x11/amule)

Thanks,
- Rpg Cyco

---

### Post by mirtux on 2005-05-15
Hi guys,
  maybe this could be a stupid question, but i'm searching for the place in aMule where i can read my score......does anybody has an idea?

Thanks in advance,
MC

---

### Post by rwabel on 2005-05-15
[QUOTE=rpgcyco]Hey jdong,

I've enabled the breezy repositries on my sister's computer (hahaha), and noticed that aMule 2.0.0 is there, but for some unknown reason, it's still being compiled against wxgtk2.4.2 and GTK1. GTK1 apps are very ugly in Ubuntu unfortunately, so if it's possible can you please compile aMule 2.0.0 against wxgtk2.5.3 with GTK2 enabled?

**EDIT:** aMule 2.0.0 is now in Debian Unstable.

[http://packages.debian.org/unstable/x11/amule](http://packages.debian.org/unstable/x11/amule)

Thanks,
- Rpg Cyco[/QUOTE]
 maybe they did compile against wxgtk2.4.2 due to performance problems. In the past there where problems with wxgtk2.5.x with GTK2.

But I've tested the amule cvs from
deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule

and it works fine and it's gtk2, kinda sweet now :-)

---

### Post by ow50 on 2005-05-15
The 2.0.0 from Breezy compiled against wx 2.5.3 works fine here. Gtk2 and no stability problems.

---

### Post by rpgcyco on 2005-05-16
> maybe they did compile against wxgtk2.4.2 due to performance problems. In the past there where problems with wxgtk2.5.x with GTK2.

Yeah, I guess that's a valid reason, though personally, I've had no performance problems. One thing I did notice, was that libwxgtk.2.5.x wasn't even in the Breezy repos, but it's in Hoary.

> But I've tested the amule cvs from
deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule

and it works fine and it's gtk2, kinda sweet now

Yeah, when I last tried that, the server was down. Will try it again in a few days if an aMule 2.0.0 doesn't appear in backports.

> The 2.0.0 from Breezy compiled against wx 2.5.3 works fine here. Gtk2 and no stability problems.

Cool. I guess it's the right time to request it in the backports, then. :)

- Rpg Cyco

---

### Post by JDay on 2005-05-16
Here's a direct link to the deb from the above site (I couldn't get it working through apt):
[http://www.vollstreckernet.de/debian/dists/testing/amule/binary-i386/amule_2.0.0-rel+CVS20050511-1_i386.deb](http://www.vollstreckernet.de/debian/dists/testing/amule/binary-i386/amule_2.0.0-rel+CVS20050511-1_i386.deb)
Works great and looks and feels SO much better than the old gtk1 version I was using.

---

### Post by daniel311 on 2005-05-17
[QUOTE=JDay]Here's a direct link to the deb from the above site (I couldn't get it working through apt):
[http://www.vollstreckernet.de/debian/dists/testing/amule/binary-i386/amule_2.0.0-rel+CVS20050511-1_i386.deb](http://www.vollstreckernet.de/debian/dists/testing/amule/binary-i386/amule_2.0.0-rel+CVS20050511-1_i386.deb)
Works great and looks and feels SO much better than the old gtk1 version I was using.[/QUOTE]

Thank you. It worked with dpkg -i --force-all, but synaptic lists it as broken and tries to remove the package. It depends on libc6 >= 2.3.2.ds1-21 but Hoary has only 2.3.2.ds1-20ubnutu13. Looks like this package was created with Breezy in mind...

---

### Post by ow50 on 2005-05-17
Still no backport? Or is this a bad backport candidate, if it would need changes (at the cost of stability?) in order to be gtk2?

Here's a gtk2 deb for hoary that I built from the breezy source:
[http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.0-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.0-1_i386.deb)

I made the following replacements in the Build-Depends section of debian/control:
libgtk1.2-dev -> libgtk2.0-dev
libwxgtk2.4-dev -> libwxgtk2.5-dev
libwxbase2.4-dev ->

As there is no libwxbase2.5-dev, I just removed that dependency, but maybe it could just have been kept there. Either way, libwxbase is some non-gui stuff. I don't know what it does for amule, maybe it's for amule-utils. I've been using this aMule for about a week now without problems.

---

### Post by rpgcyco on 2005-05-18
Hey ow50,

Thanks for that package, it's working fine so far.

Also, libwxbase has been integrated in libwxgtk as of 2.5. :)

Thanks again,
- Rpg Cyco

---

### Post by tnilsson on 2005-05-18
[QUOTE=rpgcyco]Hey ow50,

Thanks for that package, it's working fine so far.

Also, libwxbase has been integrated in libwxgtk as of 2.5. :)

Thanks again,
- Rpg Cyco[/QUOTE]
 I compiled aMule 2.0.0 from the source (downloaded from amule.org). It was working great!
Before I compiled aMule I insttalled libgtk2.0-dev and  libwxgtk2.5-dev.

---

### Post by rwabel on 2005-05-18
they have just released a new version with the cpu bug fixed. I hope vollstrecker is making some new cvs or deb files for us :-)

does the version in breezy also have the amule daemon and webserver included?

---

### Post by ow50 on 2005-05-18
[QUOTE=rwabel]does the version in breezy also have the amule daemon and webserver included?[/QUOTE]
The breezy version built only amule and amule-utils. The vollstrecker cvs version builds absolutely everything.

---

### Post by rwabel on 2005-05-18
[QUOTE=ow50]The breezy version built only amule and amule-utils. The vollstrecker cvs version builds absolutely everything.[/QUOTE]
 that was I was thinking. I wait for vollstrecker to fix his autobuild script so he can update amule :-)

---

### Post by jdong on 2005-05-18
AMule is imported into Sid already -- I'll backport it.

---

### Post by jdong on 2005-05-18
Alright, the deed is done :)

---

### Post by daniel311 on 2005-05-18
[QUOTE=ow50]Here's a gtk2 deb for hoary that I built from the breezy source:
[http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.0-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.0-1_i386.deb)[/QUOTE]
Thank you! The package works like a charm...

---

### Post by Dax0r on 2005-05-19
[QUOTE=jdong]Alright, the deed is done :)[/QUOTE]

I enabled the mirror but the avaliable version isn't the 2.0   :-?

---

### Post by jdong on 2005-05-19
It should be now.

Remember that mirrors are on a five-hour sync.

---

### Post by Dax0r on 2005-05-19
> Remember that mirrors are on a five-hour sync. 

I think that it's a my problem.
I enable too the official backports,and i run apt-get update but i get "your system is update"...Why?

---

### Post by jdong on 2005-05-19
It's currently in the staging (beta-testing) branch.

---

### Post by Dax0r on 2005-05-20
I installed amule 2.0 from backports,but it'is in gtk1,why?

---

### Post by ow50 on 2005-05-20
[QUOTE=Dax0r]I installed amule 2.0 from backports,but it'is in gtk1,why?[/QUOTE]
It seems jdong didn't alter the original source which is gtk1 for some reason I'm not sure of. Get the deb I posted earlier in this thread, that's gtk2.

---

### Post by jdong on 2005-05-20
Hmm, so the Debian version is GTK1?!?!

---

### Post by rpgcyco on 2005-05-20
> It seems jdong didn't alter the original source which is gtk1 for some reason I'm not sure of. Get the deb I posted earlier in this thread, that's gtk2.

Is it possible you can please make a DEB of 2.0.1 when it's in the Breezy repos, like you did for 2.0.0?

> Hmm, so the Debian version is GTK1?!?!

Yeah, just like the the one in Breezy as well. :)

- Rpg Cyco

---

### Post by ow50 on 2005-05-20
[QUOTE=rpgcyco]Is it possible you can please make a DEB of 2.0.1 when it's in the Breezy repos, like you did for 2.0.0?[/QUOTE]
Yes. Of course. I keep an eye on debian unstable. Once it's there I'll build it.


The reason for gtk1 seems to be powerpc:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=308874](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=308874) 
[QUOTE=Julien Delange]No, aMule is compiled against gtk1.2, because it can't compile with gtk2
on powerpc. So, if I make a release with gtk2, powerpc users can't have
the package, and it's not the debian policy.

Of course, when it can be possible, I will release as soon as possible.
But now, I prefer to keep gtk1.2, and make release for everybody.[/QUOTE]

---

### Post by ow50 on 2005-05-20
aMule 2.0.1 gtk2:
[amule_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.1-1_i386.deb)
[amule-utils_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule-utils_2.0.1-1_i386.deb)

Source was debian unstable. Changed dependencies to gtk2 and wx 2.5.

---

### Post by Teo on 2005-05-21
[QUOTE=ow50]aMule 2.0.1 gtk2[/QUOTE]
THX so mutch for aMule@GTK2 :)

BTW: thtis is my first post on this forum, so Hello to all :]

---

### Post by joele on 2005-05-24
[QUOTE=ow50]aMule 2.0.1 gtk2:
[amule_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.1-1_i386.deb)
[amule-utils_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule-utils_2.0.1-1_i386.deb)

Source was debian unstable. Changed dependencies to gtk2 and wx 2.5.[/QUOTE]

Thanks for that!

---

### Post by bored2k on 2005-05-24
[QUOTE=ow50]aMule 2.0.1 gtk2:
[amule_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.1-1_i386.deb)
[amule-utils_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule-utils_2.0.1-1_i386.deb)

Source was debian unstable. Changed dependencies to gtk2 and wx 2.5.[/QUOTE]
 "Thank you thank you... far too kind"

---

### Post by rpgcyco on 2005-06-04
Hey ow50,

I was wondering if it's possible for you to make a gtk2 and wx 2.5 DEB package for aMule 2.0.2, which was just recently released? It fixes a bug I recently experienced (**Fixed a hang-on-exit-using-100%-cpu bug**). I had to hard reset, which makes me feel dirty, lol.

Thanks,
- Rpg Cyco

---

### Post by ow50 on 2005-06-04
[QUOTE=rpgcyco]I was wondering if it's possible for you to make a gtk2 and wx 2.5 DEB package for aMule 2.0.2, which was just recently released?[/QUOTE]
I think I'll build the Vollstreckner CVS debs tomorrow (or whenever they're next released) and the official 2.0.2 once it hits debian unstable. Those Vollstreckner debs have some unstable CVS stuff that's not in 2.0.2.

I could do official backports debs as well, but Breezy's still at 2.0.0, so those might take a while.

---

### Post by rwabel on 2005-06-05
the strange thing is that I still hve 100% cpu problems with the newest cvs from vollstrecker. does anybody have it too?

---

### Post by ow50 on 2005-06-05
I uploaded today's Vollstrecker CVS aMule deb:
[amule_2.0.2+CVS20050605-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.2+CVS20050605-1_i386.deb)

Check the directory for rest of the packages:
[http://koti.mbnet.fi/ots/linux/hoary/](http://koti.mbnet.fi/ots/linux/hoary/)

I haven't used this long enough to tell whether it's stable or not and I never experienced the 100% CPU usage bug so I can't tell whether it's fixed or not.

Of the dependecies, you'll need libgcc1 from backports, rest should standard Hoary stuff.

---

### Post by rpgcyco on 2005-06-05
Thanks ow50! I'll let it run overnight and report back in the morning. :)

- Rpg Cyco

---

### Post by rpgcyco on 2005-06-06
Dang, it crashed. I've reverted back to 2.0.1 for now. :)

- Rpg Cyco

---

### Post by RastaMahata on 2005-06-10
[QUOTE=ow50]aMule 2.0.1 gtk2:
[amule_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule_2.0.1-1_i386.deb)
[amule-utils_2.0.1-1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/amule-utils_2.0.1-1_i386.deb)

Source was debian unstable. Changed dependencies to gtk2 and wx 2.5.[/QUOTE]
 why isnt this submitted to backports? :( (2.0.1)

---

### Post by rpgcyco on 2005-06-11
Do you mean 2.0.1 or 2.0.1 compiled against GTK2 and libwxgtk2.5? If the mean the latter, then it's because that can't be done for PowerPC. If you mean the former, I don't know. :P

- Rpg Cyco

---

### Post by sapo on 2005-06-11
I have the old amule installed here..

Am i going to lost my downloads if a install this 2.0?

thanx

---

### Post by bored2k on 2005-06-11
[QUOTE=sapo]I have the old amule installed here..

Am i going to lost my downloads if a install this 2.0?

thanx[/QUOTE]
 No.

---

### Post by ow50 on 2005-06-11
[QUOTE=RastaMahata]why isnt this submitted to backports? :( (2.0.1)[/QUOTE]
I believe it breaks the new rules of backporting only from Breezy. Breezy's still at 2.0.0.

For the current backports, that compile all architectures separately and provide only binaries, the gtk2 switch could be done for i386. But, if backports are moving into the ubuntu build system, the switch to gtk2 probably cannot be done, as it wouldn't work for powerpc.

---

### Post by makhand on 2005-06-15
I have 2.0.0. For some reason, it hasnt been able to 'complete' any of the files. Anyone else find a problem with this? I spend 2 days downloading stuff, and now its just stuck on 'Completing' and never gets to 'complete'. Is there anything i can do with these files like rename them or something?

---

### Post by ow50 on 2005-06-15
[QUOTE=makhand]Is there anything i can do with these files like rename them or something?[/QUOTE]
In the transfers window, right click on the file and select "Show file details". Look at the number under "met-File". Next find the part file (extension .part) with the corresponding number in your download temp directory and rename it to whatever you want. That should be your file.

Note that renaming the part file is a hack, not a proper solution. if you haven't fully downloaded the file, the renamed part file might be unusable depending on the filetype. After aMule finishes a download, it checks the hash. If that's the part where you're stuck, the renamed part file might be usable.

---

### Post by Seth on 2005-06-15
[QUOTE=RastaMahata]why isnt this submitted to backports? :( (2.0.1)[/QUOTE]
I still think that if we knew that packages would enter breezy before the freeze (e.g., this early in a release cycle), we should just backport whatever.

---

### Post by ow50 on 2005-06-16
aMule 2.0.3 has been released.

I compiled the Vollstrecker CVS debs again:
[http://koti.mbnet.fi/ots/linux/hoary/](http://koti.mbnet.fi/ots/linux/hoary/)

I have learned to use chroot, so the packages now have no non-hoary dependencies. Also, I added "~ots" (my initials) to the version number. I also rebuilt 2.0.1 with these changes.

---

### Post by jdong on 2005-06-16
[QUOTE=Seth]I still think that if we knew that packages would enter breezy before the freeze (e.g., this early in a release cycle), we should just backport whatever.[/QUOTE]
Bad assumption. I actually backported Synaptic early in Hoary development by applying Ubuntu patches to Sid archives (numerous APT integration bugfixes), but the snapshot never came. That caused many people upgrade problems.

---

### Post by ow50 on 2005-06-22
2.0.3 showed up in debian unstable. I built that
[http://koti.mbnet.fi/ots/linux/hoary/](http://koti.mbnet.fi/ots/linux/hoary/)

Also, 2.0.1 is now in breezy.

---

### Post by rpgcyco on 2005-06-23
Thank you once again. All is working well. :)

- Rpg Cyco

---

### Post by pedrorolo on 2005-06-30
[QUOTE=ow50]2.0.3 showed up in debian unstable. I built that
[http://koti.mbnet.fi/ots/linux/hoary/](http://koti.mbnet.fi/ots/linux/hoary/)

Also, 2.0.1 is now in breezy.[/QUOTE]

the current version isn't working fine:
```

psmmr@rolo:~/Desktop/ubuntuamule $ sudo dpkg -i amule_2.0.3-1~ots_i386.deb
(A ler a base de dados ... 145741 ficheiros e directórios actualmente instalados.)
Preparando para substituir amule 1.2.6+rc7-2 (a usar amule_2.0.3-1~ots_i386.deb) ...
Leaving `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule'
Leaving `diversion of /usr/share/man/man1/ed2k.1.gz to /usr/share/man/man1/ed2k.xmule.1.gz by amule'
A descompactar substituto amule ...
dpkg-deb (subprocesso); foi lido um short em buffer_copy (não foi possível escrever para o pipe na cópia)
dpkg-deb: subprocesso paste retornou erro do status de saída 2
dpkg: erro ao processar amule_2.0.3-1~ots_i386.deb (--install):
 foi lido um short em buffer_copy (backend dpkg-deb durante `./usr/bin/amule')
Foram encontrados erros enquanto processava:
 amule_2.0.3-1~ots_i386.deb

```

it has been read a short in buffer_copy (it wasn't possible to write ot the pipe during the copy)

---

### Post by pedrorolo on 2005-06-30
[QUOTE=pedrorolo]the current version isn't working fine:
```

psmmr@rolo:~/Desktop/ubuntuamule $ sudo dpkg -i amule_2.0.3-1~ots_i386.deb
(A ler a base de dados ... 145741 ficheiros e directórios actualmente instalados.)
Preparando para substituir amule 1.2.6+rc7-2 (a usar amule_2.0.3-1~ots_i386.deb) ...
Leaving `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule'
Leaving `diversion of /usr/share/man/man1/ed2k.1.gz to /usr/share/man/man1/ed2k.xmule.1.gz by amule'
A descompactar substituto amule ...
dpkg-deb (subprocesso); foi lido um short em buffer_copy (não foi possível escrever para o pipe na cópia)
dpkg-deb: subprocesso paste retornou erro do status de saída 2
dpkg: erro ao processar amule_2.0.3-1~ots_i386.deb (--install):
 foi lido um short em buffer_copy (backend dpkg-deb durante `./usr/bin/amule')
Foram encontrados erros enquanto processava:
 amule_2.0.3-1~ots_i386.deb

```

it has been read a short in buffer_copy (it wasn't possible to write ot the pipe during the copy)[/QUOTE]
 i tryied the amule2.0.3+CVS* and it worked fine

---

### Post by FilipeAC on 2005-07-12
@ow50

Amule doesn't work so well when compiled with GTK2, as you can check out:
[http://forum.amule.org/thread.php?threadid=6760&sid=65bac790bffe3f52d3752bd59fa889ad](http://forum.amule.org/thread.php?threadid=6760&sid=65bac790bffe3f52d3752bd59fa889ad)

After running for about one day amule uses almost all available memory.
So it'd be better compiling it with GTK1 (despite the awful look).

---

### Post by pulp on 2005-07-12
[QUOTE=FilipeAC]@ow50

Amule doesn't work so well when compiled with GTK2, as you can check out:
[http://forum.amule.org/thread.php?threadid=6760&sid=65bac790bffe3f52d3752bd59fa889ad](http://forum.amule.org/thread.php?threadid=6760&sid=65bac790bffe3f52d3752bd59fa889ad)

After running for about one day amule uses almost all available memory.
So it'd be better compiling it with GTK1 (despite the awful look).[/QUOTE]

I agree. 2.0.3 compiled against GTK1 would be fantastic. Especially on older machines it would be much faster in its look & feel.

---

### Post by ow50 on 2005-07-12
[QUOTE=FilipeAC]@ow50

Amule doesn't work so well when compiled with GTK2, as you can check out:
[http://forum.amule.org/thread.php?threadid=6760&sid=65bac790bffe3f52d3752bd59fa889ad](http://forum.amule.org/thread.php?threadid=6760&sid=65bac790bffe3f52d3752bd59fa889ad)

After running for about one day amule uses almost all available memory.
So it'd be better compiling it with GTK1 (despite the awful look).[/QUOTE]

I wasn't aware of this even though I often run aMule 24/7. Just to make sure, are you using hoary's wx (version 2.5.3)?

I just submitted GTK2 aMule 2.0.3 to backports (I think it's still in staging) and hence took it off my own webspace. If this indeed is a problem, maybe I should resubmit a GTK1 version and go back to hosting the GTK2 on my own webspace.

---

### Post by ow50 on 2005-07-12
I think I'll leave the fate of the backport package to the backport developers.

I'm hosting the GTK2 version again at:
[http://koti.mbnet.fi/ots/linux/hoary/](http://koti.mbnet.fi/ots/linux/hoary/)

---

### Post by rwabel on 2005-07-12
what's interesting is, that the CVS debs from vollstrecker are newly also again with gtk1. I don't know, but at least 1 weeks it's now again with gtk1...in the last time gtk2 did work fine for me...well doesn't matter, as longs as the mule is running :-)

---

### Post by FilipeAC on 2005-07-12
[QUOTE=ow50]I wasn't aware of this even though I often run aMule 24/7. Just to make sure, are you using hoary's wx (version 2.5.3)?

I just submitted GTK2 aMule 2.0.3 to backports (I think it's still in staging) and hence took it off my own webspace. If this indeed is a problem, maybe I should resubmit a GTK1 version and go back to hosting the GTK2 on my own webspace.[/QUOTE]

I think I used your builts for about a month before noticing it ('cause I only use that pc as an internet router and for aMule downloads, so it wouldn't matter the memory usage, it was only aMule, samba and iptables running:D).

Well, after noticing, I did a clean install of Kubuntu Hoary (so, yeah, wxGTK 2.5.3) and installed xfce4 just in case KDE was the evil one  :twisted: 

But the memory usage didn't drop even with xfce4, so I was looking for an answer on aMule forums and I found that guy with the same issue I had...

Anyway, I compiled aMule with GTK 1 today, so maybe tomorrow I'll reply here telling about the memory usage...
So far, so good, but it usually taked a day before the memory usage begins raising - today aMule was using 500MB of total memory (including swap and ram).


P.S.: GTK1 is too damn ugly.  :-P

---

### Post by FilipeAC on 2005-07-15
Sorry for double posting, but... 
After more than 2 days of running time, aMule's memory usage keeps normal, finally (top says 24MB of resident size and 53MB of virtual image - waaaay below the 500MB it was showing before I compiled aMule). So I guess it was indeed GTK2+wx fault... 

And, I'm not very sure, but CPU usage seems to be lower as well.

Other info, if you may care:
Kubuntu Hoary running either xfce4 v4.2.1.1 or KDE 3.4
~$ uname -sro
Linux 2.6.10-5-386 GNU/Linux
~$ amule --version
aMule 2.0.3 using wxGKT1 v2.4.2 (OS: Linux)

---

