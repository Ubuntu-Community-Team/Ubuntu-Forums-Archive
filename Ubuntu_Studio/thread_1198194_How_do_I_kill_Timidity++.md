---
title: "How do I kill Timidity++ ?"
date: 2009-06-27
forum: Ubuntu Studio
---

### Post by pedrocortez on 2009-06-27
Hi , 
I now have a good working set up for home recording using UStudio 8.04 -rt, Hydrogen, Ardour, Rakarrack etc
But I want to use Qsynth for pad sounds and just cant seem to get it running with jack ready to record the audio in Ardour. 

It seems to be a problem with Timidity which installs by default and I dont use.  
How do I kill off timidity so that Qsynth will run OK. 
I know how to configure the connections in Qjackctl etc. 

cheers
Pete

---

### Post by raboofje on 2009-06-27
> **pedrocortez said:**
> It seems to be a problem with Timidity which installs by default and I dont use. How do I kill off timidity so that Qsynth will run OK.

You could, of course, uninstall it entirely:

```
sudo apt-get remvoe timidity
```

.. or stop the service once:

```
sudo /etc/init.d/timidity stop
```

---

### Post by thorgal on 2009-06-27
you can also stop the service permanently:

```

sudo apt-get install sysv-rc-conf

```

this will install an ncurses based service configuration tool. Then you just run it from the terminal:

```

sudo sysv-rc-conf

```

browse to the timidity service (use Ctrl-n to scroll down page by page), untick all ticked run-levels for timidity, and quit (type q for that). That's all. Next time you boot, timidity will not be started at any run-level.

FYI, booting goes through different run levels because the booting sequence is divided into different sequences. You cannot boot say, the windows manager before certain things were already started. Usually, the X windows system is the last thing to be booted. It used to be at run level 5 but debian only really used 2 run levels at boot time, once the initrd had done its job and let the kernel take over the boot process.

The fact that services are ticked for run levels 2, 3, 4 and 5 is because some ppl do use up to 5 run levels. But say your service had started at run level 2; when run level 3 is triggered, the service will not be started a second time. The start-stop-daemon mechanism is clever enough to avoid redundant service startups thanks to /var/run/<some service>.pid (which contains the process id of the running service).

OK, enough blabla, that's quite OT.

---

### Post by raboofje on 2009-06-27
> **thorgal said:**
> OK, enough blabla, that's quite OT.

Actually, I had been thinking of pointing the ubuntu documentation for sysvinit tasks, but could not find it.

I noticed documentation of this kind of core functionality being poor - I couldn't find a good explanation of 'group' (as in /etc/group) either.

Am I missing something? Perhaps we should just start adding these things to wiki.ubuntu.com ?

---

### Post by khelben1979 on 2009-06-27
```
sudo ps -A | less

kill -9 [process number for Timidity++]
```

---

### Post by latinkecki9 on 2011-01-15
> **pedrocortez said:**
> Hi , I now have a good working set up for home recording using UStudio 8.04 -rt, Hydrogen, Ardour, Rakarrack etcBut I want to use Qsynth for pad sounds and just cant seem to get it running with jack ready to record the [[COLOR=#000000]audio[/COLOR]](http://www.software-to-convert.com/avi-conversion-software/avi-to-ts-software.html) in Ardour. It seems to be a problem with Timidity which installs by default and I dont use. How do I kill off timidity so that Qsynth will run OK. I know how to configure the connections in Qjackctl etc. cheersPeteThanks for your analysis! It is exactly what I need.

---

