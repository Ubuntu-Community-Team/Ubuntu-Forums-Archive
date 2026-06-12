---
title: "terminal closes"
date: 2010-09-22
forum: Security
---

### Post by corncob on 2010-09-22
I made a launcher -Type:"Application in Terminal", Command: "sudo rkhunter --check".  The terminal opens and it runs but the terminal closes immediately when it is done.  How do I get the terminal to stay open so we can look the data over like it does if I type the command directly into the treminal?  I know I can go to /var/log/rkhunter.log but the thing is I'm teaching a class on Ubuntu and want it to appear simple to use.

---

### Post by CharlesA on 2010-09-22
It's just like running a command-line tool from the run dialog box in Windows - it runs the command and closes it.

Run it like so:

Applications > Accessories > Terminal

Run chkrootkit.

Done.

---

### Post by corncob on 2010-09-22
Thanks, that's what I do myself but I was trying to find a graphical front end for rkhunter so I wouldn't be snowing the students (they're just members of the local computer club) with too much command line and digging into the file system maze.  I was hoping to find a way to keep the process going so that the terminal wouldn't close (something like elinks does).

---

### Post by CharlesA on 2010-09-22
I don't think there is a GUI version of rkhunter.

Also be careful of false positives with that tool. :)

Sidenote: Some of the best tools/utilites are CLI only.

---

### Post by bodhi.zazen on 2010-09-22
> **corncob said:**
> I was trying to find a graphical front end for rkhunter so I wouldn't be snowing the students (they're just members of the local computer club) with too much command line

IMHO , hiding the command line is a mistake.

When I teach Linux I try to include examples of how to solve problems BOTH with the graphical tools AND the command line.

Separating the CLI into a abstract interface, removed from daily tasks, makes it harder to learn. Integrate it into the daily routine.

---

