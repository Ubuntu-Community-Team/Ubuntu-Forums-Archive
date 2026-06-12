---
title: "Wine can't access external drive in Karmic"
date: 2009-11-04
forum: Wine
---

### Post by Plus+ on 2009-11-04
So far I tried Grabit and Qpar and "open file" dialogue boxes - they see the folders on the drive but not the files themselves.

In Grabit's configuration it doesn't accept setting any of the folders on the drive. It navigates to them fine, but on "open" reverts to E:\\ or something.

I must admit I messed with permissions on the drive - set umask=000 in default mount options. It solved the initial problem I had with the drive, but now Wine is misbehaving. I don't know if it worked previously in Karmic, never had a chance to try.

My previous effort is described here:

[http://ubuntuforums.org/showthread.php?t=1313964](http://ubuntuforums.org/showthread.php?t=1313964)

---

