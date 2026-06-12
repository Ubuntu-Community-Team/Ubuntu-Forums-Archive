---
title: "Restore Evolution via Ubuntu One"
date: 2010-01-30
forum: Ubuntu One (CLOSED)
---

### Post by the.scarecrow on 2010-01-30
I think this shows up an interesting problem/bug in U-1 related to restoring all your settings in Evolution from a backup settings file e.g.

evolution-backup.tar.gz

In a Karmic installation I created and placed this file in the U-1 folder, let it sync up(load) and then sync down(load) to a new installation of Lucid all apparently successful. I then tried to restore this file to Evolution from the U-1 folder in Lucid and it fails with the error message:

"Please select a valid backup file to restore"

Then in Lucid I copy the evolution-backup.tar.gz file from the U-1 folder to the Desktop and try to restore settings in Evolution from this copy file in Desktop and it works perfectly.

Is it a bug or can it be explained?

---

### Post by duanedesign on 2010-02-01
the.scarecrow
I can confirm this behaviour. I will look into this and see what i can find out.
thank you,
duanedesign

---

### Post by duanedesign on 2010-02-01
ok i looked into your bug and i have found the issue. It is actually a bug with Evolution. 

[https://bugs.edge.launchpad.net/ubuntu/+source/evolution/+bug/447888](https://bugs.edge.launchpad.net/ubuntu/+source/evolution/+bug/447888)

comment #6 might be of interest, there is a workaround. But i believe you already figured this out. 

thank you
duanedesign

---

### Post by the.scarecrow on 2010-02-02
@duanedesign, yes thanks for that the problem is almost the same. I need to move the file to other folders and see if its possible to restore from files embeded deeper in my home directory. Or maybe in my case its specific only to the Ubuntu One folder. 

I will report back later. I just re-created my Lucid USB stick from the daily Live so I must do a bit of configuration first.

---

### Post by mike_abc on 2010-03-26
I'&#314;l put my two cents in, since this thread (and links) actually solved my inability to restore the **Evolution backup file**.

(1) The backup file must be placed in your home directory (/home/<username>)
 
and, very important !!

(2) The file must have its original name i.e. "evolution-backup.tar.gz", **orelse**. I say this because I make several backup files during a month and prefix the backup files with the dates. **Evolution-restore won't accept a file that has not the original name.**

Cheers & success

Mikey

PS. And they say Windows is stupid...

---

### Post by joshuahoover on 2010-03-26
> **mike_abc said:**
> I'&#314;l put my two cents in, since this thread (and links) actually solved my inability to restore the **Evolution backup file**.

(1) The backup file must be placed in your home directory (/home/<username>)
 
and, very important !!

(2) The file must have its original name i.e. "evolution-backup.tar.gz", **orelse**. I say this because I make several backup files during a month and prefix the backup files with the dates. **Evolution-restore won't accept a file that has not the original name.**

Cheers & success

Mikey

PS. And they say Windows is stupid...

This is correct. Evolution's restore is very strict about the name and location of the backup file. I haven't tested this in Lucid yet to see if it's fixed there but know it's an issue with Karmic and lower.

Thanks for sharing this info Mikey!

Joshua

---

