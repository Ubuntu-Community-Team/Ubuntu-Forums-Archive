---
title: "Rsync via Samba errors"
date: 2009-02-25
forum: Server Platforms
---

### Post by Kementari on 2009-02-25
Hello,

What I am trying to do, is mirror a directory from a ubuntu server system, to an xp system. The drives of the XP system are shared to the server via samba, and mounted using autofs.

When I run rsync, any file with a non-english-non-numeric filename, gets the offending characters replaced with wildcards, which XP reads at as a random ascii character. The result is, that each rune of rsync, a new, random file is created.

Oddly enough, when copied via other methods, the filenames are preserved, so I suspect the issue must be a fault of rsync.

Is this a known issue with rsync's interaction with samba, or with samba itself? I didn't see a filename encoding option that looked useful in rsync, and I can transfer the files between linux directories with no loss of filename data.

Would anyone happen to know what precisely is going on? I want to be able to update the directory, and have the updates mirrored back to the XP box, and this looks like the most optimal method...if it preserves the filenames.

Thank you kindly for any help you guys are willing to give.

-Kementari

---

