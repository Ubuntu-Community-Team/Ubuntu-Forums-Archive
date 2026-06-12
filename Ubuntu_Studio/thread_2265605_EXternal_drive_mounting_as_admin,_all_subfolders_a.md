---
title: "EXternal drive mounting as admin, all subfolders also admin, cannot read/write"
date: 2015-02-16
forum: Ubuntu Studio
---

### Post by mrule on 2015-02-16
Hi, I went to make a backup today to a WesterDigital MyBook and found that I could not read/write from the drive. It seems like Ubuntu Studio is auto-mounting it with owner and group "admin", also applied to all sub-folders and files. I can change the ownership of the mountpoint but the subfolders are still all owned by admin. 

I do not remember this happening before. I have searched for some time using google and also within these forums and have not been able to find someone with a similar problem, or a solution.

What is causing this? How do I fix it? .. help

---

### Post by Bucky Ball on 2015-02-16
Do you have NTFS or EXT* partitions on the MyBook?

---

### Post by mrule on 2015-02-16
The partition is EXT4

---

### Post by mrule on 2015-02-17
Anyone? I talked with some friends and no one seems to know how to fix this. I still need to make a backup to this drive for work and so I'm still in a bind. Help...

---

### Post by Bucky Ball on 2015-02-17
Ok. Start [here]("https://duckduckgo.com/?q=change+permission+ext+ubuntu"). Perhaps you need to change the permissions on the partition. Without details, hard to know exact commands.

Perhaps let us know where the partition is mounting (have a look in Gparted for /dev/sd**).

---

### Post by mrule on 2015-02-17
ok; the drive auto-mounts at

/media/$USER/<<drivename>>

The owner and group for this mount-point is $USER, but all of the contents are owned by "admin"


Reviewing those links, I find no real solutions.
-- corrupted drive? no.. not applicable, is mounting as admin, not as read-only
-- using chown -R? yes, that will work, but will take an extremely due to the size complexity of the file tree on this drive. I'd be surprised and disappointed if this is the answer.
-- I can use sudo to interact with the drive, but this doesn't solve the underlying issue. and I'm worried new files could end up with strange ownership / permissions
-- I can add an fstab entry and reboot the machine. But this is ridicuous, this is a portable backup drive, it's not really associated with the machine, and I shouldn't have to manually add fstab entries to use a portable USB external drive, that is simply an unacceptably bad user experience and a damning assesment of the design and implementation of Ubuntu if so.

So, none of the existing solutions seem appropriate. Clearly there must be an underlying reason why this drive, and only this drive, is mounting as "admin"? None of my other external USB drives are doing this? A recursive chown on the whole drive just seems... wrong.

---

### Post by mrule on 2015-02-17
I'm just going to run the recursive chown command. It probably isn't actually fixing the real problem, but ... had I started it yesterday when I posted this thread it might just be about finished now, so it is possible that it will lead to a solution faster than actually understanding what is broken.

---

### Post by mrule on 2015-02-17
ok; here is an update of my understanding of the problem:

ext4 actually preserves and remembers permissions. somehow, this drive got set so that everythign is owned by "admin". I don't really understand how this is possbile. My best guess is that all of these files and folders were actually owned by some "other use" which didn't match my user ID, and so got mapped to "admin" when mounting. This is speculation, I don't even know if permissions work like this. If they do, then the question becomes: is there a way to set linux ownership and permissions on an external drive such that the files are always readable and writeable to anyone who mounts the drive? If so, what is the command to fix this.

chown -R $USER:$USER /path/to/mountpoint

Is a workaround that will restore access to the current user, that works but can take a long time to run on large drive. I am not sure that this repairs the problem in general.

---

