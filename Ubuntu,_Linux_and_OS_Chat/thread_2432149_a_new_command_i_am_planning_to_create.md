---
title: "a new command i am planning to create"
date: 2019-11-27
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-11-27
i am planning to create a new command called "[COLOR=#0000cd][FONT=courier new]**trash**[/FONT][/COLOR]".  perhaps someone might want to develop a GUI app around it or its library code (where the real work will happen).

what the command will do when run with file object paths is move them to a directory named [COLOR=#0000cd][FONT=courier new]**~/.trash**[/FONT][/COLOR].  options -f and --flush will dispose of all contents of [COLOR=#0000cd][FONT=courier new]**~/.trash**[/FONT][/COLOR] into the great file system ocean, never to be seen again (unless running a program to sniff de-allocated sectors of the partition).  when the file object being trashed is already in the [COLOR=#0000cd][FONT=courier new]**~/.trash**[/FONT][/COLOR] directory, it will be flushed.  when first trashed, the first N file object paths being trashed will result in output of command lines (that can be copied and pasted) that restore the trashed file object back to where it was.

i will be writing this command in Python3 with an MIT-like license.  i am interested in hearing about any comments, suggestions, complaints, opinions, thoughts or volunteers before i get started.

---

### Post by yetimon_64 on 2019-11-28
Are you aware of the trash-cli package that already exists? It sounds a bit similar to what you are planning. Some of the commands it supplies are "trash-list" "trash-put" "trash-empty" and "trash-rm". 

It may pay for you to check whether or not you are "reinventing the wheel" here. It seems from my first reading of your post that you may be doing so; although it (trash-cli) works in with the current system trash location in ~/.local/share/Trash it sounds like your functions may be doing pretty much the same thing that it currently does.

**Edit**: I have just noted the trash-cli package doesn't seem to be able to restore a file, though trash-list shows the original location of the files in the trash bin.

---

### Post by Skaperen on 2019-11-28
yes, that is one of the things i check for.  that's why i have the apt-file package.  but i have had some trouble with it and it might not be working right.  perhaps its data is not working.  it seems to be there, but i do know it changed the format since xenial.

i have no "trash" command (yet) and no ~/.local directory.  what is the package name to install?  "trash-cli"?  i didn't knot that name to try.  i only looked for "trash".  there is no package named "trash".

restoring a file will, of course, depend on whether the file still exists, in either the disposal queue, or backups.  no i'm wondering if making trash and backups combined could have some benefit.  incremental backups would have both deleted and replaced files.  but these are a bit different, like, backups are typically done daily or weekly, whereas my form of "trash" would have each version you have trashed.  integrate that with other things you do, such as your personal editor front-end, and you could have pretty much everything saved somewhere, for a while.

one thought is to save everything in a place that can be scraped when space gets tight and allow that up to a limited age (only older files can be purged automatically).

---

### Post by deadflowr on 2019-11-28
> Edit: I have just noted the trash-cli package doesn't seem to be able to restore a file, though trash-list shows the original location of the files in the trash bin.

It depends on which release. For bionic and older it's backwards, restore-trash.
On A newer release like Eoan it's forward, trash-restore.
Though the man page list it as trash-restore for all though,
there's a bug for that issue: [https://bugs.launchpad.net/ubuntu/+source/trash-cli/+bug/1207674]("https://bugs.launchpad.net/ubuntu/+source/trash-cli/+bug/1207674")

---

### Post by yetimon_64 on 2019-11-28
> **deadflowr said:**
> It depends on which release. For bionic and older it's backwards, restore-trash.
On A newer release like Eoan it's forward, trash-restore.
Though the man page list it as trash-restore for all though,
there's a bug for that issue: [https://bugs.launchpad.net/ubuntu/+source/trash-cli/+bug/1207674](https://bugs.launchpad.net/ubuntu/+source/trash-cli/+bug/1207674)

Ah yes, I was thinking it was trash-restore (I am currently on Xenial), so I had that command wrong when looking for the man page earlier. It does exist here as restore-trash. Thanks for that bit of info deadflowr.

---

### Post by deadflowr on 2019-11-28
I do see it is written in or for python, but it's using (or at least requires) python 2.7 
Perhaps try contacting the various developers upstream about working on porting it up to python3.

---

