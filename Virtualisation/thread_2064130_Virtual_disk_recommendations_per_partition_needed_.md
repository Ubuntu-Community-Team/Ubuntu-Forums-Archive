---
title: "Virtual disk recommendations per partition needed - VirtualBox"
date: 2012-09-28
forum: Virtualisation
---

### Post by damonO on 2012-09-28
I am what I would classify as between a novice  and intermediate Linux user. Definitely not a 100% n00b, but I still  have a lot to learn, and I'm definitely not a system administrator, on  Linux or any other flavor of machine.
  I'm looking for some guidelines, opinions, advice, etc. specifically  around setting up Linux on a VirtualBox VM. I know that there won't be  too many differences, but what I really think I need guidance on is  which partitions (with matching virtual drives in this case) should be  versioned with the snapshot, and which should NOT be versioned, or set  to write-through.
  On both my regular install and my VM install, I have a separate  partition for each of the following paths; on my VM install, each  partition has its own virtual disk:
  
[LIST]
[*]/
[*]/boot
[*]/home
[*]/tmp
[*]/usr
[*]/usr/local
[*]/var
[*]/var/log
[*]swap
[/LIST]
  This partition tree is due to recommendations I read a while ago that then you can leave your home directory alone on new installs, prevent log or tmp floods from taking down your entire system, set appropriate flags such as noexec and nosuid, etc.
  On my regular computer, my backup strategy only hits /home and /usr/local because I don't care if I have to reinstall. I'm strict about my scripts (which are rare anyway) going to sub-directories of /usr/local. 
  But since I'm setting up the VM *AND* it gives me the ability to snapshot, I'm thinking a workflow of somethilng like this:
  
[LIST]
[*]Get it set up how I want it
[*]Snapshot it
[*]Regular backup strategy continues on /home and /usr/local,
[*]New updates are out so:
[LIST]
[*]Roll back to the latest snapshot,
[*]Update,
[*]Snapshot,
[*]Test it out,
[*]Delete the old snapshot (merges this snapshot backward) when happy.
[/LIST]
 
[*]New software out that I want to try:
[LIST]
[*]Install it
[*]Try it out
[*]Roll back to the last snapshot,
[*]And if I liked the software, install and snapshot
[/LIST]
 
[/LIST]
  **My Question**

  So **my question,** finally, is with that workflow, am I OK with setting the following to write-through (not versioned on snapshot):
  
[LIST]
[*]/home
[*]/usr/local
[*]/tmp *because I don't need to roll these back*
[*]/var/log *because I don't need to roll these back*
[/LIST]
  and leaving the rest of the partitions / virtual drives be imaged when I do snapshots?

---

### Post by idlemind324 on 2012-10-02
The only problem I see is skipping the changes on /usr/local and that is really only if you are planning on adding your own software to the system. That said if you are not actively using that directory on your own I would encourage you to include it in your snapshots just to be safe that any future updates or software packages you install don't add stuff to that directory that wouldn't then get properly rolled back during any uses of your snapshots.

---

### Post by damonO on 2012-10-04
Thanks for the reply!

I do make backups of /home and /usr/local, which is why I wasn't going to snapshot it. But you make a good point, I rarely change it, so I'm probably fine just snapshotting it.

One other thing I thought of after posting this is I could (should) just take whatever strategy I try and make sure I can load the VM successfully on another machine, simulating a restore.

---

