---
title: "Kubuntu or just debian with kde?"
date: 2006-02-24
forum: The Cafe
---

### Post by Jessevl on 2006-02-24
I can't choose between installing Kubuntu (I already did this actually) or installing debian and kde. In Kubuntu there are lots of programs I don't use, but will i miss any special features or Ubuntu specific apps?

Please give advantages and disadvantages for both of the options, it will certainly help me to make a descission.

---

### Post by Brunellus on 2006-02-24
you'll probably miss out on Ubuntu's stupendous hardware support.  Debian stable is stable but stolid on this front.

---

### Post by xequence on 2006-02-24
Ubuntu works on my computer, debian doesent.

---

### Post by Jessevl on 2006-02-24
And when i do a base(server) install of ubuntu and install kde (including xorg, kdm, etc.) on it will i still get those apps i don't need? or will I only get a clean kde install with some kde apps?

---

### Post by Adrian on 2006-02-24
Take a look at the **kde-core** package.

[http://packages.ubuntu.com/breezy/kde/kde-core](http://packages.ubuntu.com/breezy/kde/kde-core)

---

### Post by Sheinar on 2006-02-24
Kubuntu is still too buggy, so I'd say Debian with KDE. Only problem with Debian is the lack of updated packages, though you could upgrade to testing or unstable, but it's not recommended.

---

### Post by Jessevl on 2006-02-24
[QUOTE=Adrian]Take a look at the **kde-core** package.

[http://packages.ubuntu.com/breezy/kde/kde-core](http://packages.ubuntu.com/breezy/kde/kde-core)[/QUOTE]
Thanks, So when Install (K)Ubuntu-base and
*apt-get x-window-system-core kde-core kdm*
I will just get Kubuntu without all the apps?
And does it make any difference whether I use an Ubuntu or Kubuntu cd to install the base?

[QUOTE=Sheinar]Kubuntu is still too buggy, so I'd say Debian with KDE. Only problem with Debian is the lack of updated packages, though you could upgrade to testing or unstable, but it's not recommended.[/QUOTE]
I haven't found a bug ;)
But is it really? Kubuntu isn't in beta or alpha, is it?

---

### Post by xequence on 2006-02-24
> And does it make any difference whether I use an Ubuntu or Kubuntu cd to install the base?

No difference.


> But is it really? Kubuntu isn't in beta or alpha, is it?

Its been perfectly stable for me, and no, its not in beta or alpha.

---

### Post by BWF89 on 2006-02-24
[QUOTE=Jessevl]I can't choose between installing Kubuntu (I already did this actually) or installing debian and kde. In Kubuntu there are lots of programs I don't use, but will i miss any special features or Ubuntu specific apps?[/QUOTE]
Debian is has 14 install CD's (which includes KDE and Gnome). The various flavors of Ubuntu (Ubuntu, Kubuntu, Xubuntu, Nubuntu) is only 1 install cd.

Theres a big difference.

---

### Post by Sheinar on 2006-02-24
> **Jessevl]I haven't found a bug  said:**
> 
I've found quite a few, but if it's working for you without problems, go for Kubuntu instead. I probably would still be using Kubuntu if it wasn't for the problems I came across.

[QUOTE=BWF89]Debian is has 14 install CD's (which includes KDE and Gnome). The various flavors of Ubuntu (Ubuntu, Kubuntu, Xubuntu, Nubuntu) is only 1 install cd.
That's why most people just use the netinstall CD instead.

---

### Post by Bandit on 2006-02-24
[QUOTE=Sheinar]Kubuntu is still too buggy, so I'd say Debian with KDE. Only problem with Debian is the lack of updated packages, though you could upgrade to testing or unstable, but it's not recommended.[/QUOTE]
KDE is generaly more buggy I will never argue with that.
I just thought I would comment that I have KDE 3.5.1 on Kubuntu Breezy64bit using the 2.6.15 kernel I compiled my self and its extreamly rock solid and I have yeat to have a crash or lock up.
Now they have KDE stable, lets all pray they dont F' the next few versions and the 4.0 release up...
Cheers,
Joey

---

### Post by Jessevl on 2006-02-24
Ok, last question, what will happen when i change my sources.list to dapper and do an apt-get dist-upgrade? (when the stable release is there)

---

### Post by Iandefor on 2006-02-24
[quote=Jessevl]Ok, last question, what will happen when i change my sources.list to dapper and do an apt-get dist-upgrade? (when the stable release is there)[/quote] One of two things: One, the one that will almost certainly happen, is that it upgrades your existing installation to include Dapper Drake versions of all the packages on your system, or, two, the one that should only happen if you do some serious screwing around with Ubuntu beforehand, is that it breaks your system and you get to reinstall with the Dapper CD. But I can just about guarantee you that the second won't happen.

---

### Post by adamb10 on 2006-02-24
Kubuntu has got some things to work out.(use the kde control center instead of a windows like control panel).

---

### Post by polo_step on 2006-02-24
[FONT="Fixedsys"]Kubuntu 5.04 was wildly unstable on my machine.  Dunno about 5.10.[/FONT]

---

### Post by plb on 2006-02-24
I actually believe the latest pkgs kubuntu gets are modified versions from debian unstable. Debian unstable is usually good about having the latest KDE packages, gnome on the other hand is completely different. I believe it took four months to get 2.12 in there.

---

### Post by YourSurrogateGod on 2006-02-24
[QUOTE=polo_step][FONT="Fixedsys"]Kubuntu 5.04 was wildly unstable on my machine.  Dunno about 5.10.[/FONT][/QUOTE]
I haven't tried Kubuntu 5.04, but 5.10 is quite stable. I'm basing my comparison on Ubuntu 5.04 (which had its bouts of instability) and Ubuntu 5.10.

The only problem that I've noticed is that there are little annoying bugs that Gnome doesn't have...

---

### Post by YourSurrogateGod on 2006-02-24
[QUOTE=Jessevl]I can't choose between installing Kubuntu (I already did this actually) or installing debian and kde. In Kubuntu there are lots of programs I don't use, but will i miss any special features or Ubuntu specific apps?

Please give advantages and disadvantages for both of the options, it will certainly help me to make a descission.[/QUOTE]
If you don't want some programs, use synap to uninstall them.

From my experience with Linux distros, Ubuntu has some sick hardware compatibility. Whatever problem you have, it can be solved on these forums.

---

### Post by Jessevl on 2006-02-25
[QUOTE=Iandefor]One of two things: One, the one that will almost certainly happen, is that it upgrades your existing installation to include Dapper Drake versions of all the packages on your system, or, two, the one that should only happen if you do some serious screwing around with Ubuntu beforehand, is that it breaks your system and you get to reinstall with the Dapper CD. But I can just about guarantee you that the second won't happen.[/QUOTE] Can someone confirm that? and what will happen when I do it without the "dist" ? 

Actually I want to upgrade everything that's installed and I want to add the things like xgl and the other new features, but i don't want to install burner, bluetooth, irc, etc apps. Is this possible?

---

### Post by Iandefor on 2006-02-25
[quote=Jessevl]Can someone confirm that? and what will happen when I do it without the "dist" ? 

Actually I want to upgrade everything that's installed and I want to add the things like xgl and the other new features, but i don't want to install burner, bluetooth, irc, etc apps. Is this possible?[/quote] I believe you're only supposed to do it with "dist-upgrade", although nobody's stopping you from just doing a plain old upgrade. Once/if everything's updated, all you'd have to do to get xgl/compiz is use > sudo apt-get install xgl compiz Because they're both in the Dapper repositories. But, again, I wouldn't recommend using just a plain "upgrade".

---

### Post by Jessevl on 2006-02-25
[QUOTE=Iandefor]I believe you're only supposed to do it with "dist-upgrade", although nobody's stopping you from just doing a plain old upgrade. Once/if everything's updated, all you'd have to do to get xgl/compiz is use  Because they're both in the Dapper repositories. But, again, I wouldn't recommend using just a plain "upgrade".[/QUOTE]
OK, but will i miss some **new** feature's when I do an dist-upgrade? I will not have the dummy packages, or do i?

---

### Post by maagimies on 2006-06-14
Go with Kubuntu.
I'm not sure, but while I use Debian with KDE it's just more unstable then Kubuntu. Although Kubuntu's KDE is still more unstable then my Gentoo's or Arch's KDE. Weird eh? :D

btw does anyone know how you can remove all that kubuntu specific junk from KDE in Kubuntu? It's driving me mad :confused:
edit:
hmm, I didn't realize this was so old thread, I was in search...
I guess I'm now a thread necromancer ;)

---

### Post by Christmas on 2006-06-14
I tried Debian with KDE and didn't like it at all, it made me the impression of a second Windows Me. I don't know from where this "stability" thing is told about Debian, but for me it didn't show it. Apps crush like crazy. Kubuntu is way more polished and bug free in my opinion. If you still decide for Debian Sarge which comes with KDE 3.3.2 instead of 3.5.2 for Kubuntu, you'll have some problems with font sizes and also the applications are old. There's no advantage in Debian in my opinion.

---

### Post by Christmas on 2006-06-14
[quote=BWF89]Debian is has 14 install CD's (which includes KDE and Gnome). The various flavors of Ubuntu (Ubuntu, Kubuntu, Xubuntu, Nubuntu) is only 1 install cd.[/quote]
Yes but you can install Debian 3.1 Sarge with either GNOME or KDE (or both) only using the first two CDs.

---

### Post by pelle.k on 2006-06-14
@ maagimies:
Me too, me too...!
Well let's start this baby up once again then :)

Have you ever seen a default (original, straight from kde.org) KDE desktop? It's completely crowded with pointless (well, maybe not pointless but anyway) apps belonging to the groups kde-network, kde-multimedia and so on...
I would say kubuntu:s default KDE desktop is seriously slim compared to that...
An example is kmix, which belongs to kde-multimedia depends on kde-multimedia and thus drags in ALL other apps in kde-multimedia, but in kubuntu that is solved by the wonderful devs/maintainers by split packages.

---

### Post by maagimies on 2006-06-14
[QUOTE=pelle.k]@ maagimies:
Have you ever seen a default (original, straight from kde.org) KDE desktop? It's completely crowded with pointless (well, maybe not pointless but anyway) apps belonging to the groups kde-network, kde-multimedia and so on...
I would say kubuntu:s default KDE desktop is seriously slim compared to that...
An example is kmix, which belongs to kde-multimedia depends on kde-multimedia and thus drags in ALL other apps in kde-multimedia, but in kubuntu that is solved by the wonderful devs/maintainers by split packages.[/QUOTE]
Well yeah, it's cool that Kubuntu's more sleak, but I'm bothered by "little things" like the different Kcontrol which has problems with my localisation, and Konqueror's profiles. It would be great to have some parts of the "pure" desktop because they make more sense to me ;)

---

### Post by Christmas on 2006-06-14
Not necessarily the multitude of programs is an issue, you can remove them after the installation if they're a pain in the ***. Another bad thing for Debian is the way they look at you if you are a beginner. On IRC for example, I was afraid to ask some simple and newbie question just because there always was somebody starting flaming me. In LinuxQuestions forums I didn't stay too long, but they were warmer then the IRC fellows. No official forums, Ubuntu has this wonderful forum. 

Just to remind the IRC thing, as I come from Windows, I go to the official Debian IRC channel on freenode about a DC++ client or how to install this Linux DC++ port on Debian. OMG that was my biggest mistake! There was this guy who jumped and began to flame me, I shouldn't get help for such a thing, I shouldn't come to them to ask for help if I screw up my sytem installing the port. I didn't like Valknut and I couldn't get used to it, so looking for the alternative that seemed to fit my needs I managed to actually get zero help, nada.

---

### Post by maagimies on 2006-06-14
[QUOTE=Christmas]Just to remind the IRC thing, as I come from Windows, I go to the official Debian IRC channel on freenode about a DC++ client or how to install this Linux DC++ port on Debian. OMG that was my biggest mistake! There was this guy who jumped and began to flame me, I shouldn't get help for such a thing, I shouldn't come to them to ask for help if I screw up my sytem installing the port. I didn't like Valknut and I couldn't get used to it, so looking for the alternative that seemed to fit my needs I managed to actually get zero help, nada.[/QUOTE]
It's weird why Debian users are like that. When I'm at ANY other distro's forum/irc-channel/mailing list, everyone is supportive, likes to help and gives me a few pointers to get started. I still haven't found one place where a debian user would be like that.
Gentoo and Ubuntu people are always cool :D

---

### Post by Christmas on 2006-06-14
I'm sure that the Debian has competent and polite users, but on the other hand this script kiddies have the wrong impression that if they know 2-3 tricks in Linux and use Linux they are experts, which is not true. I mean, I don't know how hard to handle or how much programming and brain you needed to use Linux distros 5 years ago, but now... let's be serious, after you learn how to configure it, Linux with KDE or GNOME is twice easier to use and manipulate than Windows.

---

### Post by sharkboy on 2006-06-14
If you think debian sarge is too old, or if you have very new hardware, try out Debian SID (unstable). Its repository is updated a lot (hence the 'unstable' name), but the distro is generally very smooth and operatively stable -- especially when it comes to kde. (Exceptions do occur though, but that's usually ... instructive :). ) The kde user list is also very friendly and glad to help out with problems in my experience. And like someone said: use the netinstall iso.

---

### Post by Christmas on 2006-06-14
I won't change from Kubuntu, at least not right now, but I tried Debian Etch, which I couldn't get to install KDE from a 2-CD set. I guess they changed it from Sarge, where 2 CDs were enough to install both KDE and GNOME. I didn't have another blank CD to burn a third ISO so I gave up.

---

### Post by Lunixfanboy on 2006-06-14
[QUOTE=BWF89]Debian is has 14 install CD's (which includes KDE and Gnome). The various flavors of Ubuntu (Ubuntu, Kubuntu, Xubuntu, Nubuntu) is only 1 install cd.
Theres a big difference.[/QUOTE]Debian install is on ONE CD as well. The 14 CDs include EVERY ONE of the 20+ thousand packages in the Debian stable archives.

---

