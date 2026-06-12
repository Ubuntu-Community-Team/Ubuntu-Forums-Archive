---
title: "Prevent user from running program without using TORQUE"
date: 2012-06-26
forum: Server Platforms
---

### Post by bacalfa on 2012-06-26
Hello, guys!

I was wondering if this is possible to do. I'm a Ubuntu server (12.04) admin and I'd like to make sure that certain programs (computational ones) are only run if the queue system is invoked, i.e. the user cannot run the program "directly" from the Terminal.

Thank you!


Bruno

---

### Post by SeijiSensei on 2012-06-27
I don't know what a "queue system" is, though I can guess.  Isn't the easiest solution to this to take the programs out of the standard paths like /usr/bin and stash them in other directories visible only via the queue system?

---

### Post by bacalfa on 2012-06-27
Thanks for your reply, SeijiSensei.

Mmmm... by queue system I meant this: [https://help.ubuntu.com/community/TorquePbsHowto](https://help.ubuntu.com/community/TorquePbsHowto).

So the idea is: the user queues jobs with the command 'qsub' and the job is usually defined in a script file in which some program is called. Let me try to give you an example:

```

// File script.sh
#!/bin/sh

myprogram options

```

```

qsub script.sh

```

That's how I want the program 'myprogram' to be called. A user cannot call 'myprogram options' directly in the Terminal. It has to be done through the command 'qsub'.

How do I enforce that? Given your idea, how would I make sure that the program can only be "seen" by TORQUE?

Thanks!

Bruno
[]("https://help.ubuntu.com/community/TorquePbsHowto")

---

### Post by SeijiSensei on 2012-06-27
If they can run a script through TORQUE that works equally well from the command prompt, I don't see how you can enforce this except in one case I'll describe in a moment.

You could remove the appropriate entries from the user's PATH, but any savvy person can avoid that by restoring the correct path or using full paths like /usr/bin/program.  Plus if their scripts are run with their own usernames, then the scripts would be equally crippled and unable to run the program requested.  However this gives rise to a possible solution....

What user owns the programs run via the queue system?  Are they run with the queue system's permissions?  If so, you could try changing permissions in /usr/bin, so that all programs are owned by root with group "torque" and turning off the world execute bit on all the programs there (chmod ug+x,o-x /usr/bin/*).  Then only root and members of the torque group can run those programs.

---

### Post by bacalfa on 2012-06-27
I don't know if I follow your suggestion. I want to forbid all users to run certain programs directly from the command line. It has to be done via the submission of a job. The two only entities that could run those programs are 'root' (directly) and any user through the command 'qsub' as I exemplified before.

Is it possible to enforce something like that? If I create a group, say 'torque', can I add root and the program 'qsub' to it and set the permissions accordingly? I don't know if that can be done.

Thanks!


Bruno

---

### Post by SeijiSensei on 2012-06-28
Suppose I log in as user seiji and schedule a job.  When the job is run, is it executed under my username and using my privileges, or is the job run under the username of scheduling system?  If the latter, it might be possible to do what you want.  If all the jobs are run with the scheduling user's privileges, then I don't see how your desire can be fulfilled.

---

### Post by bacalfa on 2012-06-28
I checked with 'top' that the USER that is running one of the programs now is me. Is that what you meant by who runs the jobs?

---

### Post by SeijiSensei on 2012-06-28
Yes.  One method the system could have used is to run all the projects under a username belonging to the system, much the same way most daemon processes run as unprivileged users.  (The Apache web server runs as user "www-data," for instance.) 

So now that we've verified that the queued jobs are run with the identities of their submittors, I don't think there's much hope for an easy solution to your request.  In order to run their scripts, they have to be able to use the software you want to restrict.  

The only solution I see is a custom application written in a language like PHP or perl.  You would build a web-based interface that enables authorized users to submit jobs and get their results.  All the jobs would be run by the application itself, not by the individual users.  That eliminates the need for the users to have accounts on the server.  All their interactions with the system would be mediated through the web interface.

---

### Post by bacalfa on 2012-06-28
Thank you very much for your help! I really appreciate it.

---

