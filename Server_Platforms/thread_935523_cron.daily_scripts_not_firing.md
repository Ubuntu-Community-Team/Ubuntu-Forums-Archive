---
title: "cron.daily scripts not firing"
date: 2008-10-01
forum: Server Platforms
---

### Post by coder_cotton on 2008-10-01
Hey all,

I have several scripts in cron.daily (none have periods), but only the first script, alphabetically, fires.  None of the others are.

Is it *required* to prepend the numbers for the cron.daily scripts?

FYI, they are all rdiff-backup scripts, which I can run manually concurrently with no issue.

Any advise appreciated.

Regards,
Cotton

---

### Post by lykwydchykyn on 2008-10-01
It's not required in my experience; I never prepend numbers to my cron.daily scripts, and they are all running.  Do you have a way to check that the first task completed?  Typically they are done sequentially, if I'm not mistaken.

---

### Post by windependence on 2008-10-02
Can you post your cron.daily so we can take a peek?

-Tim

---

### Post by whitegourd on 2008-10-02
If one of the scripts work in the cron.daily, then the problem may be somewhere w/in the scripts ...?

I ran into a similar situation where one of my scripts wouldn't run when scheduled in the cron.  When running it manually, it would work w/o any problems.  It took me a little while to figure it out, but the problem was due to some of the "echo" commands I had programmed into the script that spits the output the terminal session.  This would stop the script from running in the cron.  After making some adjustments in the script, it ran just fine the following days (both manually and in the cron).

---

### Post by Krupski on 2008-10-02
> **coder_cotton said:**
> Hey all,

I have several scripts in cron.daily (none have periods), but only the first script, alphabetically, fires.  None of the others are.

Is it *required* to prepend the numbers for the cron.daily scripts?

FYI, they are all rdiff-backup scripts, which I can run manually concurrently with no issue.

Any advise appreciated.

Regards,
Cotton

Scripts in "cron.anything" need two things to work:

(1) The FIRST line of the script must be "#!/bin/sh"
(2) Executable permissions (chmod 0755) must be set.

Scripts DO NOT need prefix numbers, and their filename is irrelevant. Dashes, numbers, etc... do not matter.

---

### Post by Krupski on 2008-10-02
> **lykwydchykyn said:**
> Typically they are done sequentially, if I'm not mistaken.

"run-parts" executes scripts in lexical order.

That is, it executes scripts in ascending order of the ascii value of the letters that make up the script name.


In other words, in this order:

0
..
..
9
..
..
A
B
..
Y
Z
..
..
a
b
..
..
z

So, "script" would run after "SCRIPT"

0-script would run before 9-script

etc...

---

### Post by pytrisss on 2008-10-02
I think too that the problem is somewhere within the scripts itself. Try to have your first working script twice in crontab and look if it was done twice too. If yes, the problem is in the scripts.
I had a similar problem, I did have a lock file created in my script but I forgot to delete it after I killed the script hard :)

---

### Post by coder_cotton on 2008-10-02
I'm trying to direct the output to a log file and see if that fixes the problem.  I'll report back either way.  Thanks for the ideas.

Regards,
Cotton

---

### Post by windependence on 2008-10-03
If we could see the scripts we may be able to help you better.

-Tim

---

### Post by coder_cotton on 2008-10-03
Seems the command output was stopping the scripts.  Piping output to a log fixed the issue.  Thanks again!

---

