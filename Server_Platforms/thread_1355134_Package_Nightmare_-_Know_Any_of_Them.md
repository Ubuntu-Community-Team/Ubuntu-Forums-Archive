---
title: "Package Nightmare - Know Any of Them?"
date: 2009-12-14
forum: Server Platforms
---

### Post by Xiuh on 2009-12-14
I wanted to get a Java compiler on my server so I installed the sun-java6-jdk package. I didn't really watch what was going on and just accepted the default includes. I walked away after the license agreement on the package. When I came back I was shocked to find a number of packages and new daemons running on my server. I started picking through some of them, but it's just all over the place...

Among others:
dbus
ConsoleKit
avahi (which decided bind wasn't doing a good enough job)
gnome-keyring

Just a sample. I guess I didn't watch this because I though, sun-java, should be A-OK? Guess not, from what I can pick up from the package details, all of this is needed for Sun's zero configuration setup. Anyone else do a jdk install only to be overwhelmed with all of the new packages?

---

### Post by modulationz on 2009-12-14
> **Xiuh said:**
> <snip> I was shocked to find a number of packages and new daemons running on my server.</snip>

This drives me nuts too.  You can always do the following (which may help):

sudo aptitude purge <package>
sudo aptitude --without-recommends --without-suggests install <package>

That blasted gnome-keyring is sneaky and always wants to be installed ;)

---

