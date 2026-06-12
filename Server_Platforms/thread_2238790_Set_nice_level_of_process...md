---
title: "Set nice level of process.."
date: 2014-08-10
forum: Server Platforms
---

### Post by dutchgigalo on 2014-08-10
a reply to this thread [ubuntuforums.org  #1868939]("http://ubuntuforums.org/showthread.php?t=1868939")  (closed)
Set nice level of process....

script:
```
 
# Some command, the server is restarted.
#...
# Get the (new) SRCDS PID, grep args depend on the output of ps.
PID=$(ps -ef | grep ... )   
# Change niceness.
renice -20 $PID
```

( for "grep ..."  set running process) 

Strange it also looks for processes that doesn't exist.? :frown:

```

renice: failed to get priority for 5871 (process ID): Process does not exist
renice: failed to get priority for 5869 (process ID): Process does not exist

```

---

### Post by Lars Noodén on 2014-08-10
Not that strange.  renice needs a positive integer, the Process ID (PID), of the process to renice.  The ps | grep combo above will not produce that, you'd really need ps plus awk to get the right column.  Instead, [pgrep](http://manpages.ubuntu.com/manpages/trusty/en/man1/pgrep.1.html) will do much of what ps and grep can do.

---

### Post by dutchgigalo on 2014-08-10
thought so its a very basic script ...  thanks for the tip about pgrep ....

---

