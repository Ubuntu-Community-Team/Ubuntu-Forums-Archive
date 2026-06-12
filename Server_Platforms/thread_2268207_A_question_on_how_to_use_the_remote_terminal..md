---
title: "A question on how to use the remote terminal."
date: 2015-03-06
forum: Server Platforms
---

### Post by schroeder25932 on 2015-03-06
Okay, I recently decided to rent a dedicated server. I've managed to successfully install Ubuntu Server 14.04 LTS and connect to it remotely via SSH. My problem lies with the terminal; every time I close the terminal on my desktop, the server program on the remote server shuts down as well. Is there anyway I could get the server program to continue running after I close the terminal on my end? If so, would I be able go back to check on it and if necessary, run commands from the program's console?

---

### Post by MAFoElffen on 2015-03-07
That is because it sounds as if you are runnign your program in the foreground, so when you disconnect your session, since the session ends, so does your program.

Offhand I know at least 4 ways to do what you want to do. Lets say the process you want to start is myProgram...
```

myProgram & 

```
^which is the basic run this program in the background...
```

$ myprogram   #start program
                     # then press <cntrl><alt><z> to suspend the program
                     # Its going to stop and show what pid it was using
$ Stopped  1033 # <-- the message displayed
$ disown -h %1033 # this leaves in table, but marks so that SIGHUP is not sent to the job if the shell receives a SIGHUP
$ bg 1033  # restarts the job as a background process

```
^The to-the-book-kind of sys admin way

```

nohup myProgram   # run a command immune to hangups, with output to a non-tty

```
^another way

The most elegant way is to use Gnome Screen, which is a screen manager with VT100/ANSI terminal emulation. 
```

screen  # start a screen session
myProgram  # start your program
# press <cntrl><a><d> to detach from that session
# when you log back in, you can re-connect to that session via
screen -r

```

---

### Post by schroeder25932 on 2015-03-07
I used your forth option. I was trying that earlier, just couldn't quite get it to work. Tried it exactly as you specified, and it works flawlessly.
Thanks

---

### Post by MAFoElffen on 2015-03-08
You are welcome. Remember to revist this thread, use the Thread Tools link in the upper right of the page to mark this thread as solved.

---

