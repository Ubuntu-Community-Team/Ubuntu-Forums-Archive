---
title: "rsync a bittorrent directory while downloading /rsync a changing directory"
date: 2009-05-19
forum: Server Platforms
---

### Post by nixservers on 2009-05-19
Hello,

I use rtorrent on my Ubuntu server to download torrents.
I want it to be incrementally transfered to my home computer
while it is being downloaded **instead** of having to wait until it's done
and then do an rsync or scp.

A simple rsync doesn't seem to do it. Rsync keeps working for a while
after rtorrent is done, but what ends up on the home computer is mostly gibberish,
while the server copy had completed long before rsync had finished.

So basically we have files that are being changed after rsync has initiated.
Instead of grabbing signatures once and then doing a transfer, I want rsync 
to be mindful that the files being transfered might change after transfer has begun.

I thought that a -S option might help since the incomplete torrented files might be similar
to sparse files. But that didn't do it either.

I still have to rsync again to fix the gibberish and the total amount transfered is greater 
than the the size of the torrent download directory.

How do we get rsync to not send the gibberish and only send useful bits, and send the
new bits after it had been initiated?

This was the format I used:
rsync -rvzS user@serverdomain:remoteDir localDir

Any ideas?

---

### Post by MartinJS on 2009-10-13
> **nixservers said:**
> 

I still have to rsync again to fix the gibberish and the total amount transfered is greater 
than the the size of the torrent download directory.

How do we get rsync to not send the gibberish and only send useful bits, and send the
new bits after it had been initiated?

This was the format I used:
rsync -rvzS user@serverdomain:remoteDir localDir

Any ideas?

I do the same. You always need to run rsync more than once for this - it does not automatically detect new file changes during the transfer. The sparse (-S) option does not really do what I/you want: It does not reduce the amount of transfered bytes by skipping not-yet-downloaded blocks if there is no destination file yet. I filled a bug report for this: [https://bugzilla.samba.org/show_bug.cgi?id=5801](https://bugzilla.samba.org/show_bug.cgi?id=5801) .

I'm using the options -aPI --inplace.
-a for the permissions/recursion, -P for the progress bar and to keep partial transmitted files, -I to tell rsync that the source file could have changed even if size and date did not, --inplace to avoid using twice the disk space during the second, third, etc. rsync run.
I also create (using an automated script) an empty target file with the correct size (or bigger) to allow rsync to skip over "empty" ("sparse") blocks as an workaround for the above bug. Using -z might be another, simpler option.

The total amount transfered will always be (slightly) greater than the the size of the torrent download directory because of the protocol overhead of rsync. However, your last rsync run should only copy all missing blocks plus some protocol blocks, not the complete download directory. Otherwise you do something wrong.

One other idea I had recently was to play with the blocksize (-B) option of rsync, e.g. match it with the torrent chunk size to optimize the rsync process.

Best,
Martin

---

