---
title: "Rsync - deleting files when using --files-from"
date: 2007-11-28
forum: Server Platforms
---

### Post by feenster on 2007-11-28
Hi,
Struggling with something in Rsync at the moment. I'm issuing the following command:

```
rsync -avz --delete --files-from=includes.txt --exclude-from=excludes.txt / /backup
```

Includes.txt contains:
```
/home/folder1
/home/folder2
/home/folder3
```

So that will happily backup the above three folders to **/backup**, and will delete any files in the destination that don't exist in the source anymore. However, if I remove **/home/folder3** from the *includes.txt* list, the folder isn't deleted from **/backup** (note: **/home/folder3** isn't added to the *excludes.txt* list, as it would be too cumbersome to maintain a big list).

Is there anyway round this - can i force Rsync to delete folders on the destination that don't exist on the source, when the data is being fed in with *--files-from*?

Cheers,
  Matt

---

### Post by p_quarles on 2007-11-28
Just to confirm that I understand correctly: you're trying to automate the process of removing folders in the target directory when they no longer have an analog in the source directory (correct?)

Deleting the source folder from includes.txt won't work, because rsync is no longer even looking at that folder. For the same reason, rsync wouldn't do anything if you passed a command that omitted the source directory altogether. 

I can think of a couple ways to do this, though. First would be to delete all the files and subdirectories in /home/folder3. Then, leaving the line in includes.txt, the folder in /backup will be emptied. This has the disadvantage of leaving some clutter, but you could always setup a cron job to delete empty directories in /backup.

Second idea is to simply replace "--files-from=includes.txt" with /home, and then use excludes.txt to specify what gets synched and what doesn't. This way, deleting a folder in /home would cause the next running of rsync to delete it in /backup as well, provided it's not listed in excludes.txt

Hope that helps, and let me know if I misunderstood the question.

---

### Post by PetePete on 2007-11-28
i had some strange problems with rsync a while ago to do with it not deleting folders, solution was to ensure that rsync was run with root perms...
eg. sudo rsync --blah lbah blah

---

### Post by feenster on 2007-11-28
Hi,
Thanks for your reply.

You have understood the question perfectly, however your answer won't work in my situation unfortunately (I think!). The data that is being sent to my server is coming from remote users, and I don't have control of their filing structure. Therefore, a user may one day decide that they don't want to backup */home/folderX*, and will remove it from their *includes.txt* file. The folder will still reside on their machine, so deleting it isn't an option. By the same token, it would be too fiddly to include everything and just exclude what isn't required.

I wonder whether the best option is to get the users backup job to upload their includes/excludes.txt file to the Server, and run a routine every so often to tidy up folders that weren't in the selection list. What do you think?

Matt

---

### Post by p_quarles on 2007-11-28
> **PetePete said:**
> i had some strange problems with rsync a while ago to do with it not deleting folders, solution was to ensure that rsync was run with root perms...
eg. sudo rsync --blah lbah blah
True if you're synching files that aren't owned by your user/group. If that's the problem in this case, it could be fixed by changing the permissions in /backup. I'm guessing that's not it, though, since the OP was able to write files there just fine.

---

### Post by MJN on 2007-11-28
It might be worth trying the **--delete-excluded** option as your --include-from option is effectively defining what's to be sync'd as p_quarles says. However, it is presumably also defining what's to be excluded (if it's not listed it's excluded) and so this delete-excluded deleting strategy may work.
 
I'd suggest trying it with --dry-run as I'm basing this suggestion on theory alone!
 
Mathew

---

### Post by p_quarles on 2007-11-28
> **MJN said:**
> It might be worth trying the **--delete-excluded** option as your --include-from option is effectively defining what's to be sync'd as p_quarles says. However, it is presumably also defining what's to be excluded (if it's not listed it's excluded) and so this delete-excluded deleting strategy may work.
 
I'd suggest trying it with --dry-run as I'm basing this suggestion on theory alone!
 
Mathew
Good call. That looks like it should work perfectly, but I second the advice about --dry-run.

If that doesn't do it, I would suggest looking at commands other than rsync to accomplish this. Using a pattern like:
```
cat include.txt | xargs *command*
```
you could use that file with a number of commands.

---

### Post by feenster on 2007-12-10
> **MJN said:**
> It might be worth trying the **--delete-excluded** option as your --include-from option is effectively defining what's to be sync'd as p_quarles says. However, it is presumably also defining what's to be excluded (if it's not listed it's excluded) and so this delete-excluded deleting strategy may work.
 
I'd suggest trying it with --dry-run as I'm basing this suggestion on theory alone!
 
Mathew

Hi,
I think this does work, but i can't prove it as i keep getting my syntax wrong. Can you guys look it over?

My command is this (line breaks added for clarity):
```
rsync -ravz --progress --rsh="ssh -p2995" --stats 
    --chmod=u+rwx --include="/home/username/testing" 
    --exclude="*" --delete --delete-excluded 
    --backup --backup-dir=~/archive/ --partial-dir=.partial 
    / username@remotehost.com:~/backup 
```

And my folder tree is this:
```

    /home/username/testing/test1
    /home/username/testing/test2
    /home/username/testing/test3
    /home/username/testing/test3/file1.txt
    /home/username/testing/test3/file2.txt
    /home/username/testing/test3/file3.txt

```

What i'm hoping should happen, is that if i delete /home/username/testing/test3 from the source, it deletes it from the destination too. However, if I run the command above, I get the following error message:
```
rsync: push_dir "/" failed: No such file or directory (2)
```

**Edit ::** Point to note: I changed from using --files-from as adding --delete-excluded to my original command didn't seem to delete the files on the destination that were no longer on the source.

Any ideas?
      Matt

---

