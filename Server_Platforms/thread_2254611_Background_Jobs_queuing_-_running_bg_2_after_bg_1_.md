---
title: "Background Jobs queuing - running bg 2 after bg 1 completes"
date: 2014-11-28
forum: Server Platforms
---

### Post by ravi9 on 2014-11-28
Hello,
I have a question regarding queuing up jobs. I currently have two jobs that are stopped. I would like to restart them in such a way that job 2 launches immediately after job 1 is completed.
I thought about doing
# bg 1; bg 2
but all that does is run both jobs in parallel. 

Is there some way that I can instruct the system to only run bg 2 once bg 1 is completed?

Thanks

---

### Post by nerdtron on 2014-11-28
What are you running jobs? Maybe we can try a different approach.

Example of queuing commands using &&:
```
sleep 10 && echo Done 
```

That sleep command should be completed first (and should be successful) only then the echo command will be trigger.

---

### Post by ravi9 on 2014-11-28
problem is that both jobs are currently stopped. 
if I type in bg 1 && bg 2 then bg 1 runs job 1 in background and successfully exits. While job 1 is now running in background, job 2 is started immediately by the commadn bg 2 even though job 1 isn't completed yet.

I do not know how long job 1 will take to finish, it could take anywhere from several hours to a day or two for it to finish.

Initially I had started both jobs by doing
# command1; command2

some of the output of command1 is used by command2 so i need to make sure that 1 is completed before I can run 2.
Instead of simply opening up a new terminal, pushed the foreground job into bg with ctrl+z and that started command2 so i pushed that to bg also.

Now i don't know how to queue them up again. 

It's not that big a deal, i'm not under time pressure. I can keep checking back every few hours to see if command1 is complete and then manually launch command2 but i'm just trying to save some time if command1 happens to complete in the middle of the night.

---

### Post by nerdtron on 2014-11-28
> While job 1 is now running in background, job 2 is started immediately  by the commadn bg 2 even though job 1 isn't completed yet.

What are your commands/jobs that you are running? Don't use "bg 1 && bg 2".
Start initially with the original commands that you are using like "/run/script1.sh && /run/script2.sh". This will only run scipt2.sh if script1.sh is completed.

But if the 2 commands are already stopped using bg. I don't of other ways since you already started them without the &&.

---

### Post by ravi9 on 2014-11-28
Yeah, I was afraid of that. The first script I started already ran for like 7-8 hours. I'd end up losing that time if I executed it again with &&
Guess I'm going to lose time either way now lol

No worries. At least now I know what to do next time. 
Thank you for your help.

---

