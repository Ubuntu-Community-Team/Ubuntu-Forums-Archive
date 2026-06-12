---
title: "gazelle upgrade to 9.10 failed: system unusable"
date: 2009-12-07
forum: System76 Support
---

### Post by shadhavar on 2009-12-07
I attempted to upgrade my Gazelle (I think its v5) to 9.10 last night. Somewhere towards the end of the upgrade process, the installer ran into an error with virtualbox-ose and quit. It warned that my system might be in an unusable state because it was unable to complete. So I figured I would remove virtualbox (I never got it working anyways) and then try again.... well I removed virtual box through synaptic package manager then rebooted. Upon reboot I see the ubuntu loading screen then I get this error:
```

init: ureadahead main process (2585) terminated with status 5
mountall:proc/: unable to mount: Device or resource busy
mountall:proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process(2586) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started
CONTROL-D will terminate this shell and re-try.

```

Under that is a root prompt.

If I restart
I can get the ubuntu boot menu, It gives me 3 options. The first 2 bring me back to the same error screen. The 3rd one is a memtest.


What do I do now? Is there a way to revive the system without starting fresh? Maybe using a liveCD? I'm still a linux newbie and I've been playing around with this laptop for about a year and a half now. I've probably messed up enough of ubuntu's inner workings installing and uninstalling stuff and messing with settings and trying things that it needs a clean install. However, if possible I'd like to be able to at least get it limping along enough to grab a couple files that missed my last backup.

Thanks for any help
-shad

---

### Post by thomasaaron on 2009-12-08
Re-image. It's pretty badly hosed, and even if we get it to boot, we might spend the next week trying to work out all the kinks.

[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

