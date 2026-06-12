---
title: "Does anyone know the limits of the PS/2 keyboard interface?"
date: 2013-05-25
forum: Server Platforms
---

### Post by vtsstumpjump on 2013-05-25
I am downloading a copy just to find out how much better a Ubunti server 12 is with a computer feeding keystrokes at a rate of nearly 4000 WPM while its doing other things to tie it up.

I was wanting to know what limits are in the system and what they rely on to increase them?

Can you start a new application with Ubunti while its still loading you keep performing commands on the keyboard for the application when it gets there?

I can bring my P4 XP box to a grinding halt when I feed it with things to do it from a command prompt. I takes over 300 000 keystrokes to do though takes about 15 minutes. When running IE8 you have to wait at least 150 mS before you can tab again or it looses sync, it only takes 3 mS to send the key. I tested Ubunti desktop 10.x today off a boot cd and the tabs in FireFox are no problem running a full speed.

I am designing a Robot Forum Moderator to deal with common problems caused by Spammers, Human or Robot.

I intend to use a server with terminal services clients as subroutines and by Alt tabling I can leave it to run a program then go on to the next client and perform another task and so on.

Will Ubunti will allow Qbasic direct port I/O some how in realtime on the parallel port? if so then I will stop my coding my building blocks on windows but the supervisor computer will be DOS running QuickBASIC because I can boot the system from a CD and have it running very quickly.

PS: I have had a 10 000 character password (upper and lower case random letters) on FaceBook, one day I will make it longer and find the limit.

---

### Post by tgalati4 on 2013-05-25
Linux servers can be set to 100 Hz, 250 Hz, or 1,000 Hz for "ticks" or how fast the kernel polls the hardware for interrupts.  So presumably, setting 1,000 Hz would allow more PS/2 keyboard characters to be handled before other CPU tasks are handled.  I don't know if these can be changed at boot time with an entry in /etc/sysctl.conf or if they are compiled into the kernel.

There are several other time-related parameters that could be tweaked:

tgalati4@Mint14-Extensa /etc $ sysctl -a | grep time
sysctl: permission denied on key 'kernel.cad_pid'
dev.parport.default.spintime = 500
dev.parport.default.timeslice = 200
fs.lease-break-time = 45
sysctl: kernel.hung_task_timeout_secs = 120
kernel.sched_rt_runtime_us = 950000
kernel.sched_time_avg = 1000
kernel.timer_migration = 1
permission denied on key 'kernel.usermodehelper.bset'
sysctl: permission denied on key 'kernel.usermodehelper.inheritable'
net.core.xfrm_aevent_etime = 10
net.ipv4.ipfrag_time = 30
net.ipv4.neigh.default.base_reachable_time_ms = 30000
net.ipv4.neigh.default.delay_first_probe_time = 5
net.ipv4.neigh.default.gc_stale_time = 60
net.ipv4.neigh.default.locktime = 100
net.ipv4.neigh.default.retrans_time_ms = 1000
net.ipv4.neigh.eth0.base_reachable_time_ms = 30000
net.ipv4.neigh.eth0.delay_first_probe_time = 5
net.ipv4.neigh.eth0.gc_stale_time = 60
net.ipv4.neigh.eth0.locktime = 100
net.ipv4.neigh.eth0.retrans_time_ms = 1000
net.ipv4.neigh.lo.base_reachable_time_ms = 30000
net.ipv4.neigh.lo.delay_first_probe_time = 5
net.ipv4.neigh.lo.gc_stale_time = 60
net.ipv4.neigh.lo.locktime = 100
net.ipv4.neigh.lo.retrans_time_ms = 1000
net.ipv4.neigh.wlan0.base_reachable_time_ms = 30000
net.ipv4.neigh.wlan0.delay_first_probe_time = 5
net.ipv4.neigh.wlan0.gc_stale_time = 60
net.ipv4.neigh.wlan0.locktime = 100
net.ipv4.neigh.wlan0.retrans_time_ms = 1000
net.ipv4.route.gc_timeout = 300
net.ipv4.tcp_fin_timeout = 60
net.ipv4.tcp_keepalive_time = 7200
net.ipv4.tcp_thin_linear_timeouts = 0
net.ipv4.tcp_timestamps = 1
net.ipv6.ip6frag_time = 60
net.ipv6.neigh.default.base_reachable_time_ms = 30000
net.ipv6.neigh.default.delay_first_probe_time = 5
net.ipv6.neigh.default.gc_stale_time = 60
net.ipv6.neigh.default.locktime = 0
net.ipv6.neigh.default.retrans_time_ms = 1000
net.ipv6.neigh.eth0.base_reachable_time_ms = 30000
net.ipv6.neigh.eth0.delay_first_probe_time = 5
net.ipv6.neigh.eth0.gc_stale_time = 60
net.ipv6.neigh.eth0.locktime = 0
net.ipv6.neigh.eth0.retrans_time_ms = 1000
net.ipv6.neigh.lo.base_reachable_time_ms = 30000
net.ipv6.neigh.lo.delay_first_probe_time = 5
net.ipv6.neigh.lo.gc_stale_time = 60
net.ipv6.neigh.lo.locktime = 0
net.ipv6.neigh.lo.retrans_time_ms = 1000
net.ipv6.neigh.wlan0.base_reachable_time_ms = 30000
net.ipv6.neigh.wlan0.delay_first_probe_time = 5
net.ipv6.neigh.wlan0.gc_stale_time = 60
net.ipv6.neigh.wlan0.locktime = 0
net.ipv6.neigh.wlan0.retrans_time_ms = 1000
net.ipv6.route.gc_timeout = 60

---------------------------------------------

I would think that network latencies would mask any local hardware limitations.  It would be interesting to plot input-characters-per-second versus IOWaits or other system parameter to see the effect of massive input flooding.

---

### Post by vtsstumpjump on 2013-05-25
Ok very interesting so you can set to poll the hardware a 1 kHz and there is 16 keys in the buffer in the hardware.

So Assuming the PC could handle a clock rate of 208 kHz on the PS2 port..I could send 15 keystrokes in 1 mS and not have a buffer overflow. Also assuming that the printer port goes at a faster speed also because I can service the port at over 400 kHz in QuickBasic on a P2-233.

The importance of my programs is queuing the commands to the slave computer then coming back to see the results, may not need terminal services.

Ps I have asked Intel about a mother board with a faster clock on the PS/2 port, I might have to revise the frequency for Ubuntu.

PPs I am doing this for FUN! and something to pass the time.


Here is some confirmations of what I have achieved.
The first 2 prove the tuning up and I have put in a link to conserve my free band width at photobucket but by all means examine the 3 screen dumps, the website for the free test now they have put a delay in there speed test on there site so I cant push the limits anymore... no fun in that at all.



[http://i231.photobucket.com/albums/ee44/smokingwheels/Typing%20Speed%20test/typingtest2883wpm.jpg](http://i231.photobucket.com/albums/ee44/smokingwheels/Typing%20Speed%20test/typingtest2883wpm.jpg)

[http://i231.photobucket.com/albums/ee44/smokingwheels/Typing%20Speed%20test/typingtest3897wpm.jpg](http://i231.photobucket.com/albums/ee44/smokingwheels/Typing%20Speed%20test/typingtest3897wpm.jpg)

My record

[IMG]http://i231.photobucket.com/albums/ee44/smokingwheels/Typing%20Speed%20test/Typingtest4104WPM.jpg[/IMG]

---

### Post by tgalati4 on 2013-05-25
I believe you can set the kernel polling to values other than 100, 250, and 1000 Hz, it's just that the kernel configurator gives you a choice of those values.  It's possible that changing the value to some oddball Hz value could cause a race condition which would lock up the machine.  So if 2000 Hz gives your typing robot a higher wps score, then you could experiment with even higher values.  Although the ticks value is not in sysctl, which would require a kernel recompile for each value that you wanted to experiment with.  

I have only played with 100, 250 and 1000 Hz.  The system is more visually responsive to mouse inputs at 1000 Hz, and I couldn't tell the difference between 100 and 250 Hz.  The server version was set to 100 or 250 and the desktop was set to 1000 Hz for default values (for older 2.6.X kernels).  My understanding is that the server and desktop kernel configuration is now the same, so I don't know what the current default tick value is in 3.X.X kernels.

---

