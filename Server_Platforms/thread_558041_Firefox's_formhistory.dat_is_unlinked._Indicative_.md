---
title: "Firefox's formhistory.dat is unlinked. Indicative of cracker?"
date: 2007-09-23
forum: Server Platforms
---

### Post by Johnny K on 2007-09-23
I was reading [this page]("http://dmiessler.com/study/lsof/") yesterday. It says that if you type **lsof +L1**, it "shows you all open files that have a link count less than 1, often indicative of a cracker trying to hide something."

Well, when I type **lsof +L1** the following is returned:
```
COMMAND    PID USER   FD   TYPE DEVICE SIZE NLINK     NODE NAME
firefox   5757 john   10r   REG    8,1 5247     0 10732613 /usr/local/firefox32/firefox (deleted)
firefox-b 5783 john   54u   REG    8,1  225     0  2425621 *[profile folder]*/formhistory.dat (deleted)
```

Yesterday, the file ***[profile folder]*/XUL.mfasl** was also listed.

Should I be worried that someone is trying to steal my form history and other information?

---

### Post by pjbgravely on 2007-09-24
The command is really lsof +L1 , and no I didn't get any hits on 2 machines. Have you updated firefox? The files say deleted, but are probably really still there because nothing is deleted in Linux until every program stops using it. Try re-logging in and see if it clears. If it doesn't then I am at a loss. 

Paul

---

### Post by cookfromfrozen on 2007-09-25
that means the file has been unlinked (deleted) while firefox still had it open.  linux does not prevent files from being unlinked while they are in use.  when firefox closes the file, it should disappear.

if not it may have become an orphaned inode and will be cleared on next reboot

---

