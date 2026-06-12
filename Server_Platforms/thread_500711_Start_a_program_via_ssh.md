---
title: "Start a program via ssh"
date: 2007-07-14
forum: Server Platforms
---

### Post by Notclive on 2007-07-14
How can I start a program via ssh so that when I close the ssh connection that program doesn't terminate?

---

### Post by bernied on 2007-07-14
there's an application called screen, that opens virtual terminals that you can open and detach, so you can reopen it from a different connection.
```
aptitude install screen
man screen
```
it's very easy to use

---

### Post by bernied on 2007-07-14
you can also run programs in the background by adding an ampersand ('&') at the end of the command line, but this is no good for interactive programs - not so easy to access it again.
Eg:
```
myprogram &
```

---

### Post by Notclive on 2007-07-14
> **bernied said:**
> you can also run programs in the background by adding an ampersand ('&') at the end of the command line, but this is no good for interactive programs - not so easy to access it again.
Eg:
```
myprogram &
```

This is the best for me, thanks a lot.

---

### Post by Notclive on 2007-07-14
the above doesn't work it still closes when the ssh connection closes so I used screen

---

### Post by Mr. C. on 2007-07-14
Unset the shell option **huponexit**, and your background jobs will not be terminated upon logout.  From the bash man page:

```
If the huponexit shell option has been set with  shopt,  bash  sends  a
SIGHUP to all jobs when an interactive login shell exits.
```

What is the output from:
```
shopt huponexit
```

MrC

---

### Post by MJN on 2007-07-16
Or apply it on a case-by-case basis using the **nohup** prefix e.g. **nohup <command> &**
 
The command process will then ignore the SIGHUP signal when you log out, and standard output will be written to the file nohup.out.
 
See **man nohup** for further details.
 
Again you can't interact with the process in the conventional sense so the suitability depends on what the process is you wish to run.
 
Mathew

---

