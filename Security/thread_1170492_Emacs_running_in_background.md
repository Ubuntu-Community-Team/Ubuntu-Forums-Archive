---
title: "Emacs running in background???"
date: 2009-05-26
forum: Security
---

### Post by dwinner on 2009-05-26
Hello,

I don't know if this is security related or not, but it is puzzling:

Running Xubuntu (hardy), and noticed that the hard drive was churning, even though I wasn't doing anything. Figured it was just a cron job or something, but for laughs and giggles, I opened an xterm and ran "top".

And at the top of top, I see emacs22 as the top process.

What????

I had no emacs sessions open, and wasn't even using the system.

Any ideas why I would see emacs22 in there?

Thanks,
DW

---

### Post by lensman3 on 2009-05-28
If you have a terminal open, then type in the command "jobs".  If emacs is in the list (with a number after it) do a "fg <number>".  That will bring it back into the terminal.  Unfortunately, you have to find the terminal that you CNTL-Z and "bg" the emacs editor.

If that doesn't work, then "kill -3 <pid>" where pid is gotten from the "ps" command.  The -3 SOMETIMES will -HUP (hangup) the process so that it will save the file as it exists, if the code was written that way.  If that doesn't work the do "kill -9 <pid>".   The -9 will kill the  process unconditionally.

CNTL-Z suspends a process and the "bg" command pops it into the background (same as the & at the end of a command). The fg <pid> brings the command back to the command prompt.  And the "jobs" command lists the suspended commands.  "fg" by itself will restart the last suspended program.  "fg -" will bring the second suspended program to the command line and leave the first program suspended.

Hope this helps.

---

### Post by Beowolf64 on 2011-03-19
This happens on my box too. Right after reboot emacs23 starts running in background. **top** reports 1 hour + running time, even thought the system was just reboot and no emacs instance was started yet.

---

