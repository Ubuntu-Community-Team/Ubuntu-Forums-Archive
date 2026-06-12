---
title: "How to &quot;see&quot; what's in &quot;.&quot; and &quot;..&quot;"
date: 2014-01-08
forum: Ubuntu, Linux and OS Chat
---

### Post by mrf14 on 2014-01-08
Years ago on an SCO system I had, there was a way of opening the dot and double-dot (local directory and previous directory) "files".  When I opened the "." file it would display a list of the names every file that was ever in this directory. As you can imagine, after a while the "." file could get rather large.

Anyway I was discussing with my friends I got a blank stare from them like I should be committed.  I tried on my Ubuntu to open the dot files and I couldn't do it.  Am I dreaming this up, or has the file systems changed over time, or is there a way to do it still?

If so how do I do it?  I fear "the men in white jackets" are on their way.

Thanks

---

### Post by lykwydchykyn on 2014-01-08
Sounds like a filesystem-specific feature, if it ever existed.  I'm pretty sure that the filesystem no longer saves the name of every file that was ever in a directory, that would be a profound waste of space.

---

### Post by hansdown on 2014-01-08
Hi mrf14.

You're right. You can see those files.

When your files folders are open, type

> cntrl +h

You will see the hidden files.

---

### Post by Copper Bezel on 2014-01-08
hansdown, I think you're confusing conventions. "Dotfiles" means hidden files in most Unix implementations, but mrf14 is talking about deleted files, unless he's also confused.

---

### Post by lisati on 2014-01-08
> **Copper Bezel said:**
> hansdown, I think you're confusing conventions. "Dotfiles" means hidden files in most Unix implementations, but mrf14 is talking about deleted files, unless he's also confused.

Agreed: "." has a special meaning, which can vary according to context. 

I don't recall ever encountering a file system where doing a directory listing of the "." or ".." *directories* showed a list of deleted files, at least not by default.

---

### Post by spjackson on 2014-01-09
> **mrf14 said:**
> Years ago on an SCO system I had, there was a way of opening the dot and double-dot (local directory and previous directory) "files".  When I opened the "." file it would display a list of the names every file that was ever in this directory. As you can imagine, after a while the "." file could get rather large.

Anyway I was discussing with my friends I got a blank stare from them like I should be committed.  I tried on my Ubuntu to open the dot files and I couldn't do it.  Am I dreaming this up, or has the file systems changed over time, or is there a way to do it still?

If so how do I do it?  I fear "the men in white jackets" are on their way.

Thanks
I don't think you should have anything to fear from "the men in white jackets". My memory's not perfect, but as an applications programmer, here's what I recall.

. and .. are simply directories, so what you can do with them is essentially the same as you can do with any directory, e.g. /bin, /home/me/Documents/ (you can't remove . and .. but I think that's the only limitation of their specialness). So what about directories? Currently under Linux, at the system call level, you can open them (see man 2 open), but you cannot read them with read (man 2 read). Attempting to read, results in the error EISDIR (Is a directory). In order to read the contents of a directory file, you must use readdir. Therefore you are not able to read them with plain read utilities like cat, more, less, od etc. (even by redirecting stdin). So I am pretty sure that the answer to "is there a way to do it still?" is no, and it is the kernel that does not allow it. (OK, if you don't use the filesystem, you can read all the blocks on a device, but that won't really help you.)

However, as you recall, with some Unix like systems, in the early(-ish) days (I first used a Unix in 1983), you could cat a directory (and probably wreck your terminal settings in the process). As I recall, the only thing you couldn't do was open a directory file for write access. I don't recall whether this was the case with early Linux. When a file was removed from a directory (via rm or mv or whatever), the directory entry would be marked as deleted, but the filename would not be overwritten. Hence you could cat the directory and see old filenames. I think that deleted entries would get reused if new files were added to the directory, so you wouldn't necessarily be able to see every filename that had ever been there.

To some extent at least, this is still the case with current Linux. Create a directory, and look at its size with "ls -ld". Add 1000 files to it, and you will see that the size of the directory increases. Delete all its files. Now the size does not shrink. Add another 1000 files with different names. The size does not increase. Although this behaviour must be filesystem specific, I can't think of one that doesn't behave like that - maybe an encrypted filesystem behaves differently.

Or maybe the men in white jackets are coming for me too!

---

### Post by Copper Bezel on 2014-01-09
Wow, fantastic explanation. Thank you!

---

### Post by hansdown on 2014-01-09
> **Copper Bezel said:**
> hansdown, I think you're confusing conventions. "Dotfiles" means hidden files in most Unix implementations, but mrf14 is talking about deleted files, unless he's also confused.

Thanks.

My mistake.:confused:

---

### Post by mrf14 on 2014-01-09
> **spjackson said:**
> [COLOR=#000000]However, as you recall, with some Unix like systems, in the early(-ish) days (I first used a Unix in 1983[/COLOR]


I'll stop looking over my shoulder:)

Your date is right on.  I thought  I was using SCO's 'full' UNIX version (that came much later) , but then I remembered it was Xenix.  I don't remember how I would look at the"." directory.  It must have been some convoluted command line as you suggested.  It never caused a problem.  It just seem strange to me that the names of the old files hung around.
 
Thanks.

---

