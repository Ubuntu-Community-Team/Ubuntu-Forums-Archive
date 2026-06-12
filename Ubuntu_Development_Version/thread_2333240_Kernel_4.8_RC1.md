---
title: "Kernel 4.8 RC1"
date: 2016-08-08
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2016-08-08
Greetings,
Finally a usable RC1, very smooth. At least on my system. Big change list.

---

### Post by Doug S on 2016-08-09
Just catching up, again.
I am running a slightly modified kernel 4.8-rc1 for a few hours now, hard hours with lots going on. So far so good.

---

### Post by Doug S on 2016-08-17
Just catching up, again. rc2 has been available for a couple of days. The kernel configuration file has a lot of changes between rc1 and rc2. I am running a slightly modified (same changes as I had in my -rc1) kernel 4.8-rc2 for a few hours now. So far so good.

---

### Post by rrnbtter on 2016-08-17
Greetings,
Intel doesn't have drivers available for 4.8 so Intel firmware users may have some screen discoloration. But tolerable.

---

### Post by Doug S on 2016-08-25
This Kernel 4.8 rc series cycle is turning out to be relatively quiet, which is a good thing. I forgot to post here about -rc3. I have been using it for a few days, without issues.

---

### Post by Doug S on 2016-08-29
Hmmm... Kernel 4.8-rc4 is available from [kernel.org]("https://www.kernel.org/"), but doesn't yet seem to be in the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"). I wonder why not? Anyway, myself I have to stay with kernel 4.8-rc3 for awhile yet, until I finish some tests.

EDIT: Evidently, there was some firewall issue, ppa - mainline 4.8-rc4 should be available by tomorrow (Thursday).

---

### Post by Rustan on 2016-08-31
linux - 4.8.0-5.6
rebase to v4.8-rc4
available from 
[https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable)

---

### Post by fyfe54 on 2016-08-31
> **Doug S said:**
> Hmmm... Kernel 4.8-rc4 is available from [kernel.org]("https://www.kernel.org/"), but doesn't yet seem to be in the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"). I wonder why not? Anyway, myself I have to stay with kernel 4.8-rc3 for awhile yet, until I finish some tests.

EDIT: Evidently, there was some firewall issue, ppa - mainline 4.8-rc4 should be available by tomorrow (Thursday).


It's available now.  7:27 pm Eastern US.

---

### Post by Doug S on 2016-09-02
Is anyone seeing extremely high loads averages immediately after boot?
For me, it started with those huge kernel configuration changes between kernel 4.7-rc4 and 4.7-rc5, it is just that I didn't notice it until now (kernel 4.8-rc3, I still haven't moved to -rc4).

I compiled kernel 4.7-rc5, but using the kernel configuration from 4.7-rc4 and the problem did not exist, from which I conclude that issue was introduced as a result of the configuration change as opposed to some code change.
I'm not sure how to isolate the specific kernel configuration change. I've tried reverting a couple of the changes that I guessed might be the cause, but they weren't.

For more detail see a post I added to the [kernel 4.7 rc series]("https://ubuntuforums.org/showthread.php?t=2326220&page=5&p=13539240#post13539240") thread.

---

### Post by Doug S on 2016-09-04
I am seeing a staggering number of kworker tasks:```
top - 09:48:40 up 50 min,  3 users,  load average: 4.16, 10.72, 7.18
Tasks: [COLOR="#FF0000"]2210[/COLOR] total,   1 running, [COLOR="#FF0000"]2209[/COLOR] sleeping,   0 stopped,   0 zombie
``````
doug@s15:~/temp-git-phoronix/phoronix-test-suite$ ps aux | grep kworker | grep -v H | grep -v u | head -20
root      5827  0.0  0.0      0     0 ?        S    09:04   0:00 [kworker/3:74]
root      5830  0.0  0.0      0     0 ?        S    09:04   0:00 [kworker/3:75]
root      6414  0.0  0.0      0     0 ?        S    09:04   0:00 [kworker/4:187]
root      6768  0.0  0.0      0     0 ?        S    09:04   0:00 [kworker/6:140]
root      6769  0.0  0.0      0     0 ?        S    09:04   0:00 [kworker/6:141]
root      6890  0.0  0.0      0     0 ?        S    09:04   0:00 [kworker/4:240]
root      8404  0.0  0.0      0     0 ?        S    09:25   0:00 [kworker/5:4]
root      8575  0.0  0.0      0     0 ?        S    09:25   0:00 [kworker/2:63]
root      8577  0.0  0.0      0     0 ?        S    09:25   0:00 [kworker/2:64]
root      8620  0.0  0.0      0     0 ?        S    09:25   0:00 [kworker/0:115]
root      8622  0.0  0.0      0     0 ?        S    09:25   0:00 [kworker/0:116]
root      8836  0.0  0.0      0     0 ?        S    09:25   0:00 [kworker/5:256]
root      8854  0.0  0.0      0     0 ?        S    09:35   0:00 [kworker/5:0]
root      8856  0.0  0.0      0     0 ?        S    09:35   0:00 [kworker/5:1]
root      8857  0.0  0.0      0     0 ?        S    09:35   0:00 [kworker/5:2]
root      8858  0.0  0.0      0     0 ?        S    09:35   0:00 [kworker/6:0]
root      8859  0.0  0.0      0     0 ?        S    09:35   0:00 [kworker/5:3]
root      8863  0.0  0.0      0     0 ?        S    09:35   0:00 [kworker/6:1]
root      8864  0.0  0.0      0     0 ?        S    09:35   0:00 [kworker/6:2]
root      8866  0.0  0.0      0     0 ?        S    09:35   0:00 [kworker/6:3]

```I haven't begun to investigate yet, I just don't recall seeing such before.

---

### Post by Doug S on 2016-09-06
[Kernel 4.8-rc5]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8-rc5/") has been available for a couple of days. I'm running it now.
I am still seeing very high load average and over 2000 kworker processes immediately after boot. Eventually, the kworker tasks terminate. Is anyone else seeing this?

EDIT: My main test computer is a server, with no GUI stuff. As such "idle" is really quite 'idle", as opposed to desktops with tons of stuff going on when supposedly "idle". Even so, and for the testing I am currently doing, I needed "idle" to be even better. So, I turn off some more services, such as samba, mysql, apache, cron, apt (which were all not doing anything anyhow). If I wait until all of those kworker processes have terminated, and then run my services_off script and then services_on, I'll get the huge load average back and again over 2000 kworker processes (I suspect 256X8 CPUs = 2048).

---

### Post by Doug S on 2016-09-18
> **Doug S said:**
> I am still seeing very high load average and over 2000 kworker processes immediately after boot. Eventually, the kworker tasks terminate. Is anyone else seeing this?Is nobody else observing this behavior? Or is nobody else using any 4.8-rc series kernel?

---

### Post by Doug S on 2016-09-19
Kernel [4.8-rc7 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8-rc7/"). Myself, I'm still on 4.8-rc5, and it'll be awhile before I can catch up.

---

### Post by zika on 2016-09-19
It took me time to get some spare time to do some checks. Try with increasing value in [COLOR=#000000]/proc/sys/vm/dirty_writeback_centisecs[/COLOR] ...
Not a magic bullet but it might work... You should find what is producing so much placeholders at Your exact install...

---

### Post by MikeMecanic on 2016-09-19
> **Doug S said:**
> Is nobody else observing this behavior? Or is nobody else using any 4.8-rc series kernel?

   	 	 	 	   Just made a fresh install of Kylin xx.1 and I don’t see anything abnormal, furthermore 4.8-rc7 runs like a Swiss clock.   
 
 
 dpkg --list | grep linux-image
 ii  [COLOR=#ff3333]**linux-imag**[/COLOR]e-4.4.0-38-generic               4.4.0-38.57                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.8.0-040800rc7-generic        4.8.0-040800rc7.201609182130                                amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]**linux-image-extra**[/COLOR]-4.4.0-38-generic         4.4.0-38.57                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-generic                        4.4.0.38.40                                                 amd64        Generic Linux kernel image

---

### Post by fthx on 2016-09-19
Have a look at proposed repository ;-)

---

### Post by Doug S on 2016-09-19
Hi zika, haven't seen you around for awhile.

> **zika said:**
> It took me time to get some spare time to do some checks. Try with increasing value in [COLOR=#000000]/proc/sys/vm/dirty_writeback_centisecs[/COLOR] ...
But why would that be kernel configuration dependent? I get that it is 500 for both the new and old kernel configuration. I'll try messing with it though.

> **zika said:**
> You should find what is producing so much placeholders at Your exact install...Well, it seems to be related to systemd and starting services. My results were inconclusive when I tried to determine which exact service. I'll try again. These are the ones I was playing with (while attempting to get a really really idle system for some other tests):
```
$ cat set_cpu_turn_on_services
#! /bin/bash
# Turn on some services that were previously turned off
sudo systemctl start apt-daily.timer
sudo systemctl start winbind.service
sudo systemctl start cron.service
sudo systemctl start nmbd.service
sudo systemctl start smbd.service
sudo systemctl start apache2.service
sudo systemctl start mysql.service

```There is nothing special with my computer. It is an Ubuntu 16.04 server, no GUI. I rarely (almost never) run the stock kernel, almost always running a recent, but patched, mainline.

---

### Post by zika on 2016-09-20
> **Doug S said:**
> Hi zika, haven't seen you around for awhile.I'm here as often as I was always. Just not having anything to s(t)ay... ;)

---

### Post by Doug S on 2016-09-21
> **Doug S said:**
> I am still seeing very high load average and over 2000 kworker processes immediately after boot. Eventually, the kworker tasks terminate. Is anyone else seeing this?

O.K. I have some more details on this issue:
. It only occurs for root processes.
. It has something to do with pipelining (I think).
. The kworker tasks linger, idle, for 5 minutes +- a few seconds after an event.
. On my server, there is a default CRON php file clean up task that runs every 30 minutes, and causes ~2000 kworker threads.
. The thread count is not limited to 8 CPU's times 256 (as I had thought earlier), I have seen, for example: [kworker/7:257]
. I can create the issue fairly simply myself (see below).
. I have tried reverting several kernel configuration settings, but still haven't isolated the exact configuration change cause.

How I create the high number of kworker threads issue:

1.) make a sub-directory.
2.) dump a bunch of small files (3000) into that directory. (I use a program I wrote one time).
3.) run this (as sudo, because as normal user doesn't work):
```
doug@s15:~/temp2$ [COLOR="#FF0000"]cat try_stuff[/COLOR]
#! /bin/bash
#
# try_stuff Smythies 2016.09.20
#       And attempt to have a simplified version of
#       obtaining the lingering (idle) kworker processes issue.
#
echo ... begin ...
ps -A --no-headers | wc -l
(
for file in abcdefgh*; do
#  touch -c $file &
  ./subroutine $file &
done
)
echo ... end ...
ps -A --no-headers | wc -l

```which calls this:
```
#! /bin/bash
grep -b bla $1 | grep zzz | grep yyy | grep xxx | grep www | grep vvv | grep uuu | grep ttt | grep sss | grep rrr | grep qqq | grep ppp | grep ooo
```

I use this to monitor the situation:```
doug@s15:~/temp2$ [COLOR="#FF0000"]cat processes2[/COLOR]
#!/bin/dash

while [ 1 ];
do
  echo $(uptime) ::: $(ps -A --no-headers | wc -l) ::: $(ps aux | grep kworker | grep -v u | grep -v H | wc -l)
  sleep 10.0
done

```And here is an example:```
08:30:52 up 9:30, 3 users, load average: 0.01, 6.02, 7.11 ::: 181 ::: 16
08:31:02 up 9:30, 3 users, load average: 0.01, 5.82, 7.03 ::: 181 ::: 16
08:31:12 up 9:30, 3 users, load average: 0.01, 5.63, 6.96 ::: 181 ::: 16
08:31:22 up 9:30, 3 users, load average: 191.46, 46.31, 20.17 ::: 2226 ::: 2057
08:31:33 up 9:31, 3 users, load average: 162.02, 44.79, 19.96 ::: 2222 ::: 2057
08:31:43 up 9:31, 3 users, load average: 137.11, 43.31, 19.74 ::: 2222 ::: 2057
08:31:53 up 9:31, 3 users, load average: 116.03, 41.88, 19.53 ::: 2222 ::: 2057
08:32:03 up 9:31, 3 users, load average: 98.19, 40.50, 19.32 ::: 2222 ::: 2057
08:32:14 up 9:31, 3 users, load average: 83.09, 39.17, 19.11 ::: 2222 ::: 2057

```And now with a kernel compiled with the old kernel configuration:```
08:39:35 up 5 min, 3 users, load average: 0.01, 0.20, 0.13 ::: 179 ::: 16
08:39:45 up 5 min, 3 users, load average: 0.01, 0.20, 0.13 ::: 179 ::: 16
08:39:55 up 6 min, 3 users, load average: 0.01, 0.19, 0.13 ::: 179 ::: 16
08:40:05 up 6 min, 3 users, load average: 0.01, 0.18, 0.13 ::: 707 ::: 16  <<< script is running
08:40:16 up 6 min, 3 users, load average: 27.56, 6.28, 2.12 ::: 181 ::: 17
08:40:26 up 6 min, 3 users, load average: 23.32, 6.08, 2.10 ::: 181 ::: 17
08:40:36 up 6 min, 3 users, load average: 19.73, 5.87, 2.08 ::: 181 ::: 17
08:40:46 up 6 min, 3 users, load average: 16.70, 5.68, 2.06 ::: 181 ::: 17
```Note: The high load average stuff is an expected by-product of the way I have done my experiment. It is the kworker thread count that is of interest here.

EDIT: I observe the same on my yakety test computer today after it got kernel 4.8 as an upgrade (2 CPUs):```
16.10 test computer:

Linux cyd-hp2 4.4.0-9136-generic #55-Ubuntu SMP Fri Aug 26 05:58:34 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

11:35:19 up 19:13, 3 users, load average: 1.20, 0.52, 0.20 ::: 224 ::: 4
11:35:29 up 19:13, 3 users, load average: 1.17, 0.54, 0.21 ::: 232 ::: 5
11:35:39 up 19:13, 4 users, load average: 1.14, 0.55, 0.22 ::: 229 ::: 5
11:35:49 up 19:13, 4 users, load average: 1.28, 0.60, 0.24 ::: 228 ::: 5
11:35:59 up 19:13, 4 users, load average: 1.55, 0.68, 0.27 ::: 223 ::: 5
11:36:09 up 19:13, 4 users, load average: 1.55, 0.71, 0.28 ::: 229 ::: 9
11:36:19 up 19:14, 4 users, load average: 1.46, 0.72, 0.29 ::: 226 ::: 11
11:36:29 up 19:14, 4 users, load average: 1.24, 0.69, 0.29 ::: 226 ::: 11
11:36:39 up 19:14, 4 users, load average: 1.05, 0.67, 0.28 ::: 226 ::: 11
11:36:50 up 19:14, 4 users, load average: 16.82, 3.95, 1.35 ::: 264 ::: 11
11:37:02 up 19:14, 4 users, load average: 67.30, 15.65, 5.21 ::: 424 ::: 11
11:37:13 up 19:14, 4 users, load average: 107.79, 26.11, 8.73 ::: 335 ::: 11
11:37:24 up 19:15, 4 users, load average: 111.12, 29.50, 10.02 ::: 611 ::: 11
11:37:36 up 19:15, 4 users, load average: 129.43, 36.13, 12.39 ::: 310 ::: 11
11:37:47 up 19:15, 4 users, load average: 125.53, 40.04, 14.06 ::: 226 ::: 11
11:37:57 up 19:15, 4 users, load average: 106.23, 38.73, 13.91 ::: 226 ::: 11
11:38:07 up 19:15, 4 users, load average: 89.89, 37.45, 13.76 ::: 226 ::: 11

Linux cyd-hp2 4.8.0-11-generic #12-Ubuntu SMP Sat Sep 17 20:00:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

12:56:55 up 1:16, 3 users, load average: 0.00, 0.00, 0.00 ::: 184 ::: 6
12:57:05 up 1:16, 3 users, load average: 0.00, 0.00, 0.00 ::: 184 ::: 6
12:57:15 up 1:16, 3 users, load average: 0.00, 0.00, 0.00 ::: 184 ::: 6
12:57:25 up 1:16, 3 users, load average: 0.00, 0.00, 0.00 ::: 183 ::: 5
12:57:35 up 1:17, 3 users, load average: 0.00, 0.00, 0.00 ::: 183 ::: 5
12:57:45 up 1:17, 3 users, load average: 0.00, 0.00, 0.00 ::: 183 ::: 5
12:57:56 up 1:17, 3 users, load average: 0.00, 0.00, 0.00 ::: 186 ::: 7
12:58:06 up 1:17, 3 users, load average: 30.59, 6.34, 2.05 ::: 830 ::: 515
12:58:16 up 1:17, 3 users, load average: 41.51, 9.52, 3.13 ::: 1065 ::: 515
12:58:26 up 1:17, 3 users, load average: 48.43, 12.05, 4.03 ::: 793 ::: 515
12:58:36 up 1:18, 3 users, load average: 72.54, 18.37, 6.16 ::: 935 ::: 515
12:58:47 up 1:18, 3 users, load average: 73.90, 20.45, 6.97 ::: 749 ::: 515
12:58:57 up 1:18, 3 users, load average: 81.89, 23.95, 8.26 ::: 842 ::: 515
12:59:07 up 1:18, 3 users, load average: 79.44, 25.37, 8.89 ::: 693 ::: 515
12:59:17 up 1:18, 3 users, load average: 67.23, 24.54, 8.80 ::: 693 ::: 515
12:59:27 up 1:18, 3 users, load average: 56.89, 23.73, 8.70 ::: 693 ::: 515

```

---

### Post by Doug S on 2016-09-22
Even simpler method to create the issue:

Run this (as sudo):```
doug@s15:~/temp2$ [COLOR="#FF0000"]cat try_stuff3[/COLOR]
#! /bin/dash
#
# try_stuff3 Smythies 2016.09.21
#       And attempt to have a simplified version of
#       obtaining the lingering (idle) kworker processes issue.
#
echo ... begin ...
ps -A --no-headers | wc -l

LOOPS=0
while [ $LOOPS -lt 8 ];do   [COLOR="#FF0000"]<<< loop count = number of CPUs[/COLOR]
  ./subroutine3 &
  LOOPS=$((LOOPS+1))
done
sleep 1
echo ... end ...
ps -A --no-headers | wc -l
``````
$ [COLOR="#FF0000"]cat subroutine3[/COLOR]
#! /bin/bash
# I do not actually want any output, so the last search terms is not present
echo 'blaooo' | grep bla | grep ooo | grep aaa
```Most of the time will result in your number of CPUs * ~257 kworker threads (not the "u" or "H" type) for 5 minutes. (on my computer, I re-compiled with a timeout of of 30 seconds instead of 5 minutes, so that I could debug faster)

---

### Post by Doug S on 2016-09-22
For the many kworker threads, with a side effect of high reported loads averages, see [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626564").

---

### Post by Doug S on 2016-09-22
For the many kworker threads, with a side effect of high reported loads averages, see [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626564").

---

### Post by zika on 2016-09-24
What is new &#8222;cloud&#8220; mainline kernel bringing to us?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2016-09-24/linux-headers-4.8.0-999-cloud_4.8.0-999.201609232201_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2016-09-24/linux-headers-4.8.0-999-cloud_4.8.0-999.201609232201_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2016-09-24/linux-image-4.8.0-999-cloud_4.8.0-999.201609232201_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2016-09-24/linux-image-4.8.0-999-cloud_4.8.0-999.201609232201_amd64.deb)

---

### Post by Doug S on 2016-10-03
I have been running [kernel 4.8]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8/") for a few hours now without any new issue (still got many kworker threads after boot).

zika: I don't know the story behind those new "cloud" kernels, nor how they are different than the other kernels.

---

### Post by dino99 on 2016-10-05
Actually using 4.8.0-21 from CKT unstable ppa: very stable as the previous ones were too.

---

