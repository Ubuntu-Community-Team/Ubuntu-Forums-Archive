---
title: "Can I mixing use PyQT and PyGTK on Ubuntu?"
date: 2022-11-24
forum: Ubuntu Application Development
---

### Post by rdzhang96 on 2022-11-24
My colleagues are using PyQT5 to develop some GUI tools on Ubuntu 16.04.
Now I am considering about turning to PyGobject (PyGTK3) because it is naturally more proper for Ubuntu.
But, my question is that can they be compatible with each other? Or is it possible or impossible to do so? Many thanks in advance :)

---

### Post by TheFu on 2022-11-25
I don't know anyone who tried it.  They can certainly be installed on the same system and used by different programs.  Within the same program, I can guess a few of the APIs would have internal collisions with exclusive-use OS features.  Also, only one can control the main event loop.  And the program would likely need 2x the RAM to run. These libraries aren't small.

BTW, support for 16.04 ended almost 2 yrs ago.  No projects should be based on that unsupported release at this point nor since 2018.  Very poor planning by whoever is leading the effort.  

Today, new projects should target 22.04 as the release.  Existing projects on 18.04 should have already migrated to 20.04 or 22.04 releases and the library versions those provide.  Standard support for 18.04 ends in April.  I'm migrating all my 18.04 production systems to 20.04 now.  22.04 isn't supported by some enterprise applications at this point and there are some show-stopper 22.04 issues that are still causing problems in my test systems.

Kubuntu uses Qt.  So does LXQt-Ubuntu in Lubuntu.  GTK+ which is used by Gnome software isn't universally loved.  Within a project, it would be smart to pick one library and stay within it.  Mixing Qt and GTK+ libraries is a terrible idea.

---

