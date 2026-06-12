---
title: "Would anyone else like to see a secure empty trash option?"
date: 2009-03-08
forum: Ubuntu Brainstorm
---

### Post by blueshiftoverwatch on 2009-03-08
Would anyone else like to see a "secure empty trash" option added to K/X/Ubuntu's trash bin in a future release, similar to what Macintosh OSX has? Basically such a feature would write over the disc space where the files that you wanted deleted were located several times with zeros to make it unrecoverable (or at least much more difficult to recover) by data recovery software.

There are various ways to do this from the command line. But it would be much easier were it included in the GUI for easy access. The Ubuntu devs wants to keep their default installation down to what will fit onto one CD. But I don't think that something like this would take up very much space.

---

### Post by Dougie187 on 2009-03-08
Sounds like a good idea. Maybe you should post it on brainstorm.

---

### Post by Zirconic on 2009-03-08
Yes.  Especially where you can choose the method and number of overwrites.  I use Eraser on Windows.  Fantastic program.

---

### Post by halovivek on 2009-03-08
sounds good.

---

### Post by mrsteveman1 on 2009-03-15
Absolutely. It might be possible to alter the way the existing one works temporarily if people really need this functionality, for instance if it is written in python or if there are hooks somewhere that could be used to change what it does. Anyone know?

---

### Post by TDK800 on 2009-03-15
Excellent suggestion, we should add it to launchpad!

---

### Post by HermanAB on 2009-03-16
This feature already exists.  Use the alternate install CD and encrypt the disk partitions when you install Ubuntu using LUKS.

Overwrite erase methods won't be implemented because they do not really work on modern file systems.

Cheers,

Herman

---

### Post by seanlano on 2009-03-17
I don't see why you wouldn't want that. Even if you don't use it that often, it would still be a useful feature to have.

---

### Post by blueshiftoverwatch on 2009-04-08
> **HermanAB said:**
> Overwrite erase methods won't be implemented because they do not really work on modern file systems.
How so?

---

### Post by Simian Man on 2009-04-08
The only way to erase data from a modern hard drive is with a blow torch.  This proposed feature would give people a false sense of security.

---

### Post by benj1 on 2009-04-08
> **Simian Man said:**
> The only way to erase data from a modern hard drive is with a blow torch.  This proposed feature would give people a false sense of security.

does that mean shred doesn't work either?
in a similar vein, how recoverable are things deleted on an ssd??

---

### Post by soltanis on 2009-04-09
What HermanAB is referring to is that on journaling file systems (read, anything higher than ext2), even if you overwrite the hard disk sector(s) where the file is stored, a copy of the file may still be kept in the journal (hence, still recoverable). Another issue is that with advanced filesystems (read, anything higher than ext2), opening a file and then overwriting it over and over does not necessarily guarantee that the file's original data on disk was actually overwritten.

Shred actually overwrites the sectors on disk where the file is stored, but doesn't overwrite other copies of the file that may exist or data in the journal.

In relation to flash drives, due to wear-leveling algorithms, attempting to physically overwrite data kept on the drive will almost never work. The best option in this case would probably be to erase the entire drive.

Encrypting your partition is a much better way to secure your data. Using utilities like shred or eraser (in Windows) still renders your data recoverable (though, with each pass, the time and expense required to recover it, even with special hardware, rises quite significantly).

---

### Post by blueshiftoverwatch on 2009-04-09
> **soltanis said:**
> What HermanAB is referring to is that on journaling file systems (read, anything higher than ext2), even if you overwrite the hard disk sector(s) where the file is stored, a copy of the file may still be kept in the journal (hence, still recoverable). Another issue is that with advanced filesystems (read, anything higher than ext2), opening a file and then overwriting it over and over does not necessarily guarantee that the file's original data on disk was actually overwritten.
Why couldn't a program be made that would keep a record of where every copy of X file is on your hard drive so that when you went to overwrite the space that file is located on to securely delete it the other locations it was copied to would also be over written?

Also, knowing what you just said why does Apple include a secure delete function in Mac OSX? It seems like the only viable option to securely delete files would be to have the OS over write every single part of the hard drive that was either blank or marked for deletion. Which OSX does include. Of course if there was a copy of the file somewhere else on the hard drive over writing blank portions of the hard drive wouldn't delete the copy since it wasn't marked for deletion it's self, only the original file. Which brings me back to my idea of keeping a record of where copies of the original file are located.

---

### Post by gnomeuser on 2009-04-10
> **Simian Man said:**
> The only way to erase data from a modern hard drive is with a blow torch.  This proposed feature would give people a false sense of security.

That is not entirely true, while current hardware does create a window for recovering data we can make it cost prohibitive to do so. Successive overwrites with random data would require significant investments to recover the underlying data. If you have the requirement that data must be 100% unrecoverable, you know what to do and have military style protocols for doing so and verifying completion. Your average person wanting to remove sensitive work data might benefit from the additional assurance.

I would even argue that once you delete something you should be assured that it is completely gone so we might want to make this the default behaviour.

One issue to consider though, SSDs tend to dislike all this writing, and this would definitely exasperate that problem considerably. There are also considerations as to performance, at least for the case of making it the default behaviour.

---

### Post by CarpKing on 2009-04-14
I've always wondered why new filesystems (ext4, btrfs, et cetera) never seem to include more secure deletion among their features.  You'd think that if older versions (ext2) allowed for more security on that front than current ones, the newer ones would try to improve.

---

