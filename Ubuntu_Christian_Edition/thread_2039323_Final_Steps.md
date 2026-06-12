---
title: "Final Steps"
date: 2012-08-08
forum: Ubuntu Christian Edition
---

### Post by stlsaint on 2012-08-08
EDIT: Step one complete. I have patched shotwell and the error is now resolved in the build.
Step two also has been complete.
Now on to e-sword. I am not 100% sure about getting 10.10 to work well with 12.04 from a script without user interaction. If i cant figure this out tomorrow than e-sword will have to be installed by the user.
Also lyricue will have to be removed from the default build. It requires the installation of mysql-server which cannot start due to an bug with upstart.

So in the spirit of keeping the community fully informed we are down to our last steps of producing a final release iso.
The list includes:

1. Patch unity-scope-shotwell
2. Finalize what applications will be included in post install script
3. Figure out a way to install e-sword post-install

The first two are to easy and will be finished probably today but the esword one is the major hold up. My current idea is to offer esword via my post-install script and point it to our great DK's installer script. I want to include the installer within the distro so that it can be tweaked and edited per the user for their specific needs. 

Unless I receive objection from the community with this, than this is the route I will be taking and a release will be announced this week or next. Jereme is handling all marketing and release announcements outside of the forums. Of course you folks here on the forums will be the first to know when the iso's are ready! ;)

---

### Post by Ardonel on 2012-08-09
Let me know as soon as there is a torrent and a tracker, and I will see about taking a currently idle machine and set it to aid the cause.

---

### Post by stlsaint on 2012-08-11
So a couple days back i came across another bug[0]. This one already being tracked by ubuntu devs but still no fix and its causing issue with sources.list. I take one step forward just to be yanked two steps back....smh...waiting

No real permanent fix for this bug aside from asking the user to manually edit their sources list post livecd boot and after fresh install.

---

