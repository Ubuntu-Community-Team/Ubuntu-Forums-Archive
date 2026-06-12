---
title: "Similarities between AIX and Ubuntu ?"
date: 2012-03-20
forum: The Cafe
---

### Post by rk0r on 2012-03-20
Hi 

Are there any similarities between AIX and Ubuntu ?

---

### Post by spynappels on 2012-03-20
Other than the UNIX bedrock? the filesystem(s)? the shells?

Can you be more specific in what you are looking for because this sounds a little like a homework question.....

---

### Post by rk0r on 2012-03-20
Sorry, i mean similarities within bash and the file structures... are the commands used in both AIX and Ubuntu similar ?

---

### Post by spynappels on 2012-03-20
Well, a Bash shell on Ubuntu is pretty much the same as a Bash shell on AIX, and an ext3 filesystem on Ubuntu is pretty much the same as an ext3 filesystem on AIX. 
The differences are in the kernels, and different tools will be available on each so that you may not be able to use IPtables on AIX or Solaris or BSD or .... and you won't be able to use sar or dtrace on Ubuntu but you can on Solaris (another UNIX system).

---

### Post by Skara Brae on 2012-03-20
At work, we use a (mainly database) program that runs on an IBM server with AIX 4.3 in an "Xnest"-window in SLED 10 :-)

The IBM server was until recently a RS6000 (extremely antique, but I don't recall it ever breaking down, except for the internal tapedrive that was used for daily backups. DDS-tapes? Gee.).

AIX has CDE as desktop environment. I barely see more of AIX than the program that we use, though (meaning I cannot answer the OP's question).

Knowing a bit of Linux (Ubuntu) does make AIX look less "alien" to me, and now and then I can brag of how much I know about AIX (which is practically nothing :p ).

Many, many, many years ago, AIX 4.3 ran in a terminal on our desks. These were later replaced with PC's running Windows 2000 (3+ minutes for W2K to boot, in the end).
In 2008 these PIII-1GHz machines were replaced with Dual-core Pentiums  with SLED 10 w/ KDE 3.5.
Last rumour had it SLED will be replaced by Windows 7 (I suspect Microsoft "lobbying" behind that decision, considering the incredulous reason for the switch I was given).

---

