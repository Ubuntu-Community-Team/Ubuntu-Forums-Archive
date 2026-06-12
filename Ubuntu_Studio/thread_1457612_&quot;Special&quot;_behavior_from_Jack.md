---
title: "&quot;Special&quot; behavior from Jack"
date: 2010-04-18
forum: Ubuntu Studio
---

### Post by hreichgott on 2010-04-18
Hi, I have been using Ubuntu (karmic 9.10) for a few months on a 2-processor Thinkpad T60 and just upgraded to Studio today.  I record and livestream music.  I am trying to understand Jack and would appreciate a bit of education about why I get certain errors when starting Jack in certain ways.  I have read all the Ubuntu Studio help files concerning Jack, and I followed all the instructions for system configuration when I upgraded to Studio; this post is only about  issues not addressed in those help files.

First of all, here's what DOES work:

1. Starting Jack from the command line like this
```
jackd -d alsa -r 44100 -p 2048
```Once jackd is started thus, I can happily run qjackctl, idjc, jackeq, and everything else I've needed so far.

2. Starting an application that politely asks Jack to start as part of its own bootup process, for example, ardour2.  But not Jack Control (qjackctl), ironically--see below.

Now here's what does NOT work.  Could someone help me understand why not, and what's going on here?

1. Starting Jack from the command line asking for realtime, -R according to the manpage
```
jackd -R -d alsa -r 44100 -p 2048
```I get a pause of a few seconds, then the message "Bus error."
Once this has happened, I cannot start Jack even without the -R flag!  I get the same "bus error" even if my syntax is identical to the syntax that normally works.  I must completely force-reload alsa in order to make the bus error go away.
Also, I am wondering whether realtime is the default way that Jack starts?  I read that it is, but then I don't understand why the -R flag would crash Jack.

2. Starting qjackctl from the menu interface or from a terminal, and asking qjackctl to start Jack.  Qjackctl opens fine.  I click "Start" and get a crash. Here are the messages:
```

20:29:38.735 Startup script...
 20:29:38.736 artsshell -q terminate
 sh: artsshell: not found
 20:29:39.139 Startup script terminated with exit status=32512.
 20:29:39.139 JACK is starting...
 20:29:39.140 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
 20:29:39.143 JACK was started with PID=3915.
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 20:29:41.954 Server configuration saved to "/home/heather/.jackdrc".
 20:29:42.151 Statistics reset.
 20:29:47.745 Client activated.
 cannot read server event (Success)
 cannot send request type 6 to server
 cannot continue execution of the processing graph (Bad file descriptor)
 cannot continue execution of the processing graph (Bad file descriptor)
<snip, the above line is repeated a couple hundred times>

20:29:50.187 Client deactivated. cannot continue
 20:29:50.189 JACK was stopped successfully.
 20:29:50.189 Post-shutdown script...
 20:29:50.190 killall jackd
 20:29:50.191 JACK has crashed.
20:29:50.969 Post-shutdown script terminated with exit status=256.
```3. Starting qjackctl with sudo, and asking qjackctl to start Jack.  Again, qjackctl starts fine, then I get a crash, with different messages:
```

20:34:29.640 Patchbay deactivated.
 20:34:29.650 Statistics reset.
 Home directory /home/heather not ours.
 20:34:29.861 ALSA connection graph change.
 20:34:30.030 ALSA connection change.
 20:34:38.026 Startup script...
 20:34:38.027 artsshell -q terminate
 sh: artsshell: not found
 20:34:38.429 Startup script terminated with exit status=32512.
 20:34:38.429 JACK is starting...
 20:34:38.430 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
 20:34:38.433 JACK was started with PID=4014.
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 20:34:41.642 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 20:34:42.489 JACK was stopped successfully.
 20:34:42.513 Post-shutdown script...
 20:34:42.513 killall jackd
 20:34:42.514 JACK has crashed.
 jackd: no process found
 20:34:43.006 Post-shutdown script terminated with exit status=256.

```4. Starting qjackctl as root, and asking qjackctl to start Jack.  Qjackctl starts beautifully. Jack starts beautifully.  I open a Jack-using program and THE ENTIRE OPERATING SYSTEM HANGS.  Makes me feel like I'm back in Windows.

---

### Post by AutoStatic on 2010-04-19
Hello hreichgott, the bus error could indicate a memory allocation problem. Did you modify your */etc/security/limits.conf* file? If so, could you post the content of it? If not, maybe it helps to add the following lines:
```
 @audio - rtprio 90       # maximum realtime priority
 @audio - memlock <amount of RAM - 20%>  # maximum locked-in-memory address space (KB)
```

The value for memlock depends on your amount of RAM of course.

More info here: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf)

---

### Post by hreichgott on 2010-04-19
Here is limits.conf.  I modified it according to the Ubuntu Studio instructions.
```
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

@audio          -       rtprio          99
@audio          -       nice           -19
@audio          -       memlock         unlimited

# End of file

```

I have 488.4 megabytes of RAM.

What would be accomplished by changing memlock to a smaller amount?
(also, if I give it a number, what units do I use--mb, gb, kb?)

---

### Post by hxcobd on 2010-04-19
Nothing would be accomplished by setting it to a smaller amount. Your limits.conf settings look fine.

(Of course, I'm assuming your user account is within the 'audio' group.)

---

### Post by AutoStatic on 2010-04-20
> **hxcobd said:**
> Nothing would be accomplished by setting it to a smaller amount. Your limits.conf settings look fine.It would accomplish that the computer won't lock up again. 500 Mb is not much these days, if you allow this memory to be fully locked then chances are this can actually happen. I would set it to a smaller amount, amount of RAM minus 20%. In kilobytes that would be approx. 400000.

---

### Post by hreichgott on 2010-04-29
That's helpful about memory usage, thanks.

Any hints on why I can't start Jack using qjackctl?  I don't understand the error messages.

---

