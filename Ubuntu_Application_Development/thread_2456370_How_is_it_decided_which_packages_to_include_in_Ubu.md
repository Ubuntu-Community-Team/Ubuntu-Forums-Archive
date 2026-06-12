---
title: "How is it decided which packages to include in Ubuntu?"
date: 2021-01-10
forum: Ubuntu Application Development
---

### Post by kjellahl on 2021-01-10
I work with the maintenance of some Gnome subroutine library packages.
I wonder how it's decided which of these packages (and which versions) to make
easily available in Ubuntu.

An example: In Ubuntu 20.10 there is a libxml++2.6-2v5 package.
Almost 5 years ago a second series of libxml++ was started, libxml++3.0,
with a different API/ABI. No package from this series is included in Ubuntu.

Another example: libsigc++-2.0-0v5 is part of Ubuntu, libsigc++-3.0 is not.

Quite recently other packages have been released with new API/ABI, parallel-installable
with old packages. See [https://mail.gnome.org/archives/gtkmm-list/2020-December/msg00013.html](https://mail.gnome.org/archives/gtkmm-list/2020-December/msg00013.html).
Will these packages be included in future versions of Ubuntu?

---

### Post by TheFu on 2021-01-10
These forums are for user-to-user help.  Few, if any, Canonical employee will ever see this.  I've met a few employees over the years, but only at Linux and F/LOSS conferences.  Plus, they tended to work on server-only stuff, nothing desktop related.

Especially for libraries, being included without any program dependencies should not happen.  What upstream programs use this library?

From a practical standpoint, for libraries to be included, key versions of important programs need to depend on them.  So, if you can get the next version of GnomeDE to depend on your library, it will be included.  Or get it added, with good reason, to Debian. Being important to optional stuff (anything java) can help, but not nearly as much.

---

### Post by kjellahl on 2021-01-14
Thanks for your reply.

I suspected already when I filed my question that this was perhaps not the most
appropriate place to ask. There are so many places to ask Ubuntu questions that
it's difficult to know which is the best one. Still I quickly got the information
I wanted.

---

