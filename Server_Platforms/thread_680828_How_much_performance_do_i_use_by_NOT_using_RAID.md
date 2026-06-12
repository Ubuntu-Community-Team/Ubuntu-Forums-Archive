---
title: "How much performance do i use by NOT using RAID?"
date: 2008-01-28
forum: Server Platforms
---

### Post by skullmunky on 2008-01-28
sorry, title should be "how much performance do I LOSE", not use. :) 

I have a Dell PowerEdge NFS server with RAID-5, server about 15 workstations mostly used for 3D animation.  I'm being upgraded to a much newer one, which has more storage but on fewer disks.  So instead of something like 4x80GB I have 2x250.  Should I fear a really noticeable drop in performance, or is the benefit of RAID-5 more in the redundancy?   

I know the question's probably meaningless in the abstract, so here are some common tasks:

3D rendering
video playback and a little editing
audio editing

---

### Post by smileypaul on 2008-01-29
Realistically, it all depends on how the server is set up.

If you have a nice hardware card, with large clusters (good for your file types), then i would say RAID5 might give you a slight performance boost.

But realistically, you won't see much of a performance hit .. RAID5 is more beneficial for redundancy.. and its something that you should probably consider if your audio/video files have any importance to you.

---

