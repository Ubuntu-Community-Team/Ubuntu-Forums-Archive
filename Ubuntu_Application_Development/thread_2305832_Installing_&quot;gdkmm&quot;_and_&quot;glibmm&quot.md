---
title: "Installing &quot;gdkmm&quot; and &quot;glibmm&quot; in Ubuntu Studio 14.04"
date: 2015-12-09
forum: Ubuntu Application Development
---

### Post by sethanath2 on 2015-12-09
Hi,

Someone here taught me how to install "gtkmm" using the command below.
sudo apt-get install libgtkmm-3.0-dev

How would I install "gdkmm" and "glibmm"?

Thanks.

---

### Post by sethanath2 on 2015-12-09
Hi,

I also would like to learn how to install "GtkGLExt" and "OpenGL or Mesa".

Thank you so much.

---

### Post by ian-weisser on 2015-12-09
> **sethanath2 said:**
> How would I install "gdkmm" and "glibmm"?

One way is to ask your favorite search engine which -dev software package gdkmm and glibmm are in.
Then simply install those packages for your release of Ubuntu.

Which part are you having trouble with?

---

### Post by sethanath2 on 2015-12-09
> **ian-weisser said:**
> One way is to ask your favorite search engine which -dev software package gdkmm and glibmm are in.
Then simply install those packages for your release of Ubuntu.

Which part are you having trouble with?

I don't know which are in what at this moment. I have been googling these for quite some time.
I also tried Software Center, and so many things would come up.

For one, I have some trouble with the version number.

Thanks.

---

### Post by ian-weisser on 2015-12-09
Let the package manager worry about the version number. That is it's job.

Let's see...let's Google 'gdkmm debian'
There's a clue, first hit: [https://packages.debian.org/sid/amd64/libgtkmm-3.0-dev/filelist](https://packages.debian.org/sid/amd64/libgtkmm-3.0-dev/filelist)

Looks like the gtkX.X-dev package include gtk AND gdk files.
Have you tried to use gdkmm yet? Test it. See if it's included in the GTK package you installed.


Next, let's ask Google for 'glibmm debian'
We hit enter, and the first hit is again a great clue: [https://packages.debian.org/search?keywords=glibmm](https://packages.debian.org/search?keywords=glibmm)
Now we know the likely package name: glibmm.

Let's query the local package data base with that name fragment:
```
$ apt-cache search glibmm
gtkmm-documentation - Documentation of C++ wrappers for GLib/GTK+
libglibmm-2.4-1v5 - C++ wrapper for the GLib toolkit (shared libraries)
libglibmm-2.4-dbg - C++ wrapper for the GLib toolkit (debug symbols)
libglibmm-2.4-dev - C++ wrapper for the GLib toolkit (development files)
libglibmm-2.4-doc - C++ wrapper for the GLib toolkit (documentation)
```
And there's the complete package name for the -dev package (libglibmm-2.4-dev).

I'm using 15.10, and the version of libglibmm-2.4-dev in 15.10 is compatible with GTK and other tools in 15.10.
You're using 14.04, and the version of libglibmm-2.4-dev in 14.04 is compatible with GTK and other tools in 14.04.
That compatibility is a key purpose of periodic-release distros like Debian and Ubuntu, and a key reason for automated package management.

---

### Post by sethanath2 on 2015-12-10
Okay. I found this for "gtkglext" and "gtkglextmm"
[https://packages.debian.org/search?keywords=gtkglext](https://packages.debian.org/search?keywords=gtkglext)

sudo apt-get install libgtkglext1-dev
sudo apt-get install libgtkglextmm-x11-1.2-dev

May I ask whether the word "x11" above matter? Do you have any lib without "x11"?
What if I try to code something later not for "x11"?

Thanks.

---

### Post by ian-weisser on 2015-12-10
The 'x11' has meaning. It refers to the X windowing system, used by most Unix-based and Linux-based desktop environments.

Does that matter for your purposes? No idea - we don't know your purposes. We only know what you told us.

---

### Post by sethanath2 on 2015-12-10
> **ian-weisser said:**
> The 'x11' has meaning. It refers to the X windowing system, used by most Unix-based and Linux-based desktop environments.

Does that matter for your purposes? No idea - we don't know your purposes. We only know what you told us.

Thanks.

---

