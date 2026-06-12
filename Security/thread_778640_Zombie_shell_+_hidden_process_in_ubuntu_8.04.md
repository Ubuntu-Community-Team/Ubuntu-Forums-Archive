---
title: "Zombie shell + hidden process in ubuntu 8.04"
date: 2008-05-02
forum: Security
---

### Post by vermoos on 2008-05-02
I upgraded to Hardy Heron 8.04 over the net, and noticed a shell process marked in the system monitor called 'sh Zombie'.

It has a 4-integer PID and has Memory N/A); it opens no files and has no memory maps, and appears to do nothing.

I had a poke around using unhide and found another PID, a hidden one with 5-integers!

unhide proc
Found HIDDEN PID: XXXXX

How do i kill-off a hidden pid?

#################################

The above happened only when i upgraded via the 'upgrade' button in synaptics. 

I burnt a cd and did a fresh install and it was ok.

Bug in synaptics upgrade?

---

### Post by 1337hippo on 2008-05-06
I'm also experiencing this issue. In fact, I usually have multiple "sh" process running, all of them Zombies with N/A in memory usage. I also did the online upgrade-- I plan to do a fresh install as soon as I am done with finals.

---

### Post by ksennin on 2008-05-06
I get two zombie processes, too, and also did an upgrade.  I really did not want to do a full install and lose all my configurations...  Sigh.

---

### Post by jARLAXL on 2008-05-07
me too! 1 shell zombie process but from fresh install.as well as an lsb_release zombie process which appears to shut down when i turn on the system monitor.

---

### Post by TheWhatkin on 2008-05-07
One more with this problem. Anyone find a solution that doesn't involve a full blown reinstall?

---

### Post by chrisubuntu on 2008-05-12
> **TheWhatkin said:**
> One more with this problem. Anyone find a solution that doesn't involve a full blown reinstall?

I don't think a few zombie processes should require a reinstall of the OS :)
Zombie processes are just processes that did not get 'cleaned up' by the parent process. They consume no resources and don't do anything.

---

### Post by Teihoo on 2008-05-13
Same here. Did an upgrade from 7.10 (which was clean install)... Same thing on my notebook :confused:

Can I make it disappear from Sys Mon? Otherwise everything is running smoothly. I just love it!

---

### Post by jacek_sw on 2008-05-13
List process (and parent)

ps -Af

in my case the parent process was:
/usr/lib/python /usr/lib/deskbar  

Deskbar Applet (search) - I have no need for it so I have removed it and don't have that problem since.

I am new to this (linux) so please use at your own risk.

Jacek

---

### Post by HunterSBuntu on 2008-05-31
I have the same problem.

From the moment I boot, there's a zombie root user sh process.  The process ID of this process increases with every refresh of the system monitor window also, which makes it next to impossible to kill it because by the time I get the kill command off it's got a different process ID and I'm told that no process with the ID I tried to kill exists.

I also did an update.  7.08 -> 7.10 -> 8.04

So...yeah.  Anyone have any further info on what this is?

---

### Post by pawnrocket on 2008-05-31
ps -AF

[sh] <defunct>


What does <defunct> mean?  I also cannot end the process

---

### Post by pawnrocket on 2008-05-31
bump

---

### Post by HalPomeranz on 2008-06-01
Google is your friend:

[http://kenno.wordpress.com/2007/04/04/how-to-kill-defunct-process/](http://kenno.wordpress.com/2007/04/04/how-to-kill-defunct-process/)
[http://www.cts.wustl.edu/~allen/kill-defunct-process.html](http://www.cts.wustl.edu/~allen/kill-defunct-process.html)

---

### Post by HunterSBuntu on 2008-06-01
I looked into my zombie sh process a little further.

It's always got a parent process ID (PPID) of 5668

I looked up what that processcis using: 

ps -F -p 5668

It tells me that process 5668 is /usr/bin/python/

The parent process of /usr/bin/python in turn is /sbin/init which as I understand is responsible for calling a whole bunch of startup scripts at boot.

I'm not sure how to proceed from this point.  Should I kill the /usr/bin/python process every time I boot my computer?  Will that impact other programs on my computer that are using Python?

Any ideas on how to further isolate why exactly Python is always leaving this zombie process?

---

### Post by HalPomeranz on 2008-06-02
> **HunterSBuntu said:**
> 
I'm not sure how to proceed from this point.  Should I kill the /usr/bin/python process every time I boot my computer?  Will that impact other programs on my computer that are using Python?


You can kill this process without impacting other Python processes on the system.  But it's going to be annoying to do it on each boot up.

> **HunterSBuntu said:**
> 
Any ideas on how to further isolate why exactly Python is always leaving this zombie process?

It's possible that the process logged some stuff to syslog before going defunct, and the log messages will be tagged with the process ID number.  So you might try:

```

sudo grep -r <pid> /var/log

```

Obviously, substitute the PID you got from the ps command for <pid> in the command above.

I'm not sure what happens in /proc when a process goes defunct.  If you can cd into /proc/<pid>, you might be able to figure out something about the process from the various files in that directory. 

 1) "cat cmdline" should give you the name the process is running under (although this may just return "defunct" unfortunately)

2) "sudo cat environ | perl -pe 's/\000/\n/g'" gets you the environment variable settings for the process

3) "sudo ls -l fd" shows you what files the process currently has open

4) "sudo ls -l cwd" shows you the current working directory of the process

5) "sudo strings exe | less" will let you see the strings embedded in the executable (something like the "usage" message or help text embedded in the executable may tip you off about what the process is)

---

### Post by Bubba64 on 2008-06-02
> **chrisubuntu said:**
> I don't think a few zombie processes should require a reinstall of the OS :)
Zombie processes are just processes that did not get 'cleaned up' by the parent process. They consume no resources and don't do anything.

I know you see zombie, and look for your shotgun I had a few on an install but after awhile they cleared as this poster suggests. All the posts on this I have seen say don't worry about it. you can run top in terminal and get a quick look at running systems.

---

### Post by HunterSBuntu on 2008-06-02
> **HunterSBuntu said:**
> I looked into my zombie sh process a little further.

It's always got a parent process ID (PPID) of 5668

I looked up what that processcis using: 

ps -F -p 5668

It tells me that process 5668 is /usr/bin/python/


I've looked at a bit more and the parent process of the zombie sh, ppid 5668, is daemon.py, not /usr/bin/python. 

Daemon.py is the startup script for the WICD network manager that I'm using.

Is anyone else that's exeperiencing this problem using WICD?

---

### Post by imdano on 2008-06-02
daemon.py is being run as "/usr/bin/python daemon.py", so techincally python is the parent.  It's a known wicd issue, some process getting called by wicd to monitor network status isn't getting reaped properly.  Every time the status is updated, the old zombie goes away and a new one appears (which is why the pid keeps changing).  I haven't put a ton of time in figuring out which call is doing it, as I'm using a unreleased development version that doesn't run any subprocesses to monitor the network (so there are no zombies).  If the bug still exists in the upcoming version (which still uses external program calls, but much fewer), I'll make some time to track down the problem call.  If you want to test it out, you can check it out from our subversion repository.  But really, the zombie is nothing to worry too much about, as someone said earlier, it takes up no memory and doesn't actually do anything.  It just can't be cleared from the running process table because it's parent doesn't know it exited.

---

### Post by HunterSBuntu on 2008-06-03
> **imdano said:**
> daemon.py is being run as "/usr/bin/python daemon.py", so techincally python is the parent.  It's a known wicd issue, some process getting called by wicd to monitor network status isn't getting reaped properly.  Every time the status is updated, the old zombie goes away and a new one appears (which is why the pid keeps changing).  I haven't put a ton of time in figuring out which call is doing it, as I'm using a unreleased development version that doesn't run any subprocesses to monitor the network (so there are no zombies).  If the bug still exists in the upcoming version (which still uses external program calls, but much fewer), I'll make some time to track down the problem call.  If you want to test it out, you can check it out from our subversion repository.  But really, the zombie is nothing to worry too much about, as someone said earlier, it takes up no memory and doesn't actually do anything.  It just can't be cleared from the running process table because it's parent doesn't know it exited.

Thanks a lot for the info, much appreciated.

Still learning the ropes on Linux and anything 'weird' that is root related tends to freak me out.

---

### Post by jARLAXL on 2008-06-14
Today's updates fixed my problem which was caused by the deskbar applet.

---

