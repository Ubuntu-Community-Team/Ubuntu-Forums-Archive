---
title: "Prevent a BASH script from being called to run again until it exits"
date: 2011-08-17
forum: Server Platforms
---

### Post by meridionaljet on 2011-08-17
Hello,

I'm planning on writing a BASH script for my website's server that will process data from user input via HTML forms, and then write data to the website's HTML documents. My question regards how to deal with the possibility that two users send form information very close to the same time, thus having the BASH script being called again while the first instance of the script has not yet finished. 

I don't even know what happens in general when a BASH script is called while it is still running. Even if that is ok, and a new, separate script process is started (or whatever really happens), how am I supposed to prevent issues that could come from two different instances of the script trying to write to the same file at the same time? Is there a way to force the BASH script to finish its work before launching again, in the event of multiple requests? 

Any help would be appreciated.

---

### Post by hawk2010 on 2011-08-17
I think the issue here is whether your BASH script writes to the same file. why dont u elaborate more?

---

### Post by Toz on 2011-08-18
At a basic level, you can have your script create a lock file of sorts and test for its existence at the beginning of the script. If the lock file exists, then wait. Otherwise proceed. And in the main block of your bash script, first thing you do is create the lock file, run your code, then delete the lock file. Something like this:
```
#!/bin/bash

while [ -f .lock ]; do
	sleep 2
done

touch .lock
echo "doing important stuff"
sleep 10
rm .lock

```

---

### Post by meridionaljet on 2011-08-18
> **Toz said:**
> At a basic level, you can have your script create a lock file of sorts and test for its existence at the beginning of the script. If the lock file exists, then wait. Otherwise proceed. And in the main block of your bash script, first thing you do is create the lock file, run your code, then delete the lock file. Something like this:
```
#!/bin/bash

while [ -f .lock ]; do
	sleep 2
done

touch .lock
echo "doing important stuff"
sleep 10
rm .lock

```

Ok, but then theoretically there is still a small piece of time between checking for the lock file and creating it, during which a 2nd instance of the script could create a lock, because the file doesn't yet exist, thereby resulting in two instances of the script, both thinking that they are locked.

I read that using "mkdir" could be more effective, as that command will return an error if the directory already exists. This combines the checking and the locking into one step, instead of two. 

Here's what I would think it would look like:

```
#!/bin/bash

if mkdir .lock; then
  echo "Lock successful"
else 
  echo "Lock failed"
  while [ -d .lock ] 
  do 
    sleep 1s
  done
  mkdir .lock
fi

echo "run commands here"

rmdir .lock

exit 0

```

Does this sound like it would work?

---

### Post by papibe on 2011-08-18
Sort of, yes. The main logic is the typical trick most people use to avoid a [race condition]("http://mywiki.wooledge.org/RaceCondition"). There is a weak spot though: if for any reason some of the code represented by "run commands here" fails, you'll end up with all instances locked (because you couldn't get to rmdir).

You can use the bash built in command '[trap]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html")', to ensure that if by any reason the code is interrupted you can redirect the execution to a grace exit. For example:
```
trap "rmdir .lock; exit" INT TERM EXIT
```
For more examples read the section 'Race Conditions' in [this]("http://www.davidpashley.com/articles/writing-robust-shell-scripts.html") tutorial.

Now, AFAIK the strongest parallelization tool available for bash scripts is '[flock]("http://www.unix.com/man-page/Linux/1/flock/")'. The standard atomic structure is something like this (from flock's man):
```
(
    flock -s 200
    # ... commands executed under lock ...
) 200>/var/lock/mylockfile
```

Here's a better [example]("http://stackoverflow.com/questions/169964/how-to-prevent-a-script-from-running-simultaneously"), and here a deeper [tutorial]("http://coldattic.info/shvedsky/pro/blogs/a-foo-walks-into-a-bar/posts/16").

Regards.

---

### Post by egpetrich on 2011-08-19
You should have a command available that takes care of this type of locking for you. It's called "setlock". I wrap it around "getmail" to ensure that I can run "getmail" as a cron job and also call it from the command line.

Here's my code:

```
#!/bin/sh
# $Id: getmail_safe.sh,v 1.2 2010/11/06 00:06:55 epetrich Exp $
#
# Purpose: Wrap "getmail" inside "setlock" to ensure that it runs only
#   one instance at a time.

date
/usr/bin/setlock -n ~/etc/getmail_lock /usr/bin/getmail $@
```

---

### Post by ian dobson on 2011-08-20
Hi,

Or maybe pipe the output of ps -A | script name to a variable and see if the variable is empty.

Creating a file might be a bad idea, if the script dies before it deletes the file......

Regards
Ian Dobson

---

