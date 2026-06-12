---
title: "Interfacing with a Running Daemon"
date: 2011-10-30
forum: Server Platforms
---

### Post by awells527 on 2011-10-30
I have sort of a general question regarding interfacing with a program console when running outside the terminal session.

For example, when running a Ventrilo or Bukkit server, you see the output in a shell session, and you can type commands to interface with the application.  What I want to do is set it up as a daemon / service so I can start & stop it with upstart and not have to keep a terminal session running.

What is the best way to interface with the daemon when it's running in this way?

---

### Post by craigp84 on 2011-10-30
I'm not familiar with those programs, however the easiest way to give stdin to a background process is using a fifo for the input. Output would just go to a log file.

Try this out:

```

mkfifo daemon_input
( cat - < daemon_input > daemon_logfile ) &

```

So cat - (which sends to stdout whatever comes in from stdin) has it's output redirected to a file, and it's input coming from a fifo. I've put it in a subshell () and backgrounded it & so that we can use the shell to test the idea.

```
echo command_string > daemon_input
```

Now you can cat daemon_logfile and see whatever was echo'd (the service process in this case is just cat'ing everything straight back out again).

Hope this helps

---

### Post by awells527 on 2011-11-01
Thanks - that is helpful!

It looks like I will have to learn how mkfifo works.

The example runs cat once and exists.  What I will need to do is have the command wait for input as needed and not hang waiting.  I know where to look now.  It was difficult to search for the answer because I didn't know what I wanted. 8)

---

