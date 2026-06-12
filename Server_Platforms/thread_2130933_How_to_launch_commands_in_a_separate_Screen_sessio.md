---
title: "How to launch commands in a separate Screen session via a bash script at startup?"
date: 2013-03-31
forum: Server Platforms
---

### Post by TheGuyWithTheFace on 2013-03-31
To start the server applications I'm running takes several steps, so I've decided to put it in a bash script to make it easier. When I do start it, I begin by opening a new screen session. The issue is, in my script, I've noticed that none of the other commands execute until the new Screen session is closed. Any Ideas?

---

### Post by spynappels on 2013-04-02
I think I can explain why it is happening, but I'm not sure how to work around it...

A Bash script is a sequential list of commands, executed one after the other (very oversimplified, but go with it). What is happening is that the screen session is opened and a new Bash shell is launched inside it. However, the original Bash script is still running on the parent shell,  and is waiting for the previous command to finish before executing the rest of the commands in the script. While the screen session and it's child Bash shell is active, the original script will not carry on.

I'm not sure how you'd get around it, my first idea of starting the screen session backgrounded and then reconnecting to it using screen -r did not work when I tested it, I'll do some more Googling to see if there is a way to make this work.

---

### Post by vanadium on 2013-04-02
This may help: [http://ubuntuforums.org/showthread.php?t=1545643](http://ubuntuforums.org/showthread.php?t=1545643)
I guess you want the commands to run in the screen session you open. For such a case, the thread suggest
```

screen -dm -t title1 bash -c 'command1 ; command2 ; command3'

```
You could replace the part after -c with the name of a script instead of a series of commands.

---

### Post by LHammonds on 2013-04-02
Or just schedule them separately.

Or issue the screen command with the nohup (no hangup) and & (run in background) command.

I call screen sessions directly from crontab rather than running a script to start the screen.

LHammonds

---

