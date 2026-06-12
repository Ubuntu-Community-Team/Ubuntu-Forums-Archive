---
title: "No CD-ROM found"
date: 2009-12-13
forum: Wine
---

### Post by The Funkbomb on 2009-12-13
I have the latest wine installed.  I have been playing Half-Life 2 with very little problems.

I looked up another game I enjoy, Max Payne 2 on winehq's app list and see that it works well.

Max Payne 2 requires 2 disks.  The install disk and the play disk.  I installed it with no problem.  When I go to play it, it says no CD-ROM found.  The disk is in the drive.

I went onto the play disk and loaded that up under WINE, the splash screen comes up with options.  One of the options is, "View the files on this CD" or something similar.  When I click that, it opens a Windows-esque file explorer and shows the CD drive as Z:

When I go into ~/.wine/dosdevices/Z:, it's locked and it shows pretty much my root, not the contents of the CD.

I'm going to try to link it but I find this very odd.  Any help?

---

### Post by The Funkbomb on 2009-12-13
I tried to link them but no luck there.

I also noticed in winecfg that under drives, it has no mappings:

"Failed to connect to the mount manager, the drive configuration cannot be edited"

---

### Post by The Funkbomb on 2009-12-13
I fixed this by doing another symlink from media/cdrom to ~/.wine/dosdevices/d:/

That gets the game to load but then Max Payne 2 crashes during the first loading screen.  Someone else has this issue too according winehq.  Tried disabling pixel shader and setting everything to low but no love.

---

