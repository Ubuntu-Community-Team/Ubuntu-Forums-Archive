---
title: "All Linux the Same?"
date: 2009-01-05
forum: The Cafe
---

### Post by mamamia88 on 2009-01-05
well i am new to linux and finally settled on ubuntu because i heard it was the easiest to use and had the best support in these forums.  well now that i look at it it looks like every version of linux does things slightly different but is basically the same thing and if you don't like something about one version of linux you can quickly customize it to be similar to another versison of linux.  am i correct in thinking this?

---

### Post by uc50_ic4more on 2009-01-05
That seems very accurate... Additionally, very often you can move to another distribution (you referred to a distribution as a "version") and keep your program settings and configurations!

---

### Post by mamamia88 on 2009-01-05
dang i felt overwhelmed with choices when trying to chose i guess i really didn't have to be

---

### Post by cardinals_fan on 2009-01-05
Ubuntu is a good place to start.  If it works for you, get comfortable with Linux basics.  Then you can try out others and tweak them to fit your needs.  Eventually, you'll probably find a good fit.

---

### Post by uc50_ic4more on 2009-01-05
> **mamamia88 said:**
> dang i felt overwhelmed with choices when trying to chose i guess i really didn't have to be

Having a system as open and free as Linux based systems means that there are almost limitless options. As daunting as it can be for new users, it is a beautiful thing for the more experienced.

You may find that although you can hop from distribution to distribution with losing data and settings, you may run into difficulty moving between Gnome and KDE (and other desktops) based distributions, only because they come with a largely different set of programs. This does not preclude you from still being able to edit your images and documents, as the file formats used by most Linux based systems are reasonably ubiquitous; but it would mean having to learn a whole new pile of programs to a limited extent. If you'd like to see what I mean first hand, try a LiveCD of both Ubuntu (using the Gnome desktop) and Kubuntu (using the KDE desktop).

---

### Post by mamamia88 on 2009-01-05
> **uc50_ic4more said:**
> Having a system as open and free as Linux based systems means that there are almost limitless options. As daunting as it can be for new users, it is a beautiful thing for the more experienced.

You may find that although you can hop from distribution to distribution with losing data and settings, you may run into difficulty moving between Gnome and KDE (and other desktops) based distributions, only because they come with a largely different set of programs. This does not preclude you from still being able to edit your images and documents, as the file formats used by most Linux based systems are reasonably ubiquitous; but it would mean having to learn a whole new pile of programs to a limited extent. If you'd like to see what I mean first hand, try a LiveCD of both Ubuntu (using the Gnome desktop) and Kubuntu (using the KDE desktop).
i've been using ubuntu for about a month and a half now and love it i tried kde but found i really didn't care for it too much.  gnome seems perfect.  only thing i really don't care for is that program files don't always seem to be in the same place like in windows and sometimes when i install something from a deb installer it doesn't show up in the main menu

---

### Post by uc50_ic4more on 2009-01-05
> **mamamia88 said:**
> i've been using ubuntu for about a month and a half now and love it i tried kde but found i really didn't care for it too much.  gnome seems perfect.  only thing i really don't care for is that program files don't always seem to be in the same place like in windows and sometimes when i install something from a deb installer it doesn't show up in the main menu

Where program files end up in the filesystem is actually very well thought out, in that there are places for system programs, user programs, etc.

If you are instead referring to where they end up in your *menu*, that is fully editable as well!

As far as the icons not immediately appearing in your menu after an installation, you can either log out and back in, or issue the command (from the terminal) killall gnome-panel, which will restart the menu application.

---

### Post by mamamia88 on 2009-01-05
> **uc50_ic4more said:**
> Where program files end up in the filesystem is actually very well thought out, in that there are places for system programs, user programs, etc.

If you are instead referring to where they end up in your *menu*, that is fully editable as well!

As far as the icons not immediately appearing in your menu after an installation, you can either log out and back in, or issue the command (from the terminal) killall gnome-panel, which will restart the menu application.

where are the user programs stored?

---

### Post by cardinals_fan on 2009-01-05
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

They take a little while to read, but these should tell you anything you want to know about the Linux filesystem hierarchy, but were afraid to ask.

---

### Post by snova on 2009-01-05
> **mamamia88 said:**
> dang i felt overwhelmed with choices when trying to chose i guess i really didn't have to be

On the contrary. An uninformed choice could have left you with something like Slackware or Gentoo.... neither of which are exactly a good first distro. ;)

But the question- yes, most distros are similar for the most part. But not entirely.

Take something like GoboLinux, for example. Filesystem-wise, GoboLinux is *completely* different. There's not a thing left from traditional Linux systems (except for compatibility reasons).

Or compare, say, Debian and Red Hat's package systems. apt-get is a program you'll find in every Debian-based distro, but is nonexistent on Red Hat-derived ones. And apt-get is a very important program.

---

### Post by uc50_ic4more on 2009-01-05
> **mamamia88 said:**
> where are the user programs stored?

Usually in /usr/bin. See here for more info: [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by obocho on 2009-01-05
many distro[s]/version[s]/desktop environment[s]...

keep in mind though, one should decide between "to learn many things about all these staff" or "to master 'the one' you really need"... Hopefully, this learning/discovering process will not take all your time. 

good luck!

---

### Post by mamamia88 on 2009-01-05
thanks eveyone it's good to at least get a basic understanding of the filesystem

---

### Post by EdThaSlayer on 2009-01-05
Linux is all the same it's just the zealots that find a huge difference between the distros. :D

---

### Post by kk0sse54 on 2009-01-05
> **mamamia88 said:**
> thanks eveyone it's good to at least get a basic understanding of the filesystem

Don't get too comfortable with one distros filesystem since they all have the same basic structure but there can be a few differences in such folders as /etc depending on for example what type of init system is being used thus effecting system configuration files and such. And then if you totally jump out of linux and go to something a little bit more unix traditional like one of the *BSD that basic structure gets a bit more screwy.

---

