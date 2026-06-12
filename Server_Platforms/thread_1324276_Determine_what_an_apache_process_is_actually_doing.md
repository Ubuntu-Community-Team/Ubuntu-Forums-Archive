---
title: "Determine what an apache process is actually doing?"
date: 2009-11-12
forum: Server Platforms
---

### Post by KayakJim on 2009-11-12
Is it possible to find out what a particular apache process is doing (e.g. what script it is running, what website it is serving, etc.)?

When I run top, I have about 20 apache2 processes but I am not able to find anyway to determine what the ones with a high cpu or mem usage is actually doing.

Any help would be appreciated.

---

### Post by KayakJim on 2009-11-12
This might help explain what I am looking for a bit better.

Here is a capture from top:
> top - 13:31:00 up 106 days, 54 min,  1 user,  load average: 10.00, 6.17, 4.31
Tasks: 229 total,  13 running, 216 sleeping,   0 stopped,   0 zombie
Cpu(s): 84.8%us, 15.1%sy,  0.0%ni,  0.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   7872040k total,  7288292k used,   583748k free,    24964k buffers
Swap:        0k total,        0k used,        0k free,  5349172k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                     
 7946 www-data  16   0  509m  30m  17m R   19  0.4   0:00.67 apache2                      
 7855 www-data  15   0  509m  40m  27m S   19  0.5   0:02.17 apache2                      
 7906 www-data  15   0  510m  49m  36m S   15  0.6   0:01.16 apache2                      
 7913 www-data  16   0  510m  32m  19m S   14  0.4   0:02.09 apache2                      
 8032 www-data  16   0  510m  28m  16m R   14  0.4   0:00.43 apache2                      
 5783 mysql     15   0  791m 269m 6256 S   14  3.5   1:56.71 mysqld                       
 7664 www-data  15   0  509m  33m  21m S   11  0.4   0:05.20 apache2                      
 7911 www-data  15   0  509m  35m  23m S   10  0.5   0:01.28 apache2                      
 8024 www-data  15   0  506m  26m  16m S    8  0.3   0:00.25 apache2                      
 8021 www-data  15   0  506m  28m  17m S    8  0.4   0:00.24 apache2                      
 7945 www-data  15   0  507m  26m  16m S    6  0.3   0:00.77 apache2                      
 8040 www-data  18   0  508m  27m  15m R    6  0.4   0:00.25 apache2                      
 7636 www-data  15   0  510m  33m  20m S    6  0.4   0:07.68 apache2                      
 7879 www-data  15   0  509m  32m  20m S    5  0.4   0:00.76 apache2                      
 7579 www-data  15   0  509m  35m  23m S    5  0.5   0:06.56 apache2                      
 7919 www-data  15   0  509m  32m  20m S    4  0.4   0:01.12 apache2                      
 8018 www-data  16   0  506m  23m  14m S    3  0.3   0:00.11 apache2                      
 7860 www-data  15   0  507m  29m  18m S    3  0.4   0:02.04 apache2                      
 7676 www-data  15   0  510m  43m  30m S    2  0.6   0:03.51 apache2                      
 7858 www-data  15   0  510m  32m  19m S    2  0.4   0:01.19 apache2                      
 7862 www-data  15   0  508m  33m  20m S    2  0.4   0:01.28 apache2                      
 7888 www-data  15   0  510m  30m  17m S    2  0.4   0:01.45 apache2                      
 8047 www-data  16   0  505m  23m  13m S    2  0.3   0:00.06 apache2                      

My load average is typically at 0.80 so this is unusually high for my system.

The top 2 apache processes are using 19% of the cpu. Is there any way to determine what those 2 processes are actually doing?

---

### Post by Ilalmi on 2009-11-12
You could use strace ([http://unixhelp.ed.ac.uk/CGI/man-cgi?strace+1](http://unixhelp.ed.ac.uk/CGI/man-cgi?strace+1)).
If a file is used by a process with pid 1234 for example, ```
strace -p1234 -e trace=file
``` shows its filename. Thus you can see what html- or script file this process handles.

---

