---
title: "Possibly the most unitentionally destructive, yet not destructive, find command"
date: 2008-01-30
forum: The Cafe
---

### Post by peabody on 2008-01-30
I just did [this](http://ubuntuforums.org/showthread.php?t=682558) to myself.

Everything's fine.  No worries.

But do you ever have those days when you think you're your own worst enemy?

---

### Post by LaRoza on 2008-01-30
I deleted the source for my System Restore program I am working on by accident. I meant to delete *.tar.gz, but put a space between the wild card and the extension and deleted every file.

Luckily, I got the byte code out of the trash of an earlier revision and did a bit of work with that and got my source back.

---

### Post by seventhc on 2008-01-30
> **peabody said:**
> 
But do you ever have those days when you think you're your own worst enemy?
I'd say that about 99% of the time I am my own worst enemy. 
:lolflag:  ](*,)

>>>This is why I always back everything up.

---

### Post by LaRoza on 2008-01-30
(Thread is going to be moved, there is no programming topic here)

---

### Post by peabody on 2008-01-30
Sorry, thought it was on-topic enough considering it was shell-code-gone-rogue.  I suppose it's more water-cooler type discussion though.

---

### Post by Ozor Mox on 2008-01-30
When I first started using Ubuntu, I deleted the file for the network loopback interface and caused my computer to stop booting. It was one of the times I almost gave up on Ubuntu due to my own idiocy.

---

### Post by erfahren on 2008-01-30
@peabody - saw your post earlier, I figured that would require a reinstall. glad it wasn't that bad. 

> **Ozor Mox said:**
> When I first started using Ubuntu, I deleted the file for the network loopback interface and caused my computer to stop booting. It was one of the times I almost gave up on Ubuntu due to my own idiocy.
I was practicing using the find command awhile back -- trying to find a file I had just named "file1" that I stuck in some directory in my ~/ and move it to ~/temp 
-- I put in "find ~/ file1 -exec mv {} ~/temp" - (forgetting the "-name")  

*everything* in my home got moved into that "temp" folder, and not "neatly" either. It was a serious mess.

- this was just after I read a post on some forum where the poster said "btw: be careful of using the find command with -exec - it can be very powerful".  --- hmmm.... he was right! lol

---

### Post by seventhc on 2008-01-30
> 
--- hmmm.... he was right! lolI've said the same thing to myself before... more than once. lol

---

