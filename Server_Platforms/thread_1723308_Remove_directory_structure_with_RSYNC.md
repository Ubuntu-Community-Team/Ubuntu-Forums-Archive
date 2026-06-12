---
title: "Remove directory structure with RSYNC"
date: 2011-04-06
forum: Server Platforms
---

### Post by sublimation on 2011-04-06
I have several copies of a file set with different organizational structures, but the same files.
i.e. 
On client1 files can be found in ~\foo\bar\file1, ~\foo\bar\file2, ~foo\tavern\file3, ~\foo\tavern\file4
On client2 files can be found in ~\foo-bar\file1, ~\foo-bar\file2, ~\foo-tavern\file5, ~\foo\tavern\file6
On client3 files can be found in ~\file1, ~\file3, ~\file5, ~\file7

I have access to one client and the server where I'd like all the files to be synced. I'm not worried about conflicts, just having a complete copy of all files[1-7]

Is there a way to cause RSYNC to remove the directory structure, so that I get something like 
client1% rsync files server:\backup\
client2% rsync files server:\backup\
etc 
where at the destination all files will be checked against the destination set regardless of the source directory structure?

---

### Post by BkkBonanza on 2011-04-07
I'm sure rsync doesn't have a built in way to do that. 

You would have to write a command loop like:

**for x in `find ~ -name files*`; do rsync $x server:/backup/; done**

see man find for details how you can match suitable files.

This example searches ~ (home) for matching "file*" and rsyncs it to server.

-name for just filename patterns
-iname for case-insensitive patterns
-regex for powerful regular expression patterns

If you have a specific filename list you could put the names in a file one per line and use something like,

**while read f; do rsync $f server:/backup/; done<listfile**

Reads list file line by line using each filename as src for rsync.

---

### Post by sublimation on 2011-04-07
hmm I was afraid of that. My idea was 

find . -name "file*" -exec rsync {} server:/backup/ \;

but I just felt like there had to be a better/faster way than that.

---

### Post by BkkBonanza on 2011-04-07
If you're worried about starting rsync sessions over and over (slow) then make a temp copy, or tar archive, locally and rsync once afterwards,

[B]for x in `find ~ -name files*`; do tar -uf work.tar $f; done
rsync work.tar server:/backup[/B]

---

### Post by sublimation on 2011-04-07
Creating local archives on each of the client machines would remove all of the benefits of using rsync. I have only part of the full set on each client, so I'm attempting to sync the full set onto the server without overlap.

I think creating a filelist through find, then sending that filelist to rsync would be more efficient in that case.

---

