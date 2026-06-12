---
title: "When can I run X-Plane on 12.04 64bit"
date: 2011-12-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sparker256 on 2011-12-01
To run X-Plane on ubuntu 64bit in the past I have had to install ia32. At this point in time Alpha1 it wants to remove a ton of stuff that does not look right. If I have read everything correctly this is because of multiarch so my question is when would it be working correctly. 

Thanks Bill

---

### Post by Sworddragon on 2011-12-04
Maybe ia32-libs from Precise will need a few weeks/months until all libraries are ready. But you can try using ia32-libs from Oneiric.

---

### Post by sparker256 on 2011-12-04
> **Sworddragon said:**
> Maybe ia32-libs from Precise will need a few weeks/months until all libraries are ready. But you can try using ia32-libs from Oneiric.
I am just wondering if there is some kind of timetable for this to be complete. I am in no hurry but just like to test early as I write plugins and like to make sure they will work with the up coming version.

Bill

---

### Post by seeker5528 on 2011-12-07
> **Sworddragon said:**
> Maybe ia32-libs from Precise will need a few weeks/months until all libraries are ready. But you can try using ia32-libs from Oneiric.

It's not an issue with ia32-libs (depending on how you look at it). As far as I can tell, from what I could follow of the dependency chain just by looking at dependencies of a ia32-libs-multiarch and a few other relevant packages, there are only something like 3 packages or so that the ia32-libs metapackage in Oneiric pulls in that should still should get pulled in in Precise.

For the rest of the packages the actuall blah-blah:i386 packages get pulled in, so the issue is getting all the related packages updated for multiarch.

I'm going the opposite direction on my systems, install *:amd64 packages on an i386 installation, so I can't just pull in the package and see what doesn't load, but theoretically the same packages 64 bit packages that are able to install or not able install on i386 should be the same as the list of i386 packages that can/can't be install on amd64.

Looking through the list of dependencies

[http://packages.ubuntu.com/precise/ia32-libs-multiarch](http://packages.ubuntu.com/precise/ia32-libs-multiarch)

most of the packages listed I have updated to :amd64 on my system, gstreamer still seems to be a sticking point, may depend on the applications you have installed and/or if you have bad and ugly packages installed in addition to the gstreamer-good set. 

If I try to install gtk2-engines it wants to remove the lubuntu default-settings and artwork packages. The other engines installed OK.

The libcap2 package wants to remove a bunch of stuff when I select it for installation.

I keep seeing a fair amount of stuff in various changlogs about multiarch, so generally speaking it is getting a fair amount of attention, but don't know what the priority is for specific packages or any kind of ETA that may be expected.

Later, Seeker

---

### Post by 3vi1 on 2011-12-07
> **sparker256 said:**
> I am just wondering if there is some kind of timetable for this to be complete. I am in no hurry but just like to test early as I write plugins and like to make sure they will work with the up coming version.

Bill

I haven't seen anything from the guys working on multiarch, but I would suspect that at the latest it would all need to be done by February 9th, when the beta iteration starts.

---

