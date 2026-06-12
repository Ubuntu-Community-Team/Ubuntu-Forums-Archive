---
title: "Cancel avgupdate process"
date: 2009-03-18
forum: Security
---

### Post by Ashin Sopaka on 2009-03-18
While running avgupdate (sudo avgupdate --online) from the terminal window, we had a power outage (situation normal) and the computer shut down (yes, yes, have UPS, but battery died on the laptop and wireless router is in another room). When the power came back (miracle of miracles), I tried to run avgupdate again, but a message appears that the process is already running. Then ran [$ ps -e] but cannot find this process at all (another name maybe?). Tried [$ kill avgupdate], but the argument needs a JOB or process ID. 

Oh yes,shutting down the computer overnight did nothing either, avgupdate is still running (couldn't find anything in AVG website FAQ)

Any suggestions? Thanks in advance

---

### Post by cariboo on 2009-03-19
Try:

```
ps ax | grep avg
```

To see if can track down the running process.

Jim

---

### Post by Ashin Sopaka on 2009-03-19
That code returned:

 8115 pts/0    S+     0:00 grep avg

and when I tried to kill 8115, 

bash: kill: (8115) - No such process

...and it's still "running" :(

---

### Post by Ashin Sopaka on 2009-03-21
So yesterday while waiting for a file to save, I ran Jim's code several times in a row, and the first number (8115) kept changing. 

Originally wanted to stop the process and start anew. Now just want to get rid of the whole program, but can't do so without stopping the process first. 

Suggestions?

---

### Post by cariboo on 2009-03-22
The result you are getting is just your search, so you can't really kill it. I don't use an antivirus on Linux, as **I** feel it isn't needed.

If you still have your avg source directory, there should be uninstall directions in that directory.

edit: You might want to have a look at [this]("http://answers.launchpad.net/ubuntu/+question/4392"), it might help you get rid of avg

Jim

---

### Post by Ashin Sopaka on 2009-03-22
Hi Jim, we do a lot of passing around of files here and with them, the accompanying viruses. Although this machine is "immune", I was afraid I was still passing on the bugs, so did a virus scan and found one! Then the problem with the update. 

Long story short, thanks for your help - AVG is history. Replaced it with ClamAV, for better or for worse :)

---

