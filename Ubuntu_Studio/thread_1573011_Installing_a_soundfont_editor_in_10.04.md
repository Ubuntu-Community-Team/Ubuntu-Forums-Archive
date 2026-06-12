---
title: "Installing a soundfont editor in 10.04"
date: 2010-09-12
forum: Ubuntu Studio
---

### Post by Sylos on 2010-09-12
Hello all.
Having recently been unable to install guitarix on Ubuntu Studio Hardy I have just upgraded to a shiny new 10.04 studio set up and.............predictably.............now have some issues.

Chief issue for the moment is getting a soundfont editor installed.

I have tried getting Swami which I used previously on Hardy but the .deb says the dependency is not met:

```
Error: Dependency is not satisfiable: libglib1.2ldbl (>= 1.2.10-18)
```

Having read on these forums that it was not working in Karmic I am assuming this is a non-starter.

S00...

I had a little google and found something called Smurf soundfont editor and decided to give that a crack. This seems also to have dependency issues. I have resolved some but appear to have hit a bit of a wall. ./configure currently results in:

```
....
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Failed to find sufficient GTK library

```

I have installed the libgtk2.0-dev package through synaptic but read a disturbing post on another forum post saying that libgtk2.0 does NOT produce a gtk-config file - hence the error. Is this case and if so is there a work around.

Any info on how to get either swami or smurf working OR other suggestions for soundfont editors will be gratefully received.

Cheers

---

### Post by cchhrriiss121212 on 2010-09-12
[Here]("http://ubuntuforums.org/showthread.php?t=1493264") are some instructions to install swami:
 >                                                                             Swami seems to be have been dropped because of dependencies of old GTK+ libraries.

You can download a deb-package of Swami from the Debian Lenny repository and install manually, like previous poster mentioned.

I also found out that you need to install some GTK+ libraries to be able to install Swami, so...

[LIST]
[*]Browse to the links below ( note that the order is relevant).
[*]Scroll down to the **Download** header and select the download link for your computer (select **all** or **i386** if you have no clue).
[*]Select a mirror close to you and save the deb-file (on your desktop or whatever).
[*]Doubleclick the deb-file to install the package.
[/LIST]

After you've installed the first three GTK+1.2 libraries you should be able to install Swami.

1. libgtk1.2-common
[http://packages.debian.org/lenny/libgtk1.2-common](http://packages.debian.org/lenny/libgtk1.2-common)

2. libglib1.2ldbl
[http://packages.debian.org/lenny/libglib1.2ldbl](http://packages.debian.org/lenny/libglib1.2ldbl)

3. libgtk1.2
[http://packages.debian.org/lenny/libgtk1.2](http://packages.debian.org/lenny/libgtk1.2)

4. swami
[http://packages.debian.org/lenny/swami](http://packages.debian.org/lenny/swami)[]("http://packages.debian.org/lenny/swami")

---

### Post by Sylos on 2010-09-12
Thanks for the info - I'll give that a shot.

Just to clarify: when you install old libraries like this what happens to the new ones? I assume they stay alongside the outdated ones and either one is accessed by whatever progs require the particular library.

---

