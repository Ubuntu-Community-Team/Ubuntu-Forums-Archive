---
title: "Memory usage / program dies problem"
date: 2009-12-31
forum: Server Platforms
---

### Post by Krupski on 2009-12-31
(platform info: Intel Core 2 Quad, 8 GB memory, 8 GB swap, Ubuntu 9.10 Server 64 bit version)

Hi all,

I don't know if this is a server specific question, but I did run into the problem on 9.10 64 bit server, so here goes...

I've been running the "Folding@Home" distributed computing client on the server since most of the time the server would just be idle anyway.

It all works great... Folding@Home runs, I can at the same time watch a DVD backup from the server, etc... everything works great.

But today, I tried something... first I looked at my server's memory:

```

root@storage:/# free -kolt
             total       used       free     shared    buffers     cached
Mem:       8090704    8039284      51420          0    3631876    3739492
Low:       8090704    8039284      51420
High:            0          0          0
Swap:      8388600        312    8388288
Total:    16479304    8039596    8439708

```

Seeing that most physical ram was being used, I wanted to see if new ram usage would cause other memory to be swapped out, so I then did this (NOTE: in **/dev/shm**):

```

root@storage:/dev/shm# dd if=/dev/zero of=fill
dd: writing to `fill': No space left on device
8052345+0 records in
8052344+0 records out
4122800128 bytes (4.1 GB) copied, 8.7335 s, 472 MB/s

```

...then...

```

root@storage:/dev/shm# rm fill

```


The memory now looked more or less exactly what I EXPECTED to happen:


```

root@storage:/dev/shm# free -kolt
             total       used       free     shared    buffers     cached
Mem:       8090704    3636996    4453708          0    1962964    1457820
Low:       8090704    3636996    4453708
High:            0          0          0
Swap:      8388600        312    8388288
Total:    16479304    3637308   12841996

```


But here's the problem... the "Folding at Home" client died and was no longer running or in memory!

Since any program is just running "in memory" regardless of whether that memory is physical or swapped (and the memory is managed by the OS), why should a running process up and die like the "Folding" client did?

Here's how it looks when "Folding at Home" is running (part of output from 'ps -A'):

```

[COLOR="Red"]
 5923 ?        00:00:00 screen
 5924 pts/1    00:00:00 fah6
 5928 pts/1    00:00:00 sh
 5929 pts/1    00:00:00 mpiexec
 5930 pts/1    00:00:30 FahCore_a2.exe
 5931 pts/1    00:00:30 FahCore_a2.exe
 5932 pts/1    00:00:30 FahCore_a2.exe
 5933 pts/1    00:00:30 FahCore_a2.exe[/COLOR]
 5949 ?        00:00:00 sshd
 6001 pts/0    00:00:00 bash
 6015 pts/0    00:00:00 ps

```

Note that I am using "screen" to start the program "FAH6" which in turn runs "MPIEXEC" to load, run and intercommunicate data between 4 instances of "FAHCORE_A2.EXE" (i.e. one for each CPU core).

Strange thing is, I can be streaming a DVD backup to the TV and do the "DD->fill, RM fill" thing and the video doesn't hiccup one bit.

But, "Folding at Home" dies. :confused:

So... any ideas what the heck is going on here?

Thanks!

-- Roger

---

### Post by Krupski on 2010-01-01
Nobody???

:confused:

---

