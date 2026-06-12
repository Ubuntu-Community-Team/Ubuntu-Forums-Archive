---
title: "Bash interrupt to continue in background?"
date: 2017-12-01
forum: Ubuntu, Linux and OS Chat
---

### Post by nnnnnn2 on 2017-12-01
So CTRL+C stops the foreground program and CTRL+Z puts it in background, paused.

Is there one that simply puts it in the background without pausing it?

---

### Post by vasa1 on 2017-12-01
Take a look at [http://mywiki.wooledge.org/BashSheet](http://mywiki.wooledge.org/BashSheet). From there:
```

Jobs/Processes

    jobs: List the current shell's active jobs.

    bg: Send the previous job (or job denoted by the given argument) to run in the background.
        The shell continues to run while the job is running. The shell's input is handled by itself, not the job. 

    fg: Send the previous job (or job denoted by the given argument) to run in the foreground.
        The shell waits for the job to end and the job can receive the input from the shell. 

    kill: Send a signal(3) to a process or job.

        As argument, give the process ID of the process or the jobspec of the job you want to send the signal to. 

    trap: Handle a signal(3) sent to the current shell.

        The code that is in the first argument is executed whenever a signal is received denoted by any of the other arguments to trap. 

    suspend: Stops the execution of the current shell until it receives a SIGCONT signal.

        This is much like what happens when the shell receives a SIGSTOP signal. 

    wait: Stops the execution of the current shell until active jobs have finished.

        In arguments, you can specify which jobs (by jobspec) or processes (by PID) to wait for. 
```

---

### Post by nnnnnn2 on 2017-12-01
That Didn't answer my question. I already know about fg, bg, jobs, kill and other process related commands.

Thats actually why I'm asking, since doing CTRL+Z And then bg instead of simply adding an interrupt seems impractical.

---

### Post by nnnnnn2 on 2017-12-01
I didn't read Trap. Nice stuff. Derp XD

---

