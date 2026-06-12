---
title: "trying to run high-priority multi-threaded processes in the background"
date: 2011-04-07
forum: Server Platforms
---

### Post by hopper333 on 2011-04-07
Hi all

Using Ubuntu server 10.04.2 64-bit all up to date.

I am running multi-threaded processes.  These use OpenMP in my own code and the multi-threaded ACML maths library.  When run in the foreground, everything is fine i.e. if I have set 

   export OMP_NUM_THREADS=8

then when I start all 8 cores are in use and things whizz along.  However, when running overnight and logged out using e.g. 'at now + 1 minute' then the command, I am only getting about 130% CPU and it slows down accordingly.  I have tried renice'ing and calling from within a bash script in case sh is doing something odd but nothing seems to solve it.  I am sure that in the recent past this wasn't the case.  Any ideas?

The libraries being used are shared versions in case that might have any bearing.

Thanks in advance.

Michael

---

### Post by gzarkadas on 2011-04-09
atd daemon does not by default run jobs when the load average is above 1.5.  I believe this causes the observed behaviour.

I haven't tried this myself (_warning_ :) ), but looks promising and does not hurt to try it.

You may try to tweak the following line in /etc/init/atd.conf (it is the last one in my Karmic system) and then issue a `sudo service atd restart' or reboot to acivate your changes:

[U]Original:
[/U]exec atd

_Modification:_
exec atd -l 8

The 8 comes from the number of your cores; it may be safe to set it even higher (say up to 12 ?). See the atd manpage (`man atd') for details and other options. You may also want to enter a smaller value for the batch interval (-b switch) in case your jobs finish sooner than this. But don't overdo it, else your jobs may drive the system to a crawl.

---

