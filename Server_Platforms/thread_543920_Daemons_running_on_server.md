---
title: "Daemons running on server?"
date: 2007-09-05
forum: Server Platforms
---

### Post by msund on 2007-09-05
Ive just recently seen my vsftpd popping up when its supposed to
be shut down.

Is there any script or program who gives a nice list of running daemons on the system?

it would be nice if a daemon crashes to just look in that list to quickly see if there is a "user" error or server error.

thanks in advance!

---

### Post by p_quarles on 2007-09-05
To get a list of running processes, you can simply use the command:
```
ps -aux
```
That won't list just daemons, but it will list all of them. 

To find errors and crash reports, you can look at the appropriate log files in the /var/log directory.

---

### Post by msund on 2007-09-05
ah nice one, thanks p_quarles.

But i was kinda looking for a program that tracks daemons, and only deamons.
It gets kinda fuzzy to find the ones youve wanted to check out with a "ps".

Guess ill have to keep looking :)

---

### Post by Mr. C. on 2007-09-06
A "daemon" is a generic concept, and not a specific entity that has meaning to the linux/unix kernel.  The kernel manages processes.  Any of the standard process listing commands (top, ps, etc.) are used to identify running processes.

The system doesn't magically run programs on its own.  Only programs that are configured to run will be run.

The correct approach is to configure what you need, and remove what you don't.  It is best to learn to at least identify the processes that are running or will run, and which system services are installed and configured.

MrC

---

### Post by msund on 2007-09-06
Well yeah i know the concept of deamons.

But with a ps or a top the "processes" are categorized as process or daemon, so a program that maybe ar written to only show process labeled daemons and maybe keep updating their status instead of just spitting them out on the screen would be what i was looking for.

I was just wondering if anyone used such a program, i didnt want a lesson in linux fundamentals.

But thats usually the response if people dont got a straight awnser.

---

### Post by HermanAB on 2007-09-06
Hmm, mostly I just use:
ps -e|grep whatever

Vsftpd (and sshd) running on the standard port will be subjected to periodic brute force password attacks.  This may be what you are seeing.

This is why it is of extreme importance to use loooooong random passwords of 9 characters or more.  I use 16 character semi-pronounceable passwords, do not run FTP and run SSH on a non-standard port and my servers have never been broken into.

Cheers,

H.

---

### Post by Mr. C. on 2007-09-06
> **msund said:**
> ...
But with a ps or a top the "processes" are categorized as process or daemon...

Where do you see this?

MrC

---

