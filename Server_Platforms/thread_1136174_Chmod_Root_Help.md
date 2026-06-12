---
title: "Chmod Root Help"
date: 2009-04-24
forum: Server Platforms
---

### Post by tybasher on 2009-04-24
Hey guys, My idiot friend ran sudo chmod 755 -R /

Now nothing works, i cant use anything at all, and i cant change the permissions back. I have important documents on the server, is there any way to fix this problem? Any help is much appreciated. 


Im running Ubuntu Server 8.10

---

### Post by neilevan814 on 2009-04-24
I am no expert, but couldn't you just sudo chmod 777 -R / and then go back and tighten up directoires from there?

---

### Post by BkkBonanza on 2009-04-24
Oh hell, way too much work to fix that. If your system isn't heavily loaded then it may be easiest to backup data and re-install. 

You could write a script to run when booted from a live cd that will run down the livecd file tree and then fix the corresponding permission on the bad-system hard drive. And then patch up your home directory manually since it won't be on the live cd.

Or in a similar way you could inspect each subdirectory of the live cd and manually apply the same permissions to the corresponding bad-system directory. If you do something like,

[B]ls -Rlsa / >masterlist
less masterlist[/B]

Then it should be easy to browse masterlist and get a sense of what the overall permission landscape is for various subdirs. At least in theory the sticky and sid/gid bits should not have been affected by his ruinous command so it's only the main perms that need fixing. Good luck - and go put out a contract on your "friend".

---

