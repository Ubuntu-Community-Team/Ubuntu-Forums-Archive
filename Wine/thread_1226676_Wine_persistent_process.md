---
title: "Wine persistent process"
date: 2009-07-29
forum: Wine
---

### Post by Baversjo on 2009-07-29
Hi!

I have a .exe file that I execute very often from a php script in wine. It's working, however it takes around 1 seconds more for the process to complete on ubuntu than on windows. When I let notepad.exe run in the background all the time, the .exe file is executed around .7 seconds faster. I beleve this is because the wineserver is allready up and running and doesn't need to be initialized again. I tried to run wineserver -p which didn't give any performance boost. I tried compiling a windows console application that would sleep all the time and act as a process that simply keeps wine up all the time (instead of having notepad up) which nether didn't work.

I am therefore looking for a solution that keeps wine up and running, ready to execute my .exe file(s).

Why I am doing thins: Our company is looking for ways of eliminating all windows computers.

Thank you very much for your help.

---

### Post by NightMKoder on 2009-07-29
Just start the wineserver in persistent mode:

wineserver -p

There are a bunch of other options that you may find useful:

```

Usage: wineserver [options]

Options:
   -d[n], --debug[=n]       set debug level to n or +1 if n not specified
   -f,    --foreground      remain in the foreground for debugging
   -h,    --help            display this help message
   -k[n], --kill[=n]        kill the current wineserver, optionally with signal n
   -p[n], --persistent[=n]  make server persistent, optionally for n seconds
   -v,    --version         display version information and exit
   -w,    --wait            wait until the current wineserver terminates

```

---

### Post by Baversjo on 2009-07-30
Running wineserver persistent doesn't seem to do it as the .exe file launches much faster when notepad is running. I have verified this over ten times. Any ideas?

---

