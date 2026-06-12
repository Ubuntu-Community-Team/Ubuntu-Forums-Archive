---
title: "Unity lenses"
date: 2012-02-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ibrahimtawbe on 2012-02-07
I have problems with lenses 
the application and music lenses don't show anything 
is there a command to refresh a 'database-cache' for the lenses ?

---

### Post by Framli on 2012-02-07
The music lens is still Banshee-only but will work with Rhythmbox really soon.

The empty Apps lens is weird.
Does this command make it work?
```
/usr/lib/unity-lens-applications/unity-applications-daemon
```

---

### Post by ibrahimtawbe on 2012-02-07
```
Another instance of the Unity Applications Daemon already appears to be running.
Bailing out.ibrahim@U405:~$ /usr/lib/unity-lens-applications/unity-applications-daemon
Another instance of the Unity Applications Daemon already appears to be running.
Bailing out.
```

---

### Post by ibrahimtawbe on 2012-02-07
solved after a reboot

---

### Post by Baldrick_NZ on 2012-02-07
> **Framli said:**
> The music lens is still Banshee-only but will work with Rhythmbox really soon.

The empty Apps lens is weird.
Does this command make it work?
```
/usr/lib/unity-lens-applications/unity-applications-daemon
```

So, it'll only work with whatever app is hard-wired as default? That's a bit off for those of us who wish to uninstall those apps in favour of more appropriate ones for the end user.

My 2 cents...

---

### Post by Framli on 2012-02-08
No, it's just that the scope (the lens search engine) supporting rhythmbox is currently not in the archive. You can already use a lot of players with the Music lens, but you need to add a PPA to do so. This is being fixed by helping devs to push all these music player scopes (for Clementine, Deadbeef, etc.) to the software center.

---

