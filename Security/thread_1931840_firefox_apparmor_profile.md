---
title: "firefox apparmor profile"
date: 2012-02-26
forum: Security
---

### Post by needhelppeeps on 2012-02-26
I'm not sure why this keeps happening, but when firefox is updated the apparmor profile breaks. This time I let it install the new apparmor profile and I simply edited in the few changes I wanted. I think this is the third time I've had this happen and I am wondering if anyone has any insight at to why this keeps happening. Should I be doing something different?

---

### Post by Dangertux on 2012-02-26
> **needhelppeeps said:**
> I'm not sure why this keeps happening, but when firefox is updated the apparmor profile breaks. This time I let it install the new apparmor profile and I simply edited in the few changes I wanted. I think this is the third time I've had this happen and I am wondering if anyone has any insight at to why this keeps happening. Should I be doing something different?


The firefox apparmor profile is contained in the same packages as firefox, so when you update firefox the profile is update as well. You should back up your existing profile , and just know whenever it is updated you will likely be restoring your changes to your apparmor profile.

Hope this helps.

---

