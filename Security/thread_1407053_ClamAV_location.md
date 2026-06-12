---
title: "ClamAV location?"
date: 2010-02-14
forum: Security
---

### Post by BSG Fan on 2010-02-14
hello
I just downloaded with a terminal the program ClamAV.

But where it is located?
I don't see it in Application - accessories -etc ?
neither in "Places", etc

where it is?

:popcorn:

ps: the place where I found about this was here:
[http://120linux.com/antivirus-para-ubuntu/](http://120linux.com/antivirus-para-ubuntu/)

---

### Post by gordintoronto on 2010-02-14
Downloaded how?  I find that Synaptic is the best bet, it put ClamAV in Administration, Virus Scanner

---

### Post by donato roque on 2010-02-14
Clamav is a command line application.
Open a terminal by typing:

(1) alt+F2
(2) gnome-terminal

To start clamav to scan a file/directory, type:

  clamscan

To use clamav to scan a directory recursively, type:

  clamscan -r

The -r option tells clamav to scan all files and directories within 
the specified target directory.

Personally, I use clamav to scan my whole /home/user using this command:

  ~$ clamav -ril /home/user/clamav.log

This command tells clamav to scan my home directory recursively and output the results to a log file in the user directory.
The -i option tells clamav to only report infections. I want the short story only.

---

### Post by BSG Fan on 2010-02-15
> **gordintoronto said:**
> Downloaded how?  I find that Synaptic is the best bet, it put ClamAV in Administration, Virus Scanner

Thanks for your help

---

### Post by BSG Fan on 2010-02-15
> **donato roque said:**
> Clamav is a command line application.
Open a terminal by typing:

(1) alt+F2
(2) gnome-terminal

To start clamav to scan a file/directory, type:

  clamscan

To use clamav to scan a directory recursively, type:

  clamscan -r

The -r option tells clamav to scan all files and directories within 
the specified target directory.

Personally, I use clamav to scan my whole /home/user using this command:

  ~$ clamav -ril /home/user/clamav.log

This command tells clamav to scan my home directory recursively and output the results to a log file in the user directory.
The -i option tells clamav to only report infections. I want the short story only.

Thanks for help me.
=)

===
thread solved

but I don't know how to put "SOLVED" here...., I mean for the title
==
I did it.
Solved!
=)

---

### Post by Atomic-Fanboy on 2012-11-07
```
clamav -ril /home/user/clamav.log
```

Should be:

```
clamscan -ril /home/user/clamav.log
```

---

### Post by Bucky Ball on 2012-11-07
[I][B]Thread closed.

Reason: [/B][/I]Necromancy. This is over two years old.

---

