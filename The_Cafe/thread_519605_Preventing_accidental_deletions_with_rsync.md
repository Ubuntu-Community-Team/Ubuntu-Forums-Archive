---
title: "Preventing accidental deletions with rsync"
date: 2007-08-07
forum: The Cafe
---

### Post by Ozor Mox on 2007-08-07
Ok, this might seem like a pretty stupid question, but I figure someone might have some clever input.

I'm using rsync to backup to my external hard drive, and then from there to my other computer, and it does the job absolutely flawlessly. The only thing is, it does exactly what I tell it, and I'm scared of human error on my part messing things up and losing me data.

For example, say I create file X, an OpenOffice document, on my computer, then later I make a backup using rsync. It will copy X to my external drive, great. Then later, I add more to X so it's now X+1. I make another backup and it will replace the old version of X on the external drive with the new version X+1, that's what I want. But if I accidentally got the source and destination backwards, X on the external drive would replace X+1 on my computer and make it X, losing my changes.

When using rsync, I use -n for dry-run, -v for verbose, and don't use --del for delete on destination until I've checked what it's doing first. But that only protects me against files that have been added or deleted, because in the logging, files I thought should be added would be deleted and vice-versa if the source and destination were backwards. But for file changes, I wouldn't notice until I'd done the rsync and it was too late.

Anyone got any clever suggestions on how I should backup and avoid this potentially happening? I guess I don't trust myself enough!

---

### Post by koenn on 2007-08-07
If a question ever  deserved a RTFM reply, I think yours would be it. 
Clearly you know how to use rsync, including the no-action, delete on target, and verbose switches. How hard is it then to look up the rest ? 

It's probably "rsync from ... to ... "  - even commands are "intuitive". 

You're right, tools like rsync do what you tell them to do. Be happy they do. Imagine how much damage they could do if they'd just do as they please regardless of what you tell them. 

And since backups are something you ought to do regularly, why don't you write down your rsync statement, say, in a file, and makke it executable, so you can run it as a script. It would save you the trouble of having to look up the syntax with every backup you want to do. 

Just make sure you don't get source and destination backwards.

---

### Post by Ozor Mox on 2007-08-07
That's a bit of a harsh reply, but I'm going to ignore that for now and just pick out the useful stuff.

I have read the man page. There are a LOT of switches, that do a LOT of extremely complicated things that I don't understand. I thought someone might be able to give me the benefit of their experience with switches other than the dry-run one that I already have found myself, for example one that shows me modification date or file size comparisons or something.

I am very happy that rsync does as its told, but still being relatively new to Linux, the command line can be a bit scary when dealing with many gigabytes of data because it does instantly what you told it as you press enter.

At the moment, I just go through my command history using the arrow keys to find the correct rsync command I used before, but putting it in an executable text file is actually a good idea that I didn't think of, thanks.

I'm not very knowledgeable with scripts and advanced command line things yet, as I have not used them before. Only found man a little while ago, for actually reading about what the commands do.

---

### Post by Isaac_x on 2007-08-07
This is the first time I see RTFM on ubuntuforums.org.

A person asked an intelligent question, at least try to give an intelligent answer.

Good question Ozor Mox, I don't know how to do it, but I'd like to know the answer too.

---

### Post by kanem on 2007-08-07
Well, the answer was useful.

I was afraid of something like this happening with my backups too so I wrote a script. They're easy, here's an example:
```

#!/bin/sh
rsync -av --delete /mnt/original/ /media/backup_drive/backup_folder

```
Write this to a file, make it executable (chmod +x filename) and put it somewhere like /usr/local/bin.
So you get it right once, make a script and not worry about screwing up the order or commands.

---

### Post by koenn on 2007-08-07
> **Isaac_x said:**
> A person asked an intelligent question, at least try to give an intelligent answer.

- I suggested a sollution/workaround for his problem (script it), 
- I hinted at a way for the OP to remember the source/destination order : whether you copy, cut/paste, drag/drop, move, ... it's always "from ... to ... ". Apparently that order comes natural to people. rsync is no exception. 

so, two usefull answers. Intelligent enhough for you ?
Plus I give the OP credit for being capable of finding answers.
There are worse ways to  reply, I'd say. 

Besides, it's the cafe. You have a better chance to a serious, friendly worded reply in the Help forums. .

---

### Post by Ozor Mox on 2007-08-09
I have produced my own scripts now.

rsynctest_toext
rsync_toext
rsynctest_fromext
rsync_fromext

To dry-run and actually run rsync to and from my external hard drive!

However, after looking through the tons of command line options for rsync I have found

```
-u, --update                skip files that are newer on the receiver
```

in case anyone's interested. It looks like with -u it would not overwrite a file that is newer on the destination than the source, and would therefore not allow work to be undone.

I'm posting this because other people asked about it.

Think this would do the job?

---

