---
title: "[idea] ies4linux .deb"
date: 2007-12-10
forum: Ubuntu Brainstorm
---

### Post by achadwick on 2007-12-10
I use ies4linux ([http://www.tatanka.com.br/]("http://www.tatanka.com.br/")) when developing websites to see what pages will look like to users stuck using IE. Essentially it operates as an installer-downloader script pulling IE packages from evolt and other sources and installing them into per-IE-version WINE environments. Quite clean, and it works (though you wouldn't use it as your main browser). I think it would be really nifty if Ubuntu users wanting IE could "install IE" - i.e. invoke ies4linux - from a regular package management interface; possibly even from Add/Remove Programs and multiverse. I'd be prepared to have a go at putting together a .deb that people could try out. Would anybody be interested in trying it out if I did?

Before you ask: yes, I know about ([http://ubuntuforums.org/showthread.php?t=370705]("http://ubuntuforums.org/showthread.php?t=370705") )and mhancoc7's good efforts in this, but his package doesn't really do what I want: it does indeed put ies4linux on the system, but the user is expected to run it for her or himself.

I've played with this software before ([http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?t=431]("http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?t=431")), and I think the best approach might be to create a central master installation of each IE at .deb postinst time, and then do the symlink trick I outlined in the ies4linux forum when the user invokes Internet Explorer via its entry in the GNOME/KDE/XFCE applications menu (blech).

I'm still trying to determine what the current state of play is with debianisations of ies4linux - I've left this project alone for way too long - but would anybody be willing to help out / advise / test the package if I tried to build such a thing here?

---

### Post by maybeway36 on 2007-12-10
The EULA for Internet Explorer requires a valid Windows license, so Ubuntu won't do it. However, someone else certainly could - anybody can make DEBs.

---

### Post by achadwick on 2007-12-10
> **maybeway36 said:**
> The EULA for Internet Explorer requires a valid Windows license, so Ubuntu won't do it. However, someone else certainly could - anybody can make DEBs.

Quite so: essentially the thing would be an installer package very like msttcorefonts: the only appropriate place for it would be multiverse (non-free, unsupported) software, or a third-party repository. ies4linux itself is GPLv2, but the same is not true of the bundles it downloads (to say the least).

Anyway, I'll give it a go and report back here when I have something built.

---

### Post by TheIdiotThatIsMe on 2007-12-10
> **achadwick said:**
> 
Anyway, I'll give it a go and report back here when I have something built.

Looking forward to it :)

---

### Post by achadwick on 2007-12-16
Okay, here's a source and .deb bundle for the latest Beta. Let me know if it breaks. This is a very early work in progress.

The .deb is compiled for Gutsy Gibbon i386: anything else, you'll have to try compiling from the source packages. BTW, remove the .txt extension from the .changes and .dsc files if you want to verify stuff: you're seeing an artefact of the board software there.

---

### Post by TooLz on 2007-12-18
Well being as I am in Gutsy x64, I had to do the tar.gz way, I thought that it would be helpful to let everyone know they will need to go to [http://www.cabextract.org.uk/](http://www.cabextract.org.uk/) and get the cabextract package for this to work.

After I downloaded that and installed it, I was able to run and install IEs4Linux and was very happy.  I have to visit a website for work often that isn't capable with Firefox, I think they're idiots for not making it work with any other browser but Internet Explorer, they're really excluding all other users, but I have to find some alternative and this was great.

Highly appreciated, keep up the great work Linux Community :)

EDIT: Thought I'd mention the reason the deb didn't work for me is because I am on a 64 bit version of Gutsy, not too sure why doing: 

sudo linux32 dpkg -i ies4linux_2.99.0-1_i386.deb

- didn't work for me, it just wasn't having it. lol..

Cya

---

### Post by achadwick on 2007-12-18
> **TooLz said:**
> Well being as I am in Gutsy x64, I had to do the tar.gz way, I thought that it would be helpful to let everyone know they will need to go to [http://www.cabextract.org.uk/](http://www.cabextract.org.uk/) and get the cabextract package for this to work.

I think cabextract is available from universe/utils for us 32-bit guys nd it can certainly just be installed in the usual way... Is the amd64 compile broken / missing?

> **TooLz said:**
> 
EDIT: Thought I'd mention the reason the deb didn't work for me is because I am on a 64 bit version of Gutsy, not too sure why doing: 

sudo linux32 dpkg -i ies4linux_2.99.0-1_i386.deb

- didn't work for me, it just wasn't having it. lol..

Could you paste (or [pastebin]("http://paste.ubuntu-nl.org/")) the error message you got? :lol: Actually, please do!

You know, technically my package is architecture independent (very), so quite why I'm going on about it being i386-only I don't know. Something for the TODO list perhaps, thanks for testing :)

But: would the setup part work at all under amd64? Not without some fiddling, I bet. How are 32-bit chroots/libs handled under Ubuntu these days? I need to understand this in order to test it; any pointers about Standard Approved Ubuntu or Debian Ways of running 32-bit X11 binaries on amd64 would be useful to me...

Annoyingly, my own amd64 box is running Debian and I can't just blat it and throw Ubuntu on it. I'll need to set up some sort of dual boot or virtualisation hackery to get this tested. If you're up for building from source and seeing how and where it breaks, and also how it could be hacked on to make it useful to 64-bit users that would be really cool. Thanks for testing so far!

---

### Post by achadwick on 2007-12-18
There is one known bug I'm also working on a fix for: if you choose to install ie5 or ie55 and turn off flash installations, launching ie5 or ie55 from the icon it sets up will fail silently because a .cab file wasn't downloaded. My fault, my apologies; for now, please install flash (or use ie6, which isn't broken). You can use

[INDENT]$ sudo dpkg-reconfigure ies4linux[/INDENT]

to go back and choose flash or deselect ie5 and ie55. BTW, the ieX scripts can be debugged by setting DEBUG to something other than undefined/blank and running them from a terminal.

---

### Post by achadwick on 2007-12-21
I've fixed the bug mentioned above, and added "support" for the ie7 beta to the downloader part. *dpkg-reconfigure* this package if you've installed it before and don't see the option to download ie7.

The ie7 beta has distinct problems on my box: it can get as far as the first page, but stops rendering halfway through, and starts consuming 100% CPU. Does this affect anyone else?

---

### Post by achadwick on 2007-12-21
Another bug that might cause you grief: when an IE is running, it holds the debconf database open, which will get in the way of package managers. This is a Bad Thing. I'll be working on a better way of getting system-level choices of IE through the user-level runtime stuff in the next revision.

---

### Post by loudnlownoma on 2007-12-21
Subscribed!  Will definitely be checking back here to try it out when I get home!  I use ies4linux on my laptop very frequently(I run a game in a local poker league and our tournament software runs from an .hta file, which IE has been about the only thing I had luck in opening it with, as well as for website building.)

A little on the noobie side myself, so I don't know how much assistance I'd be able to provide, but I figure the more real-world tests it gets, the more accurate the results can be, right?  :)

---

### Post by achadwick on 2008-01-11
I'm going to become a MOTU and get this into Multiverse, if I can. You can track the needs-packaging bug and its details at [https://bugs.launchpad.net/ubuntu/+bug/182008](https://bugs.launchpad.net/ubuntu/+bug/182008), and I'll keep updating here too.

---

### Post by Odd-rationale on 2008-01-12
Does your .deb install IEs4Linux for all users or just one?

I know there is a hack to get it working for mutliple users:
[http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?t=431](http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?t=431)

Thanks a lot!

---

### Post by Odd-rationale on 2008-01-12
I just installed the .deb. My problem is that I don't have an address bar. How do I get an address bar?

Thanks!

---

### Post by achadwick on 2008-01-13
> **Odd-rationale said:**
> Does your .deb install IEs4Linux for all users or just one?

I know there is a hack to get it working for mutliple users:
[http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?t=431](http://www.tatanka.com.br/ies4linux/forum/viewtopic.php?t=431)


For all users, but in a different way from the linked article. I should know because I wrote that post :)

What you get with my package is an up-front download into /var/cache for all users to run the install procedure from. When a user tries to run an ieX, you get the second half of a normal GUI-less ies4linux install into plain user-specific WINEPREFIXes.

Yeah, I know. It's wasteful of disk space, especially given WINE can do the symlink trick without the Win32 apps knowing about it. The problem is that ies4linux needs to run various SETUP.EXEs when it sets up a WINEPREFIX. Unfortunately, I can't think of a way of getting WINE to work in a $DISPLAY-less mode without disgusting Xvnc hacks. :(

I'll raise this with Sérgio, because you could in theory do the cabextract part up front to save some time. It should also be symlink-trick-compatible if WINE doesn't have to run up front.

---

### Post by achadwick on 2008-01-13
> **Odd-rationale said:**
> I just installed the .deb. My problem is that I don't have an address bar. How do I get an address bar?

View > Toolbars > Address Bar, in ie6 at least.

If this doesn't work for you, could you try:

[INDENT]$ mv ~/.ies4linux ~/.ies4linux.bak[/INDENT]

from a Terminal, and then try re-running Internet Explorer from your desktop menu? You can drop back to where you were before by quitting IE and doing:

[INDENT]$ mv ~/.ies4linux ~/.ies4linux.oldtest
$ mv ~/.ies4linux.bak ~/.ies4linux
$ rm -fr ~/.ies4linux.oldtest[/INDENT]

in a Terminal.

---

### Post by Odd-rationale on 2008-01-13
[quote=achadwick]For all users, but in a different way from the linked article. I should know because I wrote that post :)[/quote]

Wow! Small world...

Anyways, I don't have a toolbar either. I tried removing/backing-up the ~/.ies4linux folder. But still no toolbar.

I don't know whether this helps, but both times when I tried to start IEs4Linux for the first time from the desktop menu, I had to do the Wine Gecko Install thing. I don't remember doing that from the original script on the ies4linux website.

Thanks so much for your help.

Here's a screenshot of my problem.

EDIT: I installed ie6.

---

### Post by achadwick on 2008-01-14
> **Odd-rationale said:**
> Anyways, I don't have a toolbar either. I tried removing/backing-up the ~/.ies4linux folder. But still no toolbar.

I don't know whether this helps, but both times when I tried to start IEs4Linux for the first time from the desktop menu, I had to do the Wine Gecko Install thing. I don't remember doing that from the original script on the ies4linux website.

It shouldn't be wine-gecko these days at all - ies4linux tries to get you running with the IE rendering engine - that's sort of the point :( Would you mind pasting the output of 

[INDENT]$ dpkg -l ies4linux debconf debconf-2.0 wine cabextract wget curl unzip belocs-locales-bin libc6 awk gawk mawk  sed[/INDENT]

_[EDIT: that's all one line in a Terminal]_ into a PM or a pastebin and let me know whether you're running Gutsy Gibbon and what flavour of ubuntu/kubuntu/xubuntu you're running? I'll try to help you out as much as I can.

> **Odd-rationale said:**
> 
Thanks so much for your help.

Here's a screenshot of my problem.

That's wierd... I get everything you'd expect: menu bars, address bars etc. Do you get anything different when you type

[INDENT]DEBUG=1 /usr/bin/ie6[/INDENT]

in a terminal? If you uninstall the package, log out, and log in again, do you still see icons in the menu? If the answer to either question is "yes", you're seeing an old manual ies4linux install; perhaps a very old one.

---

### Post by Odd-rationale on 2008-01-14
Thanks so much, achadwick.

Here is the terminal output:

```
odd-rationale@ubuntu:~$ dpkg -l ies4linux debconf debconf-2.0 wine cabextract wget curl unzip belocs-locales-bin libc6 awk gawk mawk sed
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  awk            <none>         (no description available)
ii  belocs-locales 2.4-2.2ubuntu5 tools for compiling locale data files
ii  cabextract     1.2-2          a program to extract Microsoft Cabinet files
un  curl           <none>         (no description available)
ii  debconf        1.5.14ubuntu1  Debian configuration management system
un  debconf-2.0    <none>         (no description available)
un  gawk           <none>         (no description available)
ii  ies4linux      2.99.0-2       Installer for Internet Explorer 5, 5.5, 6 un
ii  libc6          2.6.1-1ubuntu1 GNU C Library: Shared libraries
ii  mawk           1.3.3-11ubuntu a pattern scanning and text processing langu
ii  sed            4.1.5-2        The GNU sed stream editor
ii  unzip          5.52-10ubuntu1 De-archiver for .zip files
ii  wget           1.10.2-3ubuntu retrieves files from the web
ii  wine           0.9.53~winehq0 Microsoft Windows Compatibility Layer (Binar
odd-rationale@ubuntu:~$
```

I get the same result if I do ```
DEBUG=1 /usr/bin/ie6
```

If I uninstall the .deb, it is no longer in my desktop menu.

I am running kubuntu 7.10.

Again, thanks a lot!

---

### Post by achadwick on 2008-01-14
> **Odd-rationale said:**
> Thanks so much, achadwick.
```

ii  wine           0.9.53~winehq0 Microsoft Windows Compatibility 
```

Could you try purging wine and then installing wine 0.9.46-0ubuntu1 from the normal Ubuntu repositories rather than the winehq ones? If you do that move your ~/.ies4linux/ directory out of the way again before testing :)

Pretty much everything else you have at the same version as mine. Lemme know if it works, because we may be looking at a versioning conflict that needs recording in the package.

---

### Post by jslmg on 2008-01-15
There is a new bug now being widely reported among ies4linux users. See this thread:

[http://ubuntuforums.org/showthread.php?t=665786](http://ubuntuforums.org/showthread.php?t=665786)

I've attached a screenshot of my IE6. It was installed using achadwick's .deb package, but I know it exists with old "manual" installs, too.

Any observations on this bug?

---

### Post by Odd-rationale on 2008-01-15
> **achadwick said:**
> Could you try purging wine and then installing wine 0.9.46-0ubuntu1 from the normal Ubuntu repositories rather than the winehq ones? If you do that move your ~/.ies4linux/ directory out of the way again before testing :)

Pretty much everything else you have at the same version as mine. Lemme know if it works, because we may be looking at a versioning conflict that needs recording in the package.

OK. I downgraded to wine 0.9.46. Everything seems to work normally. I would prefer the latest version of wine, but i guess that's ok.

Thanks so much for your help. I hope your .deb appears in the repos soon.

---

### Post by seaq on 2008-01-19
hi, great worked with your deb congrats!!!

it seems even better than the pygtk gui developed by Sergio, i wonder if it's possible to add the beta support for ie7??

also if you let install the right language as the original installer did it would be awesome

thanks again

---

### Post by teslarage on 2008-01-21
congrats on the DEB! it works flawlessly on my Ubuntu 7.10 32-bit with wine 0.9.46!

Thank you!

EDIT: why don't you add 64 bit support coz my 64-bit PC is getting ready to be formatted soon :P just a suggestion :D

---

### Post by altonbr on 2008-01-25
Using
* the .deb from this post: [http://ubuntuforums.org/showpost.php?p=3993177&postcount=9](http://ubuntuforums.org/showpost.php?p=3993177&postcount=9),
* Selecting every single check mark,
* Running Ubuntu 7.10 and,
* Wine 0.9.53 (from Wine repos),

everything installed properly, but I get that same 'toolbars do not display' error. Oh well!

What about contacting Medibuntu regarding this project? [http://www.medibuntu.org/contact.php](http://www.medibuntu.org/contact.php)

---

### Post by jslmg on 2008-01-25
> **altonbr said:**
> Using
* the .deb from this post: [http://ubuntuforums.org/showpost.php?p=3993177&postcount=9](http://ubuntuforums.org/showpost.php?p=3993177&postcount=9),
* Selecting every single check mark,
* Running Ubuntu 7.10 and,
* Wine 0.9.53 (from Wine repos),

everything installed properly, but I get that same 'toolbars do not display' error. Oh well!

What about contacting Medibuntu regarding this project? [http://www.medibuntu.org/contact.php](http://www.medibuntu.org/contact.php)

Did you check this thread:
[http://ubuntuforums.org/showthread.php?t=665786](http://ubuntuforums.org/showthread.php?t=665786)

Several suggestions there on getting the toolbars back, ranging from downgrading to some config file editing.

---

### Post by stickx911 on 2008-01-25
Installed only ie6 and extras. Works great for me so far. Thank you.
gusty on an HP dv2000cto

---

### Post by altonbr on 2008-01-26
> **jslmg said:**
> Did you check this thread:
[http://ubuntuforums.org/showthread.php?t=665786](http://ubuntuforums.org/showthread.php?t=665786)

Several suggestions there on getting the toolbars back, ranging from downgrading to some config file editing.

No but thanks, I'll try it. I'll also try install the original ies4linux instead of the .deb.

---

### Post by Mr.mouse on 2008-01-28
a better way is to add IE is with IE tab for firefox

firefox>tools>add ons>extensions>get ubuntu extensions>IE tab 

this will give more ui  integration then IE

---

### Post by jslmg on 2008-01-28
> **Mr.mouse said:**
> a better way is to add IE is with IE tab for firefox

firefox>tools>add ons>extensions>get ubuntu extensions>IE tab 

this will give more ui  integration then IE

What extension, exactly, are you referring to? Here's a link to "IE Tab" at the Firefox extensions page, clearly saying it's not for Linux:

[https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419)

---

### Post by Mr.mouse on 2008-01-28
yes i know that, 
the idea is not to create ies4linux .deb
the idea is to create only IE-engine+wine+IE-Tab pack so it will look better in ubuntu

---

### Post by achadwick on 2008-04-13
> **Mr.mouse said:**
> yes i know that, 
the idea is not to create ies4linux .deb
the idea is to create only IE-engine+wine+IE-Tab pack so it will look better in ubuntu

Except that the author pretty clearly states that ietab isn't supported under Linux. It requires Firefox, Windows and IE 4.0+. I can't legally package the latter two pieces of software :lolflag:

---

### Post by achadwick on 2008-04-13
New upstream release which fixes the blank screen bug, and I'm sorry I haven't been on the ball. Here's a new release; any testing you do would be wonderful. Thanks everyone for being so patient.

**You must install the xvfb package before installing this new revision.**

Changes from 2.99.0-2:

   * New upstream bugfix for the blank screen problem.
   * Experimental xvfb version using the old symlink-tree hack.
   * Catching updates works now, *sort of*:
     - Everything's sensitive to a saved debconf state. If you change the
       config in debconf, everybody gets an update the next time they launch
       ieX.
     - Updates xvfb-era WINEPREFIXes by saving and restoring your IE-specific
       Wine user profile directory
   * Conform to the xdg-user-dirs spec, as published
     at [http://freedesktop.org/wiki/Software/xdg-user-dirs](http://freedesktop.org/wiki/Software/xdg-user-dirs)
   * Start page is now the Ubuntu one if it's installed.

---

### Post by achadwick on 2008-04-13
> **seaq said:**
> 
it seems even better than the pygtk gui developed by Sergio, i wonder if it's possible to add the beta support for ie7??

also if you let install the right language as the original installer did it would be awesome

Thanks for testing and making suggestions!

IE7 support is now in the new .deb at the end of this thread, just turn it on in the extras screen when installing. :guitar: You should be asked automatically about installing it, but if you're not, type

   $ sudo dpkg-reconfigure ies4linux

after installation.

Also, multilingual support is in, and Should Just Work Automatically for all users of your machine. The package determines what POSIX locales your Ubuntu machine supports and converts that to IE locales to install. Certainly this bit works during installation for the pt_BR (BR, 1:1 match), en_GB (EN-US, partial match) and cy_GB (EN-US, no match) locales. When you run IE, it should reflect your current desktop session locale :)

I'm particularly interested to see whether the xdg-user-dirs support works for non-English-speaking users. Essentially, if you have xdg-user-dirs installed, do you get your IE "My Pictures" directory pointing at your ~/Pictures folder when you try to save? If you don't have xdg-user-dirs installed, will it use your home folder instead? Same thing for Desktop, "My Music" and all the usual Windows / Ubuntu suspects.

---

### Post by altonbr on 2008-09-13
I get this error after installing 'ies4linux_2.99.0.1-1_i386.deb' on Ubuntu 8.04.1, Wine 1.1.4
```
$ /usr/bin/ie6
cp: cannot stat `/usr/share/ies4linux/rack/0/EN-US/ie6': No such file or directory
```

---

### Post by pinballkid on 2008-10-26
Thanks for putting this together. Have you thought about adding it to a ppa?

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by omohat on 2008-10-29
> **altonbr said:**
> I get this error after installing 'ies4linux_2.99.0.1-1_i386.deb' on Ubuntu 8.04.1, Wine 1.1.4
```
$ /usr/bin/ie6
cp: cannot stat `/usr/share/ies4linux/rack/0/EN-US/ie6': No such file or directory
```

I get the same error (Ubunto 8.04 - Wine 1.0.0). Anyone got a solution?

---

### Post by garybrlow on 2008-11-01
```
mycomputer@mycomputer:/$ ie6
cp: cannot stat `/usr/share/ies4linux/rack/0/EN-US/ie6': No such file or directory

```I have the same error using Xubuntu 8.10. and Wine 1.1.7.  IEs4Linux doesn't seem to work anymore. :confused:

---

### Post by losko on 2008-11-02
Seems that my installation is unable to download from microsoft server...

---

