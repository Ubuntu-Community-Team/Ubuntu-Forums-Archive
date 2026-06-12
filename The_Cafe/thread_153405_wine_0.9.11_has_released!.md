---
title: "wine 0.9.11 has released!"
date: 2006-03-31
forum: The Cafe
---

### Post by snowboard975 on 2006-03-31
They say lots of bugs are fixed. I 'm excited to test it

March 31, 2006: Wine 0.9.11 Released

    Just in time to give you something to do this weekend, Alexandre released Wine 0.9.11. The more notable changes include:

        * Fake dll files created in the system directory to help installers.
        * Desktop mode now properly supports multiple processes.
        * Better type parsing in dbghelp.
        * Several OpenGL fixes.
        * A bunch of Unicode functions in advpack.

    Binary packages are in the process of being built, but the source is available now. You can find out more about this release in the announcement. Check out our download page for packages for your favorite distribution. Currently official Fedora packages lag behind, but you can get Wine-0.9.10 by running yum install wine from Fedora Extras.

---

### Post by YokoZar on 2006-04-01
My binary packages are built now, however they are *not* available via the sourceforge repository yet:

> Greetings folks.  I've gotten a new APT repository for my Ubuntu
packages set up, courtesy of Budget Dedicated -
[http://www.budgetdedicated.com/](http://www.budgetdedicated.com/)

The server is super fast and won't time out on you like Sourceforge
does, so remove the sourceforge lines from your /etc/apt/sources.list
and instead replace them with these:

deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

I've released 0.9.11 there, and in order to encourage folks to switch to
the new repository, I won't be updating the packages at sourceforge
until after the weekend.

When I finally get around to building packages against Debian sarge and
Ubuntu Dapper, they'll be available there too, and getting them will be
as easy as substituting "breezy" with the appropriate release name.
That, however, is for a later day - I'll send out another email here
when they're ready.

Enjoy,
Scott Ritchie

---

