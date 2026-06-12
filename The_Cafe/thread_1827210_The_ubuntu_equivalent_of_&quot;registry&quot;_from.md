---
title: "The ubuntu equivalent of &quot;registry&quot; from Windows?"
date: 2011-08-17
forum: The Cafe
---

### Post by zengrz on 2011-08-17
I am aware that Ubuntu is a package/folder-oriented system. But whenever I install a software without using the standard package manager, it gets very hard to manage the software update if I've somehow forgotten to "checkinstall" after the installation is completed. So I am wondering how does the package manager knows where to look for the list of software I have installed?

Also, is there a program which gives a visual representation of the file system tree/map in Ubuntu?

Thanks in advance!

---

### Post by Inodoro Pereyra on 2011-08-17
I'm not precisely an "expert", but I'd say...

>  gconf-editor 

:confused:

---

### Post by oldos2er on 2011-08-17
> **zengrz said:**
> So I am wondering how does the package manager knows where to look for the list of software I have installed?


APT keeps a database of everything. 
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

[http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers](http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers)

---

### Post by Aquix on 2011-08-17
Apt and dpkg will keep track of dependencies and where packages are installed. 

Yeah, I'm disappointed that many programs don't use checkinstall in the installation instruction. What it does is taking the make files and create a deb file to instrall and leave it to dpkg to keep track of it.

---

### Post by haqking on 2011-08-17
> **Inodoro Pereyra said:**
> I'm not precisely an "expert", but I'd say...

 

:confused:

NO.

Gconf-editor only exists for Gnome Desktop.  It is a GUI used to change the Desktop environment.

Linux does not have a registry. And there is no real equivalent. Each piece of software/app has its own configuration information.

---

### Post by NightwishFan on 2011-08-17
Checkinstall is indeed awesome. I never just run 'make install' even on software I trust.

---

### Post by capink on 2011-08-17
```
/var/lib/dpkg/status
```

don't miss with it manually though.

---

### Post by Tibuda on 2011-08-17
> **Aquix said:**
> Yeah, I'm disappointed that many programs don't use checkinstall in the installation instruction. What it does is taking the make files and create a deb file to instrall and leave it to dpkg to keep track of it.

They don't suggest in their instructions checkinstall because it is Debian-based specific.

---

### Post by 3Miro on 2011-08-17
Ubuntu has a database of all the software that has been installed with apt (i.e. from the repos). It has some things in common with the windows registry, but it is more different than not. Here are couple of examples:

1. The registry is used by running programs, while apt DB is accesses only on install/uninstall/update of software.
2. The registry holds keys with the settings for different programs, while Ubuntu uses simple text files. Apt keeps track of the settings files, however, it does not keep track of the content of those files.

The net result is that a bloated windows registry can slow down the entire system, while a bloated apt DB only slows down install and uninstall. Furthermore, broken registry can stop windows from working, while broken apt will only prevent installing new software and updates (a big thing, but not as big as in the windows case).

Gnome DE uses gconf, which is more like a windows registry, however, it only works with Gnome specific apps (panel, nautilus, metacity ... it will not work with or affect Amarok or Parole or Firefox). 

Gconf-editor is just a graphical tool for editing gconf settings, it is made to resemble windows regedit, but it is not quite the same.

---

### Post by Inodoro Pereyra on 2011-08-17
> **Inodoro Pereyra said:**
> I'm not precisely an "expert", but I'd say...

 

:confused:

[QUOTE=haqking;11161801]NO.

Gconf-editor only exists for Gnome Desktop.  It is a GUI used to change the Desktop environment.

Linux does not have a registry. And there is no real equivalent. Each piece of software/app has its own configuration information.[/QUOTE]

Oops, sorry then. :oops:

But I DID say I'm not an expert.

Anyways, it does look a lot like regedit...

---

### Post by zengrz on 2011-08-17
Hey, thanks for all the great replies!

Another question: I read from somewhere that apt-get works together with synaptic manager. Does that mean I do not have to checkinstall if I use apt-get to install a software? How is Synaptic manager different from/worse than/better than Ubuntu Software Manager? Or I can use whichever I prefer?

Thanks!

---

### Post by zengrz on 2011-08-17
> **3Miro said:**
> Ubuntu has a database of all the software that has been installed with apt (i.e. from the repos). It has some things in common with the windows registry, but it is more different than not. Here are couple of examples:

1. The registry is used by running programs, while apt DB is accesses only on install/uninstall/update of software.
2. The registry holds keys with the settings for different programs, while Ubuntu uses simple text files. Apt keeps track of the settings files, however, it does not keep track of the content of those files.

The net result is that a bloated windows registry can slow down the entire system, while a bloated apt DB only slows down install and uninstall. Furthermore, broken registry can stop windows from working, while broken apt will only prevent installing new software and updates (a big thing, but not as big as in the windows case).

Gnome DE uses gconf, which is more like a windows registry, however, it only works with Gnome specific apps (panel, nautilus, metacity ... it will not work with or affect Amarok or Parole or Firefox). 

Gconf-editor is just a graphical tool for editing gconf settings, it is made to resemble windows regedit, but it is not quite the same.


Thanks for the detailed explanation! I kind of realize the effect of a disorganized registry that's why I torrented registry mechanic, lol

---

### Post by 3Miro on 2011-08-17
apt-get is the real thing. aptitude, Synaptic and Ubuntu Software Center are front-ends, i.e. they give you an easier way to use apt-get.

Between Synaptic and USC, Synaptic is more verbose and allows for more fine grain control over what is being installed. However, Synaptic can be a bit confusing as package names are sometimes ambiguous, while USC is more clear (i.e. Firefox as opposed to firefox-branding or abrowser or ubufox ....)

I often times use both Synaptic and USC depending on what I am trying to do.

---

### Post by NightwishFan on 2011-08-17
Synaptic is more technical but is by no means complicated. They both essentially do the same thing.

---

### Post by Aquix on 2011-08-17
> **Tibuda said:**
> They don't suggest in their instructions checkinstall because it is Debian-based specific.

Hmm, I didn't know that. Been on debian based os's too long.

Find it strange though since it shouldn't be to hard to make checkinstall for rpm based systems. I mean, you can use alien to make rpm packages out of deb, and deb's from rpm with alien.

---

### Post by akand074 on 2011-08-17
Yeah, there is no equivalent of the Windows registry in Ubuntu. Thank goodness.

---

### Post by zengrz on 2011-08-17
Thanks again for all the replies! I've learned a lot today!

I think this question has been asked a million times but I can't find any satisfying answer on google: how to properly install .sh files so that it gets registered properly in the system? Or do I simply change the permission and run it?

Thanks a million!



EDITED:

What I am trying to do is to configure c++ environment in netbean and I am following this tutorial:

[http://netbeans.org/community/releases/67/cpp-setup-instructions.html](http://netbeans.org/community/releases/67/cpp-setup-instructions.html)

So I downloaded Sun Studio 12 Update 1 Compilers and ended up with a .sh file, which should probably goes into /opt. Also, the tutorial also asked me to add the complier to the system PATH, where is the system path?

EDITED AGAIN:

Ok I was being stupid. You need to kind of configure netbean in Windows, so I thought I would have to do the same in ubuntu...

---

### Post by NightwishFan on 2011-08-17
^_^

[QUOTE="From Checkinstall Man Page"]
       --type    Choose packaging system. Can be one of 'slackware',  'debian'
                 or 'rpm'.

       -D        Create a Debian package.

       -R        Create a RPM package.

       -S        Create a Slackware Package.
[/QUOTE]

---

### Post by alphacrucis2 on 2011-08-17
> **3Miro said:**
> apt-get is the real thing. aptitude, Synaptic and Ubuntu Software Center are front-ends, i.e. they give you an easier way to use apt-get.



Well apt-get is also a front end. The real thing is dpkg.

---

### Post by 3Miro on 2011-08-17
> **alphacrucis2 said:**
> Well apt-get is also a front end. The real thing is dpkg.

Can dpkg connect to the repos or does it work only offline? I always though that apt-get was the on-line version of dpkg (i.e. download then use dpkg).

---

### Post by Paqman on 2011-08-18
> **zengrz said:**
> whenever I install a software without using the standard package manager, it gets very hard to manage the software update if I've somehow forgotten to "checkinstall" after the installation is completed.

The simple answer is that unless you use the package manager there is no automatic way to handle updates.

If you software is not in the repos (and you want to have it update automatically) the next best thing would be to install it from a PPA. This uses the package manager and will install updates through Update Manager like normal.

The simplest thing to do is just not install things outside the package manager. Doing so forces you to maintain them manually, and can cause dependency problems and instability.

---

### Post by Aquix on 2011-08-18
If you know what dependencies you have installed, eigther from the website or because of error when running configure, and use checkinstall, then it's as easy to remove programs installed from source as through apt-get or ppa. Thats because checkinstall only creates a deb from the make files and install it with dpkg. So you just have to uninstall the program in synaptic and remove the dependencies that autoremove don't uninstall. 

What you want to look out for is installing from source with 'configure, make, make install', witch often is what is the instruction,  and programs that you install using python.

---

### Post by forrestcupp on 2011-08-18
> **haqking said:**
> NO.

Gconf-editor only exists for Gnome Desktop.  It is a GUI used to change the Desktop environment.

Linux does not have a registry. And there is no real equivalent. Each piece of software/app has its own configuration information.Right. Instead of having one place for everything, Linux has a thousand different config files all over the place. There are good and bad points to that. The good is that it's a lot easier to read and figure out. The bad is that the config files are all over the place.

Sometimes I wish Windows would go back to using ini files instead of the registry.

> **Inodoro Pereyra said:**
> Oops, sorry then. :oops:

But I DID say I'm not an expert.

Anyways, it does look a lot like regedit...
You're kind of right. Gconf-editor *is* kind of like a registry for Gnome settings. It didn't really fit the OP's question, though, since he was asking about installed software. You're not completely wrong, though. ;)

---

### Post by capink on 2011-08-18
> **forrestcupp said:**
> The bad is that the config files are all over the place.


They are not all over the place. System wide settings are all stored in /etc. This way you can back up all your settings with simple command. 

Per user settings are stored in your home directory. The directories which store these settings start with a dot. They are not as orderly as the system wide settings. But still better than the registry and also can be backed up easily. I think the ~/.config should be the one dir that contains all the settings, but a lot of programs don't use it, and some others put unnecessary files there (e.g. chrome puts it's cache files there instead of putting it where it belongs in ~/.cache, other browsers also put their cache in the wrong place).

---

### Post by Warpnow on 2011-08-18
> **haqking said:**
> NO.

Gconf-editor only exists for Gnome Desktop.  It is a GUI used to change the Desktop environment.

Linux does not have a registry. And there is no real equivalent. Each piece of software/app has its own configuration information.

Ubuntu Equivalent not linux Equivalent.

gconf-editor is a good comparison to windows registry editor and even functions in a similar manner.

---

