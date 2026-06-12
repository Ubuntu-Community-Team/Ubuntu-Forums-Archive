---
title: "rsync updates into a new directory"
date: 2006-09-08
forum: Server Platforms
---

### Post by carlossousa on 2006-09-08
Hello,

I would like to know if it's possible to update with rsync from pc1:/home to pc2:/home in a way that only the diferences between pc1 and pc2 end up in a rsync like pc3:/home/day[1...n].
In other words, the pc1 and pc2 are always in sync but a 3rd server would only save the updates instead of the whole copy.

Thanks

---

### Post by rastilin on 2006-09-09
There is an option for "--write-batch=FILE" which does output the differences between the systems, getting it to the third computer would involve a second step, either a remote mount to write the file into or trasnferring it accross later.

---

### Post by carlossousa on 2006-09-09
Hello and thanks for your reply.

Technically, yes, there are three machines in this process.
PC1 -> Actual work server
PC2 -> standard rsync from PC1 at 11PM daily
PC3 -> incremental update from PC1 -> PC2 on dayN

The problem is since I automagically do a rsync -av "ssh=root" pc1:/home pc2:/home, I would have to add your "--write-batch=FILE" into pc3 (via a scp copy for example) and say about 1/2 hours later make a rsync -av "ssh=root" pc1:/home pc3:/home_dayN using the FILE as a input on the rsync command?
Is this the way?

Thanks

---

### Post by rastilin on 2006-09-09
Yes and no. The batch file can go into any directory, although preferrably not one of the ones regularly synced. I just figured it would be easier to copy it across if you could remotely mount pc3 and write the file as it's being made.

Otherwise I think that's pretty much spot on.

---

### Post by carlossousa on 2006-09-11
Hi again,

What do you mean by "write the file as it's being made"? You can't "intercept" a file while it's being "rsynced"? Or can you?

Thanks

---

### Post by carlossousa on 2006-09-11
After some reading, adding the option "--backup-dir=pc3:/dayX" to the rsync command on pc2, technically makes a simultaneos backup to the 3rd server.
Gonna try it in the morning. Dont feel like ssh'ing into my server right now ... getting old sucks ... zzzzzzzzzz

Thanks

---

### Post by rastilin on 2006-09-11
I meant use nfs, sshfs or some other obscure driver to remotely mount a folder on pc3 onto a folder on your computer. Then you simply output the batch file to that folder.

---

### Post by carlossousa on 2006-09-13
Hello rastilin,

Well the only command options for rsync that appear to work as expected were:

rsyncuser@pc2:/#rsync -bav --backup-dir=pc3:/$DATE --rsh="ssh -l rsyncuser" pc1:/home home

lets see the log files generated later in the evening.

Thank a million!!

---

### Post by carlossousa on 2006-09-18
DAMN IT

I took a peek ate the pc3 directories and found out that the rsync -avb isn't workinh correctly.
There are files that have been added/changed between pc1 and pc2 that don't show up on the pc3 server.
Perhaps your idea of the batch=FILE option reveals the best situation.

This sucks

Any help?

---

