---
title: "How to log a output of program?"
date: 2015-12-29
forum: Server Platforms
---

### Post by Higgins909 on 2015-12-29
I've been given the code 
 ./gameserver >>/home/user/gameserver/logs/server.rpt 2>&1
The thing is I have no idea what the ending means.  I once had someone help me and they requested that-
I give the output of some command to them, and it some something similar.

I would like it to make a new log file every time I run it, is this possible?  So I have have a history of logs to look at.
What does >> actually do, is it some sort of shortcut for a program?  What is the programs name?

Thanks,
Higgins909

---

### Post by SeijiSensei on 2015-12-29
The > and >> symbols direct "standard output" ("stdout") to a file.  Using >> tells the operating system to append the output to an existing file.  The "2>&1" item at the end concerns output sent to the "standard error" ("stderr") device.  Usually even if you send stdout to a file, error messages sent to stderr will display on screen.  Using "2>&1" redirects those error messages to stdout and thus to the file.

If you want a separate file each time, use ">" and give the file a unique name each time the program is run.

---

### Post by MAFoElffen on 2015-12-29
Additional to what SeijiSensei said... One of my old Linux Instructors favorite sayings (each day), was that "Output from the left gets sent as input to the right..." I heard that every day for 2 years.

(output from left) ">" (gets sent right and overwrites the target file to the right)
(output from left) ">>" (gets sent right and appends to the end of the target file to the right)

There is a few more pipes and filters (use to get more specific), but those are the two basic redirections used in commandline and scripting.

As for log rotations, one way to set that up in your scripts, is to rotate through names, or concatenate a name structure where you rotate the lognames... in a cycle. So basically you move your old logs one step down (by changing their names) ... Then create a new log of the same name (same each time). That way, you always know where the latest/current log file is.
```

# Logic Example, based on if exists...
rm 5.log
mv 4.log 5.log
mv 3.log 4.log
mv 2.log 3.log
mv 1.log 2.log
mv 0.log 1.log
outputFromCurrent > 0.log

```

---

