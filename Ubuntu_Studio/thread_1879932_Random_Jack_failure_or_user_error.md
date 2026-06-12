---
title: "Random Jack failure or user error"
date: 2011-11-12
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2011-11-12
I cut off my computer last night which was running a generic kernel and jackd version 0.118.0.  We were recording last night with no problems.

I wake up this morning to find jack constantly failing.  I've had the normal problems setting jack up, but this one is different.

Here's the output.

```
14:15:29.158 Patchbay deactivated.
14:15:29.160 Statistics reset.
14:15:29.170 ALSA connection graph change.
14:15:29.367 ALSA connection change.
14:15:56.881 Startup script...
14:15:56.882 artsshell -q terminate
sh: artsshell: not found
14:15:57.284 Startup script terminated with exit status=32512.
14:15:57.284 JACK is starting...
14:15:57.285 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2 -s
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
14:15:57.292 JACK was started with PID=6741.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|soft-mode|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
14:15:59.347 Server configuration saved to "/home/ben/.jackdrc".
14:15:59.348 Statistics reset.
14:15:59.349 Client activated.
14:15:59.357 JACK connection change.
14:15:59.360 JACK connection graph change.
ALSA: poll time out, polled for 34862333 usecs
DRIVER NT: could not run driver cycle
14:16:32.168 JACK connection graph change.
jack main caught signal 12
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
14:16:32.186 Client deactivated.
cannot continue execution of the pro
14:16:32.187 JACK was stopped successfully.
14:16:32.188 Post-shutdown script...
14:16:32.188 killall jackd
cessing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
14:16:32.614 Post-shutdown script terminated with exit status=256.
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
jackd: no process found
```

For the forum's sake, I remove the **hundreds** of lines that said "cannot continue execution of the processing graph (Broken pipe)"

Can anyone help me out?  The card is an RME HDSP MADI and this is Ubuntu 10.04 desktop.

lshw:

```
ben@DAW:~$ sudo lshw -C multimedia
[sudo] password for ben: 
  *-multimedia            
       description: Multimedia audio controller
       product: RME Hammerfall DSP MADI
       vendor: Xilinx Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       version: cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=RME Hammerfall DSP MADI latency=64
       resources: irq:19 memory:dbff0000-dbffffff

```

/etc/security/limit.conf

```

ben@DAW:~$ sudo cat /etc/security/limits.conf 
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
@realtime - rtprio 99
@realtime - memlock unlimited
#@realtime - nice -10
# End of file

```

---

### Post by youtaidui on 2011-11-23
> ** said:**
> 
A bus accident in a town 30 miles south-west of Medellin,[*******](http://www.doudoune-*******-pascherfr.com/), central Colombia,[christian louboutin](http://www.christianclouboutinpascher.com), left two people dead and 35 injured Sunday afternoon.The chiva bus crashed into a house in the town of Betulia after losing its brakes on a steep slope on the border of the Betulia municipality. The vehicle was returning to the part of the municipality named Vereda El Indio and was full of residents from the area who had left the town for the day to sell their products,[coach outlet](http://www.coachoutlethandbagsstores.com/), reported Caracol Radio. Email thisThe other injured persons are being attended to at the German Velez Gutierrez hospital in Betulia. RCN Radio reported Monday morning that the four most seriously injured,[abercrombie paris](http://www.abercrombieandfitchparis.biz), one a seven year old minor,[*******](http://www.monclersitoufficialet.com/), were transferred by an air force helicopter to a hospital in Medellin. The four exhibited head and chest injuries. Tweet   Related articles&#65306;      [where conditions foster mixing of pathogens](http://www.poetry.com/poetry_forum/viewtopic.php?f=38&t=306&view=unread#unread)     [an "all or nothing" society](http://www.firelake.in.ua/forum_ru/index.php?topic=39070.msg86425#msg86425)     [34 languages in Colombia](http://thecowdentrust.com/forum/viewtopic.php?f=6&t=77982&view=unread#unread)   &#12288;Joe Sanders has the most beautiful garden in our town. Nearly everybody enters for 'The Nicest Garden&#12288;Competition' each year, but Joe wins every time. Bill Frith's garden is larger than Joe's. Bill works&#12288;harder than Joe&#12288;and grows more flowers and vegetables, but Joe's garden is more interesting. He has made neat paths and&#12288;has built&#12288;a wooden bridge over a pool. I like gardens too, but I do not like hard work. Every year I enter for the&#12288;garden&#12288;competition too, and I always win a little prize for the worst garden in the town!

---

