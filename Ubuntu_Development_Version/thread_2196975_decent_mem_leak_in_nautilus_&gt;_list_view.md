---
title: "decent mem leak in nautilus &gt; list view"
date: 2014-01-01
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-01-01
Happens when scrolling in a dir. that contains a large number of thumbnailed files, a well populated Videos folder would be a good example.
Overall not a huge issue unless one is running on limited memory or happens to leave installs up for a long time (& obviously does alot of scrolling in such dir.'s
Mem will only be freed by killing nautilus or restart
Seen in nautilus 3.8 thru 3.10, ubuntu & fedora 20 installs

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1264539](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1264539)

---

### Post by QDR06VV9 on 2014-01-01
Very Happy Nemo user here.

---

### Post by mc4man on 2014-01-01
> **runrickus said:**
> Very Happy Nemo user here.
No fan of nemo - maybe it looks, work  better on cinnamon/mint, whatever.

In any event it shows the same mem leak, at least when  used in an ubuntu session

---

### Post by d-cosner on 2014-01-01
I can confirm the memory leak. I just scrolled through my video collection and watched the memory use go up. Closing Nautilus did not release any memory either.

---

### Post by QDR06VV9 on 2014-01-01
> **mc4man said:**
> No fan of nemo - maybe it looks, work  better on cinnamon/mint, whatever.

Linux all about chioces;)  Theres a link here in forums if your interested(though I doubt it) running nemo with out deps.

```
In any event it shows the same mem leak, at least when  used in an ubuntu session
```
I dont see it running GS.
Regards

---

### Post by tista on 2014-01-02
@mc4man,

I can confirm this leak in case that nautilus tried to showing much of thumbnails.

Regards,
Tista

---

### Post by mc4man on 2014-01-02
> **runrickus said:**
> Linux all about chioces;) 
```
In any event it shows the same mem leak, at least when  used in an ubuntu session
```
I dont see it running GS.
Regards
Does happen with Gs & nemo though not at the rate of nautilus
```
Linux 3.12.0-7-generic (doug-Lenovo-IdeaPad-Y580) 	01/01/2014 	_x86_64_	(8 CPU)

11:39:53 PM   UID       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
11:39:56 PM  1000      6196  11480.33      0.00  948732  37032   0.46  nemo
11:39:59 PM  1000      6196   7434.33      0.00  950176  38468   0.48  nemo
11:40:02 PM  1000      6196   5332.23      0.00  951212  39512   0.49  nemo
11:40:05 PM  1000      6196   3075.67      0.00  951844  40148   0.50  nemo
11:40:08 PM  1000      6196   5944.33      0.00  953000  41300   0.51  nemo
11:40:11 PM  1000      6196   5040.67      0.00  953984  42284   0.52  nemo
11:40:14 PM  1000      6196   8410.67      0.00  955652  43956   0.54  nemo
11:40:17 PM  1000      6196   9211.33      0.00  957468  45772   0.57  nemo
11:40:20 PM  1000      6196   2514.67      0.00  957960  46260   0.57  nemo
11:40:23 PM  1000      6196  11452.33      0.00  960304  48612   0.60  nemo
Average:     1000      6196   6989.10      0.00  954033  42334   0.52  nemo
```

thinking gtk3 is involved..

---

### Post by QDR06VV9 on 2014-01-02
> **mc4man said:**
> Does happen with Gs & nemo though not at the rate of nautilus
```
Linux 3.12.0-7-generic (doug-Lenovo-IdeaPad-Y580)     01/01/2014     _x86_64_    (8 CPU)

11:39:53 PM   UID       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
11:39:56 PM  1000      6196  11480.33      0.00  948732  37032   0.46  nemo
11:39:59 PM  1000      6196   7434.33      0.00  950176  38468   0.48  nemo
11:40:02 PM  1000      6196   5332.23      0.00  951212  39512   0.49  nemo
11:40:05 PM  1000      6196   3075.67      0.00  951844  40148   0.50  nemo
11:40:08 PM  1000      6196   5944.33      0.00  953000  41300   0.51  nemo
11:40:11 PM  1000      6196   5040.67      0.00  953984  42284   0.52  nemo
11:40:14 PM  1000      6196   8410.67      0.00  955652  43956   0.54  nemo
11:40:17 PM  1000      6196   9211.33      0.00  957468  45772   0.57  nemo
11:40:20 PM  1000      6196   2514.67      0.00  957960  46260   0.57  nemo
11:40:23 PM  1000      6196  11452.33      0.00  960304  48612   0.60  nemo
Average:     1000      6196   6989.10      0.00  954033  42334   0.52  nemo
```

thinking gtk3 is involved..

Doug here is what i get opening Nemo/Music with about 3000 mp3s in that folder
```
you@ubuntu:~$ top

top - 17:43:26 up 25 min,  3 users,  load average: 0.16, 0.35, 0.45
Tasks: 192 total,   2 running, 190 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.9 us,  1.2 sy,  0.0 ni, 96.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   3897928 total,  1873256 used,  2024672 free,    68268 buffers
KiB Swap:  1944572 total,        0 used,  1944572 free,   912936 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 1164 root      20   0  333m  62m  39m S   3.3  1.7   1:08.52 Xorg              
 6145 you       20   0  454m  22m  12m S   3.0  0.6   0:01.35 gnome-terminal-   
 2083 you       20   0 1802m 130m  30m S   2.3  3.4   0:54.07 gnome-shell       
 2246 you       20   0  841m 8260 4940 S   2.3  0.2   0:26.50 conky             
 1019 root      20   0  339m 7208 5460 S   0.7  0.2   0:01.15 NetworkManager    
 6233 you       20   0 22304 1584 1112 R   0.7  0.0   0:00.33 top               
   17 root      20   0     0    0    0 S   0.3  0.0   0:01.42 rcu_sched         
   19 root      20   0     0    0    0 S   0.3  0.0   0:00.61 rcuos/1           
  549 root     -51   0     0    0    0 S   0.3  0.0   0:04.67 irq/47-iwlwifi    
    1 root      20   0 27352 3080 1416 S   0.0  0.1   0:01.49 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.01 ksoftirqd/0       
    5 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/0:0H      
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.20 migration/0       
    8 root      20   0     0    0    0 S   0.0  0.0   0:00.00 rcu_bh            
    9 root      20   0     0    0    0 S   0.0  0.0   0:00.00 rcuob/0           
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.00 rcuob/1           


```
I wont disagree with it being GTK3.10 seen some strange[* anomalies*]("http://www.thefreedictionary.com/anomalies") since its arrival;)
My specs
```
GNOME Shell 3.10.2.1
3.12.0-7-exton
nemo 2.0.8
GNOME nautilus 3.10.1

```

---

### Post by Mateusz Stachowski on 2014-01-03
Maybe check how it looks with health-check from ppa:colin-king/white. That's a tool developed by Colin King to diagnose resource usage.

[https://launchpad.net/~colin-king/+archive/white](https://launchpad.net/~colin-king/+archive/white)

[http://smackerelofopinion.blogspot.com/2013/09/health-check-tool-to-diagnose-resource.html](http://smackerelofopinion.blogspot.com/2013/09/health-check-tool-to-diagnose-resource.html)

This tool provides reports for multiple resources used by a one or more processes. Of course memory utilisation (including memory growth) is one of those things being reported.

I used this tool myself on Nautilus in 14.04 and it didn't report any significant memory growth during the 60 seconds of it's default duration. I browsed directories full of video files, image files and a directory containing 44 folders and 693 elements of very different type (that was my downloads folder).

```
Change in memory (K/second): PID Process Type Size RSS PSS3475 nautilus Stack 136.53 0.47 0.47 (growing moderately fast)
3475 nautilus Heap -297.73 -161.20 -161.20 (shrinking fast)
3475 nautilus Mapped 0.00 0.40 0.00 (growing slowly)


Heap Change via brk():
PID brk Count Change (K) Rate (K/Sec)
3475 nautilus 5 -284 -4.73 (shrinking)


Memory Change via mmap() and munmap():
PID mmaps munmaps Change (K) Rate (K/Sec)
3475 nautilus 0 53 -9584 -159.73 (shrinking moderately fast)
```

---

### Post by Mateusz Stachowski on 2014-01-03
Nevermind my previous health-check log I didn't use the list view when running that check. Now I've switched to the list view and Nautilus leaks memory badly.

```
Change in memory (K/second):  PID  Process              Type        Size       RSS       PSS
  3475 nautilus             Heap      274.06    274.73    274.73 (growing fast)
  3475 nautilus             Mapped      0.00      0.00     -0.07 (shrinking slowly)


Heap Change via brk():
  PID                        brk Count   Change (K)  Rate (K/Sec)
  3475 nautilus                  10365        16296        271.60 (growing fast)


Memory Change via mmap() and munmap():
  PID                          mmaps  munmaps  Change (K)  Rate (K/Sec)
  3475 nautilus                11882    11882           0          0.00 (no change)



```

---

### Post by mc4man on 2014-01-03
> **Mateusz Stachowski said:**
> Maybe check how it looks with health-check from ppa:colin-king/white. That's a tool developed by Colin King to diagnose resource usage.



```
Change in memory (K/second):
  PID  Process              Type        Size       RSS       PSS
  2949 nautilus             Heap      960.21    960.21    960.21 (growing very fast)
  2949 nautilus             Mapped      0.00     -0.07      7.70 (growing)

Heap Change via brk():
  PID                        brk Count   Change (K)  Rate (K/Sec)
  2949 nautilus                  43475        57336        955.54 (growing fast)

Memory Change via mmap() and munmap():
  PID                          mmaps  munmaps  Change (K)  Rate (K/Sec)
  2949 nautilus                17953    17952         132          2.20 (growing)


```

Are you using nautilus in list view?

---

### Post by Mateusz Stachowski on 2014-01-03
In my first comment I posted results when using Nautilus in grid view but then I looked again at the title of the thread mentioning that the problem lies in list view. Then I run helth-check again with Nautilus set to list view.

---

### Post by QDR06VV9 on 2014-01-04
```
[QUOTE=Mateusz Stachowski;12890182]Maybe check how it looks with health-check from ppa:colin-king/white. That's a tool developed by Colin King to diagnose resource usage.

[https://launchpad.net/~colin-king/+archive/white](https://launchpad.net/~colin-king/+archive/white)

[http://smackerelofopinion.blogspot.com/2013/09/health-check-tool-to-diagnose-resource.html](http://smackerelofopinion.blogspot.com/2013/09/health-check-tool-to-diagnose-resource.html)

This tool provides reports for multiple resources used by a one or more processes. Of course memory utilisation (including memory growth) is one of those things being reported./QUOTE]
```

Thanks Mateusz Stachowski Useful Tool great for testing.
If anybody is interested you can free up memory by
Code
```
sudo sync && echo 3 | sudo tee /proc/sys/vm/drop_caches[INDENT]**Or  "****sudo sysctl -w vm.drop_caches=3**"[/INDENT]

```[INDENT]
Regards
**NOTE:** *this action won't make your system faster nor it will  affect its stability and performance, it will just clean up memory used  by the Linux Kernel on caches.*
[/INDENT]

---

### Post by kansasnoob on 2014-01-28
I wonder if this might be fixed now? The changelog doesn't reference a bug#:

> nautilus (1:3.10.1-0ubuntu2) trusty; urgency=medium

  * debian/patches/interactive_search.patch:
    - Fix memory leak

 -- Daniel Wyatt <Daniel.Wyatt@gmail.com>  Tue, 28 Jan 2014 17:33:38 +1300


---

### Post by mc4man on 2014-01-28
> **kansasnoob said:**
> I wonder if this might be fixed now? The changelog doesn't reference a bug#:

I don't think so, I believe that was a mem leak caused by the return of 'type-ahead find'
(will ck. later as currently running a general leak test on nautilus-3.10's toolbar actions

Edit: still going strong & on the surface of little concern to gnome dev's

---

