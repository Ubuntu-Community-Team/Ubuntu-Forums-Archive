---
title: "LVM and snapshots"
date: 2010-06-19
forum: Server Platforms
---

### Post by denarced on 2010-06-19
I was thinking the other day that in my home fileserver, I wanna use the snapshots for taking backups and I have 3 logical volumes: root, swap and home. The files are not changing all that much when I'm sleeping (and that's when the backups will occur) so I'm thinking that something like 100MB will be enough for snapshot LV (logical volume).

But how do I know?
Can I find out a typical scenario by trying?
Is there a way to check how much of the snapshot LV was actually used?

Participation to the conversation is appreciated.
Answer and/or superior wisdom not required.
:)

---

### Post by Agent ME on 2010-06-20
Snapshots aren't for backups; they don't persist after rebooting, and having them slows down disk writes a bit. A snapshot is better suited to make a frozen copy of a live filesystem, which you then backup (like with tar) so that way you can be sure that none of the files are changed while being backed up.

---

### Post by denarced on 2010-06-20
> **Agent ME said:**
> Snapshots aren't for backups; they don't persist after rebooting, and having them slows down disk writes a bit. A snapshot is better suited to make a frozen copy of a live filesystem, which you then backup (like with tar) so that way you can be sure that none of the files are changed while being backed up.

Absolutely, sorry if I gave the impression that I didn't know that.
My point was that how much of the reserved hdd space was in fact necessary?

---

### Post by Agent ME on 2010-06-20
The snapshot needs a bit more space than the lvm partition will change; for example, if you make a 100MB snapshot, and then write a 105MB file to the partition, the snapshot will fail and unmount. I usually set my snapshots to 500MB to 1GB.

---

### Post by denarced on 2010-06-20
And no way of knowing after it's done how much the 500MB was necessary?

---

### Post by benderisgreat on 2010-06-20
lvs shows under Snap% how much of the snapshot lv is used.

---

### Post by denarced on 2010-06-20
> **benderisgreat said:**
> lvs shows under Snap% how much of the snapshot lv is used.

And we have an answer.
My thanks go to you, benderisgreat.

---

### Post by plugbert on 2010-07-23
> **Agent ME said:**
> The snapshot needs a bit more space than the lvm partition will change; for example, if you make a 100MB snapshot, and then write a 105MB file to the partition, the snapshot will fail and unmount. I usually set my snapshots to 500MB to 1GB.

Some questions:

1. So the snapshot stores an entire copy of a file, not just the deltas?
1. So you could be in the middle of doing backup against a snapshot, and it would just suddenly dismount? 
2. How would you know that this has happened, just some error on the console saying that the volume/snapshot could not be accessed, or some obscure I/O error?
3. Would the system allow the dismount, seeing that there is a process still accessing the snapshot?

tia

---

### Post by denarced on 2010-07-24
You might be violating some rules here, I'm not sure but I often see cases where people get nasty remarks for re-opening old(solved) threads. Just thought I'd mention that.

1. Based on my experience, I'd have to guess it stores the deltas. Just a guess.
1. Yes, it'd just drop the mount.
2. I guess the first sign would be that your backup program, eg. rsync, would complain.
3. I'm thinking the system would allow it since it doesn't have any other choice. The volume is full.

---

### Post by plugbert on 2010-07-26
> You might be violating some rules here, I'm not sure but I often see  cases where people get nasty remarks for re-opening old(solved) threads.  Just thought I'd mention that.


my apologies. won't happen again ;)

---

