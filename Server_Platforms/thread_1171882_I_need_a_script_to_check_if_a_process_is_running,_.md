---
title: "I need a script to check if a process is running, and if so, do one thing, else do..."
date: 2009-05-27
forum: Server Platforms
---

### Post by Underpants on 2009-05-27
I have a script on a server that needs to be executed every day. Some days the script takes longer than 24 hours to complete. Obviously, I don't want the script to run if the one that was spawned the day before is still going at it.


So, in pseudo code this is what I want....

if dailycopy.sh is running; then run send-email-that-says-job-is-still-running.sh else run dailycopy.sh

---

### Post by Tibuda on 2009-05-27
```
#!/bin/sh
if [ `pgrep dailycopy.sh` ]; then
  ./send-email-that-says-job-is-still-running.sh
else
  ./dailycopy.sh
fi
```

---

### Post by Underpants on 2009-05-27
pgrep! That's a handy trick! thanks!!!

---

### Post by lswb on 2009-05-27
The pgrep command can identify running processes by name, see man pgrep for the different options. You could also use a lock or flag file of some kind, i.e. something like

```


#!/bin/sh
if [ -e MyScriptIsRunning ]; exit;
else touch MyScriptIsRunning
fi

# Main body of your script here....

rm MyScriptIsRunning

```

With the 2nd approach you have to consider if the script can fail or exit before the file is deleted at the end, or what happens if there is a system crash while the script is running.

---

### Post by Underpants on 2009-05-27
I just set it up using the first prep method. that's a super slick utility. thanks for the help!

---

### Post by Underpants on 2009-05-27
Problem. This isn't working.

veeam-copy.sh is NOT running but "/home/gwik/email-veeam-is-still-running.sh" launches and then it exits. 



```

#!/bin/sh

if [ 'pgrep veeam-copy.sh' ]; then
 /home/gwik/email-veeam-is-still-running.sh
else
 /home/gwik/veeam-copy.sh
fi
```

---

### Post by Underpants on 2009-05-27
There are some rsync commands in the veeam-copy.sh script. I'm not able to pin down a process that pgrep can use. I can't use "rsync" because I have other scripts running at the same time which would interfere with what I'm trying to do here.


What can I do?

---

### Post by lswb on 2009-05-30
> **Underpants said:**
> Problem. This isn't working.

veeam-copy.sh is NOT running but "/home/gwik/email-veeam-is-still-running.sh" launches and then it exits. 



```

#!/bin/sh

if [ 'pgrep veeam-copy.sh' ]; then
 /home/gwik/email-veeam-is-still-running.sh
else
 /home/gwik/veeam-copy.sh
fi
```

With the single quotes you have used inside the brackets, the pgrep... line is just being treated as a string, not a command. So the if test will always be true, since the bracketed expression is a non-empty string. You may have meant to use backquote characters ( ` ) which would work OK as when they are used around a command they return the standard output of the backquoted command. Using the form $(command) is equivalent to the older `command` style and has some advantages in use.

There are a few different forms that will work, probably the simplest is just

if pgrep veeam-copy.sh ; then

When pgrep finds a process that matches its argument, it exits with 0 which an if test regards as "true" when returned from a command. If pgrep does not find a matching process or there is some kind of error, it exits with a non-zero return value which an if test will evaluate as false when returned from a command.

---

### Post by Underpants on 2009-05-30
You're right about the single quote thing. That's just my bad copying the example the first responder made for me onto another machine. 

Now onto the next problem: 

Like I said, the "veeam-copy.sh" script contains an rsync command, and some email commands to send me a log file. 

I can look at the system right now (the script is running) and ps -ax doesn't show veeam-copy.sh as a running process, but the rsync command DOES show as a running process, making it difficult (or impossible) to use the if/then thing I just fixed :) 


Thoughts?

---

### Post by Underpants on 2009-05-30
> **Underpants said:**
> You're right about the single quote thing. That's just my bad copying the example the first responder made for me onto another machine. 

Now onto the next problem: 

Like I said, the "veeam-copy.sh" script contains an rsync command, and some email commands to send me a log file. 

I can look at the system right now (the script is running) and ps -ax doesn't show veeam-copy.sh as a running process, but the rsync command DOES show as a running process, making it difficult (or impossible) to use the if/then thing I just fixed :) 


Thoughts?

OK. This is what shows in ps. ```
sh ./veeam-copy.sh
```

how can I use pgrep with that?

---

### Post by lswb on 2009-05-30
> **Underpants said:**
> OK. This is what shows in ps. ```
sh ./veeam-copy.sh
```

how can I use pgrep with that?

Here's 2 ways:

1) put "#!/bin/sh" as the first line of your script, then 
chmod +x veeam-copy.sh 
to make the script executable without having to call it with sh. After that you can just run the script itself, as ./veeam-copy, or if it is on your path, without the ./ . Then you can just use pgrep to search for the veeam-copy process with
pgrep veeam-copy

2) use the -f option to pgrep, which will find a match on the full command line, not just the process name, so you could use the line
pgrep -f "veeam-copy" and it would find "sh ./veeam-copy.sh"

---

### Post by Underpants on 2009-05-30
You're my hero! I think I just learned the significance of the "#!/bin/sh" part.... woot

---

### Post by lswb on 2009-05-30
If you are interested in scripting IMHO the best online or downloadble guide is the Advanced Bash Scripting Guide by Mendel Cooper, available here:

[http://tldp.org/guides.html](http://tldp.org/guides.html)

---

