---
title: "Running chkrootkit from a Live CD?"
date: 2005-11-25
forum: Server Platforms
---

### Post by wargames on 2005-11-25
If I want to check my Ubuntu Breezy hard drive install with chkrootkit from a Live CD such as the Ubuntu Live CD or Knoppix Live CD then how would you do this?

I would like to check it this way just to make for sure that nothing has compromised my installation and I heard using a Live CD would be a good thing because you would be running from a trusted Live OS.

Anyway to do this?

---

### Post by towsonu2003 on 2005-12-05
I am not really sure about this really, but, I would think chkrootkit would not be so useful when you run it from live cd. A rootkit is invisible to the kernel (?) it was installed 'to'... It should be visible to the live cd kernel... 

But no idea how to scan using live cd... 

PS. all the misuse of terms in the above 4 lines should give you a clue that I'm really a newbie on this. Check out this live cd, as it may have the tools you need: [http://distrowatch.com/table.php?distribution=auditor](http://distrowatch.com/table.php?distribution=auditor) [distrowatch.com] - read the documentation as usual :)

---

### Post by LordHunter317 on 2005-12-05
The only useful place to run a rootkit detection tool is a live cd.

Simply mount your compromised volumes and point the tool there.  I don't know how to do that for chrookit off hand.

---

### Post by towsonu2003 on 2005-12-05
[QUOTE=LordHunter317]The only useful place to run a rootkit detection tool is a live cd.[/QUOTE]

too much new stuff to learn, brain is exploding... :) thanks for correcting me-

---

