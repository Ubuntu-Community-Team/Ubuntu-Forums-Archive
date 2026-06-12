---
title: "Using smart package manager in Ubuntu hoary"
date: 2004-12-13
forum: The Cafe
---

### Post by retype on 2004-12-13
What about using [Smart](http://www.smartpm.org/) in ubuntu hoary by default? I am using it in warty and it works nicely (I found a bug in inserting new channels using the gui, but besides that...). It resolves problems installing packages that apt/synaptic can't handle. Maybe it would be a good idea, it is made in python and C. What is you opinion?

ps. If someone thinks it is dificult to install it I will give some more indepth help, but basically you need gcc and python-dev. Then execute python setup.py install, and then to insert a new channel you have to read the docs, but you need at least one deb-sys channel.

---

### Post by EdCrypt on 2004-12-13
[QUOTE=retype]What about using [Smart](http://www.smartpm.org/) in ubuntu hoary by default? I am using it in warty and it works nicely (I found a bug in inserting new channels using the gui, but besides that...). It resolves problems installing packages that apt/synaptic can't handle. Maybe it would be a good idea, it is made in python and C. What is you opinion?

ps. If someone thinks it is dificult to install it I will give some more indepth help, but basically you need gcc and python-dev. Then execute python setup.py install, and then to insert a new channel you have to read the docs, but you need at least one deb-sys channel.[/QUOTE]
A .deb in hoary would be cool.

---

### Post by jdong on 2004-12-13
I would like this in the next Ubuntu release, after Hoary.

Smart is too new, and therefore too bleeding-edge to deploy in production environments...

---

### Post by jdodson on 2004-12-13
[QUOTE=retype]What about using [Smart](http://www.smartpm.org/) in ubuntu hoary by default? I am using it in warty and it works nicely (I found a bug in inserting new channels using the gui, but besides that...). It resolves problems installing packages that apt/synaptic can't handle. Maybe it would be a good idea, it is made in python and C. What is you opinion?

ps. If someone thinks it is dificult to install it I will give some more indepth help, but basically you need gcc and python-dev. Then execute python setup.py install, and then to insert a new channel you have to read the docs, but you need at least one deb-sys channel.[/QUOTE]

cool, this would be good as a alternative to synaptic.

---

### Post by jdong on 2004-12-13
*** Packages for Debian (under work!)


As soon as debian packages come out, I'll definitely do a Warty extras with this, so we can start testing...


However, I don't have much faith in this package manager... Especially like with Fedora, all Fedora KDE apps (Amarok, whatever) will be linked to Fedora's castrated KDE edition, which won't be binary-compatible with , say, Debian's KDE.

Heck you can't safely mix Hoary binaries with Warty's , how can you expect to mix across distributions??

---

### Post by EdCrypt on 2004-12-14
[QUOTE=jdong]
Heck you can't safely mix Hoary binaries with Warty's , how can you expect to mix across distributions??[/QUOTE]
Ok, Let's go again...
[QUOTE=http://www.smartpm.org/]Notice that this project is **not **a magical bridge between every distribution in the planet. Instead, this is a software offering **better package management** for these distributions, even when working with their **own packages**. Using multiple package managers at the same time (like rpm and dpkg) is possible, even though not the software goal at this moment[/QUOTE] 
[http://ubuntuforums.org/showpost.php?p=33113&postcount=9](http://ubuntuforums.org/showpost.php?p=33113&postcount=9)

---

### Post by jdong on 2004-12-14
Yeah.... The first part is what I'm saying. The second part, I don't agree with.


Try installing kdelibs from Fedora with SMART... Look at what a **mess** is left in /usr -- all the so's are in the wrong places, it's a big mess!

Now, if we had this thing in Hoary, we'd have users here reporting strange problems with packages, and we wouldn't know where to **start** with helping.

Also, smart is in **BETA** status right now -- it's definitely not going to be ready for production use in Hoary.

I would love to see this for the next release though... And I will make experimental Ubuntu Warty/Hoary debs as soon as I see Debian packages released on Smart's site... We as the community need to test and tweak this powerful tool!

---

### Post by EdCrypt on 2004-12-14
[QUOTE=jdong]Yeah.... The first part is what I'm saying. The second part, I don't agree with.


Try installing kdelibs from Fedora with SMART... Look at what a **mess** is left in /usr -- all the so's are in the wrong places, it's a big mess!

Now, if we had this thing in Hoary, we'd have users here reporting strange problems with packages, and we wouldn't know where to **start** with helping.
[/QUOTE]
Mixing packages from diferent distros, i agree, is not good (that's why many people say that rpm is doomed, it's ease to mix packages from fedora, mandrake, suse, conectiva, etc etc  searching things in the internet). But do you installed kdelibs from Fedora with SMART? In that quote that i taked from the site, it's not possible yet and not the focus of the project.
Using Smart on Hoary you will get only Hoary packages.
And yes, it is not stable yet. But i think it could be in the hoary's universe.
Hey, and the Update Manager, Upgrade Notifier and Application Installer? Aren't it writen little time ago? will it be keep on the hoary until the release?

---

### Post by jdong on 2004-12-14
[QUOTE=EdCrypt]
And yes, it is not stable yet. But i think it could be in the hoary's universe.
Hey, and the Update Manager, Upgrade Notifier and Application Installer? Aren't it writen little time ago? will it be keep on the hoary until the release?[/QUOTE]
Err, those are EXTREMELY basic and trivial wrappers around synaptic... they don't taint untested/unknown repositories into Ubuntu, and **most importantly**, they are simple projects that anyone can write in a month's time!

---

### Post by EdCrypt on 2004-12-14
[QUOTE=jdong]Err, those are EXTREMELY basic and trivial wrappers around synaptic... _***they don't taint untested/unknown repositories***_ into Ubuntu, and **most importantly**, they are simple projects that anyone can write in a month's time![/QUOTE]
Well, but i hope you don't think anymore that SMART do that...

---

### Post by retype on 2004-12-17
Smart is not beta, the first stable has been released and I used it without problems. I think it could work as the only package manager, doing everything including updates in hoary. There is already a kde applet that does this and ubuntu could use the code they have developed to make a gnome applet.

**I WILL SAY THIS AGAIN, WITH BOLD AND CAPS, YOU ARE NOT GOING TO INSTALL FEDORA PACKAGES IN ANY DEBIAN AND GET AWAY WITH IT, THIS IS A REALLY STUPID THING TO DO.** 

But I really think that using it in ubuntu would give an advantage to the hole system package management. I really does the things apt should be doing, but in a clean and portable (but not hybrid (this second level parenthesis is to remind everyone to not mix apt-rpm or yum channels in an Ubuntu dist)) solution, and the update applet could be used by others distributions helping the hole linux community.

---

### Post by jdong on 2004-12-17
Does SMART act as a frontend over the other packaging tools, like Synaptic or KPackage is in relation to APT or RPM, or does SMART actually handle dependency resolving and REPLACE APT (Like up2date)?

If it was just another better frontend, then I'd have more tolerance for Smart.

---

### Post by asimon on 2004-12-18
[QUOTE=jdong]Does SMART act as a frontend over the other packaging tools, like Synaptic or KPackage is in relation to APT or RPM, or does SMART actually handle dependency resolving and REPLACE APT (Like up2date)?
[/QUOTE]
No, Smart is not another interface to apt like synaptic, you would use it instead of apt. You could see it as a frontend to dpkg, like yum is a frontend to rpm. Smart doesn't use apt, it's only dependency for deb support is dpkg.

Smart implements new and better algorithms than yum, apt, or urpmi to resolve dependencies. That is what Smart is all about, a more intelligent dependency resolver.

There are some case studies on the Smart website which show real-world dependency problems which yum and apt failed to resolve, but smart resolves them.

---

### Post by jdong on 2004-12-18
Ok, after reading some of the documentation, I'll let down my hostility shield...

**Making debs of SPM**

---

### Post by jdong on 2004-12-18
Ok, I have preliminary debs made. I'll think about what to do with them.

---

### Post by jdong on 2004-12-18
Smart Package Manager debs uploaded to my Warty-extras-staging area.

deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-extras-staging contrib universe

---

### Post by ubuntu_demon on 2004-12-18
i installed the debian package from smartpm.org on my hoary. It doesn't work. A hoary package would be handy.

smart output :
```

Traceback (most recent call last):
  File "/usr/bin/smart", line 27, in ?
    from smart.const import VERSION, DEBUG, DATADIR
ImportError: No module named smart.const

```

---

### Post by jdong on 2004-12-18
Does my warty .deb work in Hoary? Hoary should be 100% backwards-compatible with my build.

---

### Post by ubuntu_demon on 2004-12-19
[QUOTE=jdong]Does my warty .deb work in Hoary? Hoary should be 100% backwards-compatible with my build.[/QUOTE]
 I'll try and otherwise I'll just build the source or something :).

---

### Post by retype on 2004-12-24
Building from source is easy, but if someone made a debian package it will be easier, I made a script to import all sources from source.list to smart, If someone wants me to help in making it in the official package I would be very proud to help.

---

### Post by HiddenWolf on 2004-12-25
[QUOTE=jdodson]cool, this would be good as a alternative to synaptic.[/QUOTE]


Alternative to the best software-package I've ever seen....
Blasphemy

---

### Post by EdCrypt on 2004-12-26
Smartpm .deb avaliable:
[http://people.labmice.com.br/rst/stuff/debian/](http://people.labmice.com.br/rst/stuff/debian/)

---

### Post by rwabel on 2005-01-03
[QUOTE=demon666_nl]i installed the debian package from smartpm.org on my hoary. It doesn't work. A hoary package would be handy.

smart output :
```

Traceback (most recent call last):
  File "/usr/bin/smart", line 27, in ?
    from smart.const import VERSION, DEBUG, DATADIR
ImportError: No module named smart.const

```[/QUOTE]

I get the exact same error message with the debian package from the smart homepage. I then took the warty backport even I run hoary. Same problem. Don't know what the problem is. Anyone achieved make it run under hoary?

---

### Post by jdong on 2005-01-03
[QUOTE=EdCrypt]Smartpm .deb avaliable:
[http://people.labmice.com.br/rst/stuff/debian/](http://people.labmice.com.br/rst/stuff/debian/)[/QUOTE]

Without sources or , more importantly, the necessary diff.gz debianized patch to the source. VERY helpful...

---

### Post by Randabis on 2005-01-03
so how do you effectively add sources to it?

I tired but it doesn't seem to fetch the information.

---

### Post by nuopus on 2005-01-05
[QUOTE=jdong]*** Packages for Debian (under work!)


As soon as debian packages come out, I'll definitely do a Warty extras with this, so we can start testing...


However, I don't have much faith in this package manager... Especially like with Fedora, all Fedora KDE apps (Amarok, whatever) will be linked to Fedora's castrated KDE edition, which won't be binary-compatible with , say, Debian's KDE.

Heck you can't safely mix Hoary binaries with Warty's , how can you expect to mix across distributions??[/QUOTE]
 Because it allows you to specify priorities to each repository or channel. I have added hoary and made it top priority. It does not mess anything up since it always takes from the hoary repository ... and if it is not in hoary it will go to the warty ones. You can also specify priorities to individual packages and say ... only update mplayer from THIS repo whenever you do an update.  You can force a version with synaptic ... but when you update there are no priorities and will go to whichever one.

---

### Post by rwabel on 2005-01-05
[QUOTE=nuopus]Because it allows you to specify priorities to each repository or channel. I have added hoary and made it top priority. It does not mess anything up since it always takes from the hoary repository ... and if it is not in hoary it will go to the warty ones. You can also specify priorities to individual packages and say ... only update mplayer from THIS repo whenever you do an update.  You can force a version with synaptic ... but when you update there are no priorities and will go to whichever one.[/QUOTE]

Did you achieve to make it work under hoary? Can you explain the steps?
thanks

---

### Post by nuopus on 2005-01-05
[QUOTE=rwabel]Did you achieve to make it work under hoary? Can you explain the steps?
 thanks[/QUOTE]
  Yes. Just add a new channel with [http://archive.ubuntulinux.org/ubuntu]("http://archive.ubuntulinux.org/ubuntu") as the location, warty as distrib and main restricted universe multiverse. I then set the priority of the warty channel to -10 and the priority of the hoary one to 1.
 
 After that you then have to go and hit the reload button. You can then do a full upgrade and it will only upgrade from warty since the priority of it is so much higher than warty.
 
 Another advantage is you can set an individual package from warty to higher than the hoary ones so when you upgrade you only get that ONE package upgraded from warty. Works very nice for buggy packages that you want to keep the warty version for.

---

### Post by nuopus on 2005-01-05
[QUOTE=rwabel]Did you achieve to make it work under hoary? Can you explain the steps?
thanks[/QUOTE]
 I think I am going to get brave and try to add an rpm repository to it too just to see if it will work. I should though ... as long as I set the priority to -10 and change warty to -9 or something. Will let you know if it works!

---

### Post by rwabel on 2005-01-05
[QUOTE=nuopus]Yes. Just add a new channel with [http://archive.ubuntulinux.org/ubuntu]("http://archive.ubuntulinux.org/ubuntu") as the location, warty as distrib and main restricted universe multiverse. I then set the priority of the warty channel to -10 and the priority of the hoary one to 1.
 
 After that you then have to go and hit the reload button. You can then do a full upgrade and it will only upgrade from warty since the priority of it is so much higher than warty.
 
 Another advantage is you can set an individual package from warty to higher than the hoary ones so when you upgrade you only get that ONE package upgraded from warty. Works very nice for buggy packages that you want to keep the warty version for.[/QUOTE]

That sounds great, my problem is already with smart. How the heck did you make smart work? I always get the same message:
Traceback (most recent call last):
  File "/usr/bin/smart", line 27, in ?
    from smart.const import VERSION, DEBUG, DATADIR
ImportError: No module named smart.const

---

### Post by jdong on 2005-01-05
Please stay on the topic of discussing Smart and Hoary, problems with installing smart.

---

### Post by nuopus on 2005-01-05
[QUOTE=rwabel]That sounds great, my problem is already with smart. How the heck did you make smart work? I always get the same message:
Traceback (most recent call last):
  File "/usr/bin/smart", line 27, in ?
    from smart.const import VERSION, DEBUG, DATADIR
ImportError: No module named smart.const[/QUOTE]
 go to the console and type sudo smart --gui. You can also create a .desktop file and have it execute gksudo smart --gui so that you can just click an icon and run it.

---

### Post by rwabel on 2005-01-05
[QUOTE=nuopus]go to the console and type sudo smart --gui. You can also create a .desktop file and have it execute gksudo smart --gui so that you can just click an icon and run it.[/QUOTE]

that's what I tried.
[I]rwabel@RALPH:~/disksearch-1.1.0 $ sudo smart --gui
Password:
Traceback (most recent call last):
  File "/usr/bin/smart", line 27, in ?
    from smart.const import VERSION, DEBUG, DATADIR
ImportError: No module named smart.const[/I]


I don't know if I need to configure something or change something.

---

### Post by nuopus on 2005-01-05
[QUOTE=rwabel]that's what I tried.
 [i]rwabel@RALPH:~/disksearch-1.1.0 $ sudo smart --gui
 Password:
 Traceback (most recent call last):
   File "/usr/bin/smart", line 27, in ?
     from smart.const import VERSION, DEBUG, DATADIR
 ImportError: No module named smart.const[/i]
 
 
 I don't know if I need to configure something or change something.[/QUOTE]
 
 Sounds like a Python error. Try removing and re-installing python and smart.

---

### Post by rwabel on 2005-01-06
[QUOTE=nuopus]Sounds like a Python error. Try removing and re-installing python and smart.[/QUOTE]

thanks for the help. The problem was that I took the wrong smart version. I had to take smartpm version and not the posted repository for warty.

Now I can start trying it out

---

### Post by mattblack_uk on 2005-06-04
So... just run that by me again. If you got it to work on Hoary, where did you get the package from? I've tried the universe package, the debian package which is linked from the [www.smartpm.org](www.smartpm.org) page, and compiling from the debian source from the same place... all give me errors similar to ones already mentioned here. I installed all dependancies needed. The debian package wouldn't install as it wouldn't let me install python2.3-gtk2 as python2.4-gtk2 was already installed. 

When I installed from source, all I did was a make, and make install. It didn't create a make uninstall, so how do I get rid of it? I'm quite a newbie and haven't got a clue.

---

### Post by rwabel on 2005-06-04
[QUOTE=mattblack_uk]So... just run that by me again. If you got it to work on Hoary, where did you get the package from? I've tried the universe package, the debian package which is linked from the [www.smartpm.org](www.smartpm.org) page, and compiling from the debian source from the same place... all give me errors similar to ones already mentioned here. I installed all dependancies needed. The debian package wouldn't install as it wouldn't let me install python2.3-gtk2 as python2.4-gtk2 was already installed. 

When I installed from source, all I did was a make, and make install. It didn't create a make uninstall, so how do I get rid of it? I'm quite a newbie and haven't got a clue.[/QUOTE]
 I'm not sure about where I got the packages now. But doesn't hoary come with a package?

---

### Post by mattblack_uk on 2005-06-04
No, its in the Universe repository - and doesn't work.

---

### Post by rwabel on 2005-06-04
[QUOTE=mattblack_uk]No, its in the Universe repository - and doesn't work.[/QUOTE]
 I've version 0.29.2 from universe. What doesn't work or what is the problem witht he package? I can't remember how to use it :-)

---

### Post by mattblack_uk on 2005-06-04
OK... I've reinstalled the 0.29 version from Universe. If I run:

> sudo smart --shell 

then it runs fine, however if I run:

> sudo smart --gui 

then it gives me the following:

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Traceback (most recent call last):
  File "/usr/bin/smart", line 184, in ?
    main(sys.argv[1:])
  File "/usr/bin/smart", line 153, in main
    forcelocks=opts.ignore_locks, loglevel=opts.log_level)
  File "/usr/lib/python2.4/site-packages/smart/__init__.py", line 109, in init
    iface.object = createInterface(ifacename, ctrl, command, argv)
  File "/usr/lib/python2.4/site-packages/smart/interface.py", line 144, in createInterface
    smart = __import__("smart.interfaces."+xname)
  File "/usr/lib/python2.4/site-packages/PIL/__init__.py", line 29, in ?

  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?    from _gtk import *
RuntimeError: could not open display


---

### Post by rwabel on 2005-06-04
that's strange, because I'm using the same version and it's working fine. I really have no clue what this error message is. did u try to google after it?

---

### Post by mattblack_uk on 2005-06-05
I tried googling for this:

> Xlib: connection to ":0.0" refused by server

but it came up with many different responses and as somebody relatively new top linux, I struggled to understand any of them. Some were talking of problems with permissions and X server but to be honest, most of it went straight over my head...

I tried reinstalling python and smart, but it made no difference to the error....

guess I'm a bit useless at this kind of stuff....

---

### Post by rwabel on 2005-06-05
I don't think the problem with smart is related with 
 ```
Xlib: connection to ":0.0" refused by server
``` 
It seems more that something is wrong configured within smart

With the following command you can use smart without any problems? This would mean that smart is working but only in shell!
 ```
 smart --shell 
```

maybe u are also missing channels. what does this command say
 ```
smart channel --show 
```

with the command 
```
smart channel --add
```  

you can add somehow channels.

I've no big experience with that tool and I've never used it.
Maybe there is someone around who know SMART a bit and can explain the error message. And maybe some of my adived can help u.

Good luck and let me know

---

### Post by mattblack_uk on 2005-06-06
Ok.. I'll have a look at the channels tonight, but as far as I understand, the Hoary package has the channels already set up. If it continues to fail, then I may try the package in breezy.

---

### Post by mattblack_uk on 2005-06-06
I've worked out how to add the Hoary channels, and I can get smart working via the shell no problems, but still can't get the gui. I'm guessing that its a problem with python-gtk2...

I've learnt a lot tonight - like what to do when I accidentally remove myself from the sudo group!
I won't be doing that again!

---

### Post by rwabel on 2005-06-06
did u try to completely remove python-gtk2 and reinstall it?
what version of it do u have installed?

---

### Post by SymGeosis on 2005-06-12
Has anybody gotten this to work with the backports repositories?

Getting SmartPM to work with the other repositories was cake but it appears to not know how to handle "Release" or "Release.gpg" being in "main/i386-binaries." I've tried modifying various fields via the shell and the gui to correct this but as of so far have been unsucessful.

Any suggestions?

---

### Post by geearf on 2005-08-04
I've just read this topic, and their website, this seems very nice, if it really resolves the problems it lists (which of course I already had).

Any news for this on breezy ?

---

