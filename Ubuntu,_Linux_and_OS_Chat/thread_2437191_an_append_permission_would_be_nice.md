---
title: "an append permission would be nice"
date: 2020-02-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2020-02-19
it would be nice if Linux supported an append permission.  and i don't mean the 'a' extended file attribute which only root can set or unset.

---

### Post by TheFu on 2020-02-19
Exactly, how would that be implemented in any current file system?  
How do 10,000 users with append not get allowed to remove each other's prior additions?  Basically, a DB would be needed, so why not just use a DB with row-level access controls?

Plus, Linux is trying to retain compatibility with BSD and Unix.  How do those systems accomplish this feature?

---

### Post by Skaperen on 2020-02-19
it would not make sense to have more than one concurrent append-only open on a file.  but that is already the case for write.  when a file is normally open for append under the current permission scheme by 2 processes, they can still overwrite each other as simply as just writing their append data.  my suggestion is not about changing that.  it is about disallowing existing data from being overwritten.

it would be implemented with a range value in the open descriptor structure as large a C type as the file size.  when open, if write permission does not exist then the range value is set to the current file size, otherwise it is set to zero.  no writes are allowed at any position lower than the range value.

i have thought about the overwrite issue.  a way to do that is a new syscall that could be called [COLOR=#0000cd][FONT=courier new]**atomicappend(const void *buf, size_t count, const char *pathname, int flags, mode_t mode)**[/FONT][/COLOR] with mode being optional as it is in open(2).  the filesystem code would handle it or the kernal can do the open/write/close sequence.  this could be defined to write in the order called if on a single processor and "best effort" on a multiprocessor.

Linux has features the others don't have.  but if they have added them and Linux has stopped adding any, then consider this for all, if that's the only way progress can happen.

i am not really suggesting a change.  it would be too disruptive.  imagine the effect on chmod having an argument now in hexadecimal.  but what if someone implemented a whole new OS with a file system that included such permissions in it inode structure and someone wanted to be able to mount it on Linux.  that would be a "fun" development.

---

### Post by Skaperen on 2020-02-19
there perhaps could be a mixed-sequential-record-write mode that could allow 2 or 10,000 processes to put intact records into a file.  an append mode would be an agreement not to truncate.  an append-only permission would require that.  all opens after the first must request append mode.  sequential mode would disable seek and tell.  position is meaningless to other than the kernel thread putting the queue of written records into the file (in kernel page buffers).

---

### Post by TheFu on 2020-02-20
What happens if the file owner inserts data at the beginning, shifting the append location while someone else has it opened for append and is writing?

Why not just use existing file locking techniques that have been around 40 yrs, if only 1 appender is allowed at a time?  There are methods for that today. Yes?

I thought you wanted different users to have full unix-style permissions on each appended block to prevent others from modifying their data and preventing modification of any previously written data, earlier in the file.  That would be harder, methinks.

---

### Post by Skaperen on 2020-02-20
i'm not aware of an insert() file syscall/operation.  i doubt an owner of a file that has granted append-only operation permission would modify the file in a disruptive way without locking in.

this read-only idea is simply about being able to grant permission to write but not over the data that exists.  other scenarios are not the idea.  it is about what the owner permits others to do, not about what the owner permits herself to do.

---

