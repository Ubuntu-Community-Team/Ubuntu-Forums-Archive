---
title: "Tron Legacy, What commands were used?"
date: 2011-01-04
forum: The Cafe
---

### Post by Mercenary(FH) on 2011-01-04
So Im sure most of us have HOPEFULLY seen Tron Legacy, great movie. But anyways im sure this has been brought up, but I could've SWORN i saw Ubuntu appear in the terminal they were using at the encom meeting.

Anyways I know about Sam using the "top" command but I wonder what commands cillian murphy was putting in to stop the "barking dog" video. (im not really spoiling anything if u havent seen it)

I saw "Kill" and maybe a grep......but lets think realistically what he would've done to stop an application from running like that? Any ideas?

maybe some combination of grep to find the process id's (maybe newest process) then kill to get rid of it?

---

### Post by ssam on 2011-01-04
i think he stopped the video with a
```
kill -9 ####
```
didn't catch what command he got the PID with, but it would probably be pgrep.

also when sam runs 'history' on his dads computer there were a bunch of 'make' and 'make install'.

there is a screen shot, [http://www.omgubuntu.co.uk/2010/09/linux-top-command-used-in-tron-trailer/](http://www.omgubuntu.co.uk/2010/09/linux-top-command-used-in-tron-trailer/)

---

### Post by Mercenary(FH) on 2011-01-04
What does kill -9 #### do?

---

### Post by Grenage on 2011-01-04
I room to recall *whoami*, just before I fell asleep. ;)

---

### Post by ssam on 2011-01-04
> **Mercenary(FH) said:**
> What does kill -9 #### do?

```
kill 123
```
sends a TERM (terminate) signal to process 123. A program ought to stop when it receives this.

```
kill -9 123
```
sends a KILL, which a program cannot block.

there was a whoami, when he's at his dads terminal. then he try to log in as root, and fails, then he logs in with the username 'backdoor'

---

### Post by Mercenary(FH) on 2011-01-04
Kinda random they'd use a number (like -9) to make it where it cannot block...

---

### Post by Grenage on 2011-01-04
> **Mercenary(FH) said:**
> Kinda random they'd use a number (like -9) to make it where it cannot block...

There are multiple levels of kill...

Also, you don't actually have to kill something with *kill* - it can be used for other purposes.

---

### Post by spupy on 2011-01-04
The computer at the arcade's basement was not only running TOP in a console, but one of the top running processes was an X server.

But as someone pointed out at omgubuntu, it most probably wasn't linux, since linux didn't exist at the time of the first movie. The windows' titles refer to some other OS, the name of which I forgot.

---

### Post by Primefalcon on 2011-01-16
how about just a ```
killall -9 barkingdog
``` lol

---

### Post by jrdjrd on 2011-05-09
> **spupy said:**
> The computer at the arcade's basement was not only running TOP in a console, but one of the top running processes was an X server.

But as someone pointed out at omgubuntu, it most probably wasn't linux, since linux didn't exist at the time of the first movie. The windows' titles refer to some other OS, the name of which I forgot.

It was SolarOS according to the the uname command...

---

### Post by Jamessharpshooter on 2011-05-31
You want a clear view of the commands used?
[http://work.gmunk.com/#1190825/TRON-Board-Room]("http://work.gmunk.com/#1190825/TRON-Board-Room")

Your welcome. :)

---

