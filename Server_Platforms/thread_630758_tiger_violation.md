---
title: "tiger violation"
date: 2007-12-03
forum: Server Platforms
---

### Post by bigmac_bb63 on 2007-12-03
15:40> Checking permissions and ownership of system files...
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem
15:40> Checking for indications of break-in...
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem


This is what I'm getting. Does anybody know what this is or how to fix it? 

Thanks,
Penguinista

---

### Post by akvik on 2007-12-04
Found this, haven't tried it. Have the same thing:
> 
Binary package hint: tiger

Tiger reports the following information:

  --CONFIG-- [con010c] Filesystem securityfs used by securityfs is not
recognised as a local filesystem

The fix is to add this line around line 100:

  [ "$1" = "securityfs" ] && LOCAL=0

A similar problem was described here:

  [EMAIL PROTECTED]/msg00006.html

This affects the version of tiger in gutsy.

** Affects: tiger (Ubuntu)
     Importance: Undecided
         Status: New


---

### Post by fireman71 on 2007-12-04
> **akvik said:**
> Found this, haven't tried it. Have the same thing:

I am having the same problem and found the above information as well, but I am not a coder and don't claim to be.

I did look in the /etc/tiger/config file around line 100 and it dosen't look like the above line fits in there.

Can anyone point us to which exact file and maybe something to look for in that file that gives us a landmark on where to insert the line at? Like the line that immediately preceeds the insertion point?

Thanks!

---

### Post by akvik on 2007-12-11
I think the qoute above is an adjustment you do in the source code. Haven't checked it myself, just learning to live with it... :)

---

### Post by glenstewart on 2007-12-12
To fix, open /usr/lib/tiger/systems/Linux/2/gen_mounts with a text editor.

Scroll down to anywhere near line 100 and paste in the following lines:

  [ "$1" = "securityfs" ] && LOCAL=1
  [ "$1" = "unionfs" ] && LOCAL=0

The file is attached for those who don't like text editors (be sure to remove the .txt suffix when saving to disk) :)

You'll notice I also added unionfs, which on my system is also generating a complaint.  The gen_mounts list is a little behind the times, I guess.

---

### Post by simon_w on 2008-04-01
Thanks for this!

---

