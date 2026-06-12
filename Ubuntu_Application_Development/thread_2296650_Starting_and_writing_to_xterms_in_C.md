---
title: "Starting and writing to xterms in C"
date: 2015-09-27
forum: Ubuntu Application Development
---

### Post by rkraml on 2015-09-27
I am trying to get a c program to create and write output to multiple xterms. i have tried fp = popen( "xterm", "w" ) and tried to write to the file pointer returned printf( fp, "Hello Worldl\n" ) ) but nothing appears in the terminal.

Alternatively I have used system( "xterm" ) and tried various ways to get the new pseudo-terminal including such gyrations as diffing ls /dev/pts before and after the system call but this seems like a really wrong way.  I can write to /dev/pts/n fine but the c program has no way of knowing the terminal number it just opened.

-Bob

---

### Post by TheFu on 2015-09-27
Most of the time, I just write to different log files and have each terminal watch those with the tail. Not really what you asked, just a more standard solution. Don't know if this will work for your needs.

Have you tried using the full path the the xterm program? Don't trust the PATH, since there isn't a shell to fill in the stuff most programs expect.

---

