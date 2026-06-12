---
title: "HowTo: Install monodevelop 0.7 on powerpc"
date: 2005-06-19
forum: Ubuntu Backports
---

### Post by jonatin on 2005-06-19
Here's my problem: I'm trying to use ubuntu as my linux development platform for mono. And I want to use monodevelop 0.7 as my IDE. 

**EDIT: **Monodevelop is in the backports, but I couldn't find all the dependencies.

So here's what I did to get monodevelop running, perhaps this will enlighten others...

First, I installed monodevelop requirements using the available backports.

**sudo apt-get install** *the following requirements if necessary*
```

gnome-icon-theme (2.10.1-1ubuntu1)
libgconf2.0-cil (1.9.5-0ubuntu1~5.04ubp1)
libglade2.0-cil (1.9.5-0ubuntu1~5.04ubp1)
libglib2.0-0 (2.6.3-1)
libglib2.0-cil (1.9.5-0ubuntu1~5.04ubp1)
libgnome2.0-cil (1.9.5-0ubuntu1~5.04ubp1)
libgtk2.0-0 (2.6.4-0ubuntu3)
libgtk2.0-cil (1.9.5-0ubuntu1~5.04ubp1)
libgtksourceview1.0-0 (1.2.0-0ubuntu1)
mono-assemblies-base (1.1.7-0ubuntu4~5.04ubp1)
mono-jit (1.1.7-0ubuntu4~5.04ubp1)
mono-devel (1.1.7-0ubuntu4~5.04ubp1)
pkg-config (0.15.0-4ubuntu2)
xterm (6.8.2-10)

```

As you can see, most of this comes from the backports (ubp).

Several requirements were not available in the backports:
```

libgecko2.0-cil_0.10
libgtksourceview2.0-cil_0.10
monodoc-base_1.0.6
monodoc-browser_1.0.6
monodoc-manual_1.0.6

```

Go to [http://packages.ubuntu.com/breezy/devel/monodevelop]("http://packages.ubuntu.com/breezy/devel/monodevelop")

Navigate to the pages for each of the above packages and download the .deb files from breezy. (Get the powerpc architecture version when available.)

Now install the requirements:
```

cd /where/ever/the/.debs/are/
sudo dpkg -i libgecko2.0-cil_0.10-2ubuntu2_all.deb
sudo dpkg -i libgtksourceview2.0-cil_0.10-0ubuntu2_all.deb
sudo dpkg -i monodoc-base_1.0.6-1ubuntu2_all.deb
sudo dpkg -i monodoc-browser_1.0.6-1ubuntu2_all.deb monodoc-manual_1.0.6-1ubuntu2_all.deb
**NOTE** *put monodoc browser and manual in the same* dpkg -i *command*

```

I deleted the old 0.5 monodevelop config folder to get rid of cruft

**optional:** rm -r ~/.config/MonoDevelop

**install monodevelop from the backports:**
sudo apt-get install monodevelop

start MonoDevelop!  (Give it a while to re-index your .dlls for code completion)

**NOTE **if you start this from the command line then you will see errors about missing icons, and occasional GLib-GObject-CRITICAL failures when referencing GTK files. Convert to GTK2 until the mono folks fix the problem. (You didn't go through all this un-official stuff and expect perfection, did you?)

;)

Hope this helps

---

### Post by Slo Mo Snail on 2005-06-20
Hum... I uploaded monodevelop 0.7 for ppc a few weeks ago... don't know where it got lost ;) I'll reupload it later today

---

### Post by jonatin on 2005-07-05
Just a quick note, the above procedures worked to get **monodoc 1.0.6** and **monodevelop 0.7** installed on my i86 machine as well.

I don't know the status of the monodoc backport, but the breezy .debs worked perfectly.

---

