---
title: "Ubuntu Server + QuarkXpress and legacy font files"
date: 2009-11-03
forum: Server Platforms
---

### Post by mistarjay on 2009-11-03
Hiya there

I recently installed and commissioned 2xUbuntu servers for my company (We work in design).

I will try and explain the problem the best way I can. (I am running Ubuntu 9.04 - Jaunty Jackalope)

Right, I have created a directory on my server, /data/Studio in this folder there are numerous design files, some QuarkXpress and legacy font files. 

These are used by designers who are on macs, when they put the files on the server they can access them and the work perfectly. I wanted to implament a sync between the two boxes using Unison and also incremental backs using 'Back in Time'.

Now the incremental backups work fine as far as the server are concerned, however when someone deletes the file and then I restore via Back In Time the file (QuarkXpress or fonts) are no longer useable on the mac.

My newest concern is that peforming the sync will also appear to damage the files, rendering them useless.

I am truely and utterly stumped and I have exhusted any avenue of fixing this that I am aware of.

Thanks for any help you can provide!

Quick Edit:

After backing up and restoring the file after it had been deleted the MAC could still not see the file however the server still thinks its a quark file and the md5 check is the same before and after. However the macs see a change in file size..

jl@bellside:/data/Studio/Test Sync/BAPC$ file "5717527 - BAPC B_c"
5717527 - BAPC B_c: Motorola Quark Express Document (English)
jl@bellside:/data/Studio/Test Sync/BAPC$ md5sum "5717527 - BAPC B_c"
199c98733f1d8cfcc213f66ad305b65f 5717527 - BAPC B_c

And when checking against other snapshots I get the error; "It conains ascii nulls, Perhaps it is a binary file"


Jamie

---

